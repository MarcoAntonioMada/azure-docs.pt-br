---
title: Introdução ao Azure AD em projetos WebApi do Visual Studio
description: Como começar a usar o Active Directory do Azure em projetos da API Web após a conexão ou criação de um AD do Azure usando os serviços conectados do Visual Studio
services: active-directory
author: ghogen
manager: douge
ms.assetid: bf1eb32d-25cd-4abf-8679-2ead299fedaa
ms.prod: visual-studio-dev15
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/12/2018
ms.author: ghogen
ms.custom: aaddev, vs-azure
ms.openlocfilehash: 69f17b366b2480b34873d8fede223715619d0e66
ms.sourcegitcommit: 30c7f9994cf6fcdfb580616ea8d6d251364c0cd1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/18/2018
ms.locfileid: "42145703"
---
# <a name="get-started-with-azure-active-directory-webapi-projects"></a>Introdução ao Azure Active Directory (projetos WebApi)

> [!div class="op_single_selector"]
> - [Introdução](vs-active-directory-webapi-getting-started.md)
> - [O que aconteceu](vs-active-directory-webapi-what-happened.md)

Este artigo fornece orientações adicionais depois de você ter adicionado o Active Directory para um projeto WebAPI ASP.NET por meio do comando **Projeto > Serviços Conectados** do Visual Studio. Se você ainda não adicionou o serviço ao seu projeto, você pode fazer isso a qualquer momento.

Consulte [O que aconteceu com meu projeto WebAPI?](vs-active-directory-webapi-what-happened.md) para as alterações feitas ao seu projeto ao adicionar o serviço conectado.

## <a name="requiring-authentication-to-access-controllers"></a>Exigir autenticação para acessar os controladores

Todos os controladores em seu projeto foram marcados com o `[Authorize]` atributo. Este atributo exige que o usuário seja autenticado antes de acessar as APIs definidas por esses controladores. Para permitir que o controlador seja acessado anonimamente, remova este atributo do controlador. Se desejar definir as permissões em um nível mais granular, aplique o atributo a cada método que necessita de autorização em vez de aplicá-lo à classe do controlador.

## <a name="next-steps"></a>Próximas etapas

- [Cenários de autenticação do Azure Active Directory](authentication-scenarios.md)
- [Adicionar entrada com a Microsoft para um aplicativo Web ASP.NET](quickstart-v1-aspnet-webapp.md)
