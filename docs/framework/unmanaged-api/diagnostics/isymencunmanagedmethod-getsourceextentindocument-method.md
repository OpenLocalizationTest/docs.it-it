---
title: Metodo ISymENCUnmanagedMethod::GetSourceExtentInDocument
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymENCUnmanagedMethod.GetSourceExtentInDocument
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymENCUnmanagedMethod::GetSourceExtentInDocument
helpviewer_keywords:
- GetSourceExtentInDocument method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetSourceExtentInDocument method [.NET Framework debugging]
ms.assetid: 9c5566ab-4ec7-4b61-9753-839bb90ae78c
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3cff81968926f608de8d28d730a00e79dc8b1c3b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2017
---
# <a name="isymencunmanagedmethodgetsourceextentindocument-method"></a>Metodo ISymENCUnmanagedMethod::GetSourceExtentInDocument
Ottiene il valore più piccolo start riga e la riga finale per il metodo in un documento specifico.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetSourceExtentInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [out] ULONG32* pstartLine,  
    [out] ULONG32* pendLine);  
```  
  
#### <a name="parameters"></a>Parametri  
 `document`  
 [in] Puntatore al documento.  
  
 `pstartLine`  
 [out] Un puntatore a un `ULONG32` che riceve la riga iniziale.  
  
 `pendLine`  
 [out] Un puntatore a un `ULONG32` che riceve la riga finale.  
  
## <a name="return-value"></a>Valore restituito  
 S_OK se il metodo ha esito positivo. in caso contrario, E_FAIL o un altro codice di errore.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Vedere anche  
 [ISymENCUnmanagedMethod (interfaccia)](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
