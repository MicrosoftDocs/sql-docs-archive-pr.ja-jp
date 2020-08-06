---
title: 警告 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent alerts, event types
- SQL Server Agent alerts, names
- alerts [SQL Server], performance conditions
- alerts [SQL Server], about alerts
- WMI event responses [SQL Server Agent alerts]
- events [WMI]
- performance condition alerts [SQL Server Agent]
- alerts [SQL Server], event types
- SQL Server Agent alerts, performance conditions
- SQL Server Agent alerts, about alerts
- alerts [SQL Server], names
ms.assetid: 3f57d0f0-4781-46ec-82cd-b751dc5affef
author: stevestein
ms.author: sstein
ms.openlocfilehash: 946bfd0c05e7739af4bfebf799980a0dc27de245
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737477"
---
# <a name="alerts"></a><span data-ttu-id="58780-102">警告</span><span class="sxs-lookup"><span data-stu-id="58780-102">Alerts</span></span>
  <span data-ttu-id="58780-103">イベントは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって生成され、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アプリケーション ログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="58780-103">Events are generated by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and entered into the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows application log.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="58780-104">エージェントは、アプリケーション ログを読み取り、そこに書き込まれているイベントを、定義済みの警告と比較します。</span><span class="sxs-lookup"><span data-stu-id="58780-104">Agent reads the application log and compares events written there to alerts that you have defined.</span></span> <span data-ttu-id="58780-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントによって一致が検出されると、イベントに対する自動応答である警告を発します。</span><span class="sxs-lookup"><span data-stu-id="58780-105">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent finds a match, it fires an alert, which is an automated response to an event.</span></span> <span data-ttu-id="58780-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] イベントの監視だけでなく、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントはパフォーマンス状態および Windows Management Instrumentation (WMI) イベントも監視します。</span><span class="sxs-lookup"><span data-stu-id="58780-106">In addition to monitoring [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] events, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent can also monitor performance conditions and Windows Management Instrumentation (WMI) events.</span></span>  
  
 <span data-ttu-id="58780-107">警告を定義するには、次の項目を指定します。</span><span class="sxs-lookup"><span data-stu-id="58780-107">To define an alert, you specify:</span></span>  
  
-   <span data-ttu-id="58780-108">警告の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="58780-108">The name of the alert.</span></span>  
  
-   <span data-ttu-id="58780-109">警告をトリガーするイベントまたはパフォーマンス状態</span><span class="sxs-lookup"><span data-stu-id="58780-109">The event or performance condition that triggers the alert.</span></span>  
  
-   <span data-ttu-id="58780-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントがそのイベントまたはパフォーマンス状態への応答として実行するアクション</span><span class="sxs-lookup"><span data-stu-id="58780-110">The action that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent takes in response to the event or performance condition.</span></span>  
  
## <a name="naming-an-alert"></a><span data-ttu-id="58780-111">警告の命名</span><span class="sxs-lookup"><span data-stu-id="58780-111">Naming an Alert</span></span>  
 <span data-ttu-id="58780-112">すべての警告に名前を付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="58780-112">Every alert must have a name.</span></span> <span data-ttu-id="58780-113">警告名は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス内で一意である必要があります。使用できる文字数は最大 **128** 文字です。</span><span class="sxs-lookup"><span data-stu-id="58780-113">Alert names must be unique within the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and can be no longer than **128** characters.</span></span>  
  
## <a name="selecting-an-event-type"></a><span data-ttu-id="58780-114">イベントの種類の選択</span><span class="sxs-lookup"><span data-stu-id="58780-114">Selecting an Event Type</span></span>  
 <span data-ttu-id="58780-115">警告は特定の種類のイベントに応答します。</span><span class="sxs-lookup"><span data-stu-id="58780-115">An alert responds to an event of a specific type.</span></span> <span data-ttu-id="58780-116">警告は次のイベントの種類に応答します。</span><span class="sxs-lookup"><span data-stu-id="58780-116">Alerts respond to the following event types:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="58780-117">のイベント</span><span class="sxs-lookup"><span data-stu-id="58780-117">events</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="58780-118">のパフォーマンス状態</span><span class="sxs-lookup"><span data-stu-id="58780-118">performance conditions</span></span>  
  
-   <span data-ttu-id="58780-119">WMI イベント</span><span class="sxs-lookup"><span data-stu-id="58780-119">WMI events</span></span>  
  
 <span data-ttu-id="58780-120">イベントの種類によって、イベントの詳細を指定するために使用するパラメーターが異なります。</span><span class="sxs-lookup"><span data-stu-id="58780-120">The type of the event determines the parameters that you use to specify the precise event.</span></span>  
  
