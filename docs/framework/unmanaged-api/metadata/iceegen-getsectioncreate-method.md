---
title: Metodo ICeeGen::GetSectionCreate
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.GetSectionCreate
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::GetSectionCreate
helpviewer_keywords:
- ICeeGen::GetSectionCreate method [.NET Framework metadata]
- GetSectionCreate method [.NET Framework metadata]
ms.assetid: 154b2460-59ce-4874-a9f2-1b3353486ac5
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2ea9cb20b62e1b1fa8e726ba0c49c5e24202530c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2017
---
# <a name="iceegengetsectioncreate-method"></a>Metodo ICeeGen::GetSectionCreate
Genera l'errore e ottiene una sezione di codice utilizzando il nome specificato e i valori di flag.  
  
 Questo metodo è obsoleto e non deve essere utilizzato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetSectionCreate (  
    [in]  const char     *name,  
    [in]  DWORD          flags,  
    [out] HCEESECTION    *section  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `name`  
 [in] Un puntatore a una stringa che specifica il nome della sezione da creare.  
  
 `flags`  
 [in] Flag che specificano le opzioni.  
  
 `section`  
 [out] Puntatore alla sezione di codice appena creato.  
  
## <a name="remarks"></a>Note  
 Chiamare `GetSectionCreate` solo se sono necessari requisiti speciali di sezione che non sono gestiti da altri metodi.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** Cor. h  
  
 **Libreria:** usata come risorsa in MsCorEE.dll  
  
 **Versioni di .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [ICeeGen (interfaccia)](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
