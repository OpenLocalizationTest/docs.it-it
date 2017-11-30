---
title: Enumerazione COR_PRF_STATIC_TYPE
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_STATIC_TYPE
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_STATIC_TYPE
helpviewer_keywords: COR_PRF_STATIC_TYPE enumeration [.NET Framework profiling]
ms.assetid: 441d7809-5b65-41a5-ba64-2910a8008315
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 446967cc157962a1ec4a87193bbf84b1a356efa6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2017
---
# <a name="corprfstatictype-enumeration"></a><span data-ttu-id="04768-102">Enumerazione COR_PRF_STATIC_TYPE</span><span class="sxs-lookup"><span data-stu-id="04768-102">COR_PRF_STATIC_TYPE Enumeration</span></span>
<span data-ttu-id="04768-103">Indica se un campo è statico e, in tal caso, la qualità statica che si applica al campo.</span><span class="sxs-lookup"><span data-stu-id="04768-103">Indicates whether a field is static and, if so, the static quality that applies to the field.</span></span> <span data-ttu-id="04768-104">Questi valori possono essere combinati utilizzando l'operatore OR bit per indicare che il campo ha più qualità statiche diverse.</span><span class="sxs-lookup"><span data-stu-id="04768-104">These values can be combined using the bitwise OR operation to indicate that the field has multiple, different static qualities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04768-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="04768-105">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_FIELD_NOT_A_STATIC = 0x0,  
    COR_PRF_FIELD_APP_DOMAIN_STATIC = 0x1,  
    COR_PRF_FIELD_THREAD_STATIC = 0x2,  
    COR_PRF_FIELD_CONTEXT_STATIC = 0x4,  
    COR_PRF_FIELD_RVA_STATIC = 0x8  
} COR_PRF_STATIC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="04768-106">Membri</span><span class="sxs-lookup"><span data-stu-id="04768-106">Members</span></span>  
  
|<span data-ttu-id="04768-107">Membro</span><span class="sxs-lookup"><span data-stu-id="04768-107">Member</span></span>|<span data-ttu-id="04768-108">Descrizione</span><span class="sxs-lookup"><span data-stu-id="04768-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FIELD_NOT_A_STATIC`|<span data-ttu-id="04768-109">Il campo non è statico.</span><span class="sxs-lookup"><span data-stu-id="04768-109">The field is not static.</span></span>|  
|`COR_PRF_FIELD_APP_DOMAIN_STATIC`|<span data-ttu-id="04768-110">Il campo è statico a livello di dominio di applicazione.</span><span class="sxs-lookup"><span data-stu-id="04768-110">The field is application domain-static.</span></span>|  
|`COR_PRF_FIELD_THREAD_STATIC`|<span data-ttu-id="04768-111">Il campo è statico.</span><span class="sxs-lookup"><span data-stu-id="04768-111">The field is thread-static.</span></span>|  
|`COR_PRF_FIELD_CONTEXT_STATIC`|<span data-ttu-id="04768-112">Il campo è statico.</span><span class="sxs-lookup"><span data-stu-id="04768-112">The field is context-static.</span></span>|  
|`COR_PRF_FIELD_RVA_STATIC`|<span data-ttu-id="04768-113">Il campo è di indirizzi virtuali relativi (RVA)-statico.</span><span class="sxs-lookup"><span data-stu-id="04768-113">The field is relative virtual address (RVA)-static.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="04768-114">Requisiti</span><span class="sxs-lookup"><span data-stu-id="04768-114">Requirements</span></span>  
 <span data-ttu-id="04768-115">**Piattaforme:** vedere [requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04768-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04768-116">**Intestazione:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="04768-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="04768-117">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="04768-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04768-118">**Versioni di .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04768-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04768-119">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="04768-119">See Also</span></span>  
 [<span data-ttu-id="04768-120">Enumerazioni di profilatura</span><span class="sxs-lookup"><span data-stu-id="04768-120">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)