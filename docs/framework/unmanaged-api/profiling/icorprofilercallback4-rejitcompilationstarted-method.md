---
title: Metodo ICorProfilerCallback4::ReJITCompilationStarted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback4.ReJITCompilationStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback4::ReJITCompilationStarted
helpviewer_keywords:
- ReJITCompilationStarted method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITCompilationStarted method [.NET Framework profiling]
ms.assetid: 512fdd00-262a-4456-a075-365ef4133c4d
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ddcacf72d21ec076fe74a1c069311ef3f73a20c2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a>Metodo ICorProfilerCallback4::ReJITCompilationStarted
Notifica al profiler che il compilatore di just-in-time (JIT) è stato avviato ricompilare una funzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT ReJITCompilationStarted(    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a>Parametri  
 `functionId`  
 [in] L'ID della funzione che il compilatore JIT è stata avviata da ricompilare.  
  
 `rejitId`  
 [in] L'ID della ricompilazione della nuova versione della funzione.  
  
 `fIsSafeToBlock`  
 [in] `true` per indicare che il blocco può causare il runtime di attesa per il thread chiamante da questo callback; `false` per indicare che il blocco non avranno effetto l'operazione di runtime. Il valore `true` non influisce sul runtime, ma possono influenzare i risultati di profilatura.  
  
## <a name="remarks"></a>Note  
 È possibile ricevere più di una coppia di `ReJITCompilationStarted` e [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) metodo chiama per ogni funzione a causa del modo il runtime gestisce i costruttori di classe. Ad esempio, il runtime Avvia ricompilazione di un metodo, ma il costruttore della classe per classe B deve essere eseguito. Pertanto, il runtime ricompila il costruttore di classe B e lo esegue. Durante l'esecuzione, il costruttore che effettua una chiamata al metodo che determina il metodo per la ricompilazione nuovamente. In questo scenario, viene interrotta la ricompilazione prima del metodo. Tuttavia, entrambi tenta ricompilare metodo vengono segnalata con gli eventi di ricompilazione JIT.  
  
 I profiler devono supportare la sequenza di callback di ricompilazione JIT nei casi in cui due thread effettuano callback simultaneamente. Ad esempio, il thread chiama `ReJITCompilationStarted`; tuttavia, prima di un thread chiama [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md), thread B chiama [ICorProfilerCallback:: ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) con l'ID (funzione) dal `ReJITCompilationStarted` callback per thread A. Potrebbe sembrare che l'ID della funzione non deve ancora essere valido perché una chiamata a [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) non ha ancora ricevuto dal profiler. Tuttavia, in questo caso, l'ID della funzione è valido.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorProf.idl, CorProf.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ICorProfilerCallback4 (interfaccia)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 [JITCompilationFinished (metodo)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)  
 [ReJITCompilationFinished (metodo)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)
