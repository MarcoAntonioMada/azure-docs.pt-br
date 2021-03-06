---
title: Recursos para o desenvolvimento de um data warehouse no Azure | Microsoft Docs
description: Conceitos de desenvolvimento, decisões de design, recomendações e técnicas de codificação para o SQL Data Warehouse.
services: sql-data-warehouse
author: kevinvngo
manager: craigg
ms.service: sql-data-warehouse
ms.topic: conceptual
ms.component: implement
ms.date: 08/29/2018
ms.author: kevinvngo
ms.reviewer: igorstan
ms.openlocfilehash: 5cb3b3b261bcb762187b165e297225080b0fee81
ms.sourcegitcommit: 1fb353cfca800e741678b200f23af6f31bd03e87
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43306051"
---
# <a name="design-decisions-and-coding-techniques-for-sql-data-warehouse"></a>Decisões de design e técnicas de codificação para o SQL Data Warehouse
Leia estes artigos sobre desenvolvimento para reconhecer melhor as principais decisões de design, recomendações e técnicas de codificação para SQL Data Warehouse.

## <a name="key-design-decisions"></a>Principais decisões de design
Os artigos a seguir destacam conceitos e decisões de design para desenvolver um data warehouse distribuído utilizando o SQL Data Warehouse:

* [conexões][connections]
* [simultaneidade][concurrency]
* [transações][transactions]
* [esquemas definidos pelo usuário][user-defined schemas]
* [distribuição de tabelas][table distribution]
* [índices da tabela][table indexes]
* [partições da tabela][table partitions]
* [CTAS][CTAS]
* [estatísticas][statistics]

## <a name="development-recommendations-and-coding-techniques"></a>Recomendações para o desenvolvimento e técnicas de codificação
Esses artigos destacam recomendações, dicas e técnicas de codificação específicas para o desenvolvimento do SQL Data Warehouse:

* [procedimentos armazenados][stored procedures]
* [rótulos][labels]
* [modos de exibição][views]
* [tabelas temporárias][temporary tables]
* [SQL dinâmico][dynamic SQL]
* [looping][looping]
* [agrupar por opções][group by options]
* [atribuição de variável][variable assignment]

## <a name="next-steps"></a>Próximas etapas
Para obter mais informações de referência, consulte [Instruções T-AQL do SQL Data Warehouse](sql-data-warehouse-reference-tsql-statements.md).

<!--Image references-->

<!--Article references-->
[concurrency]: ./resource-classes-for-workload-management.md
[connections]: ./sql-data-warehouse-connect-overview.md
[CTAS]: ./sql-data-warehouse-develop-ctas.md
[dynamic SQL]: ./sql-data-warehouse-develop-dynamic-sql.md
[group by options]: ./sql-data-warehouse-develop-group-by-options.md
[labels]: ./sql-data-warehouse-develop-label.md
[looping]: ./sql-data-warehouse-develop-loops.md
[statistics]: ./sql-data-warehouse-tables-statistics.md
[stored procedures]: ./sql-data-warehouse-develop-stored-procedures.md
[table distribution]: ./sql-data-warehouse-tables-distribute.md
[table indexes]: ./sql-data-warehouse-tables-index.md
[table partitions]: ./sql-data-warehouse-tables-partition.md
[temporary tables]: ./sql-data-warehouse-tables-temporary.md
[transactions]: ./sql-data-warehouse-develop-transactions.md
[user-defined schemas]: ./sql-data-warehouse-develop-user-defined-schemas.md
[variable assignment]: ./sql-data-warehouse-develop-variable-assignment.md
[views]: ./sql-data-warehouse-develop-views.md


<!--MSDN references-->
[renaming objects]: https://msdn.microsoft.com/library/mt631611.aspx

<!--Other Web references-->
