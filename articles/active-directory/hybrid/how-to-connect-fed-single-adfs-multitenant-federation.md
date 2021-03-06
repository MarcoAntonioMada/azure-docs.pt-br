---
title: Associando vários Azure AD com um AD FS único | Microsoft Docs
description: Neste documento, você aprenderá a federar vários Azure AD com um único AD FS.
keywords: federar, ADFS, AD FS, vários locatários, único AD FS, um ADFS, federação multilocatária, adfs de várias florestas, aad connect, federação, federação entre locatários
services: active-directory
documentationcenter: ''
author: billmath
manager: mtillman
editor: ''
ms.assetid: ''
ms.service: active-directory
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: get-started-article
ms.date: 07/17/2017
ms.component: hybrid
ms.author: billmath
ms.openlocfilehash: 951b47c7193b2b405def9831e94c5e29faff3119
ms.sourcegitcommit: 295babdcfe86b7a3074fd5b65350c8c11a49f2f1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/27/2018
ms.locfileid: "53791109"
---
# <a name="federate-multiple-instances-of-azure-ad-with-single-instance-of-ad-fs"></a>Federar várias instâncias do Azure AD com uma instância única do AD FS

Um único farm do AD FS de alta disponibilidade pode federar várias florestas se tiverem uma relação de confiança bidirecional. Essas várias florestas podem ou não corresponder ao mesmo Azure Active Directory. Este artigo fornece instruções sobre como configurar a federação entre uma única implantação do AD FS e mais de uma floresta que sincronizam com Azure AD diferentes.

![Federação de multilocatária com AD FS único](./media/how-to-connect-fed-single-adfs-multitenant-federation/concept.png)
 
> [!NOTE]
> O write-back de dispositivo e o ingresso automático de dispositivo não têm suporte neste cenário.

> [!NOTE]
> O Azure AD Connect não pode ser usado para configurar a federação neste cenário como o Azure AD Connect pode configurar a federação de domínios em um único Azure AD.

## <a name="steps-for-federating-ad-fs-with-multiple-azure-ad"></a>Etapas para federar o AD FS com vários Azure AD

Imagine um domínio contoso.com no contoso.onmicrosoft.com do Azure Active Directory já é federado com o AD FS local instalado no ambiente de Active Directory local contoso.com. Fabrikam.com é um domínio no Azure Active Directory fabrikam.onmicrosoft.com.

## <a name="step-1-establish-a-two-way-trust"></a>Etapa 1: estabelecer uma relação de confiança bidirecional
 
Para que o AD FS em contoso.com seja capaz de autenticar usuários no fabrikam.com, uma relação de confiança bidirecional é necessária entre contoso.com e fabrikam.com. Siga as diretrizes neste [artigo](https://technet.microsoft.com/library/cc816590.aspx) para criar a relação de confiança bidirecional.
 
## <a name="step-2-modify-contosocom-federation-settings"></a>Etapa 2: modificar configurações de federação de contoso.com 
 
O emissor padrão definido para um único domínio federado ao AD FS é "http\://ADFSServiceFQDN/adfs/services/trust", por exemplo, `http://fs.contoso.com/adfs/services/trust`. O Azure Active Directory requer um emissor exclusivo para cada domínio. Já que o mesmo AD FS vai federar dois domínios, o valor do emissor deve ser modificado para ser exclusivo para cada domínio federado pelo AD FS com o Azure Active Directory. 
 
No servidor do AD FS, abra o PowerShell do Azure AD (certifique-se de que o módulo MSOnline esteja instalado) e execute as seguintes etapas:
 
Conecte-se ao Azure Active Directory que contém o domínio contoso.com Connect-MsolService Atualize as configurações de federação para contoso.com Update-MsolFederatedDomain - DomainName contoso.com – SupportMultipleDomain
 
O emissor na configuração da federação de domínio será alterado para "http\://contoso.com/adfs/services/trust" e uma regra de declaração de emissão será adicionada para que o objeto de confiança de terceira parte confiável do Azure AD emita o valor de issuerId correto com base no sufixo de UPN.
 
## <a name="step-3-federate-fabrikamcom-with-ad-fs"></a>Etapa 3: federar fabrikam.com com o AD FS
 
Na sessão do PowerShell do Azure AD, siga estas etapas: Conectar-se ao Azure Active Directory que contém o domínio fabrikam.com

    Connect-MsolService
Converta o domínio gerenciado fabrikam.com em federado:

    Convert-MsolDomainToFederated -DomainName fabrikam.com -Verbose -SupportMultipleDomain
 
A operação acima vai federar o domínio fabrikam.com com o mesmo AD FS. Você pode verificar as configurações de domínio usando Get-MsolDomainFederationSettings para os dois domínios.

## <a name="next-steps"></a>Próximas etapas
[Conectar o Active Directory com o Azure Active Directory](whatis-hybrid-identity.md)
