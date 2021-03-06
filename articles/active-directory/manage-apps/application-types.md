---
title: Aplicativo inesperado em minha lista de aplicativos | Microsoft Docs
description: Como ver todos os aplicativos em seu locatário e entender como os aplicativos aparecem na lista Todos os Aplicativos em Aplicativos Empresariais
services: active-directory
documentationcenter: ''
author: barbkess
manager: mtillman
ms.assetid: ''
ms.service: active-directory
ms.component: app-mgmt
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 07/11/2017
ms.author: barbkess
ms.openlocfilehash: f6c18ce80e1c94ceac56bf188dcf62cc9ea94f7a
ms.sourcegitcommit: 11d8ce8cd720a1ec6ca130e118489c6459e04114
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2018
ms.locfileid: "52832795"
---
# <a name="unexpected-application-in-my-applications-list"></a>Aplicativo inesperado em minha lista de aplicativos

Este artigo o ajudará a entender como os aplicativos aparecem na lista **Todos os Aplicativos** em **Aplicativos Empresariais**. 

## <a name="how-to-see-all-applications-in-your-tenant"></a>Como ver todos os aplicativos em seu locatário

Para ver todos os aplicativos em seu locatário, você precisa usar o controle de **Filtro** para exibir **Todos os Aplicativos** na lista **Todos os Aplicativos**. Siga estas etapas:

