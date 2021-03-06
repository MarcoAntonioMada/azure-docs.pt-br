---
title: O que é o Cofre da Chave do Azure? - Azure Key Vault | Microsoft Docs
description: O Cofre da Chave do Azure ajuda a proteger chaves criptográficas e segredos usados por aplicativos e serviços em nuvem. Usando o Cofre da Chave do Azure, os clientes podem criptografar chaves e segredos (como chaves de autenticação, chaves de conta de armazenamento, chaves de criptografia de dados, arquivos .PFX e senhas) usando chaves que são protegidas por HSMs (módulos de segurança de hardware).
services: key-vault
documentationcenter: ''
author: barclayn
manager: mbaldwin
tags: azure-resource-manager
ms.assetid: e759df6f-0638-43b1-98ed-30b3913f9b82
ms.service: key-vault
ms.workload: identity
ms.tgt_pltfrm: na
ms.topic: conceptual
ms.date: 01/07/2019
ms.author: barclayn
ms.openlocfilehash: f3c198ab8a17df019f1735a9b62e27f1051f64c5
ms.sourcegitcommit: fbf0124ae39fa526fc7e7768952efe32093e3591
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54076324"
---
# <a name="what-is-azure-key-vault"></a>O que é o Cofre da Chave do Azure?

O Azure Key Vault ajuda a resolver os problemas a seguir:

- **Gerenciamento de Segredos**: o Azure Key Vault pode ser usado para armazenar com segurança e controlar firmemente o acesso a tokens, senhas, certificados, chaves de API e outros segredos.
- **Gerenciamento de Chaves** – O Azure Key Vault também pode ser usado como uma solução de gerenciamento de chaves. O Azure Key Vault torna fácil criar e controlar as chaves de criptografia usadas para criptografar seus dados. 
- **Gerenciamento de Certificado** – O Azure Key Vault também é um serviço que permite provisionar, gerenciar e implantar certificados de protocolo SSL/TLS (Secure Sockets Layer/Transport Layer Security) públicos e privados para uso com o Azure e seus recursos internos conectados com facilidade. 
- **Armazenar segredos com suporte de módulos de segurança de hardware**: as chaves e os segredos podem ser protegidos por software ou FIPS 140-2 Nível 2 que valida HSMs.

## <a name="basic-concepts"></a>Conceitos básicos

O Azure Key Vault é uma ferramenta para armazenar e acessar segredos de forma segura. Um segredo é tudo o que você deseja controlar rigorosamente o acesso, como certificados, senhas ou chaves de API. Um **cofre** é um grupo lógico de segredos. Agora para fazer todas as operações com o Key Vault primeiro você precisará autenticar-se a ele. 

Fundamentalmente, há três maneiras de autenticar no Key Vault:

