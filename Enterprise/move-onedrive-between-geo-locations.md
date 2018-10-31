---
title: Verschieben einer OneDrive-Website an einen anderen geografischen Standort
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: In diesem Artikel finden Sie Informationen zum Verschieben einer OneDrive-Website an einen anderen geografischen Standort.
ms.openlocfilehash: 258c562343875ff4ad115b81dba5338c79641dfc
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849851"
---
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a>Verschieben einer OneDrive-Website an einen anderen geografischen Standort 

Mit der Verschiebung von geografischen Standorten in OneDrive können Sie die OneDrive-Umgebung eines Benutzern an einen anderen geografischen Standort verschieben. Die Verschiebung von geografischen Standorten in OneDrive kann von einem SharePoint Online-Administrator oder dem globalen Office 365-Administrator durchgeführt werden. Bevor Sie einen geografischen Standort in OneDrive verschieben, vergewissern Sie sich, dass der Benutzer, dessen OneDrive-Umgebung verschoben wird, darüber informiert wird, und es wird empfohlen, dass Benutzer alle Dateien für die Dauer der Verschiebung schließen. (Wenn der Benutzer während der Verschiebung ein Dokument unter Verwendung des Office-Clients geöffnet hat, muss das Dokument nach Abschluss der Verschiebung an dem neuen Ort gespeichert werden.) Die Verschiebung kann bei Bedarf für einen künftigen Zeitpunkt geplant werden.

Der OneDrive-Dienst verwendet Azure Blob Storage zum Speichern von Inhalten. Der Storage Blob, der der OneDrive-Umgebung des Benutzers zugewiesen ist, wird von dem geografischen Quellstandort an den Zielstandort innerhalb von 40 Tagen verschoben, nachdem die OneDrive-Zielumgebung dem Benutzer zur Verfügung gestellt wurde. Der Benutzerzugriff auf OneDrive wird wiederhergestellt, sobald die OneDrive-Zielumgebung verfügbar ist.

In dem Zeitfenster, in dem geografische Standorte in OneDrive verschoben werden (ca. 2 bis 6 Stunden), ist die OneDrive-Umgebung des Benutzers schreibgeschützt. Der Benutzer kann weiterhin auf seine Dateien über den OneDrive-Synchronisierungsclient oder die OneDrive-Website in SharePoint Online zugreifen. Nach Abschluss des Verschiebevorgangs des geografischen Standorts in OneDrive wird der Benutzer automatisch mit OneDrive an seinem geografischen Zielstandort verbunden, wenn er in dem Office 365-App-Startfeld zu OneDrive navigiert. Der Synchronisierungsclient startet automatisch die Synchronisierung an dem neuen Ort.

