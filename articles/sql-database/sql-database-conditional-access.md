---
title: Acesso Condicional – Banco de Dados SQL do Azure e Data Warehouse | Microsoft Doc
description: Saiba como configurar o Acesso Condicional para o Banco de Dados SQL do Azure e o Data Warehouse.
services: sql-database
ms.service: sql-database
ms.subservice: security
ms.custom: sql-data-warehouse
ms.devlang: ''
ms.topic: conceptual
author: GithubMirek
ms.author: mireks
ms.reviewer: vanto
manager: craigg
ms.date: 04/01/2018
ms.openlocfilehash: e7386e2f926132f5657bdb17011dafe1e1c7b101
ms.sourcegitcommit: cc4fdd6f0f12b44c244abc7f6bc4b181a2d05302
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47063074"
---
# <a name="conditional-access-mfa-with-azure-sql-database-and-data-warehouse"></a>Acesso Condicional (MFA) com o Banco de Dados SQL do Azure e o Data Warehouse  

O [Banco de Dados SQL](sql-database-technical-overview.md) do Azure e o [SQL Data Warehouse](../sql-data-warehouse/sql-data-warehouse-overview-what-is.md) dão suporte ao Acesso Condicional da Microsoft. 

> [!NOTE]
> Este tópico aplica-se ao servidor SQL do Azure e aos bancos de dados SQL e SQL Data Warehouse criados no servidor do SQL do Azure. Para simplificar, o banco de dados SQL é usado quando se refere ao Banco de Dados SQL e ao SQL Data Warehouse.

As próximas etapas mostram como configurar o Banco de Dados SQL para impor uma política de Acesso Condicional.  

## <a name="prerequisites"></a>Pré-requisitos  
- Você deve configurar o Banco de Dados SQL ou o SQL Data Warehouse para dar suporte à autenticação do Azure Active Directory. Para obter etapas específicas, consulte [Configurar e gerenciar a autenticação do Azure Active Directory com o Banco de Dados SQL ou o SQL Data Warehouse](sql-database-aad-authentication-configure.md).  
- Quando a autenticação multifator estiver habilitada, você deverá se conectar com uma ferramenta com suporte, como o último SSMS. Para obter mais informações, consulte [Configurar a autenticação multifator do Banco de Dados SQL do Azure para o SQL Server Management Studio](sql-database-ssms-mfa-authentication-configure.md).  

## <a name="configure-ca-for-azure-sql-dbdw"></a>Configurar a AC para o BD SQL do Azure/DW  
1.  Entre no Portal, selecione **Azure Active Directory** e, em seguida, selecione **Acesso condicional**. Para obter mais informações, consulte [Referência técnica do Acesso Condicional ao Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference).  
  ![folha do acesso condicional](./media/sql-database-conditional-access/conditional-access-blade.png) 
     
2.  Na folha **Políticas de Acesso Condicional**, clique em **Nova política**, forneça um nome e, em seguida, clique em **Configurar regras**.  
3.  Em **Atribuições**, selecione **Usuários e grupos**, marque a opção **Selecionar usuários e grupos** e, em seguida, selecione o usuário ou o grupo para o acesso condicional. Clique em **Selecionar** e, em seguida, em **Concluído** para aceitar a seleção.  
  ![selecionar usuários e grupos](./media/sql-database-conditional-access/select-users-and-groups.png)  

4.  Selecione **Aplicativos na nuvem** e clique em **Selecionar aplicativos**. Você verá todos os aplicativos disponíveis para o acesso condicional. Selecione **Banco de Dados SQL do Azure**, na parte inferior clique em **Selecionar** e, em seguida, clique em **Concluído**.  
  ![selecionar Banco de Dados SQL](./media/sql-database-conditional-access/select-sql-database.png)  
  Se você não encontrar o **Banco de Dados SQL do Azure** listado na terceira captura de tela a seguir, conclua as seguintes etapas:   
  - Entre na instância do BD SQL do Azure/DW usando o SSMS com uma conta do administrador do AAD.  
  - Execute `CREATE USER [user@yourtenant.com] FROM EXTERNAL PROVIDER`.  
  - Entre no AAD e verifique se o Banco de Dados SQL do Azure e o Data Warehouse estão listados nos aplicativos no AAD.  

5.  Selecione **Controles de acesso**, selecione **Conceder** e, em seguida, marque a política que você deseja aplicar. Para este exemplo, selecionamos **Exigir autenticação multifator**.  
  ![selecionar conceder acesso](./media/sql-database-conditional-access/grant-access.png)  

## <a name="summary"></a>Resumo  
O aplicativo selecionado (Banco de Dados SQL do Azure), que permite se conectar ao BD SQL do Azure/DW usando o Azure AD Premium, agora impõe a política de Acesso Condicional selecionada, **Exigir autenticação multifator.**  
Em caso de dúvidas sobre o Banco de Dados SQL do Azure e o Data Warehouse com relação à autenticação multifator, contate MFAforSQLDB@microsoft.com.  

## <a name="next-steps"></a>Próximas etapas  

Para obter um tutorial, consulte [Proteger o Banco de Dados SQL do Azure](sql-database-security-tutorial.md).
