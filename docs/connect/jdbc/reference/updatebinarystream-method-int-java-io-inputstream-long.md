---
title: Método updateBinaryStream (int, java.io.InputStream, long) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: f84cfbe6-ebab-4357-8770-f1db34ecb04f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d72ab6b28dd1622c628619fbf6ef773742245dc3
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80925545"
---
# <a name="updatebinarystream-method-int-javaioinputstream-long"></a>Método updateBinaryStream (int, java.io.InputStream, longo)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Atualiza a coluna designada com um valor de fluxo binário que terá o número de bytes especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public void updateBinaryStream(int columnIndex,  
                               java.io.InputStream x,  
                               long length)  
```  
  
#### <a name="parameters"></a>parâmetros  
 *columnIndex*  
  
 Um **int** que indica o índice de coluna.  
  
 *x*  
  
 Um objeto InputStream.  
  
 *length*  
  
 Um **long** que indica o comprimento do fluxo.  
  
## <a name="exceptions"></a>Exceções  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentários  
 Esse método updateBinaryStream é especificado pelo método updateBinaryStream na interface java.sql.ResultSet.  
  
 Esse método passa bytes de um objeto InputStream para colunas binárias [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] selecionadas do como binary, varbinary, varbinary(max), image, xml e udt. Não há suporte para a atualização de colunas de caracteres nesse método. Para atualizar colunas de caracteres com um InputStream, use o método [updateAsciiStream](../../../connect/jdbc/reference/updateasciistream-method-sqlserverresultset.md).  
  
 Se o comprimento do fluxo for diferente do especificado no parâmetro *length*, o driver JDBC lançará uma exceção quando a linha for atualizada ou inserida.  
  
 Se o comprimento do fluxo for desconhecido, o parâmetro *length* poderá ser definido como -1 para indicar que o driver deve aceitar o fluxo independentemente do seu comprimento. Com sqljdbc4.jar, é recomendável usar o [Método updateBinaryStream &#40;int, java.io.InputStream&#41;](../../../connect/jdbc/reference/updatebinarystream-method-int-java-io-inputstream.md) do JDBC 4.0 quando o aplicativo quiser atualizar a coluna de um fluxo cujo comprimento é desconhecido.  
  
## <a name="see-also"></a>Consulte Também  
 [Método updateBinaryStream &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatebinarystream-method-sqlserverresultset.md)   
 [Membros de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
