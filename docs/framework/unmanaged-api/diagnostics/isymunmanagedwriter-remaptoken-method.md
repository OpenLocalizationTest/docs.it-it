---
title: Metodo ISymUnmanagedWriter::RemapToken
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.RemapToken
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::RemapToken
helpviewer_keywords:
- ISymUnmanagedWriter::RemapToken method [.NET Framework debugging]
- RemapToken method [.NET Framework debugging]
ms.assetid: bca92682-ee1e-467f-8fb0-d8d4617f82fe
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 857b68c0443e7b23af30ed64ecc9b78af0b40880
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriterremaptoken-method"></a>Metodo ISymUnmanagedWriter::RemapToken
Notifica il writer di simboli che è stato rimappato un token di metadati come i metadati è stato creato. Se il writer di simboli è archiviato il token precedente nell'archivio di simboli, deve aggiornare che il token con il nuovo valore oppure salvare la mappa per il lettore di simboli corrispondenti modificare il mapping durante la fase di lettura.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT RemapToken(  
    [in] mdToken  oldToken,  
    [in] mdToken  newToken);  
```  
  
#### <a name="parameters"></a>Parametri  
 `oldToken`  
 [in] Il token di metadati che è stato rimappato.  
  
 `newToken`  
 [in] Il nuovo token di metadati a cui `oldToken` rimappato.  
  
## <a name="return-value"></a>Valore restituito  
 S_OK se il metodo ha esito positivo. in caso contrario, E_FAIL o un altro codice di errore.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Vedere anche  
 [ISymUnmanagedWriter (interfaccia)](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
