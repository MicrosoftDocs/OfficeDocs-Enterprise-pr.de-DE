---
title: Hinzufügen oder Entfernen eines Geo-Administrators
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
description: So fügen Sie eine Geo-Administrator in Office 365 Multi-Geo hinzu oder entfernen ihn.
ms.openlocfilehash: 54850252d133e3e26b02cabe3ead0900287e832c
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490911"
---
# <a name="add-or-remove-a-geo-administrator-in-office-365-multi-geo"></a>Fügen Sie einen Geo-Administrator in Office 365 Multi-Geo hinzu oder entfernen Sie ihn.

Sie können für jeden geographischen Standort in Ihrem Mandanten einen eigenen Administrator festlegen. Dieser Administrator hat Zugriff auf SharePoint Online- und OneDrive-Einstellungen, die für seinen geographischen Standort gelten.

Einige Dienste – wie Terminologiespeicher – werden an einem zentralen Standort verwaltet und an Satellitenstandorten repliziert. Der Geo-Administrator des zentralen Standorts hat Zugriff auf diese, was für Administratoren von Satellitenstandorten nicht gilt.

Globale Administratoren und SharePoint-Onlineadministratoren haben weiterhin Zugriff auf Einstellungen am zentralen Standort und allen Satellitenstandorten.

## <a name="configuring-geo-administrators"></a>Konfigurieren von Geo-Administratoren

Für das Konfigurieren von Geo-Administratoren ist das SharePoint Online-PowerShell-Modul erforderlich.

Verwenden Sie [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService), um eine Verbindung zum Administrationscenter des geographischen Standorts herzustellen, an dem Sie den Geo-Administrator hinzufügen möchten (zum Beispiel Connect-SPOService https://ContosoEUR-admin.sharepoint.com.))

Führen Sie `Get-SPOGeoAdministrator` aus, um die vorhandenen Geo-Administratoren eines Standorts anzuzeigen.

### <a name="adding-a-user-as-a-geo-admin"></a>Einen Benutzer als Geo-Administrator hinzufügen

Führen Sie `Add-SPOGeoAdministrator -UserPrincipalName <UPN>` aus, um einen Benutzer als Geo-Administrator hinzuzufügen.

Führen Sie `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>` aus, um einen Benutzer als Geo-Administrator zu entfernen

### <a name="adding-a-group-as-a-geo-admin"></a>Eine Gruppe als Geo-Administrator hinzufügen

Sie können eine Sicherheitsgruppe oder eine E-Mail-aktivierte Sicherheitsgruppeals Geo-Administrator hinzufügen. (Verteilergruppen und Office 365-Gruppen werden nicht unterstützt.)

Führen Sie `Add-SPOGeoAdministrator -GroupAlias <alias>` aus, um eine Gruppe als Geo-Administrator hinzuzufügen.

Führen Sie `Remove-SPOGeoAdministrator -GroupAlias <alias>` aus, um eine Gruppe als Geo-Administrator zu entfernen.

Beachten Sie, dass nicht alle Sicherheitsgruppen einen Gruppenalias besitzen. Wenn Sie eine Sicherheitsgruppe hinzufügen möchten, die keinen Alias besitzt, führen Sie [Get-MsolGroup](https://docs.microsoft.com/de-DE/powershell/module/msonline/get-msolgroup) aus, um eine Liste der Gruppen anzurufen. Suchen Sie nach der ObjectID Ihrer Sicherheitsgruppe Sie dann Folgendes aus:

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

Führen Sie `Remove-SPOGeoAdministrator -ObjectID <ObjectID>` aus, um eine Gruppe anhand der ObjectID zu entfernen.

## <a name="see-also"></a>Siehe auch

[Add-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[Get-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[Remove-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)

[Legen Sie einen Alias ("MailNickName") für eine Sicherheitsgruppe fest](https://docs.microsoft.com/de-DE/powershell/module/azuread/set-azureadgroup)