---
title: Enumerazione CorCheckDuplicatesFor
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorCheckDuplicatesFor
api_location: mscoree.dll
api_type: COM
f1_keywords: CorCheckDuplicatesFor
helpviewer_keywords: CorCheckDuplicatesFor enumeration [.NET Framework metadata]
ms.assetid: d8ec8d3c-70f7-4cc6-9957-68068fd8f49c
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d9bd0409f22e6ca47a7bc97bec634381158167da
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2017
---
# <a name="corcheckduplicatesfor-enumeration"></a><span data-ttu-id="67963-102">Enumerazione CorCheckDuplicatesFor</span><span class="sxs-lookup"><span data-stu-id="67963-102">CorCheckDuplicatesFor Enumeration</span></span>
<span data-ttu-id="67963-103">Specifica il token di metadati che verrà controllato la presenza di duplicati.</span><span class="sxs-lookup"><span data-stu-id="67963-103">Specifies the metadata tokens that will be checked for duplicates.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67963-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="67963-104">Syntax</span></span>  
  
```  
typedef enum CorCheckDuplicatesFor {  
  
    MDDupAll                    = 0xffffffff,  
    MDDupENC                    = MDDupAll,  
    MDNoDupChecks               = 0x00000000,  
    MDDupTypeDef                = 0x00000001,  
    MDDupInterfaceImpl          = 0x00000002,  
    MDDupMethodDef              = 0x00000004,  
    MDDupTypeRef                = 0x00000008,  
    MDDupMemberRef              = 0x00000010,  
    MDDupCustomAttribute        = 0x00000020,  
    MDDupParamDef               = 0x00000040,  
    MDDupPermission             = 0x00000080,  
    MDDupProperty               = 0x00000100,  
    MDDupEvent                  = 0x00000200,  
    MDDupFieldDef               = 0x00000400,  
    MDDupSignature              = 0x00000800,  
    MDDupModuleRef              = 0x00001000,  
    MDDupTypeSpec               = 0x00002000,  
    MDDupImplMap                = 0x00004000,  
    MDDupAssemblyRef            = 0x00008000,  
    MDDupFile                   = 0x00010000,  
    MDDupExportedType           = 0x00020000,  
    MDDupManifestResource       = 0x00040000,  
    MDDupGenericParam           = 0x00080000,  
    MDDupMethodSpec             = 0x00100000,  
    MDDupGenericParamConstraint = 0x00200000,  
  
    MDDupAssembly               = 0x10000000,  
  
    MDDupDefault =   
        MDNoDupChecks | MDDupTypeRef | MDDupMemberRef |   
        MDDupSignature | MDDupTypeSpec | MDDupMethodSpec  
  
} CorCheckDuplicatesFor;  
```  
  
## <a name="members"></a><span data-ttu-id="67963-105">Membri</span><span class="sxs-lookup"><span data-stu-id="67963-105">Members</span></span>  
  
