---
title: Enumerazione ValidatorFlags
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ValidatorFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: ValidatorFlags
helpviewer_keywords: ValidatorFlags enumeration [.NET Framework hosting]
ms.assetid: a3f5c266-3fcc-4ad1-aaf5-4cdbe26304ad
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f283beb79ec47454185800bd772904c3c696c7c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="validatorflags-enumeration"></a>Enumerazione ValidatorFlags
Contiene valori che indicano il tipo di convalida che deve essere eseguita in una chiamata al [ICLRValidator:: Validate](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md) metodo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
enum ValidatorFlags {  
    VALIDATOR_EXTRA_VERBOSE =       0x00000001,  
    VALIDATOR_SHOW_SOURCE_LINES =   0x00000002,  
    VALIDATOR_CHECK_ILONLY =        0x00000004,  
    VALIDATOR_CHECK_PEFORMAT_ONLY = 0x00000008,  
    VALIDATOR_NOCHECK_PEFORMAT =    0x00000010,  
};  
```  
  
## <a name="members"></a>Membri  
  
|Membro|Descrizione|  
|------------|-----------------|  
|`VALIDATOR_CHECK_ILONLY`|Specifica che solo il Microsoft intermediate language (MSIL) nel file eseguibile deve essere convalidato.|  
|`VALIDATOR_CHECK_PEFORMAT_ONLY`|Specifica che solo il formato del file eseguibile deve essere convalidato.|  
|`VALIDATOR_EXTRA_VERBOSE`|Specifica che tutti i tipi di convalida devono essere eseguiti e segnalati a.|  
|`VALIDATOR_NOCHECK_PEFORMAT`|Specifica che il formato del file eseguibile non deve essere convalidato.|  
|`VALIDATOR_SHOW_SOURCE_LINES`|Specifica che i messaggi di errore di convalida devono includere le righe di codice sorgente che generano errori di convalida. Valore di questo campo non è valido in .NET Framework versione 2.0.|  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** IValidator. idl, IValidator.h  
  
 **Libreria:** MSCorEE.dll  
  
 **Versioni di .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [ICLRErrorReportingManager (interfaccia)](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 [Enumerazioni di hosting](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
