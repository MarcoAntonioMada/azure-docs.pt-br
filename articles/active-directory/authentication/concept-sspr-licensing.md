---
title: Licenciar a senha de autoatendimento do Microsoft Azure Active Directory
description: Requisitos de licenciamento para redefinição da senha de autoatendimento do Azure AD
services: active-directory
ms.service: active-directory
ms.component: authentication
ms.topic: conceptual
ms.date: 07/17/2018
ms.author: joflore
author: MicrosoftGuyJFlo
manager: mtillman
ms.reviewer: sahenry
ms.openlocfilehash: 6da0bddc3f6c90d0ecd3a554988f510e1063caac
ms.sourcegitcommit: 8330a262abaddaafd4acb04016b68486fba5835b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54043032"
---
# <a name="licensing-requirements-for-azure-ad-self-service-password-reset"></a>Requisitos de licenciamento para redefinição da senha de autoatendimento do Azure AD

O Azure AD (Azure Active Directory) é fornecido em quatro edições: Gratuito, Básico, Premium P1 e Premium P2. Há vários recursos diferentes que compõem a redefinição de senha de autoatendimento, incluindo alteração, redefinição, desbloqueio e write-back, que estão disponíveis nas diferentes edições do Azure AD. Este artigo tenta explicar as diferenças. Mais detalhes dos recursos incluídos em cada edição do Azure AD podem ser encontrados na [página de preços do Microsoft Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/).

## <a name="compare-editions-and-features"></a>Comparar edições e recursos

A redefinição de senha de autoatendimento do Azure AD é licenciada por usuário e, para manter a conformidade, é necessário que as organizações atribuam a licença apropriada aos seus usuários.

* Alteração de senhas por autoatendimento para usuários de nuvem
   * Eu sou um **usuário somente na nuvem** e sei minha senha.
      * Eu queria **alterar** minha senha para algo novo.
   * Essa funcionalidade está incluída em todas as edições do Azure AD.

* Redefinição de senha por autoatendimento para usuários de nuvem
   * Eu sou um **usuário somente na nuvem** e esqueci minha senha.
      * Eu queria **alterar** minha senha para algo que eu saiba.
   * Essa funcionalidade está incluída nas edições do Azure AD Basic, Premium P1 ou Premium P2.

* Redefinição/Alteração/Desbloqueio da Senha de Autoatendimento **com write-back local**
   * Eu sou um **usuário híbrido**, minha conta de usuário do Active Directory local está sincronizada com minha conta do Azure AD usando o Azure AD Connect. Eu queria alterar minha senha, esqueci minha senha ou ela foi bloqueada.
      * Eu queria alterar ou redefinir minha senha para algo que conheça, ou desbloquear minha conta **e** sincronizar novamente essa alteração no Active Directory local.
   * Essa funcionalidade está incluída nas edições do Azure AD Premium P1 ou Premium P2.

> [!WARNING]
> Os planos de licenciamento do Office 365 autônomo *não oferecem suporte à/ao "Redefinição/alteração/desbloqueio de senha de autoatendimento com write-back local"* e exigem um plano que inclui as edições P1 e P2 do Azure AD Premium para que essa funcionalidade funcione.
>

As informações de licenciamento adicionais, inclusive custos, podem ser encontradas nas páginas a seguir:

* [Site de preços do Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/)
* [Recursos e funcionalidades do Azure Active Directory](https://www.microsoft.com/cloud-platform/azure-active-directory-features)
* [Enterprise Mobility + Security](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)
* [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise)

## <a name="enable-group-or-user-based-licensing"></a>Habilitar licenciamento com base em grupo ou usuário

O Azure AD agora é compatível com o licenciamento baseado em grupo. Os administradores podem atribuir licenças em massa a um grupo de usuários, em vez de atribuí-las uma por vez. Para obter mais informações, consulte [Atribuir, verificar e resolver problemas com licenças](../users-groups-roles/licensing-groups-assign.md#step-1-assign-the-required-licenses).

Alguns serviços da Microsoft não estão disponíveis em todos os locais. Para que uma licença possa ser atribuída a um usuário, o administrador precisa especificar a propriedade **Local de uso** para o usuário. A atribuição de licenças pode ser feita na seção **Usuário** > **Perfil** > **Configurações** no portal do Azure. *Ao usar a atribuição de licença de grupo, qualquer usuário sem um local de uso especificado herda o local do diretório.*

## <a name="next-steps"></a>Próximas etapas

* [Como concluir uma implementação do SSPR com êxito?](howto-sspr-deployment.md)
* [Redefinir ou alterar sua senha](../user-help/active-directory-passwords-update-your-own-password.md)
* [Registro de redefinição de senha de autoatendimento](../user-help/active-directory-passwords-reset-register.md)
* [Quais dados são usados pelo SSPR e quais dados você deve preencher para seus usuários?](howto-sspr-authenticationdata.md)
* [Quais métodos de autenticação estão disponíveis para os usuários?](concept-sspr-howitworks.md#authentication-methods)
* [Quais são as opções de política com o SSPR?](concept-sspr-policy.md)
* [O que é o write-back de senha e por que devo me importar com isso?](howto-sspr-writeback.md)
* [Como faço para informar sobre a atividade no SSPR?](howto-sspr-reporting.md)
* [Quais são todas as opções no SSPR e o que elas significam?](concept-sspr-howitworks.md)
* [Acho que algo não está funcionando. Como faço para solucionar o problema no SSPR?](active-directory-passwords-troubleshoot.md)
* [Tenho uma pergunta que não foi respondida em nenhum lugar](active-directory-passwords-faq.md)
