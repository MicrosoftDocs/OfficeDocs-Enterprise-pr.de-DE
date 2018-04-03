---
title: Hinzufügen oder Entfernen einer Geo-Administrators
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Informationen Sie zum Hinzufügen oder Entfernen von Geo-Administrator in OneDrive for Business Multi-Geo.
ms.openlocfilehash: 0007f1ac3c73fa7a2ada562f8da65215f80744ca
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/03/2018
---
# <a name="add-or-remove-a-geo-administrator-in-onedrive-for-busniess-multi-geo"></a>Hinzufügen oder Entfernen von ein Administrator Geo in OneDrive für Busniess Multi-Geo

Sie können verschiedene Administratoren für jeden Standort Geo konfigurieren, die Ihnen in Ihrem Mandanten. Diese Administratoren haben Zugriff auf die SharePoint Online und OneDrive-Einstellungen, die an ihre Geo-Position spezifisch sind.

Einige Dienste - wie der Laufzeitspeicher - werden vom zentralen Speicherort verwaltet und auf Satelliten Speicherorte repliziert. Der Administrator Geo für den zentralen Standort hat Zugriff auf diese, während Geo-Admins für Satelliten Speicherorte nicht.

Globale Administratoren und SharePoint Online-Administratoren weiterhin an allen Speicherorten von Geo auf Einstellungen zugreifen.

## <a name="configuring-geo-administrators"></a>Konfigurieren von Geo-Administratoren

Konfigurieren von Geo-Admins ist SharePoint Online-PowerShell-Modul erforderlich.

Verwenden Sie die [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) für die Verbindung der Verwaltungskonsole des Speicherorts Geo, wo Sie den Geo-Administrator hinzufügen möchten (Z. B. Connect-SPOServicehttps://ContosoEUR-admin.sharepoint.com.)

Führen Sie zum Hinzufügen eines Benutzers als eine Geo-admin`Add-SPOGeoAdministrator -UserPrincipalName <UPN>`

Führen Sie zum Anzeigen der vorhandenen Geo-Admins eines Standorts`Get-SPOGeoAdministrators`

Führen Sie zum Entfernen eines Benutzers als eine Geo Admin eines Standorts`Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`

## <a name="see-also"></a>Siehe auch

[Hinzufügen von SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[Get-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[Remove-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)