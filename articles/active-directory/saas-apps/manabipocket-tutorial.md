---
title: 'Tutorial: integração do Microsoft Azure Active Directory com o Manabi Pocket | Microsoft Docs'
description: Saiba como configurar o logon único entre o Microsoft Active Directory do Azure e o  Manabi Pocket.
services: active-directory
documentationCenter: na
author: jeevansd
manager: femila
ms.reviewer: joflore
ms.assetid: 8e521099-bf7d-43ab-a0e0-86aa1c9e577e
ms.service: active-directory
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 06/20/2018
ms.author: jeedes
ms.openlocfilehash: 0116cac7d0e44efee0112d57aedd4f5ee02833b3
ms.sourcegitcommit: 1d850f6cae47261eacdb7604a9f17edc6626ae4b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39430708"
---
# <a name="tutorial-azure-active-directory-integration-with-manabi-pocket"></a>Tutorial: integração do Microsoft Azure Active Directory com o Manabi Pocket.

Neste tutorial, você aprenderá a integrar o  Manabi Pocket ao Azure Active Directory (Azure AD).

A integração do Core Directory ao Microsoft Azure Active Directory oferece os seguintes benefícios:

- No Microsoft Azure Directory, você poderá controlar quem tem acesso ao Manabi Pocket.
- Você pode permitir que seus usuários façam logon automaticamente no Manabi Pocket (logon único) com suas contas do Microsoft Azure Active Directory.
- Você pode gerenciar suas contas em um único local central – o portal do Azure.

Para conhecer mais detalhadamente a integração de aplicativos de SaaS ao Azure AD, consulte [o que é o acesso a aplicativos e logon único com o Azure Active Directory](../manage-apps/what-is-single-sign-on.md).

## <a name="prerequisites"></a>Pré-requisitos

Para configurar a integração do Microsoft Azure Active Directory com o Pocket, você precisa dos seguintes itens:

- Uma assinatura do AD do Azure
- Uma assinatura habilitada para logon único no Manabi Pocket

> [!NOTE]
> Para testar as etapas deste tutorial, nós não recomendamos o uso de um ambiente de produção.

Para testar as etapas deste tutorial, você deve seguir estas recomendações:

