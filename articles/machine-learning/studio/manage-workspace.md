---
title: Gerenciar um workspace do Machine Learning Studio | Microsoft Docs
description: Gerencie o acesso aos workspace de Azure Machine Learning e implante e gerencie serviços Web da API ML
services: machine-learning
documentationcenter: ''
author: ericlicoding
ms.custom: previous-author=heatherbshapiro, previous-ms.author=hshapiro
ms.author: amlstudiodocs
editor: cgronlun
ms.assetid: daf3d413-7a77-4beb-9a7a-6b4bdf717719
ms.service: machine-learning
ms.component: studio
ms.workload: data-services
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 02/27/2017
ms.openlocfilehash: 8c5dfd82a7bf0d1985869c8de4e3b313ef885947
ms.sourcegitcommit: 7fd404885ecab8ed0c942d81cb889f69ed69a146
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/12/2018
ms.locfileid: "53270766"
---
# <a name="manage-an-azure-machine-learning-studio-workspace"></a>Gerenciar um workspace do Azure Machine Learning Studio

> [!NOTE]
> Para obter informações sobre como gerenciar serviços Web no portal de serviços Web do Machine Learning, veja [Gerenciar um serviço Web usando o portal de serviços Web do Azure Machine Learning](manage-new-webservice.md).
> 
> 

Você pode gerenciar os workspaces do Machine Learning no Portal do Azure.



## <a name="use-the-azure-portal"></a>Use o Portal do Azure

Para gerenciar um workspace no portal do Azure:

1. Entre no [Portal do Azure](https://portal.azure.com/) usando uma conta de administrador de assinatura do Azure.
2. Na caixa de pesquisa na parte superior da página, insira "workspaces do machine learning" e, em seguida, escolha **Workspace do Machine Learning**.
3. Clique no workspace que você deseja gerenciar.

Além das informações de gerenciamento de recursos padrão e das opções disponíveis, você pode:

- Exibir **Propriedades** - essa página exibe as informações do workspace e dos recursos e você pode alterar o assinatura e o grupo de recursos aos quais esse workspace está conectado.
- **Ressincronizar as Chaves de Armazenamento** - o workspace mantém chaves para a conta de armazenamento. Se a conta de armazenamento alterar as chaves, clique em **Ressincronizar chaves** para sincronizar as chaves com o workspace.

Para gerenciar os serviços Web associados a esse workspace, use o Portal de Serviços Web do Machine Learning. Consulte [Gerenciar um serviço Web usando o portal de Serviços Web do Azure Machine Learning](manage-new-webservice.md) para obter informações completas.

> [!NOTE]
> Para implantar ou gerenciar Novos serviços Web, você deverá ser atribuído a uma função de colaborador ou de administrador na assinatura na qual o serviço Web é implantado. Se você convidar outro usuário para um workspace do Machine Learning, deverá atribuí-lo a uma função colaborador ou administrador na assinatura antes de implantar ou gerenciar os serviços Web. 
> 
>Para obter mais informações sobre como definir permissões de acesso, confira [Gerenciar o acesso usando o RBAC e o portal do Azure](../../role-based-access-control/role-assignments-portal.md).

## <a name="next-steps"></a>Próximas etapas
* Saiba mais sobre [implantar o Machine Learning com modelos do Azure Resource Manager](deploy-with-resource-manager-template.md). 