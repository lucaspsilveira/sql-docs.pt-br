---
title: 'Etapa 2: executar o Assistente de Instalação de Pacotes | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f91fbb89-4626-4c47-b96d-56052dc45861
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 52b0ee24cc9e76bda96b5fda64bf8dca425c5638
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37300566"
---
# <a name="step-2-running-the-package-installation-wizard"></a>Etapa 2: Executando o Assistente de Instalação de Pacotes
  Nesta tarefa, você executará o Assistente de Instalação de Pacotes para implantar os pacotes do projeto Tutorial de Implantação em uma instância do [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Somente pacotes podem ser instalados na tabela sysssispackages no banco de dados msdb do [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Os arquivos que dão suporte incluídos no pacote de implantação serão implantados no sistema de arquivos.  
  
 O Assistente de Instalação de Pacotes o guiará pelas etapas para instalar e configurar os pacotes. Você instalará os pacotes em uma instância do [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] no computador de destino (o computador em que você copiou o pacote de implantação). Você também criará uma pasta, C:\DeploymentTutorialInstall, em que o assistente instalará os arquivos que não são pacotes.  
  
 Em uma lição anterior, você modificou os pacotes no tutorial para usar as configurações. Usando o Assistente de Instalação de Pacotes, você editará essas configurações para habilitar os pacotes a serem executados com êxito no ambiente em que foram instalados.  
  
### <a name="to-install-the-packages"></a>Para instalar os pacotes  
  
1.  No computador de destino, localize o pacote de implantação.  
  
     Se você tiver usado o valor padrão – bin\Deployment – como local para o utilitário de implantação, o pacote de implantação será a pasta de Implantação do projeto Tutorial de Implantação.  
  
2.  Na pasta Implantação, clique duas vezes no arquivo de manifesto, Deployment Tutorial.SSISDeploymentManifest.  
  
3.  Na página inicial do Assistente de Instalação de Pacotes, clique em **Avançar**.  
  
4.  Na página Implantar Pacotes SSIS, selecione a opção **Implantação no SQL Server** , marque a caixa de seleção **Validar pacotes após instalação** e clique em **Avançar**.  
  
5.  Na página Especificar SQL Server de Destino, especifique o **(local)**, na caixa **Nome do servidor** .  
  
6.  Se a instância do SQL Server der suporte à Autenticação do Windows, selecione **Usar Autenticação do Windows**; caso contrário, selecione **Usar Autenticação do SQL Server** e forneça um nome de usuário e uma senha.  
  
7.  Verifique se a caixa de seleção **Depender do armazenamento do servidor para criptografia** está desmarcada.  
  
8.  Clique em **Avançar**.  
  
9. Na página Selecionar Pasta de Instalação, clique em **Procurar**.  
  
10. Na caixa de diálogo **Procurar Pasta** , expanda **Meu Computador** e clique em **Disco Local (C:)**.  
  
11. Clique em **Criar Nova Pasta** e substitua o nome padrão da pasta criada, **Nova Pasta**, por **DeploymentTutorialInstall**.  
  
    > [!IMPORTANT]  
    >  Este nome é mencionado no valor das variáveis de ambiente usado pelas configurações. O nome da pasta e a referência devem coincidir ou o pacote não será executado.  
  
12. Clique em **OK**.  
  
13. Na página Selecionar Pasta de Instalação, verifique se a caixa Pasta contém **C:\DeploymentTutorialInstall** e clique em **Avançar**.  
  
14. Na página Confirmar Instalação, clique em **Avançar**.  
  
     O assistente instala os pacotes. Depois que a instalação for concluída, a página Configurar Pacotes será aberta.  
  
15. Na página Configurar Pacotes, verifique se a caixa **Arquivo de configuração** lista datatransferconfig.dtsconfig e loadxmldataconfig.dtsconfig.  
  
16. Na lista **Arquivo de configuração** , clique em **datatransferconfig.dtsconfig**, expanda Propriedades na coluna **Caminho** da caixa **Configurações** e atualize a coluna **Valor** com os seguintes valores:  
  
    |Propriedade|Valor|Valor atualizado|  
    |--------------|-----------|-------------------|  
    |\Package.Connections[Deployment Tutorial Log].Properties[ConnectionString]|C:\Arquivos de Programas\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Completed Packages\Deployment Tutorial Log|C:\DeploymentTutorialInstall\Deployment Tutorial Log|  
    |\Package.Connections[NewCustomers].Properties[ConnectionString]|C:\Arquivos de Programas\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Sample Data\NewCustomers.txt|C:\DeploymentTutorialInstall\NewCustomers.txt|  
  
17. Na lista **Arquivo de configuração** , clique em loadxmldataconfig.dtsconfig, expanda Propriedades na coluna **Caminho** da caixa **Configurações** e atualize a coluna **Valor** com os seguintes valores:  
  
    |Propriedade|Valor|Valor atualizado|  
    |--------------|-----------|-------------------|  
    |\Package.LoadXMLData.Properties[[XML Source].[XMLData]]|C:\Arquivos de Programas\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Sample Data\orders.xml|C:\DeploymentTutorialInstall\orders.xml|  
    |\Package.LoadXMLData.Properties[[XML Source].[XMLSchemaDefinition]]|C:\Arquivos de Programas\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Sample Data\orders.xsd|C:\DeploymentTutorialInstall\orders.xsd|  
  
18. Na página Validação de Pacote, exiba os resultados de validação de cada pacote instalado e clique em **Avançar**.  
  
     Como os valores das variáveis de ambiente no computador de destino diferem dos valores das variáveis de ambiente no computador de desenvolvimento, várias avisos são exibidos na página Validação de Pacote. Você deve esperar por quatro avisos:  
  
    -   O arquivo de configuração: “C:\DeploymentTutorial\DataTransferConfig.dtsConfig” não é válido. Verifique o nome do arquivo de configuração.  
  
    -   Falha ao carregar pelo menos uma das entradas de configuração no pacote. Verifique as entradas de configuração e os avisos anteriores para ver a descrição da configuração em que houve falha.  
  
    -   O arquivo de configuração: “C:\DeploymentTutorial\LoadXMLDataConfig.dtsConfig” não é válido. Verifique o nome do arquivo de configuração.  
  
    -   Falha ao carregar pelo menos uma das entradas de configuração no pacote. Verifique as entradas de configuração e os avisos anteriores para ver a descrição da configuração em que houve falha.  
  
     Esses avisos não afetam a instalação do pacote.  
  
     Se você não tiver selecionado a opção **Validar pacotes após instalação** na página Implantar Pacotes SSIS, as páginas Validação de Pacote não serão abertas e o assistente não exibirá as informações da instalação pós-validação.  
  
19. Na página Concluir o Assistente de Instalação de Pacotes, leia o resumo da instalação e clique em **Concluir**.  
  
    > [!NOTE]  
    >  Um arquivo de log temporário é criado para ser usado na validação do pacote. Esse arquivo não é usado quando o pacote é executado.  
  
## <a name="next-task-in-lesson"></a>Próxima tarefa da lição  
 [Etapa 3: Testando os pacotes implantados](../integration-services/lesson-3-3-testing-the-deployed-packages.md)  
  
![Ícone do Integration Services (pequeno)](media/dts-16.gif "ícone do Integration Services (pequeno)")**mantenha-se para cima até o momento com o Integration Services  **<br /> Para obter os downloads, artigos, exemplos e vídeos mais recentes da Microsoft, assim como soluções selecionadas pela comunidade, visite a página do [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] no MSDN:<br /><br /> [Visite a página do Integration Services no MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Para receber uma notificação automática dessas atualizações, assine os RSS feeds disponíveis na página.  
  
## <a name="see-also"></a>Consulte também  
 [Serviço Integration Services &#40;serviço SSIS&#41;](service/integration-services-service-ssis-service.md)   
 [Gerenciar o serviço Integration Services](../../2014/integration-services/manage-the-integration-services-service.md)  
  
  