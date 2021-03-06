---
title: Instruções | Microsoft Docs
ms.custom: ''
ms.date: 04/17/2020
ms.prod: sql
ms.prod_service: sql-data-warehouse, database-engine, pdw, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: d8d6f62a-e815-425c-a80e-a63fd34ec275
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: bf492b24e1473ce189f39a84096242773b78cc4a
ms.sourcegitcommit: c37777216fb8b464e33cd6e2ffbedb6860971b0d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82086805"
---
# <a name="transact-sql-statements"></a>instruções Transact-SQL

[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Uma instrução SQL é uma unidade atômica de trabalho que é totalmente concluída com êxito ou falha por completo. Uma instrução SQL é um conjunto de instruções que consiste em identificadores, parâmetros, variáveis, nomes, tipos de dados e palavras reservadas do SQL compilados com sucesso. O [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] criará uma transação *implícita* para uma instrução SQL se o comando `BeginTransaction` não especificar o início de uma transação. O [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sempre confirmará uma transação implícita se a instrução for bem-sucedida e reverterá uma transação implícita se o comando falhar.  

Há vários tipos de instruções. Talvez o mais importante seja [SELECT](../queries/select-transact-sql.md), que recupera linhas do banco de dados e permite a seleção de uma ou várias linhas ou colunas de uma ou várias tabelas no [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Este artigo resume as categorias de instruções para uso com o T-SQL (Transact-SQL), em adição à instrução `SELECT`. Você pode encontrar todas as instruções listadas no painel de navegação esquerdo.

## <a name="backup-and-restore"></a>Backup e restauração

As instruções de backup e restauração oferecem maneiras de criar backups e fazer a restauração de backups.  Para obter mais informações, veja a [Visão geral de backup e restauração](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).

## <a name="data-definition-language"></a>Linguagem de definição de dados

Instruções DDL (linguagem de definição de dados) definem as estruturas de dados. Use estas instruções para criar, alterar ou remover estruturas de dados em um banco de dados.

- ALTER
- Ordenações
- CREATE
- DROP
- DISABLE TRIGGER
- ENABLE TRIGGER
- RENAME
- UPDATE STATISTICS

## <a name="data-manipulation-language"></a>Linguagem de manipulação de dados

A DML (linguagem de manipulação de dados) afeta as informações armazenadas no banco de dados. Use estas instruções para inserir, atualizar e alterar as linhas no banco de dados.

- BULK INSERT
- Delete (excluir)
- INSERT
- UPDATE
- MESCLAR
- TRUNCATE TABLE

## <a name="permissions-statements"></a>Instruções de permissões

Instruções de permissões determinam quais logons e usuários podem acessar os dados e executar operações. Para obter mais informações sobre o acesso e autenticação, veja a [Central de segurança](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md).

## <a name="service-broker-statements"></a>Instruções do Service Broker

O Service Broker é um recurso que oferece suporte nativo para aplicativos de mensagens e enfileiramento. Para obter mais informações, veja [Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md).

## <a name="session-settings"></a>Configurações da sessão

Instruções SET determinam como os identificadores de sessão atual lidam com configurações de tempo. Para obter uma visão geral, veja [instruções SET](set-statements-transact-sql.md).
