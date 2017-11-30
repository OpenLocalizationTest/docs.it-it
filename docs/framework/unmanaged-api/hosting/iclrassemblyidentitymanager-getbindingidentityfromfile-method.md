---
title: Metodo ICLRAssemblyIdentityManager::GetBindingIdentityFromFile
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyIdentityManager.GetBindingIdentityFromFile
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyIdentityManager::GetBindingIdentityFromFile
helpviewer_keywords:
- GetBindingIdentityFromFile method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetBindingIdentifyFromFile method [.NET Framework hosting]
ms.assetid: 7797562d-7b4c-4bd9-8b93-f35e0e2869e4
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 140240f5f108cdd26cd0e813d7fe47f102a3b941
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromfile-method"></a><span data-ttu-id="856ce-102">Metodo ICLRAssemblyIdentityManager::GetBindingIdentityFromFile</span><span class="sxs-lookup"><span data-stu-id="856ce-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromFile Method</span></span>
<span data-ttu-id="856ce-103">Ottiene l'identità dell'assembly di associazione dati per l'assembly nel percorso del file specificato.</span><span class="sxs-lookup"><span data-stu-id="856ce-103">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="856ce-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="856ce-104">Syntax</span></span>  
  
```  
HRESULT GetBindingIdentityFromFile(  
    [in] LPCWSTR     pwzFilePath,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="856ce-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="856ce-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="856ce-106">[in] Il percorso del file da valutare.</span><span class="sxs-lookup"><span data-stu-id="856ce-106">[in] The path to the file to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="856ce-107">[in] Il valore di [ECLRAssemblyIdentityFlags](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md) enumerazione che indica il tipo di identità di un assembly.</span><span class="sxs-lookup"><span data-stu-id="856ce-107">[in] A value of the [ECLRAssemblyIdentityFlags](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md) enumeration that indicates an assembly's identity type.</span></span> <span data-ttu-id="856ce-108">Fornito per l'estensibilità futura.</span><span class="sxs-lookup"><span data-stu-id="856ce-108">Provided for future extensibility.</span></span> <span data-ttu-id="856ce-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT è l'unico valore che common language runtime (CLR) versione 2.0 supporta.</span><span class="sxs-lookup"><span data-stu-id="856ce-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the common language runtime (CLR) version 2.0 supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="856ce-110">[out] Un buffer contenente i dati di identità di assembly opaca.</span><span class="sxs-lookup"><span data-stu-id="856ce-110">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="856ce-111">[in, out] Un puntatore alla dimensione del `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="856ce-111">[in, out] A pointer to the size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="856ce-112">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="856ce-112">Return Value</span></span>  
  
|<span data-ttu-id="856ce-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="856ce-113">HRESULT</span></span>|<span data-ttu-id="856ce-114">Descrizione</span><span class="sxs-lookup"><span data-stu-id="856ce-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="856ce-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="856ce-115">S_OK</span></span>|<span data-ttu-id="856ce-116">Il metodo è stato restituito correttamente.</span><span class="sxs-lookup"><span data-stu-id="856ce-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="856ce-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="856ce-117">E_INVALIDARG</span></span>|<span data-ttu-id="856ce-118">Fornito `pwzFilePath` è null.</span><span class="sxs-lookup"><span data-stu-id="856ce-118">The supplied `pwzFilePath` is null.</span></span>|  
|<span data-ttu-id="856ce-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="856ce-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="856ce-120">Le dimensioni di `pwzBuffer` è troppo piccolo.</span><span class="sxs-lookup"><span data-stu-id="856ce-120">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="856ce-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="856ce-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="856ce-122">CLR non è stato caricato in un processo oppure si trova in uno stato in cui non può eseguire codice gestito o elaborare correttamente la chiamata.</span><span class="sxs-lookup"><span data-stu-id="856ce-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="856ce-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="856ce-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="856ce-124">Timeout della chiamata.</span><span class="sxs-lookup"><span data-stu-id="856ce-124">The call timed out.</span></span>|  
|<span data-ttu-id="856ce-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="856ce-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="856ce-126">Il chiamante non dispone del blocco.</span><span class="sxs-lookup"><span data-stu-id="856ce-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="856ce-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="856ce-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="856ce-128">Un evento è stato annullato mentre un thread bloccato o fiber era in attesa su di esso.</span><span class="sxs-lookup"><span data-stu-id="856ce-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="856ce-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="856ce-129">E_FAIL</span></span>|<span data-ttu-id="856ce-130">Si è verificato un errore irreversibile sconosciuto.</span><span class="sxs-lookup"><span data-stu-id="856ce-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="856ce-131">Se un metodo restituisce E_FAIL, Common Language Runtime non è più utilizzabile all'interno del processo.</span><span class="sxs-lookup"><span data-stu-id="856ce-131">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="856ce-132">Le chiamate successive ai metodi di hosting restituiranno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="856ce-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="856ce-133">Note</span><span class="sxs-lookup"><span data-stu-id="856ce-133">Remarks</span></span>  
 <span data-ttu-id="856ce-134">`GetBindingIdentityFromFile`viene in genere chiamato due volte.</span><span class="sxs-lookup"><span data-stu-id="856ce-134">`GetBindingIdentityFromFile` is typically called twice.</span></span> <span data-ttu-id="856ce-135">La prima chiamata fornisce un valore null per `pwzBuffer`, e il metodo restituisce le dimensioni appropriate in `pcchBufferSize`.</span><span class="sxs-lookup"><span data-stu-id="856ce-135">The first call supplies a null value for `pwzBuffer`, and the method returns the appropriate size in `pcchBufferSize`.</span></span> <span data-ttu-id="856ce-136">La seconda chiamata viene fornito un buffer allocato in modo appropriato, e il metodo restituisce i dati effettiva del buffer al termine dell'operazione.</span><span class="sxs-lookup"><span data-stu-id="856ce-136">The second call supplies an appropriately allocated buffer, and the method returns with the actual buffer data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="856ce-137">Requisiti</span><span class="sxs-lookup"><span data-stu-id="856ce-137">Requirements</span></span>  
 <span data-ttu-id="856ce-138">**Piattaforme:** vedere [requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="856ce-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="856ce-139">**Intestazione:** Mscoree. H</span><span class="sxs-lookup"><span data-stu-id="856ce-139">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="856ce-140">**Libreria:** inclusa come risorsa in MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="856ce-140">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="856ce-141">**Versioni di .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="856ce-141">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="856ce-142">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="856ce-142">See Also</span></span>  
 [<span data-ttu-id="856ce-143">ICLRAssemblyIdentityManager (interfaccia)</span><span class="sxs-lookup"><span data-stu-id="856ce-143">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="856ce-144">ICLRAssemblyReferenceList (interfaccia)</span><span class="sxs-lookup"><span data-stu-id="856ce-144">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="856ce-145">ICLRHostBindingPolicyManager (interfaccia)</span><span class="sxs-lookup"><span data-stu-id="856ce-145">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)