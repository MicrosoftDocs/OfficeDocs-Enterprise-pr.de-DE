---
title: Anzeigen des Status der Directory-Synchronisierung in Office 365
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
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: Hier erfahren Sie, wie Sie die verzeichnissynchronisierung deaktivieren. Sie können auch den Status anzeigen.
ms.openlocfilehash: c843fa4d71976cbdd0d6d3d10720e2845b26796c
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541029"
---
# <a name="view-directory-synchronization-status-in-office-365"></a>Anzeigen des Status der Directory-Synchronisierung in Office 365
Wenn Sie Ihre lokale Active Directory mit Azure AD durch die Synchronisierung Ihrer lokalen Umgebung mit Office 365 integriert haben, können Sie auch den Status der Synchronisierung überprüfen.
  
## <a name="view-directory-synchronization-status"></a>Anzeigen des Status Directory-Synchronisierung
- Melden Sie sich bei Office 365 Administrationscenter, und wählen Sie **Dirsync-Status** auf der Homepage. 
- Alternativ können Sie für **Benutzer** wechseln \> **aktive Benutzer**, und wählen Sie auf der Seite **aktive Benutzer** **Weitere** \> **Directory-Synchronisierung**. Wählen Sie im Bereich **Directory-Synchronisierung** **Wechseln Sie zur Dirsync-Verwaltung**.
    
## <a name="information-on-the-manage-directory-synchronization-page"></a>Informationen auf der Seite verwalten Directory-Synchronisierung

Die folgende Tabelle enthält die Features, die Sie können Informationen auf der Seite zu erhalten.
  
Liegt ein Problem mit der verzeichnissynchronisierung, werden auf dieser Seite auch die Fehler aufgeführt. Weitere Informationen zu anderen Fehlern, die auftreten können, finden Sie unter [Identifizieren von verzeichnissynchronisierungsfehlern in Office 365](identify-directory-synchronization-errors.md).
  
|**Element**|**Neuigkeiten für**|
|:-----|:-----|
|**Domänen überprüft** | Anzahl von Domänen in Ihrer Office 365-Mandanten, dass Sie Sie überprüft haben besitzen. |
|**Domänen, die nicht überprüft.** | Domänen, die Sie hinzugefügt haben, die aber nicht überprüft. |
|**Verzeichnissynchronisierung aktiviert** |True oder False. Gibt an, ob Sie die verzeichnissynchronisierung aktiviert haben. |
|**Neueste Directory-Synchronisierung** | Zeitpunkt der letzten Directory Sync ausgeführt wurde. Zeigt eine Warnung und einen Link für Problembehandlungstool die letzte Synchronisierung befand sich mehr als drei Tage zurückliegt. |
|**Kennwortsynchronisierung aktiviert** | True oder False. Gibt an, ob Sie Kennwort Hash Sync zwischen unsere lokalen und Office 365-Mandanten verfügen. |
|**Letzte Kennwortsynchronisierung** | Zeitpunkt der letzten Hash kennwortsynchronisierung ausgeführt wurde. Zeigt eine Warnung und einen Link für Problembehandlungstool die letzte Synchronisierung befand sich mehr als drei Tage zurückliegt. |
|**Directory Sync-Client-version** | Enthält einen Link herunterladen, wenn eine neue Version des Azure AD-Connect freigegeben wurde. |
|**IDFix-Tool** | Laden Sie Link, um [IDFix](install-and-run-idfix.md), ein Tool, das Sie verwenden können, um lokale Active Directory zu überprüfen. |
|**Directory Sync-Dienstkonto** | Zeigt den Namen der Sie Office 365 Directory Sync-Dienstkonto. |