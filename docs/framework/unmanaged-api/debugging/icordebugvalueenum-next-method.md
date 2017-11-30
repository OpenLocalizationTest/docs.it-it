---
title: Metodo ICorDebugValueEnum::Next
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValueEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValueEnum::Next
helpviewer_keywords:
- ICorDebugValueEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugValueEnum interface [.NET Framework debugging]
ms.assetid: f5ef94dd-dfee-49d3-a398-b110f8906dd8
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 71775db7134c8f376099b0820f4330602d3db0e6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugvalueenumnext-method"></a><span data-ttu-id="6db3c-102">Metodo ICorDebugValueEnum::Next</span><span class="sxs-lookup"><span data-stu-id="6db3c-102">ICorDebugValueEnum::Next Method</span></span>
<span data-ttu-id="6db3c-103">Ottiene il numero specificato di istanze di "ICorDebugValue" dell'enumerazione, a partire dalla posizione corrente.</span><span class="sxs-lookup"><span data-stu-id="6db3c-103">Gets the specified number of "ICorDebugValue" instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6db3c-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="6db3c-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugValue *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6db3c-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="6db3c-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="6db3c-106">[in] Il numero di `ICorDebugValue` istanze da recuperare.</span><span class="sxs-lookup"><span data-stu-id="6db3c-106">[in] The number of `ICorDebugValue` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="6db3c-107">[out] Matrice di puntatori, ognuno dei quali punta a un `ICorDebugValue` oggetto.</span><span class="sxs-lookup"><span data-stu-id="6db3c-107">[out] An array of pointers, each of which points to an `ICorDebugValue` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="6db3c-108">[out] Puntatore al numero di `ICorDebugValue` istanze effettivamente restituite.</span><span class="sxs-lookup"><span data-stu-id="6db3c-108">[out] Pointer to the number of `ICorDebugValue` instances actually returned.</span></span> <span data-ttu-id="6db3c-109">Questo valore può essere null se `celt` è uno.</span><span class="sxs-lookup"><span data-stu-id="6db3c-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6db3c-110">Requisiti</span><span class="sxs-lookup"><span data-stu-id="6db3c-110">Requirements</span></span>  
 <span data-ttu-id="6db3c-111">**Piattaforme:** vedere [requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6db3c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6db3c-112">**Intestazione:** CorDebug.idl, Cordebug. H</span><span class="sxs-lookup"><span data-stu-id="6db3c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6db3c-113">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6db3c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6db3c-114">**Versioni di .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6db3c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6db3c-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6db3c-115">See Also</span></span>  
    
 