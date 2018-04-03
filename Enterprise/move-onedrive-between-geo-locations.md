---
title: Verschieben einer OneDrive-Website an einem anderen Geo-Speicherort
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Erfahren Sie, wie eine OneDrive-Website an einem anderen Geo-Speicherort zu verschieben.
ms.openlocfilehash: a31f683170fdb83dac90e9d09884c3020d1a47b1
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/03/2018
---
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a>Verschieben einer OneDrive-Website an einem anderen Geo-Speicherort 

Mit OneDrive Geo verschieben, OneDrive eines Benutzers an einen anderen Geo Speicherort verschoben werden kann. OneDrive Geo Move wird von der SharePoint Online-Administrator oder Office 365 globaler Administrator ausgeführt. Bevor Sie eine OneDrive Geo verschieben beginnen, müssen Sie unbedingt benachrichtigt den Benutzer, dessen OneDrive verschoben wird, und wird empfohlen, dass sie alle Dateien für die Dauer der Verschiebung schließen. (Wenn der Benutzer hat dann mithilfe des Office-Clients während des Verschiebens bei geöffnetem Dokument verschieben Abschluss benötigten das Dokument am neuen Speicherort gespeichert werden sollen.) Die Verschiebung kann zu einem späteren Zeitpunkt, geplant werden, falls gewünscht.

Der OneDrive-Dienst verwendet Azure BLOB-Speicher zum Speichern von Inhalten. Blob Storage des Benutzers OneDrive zugeordnet werden aus der Quelle in Geo Zielspeicherort innerhalb von 40 Tagen Ziel OneDrive für den Benutzer verfügbar wird verschoben. Wie das Ziel OneDrive verfügbar ist, wird der Zugriff auf den Benutzer OneDrive wiederhergestellt werden.

Während der OneDrive Geo Move Fenster (ungefähr 2 bis 6 Stunden) ist der Benutzer OneDrive schreibgeschützt festgelegt. Der Benutzer zugreifen kann weiterhin ihre Dateien über OneDrive-Synchronisierungsclient oder ihre OneDrive-Website in SharePoint Online. Nach Abschluss der OneDrive Geo verschieben, wird der Benutzer automatisch verbunden, ihre OneDrive am Zielspeicherort Geo beim Navigieren sie zu OneDrive in Office 365-app-Start. Sync-Client startet automatisch vom neuen Speicherort synchronisieren.

