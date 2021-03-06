---
title: Interfaccia ICLRTask2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask2
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask2
helpviewer_keywords: ICLRTask2 interface [.NET Framework hosting]
ms.assetid: b5a22ebc-0582-49de-91f9-97a3d9789290
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5f2312d193031eae556f55b061a36259531d013b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtask2-interface"></a>Interfaccia ICLRTask2
Fornisce tutte le funzionalità del [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interfaccia; inoltre, fornisce metodi che consentono l'interruzione di thread per ritardare il thread corrente.  
  
## <a name="methods"></a>Metodi  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[BeginPreventAsyncAbort (metodo)](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)|Ritardi nuove richieste di interruzione sul thread corrente.|  
|[EndPreventAsyncAbort (metodo)](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)|Consente di nuovo o richieste di interruzione del thread restituiscono di thread in sospeso interrompe il thread corrente.|  
  
## <a name="remarks"></a>Note  
 Il `ICLRTask2` interfaccia eredita il `ICLRTask` l'interfaccia e aggiunge i metodi che consentono all'host di ritardo interruzioni del thread, per proteggere un'area di codice che non deve avere esito negativo. La chiamata `BeginPreventAsyncAbort` incrementa il contatore di ritardo di interruzione per il thread corrente e la chiamata `EndPreventAsyncAbort` decrementa il. Le chiamate a `BeginPreventAsyncAbort` e `EndPreventAsyncAbort` possono essere annidati. Fino a quando il contatore è maggiore di zero, vengono posticipate interruzioni del thread per il thread corrente.  
  
 Se le chiamate a `BeginPreventAsyncAbort` e `EndPreventAsyncAbort` non sono associato, è possibile raggiungere uno stato nel quale thread viene interrotta non può essere recapitato al thread corrente.  
  
 Il ritardo non è valido per un thread che interrompe se stesso.  
  
 La funzionalità esposta da questa funzionalità viene utilizzata internamente dalla macchina virtuale (VM). Un utilizzo improprio di questi metodi può causare un comportamento non specificato nella macchina virtuale. Ad esempio, la chiamata `EndPreventAsyncAbort` senza prima chiamare `BeginPreventAsyncAbort` Impossibile impostare il contatore a zero quando la macchina virtuale ha incrementato in precedenza in. Analogamente, il contatore interno non viene verificato per overflow. Se superato questo limite integrale perché aumenta di host e la macchina virtuale, il comportamento risultante è specificato.  
  
 Per informazioni sui membri ereditati da `ICLRTask` e sugli altri utilizzi di questa interfaccia, vedere il [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interfaccia.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** Mscoree. H  
  
 **Libreria:** inclusa come risorsa in MSCorEE.dll  
  
 **Versioni di .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [ICLRTask (interfaccia)](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [ICLRTaskManager (interfaccia)](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [IHostTask (interfaccia)](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [IHostTaskManager (interfaccia)](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [Interfacce di hosting](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
