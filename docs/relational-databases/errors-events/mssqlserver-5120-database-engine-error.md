---
title: MSSQLSERVER_5228 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 5120 (Database Engine error)
ms.assetid: ''
author: PijoCoder
ms.author: mathoma
ms.openlocfilehash: ff8fb262b643390f2914a4a5e6c42dcc887206f8
ms.sourcegitcommit: 66407a7248118bb3e167fae76bacaa868b134734
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81728613"
---
# <a name="mssqlserver_5120"></a>MSSQLSERVER_5120
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Detalhes  
  
|||  
|-|-|  
|Nome do Produto|SQL Server|  
|ID do evento|5120|  
|Origem do Evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbólico|DSK_FCB_FAILURE|  
|Texto da mensagem|Erro de tabela: Não é possível abrir o arquivo físico "%.*ls". Erro no sistema operacional %d: “%ls”.|  
  
## <a name="explanation"></a>Explicação  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] não conseguiu abrir um arquivo de banco de dados.  O erro do sistema operacional fornecido na mensagem aponta para os motivos subjacentes mais específicos da falha. Normalmente, você pode ver esse erro junto com outros, como [17204](mssqlserver-17204-database-engine-error.md) ou [17207](mssqlserver-17207-database-engine-error.md)
  
## <a name="user-action"></a>Ação do usuário  
  
  Faça o diagnóstico, corrija o erro e, em seguida, tente novamente a operação. Existem vários estados que podem ajudar a Microsoft a restringir a área de ocorrência no produto. 
  
### <a name="access-is-denied"></a>Acesso negado 
Se você receber o erro do sistema operacional ```Access is Denied``` = 5, considere estes métodos:
   -  Verifique se as permissões estão definidas no arquivo examinando as propriedades dele no Windows Explorer. O [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usa grupos do Windows para provisionar o Controle de Acesso em vários recursos do arquivo. Verifique se o grupo apropriado [com nomes como SQLServerMSSQLUser$ComputerName$MSSQLSERVER ou SQLServerMSSQLUser$ComputerName$InstanceName] tem as permissões necessárias no arquivo de banco de dados mencionado na mensagem de erro. Para obter mais informações, confira [Configurar permissões do sistema de arquivos para acesso ao Mecanismo de Banco de Dados](../../2014/database-engine/configure-windows/configure-file-system-permissions-for-database-engine-access.md). Verifique se o grupo do Windows realmente inclui a conta de inicialização do serviço [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou o SID do serviço.
   -  Examine a conta de usuário na qual o serviço do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] está atualmente em execução. Você pode usar o Gerenciador de Tarefas do Windows para obter essas informações. Procure o valor de "Nome de Usuário" para o executável "sqlservr.exe". Além disso, se você alterou recentemente a conta de serviço [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], saiba que a maneira com suporte para realizar essa operação é usar o utilitário [SQL Server Configuration Manager](../sql-server-configuration-manager.md). 
   -  Dependendo do tipo de operação – abrir bancos de dados durante a inicialização do servidor, anexar um banco de dados, restaurar o banco de dados etc. – a conta usada para representação e acesso ao arquivo de banco de dados pode variar. Examine o tópico [Proteger arquivos de log e dados](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms189128(v=sql.105)?redirectedfrom=MSDN) para entender qual operação define qual permissão e de quais contas. Use uma ferramenta como [Monitor do Processo](https://docs.microsoft.com/sysinternals/downloads/procmon) do SysInternals do Windows para entender se o acesso ao arquivo está acontecendo no contexto de segurança da conta de inicialização do serviço (ou SID do serviço) da instância [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou de uma conta representada.

      Se [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] estiver representando as credenciais de usuário do logon que executa a operação ALTER DATABASE ou CREATE DATABASE, você observará as seguintes informações na ferramenta Monitor do Processo (um exemplo):
        ```Date & Time:      3/27/2010 8:26:08 PM
        Event Class:        File System
        Operation:          CreateFile
        Result:                ACCESS DENIED
        Path:                  C:\Program Files\Microsoft SQL Server\MSSQL13.SQL2016\MSSQL\DATA\attach_test.mdf
        TID:                   4288
        Duration:             0.0000366
        Desired Access:Generic Read/Write
        Disposition:        Open
        Options:            Synchronous IO Non-Alert, Non-Directory File, Open No Recall
        Attributes:          N
        ShareMode:       Read
        AllocationSize:   n/a
        Impersonating: DomainName\UserName```
  
  
### Attaching Files that Reside on a Network-attached storage  
If you cannot re-attach a database that resides on network-attached storage, a message like this may be logged in the Application log:

```Msg 5120, Level 16, State 101, Line 1 Unable to open the physical file "\\servername\sharename\filename.mdf". Operating system error 5: (Access is denied.).```

This problem occurs because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resets the file permissions when the database is detached. When you try to reattach the database, a failure occurs because of limited share permissions.

To resolve, follow these steps:
1. Use the -T startup option to start [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Use this startup option to turn on trace flag 1802 in [SQL Server Configuration Manager](../sql-server-configuration-manager.md) (see [Trace Flags](../../t-sql/database-console-commands/dbcc-traceon-transact-sql.md) for information on 1802). For more information about how to change the startup parameters, see [Database Engine Service Startup Options](../../database-engine/configure-windows/database-engine-service-startup-options.md)

2. Use the following command to detach the database.
```tsql
 exec sp_detach_db DatabaseName
 go 
```

3. Use o comando a seguir para reconectar o banco de dados.
```tsql
exec sp_attach_db DatabaseName, '\\Network-attached storage_Path\DatabaseMDFFile.mdf', '\\Network-attached storage_Path\DatabaseLDFFile.ldf'
go
```
 
