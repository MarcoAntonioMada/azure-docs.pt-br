---
title: Exibir o histórico de auditoria para funções de diretório do Azure AD no PIM | Microsoft Docs
description: Saiba como exibir o histórico de auditoria para funções do diretório do Azure AD no Azure AD PIM (Privileged Identity Management).
services: active-directory
documentationcenter: ''
author: rolyon
manager: mtillman
editor: ''
ms.service: active-directory
ms.topic: conceptual
ms.workload: identity
ms.component: pim
ms.date: 02/14/2017
ms.author: rolyon
ms.custom: pim
ms.openlocfilehash: ab5a072d845bfdbaafabe1e0e7bdce2dfce6184d
ms.sourcegitcommit: 63613e4c7edf1b1875a2974a29ab2a8ce5d90e3b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43188172"
---
# <a name="view-audit-history-for-azure-ad-directory-roles-in-pim"></a>Exibir histórico de auditoria para funções de diretório do Azure AD no PIM
Você pode usar o histórico de auditoria do PIM (Privileged Identity Management) para ver todas as ativações e atribuições de usuário dentro de um determinado período de tempo para todas as funções com privilégios. Se você quiser ver o histórico completo de auditoria da atividade em seu locatário, incluindo o administrador, usuário final e atividade de sincronização, use os [Relatórios de acesso e uso do Azure Active Directory.](../reports-monitoring/overview-reports.md)

## <a name="navigate-to-audit-history"></a>Navegar para o histórico de auditoria
No painel do [portal do Azure](https://portal.azure.com) , selecione o aplicativo **Azure AD Privileged Identity Management** . De lá, acesse o histórico de auditoria clicando em **Gerenciar funções privilegiadas** > **Histórico de auditoria** no painel do PIM.

![](media/azure-ad-pim-approval-workflow/image021.png)

>[!NOTE]
É possível classificar os dados por Ação e procurar “Ativação Aprovada”


## <a name="audit-history-graph"></a>Grafo do histórico de auditoria
Você pode usar o histórico de auditoria para exibir, em um grafo de linha, o total de ativações, o número máximo de ativações diárias e a média diária de ativações.  Você também pode filtrar os dados por função se houver mais de uma função no histórico de auditoria.

Use os botões de **tempo**, **ação** e **função** para classificar o histórico.

## <a name="audit-history-list"></a>Lista do histórico de auditoria
As colunas na lista do histórico de auditoria são:

* **Solicitante** : o usuário que solicitou a ativação ou alteração da função.  Se o valor for "Sistema Azure", verifique o histórico de auditoria do Azure para obter mais informações.
* **Usuário** : o usuário que está ativando ou está atribuído a uma função.
* **Função** : a função atribuída ou ativada pelo usuário.
* **Ação** : as ações tomadas pelo solicitante. Isso pode incluir a atribuição, o cancelamento da atribuição, a ativação ou a desativação.
* **Tempo** - quando a ação aconteceu.
* **Raciocínio** -se qualquer texto foi digitado no campo de motivo durante a ativação, ele será mostrado aqui.
* **Expiração** : relevante apenas para a ativação de funções.

## <a name="filter-audit-history"></a>Filtrar histórico de auditoria
Você pode filtrar as informações que aparecem no histórico de auditoria clicando no botão **Filtrar**.  A **folha Atualizar parâmetros do gráfico** será exibida.

Depois de definir os filtros, clique em **Atualizar** para filtrar os dados no histórico.  Se os dados não aparecerem imediatamente, atualize a página.

### <a name="change-the-date-range"></a>Alterar o intervalo de data
Use os botões **Hoje**, **Última semana**, **Mês Passado** ou **Personalizar** para alterar o intervalo de tempo do histórico de auditoria.

Quando você escolher o botão **Personalizar**, terá dois campos de data, **De** e **Até**, para especificar um intervalo de datas para o histórico.  Você pode digitar as datas no formato DD/MM/AAAA, ou clique no ícone **calendário** e escolha a data em um calendário.

### <a name="change-the-roles-included-in-the-history"></a>Alterar as funções incluídas no histórico
Marque ou desmarque a caixa de seleção **Função** ao lado de cada função para incluí-la ou excluí-la do histórico.

<!--Every topic should have next steps and links to the next logical set of content to keep the customer engaged-->
## <a name="next-steps"></a>Próximas etapas

- [Exibir histórico de auditoria para funções de recurso do Azure no PIM](pim-resource-roles-use-the-audit-log.md)
