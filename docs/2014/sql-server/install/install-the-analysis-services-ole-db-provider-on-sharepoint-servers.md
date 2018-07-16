---
title: Instalar o Analysis Services OLE DB Provider em servidores do SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 2c62daf9-1f2d-4508-a497-af62360ee859
caps.latest.revision: 34
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 8403b4a4d65f81ccc5b43e50f69d58efb71508ec
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37292276"
---
# <a name="install-the-analysis-services-ole-db-provider-on-sharepoint-servers"></a>Instalar o provedor OLE DB do Analysis Services em SharePoint Servers
  O Provedor OLE DB da Microsoft para Analysis Services (MSOLAP) é uma interface que os aplicativos cliente usam para interagir com dados do [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Em um ambiente do SharePoint que inclui o [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)], o provedor administra solicitações de conexões para dados [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)].  
  
 O provedor de dados é incluído no pacote de instalação do [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] (spPowerPivot.msi), mas pode exigir a instalação manual. Há duas razões para você precisar instalar uma biblioteca de cliente ou um provedor de dados manualmente em um servidor do SharePoint.  
  
-   **Habilitar a compatibilidade com versões anteriores**. As pastas de trabalho do [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] especificam a versão [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] do provedor OLE DB do Analysis Services na cadeia de conexão. Como tal, a versão desse provedor deve estar presente no computador para que a solicitação tenha sucesso.  
  
-   **Habilitar o acesso a dados em uma instância dedicada de serviços do Excel**. Se seu farm do SharePoint incluir Serviços do Excel em um servidor que também não tenha [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)], instale a versão do [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] do provedor e outros componentes de conectividade de cliente usando o pacote de instalação do [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)].  
  
    > [!NOTE]  
    >  Esses cenários não são mutuamente exclusivos. Hospedar várias versões de pasta de trabalho em um farm que inclui servidores de aplicativos que executam Serviços do Excel sem uma instância do [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] requer que você instale versões mais antigas e mais novas do provedor de dados em cada computador com os Serviços do Excel.  
  
  
##  <a name="bkmk_vers"></a> Versões do provedor OLE DB que dão suporte a acesso a dados PowerPivot  
 Um farm do SharePoint pode incluir várias versões do provedor OLE DB do Analysis Services, incluindo versões mais antigas que não têm suporte para o acesso a dados PowerPivot.  
  
 Por padrão, o SharePoint 2010 instala a versão [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] do provedor. Embora seja identificada como MSOLAP.4 (mesmo número de versão usado no [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]), essa versão não funciona para o acesso a dados PowerPivot. Para que as conexões sejam bem-sucedidas, você deve ter a versão [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] ou [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] do provedor.  
  
 Uma versão pós-[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] do provedor OLE DB inclui transportes e suporte à conexão para estruturas de dados do [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]. As pastas de trabalho [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] usam versões mais novas desse provedor para solicitar processamento de consulta em servidores do [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] no farm. Para obter uma versão atualizada, você pode baixá-la e instalá-la diretamente de uma página do SQL Server Feature Pack.  
  
 A tabela a seguir descreve as versões válidas:  
  
