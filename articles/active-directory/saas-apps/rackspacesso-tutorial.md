---
title: 'Tutorial: integração do Azure Active Directory ao Rackspace SSO | Microsoft Docs'
description: Saiba como configurar o logon único entre o Azure Active Directory e o Rackspace SSO.
services: active-directory
documentationCenter: na
author: jeevansd
manager: femila
ms.reviewer: joflore
ms.assetid: 36b398be-2f7e-4ce8-9031-53587299bc4a
ms.service: active-directory
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 09/20/2018
ms.author: jeedes
ms.openlocfilehash: b825fb1d7f56aae923f6760c4fd6384e03274b7a
ms.sourcegitcommit: 4ecc62198f299fc215c49e38bca81f7eb62cdef3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2018
ms.locfileid: "47042050"
---
# <a name="tutorial-azure-active-directory-integration-with-rackspace-sso"></a>Tutorial: integração do Azure Active Directory ao Rackspace SSO

Neste tutorial, você aprenderá a integrar o Rackspace SSO com o Microsoft Azure AD (Azure Active Directory).

A integração do Rackspace SSO ao Microsoft Azure AD oferece os seguintes benefícios:

- É possível controlar no Microsoft Azure AD quem tem acesso ao Rackspace SSO.
- É possível habilitar que os usuários façam logon automaticamente no Rackspace SSO (logon único) com suas contas do Microsoft Azure AD.
- Você pode gerenciar suas contas em um único local central – o portal do Azure.

Para conhecer mais detalhadamente a integração de aplicativos de SaaS ao Azure AD, consulte [o que é o acesso a aplicativos e logon único com o Azure Active Directory](../manage-apps/what-is-single-sign-on.md).

## <a name="prerequisites"></a>Pré-requisitos

Para configurar a integração do Microsoft Azure AD ao Rackspace SSO, são necessários os seguintes itens:

- Uma assinatura do AD do Azure
- Uma assinatura do Rackspace SSO habilitada para logon único

> [!NOTE]
> Para testar as etapas deste tutorial, nós não recomendamos o uso de um ambiente de produção.

Para testar as etapas deste tutorial, você deve seguir estas recomendações:

