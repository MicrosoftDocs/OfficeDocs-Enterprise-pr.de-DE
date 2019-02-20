---
title: Deaktivieren der Verzeichnissynchronisierung für Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: Informationen zur Verwendung von PowerShell zum Deaktivieren der Verzeichnissynchronisierung für Office 365
ms.openlocfilehash: 4fbfb6b9e3fcb1512fc4aa9c3d8ee6c37682e58a
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085074"
---
# <a name="turn-off-directory-synchronization-for-office-365"></a>Deaktivieren der Verzeichnissynchronisierung für Office 365
Sie können die Verzeichnissynchronisierung mithilfe von PowerShell deaktivieren. Es wird jedoch nicht empfohlen, die Verzeichnissynchronisierung als Schritt zur Problembehandlung zu deaktivieren. Wenn Sie Unterstützung bei der Problembehandlung bei der Verzeichnissynchronisierung benötigen, lesen Sie den Artikel [Beheben von Problemen mit der Verzeichnissynchronisierung für Office 365](fix-problems-with-directory-synchronization.md) . 
  
[Wenden Sie sich](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) bei Bedarf an den Support für Business-Produkte.
  
## <a name="turn-off-directory-synchronization"></a>Deaktivieren der Verzeichnissynchronisierung  
So deaktivieren Sie die Verzeichnissynchronisierung
  
1. Installieren Sie zunächst die erforderliche Software, und stellen Sie eine Verbindung mit Ihrem Office 365-Abonnement her. Anweisungen für beide finden Sie unter [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=821938).
    
2. Verwenden Sie [Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) , um die Verzeichnissynchronisierung zu deaktivieren: 
    
  ```
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```