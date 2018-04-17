---
title: OneDrive for Business Multi-Geo Mandantenkonfiguration
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: Informationen Sie zum Konfigurieren von OneDrive für Unternehmen Multi-Geo.
ms.openlocfilehash: 56268acd319684ecb713e674b8accbe311d08dce
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="onedrive-for-business-multi-geo-tenant-configuration"></a>OneDrive for Business Multi-Geo Mandantenkonfiguration

Bevor Sie Ihrem Mandanten für OneDrive for Business Multi-Geo konfigurieren, sollten Sie darauf achten Sie, dass Sie [Planen von OneDrive for Business Multi-Geo](plan-for-multi-geo.md)gelesen haben. Wenn Sie die Schritte in diesem Artikel auszuführen, benötigen Sie eine Liste der Speicherorte, die Sie aktivieren möchten und den Testbenutzern, die Sie für diese Standorte bereitstellen möchten.

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a>Fügen Sie die Multi-Geo-Funktionen in Office 365-Plan Ihres Mandanten

Um OneDrive for Business Multi-Geo verwenden, benötigen Sie den _Multi-Geo-Funktionen in Office 365_ -Plan. Arbeiten Sie mit Ihrem Team Konto Ihres Mandanten diesem Plan hinzugefügt. Ihr Kundenteam wird verbinden Sie mit der entsprechenden Lizenzierung Spezialist und Abrufen von Ihrem Mandanten konfiguriert.

Beachten Sie, dass der _Multi-Geo-Funktionen in Office 365_ -Plan eine auf Benutzerebene Dienstplan ist. Sie benötigen eine Lizenz für jeden Benutzer, die Sie an einem Speicherort Satelliten hosten möchten. Sie können weitere Lizenzen über einen Zeitraum beim Hinzufügen von Benutzern in Satelliten Speicherorte hinzufügen.

