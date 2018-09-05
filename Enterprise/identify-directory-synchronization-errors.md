---
title: Anzeigen von verzeichnissynchronisierungsfehlern in Office 365
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
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: Hier erfahren Sie, wie Sie zum Anzeigen von verzeichnissynchronisierungsfehlern in Office 365 Administrationscenter.
ms.openlocfilehash: 62f1135568261eccf0e7e66b78c5aaff966c7281
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540871"
---
# <a name="view-directory-synchronization-errors-in-office-365"></a>Anzeigen von verzeichnissynchronisierungsfehlern in Office 365

Sie können verzeichnissynchronisierungsfehlern in Office 365 Administrationscenter anzeigen. Nur die Benutzer Objekt-Fehler werden angezeigt. Fehler mithilfe von PowerShell finden Sie unter [identifizieren Objekte mit DirSyncProvisioningErrors](https://go.microsoft.com/fwlink/p/?LinkId=798300).

Nach der Wiedergabe, finden Sie unter [Beheben von Problemen mit der verzeichnissynchronisierung für Office 365](fix-problems-with-directory-synchronization.md) , um identifizierten Probleme zu beheben.
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a>Anzeigen von verzeichnissynchronisierungsfehlern in der Verwaltungskonsole

Zum Anzeigen von Fehlern in der Verwaltungskonsole:
  
1. Melden Sie sich mit Ihrem Geschäfts- oder Schulkonto bei Office 365 an. 
    
2. Öffnen Sie die [zu Office 365 Administrationscenter](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).
    
3. Auf **der Homepage** finden Sie die Kachel **Dirsync-Status** . 
    
    ![Der Status der Dirsync-Kachel im Admin Center – Vorschau](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. Wählen Sie auf die Kachel **Dirsync-Status** So wechseln zur der Seite **Directory Sync Status** . 
    
    Am unteren Rand der Seite können Sie sehen, wenn Dirsync-Fehler aufgetreten sind.
    
    ![Auf der Seite Directory Sync Status können Sie sehen, wenn Dirsync-Objekt Fehler aufgetreten sind](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    Wählen Sie, **wir Dirsync-Objekt Fehler gefunden** , um eine detaillierte Ansicht Synchronisierungsfehler Verzeichnis zu wechseln. 
    
    > [!NOTE]
    > Sie können auch auf der Seite **Dirsync-Fehler** wechseln, wenn Sie auf die Kachel **Dirsync-Status** **wir Dirsync-Objekt Fehler gefunden wählen** . 
  
![Dirsync-Fehler-Seite](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. Wählen Sie auf der Seite **Dirsync-Fehler** der Fehler aus, um die im Detailbereich mit Informationen zu dem Fehler und Tipps zur Problembehebung anzuzeigen. 