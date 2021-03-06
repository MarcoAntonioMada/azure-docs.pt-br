---
title: Personalizar as configurações de avaliação de Migrações para Azure | Microsoft Docs
description: Descreve como configurar e executar uma avaliação de migração de VMs VMware para o Azure usando o Planejador de Migrações para Azure
author: rayne-wiselman
ms.service: azure-migrate
ms.topic: article
ms.date: 10/30/2018
ms.author: raynew
ms.openlocfilehash: 2423c4fde177ab50552af580a60c7a15550e5586
ms.sourcegitcommit: 11d8ce8cd720a1ec6ca130e118489c6459e04114
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2018
ms.locfileid: "52840428"
---
# <a name="customize-an-assessment"></a>Personalizar uma avaliação

As [Migrações para Azure](migrate-overview.md) criam avaliações com configurações padrão. Depois de criar uma avaliação, você pode modificar essas configurações padrão usando as instruções neste artigo.


## <a name="edit-assessment-properties"></a>Editar propriedades de avaliação

1. Na página **Avaliações** do projeto de migração, selecione a avaliação e clique em **Editar propriedades**.
2. Personalize as propriedades de avaliação com base nos detalhes abaixo:

    **Configuração** | **Detalhes** | **Padrão**
    --- | --- | ---
    **Local de destino** | O local do Azure para o qual você deseja migrar.<br/><br/> Atualmente, as Migrações para Azure dão suporte a 30 regiões, incluindo Leste da Austrália, Sudeste da Austrália, Sul do Brasil, Canadá Central, Leste do Canadá, Índia Central, EUA Central, Leste da China, Norte da China, Ásia Oriental, Leste dos EUA, Alemanha Central, Nordeste da Alemanha, Leste dos EUA 2, Leste do Japão, Oeste do Japão, Coreia Central, Sul da Coreia, Centro-Norte dos EUA, Europa Setentrional, Centro-Sul dos EUA, Sudeste Asiático, Sul da Índia, Sul do Reino Unido, Oeste do Reino Unido, US Gov – Arizona, US Gov – Texas, US Gov – Virgínia, Centro-Oeste dos EUA, Europa Ocidental, Índia Ocidental, Oeste dos EUA e Oeste dos EUA 2. |  Oeste dos EUA 2 é o local padrão.
    **Tipo de armazenamento** | Você pode usar essa propriedade para especificar o tipo dos discos que deseja alocar no Azure. Para dimensionamento local, especifique o tipo de disco de destino como discos gerenciados Premium ou Standard. Para dimensionamento baseado em desempenho, especifique o tipo de disco de destino como discos gerenciados Automático, Premium ou Standard. Quando você especifica o tipo de armazenamento como automático, a recomendação de disco é feita com base nos dados de desempenho dos discos (IOPS e taxa de transferência). Por exemplo, para obter um [SLA de VM de instância única de 99,9%](https://azure.microsoft.com/support/legal/sla/virtual-machines/v1_8/), você talvez queira especificar o tipo de armazenamento como discos gerenciados Premium que garantam que todos os discos na avaliação sejam recomendados como discos gerenciados Premium. Observe que as Migrações para Azure são compatíveis apenas com discos gerenciados para avaliação de migração. | O valor padrão é discos gerenciados Premium (com o critério de dimensionamento *como dimensionamento local*).
    **Instâncias reservadas** |  Você também pode especificar se tem [instâncias reservadas](https://azure.microsoft.com/pricing/reserved-vm-instances/) no Azure, e as Migrações para Azure estimarão o custo adequadamente. As instâncias reservadas não são aplicáveis a regiões soberanas (Azure Governamental, Alemanha e China) e são aplicáveis somente à oferta Pagamento Conforme o Uso nas Migrações para Azure. | O valor padrão para essa propriedade é de 3 anos de instâncias reservadas.
    **Critério de dimensionamento** | O critério a ser usado pelas Migrações para Azure para redimensionar VMs para o Azure. Você pode fazer dimensionamento *com base no desempenho* ou dimensionar as VMs *como locais*, sem considerar o histórico de desempenho. | O dimensionamento com base no desempenho é a opção padrão.
    **Histórico de desempenho** | A duração a considerar para avaliar o desempenho das VMs. Essa propriedade só é aplicável quando o critério de dimensionamento é *dimensionamento com base no desempenho*. | O padrão é um dia.
    **Utilização de percentual** | O valor percentual da amostra de desempenho definido para ser considerado para o redimensionamento. Essa propriedade só é aplicável quando o critério de dimensionamento é *dimensionamento com base no desempenho*.  | O padrão é 95 por cento.
    **Série de VM** | Você pode especificar a série de VM que deseja considerar para o dimensionamento correto. Por exemplo, se você tiver um ambiente de produção que não pretende migrar para VMs da série A no Azure, poderá excluir a série A da lista ou da série e o dimensionamento correto será feito apenas na série selecionada. | Por padrão, todos as séries VM são selecionadas.
    **Fator de conforto** | As Migrações para Azure consideram um buffer (fator de conforto) durante a avaliação. Esse buffer é aplicado sobre os dados de utilização da máquina para VMs (CPU, memória, disco e rede). O fator de conforto considera problemas como uso sazonal, histórico curto de desempenho e aumento provável do uso futuro.<br/><br/> Por exemplo, uma VM com 10 núcleos e 20% de utilização normalmente resulta em uma VM de dois núcleos. No entanto, com um fator de conforto de 2.0x, o resultado é uma VM de quatro núcleos. | A configuração padrão é 1.3 x.
    **Oferta** | A [Oferta do Azure](https://azure.microsoft.com/support/legal/offer-details/) em que você está inscrito. | [Pré-pago](https://azure.microsoft.com/offers/ms-azr-0003p/) é o padrão.
    **Moeda** | Moeda de cobrança. | O padrão é dólares americanos.
    **Desconto (%)** | Qualquer desconto específico da assinatura  recebido por você sobre a oferta do Azure. | A configuração padrão é 0%.
    **Tempo de atividade da VM** | Se as VMs não estiverem em execução 24x7 no Azure, será possível especificar a duração da execução (número de dias por mês e número de horas por dia) e as estimativas de custo serão feitas adequadamente. | O valor padrão é 31 dias por mês e 24 horas por dia.
    **Benefício Híbrido do Azure** | Especifique se você tem a garantia do software e é qualificado para o [Benefício Híbrido do Azure](https://azure.microsoft.com/pricing/hybrid-use-benefit/). Se definido como Sim, os preços do Windows Azure são considerados para VMs do Windows. | O padrão é Sim.

3. Clique em **Salvar** para atualizar a avaliação.


## <a name="next-steps"></a>Próximas etapas

[Saiba mais](concepts-assessment-calculation.md) sobre como as avaliações são calculadas.