- Não use o ambiente de produção, a menos que seja necessário.
- Se não tiver um ambiente de avaliação do Azure AD, você pode [obter uma versão de avaliação de um mês](https://azure.microsoft.com/pricing/free-trial/).

## <a name="scenario-description"></a>Descrição do cenário

Neste tutorial, você testará o logon único do Azure AD em um ambiente de teste. O cenário descrito neste tutorial consiste em dois blocos de construção principais:

1. Adicionando o Rackspace SSO da galeria
2. configurar e testar o logon único do AD do Azure

## <a name="adding-rackspace-sso-from-the-gallery"></a>Adicionando o Rackspace SSO da galeria

Para configurar a integração do Rackspace SSO ao Microsoft Azure AD, é necessário adicionar o Rackspace SSO da galeria à sua lista de aplicativos SaaS gerenciados.

**Para adicionar o Rackspace SSO da galeria, execute as etapas abaixo:**

1. No **[Portal do Azure](https://portal.azure.com)**, no painel navegação à esquerda, clique no ícone **Azure Active Directory**. 

    ![O botão Azure Active Directory][1]

2. Navegue até **aplicativos empresariais**. Em seguida, vá para **todos os aplicativos**.

    ![A folha Aplicativos empresariais][2]

3. Clique no botão **Novo aplicativo** na parte superior da caixa de diálogo para adicionar o novo aplicativo.

    ![O botão Novo aplicativo][3]

4. Na caixa de pesquisa, digite **Rackspace SSO**, selecione **Rackspace SSO** no painel de resultados e, em seguida, clique no botão **Adicionar** para adicionar o aplicativo.

    ![Rackspace SSO na lista de resultados](./media/rackspacesso-tutorial/tutorial_rackspacesso_addfromgallery.png)

## <a name="configure-and-test-azure-ad-single-sign-on"></a>Configurar e testar logon único do Azure AD

Nesta seção, você configurará e testará o logon único do Microsoft Azure AD com o Rackspace SSO, com base em um usuário de teste chamado “Brenda Fernandes”.

Para que o logon único funcione, o Microsoft Azure AD precisa saber qual usuário do Rackspace SSO é equivalente a um usuário do Microsoft Azure AD. Em outras palavras, é necessário estabelecer uma relação de vínculo entre um usuário do Microsoft Azure AD e o usuário relacionado do Rackspace SSO.

Para configurar e testar o logon único do Microsoft Azure AD com o Rackspace SSO, é necessário concluir os seguintes blocos de construção:

1. **[Configurar o logon único do Azure AD](#configure-azure-ad-single-sign-on)** – para habilitar seus usuários a usar esse recurso.
2. **[Criar um usuário de teste do Azure AD](#create-an-azure-ad-test-user)** – para testar o logon único do Azure AD com Brenda Fernandes.
3. **[Criar um usuário de teste do Rackspace SSO](#create-a-rackspace-sso-test-user)** – para ter um equivalente de Brenda Fernandes no Rackspace SSO que esteja vinculado à representação de usuário no Microsoft Azure AD.
4. **[Atribuir o usuário de teste do Azure AD](#assign-the-azure-ad-test-user)** – para permitir que Brenda Fernandes use o logon único do Azure AD.
5. **[Teste o logon único](#test-single-sign-on)** – para verificar se a configuração funciona.

### <a name="configure-azure-ad-single-sign-on"></a>Configurar o logon único do Azure AD

Nesta seção, você habilitará o logon único do Microsoft Azure AD no portal do Azure e configurará o logon único em seu aplicativo Rackspace SSO.

**Para configurar o logon único do Microsoft Azure AD com o Rackspace SSO, siga as etapas abaixo:**

1. No portal do Azure, na página de integração do aplicativo **Rackspace SSO**, clique em **Logon único**.

    ![Link Configurar logon único][4]

2. Na caixa de diálogo **Logon único**, selecione **Modo** como **Logon baseado em SAML** para habilitar o logon único.

    ![Caixa de diálogo Logon único](./media/rackspacesso-tutorial/tutorial_rackspacesso_samlbase.png)

3. Na seção **URLs e Domínio do Rackspace SSO**, execute as seguintes etapas:

    ![Informações de logon único em Domínio e URLs do Rackspace SSO](./media/rackspacesso-tutorial/tutorial_rackspacesso_url.png)

    Na caixa de texto **URL de Logon**, digite uma URL: `https://login.rackspace.com/federate/`

4. Na seção **Certificado de Autenticação SAML**, clique em **Metadados XML** e, em seguida, salve o arquivo de metadados em seu computador.

    ![O link de download do Certificado](./media/rackspacesso-tutorial/tutorial_rackspacesso_certificate.png)

5. Clique no botão **Salvar** .

    ![Botão Salvar em Configurar Logon Único](./media/rackspacesso-tutorial/tutorial_general_400.png)

6. Para configurar o logon único no lado do **Rackspace SSO**, é necessário enviar o **XML de metadados** baixado para a [equipe de suporte do Rackspace SSO](https://support.rackspace.com/). Eles definem essa configuração para ter a conexão de SSO de SAML definida corretamente em ambos os lados.

### <a name="create-an-azure-ad-test-user"></a>Criar um usuário de teste do Azure AD

O objetivo desta seção é criar um usuário de teste no Portal do Azure chamado Brenda Fernandes.

   ![Criar um usuário de teste do Azure AD][100]

**Para criar um usuário de teste no AD do Azure, execute as seguintes etapas:**

1. No portal do Azure, no painel esquerdo, clique no botão **Azure Active Directory**.

    ![O botão Azure Active Directory](./media/rackspacesso-tutorial/create_aaduser_01.png)

2. Para exibir a lista de usuários, acesse **Usuários e grupos** e, depois, clique em **Todos os usuários**.

    ![Os links “Usuários e grupos” e “Todos os usuários”](./media/rackspacesso-tutorial/create_aaduser_02.png)

3. Para abrir a caixa de diálogo **Usuário**, clique em **Adicionar** na parte superior da caixa de diálogo **Todos os Usuários**.

    ![O botão Adicionar](./media/rackspacesso-tutorial/create_aaduser_03.png)

4. Na caixa de diálogo **Usuário**, execute as seguintes etapas:

    ![A caixa de diálogo Usuário](./media/rackspacesso-tutorial/create_aaduser_04.png)

    a. Na caixa **Nome**, digite **BrendaFernandes**.

    b. Na caixa **Nome de usuário**, digite o endereço de email do usuário Brenda Fernandes.

    c. Marque a caixa de seleção **Mostrar Senha** e, em seguida, anote o valor exibido na caixa **Senha**.

    d. Clique em **Criar**.

### <a name="create-a-rackspace-sso-test-user"></a>Criar um usuário de teste do Rackspace SSO

Nesta seção, você trabalhará com a [equipe de suporte do Rackspace SSO](https://support.rackspace.com/) para integrar sua conta na plataforma do Rackspace SSO.

### <a name="assign-the-azure-ad-test-user"></a>Atribuir o usuário de teste do Azure AD

Nesta seção, você permitirá que Brenda Fernandes use o logon único do Azure concedendo acesso ao Rackspace SSO.

![Atribuir a função de usuário][200]

**Para atribuir Brenda Fernandes ao Rackspace SSO, siga as etapas abaixo:**

1. No Portal do Azure, abra a exibição de aplicativos e, em seguida, navegue até a exibição de diretório e vá para **Aplicativos Empresariais** e clique em **Todos os aplicativos**.

    ![Atribuir usuário][201] 

2. Na lista de aplicativos, selecione **Rackspace SSO**.

    ![O link do Rackspace SSO na lista de Aplicativos](./media/rackspacesso-tutorial/tutorial_rackspacesso_app.png)  

3. No menu à esquerda, clique em **usuários e grupos**.

    ![O link “Usuários e grupos”][202]

4. Clique no botão **Adicionar**. Em seguida, selecione **usuários e grupos** na **Adicionar atribuição** caixa de diálogo.

    ![O painel Adicionar Atribuição][203]

5. Em **usuários e grupos** caixa de diálogo, selecione **Britta Simon** na lista de usuários.

6. Clique em **selecione** botão **usuários e grupos** caixa de diálogo.

7. Clique em **atribuir** botão **Adicionar atribuição** caixa de diálogo.

### <a name="test-single-sign-on"></a>Testar logon único

Nesta seção, você testará sua configuração de logon único do Azure AD usando o Painel de Acesso.

Ao clicar no bloco do Rackspace SSO no Painel de Acesso, seu logon deverá ser feito automaticamente no aplicativo Rackspace SSO.
Para saber mais sobre o Painel de Acesso, veja [Introdução ao Painel de Acesso](../active-directory-saas-access-panel-introduction.md). 

## <a name="additional-resources"></a>Recursos adicionais

* [Lista de tutoriais sobre como integrar aplicativos SaaS com o Active Directory do Azure](tutorial-list.md)
* [O que é o acesso a aplicativos e logon único com o Azure Active Directory?](../manage-apps/what-is-single-sign-on.md)

<!--Image references-->

[1]: ./media/rackspacesso-tutorial/tutorial_general_01.png
[2]: ./media/rackspacesso-tutorial/tutorial_general_02.png
[3]: ./media/rackspacesso-tutorial/tutorial_general_03.png
[4]: ./media/rackspacesso-tutorial/tutorial_general_04.png

[100]: ./media/rackspacesso-tutorial/tutorial_general_100.png

[200]: ./media/rackspacesso-tutorial/tutorial_general_200.png
[201]: ./media/rackspacesso-tutorial/tutorial_general_201.png
[202]: ./media/rackspacesso-tutorial/tutorial_general_202.png
[203]: ./media/rackspacesso-tutorial/tutorial_general_203.png