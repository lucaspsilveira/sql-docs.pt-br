---
title: Metadados de TVP para instruções preparadas
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), metadata for prepared statements
ms.assetid: fd2fc705-2e98-4011-9822-c7e6cca4a535
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6928c24b1c06e75c8e20b318321eac4f4bd99985
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81297744"
---
# <a name="table-valued-parameter-metadata-for-prepared-statements"></a>Metadados do parâmetro com valor de tabela para instruções preparadas
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Um aplicativo pode obter metadados para uma chamada de procedimento preparada por meio de SQLNumParams e SQLDescribeParam. Para parâmetros com valor de tabela, *DataTypePtr* é definido como SQL_SS_TABLE. Os metadados adicionais estão disponíveis por meio do SQLGetDescField para SQL_CA_SS_TYPE_NAME, SQL_CA_SS_CATALOG_NAME e SQL_CA_SS_SCHEMA_NAME.  
  
 SQL_CA_SS_TYPE_NAME, SQL_CA_SS_CATALOG_NAME e SQL_CA_SS_SCHEMA_NAME podem ser usados com SQLColumns para obter metadados de coluna para tipos de tabela associados a parâmetros com valor de tabela. Nesse caso, SQL_SOPT_SS_NAME_SCOPE deve ser definido como SQL_SS_NAME_SCOPE_TABLE_TYPE antes que SQLColumns seja chamado. SQL_SOPT_SS_NAME_SCOPE deve ser definido novamente com o valor padrão, SQL_SS_NAME_SCOPE_TABLE, quando o aplicativo concluir a recuperação de metadados da coluna do parâmetro com valor de tabela.  
  
 SQL_CA_SS_TYPE_NAME , SQL_CA_SS_CATALOG_NAME e SQL_CA_SS_SCHEMA_NAME também podem ser usados com parâmetros de tipo de dado CLR definido pelo usuário.  
  
 Você não pode obter metadados de parâmetro com valor de tabela para instruções preparadas que não são chamadas de procedimento armazenado. Se você tentar fazer isto, o aplicativo retornará SQL_ERROR com SQLSTATE 42000 e a mensagem "Erro de sintaxe ou violação de acesso".  
  
## <a name="see-also"></a>Consulte Também  
 [Parâmetros com valor de tabela &#40;&#41;ODBC](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
