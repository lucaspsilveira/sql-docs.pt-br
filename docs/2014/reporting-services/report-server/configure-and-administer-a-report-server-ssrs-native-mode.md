---
title: Configurar e administrar um servidor de relatório (modo nativo do SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Reporting Services, components
- deploying [Reporting Services], component options
- report servers [Reporting Services], component options
- configuration options [Reporting Services]
- administering Reporting Services
- components [Reporting Services], configuring
- configuring servers [Reporting Services]
ms.assetid: cfec012b-56f1-4346-9814-247acf22351c
caps.latest.revision: 50
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: d5a004993ab886151ce9e3f5e3f7b2a2970f60d0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36012424"
---
# <a name="configure-and-administer-a-report-server-ssrs-native-mode"></a>Configurar e administrar um servidor de relatório (modo nativo do SSRS)
  Este tópico resume as abordagens que podem ser usadas para configurar o [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Também inclui uma lista de tópicos que explicam como configurar componentes, recursos ou recursos específicos de servidor. Para configurar o [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], você pode:  
  
-   Usar o Gerenciador de Configuração do Reporting Services. Muitos dos tópicos nesta seção contêm informações sobre como configurar recursos específicos com essa ferramenta.  
  
-   Usar o [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] para personalizar propriedades de servidor, habilitar Meus Relatórios, habilitar logs de rastreamento e definir padrões em todo o site. Para obter mais informações sobre configurações de site, consulte [servidor de relatório do Reporting Services &#40;modo nativo&#41; ](reporting-services-report-server-native-mode.md) do Management Studio. Observe que é possível criar e executar um script que defina propriedades de servidor programaticamente. Para obter mais informações, consulte [tarefas administrativas e implantação de Script](../tools/script-deployment-and-administrative-tasks.md) e [propriedades de sistema do servidor de relatório](../report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md).  
  
-   Use o Gerenciador de Relatórios para conceder permissões de acesso ao servidor de relatório. Permissões são concedidas por atribuições de função definidas para cada usuário ou conta de grupo. Para obter mais informações, consulte [Funções e permissões &#40;Reporting Services&#41;](../security/roles-and-permissions-reporting-services.md).  
  
-   Como alternativa, modifique arquivos de configuração para alterar configurações do aplicativo. Para obter mais informações sobre cada arquivo e diretrizes para modificá-los, consulte [arquivos de configuração do Reporting Services](reporting-services-configuration-files.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Configurar as URLs do servidor de relatório &#40;SSRS Configuration Manager&#41;](../install-windows/configure-report-server-urls-ssrs-configuration-manager.md)  
 Descreve como definir as URLs usadas para acessar o servidor de relatório e o Gerenciador de Relatórios.  
  
 [Configurar a conta de serviço do servidor de relatório &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)  
 Fornece recomendações e etapas sobre como modificar a conta de serviço e a senha.  
  
 [Criar um banco de dados do servidor de relatório &#40;SSRS Configuration Manager&#41;](../../sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md)  
 Descreve como criar um banco de dados de servidor de relatório, exigido por armazenar metadados e objetos de servidor.  
  
 [Configurar uma Conexão de banco de dados do servidor de relatório &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
 Descreve como modificar a cadeia de conexão usada pelo servidor de relatório para conexão com o banco de dados do servidor de relatório.  
  
 [Configurar um servidor de relatório para entrega de email &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)  
 Descreve como configurar um servidor de relatório para dar suporte à distribuição de relatório por email.  
  
 [Configurar a conta de execução autônoma &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)  
 Descreve como configurar uma conta do usuário para processar relatórios no modo autônomo.  
  
## <a name="see-also"></a>Consulte também  
 [Configurar o acesso do construtor de relatórios](configure-report-builder-access.md)   
 [Arquivos de configuração do Reporting Services](reporting-services-configuration-files.md)   
 [Gerenciador de configuração do Reporting Services &#40;modo nativo&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)   
 [Segurança e proteção do Reporting Services](../security/reporting-services-security-and-protection.md)   
 [Servidor de Relatório do Reporting Services &#40;modo nativo&#41;](reporting-services-report-server-native-mode.md)  
  
  