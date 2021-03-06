---
title: Contas de armazenamento no Azure Stack | Microsoft Docs
description: Saiba como criar uma conta de armazenamento do Azure Stack.
services: azure-stack
documentationcenter: ''
author: mattbriggs
manager: femila
ms.service: azure-stack
ms.workload: na
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: get-started-article
ms.date: 1/14/2019
ms.author: mabrigg
ms.openlocfilehash: 66a6fa88956db40ced9ee3fd13a0f74585c528fc
ms.sourcegitcommit: 70471c4febc7835e643207420e515b6436235d29
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/15/2019
ms.locfileid: "54303200"
---
# <a name="storage-accounts-in-azure-stack"></a>Contas de armazenamento no Azure Stack
As contas de armazenamento incluem serviços Blob e Tabela e um namespace exclusivo para os objetos de dados de armazenamento. Por padrão, os dados em sua conta estão disponíveis somente para você, o proprietário da conta de armazenamento.

1. No computador do Azure Stack POC, entrar no `https://adminportal.local.azurestack.external` como [um admin](azure-stack-connect-azure-stack.md)e, em seguida, clique em **+ criar um recurso** > **dados + armazenamento**  >  **Conta de armazenamento**.

   ![](media/azure-stack-provision-storage-account/image01.png)
2. No **criar conta de armazenamento** folha, digite um nome para sua conta de armazenamento. Criar um novo **grupo de recursos**, ou selecione um existente e clique em **criar** para criar a conta de armazenamento.

   ![](media/azure-stack-provision-storage-account/image02.png)
3. Para ver sua nova conta de armazenamento, clique em **todos os recursos**, em seguida, procure a conta de armazenamento e clique em seu nome.

    ![](media/azure-stack-provision-storage-account/image03.png)

### <a name="next-steps"></a>Próximas etapas
[Usar modelos do Gerenciador de Recursos do Azure](user/azure-stack-arm-templates.md)

[Saiba mais sobre as contas de armazenamento do Azure](../storage/common/storage-create-storage-account.md)

[Baixe o guia de validação de armazenamento do Azure consistente do Azure Stack](https://aka.ms/azurestacktp1doc)
