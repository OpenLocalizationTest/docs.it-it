---
title: Metodo ICorDebugAppDomain::GetObject
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain.GetObject
api_location: corguids.lib
api_type: COM
f1_keywords: ICorDebugAppDomain::GetObject
helpviewer_keywords:
- ICorDebugAppDomain::GetObject method [.NET Framework debugging]
- GetObject method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 78232e6f-ae18-4cfa-a6cd-e79471cf9d76
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c4f923d8e9bf9762d5208dd6e9be527a50a688b1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomaingetobject-method"></a>Metodo ICorDebugAppDomain::GetObject
Ottiene un puntatore a interfaccia per il dominio di applicazione di common language runtime (CLR).  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppObject`  
 [out] Un puntatore all'indirizzo di un oggetto di interfaccia ICorDebugValue che rappresenta il dominio dell'applicazione CLR.  
  
## <a name="return-value"></a>Valore restituito  
 Se un oggetto gestito <xref:System.AppDomain?displayProperty=nameWithType> oggetto non è stato costruito per il dominio applicazione, il metodo restituisce `S_FALSE` e inserisce `NULL` in `*ppObject`.  
  
## <a name="remarks"></a>Note  
 Ogni dominio applicazione in un processo potrebbe essere gestita <xref:System.AppDomain?displayProperty=nameWithType> oggetto runtime che lo rappresenta. Questa funzione Ottiene un oggetto di interfaccia ICorDebugValue che corrisponde a questo gestiti <xref:System.AppDomain?displayProperty=nameWithType> oggetto.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorDebug.idl, Cordebug. H  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]
