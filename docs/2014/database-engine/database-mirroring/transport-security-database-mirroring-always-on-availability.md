---
title: Segurança de transporte para espelhamento de banco de dados e Grupos de Disponibilidade AlwaysOn (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- sessions [SQL Server], database mirroring
- cryptography [SQL Server], database mirroring
- certificates [SQL Server], database mirroring
- encryption [SQL Server], database mirroring
- Windows authentication [SQL Server]
- authentication [SQL Server], database mirroring
- transport security
- database mirroring [SQL Server], security
ms.assetid: 49239d02-964e-47c0-9b7f-2b539151ee1b
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 18b52163cb1e8c6be0cf7fdea37861662d6e4830
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62754293"
---
# <a name="transport-security-for-database-mirroring-and-alwayson-availability-groups-sql-server"></a>Segurança de transporte para espelhamento de banco de dados e grupos de disponibilidade AlwaysOn (SQL Server)
  A segurança de transporte envolve autenticação e, como opção, criptografia de mensagens trocadas entre os bancos de dados. Para o espelhamento de banco de dados e [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], a autenticação e a criptografia são configuradas no ponto de extremidade do espelhamento de banco de dados. Para obter uma introdução aos pontos de extremidade de espelhamento de banco de dados, consulte [O ponto de extremidade de espelhamento de banco de dados &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md).  
  

  
##  <a name="authentication"></a><a name="Authentication"></a> Autenticação  
 Autenticação é o processo de verificar se um usuário é quem o usuário diz ser. Conexões entre pontos de extremidade espelhamento de banco de dados requerem autenticação. Exigências de conexão de um parceiro ou testemunha, se existir, devem ser autenticadas.  
  
 O tipo de autenticação usado por uma instância do servidor para o espelhamento de banco de dados ou [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] é uma propriedade do ponto de extremidade do espelhamento de banco de dados. Dois tipos de segurança de transporte estão disponíveis para pontos de extremidade do espelhamento de banco de dados: Autenticação do Windows (SSPI) e autenticação baseada em certificado.  
  
### <a name="windows-authentication"></a>Autenticação do Windows  
 Sob autenticação do Windows, cada instância de servidor faz o logon para o outro lado usando as credenciais da conta de usuário do Windows sob o qual o processo está sendo executado. A Autenticação do Windows pode exigir configuração manual de contas de logon, como segue:  
  
-   Se as instâncias do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] forem executadas como serviços sob a mesma conta de domínio, nenhuma configuração adicional será necessária.  
  
-   Se as instâncias do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] forem executadas como serviços em diferentes contas de domínio (nos mesmos domínios ou em domínios confiáveis), o logon de cada conta deverá ser criado no **mestre** em cada uma das outras instâncias de servidor, e esse logon deverá receber permissões CONNECT no ponto de extremidade.  
  
-   Se as instâncias do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] forem executadas como conta de serviço de rede, o logon da conta de cada computador host(*DomainName***\\***ComputerName$*) deverá ser criado no **mestre** em cada um dos outros servidores e esse logon deverá receber permissões CONNECT no ponto de extremidade. Isso é porque uma instância de servidor em execução sob a conta de serviço de rede é autenticada usando a conta de domínio do computador host.  
  
> [!NOTE]  
>  Para obter um exemplo de como configurar a sessão de espelhamento de banco de dados usando a Autenticação do Windows, consulte [Exemplo: Configurando o espelhamento de banco de dados usando a Autenticação do Windows &#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-windows-authentication-transact-sql.md).  
  
### <a name="certificates"></a>Certificados  
 Em algumas situações, como quando as instâncias de servidor não estão em domínios confiáveis ou quando o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] estiver executando como um serviço local, a Autenticação do Windows é indisponível. Em tais casos, em vez de credenciais de usuário, são exigidos certificados para autenticar solicitações de conexão. O ponto de extremidade do espelhamento de cada instância de servidor deve ser configurado com seu próprio certificado localmente criado.  
  
 O método de criptografia é estabelecido quando o certificado é criado. Para obter mais informações, consulte [Permitir que um ponto de extremidade de espelhamento de banco de dados use certificados para conexões de saída &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md). Administre cuidadosamente os certificados que você usa.  
  
 Uma instância de servidor usa a chave privada de seu próprio certificado para estabelecer sua identidade ao configurar uma conexão. A instância de servidor que recebe a solicitação de conexão usa a chave pública do certificado do remetente para autenticar a identidade do remetente. Por exemplo, considere duas instâncias de servidor, Server_A e Server_B. Server_A usa sua chave privada para criptografar o cabeçalho da conexão antes de enviar uma solicitação de conexão a Server_B. Server_B usa a chave pública do certificado de Server_A para descriptografar o cabeçalho da conexão. Se o cabeçalho descriptografado estiver correto, Server_B saberá que o cabeçalho foi criptografado por Server_A, e a conexão é autenticada. Se o cabeçalho descriptografado estiver incorreto, Server_B saberá que a solicitação de conexão não é autêntica e recusará a conexão.  
  