1. **Usando a [Identidade de Serviço Gerenciada](https://docs.microsoft.com/azure/active-directory/managed-identities-azure-resources/overview)**  (**Práticas Recomendadas**): quando você implanta um aplicativo em uma máquina Virtual no Azure, é possível atribuir uma identidade para sua máquina Virtual que tem acesso Key Vault. Você também pode atribuir identidades para outros recursos do Azure que estão listados [aqui](https://docs.microsoft.com/azure/active-directory/managed-identities-azure-resources/overview). O benefício dessa abordagem é que o aplicativo / serviço não está gerenciando a rotação do segredo primeiro. Azure gira automaticamente a identidade. 
2. **Usando a entidade de serviço e o certificado:** a segunda opção é usar uma entidade de serviço e um certificado associado que tem acesso ao Key Vault. O ônus de girar o certificado é sobre o proprietário do aplicativo ou o desenvolvedor e, portanto, isso não é recomendado.
3. **Usando a entidade de serviço e o segredo:** a terceira opção (não preferencial) é usar uma entidade de serviço e um segredo para autenticar ao Key Vault.

> [!NOTE]
> A terceira opção acima não deve ser usada, pois é difícil girar automaticamente o segredo de inicialização usado para autenticar no Key Vault.

Estes são alguns termos principais:

- **Tenant**: um locatário é a organização que possui e gerencia uma instância específica de serviços em nuvem da Microsoft. Geralmente, ele é usado de maneira exata para referir-se ao conjunto de serviços do Azure e do Office 365 para uma organização.
- **Proprietário do cofre**: pode criar um cofre de chaves e obter acesso e controle totais sobre ele. O proprietário do cofre também pode configurar a auditoria para registrar quem acessa os segredos e as chaves. Os administradores podem controlar o ciclo de vida da chave. Eles podem reverter para uma nova versão da chave, fazer o backup e tarefas relacionadas.
- **Consumidor do cofre**: pode executar ações nos ativos dentro do cofre de chaves quando seu proprietário concede acesso ao cliente. As ações disponíveis dependem das permissões concedidas.
- **Recurso**: Trata-se de um item gerenciável que está disponível por meio do Azure. Alguns recursos comuns são uma máquina virtual, conta de armazenamento, aplicativo Web, banco de dados e rede virtual, mas há muito mais.
- **Grupo de recursos**: Um grupo de recursos é um contêiner que mantém os recursos relacionados a uma solução do Azure. O grupo de recursos pode incluir todos os recursos para a solução ou apenas os recursos que você deseja gerenciar como um grupo. Você decide como deseja alocar recursos para grupos de recursos com base no que faz mais sentido para sua organização.
- **Entidade de serviço**: uma entidade de serviço do Azure é uma identidade de segurança usada por aplicativos criados pelo usuário, serviços e ferramentas de automação para acessar recursos específicos do Azure. Pense nela como uma “identidade de usuário” (nome de usuário e senha ou certificado) com uma função específica e permissões rigidamente controladas. Uma entidade de serviço só precisa fazer coisas específicas, ao contrário de uma identidade de usuário geral. A segurança aumenta se você só conceder a ela o nível mínimo de permissões necessárias para realizar suas tarefas de gerenciamento.
- **[Azure AD (Azure Active Directory)](../active-directory/active-directory-whatis.md)**: o Azure AD é o serviço do Active Directory de um locatário. Cada diretório tem um ou mais domínios. Um diretório pode ter várias assinaturas associadas a ele, mas apenas um locatário. 
- **ID de Locatário do Azure**: uma ID de locatário é uma maneira exclusiva para identificar uma instância do Azure AD dentro de uma assinatura do Azure.
- **Identidades gerenciadas para recursos do Azure**: O Azure Key Vault fornece uma maneira de armazenar com segurança as credenciais e outras chaves e segredos, mas seu código precisa autenticar para o Key Vault para recuperá-los. Usar a identidade gerenciada torna a solução desse problema mais simples, fornecendo aos serviços do Azure uma identidade gerenciada automaticamente no Microsoft Azure Active Directory. Você pode usar essa identidade para autenticar o Key Vault ou qualquer serviço que dê suporte à autenticação do Azure AD sem ter as credenciais no código. Para obter mais informações, veja a imagem abaixo e as [identidades para visão geral de recursos do Azure gerenciadas](../active-directory/managed-identities-azure-resources/overview.md).

    ![diagrama sobre como usar identidades gerenciadas para recursos do Azure](./media/key-vault-whatis/msi.png)

## <a name="key-vault-roles"></a>Funções do Key Vault

Use a tabela a seguir para entender melhor como o Cofre da Chave pode ajudar a atender às necessidades de desenvolvedores e administradores de segurança.

| Função | Problema declarado | Solucionado pelo Cofre da Chave do Azure |
| --- | --- | --- |
| Desenvolvedor de um aplicativo do Azure |"Eu quero escrever um aplicativo para o Azure que use chaves de assinatura e criptografia, mas quero que as chaves sejam externas ao aplicativo, para que a solução seja adequada a um aplicativo distribuído geograficamente. <br/><br/>Quero que essas chaves e segredos sejam protegidos, sem precisar escrever o código sozinho. E também que essas chaves e segredos sejam fáceis de usar em meu aplicativo, com desempenho ideal.” |√ As chaves são armazenadas em um cofre e invocadas pelo URI quando necessário.<br/><br/> √ As chaves são protegidas pelo Azure, usando módulos de segurança de hardware, comprimentos da chave e algoritmos padrão da indústria.<br/><br/>  √ As chaves são processadas em HSMs que residem nos mesmos datacenters do Azure que os aplicativos. Esse método permite uma maior confiabilidade e uma latência reduzida em comparação às chaves que residem em um local separado, como no local. |
| Desenvolvedor de SaaS (software como serviço) |"Eu não quero a responsabilidade ou ser o possível culpado por problemas com as chaves e segredos de locatário dos meus clientes. <br/><br/>Quero que os clientes tenham e gerenciem suas chaves para que eu possa me concentrar em fazer o que faço melhor, que é fornecer os recursos centrais do software." |√ Os clientes podem importar suas próprias chaves para o Azure e gerenciá-las. Quando um aplicativo de SaaS precisa executar operações criptográficas usando as chaves de seus clientes, o Cofre de Chaves faz essas operações em nome dele. O aplicativo não vê as chaves dos clientes. |
| Diretor-chefe de segurança (CSO) |"Quero saber que nossos aplicativos estão em conformidade com HSMs FIPS 140-2 Nível 2, para um gerenciamento de chaves seguro. <br/><br/>Quero garantir que minha organização controle o ciclo de vida da chave e possa monitorar seu uso. <br/><br/>E embora usemos vários recursos e serviços do Azure, quero gerenciar as chaves de um único local no Azure. |√ Os HSMs têm certificação FIPS 140-2 Nível 2.<br/><br/>√ O Cofre de Chaves foi projetado para que a Microsoft não veja nem extraia suas chaves.<br/><br/>√ Uso de chave é registrado praticamente em tempo real.<br/><br/>√ O cofre fornece uma única interface, independentemente de quantos cofres você tenha no Azure, quais sejam as regiões com suporte e quais aplicativos as usem. |

Qualquer pessoa com uma assinatura do Azure pode criar e usar cofres de chaves. Embora o Key Vault beneficie desenvolvedores e administradores de segurança, ele pode ser implementado e gerenciado pelo administrador de uma organização que gerencie outros serviços do Azure para a organização. Por exemplo, esse administrador pode fazer logon com uma assinatura do Azure, criar um cofre para a organização armazenar as chaves e ser responsável por tarefas operacionais, como:

- Criar ou importar uma chave ou segredo
- Revogar ou excluir uma chave ou segredo
- Autorizar usuários ou aplicativos a acessar o cofre da chave para que eles possam gerenciar ou usar suas chaves e segredos
- Configurar o uso de chaves (por exemplo, assinar ou criptografar)
- Monitorar o uso de chaves

Esse administrador, então, forneceria aos desenvolvedores URIs a serem chamados de seus aplicativos e forneceria ao administrador de segurança as informações de log de uso de chave. 

![Overview of Azure Key Vault][1]

Os desenvolvedores também podem gerenciar as chaves diretamente, por meio de APIs. Para saber mais, confira o [guia do desenvolvedor do Cofre da Chave](key-vault-developers-guide.md).

## <a name="next-steps"></a>Próximas etapas

Saiba como [proteger seu cofre](key-vault-secure-your-key-vault.md)
<!--Image references--> [1]: ./media/key-vault-what is / Azure Key Vault overview.png O Cofre de Chaves do Azure está disponível na maioria das regiões. Para obter mais informações, consulte a [Página de preços do Cofre da Chave](https://azure.microsoft.com/pricing/details/key-vault/).