|Versão do produto|Versão do arquivo|Válida para:|  
|---------------------|------------------|----------------|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|MSOLAP100.dll no sistema de arquivos<br /><br /> MSOLAP.4 em uma cadeia de conexão do Excel<br /><br /> 10.50.1600 ou posterior nos detalhes de versão do arquivo|Use para modelos de dados criados usando a versão [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] do PowerPivot para Excel.|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|MSOLAP110.dll no sistema de arquivos<br /><br /> MSOLAP.5 em uma cadeia de conexão do Excel<br /><br /> 11.0.0000 ou posterior nos detalhes de versão do arquivo|Use para modelos de dados criados usando a versão [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ou [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] do [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] para Excel.|  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|MSOLAP120.dll no sistema de arquivos<br /><br /> 12.0.20000 ou posterior nos detalhes de versão do arquivo|Use para modelos de dados além dos modelos do [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)].|  
  
  
##  <a name="bkmk_why"></a> Por que você precisa instalar o provedor OLE DB  
 Há dois cenários que requerem a instalação manual do provedor OLE DB em servidores no farm.  
  
 **O cenário mais comum** é quando você tem mais antiga e versões mais recentes do [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pastas de trabalho que são salvas em bibliotecas de documento no farm. Se os analistas na sua organização estiver usando o [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] versão do [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] para Excel e salvarem essas pastas de trabalho para um [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] instalação, a pasta de trabalho mais antiga não funcionará. Sua cadeia de conexão referenciará uma versão mais antiga do provedor, que não estará no servidor, a menos que você a instale. A instalação de ambas as versões habilitará o acesso a dados para pastas de trabalho PowerPivot criadas em versões mais antigas e mais novas do [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] para Excel. A Instalação do [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] não instala a versão [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] do provedor, portanto, você deverá instalá-la manualmente se estiver usando pastas de trabalho de uma versão anterior.  
  
 **O segundo cenário** é quando você tem um servidor em um farm do SharePoint que executa os serviços do Excel, mas não [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]. Nesse caso, o servidor de aplicativo que executa os Serviços do Excel deve ser atualizado manualmente para usar uma versão mais nova do provedor. Isso é necessário para conectar-se a uma instância do PowerPivot para SharePoint. Se os Serviços do Excel estiverem usando uma versão anterior do provedor, a solicitação de conexão falhará. Observe que o provedor deve ser instalado com a instalação do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou o pacote de instalação do [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] (spPowerPivot.msi) para se certificar de que todos os componentes que exigirem o suporte a [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] serão instalados.  
  
  
##  <a name="bkmk_sql11"></a> Instalar o SQL Server 2012 OLE DB Provider em um servidor de serviços do Excel usando a instalação do SQL Server  
 Use as instruções a seguir para adicionar o provedor OLE DB e outros componentes de conectividade de cliente aos SharePoint Servers que ainda não tenham esse recurso instalado, como servidores de aplicativo que executem os Serviços do Excel sem o PowerPivot para SharePoint no mesmo hardware.  
  
 Use estas instruções para instalar o provedor OLE DB do Analysis Services atual e adicionar o **Microsoft.AnalysisServices.Xmla.dll** ao assembly global.  
  
#### <a name="run-sql-server-setup-and-install-the-client-connectivity-tools"></a>Executar a instalação do SQL Server e instalar as Ferramentas de Conectividade de Cliente  
  
1.  No servidor de aplicativo que hospeda os Serviços do Excel, execute a instalação do SQL Server.  
  
2.  Na página de instalação, escolha **instalação autônoma do novo SQL Server ou adicionar recursos a uma instalação existente**.  
  
3.  Na página tipo de instalação, escolha **executar uma nova instalação do SQL Server 2012**.  
  
4.  Na página função de instalação, escolha **instalação de recurso do SQL Server**.  
  
5.  Sobre o **seleção de recursos** , clique em **conectividade das ferramentas de cliente**. Esta opção instala **Microsoft.AnalysisServices.Xmla.dll**  
  
     Não selecione nenhum outro recurso.  
  
6.  Clique em **próxima** para concluir o assistente e, em seguida, clique em **instalar** para executar a instalação.  
  
7.  Repita as etapas anteriores se você tiver outros servidores executando Serviços do Excel, sem uma instalação do PowerPivot para SharePoint no mesmo servidor.  
  
#### <a name="verify-msolap5-is-a-trusted-provider"></a>Verifique se MSOLAP.5 é um provedor de confiança  
  
1.  Na Administração Central, clique em **Gerenciar aplicativos de serviço**e clique no aplicativo de serviço de Serviços do Excel.  
  
2.  Clique em **Provedores de Dados Confiáveis**.  
  
3.  Verifique se MSOLAP.5 aparece na lista. Dependendo do modo como você configurou o PowerPivot para SharePoint, o MSOLAP.5 talvez já seja confiável. Se você usasse a ferramenta de Configuração do PowerPivot, mas excluísse essa ação da lista de tarefas, o MSOLAP.5 não será confiável para os Serviços do Excel e deverá ser adicionado manualmente.  
  
4.  Se MSOLAP não estiver listado, clique em **Adicionar provedor de dados confiável**.  
  
5.  Na ID do provedor, digite `MSOLAP.5`.  
  
6.  Em Tipo de Provedor, verifique se a opção OLE DB está selecionada.  
  
7.  Na Descrição do Provedor, digite **Microsoft OLE DB Provider for OLAP Services 11.0**.  
  
#### <a name="verify-installation"></a>Verifique a instalação  
  
1.  Vá para Arquivos de Programas\Microsoft Analysis Services\AS OLEDB\110.  
  
2.  Clique com o botão direito do mouse em msolap110.dll e selecione **Propriedades**.  
  
3.  Clique em **Detalhes**.  
  
4.  Exiba as informações de versão do arquivo. A versão deve incluir 11.00.<BuildNumber&gt. \<número_da_compilação >.  
  
5.  Na pasta Windows\assembly, verifique se Microsoft.AnalysisServices.Xmla.dll, versão 11.0.0.0 está listado.  
  
  
##  <a name="bkmk_install2012_from_sppowerpivot_msi"></a> Use o PowerPivot para o pacote de instalação do SharePoint (sppowerpivot. msi) para instalar o SQL Server 2012 OLE DB Provider  
 Instalar o [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] OLE DB Provider em e servidor de serviços do Excel usando o [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] pacote de instalação **(sppowerpivot. msi)**.  
  
#### <a name="download-the-msolap5-provider-from-the-includesssql11sp1includessssql11sp1-mdmd-feature-pack"></a>Baixe o provedor MSOLAP.5 do [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] Feature Pack.  
  
1.  Navegue até [Microsoft® SQL Server® 2012 SP1 Feature Pack](http://www.microsoft.com/download/details.aspx?id=35580)  
  
2.  Clique em **instruções de instalação**.  
  
3.  Consulte a seção "Microsoft Analysis Services OLE DB Provider para Microsoft SQL Server 2012 SP1". Baixe o arquivo e inicie a instalação.  
  
4.  Sobre o **seleção de recursos** página, selecione **Analysis Services OLE DB Provider for SQL Server**. Desmarque os outros componentes e conclua a instalação. Para obter mais informações sobre o sppowerpivot. msi, consulte [instalar ou desinstalar o PowerPivot para SharePoint Add-in &#40;SharePoint 2013&#41;](../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md).  
  
5.  Registre o MSOLAP.5 como um provedor confiável em Serviços do Excel do SharePoint. Para obter mais informações, consulte [Add MSOLAP.5 as a Trusted Data Provider in Excel Services](http://technet.microsoft.com/library/hh758436.aspx).  
  
  
##  <a name="bkmk_kj"></a> Instalar o provedor SQL Server 2008 R2 OLE DB para hospedar anteriormente pastas de trabalho de versão  
 Use as instruções seguintes para instalar a versão [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] do provedor de MSOLAP.4 e registrar o arquivo Microsoft.AnalysisServices.ChannelTransport.dll arquivo. O ChannelTransport é um subcomponente do provedor OLE DB do Analysis Services. A versão [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] do provedor lê o registro ao usar ChannelTransport para fazer uma conexão. Registrar esse arquivo é uma etapa pós-instalação necessária somente para conexões tratadas pelo provedor [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] em um servidor do [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  
  
#### <a name="step-1-download-and-install-the-client-library"></a>Etapa 1: baixar e instalar a biblioteca de cliente  
  
1.  Sobre o [página do SQL Server 2008 R2 Feature Pack](http://go.microsoft.com/fwlink/?LinkId=159570), localizar o Microsoft Analysis Services OLE DB Provider para Microsoft SQL Server 2008 R2.  
  
2.  Baixe o Pacote x64 do programa de instalação `SQLServer2008_ASOLEDB10.msi`. Embora o nome do arquivo contenha SQLServer2008, é o arquivo correto para a versão do SQL Server 2008 R2 do provedor.  
  
3.  No computador que tem uma instalação do [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)], execute o .msi para instalar a biblioteca.  
  
4.  Se você houver outros servidores no farm que executam apenas os Serviços do Excel, sem o [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] no mesmo servidor, repetir as etapas anteriores para instalar a versão 2008 R2 do provedor no computador com Serviços do Excel.  
  
#### <a name="step-2-register-the-microsoftanalysisserviceschanneltransportdll-file"></a>Etapa 2: registrar o arquivo Microsoft.AnalysisServices.ChannelTransport.dll  
  
1.  Use o utilitário regasm.exe para registrar o arquivo. Se você não executou regasm.exe antes, adicione sua pasta pai, c:\windows\microsoft.net\framework64\v4.0.30319>Aspnet_regiis.exe\\, para a variável de caminho do sistema.  
  
2.  Abra um prompt de comando com permissões de administrador.  
  
3.  Vá para esta pasta C: \Windows\assembly\GAC_MSIL\Microsoft.AnalysisServices.ChannelTransport\10.0.0.0__89845dcd8080cc91  
  
4.  Digite este comando: `regasm microsoft.analysisservices.channeltransport.dll`  
  
5.  Repita as etapas anteriores para qualquer computador no qual você instalou a versão 2008 R2 do provedor manualmente.  
  
#### <a name="verify-installation"></a>Verifique a instalação  
  
1.  Agora você já deve poder dividir ou filtrar pastas de trabalho do [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]. Se um erro ocorrer, verifique se você usou a versão de 64 bits de regasm.exe para registrar o arquivo.  
  
2.  Além disso você pode verificar a versão de arquivo.  
  
     Vá para `C:\Program files\Microsoft Analysis Services\AS OLEDB\10`. Clique com botão direito **msolap100.dll** e selecione **propriedades**. Clique em **Detalhes**.  
  
     Exiba as informações de versão do arquivo. A versão deve incluir 10.50. \<número_da_compilação >.  
  
  
## <a name="see-also"></a>Consulte também  
 [Instalação do PowerPivot para SharePoint 2010](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  