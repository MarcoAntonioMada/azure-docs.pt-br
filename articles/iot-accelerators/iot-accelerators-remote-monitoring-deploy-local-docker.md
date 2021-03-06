---
title: Implante a solução de monitoramento remoto localmente – Docker - Azure | Microsoft Docs
description: Este guia de instruções mostra como implantar o acelerador de solução de monitoramento remoto no computador local usando o Docker para teste e desenvolvimento.
author: avneet723
manager: hegate
ms.author: avneet723
ms.service: iot-accelerators
services: iot-accelerators
ms.date: 10/25/2018
ms.topic: conceptual
ms.openlocfilehash: cf3c30d33e618ae3fd9d4ad942c77d211a414e82
ms.sourcegitcommit: 4eeeb520acf8b2419bcc73d8fcc81a075b81663a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53601144"
---
# <a name="deploy-the-remote-monitoring-solution-accelerator-locally---docker"></a>Implante o acelerador de solução de Monitoramento Remoto localmente - Docker

[!INCLUDE [iot-accelerators-selector-local](../../includes/iot-accelerators-selector-local.md)]

Este artigo mostra como implantar o acelerador de solução de Monitoramento Remoto no computador local para teste e desenvolvimento. Você aprenderá como implantar os microsserviços nos contêineres locais do Docker. Uma implantação de microsserviços local usa os seguintes serviços de nuvem: Hub IoT, Cosmos DB, Azure Stream Analytics e serviços na nuvem do Azure Time Series Insights.

Se você quiser executar o acelerador de solução de Monitoramento Remoto em um IDE em seu computador local, consulte [Implantar o acelerador de solução de Monitoramento Remoto localmente – Visual Studio](iot-accelerators-remote-monitoring-deploy-local.md).

## <a name="prerequisites"></a>Pré-requisitos

Para implantar os serviços do Azure usados pelo acelerador de solução de Monitoramento Remoto, você precisará de uma assinatura ativa do Azure.

Se você não tiver uma conta, poderá criar uma conta de avaliação gratuita em apenas alguns minutos. Para obter detalhes, consulte [Avaliação gratuita do Azure](https://azure.microsoft.com/pricing/free-trial/).

### <a name="machine-setup"></a>Configuração do computador

Para concluir a implantação local, você precisa ter as seguintes ferramentas instaladas no computador de desenvolvimento local:

* [Git](https://git-scm.com/)
* [Docker](https://www.docker.com)
* [Visual Studio](https://visualstudio.microsoft.com/)
* [Node.js v8](https://nodejs.org/) – este software é um pré-requisito para a CLI do PCS que os scripts usam para criar recursos do Azure. Não use o Node.js v10.

> [!NOTE]
> Essas ferramentas estão disponíveis em muitas plataformas, inclusive Windows, Linux e iOS.

[!INCLUDE [iot-accelerators-local-setup](../../includes/iot-accelerators-local-setup.md)]

## <a name="run-the-microservices-in-docker"></a>Executar os microsserviços no Docker

Abra um novo prompt de comando para garantir que tenha acesso às variáveis de ambiente definidas pelo script **start.cmd**. No Windows, você pode verificar que as variáveis de ambiente são definidas executando o seguinte comando:

```cmd
set PCS
```

O comando mostra todas as variáveis de ambiente definidas pelo script **start.cmd**.

Certifique-se de que o Docker está em execução no computador local.

Os microsserviços em execução nos contêineres de Docker locais precisam acessar os serviços de nuvem do Azure. Você pode testar a conectividade de internet do seu ambiente do Docker usando o seguinte comando para executar o ping de um endereço de internet de dentro de um contêiner:

```cmd/sh
docker run --rm -ti library/alpine ping google.com
```

Para executar o acelerador de solução, navegue até a pasta **services\\scripts\\local** no seu ambiente de linha de comando e execute o seguinte comando:

```cmd/sh
docker-compose up
```

Na primeira vez que você executar esse comando, o Docker baixa as imagens de microsserviço do hub do Docker para criar os contêineres localmente. Nas execuções seguintes, o Docker executa os contêineres imediatamente.

> [!TIP]
> Frequentemente, a Microsoft publica novas imagens do Docker com novas funcionalidades. Você pode usar o conjunto de comandos a seguir para limpar os contêineres e imagens correspondentes do Docker antes de efetuar pull dos mais recentes:

```cmd/sh
docker list
docker rm <list_of_containers>
docker rmi <list_of_images>
```

Você pode usar um shell separado para exibir os logs do contêiner. Primeiro, encontre a ID de contêiner usando o comando `docker ps`. Em seguida, use `docker logs {container-id} --tail 1000` para exibir as últimas 1000 entradas para o contêiner especificado.

### <a name="start-the-stream-analytics-job"></a>Iniciar o trabalho do Stream Analytics

Execute estas etapas para iniciar o trabalho do Stream Analytics:

1. Navegue até o [Portal do Azure](https://portal.azure.com).
1. Navegue até o **Grupo de recursos** criado para sua solução. O nome do grupo de recursos é o nome da solução que você escolheu quando executou o script **start.cmd**.
1. Clique no **trabalho do Stream Analytics** na lista de recursos.
1. Na página **visão geral** do trabalho do Stream Analytics, clique no botão **Iniciar**. Depois, clique em **Iniciar** para iniciar o trabalho agora.

### <a name="connect-to-the-dashboard"></a>Conectar-se ao painel

Para acessar o painel da solução de Monitoramento Remoto, navegue até [http://localhost:8080](http://localhost:8080) em seu navegador. Agora você pode usar a IU da Web e os microsserviços de locais.

## <a name="clean-up"></a>Limpar

Para evitar encargos desnecessários, quando terminar o teste, remova os serviços de nuvem de sua assinatura do Azure. Para remover os serviços, navegue até o [portal do Azure](https://ms.portal.azure.com) e exclua o grupo de recursos que o script **start.cmd** criou.

Use o comando `docker-compose down --rmi all` para remover as imagens do Docker e liberar espaço no seu computador local. Você também pode excluir a cópia local do repositório de Monitoramento Remoto criada quando você clonou o código-fonte do GitHub.

## <a name="next-steps"></a>Próximas etapas

Agora que você implantou a solução de monitoramento remoto, a próxima etapa é [explorar os recursos do painel de solução](quickstart-remote-monitoring-deploy.md).
