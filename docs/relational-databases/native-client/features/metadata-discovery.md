---
title: Descoberta de metadados | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.reviewer: ''
ms.prod: sql
ms.technology: native-client
ms.topic: reference
ms.assetid: ec3c0f4f-f838-43ce-85f2-cf2761e2aac5
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5d822362e9f9f7e70e4421056383aae8ddef03dc
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303337"
---
# <a name="metadata-discovery"></a>Descoberta de metadados
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  A melhoria na descoberta de metadados no [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] permite que aplicativos do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client assegurem que os metadados de colunas ou parâmetros retornados da execução de uma consulta sejam idênticos ou compatíveis com o formato de metadados especificado antes da execução da consulta. Você receberá um erro se os metadados retornados depois da execução da consulta não forem compatíveis com o formato de metadados especificado antes da execução da consulta.  
  
 Em funções bcp e ODBC, e em interfaces IBCPSession e IBCPSession2, agora você pode especificar uma leitura atrasada (descoberta de metadados atrasada) para evitar a descoberta de metadados para operações de saída de consulta. Isso melhora o desempenho e elimina falhas de descoberta de metadados.  
  
 Se você desenvolver um aplicativo usando o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client no [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] , mas se conectar a uma versão de servidor anterior ao [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], a funcionalidade de descoberta de metadados corresponderá à versão do servidor.  
  
## <a name="remarks"></a>Comentários  
 As funções bcp a seguir foram aperfeiçoadas no [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] para fornecer descoberta de metadados aprimorada:  
  
-   [bcp_columns](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md)  
  
-   [bcp_control](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)  
  
-   [bcp_getcolfmt](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-getcolfmt.md)  
  
-   [bcp_readfmt](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md)  
  
-   [bcp_setcolfmt](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-setcolfmt.md)  
  
 Você também verá uma melhoria no desempenho ao especificar o formato de metadados usando [bcp_setbulkmode](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-setbulkmode.md).  
  
 [bcp_control](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) tem um novo *eOption* para controlar o comportamento de bcp_readfmt: **BCPDELAYREADFMT**.  
  
 As funções ODBC a seguir foram aperfeiçoadas no [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] para fornecer descoberta de metadados aprimorada:  
  
-   [SQLNumResultCols](../../../relational-databases/native-client-odbc-api/sqlnumresultcols.md)  
  
-   [SQLDescribeCol](../../../relational-databases/native-client-odbc-api/sqldescribecol.md)  
  
-   [SQLNumParams](../../../relational-databases/native-client-odbc-api/sqlnumparams.md)  
  
-   [SQLDescribeParam](../../../relational-databases/native-client-odbc-api/sqldescribeparam.md)  
  
 As funções de membros OLE DB a seguir foram aperfeiçoadas no [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] para fornecer descoberta de metadados aprimorada:  
  
-   IColumnsInfo::GetColumnInfo  
  
-   IColumnsRowset::GetColumnsRowset  
  
-   ICommandWithParameters::GetParameterInfo (confira [ICommandWithParameters](../../../relational-databases/native-client-ole-db-interfaces/icommandwithparameters.md) para obter mais informações)  
  
 Você também verá uma melhoria no desempenho ao especificar o formato de metadados usando IBCPSession::BCPSetBulkMode  
  
 A descoberta de metadados aprimorada no [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client é possível devido à adição de dois procedimentos armazenados no [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]:  
  
-   sp_describe_first_result_set  
  
-   sp_describe_undeclared_parameters  
  
## <a name="see-also"></a>Consulte Também  
 [Recursos do SQL Server Native Client](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
