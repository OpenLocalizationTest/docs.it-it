---
title: Metodo ICorDebugUnmanagedCallback::DebugEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugUnmanagedCallback.DebugEvent
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugUnmanagedCallback::DebugEvent
helpviewer_keywords:
- DebugEvent method [.NET Framework debugging]
- ICorDebugUnmanagedCallback::DebugEvent method [.NET Framework debugging]
ms.assetid: be9cab04-65ec-44d5-a39a-f90709fdd043
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 008ae1bd1a5774604bf2c0f196352dcf07da6ee7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugunmanagedcallbackdebugevent-method"></a><span data-ttu-id="24f3d-102">Metodo ICorDebugUnmanagedCallback::DebugEvent</span><span class="sxs-lookup"><span data-stu-id="24f3d-102">ICorDebugUnmanagedCallback::DebugEvent Method</span></span>
<span data-ttu-id="24f3d-103">Notifica al debugger che un evento nativo è stato attivato.</span><span class="sxs-lookup"><span data-stu-id="24f3d-103">Notifies the debugger that a native event has been fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24f3d-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="24f3d-104">Syntax</span></span>  
  
```  
HRESULT DebugEvent (  
    [in] LPDEBUG_EVENT  pDebugEvent,  
    [in] BOOL           fOutOfBand  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="24f3d-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="24f3d-105">Parameters</span></span>  
 `pDebugEvent`  
 <span data-ttu-id="24f3d-106">[in] Un puntatore all'evento nativo.</span><span class="sxs-lookup"><span data-stu-id="24f3d-106">[in] A pointer to the native event.</span></span>  
  
 `fOutOfBand`  
 <span data-ttu-id="24f3d-107">[in] `true`, se l'interazione con lo stato del processo gestito è impossibile dopo che si verifica un evento non gestito, fino a quando il debugger chiama [ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md); in caso contrario, `false`.</span><span class="sxs-lookup"><span data-stu-id="24f3d-107">[in] `true`, if interaction with the managed process state is impossible after an unmanaged event occurs, until the debugger calls [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md); otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24f3d-108">Note</span><span class="sxs-lookup"><span data-stu-id="24f3d-108">Remarks</span></span>  
 <span data-ttu-id="24f3d-109">Se il thread in fase di debug è un thread Win32, non utilizzare tutti i membri di Win32 interfaccia di debug.</span><span class="sxs-lookup"><span data-stu-id="24f3d-109">If the thread being debugged is a Win32 thread, do not use any members of the Win32 debugging interface.</span></span> <span data-ttu-id="24f3d-110">È possibile chiamare `ICorDebugController::Continue` solo su un thread Win32 e solo continuando dopo un evento fuori banda.</span><span class="sxs-lookup"><span data-stu-id="24f3d-110">You can call `ICorDebugController::Continue` only on a Win32 thread and only when continuing past an out-of-band event.</span></span>  
  
 <span data-ttu-id="24f3d-111">Il `DebugEvent` callback non segue le regole standard per i callback.</span><span class="sxs-lookup"><span data-stu-id="24f3d-111">The `DebugEvent` callback does not follow the standard rules for callbacks.</span></span> <span data-ttu-id="24f3d-112">Quando si chiama `DebugEvent`, il processo sarà semplicemente, lo stato di arresto del debug del sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="24f3d-112">When you call `DebugEvent`, the process will be in the raw, OS-debug stopped state.</span></span> <span data-ttu-id="24f3d-113">Il processo non verranno sincronizzato.</span><span class="sxs-lookup"><span data-stu-id="24f3d-113">The process will not be synchronized.</span></span> <span data-ttu-id="24f3d-114">Passerà automaticamente allo stato sincronizzato quando è necessario soddisfare le richieste di informazioni sul codice gestito, che potrebbe comportare l'altro annidati `DebugEvent` callback.</span><span class="sxs-lookup"><span data-stu-id="24f3d-114">It will automatically enter the synchronized state when necessary to satisfy requests for information about managed code, which may result in other nested `DebugEvent` callbacks.</span></span>  
  
 <span data-ttu-id="24f3d-115">Chiamare [ICorDebugProcess:: ClearCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md) sul processo per ignorare un evento di eccezione prima di continuare il processo.</span><span class="sxs-lookup"><span data-stu-id="24f3d-115">Call [ICorDebugProcess::ClearCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md) on the process to ignore an exception event before continuing the process.</span></span> <span data-ttu-id="24f3d-116">Chiamare questo metodo invia la richiesta continua DBG_CONTINUE anziché DBG_EXCEPTION_NOT_HANDLED e cancella automaticamente i punti di interruzione fuori banda e le eccezioni solo passaggio.</span><span class="sxs-lookup"><span data-stu-id="24f3d-116">Calling this method sends DBG_CONTINUE instead of DBG_EXCEPTION_NOT_HANDLED on the continue request, and automatically clears out-of-band breakpoints and single-step exceptions.</span></span> <span data-ttu-id="24f3d-117">Gli eventi fuori banda possono provenire in qualsiasi momento, anche quando l'applicazione in fase di debug viene visualizzato arrestato e se esiste già un evento in banda in sospeso.</span><span class="sxs-lookup"><span data-stu-id="24f3d-117">Out-of-band events can come at any time, even when the application being debugged appears stopped and when an outstanding in-band event already exists.</span></span>  
  
 <span data-ttu-id="24f3d-118">In .NET Framework versione 2.0, il debugger deve proseguire immediatamente dopo un evento punto di interruzione fuori banda.</span><span class="sxs-lookup"><span data-stu-id="24f3d-118">In the .NET Framework version 2.0, the debugger should immediately continue past an out-of-band breakpoint event.</span></span> <span data-ttu-id="24f3d-119">Il debugger deve utilizzare il [ICorDebugProcess2::](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) e [ICorDebugProcess2:: ClearUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md) metodi per aggiungere e rimuovere i punti di interruzione.</span><span class="sxs-lookup"><span data-stu-id="24f3d-119">The debugger should be using the [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) and [ICorDebugProcess2::ClearUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md) methods to add and remove breakpoints.</span></span> <span data-ttu-id="24f3d-120">Questi metodi si passa automaticamente i punti di interruzione fuori banda.</span><span class="sxs-lookup"><span data-stu-id="24f3d-120">These methods will skip over any out-of-band breakpoints automatically.</span></span> <span data-ttu-id="24f3d-121">Di conseguenza, i punti di interruzione solo fuori banda da inviare devono essere i punti di interruzione non elaborati che sono già nel flusso di istruzioni, ad esempio una chiamata a Win32 `DebugBreak` (funzione).</span><span class="sxs-lookup"><span data-stu-id="24f3d-121">Thus, the only out-of-band breakpoints that get dispatched should be raw breakpoints that are already in the instruction stream, such as a call to the Win32 `DebugBreak` function.</span></span> <span data-ttu-id="24f3d-122">Non tentare di utilizzare `ICorDebugProcess::ClearCurrentException`, [ICorDebugProcess:: GetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess:: SetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md), o qualsiasi altro membro del [l'API di debug](../../../../docs/framework/unmanaged-api/debugging/index.md).</span><span class="sxs-lookup"><span data-stu-id="24f3d-122">Do not try to use `ICorDebugProcess::ClearCurrentException`, [ICorDebugProcess::GetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess::SetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md), or any other member of the [debugging API](../../../../docs/framework/unmanaged-api/debugging/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24f3d-123">Requisiti</span><span class="sxs-lookup"><span data-stu-id="24f3d-123">Requirements</span></span>  
 <span data-ttu-id="24f3d-124">**Piattaforme:** vedere [requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24f3d-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24f3d-125">**Intestazione:** CorDebug.idl, Cordebug. H</span><span class="sxs-lookup"><span data-stu-id="24f3d-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="24f3d-126">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24f3d-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24f3d-127">**Versioni di .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24f3d-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24f3d-128">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="24f3d-128">See Also</span></span>  
 [<span data-ttu-id="24f3d-129">ICorDebugUnmanagedCallback (interfaccia)</span><span class="sxs-lookup"><span data-stu-id="24f3d-129">ICorDebugUnmanagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)