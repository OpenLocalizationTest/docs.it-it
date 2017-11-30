---
title: Metodo IMetaDataAssemblyEmit::SetManifestResourceProps
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.SetManifestResourceProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::SetManifestResourceProps
helpviewer_keywords:
- SetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetManifestResourceProps method [.NET Framework metadata]
ms.assetid: ef77efd1-849c-4e51-ba92-7ee3d2bf0339
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e3cc447b18ac6ccabd642ab0a1fb5b887fb4fbe4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyemitsetmanifestresourceprops-method"></a><span data-ttu-id="57b5a-102">Metodo IMetaDataAssemblyEmit::SetManifestResourceProps</span><span class="sxs-lookup"><span data-stu-id="57b5a-102">IMetaDataAssemblyEmit::SetManifestResourceProps Method</span></span>
<span data-ttu-id="57b5a-103">Modifica la struttura dei metadati `ManifestResource` specificata.</span><span class="sxs-lookup"><span data-stu-id="57b5a-103">Modifies the specified `ManifestResource` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57b5a-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="57b5a-104">Syntax</span></span>  
  
```  
HRESULT SetManifestResourceProps (  
    [in] mdManifestResource  mr,  
    [in] mdToken             tkImplementation,   
    [in] DWORD               dwOffset,  
    [in] DWORD               dwResourceFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="57b5a-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="57b5a-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="57b5a-106">[in] Il token che specifica il `ManifestResource` struttura dei metadati da modificare.</span><span class="sxs-lookup"><span data-stu-id="57b5a-106">[in] The token that specifies the `ManifestResource` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="57b5a-107">[in] Il token, di tipo `File` o `AssemblyRef`, che esegue il mapping al provider di risorse.</span><span class="sxs-lookup"><span data-stu-id="57b5a-107">[in] The token, of type `File` or `AssemblyRef`, that maps to the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="57b5a-108">[in] L'offset all'inizio della risorsa all'interno del file.</span><span class="sxs-lookup"><span data-stu-id="57b5a-108">[in] The offset to the beginning of the resource within the file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="57b5a-109">[in] Combinazione bit per bit dei valori di flag che specificano gli attributi della risorsa.</span><span class="sxs-lookup"><span data-stu-id="57b5a-109">[in] A bitwise combination of flag values that specify the attributes of the resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57b5a-110">Note</span><span class="sxs-lookup"><span data-stu-id="57b5a-110">Remarks</span></span>  
 <span data-ttu-id="57b5a-111">Per creare un `ManifestResource` struttura dei metadati, usare il [IMetaDataAssemblyEmit:: DefineManifestResource](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md) metodo.</span><span class="sxs-lookup"><span data-stu-id="57b5a-111">To create a `ManifestResource` metadata structure, use the [IMetaDataAssemblyEmit::DefineManifestResource](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57b5a-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="57b5a-112">Requirements</span></span>  
 <span data-ttu-id="57b5a-113">**Piattaforme:** vedere [requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57b5a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57b5a-114">**Intestazione:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="57b5a-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="57b5a-115">**Libreria:** usata come risorsa in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="57b5a-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="57b5a-116">**Versioni di .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57b5a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57b5a-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="57b5a-117">See Also</span></span>  
 [<span data-ttu-id="57b5a-118">Interfaccia IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="57b5a-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)