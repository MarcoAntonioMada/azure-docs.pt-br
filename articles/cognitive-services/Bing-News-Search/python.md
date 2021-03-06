---
title: 'Início Rápido: Executar uma pesquisa de notícias com Python – API REST de Pesquisa de Notícias do Bing'
titlesuffix: Azure Cognitive Services
description: Use este Início Rápido para enviar uma solicitação para a API REST de Pesquisa de Notícias do Bing usando Python e receber uma resposta JSON.
services: cognitive-services
author: aahill
manager: cgronlun
ms.service: cognitive-services
ms.component: bing-news-search
ms.topic: quickstart
ms.date: 9/21/2017
ms.author: aahi
ms.custom: seodec2018
ms.openlocfilehash: 8ce8353df9a6f8354c56d9c9115645c0b7f2136a
ms.sourcegitcommit: 1c1f258c6f32d6280677f899c4bb90b73eac3f2e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53251650"
---
# <a name="quickstart-perform-a-news-search-using-python-and-the-bing-news-search-rest-api"></a>Início Rápido: Executar uma pesquisa de notícias usando Python e a API REST de Pesquisa de Notícias do Bing

Este passo a passo demonstra um exemplo simples de como chamar a API de Pesquisa de Notícias do Bing e o pós-processamento do objeto JSON resultante. Para obter mais informações, confira [Documentação da Pesquisa de Notícias do Bing](https://docs.microsoft.com/rest/api/cognitiveservices/bing-web-api-v7-reference).  

Execute este exemplo como um Jupyter Notebook em [MyBinder](https://mybinder.org) clicando na notificação de inicialização do Associador: 

[![Associador](https://mybinder.org/badge.svg)](https://mybinder.org/v2/gh/Microsoft/cognitive-services-notebooks/master?filepath=BingNewsSearchAPI.ipynb)

## <a name="prerequisites"></a>Pré-requisitos

É necessário ter uma [conta da API dos Serviços Cognitivos](https://docs.microsoft.com/azure/cognitive-services/cognitive-services-apis-create-account) com **APIs de Pesquisa do Bing**. A [avaliação gratuita](https://azure.microsoft.com/try/cognitive-services/?api=bing-web-search-api) é suficiente para esse início rápido. Você precisa da chave de acesso fornecida quando ativar sua avaliação gratuita.  Veja também [Cognitive Services Pricing - API de Pesquisa do Bing](https://azure.microsoft.com/pricing/details/cognitive-services/search-api/).

## <a name="running-the-walkthrough"></a>Executando o passo a passo
Primeiro, defina `subscription_key` com a chave de API do serviço de API do Bing.


```python
subscription_key = None
assert subscription_key
```

Em seguida, verifique se o ponto de extremidade `search_url` está correto. Atualmente, apenas um ponto de extremidade é usado para APIs de pesquisa do Bing. Caso encontre erros de autorização, verifique esse valor em relação ao ponto de extremidade de pesquisa do Bing no painel do Azure.


```python
search_url = "https://api.cognitive.microsoft.com/bing/v7.0/news/search"
```

Defina `search_term` para procurar artigos de notícias sobre a Microsoft.


```python
search_term = "Microsoft"
```

O bloco a seguir usa a biblioteca `requests` do Python para chamar as APIs de Pesquisa do Bing e retornar os resultados como um objeto JSON. Observe que passamos a chave de API por meio do dicionário `headers` e o termo de pesquisa por meio do dicionário `params`. Para ver a lista completa de opções que podem ser usadas para filtrar os resultados da pesquisa, veja a documentação da [API REST](https://docs.microsoft.com/rest/api/cognitiveservices/bing-news-api-v7-reference).


```python
import requests

headers = {"Ocp-Apim-Subscription-Key" : subscription_key}
params  = {"q": search_term, "textDecorations": True, "textFormat": "HTML"}
response = requests.get(search_url, headers=headers, params=params)
response.raise_for_status()
search_results = response.json()
```

O objeto `search_results` contém os novos artigos relevantes junto com metadados avançados. Por exemplo, a linha de código a seguir extrai as descrições dos artigos.


```python
descriptions = [article["description"] for article in search_results["value"]]
```

Essas descrições podem então ser renderizadas como uma tabela com a palavra-chave de pesquisa realçada em **negrito**.


```python
from IPython.display import HTML
rows = "\n".join(["<tr><td>{0}</td></tr>".format(desc) for desc in descriptions])
HTML("<table>"+rows+"</table>")
```

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Percorrendo notícias](paging-news.md)
> [Usando marcadores de decoração para realçar o texto](hit-highlighting.md)

## <a name="see-also"></a>Consulte também 

 [Pesquisando notícias na Web](search-the-web.md)  
 [Experimente](https://azure.microsoft.com/services/cognitive-services/bing-news-search-api/)
