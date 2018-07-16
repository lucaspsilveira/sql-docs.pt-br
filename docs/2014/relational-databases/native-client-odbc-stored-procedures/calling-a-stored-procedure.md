---
title: Chamar um procedimento armazenado | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- calling stored procedures
- ODBC, stored procedures
- stored procedures [ODBC], calling
- SQL Server Native Client ODBC driver, stored procedures
- ODBC CALL escape sequence
- escape sequences [SQL Server]
- CALL statement
ms.assetid: d13737f4-f641-45bf-b56c-523e2ffc080f
caps.latest.revision: 40
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 11c8c691cf605942ef226927c9f0c2e940b28d63
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37411535"
---
# <a name="calling-a-stored-procedure"></a>Chamando um procedimento armazenado
  O [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client dá suporte a ODBC CALL sequência de escape do e o [!INCLUDE[tsql](../../includes/tsql-md.md)] [EXECUTE](/sql/t-sql/language-elements/execute-transact-sql) instrução para a execução de procedimentos armazenados; a sequência de escape CALL do ODBC é o método preferencial. Usar a sintaxe ODBC permite que um aplicativo recupere os códigos de retorno dos procedimentos armazenados e o driver ODBC do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client também é otimizado para usar um protocolo originalmente desenvolvido para enviar RPCs (chamadas de procedimento remoto) entre computadores que estejam executando o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Este protocolo de RPC aumenta o desempenho, eliminando grande parte do processamento de parâmetros e da análise da instrução feita no servidor.  
  
> [!NOTE]  
>  Ao chamar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] procedimentos armazenados usando parâmetros nomeados com ODBC (para obter mais informações, consulte [associando parâmetros por nome (parâmetros nomeados)](http://go.microsoft.com/fwlink/?LinkID=209721)), os nomes de parâmetro devem começar com o ' @' caracteres. Esta é uma restrição específica do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. O driver ODBC do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client impõe esta restrição de forma mais rigorosa que os MDAC (Microsoft Data Access Components).  
  
 A sequência de escape CALL do ODBC para chamar um procedimento é:  
  
 {[**? =**]**chamada * **procedure_name*[([*parâmetro*] [**, **[* parâmetro *]]...)]}  
  
 em que *procedure_name* Especifica o nome de um procedimento e *parâmetro* Especifica um parâmetro de procedimento. Há suporte para parâmetros nomeados somente em instruções que usam a sequência de escape ODBC CALL.  
  
 Um procedimento pode ter zero ou mais parâmetros. Ele também pode retornar um valor (conforme indicado pelo marcador de parâmetro opcional ?= no início da sintaxe). Se um parâmetro for de entrada ou entrada/saída, poderá ser um literal ou um marcador de parâmetro. Se o parâmetro for de saída, deve ser um marcador de parâmetro, porque a saída é desconhecida. Marcadores de parâmetro devem ser associados com [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md) antes da chamada de procedimento instrução é executada.  
  
 Parâmetros de entrada e entrada/saída podem ser omitidos das chamadas de procedimento. Se um procedimento for chamado usando parênteses, mas sem nenhum parâmetro, o driver instruirá a fonte de dados a usar o valor padrão para o primeiro parâmetro. Por exemplo:  
  
 {**chamar** * * procedure_name **()**}  
  
 Se o procedimento não tiver nenhum parâmetro, ele poderá falhar. Se um procedimento for chamado sem parênteses, o driver não enviará nenhum valor de parâmetro. Por exemplo:  
  
 {**chamar** *procedure_name*}  
  
 Literais podem ser especificados para parâmetros de entrada e de entrada/saída em chamadas de procedimento. Por exemplo, o procedimento InsertOrder tem cinco parâmetros de entrada. A seguinte chamada a InsertOrder omite o primeiro parâmetro, fornece um literal para o segundo parâmetro e usa um marcador de parâmetro para o terceiro, quarto e quinto parâmetros. (Os parâmetros são numerados sequencialmente, a partir do valor 1.)  
  
```  
{call InsertOrder(, 10, ?, ?, ?)}  
```  
  
 Observe que, se um parâmetro for omitido, a vírgula que o separa de outros parâmetros ainda precisará aparecer. Se um parâmetro de entrada ou entrada/saída for omitido, o procedimento usará o valor padrão do parâmetro. Outras formas de especificar o valor padrão de um parâmetro de entrada ou entrada/saída são definir o valor do buffer de comprimento/indicador associado ao parâmetro como SQL_DEFAULT_PARAM, ou usar a palavra-chave DEFAULT.  
  
 Se um parâmetro de entrada/saída for omitido ou se for fornecido um literal para o parâmetro, o driver descartará o valor de saída. De forma semelhante, se o marcador de parâmetro para o valor de retorno de um procedimento for omitido, o driver descartará o valor de retorno. Finalmente, se um aplicativo especificar um parâmetro de valor de retorno para um procedimento que não retorna um valor, o driver definirá o valor do buffer de comprimento/indicador associado ao parâmetro como SQL_NULL_DATA.  
  
## <a name="delimiters-in-call-statements"></a>Delimitadores em instruções CALL  
 O driver ODBC do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, por padrão, também dá suporte uma opção de compatibilidade específica para a sequência de escape {CALL} do ODBC. O driver aceita instruções CALL com um único conjunto de aspas duplas que delimitam o nome de procedimento armazenado inteiro:  
  
```  
{ CALL "master.dbo.sp_who" }  
```  
  
 Por padrão, o driver ODBC do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client também aceita instruções CALL que seguem as regras ISO e colocam cada identificador entre aspas duplas:  
  
```  
{ CALL "master"."dbo"."sp_who" }  
```  
  
 Entretanto, ao ser executado com as configurações padrão, o driver ODBC do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client não dá suporte ao uso de nenhuma forma de identificador entre aspas com identificadores que contenham caracteres que não sejam especificados como válidos em identificadores, de acordo com a norma ISO. Por exemplo, o driver não pode acessar um procedimento armazenado denominado **"My. proc"** usar uma instrução CALL com identificadores entre aspas:  
  
```  
{ CALL "MyDB"."MyOwner"."My.Proc" }  
```  
  
 Esta instrução é interpretada pelo driver como:  
  
```  
{ CALL MyDB.MyOwner.My.Proc }  
```  
  
 O servidor gera um erro que um servidor vinculado nomeado **MyDB** não existe.  
  
 O problema não existe ao usar identificadores entre colchetes, esta instrução é interpretada corretamente:  
  
```  
{ CALL [MyDB].[MyOwner].[My.Table] }  
```  
  
## <a name="see-also"></a>Consulte também  
 [Executando procedimentos armazenados](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
  