## <a name="specifying-a-sql-server-event"></a><span data-ttu-id="58780-121">SQL Server イベントの指定</span><span class="sxs-lookup"><span data-stu-id="58780-121">Specifying a SQL Server Event</span></span>  
 <span data-ttu-id="58780-122">1 つ以上のイベントに応答して発生する警告を指定できます。</span><span class="sxs-lookup"><span data-stu-id="58780-122">You can specify an alert to occur in response to one or more events.</span></span> <span data-ttu-id="58780-123">次のパラメーターを使用して警告をトリガーするイベントを指定します。</span><span class="sxs-lookup"><span data-stu-id="58780-123">Use the following parameters to specify the events that trigger an alert:</span></span>  
  
-   <span data-ttu-id="58780-124">**エラー番号**</span><span class="sxs-lookup"><span data-stu-id="58780-124">**Error number**</span></span>  
  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="58780-125">エージェントは、特定のエラーが発生したときに警告を発します。</span><span class="sxs-lookup"><span data-stu-id="58780-125">Agent fires an alert when a specific error occurs.</span></span> <span data-ttu-id="58780-126">たとえば、データベース コンソール コマンド (DBCC) の不正な起動試行に対する応答をエラー番号 2571 と指定できます。</span><span class="sxs-lookup"><span data-stu-id="58780-126">For example, you might specify error number 2571 to respond to unauthorized attempts to invoke Database Console Commands (DBCC).</span></span>  
  
-   <span data-ttu-id="58780-127">**重大度レベル**</span><span class="sxs-lookup"><span data-stu-id="58780-127">**Severity level**</span></span>  
  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="58780-128">エージェントは、特定の重大度のエラーが発生したときに警告を発します。</span><span class="sxs-lookup"><span data-stu-id="58780-128">Agent fires an alert when any error of the specific severity occurs.</span></span> <span data-ttu-id="58780-129">たとえば、Transact-SQL ステートメントでの構文エラーに重大度 15 を指定できます。</span><span class="sxs-lookup"><span data-stu-id="58780-129">For example, you might specify a severity level of 15 to respond to syntax errors in Transact-SQL statements.</span></span>  
  
-   <span data-ttu-id="58780-130">**[データベース]**</span><span class="sxs-lookup"><span data-stu-id="58780-130">**Database**</span></span>  
  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="58780-131">エージェントは、特定のデータベースでイベントが発生した場合のみ警告を発します。</span><span class="sxs-lookup"><span data-stu-id="58780-131">Agent fires an alert only when the event occurs in a particular database.</span></span> <span data-ttu-id="58780-132">このオプションは、エラー番号または重大度に加えて適用できます。</span><span class="sxs-lookup"><span data-stu-id="58780-132">This option applies in addition to the error number or severity level.</span></span> <span data-ttu-id="58780-133">たとえば、1 つのインスタンスで運用データベースとレポート用データベースを使用している場合、運用データベースで構文エラーが発生した場合のみ、警告を発するように定義できます。</span><span class="sxs-lookup"><span data-stu-id="58780-133">For example, if an instance contains one database that is used for production and one database that is used for reporting, you can define an alert that responds to syntax errors in the production database only.</span></span>  
  
-   <span data-ttu-id="58780-134">**イベント テキスト**</span><span class="sxs-lookup"><span data-stu-id="58780-134">**Event text**</span></span>  
  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="58780-135">エージェントは、指定されたイベントのイベント メッセージに特定の文字列が含まれている場合に警告を発します。</span><span class="sxs-lookup"><span data-stu-id="58780-135">Agent fires an alert when the specified event contains a particular text string in the event message.</span></span> <span data-ttu-id="58780-136">たとえば、特定のテーブル名または特定の定数を含んでいるメッセージに応答する警告を定義できます。</span><span class="sxs-lookup"><span data-stu-id="58780-136">For example, you might define an alert that responds to messages that contain the name of a particular table or a particular constraint.</span></span>  
  
## <a name="selecting-a-performance-condition"></a><span data-ttu-id="58780-137">パフォーマンス状態の選択</span><span class="sxs-lookup"><span data-stu-id="58780-137">Selecting a Performance Condition</span></span>  
 <span data-ttu-id="58780-138">特定のパフォーマンス状態に応答する警告を指定できます。</span><span class="sxs-lookup"><span data-stu-id="58780-138">You can specify an alert to occur in response to a particular performance condition.</span></span> <span data-ttu-id="58780-139">この場合、監視するパフォーマンス カウンター、警告を発生するしきい値、および警告発生時にカウンターが示す動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="58780-139">In this case, you specify the performance counter to monitor, a threshold for the alert, and the behavior that the counter must show if the alert is to occur.</span></span> <span data-ttu-id="58780-140">パフォーマンス状態を設定するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの **[新しい警告]** または **[警告のプロパティ]** ダイアログ ボックスを開き、 **[全般]** ページで次の項目を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58780-140">To set a performance condition, you must define the following items on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent **General** page of the **New Alert** or the **Alert Properties** dialog box:</span></span>  
  
