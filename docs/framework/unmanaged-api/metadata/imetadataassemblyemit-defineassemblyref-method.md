---
title: Metodo IMetaDataAssemblyEmit::DefineAssemblyRef
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.DefineAssemblyRef
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::DefineAssemblyRef
helpviewer_keywords:
- DefineAssemblyRef method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineAssemblyRef method [.NET Framework metadata]
ms.assetid: 0b284b18-0084-4b3a-912a-5ebe9f29c88b
topic_type: apiref
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 074e589b84e21de4ec3bcc3c54a865297587d383
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyemitdefineassemblyref-method"></a>Metodo IMetaDataAssemblyEmit::DefineAssemblyRef
Crea una struttura `AssemblyRef` che contiene i metadati per l'assembly a cui fa riferimento questo assembly e restituisce il token di metadati associato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT DefineAssemblyRef (  
    [in]  void                *pbPublicKeyOrToken,  
    [in]  ULONG               cbPublicKeyOrToken,  
    [in]  LPCWSTR             szName,  
    [in]  ASSEMBLYMETADATA    pMetaData,  
    [in]  void                *pbHashValue,  
    [in]  ULONG               cbHashValue,  
    [in]  DWORD               dwAssemblyRefFlags,  
    [out] mdAssemblyRef       *pmdar  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pbPublicKeyOrToken`  
 [in] La chiave pubblica del server di pubblicazione dell'assembly di riferimento. La funzione di supporto [StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md) può essere utilizzato per ottenere l'hash della chiave pubblica da passare come questo parametro.  
  
 `cbPublicKeyOrToken`  
 [in] Le dimensioni in byte di `pbPublicKeyOrToken`.  
  
 `szName`  
 [in] Il nome di un testo leggibile dell'assembly. Questo valore non deve superare i 1024 caratteri.  
  
 `pMetaData`  
 [in] Un'istanza ASSEMBLYMETADATA che contiene le informazioni di versione, alla piattaforma e delle impostazioni locali dell'assembly di riferimento.  
  
 `pbHashValue`  
 [in] I dati di hash associati all'assembly di riferimento. Parametro facoltativo.  
  
 `cbHashValue`  
 [in] Le dimensioni in byte di `pbHashValue`.  
  
 `dwAssemblyRefFlags`  
 [in] Combinazione bit per bit di [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) valori che influenzano il comportamento del motore di esecuzione.  
  
 `pmdar`  
 [out] Un puntatore all'oggetto restituito `AssemblyRef` token di metadati.  
  
## <a name="remarks"></a>Note  
 Una `AssemblyRef` struttura dei metadati deve essere definita per ogni assembly che fa riferimento questo assembly.  
  
 In fase di esecuzione, vengono passati i dettagli di un assembly di riferimento per il resolver dell'assembly con un'indicazione che rappresentano le informazioni "così com'è"compilato. Il resolver dell'assembly applica quindi i criteri.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** Cor. h  
  
 **Libreria:** usata come risorsa in MsCorEE.dll  
  
 **Versioni di .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
