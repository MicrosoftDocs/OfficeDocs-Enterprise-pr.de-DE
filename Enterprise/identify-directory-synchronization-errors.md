---
title: Anzeigen von Verzeichnis Synchronisierungsfehlern in Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
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
description: Informationen zum Anzeigen von Verzeichnis Synchronisierungsfehlern im Microsoft 365 Admin Center.
ms.openlocfilehash: d10abc29a08da4352d4c0779698e2062175008b4
ms.sourcegitcommit: d2a3d6eeeaa07510ee94c2bc675284d893221a95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2020
ms.locfileid: "44711645"
---
# <a name="view-directory-synchronization-errors-in-microsoft-365"></a>Anzeigen von Verzeichnis Synchronisierungsfehlern in Microsoft 365

Sie können Verzeichnis Synchronisierungsfehler im [Microsoft 365 Admin Center](https://admin.microsoft.com)anzeigen. Es werden nur die Fehler des Benutzerobjekts angezeigt. Informationen zum Anzeigen von Fehlern mithilfe von PowerShell finden Sie unter [Identifizieren von Objekten mit DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).

Nach der Anzeige finden Sie unter [Beheben von Problemen mit der Verzeichnissynchronisierung für Microsoft 365](fix-problems-with-directory-synchronization.md) , um identifizierte Probleme zu beheben.
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a>Anzeigen von Verzeichnis Synchronisierungsfehlern im Admin Center

So zeigen Sie Fehler im Admin Center an:
  
1. Melden Sie sich mit Ihrem Geschäfts- oder Schulkonto bei Microsoft 365 an. 
    
2. Wechseln Sie zum [Admin Center](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).
    
3. Auf der **Start** Seite wird die Status Kachel **Dirsync** angezeigt. 
    
    ![Die Kachel "DirSync-Status" in Admin Center Preview](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. Wählen Sie auf der Kachel **Dirsync-Status** aus, um zur Seite **Verzeichnis Synchronisierungsstatus** zu wechseln. 
    
    Unten auf der Seite können Sie sehen, ob Dirsync-Fehler vorliegen.
    
    ![Auf der Seite Verzeichnis Synchronisierungs Status können Sie sehen, ob es Fehler des Dirsync-Objekts gibt.](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    Wählen Sie die Option **wir haben Dirsync-Objekt Fehler gefunden** , um zu einer detaillierten Ansicht der Verzeichnis Synchronisierungsfehler zu gelangen. 
    
    > [!NOTE]
    > Sie können auch zur Seite **Dirsync-Fehler** wechseln, wenn Sie die Option **Dirsync-Objekt Fehler** auf der **Status Kachel Dirsync** gefunden haben. 
  
![Dirsync-Fehlerseite](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. Wählen Sie auf der Seite **Dirsync-Fehler** einen der aufgelisteten Fehler aus, um den Detailbereich mit Informationen zum Fehler und Tipps zur Problembehebung anzuzeigen. 
