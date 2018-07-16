---
title: Suporte a construções em procedimentos armazenados compilados nativamente | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 05515013-28b5-4ccf-9a54-ae861448945b
caps.latest.revision: 34
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 91434af003bdf783ee4f2bd2c946e4a871eac44d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37240842"
---
# <a name="supported-constructs-in-natively-compiled-stored-procedures"></a>Construções com suporte nos procedimentos armazenados compilados de modo nativo
  Este tópico contém uma lista de recursos com suporte para procedimentos armazenados compilados nativamente ([CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql)):  
  
-   [Programação em procedimentos armazenados compilados nativamente](#pncsp)  
  
-   [Operadores com suporte](#so)  
  
-   [Funções internas em procedimentos armazenados compilados nativamente](#bfncsp)  
  
-   [Área de superfície de consulta em procedimentos armazenados compilados nativamente](#qsancsp)  
  
-   [Auditoria](#auditing)  
  
-   [Tabela, consulta e dicas de junção](#tqh)  
  
-   [Limitações na classificação](#los)  
  
 Para obter informações sobre tipos de dados, suporte nativo para procedimentos armazenados compilados, consulte [suporte para tipos de dados](supported-data-types-for-in-memory-oltp.md).  
  
 Para obter informações completas sobre construções sem suporte e para obter informações sobre como solucionar alguns dos recursos sem suporte em procedimentos armazenados compilados nativamente, consulte [Migration Issues for Natively Compiled Stored Procedures](migration-issues-for-natively-compiled-stored-procedures.md). Para mais informações sobre os recursos sem suporte, veja [Constructos do Transact-SQL sem suporte no OLTP in-memory](transact-sql-constructs-not-supported-by-in-memory-oltp.md).  
  
##  <a name="pncsp"></a> Programação em procedimentos armazenados compilados nativamente  
 Há suporte para o seguinte:  
  
-   BEGIN ATOMIC (no nível externo do procedimento armazenado), LANGUAGE, ISOLATION LEVEL, DATEFORMAT e DATEFIRST.  
  
-   Declaração de variáveis como NULL ou NOT NULL. Se uma variável for declarada como NOT NULL, a declaração deverá ter um inicializador. Se uma variável não for declarada como NOT NULL, um inicializador será opcional.  
  
-   IF e WHILE  
  
-   INSERT/UPDATE/DELETE  
  
     Subconsultas têm suporte. Na cláusula WHERE ou HAVING, há suporte para AND e BETWEEN; não há suporte para OR, NOT e IN.  
  
-   Tipos de tabela com otimização de memória e variáveis de tabela.  
  
-   RETURN  
  
-   SELECT  
  
-   SET  
  
-   TRY/CATCH/THROW  
  
     Para otimizar o desempenho, use um único bloco TRY/CATCH para um procedimento armazenado originalmente compilado inteiro.  
  
##  <a name="so"></a> Operadores com suporte  
 Há suporte para os operadores que se seguem.  
  
-   [Operadores de comparação &#40;Transact-SQL&#41; ](/sql/t-sql/language-elements/comparison-operators-transact-sql) (por exemplo, >, \<, > =, e < =) têm suporte em condicionais (IF, ENQUANTO).  
  
-   Operadores unários (+, -).  
  
-   Operadores binários (*, /, +, -, % (módulo)).  
  
     O operador de adição (+) tem suporte em números e cadeias de caracteres.  
  
-   Operadores lógicos (AND, OR, NOT). OR e NOT têm suporte em instruções IF e WHILE, mas não nas cláusulas WHERE ou HAVING.  
  
-   Operadores bit a bit ~, &, |, e ^  
  
##  <a name="bfncsp"></a> Funções internas em procedimentos armazenados compilados nativamente  
 As seguintes funções têm suporte em restrições padrão nas tabelas com otimização de memória e em procedimentos armazenados compilados nativamente.  
  
-   Funções matemáticas: ACOS, ASIN, ATAN, ATN2, COS, COT, DEGREES, EXP, LOG, LOG10, PI, POWER, RADIANS, RAND, SIN, SQRT, SQUARE e TAN  
  
-   Funções de data: CURRENT_TIMESTAMP, DATEADD, DATEDIFF, DATEFROMPARTS, DATEPART, DATETIME2FROMPARTS, DATETIMEFROMPARTS, DAY, EOMONTH, GETDATE, GETUTCDATE, MONTH, SMALLDATETIMEFROMPARTS, SYSDATETIME, SYSUTCDATETIME e YEAR.  
  
-   Funções de cadeia de caracteres: LEN, LTRIM, RTRIM e SUBSTRING  
  
-   Função de identidade: SCOPE_IDENTITY  
  
-   Funções NULL: ISNULL  
  
-   Funções Uniqueidentifier: NEWID e NEWSEQUENTIALID  
  
-   Funções de erro: ERROR_LINE, ERROR_MESSAGE, ERROR_NUMBER, ERROR_PROCEDURE, ERROR_SEVERITY e ERROR_STATE  
  
-   Conversões: CAST e CONVERT. Não há suporte para conversões entre cadeias de caracteres Unicode e não Unicode (n(var)char e (var)char).  
  
-   Funções do sistema: @@rowcount. As instruções dentro de procedimentos armazenados compilados nativamente atualizam @@rowcount e você pode usar @@rowcount em um procedimento armazenado compilado nativamente para determinar o número de linhas afetadas pela última instrução executada nesse procedimento armazenado compilado nativamente. No entanto, @@rowcount é redefinido como 0 no início e no final da execução de um procedimento armazenado compilado nativamente.  
  
##  <a name="qsancsp"></a> Área de superfície de consulta em procedimentos armazenados compilados nativamente  
 Há suporte para o seguinte:  
  
-   BETWEEN  
  
-   Aliases de nome de coluna (usando AS ou a sintaxe =).  
  
-   CROSS JOIN e INNER JOIN, com suporte apenas com consultas SELECT.  
  
-   As expressões têm suporte na lista de seleção e [onde &#40;Transact-SQL&#41; ](/sql/t-sql/queries/where-transact-sql) cláusula se eles usarem um operador com suporte. Consulte [Supported Operators](#so) para obter a lista de operadores com suporte no momento.  
  
-   Predicado de filtro IS [NOT] NULL  
  
-   DE \<tabela com otimização de memória >  
  
-   [Agrupar por &#40;Transact-SQL&#41; ](/sql/t-sql/queries/select-group-by-transact-sql) tem suporte, juntamente com as funções de agregação AVG, COUNT, COUNT_BIG, MIN, MAX e soma. MIN e MAX não têm suporte para os tipos nvarchar, char, varchar, varchar, varbinary e binary. [Cláusula ORDER BY &#40;Transact-SQL&#41; ](/sql/t-sql/queries/select-order-by-clause-transact-sql) é compatível com [GROUP BY &#40;Transact-SQL&#41; ](/sql/t-sql/queries/select-group-by-transact-sql) se uma expressão na lista ORDER BY for exibida literalmente na lista GROUP BY. Por exemplo, GROUP BY + b ORDER BY a + b tem suporte, mas GROUP BY a, b ORDER BY a + b, não.  
  
-   HAVING, sujeita às mesmas limitações de expressão da cláusula WHERE.  
  
-   INSERT VALUES (uma linha por instrução) e INSERT SELECT  
  
-   ORDER BY <sup>1</sup>  
  
-   Predicados que não fazem referência a uma coluna.  
  
-   SELECT, UPDATE e DELETE  
  
-   PARTE SUPERIOR <sup>1</sup>  
  
-   Atribuição de variável na lista SELECT.  
  
-   WHERE... AND  
  
 <sup>1</sup> ORDER BY e TOP têm suporte em procedimentos armazenados compilados nativamente, com algumas restrições:  
  
-   Não há suporte para `DISTINCT` no `SELECT` ou `ORDER BY` cláusula.  
  
-   Não há suporte para `WITH TIES` ou `PERCENT` na cláusula `TOP`.  
  
-   `TOP` combinado com `ORDER BY` não dá suporte a mais de 8.192 ao usar uma constante no `TOP` cláusula. Esse limite poderá ser diminuído caso a consulta contenha junções ou funções de agregação. (Por exemplo, com uma junção (duas tabelas), o limite é 4.096 linhas. Com duas junções (três tabelas), o limite é 2.730 linhas.)  
  
     Você pode obter resultados maiores que 8.192 armazenando o número de linhas em uma variável:  
  
    ```tsql  
    DECLARE @v INT = 9000  
    SELECT TOP (@v) … FROM … ORDER BY …  
    ```  
  
 No entanto, uma constante na cláusula `TOP` resulta em um desempenho melhor comparado a usar uma variável.  
  
 Essas restrições não se aplicam ao interpretado [!INCLUDE[tsql](../../includes/tsql-md.md)] acesso às tabelas com otimização de memória.  
  
##  <a name="auditing"></a> Auditoria  
 A auditoria no nível de procedimento tem suporte em procedimentos armazenados compilados nativamente. Não há suporte para a auditoria no nível da instrução.  
  
 Para obter mais informações sobre a auditoria, consulte [Create a Server Audit and Database Audit Specification](../security/auditing/create-a-server-audit-and-database-audit-specification.md).  
  
##  <a name="tqh"></a> Tabela, consulta e dicas de junção  
 Há suporte para o seguinte:  
  
-   As dicas INDEX, FORCESCAN e FORCESEEK, seja na sintaxe das dicas de tabela ou na [Cláusula OPTION &#40;Transact-SQL&#41;](/sql/t-sql/queries/option-clause-transact-sql) da consulta.  
  
-   FORCE ORDER  
  
-   INNER LOOP JOIN  
  
-   OPTIMIZE FOR  
  
 Para obter mais informações, consulte [dicas de &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql).  
  
##  <a name="los"></a> Limitações na classificação  
 Você pode classificar maior que 8.000 linhas em uma consulta que usa [TOP &#40;Transact-SQL&#41;](/sql/t-sql/queries/top-transact-sql) e uma [Cláusula ORDER BY &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql). No entanto, sem a [Cláusula ORDER BY &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql), [TOP &#40;Transact-SQL&#41;](/sql/t-sql/queries/top-transact-sql) pode classificar até 8.000 linhas (menos linhas se houver junções).  
  
 Se sua consulta usar o operador [TOP &#40;Transact-SQL&#41;](/sql/t-sql/queries/top-transact-sql) e uma [Cláusula ORDER BY &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql), você pode especificar até 8192 linhas para o operador TOP. Se você especificar mais de 8192 linhas, receberá a mensagem de erro: **Msg 41398, Nível 16, Estado 1, Procedimento *\<procedureName>*, Linha *\<lineNumber>* O operador TOP pode retornar no máximo 8192 linhas; *\<number>* foi solicitado.**  
  
 Se você não tiver uma cláusula TOP, poderá classificar qualquer número de linhas com ORDER BY.  
  
 Se você não usar uma cláusula ORDER BY, poderá usar qualquer valor inteiro com o operador TOP.  
  
 Exemplo com TOP N = 8192: compila  
  
```tsql  
CREATE PROCEDURE testTop  
WITH EXECUTE AS OWNER, SCHEMABINDING, NATIVE_COMPILATION  
  AS  
  BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
    SELECT TOP 8192 ShoppingCartId, CreatedDate, TotalPrice FROM dbo.ShoppingCart  
    ORDER BY ShoppingCartId DESC  
  END;  
GO  
```  
  
 Exemplo com TOP N > 8192: não compila.  
  
```tsql  
CREATE PROCEDURE testTop  
WITH EXECUTE AS OWNER, SCHEMABINDING, NATIVE_COMPILATION  
  AS  
  BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
    SELECT TOP 8193 ShoppingCartId, CreatedDate, TotalPrice FROM dbo.ShoppingCart  
    ORDER BY ShoppingCartId DESC  
  END;  
GO  
```  
  
 A limitação de 8192 linhas só se aplica a `TOP N` onde `N` é uma constante, como nos exemplos anteriores.  Se você precisar de `N` maior que 8192, poderá atribuir o valor a uma variável e usar essa variável com `TOP`.  
  
 Exemplo que usa uma variável: compila  
  
```tsql  
CREATE PROCEDURE testTop  
WITH EXECUTE AS OWNER, SCHEMABINDING, NATIVE_COMPILATION  
  AS  
  BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
    DECLARE @v int = 8193   
    SELECT TOP (@v) ShoppingCartId, CreatedDate, TotalPrice FROM dbo.ShoppingCart  
    ORDER BY ShoppingCartId DESC  
  END;  
GO  
```  
  
 **Limitações nas linhas retornadas:** Há dois casos em que isso pode, potencialmente, reduzir o número de linhas a serem retornadas pelo operador TOP:  
  
-   Uso de JOINs na consulta.  A influência de JOINs na limitação depende do plano de consulta.  
  
-   Uso de funções de agregação ou de referências a funções de agregação na cláusula ORDER BY.  
  
 A fórmula para calcular o pior caso de N com suporte em TOP N é: `N = floor ( 65536 / number_of_tables * 8 + total_size+of+aggs )`.  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos armazenados compilados nativamente](natively-compiled-stored-procedures.md)   
 [Problemas de migração para procedimentos armazenados compilados nativamente](migration-issues-for-natively-compiled-stored-procedures.md)  
  
  