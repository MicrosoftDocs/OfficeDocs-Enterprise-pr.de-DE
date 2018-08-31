---
title: Deaktivieren der verzeichnissynchronisierung für Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: Hier erfahren Sie, wie Sie mithilfe von PowerShell für Office 365 verzeichnissynchronisierung deaktivieren
ms.openlocfilehash: f47209dd8b6be47b7ae7a4b63a9fae38c5cb498f
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540955"
---
# <a name="turn-off-directory-synchronization-for-office-365"></a>Deaktivieren der verzeichnissynchronisierung für Office 365
PowerShell können Sie um die verzeichnissynchronisierung zu deaktivieren. Es ist jedoch nicht empfohlen, dass Sie die verzeichnissynchronisierung im Rahmen der Problembehandlung zu deaktivieren. Wenn Sie Hilfe bei der Problembehandlung Directory-Synchronisierung benötigen, finden Sie im Artikel [behoben Probleme mit der verzeichnissynchronisierung für Office 365](fix-problems-with-directory-synchronization.md) . 
  
Der [Kontakt support](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) für Business-Produkte bei Bedarf.
  
## <a name="turn-off-directory-synchronization"></a>Deaktivieren der verzeichnissynchronisierung  
So deaktivieren Sie die verzeichnissynchronisierung:
  
1. Erstens Installieren der erforderlichen Software und Verbinden mit Office 365-Abonnements. Anweisungen für beide finden Sie unter [Verbinden mit Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=821938).
    
2. Verwenden Sie [Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) Directory-Synchronisierung zu deaktivieren: 
    
  ```
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```