Nach Ihrem Mandanten mit der _Multi-Geo-Funktionen in Office 365_ -Plan bereitgestellt wurde, wird in der [OneDrive-Verwaltungskonsole](https://admin.onedrive.com)auf der Registerkarte **Geo Speicherorte** verfügbar.

## <a name="set-the-allowed-data-locations-adl-to-your-tenant"></a>Legen Sie die zulässigen Daten Speicherorte (ADL) auf Ihres Mandanten

Sie müssen Festlegen einer Datenspeicherort zulässig für SharePoint für jeden Geo-Standort, wo OneDrive für Unternehmen verwendet werden soll. Verfügbare Geo-Standorte sind in der folgenden Tabelle aufgeführt:

<table>
<thead>
<tr class="header">
<th align="left"><strong>Speicherort</strong></th>
<th align="left"><strong>Code</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Nordamerika</td>
<td align="left">NAME</td>
</tr>
<tr class="even">
<td align="left">Europa / Mittlerer Osten / Afrika</td>
<td align="left">EUR</td>
</tr>
<tr class="odd">
<td align="left">Asien-Pazifik</td>
<td align="left">APC</td>
</tr>
<tr class="even">
<td align="left">Australien</td>
<td align="left">AUS</td>
</tr>
<tr class="odd">
<td align="left">Japan</td>
<td align="left">JAPANISCHE</td>
</tr>
<tr class="even">
<td align="left">Kanada</td>
<td align="left">KÖNNEN</td>
</tr>
<tr class="odd">
<td align="left">Vereinigtes Königreich</td>
<td align="left">GBR</td>
</tr>
<tr class="even">
<td align="left">Korea</td>
<td align="left">KOREANISCHE</td>
</tr>
</tbody>
</table>

So fügen Sie einen Satelliten Geo-Speicherort hinzu

1. Öffnen Sie die [OneDrive-Verwaltungskonsole](https://admin.onedrive.com).

2. Navigieren Sie zur Registerkarte **Geo-Speicherorte** .

3. Klicken Sie auf **Speicherort hinzufügen**.

4. Wählen Sie den Speicherort an, dem Sie hinzufügen möchten, und klicken Sie dann auf **Weiter**.

5. Geben Sie die Domäne, die Sie mit dem Speicherort Geo verwenden möchten, und klicken Sie dann auf **Hinzufügen**.

6. Klicken Sie auf **Schließen**.

Bereitstellung kann von ein paar Stunden bis 72 Stunden, je nach der Größe Ihres Mandanten dauern, bis. Nach der Bereitstellung von einem Speicherort Satelliten abgeschlossen wurde, erhalten Sie eine e-Mail-Bestätigung. Wenn am neuen Speicherort Geo Blau auf der Karte auf der Registerkarte **Geo Speicherorte** in der OneDrive-Verwaltungskonsole angezeigt wird, können Sie fortfahren, bevorzugte Datenspeicherort Benutzer auf diesen Geo-Speicherort festgelegt. 

> [!IMPORTANT]
> Ihre neuen Satelliten Geo Speicherort wird mit den Standardeinstellungen festgelegt. Dadurch können Sie diesen Speicherort Geo entsprechend Ihren lokalen Compliance-Anforderungen konfigurieren.

## <a name="setting-users-preferred-data-location"></a>Festlegen der bevorzugten Datenspeicherort Users
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

Nachdem Sie die benötigten Datenspeicherorte aktivieren, können Sie Ihre Benutzerkonten den entsprechenden Daten Speicherort aktualisieren. Es wird empfohlen, dass Sie für jeden Benutzer eine bevorzugte Datenspeicherort festlegen, selbst wenn der Benutzer im Standardspeicherort Daten Kontaktpflege ist.

> [!TIP]
> Es wird empfohlen, dass Sie Überprüfungen mit einem Testbenutzers oder eine kleine Gruppe von Benutzern beginnen, vor der Einführung der zahlreichen organisationsinterne Multi-Geo-Funktionen.

In AAD es gibt zwei Arten von Benutzerobjekten: cloud nur und synchronisierten Benutzer. Führen Sie die entsprechenden Anweisungen für den Typ des Benutzers an.

### <a name="synchronize-users-preferred-data-location-using-ad-connect"></a>Synchronisieren des Benutzers bevorzugte Datenspeicherort mit Active Directory verbinden 

Benutzer Ihres Unternehmens Azure Active Directory (AAD) von einem lokalen Active Directory (AD) System synchronisiert sind, muss ihre PreferredDataLocation in AD gefüllt und mit AAD synchronisiert. Befolgen Sie das Verfahren in [Verbinden von Azure AD-Synchronisierung: Führen Sie eine Änderung der Standardkonfiguration](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration) so konfigurieren Sie bevorzugte Datenspeicherort die Synchronisierung von lokalen AD zu AAD.

Es wird empfohlen, dass Sie zählen das Festlegen der bevorzugten Daten Standort des Benutzers als Teil des standard-Benutzer Workflows erstellen.

> [!IMPORTANT]
> Warten Sie für neue Benutzer mit keine OneDrive bereitgestellt die mindestens 24 Stunden, nachdem ein Benutzer Verteilerliste mit AAD, damit die Änderungen weitergegeben wird, bevor der Benutzer zu OneDrive for Business anmeldet synchronisiert ist. (Festlegen der bevorzugten Daten sichergestellt Speicherort, bevor der Benutzer meldet sich bei ihrer OneDrive für Unternehmen bereitstellen, dass neue OneDrive des Benutzers in den richtigen Speicherort bereitgestellt wird.)

### <a name="setting-preferred-data-location-for-cloud-only-users"></a>Bevorzugte Datenspeicherort festlegen für die Cloud nur Benutzer. 

Wenn Ihr Unternehmen Benutzer nicht von einem lokalen Active Directory (AD) System Azure Active Directory (AAD) synchronisiert sind, muss was bedeutet, dass sie in Office 365 oder AAD, erstellt werden dann Verteilerliste festgelegt werden von AAD PowerShell.

In diesem Abschnitt Verfahren benötigen Sie die [Microsoft Azure Active Directory Modul für Windows PowerShell-Modul](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). Wenn Sie bereits AAD PowerShell installiert haben, stellen Sie sicher, dass Sie auf die neueste Version aktualisieren.

1.  Öffnen Sie die Microsoft Azure Active Directory-Moduls für Windows PowerShell.

2.  Führen Sie `Connect-MsolService` , und geben Sie die globalen Administratoranmeldeinformationen für Ihre Mandanten.

3.  Verwenden Sie das [Set-MsolUser](https://docs.microsoft.com/en-us/powershell/msonline/v1/set-msoluser) -Cmdlet zum Festlegen der bevorzugten Daten für jeden Ihrer Benutzer. Zum Beispiel:

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    Sie können überprüfen, um zu bestätigen, dass der Speicherort des bevorzugten Daten mit dem Cmdlet Get-MsolUser ordnungsgemäß aktualisiert wurde. Zum Beispiel:

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![](media/multi-geo-tenant-configuration_image3.png)

Es wird empfohlen, dass Sie zählen das Festlegen der bevorzugten Daten Standort des Benutzers als Teil des standard-Benutzer Workflows erstellen.

> [!IMPORTANT]
> Warten Sie für neue Benutzer mit keine OneDrive bereitgestellt mindestens 24 Stunden, nachdem ein Benutzer Verteilerliste, damit die Änderungen festgelegt ist weitergegeben wird, bevor der Benutzer zu SharePoint OneDrive anmeldet. (Festlegen der bevorzugten Daten sichergestellt Speicherort, bevor der Benutzer meldet sich bei ihrer OneDrive für Unternehmen bereitstellen, dass neue OneDrive des Benutzers in den richtigen Speicherort bereitgestellt wird.)

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a>Bereitstellung von OneDrive und die Auswirkungen der Verteilerliste

Wenn der Benutzer bereits eine OneDrive-Website in den Mandanten erstellt hat, wird die Verteilerliste festlegen nicht automatisch ihre vorhandenen OneDrive verschoben. Zum Verschieben eines Benutzers OneDrive finden Sie unter [OneDrive for Business Geo verschieben](move-onedrive-between-geo-locations.md) , führen Sie die Anweisungen in OneDrive Verschieben zwischen Geo-Speicherorte.

Wenn der Benutzer keine OneDrive-Website in den Mandanten, wird OneDrive bereitgestellt werden für diese in Übereinstimmung mit deren Verteilerliste Wert ab, unter der Voraussetzung, dass der persönlichen Verteilerliste für den Benutzer eine der zulässigen Datenspeicherorte (ADLs) des Unternehmens übereinstimmt.

## <a name="configuring-multi-geo-search"></a>Konfigurieren der Multi-Geo-Suche

Ihres Mandanten Multi-Geo müssen aggregierte Suchfunktionen ermöglichen eine Suchabfrage Ergebnisse zurückgegeben werden, unabhängig vom Standort in den Mandanten.

Standardmäßig werden sucht über diese Einstiegspunkte aggregierte Ergebnisse zurückgegeben, obwohl Sie jede Suchindex in den entsprechenden Geo Speicherort befindet:

- OneDrive für Unternehmen

- Delve

- SharePoint – Startseite

- Suchcenter

Darüber hinaus können Multi-Geo-Suchfunktionen für Ihre benutzerdefinierte suchanwendungen konfiguriert werden, die die SharePoint-Suche API verwenden.

Überprüfen Sie [Konfigurieren der Suche für OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) Anweisungen, einschließlich aller Einschränkungen und Unterschiede.

## <a name="validating-the-onedrive-for-business-multi-geo-configuration"></a>Überprüfen die OneDrive for Business Multi-Geo-Konfiguration

Im folgenden sind einige grundlegende Verwendungsszenarien, die Sie Überprüfung vor dem Allgemein Rollout OneDrive for Business Multi-Geo Ihres Unternehmens aufnehmen möchten. Nachdem Sie diese Tests und alle zusätzlichen Anwendungsfälle, die für Ihr Unternehmen relevant sind abgeschlossen haben, können Sie auswählen, gehen Sie zum Hinzufügen von Benutzern in der anfänglichen Pilotgruppe.

**OneDrive für Unternehmen**

Wählen Sie OneDrive in das Startprogramm für Office 365-app, und bestätigen Sie, dass Sie automatisch an den entsprechenden Geo-Speicherort für den Benutzer, basierend auf der Benutzer Verteilerliste weitergeleitet werden. OneDrive für Unternehmen sollte an dieser Stelle Bereitstellung beginnen. Versuchen Sie nach der Bereitstellung, hoch- und Herunterladen von Dokumenten.

**OneDrive Mobile App**

Melden Sie sich bei Ihrer mobilen OneDrive-App mit den Anmeldeinformationen Ihres Test. Vergewissern Sie sich, dass Ihre OneDrive for Business-Dateien angezeigt und können von Ihrem mobilen Gerät mit ihnen interagieren.

**OneDrive Sync-client**

Vergewissern Sie sich, dass der OneDrive-Synchronisierungsclient Ihrer OneDrive for Business Geo-Speicherort nach der Anmeldung automatisch erkennt. Wenn Sie den Sync-Client herunterladen müssen, können Sie die **Synchronisierung** in der Bibliothek OneDrive klicken.

**Office-Anwendungen**

Vergewissern Sie sich, dass Sie von einer Office-Anwendung, wie Word anmelden OneDrive für Unternehmen zugreifen können. Öffnen Sie das Office-Anwendung, und wählen "OneDrive – <TenantName>". Office erkennt Ihres Standorts für OneDrive und zeigen Sie die Dateien, die Sie öffnen können.

**Sharing**

Versuchen Sie es Freigeben von OneDrive-Dateien. Vergewissern Sie sich, dass die Personenauswahl Sie alle SharePoint online Benutzer unabhängig von ihrem Geo-Standort angezeigt wird.
