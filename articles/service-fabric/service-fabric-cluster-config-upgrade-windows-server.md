---
title: Atualizar a configuração de um cluster autônomo do Service Fabric do Azure | Microsoft Docs
description: Aprenda a atualizar a configuração que executa um cluster autônomo do Service Fabric.
services: service-fabric
documentationcenter: .net
author: dkkapur
manager: timlt
editor: ''
ms.assetid: 66296cc6-9524-4c6a-b0a6-57c253bdf67e
ms.service: service-fabric
ms.devlang: dotnet
ms.topic: conceptual
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 11/09/2018
ms.author: dekapur
ms.openlocfilehash: 88846845f1f8ffc71fb193e134a18ec38f619141
ms.sourcegitcommit: 7804131dbe9599f7f7afa59cacc2babd19e1e4b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2018
ms.locfileid: "51857871"
---
# <a name="upgrade-the-configuration-of-a-standalone-cluster"></a>Atualize a configuração de um cluster independente 

Para qualquer sistema moderno, a capacidade de atualização é fundamental para o sucesso de seu produto a longo prazo. Um cluster do Azure Service Fabric é um recurso que pertence a você. Este artigo descreve como atualizar as definições de configuração do cluster autônomo do Service Fabric.

## <a name="customize-cluster-settings-in-the-clusterconfigjson-file"></a>Personalizar configurações de cluster no arquivo ClusterConfig.json
Os clusters independentes são configurados por meio do arquivo *ClusterConfig.json*. Para saber mais sobre as diferentes configurações, consulte [Definições de configuração para um cluster autônomo do Windows](service-fabric-cluster-manifest.md).

Adicionar, atualizar ou remover as configurações na `fabricSettings` seção sob o [propriedades do Cluster](./service-fabric-cluster-manifest.md#cluster-properties) seção *Clusterconfig*. 

Por exemplo, o JSON a seguir adiciona uma nova configuração *MaxDiskQuotaInMB* para a *seção de diagnóstico*  em `fabricSettings`:

```json
      {
        "name": "Diagnostics",
        "parameters": [
          {
            "name": "MaxDiskQuotaInMB",
            "value": "65536"
          }
        ]
      }
```

Depois de modificar as configurações no arquivo ClusterConfig.json, [teste a configuração do cluster](#test-the-cluster-configuration) e, em seguida, [atualize a configuração do cluster](#upgrade-the-cluster-configuration) para aplicar as configurações ao cluster. 

## <a name="test-the-cluster-configuration"></a>Testar a configuração de cluster
Antes de iniciar a atualização de configuração, você pode testar seu novo JSON de configuração de cluster executando o seguinte script do PowerShell no pacote autônomo:

```powershell
TestConfiguration.ps1 -ClusterConfigFilePath <Path to the new Configuration File> -OldClusterConfigFilePath <Path to the old Configuration File>
```

Ou use este script:

```powershell
TestConfiguration.ps1 -ClusterConfigFilePath <Path to the new Configuration File> -OldClusterConfigFilePath <Path to the old Configuration File> -FabricRuntimePackagePath <Path to the .cab file which you want to test the configuration against>
```

Algumas configurações não podem ser atualizadas, como pontos de extremidade, nome do cluster, nó IP, etc. O novo JSON de configuração do cluster contra é testado com relação ao antigo e gera erros na janela do PowerShell se houver qualquer problema.

## <a name="upgrade-the-cluster-configuration"></a>Atualizar a configuração do cluster
Para atualizar a configuração do cluster, execute o comando [Start-ServiceFabricClusterConfigurationUpgrade](https://docs.microsoft.com/powershell/module/servicefabric/start-servicefabricclusterconfigurationupgrade). A atualização de configuração é processada domínio de atualização por domínio de atualização.

```powershell
Start-ServiceFabricClusterConfigurationUpgrade -ClusterConfigPath <Path to Configuration File>
```

## <a name="upgrade-cluster-certificate-configuration"></a>Atualizar configuração de certificado do cluster
Um certificado de cluster é usado para autenticação entre os nós de cluster. A substituição do certificado deve ser executada com muito cuidado, pois a falha bloqueia a comunicação entre os nós de cluster.

Há suporte para quatro opções:  

* Atualização de um certificado: o caminho de atualização é Certificado A (Primário)-> Certificado B (Primário)-> Certificado C (Primário)->....

* Atualização de dois certificados: o caminho de atualização é Certificado A (Primário) - > Certificado A (Primário) e B (Secundário) -> Certificado B (Primário) -> Certificado B (Primário) e C (Secundário) -> Certificado C (Primário)->....

* Atualização do tipo de certificado: configuração de certificados com base em CommonName configuração <-> com base em impressão digital do certificado. Por exemplo, impressão digital do certificado (primária) e a impressão digital B (secundários) -> certificado CommonName C.

* Atualização da impressão digital do emissor do certificado: o caminho de atualização é Certificado CN=A,IssuerThumbprint=IT1 (Principal) -> Certificado CN=A,IssuerThumbprint=IT1,IT2 (Principal) -> Certificado CN=A,IssuerThumbprint=IT2 (Principal).


## <a name="next-steps"></a>Próximas etapas
* Saiba como personalizar algumas das [configurações de cluster do Service Fabric](service-fabric-cluster-fabric-settings.md).
* Saiba como [reduzir e escalar horizontalmente seu cluster](service-fabric-cluster-scale-up-down.md).
* Saiba mais sobre [atualizações de aplicativo](service-fabric-application-upgrade.md).

<!--Image references-->
[getfabversions]: ./media/service-fabric-cluster-upgrade-windows-server/getfabversions.PNG
