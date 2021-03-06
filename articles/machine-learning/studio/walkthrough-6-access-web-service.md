---
title: 'Etapa 6: Acessar serviço Web – Azure Machine Learning Studio | Microsoft Docs'
description: 'Etapa 6 do passo a passo Desenvolver uma solução de previsão: Acessar um serviço Web ativo do Azure Machine Learning Studio.'
services: machine-learning
documentationcenter: ''
author: garyericson
ms.custom: seodec18
ms.author: garye
editor: cgronlun
ms.assetid: 6a65c89a-40ab-4673-8dd8-8eee0a150e3b
ms.service: machine-learning
ms.component: studio
ms.workload: data-services
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 03/23/2017
ms.openlocfilehash: e0628f6ed39652f3168917e26383b5d3c4a4fa4b
ms.sourcegitcommit: 1c1f258c6f32d6280677f899c4bb90b73eac3f2e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53260915"
---
# <a name="walkthrough-step-6-access-the-azure-machine-learning-studio-web-service"></a>Etapa 6 do passo a passo: Acessar o serviço Web do Azure Machine Learning Studio

Esta é a última etapa do passo a passo, [Desenvolver uma solução de análise preditiva com o Azure Machine Learning](walkthrough-develop-predictive-solution.md)

1. [Criar um workspace do Machine Learning](walkthrough-1-create-ml-workspace.md)
2. [Carregar dados existentes](walkthrough-2-upload-data.md)
3. [Criar um novo teste](walkthrough-3-create-new-experiment.md)
4. [Treinar e avaliar os modelos](walkthrough-4-train-and-evaluate-models.md)
5. [Implantar o serviço Web](walkthrough-5-publish-web-service.md)
6. **Acessar o serviço Web**

- - -
Na etapa anterior neste passo a passo, implantamos um serviço Web que usa o nosso modelo de previsão de risco de crédito. Agora, os usuários podem enviar dados a ele e receber os resultados. 

O serviço Web é um serviço Web do Azure que pode receber e retornar dados usando as APIs REST de uma das duas maneiras:  

* **Solicitação/Resposta** – O usuário envia uma ou mais linhas de dados de crédito para o serviço usando um protocolo HTTP, e o serviço responde com um ou mais conjunto de resultados.
* **Execução em lote** - o usuário armazena uma ou mais linhas de dados de crédito em um blob do Azure e envia o local do blob ao serviço. O serviço pontua todas as linhas de dados no blob de entrada, armazena os resultados em outro blob e retorna a URL desse contêiner.  

A maneira mais rápida e fácil de acessar um serviço Web Clássico é por meio do [Aplicativo Web do Serviço de Solicitação-Resposta do Azure ML](https://azure.microsoft.com/marketplace/partners/microsoft/azuremlaspnettemplateforrrs/) ou do [Modelo do Aplicativo Web do Serviço de Execução em Lotes do Azure ML](https://azure.microsoft.com/marketplace/partners/microsoft/azuremlbeswebapptemplate/).

Esses modelos de aplicativo Web podem compilar um aplicativo Web personalizado que conhece os dados de entrada do seu serviço Web e o que ele retornará. Basta fornecer acesso aos dados e ao serviço Web, para que o modelo faça o resto.

Para obter mais informações sobre como usar modelos de aplicativos Web, consulte [Consumir um serviço Web do Azure Machine Learning com um modelo de aplicativo Web](consume-web-service-with-web-app-template.md).

Você também pode desenvolver um aplicativo personalizado para acessar o serviço Web usando código inicial fornecido nas linguagens de programação R, C# e Python.

Encontre detalhes mais completos em [Como consumir um serviço Web do Azure Machine Learning](consume-web-services.md).

