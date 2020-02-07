---
title: Anzeigen des Status der Verzeichnissynchronisierung in Office 365
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
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: Hier erfahren Sie, wie Sie die Verzeichnissynchronisierung deaktivieren. Sie können den Status auch anzeigen.
ms.openlocfilehash: 74e2eee0086e4f8098221f4aaa30d408091a6a0f
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840982"
---
# <a name="view-directory-synchronization-status-in-office-365"></a>Anzeigen des Status der Verzeichnissynchronisierung in Office 365

Wenn Sie Ihre lokale Active Directory mit Azure AD integriert haben, indem Sie Ihre lokale Umgebung mit Office 365 synchronisieren, können Sie auch den Status der Synchronisierung überprüfen.
  
## <a name="view-directory-synchronization-status"></a>Anzeigen des Status der Verzeichnissynchronisierung

- Melden Sie sich beim [Microsoft 365 Admin Center](https://admin.microsoft.com) an, und wählen Sie auf der Startseite **Dirsync-Status** aus.
- Alternativ können Sie zu " **Benutzer** \> **aktive**Benutzer" wechseln und auf der Seite " **aktive Benutzer** " **Weitere** \> **Verzeichnis Synchronisierungen**auswählen. Wählen Sie im Bereich **Verzeichnissynchronisierung** die Option **zu Dirsync-Verwaltung wechseln**aus.

## <a name="information-on-the-manage-directory-synchronization-page"></a>Informationen auf der Seite "Verzeichnissynchronisierung verwalten"

In der folgenden Tabelle sind die Features aufgeführt, auf denen Sie auf der Seite Informationen abrufen können.
  
Wenn ein Problem mit der Verzeichnissynchronisierung vorliegt, werden die Fehler auch auf dieser Seite aufgeführt. Weitere Informationen zu unterschiedlichen Fehlern, die auftreten können, finden Sie unter [Identifizieren von Verzeichnis Synchronisierungsfehlern in Office 365](identify-directory-synchronization-errors.md).
  
|**Item**|**Zweck**|
|:-----|:-----|
|**Domänen überprüft** | Die Anzahl der Domänen in Ihrem Office 365 Mandanten, die Sie selbst überprüft haben. |
|**Domänen nicht überprüft** | Domänen, die Sie hinzugefügt, aber nicht überprüft haben. |
|**Verzeichnissynchronisierung aktiviert** |True oder false. Gibt an, ob die Verzeichnissynchronisierung aktiviert ist. |
|**Neueste Verzeichnissynchronisierung** | Zeitpunkt der letzten Verzeichnissynchronisierung wurde ausgeführt. Zeigt eine Warnung und einen Link zu einem Tool zur Problembehandlung an, wenn die letzte Synchronisierung vor mehr als drei Tagen stattfand. |
|**Kennwortsynchronisierung aktiviert** | True oder false. Gibt an, ob eine Kennworthash Synchronisierung zwischen unserem lokalen und Ihrem Office 365 Mandanten vorliegt. |
|**Letzte Kennwortsynchronisierung** | Das letzte Mal, als Password Hash Sync ausgeführt wurde. Zeigt eine Warnung und einen Link zu einem Tool zur Problembehandlung an, wenn die letzte Synchronisierung vor mehr als drei Tagen stattfand. |
|**Version des Verzeichnis Synchronisierungs Clients** | Enthält einen Download Link, wenn eine neue Version von Azure AD Connect veröffentlicht wurde. |
|**IDFix-Tool** | Download Link to [IDFix](install-and-run-idfix.md), ein Tool, mit dem Sie lokale Active Directory überprüfen können. |
|**Verzeichnissynchronisierungsdienst Konto** | Zeigt den Namen Ihres Office 365 Verzeichnissynchronisierungsdienst Kontos an. |