|<span data-ttu-id="67963-106">Membro</span><span class="sxs-lookup"><span data-stu-id="67963-106">Member</span></span>|<span data-ttu-id="67963-107">Descrizione</span><span class="sxs-lookup"><span data-stu-id="67963-107">Description</span></span>|  
|------------|-----------------|  
|`MDDupAll`|<span data-ttu-id="67963-108">Controllare tutti i token di metadati per i duplicati.</span><span class="sxs-lookup"><span data-stu-id="67963-108">Check all metadata tokens for duplicates.</span></span>|  
|`MDDupENC`|<span data-ttu-id="67963-109">Non usato.</span><span class="sxs-lookup"><span data-stu-id="67963-109">Not used.</span></span>|  
|`MDNoDupChecks`|<span data-ttu-id="67963-110">Non archiviare i token di metadati per i duplicati.</span><span class="sxs-lookup"><span data-stu-id="67963-110">Do not check metadata tokens for duplicates.</span></span>|  
|`MDDupTypeDef`|<span data-ttu-id="67963-111">Verificare la presenza di duplicati di `mdTypeDef` token.</span><span class="sxs-lookup"><span data-stu-id="67963-111">Check for duplicates of `mdTypeDef` tokens.</span></span>|  
|`MDDupInterfaceImpl`|<span data-ttu-id="67963-112">Verificare la presenza di duplicati di `mdInterfaceImpl` token.</span><span class="sxs-lookup"><span data-stu-id="67963-112">Check for duplicates of `mdInterfaceImpl` tokens.</span></span>|  
|`MDDupMethodDef`|<span data-ttu-id="67963-113">Verificare la presenza di duplicati di `mdMethodDef` token.</span><span class="sxs-lookup"><span data-stu-id="67963-113">Check for duplicates of `mdMethodDef` tokens.</span></span>|  
|`MDDupTypeRef`|<span data-ttu-id="67963-114">Verificare la presenza di duplicati di `mdTypeRef` token.</span><span class="sxs-lookup"><span data-stu-id="67963-114">Check for duplicates of `mdTypeRef` tokens.</span></span>|  
|`MDDupMemberRef`|<span data-ttu-id="67963-115">Verificare la presenza di duplicati di `mdMemberRef` token.</span><span class="sxs-lookup"><span data-stu-id="67963-115">Check for duplicates of `mdMemberRef` tokens.</span></span>|  
|`MDDupCustomAttribute`|<span data-ttu-id="67963-116">Verificare la presenza di duplicati di `mdCustomAttribute` token.</span><span class="sxs-lookup"><span data-stu-id="67963-116">Check for duplicates of `mdCustomAttribute` tokens.</span></span>|  
|`MDDupParamDef`|<span data-ttu-id="67963-117">Verificare la presenza di duplicati di `mdParamDef` token.</span><span class="sxs-lookup"><span data-stu-id="67963-117">Check for duplicates of `mdParamDef` tokens.</span></span>|  
|`MDDupPermission`|<span data-ttu-id="67963-118">Verificare la presenza di duplicati di `mdPermission` token.</span><span class="sxs-lookup"><span data-stu-id="67963-118">Check for duplicates of `mdPermission` tokens.</span></span>|  
|`MDDupProperty`|<span data-ttu-id="67963-119">Verificare la presenza di duplicati di `mdProperty` token.</span><span class="sxs-lookup"><span data-stu-id="67963-119">Check for duplicates of `mdProperty` tokens.</span></span>|  
|`MDDupEvent`|<span data-ttu-id="67963-120">Verificare la presenza di duplicati di `mdEvent` token.</span><span class="sxs-lookup"><span data-stu-id="67963-120">Check for duplicates of `mdEvent` tokens.</span></span>|  
|`MDDupFieldDef`|<span data-ttu-id="67963-121">Verificare la presenza di duplicati di `mdFieldDef` token.</span><span class="sxs-lookup"><span data-stu-id="67963-121">Check for duplicates of `mdFieldDef` tokens.</span></span>|  
|`MDDupSignature`|<span data-ttu-id="67963-122">Verificare la presenza di duplicati di `mdSignature` token.</span><span class="sxs-lookup"><span data-stu-id="67963-122">Check for duplicates of `mdSignature` tokens.</span></span>|  
|`MDDupModuleRef`|<span data-ttu-id="67963-123">Verificare la presenza di duplicati di `mdModuleRef` token.</span><span class="sxs-lookup"><span data-stu-id="67963-123">Check for duplicates of `mdModuleRef` tokens.</span></span>|  
|`MDDupTypeSpec`|<span data-ttu-id="67963-124">Verificare la presenza di duplicati di `mdTypeSpec` token.</span><span class="sxs-lookup"><span data-stu-id="67963-124">Check for duplicates of `mdTypeSpec` tokens.</span></span>|  
|`MDDupImplMap`|<span data-ttu-id="67963-125">Verificare la presenza di duplicati di `mdImplMap` token.</span><span class="sxs-lookup"><span data-stu-id="67963-125">Check for duplicates of `mdImplMap` tokens.</span></span>|  
|`MDDupAssemblyRef`|<span data-ttu-id="67963-126">Verificare la presenza di duplicati di `mdAssemblyRef` token.</span><span class="sxs-lookup"><span data-stu-id="67963-126">Check for duplicates of `mdAssemblyRef` tokens.</span></span>|  
|`MDDupFile`|<span data-ttu-id="67963-127">Verificare la presenza di duplicati di `mdFile` token.</span><span class="sxs-lookup"><span data-stu-id="67963-127">Check for duplicates of `mdFile` tokens.</span></span>|  
|`MDDupExportedType`|<span data-ttu-id="67963-128">Verificare la presenza di duplicati di `mdExportedType` token.</span><span class="sxs-lookup"><span data-stu-id="67963-128">Check for duplicates of `mdExportedType` tokens.</span></span>|  
|`MDDupManifestResource`|<span data-ttu-id="67963-129">Verificare la presenza di duplicati di `mdManifestResource` token.</span><span class="sxs-lookup"><span data-stu-id="67963-129">Check for duplicates of `mdManifestResource` tokens.</span></span>|  
|`MDDupGenericParam`|<span data-ttu-id="67963-130">Verificare la presenza di duplicati di `mdGenericParam` token.</span><span class="sxs-lookup"><span data-stu-id="67963-130">Check for duplicates of `mdGenericParam` tokens.</span></span>|  
|`MDDupMethodSpec`|<span data-ttu-id="67963-131">Verificare la presenza di duplicati di `mdMethodSpec` token.</span><span class="sxs-lookup"><span data-stu-id="67963-131">Check for duplicates of `mdMethodSpec` tokens.</span></span>|  
|`MDDupGenericParamConstraint`|<span data-ttu-id="67963-132">Verificare la presenza di duplicati di `mdGenericParamConstraint` token.</span><span class="sxs-lookup"><span data-stu-id="67963-132">Check for duplicates of `mdGenericParamConstraint` tokens.</span></span>|  
|`MDDupAssembly`|<span data-ttu-id="67963-133">Verificare la presenza di duplicati di `mdAssembly` token.</span><span class="sxs-lookup"><span data-stu-id="67963-133">Check for duplicates of `mdAssembly` tokens.</span></span>|  
|`MDDupDefault`|<span data-ttu-id="67963-134">Verificare la presenza di duplicati di `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`, e `mdMethodSpec` token.</span><span class="sxs-lookup"><span data-stu-id="67963-134">Check for duplicates of `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`, and `mdMethodSpec` tokens.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="67963-135">Requisiti</span><span class="sxs-lookup"><span data-stu-id="67963-135">Requirements</span></span>  
 <span data-ttu-id="67963-136">**Piattaforme:** vedere [requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67963-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67963-137">**Intestazione:** CorHdr. H</span><span class="sxs-lookup"><span data-stu-id="67963-137">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="67963-138">**Versioni di .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67963-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67963-139">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="67963-139">See Also</span></span>  
 [<span data-ttu-id="67963-140">Enumerazioni dei metadati</span><span class="sxs-lookup"><span data-stu-id="67963-140">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)