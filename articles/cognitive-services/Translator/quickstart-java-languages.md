---
title: 'Início Rápido: Obter lista de idiomas compatíveis, Java - API de Tradução de Texto'
titleSuffix: Azure Cognitive Services
description: Neste início rápido, você obtém uma lista dos idiomas com suporte para tradução, transliteração e pesquisa em dicionário usando a API de Tradução de Texto.
services: cognitive-services
author: erhopf
manager: cgronlun
ms.service: cognitive-services
ms.component: translator-text
ms.topic: quickstart
ms.date: 12/03/2018
ms.author: erhopf
ms.openlocfilehash: 9a5985adb92799726951ad37c1dbd0b72c6c9709
ms.sourcegitcommit: 2bb46e5b3bcadc0a21f39072b981a3d357559191
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52888997"
---
# <a name="quickstart-use-the-translator-text-api-to-get-a-list-of-supported-languages-using-java"></a>Início Rápido: Usar a API de Tradução de Texto para obter uma lista dos idiomas compatíveis usando Java

Neste início rápido, você obtém uma lista dos idiomas com suporte para tradução, transliteração e pesquisa em dicionário usando a API de Tradução de Texto.

Este início rápido requer uma [Conta dos Serviços Cognitivos do Azure](https://docs.microsoft.com/azure/cognitive-services/cognitive-services-apis-create-account) com um recurso de Tradução de Texto. Se não tiver uma conta, você poderá usar a [avaliação gratuita](https://azure.microsoft.com/try/cognitive-services/) para obter uma chave de assinatura.

## <a name="prerequisites"></a>Pré-requisitos

* [JDK 7 ou posterior](https://www.oracle.com/technetwork/java/javase/downloads/index.html)
* [Gradle](https://gradle.org/install/)
* Uma chave de assinatura do Azure para a Tradução de Texto

## <a name="initialize-a-project-with-gradle"></a>Inicializar um projeto com o Gradle

Vamos começar criando um diretório de trabalho para esse projeto. Na linha de comando (ou terminal), execute este comando:

```console
mkdir get-languages-sample
cd get-languages-sample
```

Em seguida, você vai para inicializar um projeto do Gradle. Esse comando criará arquivos de compilação essenciais para o Gradle, principalmente o `build.gradle.kts`, que é usado para criar e configurar seu aplicativo no tempo de execução. Execute este comando no diretório de trabalho:

```console
gradle init --type basic
```

Quando solicitado a escolher uma **DSL**, escolha **Kotlin**.

## <a name="configure-the-build-file"></a>Configurar o arquivo de compilação

Localize `build.gradle.kts` e abra-o com seu editor de texto ou IDE favorito. Depois, copie nessa configuração de compilação:

```
plugins {
    java
    application
}
application {
    mainClassName = "GetLanguages"
}
repositories {
    mavenCentral()
}
dependencies {
    compile("com.squareup.okhttp:okhttp:2.5.0")
    compile("com.google.code.gson:gson:2.8.5")
}
```

Observe que esse exemplo tem dependências de OkHttp para solicitações HTTP e de Gson para manipular e analisar o JSON. Para saber mais sobre as configurações de compilação, confira [Criar Novas Compilações do Gradle](https://guides.gradle.org/creating-new-gradle-builds/).

## <a name="create-a-java-file"></a>Criar um arquivo Java

Vamos criar uma pasta para seu aplicativo de exemplo. No diretório de trabalho, execute:

```console
mkdir -p src/main/java
```

Em seguida, nessa pasta, crie um arquivo chamado `GetLanguages.java`.

## <a name="import-required-libraries"></a>Importar bibliotecas necessárias

Abra `GetLanguages.java` e adicione estas instruções de importação:

```java
import java.io.*;
import java.net.*;
import java.util.*;
import com.google.gson.*;
import com.squareup.okhttp.*;
```

## <a name="define-variables"></a>Definir variáveis

Primeiro, você precisará criar uma classe pública para seu projeto:

```java
public class GetLanguages {
  // All project code goes here...
}
```

Adicione essas linhas à classe `GetLanguages`:

```java
String subscriptionKey = "YOUR_SUBSCRIPTION_KEY";
String url = "https://api.cognitive.microsofttranslator.com/languages?api-version=3.0";
```

## <a name="create-a-client-and-build-a-request"></a>Criar um cliente e compilar uma solicitação

Adicione esta linha à classe `GetLanguages` para instanciar o `OkHttpClient`:

```java
// Instantiates the OkHttpClient.
OkHttpClient client = new OkHttpClient();
```

Em seguida, vamos compilar a solicitação GET.

```java
// This function performs a GET request.
public String Get() throws IOException {
    Request request = new Request.Builder()
            .url(url).get()
            .addHeader("Ocp-Apim-Subscription-Key", subscriptionKey)
            .addHeader("Content-type", "application/json").build();
    Response response = client.newCall(request).execute();
    return response.body().string();
}
```

## <a name="create-a-function-to-parse-the-response"></a>Criar uma função para analisar a resposta

Essa função simples analisa e melhora a aparência da resposta JSON no serviço de Tradução de Texto.

```java
// This function prettifies the json response.
public static String prettify(String json_text) {
    JsonParser parser = new JsonParser();
    JsonElement json = parser.parse(json_text);
    Gson gson = new GsonBuilder().setPrettyPrinting().create();
    return gson.toJson(json);
}
```

## <a name="put-it-all-together"></a>Colocar tudo isso junto

A última etapa é fazer uma solicitação e obter uma resposta. Adicione essas linhas ao projeto:

```java
public static void main(String[] args) {
    try {
        GetLanguages getLanguagesRequest = new GetLanguages();
        String response = getLanguagesRequest.Get();
        System.out.println(prettify(response));
    } catch (Exception e) {
        System.out.println(e);
    }
}
```

## <a name="run-the-sample-app"></a>Executar o aplicativo de exemplo

E, pronto, você já pode executar seu aplicativo de exemplo. Na linha de comando (ou sessão de terminal), navegue até a raiz do diretório de trabalho e execute:

```console
gradle build
```

## <a name="sample-response"></a>Resposta de exemplo

Uma resposta bem-sucedida é retornada em JSON, conforme mostrado no seguinte exemplo:

```json
{
  "translation": {
    "af": {
      "name": "Afrikaans",
      "nativeName": "Afrikaans",
      "dir": "ltr"
    },
    "ar": {
      "name": "Arabic",
      "nativeName": "العربية",
      "dir": "rtl"
    },
...
  },
  "transliteration": {
    "ar": {
      "name": "Arabic",
      "nativeName": "العربية",
      "scripts": [
        {
          "code": "Arab",
          "name": "Arabic",
          "nativeName": "العربية",
          "dir": "rtl",
          "toScripts": [
            {
              "code": "Latn",
              "name": "Latin",
              "nativeName": "اللاتينية",
              "dir": "ltr"
            }
          ]
        },
        {
          "code": "Latn",
          "name": "Latin",
          "nativeName": "اللاتينية",
          "dir": "ltr",
          "toScripts": [
            {
              "code": "Arab",
              "name": "Arabic",
              "nativeName": "العربية",
              "dir": "rtl"
            }
          ]
        }
      ]
    },
...
  },
  "dictionary": {
    "af": {
      "name": "Afrikaans",
      "nativeName": "Afrikaans",
      "dir": "ltr",
      "translations": [
        {
          "name": "English",
          "nativeName": "English",
          "dir": "ltr",
          "code": "en"
        }
      ]
    },
    "ar": {
      "name": "Arabic",
      "nativeName": "العربية",
      "dir": "rtl",
      "translations": [
        {
          "name": "English",
          "nativeName": "English",
          "dir": "ltr",
          "code": "en"
        }
      ]
    },
...
  }
}
```

## <a name="next-steps"></a>Próximas etapas

Explore o exemplo de código para este início rápido e outros, incluindo tradução e transliteração, bem como outros projetos de Tradução de Texto de exemplo no GitHub.

> [!div class="nextstepaction"]
> [Explorar exemplos de Java no GitHub](https://aka.ms/TranslatorGitHub?type=&language=java)

## <a name="see-also"></a>Consulte também

* [Traduzir o texto](quickstart-java-translate.md)
* [Transliteração de texto](quickstart-java-transliterate.md)
* [Identificar a linguagem pela entrada](quickstart-java-detect.md)
* [Obter traduções alternativas](quickstart-java-dictionary.md)
* [Determinar o comprimento da frase em uma entrada](quickstart-java-sentences.md)
