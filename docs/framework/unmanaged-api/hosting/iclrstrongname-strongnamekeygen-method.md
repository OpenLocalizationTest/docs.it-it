---
title: Metodo ICLRStrongName::StrongNameKeyGen
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameKeyGen
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyGen method [.NET Framework hosting]
ms.assetid: ac5c1245-9acf-4271-9c08-3d9b7c670df3
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 13eef3e4c0cf4aa8de55aa96335e570ef1985e9a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongnamestrongnamekeygen-method"></a><span data-ttu-id="45d25-102">Metodo ICLRStrongName::StrongNameKeyGen</span><span class="sxs-lookup"><span data-stu-id="45d25-102">ICLRStrongName::StrongNameKeyGen Method</span></span>
<span data-ttu-id="45d25-103">Crea una nuova coppia di chiavi pubblica/privata per l'utilizzo con nome sicuro.</span><span class="sxs-lookup"><span data-stu-id="45d25-103">Creates a new public/private key pair for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45d25-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="45d25-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="45d25-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="45d25-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="45d25-106">[in] Il nome di contenitore di chiavi richiesto.</span><span class="sxs-lookup"><span data-stu-id="45d25-106">[in] The requested key container name.</span></span> <span data-ttu-id="45d25-107">`wszKeyContainer`deve essere una stringa non vuota o null per generare un nome temporaneo.</span><span class="sxs-lookup"><span data-stu-id="45d25-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="45d25-108">[in] Un valore che specifica se mantenere la chiave è stato registrato.</span><span class="sxs-lookup"><span data-stu-id="45d25-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="45d25-109">Sono supportati i seguenti valori:</span><span class="sxs-lookup"><span data-stu-id="45d25-109">The following values are supported:</span></span>  
  
-   <span data-ttu-id="45d25-110">0x00000000 - utilizzato quando `wszKeyContainer` è null per generare un nome di contenitore di chiavi temporaneo.</span><span class="sxs-lookup"><span data-stu-id="45d25-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
-   <span data-ttu-id="45d25-111">0x00000001 (`SN_LEAVE_KEY`)-specifica che la chiave deve essere registrata a sinistra.</span><span class="sxs-lookup"><span data-stu-id="45d25-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="45d25-112">[out] La coppia di chiavi pubblica/privata restituita.</span><span class="sxs-lookup"><span data-stu-id="45d25-112">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="45d25-113">[out] Le dimensioni, in byte, di `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="45d25-113">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="45d25-114">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="45d25-114">Return Value</span></span>  
 <span data-ttu-id="45d25-115">`S_OK`Se il metodo viene completato correttamente. in caso contrario, un valore HRESULT indicante un errore (vedere [valori HRESULT comuni](http://go.microsoft.com/fwlink/?LinkId=213878) per un elenco).</span><span class="sxs-lookup"><span data-stu-id="45d25-115">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45d25-116">Note</span><span class="sxs-lookup"><span data-stu-id="45d25-116">Remarks</span></span>  
 <span data-ttu-id="45d25-117">Il [ICLRStrongName:: StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) metodo crea una chiave a 1024 bit.</span><span class="sxs-lookup"><span data-stu-id="45d25-117">The [ICLRStrongName::StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) method creates a 1024-bit key.</span></span> <span data-ttu-id="45d25-118">Dopo il recupero della chiave, è necessario chiamare il [ICLRStrongName:: StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metodo per rilasciare la memoria allocata.</span><span class="sxs-lookup"><span data-stu-id="45d25-118">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45d25-119">Requisiti</span><span class="sxs-lookup"><span data-stu-id="45d25-119">Requirements</span></span>  
 <span data-ttu-id="45d25-120">**Piattaforme:** vedere [requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45d25-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45d25-121">**Intestazione:** Metahost. H</span><span class="sxs-lookup"><span data-stu-id="45d25-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="45d25-122">**Libreria:** inclusa come risorsa in MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="45d25-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="45d25-123">**Versioni di .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45d25-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45d25-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="45d25-124">See Also</span></span>  
 [<span data-ttu-id="45d25-125">StrongNameKeyGenEx (metodo)</span><span class="sxs-lookup"><span data-stu-id="45d25-125">StrongNameKeyGenEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)  
 [<span data-ttu-id="45d25-126">ICLRStrongName (interfaccia)</span><span class="sxs-lookup"><span data-stu-id="45d25-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)