---
title: Metodo ICeeGen::GetString
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.GetString
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::GetString
helpviewer_keywords:
- ICeeGen::GetString method [.NET Framework metadata]
- GetString method, ICeeGen interface [.NET Framework metadata]
ms.assetid: 7cc22562-128c-440a-9147-55ff20f173d7
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f7afe07309850a564ec75e69c07f63a3210f3810
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2017
---
# <a name="iceegengetstring-method"></a>Metodo ICeeGen::GetString
Ottiene la stringa archiviata nell'indirizzo virtuale relativo specificato.  
  
 Questo metodo è obsoleto e non deve essere utilizzato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetString (  
    [in]  ULONG      RVA,   
    [out] LPWSTR     *lpString  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `RVA`  
 [in] L'indirizzo virtuale relativo, della stringa da restituire.  
  
 `lpString`  
 [out] La stringa restituita.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** Cor. h  
  
 **Libreria:** usata come risorsa in MsCorEE.dll  
  
 **Versioni di .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [ICeeGen (interfaccia)](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
