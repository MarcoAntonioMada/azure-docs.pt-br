---
title: Gerenciar acesso usando o RBAC e o Portal do Azure | Microsoft Docs
description: Aprenda a gerenciar o acesso de usuários, grupos, entidades de serviço e identidades gerenciadas, usando o controle de acesso baseado em função (RBAC) e o portal do Azure. Isso inclui como listar o acesso, conceder o acesso e remover o acesso.
services: active-directory
documentationcenter: ''
author: rolyon
manager: mtillman
ms.assetid: 8078f366-a2c4-4fbb-a44b-fc39fd89df81
ms.service: role-based-access-control
ms.devlang: na
ms.topic: conceptual
ms.tgt_pltfrm: na
ms.workload: identity
ms.date: 11/30/2018
ms.author: rolyon
ms.reviewer: bagovind
ms.openlocfilehash: 9f5d48a074f8069e243af5644f86ad3c3d8f559b
ms.sourcegitcommit: c8088371d1786d016f785c437a7b4f9c64e57af0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2018
ms.locfileid: "52634856"
---
# <a name="manage-access-using-rbac-and-the-azure-portal"></a>Gerenciar acesso usando o RBAC e o Portal do Azure

O [Controle de acesso baseado em função (RBAC)](overview.md) é a maneira de gerenciar o acesso aos recursos no Azure. Este artigo descreve como você gerencia o acesso de usuários, grupos, entidades de serviço e identidades gerenciadas usando o RBAC e o portal do Azure.

## <a name="open-access-control-iam"></a>Abra o controle de acesso (IAM)

O **blade de controle de acesso (IAM)**, também conhecido como gerenciamento de identidade e acesso, aparece em todo o portal. Para exibir ou gerenciar o acesso no portal, a primeira coisa que você normalmente faz é abrir o blade Controle de acesso (IAM) no escopo em que deseja visualizar ou fazer uma alteração.

1. No portal do Azure, clique em **Todos os serviços** e selecione o escopo ou recurso que você deseja exibir ou gerenciar. Por exemplo, você pode selecionar **grupos de gerenciamento**, **assinaturas**, **grupos de recursos**, ou um recurso.

1. Clique no recurso específico que você deseja exibir ou gerenciar.

1. Clique em **controle de acesso (IAM)**.

    O exemplo a seguir mostra um exemplo de folha de controle (IAM) de acesso para uma assinatura.

    ![Folha IAM (controle) de acesso para uma assinatura](./media/role-assignments-portal/access-control-subscription.png)

## <a name="view-roles-and-permissions"></a>Modo de exibição de funções e permissões

Uma definição de função é uma coleção de permissões que podem ser usadas para atribuições de função. O Azure tem mais de 70 [funções internas](built-in-roles.md). Siga estas etapas para visualizar as funções e permissões que podem ser executadas no plano de gerenciamento e dados.

1. Abra **Controle de acesso (IAM)** em um escopo, como grupo de gerenciamento, assinatura, grupo de recursos ou recurso, onde você deseja visualizar funções e permissões.

1. Clique na guia **Funções** para ver uma lista de todas as funções integradas e personalizadas.

   Você pode ver o número de usuários e grupos que são atribuídos a cada função neste escopo.

   ![Lista de funções](./media/role-assignments-portal/roles-list.png)

1. Clique em uma função individual para ver quem foi atribuído a essa função e também visualize as permissões para a função.

   ![Atribuições de funções](./media/role-assignments-portal/role-assignments.png)

## <a name="view-role-assignments"></a>Exibir atribuições de função

Ao gerenciar o acesso, você deseja saber quem tem acesso, quais são suas permissões e em que nível. Para listar o acesso de um usuário, grupo, entidade de serviço ou identidade gerenciada, você visualiza as atribuições de função.

### <a name="view-role-assignments-for-a-single-user"></a>Ver atribuições de função para um único usuário

Siga estas etapas para exibir o acesso para um único usuário, grupo, entidade de serviço ou identidade gerenciada em um escopo específico.

1. Abra **Controle de acesso (IAM)** em um escopo, como grupo de gerenciamento, assinatura, grupo de recursos ou recurso, no qual você deseja visualizar o acesso.

1. Clique na guia **Verificar acesso**.

    ![Controle de acesso - verifique a guia de acesso](./media/role-assignments-portal/access-control-check-access.png)

1. Na lista **Localizar**, selecione o tipo de entidade de segurança para a qual você deseja verificar o acesso.

1. Na caixa de pesquisa, insira uma cadeia de caracteres para pesquisar no diretório nomes de exibição, endereços de e-mail ou identificadores de objetos.

    ![Verifique a lista de seleção de acesso](./media/role-assignments-portal/check-access-select.png)

1. Clique na entidade de segurança para abrir o painel **designações**.

    ![painel atribuições](./media/role-assignments-portal/check-access-assignments.png)

    Neste painel, você pode ver as funções atribuídas à entidade de segurança selecionada e ao escopo. Se houver alguma atribuição de negação neste escopo ou herdada para esse escopo, ela será listada.

### <a name="view-all-role-assignments-at-a-scope"></a>Exibir todas as atribuições de função em um escopo

1. Abra **Controle de acesso (IAM)** em um escopo, como grupo de gerenciamento, assinatura, grupo de recursos ou recurso, no qual você deseja visualizar o acesso.

