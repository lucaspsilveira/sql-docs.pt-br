---
title: Carregar dados XML | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- XML data [SQL Server], loading
- loading XML data
ms.assetid: d1741e8d-f44e-49ec-9f14-10208b5468a7
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a5048132c50460475ffe9c04f0f03a75cf6368b7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37166293"
---
# <a name="load-xml-data"></a>Carregar dados XML
  É possível transferir dados XML para o [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] de várias maneiras. Por exemplo:  
  
-   Se você tiver dados em uma coluna de imagem ou [n]text em um banco de dados do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , poderá importar a tabela usando o [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Altere o tipo da coluna para XML usando a instrução ALTER TABLE.  
  
-   É possível copiar os dados em massa de outro banco de dados do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando bcp out e inserir os dados em massa no banco de dados da versão posterior usando bcp in.  
  
-   Se você tiver dados em colunas relacionais em um banco de dados do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , crie uma nova tabela com uma coluna [n]text e, opcionalmente, uma coluna de chave primária para um identificador de linha. Usar o cliente de programação para recuperar o XML gerado no servidor com FOR XML e gravá-la na `[n]text` coluna. Em seguida, use as técnicas mencionadas anteriormente para transferir dados para um banco de dados de versão posterior. É possível optar por gravar diretamente o XML em uma coluna XML no banco de dados da versão posterior.  
  
## <a name="bulk-loading-xml-data"></a>Carregando dados XML em massa  
 É possível carregar dados XML em massa no servidor usando os recursos de carregamento em massa do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], como bcp. O OPENROWSET permite carregar dados de arquivos em uma coluna de XML. O exemplo a seguir ilustra esse ponto.  
  
##### <a name="example-loading-xml-from-files"></a>Exemplo: Carregando XML de arquivos  
 Este exemplo mostra como inserir uma linha na tabela T. O valor da coluna XML é carregado do arquivo C:\MyFile\xmlfile.xml como CLOB, e a coluna de inteiro recebe o valor 10.  
  
```  
INSERT INTO T  
SELECT 10, xCol  
FROM    (SELECT *      
    FROM OPENROWSET (BULK 'C:\MyFile\xmlfile.xml', SINGLE_CLOB)   
 AS xCol) AS R(xCol)  
```  
  
## <a name="text-encoding"></a>Codificação de texto  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] armazena dados XML em Unicode (UTF-16). Os dados XML recuperados do servidor são fornecidos em codificação UTF-16. Para obter uma codificação diferente, você precisa executar a conversão necessária nos dados recuperados. Às vezes, os dados XML podem estar em uma codificação diferente. Nesse caso, você precisará ter cuidado durante o carregamento dos dados. Por exemplo:  
  
-   Se o texto XML estiver em Unicode (UCS-2, UTF-16), você poderá atribuí-lo a uma coluna, variável ou parâmetro XML sem nenhum problema.  
  
-   Se a codificação não for Unicode e for implícita, por causa da página de código de origem, a página de código da cadeia de caracteres no banco de dados deverá ser igual ou compatível com os pontos de código que você deseja carregar. Se necessário, use COLLATE. Se não houver nenhuma página de código desse tipo, será necessário adicionar uma declaração XML explícita com a codificação correta.  
  
-   Para usar uma codificação explícita, use o `varbinary()` de tipo, que não tem nenhuma interação com páginas de código, ou use um tipo de cadeia de caracteres da página de código apropriada. Em seguida, atribua os dados a uma coluna, variável ou parâmetro XML.  
  
### <a name="example-explicitly-specifying-an-encoding"></a>Exemplo: Especificando uma codificação explicitamente  
 Assuma que você tem um documento XML, vcdoc, armazenado como `varchar(max)` que não tem uma declaração XML explícita. A instrução a seguir adiciona uma declaração XML com codificação "iso8859-1", concatena o documento XML, converte o resultado em `varbinary(max)` para que a representação de bytes é preservada e, finalmente, converte-la para XML. Isso permite que o processador XML analise os dados de acordo com a codificação "iso8859-1" especificada e gere a representação UTF-16 correspondente para valores de cadeias de caracteres.  
  
```  
SELECT CAST(   
CAST (('<?xml version="1.0" encoding="iso8859-1"?>'+ vcdoc) AS VARBINARY (MAX))   
 AS XML)  
```  
  
### <a name="string-encoding-incompatibilities"></a>Incompatibilidades de codificação de cadeia de caracteres  
 Se você copiar e analisar XML como uma cadeia de caracteres literal na janela Editor de Consultas no [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], poderá experimentar incompatibilidades de codificação de cadeia de caracteres [N]VARCHAR. Isso dependerá da codificação de sua instância XML. Em muitas casos, você poderá desejar remover a declaração XML. Por exemplo:  
  
```  
<?xml version="1.0" encoding="UTF-8"?>  
  <xsd:schema …  
```  
  
 Você deve incluir um N para transformar a instância de XML em uma instância de Unicode. Por exemplo:  
  
```  
-- Assign XML instance to a variable.  
DECLARE @X XML  
SET @X = N'…'  
-- Insert XML instance into an xml type column.  
INSERT INTO T VALUES (N'…')  
-- Create an XML schema collection  
CREATE XML SCHEMA COLLECTION XMLCOLL1 AS N'<xsd:schema … '  
```  
  
## <a name="see-also"></a>Consulte também  
 [Dados XML &#40;SQL Server&#41;](xml-data-sql-server.md)  
  
  