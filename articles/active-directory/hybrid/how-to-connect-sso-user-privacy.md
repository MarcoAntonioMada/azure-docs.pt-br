---
title: Privacidade do usuário e logon único contínuo do Microsoft Azure AD | Microsoft Docs
description: Este artigo trata do SSO Contínuo do Microsoft Azure AD (Azure Active Directory) e conformidade com GDPR.
services: active-directory
keywords: o que é o Azure AD Connect, GDPR, componentes necessários para o Microsoft Azure AD, SSO, Logon Único
documentationcenter: ''
author: billmath
manager: mtillman
ms.assetid: 9f994aca-6088-40f5-b2cc-c753a4f41da7
ms.service: active-directory
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 05/21/2018
ms.component: hybrid
ms.author: billmath
ms.openlocfilehash: 9fc31c85863a36333d36edca9089cd533b3222a1
ms.sourcegitcommit: 5b869779fb99d51c1c288bc7122429a3d22a0363
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53188819"
---
# <a name="user-privacy-and-azure-ad-seamless-single-sign-on"></a>Privacidade do usuário e logon único contínuo do Microsoft Azure AD

[!INCLUDE [Privacy](../../../includes/gdpr-intro-sentence.md)]

## <a name="overview"></a>Visão geral


O SSO Contínuo do Microsoft Azure AD cria o seguinte tipo de log, que pode conter Dados Pessoais: 

- Arquivos de log de rastreamento do Azure AD Connect.

Melhore a privacidade do usuário para o SSO Contínuo de duas maneiras:

1.  Mediante solicitação, extraia dados de uma pessoa e remova os dados dessa pessoa das instalações.
2.  Certifique-se de que nenhum dado é retido além de 48 horas.

É altamente recomendável a segunda opção, pois é mais fácil de implementar e manter. Consulte as instruções a seguir para cada tipo de log:

### <a name="delete-azure-ad-connect-trace-log-files"></a>Arquivos de log de rastreamento do Azure AD Connect

Verifique o conteúdo da pasta **%ProgramData%\AADConnect** e exclua o conteúdo do log de rastreamento (arquivos **trace-\*.log**) dessa pasta dentro de 48 horas após instalar ou atualizar o Azure AD Connect ou modificar a configuração do SSO Contínuo, pois essa ação pode criar dados cobertos pelo GDPR.

>[!IMPORTANT]
>Não exclua o arquivo **PersistedState.xml** nessa pasta, pois esse arquivo será utilizado para manter o estado da instalação anterior do Azure AD Connect e quando uma instalação de upgrade for feita. Esse arquivo nunca conterá dados sobre uma pessoa e nunca deverá ser excluído.

É possível revisar e excluir esses arquivos de log de rastreamento utilizando o Windows Explorer ou usar o script a seguir do PowerShell para executar as ações necessárias:

```
$Files = ((Get-Item -Path "$env:programdata\aadconnect\trace-*.log").VersionInfo).FileName 
 
Foreach ($file in $Files) { 
    {Remove-Item -Path $File -Force} 
}
```

Salve o script em um arquivo com a extensão ".PS1". Execute esse script, conforme necessário.

Para saber mais sobre os requisitos do GDPR do Azure AD Connect relacionados, consulte [este artigo](reference-connect-user-privacy.md).

### <a name="note-about-domain-controller-logs"></a>Observação sobre os logs do Controlador de Domínio

Se o log de auditoria estiver habilitado, esse produto poderá gerar logs de segurança para os Controladores de Domínio. Para saber mais sobre como configurar políticas de auditoria, leia este [artigo](https://technet.microsoft.com/library/dd277403.aspx).

## <a name="next-steps"></a>Próximas etapas
* [Revise a Política de Privacidade da Microsoft na Central de Confiabilidade](https://www.microsoft.com/trustcenter)
  - [**Solução de problemas**](tshoot-connect-sso.md) – Saiba como resolver problemas comuns do recurso.
  - [**UserVoice**](https://feedback.azure.com/forums/169401-azure-active-directory/category/160611-directory-synchronization-aad-connect) – para registrar solicitações de novos recursos.