1.  Abra o [**Portal do Azure**](https://portal.azure.com/) e entre como um **Administrador Global** ou **Coadministrador.**

2.  Abra a **Extensão do Azure Active Directory** clicando em **Todos os serviços** na parte superior do menu de navegação esquerdo principal.

3.  Digite **“Azure Active Directory**” na caixa de pesquisa do filtro e selecione o item **Azure Active Directory**.

4.  clique em **Aplicativos Empresariais** no menu de navegação esquerdo do Azure Active Directory.

5.  clique em **Todos os Aplicativos** para exibir uma lista com todos os seus aplicativos.

6.  Clique para usar o controle de **Filtro** na parte superior do **Lista de Todos os Aplicativos**.

7.  No painel **Filtro**, defina a opção **Exibir** como **Todos os Aplicativos.**

## <a name="why-does-a-specific-application-appear-in-my-all-applications-list"></a>Por que um aplicativo específico aparece em minha lista de todos os aplicativos?

Quando filtrada para **Todos os Aplicativos**, a **Lista** **Todos os Aplicativos** mostra todos os objetos de Entidade de Serviço em seu locatário. Objetos de Entidade de Serviço podem aparecer nessa lista de uma várias maneiras:

1.  Quando você adiciona qualquer aplicativo da galeria de aplicativos, incluindo:

   1. **Aplicativos da Galeria do Azure AD** – um aplicativo que foi integrado previamente para logon único com o Azure Active Directory

   2. **Aplicativos do Proxy de Aplicativo** – um aplicativo em execução em seu ambiente local para o qual você deseja fornecer logon único seguro externamente

   3. **Aplicativos desenvolvidos de forma personalizada** – um aplicativo que sua organização deseja desenvolver na Plataforma de Desenvolvimento de Aplicativo do Microsoft Azure Active Directory, mas que talvez ainda não exista

   4. **Aplicativos inexistentes na Galeria** – traga seus aplicativos! Qualquer link da Web desejado, ou qualquer aplicativo que renderiza um campo de nome de usuário e senha, dá suporte aos protocolos SAML ou OpenID Connect ou dá suporte ao SCIM que você deseja integrar para logon único com o Azure Active Directory.

2.  Ao se inscrever ou entrar em um aplicativo de <sup>terceiros</sup> integrado ao Azure Active Directory. Um exemplo é o [Smartsheet](https://app.smartsheet.com/b/home) ou o [DocuSign](https://www.docusign.net/member/MemberLogin.aspx).

3.  Ao inscrever-se ou adicionar uma licença a um usuário ou grupo a um aplicativo interno, como [Microsoft Office 365](https://products.office.com/)

4.  Quando você adiciona um novo registro de aplicativo criando um aplicativo personalizado usando o [Registro de Aplicativo](https://docs.microsoft.com/azure/active-directory/active-directory-app-registration)

5.  Quando você adiciona um novo registro de aplicativo criando um aplicativo personalizado usando o [Portal de Registro de Aplicativos V2.0](https://docs.microsoft.com/azure/active-directory/develop/active-directory-v2-app-registration#visit-the-microsoft-app-registration-portal)

6.  Quando você adiciona um aplicativo que está desenvolvendo usando os [Métodos de autenticação do ASP.net](https://www.asp.net/visual-studio/overview/2013/creating-web-projects-in-visual-studio#orgauthoptions) ou os [Serviços Conectados](https://blogs.msdn.com/b/visualstudio/archive/2014/11/19/connecting-to-cloud-services.aspx) do Visual Studio

7.  Quando você cria um objeto de entidade de serviço usando o [Módulo do PowerShell do Azure Active Directory](/powershell/azure/install-adv2?view=azureadps-2.0)

8.  Quando você [dá consentimento a um aplicativo](https://docs.microsoft.com/azure/active-directory/develop/active-directory-devhowto-multi-tenant-overview#understanding-user-and-admin-consent) como administrador para usar dados em seu locatário

9.  Quando um [usuário dá consentimento para um aplicativo](https://docs.microsoft.com/azure/active-directory/develop/active-directory-devhowto-multi-tenant-overview#understanding-user-and-admin-consent) usar dados no seu locatário

10. Quando você habilita determinados serviços que armazenam dados em seu locatário. Um exemplo é a Redefinição de Senha, que é modelada como uma entidade de serviço para armazenar sua senha de redefinição de senha com segurança.

Para obter mais detalhes sobre como aplicativos são adicionados ao seu diretório, leia [Como e por que os aplicativos são adicionados ao Azure AD](https://docs.microsoft.com/azure/active-directory/develop/active-directory-how-applications-are-added).

## <a name="i-want-to-remove-a-specific-users-or-groups-assignment-to-an-application"></a>Quero remover a atribuição de um usuário ou grupo específico para um aplicativo

Para remover uma atribuição de um usuário ou grupo a um aplicativo, siga as etapas listadas no artigo [Remover uma atribuição de usuário ou grupo de um aplicativo empresarial no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-coreapps-remove-assignment-azure-portal).

## <a name="i-want-to-disable-all-access-to-an-application-for-every-user"></a>Quero desabilitar todo o acesso a um aplicativo para todos os usuários

Para desabilitar todos os logons de usuário em um aplicativo, siga as etapas listadas no artigo [Desabilitar logons de usuário para um aplicativo empresarial no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-coreapps-disable-app-azure-portal).

## <a name="i-want-to-delete-an-application-entirely"></a>Quero excluir um aplicativo completamente

Para **excluir um aplicativo**, siga estas etapas:

1.  Abra o [**Portal do Azure**](https://portal.azure.com/) e entre como um **Administrador Global** ou **Coadministrador.**

2.  Abra a **Extensão do Azure Active Directory** clicando em **Todos os serviços** na parte superior do menu de navegação esquerdo principal.

3.  Digite **“Azure Active Directory**” na caixa de pesquisa do filtro e selecione o item **Azure Active Directory**.

4.  clique em **Aplicativos Empresariais** no menu de navegação esquerdo do Azure Active Directory.

5.  clique em **Todos os Aplicativos** para exibir uma lista com todos os seus aplicativos.

  * Se você não vir o aplicativo desejado, use o controle **Filtro** na parte superior da **Lista com Todos os Aplicativos** e defina a opção **Mostrar** como **Todos os Aplicativos.**

6.  Selecione o aplicativo que deseja excluir.

7.  Após o carregamento do aplicativo, clique no ícone **Excluir** do painel **Visão Geral** do aplicativo.

## <a name="i-want-to-disable-all-future-user-consent-operations-to-any-application"></a>Quero desabilitar todas as futuras operações de consentimento do usuário para qualquer aplicativo

Desabilitar o consentimento do usuário para todo o seu diretório impede que os usuários finais consintam com qualquer aplicativo. Os administradores ainda podem consentir em nome dos usuários. Para saber mais sobre o consentimento de aplicativo e por que você pode ou não querer consentir, leia [Entendendo o consentimento do usuário e do administrador](https://docs.microsoft.com/azure/active-directory/develop/active-directory-devhowto-multi-tenant-overview#understanding-user-and-admin-consent).

Para **desabilitar todas as futuras operações de consentimento do usuário no diretório inteiro**, siga estas etapas:

1.  Abra o [**Portal do Azure**](https://portal.azure.com/) e entre como um **Administrador Global.**

2.  Abra a **Extensão do Azure Active Directory** clicando em **Todos os serviços** na parte superior do menu de navegação esquerdo principal.

3.  Digite **“Azure Active Directory**” na caixa de pesquisa do filtro e selecione o item **Azure Active Directory**.

4.  Clique em **Usuários e grupos** no menu de navegação.

5.  Clique em **Configurações de usuário**.

6.  Desabilite todas as futuras operações de consentimento do usuário definindo o controle de alternância **Os usuários podem permitir que os aplicativos acessem seus dados** como **Não** e clique no botão **Salvar**.

## <a name="next-steps"></a>Próximas etapas
[Gerenciando aplicativos com o Azure Active Directory](what-is-application-management.md)
