---
title: Anzeigen von Verzeichnis Synchronisierungsfehlern in Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
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
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: Informationen zum Anzeigen von Verzeichnis Synchronisierungsfehlern in Office 365 Admin Center.
ms.openlocfilehash: 8b7bb16aeddbf1765426c3725cd1f670524ef6d1
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085034"
---
# <a name="view-directory-synchronization-errors-in-office-365"></a>Anzeigen von Verzeichnis Synchronisierungsfehlern in Office 365

Sie können Verzeichnis Synchronisierungsfehler im Office 365 Admin Center anzeigen. Nur die Fehler des Benutzerobjekts werden angezeigt. Informationen zum Anzeigen von Fehlern mithilfe von PowerShell finden Sie unter [Identifizieren von Objekten mit DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).

Weitere Informationen finden Sie unter [Beheben von Problemen mit der Verzeichnissynchronisierung für Office 365](fix-problems-with-directory-synchronization.md) , um erkannte Probleme zu beheben.
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a>Anzeigen von Verzeichnis Synchronisierungsfehlern im Admin Center

So zeigen Sie Fehler im Admin Center an:
  
1. Melden Sie sich bei Office 365 mit Ihrem Geschäfts, Schul- oder Unikonto an. 
    
2. Wechseln Sie zum [Office 365 Admin Center](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).
    
3. Auf der **Start** Seite sehen Sie die Dirsync- **Status** Kachel. 
    
    ![Die dirSync-Status Kachel in der Admin Center-Vorschau](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. Wählen Sie auf der Kachel **Dirsync Status** aus, um zur Seite **Verzeichnis Synchronisierungsstatus** zu wechseln. 
    
    Am unteren Rand der Seite sehen Sie, ob es dirSync-Fehler gibt.
    
    ![Auf der Seite Verzeichnis Synchronisierungs Status wird angezeigt, ob dirSync-Objekt Fehler vorliegen.](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    Wählen Sie "dirSync- **Objekt Fehler** " aus, um zu einer detaillierten Ansicht der Verzeichnis Synchronisierungsfehler zu wechseln. 
    
    > [!NOTE]
    > Sie können auch auf die Seite **Dirsync Errors** wechseln, wenn Sie sich für Dirsync- **Objekt Fehler** auf der Dirsync- **Status** Kachel entschieden haben. 
  
![Seite "dirSync-Fehler"](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. Wählen Sie auf der Seite dirSync- **Fehler** einen der aufgeführten Fehler aus, um den Detailbereich mit Informationen zu dem Fehler anzuzeigen, und Tipps zur Problembehebung. 
