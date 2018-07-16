---
title: Propriedade Detail | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Detail property
- SoapException class
ms.assetid: c1ddaeb6-c540-49fa-b06e-b6359d377ee8
caps.latest.revision: 32
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: f7b2efb142573468b3231f28ea7ac7a337bda2a5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37151957"
---
# <a name="detail-property"></a>Propriedade Detail
  A propriedade **Detail** da classe **SoapException** do [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] tem a seguinte estrutura XML:  
  
## <a name="elements"></a>Elementos  
 **Detail**  
 O elemento de alto nível que contém todos os outros elementos de detalhe de erro.  
  
 **ErrorCode**  
 O código de erro específico do [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 **HttpStatus**  
 O código de status HTTP.  
  
 **Mensagem**  
 A mensagem de erro e o código de erro atribuídos pelo servidor de relatório.  
  
 **HelpLink**  
 A URL do link de Ajuda para um site no qual poderão ser encontradas informações adicionais sobre o erro. Para obter mais informações, consulte [Elemento HelpLink](helplink-element.md).  
  
 **LinkID**  
 A ID atribuída ao link.  
  
 **ProductName**  
 O nome do produto. O valor padrão é **Microsoft SQL Server Reporting Services**.  
  
 **ProductVersion**  
 A versão do [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. O tamanho máximo é de 15 caracteres. O formato do número da versão deve ser assim: 8.00.0xxx.00.  
  
 **ProductLocaleId**  
 A ID de localidade ou ID de idioma da DLL INTL do aplicativo (por exemplo, 0x41A).  
  
 **OperatingSystem**  
 O sistema operacional em que o [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] está instalado. Os valores válidos incluem **0** para o sistema operacional independente, **1** para o [!INCLUDE[win2kfamily](../../../includes/win2kfamily-md.md)] e **16** para o Windows XP.  
  
 **CountryLocaleId**  
 A ID de localidade ou a ID de idioma do sistema operacional. Por exemplo, o valor para a versão francesa de Windows é 0x040c.  
  
 **MoreInformation**  
 Uma cadeia de caracteres XML que contém exceções aninhadas ocorridas durante a execução do método.  
  
 **Origem**  
 Um elemento filho de **MoreInformation**. A origem do erro.  
  
 **Mensagem**  
 Um elemento filho de **MoreInformation**. A mensagem de erro de uma exceção aninhada. Esse elemento inclui atributos XML para **ErrorCode** e **HelpLink**.  
  
 **Warnings**  
 Uma cadeia de caracteres XML que contém os avisos retornados do processamento de relatório.  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao tratamento de exceção no Reporting Services](../introducing-exception-handling-in-reporting-services.md)   
 [Classe SoapException do Reporting Services](reporting-services-soapexception-class.md)   
 [Usar a propriedade Detail para manipular erros específicos](../best-practices/using-the-detail-property-to-handle-specific-errors.md)  
  
  