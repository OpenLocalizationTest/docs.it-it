---
title: Metodo ICorProfilerCallback::RootReferences
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RootReferences
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RootReferences
helpviewer_keywords:
- RootReferences method [.NET Framework profiling]
- ICorProfilerCallback::RootReferences method [.NET Framework profiling]
ms.assetid: dbdf853b-d1a4-4828-8ef7-53d121d8e6ae
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a12dec1ed0fecad235090592def9689f60e50193
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackrootreferences-method"></a>Metodo ICorProfilerCallback::RootReferences
Notifica al profiler con informazioni sui riferimenti principali dopo l'operazione di garbage collection.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT RootReferences(  
    [in] ULONG    cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[] );  
```  
  
#### <a name="parameters"></a>Parametri  
 `cRootRefs`  
 [in] Il numero di riferimenti nel `rootRefIds` matrice.  
  
 `rootRefIds`  
 [in] Matrice di ID di oggetto che fanno riferimento a un oggetto statico o un oggetto di nello stack.  
  
## <a name="remarks"></a>Note  
 Entrambi `RootReferences` e [ICorProfilerCallback2:: Rootreferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) vengono chiamati per notificare al profiler. I profiler in genere implementano uno o l'altro, ma non entrambi, in quanto le informazioni passate in `RootReferences2` è un superset di passati `RootReferences`.  
  
 È possibile che il `rootRefIds` matrice per contenere un oggetto null. Ad esempio, tutti i riferimenti all'oggetto dichiarati nello stack vengono trattati come radici dal garbage collector e verrà segnalati sempre.  
  
 L'ID di oggetto restituito da `RootReferences` non validi durante il callback vero e proprio, perché l'operazione di garbage collection potrebbe essere ancora spostando gli oggetti provenienti da indirizzi precedenti a nuovi indirizzi. Di conseguenza, i profiler non devono tentare di controllare gli oggetti durante una `RootReferences` chiamare. Quando [ICorProfilerCallback2::](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) viene chiamato, tutti gli oggetti sono stati spostati nelle nuove posizioni e possono essere controllati in modo sicuro.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorProf.idl, CorProf.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
