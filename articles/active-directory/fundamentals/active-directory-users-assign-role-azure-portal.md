---
title: Atribuir funções de diretório aos usuários - Azure Active Directory | Microsoft Docs
description: Instruções sobre como atribuir funções de administrador e não administrador aos usuários com Azure Active Directory.
services: active-directory
author: eross-msft
manager: mtillman
ms.service: active-directory
ms.workload: identity
ms.component: fundamentals
ms.topic: conceptual
ms.date: 09/06/2018
ms.author: lizross
ms.reviewer: jeffsta
ms.custom: it-pro, seodec18
ms.openlocfilehash: e8646893d6dd57fd3f743f450f438cd962f02b36
ms.sourcegitcommit: 9fb6f44dbdaf9002ac4f411781bf1bd25c191e26
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/08/2018
ms.locfileid: "53095113"
---
# <a name="assign-administrator-and-non-administrator-roles-to-users-with-azure-active-directory"></a>Atribuir funções de administrador e não administrador aos usuários com Azure Active Directory
Se um usuário da sua organização precisar de permissão para gerenciar recursos do Azure AD (Azure Active Directory), você deverá atribuir ao usuário uma função apropriada no AD do Azure, com base nas ações que o usuário precisa de permissão para executar.

Para obter mais informações sobre as funções disponíveis, consulte [Atribuindo funções de administrador no Active Directory do Azure](../users-groups-roles/directory-assign-admin-roles.md). Para obter mais informações sobre como adicionar usuários, consulte [adicionar novos usuários ao Azure Active Directory](add-users-azure-active-directory.md).

## <a name="assign-roles"></a>Atribuir funções
Uma maneira comum de atribuir funções do Azure AD a um usuário está na **função de diretório** página para um usuário.

Você também pode atribuir funções usando o Privileged Identity Management (PIM). Para obter mais informações sobre como usar o PIM, consulte [Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/privileged-identity-management).

### <a name="to-assign-a-role-to-a-user"></a>Para atribuir uma função a um usuário
1. Faça login no [portal do Azure](https://portal.azure.com/) usando uma conta de administrador global para o diretório.

2. Selecione **Active Directory do Azure**, selecione **Usuários** e pesquise e selecione o usuário que está recebendo a atribuição de função. Por exemplo, _Alain Charon_.

3. Na página **Alain Charon - Perfil**, selecione **Papel de diretório**.

    O **Alain Charon - função de diretório** página será exibida.

4. Selecione **Adicionar função**, selecione a função a ser atribuída a Alain (por exemplo, _Administrador do aplicativo_) e, em seguida, escolha **Selecionar**.

    ![Página de funções de diretório, que mostra a função selecionada](media/active-directory-users-assign-role-azure-portal/directory-role-select-role.png)

    A função de administrador do Aplicativo é atribuída a Alain Charon e aparece na página **Alain Charon - Função de Diretório**.

## <a name="remove-a-role-assignment"></a>Excluir uma atribuição de função
Se você precisar remover a atribuição de função de um usuário, você também pode fazer isso na **Alain Charon - função de diretório** página.

### <a name="to-remove-a-role-assignment-from-a-user"></a>Para remover uma atribuição de função de um usuário

1. Selecione **Azure Active Directory**, selecione **usuários**e, em seguida, pesquise e selecione o usuário Obtendo a atribuição de função removida. Por exemplo, _Alain Charon_.

2. Selecione **Papel de diretório**, selecione **Administrador do aplicativo** e, em seguida, selecione **Remover função**.

    ![Página de funções de diretório, que mostra a função selecionada e a opção Remover](media/active-directory-users-assign-role-azure-portal/directory-role-remove-role.png)

    A função de administrador do aplicativo é removida do Alain Charon e ele não aparecerá mais na **Alain Charon - função de diretório** página.

## <a name="next-steps"></a>Próximas etapas
- [Adicionar ou excluir usuários](add-users-azure-active-directory.md)

- [Adicionar ou alterar informações de perfil](active-directory-users-profile-azure-portal.md)

- [Adicionar usuários convidados de outro diretório](../b2b/what-is-b2b.md)

Ou você pode executar outras tarefas de gerenciamento de usuários como atribuir delegados, usar políticas e compartilhar contas de usuários. Para obter mais informações sobre outras ações disponíveis, consulte [documentação de gerenciamento de usuário do Azure Active Directory](../users-groups-roles/index.yml).


