---
title: Solucionar problemas de alertas de log no Azure Monitor
description: Problemas comuns, erros e resoluções para as regras de alerta de log no Azure.
author: msvijayn
services: azure-monitor
ms.service: azure-monitor
ms.topic: conceptual
ms.date: 10/29/2018
ms.author: vinagara
ms.component: alerts
ms.openlocfilehash: cffc3ac8808992f7884839329e5bf152d318820c
ms.sourcegitcommit: 295babdcfe86b7a3074fd5b65350c8c11a49f2f1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/27/2018
ms.locfileid: "53789357"
---
# <a name="troubleshooting-log-alerts-in-azure-monitor"></a>Solucionar problemas de alertas de log no Azure Monitor  

## <a name="overview"></a>Visão geral

Este artigo mostra como resolver problemas comuns observados ao configurar alertas de log no monitor do Azure. Além disso, fornece soluções para perguntas frequentes sobre funcionalidade ou configuração de alertas de log. 

O termo **Alertas de Log** descreve alertas que são acionados com base em uma consulta personalizada no [Log Analytics](../learn/tutorial-viewdata.md) ou [Application Insights](../../azure-monitor/app/analytics.md). Saiba mais sobre funcionalidade, terminologia e tipos em [Alertas de log - Visão geral](../platform/alerts-unified-log.md).

> [!NOTE]
> Este artigo não considera os casos em que o portal do Azure é exibido, a regra de alerta é disparada e uma notificação é executada por Grupos de Ações associados. Para esses casos, consulte os detalhes no artigo sobre [Grupos de Ação](../platform/action-groups.md).


## <a name="log-alert-didnt-fire"></a>Alerta de log não acionado

A seguir, são apresentados alguns motivos comuns por que uma regra de alerta de log [configurada no estado do Azure Monitor](../platform/alerts-log.md) não mostra [como *acionado* quando esperado](../platform/alerts-managing-alert-states.md). 

### <a name="data-ingestion-time-for-logs"></a>Hora da ingestão de dados para logs

O alerta de log executa periodicamente a consulta com base no [Log Analytics](../learn/tutorial-viewdata.md) ou [Application Insights](../../azure-monitor/app/analytics.md). Como o Log Analytics processa muitos terabytes de dados de milhares de clientes de fontes variadas em todo o mundo, o serviço é suscetível a um atraso de tempo variável. Para saber mais, confira [Tempo de ingestão de dados no Log Analytics](../platform/data-ingestion-time.md).

Para atenuar atraso na ingestão de dados, o sistema aguardará e repetirá a consulta de alerta várias vezes, se descobrir que os dados necessários ainda não foram processados. O sistema tem um tempo de espera de aumento exponencial. O alerta de log será disparado somente depois que os dados estiverem disponíveis, portanto, o atraso poderá ocorrer devido à lenta ingestão de dados. 

### <a name="incorrect-time-period-configured"></a>Período de tempo incorreto configurado

