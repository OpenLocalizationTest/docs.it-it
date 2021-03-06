---
title: Metodo ISymUnmanagedENCUpdate::GetLocalVariables
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedENCUpdate.GetLocalVariables
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedENCUpdate::GetLocalVariables
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables method [.NET Framework debugging]
- GetLocalVariables method [.NET Framework debugging]
ms.assetid: 5c8840be-ffea-447f-9c8d-178f1eaf8d06
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 492d41402531cb6fb92f90ab0e533fb20c6129df
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedencupdategetlocalvariables-method"></a>Metodo ISymUnmanagedENCUpdate::GetLocalVariables
Ottiene le variabili locali.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetLocalVariables(  
    [in]  mdMethodDef  mdMethodToken,  
    [in]  ULONG        cLocals,  
    [out, size_is(cLocals), length_is(*pceltFetched)]  
        ISymUnmanagedVariable *rgLocals[],  
    [out] ULONG        *pceltFetched);  
```  
  
#### <a name="parameters"></a>Parametri  
 `mdMethodToken`  
 [in] Il token di metadati del metodo.  
  
 `cLocals`  
 [in] Oggetto `ULONG` che indica le dimensioni del `rgLocals` parametro.  
  
 `rgLocals`  
 [out] La matrice restituita di <!--zz<xref:ISymUnmanagedVariable>--> `ISymUnmanagedVariable` istanze.  
  
 `pceltFetched`  
 [out] Un puntatore a un `ULONG` che riceve le dimensioni del `rgLocals` buffer necessaria per contenere le variabili locali.  
  
## <a name="return-value"></a>Valore restituito  
 S_OK se il metodo ha esito positivo. in caso contrario, E_FAIL o un altro codice di errore.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Vedere anche  
 [ISymUnmanagedENCUpdate (interfaccia)](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
