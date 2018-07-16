---
title: Claims to Windows Token Service (C2WTS) e o Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 03/25/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- c2wts.exe.config
- SharePoint mode
- C2WTS
- WSS_WPG
ms.assetid: 4d380509-deed-4b4b-a9c1-a9134cc40641
caps.latest.revision: 11
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: e3a44f0beff9bd3351265caca0ee9490a7c6aeeb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37278182"
---
# <a name="claims-to-windows-token-service-c2wts-and-reporting-services"></a>Claims to Windows Token Service (C2WTS) e Reporting Services
  O Claims to Windows Token Service (c2WTS) do SharePoint é necessário com [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] modo do SharePoint se você quiser usar a autenticação do windows para fontes de dados que estão fora do farm do SharePoint. Isso ocorre mesmo quando o usuário acessa as fontes de dados com a Autenticação do Windows porque a comunicação entre o WFE (front-end da Web) e o serviço compartilhado do [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sempre será uma autenticação de Reivindicações.  
  
 O C2WTS é necessário até mesmo quando as fontes de dados estão no mesmo computador que o serviço compartilhado. Entretanto, neste cenário, a delegação restrita não é necessária.  
  
 Os tokens criados por c2WTS só funcionarão com a delegação restrita (restrições a serviços específicos) e a opção de configuração "usando qualquer protocolo de autenticação". Conforme observado anteriormente, se suas fontes de dados estiverem no mesmo computador que o serviço compartilhado, a delegação restrita não será necessária.  
  
 Se seu ambiente usar a delegação restrita de Kerberos, o serviço do SharePoint Server e as fontes de dados externas precisarão residir no mesmo domínio do Windows. Qualquer serviço que dependa do c2WTS (Declarações para Serviço de Token do Windows) deve usar a delegação **restrita** Kerberos para permitir que o c2WTS use a transição do protocolo Kerberos para traduzir declarações em credenciais do Windows. Estes requisitos são verdadeiros para todos os Serviços Compartilhados do SharePoint. Para obter mais informações, consulte [visão geral da autenticação do Kerberos para produtos do Microsoft SharePoint 2010 (http://technet.microsoft.com/library/gg502594.aspx)](http://technet.microsoft.com/library/gg502594.aspx).  
  
 O procedimento é resumido neste tópico.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 &#124; SharePoint 2010|  
  
## <a name="prerequisites"></a>Prerequisites  
  
> [!NOTE]  
>  Nota: Algumas das etapas de configuração podem mudar ou não funcionar em certas topologias de farm. Por exemplo, uma única instalação de servidor não oferece suporte aos serviços Windows Identity Foundation C2WTS; portanto, reivindicações assim a janelas cenários de delegação simbólicos não são possíveis com esta configuração de farm.  
  
### <a name="basic-steps-needed-to-configure-c2wts"></a>Etapas básicas necessárias para configurar o c2WTS  
  
1.  Configure a conta de serviço do c2WTS. Adicione a conta de serviço ao grupo de Administradores local em cada servidor de aplicativos executando c2WTS. Além disso, verifique se a conta tem os seguintes direitos de política de segurança local:  
  
    -   Atuar como parte do sistema operacional  
  
    -   Representar um cliente após a autenticação  
  
    -   Fazer logon como um serviço  
  
     A conta que você usa para C2WTS também precisa ser configurada para Delegação Restrita com Protocolo que Faz a transição e precisa de permissões para delegar aos Serviços com os quais ela precisa se comunicar (isto é, mecanismo SQL Server, SQL Server Analysis Services). Para configurar a delegação, você pode usar o snap-in do computador de usuários do Active Directory.  
  
    1.  Clique com o botão direito do mouse em cada conta de serviço e abra a caixa de diálogo de propriedades. Na caixa de diálogo, clique na guia **Delegação** .  
  
        > [!NOTE]  
        >  Nota: a guia delegação só ficará visível se o objeto tiver um SPN atribuído a ele. c2WTS does not require an SPN on the c2WTS Account, however, without an SPN, the **Delegação** não ficará visível. Um modo alternativo de configurar a delegação restrita é usar um utilitário como **ADSIEdit**.  
  
    2.  Principais opções de configuração na guia delegação:  
  
        -   Selecione "Confiar neste usuário apenas para delegação a serviços especificados"  
  
        -   Selecione "Usar qualquer protocolo de autenticação"  
  
         Para obter mais informações, consulte a seção "configurar a delegação restrita a Kerberos para computadores e contas de serviço" do white paper [Configurando a autenticação de Kerberos para produtos do SharePoint 2010 e do SQL Server 2008 R2](http://blogs.technet.com/b/tothesharepoint/archive/2010/07/22/whitepaper-configuring-kerberos-authentication-for-sharepoint-2010-and-sql-server-2008-r2-products.aspx)  
  
2.  Configure o c2WTS ‘AllowedCallers’  
  
     c2WTS requer as identidades dos 'chamadores' explicitamente listadas no arquivo de configuração **c2wtshost.exe.config**. c2WTS não aceita solicitações de todos os usuários autenticados no sistema, a menos que ele está configurado para fazer isso. Neste caso, o 'chamador' é o grupo WSS_WPG do Windows. O arquivo c2wtshost.exe.confi é salvo no seguinte local:  
  
     **\Program identity Foundation\v3.5\c2wtshost.exe.config**  
  
     Este é um exemplo do arquivo de configuração:  
  
    ```  
    <configuration>  
      <windowsTokenService>  
        <!--  
            By default no callers are allowed to use the Windows Identity Foundation Claims To NT Token Service.  
            Add the identities you wish to allow below.  
          -->  
        <allowedCallers>  
          <clear/>  
          <add value="WSS_WPG" />  
        </allowedCallers>  
      </windowsTokenService>  
    </configuration>  
    ```  
  
3.  Inicie o serviço C2WTS do sistema operacional:  
  
    1.  Configure o serviço para usar a conta de serviço configurada na etapa anterior.  
  
    2.  Mude o tipo de Inicialização para “**Automático**“ e inicie o serviço.  
  
4.  Inicie o “Claims to Windows Token Service” do SharePoint: Inicie o Claims to Windows Token Service pela Administração Central do SharePoint na página **Gerenciar serviços no servidor** . O serviço deverá ser iniciado no servidor que estará executando a ação. Por exemplo, se você tiver um servidor que é um WFE e outro servidor que é um Servidor de aplicativos com o serviço compartilhado do [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] shared service running, you only need to start c2WTS on the Application Server. O c2WTS não é necessário no WFE.  
  
## <a name="see-also"></a>Consulte também  
 [(Visão geral de declarações para o Windows Token Service (c2WTS)http://msdn.microsoft.com/library/ee517278.aspx)](http://msdn.microsoft.com/library/ee517278.aspx)   
 [Visão geral da autenticação Kerberos para produtos do Microsoft SharePoint 2010 (http://technet.microsoft.com/library/gg502594.aspx)](http://technet.microsoft.com/library/gg502594.aspx)  
  
  