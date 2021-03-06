---
title: Solucionar problemas comuns do Serviço do Azure Kubernetes
description: Aprenda a solucionar problemas comuns ao usar o Serviço de Kubernetes do Azure (AKS)
services: container-service
author: sauryadas
ms.service: container-service
ms.topic: troubleshooting
ms.date: 08/13/2018
ms.author: saudas
ms.openlocfilehash: fd3d1c464c6f2d4cbecd715db0689581ca141769
ms.sourcegitcommit: e68df5b9c04b11c8f24d616f4e687fe4e773253c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53654063"
---
# <a name="aks-troubleshooting"></a>Solução de problemas do AKS

Quando você cria ou gerencia clusters do Serviço de Kubernetes do Azure (AKS), você pode ocasionalmente encontrar problemas. Este artigo detalha alguns problemas comuns e etapas de solução de problemas.

## <a name="in-general-where-do-i-find-information-about-debugging-kubernetes-problems"></a>Em geral, onde encontro informações sobre como depurar problemas do Kubernetes?

Experimente o [guia oficial para solucionar problemas de clusters de Kubernetes](https://kubernetes.io/docs/tasks/debug-application-cluster/troubleshooting/).
Há também um [guia de solução de problemas](https://github.com/feiskyer/kubernetes-handbook/blob/master/en/troubleshooting/index.md) publicado por um engenheiro da Microsoft sobre solução de problemas de pods, nós, clusters e outros recursos.

## <a name="im-getting-a-quota-exceeded-error-during-creation-or-upgrade-what-should-i-do"></a>Estou recebendo um erro de “cota excedida” durante a criação ou atualização. O que devo fazer? 

Você precisa [solicitar núcleos](https://docs.microsoft.com/azure/azure-supportability/resource-manager-core-quotas-request).

## <a name="what-is-the-maximum-pods-per-node-setting-for-aks"></a>Qual é a configuração máxima de pods por nó para o AKS?

A configuração máxima de pods por nó é 30 por padrão, se você implantar um cluster AKS no portal do Azure.
A configuração máxima de pods por nó é 110 por padrão, se você implantar um cluster AKS na CLI do Azure. (Verifique se está usando a versão mais recente da CLI do Azure). Essa configuração padrão pode ser alterada usando o sinalizador `–-max-pods` no comando `az aks create`.

## <a name="im-getting-an-insufficientsubnetsize-error-while-deploying-an-aks-cluster-with-advanced-networking-what-should-i-do"></a>Estou recebendo o erro “insuficienteSubnetSize” ao implantar um cluster AKS com a rede avançada. O que devo fazer?

A opção de Rede Virtual personalizada do Azure para a rede durante a criação do AKS, a Interface de Rede de Contêiner do Azure (CNI) é usada para gerenciamento de endereço IP (IPAM). O número de nós em um cluster AKS pode estar em qualquer lugar entre 1 e 100. Com base na seção anterior, o tamanho da sub-rede deve ser maior que o produto do número de nós e o máximo de pods por nó. A relação pode ser expressa dessa forma: tamanho da sub-rede > número de nós no cluster * máximo pods por nó.

## <a name="my-pod-is-stuck-in-crashloopbackoff-mode-what-should-i-do"></a>Meu pod está preso no modo CrashLoopBackOff. O que devo fazer?

Pode haver vários motivos para o pod trave nesse modo. Você pode examinar:

* O próprio pod, usando `kubectl describe pod <pod-name>`.
* Os logs, usando `kubectl log <pod-name>`.

Para obter mais informações sobre como solucionar problemas de pod, consulte [Depurar aplicativos](https://kubernetes.io/docs/tasks/debug-application-cluster/debug-application/#debugging-pods).

## <a name="im-trying-to-enable-rbac-on-an-existing-cluster-how-can-i-do-that"></a>Estou tentando habilitar RBAC em um cluster existente. Como posso fazer isso?

Infelizmente, a ativação do controle de acesso baseado em função (RBAC) em clusters existentes não é suportada no momento. Você deve explicitamente criar novos clusters. Se você usar a CLI, o RBAC é habilitado por padrão. Se você usar o portal do AKS, um botão de alternância para habilitar o RBAC está disponível no fluxo de trabalho de criação.

## <a name="i-created-a-cluster-with-rbac-enabled-by-using-either-the-azure-cli-with-defaults-or-the-azure-portal-and-now-i-see-many-warnings-on-the-kubernetes-dashboard-the-dashboard-used-to-work-without-any-warnings-what-should-i-do"></a>Eu criei um cluster com o RBAC habilitado usando a CLI do Azure com padrões ou o portal do Azure, agora vejo vários avisos no painel do Kubernetes. O painel costumava trabalhar sem nenhum aviso. O que devo fazer?

O motivo para os avisos no painel é que agora o cluster está habilitado com o RBAC e o acesso a ele foi desabilitado por padrão. Em geral, essa abordagem é uma boa prática, já que a exposição padrão do painel a todos os usuários do cluster pode levar a ameaças de segurança. Se você ainda quiser ativar o painel, siga os passos nesta [postagem de blog](https://pascalnaber.wordpress.com/2018/06/17/access-dashboard-on-aks-with-rbac-enabled/).

## <a name="i-cant-connect-to-the-dashboard-what-should-i-do"></a>Não consigo conectar-me ao painel. O que devo fazer?

A maneira mais fácil de acessar seu serviço fora do cluster é executar `kubectl proxy`, que enviará solicitações de proxy para sua porta local 8001 ao servidor Kubernetes API. A partir daí, o servidor de API pode usar um proxy ao seu serviço: `http://localhost:8001/api/v1/namespaces/kube-system/services/kubernetes-dashboard/proxy/#!/node?namespace=default`.

Se você não vir o painel do Kubernetes, verifique se o pod `kube-proxy` está em execução no namespace `kube-system`. Se não estiver em estado de execução, exclua o pod e ele será reiniciado.

## <a name="i-cant-get-logs-by-using-kubectl-logs-or-i-cant-connect-to-the-api-server-im-getting-error-from-server-error-dialing-backend-dial-tcp-what-should-i-do"></a>Não consigo obter os logs, usando kubectl logs ou não é possível conectar-se ao servidor de API. Estou recebendo o "Erro do servidor: erro de discagem back-end: discar tcp..." O que devo fazer?

Certifique-se de que o grupo de segurança de rede (NSG) padrão não seja modificado e a porta 22 esteja aberta para conexão com o servidor da API. Verifique se o pod `tunnelfront` está em execução no namespace `kube-system`. Se não estiver, force a exclusão do pod e ele será reiniciado.

## <a name="im-trying-to-upgrade-or-scale-and-am-getting-a-message-changing-property-imagereference-is-not-allowed-error--how-do-i-fix-this-problem"></a>Eu estou tentando atualizar ou dimensionar e estou recebendo erro "mensagem: Não é permitido alterar a propriedade 'imageReference'".  Como faço para corrigir esse problema?

Você pode estar recebendo este erro porque modificou as tags nos nós do agente dentro do cluster do AKS. Modificar e excluir tags e outras propriedades de recursos no grupo de recursos MC_ * pode levar a resultados inesperados. Modificar os recursos sob o grupo MC_ * no cluster do AKS quebra o objetivo de nível de serviço (SLO).

## <a name="how-do-i-renew-the-service-principal-secret-on-my-aks-cluster"></a>Como faço para renovar o segredo da entidade de serviço em meu cluster do AKS?

Por padrão, os clusters do AKS são criados com uma entidade de serviço que tem um tempo de término de um ano. Conforme você se aproxima da data do término, pode redefinir as credenciais para estender a entidade de serviço por um período adicional.

O exemplo a seguir executa estas etapas:

1. Obtém a ID de entidade de serviço do seu cluster usando o comando [az aks show](/cli/azure/aks#az-aks-show).
1. Lista o segredo do cliente da entidade de serviço usando [az ad sp credential list](/cli/azure/ad/sp/credential#az-ad-sp-credential-list).
1. Estende a entidade de serviço por mais um ano usando o comando [az ad sp credential-reset](/cli/azure/ad/sp/credential#az-ad-sp-credential-reset). O segredo do cliente da entidade de serviço deve permanecer o mesmo para o cluster do AKS ser executado corretamente.

```azurecli
# Get the service principal ID of your AKS cluster.
sp_id=$(az aks show -g myResourceGroup -n myAKSCluster \
    --query servicePrincipalProfile.clientId -o tsv)

# Get the existing service principal client secret.
key_secret=$(az ad sp credential list --id $sp_id --query [].keyId -o tsv)

# Reset the credentials for your AKS service principal and extend for one year.
az ad sp credential reset \
    --name $sp_id \
    --password $key_secret \
    --years 1
```
