---
title: Termos de pesquisa de sugestão automática - API de Pesquisa na Web do Bing
titleSuffix: Azure Cognitive Services
description: Emparelhe a API de Pesquisa na Web do Bing com a API de Sugestão Automática do Bing para fornecer aos usuários uma experiência de pesquisa aprimorada.
services: cognitive-services
author: aahill
manager: cgronlun
ms.service: cognitive-services
ms.component: bing-web-search
ms.topic: conceptual
ms.date: 8/13/2018
ms.author: aahi
ms.openlocfilehash: 1df478f02e90c95d11c9305381e89e147fee3077
ms.sourcegitcommit: ebf2f2fab4441c3065559201faf8b0a81d575743
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52164009"
---
# <a name="autosuggest-bing-search-terms-in-your-application"></a>Termos de pesquisa de Sugestão Automática do Bing no aplicativo

Se você fornecer uma caixa de pesquisa em que o usuário insere seu termo de pesquisa, use a [API de Sugestão Automática do Bing](../bing-autosuggest/get-suggested-search-terms.md) para melhorar a experiência. A API retorna cadeias de caracteres de consulta sugeridas com base em termos de pesquisa parciais como os tipos de usuário.

Depois que o usuário insere um termo de pesquisa, ele deve ser codificado como URL antes que o parâmetro de consulta [q](https://docs.microsoft.com/rest/api/cognitiveservices/bing-web-api-v7-reference#query) seja definido. Por exemplo, se o usuário inserir *sailing dinghies* (bote à vela), defina `q` como `sailing+dinghies` ou `sailing%20dinghies`.

Se o termo de consulta contiver um erro de ortografia, a resposta da pesquisa incluirá um objeto [QueryContext](https://docs.microsoft.com/rest/api/cognitiveservices/bing-web-api-v7-reference#querycontext). O objeto mostra a ortografia original e a ortografia corrigida usada pelo Bing para a pesquisa.

```json
"queryContext": {
    "originalQuery": "sialing dingy for sale",
    "alteredQuery": "sailing dinghy for sale",
    "alterationOverrideQuery": "+sialing +dingy for sale"
}
```

Você pode usar essas informações para, ao exibir os resultados da pesquisa, informar o usuário de que você modificou a cadeia de caracteres de consulta fornecida por ele.

![Exemplo de experiência do usuário do contexto de consulta](./media/cognitive-services-bing-web-api/bing-query-context.PNG)  

## <a name="next-steps"></a>Próximas etapas  

* Revise o exemplo [Respostas da API de Pesquisa na Web do Bing](search-responses.md).  

## <a name="see-also"></a>Consulte também  

* [Referência da API de Pesquisa na Web do Bing](https://docs.microsoft.com/rest/api/cognitiveservices/bing-web-api-v7-reference)
