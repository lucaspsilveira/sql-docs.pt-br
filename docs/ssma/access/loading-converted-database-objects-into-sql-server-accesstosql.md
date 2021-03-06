---
title: Carregando objetos de banco de dados convertidos em SQL Server (AccessToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Access databases, loading converted objects into SQL Azure
- Access databases, loading converted objects into SQL Server
- data, securing
- loading objects into SQL Azure
- loading objects into SQL Server
- migrating objects into SQL Azure
- migrating objects into SQL Server
- moving objects into SQL Azure
- moving objects into SQL Server
- schemas, loading into SQL Azure
- schemas, loading into SQL Server
- scripting converted objects
- securing data
- SQL Azure, loading objects into
- SQL Server, loading objects into
- synchronizing metadata with SQL Azure
- synchronizing metadata with SQL Server
- uploading objects into SQL Azure
- uploading objects into SQL Server
ms.assetid: 4e854eee-b10c-4f0b-9d9e-d92416e6f2ba
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 7effaa973b7a39df6fc0b9385a5cfde4fdad18d4
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67986316"
---
# <a name="loading-converted-database-objects-into-sql-server-accesstosql"></a>Carregando objetos de banco de dados convertidos em SQL Server (AccessToSQL)
Depois de ter convertido objetos de banco de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dados do Access para o ou SQL Azure, você pode carregar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] os objetos de banco de dados resultantes no ou SQL Azure. Você pode fazer com que o SSMA crie os objetos, ou pode criar o script dos objetos e executar os scripts por conta própria. Além disso, o SSMA permite que você atualize os metadados de destino [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] com o conteúdo real do banco de dados ou SQL Azure.  
  
