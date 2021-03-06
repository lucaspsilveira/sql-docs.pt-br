---
title: Ajuda F1 do Visualizador do Arquivo de Log | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.configurelogs.errorlog.f1
helpviewer_keywords:
- Log File Viewer
ms.assetid: 2243845c-4880-4aa0-9ee8-0a97a128996b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3ce118fb3234d45ae0606fb4bcc99777a945acda
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63143821"
---
# <a name="log-file-viewer-f1-help"></a>Ajuda F1 do Visualizador do Arquivo de Log
  O Visualizador do Arquivo de Log exibe informações de muitos componentes diferentes. Quando o Visualizador do Arquivo de Log estiver aberto, use o painel **Selecionar logs** para selecionar os logs que deseja exibir. Cada log exibe as colunas adequadas àquele tipo de log.  
  
 Os logs disponíveis dependem de como o Visualizador do Arquivo de Log é aberto. Para obter mais informações, consulte [Abrir o Visualizador do Arquivo de Log](open-log-file-viewer.md).  
  
 O número de linhas exibidas para logs de auditoria pode ser configurado na página **Pesquisador de Objetos do SQL Server/Comandos** da caixa de diálogo **Ferramentas/Opções** . Para obter descrições das colunas exibidas para logs de auditoria, consulte [sys.fn_get_audit_file &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-get-audit-file-transact-sql).  
  
## <a name="options"></a>Opções  
 **Carregar Log**  
 Abra uma caixa de diálogo onde seja possível especificar um arquivo de log a ser carregado.  
  
 **Exportar**  
 Abra uma caixa de diálogo que permita exportar as informações mostradas na grade **Resumo do arquivo de log** para um arquivo de texto.  
  
 **Atualizar**  
 Atualize a exibição dos logs selecionados. O botão **Atualizar** relê os logs selecionados do servidor de destino ao aplicar qualquer configuração de filtro.  
  
 **Filter**  
 Abra uma caixa de diálogo que permita especificar configurações usadas para filtrar o arquivo de log, como **Conexão**, **Data**ou outros critérios de filtragem **Gerais** .  
  
 **Pesquisar**  
 Pesquise o texto específico no arquivo de log. Não há suporte à pesquisa com caracteres curinga.  
  
 **Parar**  
 Interrompe o carregamento das entradas do arquivo de log. Por exemplo, você poderá usar essa opção se um arquivo de log remoto ou offline demorar muito tempo para ser carregado e você desejar exibir apenas as entradas mais recentes.  
  
 **Resumo do arquivo de log**  
 Esse painel de informações exibe um resumo da filtragem do arquivo de log. Se o arquivo não for filtrado, você verá o seguinte texto, **Nenhum filtro aplicado**. Se um filtro for aplicado ao log, você verá o texto **Filtrar entradas do log, em que:**  \<critérios do filtro>.  
  
 **Detalhes da linha selecionada**  
 Selecione uma linha para exibir detalhes adicionais sobre a linha de evento selecionada na parte inferior da página. As colunas podem ser reordenadas arrastando-as para locais novos na grade. As colunas podem ser redimensionadas arrastando para a esquerda ou direta as barras separadoras de coluna no cabeçalho de grade. Clique duas vezes nas barras separadoras de coluna no cabeçalho da grade para dimensionar automaticamente a coluna para a largura do conteúdo.  
  
 **Instância**  
 O nome da instância do na qual ocorreu o evento. Esse nome é exibido como *nome do computador*\\*nome da instância*.  
  
## <a name="frequently-displayed-columns"></a>Colunas exibidas frequentemente  
 **Data**  
 Exibe a data do evento.  
  
 **Origem**  
 Exibe o recurso de origem do qual o evento é criado, como o nome do serviço (MSSQLSERVER, por exemplo). Isso não é exibido para todos os tipos de log.  
  
 **Mensagem**  
 Exibe todas as mensagens associadas ao evento.  
  
 **Tipo de Log**  
 Exibe o tipo de log ao qual o evento pertence. Todos os logs selecionados são exibidos na janela de resumo de arquivo de log.  
  
 **Origem do Log**  
 Exibe uma descrição do log de origem no qual o evento é capturado.  
  
## <a name="permissions"></a>Permissões  
 Para acessar arquivos de log de instâncias do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] que estão online, é necessária associação na função de servidor fixa securityadmin.  
  
 Para acessar arquivos de log de instâncias do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] que estão offline, é necessário ter acesso de leitura no namespace do WMI **Root\Microsoft\SqlServer\ComputerManagement10** e na pasta em que os arquivos de log estão armazenados. Para obter mais informações, veja a seção Segurança do tópico [Exibir arquivos de log offline](view-offline-log-files.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Visualizador do Arquivo de Log](log-file-viewer.md)   
 [Abrir o Visualizador do Arquivo de Log](open-log-file-viewer.md)   
 [Exibir arquivos de log offline](view-offline-log-files.md)  
  
  
