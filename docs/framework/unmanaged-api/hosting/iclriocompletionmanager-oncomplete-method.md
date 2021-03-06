---
title: Metodo ICLRIoCompletionManager::OnComplete
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRIoCompletionManager.OnComplete
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRIoCompletionManager::OnComplete
helpviewer_keywords:
- OnComplete method [.NET Framework hosting]
- ICLRIoCompletionManager::OnComplete method [.NET Framework hosting]
ms.assetid: 003f6974-9727-4322-bed5-e330d1224d0b
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9bd38679d1b8d099e5eb6330e03e2333b03780dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="iclriocompletionmanageroncomplete-method"></a>Metodo ICLRIoCompletionManager::OnComplete
Notifica lo stato di una richiesta dei / o che è stato effettuato mediante una chiamata a common language runtime (CLR) di [IHostIoCompletionManager:: Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) metodo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT OnComplete (  
    [in] DWORD dwErrorCode,  
    [in] DWORD NumberOfBytesTransferred,  
    [in] void* pvOverlapped  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwErrorCode`  
 [in] Valore HRESULT che indica lo stato dell'operazione di associazione.  
  
-   S_OK indica che l'operazione è stata completata.  
  
-   HOST_E_INTERRUPTED indica che la chiamata è terminata prima del completamento.  
  
-   E_FAIL indica che si è verificato un errore sconosciuto e irreversibile.  
  
 `NumberOfBytesTransferred`  
 [in] Il numero di byte trasferiti durante l'elaborazione della richiesta dei / o.  
  
 `pvOverlapped`  
 [in] Un puntatore al `OVERLAPPED` struttura che è stato passato alla chiamata di `IHostIoCompletionManager::Bind` (metodo).  
  
## <a name="return-value"></a>Valore restituito  
  
|HRESULT|Descrizione|  
|-------------|-----------------|  
|S_OK|`OnComplete`stato restituito correttamente.|  
|HOST_E_CLRNOTAVAILABLE|CLR non è stato caricato in un processo oppure si trova in uno stato in cui non può eseguire codice gestito o elaborare correttamente la chiamata.|  
|HOST_E_TIMEOUT|Timeout della chiamata.|  
|HOST_E_NOT_OWNER|Il chiamante non dispone del blocco.|  
|HOST_E_ABANDONED|Un evento è stato annullato mentre un thread bloccato o fiber era in attesa su di esso.|  
|E_FAIL|Si è verificato un errore irreversibile sconosciuto. Se un metodo restituisce E_FAIL, Common Language Runtime non è più utilizzabile all'interno del processo. Le chiamate successive ai metodi di hosting restituiranno HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Note  
 Se l'host implementa un'astrazione di completamento i/o, CLR effettua le richieste dei / o tramite l'host utilizzando i metodi di [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md). L'host chiama quindi il `OnComplete` metodo per notificare il runtime del risultato di tali richieste.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** Mscoree. H  
  
 **Libreria:** inclusa come risorsa in MSCorEE.dll  
  
 **Versioni di .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [ICLRIoCompletionManager (interfaccia)](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [IHostIoCompletionManager (interfaccia)](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 [IHostThreadPoolManager (interfaccia)](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
