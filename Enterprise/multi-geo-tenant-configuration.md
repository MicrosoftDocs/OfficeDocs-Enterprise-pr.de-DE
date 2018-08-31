---
title: Konfiguration des Mandanten für Multi-Geo in OneDrive for Business
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
ms.collection: Strat_SP_gtc
description: Konfigurieren von Multi-Geo in OneDrive for Business.
ms.openlocfilehash: 1817eee1bb2ceefa0e2e167e327af417dd0c517d
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915250"
---
# <a name="onedrive-for-business-multi-geo-tenant-configuration"></a>Konfiguration des Mandanten für Multi-Geo in OneDrive for Business

Bevor Sie Ihren Mandanten für Multi-Geo in OneDrive for Business konfigurieren, stellen Sie sicher, dass Sie den Artikel [Planen von Multi-Geo in OneDrive for Business](plan-for-multi-geo.md). Um die Schritte in diesem Artikel auszuführen, benötigen Sie eine Liste der Standorte, die Sie aktivieren möchten, und der Testbenutzer, für die Sie diese Standorte bereitstellen möchten.

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a>Hinzufügen des Plans für Multi-Geo-Funktionen in Office 365 zu Ihrem Mandanten

Wenn Sie Multi-Geo in OneDrive for Business verwenden möchten, benötigen Sie den Plan für _Multi-Geo-Funktionen in Office 365_. Arbeiten Sie mit Ihrem Kontoteam, um diesen Plan zu Ihrem Mandanten hinzuzufügen. Ihr Kontoteam stellt den Kontakt mit dem entsprechenden Lizenzierungsexperten her und unterstützt Sie bei der Konfiguration des Mandanten.

Beachten Sie, dass der Plan für _Multi-Geo-Funktionen in Office 365_ ein Serviceplan auf Benutzerebene ist. Sie benötigen eine Lizenz für jeden Benutzer, der an einem Satellitenstandort gehostet werden soll. Sie können mit der Zeit weitere Lizenzen hinzufügen, wenn Sie Benutzer in Ihrem Satellitenstandort hinzufügen.