Verfahren in diesem Artikel benötigen Sie das [Microsoft SharePoint Online-PowerShell-Modul](https://www.microsoft.com/en-us/download/details.aspx?id=35588).

## <a name="moving-a-onedrive-site"></a>Verschieben einer OneDrive-Website

Informationen zum Ausführen einer OneDrive Geo verschieben, der mandantenadministrator des Benutzers bevorzugte Daten Speicherort (Verteilerliste) zuerst auf den entsprechenden Geo Speicherort festlegen muss. Nachdem Sie der persönlichen Verteilerliste festgelegt ist, warten Sie mindestens 24 Stunden für die Aktualisierung der Verteilerliste standortübergreifenden Geo synchronisieren, bevor Sie beginnen, OneDrive Geo verschieben.

Wenn die Geo mit Cmdlets zu verschieben, verbinden Sie SPO-Webdienst unter der aktuellen Position des Benutzers OneDrive Geo, mithilfe der folgenden Syntax:

`connect-sposervice -url https://<tenantName>-admin.sharepoint.com`

Beispiel: um OneDrive des Benutzers 'Matt@contosoenergy.onmicrosoft.com' verschieben, Herstellen einer Verbindung mit EUR SharePoint Admin Center wie der Benutzer OneDrive EUR Geo Speicherort befindet:

`connect-sposervice -url https://contosoenergyeur-admin.sharepoint.com`

![](media/move-onedrive-between-geo-locations_image1.png)

## <a name="validating-the-environment"></a>Überprüfen der Umgebung

Bevor Sie beginnen eine OneDrive Geo verschieben, und es wird empfohlen, dass Sie die Umgebung überprüfen.

Um sicherzustellen, dass alle Geo Speicherorte kompatibel sind, führen Sie Folgendes aus:

`Get-SPOGeoMoveCompatibilityStatus -AllLocations 1`

Wenn eine OneDrive in rechtliche Aufbewahrungspflicht oder eine Unterwebsite enthalten, es kann nicht verschoben werden. Sie können das Cmdlet Start-SPOUserAndContentMove mit dem Parameter - ValidationOnly überprüfen, ob die OneDrive verschoben werden kann:

`Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly`

Dadurch wird Erfolg zurückgegeben, wenn die OneDrive ist bereit zur verschoben werden oder nicht möglich, wenn eine rechtliche Aufbewahrungspflicht oder Unterwebsite, die die Verschiebung verhindern würden. Nachdem Sie überprüft haben, dass die OneDrive zum Fortfahren bereit ist, können Sie die Verschiebung starten.

## <a name="start-a-onedrive-geo-move"></a>Starten Sie eine OneDrive Geo-Verschiebung

Um die Verschiebung zu starten, führen Sie Folgendes aus:  

`Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>`

Verwenden diesen Parameter:

-   _UserPrincipalName_ – UPN des Benutzers, dessen OneDrive verschoben wird.

-   _DestinationDataLocation_ – Geo-Speicherort, in dem die OneDrive verschoben werden muss. Dies sollte als bevorzugte Datenspeicherort des Benutzers übereinstimmen.

> [!NOTE]
> Wir empfehlen die Ausführung `Get-SPOGeoMoveStateCompatibility` mit `ValidationOnly` Zugang OneDrive Geo verschieben.

Angenommen, um die OneDrive des matt@contosoenergy.onmicrosoft.com von EUR in AUS zu verschieben, führen Sie Folgendes aus:

`Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS`

![](media/move-onedrive-between-geo-locations_image2.png)

Um eine Geo-Verschiebung für einen späteren Zeitpunkt planen, verwenden Sie einen der folgenden Parameter:

-   _PreferredMoveBeginDate_ – wahrscheinlich Move beginnen zu diesem angegebenen Zeitpunkt.

-   _PreferredMoveEndDate_ – wahrscheinlich Move sein diesmal angegebenen für einzelne best Effort abgeschlossen.

## <a name="cancel-a-onedrive-geo-move"></a>Abbrechen einer OneDrive Geo-Verschiebung 

Sie können die Geo Verschiebung des OneDrive eines Benutzers, beenden, sofern die Verschiebung nicht ausgeführt wird oder abgeschlossen, indem Sie mit dem Cmdlet:

`Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>`

Dabei ist _UserPrincipalName_ den UPN des Benutzers, dessen OneDrive verschieben, dass Sie beenden möchten.

## <a name="determining-current-status"></a>Bestimmen der aktuellen status

Sie können Überprüfen des Status einer OneDrive Geo Verschieben an- und Abmelden der Geo, die Sie mit dem Cmdlet Get-SPOUserAndContentMoveState verbunden sind.

Die Move-Status werden in der folgenden Tabelle beschrieben.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Status</strong></th>
<th align="left"><strong>Beschreibung</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Nicht gestartet</td>
<td align="left">Die Verschiebung wurde nicht gestartet.</td>
</tr>
<tr class="even">
<td align="left">In Bearbeitung (<em>n</em>/4)</td>
<td align="left">Die Verschiebung wird gerade in einem der folgenden Zustände: Validierung (1/4) (2/4) zu sichern, wiederherstellen (3/4), Bereinigung (4.4).</td>
</tr>
<tr class="odd">
<td align="left">Erfolg</td>
<td align="left">Die Verschiebung wurde erfolgreich abgeschlossen.</td>
</tr>
<tr class="even">
<td align="left">Failed</td>
<td align="left">Die Verschiebung nicht erfolgreich.</td>
</tr>
</tbody>
</table>

Um den Status eines bestimmten Benutzers Move suchen möchten, verwenden Sie den Parameter UserPrincipalName:

`Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>`

Damit ermittelt wird den Status aller der hingegen an- und Abmelden der Geo-Speicherort, der Sie verbunden sind, verwenden Sie den MoveState-Parameter mit einem der folgenden Werte: nicht gestartet "," in Bearbeitung "," Erfolg "," Fehler "," alle.

`Get-SPOUserAndContentMoveState -MoveState <value>`

Sie können auch hinzufügen der `-Verbose` Parameter ausführlichere Beschreibung des Status verschieben.

## <a name="user-experience"></a>Benutzererfahrung

Benutzer OneDrive sollte minimalen Unterbrechung bemerken, wenn ihre OneDrive in einen anderen Geo Speicherort verschoben wird. Neben dem eine kurze schreibgeschützten Zustand beim Verschieben bleiben vorhandene Verknüpfungen und Berechtigungen ordnungsgemäß ausgeführt, wenn die Verschiebung abgeschlossen ist.

### <a name="onedrive-for-business"></a>OneDrive für Unternehmen

Während der Verschiebevorgang ausgeführt wird ist OneDrive für den Benutzer schreibgeschützt festgelegt. Wenn die Verschiebung abgeschlossen ist, wird der Benutzer auf ihre OneDrive am neuen Speicherort Geo umgeleitet, wenn sie das Startprogramm für Office 365-app oder einem Webbrowser zu OneDrive navigieren.

### <a name="permissions-on-onedrive-content"></a>Berechtigungen für OneDrive-Inhalte

Benutzer mit Berechtigungen zur OneDrive-Inhalt werden weiterhin haben Zugriff auf die Inhalte beim Verschieben und abgeschlossen ist.

### <a name="onedrive-sync-client"></a>OneDrive-Synchronisierungsclient 

OneDrive-Synchronisierungsclient erkennt automatisch und nahtlos übertragen am neuen Speicherort OneDrive synchronisiert wird, sobald die OneDrive Geo Verschiebung abgeschlossen ist. Der Benutzer muss nicht-Anmeldung erneut oder eine andere Aktion ausführen.

Wenn ein Benutzer eine Datei aktualisiert, während die OneDrive Geo Verschiebung ausgeführt wird, der Sync-Client benachrichtigt werden, wenn Dateiuploads ausstehen während des Verschiebens ausgeführt wird.

### <a name="sharing-links"></a>Freigeben von links 

Bei OneDrive Geo verschieben Abschluss, die vorhandenen freigegebenen Links für die Dateien, die verschoben wurden, werden automatisch am neuen Speicherort Geo umgeleitet.

### <a name="onenote-experience"></a>OneNote-Erfahrung 

OneNote Win32-Clients und UWP (Universal) App erkennt automatisch und nahtlos synchronisieren Notizbücher am neuen Speicherort OneDrive nach Abschluss der OneDrive Geo verschieben. Der Benutzer muss nicht-Anmeldung erneut oder eine andere Aktion ausführen. Das Symbol nur angezeigt, die dem Benutzer handelt es sich Notizbuch Sync fehlschlagen würde, wenn OneDrive Geo Verschiebevorgang ausgeführt wird. Diese Erfahrung ist in den folgenden OneNote-Client-Versionen verfügbar:

-   OneNote win32 – Version 16.0.8326.2096 (und höher)

-   OneNote UWP – Version 16.0.8431.1006 (und höher)

-   OneNote Mobile App – Version 16.0.8431.1011 (und höher)

### <a name="teams-app"></a>Teams-app

Bei OneDrive Geo verschieben Abschluss, Benutzer werden haben Zugriff auf ihre OneDrive-Dateien auf der App Teams darüber, Dateien, die per Chat aus ihrer OneDrive vor dem Verschieben Geo Teams freigegeben sind weiterhin funktionsfähig nach verschieben.

### <a name="onedrive-for-business-mobile-app-ios"></a>OneDrive für Unternehmen Mobile App (iOS) 

Verschieben Sie nach OneDrive Geo Abschluss, und der Benutzer muss sich abmelden und dann erneut anmelden, auf die iOS Mobile App am neuen Speicherort OneDrive synchronisieren.

### <a name="existing-followed-groups-and-sites"></a>Vorhandene gefolgt, Gruppen und Websites

Beobachteter Websites und Gruppen werden in OneDrive für Unternehmen unabhängig vom Standort Geo des Benutzers angezeigt. Websites und Gruppen in einen anderen Speicherort für Geo gehostet werden in einer separaten Registerkarte geöffnet.