- Não use o ambiente de produção, a menos que seja necessário.
- Se não tiver um ambiente de avaliação do Azure AD, você pode [obter uma versão de avaliação de um mês](https://azure.microsoft.com/pricing/free-trial/).

## <a name="scenario-description"></a>Descrição do cenário
Neste tutorial, você testará o logon único do Azure AD em um ambiente de teste. O cenário descrito neste tutorial consiste em dois blocos de construção principais:

1. Adicionando o Manabi Pocket da Galeria
1. configurar e testar o logon único do AD do Azure

## <a name="adding-manabi-pocket-from-the-gallery"></a>Adicionando o Manabi Pocket da Galeria
Para configurar a integração do Manabi Pocket ao Microsoft Azure AD, você precisa adicionar o Manabi Pocket por meio da galeria à sua lista de aplicativos SaaS gerenciados.

**Para adicionar o Manabi Pocket por meio da galeria, execute as seguintes etapas:**

1. No **[Portal do Azure](https://portal.azure.com)**, no painel navegação à esquerda, clique no ícone **Azure Active Directory**. 

    ![O botão Azure Active Directory][1]

1. Navegue até **aplicativos empresariais**. Em seguida, vá para **todos os aplicativos**.

    ![A folha Aplicativos empresariais][2]
    
1. Clique no botão **Novo aplicativo** na parte superior da caixa de diálogo para adicionar o novo aplicativo.

    ![O botão Novo aplicativo][3]

1. Na caixa de pesquisa, digite **Manabi Pocket**, selecione **Manabi Pocket** no painel de resultados e, em seguida, clique no botão **Adicionar** para adicionar o aplicativo.

    ![Manabi Pocket na lista de resultados](./media/manabipocket-tutorial/tutorial_manabipocket_addfromgallery.png)

## <a name="configure-and-test-azure-ad-single-sign-on"></a>Configurar e testar logon único do Azure AD

Nesta seção, você configurará e testará o logon único do Microsoft Azure AD com o Manabi Pocket, com base em um usuário de teste chamado “Brenda Fernandes”.

Para que o logon único funcione, o Azure AD precisa saber qual usuário do Manabi Pocket é equivalente a um usuário do Microsoft Azure AD. Em outras palavras, é necessário estabelecer uma relação de vínculo entre um usuário do Microsoft Azure AD e o usuário relacionado no Manabi Pocket.

Para configurar e testar o logon único do AD do Azure com o Manabi Pocket, você precisa concluir os seguintes blocos de construção:

1. **[Configurar o logon único do Azure AD](#configure-azure-ad-single-sign-on)** – para habilitar seus usuários a usar esse recurso.
1. **[Criar um usuário de teste do Azure AD](#create-an-azure-ad-test-user)** – para testar o logon único do Azure AD com Brenda Fernandes.
1. **[Criar de um usuário de teste do Manabi Pocket](#create-a-manabi-pocket-test-user)** - para ter um equivalente de Brenda Fernandes no Manabi Pocket que esteja vinculado à representação de usuário no Microsoft Azure AD.
1. **[Atribuir o usuário de teste do Azure AD](#assign-the-azure-ad-test-user)** – para permitir que Brenda Fernandes use o logon único do Azure AD.
1. **[Teste o logon único](#test-single-sign-on)** – para verificar se a configuração funciona.

### <a name="configure-azure-ad-single-sign-on"></a>Configurar o logon único do Azure AD

Nesta seção, você habilitará o logon único do Microsoft Azure AD no Portal do Azure e configurará o logon único no aplicativo Manabi Pocket.

**Para configurar o logon único do Microsoft Azure Active Directory com o Manabi Pocket, execute as seguintes etapas:**

1. No Portal do Azure, na página de integração de aplicativos do **Manabi Pocket**, clique em **Logon único**.

    ![Link Configurar logon único][4]

1. Na caixa de diálogo **Logon único**, selecione **Modo** como **Logon baseado em SAML** para habilitar o logon único.

    ![Caixa de diálogo Logon único](./media/manabipocket-tutorial/tutorial_manabipocket_samlbase.png)

1. Na seção **Domínio e URLs do Manabi Pocket**, execute as seguintes etapas:

    ![Informações de logon único de Domínio e URLs do Manabi Pocket](./media/manabipocket-tutorial/tutorial_manabipocket_url.png)

    a. Na caixa de texto **URL de Logon**, digite a URL: `https://ed-cl.com/`

    b. Na caixa de texto **Identificador**, digite uma URL usando o seguinte padrão: `https://<SERVER-NAME>.ed-cl.com/<TENANT-ID>/idp/provider`

    > [!NOTE]
    > O valor do Identificador não é real. Atualize esse valor com o Identificador real. Contate a [equipe de suporte ao Cliente do Manabi Pocket](mailto:info-ed-cl@ntt.com) para obter esse valor.

1. Na seção **Certificado de Autenticação SAML**, clique em **Metadados XML** e, em seguida, salve o arquivo de metadados em seu computador.

    ![O link de download do Certificado](./media/manabipocket-tutorial/tutorial_manabipocket_certificate.png) 

1. Clique no botão **Salvar** .

    ![Botão Salvar em Configurar Logon Único](./media/manabipocket-tutorial/tutorial_general_400.png)

1. Para configurar o logon único no lado do **Manabi Pocket**, é necessário enviar o **XML de Metadados** baixado para a [equipe de suporte Manabi Pocket](mailto:info-ed-cl@ntt.com). Eles definem essa configuração para ter a conexão de SSO de SAML definida corretamente em ambos os lados.

### <a name="create-an-azure-ad-test-user"></a>Criar um usuário de teste do Azure AD

O objetivo desta seção é criar um usuário de teste no Portal do Azure chamado Brenda Fernandes.

   ![Criar um usuário de teste do Azure AD][100]

**Para criar um usuário de teste no AD do Azure, execute as seguintes etapas:**

1. No portal do Azure, no painel esquerdo, clique no botão **Azure Active Directory**.

    ![O botão Azure Active Directory](./media/manabipocket-tutorial/create_aaduser_01.png)

1. Para exibir a lista de usuários, acesse **Usuários e grupos** e, depois, clique em **Todos os usuários**.

    ![Os links “Usuários e grupos” e “Todos os usuários”](./media/manabipocket-tutorial/create_aaduser_02.png)

1. Para abrir a caixa de diálogo **Usuário**, clique em **Adicionar** na parte superior da caixa de diálogo **Todos os Usuários**.

    ![O botão Adicionar](./media/manabipocket-tutorial/create_aaduser_03.png)

1. Na caixa de diálogo **Usuário**, execute as seguintes etapas:

    ![A caixa de diálogo Usuário](./media/manabipocket-tutorial/create_aaduser_04.png)

    a. Na caixa **Nome**, digite **BrendaFernandes**.

    b. Na caixa **Nome de usuário**, digite o endereço de email do usuário Brenda Fernandes.

    c. Marque a caixa de seleção **Mostrar Senha** e, em seguida, anote o valor exibido na caixa **Senha**.

    d. Clique em **Criar**.
 
### <a name="create-a-manabi-pocket-test-user"></a>Criar um usuário de teste do Manabi Pocket

Nesta seção, você criará uma usuária chamada Brenda Fernandes no Manabi Pocket. Trabalhar com [a equipe de suporte Manabi Pocket](mailto:info-ed-cl@ntt.com) para adicionar os usuários na plataforma do Manabi Pocket. Os usuários devem ser criados e ativados antes de usar o logon único.

### <a name="assign-the-azure-ad-test-user"></a>Atribuir o usuário de teste do Azure AD

Nesta seção, você permite que Brenda Fernandes use o logon único do Microsoft Azure concedendo acesso ao Manabi Pocket.

![Atribuir a função de usuário][200] 

**Para atribuir Brenda Fernandes ao Manabi Pocket, execute as seguintes etapas:**

1. No Portal do Azure, abra a exibição de aplicativos e, em seguida, navegue até a exibição de diretório e vá para **Aplicativos Empresariais** e clique em **Todos os aplicativos**.

    ![Atribuir usuário][201] 

1. Na lista de aplicativos, escolha **Manabi Pocket**.

    ![Link do Manabi Pocket na lista de Aplicativos](./media/manabipocket-tutorial/tutorial_manabipocket_app.png)  

1. No menu à esquerda, clique em **usuários e grupos**.

    ![O link “Usuários e grupos”][202]

1. Clique no botão **Adicionar**. Em seguida, selecione **usuários e grupos** na **Adicionar atribuição** caixa de diálogo.

    ![O painel Adicionar Atribuição][203]

1. Em **usuários e grupos** caixa de diálogo, selecione **Britta Simon** na lista de usuários.

1. Clique em **selecione** botão **usuários e grupos** caixa de diálogo.

1. Clique em **atribuir** botão **Adicionar atribuição** caixa de diálogo.

### <a name="test-single-sign-on"></a>Testar logon único

Nesta seção, você testará sua configuração de logon único do Azure AD usando o Painel de Acesso.

Quando você clica no bloco Manabi Pocket no Painel de Acesso, deve fazer logon automaticamente no seu aplicativo do Manabi Pocket.
Para saber mais sobre o Painel de Acesso, veja [Introdução ao Painel de Acesso](../user-help/active-directory-saas-access-panel-introduction.md). 

## <a name="additional-resources"></a>Recursos adicionais

* [Lista de tutoriais sobre como integrar aplicativos SaaS com o Active Directory do Azure](tutorial-list.md)
* [O que é o acesso a aplicativos e logon único com o Azure Active Directory?](../manage-apps/what-is-single-sign-on.md)

<!--Image references-->

[1]: ./media/manabipocket-tutorial/tutorial_general_01.png
[2]: ./media/manabipocket-tutorial/tutorial_general_02.png
[3]: ./media/manabipocket-tutorial/tutorial_general_03.png
[4]: ./media/manabipocket-tutorial/tutorial_general_04.png

[100]: ./media/manabipocket-tutorial/tutorial_general_100.png

[200]: ./media/manabipocket-tutorial/tutorial_general_200.png
[201]: ./media/manabipocket-tutorial/tutorial_general_201.png
[202]: ./media/manabipocket-tutorial/tutorial_general_202.png
[203]: ./media/manabipocket-tutorial/tutorial_general_203.png