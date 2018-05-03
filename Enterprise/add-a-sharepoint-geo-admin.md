---
title: Hinzufügen oder Entfernen einer Geo-Administrators
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Informationen Sie zum Hinzufügen oder Entfernen von Geo-Administrator in OneDrive for Business Multi-Geo.
ms.openlocfilehash: b88467cf2f33ec3a3a8bf6c2d6927e69e9f7af65
ms.sourcegitcommit: a4322cac992ce64b92f0335bf005a7420195d9be
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="add-or-remove-a-geo-administrator-in-onedrive-for-busniess-multi-geo"></a>Hinzufügen oder Entfernen von ein Administrator Geo in OneDrive für Busniess Multi-Geo

Sie können verschiedene Administratoren für jeden Standort Geo konfigurieren, die Ihnen in Ihrem Mandanten. Diese Administratoren haben Zugriff auf die SharePoint Online und OneDrive-Einstellungen, die an ihre Geo-Position spezifisch sind.

Einige Dienste - wie der Laufzeitspeicher - werden vom zentralen Speicherort verwaltet und auf Satelliten Speicherorte repliziert. Der Administrator Geo für den zentralen Standort hat Zugriff auf diese, während Geo-Admins für Satelliten Speicherorte nicht.

Globale Administratoren und SharePoint Online-Administratoren weiterhin an allen Speicherorten von Geo auf Einstellungen zugreifen.

## <a name="configuring-geo-administrators"></a>Konfigurieren von Geo-Administratoren

Konfigurieren von Geo-Admins ist SharePoint Online-PowerShell-Modul erforderlich.

Verwenden Sie die [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) für die Verbindung der Verwaltungskonsole des Speicherorts Geo, wo Sie den Geo-Administrator hinzufügen möchten (Z. B. Connect-SPOServicehttps://ContosoEUR-admin.sharepoint.com.)

Führen Sie zum Anzeigen der vorhandenen Geo-Admins eines Standorts`Get-SPOGeoAdministrator`

### <a name="adding-a-user-as-a-geo-admin"></a>Hinzufügen eines Benutzers als ein Geo-Administrator

Führen Sie zum Hinzufügen eines Benutzers als eine Geo-admin`Add-SPOGeoAdministrator -UserPrincipalName <UPN>`

Führen Sie zum Entfernen eines Benutzers als eine Geo Admin eines Standorts`Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`

### <a name="adding-a-group-as-a-geo-admin"></a>Hinzufügen einer Gruppe als eine Geo-admin

Sie können eine Sicherheitsgruppe oder eine e-Mail-aktivierte Sicherheitsgruppe als eine Geo-Portals hinzufügen. (Verteilergruppen und Office 365-Gruppen werden nicht unterstützt.)

Führen Sie zum Hinzufügen einer Gruppe als eine Geo-admin`Add-SPOGeoAdministrator -GroupAlias <alias>`

Führen Sie zum Entfernen einer Gruppe als eine Geo-admin`Remove-SPOGeoAdministrator -GroupAlias <alias>`

Beachten Sie, dass nicht alle Sicherheitsgruppen einen Gruppen-Alias verfügen. Wenn Sie eine Sicherheitsgruppe hinzu, die nicht über einen Alias, und führen Sie [Get-MsolGroup](https://docs.microsoft.com/en-us/powershell/module/msonline/get-msolgroup) zum Abrufen einer Liste von Gruppen verfügt möchten, suchen Sie nach der Sicherheitsgruppe ObjectID, und führen Sie:

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

Führen Sie zum Entfernen einer Gruppe mithilfe der ObjectID`Remove-SPOGeoAdministrator -ObjectID <ObjectID>`

### <a name="accessing-the-admin-center-for-a-specific-geo-location"></a>Zugreifen auf das Administrationscenter für einen bestimmten Geo-Speicherort

Zum Verwalten von Einstellungen für OneDrive für ihre Geo-Speicherort müssen Administratoren die OneDrive-Verwaltungskonsole direkt mit der folgenden URL-Format zugreifen:

https://admin.onedrive.com/?geo=<*Geo*>

Beispielsweise ist der OneDrive-Verwaltungskonsole für Kanada finden Sie unter: https://admin.onedrive.com/?geo=CAN.

## <a name="see-also"></a>Siehe auch

[Hinzufügen von SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[Get-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[Remove-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)

[Legen Sie einen Alias (MailNickName) für eine Sicherheitsgruppe](https://docs.microsoft.com/en-us/powershell/module/azuread/set-azureadgroup)