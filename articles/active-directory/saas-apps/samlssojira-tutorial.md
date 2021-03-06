---
title: 'Tutorial: Integração do Azure Active Directory com o SSO do SAML para Jira da Resolution GmbH | Microsoft Docs'
description: Saiba como configurar o logon único entre o Azure Active Directory e SSO do SAML para Jira da Resolution GmbH.
services: active-directory
documentationCenter: na
author: jeevansd
manager: mtillman
ms.reviewer: barbkess
ms.assetid: 20e18819-e330-4e40-bd8d-2ff3b98e035f
ms.service: Azure-Active-Directory
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: tutorial
ms.date: 01/03/2018
ms.author: jeedes
ms.openlocfilehash: 3e527965782cc951553a5b5721955d4d3cfe67c6
ms.sourcegitcommit: 3ab534773c4decd755c1e433b89a15f7634e088a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2019
ms.locfileid: "54065470"
---
# <a name="tutorial-azure-active-directory-integration-with-saml-sso-for-jira-by-resolution-gmbh"></a>Tutorial: Integração do Azure Active Directory com o SSO do SAML para Jira da Resolution GmbH

Neste tutorial, você aprenderá a integrar o SSO do SAML para Jira da Resolution GmbH com o Azure AD (Azure Active Directory).
A integração de SSO do SAML para Jira da Resolution GmbH com o Azure AD oferece os seguintes benefícios:

* Você pode controlar no Azure AD quem tem acesso ao SSO do SAML para Jira da Resolution GmbH.
* Você pode permitir que os usuários sejam conectados automaticamente ao SSO do SAML para Jira da Resolution GmbH (Logon Único) usando suas contas do Azure AD.
* Você pode gerenciar suas contas em um único local central – o portal do Azure.

