---
title: 大きなデータの取得 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- BLOBs, OLE objects
- DBPROP_ACCESSORDER property
- SQL Server Native Client OLE DB provider, BLOBs
- large data, OLE objects
ms.assetid: a31c5632-96aa-483f-a307-004c5149fbc0
author: rothja
ms.author: jroth
ms.openlocfilehash: 38602df026d2e752a758672dde23a59a26ad4917
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741926"
---
# <a name="getting-large-data"></a>大きなデータの取得
  一般に、コンシューマーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **ISequentialStream**インターフェイスポインターによって参照されていないデータを処理する他のコードから、Native Client OLE DB プロバイダーストレージオブジェクトを作成するコードを分離する必要があります。  
  
 このトピックでは、次の関数で使用可能な機能について説明します。  
  
-   IRowset:GetData  
  
-   IRow::GetColumns  
  
-   ICommand::Execute  
  
 DBPROP_ACCESSORDER プロパティ (行セットプロパティグループ) が DBPROPVAL_AO_SEQUENTIAL または DBPROPVAL_AO_SEQUENTIALSTORAGEOBJECTS のいずれかの値に設定されている場合、コンシューマーは**GetNextRows**メソッドの呼び出しで1行のデータのみをフェッチする必要があります。これは、BLOB データがバッファリングされていないためです。 DBPROP_ACCESSORDER の値を DBPROPVAL_AO_RANDOM に設定した場合は、**GetNextRows** で複数行のデータをフェッチできます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンシューマーによって要求されるまで、から大きなデータを取得しません。 コンシューマーは、すべての短いデータを 1 つのアクセサーにバインドし、次に 1 つ以上の一時アクセサーを使用して、必要に応じて大きなデータ値を取得する必要があります。  
  
## <a name="example"></a>例  
 次の例では、大きなデータ値を 1 つの列から取得します。  
  
```  
HRESULT GetUnboundData  
    (  
    IRowset* pIRowset,  
    HROW hRow,  
    ULONG nCol,   
    BYTE* pUnboundData  
    )  
    {  
    UINT                cbRow = sizeof(IUnknown*) + sizeof(ULONG);  
    BYTE*               pRow = new BYTE[cbRow];  
  
    DBOBJECT            dbobject;  
  
    IAccessor*          pIAccessor = NULL;  
    HACCESSOR           haccessor;  
  
    DBBINDING           dbbinding;  
    ULONG               ulbindstatus;  
  
    ULONG               dwStatus;  
    ISequentialStream*  pISequentialStream;  
    ULONG               cbRead;  
  
    HRESULT             hr;  
  
    // Set up the DBOBJECT structure.  
    dbobject.dwFlags = STGM_READ;  
    dbobject.iid = IID_ISequentialStream;  
  
    // Create the DBBINDING, requesting a storage-object pointer from  
    // The SQL Server Native Client OLE DB provider.  
    dbbinding.iOrdinal = nCol;  
    dbbinding.obValue = 0;  
    dbbinding.obStatus = sizeof(IUnknown*);  
    dbbinding.obLength = 0;  
    dbbinding.pTypeInfo = NULL;  
    dbbinding.pObject = &dbobject;  
    dbbinding.pBindExt = NULL;  
    dbbinding.dwPart = DBPART_VALUE | DBPART_STATUS;  
    dbbinding.dwMemOwner = DBMEMOWNER_CLIENTOWNED;  
    dbbinding.eParamIO = DBPARAMIO_NOTPARAM;  
    dbbinding.cbMaxLen = 0;  
    dbbinding.dwFlags = 0;  
    dbbinding.wType = DBTYPE_IUNKNOWN;  
    dbbinding.bPrecision = 0;  
    dbbinding.bScale = 0;  
  
    if (FAILED(hr = pIRowset->  
        QueryInterface(IID_IAccessor, (void**) &pIAccessor)))  
        {  
        // Process QueryInterface failure.  
        return (hr);  
        }  
  
    // Create the accessor.  
    if (FAILED(hr = pIAccessor->CreateAccessor(DBACCESSOR_ROWDATA, 1,  
        &dbbinding, 0, &haccessor, &ulbindstatus)))  
        {  
        // Process error from CreateAccessor.  
        pIAccessor->Release();  
        return (hr);  
        }  
  
    // Read and process BLOCK_SIZE bytes at a time.  
    if (SUCCEEDED(hr = pIRowset->GetData(hRow, haccessor, pRow)))  
        {  
        dwStatus = *((ULONG*) (pRow + dbbinding.obStatus));  
  
        if (dwStatus == DBSTATUS_S_ISNULL)  
            {  
            // Process NULL data  
            }  
        else if (dwStatus == DBSTATUS_S_OK)  
            {  
            pISequentialStream = *((ISequentialStream**)   
                (pRow + dbbinding.obValue));  
  
            do  
                {  
                if (SUCCEEDED(hr =  
                    pISequentialStream->Read(pUnboundData,  
                    BLOCK_SIZE, &cbRead)))  
                    {  
                    pUnboundData += cbRead;  
                    }  
                }  
            while (SUCCEEDED(hr) && cbRead >= BLOCK_SIZE);  
  
            pISequentialStream->Release();  
            }  
        }  
    else  
        {  
        // Process error from GetData.  
        }  
  
    pIAccessor->ReleaseAccessor(haccessor, NULL);  
    pIAccessor->Release();  
    delete [] pRow;  
  
    return (hr);  
    }  
```  
  
## <a name="see-also"></a>参照  
 [Blob と OLE オブジェクト](blobs-and-ole-objects.md)   
 [大きな値をとるデータ型の使用](../native-client/features/using-large-value-types.md)  
  
  
