---
title: Microsoft 365 Multi-Geo-Mandantenkonfiguration
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection: Strat_SP_gtc
f1.keywords:
- NOCSH
ms.custom: ''
localization_priority: Priority
description: Erfahren Sie, wie Sie Microsoft 365 Multi-Geo konfigurieren.
ms.openlocfilehash: 928033dcbec0ad0b52f24bd0bec4dd6b9f9331bc
ms.sourcegitcommit: c6a2256f746f55d1cfb739649ffeee1f2f2152aa
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2020
ms.locfileid: "45052568"
---
# <a name="microsoft-365-multi-geo-tenant-configuration"></a>Microsoft 365 Multi-Geo-Mandantenkonfiguration

Bevor Sie Ihren Mandanten für Microsoft 365 Multi-Geo konfigurieren, stellen Sie sicher, dass Sie [Plan für Microsoft 365 Multi-Geo](plan-for-multi-geo.md) gelesen haben. Um die Schritte in diesem Artikel auszuführen, benötigen Sie eine Liste der geografischen Standorte, die Sie als Satellitenstandorte aktivieren möchten, und der Testbenutzer, die Sie für diese Standorte bereitstellen möchten.

## <a name="add-the-multi-geo-capabilities-in-your-microsoft-365-plan-to-your-tenant"></a>Hinzufügen der Multi-Geo-Funktionen in Ihrem Microsoft 365-Plan zu Ihrem Mandanten

Wenn Sie Microsoft 365 Multi-Geo verwenden möchten, benötigen Sie den Plan _Multi-Geo-Funktionen in Microsoft 365_. Arbeiten Sie mit Ihrem Kontoteam, um diesen Plan zu Ihrem Mandanten hinzuzufügen. Ihr Kontoteam setzt Sie mit dem entsprechenden Lizenzierungsexperten in Verbindung und konfiguriert Ihren Mandanten für Sie.

Note that the _Multi-Geo Capabilities in Microsoft 365_ plan are a user-level service plan. You need a license for each user that you want to host in a satellite location. You can add more licenses over time as you add users in satellite locations.

Nachdem der Plan _Multi-Geo-Funktionen in Microsoft 365_ Ihrem Mandanten bereitgestellt wurde, steht die Registerkarte **Geografische Standorte** im Admin Center von OneDrive sowie SharePoint zur Verfügung.

## <a name="add-satellite-locations-to-your-tenant"></a>Hinzufügen von Satellitenstandorten zu Ihrem Mandanten

Sie müssen für jeden geografischen Standort, an dem Sie Daten speichern möchten, einen Satellitenstandort hinzufügen. In der folgenden Tabelle werden verfügbare geografische Standorte angezeigt:

