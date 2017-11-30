---
title: Metodo IMetaDataImport::EnumMemberRefs
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumMemberRefs
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumMemberRefs
helpviewer_keywords:
- EnumMemberRefs method [.NET Framework metadata]
- IMetaDataImport::EnumMemberRefs method [.NET Framework metadata]
ms.assetid: e97c97a6-6e4f-41f5-9af1-9b3cf3bdbd6b
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a9a47d723aaf7dd83bc488a07b040b43a206be55
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenummemberrefs-method"></a><span data-ttu-id="be574-102">Metodo IMetaDataImport::EnumMemberRefs</span><span class="sxs-lookup"><span data-stu-id="be574-102">IMetaDataImport::EnumMemberRefs Method</span></span>
<span data-ttu-id="be574-103">Enumera i token MemberRef che rappresentano i membri del tipo specificato.</span><span class="sxs-lookup"><span data-stu-id="be574-103">Enumerates MemberRef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be574-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="be574-104">Syntax</span></span>  
  
```  
HRESULT EnumMemberRefs (  
   [in, out] HCORENUM    *phEnum,   
   [in]   mdToken        tkParent,   
   [out]  mdMemberRef    rMemberRefs[],   
   [in]   ULONG          cMax,   
   [out]  ULONG          *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="be574-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="be574-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="be574-106">[in, out] Un puntatore all'enumeratore.</span><span class="sxs-lookup"><span data-stu-id="be574-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="be574-107">[in] Un token TypeDef, TypeRef, MethodDef o ModuleRef per il tipo i cui membri sono da enumerare.</span><span class="sxs-lookup"><span data-stu-id="be574-107">[in] A TypeDef, TypeRef, MethodDef, or ModuleRef token for the type whose members are to be enumerated.</span></span>  
  
 `rMemberRefs`  
 <span data-ttu-id="be574-108">[out] Matrice utilizzata per archiviare i token MemberRef.</span><span class="sxs-lookup"><span data-stu-id="be574-108">[out] The array used to store MemberRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="be574-109">[in] Dimensione massima della matrice `rMemberRefs`.</span><span class="sxs-lookup"><span data-stu-id="be574-109">[in] The maximum size of the `rMemberRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="be574-110">[out] Il numero effettivo di token di MemberRef restituiti in `rMemberRefs`.</span><span class="sxs-lookup"><span data-stu-id="be574-110">[out] The actual number of MemberRef tokens returned in `rMemberRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="be574-111">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="be574-111">Return Value</span></span>  
  
|<span data-ttu-id="be574-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="be574-112">HRESULT</span></span>|<span data-ttu-id="be574-113">Descrizione</span><span class="sxs-lookup"><span data-stu-id="be574-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="be574-114">`EnumMemberRefs`stato restituito correttamente.</span><span class="sxs-lookup"><span data-stu-id="be574-114">`EnumMemberRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="be574-115">Non sono presenti token MemberRef da enumerare.</span><span class="sxs-lookup"><span data-stu-id="be574-115">There are no MemberRef tokens to enumerate.</span></span> <span data-ttu-id="be574-116">In tal caso, `pcTokens` è impostato su zero.</span><span class="sxs-lookup"><span data-stu-id="be574-116">In that case, `pcTokens` is to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="be574-117">Requisiti</span><span class="sxs-lookup"><span data-stu-id="be574-117">Requirements</span></span>  
 <span data-ttu-id="be574-118">**Piattaforme:** vedere [requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be574-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be574-119">**Intestazione:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="be574-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="be574-120">**Libreria:** inclusa come risorsa in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="be574-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="be574-121">**Versioni di .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be574-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be574-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="be574-122">See Also</span></span>  
 [<span data-ttu-id="be574-123">IMetaDataImport (interfaccia)</span><span class="sxs-lookup"><span data-stu-id="be574-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="be574-124">IMetaDataImport2 (interfaccia)</span><span class="sxs-lookup"><span data-stu-id="be574-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)