-   <span data-ttu-id="58780-141">**Object**</span><span class="sxs-lookup"><span data-stu-id="58780-141">**Object**</span></span>  
  
     <span data-ttu-id="58780-142">オブジェクトは、監視されるパフォーマンスの領域です。</span><span class="sxs-lookup"><span data-stu-id="58780-142">The object is the area of performance to be monitored.</span></span>  
  
-   <span data-ttu-id="58780-143">**カウンター**</span><span class="sxs-lookup"><span data-stu-id="58780-143">**Counter**</span></span>  
  
     <span data-ttu-id="58780-144">カウンターは、監視される領域の属性です。</span><span class="sxs-lookup"><span data-stu-id="58780-144">A counter is an attribute of the area to be monitored.</span></span>  
  
-   <span data-ttu-id="58780-145">**インスタンス**</span><span class="sxs-lookup"><span data-stu-id="58780-145">**Instance**</span></span>  
  
     <span data-ttu-id="58780-146">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスでは、監視する属性に特定のインスタンスがある場合、そのインスタンスを定義します。</span><span class="sxs-lookup"><span data-stu-id="58780-146">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance defines the specific instance (if any) of the attribute to be monitored.</span></span>  
  
-   <span data-ttu-id="58780-147">**[警告カウンター]** および **[値]**</span><span class="sxs-lookup"><span data-stu-id="58780-147">**Alert if counter** and **Value**</span></span>  
  
     <span data-ttu-id="58780-148">警告およびそれを生成する動作のしきい値です。</span><span class="sxs-lookup"><span data-stu-id="58780-148">The threshold for the alert and the behavior that produces the alert.</span></span> <span data-ttu-id="58780-149">しきい値は数値です。</span><span class="sxs-lookup"><span data-stu-id="58780-149">The threshold is a number.</span></span> <span data-ttu-id="58780-150">動作は、 **[設定値未満]** 、 **[設定値に等しい]** 、 **[設定値を超える]** のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="58780-150">The behavior is one **of the following: falls below**, **becomes equal to**, or **rises above a number specified for Value**.</span></span> <span data-ttu-id="58780-151">**[値]** は、パフォーマンス状況の警告カウンターの基準となる数値です。</span><span class="sxs-lookup"><span data-stu-id="58780-151">The **Value** is a number that describes the performance condition counter.</span></span> <span data-ttu-id="58780-152">たとえば、パフォーマンス オブジェクト **SQLServer:Locks** で、 **Lock Wait Time** が 30 分を超えると警告が発生するように設定するには、 **[設定値を超える]** を選択し、 **[値] を 30 に指定**します。</span><span class="sxs-lookup"><span data-stu-id="58780-152">For example, to set an alert to occur for the performance object **SQLServer:Locks** when the **Lock Wait Time** exceeds 30 minutes, you would choose **rises above** and **specify 30 as the value**.</span></span>  
  
     <span data-ttu-id="58780-153">別の例として、 **tempdb** の空き領域が 1,000 KB を下回った場合にパフォーマンス オブジェクト **SQLServer:Transactions** に対して警告が発生するように指定できます。</span><span class="sxs-lookup"><span data-stu-id="58780-153">As another example, you might specify that an alert occurs for the performance object **SQLServer:Transactions** when the free space in **tempdb** falls below 1000 KB.</span></span> <span data-ttu-id="58780-154">このように設定するには、カウンター **[Free space in tempdb (KB)]** を選択し **[設定値未満]** を選択します。さらに、 **[値]** を **1000**に設定します。</span><span class="sxs-lookup"><span data-stu-id="58780-154">To set this, you would choose the counter **Free space in tempdb (KB)**, **falls below**,and a **Value** of **1000**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="58780-155">パフォーマンス データは定期的にサンプリングされます。したがって、しきい値に達してからパフォーマンス警告が発せられるまでの間にわずかな遅延 (数秒) が生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="58780-155">Performance data is sampled periodically, which can lead to a small delay (a few seconds) between the threshold being reached and the occurrence of the performance alert.</span></span>  
  
## <a name="selecting-a-wmi-event"></a><span data-ttu-id="58780-156">WMI イベントの選択</span><span class="sxs-lookup"><span data-stu-id="58780-156">Selecting a WMI Event</span></span>  
 <span data-ttu-id="58780-157">特定の WMI イベントに応答して警告が発生するように指定できます。</span><span class="sxs-lookup"><span data-stu-id="58780-157">You can specify that an alert occur in response to a particular WMI event.</span></span> <span data-ttu-id="58780-158">WMI イベントを選択するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの **[新しい警告]** または **[警告のプロパティ]** ダイアログ ボックスを開き、 **[全般]** ページで次の項目を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58780-158">To select a WMI event, you must define the following on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent **General** page of the **New Alert** or the **Alert Properties** dialog box:</span></span>  
  
