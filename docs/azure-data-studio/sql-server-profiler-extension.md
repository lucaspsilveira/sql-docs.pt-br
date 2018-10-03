---
title: Extensão de dados Studio SQL Server Profiler do Azure | Microsoft Docs
description: Extensão do SQL Server Profiler (visualização) para o Studio de dados do Azure
ms.custom: tools|sos
ms.date: 09/24/2018
ms.reviewer: alayu; sstein
ms.prod: sql
ms.prod_service: sql-tools
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: f92391c3d18648555a0c65d55915bf6752c195b8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "48037687"
---
# <a name="sql-server-profiler-extension-preview"></a>Extensão do SQL Server Profiler (visualização)

A extensão do SQL Server Profiler (versão prévia) fornece uma solução simples de rastreamento de SQL Server semelhante ao Profiler do SQL Server Management Studio (SSMS), exceto criados usando o XEvents. SQL Server Profiler é muito fácil de usar e tem bons valores padrão para as configurações de rastreamento mais comuns. A experiência do usuário é otimizada para navegação por meio de eventos e exibindo o texto associado do Transact-SQL (T-SQL). O Profiler de servidor SQL para o Studio de dados do Azure também pressupõe que bons valores padrão para coleta de atividades de execução de T-SQL com uma experiência do usuário fácil de usar. Esta extensão está atualmente em visualização.

**SQL Profiler-casos de uso comuns:**

- Percorrer consultas de problemas para localizar a causa do problema.
- Localizar e diagnosticar consultas de execução lenta.
- Capturar a série de instruções Transact-SQL que levam a um problema.
- Monitorando o desempenho do SQL Server para ajustar cargas de trabalho.
- Correlacionar contadores de desempenho para diagnosticar problemas.


## <a name="install-the-sql-server-profiler-extension"></a>Instalar a extensão do SQL Server Profiler

1. Para abrir o Gerenciador de extensões e acessar as extensões disponíveis, selecione o ícone de extensões ou selecione **extensões** na **exibição** menu.
2. Selecione uma extensão disponível para exibir seus detalhes.

   ![Gerenciador de extensões do criador de perfil](media/extensions/sql-server-profiler-extension/profiler-extension.png)

1. Selecione a extensão desejada e **instalar** -lo.
2. Selecione **recarregar** para habilitar a extensão (necessário somente na primeira vez que você instalar uma extensão).

## <a name="start-profiler"></a>Iniciar o Profiler

1. Para iniciar o Profiler, fazer uma conexão a um servidor na guia servidores.
2. Depois de fazer uma conexão, digite **Alt + P** para iniciar o Profiler.
3. Para iniciar o Profiler, digite **Alt + S.** Agora você pode começar a ver eventos estendidos.
    ![Gerenciador de extensões do criador de perfil](media/extensions/sql-server-profiler-extension/view-profiler.png)    
1. Para parar o Profiler, digite **Alt + S.** Esta tecla de acesso é um controle de alternância.

## <a name="next-steps"></a>Próximas etapas

Para saber mais sobre o Profiler e eventos estendidos, consulte [eventos estendidos](https://docs.microsoft.com/sql/relational-databases/extended-events/extended-events).