Für die Vorgehensweisen in diesem Artikel ist das [Microsoft SharePoint Online PowerShell-Modul](https://www.microsoft.com/en-us/download/details.aspx?id=35588) erforderlich.

## <a name="communicating-to-your-users"></a>Kommunikation mit Benutzern

Beim Verschieben von OneDrive-Websites zwischen geografischen Standorten, ist es wichtig, dass Sie Ihren Benutzer kommunizieren, was sie zu erwarten haben. Auf diese Weise werden Verunsicherungen seitens der Benutzer und Anrufe bei Ihrem Help Desk verhindert. Schreiben Sie Ihren Benutzer vor der Verschiebung eine E-Mail, und teilen Sie ihnen die folgenden Informationen mit:

- Wann die Verschiebung voraussichtlich stattfinden soll und wie lange sie dauern wird.
- An welchen geografischen Standort OneDrive verschoben wird sowie die URL zum Zugreifen auf den neuen Standort.
- Der Benutzer sollte alle Dateien schließen und während der Verschiebung keine Änderungen vornehmen.
- Dateiberechtigungen und Freigabe werden als Ergebnis der Verschiebung nicht geändert.
- Erwartungen im Hinblick auf die [Benutzererfahrung in einer Multi-Geo-Umgebung](multi-geo-user-experience.md)

Vergessen Sie nicht, Ihren Benutzer eine E-Mail zu schicken, wenn die Verschiebung erfolgreich abgeschlossen wurde, um sie darüber zu informieren, dass sie ihre Arbeit in OneDrive fortsetzen können.

## <a name="scheduling-onedrive-site-moves"></a>Planen der Verschiebung von OneDrive-Sites

Sie können die Verschiebung von OneDrive-Sites im Voraus planen (weiter unten in diesem Artikel beschrieben). Wir empfehlen, zunächst mit einer kleinen Anzahl Benutzer zu beginnen, um die Arbeitsabläufe und Kommunikationsstrategien zu überprüfen. Sobald Sie mit dem Prozess vertraut sind, können Sie die Verschiebungen wie folgt planen:

- Sie können bis zu 4.000 Verschiebungen zugleich planen.
- Wenn mit dem Verschieben begonnen wird, können Sie weitere planen, bis zu maximal jeweils 4.000 ausstehenden Verschiebungen in der Warteschlange.
- Es wird empfohlen, nicht mehr als 4.000 Verschiebungen pro Monat zu planen.

## <a name="moving-a-onedrive-site"></a>Verschieben einer OneDrive-Website

Um geografische Standorte in OneDrive zu verschieben, muss der Mandantenadministrator zunächst den bevorzugten Datenspeicherort für den Benutzer auf den entsprechenden geografischen Standort festlegen. Warten Sie nach Festlegung des bevorzugten Datenspeicherorts mindestens 24 Stunden, bis der bevorzugte Datenspeicherort mit allen geografischen Standorten synchronisiert wird, bevor Sie mit dem Verschieben von geografischen Standorten in OneDrive beginnen.

Stellen Sie beim Verwenden von Cmdlets für das Verschieben von geografischen Standorten eine Verbindung mit dem SPO-Dienst an dem aktuellen geografischen OneDrive-Standort des Benutzers her, indem Sie die folgenden Syntax verwenden:

`connect-sposervice -url https://<tenantName>-admin.sharepoint.com`

Beispiel: Um die OneDrive-Umgebung des Benutzers „Matt@contosoenergy.onmicrosoft.com“ zu verschieben, stellen Sie eine Verbindung mit dem EUR SharePoint Admin Center, da sich die OneDrive-Umgebung des Benutzers an dem geografischen Standort in EUR befindet:

`connect-sposervice -url https://contosoenergyeur-admin.sharepoint.com`

![](media/move-onedrive-between-geo-locations-image1.png)

## <a name="validating-the-environment"></a>Überprüfen der Umgebung

Bevor Sie mit dem Verschieben von geografischen Standorten in OneDrive beginnen, sollten Sie die Umgebung überprüfen.

Um sicherzustellen, dass alle geografischen Standorte kompatibel sind, führen Sie den folgenden Befehl aus:

`Get-SPOGeoMoveCompatibilityStatus -AllLocations 1`

Wenn die gesetzliche Aufbewahrungspflicht für eine OneDrive-Umgebung aktiviert ist oder diese eine Unterwebsite enthält, kann die Umgebung nicht verschoben werden. Sie können das Start-SPOUserAndContentMove-Cmdlet mit dem -ValidationOnly-Parameter verwenden, um zu prüfen, ob die OneDrive-Umgebung verschoben werden kann:

`Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly`

Dieses gibt „Success“ zurück, wenn OneDrive verschoben werden kann, oder „Fail“, wenn die gesetzliche Aufbewahrungspflicht aktiviert ist oder eine Unterwebsite vorhanden ist, die die Verschiebung verhindert. Nachdem Sie überprüft haben, dass die OneDrive-Umgebung verschoben werden kann, können Sie mit der Verschiebung beginnen.

## <a name="start-a-onedrive-geo-move"></a>Starten einer Verschiebung von geografischen Standorten in OneDrive

Um mit der Verschiebung zu beginnen, führen Sie den folgenden Befehl aus:  

`Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>`

Verwenden Sie die folgenden Parameter:

-   _UserPrincipalName_ – Benutzerprinzipalname des Benutzers, dessen OneDrive-Umgebung verschoben wird.

-   _DestinationDataLocation_ – Geografischer Standort, an den die OneDrive-Umgebung verschoben werden soll. Dieser sollte mit dem bevorzugten Datenspeicherort des Benutzers identisch sein.

> [!NOTE]
> Es wird empfohlen, `Get-SPOGeoMoveStateCompatibility` mit `ValidationOnly` durchzuführen, bevor die Verschiebung des geografischen Standorts in OneDrive initiiert wird.

Führen Sie zum Beispiel zum Verschieben von OneDrive von matt@contosoenergy.onmicrosoft.com von EUR nach AUS den folgenden Befehl durch:

`Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS`

![](media/move-onedrive-between-geo-locations-image2.png)

Wenn Sie die Verschiebung eines geografischen Standorts zu einem späteren Zeitpunkt durchführen möchten, verwenden Sie einen der folgenden Parameter:

-   _PreferredMoveBeginDate_ – Die Verschiebung beginnt zu diesem Zeitpunkt. Die Zeit muss in koordinierter Weltzeit (UTC) angegeben werden.

-   _PreferredMoveEndDate_ – Die Verschiebung endet basieren auf dem Best-Effort-Prinzip zu diesem Zeitpunkt. Die Zeit muss in koordinierter Weltzeit (UTC) angegeben werden. 

## <a name="cancel-a-onedrive-geo-move"></a>Abbrechen einer Verschiebung von geografischen Standorten in OneDrive 

Sie können die Verschiebung der OneDrive-Umgebung eines Benutzers beenden, sofern die Verschiebung noch nicht ausgeführt oder abgeschlossen ist, indem Sie das folgende Cmdlet verwenden:

`Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>`

Dabei ist _UserPrincipalName_ der Benutzerprinzipalname des Benutzers, dessen OneDrive-Verschiebung beendet werden soll.

## <a name="determining-current-status"></a>Bestimmen des aktuellen Status

Sie können den Status einer OneDrive-Verschiebung von oder an einen geografischen Standort prüfen, mit dem Sie verbunden sind, indem Sie das Cmdlet „Get-SPOUserAndContentMoveState“ verwenden.

Die Statuswerte der Verschiebung werden in der folgenden Tabelle beschrieben.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Status</strong></th>
<th align="left"><strong>Beschreibung</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">NotStarted</td>
<td align="left">Die Verschiebung wurde noch nicht begonnen.</td>
</tr>
<tr class="even">
<td align="left">InProgress (<em>n</em>/4)</td>
<td align="left">Die Verschiebung wird ausgeführt, wenn einer der folgenden Statuswerte angezeigt wird: Validation (1/4), Backup (2/4), Restore (3/4), Cleanup (4/4).</td>
</tr>
<tr class="odd">
<td align="left">Success</td>
<td align="left">Die Verschiebung wurde erfolgreich ausgeführt.</td>
</tr>
<tr class="even">
<td align="left">Failed</td>
<td align="left">Beim Verschieben ist ein Fehler aufgetreten.</td>
</tr>
</tbody>
</table>

Um den Status einer bestimmten Verschiebung für einen Benutzer zu ermitteln, verwenden Sie den Parameter „UserPrincipalName“:

`Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>`

Um den Status aller Verschiebungen von oder an einen geografischen Standort zu ermitteln, mit dem Sie verbunden sind, verwenden Sie den MoveState-Parameter mit einem der folgenden Werte: NotStarted, InProgress, Success, Failed, All.

`Get-SPOUserAndContentMoveState -MoveState <value>`

Sie können auch den `-Verbose`-Parameter für weitere ausführliche Beschreibungen des Status der Verschiebung hinzufügen.

## <a name="user-experience"></a>Benutzererfahrung

OneDrive-Benutzer sollten minimale Unterbrechungen feststellen, wenn ihre OneDrive-Umgebung an einen anderen geografischen Standort verschoben wird. Neben einem kurzzeitigen Schreibschutz während des Verschiebevorgangs funktionieren vorhandene Links und Berechtigungen weiterhin wie gewohnt, sobald die Verschiebung abgeschlossen ist.

### <a name="onedrive-for-business"></a>OneDrive for Business

Während die Verschiebung ausgeführt wird, wird der Schreibschutz für die OneDrive-Umgebung des Benutzers aktiviert. Sobald die Verschiebung abgeschlossen ist, wird der Benutzer zu seiner OneDrive-Umgebung an dem neuen geografischen Standort weitergeleitet, wenn er im Office 365-App-Startfeld oder einem Webbrowser zu OneDrive navigiert.

### <a name="permissions-on-onedrive-content"></a>Berechtigungen für OneDrive-Inhalte

Benutzer mit Berechtigungen für OneDrive-Inhalte haben weiterhin Zugriff auf die Inhalte, sowohl während des Verschiebevorgangs als auch nach dessen Abschluss.

### <a name="onedrive-sync-client"></a>OneDrive-Synchronisierungsclient 

Der OneDrive-Synchronisierungsclient überträgt die Synchronisierung automatisch an den neuen OneDrive-Standort, sobald die Verschiebung des geografischen Standorts abgeschlossen ist. Der Benutzer muss sich weder erneut anmelden noch eine andere Aktion durchführen. ( (Version 17.3.6943.0625 oder höher des Synchronisierungsclients erforderlich.)

Wenn ein Benutzer eine Datei aktualisiert, während die Verschiebung des geografischen OneDrive-Standorts ausgeführt wird, benachrichtigt der Synchronisierungsclient den Benutzer, dass Dateiuploads ausstehen, während die Verschiebung ausgeführt wird.

### <a name="sharing-links"></a>Freigabelinks 

Nach Abschluss der geografischen Standortverschiebung in OneDrive werden vorhandene Freigabelinks für verschobene Dateien automatisch zu den Dateien an dem neuen geografischen Standort weiterleiten.

### <a name="onenote-experience"></a>OneNote-Benutzererfahrung 

OneNote-Win32-Client und UWP-App werden automatisch erkannt und synchronisieren nahtlos die Notizbücher mit dem neuen geografischen OneDrive-Standort, nachdem die geografische Standortverschiebung von OneDrive abgeschlossen wurde. Der Benutzer muss sich weder erneut anmelden noch eine andere Aktion durchführen. Der einzige für den Benutzer sichtbare Indikator ist, dass beim Synchronisieren des Notizbuchs ein Fehler auftritt, während die geografische Standortverschiebung von OneDrive ausgeführt wird. Diese Erfahrung gilt für die folgenden OneNote-Clientversionen:

-   OneNote-Win32 – Version 16.0.8326.2096 (und höher)

-   OneNote UWP – Version 16.0.8431.1006 (und höher)

-   Mobile OneNote-App – Version 16.0.8431.1011 (und höher)

### <a name="teams-app"></a>Teams-App

Nach Abschluss der geografischen Standortverschiebung von OneDrive haben Benutzer Zugriff auf ihre OneDrive-Dateien in der Teams-App. Darüber hinaus können die über Teams-Chat in OneDrive vor der Verschiebung freigegebenen Dateien weiterhin verwendet werden, sobald die Verschiebung abgeschlossen ist.

### <a name="onedrive-for-business-mobile-app-ios"></a>Mobile OneDrive for Business-App (iOS) 

Nach Abschluss der geografischen Standortverschiebung von OneDrive müssen sich Benutzer abmelden und erneut in der mobilen iOS-App anmelden, damit mit dem neuen OneDrive-Standort synchronisiert wird.

### <a name="existing-followed-groups-and-sites"></a>Vorhandene gefolgte Gruppen und Websites

Gefolgte Websites und Gruppen werden in OneDrive for Business unabhängig vom geografischen Standort angezeigt. Websites und Gruppen, die an einem anderen geografischen Standort gehostet werden, werden auf einer separaten Registerkarte geöffnet.
