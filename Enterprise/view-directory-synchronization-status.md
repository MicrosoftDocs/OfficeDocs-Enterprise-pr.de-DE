---
title: Anzeigen des Status der Verzeichnissynchronisierung in Office 365
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
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: Erfahren Sie, wie Sie die Verzeichnissynchronisierung deaktivieren. Sie können den Status auch anzeigen.
ms.openlocfilehash: a38b723db6f5bafe246e774972ca89c65bc9c846
ms.sourcegitcommit: 29f937b7430c708c9dbec23bdc4089e86c37c225
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2019
ms.locfileid: "31001568"
---
# <a name="view-directory-synchronization-status-in-office-365"></a>Anzeigen des Status der Verzeichnissynchronisierung in Office 365

Wenn Sie Ihr lokales Active Directory mit Azure AD integriert haben, indem Sie Ihre lokale Umgebung mit Office 365 synchronisieren, können Sie auch den Status Ihrer Synchronisierung überprüfen.
  
## <a name="view-directory-synchronization-status"></a>Anzeigen des Verzeichnis Synchronisierungsstatus

- Melden Sie sich beim [Microsoft 365 Admin Center](https://admin.microsoft.com) an, **** und wählen Sie auf der Startseite dirsyncstatus aus.
- Alternativ können Sie zu **aktiven**Benutzern für **Benutzer** \> wechseln und auf der Seite **aktive Benutzer** **Weitere** \> **Verzeichnissynchronisierung**auswählen. Wählen Sie im Bereich **Verzeichnissynchronisierung** die Option **zu Dirsync-Verwaltung wechseln**aus.

## <a name="information-on-the-manage-directory-synchronization-page"></a>Informationen auf der Seite "Verzeichnissynchronisierung verwalten"

In der folgenden Tabelle sind die Features aufgeführt, auf die Sie auf der Seite Informationen erhalten.
  
Wenn ein Problem mit der Verzeichnissynchronisierung auftritt, werden die Fehler auch auf dieser Seite aufgeführt. Weitere Informationen zu unterschiedlichen Fehlern, die auftreten können, finden Sie unter [Identifizieren von Verzeichnis Synchronisierungsfehlern in Office 365](identify-directory-synchronization-errors.md).
  
|**Element**|**Zweck**|
|:-----|:-----|
|**Domänen überprüft** | Die Anzahl der Domänen in Ihrem Office 365-Mandanten, die Sie überprüft haben. |
|**Domänen wurden nicht überprüft** | Domänen, die Sie hinzugefügt, jedoch nicht überprüft haben. |
|**Verzeichnissynchronisierung aktiviert** |True oder false. Gibt an, ob die Verzeichnissynchronisierung aktiviert ist. |
|**Neueste Verzeichnissynchronisierung** | Zeitpunkt, zu dem die Verzeichnissynchronisierung zuletzt ausgeführt wurde. Zeigt eine Warnung und einen Link zu einem Problembehandlungstool an, wenn die letzte Synchronisierung mehr als drei Tage zurückliegt. |
|**Kennwortsynchronisierung aktiviert** | True oder false. Gibt an, ob eine Kennworthash Synchronisierung zwischen unserem lokalen und Ihrem Office 365-Mandanten statt. |
|**Letzte Kennwortsynchronisierung** | Zeitpunkt der letzten Kennworthash Synchronisierung. Zeigt eine Warnung und einen Link zu einem Problembehandlungstool an, wenn die letzte Synchronisierung mehr als drei Tage zurückliegt. |
|**Version des Verzeichnis Synchronisierungs Clients** | Enthält einen Download Link, wenn eine neue Version von Azure AD Connect veröffentlicht wurde. |
|**IDFix-Tool** | Download Link zu [IDFix](install-and-run-idfix.md), ein Tool, mit dem Sie lokale Active Directory-Dateien überprüfen können. |
|**Verzeichnissynchronisierungsdienst Konto** | Zeigt den Namen des Office 365-Verzeichnissynchronisierungsdienst Kontos an. |