---
title: '@@FETCH_STATUS (Transact-SQL) | Microsoft Docs'
ms.custom: ''
ms.date: 09/18/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '@@FETCH_STATUS'
- '@@FETCH_STATUS_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- FETCH statement
- status information [SQL Server], FETCH
- '@@FETCH_STATUS function'
ms.assetid: 93659193-e4ff-4dfb-9043-0c4114921b91
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: b8fb20416fb1a36d19c719b568f0d8bc651c3a1a
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82824221"
---
# <a name="x40x40fetch_status-transact-sql"></a>&#x40;&#x40;FETCH_STATUS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Essa função retorna o status do último cursor que a instrução FETCH emitiu em relação a qualquer cursor atualmente aberto pela conexão.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Ícone de link do tópico") [Convenções da sintaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
@@FETCH_STATUS  
```  
  
## <a name="return-type"></a>Tipo de retorno  
 **inteiro**  
  
## <a name="return-value"></a>Valor retornado  
  
|Valor retornado|DESCRIÇÃO|  
|------------------|-----------------|  
|&nbsp;0|A instrução FETCH foi bem-sucedida.|  
|-1|A instrução FETCH falhou ou a linha estava além do conjunto de resultados.|  
|-2|A linha buscada está ausente.|
|-9|O cursor não está executando uma operação de busca.|  
  
## <a name="remarks"></a>Comentários  
Como `@@FETCH_STATUS` é global para todos os cursores em uma conexão, use-o com cuidado. Depois que uma instrução FETCH é executada, o teste para `@@FETCH_STATUS` deve ocorrer antes que qualquer outra instrução FETCH seja executada com relação a outro cursor. `@@FETCH_STATUS` é indefinido antes de ocorrer qualquer busca na conexão.  
  
Por exemplo, um usuário executa uma instrução FETCH a partir de um cursor e, depois, chama um procedimento armazenado que abre e processa os resultados de outro cursor. Quando o controle retorna desse procedimento armazenado chamado, `@@FETCH_STATUS` reflete o último FETCH executado no procedimento armazenado, não a instrução FETCH executada antes de chamar o procedimento armazenado.  
  
Para recuperar o último status chamado de um cursor específico, veja a coluna **fetch_status** da função de gerenciamento dinâmico **sys.dm_exec_cursors**.  
  
## <a name="examples"></a>Exemplos  
Este exemplo usa `@@FETCH_STATUS` para controlar atividades de cursor em um loop `WHILE`.  
  
```  
DECLARE Employee_Cursor CURSOR FOR  
SELECT BusinessEntityID, JobTitle  
FROM AdventureWorks2012.HumanResources.Employee;  
OPEN Employee_Cursor;  
FETCH NEXT FROM Employee_Cursor;  
WHILE @@FETCH_STATUS = 0  
   BEGIN  
      FETCH NEXT FROM Employee_Cursor;  
   END;  
CLOSE Employee_Cursor;  
DEALLOCATE Employee_Cursor;  
GO  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Funções de cursor &#40;Transact-SQL&#41;](../../t-sql/functions/cursor-functions-transact-sql.md)   
 [FETCH &#40;Transact-SQL&#41;](../../t-sql/language-elements/fetch-transact-sql.md)  
  
  
