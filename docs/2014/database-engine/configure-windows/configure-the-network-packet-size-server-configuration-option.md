---
title: Configurar a opção de configuração de servidor network packet size | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- default packet size
- size [SQL Server], packets
- packets [SQL Server], size
- network packet size option
ms.assetid: 236985bf-fc4a-4a57-98f7-a71ef977fd7b
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 4bd992f16158e7286db668256dc5963d83dbd4b8
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62786995"
---
# <a name="configure-the-network-packet-size-server-configuration-option"></a>Configurar a opção de configuração de servidor network packet size
  Este tópico descreve como configurar a opção `network packet size` de configuração de servidor [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] no usando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]ou o. A `network packet size` opção define o tamanho do pacote (em bytes) que é usado em toda a rede. Os pacotes são partes de dados de tamanho fixo que transferem solicitações e resultados entre clientes e servidores. O tamanho do pacote padrão é de 4.096 bytes.  
  
> [!NOTE]  
>  Não altere o tamanho do pacote a menos que você tenha certeza que melhorará o desempenho. Para a maioria dos aplicativos, o tamanho do pacote padrão é o melhor.  
  
 **Neste tópico**  
  
-   **Antes de começar:**  
  
     [Limitações e restrições](#Restrictions)  
  
     [Recomendações](#Recommendations)  
  
     [Segurança](#Security)  
  
-   **Para configurar a opção network packet size usando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Acompanhamento:**  [depois de configurar a opção network packet size](#FollowUp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Antes de começar  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Limitações e restrições  
  
-   O tamanho máximo de pacote de rede para conexões criptografadas é 16.383 bytes.  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Recomendações  
  
-   Esta é uma opção avançada e deve ser alterada somente por um administrador de banco de dados experiente ou técnico certificado do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Se um aplicativo fizer operações de cópia em massa ou enviar ou receber grandes quantidades de texto ou dados de imagem, um tamanho do pacote maior que o padrão poderá melhorar a eficiência, porque resulta em menos operações de leitura e gravação em rede. Se um aplicativo enviar e receber pequenas quantidades de informações, o tamanho do pacote poderá ser definido como 512 bytes, o que é suficiente para a maioria das transferências de dados.  
  
-   Nos sistemas que usam protocolos de rede diferentes, defina network packet size como o tamanho para o protocolo mais comum usado. A opção network packet size melhora o desempenho da rede quando protocolos de rede oferecem suporte a pacotes maiores. Aplicativos cliente podem substituir esse valor.  
  
-   Você também pode chamar funções OLE DB, ODBC e DB-Library para solicitar uma alteração do tamanho do pacote. Se o servidor não der suporte ao tamanho de pacote solicitado, o [!INCLUDE[ssDE](../../includes/ssde-md.md)] enviará uma mensagem de aviso ao cliente. Em algumas circunstâncias, alterar o tamanho de pacote pode conduzir a uma falha de link de comunicação, como esta:  
  
     `Native Error: 233, no process is on the other end of the pipe.`  
  
###  <a name="security"></a><a name="Security"></a> Segurança  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissões  
 Permissões de execução sem parâmetros ou com apenas o primeiro parâmetro em **sp_configure** são concedidas a todos os usuários por padrão. Para executar **sp_configure** com ambos os parâmetros para alterar uma opção de configuração ou executar a instrução RECONFIGURE, o usuário deve ter a permissão ALTER SETTINGS no nível do servidor. A permissão ALTER SETTINGS é implicitamente mantida pelas funções de servidor fixas **sysadmin** e **serveradmin** .  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Usando o SQL Server Management Studio  
  
#### <a name="to-configure-the-network-packet-size-option"></a>Para configurar a opção network packet size  
  
1.  No Pesquisador de Objetos, clique com o botão direito do mouse em um servidor e selecione **Propriedades**.  
  
2.  Clique no nó **Avançado** .  
  
3.  Em **Rede**, selecione um valor para a caixa **Tamanho de Pacote de Rede** .  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Usando o Transact-SQL  
  
#### <a name="to-configure-the-network-packet-size-option"></a>Para configurar a opção network packet size  
  
1.  Conecte-se ao [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Na barra Padrão, clique em **Nova Consulta**.  
  
3.  Copie e cole o exemplo a seguir na janela de consulta e clique em **Executar**. Este exemplo mostra como usar [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) para definir o valor da opção `network packet size` como `6500` bytes.  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'network packet size', 6500 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 Para obter mais informações, veja [Opções de configuração do servidor &#40;SQL Server&#41;](server-configuration-options-sql-server.md).  
  
##  <a name="follow-up-after-you-configure-the-network-packet-size-option"></a><a name="FollowUp"></a> Acompanhamento: depois de configurar a opção network packet size  
 A configuração entra em vigor imediatamente sem reiniciar o servidor.  
  
## <a name="see-also"></a>Consulte Também  
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Opções de configuração do servidor &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
