---
title: Metodo ICorDebugHeapValue2::CreateHandle
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapValue2.CreateHandle
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapValue2::CreateHandle
helpviewer_keywords:
- CreateHandle method [.NET Framework debugging]
- ICorDebugHeapValue2::CreateHandle method [.NET Framework debugging]
ms.assetid: fbc418e8-fa22-420d-84ec-e0e1800db041
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7feef9af174a63976729f91b5a0b4967fea55b23
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugheapvalue2createhandle-method"></a><span data-ttu-id="7a16a-102">Metodo ICorDebugHeapValue2::CreateHandle</span><span class="sxs-lookup"><span data-stu-id="7a16a-102">ICorDebugHeapValue2::CreateHandle Method</span></span>
<span data-ttu-id="7a16a-103">Crea un handle del tipo specificato per il valore di heap rappresentato dall'oggetto ICorDebugHeapValue2.</span><span class="sxs-lookup"><span data-stu-id="7a16a-103">Creates a handle of the specified type for the heap value represented by this ICorDebugHeapValue2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a16a-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="7a16a-104">Syntax</span></span>  
  
```  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,   
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7a16a-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="7a16a-105">Parameters</span></span>  
 `type`  
 <span data-ttu-id="7a16a-106">[in] Valore dell'enumerazione CorDebugHandleType che specifica il tipo di handle da creare.</span><span class="sxs-lookup"><span data-stu-id="7a16a-106">[in] A value of the CorDebugHandleType enumeration that specifies the type of handle to be created.</span></span>  
  
 `ppHandle`  
 <span data-ttu-id="7a16a-107">[out] Un puntatore all'indirizzo di un oggetto ICorDebugHandleValue che rappresenta il nuovo handle per il valore dell'heap.</span><span class="sxs-lookup"><span data-stu-id="7a16a-107">[out] A pointer to the address of an ICorDebugHandleValue object that represents the new handle for this heap value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a16a-108">Note</span><span class="sxs-lookup"><span data-stu-id="7a16a-108">Remarks</span></span>  
 <span data-ttu-id="7a16a-109">L'handle verrà creato nel dominio dell'applicazione che è associato il valore dell'heap e non sarà più valido se il dominio applicazione viene scaricato.</span><span class="sxs-lookup"><span data-stu-id="7a16a-109">The handle will be created in the application domain that is associated with the heap value, and will become invalid if the application domain gets unloaded.</span></span>  
  
 <span data-ttu-id="7a16a-110">Più chiamate a questa funzione per lo stesso valore di heap creerà più handle.</span><span class="sxs-lookup"><span data-stu-id="7a16a-110">Multiple calls to this function for the same heap value will create multiple handles.</span></span> <span data-ttu-id="7a16a-111">Poiché gli handle di influire sulle prestazioni del garbage collector, il debugger deve limitarsi a un numero relativamente ridotto di handle (circa 256) che sono attive contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="7a16a-111">Because handles affect the performance of the garbage collector, the debugger should limit itself to a relatively small number of handles (about 256) that are active at a time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a16a-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="7a16a-112">Requirements</span></span>  
 <span data-ttu-id="7a16a-113">**Piattaforme:** vedere [requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a16a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a16a-114">**Intestazione:** CorDebug.idl, Cordebug. H</span><span class="sxs-lookup"><span data-stu-id="7a16a-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7a16a-115">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a16a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a16a-116">**Versioni di .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a16a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>