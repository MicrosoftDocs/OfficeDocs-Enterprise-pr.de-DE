---
title: Anzeigen von Verzeichnis Synchronisierungsfehlern in Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
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
description: Informationen zum Anzeigen von Verzeichnis Synchronisierungsfehlern in Microsoft 365 Admin Center.
ms.openlocfilehash: b1cda68590131967ea2fe91506c8e71769f4c32b
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067521"
---
# <a name="view-directory-synchronization-errors-in-office-365"></a>Anzeigen von Verzeichnis Synchronisierungsfehlern in Office 365

Verzeichnis Synchronisierungsfehler können im [Microsoft 365 Admin Center](https://admin.microsoft.com)angezeigt werden. Nur die Fehler des Benutzerobjekts werden angezeigt. Informationen zum Anzeigen von Fehlern mithilfe von PowerShell finden Sie unter [Identifizieren von Objekten mit DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).

Weitere Informationen finden Sie unter [Beheben von Problemen mit der Verzeichnissynchronisierung für Office 365](fix-problems-with-directory-synchronization.md) , um erkannte Probleme zu beheben.
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a>Anzeigen von Verzeichnis Synchronisierungsfehlern im Admin Center

So zeigen Sie Fehler im Admin Center an:
  
1. Melden Sie sich mit Ihrem Geschäfts- oder Schulkonto bei Office 365 an. 
    
2. Wechseln Sie zum [Admin Center](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).
    
3. Auf der **Start** Seite sehen Sie die Dirsync- **Status** Kachel. 
    
    ![Die Dirsync-Status Kachel in der Admin Center-Vorschau](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. Wählen Sie auf der Kachel **Dirsync Status** aus, um zur Seite **Verzeichnis Synchronisierungsstatus** zu wechseln. 
    
    Am unteren Rand der Seite sehen Sie, ob es Dirsync-Fehler gibt.
    
    ![Auf der Seite Verzeichnis Synchronisierungs Status wird angezeigt, ob Dirsync-Objekt Fehler vorliegen.](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    Wählen Sie "Dirsync- **Objekt Fehler** " aus, um zu einer detaillierten Ansicht der Verzeichnis Synchronisierungsfehler zu wechseln. 
    
    > [!NOTE]
    > Sie können auch auf die Seite **Dirsync Errors** wechseln, wenn Sie sich für Dirsync- **Objekt Fehler** auf der Dirsync- **Status** Kachel entschieden haben. 
  
![Seite "Dirsync-Fehler"](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. Wählen Sie auf der Seite Dirsync- **Fehler** einen der aufgeführten Fehler aus, um den Detailbereich mit Informationen zu dem Fehler anzuzeigen, und Tipps zur Problembehebung. 