Nachdem Ihr Mandant mit dem Plan für _Multi-Geo-Funktionen in Office 365_ bereitgestellt wurde, wird die Registerkarte **Geografische Standorte** im [OneDrive Admin Center](https://admin.onedrive.com) angezeigt.

## <a name="set-the-allowed-data-locations-adl-to-your-tenant"></a>Festlegen der zugelassenen Datenspeicherorte für Ihren Mandanten

Sie müssen den zugelassenen Speicherort für SharePoint für jeden geografischen Standort festlegen, für den Sie OneDrive for Business verwenden möchten. In der folgenden Tabelle werden die verfügbaren geografischen Standorte aufgeführt:

<table>
<thead>
<tr class="header">
<th align="left"><strong>Standort</strong></th>
<th align="left"><strong>Code</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Asien-Pazifik</td>
<td align="left">APC</td>
</tr>
<tr class="even">
<td align="left">Australien</td>
<td align="left">AUS</td>
</tr>
<tr class="even">
<td align="left">Kanada</td>
<td align="left">CAN</td>
</tr>
<tr class="even">
<td align="left">Europa/Naher Osten/Afrika</td>
<td align="left">EUR</td>
</tr>
<tr class="even">
<td align="left">Frankreich</td>
<td align="left">FRA</td>
</tr>
<tr class="odd">
<td align="left">Japan</td>
<td align="left">JPN</td>
</tr>
<tr class="even">
<td align="left">Korea</td>
<td align="left">KOR</td>
</tr>
<tr class="odd">
<td align="left">Nordamerika</td>
<td align="left">NAM</td>
</tr>
<tr class="odd">
<td align="left">Vereinigtes Königreich</td>
<td align="left">GBR</td>
</tr>
</tbody>
</table>

So fügen Sie einen Satellitenstandort hinzu

1. Öffnen Sie das [OneDrive Admin Center](https://admin.onedrive.com).

2. Navigieren Sie zu der Registerkarte **Geografische Standorte**.

3. Klicken Sie auf **Ort hinzufügen**.

4. Wählen Sie den Standort aus, den Sie hinzufügen möchten, und klicken Sie auf **Weiter**.

5. Geben Sie die Domäne ein, die Sie mit dem geografischen Standort verwenden möchten, und klicken Sie dann auf **Hinzufügen**.

6. Klicken Sie auf **Schließen**.

Die Bereitstellung kann je nach Größe des Mandanten bis zu 72 Stunden dauern. Sobald die Bereitstellung für einen Satellitenstandort abgeschlossen ist, erhalten Sie eine E-Mail-Bestätigung. Wenn der neue geografische Standort blau auf der Karte auf der Registerkarte **Geografische Standorte** im OneDrive Admin Center angezeigt wird, können Sie mit dem Festlegen der bevorzugten Datenspeicherorte für die Benutzer für diesen geografischen Standort fortfahren. 

> [!IMPORTANT]
> Ihr neuer Satellitenstandort wird mit Standardeinstellungen eingerichtet. Sie können diesen geografischen Standort entsprechend den lokalen Complianceanforderungen konfigurieren.

## <a name="setting-users-preferred-data-location"></a>Festlegen der bevorzugen Datenspeicherorte für Benutzer
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

Nachdem Sie die notwendigen Datenspeicherorte aktiviert haben, können Sie Ihre Benutzerkonten für die Verwendung des entsprechenden Datenspeicherorts aktualisieren. Es wird empfohlen, auch dann einen bevorzugten Datenspeicherort für jeden Benutzer festzulegen, wenn dieser Benutzer am standardmäßigen Datenspeicherort verbleibt.

> [!TIP]
> Es wird empfohlen, die Prüfungen mit einem Testbenutzer oder einer kleinen Gruppe von Benutzern durchzuführen, bevor die Multi-Geo-Funktionen für Ihre Organisation bereitgestellt werden.

In AAD gibt es zwei Typen von Benutzerobjekten: Nur-Cloud-Benutzer und synchronisierte Benutzer. Befolgen Sie die entsprechenden Anweisungen für jeden Benutzertyp.

### <a name="synchronize-users-preferred-data-location-using-ad-connect"></a>Synchronisieren der bevorzugten Datenspeicherorte für Benutzer mithilfe von AD Connect 

Wenn für Benutzer in Ihrem Unternehmen eine Synchronisierung zwischen dem lokalen Active Directory (AD)-System und Azure Active Directory (AAD) durchgeführt wird, muss PreferredDataLocation in AD aufgefüllt werden und mit AAD synchronisiert werden. Befolgen Sie den Prozess unter [Azure AD Connect-Synchronisierung: Ändern der Standardkonfiguration](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration), um die Synchronisierung der bevorzugten Datenspeicherorte zwischen lokalem AD und AAD zu konfigurieren.

Es wird empfohlen, die Einstellung des bevorzugten Datenspeicherorts des Benutzers im Rahmen des Standardworkflows für das Erstellen von Benutzern hinzuzufügen.

> [!IMPORTANT]
> Warten Sie bei neuen Benutzern ohne OneDrive mindestens 24 Stunden nach der Synchronisierung der bevorzugten Datenspeicherorte für Benutzer mit AAD, damit die Änderungen in Kraft treten, bevor sich die Benutzer bei OneDrive for Business anmelden. (Durch Festlegen des bevorzugten Datenspeicherorts vor der Anmeldung des Benutzers für die Bereitstellung für OneDrive for Business wird sichergestellt, dass die neue OneDrive-Umgebung an dem richtigen Ort bereitgestellt wird.)

### <a name="setting-preferred-data-location-for-cloud-only-users"></a>Festlegen des bevorzugten Datenspeicherorts für Nur-Cloud-Benutzer 

Wenn für Benutzer in Ihrem Unternehmen keine Synchronisierung zwischen dem lokalen Active Directory (AD)-System und Azure Active Directory (AAD) erfolgt, was bedeutet, dass sie in Office 365 oder AAD erstellt werden, müssen die bevorzugten Datenspeicherorte mithilfe von AAD PowerShell festgelegt werden.

Für die Vorgehensweisen in diesem Abschnitt ist das [Microsoft Azure Active Directory-Modul für Windows PowerShell](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0) erforderlich. Wenn AAD PowerShell bereits installiert ist, stellen Sie sicher, dass Sie ein Update auf die neueste Version durchführen.

1.  Öffnen Sie das Microsoft Azure Active Directory-Modul für Windows PowerShell.

2.  Führen Sie `Connect-MsolService` aus, und geben Sie die Anmeldeinformationen des globalen Administrators für Ihren Mandanten ein.

3.  Verwenden Sie das [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser)-Cmdlet zum Festlegen des bevorzugten Datenspeicherorts für jeden Benutzer. Zum Beispiel:

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    Sie können mithilfe des Get-MsolUser-Cmdlets prüfen, ob der bevorzugte Datenspeicherort korrekt festgelegt wurde. Zum Beispiel:

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![](media/multi-geo-tenant-configuration-image3.png)

Es wird empfohlen, die Einstellung des bevorzugten Datenspeicherorts des Benutzers im Rahmen des Standardworkflows für das Erstellen von Benutzern hinzuzufügen.

> [!IMPORTANT]
> Warten Sie bei neuen Benutzern ohne OneDrive mindestens 24 Stunden nach Festlegung der bevorzugten Datenspeicherorte für Benutzer, damit die Änderungen in Kraft treten, bevor sich die Benutzer bei SharePoint OneDrive anmelden. (Durch Festlegen des bevorzugten Datenspeicherorts vor der Anmeldung des Benutzers für die Bereitstellung für OneDrive for Business wird sichergestellt, dass die neue OneDrive-Umgebung an dem richtigen Ort bereitgestellt wird.)

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a>Bereitstellung von OneDrive und Auswirkungen auf den bevorzugten Datenspeicherort

Wenn der Benutzer bereits eine OneDrive-Website in dem Mandanten erstellt hat, wird beim Festlegen des bevorzugten Datenspeicherorts die vorhandene OneDrive-Bereitstellung nicht automatisch verschoben. Informationen zum Verschieben der OneDrive-Umgebung eines Benutzers finden Sie unter [Verschieben von OneDrive for Business](move-onedrive-between-geo-locations.md). Befolgen Sie die Anweisungen zum Verschieben von OneDrive zwischen geografischen Standorten.

Wenn der Benutzer über keine OneDrive-Website innerhalb des Mandanten verfügt, wird OneDrive automatisch entsprechend des festgelegten Werts für den bevorzugten Datenspeicherort bereitgestellt, wobei davon ausgegangen wird, dass der bevorzugte Datenspeicherort für den Benutzer mit den zugelassenen Datenspeicherorten des Unternehmens übereinstimmt.

## <a name="configuring-multi-geo-search"></a>Konfigurieren der Multi-Geo-Suche

Der Multi-Geo-Mandant verfügt über aggregierte Suchfunktionen, mit denen eine Suchabfrage Ergebnisse von allen Orten innerhalb des Mandanten zurückgibt.

Standardmäßig geben Suchen von diesen Einstiegspunkten aggregierte Ergebnisse zurück, auch wenn sich jeder Suchindex an dem jeweiligen relevanten geografischen Standort befindet:

- OneDrive for Business

- Delve

- SharePoint-Homepage

- Suchcenter

Darüber hinaus können Multi-Geo-Suchfunktionen für Ihre benutzerdefinierte Suchanwendung konfiguriert werden, die die SharePoint-Suche-API verwendet.

Anweisungen, einschließlich Einschränkungen und Unterschiede, finden Sie unter [Konfigurieren der Suche für Multi-Geo in OneDrive for Business](configure-search-for-multi-geo.md).

## <a name="validating-the-onedrive-for-business-multi-geo-configuration"></a>Prüfen der Konfiguration von Multi-Geo in OneDrive for Business

Im Folgenden finden Sie einige grundlegende Anwendungsfälle, in denen eine Überprüfung vor dem Rollout von Multi-Geo in OneDrive for Business im Unternehmen möglicherweise sinnvoll ist. Nach Abschluss dieser Tests und zusätzlicher Anwendungsfälle, die für Ihr Unternehmen relevant sind, möchten Sie der ursprünglichen Pilotgruppe möglicherweise weitere Benutzer hinzufügen.

**OneDrive for Business**

Wählen Sie im Office 365-App-Startfeld OneDrive aus, und stellen Sie sicher, dass Sie automatisch an den entsprechenden geografischen Standort für den Benutzer, basierend auf dem bevorzugten Datenspeicherort, weitergeleitet werden. OneDrive for Business sollte jetzt an diesem Ort bereitgestellt werden. Versuchen Sie nach der Bereitstellung einige Dokumente hoch- und herunterzuladen.

**Mobile OneDrive-App**

Melden Sie sich bei Ihrer mobilen OneDrive-App mit den Anmeldeinformationen Ihres Testkontos an. Stellen Sie sicher, dass Ihre OneDrive for Business-Dateien angezeigt werden und mit denjenigen auf Ihrem Mobilgerät interagieren können.

**OneDrive-Synchronisierungsclient**

Vergewissern Sie sich, dass der OneDrive-Synchronisierungsclient den geografischen Standort für OneDrive for Business nach Anmeldung automatisch erkennt. Wenn Sie den Synchronisierungsclient herunterladen müssen, klicken Sie in der OneDrive-Bibliothek auf **Synchronisieren**.

**Office-Anwendungen**

Vergewissern Sie sich, dass Sie auf OneDrive for Business zugreifen können, indem Sie sich von einer Office-Anwendung wie Word aus anmelden. Öffnen Sie die Office-Anwendung, und wählen Sie „OneDrive – <TenantName>„. Office erkennt Ihren OneDrive-Ort und zeigt die Dateien, die Sie öffnen können.

**Freigabe**

Testen Sie die Freigabe von OneDrive-Dateien. Vergewissern Sie sich, dass die Personenauswahl alle SharePoint-Onlinebenutzer unabhängig vom geografischen Standort anzeigt.