Conforme descrito no artigo sobre terminologia [para alertas de log](../platform/alerts-unified-log.md#log-search-alert-rule---definition-and-types), o período de tempo indicado na configuração especifica o intervalo de tempo da consulta. A consulta retorna somente os registros que foram criados dentro desse intervalo de tempo. O período de tempo restringe os dados buscados para consulta de log para evitar abusos e contorna qualquer comando de tempo (como *atrás*) usados na consulta de log. Por exemplo, se o período de tempo estiver definido como 60 minutos e a consulta for executada às 13h15, somente registros criados entre 12h15 e 13h15 serão usados para a consulta de log. Se a consulta de log usar um comando de tempo como *atrás (1d)*, a consulta ainda usará dados entre 12h15 e 13h15 porque o período de tempo está definido para esse intervalo.*

Portanto, verifique se o período de tempo na configuração corresponde à consulta. Para o exemplo especificado anteriormente, se a consulta de log usar *atrás (1d)* como mostrado com marcador Verde, o período de tempo deverá ser definido como 24 horas ou 1440 minutos (conforme indicado em Vermelho), para garantir que a consulta seja executada conforme pretendido.

![Período de tempo](media/alert-log-troubleshoot/LogAlertTimePeriod.png)

### <a name="suppress-alerts-option-is-set"></a>A opção Suprimir Alertas está definida

Conforme descrito na etapa 8 do artigo sobre a [criação de uma regra de alerta de log no portal do Azure](../platform/alerts-log.md#managing-log-alerts-from-the-azure-portal), os alertas de log fornecem uma opção **Suprimir Alertas** para suprimir ações de disparo e notificação por um período de tempo configurado. Como resultado, você poderá pensar que um alerta não disparou enquanto na verdade isso aconteceu, mas foi suprimido.  

![Suprimir alertas](media/alert-log-troubleshoot/LogAlertSuppress.png)

### <a name="metric-measurement-alert-rule-is-incorrect"></a>A regra de alerta com medição métrica está incorreta

**Alertas de log de medição métrica** são um subtipo de alertas de log que possuem recursos especiais e uma sintaxe de consulta de alerta restrita. Uma regra de alerta de log de medição métrica requer que a saída da consulta seja uma série temporal métrica, ou seja, uma tabela com períodos de tempo distintos igualmente dimensionados, juntamente com os valores agregados correspondentes. Além disso, os usuários podem optar por ter variáveis adicionais na tabela ao lado de AggregatedValue. Essas variáveis podem ser usadas para classificar a tabela. 

Por exemplo, suponha que uma regra de alerta de log de medição métrica foi configurada como:

- a consulta era: `search *| summarize AggregatedValue = count() by $table, bin(timestamp, 1h)`  
- período de 6 horas
- limite de 50
- lógica de alerta de três violações consecutivas
- Aggregate Upon escolhido como $table

Como o comando incluiu *resumir … por* e forneceu duas variáveis (carimbo de data/hora e $table), o sistema escolherá $table como *Aggregate Upon*. Ele classifica a tabela de resultados pelo campo *$table*, conforme mostrado abaixo, e analisa o AggregatedValue múltiplo para cada tipo de tabela (como availabilityResults) para verificar se houve violações consecutivas de 3 ou mais.

![Execução de consulta de medição métrica com vários valores](media/alert-log-troubleshoot/LogMMQuery.png)

Como *Aggregate Upon* é definido em *$table* – os dados são classificados na coluna $table (como em VERMELHO); em seguida, agrupamos e procuramos por tipos de campo de *Aggregate Upon* (ou seja) $table – por exemplo: valores para availabilityResults serão considerados como uma plotagem/entidade (conforme realçado em Laranja). Nessa plotagem/entidade de valor – o serviço de alerta procura três violações consecutivas (como mostrado em Verde), para as quais o alerta será disparado para o valor de tabela 'availabilityResults'. Da mesma forma, se para qualquer outro valor de $table três violações consecutivas forem vistas - outra notificação de alerta será disparada para a mesma coisa; com o serviço de alerta classificando automaticamente os valores em uma plotagem/entidade (como em Laranja) por vez.

Agora suponha que a regra de alerta de log de medição métrica tenha sido modificada e a consulta fosse `search *| summarize AggregatedValue = count() by bin(timestamp, 1h)` com o restante da configuração igual à anterior, incluindo a lógica de alerta para três violações consecutivas. A opção "Aggregate Upon" nesse caso será por padrão: carimbo de hora. Já que apenas um valor é fornecido na consulta para *resumir ... por* (ou seja) *timestamp*; semelhante ao exemplo anterior, no final da execução, a saída seria igual à ilustrada abaixo.

   ![Execução de consulta de medição métrica com valor singular](media/alert-log-troubleshoot/LogMMtimestamp.png)

Como *Aggregate Upon* é definido por timestamp – os dados são classificados na coluna de *timestamp* (como em VERMELHO); em seguida, agrupamos por data/hora – por exemplo: os valores para  `2018-10-17T06:00:00Z` serão considerados como uma plotagem/entidade (conforme realçado em Laranja). Nessa plotagem/entidade de valor, o serviço de alerta não encontrará violações consecutivas (pois cada valor de carimbo de data e hora tem apenas uma entrada) e, portanto, nunca será disparado. Portanto, nesse caso, o usuário precisa:

- Adicionar uma variável fictícia ou uma variável existente (como $table) para classificar corretamente usando o campo "Aggregate Upon" configurado
- (Ou) reconfigurar a regra de alerta para usar a lógica de alerta com base no *total de violações*, conforme adequado

## <a name="log-alert-fired-unnecessarily"></a>Alerta de log disparado desnecessariamente

Veja a seguir alguns motivos comuns por que uma [regra de alerta de log configurada no Azure Monitor](../platform/alerts-log.md) pode disparar quando exibida nos [Alertas do Azure](../platform/alerts-managing-alert-states.md), quando não era essa a expectativa.

### <a name="alert-triggered-by-partial-data"></a>Alerta disparado por dados parciais

As análises que capacitam o Log Analytics e o Application Insights estão sujeitas a atrasos de ingestão e processamento; por isso, no momento da execução da consulta de alerta de log especificada, talvez nenhum dado esteja disponível ou apenas alguns dados estejam disponíveis. Para saber mais, confira [Tempo de ingestão de dados no Log Analytics](../platform/data-ingestion-time.md).

Dependendo de como a regra de alerta foi configurada, poderá haver acionamentos incorretos se não houver dados ou apenas dados parciais nos logs no momento da execução do alerta. Nesses casos, aconselhamos que você altere a consulta do alerta ou a configuração. 

Por exemplo, se a regra de alerta do log estiver configurada para disparar quando o número de resultados da consulta de análise for menor que 5, o alerta será disparado quando não houver dados (zero registro) ou resultados parciais (um registro). No entanto, após o atraso de ingestão de dados, a mesma consulta com os dados completos poderá fornecer um resultado de 10 registros.

### <a name="alert-query-output-misunderstood"></a>Saída de consulta do alerta incompreendida

Você fornece a lógica para alertas de log em uma consulta de análise. A consulta de análise pode usar várias funções matemáticas e de Big Data.  O serviço de alerta executa sua consulta em intervalos especificados com os dados para o período especificado. O serviço de alerta faz alterações sutis para consulta fornecida com base no tipo de alerta escolhido. Isso pode ser visto na seção "Consulta a ser executada" na tela *Configurar lógica de sinal*, conforme mostrado abaixo: ![Consulta a ser executada](media/alert-log-troubleshoot/LogAlertPreview.png)

O que é mostrado na caixa da **consulta a ser executada** é o que o serviço de alerta de log é executa. Você poderá executar a consulta indicada, bem como o intervalo por meio do [portal do Analytics](../log-query/portals.md) ou da [API de Análise](https://docs.microsoft.com/rest/api/loganalytics/) se quiser entender o que pode ser a saída da consulta de alerta antes de realmente criar o alerta.

## <a name="next-steps"></a>Próximas etapas

- Saiba mais sobre os [Alertas de log nos alertas do Azure](../platform/alerts-unified-log.md)
- Saiba mais sobre o [Application Insights](../../azure-monitor/app/analytics.md)
- Saiba mais sobre o [Log Analytics](../../log-analytics/log-analytics-overview.md)