1. Clique na guia **Atribuições de funções** (ou clique no botão **Visualizar** no bloco Exibir atribuições de função) para exibir todas as atribuições de função nesse escopo.

   ![Controle de acesso – guia de atribuições de função](./media/role-assignments-portal/access-control-role-assignments.png)

   Na guia Atribuições de função, você pode ver quem tem acesso nesse escopo. Observe que algumas funções são definidas para **Este recurso** enquanto outras são **(Herdadas)** de outro escopo. O acesso é atribuído especificamente a esse recurso ou herdado de uma atribuição ao escopo pai.

## <a name="add-a-role-assignment"></a>Adicionar uma atribuição de função

No RBAC, para conceder acesso, você atribui uma função a um usuário, grupo, entidade de serviço ou identidade gerenciada. Siga estas etapas para conceder acesso em diferentes escopos.

### <a name="assign-a-role-at-a-scope"></a>Atribuir uma função em um escopo

1. Abra **Controle de acesso (IAM)** em um escopo, como grupo de gerenciamento, assinatura, grupo de recursos ou recurso, no qual você deseja conceder acesso.

1. Clique na guia **Atribuições de função** para visualizar todas as atribuições de função nesse escopo.

1. Clique em **Adicionar atribuição de função** para abrir o painel Adicionar atribuição de função.

   Se você não tiver permissões para atribuir funções, a opção Adicionar atribuição de função será desativada.

   ![Adicionar painel de atribuição de função](./media/role-assignments-portal/add-role-assignment.png)

1. Na lista suspensa **Função**, selecione uma função, por exemplo, **Colaborador da Máquina Virtual**.

1. Na lista **Selecionar**, selecione um usuário, grupo, entidade de serviço ou identidade gerenciada. Se você não vir a entidade de segurança na lista, digite na caixa **Selecionar** para pesquisar nomes de exibição, endereços de email e identificadores de objeto no diretório.

1. Clique em **Salvar** para atribuir a função.

   Após alguns instantes, a entidade de segurança é atribuída a função no escopo selecionado.

### <a name="assign-a-user-as-an-administrator-of-a-subscription"></a>Atribuir um usuário como um administrador de uma assinatura

Para tornar um usuário administrador de uma assinatura do Azure, atribua-o à função [Proprietário](built-in-roles.md#owner) no escopo da assinatura. A função Proprietário permite ao usuário acesso completo a todos os recursos na assinatura, inclusive o direito de delegar acesso a outras pessoas. Essas etapas são as mesmas que as de qualquer outra atribuição de função.

1. No portal do Microsoft Azure, clique em **Todos os serviços** e, em seguida, em **Assinaturas**.

1. Clique na assinatura em que você deseja conceder acesso.

1. Clique em **controle de acesso (IAM)**.

1. Clique na guia **Atribuições de funções** para visualizar todas as atribuições de função para essa assinatura.

1. Clique em **Adicionar atribuição de função** para abrir o painel Adicionar atribuição de função.

   Se você não tiver permissões para atribuir funções, a opção Adicionar atribuição de função será desativada.

   ![Adicionar painel de atribuição de função](./media/role-assignments-portal/add-role-assignment.png)

1. Na lista suspensa **Função**, selecione a função **Proprietário**.

1. Na lista **Selecionar**, selecione um usuário. Se o usuário não estiver na lista, digite na caixa **Selecionar** para pesquisar no diretório os nomes de exibição e os endereços de email.

1. Clique em **Salvar** para atribuir a função.

   Após alguns instantes, o usuário é atribuído à função Proprietário no escopo da assinatura.

## <a name="remove-role-assignments"></a>Remover atribuições de função

No RBAC, para remover o acesso, você deve remover uma atribuição de função. Siga estas etapas para remover o acesso.

1. Abra **Controle de acesso (IAM)** em um escopo, como grupo de gerenciamento, assinatura, grupo de recursos ou recurso, no qual você deseja remover o acesso.

1. Clique na guia **Atribuições de funções** para visualizar todas as atribuições de função para essa assinatura.

1. Na lista de atribuições de função, marque a caixa de seleção ao lado de objeto com a atribuição de função de segurança que você deseja remover.

   ![Remover mensagem de atribuição de função](./media/role-assignments-portal/remove-role-assignment-select.png)

1. Clique em **Remover**.

   ![Remover mensagem de atribuição de função](./media/role-assignments-portal/remove-role-assignment.png)

1. Na mensagem para remover a atribuição de função exibida, clique em **Sim**.

    As atribuições herdadas não podem ser removidas. Se você precisar remover uma atribuição de função herdada, precisará fazê-lo no escopo em que a atribuição de função foi criada. No **escopo** coluna, próximo a **(herdado)** há um link que leva você para o escopo em que essa função foi atribuída. Vá para o escopo listado a fim de remover a atribuição de função.

   ![Remover mensagem de atribuição de função](./media/role-assignments-portal/remove-role-assignment-inherited.png)

## <a name="next-steps"></a>Próximas etapas

* [Tutorial: Conceda acesso a um usuário usando o RBAC e o portal do Microsoft Azure](quickstart-assign-role-user-portal.md)
* [Tutorial: conceder acesso a um usuário usando o RBAC e o Azure PowerShell](tutorial-role-assignments-user-powershell.md)
* [Funções internas](built-in-roles.md)
* [Organizar seus recursos com grupos de gerenciamento do Azure](../azure-resource-manager/management-groups-overview.md)