##  <a name="data-encryption"></a><a name="DataEncryption"></a>Criptografia de dados  
 Por padrão, um ponto de extremidade de espelhamento de banco de dados solicita a criptografia de dados enviados por conexões de espelhamento. Neste caso, os pontos de extremidade podem se conectar apenas a pontos de extremidade que também usam criptografia. A menos que você possa garantir que sua rede está segura, recomendamos que você solicite criptografia para suas conexões de espelhamento de banco de dados. Porém, você pode desabilitar a criptografia ou torná-la suportável, mas não obrigatória. Se a criptografia estiver desabilitada, nunca serão criptografados dados e os pontos de extremidade não poderão se conectar a um ponto de extremidade que solicita criptografia. Se a criptografia for suportada, só serão criptografados dados se o ponto de extremidade suportar ou solicitar criptografia.  
  
> [!NOTE]  
>  Os pontos de extremidade de espelhamento criados por [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] são criados com criptografia obrigatória ou desabilitada. Para alterar a configuração de criptografia para SUPPORTED, use a instrução ALTER ENDPOINT [!INCLUDE[tsql](../../includes/tsql-md.md)] . Para obter mais informações, consulte [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql).  
  
 Opcionalmente, você pode controlar os algoritmos de criptografia que podem ser usados por um ponto de extremidade, especificando um dos seguintes valores para a opção de ALGORITHM em uma instrução CREATE ENDPOINT ou instrução ALTER ENDPOINT:  
  
|Valor de ALGORITHM|Descrição|  
|---------------------|-----------------|  
|RC4|Especifica que o ponto de extremidade deve usar o algoritmo RC4. Esse é o padrão.<br /><br /> Observação: o algoritmo RC4 foi preterido. [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Recomendamos usar AES.|  
|AES|Especifica que o ponto de extremidade deve usar o algoritmo AES.|  
|AES RC4|Especifica que o dois pontos de extremidade negociarão por um algoritmo de criptografia com esse ponto de extremidade, dando preferência ao algoritmo AES.|  
|RC4 AES|Especifica que o dois pontos de extremidade negociarão por um algoritmo de criptografia com esse ponto de extremidade, dando preferência ao algoritmo RC4.|  
  
 Se os pontos de extremidade especificarem ambos os algoritmos, mas em ordens diferentes, vence o ponto de extremidade que aceita a conexão.  
  
> [!NOTE]  
>  O algoritmo RC4 tem suporte somente para compatibilidade com versões anteriores. O novo material só pode ser criptografado por meio do algoritmo RC4 ou RC4_128 quando o banco de dados está no nível de compatibilidade 90 ou 100. (Não recomendável.) Use um algoritmo mais recente; por exemplo, um dos algoritmos AES. No [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] e versões posteriores, o material criptografado por meio do algoritmo RC4 ou RC4_128 pode ser descriptografado em qualquer nível de compatibilidade.  
>   
>  Embora consideravelmente mais rápido que o AES, o RC4 é um algoritmo relativamente fraco, enquanto o AES é um algoritmo relativamente forte. Portanto, nós recomendamos que você use o algoritmo AES.  
  
 Para obter informações sobre a sintaxe [!INCLUDE[tsql](../../includes/tsql-md.md)] para especificar criptografia, consulte [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql).  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Tarefas relacionadas  
 **Para configurar a segurança de transporte para o ponto de extremidade do espelhamento de banco de dados**  
  
-   [Criar um ponto de extremidade de espelhamento de banco de dados para a Autenticação do Windows &#40;SQL Server&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [Estabelecer uma sessão de espelhamento de banco de dados usando a Autenticação do Windows &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md)  
  
-   [Criar um ponto de extremidade de espelhamento de banco de dados para a Autenticação do Windows &#40;SQL Server&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [Permitir que um ponto de extremidade de espelhamento de banco de dados use certificados para conexões de saída &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md)  
  
## <a name="see-also"></a>Consulte Também  
 [Escolher um algoritmo de criptografia](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)   
 [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql)   
 [Descartar ponto de extremidade &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-endpoint-transact-sql)   
 [Central de segurança para SQL Server Mecanismo de Banco de Dados e banco de dados SQL do Azure](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)   
 [Gerenciar metadados ao disponibilizar um banco de dados em outra instância de servidor &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md)   
 [O ponto de extremidade de espelhamento de banco de dados &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md)   
 [sys. database_mirroring_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)   
 [sys. dm_db_mirroring_connections &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/database-mirroring-sys-dm-db-mirroring-connections)   
 [Solução de problemas de configuração de espelhamento de banco de dados &#40;SQL Server&#41;](troubleshoot-database-mirroring-configuration-sql-server.md)   
 [Solucionar problemas de &#40;de configuração de Grupos de Disponibilidade AlwaysOn SQL Server&#41;excluídos](../availability-groups/windows/troubleshoot-always-on-availability-groups-configuration-sql-server.md)
  
  
