---
title: Criar um workspace do Log Analytics no portal do Azure | Microsoft Docs
description: Saiba como criar um workspace do Log Analytics para habilitar as soluções de gerenciamento e a coleta de dados da sua nuvem e dos ambientes locais no portal do Azure.
services: log-analytics
documentationcenter: log-analytics
author: mgoedtel
manager: carmonm
editor: ''
ms.assetid: ''
ms.service: log-analytics
ms.workload: na
ms.tgt_pltfrm: na
ms.topic: conceptual
ms.date: 08/23/2018
ms.author: magoedte
ms.openlocfilehash: dc68f00779d7b06b0498ffddbbee75a8396e952b
ms.sourcegitcommit: 5b869779fb99d51c1c288bc7122429a3d22a0363
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53186286"
---
# <a name="create-a-log-analytics-workspace-in-the-azure-portal"></a>Criar um workspace do Log Analytics no Portal do Azure
No portal do Azure, você pode configurar um workspace do Log Analytics, que é um ambiente exclusivo do Log Analytics com seu próprio repositório de dados, fontes de dados e soluções.  As etapas descritas neste artigo serão necessárias se você pretender coletar dados das seguintes fontes:

* Recursos do Azure em sua assinatura
* Computadores locais monitorados pelo System Center Operations Manager
* Coleções de dispositivos do System Center Configuration Manager 
* Dados de diagnóstico ou de log do armazenamento do Azure

Para outras fontes, como as VMs do Azure e as VMs do Windows ou do Linux em seu ambiente, veja os tópicos a seguir:

*  [Coletar dados de máquinas virtuais do Azure](../../azure-monitor/learn/quick-collect-azurevm.md) 
*  [Coletar dados de um computador Linux híbrido](../../azure-monitor/learn/quick-collect-linux-computer.md)
*  [Coletar dados de um computador Windows híbrido](quick-collect-windows-computer.md)

Se você não tiver uma assinatura do Azure, crie uma [conta gratuita](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) antes de começar.

## <a name="sign-in-to-azure-portal"></a>Entre no portal do Azure
Entre no Portal do Azure em [https://portal.azure.com](https://portal.azure.com). 

## <a name="create-a-workspace"></a>Criar um workspace
1. No portal do Azure, clique em **Todos os serviços**. Na lista de recursos, digite **Log Analytics**. Quando você começa a digitar, a lista é filtrada com base em sua entrada. Selecione **Log Analytics**.

    ![Portal do Azure](media/quick-create-workspace/azure-portal-01.png)
  
2. Clique em **Criar** e, em seguida, selecione opções para os seguintes itens:

  * Forneça um nome para o novo **Workspace do Log Analytics**, como *DefaultLAWorkspace*. 
  * Selecione uma **Assinatura** a vincular escolhendo uma na lista suspensa, se a selecionada por padrão não é adequada.
  * Para o **Grupo de Recursos**, escolha entre usar um grupo de recursos existente já configurado ou criar um novo.  
  * Selecione um **local** disponível.  Para obter mais informações, veja em quais [regiões o Log Analytics está disponível](https://azure.microsoft.com/regions/services/).
  * Se você estiver criando um workspace em uma nova assinatura feita depois de 2 de abril de 2018, ele usará o plano de preços *por GB* e a opção de selecionar um tipo de preço não estará disponível.  Se você estiver criando um workspace para uma assinatura existente feita antes de 2 de abril ou uma assinatura associada a um registro do Enterprise Agreement existente, selecione seu tipo de preço preferido.  Para obter mais informações sobre os tipos de preço específicos, consulte [Detalhes de preço do Log Analytics](https://azure.microsoft.com/pricing/details/log-analytics/).

        ![Create Log Analytics resource blade](media/quick-create-workspace/create-loganalytics-workspace-02.png)  

3. Depois de fornecer as informações necessárias no painel **Workspace do Log Analytics**, clique em **OK**.  

Enquanto as informações são verificadas e o workspace é criado, você pode acompanhar seu progresso no menu **Notificações**. 

## <a name="next-steps"></a>Próximas etapas
Agora que já tem um workspace disponível, você pode configurar a coleta de monitoramento de telemetria, executar pesquisas de logs para analisar os dados e adicionar uma solução de gerenciamento para fornecer dados adicionais e informações analíticas. 

* Para habilitar a coleta de dados de recursos do Azure com o Diagnóstico do Azure ou com o armazenamento do Azure, consulte [Coletar logs e as métricas do serviço do Azure para uso no Log Analytics](../../azure-monitor/platform/collect-azure-metrics-logs.md).  
* Adicione o [System Center Operations Manager como uma fonte de dados](../../azure-monitor/platform/om-agents.md) para coletar dados de agentes que se reportam ao seu grupo de gerenciamento do Operations Manager e armazene-o em seu repositório de workspace do Log Analytics. 
* Conecte-se ao [Configuration Manager](../../azure-monitor/platform/collect-sccm.md) para importar computadores que são membros de coleções na hierarquia.  
* Examine as [soluções de gerenciamento](https://docs.microsoft.com/azure/monitoring/monitoring-solutions-inventory?toc=%2fazure%2flog-analytics%2ftoc.json) disponíveis e como adicionar ou remover uma solução do workspace.
