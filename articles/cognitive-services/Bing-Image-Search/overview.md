---
title: O que é a API de Pesquisa de Imagem do Bing?
titleSuffix: Azure Cognitive Services
description: A API de Pesquisa de Imagem do Bing permite o uso de recursos de pesquisa de imagens cognitivas do Bing em seu aplicativo. Ao enviar consultas de pesquisa de usuário com a API, você pode obter e exibir imagens relevantes e de alta qualidade semelhantes às Imagens do Bing.
services: cognitive-services
author: aahill
manager: cgronlun
ms.assetid: 1446AD8B-A685-4F5F-B4AA-74C8E9A40BE9
ms.service: cognitive-services
ms.component: bing-image-search
ms.topic: overview
ms.date: 10/11/2017
ms.author: aahi
ms.custom: seodec2018
ms.openlocfilehash: eb5f508916ef0944a61d556725ae1ba04123584b
ms.sourcegitcommit: 1c1f258c6f32d6280677f899c4bb90b73eac3f2e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53258297"
---
# <a name="what-is-the-bing-image-search-api"></a>O que é a API de Pesquisa de Imagem do Bing?

A API de Pesquisa de Imagem do Bing permite o uso de recursos de pesquisa de imagens cognitivas do Bing em seu aplicativo. Ao enviar consultas de pesquisa de usuário com a API, você pode obter e exibir imagens relevantes e de alta qualidade semelhantes às [Imagens do Bing](https://www.bing.com/images).

Lembre-se de que a API de Pesquisa de Imagem do Bing fornece resultados da pesquisa apenas com imagens. Use a [API de Pesquisa na Web do Bing](../bing-web-search/search-the-web.md), a [API de Pesquisa de Vídeo](https://docs.microsoft.com/azure/cognitive-services/Bing-Video-Search) e a [API de Pesquisa de Notícias](https://review.docs.microsoft.com/azure/cognitive-services/bing-news-search) para outros tipos de conteúdo da Web.

## <a name="bing-image-search-features"></a>Recursos da Pesquisa de Imagem do Bing

Embora a Pesquisa de Imagem do Bing localize e retorne, principalmente, imagens relevantes de uma consulta de pesquisa, o serviço também fornece vários recursos adicionais para uma recuperação de imagem inteligente e com foco na Web.


| Recurso                                                                                                                                                                                 | DESCRIÇÃO                                                                                                                                                            |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Sugerir os termos de pesquisa em tempo real](https://docs.microsoft.com/azure/cognitive-services/bing-image-search/concepts/bing-image-search-sending-queries#using-and-suggesting-search-terms) | Aprimore sua experiência com aplicativos usando a [API de Sugestão Automática do Bing](../bing-autosuggest/get-suggested-search-terms.md) para exibir os termos de pesquisa sugeridos à medida que eles são digitados. |
| [Filtrar e restringir resultados de imagem](https://docs.microsoft.com/azure/cognitive-services/bing-image-search/concepts/bing-image-search-get-images#filtering-images)                       | Filtrar as imagens que o Bing retorna ao editar parâmetros de consulta.                                                                                                       |
| [Cortar, redimensionar e exibir miniaturas](https://docs.microsoft.com/azure/cognitive-services/bing-image-search/resize-and-crop-thumbnails)                                                | Editar e exibir as visualizações de miniaturas para imagens retornadas pela Pesquisa de Imagem do Bing.                                                                                      |
| [Dinamizar e expandir as consultas de pesquisa do usuário](https://docs.microsoft.com/azure/cognitive-services/bing-image-search/concepts/bing-image-search-sending-queries#pivoting-the-query)               | Expanda seus recursos de pesquisa por meio da inclusão e exibição dos termos de pesquisa sugeridos pelo Bing para consultas.                                                                    |
| [Obter imagens populares](https://review.docs.microsoft.com/azure/cognitive-services/bing-image-search/trending-images)                                                                     | Personalize uma pesquisa para as imagens mais populares no mundo inteiro.                                                                                                          |

## <a name="workflow"></a>Fluxo de trabalho

A API de Pesquisa de Imagem do Bing é um serviço Web RESTful, facilitando a chamada a partir de qualquer linguagem de programação que pode fazer solicitações HTTP e analisar JSON. Você pode usar o serviço usando a [API REST](https://docs.microsoft.com/azure/cognitive-services/bing-image-search/quickstarts/csharp?), ou o [SDK](https://docs.microsoft.com/azure/cognitive-services/bing-image-search/image-search-sdk-quickstart).

1. Crie uma [Conta da API dos Serviços Cognitivos](https://docs.microsoft.com/azure/cognitive-services/cognitive-services-apis-create-account) com acesso às APIs de Pesquisa do Bing. Caso não tenha uma assinatura do Azure, [crie uma conta](https://azure.microsoft.com/try/cognitive-services/?api=bing-web-search-api) gratuitamente.
2. Envie uma solicitação para a API, com uma [consulta de pesquisa](https://docs.microsoft.com/azure/cognitive-services/bing-image-search/concepts/bing-image-search-sending-queries) válida.
3. Processe a resposta da API analisando a mensagem JSON retornada.

## <a name="next-steps"></a>Próximas etapas

Primeiro, experimente a [demonstração interativa](https://azure.microsoft.com/services/cognitive-services/bing-image-search-api/) da API de Pesquisa de Imagem do Bing.
Essa demonstração mostra como você pode, de modo rápido, personalizar uma consulta de pesquisa e vasculhar a Web em busca de imagens.

Quando você estiver pronto para chamar a API, crie uma [Conta de API de serviços cognitivos](https://docs.microsoft.com/azure/cognitive-services/cognitive-services-apis-create-account). Caso não tenha uma assinatura do Azure, [crie uma conta](https://azure.microsoft.com/try/cognitive-services/?api=bing-web-search-api) gratuitamente.

Para iniciar sua primeira solicitação de API rapidamente, você pode aprender a:

* [Enviar consultas de pesquisa ao Bing](https://docs.microsoft.com/azure/cognitive-services/bing-image-search/quickstarts/csharp) usando a API REST ou
* [Solicitar e filtrar](https://docs.microsoft.com/azure/cognitive-services/bing-image-search/image-search-sdk-quickstart) as imagens que o Bing retorna usando o SDK.

## <a name="see-also"></a>Consulte também

* A seção de referência da [API de Pesquisa de Imagem do Bing v7](https://docs.microsoft.com/rest/api/cognitiveservices/bing-images-api-v7-reference) contém definições e informações sobre os pontos de extremidade, cabeçalhos, respostas de API e parâmetros de consulta que podem ser usados para solicitar os resultados da pesquisa baseada em imagem.

* Os [Requisitos de exibição e uso do Bing](./useanddisplayrequirements.md) especificam os usos aceitáveis do conteúdo e das informações obtidas por meio das APIs de pesquisa do Bing.

* O tópico [Obtendo imagens da Web com a API de Pesquisa de Imagem do Bing](https://docs.microsoft.com/azure/cognitive-services/bing-image-search/concepts/bing-image-search-get-images) descreve como pesquisar e obter imagens da Web.

* O tópico [Enviando e trabalhando com consultas de pesquisa](https://docs.microsoft.com/azure/cognitive-services/bing-image-search/concepts/bing-image-search-sending-queries) descreve como criar, personalizar e dinamizar consultas de pesquisa.