Para conhecer mais detalhadamente a integração de aplicativos de SaaS ao AD do Azure, consulte [O que é o acesso a aplicativos e logon único com o Active Directory do Azure](https://docs.microsoft.com/azure/active-directory/active-directory-appssoaccess-whatis).
Se você não tiver uma assinatura do Azure, [crie uma conta gratuita](https://azure.microsoft.com/free/) antes de começar.

## <a name="prerequisites"></a>Pré-requisitos

Para configurar a integração do Azure AD com o SSO de SAML para Jira da Resolution GmbH, você precisa dos seguintes itens:

* Uma assinatura do Azure AD. Se não tiver um ambiente do Azure AD, você pode obter uma versão de avaliação de um mês [aqui](https://azure.microsoft.com/pricing/free-trial/)
* Uma assinatura do SSO do SAML para Jira da Resolution GmbH habilitada para logon único

## <a name="scenario-description"></a>Descrição do cenário

Neste tutorial, você configurará e testará o logon único do Azure AD em um ambiente de teste.

* O SSO do SAML para Jira da Resolution GmbH é compatível com o SSO iniciado por **SP** e **IDP**

## <a name="adding-saml-sso-for-jira-by-resolution-gmbh-from-the-gallery"></a>Adicionar o SSO do SAML para Jira da Resolution GmbH da galeria

Para configurar a integração do SSO do SAML para Jira da Resolution GmbH no Azure AD, adicione o SSO do SAML para Jira da Resolution GmbH da galeria à sua lista de aplicativos SaaS gerenciados.

**Para adicionar SSO do SAML para Jira da Resolution GmbH da galeria, execute as seguintes etapas:**

1. No **[Portal do Azure](https://portal.azure.com)**, no painel navegação à esquerda, clique no ícone **Azure Active Directory**.

    ![O botão Azure Active Directory](common/select-azuread.png)

2. Navegue até **Aplicativos Empresariais** e, em seguida, selecione a opção **Todos os Aplicativos**.

    ![A folha Aplicativos empresariais](common/enterprise-applications.png)

3. Clique no botão **Novo aplicativo** na parte superior da caixa de diálogo para adicionar o novo aplicativo.

    ![O botão Novo aplicativo](common/add-new-app.png)

4. Na caixa de pesquisa, digite **SSO do SAML para Jira da Resolution GmbH**, selecione **SSO do SAML para Jira da Resolution GmbH** no painel de resultados e clique no botão **Adicionar** para adicionar o aplicativo.

     ![SSO do SAML para Jira da Resolution GmbH na lista de resultados](common/search-new-app.png)

## <a name="configure-and-test-azure-ad-single-sign-on"></a>Configurar e testar logon único do Azure AD

Nesta seção, você configura e testa o logon único do Azure AD com o SSO de SAML para Jira da Resolution GmbH com base em um usuário de teste chamado **Brenda Fernandes**.
Para que o logon único funcione, é necessário estabelecer uma relação de vínculo entre um usuário do Azure AD e o usuário relacionado do SSO do SAML para Jira da Resolution GmbH.

Para configurar e testar o logon único do Azure AD com o SSO de SAML para Jira da Resolution GmbH, conclua os seguintes blocos de construção:

1. **[Configurar o logon único do Azure AD](#configure-azure-ad-single-sign-on)** – para habilitar seus usuários a usar esse recurso.
2. **[Configurar o Logon Único do SSO do SAML para Jira da Resolution GmbH](#configure-saml-sso-for-jira-by-resolution-gmbh-single-sign-on)** – para definir as configurações de Logon Único no lado do aplicativo.
3. **[Criar um usuário de teste do Azure AD](#create-an-azure-ad-test-user)** – para testar o logon único do Azure AD com Brenda Fernandes.
4. **[Atribuir o usuário de teste do Azure AD](#assign-the-azure-ad-test-user)** – para permitir que Brenda Fernandes use o logon único do Azure AD.
5. **[Criar um usuário de teste de SSO do SAML para Jira da Resolution GmbH](#create-saml-sso-for-jira-by-resolution-gmbh-test-user)**  – para ter um equivalente de Brenda Fernandes no SSO do SAML para Jira da Resolution GmbH vinculado à representação do usuário do Azure AD.
6. **[Teste o logon único](#test-single-sign-on)** – para verificar se a configuração funciona.

### <a name="configure-azure-ad-single-sign-on"></a>Configurar o logon único do Azure AD

Nesta seção, você habilitará o logon único do Azure AD no portal do Azure.

Para configurar o logon único do Azure AD com o SSO de SAML para Jira da Resolution GmbH, execute as seguintes etapas:

1. No [portal do Azure](https://portal.azure.com/), na página de integração de aplicativo **SSO do SAML para Jira da Resolution GmbH**, selecione **Logon único**.

    ![Link Configurar logon único](common/select-sso.png)

2. Na caixa de diálogo **Selecionar um método de logon único**, selecione o modo **SAML/WS-Fed** para habilitar o logon único.

    ![Modo de seleção de logon único](common/select-saml-option.png)

3. Na página **Definir logon único com SAML**, clique no ícone **Editar** para abrir a caixa de diálogo **Configuração básica do SAML**.

    ![Editar a Configuração Básica de SAML](common/edit-urls.png)

4. Na seção **Configuração Básica do SAML**, execute as etapas a seguir caso deseje configurar o aplicativo no modo iniciado por **IDP**:

    ![Informações de Domínio e URLs do logon único do SAML SSO para Jira da Resolution GmbH](common/idp-intiated.png)

     a. No **identificador** caixa de texto, digite uma URL usando o seguinte padrão: `https://<server-base-url>/plugins/servlet/samlsso`

    b. No **URL de resposta** caixa de texto, digite uma URL usando o seguinte padrão: `https://<server-base-url>/plugins/servlet/samlsso`

    c. Clique em **Definir URLs adicionais** e execute a seguinte etapa se desejar configurar o aplicativo no modo iniciado por **SP**:

    ![Informações de Domínio e URLs do logon único do SAML SSO para Jira da Resolution GmbH](common/metadata-upload-additional-signon.png)

    Na caixa de texto **URL de login**, digite um URL usando o seguinte padrão: `https://<server-base-url>/plugins/servlet/samlsso`

    > [!NOTE]
    > Esses valores não são reais. Atualize esses valores com o Identificador, a URL de Resposta e a URL de Logon reais. Entre em contato com a [equipe de suporte ao Cliente do SSO do SAML para Jira da Resolution GmbH](https://www.resolution.de/go/support) para obter esses valores. Você também pode consultar os padrões exibidos na seção **Configuração Básica de SAML** no portal do Azure.

4. Na página **Configurar Logon Único com SAML**, na seção **Certificado de Autenticação SAML**, clique em **Baixar** para baixar o **XML de Metadados de Federação** usando as opções fornecidas de acordo com seus requisitos e salve-o no computador.

    ![O link de download do Certificado](common/metadataxml.png)

6. Na seção **Configurar o SSO do SAML para Jira da Resolution GmbH**, copie as URLs apropriadas de acordo com suas necessidades.

    ![Copiar URLs de configuração](common/copy-configuration-urls.png)

     a. URL de logon

    b. Identificador do Azure Ad

    c. URL de logoff

### <a name="configure-saml-sso-for-jira-by-resolution-gmbh-single-sign-on"></a>Configurar o Logon Único do SSO do SAML para Jira da Resolution GmbH

1. Em uma janela diferente do navegador da Web, faça logon no **portal do administrador do SSO do SAML para Jira da Resolution GmbH** como administrador.

2. Passe o cursor do mouse sobre a engrenagem e clique em **Complementos**.
    
    ![Configurar o logon único](./media/samlssojira-tutorial/addon1.png)

3. Você é redirecionado à página de Acesso de Administrador. Insira a **Senha** e clique no botão **Confirmar**.

    ![Configurar o logon único](./media/samlssojira-tutorial/addon2.png)

4. Na seção da guia Complementos, clique em **Localizar novos complementos**. Pesquise **SSO (Logon Único) do SAML para JIRA** e clique no botão **Instalar** para instalar o novo plug-in do SAML.

    ![Configurar o logon único](./media/samlssojira-tutorial/addon7.png)

5. A instalação do plug-in será iniciada. Clique em **fechar**

    ![Configurar o logon único](./media/samlssojira-tutorial/addon8.png)

    ![Configurar o logon único](./media/samlssojira-tutorial/addon9.png)

6.  Clique em **Gerenciar**.

    ![Configurar o logon único](./media/samlssojira-tutorial/addon10.png)
    
8. Clique em **Configurar** para configurar o novo plug-in.

    ![Configurar o logon único](./media/samlssojira-tutorial/addon11.png)

9. Em **Configuração de Plug-in de Logon Único do SAML**, clique no botão **Adicionar novo IdP** para definir as configurações do Provedor de Identidade.

    ![Configurar o logon único](./media/samlssojira-tutorial/addon4.png)

10. Na página **Escolher seu Provedor de Identidade SAML**, execute as seguintes etapas:

    ![Configurar o logon único](./media/samlssojira-tutorial/addon5a.png)
 
     a. Definir o **Azure Active Directory** como o tipo de IdP.
    
    b. Adicionar **Nome** do Provedor de Identidade (por exemplo, Azure AD).
    
    c. Adicionar **Descrição** do Provedor de Identidade (por exemplo, Azure AD).
    
    d. Clique em **Próximo**.
    
11. Na página **Configuração do provedor de identidade**, clique no botão **Avançar**.

    ![Configurar o logon único](./media/samlssojira-tutorial/addon5b.png)

12. Na página **Importar metadados de IdP do SAML**, execute as seguintes etapas:

    ![Configurar o logon único](./media/samlssojira-tutorial/addon5c.png)

     a. Clique no botão **Carregar arquivo** e selecione o arquivo XML de metadados que você baixou na etapa 5.

    b. Clique no botão **Importar**.
    
    c. Espere um pouco até que a importação seja bem-sucedida.
    
    d. Clique no botão **Avançar**.
    
13. Na página de **Transformação e atributo de ID de usuário**, clique no botão **Avançar**.

    ![Configurar o logon único](./media/samlssojira-tutorial/addon5d.png)
    
14. Na página **Criação e atualização de usuário**, clique em **Salvar e avançar** para salvar as configurações.   
    
    ![Configurar o logon único](./media/samlssojira-tutorial/addon6a.png)
    
15. Na página **Testar suas configurações**, clique em **Ignorar teste e configurar manualmente** para ignorar momentaneamente o teste do usuário. Isso será executado na próxima seção e requer algumas configurações no portal do Azure. 
    
    ![Configurar o logon único](./media/samlssojira-tutorial/addon6b.png)
    
16. No diálogo que mostra **Ignorar o teste significa...**, clique em **OK**.
    
    ![Configurar o logon único](./media/samlssojira-tutorial/addon6c.png)

### <a name="create-an-azure-ad-test-user"></a>Criar um usuário de teste do Azure AD 

O objetivo desta seção é criar um usuário de teste no Portal do Azure chamado Brenda Fernandes.

1. No Portal do Azure, no painel esquerdo, selecione **Azure Active Directory**, selecione **Usuários** e, em seguida, **Todos os usuários**.

    ![Os links “Usuários e grupos” e “Todos os usuários”](common/users.png)

2. Selecione **Novo usuário** na parte superior da tela.

    ![Botão Novo usuário](common/new-user.png)

3. Nas Propriedades do usuário, execute as etapas a seguir.

    ![A caixa de diálogo Usuário](common/user-properties.png)

     a. No campo **Nome**, insira **BrendaFernandes**.
  
    b. No campo **Nome de usuário**, digite **brittasimon@yourcompanydomain.extension**  
    Por exemplo, BrittaSimon@contoso.com

    c. Marque a caixa de seleção **Mostrar senha** e, em seguida, anote o valor exibido na caixa Senha.

    d. Clique em **Criar**.

### <a name="assign-the-azure-ad-test-user"></a>Atribuir o usuário de teste do Azure AD

Nesta seção, habilite Brenda Fernandes a usar o logon único do Azure concedendo acesso ao SSO do SAML para Jira da Resolution GmbH.

1. No portal do Azure, selecione **Aplicativos Empresariais**, **Todos os aplicativos** e, em seguida, **SSO do SAML para Jira da Resolution GmbH**.

    ![Folha de aplicativos empresariais](common/enterprise-applications.png)

2. Na lista de aplicativos, digite e selecione **SSO do SAML para Jira da Resolution GmbH**.

    ![SSO do SAML para Jira da Resolution GmbH na lista de Aplicativos](common/all-applications.png)

3. No menu à esquerda, selecione **Usuários e grupos**.

    ![O link “Usuários e grupos”](common/users-groups-blade.png)

4. Escolha o botão **Adicionar usuário** e, em seguida, escolha **Usuários e grupos** na caixa de diálogo **Adicionar Atribuição**.

    ![O painel Adicionar Atribuição](common/add-assign-user.png)

5. Na caixa de diálogo **Usuários e grupos**, escolha **Brenda Fernandes** na lista Usuários e clique no botão **Selecionar** na parte inferior da tela.

6. Se você estiver esperando um valor de função na declaração SAML, na caixa de diálogo **Selecionar função**, escolha a função de usuário apropriada na lista e clique no botão **Selecionar** na parte inferior da tela.

7. Na caixa de diálogo **Adicionar atribuição**, clique no botão **Atribuir**.

### <a name="create-saml-sso-for-jira-by-resolution-gmbh-test-user"></a>Criar um usuário de teste do SSO do SAML para Jira da Resolution GmbH

Para habilitar usuários do Azure AD a fazerem logon no SSO do SAML para Jira da Resolution GmbH, eles devem ser provisionados no SSO do SAML para Jira da Resolution GmbH.  
No SSO do SAML para Jira da Resolution GmbH, o provisionamento é uma tarefa manual.

**Para provisionar uma conta de usuário, execute as seguintes etapas:**

1. Faça logon no site da empresa do SAML SSO para Jira da Resolution GmbH como administrador.

2. Passe o cursor do mouse sobre a engrenagem e clique em **Gerenciamento de usuário**.

    ![Adicionar Funcionário](./media/samlssojira-tutorial/user1.png) 

3. Você será redirecionado à página de acesso de administrador para inserir a **Senha** e clicar no botão **Confirmar**.

    ![Adicionar Funcionário](./media/samlssojira-tutorial/user2.png) 

4. Na seção da guia **Gerenciamento de usuário**, clique em **criar usuário**.

    ![Adicionar Funcionário](./media/samlssojira-tutorial/user3.png) 

5. Na página da caixa de diálogo **"Criar novo usuário"**, execute as seguintes etapas:

    ![Adicionar Funcionário](./media/samlssojira-tutorial/user4.png) 

     a. Na caixa de texto **Endereço de email**, digite o endereço de email do usuário, como Brittasimon@contoso.com.

    b. Na caixa de texto **Nome completo**, digite o nome completo do usuário, como Brenda Fernandes.

    c. Na caixa de texto **Nome de usuário**, digite o email do usuário, como Brittasimon@contoso.com.

    d. Na caixa de texto **Senha**, digite a senha do usuário.

    e. Clique em **Criar usuário**.

### <a name="test-single-sign-on"></a>Testar logon único 

Nesta seção, você testará sua configuração de logon único do Azure AD usando o Painel de Acesso.

Ao clicar no bloco do SSO do SAML para Jira da Resolution GmbH no Painel de Acesso, você deverá ser conectado automaticamente ao SSO do SAML para Jira da Resolution GmbH para o qual você configurou o SSO. Para saber mais sobre o Painel de Acesso, veja [Introdução ao Painel de Acesso](https://docs.microsoft.com/azure/active-directory/active-directory-saas-access-panel-introduction).

## <a name="additional-resources"></a>Recursos adicionais

- [ Lista de tutoriais sobre como integrar aplicativos SaaS com o Active Directory do Azure ](https://docs.microsoft.com/azure/active-directory/active-directory-saas-tutorial-list)

- [O que é o acesso a aplicativos e logon único com o Azure Active Directory? ](https://docs.microsoft.com/azure/active-directory/active-directory-appssoaccess-whatis)

- [O que é o acesso condicional no Azure Active Directory?](https://docs.microsoft.com/azure/active-directory/conditional-access/overview)

