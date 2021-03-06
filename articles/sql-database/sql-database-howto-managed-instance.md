---
title: Como configurar a Instância Gerenciada do Banco de Dados SQL do Azure | Microsoft Docs
description: Saiba como configurar e gerenciar a Instância Gerenciada do Banco de Dados SQL do Azure.
services: sql-database
ms.service: sql-database
ms.subservice: managed-instance
ms.custom: ''
ms.devlang: ''
ms.topic: howto
author: jovanpop-msft
ms.author: jovanpop
ms.reviewer: carlr
manager: craigg
ms.date: 12/14/2018
ms.openlocfilehash: 10a33ac09b5cfa588bef88e6c1587d67036b1aef
ms.sourcegitcommit: c2e61b62f218830dd9076d9abc1bbcb42180b3a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2018
ms.locfileid: "53439513"
---
# <a name="how-to-use-managed-instance"></a>Como usar a Instância Gerenciada

Nesta seção, é possível encontrar vários guias, scripts e explicações que podem ajudar você a gerenciar e configurar seu Banco de Dados SQL do Azure – Instância Gerenciada.

## <a name="migration"></a>Migração

- [Migrar para a Instância Gerenciada](sql-database-managed-instance-migrate.md) – saiba mais sobre o processo de migração recomendado e ferramentas para a migração para a Instância Gerenciada.

- [Migrar certificados TDE para a Instância Gerenciada](sql-database-managed-instance-migrate-tde-certificate.md) – se o seu banco de dados do SQL Server estiver protegido com a TDE (Transparent Data Encryption), será necessário migrar o certificado que a Instância Gerenciada pode usar para descriptografar o backup que deseja restaurar no Azure.

## <a name="network-configuration"></a>Configuração de rede

- [Determinar o tamanho da sub-rede da Instância Gerenciada](sql-database-managed-instance-determine-size-vnet-subnet.md) – a Instância Gerenciada é colocada em sub-redes dedicadas que não podem ser redimensionadas após adicionar os recursos. Portanto, você precisa calcular qual intervalo de IP de endereços seria necessário para a sub-rede dependendo do número e dos tipos de instâncias que você deseja implantar na sub-rede.
- [Criar nova rede virtual e sub-rede para a Instância Gerenciada](sql-database-managed-instance-create-vnet-subnet.md) – a rede virtual e a sub-rede do Azure em que você deseja implantar suas Instâncias Gerenciadas devem ser configuradas acordo com os [requisitos de rede descritos aqui](sql-database-managed-instance-connectivity-architecture.md#network-requirements). Neste guia, você pode encontrar a maneira mais fácil de criar sua nova rede virtual e sub-rede configuradas corretamente para Instâncias Gerenciadas.
- [Configurar a rede virtual e a sub-rede existentes para a Instância Gerenciada](sql-database-managed-instance-configure-vnet-subnet.md) – se deseja configurar sua rede virtual e sub-rede existentes para implantar as Instâncias Gerenciadas nelas, aqui você pode encontrar o script que verifica os [requisitos de rede](sql-database-managed-instance-connectivity-architecture.md#network-requirements) e fazer as configurações na sua sub-rede de acordo com eles.
- [Configurar DNS personalizado](sql-database-managed-instance-custom-dns.md) – você precisa configurar o DNS personalizado caso deseje acessar recursos externos nos domínios personalizados da sua Instância Gerenciada por meio de um servidor vinculado de perfis de email de banco de dados.
- [Sincronizar configurações de rede](sql-database-managed-instance-sync-network-configuration.md) – pode acontecer que, embora tenha [integrado seu aplicativo a uma Rede Virtual do Azure](../app-service/web-sites-integrate-with-vnet.md), não seja possível estabelecer a conexão com a Instância Gerenciada. Algo que você pode é tentar atualizar a configuração de rede para o plano de serviço.
- [Localizar o endereço IP do ponto de extremidade de gerenciamento](sql-database-managed-instance-find-management-endpoint-ip-address.md) – a Instância Gerenciada usa o ponto de extremidade público apenas para fins de gerenciamento. Você pode determinar o endereço IP do ponto de extremidade de gerenciamento usando o script descrito aqui.
- [Verificar a proteção de firewall interno](sql-database-managed-instance-management-endpoint-verify-built-in-firewall.md) – a Instância Gerenciada é protegida com o firewall interno que permite o tráfego apenas nas portas necessárias. Você pode verificar as regras do firewall interno usando o script descrito neste guia.
- [Conectar aplicativos](sql-database-managed-instance-connect-app.md) – a Instância Gerenciada é colocada em sua própria rede virtual privada do Azure com um endereço IP privado. Saiba mais sobre padrões diferentes para conectar os aplicativos à sua Instância Gerenciada.

## <a name="feature-configuration"></a>Configuração de recurso

- [Replicação transacional](replication-with-sql-database-managed-instance.md) permite que você replique seus dados entre Instâncias Gerenciadas ou do SQL Server local para a Instância Gerenciada e vice-versa. Encontre mais informações sobre como usar e configurar a replicação de transação neste guia.
- [Configurar a detecção de ameaças](sql-database-managed-instance-threat-detection.md) – a [detecção de ameaças](sql-database-threat-detection-overview.md) é um recurso interno do Banco de Dados SQL do Azure que detecta vários ataques potenciais, como Injeção de SQL ou o acesso de locais suspeitos. Neste guia, você pode aprender como habilitar e configurar a [detecção de ameaças](sql-database-threat-detection-overview.md) para a Instância Gerenciada.

## <a name="next-steps"></a>Próximas etapas
- Saiba mais sobre [Guias de instruções em um banco de dados individual](sql-database-howto-single-database.md)