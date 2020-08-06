---
title: Transact-SQL デバッガー情報
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, Locals Window
- Transact-SQL debugger, Watch Window
- Transact-SQL debugger, Threads Window
- Transact-SQL debugger, Call Stack Window
- Transact-SQL debugger, QuickWatch
- Transact-SQL debugger, viewing information
ms.assetid: b99819cc-f388-41a1-b304-36e78ce24147
author: rothja
ms.author: jroth
ms.openlocfilehash: c51ed39f0ed5f4ffb3e1a0c0dcb307f82d10bb10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741757"
---
# <a name="transact-sql-debugger-information"></a><span data-ttu-id="31e2d-102">Transact-SQL デバッガー情報</span><span class="sxs-lookup"><span data-stu-id="31e2d-102">Transact-SQL Debugger Information</span></span>
  <span data-ttu-id="31e2d-103">デバッガーが特定の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントで実行を一時停止するたびに、さまざまなデバッガー ウィンドウを使用して現在の実行状態を表示できます。</span><span class="sxs-lookup"><span data-stu-id="31e2d-103">Every time that the debugger pauses execution on a specific [!INCLUDE[tsql](../../includes/tsql-md.md)] statement, you can use the various debugger windows to view the current execution state.</span></span>  
  
## <a name="debugger-windows"></a><span data-ttu-id="31e2d-104">デバッガー ウィンドウ</span><span class="sxs-lookup"><span data-stu-id="31e2d-104">Debugger Windows</span></span>  
 <span data-ttu-id="31e2d-105">デバッガー モードでは、デバッガーにより、メイン [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ウィンドウの下部に 2 つのウィンドウが開かれます。</span><span class="sxs-lookup"><span data-stu-id="31e2d-105">In debugger mode, the debugger opens two windows at the bottom of the main [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] window.</span></span> <span data-ttu-id="31e2d-106">デバッガーをこれら 2 つのウィンドウで、すべてその情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="31e2d-106">The debugger displays all its information in these two windows.</span></span> <span data-ttu-id="31e2d-107">それぞれのデバッガー ウィンドウには、ウィンドウに表示される情報のセットを制御するために選択できるタブがあります。</span><span class="sxs-lookup"><span data-stu-id="31e2d-107">Each of the debugger windows has tabs that you can select to control which set of information is displayed in the window.</span></span> <span data-ttu-id="31e2d-108">左側のデバッガー ウィンドウには、 **[ローカル]** 、 **[ウォッチ 1]** 、 **[ウォッチ 2]** 、 **[ウォッチ 3]** 、および **[ウォッチ 4]** の各タブがあります。</span><span class="sxs-lookup"><span data-stu-id="31e2d-108">The left debugger window contains the **Locals**, **Watch1**, **Watch2**, **Watch3**, and **Watch4** tabs.</span></span> <span data-ttu-id="31e2d-109">右側のデバッガー ウィンドウには、 **[呼び出し履歴]** 、 **[スレッド]** 、 **[ブレークポイント]** 、 **[コマンド ウィンドウ]** 、および **[出力]** の各タブがあります。</span><span class="sxs-lookup"><span data-stu-id="31e2d-109">The right debugger window contains the **Call Stack**, **Threads**, **Breakpoints**, **Command Window**, and **Output** tabs.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="31e2d-110">前の説明は、デバッガー ウィンドウの既定の場所に適用されます。</span><span class="sxs-lookup"><span data-stu-id="31e2d-110">The previous descriptions apply to the default locations of the debugger windows.</span></span> <span data-ttu-id="31e2d-111">タブは、ドラッグすることでウィンドウ間で移動できます。また、タブのドッキングを解除して新しいウィンドウを作成し、任意の場所に配置することもできます。</span><span class="sxs-lookup"><span data-stu-id="31e2d-111">You can drag a tab to move it from one window to another, or you can undock a tab to create a new window that you can put wherever you want.</span></span>  
  
 <span data-ttu-id="31e2d-112">既定では、これらのタブまたはウィンドウの一部がアクティブになりません。</span><span class="sxs-lookup"><span data-stu-id="31e2d-112">By default, not all of these tabs or windows are active.</span></span> <span data-ttu-id="31e2d-113">特定のウィンドウを開くには、次のどちらかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="31e2d-113">You can open a particular window by using either of the following ways:</span></span>  
  
-   <span data-ttu-id="31e2d-114">**[デバッグ]** メニューの **[ウィンドウ]** をクリックし、目的のウィンドウを選択する。</span><span class="sxs-lookup"><span data-stu-id="31e2d-114">On the **Debug** menu, click **Windows**, and then select the window you want.</span></span>  
  
-   <span data-ttu-id="31e2d-115">**[デバッグ]** ツール バーの **[ブレークポイント]** をクリックし、目的のウィンドウを選択する。</span><span class="sxs-lookup"><span data-stu-id="31e2d-115">On the **Debug** toolbar, click **Breakpoints**, and then select the window you want.</span></span>  
  
## <a name="transact-sql-expressions"></a><span data-ttu-id="31e2d-116">Transact-SQL 式</span><span class="sxs-lookup"><span data-stu-id="31e2d-116">Transact-SQL Expressions</span></span>  
 <span data-ttu-id="31e2d-117">式は、変数やパラメーターなどの単独のスカラー値に評価される [!INCLUDE[tsql](../../includes/tsql-md.md)] 句です。</span><span class="sxs-lookup"><span data-stu-id="31e2d-117">Expressions are [!INCLUDE[tsql](../../includes/tsql-md.md)] clauses that evaluate to a single, scalar value, such as variables or parameters.</span></span> <span data-ttu-id="31e2d-118">左側のデバッガー ウィンドウでは、式に現在割り当てられているデータ値を最大で 5 つのタブまたはウィンドウ ( **[ローカル]、[ウォッチ 1]** 、 **[ウォッチ 2]** 、 **[ウォッチ 3]** 、および **[ウォッチ 4]** ) に表示できます。</span><span class="sxs-lookup"><span data-stu-id="31e2d-118">The left debugger window can display the data values that are currently assigned to expressions in up to five tabs or windows: **Locals, Watch1**, **Watch2**, **Watch3**, and **Watch4**.</span></span>  
  
 <span data-ttu-id="31e2d-119">**[ローカル]** ウィンドウには、 [!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーの現在のスコープ内のローカル変数についての情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="31e2d-119">The **Locals** window displays information about the local variables in the current scope of the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger.</span></span> <span data-ttu-id="31e2d-120">**[ローカル]** ウィンドウに表示される式のセットは、一覧の式を追加または削除しない限り変更されません。</span><span class="sxs-lookup"><span data-stu-id="31e2d-120">The set of expressions that are listed in the **Locals** window changes as the debugger runs through the different parts of the code.</span></span>  
  
 <span data-ttu-id="31e2d-121">**[クイック ウォッチ]** と 4 つの **[ウォッチ]** ウィンドウに指定できる式は、変数の識別子だけではありません。</span><span class="sxs-lookup"><span data-stu-id="31e2d-121">The expressions in the **QuickWatch** and the four **Watch** windows are not limited to just listing the identifier of a variable.</span></span> <span data-ttu-id="31e2d-122">単一の値に評価される [!INCLUDE[tsql](../../includes/tsql-md.md)] 式 (変数に対して数値を加算する式など) や単一の値に評価される SELECT ステートメントを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="31e2d-122">You can specify a [!INCLUDE[tsql](../../includes/tsql-md.md)] expression that evaluates to a single value, such as adding a number to a variable, or a SELECT statement that evaluates to a single value.</span></span> <span data-ttu-id="31e2d-123">たとえば、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="31e2d-123">Examples include:</span></span>  
  
-   <span data-ttu-id="31e2d-124">変数の名前 (@IntegerCounter など)。</span><span class="sxs-lookup"><span data-stu-id="31e2d-124">The name of a variable, such as @IntegerCounter.</span></span>  
  
-   <span data-ttu-id="31e2d-125">変数に対する算術演算 (@IntegerCounter + 1 など)。</span><span class="sxs-lookup"><span data-stu-id="31e2d-125">An arithmetic operation on a variable, such as @IntegerCounter + 1.</span></span>  
  
-   <span data-ttu-id="31e2d-126">2 つの文字変数に対する文字列操作 (@FirstName + @LastName など)。</span><span class="sxs-lookup"><span data-stu-id="31e2d-126">A string operation on two character variables, such as @FirstName + @LastName.</span></span>  
  
-   <span data-ttu-id="31e2d-127">単一の値を返す SELECT ステートメント (SELECT CharCol FROM MyTable WHERE PrimaryKey = 1)。</span><span class="sxs-lookup"><span data-stu-id="31e2d-127">A SELECT statement that returns a single value, such as SELECT CharCol FROM MyTable WHERE PrimaryKey = 1.</span></span>  
  
 <span data-ttu-id="31e2d-128">**[クイック ウォッチ]** ウィンドウを使用すると、 [!INCLUDE[tsql](../../includes/tsql-md.md)] 式の値を表示した後、その式を **[ウォッチ]** ウィンドウに保存できます。</span><span class="sxs-lookup"><span data-stu-id="31e2d-128">You can use the **QuickWatch** window to view the value of a [!INCLUDE[tsql](../../includes/tsql-md.md)] expression, and then save that expression to a **Watch** window.</span></span> <span data-ttu-id="31e2d-129">**[クイック ウォッチ]** で式を選択するには、 **[式]** ボックスで式の名前を選択または入力します。</span><span class="sxs-lookup"><span data-stu-id="31e2d-129">To select an expression in **QuickWatch**, either select or enter the name of the expression in the **Expression** box.</span></span>  
  
 <span data-ttu-id="31e2d-130">4 つの **[ウォッチ]** ウィンドウには、選択した変数および式に関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="31e2d-130">The four **Watch** windows display information about variables and expressions that you have selected.</span></span> <span data-ttu-id="31e2d-131">**[ウォッチ]** ウィンドウに表示される式のセットは、一覧の式を追加または削除しない限り変更されません。</span><span class="sxs-lookup"><span data-stu-id="31e2d-131">The set of expressions that are listed in the **Watch** windows does not change until you either add or delete expressions from the list.</span></span>  
  
 <span data-ttu-id="31e2d-132">式を **[ウォッチ]** ウィンドウに追加するには、 **[クイック ウォッチ]** ダイアログ ボックスで **[ウォッチ式の追加]** を選択するか、または **[ウォッチ]** ウィンドウで空の行の **[名前]** 列に式の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="31e2d-132">To add an expression to a **Watch** window, you can either select **Add Watch** in the **QuickWatch** dialog box, or enter the name of the expression in the **Name** column of an empty row in a **Watch** window.</span></span>  
  
 <span data-ttu-id="31e2d-133">**[ローカル]** 、 **[ウォッチ]** 、または **[クイック ウォッチ]** の各ウィンドウで変数にデータ値を設定するには、行を右クリックし、 **[値の編集]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="31e2d-133">You can set the data values for variables in the **Locals**, **Watch**, or **QuickWatch** windows by right-clicking the row and then selecting **Edit Value**.</span></span> <span data-ttu-id="31e2d-134">**[ローカル]** 、 **[ウォッチ]** 、および **[クイック ウォッチ]** ダイアログ ボックスの **[値]** 列では、テキスト、XML、および HTML のデータ ビジュアライザーがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="31e2d-134">The **Value** columns in the **Locals** window, **Watch** window, and **QuickWatch** dialog box all support text, XML, and HTML data visualizers.</span></span> <span data-ttu-id="31e2d-135">ビジュアライザーは、 **[値]** 列の右側の虫眼鏡データ ヒントとして表されます。</span><span class="sxs-lookup"><span data-stu-id="31e2d-135">The visualizers are represented by a magnifying glass data tip on the right side end of the **Values** column.</span></span> <span data-ttu-id="31e2d-136">ビジュアライザーを使用すると、データ型に一致するテキスト、XML、または HTML のデータ値を表示できます (たとえば、XML ファイルをブラウザー ウィンドウに表示できます)。</span><span class="sxs-lookup"><span data-stu-id="31e2d-136">You can use the visualizers to view text, XML, or HTML data values in displays that match the data types, for example, viewing XML files in a browser window.</span></span>  
  
 <span data-ttu-id="31e2d-137">デバッグ モードでは、識別子の上にマウス ポインターを移動すると、式の名前とその現在の値が **クイック ヒント** ポップアップに表示されます。</span><span class="sxs-lookup"><span data-stu-id="31e2d-137">In debug mode, when you move the mouse pointer over an identifier, a **Quick Info** pop up is displayed with the name of the expression and its current value.</span></span> <span data-ttu-id="31e2d-138">詳細については、「[クイック ヒント &#40;IntelliSense&#41;](quick-info-intellisense.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="31e2d-138">For more information, see [Quick Info &#40;IntelliSense&#41;](quick-info-intellisense.md).</span></span>  
  
## <a name="breakpoints"></a><span data-ttu-id="31e2d-139">ブレークポイント</span><span class="sxs-lookup"><span data-stu-id="31e2d-139">Breakpoints</span></span>  
 <span data-ttu-id="31e2d-140">**[ブレークポイント]** ウィンドウでは、現在設定されているブレークポイントを表示および管理できます。</span><span class="sxs-lookup"><span data-stu-id="31e2d-140">You can use the **Breakpoints** window to view and manage the currently set breakpoints.</span></span> <span data-ttu-id="31e2d-141">詳細については、「 [Transact-SQL コードのステップ実行](step-through-transact-sql-code.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="31e2d-141">For more information, see [Step Through Transact-SQL Code](step-through-transact-sql-code.md).</span></span>  
  
## <a name="call-stacks"></a><span data-ttu-id="31e2d-142">呼び出し履歴</span><span class="sxs-lookup"><span data-stu-id="31e2d-142">Call Stacks</span></span>  
 <span data-ttu-id="31e2d-143">**[呼び出し履歴]** ウィンドウには、現在の実行場所が表示されます。また、実行が元のエディター ウィンドウから [!INCLUDE[tsql](../../includes/tsql-md.md)] モジュール (関数、ストアド プロシージャ、またはトリガー) 経由で現在の実行場所まで、どのように渡されたかについての情報も表示されます。</span><span class="sxs-lookup"><span data-stu-id="31e2d-143">The **Call Stack** window displays the current execution location, and information about how execution passed from the original editor window through any [!INCLUDE[tsql](../../includes/tsql-md.md)] modules (functions, stored procedures, or triggers) to reach the current execution location.</span></span> <span data-ttu-id="31e2d-144">**[呼び出し履歴]** ウィンドウの各行はスタック フレームと呼ばれ、次のいずれかの項目を表します。</span><span class="sxs-lookup"><span data-stu-id="31e2d-144">Each row in the **Call Stack** window is called a stack frame and represents any one of the following items:</span></span>  
  
-   <span data-ttu-id="31e2d-145">現在の実行場所</span><span class="sxs-lookup"><span data-stu-id="31e2d-145">The current execution location.</span></span>  
  
-   <span data-ttu-id="31e2d-146">1 つのモジュールから別のモジュールへの呼び出し</span><span class="sxs-lookup"><span data-stu-id="31e2d-146">A call from one module to another.</span></span>  
  
-   <span data-ttu-id="31e2d-147">エディター ウィンドウから [!INCLUDE[tsql](../../includes/tsql-md.md)] モジュールへの呼び出し</span><span class="sxs-lookup"><span data-stu-id="31e2d-147">A call from an editor window to a [!INCLUDE[tsql](../../includes/tsql-md.md)] module.</span></span>  
  
 <span data-ttu-id="31e2d-148">スタックの順序は、モジュールが呼び出された順序の逆順になっています。</span><span class="sxs-lookup"><span data-stu-id="31e2d-148">The order of the stack is the reverse of that in which the modules were called.</span></span> <span data-ttu-id="31e2d-149">現在の実行場所はスタックの最上部に表示され、元の呼び出しは最下部に表示されます。</span><span class="sxs-lookup"><span data-stu-id="31e2d-149">The current execution location is at the top of the stack and the original call at the bottom.</span></span> <span data-ttu-id="31e2d-150">スタック フレームの左余白の黄色の矢印は、デバッガーが実行を一時停止したフレームを表します。</span><span class="sxs-lookup"><span data-stu-id="31e2d-150">A yellow arrow on the left margin of the stack frame identifies the frame in which the debugger paused execution.</span></span>  
  
 <span data-ttu-id="31e2d-151">**[名前]** 列には、次の情報が記録されます。</span><span class="sxs-lookup"><span data-stu-id="31e2d-151">The **Name** column records the following information:</span></span>  
  
-   <span data-ttu-id="31e2d-152">次のレベルへの呼び出しを行ったコード行を含む呼び出し元のモジュール。</span><span class="sxs-lookup"><span data-stu-id="31e2d-152">The source module that contains the line of code that called down to the next level.</span></span>  
  
-   <span data-ttu-id="31e2d-153">スタック上の次のモジュールを呼び出したコード行。</span><span class="sxs-lookup"><span data-stu-id="31e2d-153">The line of code that called the next module on the stack.</span></span>  
  
-   <span data-ttu-id="31e2d-154">パラメーターを受け取るストアド プロシージャまたは関数が呼び出された場合、すべてのパラメーターについて、名前、データ型、および値も表示されます。</span><span class="sxs-lookup"><span data-stu-id="31e2d-154">If the call went to a stored procedure or function that took parameters, the names, data types, and values of all the parameters are also listed.</span></span>  
  
 <span data-ttu-id="31e2d-155">**[ローカル]** 、 **[ウォッチ]** 、および **[クイック ウォッチ]** の各ウィンドウ内の式は、現在のスタック フレームに対して評価されます。</span><span class="sxs-lookup"><span data-stu-id="31e2d-155">The expressions in the **Locals**, **Watch**, and **QuickWatch** windows are evaluated for the current stack frame.</span></span> <span data-ttu-id="31e2d-156">既定では、現在のスタック フレームは、デバッガーが実行を一時停止したスタック内の最上位のフレームです。</span><span class="sxs-lookup"><span data-stu-id="31e2d-156">By default, the current stack frame is the top frame in the stack, where the debugger paused execution.</span></span> <span data-ttu-id="31e2d-157">別のスタック フレームを現在のフレームとして指定した場合、 **[ローカル]** 、 **[ウォッチ]** 、および **[クイック ウォッチ]** の各ウィンドウ内の式は、新しいスタック フレームに対して再評価されます。</span><span class="sxs-lookup"><span data-stu-id="31e2d-157">When you specify another stack frame as the current frame, the expressions in the **Locals**, **Watch**, and **QuickWatch** windows are reevaluated for the new stack frame.</span></span> <span data-ttu-id="31e2d-158">現在のスタック フレームを変更するには、フレームをダブルクリックするか、またはフレームをクリックし、 **[フレームに切り替え]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="31e2d-158">You can change the current stack frame by either by double-clicking a frame or clicking a frame and selecting **Switch To Frame**.</span></span> <span data-ttu-id="31e2d-159">その時点で、 **[ローカル]** 、 **[ウォッチ]** 、および **[クイック ウォッチ]** の各ウィンドウ内の式が新しいフレームに対して再評価されます。</span><span class="sxs-lookup"><span data-stu-id="31e2d-159">At that point, the expressions in the **Locals**, **Watch**, and **QuickWatch** windows are reevaluated for the new frame.</span></span> <span data-ttu-id="31e2d-160">現在のスタック フレームがスタック内で最上位のフレームでない場合、現在のスタック フレームは、スタック フレームの左余白の緑色の矢印によって識別されます。</span><span class="sxs-lookup"><span data-stu-id="31e2d-160">Whenever the current stack frame is not the top frame in the stack, a green arrow on the left margin of the stack frame identifies the current stack frame.</span></span>  
  
 <span data-ttu-id="31e2d-161">スタック フレームを右クリックし、 **[ソース コードへ移動]** を選択すると、そのフレームのコードがクエリ エディター ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="31e2d-161">When you right-click a stack frame and select **Go To Source Code**, the code for that frame is displayed in a Query Editor window.</span></span> <span data-ttu-id="31e2d-162">ただし、そのフレームは現在のフレームには設定されず、 **[ローカル]** 、 **[ウォッチ]** 、および **[クイック ウォッチ]** の各ウィンドウの内容も変更されません。</span><span class="sxs-lookup"><span data-stu-id="31e2d-162">However, that frame is not made the current frame, and the contents of the **Locals**, **Watch**, and **QuickWatch** windows are not changed.</span></span>  
  
## <a name="system-information-and-transact-sql-results"></a><span data-ttu-id="31e2d-163">システム情報および Transact-SQL の結果</span><span class="sxs-lookup"><span data-stu-id="31e2d-163">System Information and Transact-SQL Results</span></span>  
 <span data-ttu-id="31e2d-164">**[出力]** ウィンドウには、デバッガーから出力される状態メッセージおよびイベント メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="31e2d-164">The debugger lists its status and event messages in the **Output** window.</span></span> <span data-ttu-id="31e2d-165">たとえば、デバッガーがいつ他のプロセスにアタッチしたか、デバッガー スレッドがいつ終了したかなどの情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="31e2d-165">This includes information such as when the debugger attaches to other processes or when debugger threads end.</span></span>  
  
 <span data-ttu-id="31e2d-166">デバッグ モードのとき、クエリ エディターの **[結果]** タブと **[メッセージ]** タブはアクティブ状態で維持されます。</span><span class="sxs-lookup"><span data-stu-id="31e2d-166">While in debug mode, the **Results** and **Messages** tabs are still active in the Query Editor.</span></span> <span data-ttu-id="31e2d-167">**[結果]** タブには、デバッグ セッション中に実行された [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントからの結果セットが表示されます。</span><span class="sxs-lookup"><span data-stu-id="31e2d-167">The **Results** tab continues to display the result sets from the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that are executed during a debugging session.</span></span> <span data-ttu-id="31e2d-168">**[メッセージ]** タブには、システム メッセージ (たとえば " *xx* 行処理されました") や、PRINT ステートメントおよび RAISERROR ステートメントの出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="31e2d-168">The **Messages** tab continues to display system messages, such as *xx* Rows Affected and the output of PRINT and RAISERROR statements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31e2d-169">参照</span><span class="sxs-lookup"><span data-stu-id="31e2d-169">See Also</span></span>  
 <span data-ttu-id="31e2d-170">[[ローカル] ウィンドウ](transact-sql-debugger-locals-window.md) </span><span class="sxs-lookup"><span data-stu-id="31e2d-170">[Locals Window](transact-sql-debugger-locals-window.md) </span></span>  
 <span data-ttu-id="31e2d-171">[[ウォッチ] ウィンドウ](transact-sql-debugger-watch-window.md) </span><span class="sxs-lookup"><span data-stu-id="31e2d-171">[Watch Window](transact-sql-debugger-watch-window.md) </span></span>  
 <span data-ttu-id="31e2d-172">[[クイック ウォッチ] ダイアログ ボックス](transact-sql-debugger-quickwatch-dialog-box.md) </span><span class="sxs-lookup"><span data-stu-id="31e2d-172">[QuickWatch Dialog Box](transact-sql-debugger-quickwatch-dialog-box.md) </span></span>  
 <span data-ttu-id="31e2d-173">[[ブレークポイント] ウィンドウ](transact-sql-debugger-breakpoints-window.md) </span><span class="sxs-lookup"><span data-stu-id="31e2d-173">[Breakpoints Window](transact-sql-debugger-breakpoints-window.md) </span></span>  
 <span data-ttu-id="31e2d-174">[[呼び出し履歴] ウィンドウ](transact-sql-debugger-call-stack-window.md) </span><span class="sxs-lookup"><span data-stu-id="31e2d-174">[Call Stack Window](transact-sql-debugger-call-stack-window.md) </span></span>  
 <span data-ttu-id="31e2d-175">[[スレッド] ウィンドウ](transact-sql-debugger-threads-window.md) </span><span class="sxs-lookup"><span data-stu-id="31e2d-175">[Threads Window](transact-sql-debugger-threads-window.md) </span></span>  
 <span data-ttu-id="31e2d-176">[[出力ウィンドウ]](transact-sql-debugger-output-window.md) </span><span class="sxs-lookup"><span data-stu-id="31e2d-176">[Output Window](transact-sql-debugger-output-window.md) </span></span>  
 [<span data-ttu-id="31e2d-177">Transact-SQL デバッガー</span><span class="sxs-lookup"><span data-stu-id="31e2d-177">Transact-SQL Debugger</span></span>](transact-sql-debugger.md)  
  
  