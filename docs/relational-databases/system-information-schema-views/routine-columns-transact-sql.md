---
title: ROUTINE_COLUMNS (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- ROUTINE_COLUMNS_TSQL
- ROUTINE_COLUMNS
dev_langs:
- TSQL
helpviewer_keywords:
- ROUTINE_COLUMNS view
- INFORMATION_SCHEMA.ROUTINE_COLUMNS view
ms.assetid: 91dbc61b-e4c0-4826-976c-b2fce88b7793
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 5b0ed500b1217ae70dca72ab6eab64ab661c22ce
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68078531"
---
# <a name="routine_columns-transact-sql"></a>ROUTINE_COLUMNS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retorna uma linha para cada coluna retornada pelas funções com valor de tabela que podem ser acessadas pelo usuário atual no banco de dados atual.  
  
 Para recuperar informações dessa exibição, especifique o nome totalmente qualificado de **INFORMATION_SCHEMA.** _view_name_.  
  
|Nome da coluna|Tipo de dados|Descrição|  
|-----------------|---------------|-----------------|  
|**TABLE_CATALOG**|**nvarchar (** 128 **)**|Catálogo ou nome de banco de dados da função com valor de tabela.|  
|**TABLE_SCHEMA**|**nvarchar (** 128 **)**|Nome do esquema que contém a função com valor de tabela.<br /><br /> <strong> \* Importante \* \* </strong> Não use INFORMATION_SCHEMA exibições para determinar o esquema de um objeto. O único modo seguro de localizar o esquema de um objeto é consultar a exibição de catálogo sys.objects.|  
|**TABLE_NAME**|**nvarchar (** 128 **)**|Nome da função com valor de tabela.|  
|**COLUMN_NAME**|**nvarchar (** 128 **)**|Nome da coluna.|  
|**ORDINAL_POSITION**|**int**|Número de identificação da coluna.|  
|**COLUMN_DEFAULT**|**nvarchar (** 4000 **)**|Valor padrão da coluna.|  
|**IS_NULLABLE**|**varchar (** 3 **)**|Se essa coluna permitir NULL, ela retornará YES. Caso contrário, retorna NO.|  
|**DATA_TYPE**|**nvarchar (** 128 **)**|Tipo de dados fornecido pelo sistema.|  
|**CHARACTER_MAXIMUM_LENGTH**|**int**|Comprimento máximo, em caracteres, de dados binários, dados de caracteres e dados de texto e imagem.<br /><br /> -1 para **XML** e dados de tipo de valor grande. Caso contrário, retorna NULL. Para obter mais informações, veja [Tipos de dados &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md).|  
|**CHARACTER_OCTET_LENGTH**|**int**|Comprimento máximo, em bytes, de dados binários, dados de caracteres e dados de texto e imagem.<br /><br /> -1 para **XML** e dados de tipo de valor grande. Caso contrário, retorna NULL.|  
|**NUMERIC_PRECISION**|**tinyint**|Precisão de dados numéricos aproximados, dados numéricos exatos, dados de inteiro ou dados monetários. Caso contrário, retorna NULL.|  
|**NUMERIC_PRECISION_RADIX**|**smallint**|Base de precisão de dados numéricos aproximados, dados numéricos exatos, dados de inteiro ou dados monetários. Caso contrário, retorna NULL.|  
|**NUMERIC_SCALE**|**tinyint**|Escala de dados numéricos aproximados, dados numéricos exatos, dados de inteiro ou dados monetários. Caso contrário, retorna NULL.|  
|**DATETIME_PRECISION**|**smallint**|Código de subtipo para tipos de dados **DateTime** e ISO**inteiro** . Para outros tipos de dados, retorna NULL.|  
|**CHARACTER_SET_CATALOG**|**varchar (** 6 **)**|Retorna o **mestre**. Isso indica o banco de dados no qual o conjunto de caracteres está localizado se a coluna é de dados de caracteres ou de **texto** . Caso contrário, retorna NULL.|  
|**CHARACTER_SET_SCHEMA**|**varchar (** 3 **)**|Sempre retorna NULL.|  
|**CHARACTER_SET_NAME**|**nvarchar (** 128 **)**|Retorna o nome exclusivo para o conjunto de caracteres se esta coluna for de dados de caracteres ou tipo de dados de **texto** . Caso contrário, retorna NULL.|  
|**COLLATION_CATALOG**|**varchar (** 6 **)**|Sempre retorna NULL.|  
|**COLLATION_SCHEMA**|**varchar (** 3 **)**|Sempre retorna NULL.|  
|**COLLATION_NAME**|**nvarchar (** 128 **)**|Retorna o nome exclusivo da ordem de classificação se a coluna for de dados de caracteres ou tipo de dados de **texto** . Caso contrário, retorna NULL.|  
|**DOMAIN_CATALOG**|**nvarchar (** 128 **)**|Se a coluna for do tipo de dados de alias, essa coluna será o nome do banco de dados no qual foi criado o tipo de dados definido pelo usuário. Caso contrário, retorna NULL.|  
|**DOMAIN_SCHEMA**|**nvarchar (** 128 **)**|Se a coluna for do tipo definido pelo usuário, essa coluna será o nome do esquema que contém o tipo de dados definido pelo usuário. Caso contrário, retorna NULL.<br /><br /> <strong> \* Importante \* \* </strong> Não use INFORMATION_SCHEMA exibições para determinar o esquema de um objeto. O único modo seguro de localizar o esquema de um objeto é consultar a exibição de catálogo sys.objects.|  
|**DOMAIN_NAME**|**nvarchar (** 128 **)**|Se a coluna for do tipo de dados definido pelo usuário, essa coluna será o nome do tipo de dados definido pelo usuário. Caso contrário, retorna NULL.|  
  
## <a name="see-also"></a>Consulte Também  
 [Exibições do sistema &#40;&#41;Transact-SQL](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Exibições do esquema de informações &#40;&#41;Transact-SQL](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [&#41;sys. Columns &#40;Transact-SQL](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)  
  
  