[!INCLUDE [Microsoft 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

![Screenshot der Seite mit geografischen Orten im SharePoint-Admin Center](media/sharepoint-multi-geo-admin-center.png)

So fügen Sie einen Satellitenstandort hinzu

1. Öffnen Sie das SharePoint Admin Center.

2. Navigieren Sie zu der Registerkarte **Geografische Standorte**.

3. Klicken Sie auf **Ort hinzufügen**.

4. Wählen Sie den Standort aus, den Sie hinzufügen möchten, und klicken Sie auf **Weiter**.

5. Geben Sie die Domäne ein, die Sie mit dem geografischen Standort verwenden möchten, und klicken Sie dann auf **Hinzufügen**.

6. Klicken Sie auf **Schließen**.

Provisioning may take from a few hours up to 72 hours, depending on the size of your tenant. Once provisioning of a satellite location has completed, you will receive an email confirmation. When the new geo location appears in blue on the map on the **Geo locations** tab in the OneDrive admin center, you can proceed to set users' preferred data location to that geo location. 

> [!IMPORTANT]
> Your new satellite location will be set up with default settings. This will allow you to configure that satellite location as appropriate for your local compliance needs.

## <a name="setting-users-preferred-data-location"></a>Festlegen des bevorzugten Datenspeicherorts für Benutzer
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

Once you enable the needed satellite locations, you can update your user accounts to use the appropriate preferred data location. We recommend that you set a preferred data location for every user, even if that user is staying in the central location.

> [!IMPORTANT]
> Wenn ein Standort, der noch nicht als Satellitenspeicherort oder zentraler Standort konfiguriert wurde, als bevorzugter Datenspeicherort eines Benutzers festgelegt wird, verwendet das System bei der Bereitstellung von OneDrive- und SharePoint-Websites sowie Gruppenpostfächern standardmäßig den zentralen Standort.

> [!TIP]
> Es wird empfohlen, die Prüfungen mit einem Testbenutzer oder einer kleinen Gruppe von Benutzern durchzuführen, bevor die Multi-Geo-Funktionen für Ihre Organisation bereitgestellt werden.

In Azure Active Directory (Azure AD) gibt es zwei Arten von Benutzerobjekten: Nur-Cloud-Benutzer und synchronisierte Benutzer. Bitte befolgen Sie die Anweisungen für die entsprechende Benutzerart.

### <a name="synchronize-users-preferred-data-location-using-azure-ad-connect"></a>Synchronisieren der bevorzugten Datenspeicherorte für Benutzer mithilfe von Azure AD Connect 

Wenn die Benutzer in Ihrem Unternehmen von einem lokalen Active Directory-System mit Azure AD synchronisiert werden, muss ihre "PreferredDataLocation" in AD aufgefüllt und mit Azure AD synchronisiert werden.

Folgen Sie dem Prozess in [Azure Active Directory Connect-Synchronisierung: Konfigurieren des bevorzugten Datenstandorts für Microsoft 365-Ressourcen](/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation), um die Synchronisierung des bevorzugten Datenstandorts von Ihren lokalen Active Directory Domain Services (AD DS) mit Azure AD zu konfigurieren.

Wir empfehlen, die Einstellung des bevorzugten Datenspeicherorts von Benutzern im Rahmen des Standardworkflows für das Erstellen von Benutzern vorzunehmen.

> [!IMPORTANT]
> Im Falle von Benutzern ohne bereitgestellte OneDrive-Umgebung sollten Sie nach der Synchronisierung des bevorzugten Datenspeicherortes mit Azure AD mindestens 24 Stunden warten, damit die Änderungen in Kraft treten, bevor sich die Benutzer bei OneDrive for Business anmelden. (Durch Festlegen des bevorzugten Datenspeicherorts vor der Anmeldung des Benutzers für die Bereitstellung von OneDrive for Business wird sichergestellt, dass die neue OneDrive-Umgebung an dem richtigen Ort bereitgestellt wird.)

### <a name="setting-preferred-data-location-for-cloud-only-users"></a>Festlegen des bevorzugten Datenspeicherorts für Nur-Cloud-Benutzer 

Wenn die Benutzer Ihres Unternehmens nicht über ein lokales Active Directory-System mit Azure AD synchronisiert werden (d. h. wenn sie in Microsoft 365 oder Azure AD erstellt werden), muss der PDL über das Microsoft Azure Active Directory-Modul für Windows PowerShell festgelegt verwenden.

Die Verfahren in diesem Abschnitt setzen das [Microsoft Azure Active Directory-Modul für Windows PowerShell](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0) voraus. Wenn dieses Modul bereits installiert ist, stellen Sie sicher, dass Sie die neueste Version verwenden.

1.  [Stellen Sie eine Verbindung her, und melden Sie sich mit den Anmeldeinformationen eines globaler Administrators für Ihren Mandanten an](/powershell/connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

2.  Use the [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser) cmdlet to set the preferred data location for each of your users. For example:

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    You can check to confirm that the preferred data location was updated properly by using the Get-MsolUser cmdlet. For example:

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![Screenshot des PowerShell-Fensters mit Set-MsolUser](media/multi-geo-tenant-configuration-image3.png)

Wir empfehlen, die Einstellung des bevorzugten Datenspeicherorts von Benutzern im Rahmen des Standardworkflows für das Erstellen von Benutzern vorzunehmen.

> [!IMPORTANT]
> Im Falle von neuen Benutzern ohne bereitgestellte OneDrive-Umgebung sollten Sie nach der Einstellung des bevorzugten Datenspeicherortes mindestens 24 Stunden warten, damit die Änderungen in Kraft treten, bevor sich die Benutzer bei OneDrive for Business anmelden. (Durch Festlegen des bevorzugten Datenspeicherorts vor der Anmeldung des Benutzers für die Bereitstellung von OneDrive for Business wird sichergestellt, dass die neue OneDrive-Umgebung an dem richtigen Ort bereitgestellt wird.)

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a>Bereitstellung von OneDrive und Auswirkungen auf den bevorzugten Datenspeicherort

Wenn für einen Benutzer bereits eine OneDrive-Website im Mandanten erstellt wurde, wird beim Festlegen des bevorzugten Speicherorts die vorhandene OneDrive-Bereitstellung nicht automatisch verschoben. Informationen zum Migrieren der OneDrive-Umgebung eines Benutzers finden Sie unter [Verschieben von One Drive for Business](move-onedrive-between-geo-locations.md). Befolgen Sie die Anweisungen zum Migrieren von OneDrive zwischen geografischen Standorten. (Bitte beachten Sie, dass Exchange-Postfächer automatisch migriert werden, wenn Sie den PDL eines Benutzers festlegen.)

Wenn ein Benutzer nicht über eine OneDrive-Website innerhalb des Mandanten verfügt, wird OneDrive in Übereinstimmung mit den jeweiligen PDL-Einstellungen bereitgestellt, sofern der PDL des Benutzers einem der Satellitenstandorte des Unternehmens entspricht.

## <a name="configuring-multi-geo-search"></a>Konfigurieren der Multi-Geo-Suche

Der Multi-Geo-Mandant verfügt über aggregierte Suchfunktionen, mit denen eine Suchabfrage Ergebnisse von allen Orten innerhalb des Mandanten zurückgibt.

Standardmäßig geben Suchen von diesen Einstiegspunkten aggregierte Ergebnisse zurück, auch wenn sich jeder Suchindex an dem jeweiligen relevanten geografischen Standort befindet:

- OneDrive for Business

- Delve

- SharePoint-Homepage

- Suchcenter

Darüber hinaus können Multi-Geo-Suchfunktionen für Ihre benutzerdefinierte Suchanwendung konfiguriert werden, die die SharePoint-Suche-API verwendet.

Anweisungen, einschließlich Einschränkungen und Unterschiede, finden Sie unter [Konfigurieren der Suche für Multi-Geo in OneDrive for Business](configure-search-for-multi-geo.md).

## <a name="validating-the-microsoft-365-multi-geo-configuration"></a>Überprüfen der Microsoft 365 Multi-Geo-Konfiguration

Im Folgenden finden Sie einige grundlegende Anwendungsfälle, in denen eine Überprüfung vor dem Rollout von Microsoft 365 Multi-Geo im Unternehmen möglicherweise sinnvoll ist. Nach Abschluss dieser Tests und zusätzlicher Anwendungsfälle, die für Ihr Unternehmen relevant sind, können Sie der ursprünglichen Pilotgruppe bei Bedarf weitere Benutzer hinzufügen.

**OneDrive for Business**

Wählen Sie OneDrive im Microsoft 365-Startprogramm aus und bestätigen Sie, dass Sie automatisch an den entsprechenden geografischen Standort des Benutzers (gemäß dessen PDL) weitergeleitet werden. OneDrive for Business sollte jetzt an diesem Standort bereitgestellt werden. Versuchen Sie nach der Bereitstellung, einige Dokumente hoch- und herunterzuladen.

**Mobile OneDrive-App**

Melden Sie sich bei Ihrer mobilen OneDrive-App mit den Anmeldeinformationen Ihres Testkontos an. Stellen Sie sicher, dass Ihre OneDrive for Business-Dateien angezeigt werden und mit denjenigen auf Ihrem Mobilgerät interagieren können.

**OneDrive-Synchronisierungsclient**

Confirm that the OneDrive sync client automatically detects your OneDrive for Business geo location upon login. If you need to download the sync client, you can click **Sync** in the OneDrive library.

**Office-Anwendungen**

Confirm that you can access OneDrive for Business by logging in from an Office application, such as Word. Open the Office application and select "OneDrive – <TenantName>". Office will detect your OneDrive location and show you the files that you can open.

**Freigabe**

Try sharing OneDrive files. Confirm that the people picker shows you all your SharePoint online users regardless of their geo location.
