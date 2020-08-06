---
title: サービス マスター キーのバックアップ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- service master key [SQL Server], exporting
ms.assetid: f60b917c-6408-48be-b911-f93b05796904
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: b79212040df67c22ae7e34cd380a1a1f1bd10773
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741721"
---
# <a name="back-up-the-service-master-key"></a><span data-ttu-id="d9b44-102">サービス マスター キーのバックアップ</span><span class="sxs-lookup"><span data-stu-id="d9b44-102">Back Up the Service Master Key</span></span>
  <span data-ttu-id="d9b44-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用してサービス マスター キーをバックアップする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d9b44-103">This topic describes how to back-up the Service Master key in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="d9b44-104">サービス マスター キーは、暗号化階層のルートになります。</span><span class="sxs-lookup"><span data-stu-id="d9b44-104">The service master key is the root of the encryption hierarchy.</span></span> <span data-ttu-id="d9b44-105">サービス マスター キーは、バックアップして安全な別の場所に保存してください。</span><span class="sxs-lookup"><span data-stu-id="d9b44-105">It should be backed up and stored in a secure, off-site location.</span></span> <span data-ttu-id="d9b44-106">このバックアップの作成は、サーバー管理操作の最初の段階で実行します。</span><span class="sxs-lookup"><span data-stu-id="d9b44-106">Creating this backup should be one of the first administrative actions performed on the server.</span></span>  
  
 <span data-ttu-id="d9b44-107">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="d9b44-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="d9b44-108">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="d9b44-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="d9b44-109">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="d9b44-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="d9b44-110">Security</span><span class="sxs-lookup"><span data-stu-id="d9b44-110">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="d9b44-111">サービス マスター キーをバックアップするには</span><span class="sxs-lookup"><span data-stu-id="d9b44-111">To back-up the Service Master key</span></span>](#Procedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d9b44-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="d9b44-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="d9b44-113">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="d9b44-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="d9b44-114">マスター キーは開かれている必要があります。したがって、バックアップ前に暗号化を解除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d9b44-114">The master key must be open and, therefore, decrypted before it is backed up.</span></span> <span data-ttu-id="d9b44-115">サービス マスター キーで暗号化されている場合は、マスター キーを明示的に開く必要はありません。ただし、マスター キーがパスワードのみで暗号化されている場合は、明示的に開く必要があります。</span><span class="sxs-lookup"><span data-stu-id="d9b44-115">If it is encrypted with the service master key, the master key does not have to be explicitly opened; however, if the master key is encrypted only with a password, it must be explicitly opened.</span></span>  
  
-   <span data-ttu-id="d9b44-116">マスター キーは作成後すぐにバックアップし、安全な別の場所に保存することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d9b44-116">We recommend that you back up the master key as soon as it is created, and store the backup in a secure, off-site location.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d9b44-117">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="d9b44-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d9b44-118">Permissions</span><span class="sxs-lookup"><span data-stu-id="d9b44-118">Permissions</span></span>  
 <span data-ttu-id="d9b44-119">データベースに対する CONTROL 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="d9b44-119">Requires CONTROL permission on the database.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="Procedure"></a> <span data-ttu-id="d9b44-120">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="d9b44-120">Using Transact-SQL</span></span>  
  
#### <a name="to-back-up-the-service-master-key"></a><span data-ttu-id="d9b44-121">サービス マスター キーをバックアップするには</span><span class="sxs-lookup"><span data-stu-id="d9b44-121">To back-up the Service Master key</span></span>  
  
1.  <span data-ttu-id="d9b44-122">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]で、バックアップするサービス マスター キーが格納されている [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="d9b44-122">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance containing the service master key you wish to back up.</span></span>  
  
2.  <span data-ttu-id="d9b44-123">バックアップ メディアでサービス マスター キーの暗号化に使用するパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="d9b44-123">Choose a password that will be used to encrypt the service master key on the backup medium.</span></span> <span data-ttu-id="d9b44-124">このパスワードに対しては、複雑性がチェックされます。</span><span class="sxs-lookup"><span data-stu-id="d9b44-124">This password is subject to complexity checks.</span></span> <span data-ttu-id="d9b44-125">詳細については、「 [Password Policy](../password-policy.md)」をご参照ください。</span><span class="sxs-lookup"><span data-stu-id="d9b44-125">For more information, see [Password Policy](../password-policy.md).</span></span>  
  
3.  <span data-ttu-id="d9b44-126">バックアップしたキーのコピーを保存するためにリムーバブル バックアップ メディアを用意します。</span><span class="sxs-lookup"><span data-stu-id="d9b44-126">Obtain a removable backup medium for storing a copy of the backed-up key.</span></span>  
  
4.  <span data-ttu-id="d9b44-127">キーのバックアップを作成する NTFS ディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="d9b44-127">Identify an NTFS directory in which to create the backup of the key.</span></span> <span data-ttu-id="d9b44-128">このディレクトリは、次の手順で指定するファイルの作成先となります。</span><span class="sxs-lookup"><span data-stu-id="d9b44-128">This is where you will create the file specified in the next step.</span></span> <span data-ttu-id="d9b44-129">このディレクトリは、制限の厳しいアクセス制御リスト (ACL) で保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d9b44-129">The directory should be protected with highly restrictive access control lists (ACLs).</span></span>  
  
5.  <span data-ttu-id="d9b44-130">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="d9b44-130">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
6.  <span data-ttu-id="d9b44-131">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d9b44-131">On the Standard bar, click **New Query**.</span></span>  
  
7.  <span data-ttu-id="d9b44-132">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d9b44-132">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Creates a backup of the "AdventureWorks2012" master key.  
    -- Because this master key is not encrypted by the service master key, a password must be specified when it is opened.  
    USE AdventureWorks2012;  
    GO  
    BACKUP SERVICE MASTER KEY TO FILE = 'c:\temp_backups\keys\service_master_ key'   
        ENCRYPTION BY PASSWORD = '3dH85Hhk003GHk2597gheij4';  
    GO  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="d9b44-133">キーのファイル パスとキーのパスワード (存在する場合) は、実際は上に示したものと異なります。</span><span class="sxs-lookup"><span data-stu-id="d9b44-133">The file path to the key and the key's password (if it exists) will be different than what is indicated above.</span></span> <span data-ttu-id="d9b44-134">両方がサーバーとキーのセットアップで固有であることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="d9b44-134">Make sure that both are specific to your server and key set-up.</span></span>  
  
8.  <span data-ttu-id="d9b44-135">ファイルをバックアップ メディアにコピーして、コピーしたファイルを確認します。</span><span class="sxs-lookup"><span data-stu-id="d9b44-135">Copy the file to the backup medium and verify the copy.</span></span>  
  
9. <span data-ttu-id="d9b44-136">バックアップを安全な場所に保存します。</span><span class="sxs-lookup"><span data-stu-id="d9b44-136">Store the backup in a secure, off-site location.</span></span>  
  
 <span data-ttu-id="d9b44-137">詳細については、「[OPEN MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/open-master-key-transact-sql)」と「[BACKUP MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-master-key-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9b44-137">For more information, see [OPEN MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/open-master-key-transact-sql) and [BACKUP MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-master-key-transact-sql).</span></span>  
  
  