---
title: Metodo ICLRRuntimeInfo::LoadLibrary
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.LoadLibrary
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::LoadLibrary
helpviewer_keywords:
- ICLRRuntimeInfo::LoadLibrary method [.NET Framework hosting]
- LoadLibrary method [.NET Framework hosting]
ms.assetid: 4517ada3-4417-4ac5-a150-73da7a87c686
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c1d943f45a4e665836f376bddf65d84329c1900e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimeinfoloadlibrary-method"></a><span data-ttu-id="ad418-102">Metodo ICLRRuntimeInfo::LoadLibrary</span><span class="sxs-lookup"><span data-stu-id="ad418-102">ICLRRuntimeInfo::LoadLibrary Method</span></span>
<span data-ttu-id="ad418-103">Carica una libreria .NET Framework da common language runtime (CLR) rappresentato da un [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfaccia.</span><span class="sxs-lookup"><span data-stu-id="ad418-103">Loads a .NET Framework library from the common language runtime (CLR) represented by an [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="ad418-104">Questo metodo sostituisce il [LoadLibraryShim](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md) (funzione).</span><span class="sxs-lookup"><span data-stu-id="ad418-104">This method supersedes the [LoadLibraryShim](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad418-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="ad418-105">Syntax</span></span>  
  
```  
HRESULT LoadLibrary(  
     [in]  LPCWSTR pwzDllName,  
     [out, retval] HMODULE *phndModule);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ad418-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="ad418-106">Parameters</span></span>  
 `pwzDllName`  
 <span data-ttu-id="ad418-107">[in] Il nome dell'assembly da caricare.</span><span class="sxs-lookup"><span data-stu-id="ad418-107">[in] The name of the assembly to be loaded.</span></span>  
  
 `phndModule`  
 <span data-ttu-id="ad418-108">[out] Handle per l'assembly caricato.</span><span class="sxs-lookup"><span data-stu-id="ad418-108">[out] A handle to the loaded assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ad418-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="ad418-109">Return Value</span></span>  
 <span data-ttu-id="ad418-110">Questo metodo restituisce gli specifici HRESULT seguenti, nonché gli errori di HRESULT che indicano la mancata riuscita del metodo.</span><span class="sxs-lookup"><span data-stu-id="ad418-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ad418-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ad418-111">HRESULT</span></span>|<span data-ttu-id="ad418-112">Descrizione</span><span class="sxs-lookup"><span data-stu-id="ad418-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ad418-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="ad418-113">S_OK</span></span>|<span data-ttu-id="ad418-114">Metodo completato correttamente.</span><span class="sxs-lookup"><span data-stu-id="ad418-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="ad418-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="ad418-115">E_POINTER</span></span>|<span data-ttu-id="ad418-116">`pwzDllName` o `phndModule` è null.</span><span class="sxs-lookup"><span data-stu-id="ad418-116">`pwzDllName` or `phndModule` is null.</span></span>|  
|<span data-ttu-id="ad418-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="ad418-117">E_OUTOFMEMORY</span></span>|<span data-ttu-id="ad418-118">Memoria insufficiente è disponibile per gestire la richiesta.</span><span class="sxs-lookup"><span data-stu-id="ad418-118">Not enough memory is available to handle the request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad418-119">Note</span><span class="sxs-lookup"><span data-stu-id="ad418-119">Remarks</span></span>  
 <span data-ttu-id="ad418-120">Questo metodo carica solo le DLL incluse nel pacchetto ridistribuibile di .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ad418-120">This method only loads DLLs included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="ad418-121">Non può caricare gli assembly generati dall'utente.</span><span class="sxs-lookup"><span data-stu-id="ad418-121">It can not load user-generated assemblies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad418-122">Requisiti</span><span class="sxs-lookup"><span data-stu-id="ad418-122">Requirements</span></span>  
 <span data-ttu-id="ad418-123">**Piattaforme:** vedere [requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad418-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad418-124">**Intestazione:** Metahost. H</span><span class="sxs-lookup"><span data-stu-id="ad418-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ad418-125">**Libreria:** inclusa come risorsa in MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ad418-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ad418-126">**Versioni di .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad418-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad418-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ad418-127">See Also</span></span>  
 [<span data-ttu-id="ad418-128">ICLRRuntimeInfo (interfaccia)</span><span class="sxs-lookup"><span data-stu-id="ad418-128">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="ad418-129">Interfacce di hosting</span><span class="sxs-lookup"><span data-stu-id="ad418-129">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="ad418-130">Hosting</span><span class="sxs-lookup"><span data-stu-id="ad418-130">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)