## <a name="choosing-between-synchronization-and-scripts"></a>Escolhendo entre a sincronização e os scripts  
Se você quiser carregar os objetos de banco de dados [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] convertidos no ou SQL Azure sem modificação, poderá fazer com que o SSMA crie ou recrie os objetos de banco de dados diretamente. Esse método é rápido e fácil, mas não permite a [!INCLUDE[tsql](../../includes/tsql-md.md)] personalização do código que define os [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objetos ou SQL Azure, além de procedimentos armazenados.  
  
Se você quiser modificar o que [!INCLUDE[tsql](../../includes/tsql-md.md)] é usado para criar objetos ou se quiser mais controle sobre a criação de objetos, use o SSMA para criar scripts. Em seguida, você pode modificar esses scripts, criar cada objeto individualmente e até [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mesmo usar o Agent para agendar a criação desses objetos.  
  
## <a name="using-ssma-to-synchronize-objects-with-sql-server"></a>Usando o SSMA para sincronizar objetos com SQL Server  
Para usar o SSMA para [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] criar ou SQL Azure objetos de banco de dados, você [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] seleciona os objetos no ou SQL Azure o Gerenciador de metadados e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , em seguida, sincroniza os objetos com ou SQL Azure, conforme mostrado no procedimento a seguir. Por padrão, se os objetos já existirem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no ou SQL Azure, e se os metadados do SSMA tiverem algumas alterações locais ou atualizações na definição desses objetos, o SSMA alterará as definições de objeto no [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure. Você pode alterar o comportamento padrão editando **as configurações do projeto**.  
  
> [!NOTE]  
> Você pode selecionar objetos [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de banco de dados existentes ou SQL Azure que não foram convertidos de bancos de dados do Access. No entanto, o SSMA não recriará nem alterará esses objetos.  
  
**Para sincronizar objetos com SQL Server ou SQL Azure**  
  
1.  No [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure Gerenciador de metadados, expanda [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o nó superior ou SQL Azure e, em seguida, expanda **bancos de dados**.  
  
2.  Selecione os objetos a serem processados:  
  
    -   Para sincronizar um banco de dados completo, marque a caixa de seleção ao lado do nome do banco de dados.  
  
    -   Para sincronizar ou omitir objetos individuais ou categorias de objetos, marque ou desmarque a caixa de seleção ao lado do objeto ou da pasta.  
  
3.  Depois de selecionar os objetos a serem processados [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure o Gerenciador de metadados, clique com o botão direito do mouse em **bancos**de dados e clique em **sincronizar com o Database**.  
  
    Você também pode sincronizar objetos individuais ou categorias de objetos clicando com o botão direito do mouse no objeto ou em sua pasta pai e clicando em **sincronizar com o banco de dados**.  
  
    Depois disso, o SSMA exibirá a caixa de diálogo **sincronizar com o banco de dados** , onde você poderá ver dois grupos de itens. No lado esquerdo, o SSMA mostra os objetos de banco de dados selecionados representados em uma árvore. No lado direito, você pode ver uma árvore que representa os mesmos objetos em metadados do SSMA. Você pode expandir a árvore clicando no botão à direita ou à esquerda ' + '. A direção da sincronização é mostrada na coluna ação colocada entre as duas árvores.  
  
    Um sinal de ação pode estar em três Estados:  
  
    -   Uma seta para a esquerda significa que o conteúdo dos metadados será salvo no banco de dados (o padrão).  
  
    -   Uma seta para a direita significa que o conteúdo do banco de dados substituirá os metadados do SSMA.  
  
    -   Um sinal cruzado significa que nenhuma ação será executada.  
  
    Clique no sinal de ação para alterar o estado. A sincronização real será executada quando você clicar no botão **OK** da caixa de diálogo **sincronizar com Banco de dados** .  
  
## <a name="scripting-objects"></a>Objetos de script  
Se você quiser salvar [!INCLUDE[tsql](../../includes/tsql-md.md)] as definições dos objetos de banco de dados convertidos ou desejar alterar as definições de objeto e executar scripts por conta própria, poderá salvar as definições de objeto [!INCLUDE[tsql](../../includes/tsql-md.md)] de banco de dados convertido em scripts.  
  
**Para salvar um ou mais objetos em um script**  
  
1.  No [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Gerenciador de metadados, expanda o nó superior (o nome do servidor) e, em seguida, expanda **bancos de dados**.  
  
2.  Execute uma ou mais das seguintes opções:  
  
    -   Para gerar script de um banco de dados completo, marque a caixa de seleção ao lado do nome do banco de dados.  
  
    -   Para gerar script ou omitir exibições individuais, expanda o banco de dados, expanda **exibições**e marque ou desmarque a caixa de seleção ao lado da exibição.  
  
    -   Para criar um script ou omitir tabelas individuais, expanda o banco de dados, expanda **tabelas**e marque ou desmarque a caixa de seleção ao lado da tabela.  
  
    -   Para criar o script ou omitir índices individuais para uma tabela, expanda a tabela, expanda **índices**e selecione ou limpe o índice.  
  
3.  Clique com o botão direito do mouse em **bancos de dados** e selecione **salvar como script**.  
  
    Você também pode criar scripts de objetos individuais. Para criar um script de um objeto, independentemente dos objetos selecionados, clique com o botão direito do mouse no objeto e selecione **salvar como script**.  
  
4.  Na caixa de diálogo **salvar como** , localize a pasta onde você deseja salvar o script, insira um nome de arquivo na caixa **nome do arquivo** e clique em **OK**.  
  
    O SSMA acrescentará a extensão de nome de arquivo. Sql.  
  
### <a name="modifying-scripts"></a>Modificando scripts  
Depois de salvar as definições [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de objeto do ou do SQL Azure como um script, você [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pode usar o para modificar o script.  
  
**Para modificar um script**  
  
1.  No menu [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] **Arquivo** , aponte para **Abrir**e clique em **Arquivo**.  
  
2.  Na caixa de diálogo **abrir** , localize e selecione o arquivo de script e clique em **OK**.  
  
3.  Edite o arquivo de script usando o editor de consultas.  
  
    Para obter mais informações sobre o editor de consultas, consulte "comandos e recursos de conveniência [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] do editor" nos manuais online do.  
  
4.  Para salvar o script, no menu arquivo, selecione **salvar**.  
  
### <a name="running-scripts"></a>Executando scripts  
Você pode executar um script, ou instruções individuais, no [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
**Para executar um script**  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] No menu **arquivo** , aponte para **abrir** e clique em **arquivo**.  
  
2.  Na caixa de diálogo **abrir** , localize e selecione o arquivo de script e clique em **OK**.  
  
3.  Para executar o script completo, pressione a tecla **F5** .  
  
4.  Para executar um conjunto de instruções, selecione as instruções na janela do editor de consultas e pressione a tecla **F5** .  
  
Para obter mais informações sobre como usar o editor de consultas para executar scripts, consulte [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] "consultar" [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nos manuais online do.  
  
Você também pode executar scripts na linha de comando usando o utilitário **sqlcmd** e do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Para obter mais informações sobre o **sqlcmd**, consulte o "utilitário [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sqlcmd" nos manuais online do. Para obter mais informações [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sobre o Agent, consulte "automatizando tarefas [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] administrativas (agente) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] " nos manuais online do.  
  
## <a name="securing-objects-in-sql-server"></a>Protegendo objetos no SQL Server  
Depois de carregar os objetos de banco de dados [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]convertidos no, você pode conceder e negar permissões nesses objetos. É uma boa ideia fazer isso antes de migrar dados para [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]o. Para obter informações sobre como ajudar a proteger objetos [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]no, consulte "considerações de segurança para bancos de dados e aplicativos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] banco de dados" nos manuais online do.  
  
## <a name="next-step"></a>Próxima etapa  
A próxima etapa no processo de migração é [migrar dados para o SQL Server](migrating-access-data-into-sql-server-azure-sql-db-accesstosql.md).  
  
## <a name="see-also"></a>Consulte Também  
[Migrando bancos de dados do Access para SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
