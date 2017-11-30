---
title: Interfaccia ICorDebugCode3
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode3
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode3
helpviewer_keywords: ICorDebugCode3 interface [.NET Framework debugging]
ms.assetid: 70f07c9e-0614-4bee-ac34-09fe6c51c5a9
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ee60d052c65df64b1a753166b301ba0012cdc8e4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugcode3-interface"></a><span data-ttu-id="c640c-102">Interfaccia ICorDebugCode3</span><span class="sxs-lookup"><span data-stu-id="c640c-102">ICorDebugCode3 Interface</span></span>
<span data-ttu-id="c640c-103">Fornisce un metodo che estende "ICorDebugCode" e "ICorDebugCode2" per ottenere informazioni su un valore restituito gestito.</span><span class="sxs-lookup"><span data-stu-id="c640c-103">Provides a method that extends "ICorDebugCode" and "ICorDebugCode2" to provide information about a managed return value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c640c-104">Metodi</span><span class="sxs-lookup"><span data-stu-id="c640c-104">Methods</span></span>  
  
|<span data-ttu-id="c640c-105">Metodo</span><span class="sxs-lookup"><span data-stu-id="c640c-105">Method</span></span>|<span data-ttu-id="c640c-106">Descrizione</span><span class="sxs-lookup"><span data-stu-id="c640c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c640c-107">Metodo GetReturnValueLiveOffset</span><span class="sxs-lookup"><span data-stu-id="c640c-107">GetReturnValueLiveOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)|<span data-ttu-id="c640c-108">Per un offset IL specificato, ottiene gli offset nativi in un punto di interruzione deve essere posizionato in modo che il debugger è possibile ottenere il valore restituito da una funzione.</span><span class="sxs-lookup"><span data-stu-id="c640c-108">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c640c-109">Note</span><span class="sxs-lookup"><span data-stu-id="c640c-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c640c-110">Questa interfaccia non supporta la chiamata in modalità remota, tra computer o tra processi.</span><span class="sxs-lookup"><span data-stu-id="c640c-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c640c-111">Requisiti</span><span class="sxs-lookup"><span data-stu-id="c640c-111">Requirements</span></span>  
 <span data-ttu-id="c640c-112">**Piattaforme:** vedere [requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c640c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c640c-113">**Intestazione:** CorDebug.idl, Cordebug. H</span><span class="sxs-lookup"><span data-stu-id="c640c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c640c-114">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c640c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c640c-115">**Versioni di .NET framework:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c640c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c640c-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c640c-116">See Also</span></span>  
    
    
    
 [<span data-ttu-id="c640c-117">Interfaccia ICorDebugILFrame3</span><span class="sxs-lookup"><span data-stu-id="c640c-117">ICorDebugILFrame3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)  
 [<span data-ttu-id="c640c-118">Interfacce di debug</span><span class="sxs-lookup"><span data-stu-id="c640c-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)