---
title: Usar Apache Hive e Área de Trabalho Remota no HDInsight - Azure
description: Aprenda a conectar-se a um cluster do Hadoop no HDInsight usando a área de trabalho remota e então executar consultas Hive usando a Interface de Linha de Comando do Hive.
services: hdinsight
author: hrasheed-msft
ms.reviewer: jasonh
ms.service: hdinsight
ms.topic: conceptual
ms.date: 01/12/2017
ms.author: hrasheed
ROBOTS: NOINDEX
ms.openlocfilehash: 6e0641f2d9427133f951ef63720b4efdac4defe5
ms.sourcegitcommit: c37122644eab1cc739d735077cf971edb6d428fe
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53409047"
---
# <a name="use-apache-hive-with-apache-hadoop-on-hdinsight-with-remote-desktop"></a>Usar Apache Hive com Apache Hadoop no HDInsight com Área de Trabalho Remota
[!INCLUDE [hive-selector](../../../includes/hdinsight-selector-use-hive.md)]

Neste artigo, você aprenderá como se conectar a um cluster HDInsight usando a Área de Trabalho Remota e então executar consultas usando a CLI (Interface de Linha de Comando) do Apache Hive.

> [!IMPORTANT]  
> A Área de Trabalho Remota está disponível somente em clusters HDInsight que usam o Windows como o sistema operacional. O Linux é o único sistema operacional usado no HDInsight versão 3.4 ou superior. Para obter mais informações, confira [baixa do HDInsight no Windows](../hdinsight-component-versioning.md#hdinsight-windows-retirement).
>
> No caso do HDInsight 3.4 ou superior, confira [Usar o Apache Hive com o HDInsight e o Beeline](apache-hadoop-use-hive-beeline.md) para obter informações sobre como executar consultas do Hive diretamente no cluster de uma linha de comando.

## <a id="prereq"></a>Pré-requisitos
Para concluir as etapas neste artigo, você precisará do seguinte:

* Um cluster HDInsight baseado em Windows (Hadoop no HDInsight)
* Um computador cliente executando o Windows 7, Windows 8 ou Windows 10

## <a id="connect"></a>Conectar com a área de trabalho remota
Habilite a área de trabalho remota para o cluster HDInsight e conecte-se a ele seguindo as instruções em [Conectar aos clusters HDInsight usando o RDP](../hdinsight-administer-use-management-portal.md#connect-to-clusters-using-rdp).

## <a id="hive"></a>Usar o comando do Hive
Quando conectado à área de trabalho para o cluster HDInsight, use as etapas a seguir para trabalhar com o Hive:

1. Na área de trabalho do HDInsight, inicie a **Linha de Comando do Hadoop**.
2. Digite o seguinte comando para iniciar a CLI do Hive:

        %hive_home%\bin\hive

    Depois de iniciar a CLI, você verá o prompt da CLI do Hive: `hive>`.
3. Usando a CLI, digite as instruções a seguir para criar uma nova tabela chamada **log4jLogs** usando os dados de exemplo:

        set hive.execution.engine=tez;
        DROP TABLE log4jLogs;
        CREATE EXTERNAL TABLE log4jLogs (t1 string, t2 string, t3 string, t4 string, t5 string, t6 string, t7 string)
        ROW FORMAT DELIMITED FIELDS TERMINATED BY ' '
        STORED AS TEXTFILE LOCATION 'wasb:///example/data/';
        SELECT t4 AS sev, COUNT(*) AS count FROM log4jLogs WHERE t4 = '[ERROR]' AND INPUT__FILE__NAME LIKE '%.log' GROUP BY t4;

    Essas instruções executam as seguintes ações:

   * **DROP TABLE**: Exclui a tabela e o arquivo de dados, caso a tabela já exista.
   * **CREATE EXTERNAL TABLE**: Cria uma nova tabela ‘externa’ no Hive. As tabelas externas armazenam apenas a definição da tabela no Hive (os dados são deixados no local original).

     > [!NOTE]  
     > As tabelas externas devem ser usadas quando você espera que os dados subjacentes sejam atualizados por uma fonte externa (como um processo automático de carregamento de dados) ou por outra operação MapReduce, mas você sempre quer que as consultas Hive utilizem os dados mais recentes.
     >
     > Remover uma tabela externa **não** exclui os dados, somente a definição de tabela.
     >
     >
   * **FORMATO DO PIN**: Informa ao Hive como os dados são formatados. Nesse caso, os campos em cada log são separados por um espaço.
   * **ARMAZENADO COMO ARQUIVO DE TEXTO LOCAL**: Informa ao Hive o local em que os dados são armazenados (o diretório de exemplos/dados) e que estão armazenados como texto.
   * **SELECIONAR**: Seleciona uma contagem de todas as linhas em que a coluna **t4** contém o valor **[ERROR]**. Isso deve retornar um valor de **3** , já que existem três linhas que contêm esse valor.
   * **INPUT__FILE__NAME LIKE '%.log'** - informa ao Hive que só devemos retornar dados de arquivos que terminam em .log. Isso restringe a pesquisa ao arquivo sample.log que contém os dados e impede que ela retorne dados de outros arquivos de dados de exemplo que não correspondem ao esquema que definimos.
4. Use as instruções a seguir para criar uma nova tabela "interna" chamada **errorLogs**:

        CREATE TABLE IF NOT EXISTS errorLogs (t1 string, t2 string, t3 string, t4 string, t5 string, t6 string, t7 string) STORED AS ORC;
        INSERT OVERWRITE TABLE errorLogs SELECT t1, t2, t3, t4, t5, t6, t7 FROM log4jLogs WHERE t4 = '[ERROR]' AND INPUT__FILE__NAME LIKE '%.log';

    Essas instruções executam as seguintes ações:

   * **CRIAR TABELA SE NÃO EXISTE**: Cria uma tabela, se ela ainda não existir. Já que a palavra-chave **EXTERNAL** não é utilizada, essa é uma tabela interna, armazenada no depósito de dados do Hive e gerenciada totalmente pelo Hive.

     > [!NOTE]  
     > Diferentemente de tabelas **EXTERNAS** , o descarte de uma tabela interna excluirá também os dados subjacentes.
     >
     >
   * **ARMAZENADO COMO ORC**: Armazena os dados no formato Colunar de linha otimizado (ORC). Esse é um formato altamente otimizado e eficiente para o armazenamento de dados do Hive.
   * **INSERT OVERWRITE ... SELECT**: Seleciona linhas da tabela **log4jLogs** que contêm **[ERROR]** e insere os dados na tabela **errorLogs**.

     Para verificar se apenas as linhas que contêm **[ERROR]** na coluna t4 foram armazenadas na tabela **errorLogs**, use a seguinte instrução para retornar todas as linhas de **errorLogs**:

       SELECT * de errorLogs;

     Três linhas de dados devem ser devolvidas, todas contendo **[ERROR]** na coluna t4.

## <a id="summary"></a>Resumo
Como você pode ver, o comando do Hive fornece uma maneira fácil de executar consultas Hive interativamente em um cluster HDInsight, monitorar o status do trabalho e recuperar a saída.

## <a id="nextsteps"></a>Próximas etapas
Para obter informações gerais sobre o Hive no HDInsight:

* [Use o Apache Hive com o Apache Hadoop no HDInsight](hdinsight-use-hive.md)

Para obter informações sobre outros modos possíveis de trabalhar com Hadoop no HDInsight:

* [Use o Apache Pig com o Apache Hadoop no HDInsight](hdinsight-use-pig.md)
* [Usar o MapReduce com o Apache Hadoop no HDInsight](hdinsight-use-mapreduce.md)

Se você estiver usando o Tez com o Hive, consulte os seguintes documentos para as informações de depuração:

* [Usar a interface do usuário do Apache Tez no HDInsight baseado no Windows](../hdinsight-debug-tez-ui.md)
* [Usar a exibição de Apache Ambari Tez no HDInsight baseado no Linux](../hdinsight-debug-ambari-tez-view.md)

[1]:apache-hadoop-visual-studio-tools-get-started.md

[azure-purchase-options]: https://azure.microsoft.com/pricing/purchase-options/
[azure-member-offers]: https://azure.microsoft.com/pricing/member-offers/
[azure-free-trial]: https://azure.microsoft.com/pricing/free-trial/

[apache-tez]: https://tez.apache.org
[apache-hive]: https://hive.apache.org/
[apache-log4j]: https://en.wikipedia.org/wiki/Log4j
[hive-on-tez-wiki]: https://cwiki.apache.org/confluence/display/Hive/Hive+on+Tez
[import-to-excel]: https://azure.microsoft.com/documentation/articles/hdinsight-connect-excel-power-query/


[hdinsight-use-oozie]: hdinsight-use-oozie.md
[hdinsight-analyze-flight-data]: hdinsight-analyze-flight-delay-data.md





[hdinsight-provision]: hdinsight-provision-clusters.md
[hdinsight-submit-jobs]:submit-apache-hadoop-jobs-programmatically.md
[hdinsight-upload-data]: hdinsight-upload-data.md


[Powershell-install-configure]: /powershell/azureps-cmdlets-docs
[powershell-here-strings]: https://technet.microsoft.com/library/ee692792.aspx