-   <span data-ttu-id="58780-159">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="58780-159">**Namespace**</span></span>  
  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="58780-160">エージェントを WMI クライアントとして、イベントをクエリするために用意された WMI 名前空間に登録します。</span><span class="sxs-lookup"><span data-stu-id="58780-160">Agent registers as a WMI client to the WMI namespace that is provided to query for events.</span></span>  
  
-   <span data-ttu-id="58780-161">**クエリ**</span><span class="sxs-lookup"><span data-stu-id="58780-161">**Query**</span></span>  
  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="58780-162">エージェントは、Windows Management Instrumentation Query Language (WQL) ステートメントを使用して、特定のイベントを識別します。</span><span class="sxs-lookup"><span data-stu-id="58780-162">Agent uses the Windows Management Instrumentation Query Language (WQL) statement provided to identify the specific event.</span></span>  
  
 <span data-ttu-id="58780-163">一般的なタスクへのリンクは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="58780-163">Following are links to common tasks:</span></span>  
  
 <span data-ttu-id="58780-164">**メッセージ番号に基づいた警告を作成するには**</span><span class="sxs-lookup"><span data-stu-id="58780-164">**To create an alert based on a message number**</span></span>  
  
-   [<span data-ttu-id="58780-165">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="58780-165">SQL Server Management Studio</span></span>](create-an-alert-using-an-error-number.md)  
  
-   [<span data-ttu-id="58780-166">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="58780-166">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql)  
  
 <span data-ttu-id="58780-167">**重大度レベルに基づいた警告を作成するには**</span><span class="sxs-lookup"><span data-stu-id="58780-167">**To create an alert based on severity levels**</span></span>  
  
-   [<span data-ttu-id="58780-168">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="58780-168">SQL Server Management Studio</span></span>](create-an-alert-using-severity-level.md)  
  
-   [<span data-ttu-id="58780-169">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="58780-169">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql)  
  
 <span data-ttu-id="58780-170">**WMI イベントに基づいた警告を作成するには**</span><span class="sxs-lookup"><span data-stu-id="58780-170">**To create an alert based on a WMI event**</span></span>  
  
-   [<span data-ttu-id="58780-171">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="58780-171">SQL Server Management Studio</span></span>](create-a-wmi-event-alert.md)  
  
-   [<span data-ttu-id="58780-172">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="58780-172">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql)  
  
 <span data-ttu-id="58780-173">**警告に対する応答を定義するには**</span><span class="sxs-lookup"><span data-stu-id="58780-173">**To define the response to an alert**</span></span>  
  
-   [<span data-ttu-id="58780-174">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="58780-174">SQL Server Management Studio</span></span>](../sql-server-management-studio-ssms.md)  
  
-   [<span data-ttu-id="58780-175">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="58780-175">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql)  
  
 <span data-ttu-id="58780-176">**ユーザー定義のイベント エラー メッセージを作成するには**</span><span class="sxs-lookup"><span data-stu-id="58780-176">**To create a user-defined event error message**</span></span>  
  
-   [<span data-ttu-id="58780-177">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="58780-177">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-addmessage-transact-sql)  
  
 <span data-ttu-id="58780-178">**ユーザー定義のイベント エラー メッセージを変更するには**</span><span class="sxs-lookup"><span data-stu-id="58780-178">**To modify a user-defined event error message**</span></span>  
  
-   [<span data-ttu-id="58780-179">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="58780-179">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-altermessage-transact-sql)  
  
 <span data-ttu-id="58780-180">**ユーザー定義のイベント エラー メッセージを削除するには**</span><span class="sxs-lookup"><span data-stu-id="58780-180">**To delete a user-defined event error message**</span></span>  
  
-   [<span data-ttu-id="58780-181">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="58780-181">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-dropmessage-transact-sql)  
  
 <span data-ttu-id="58780-182">**警告を無効にしたり、再び有効にするには**</span><span class="sxs-lookup"><span data-stu-id="58780-182">**To disable or reactivate an alert**</span></span>  
  
-   [<span data-ttu-id="58780-183">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="58780-183">SQL Server Management Studio</span></span>](disable-or-reactivate-an-alert.md)  
  
-   [<span data-ttu-id="58780-184">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="58780-184">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-update-alert-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="58780-185">参照</span><span class="sxs-lookup"><span data-stu-id="58780-185">See Also</span></span>  
 [<span data-ttu-id="58780-186">SQL Server オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="58780-186">Use SQL Server Objects</span></span>](../../relational-databases/performance-monitor/use-sql-server-objects.md)  
  
  