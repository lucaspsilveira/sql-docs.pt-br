---
title: CHARINDEX (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CHARINDEX
- CHARINDEX_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- expressions [SQL Server], pattern searching
- CHARINDEX function
- pattern searching [SQL Server]
- starting point of expression in character string
ms.assetid: 78c10341-8373-4b30-b404-3db20e1a3ac4
caps.latest.revision: 52
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 9ac0d0a9cd8af41eddf90a0aeea85bcf7013ee27
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="charindex-transact-sql"></a>CHARINDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Essa função pesquisa uma expressão de caractere dentro de uma segunda expressão de caractere, retornando a posição inicial da primeira expressão, se localizada.
  
![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Ícone de link do tópico") [Convenções de sintaxe de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintaxe  
  
```sql
CHARINDEX ( expressionToFind , expressionToSearch [ , start_location ] )   
```  
  
## <a name="arguments"></a>Argumentos  
*expressionToFind*  
Uma [expressão](../../t-sql/language-elements/expressions-transact-sql.md) de caractere que contém a sequência a localizar. *expressionToFind* tem um limite de 8.000 caracteres.
  
*expressionToSearch*  
Uma expressão de caractere a ser pesquisada.
  
*start_location*  
Uma expressão **integer** ou **bigint** em que a pesquisa inicia. Se *start_location* não for especificado, tiver um valor negativo ou for um valor zero (0), a pesquisa começará no início de *expressionToSearch*.
  
## <a name="return-types"></a>Tipos de retorno
**bigint** se *expressionToSearch* tiver um tipo de dados **nvarchar (max)**, **varbinary (max)** ou **varchar (max)**; **int** caso contrário.
  
## <a name="remarks"></a>Remarks  
Se a expressão *expressionToFind* ou *expressionToSearch* tiver um tipo de dados Unicode (**nchar** ou **nvarchar**) e o outra expressão não, a função CHARINDEX converterá essa outra expressão em um tipo de dados Unicode. CHARINDEX não pode ser usado com os tipos de dados **image**, **ntext** ou **text**.
  
Se a expressão *expressionToFind* ou *expressionToSearch* tiver um valor NULL, CHARINDEX retornará NULL.
  
Se CHARINDEX não encontrar *expressionToFind* em *expressionToSearch*, CHARINDEX retornará 0.
  
CHARINDEX efetua comparações com base no agrupamento de entrada. Para fazer uma comparação em um agrupamento especificado, use COLLATE para aplicar um agrupamento explícito à entrada.
  
A posição inicial retornada é com base em 1, não com base em 0.
  
0x0000 (**char(0)**) é um caractere indefinido em agrupamentos do Windows e não pode ser incluído em CHARINDEX.
  
## <a name="supplementary-characters-surrogate-pairs"></a>Caracteres suplementares (pares substitutos)  
Ao usar agrupamentos de SC, *start_location* e o valor retornado contam pares substitutos como um caractere, e não dois. Para obter mais informações, consulte [Suporte a agrupamentos e Unicode](../../relational-databases/collations/collation-and-unicode-support.md).
  
## <a name="examples"></a>Exemplos  
  
### <a name="a-returning-the-starting-position-of-an-expression"></a>A. Retornando a posição inicial de uma expressão  
Este exemplo pesquisa `bicycle` na variável de valor de cadeia de caracteres pesquisada `@document`.
  
```sql
DECLARE @document varchar(64);  
SELECT @document = 'Reflectors are vital safety' +  
                   ' components of your bicycle.';  
SELECT CHARINDEX('bicycle', @document);  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
-----------   
48            
```  
  
### <a name="b-searching-from-a-specific-position"></a>B. Pesquisando em uma posição específica  
Este exemplo usa o parâmetro *start_location* opcional para iniciar a pesquisa para `vital` no quinto caractere da variável de valor de cadeia de caracteres pesquisada `@document`.
  
```sql
DECLARE @document varchar(64);  
  
SELECT @document = 'Reflectors are vital safety' +  
                   ' components of your bicycle.';  
SELECT CHARINDEX('vital', @document, 5);  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
-----------   
16            
  
(1 row(s) affected)  
```  
  
### <a name="c-searching-for-a-nonexistent-expression"></a>C. Pesquisando uma expressão inexistente  
Este exemplo mostra o conjunto de resultados quando CHARINDEX não localiza *expressionToFind* em *expressionToSearch*.
  
```sql
DECLARE @document varchar(64);  
  
SELECT @document = 'Reflectors are vital safety' +  
                   ' components of your bicycle.';  
SELECT CHARINDEX('bike', @document);  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
-----------
0
  
(1 row(s) affected)
```
  
### <a name="d-performing-a-case-sensitive-search"></a>D. Executando uma pesquisa com diferenciação de maiúsculas e minúsculas  
Este exemplo mostra uma pesquisa que diferencia maiúsculas de minúsculas para a cadeia de caracteres `'TEST'` na cadeia de caracteres de pesquisada `'This is a Test``'`.
  
```sql
USE tempdb;  
GO  
--perform a case sensitive search  
SELECT CHARINDEX ( 'TEST',  
       'This is a Test'  
       COLLATE Latin1_General_CS_AS);  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
-----------
0
```  
  
Este exemplo mostra uma pesquisa que diferencia maiúsculas de minúsculas para a cadeia de caracteres `'Test'` em `'This is a Test'`.
  
```sql
  
USE tempdb;  
GO  
SELECT CHARINDEX ( 'Test',  
       'This is a Test'  
       COLLATE Latin1_General_CS_AS);  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
-----------
11
```  
  
### <a name="e-performing-a-case-insensitive-search"></a>E. Executando uma pesquisa sem diferenciação de maiúsculas e minúsculas  
Este exemplo mostra uma pesquisa que não diferencia maiúsculas de minúsculas para a cadeia de caracteres `'TEST'` em `'This is a Test'`.
  
```sql
  
USE tempdb;  
GO  
SELECT CHARINDEX ( 'TEST',  
       'This is a Test'  
       COLLATE Latin1_General_CI_AS);  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
-----------
13
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemplos: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="f-searching-from-the-start-of-a-string-expression"></a>F. Pesquisar desde o início de uma expressão de cadeia de caracteres  
Este exemplo retorna o primeiro local da cadeia de caracteres `is` na cadeia de caracteres `This is a string`, começando da posição 1 (o primeiro caractere) de `This is a string`.
  
```sql
SELECT CHARINDEX('is', 'This is a string');  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
---------
3
```  
  
### <a name="g-searching-from-a-position-other-than-the-first-position"></a>G. Busca de uma posição que não a primeira  
Este exemplo retorna o primeiro local da cadeia de caracteres `is` na cadeia de caracteres `This is a string` começando a pesquisa da posição 4 (o quarto caractere).
  
```sql
SELECT CHARINDEX('is', 'This is a string', 4);  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
---------
 6
 ```  
  
### <a name="h-results-when-the-string-is-not-found"></a>H. Resulta quando a cadeia de caracteres não é encontrada  
Este exemplo mostra o valor retornado quando CHARINDEX não encontra a cadeia de caracteres *string_pattern* na cadeia de caracteres pesquisada.
  
```sql
SELECT TOP(1) CHARINDEX('at', 'This is a string') FROM dbo.DimCustomer;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
---------
0
```  
  
## <a name="see-also"></a>Confira também
 [LEN &#40;Transact-SQL&#41;](../../t-sql/functions/len-transact-sql.md)  
 [PATINDEX &#40;Transact-SQL&#41;](../../t-sql/functions/patindex-transact-sql.md)  
 [Funções de cadeia de caracteres &#40;Transact-SQL&#41;](../../t-sql/functions/string-functions-transact-sql.md)  
 [+ &#40;Concatenação de cadeias de caracteres&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/string-concatenation-transact-sql.md)  
 [Suporte a agrupamentos e a Unicode](../../relational-databases/collations/collation-and-unicode-support.md)  
  
  

