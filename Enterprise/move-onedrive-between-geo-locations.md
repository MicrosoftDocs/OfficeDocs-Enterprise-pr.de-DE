---
title: Verschieben einer OneDrive-Website an einem anderen Geo-Speicherort
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: Erfahren Sie, wie eine OneDrive-Website an einem anderen Geo-Speicherort zu verschieben.
ms.openlocfilehash: 7ce9106fa7d8d144f0f8935713b4df926a73fb6b
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a><span data-ttu-id="21d56-103">Verschieben einer OneDrive-Website an einem anderen Geo-Speicherort</span><span class="sxs-lookup"><span data-stu-id="21d56-103">Move a OneDrive site to a different geo-location</span></span> 

<span data-ttu-id="21d56-p101">Mit OneDrive Geo verschieben, OneDrive eines Benutzers an einen anderen Geo Speicherort verschoben werden kann. OneDrive Geo Move wird von der SharePoint Online-Administrator oder Office 365 globaler Administrator ausgeführt. Bevor Sie eine OneDrive Geo verschieben beginnen, müssen Sie unbedingt benachrichtigt den Benutzer, dessen OneDrive verschoben wird, und wird empfohlen, dass sie alle Dateien für die Dauer der Verschiebung schließen. (Wenn der Benutzer hat dann mithilfe des Office-Clients während des Verschiebens bei geöffnetem Dokument verschieben Abschluss benötigten das Dokument am neuen Speicherort gespeichert werden sollen.) Die Verschiebung kann zu einem späteren Zeitpunkt, geplant werden, falls gewünscht.</span><span class="sxs-lookup"><span data-stu-id="21d56-p101">With OneDrive geo move, you can move a user’s OneDrive to a different geo location. OneDrive geo move is performed by the SharePoint Online administrator or the Office 365 global administrator. Before you start a OneDrive geo move, be sure to notify the user whose OneDrive is being moved and recommend they close all files for the duration of the move. (If the user has a document open using the Office client during the move, then upon move completion the document will need to be saved to the new location.) The move can be scheduled for a future time, if desired.</span></span>

<span data-ttu-id="21d56-p102">Der OneDrive-Dienst verwendet Azure BLOB-Speicher zum Speichern von Inhalten. Blob Storage des Benutzers OneDrive zugeordnet werden aus der Quelle in Geo Zielspeicherort innerhalb von 40 Tagen Ziel OneDrive für den Benutzer verfügbar wird verschoben. Wie das Ziel OneDrive verfügbar ist, wird der Zugriff auf den Benutzer OneDrive wiederhergestellt werden.</span><span class="sxs-lookup"><span data-stu-id="21d56-p102">The OneDrive service uses Azure Blob Storage to store content. The Storage blob associated with the user’s OneDrive will be moved from the source to destination geo location within 40 days of destination OneDrive being available to the user. The access to the user’s OneDrive will be restored as soon as the destination OneDrive is available.</span></span>

<span data-ttu-id="21d56-p103">Während der OneDrive Geo Move Fenster (ungefähr 2 bis 6 Stunden) ist der Benutzer OneDrive schreibgeschützt festgelegt. Der Benutzer zugreifen kann weiterhin ihre Dateien über OneDrive-Synchronisierungsclient oder ihre OneDrive-Website in SharePoint Online. Nach Abschluss der OneDrive Geo verschieben, wird der Benutzer automatisch verbunden, ihre OneDrive am Zielspeicherort Geo beim Navigieren sie zu OneDrive in Office 365-app-Start. Sync-Client startet automatisch vom neuen Speicherort synchronisieren.</span><span class="sxs-lookup"><span data-stu-id="21d56-p103">During OneDrive geo move window (about 2-6 hours) the user's OneDrive is set to read-only. The user can still access their files via the OneDrive sync client or their OneDrive site in SharePoint Online. After OneDrive geo move is complete, the user will be automatically connected to their OneDrive at the destination geo location when they navigate to OneDrive in the Office 365 app launcher. The sync client will automatically begin syncing from the new location.</span></span>

<span data-ttu-id="21d56-115">Verfahren in diesem Artikel benötigen Sie das [Microsoft SharePoint Online-PowerShell-Modul](https://www.microsoft.com/en-us/download/details.aspx?id=35588).</span><span class="sxs-lookup"><span data-stu-id="21d56-115">The procedures in this article require the [Microsoft SharePoint Online PowerShell Module](https://www.microsoft.com/en-us/download/details.aspx?id=35588).</span></span>

## <a name="moving-a-onedrive-site"></a><span data-ttu-id="21d56-116">Verschieben einer OneDrive-Website</span><span class="sxs-lookup"><span data-stu-id="21d56-116">Moving a OneDrive site</span></span>

<span data-ttu-id="21d56-p104">Informationen zum Ausführen einer OneDrive Geo verschieben, der mandantenadministrator des Benutzers bevorzugte Daten Speicherort (Verteilerliste) zuerst auf den entsprechenden Geo Speicherort festlegen muss. Nachdem Sie der persönlichen Verteilerliste festgelegt ist, warten Sie mindestens 24 Stunden für die Aktualisierung der Verteilerliste standortübergreifenden Geo synchronisieren, bevor Sie beginnen, OneDrive Geo verschieben.</span><span class="sxs-lookup"><span data-stu-id="21d56-p104">To perform a OneDrive geo move, the tenant administrator must first set the user’s Preferred Data Location (PDL) to the appropriate geo location. Once the PDL is set, wait for at least 24 hours for the PDL update to sync across the geo locations before starting the OneDrive geo move.</span></span>

<span data-ttu-id="21d56-119">Wenn die Geo mit Cmdlets zu verschieben, verbinden Sie SPO-Webdienst unter der aktuellen Position des Benutzers OneDrive Geo, mithilfe der folgenden Syntax:</span><span class="sxs-lookup"><span data-stu-id="21d56-119">When using the geo move cmdlets, connect to SPO Service at the user’s current OneDrive geo location, using the following syntax:</span></span>

`connect-sposervice -url https://<tenantName>-admin.sharepoint.com`

<span data-ttu-id="21d56-120">Beispiel: um OneDrive des Benutzers 'Matt@contosoenergy.onmicrosoft.com' verschieben, Herstellen einer Verbindung mit EUR SharePoint Admin Center wie der Benutzer OneDrive EUR Geo Speicherort befindet:</span><span class="sxs-lookup"><span data-stu-id="21d56-120">For example: To move OneDrive of user ‘Matt@contosoenergy.onmicrosoft.com’, connect to EUR SharePoint Admin center as the user’s OneDrive is in EUR geo location:</span></span>

`connect-sposervice -url https://contosoenergyeur-admin.sharepoint.com`

![](media/move-onedrive-between-geo-locations_image1.png)

## <a name="validating-the-environment"></a><span data-ttu-id="21d56-121">Überprüfen der Umgebung</span><span class="sxs-lookup"><span data-stu-id="21d56-121">Validating the environment</span></span>

<span data-ttu-id="21d56-122">Bevor Sie beginnen eine OneDrive Geo verschieben, und es wird empfohlen, dass Sie die Umgebung überprüfen.</span><span class="sxs-lookup"><span data-stu-id="21d56-122">Before you start a OneDrive geo move, we recommend that you validate the environment.</span></span>

<span data-ttu-id="21d56-123">Um sicherzustellen, dass alle Geo Speicherorte kompatibel sind, führen Sie Folgendes aus:</span><span class="sxs-lookup"><span data-stu-id="21d56-123">To ensure that all geo locations are compatible, run:</span></span>

`Get-SPOGeoMoveCompatibilityStatus -AllLocations 1`

<span data-ttu-id="21d56-p105">Wenn eine OneDrive in rechtliche Aufbewahrungspflicht oder eine Unterwebsite enthalten, es kann nicht verschoben werden. Sie können das Cmdlet Start-SPOUserAndContentMove mit dem Parameter - ValidationOnly überprüfen, ob die OneDrive verschoben werden kann:</span><span class="sxs-lookup"><span data-stu-id="21d56-p105">If a OneDrive is under legal hold or if it contains a subsite, it cannot be moved. You can use the Start-SPOUserAndContentMove cmdlet with the -ValidationOnly parameter to validate if the OneDrive is able to be moved:</span></span>

`Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly`

<span data-ttu-id="21d56-p106">Dadurch wird Erfolg zurückgegeben, wenn die OneDrive ist bereit zur verschoben werden oder nicht möglich, wenn eine rechtliche Aufbewahrungspflicht oder Unterwebsite, die die Verschiebung verhindern würden. Nachdem Sie überprüft haben, dass die OneDrive zum Fortfahren bereit ist, können Sie die Verschiebung starten.</span><span class="sxs-lookup"><span data-stu-id="21d56-p106">This will return Success if the OneDrive is ready to be moved or Fail if there is a legal hold or subsite that would prevent the move. Once you have validated that the OneDrive is ready to move, you can start the move.</span></span>

## <a name="start-a-onedrive-geo-move"></a><span data-ttu-id="21d56-128">Starten Sie eine OneDrive Geo-Verschiebung</span><span class="sxs-lookup"><span data-stu-id="21d56-128">Start a OneDrive geo move</span></span>

<span data-ttu-id="21d56-129">Um die Verschiebung zu starten, führen Sie Folgendes aus:</span><span class="sxs-lookup"><span data-stu-id="21d56-129">To start the move, run:</span></span>  

`Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>`

<span data-ttu-id="21d56-130">Verwenden diesen Parameter:</span><span class="sxs-lookup"><span data-stu-id="21d56-130">Using these parameters:</span></span>

-   <span data-ttu-id="21d56-131">_UserPrincipalName_ – UPN des Benutzers, dessen OneDrive verschoben wird.</span><span class="sxs-lookup"><span data-stu-id="21d56-131">_UserPrincipalName_ – UPN of the user whose OneDrive is being moved.</span></span>

-   <span data-ttu-id="21d56-p107">_DestinationDataLocation_ – Geo-Speicherort, in dem die OneDrive verschoben werden muss. Dies sollte als bevorzugte Datenspeicherort des Benutzers übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="21d56-p107">_DestinationDataLocation_ – Geo-Location where the OneDrive needs to be moved. This should be same as the user’s preferred data location.</span></span>

> [!NOTE]
> <span data-ttu-id="21d56-134">Wir empfehlen die Ausführung `Get-SPOGeoMoveStateCompatibility` mit `ValidationOnly` Zugang OneDrive Geo verschieben.</span><span class="sxs-lookup"><span data-stu-id="21d56-134">We recommend running `Get-SPOGeoMoveStateCompatibility` with `ValidationOnly` prior to initiating OneDrive geo move.</span></span>

<span data-ttu-id="21d56-135">Angenommen, um die OneDrive des matt@contosoenergy.onmicrosoft.com von EUR in AUS zu verschieben, führen Sie Folgendes aus:</span><span class="sxs-lookup"><span data-stu-id="21d56-135">For example, to move the OneDrive of matt@contosoenergy.onmicrosoft.com from EUR to AUS, run:</span></span>

`Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS`

![](media/move-onedrive-between-geo-locations_image2.png)

<span data-ttu-id="21d56-136">Um eine Geo-Verschiebung für einen späteren Zeitpunkt planen, verwenden Sie einen der folgenden Parameter:</span><span class="sxs-lookup"><span data-stu-id="21d56-136">To schedule a geo move for a later time, use one of the following parameters:</span></span>

-   <span data-ttu-id="21d56-p108">_PreferredMoveBeginDate_ – wahrscheinlich Move beginnen zu diesem angegebenen Zeitpunkt. Uhrzeit muss in koordinierter Weltzeit (UTC) angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="21d56-p108">_PreferredMoveBeginDate_ – The move will likely begin at this specified time. Time must be specified in Coordinated Universal Time (UTC).</span></span>

-   <span data-ttu-id="21d56-p109">_PreferredMoveEndDate_ – wahrscheinlich Move sein diesmal angegebenen für einzelne best Effort abgeschlossen. Uhrzeit muss in koordinierter Weltzeit (UTC) angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="21d56-p109">_PreferredMoveEndDate_ – The move will likely be completed by this specified time, on a best effort basis. Time must be specified in Coordinated Universal Time (UTC).</span></span> 

## <a name="cancel-a-onedrive-geo-move"></a><span data-ttu-id="21d56-141">Abbrechen einer OneDrive Geo-Verschiebung</span><span class="sxs-lookup"><span data-stu-id="21d56-141">Cancel a OneDrive geo move</span></span> 

<span data-ttu-id="21d56-142">Sie können die Geo Verschiebung des OneDrive eines Benutzers, beenden, sofern die Verschiebung nicht ausgeführt wird oder abgeschlossen, indem Sie mit dem Cmdlet:</span><span class="sxs-lookup"><span data-stu-id="21d56-142">You can stop the geo move of a user’s OneDrive, provided the move is not in progress or completed by using the cmdlet:</span></span>

`Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>`

<span data-ttu-id="21d56-143">Dabei ist _UserPrincipalName_ den UPN des Benutzers, dessen OneDrive verschieben, dass Sie beenden möchten.</span><span class="sxs-lookup"><span data-stu-id="21d56-143">Where _UserPrincipalName_ is the UPN of the user whose OneDrive move you want to stop.</span></span>

## <a name="determining-current-status"></a><span data-ttu-id="21d56-144">Bestimmen der aktuellen status</span><span class="sxs-lookup"><span data-stu-id="21d56-144">Determining current status</span></span>

<span data-ttu-id="21d56-145">Sie können Überprüfen des Status einer OneDrive Geo Verschieben an- und Abmelden der Geo, die Sie mit dem Cmdlet Get-SPOUserAndContentMoveState verbunden sind.</span><span class="sxs-lookup"><span data-stu-id="21d56-145">You can check the status of a OneDrive geo move in or out of the geo that you’re connected to by using the Get-SPOUserAndContentMoveState cmdlet.</span></span>

<span data-ttu-id="21d56-146">Die Move-Status werden in der folgenden Tabelle beschrieben.</span><span class="sxs-lookup"><span data-stu-id="21d56-146">The move statuses are described in the following table.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="21d56-147"><strong>Status</strong></span><span class="sxs-lookup"><span data-stu-id="21d56-147"><strong>Status</strong></span></span></th>
<th align="left"><span data-ttu-id="21d56-148"><strong>Beschreibung</strong></span><span class="sxs-lookup"><span data-stu-id="21d56-148"><strong>Description</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="21d56-149">Nicht gestartet</span><span class="sxs-lookup"><span data-stu-id="21d56-149">NotStarted</span></span></td>
<td align="left"><span data-ttu-id="21d56-150">Die Verschiebung wurde nicht gestartet.</span><span class="sxs-lookup"><span data-stu-id="21d56-150">The move has not started.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="21d56-151">In Bearbeitung (<em>n</em>/4)</span><span class="sxs-lookup"><span data-stu-id="21d56-151">InProgress (<em>n</em>/4)</span></span></td>
<td align="left"><span data-ttu-id="21d56-152">Die Verschiebung wird gerade in einem der folgenden Zustände: Validierung (1/4) (2/4) zu sichern, wiederherstellen (3/4), Bereinigung (4.4).</span><span class="sxs-lookup"><span data-stu-id="21d56-152">The move is in progress in one of the following states: Validation (1/4), Backup (2/4), Restore (3/4), Cleanup (4/4).</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="21d56-153">Erfolg</span><span class="sxs-lookup"><span data-stu-id="21d56-153">Success</span></span></td>
<td align="left"><span data-ttu-id="21d56-154">Die Verschiebung wurde erfolgreich abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="21d56-154">The move has completed successfully.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="21d56-155">Failed</span><span class="sxs-lookup"><span data-stu-id="21d56-155">Failed</span></span></td>
<td align="left"><span data-ttu-id="21d56-156">Die Verschiebung nicht erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="21d56-156">The move failed.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="21d56-157">Um den Status eines bestimmten Benutzers Move suchen möchten, verwenden Sie den Parameter UserPrincipalName:</span><span class="sxs-lookup"><span data-stu-id="21d56-157">To find the status of a specific user’s move, use the UserPrincipalName parameter:</span></span>

`Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>`

<span data-ttu-id="21d56-158">Damit ermittelt wird den Status aller der hingegen an- und Abmelden der Geo-Speicherort, der Sie verbunden sind, verwenden Sie den MoveState-Parameter mit einem der folgenden Werte: nicht gestartet "," in Bearbeitung "," Erfolg "," Fehler "," alle.</span><span class="sxs-lookup"><span data-stu-id="21d56-158">To find the status of all of the moves in or out of the geo location that you’re connected to, use the MoveState parameter with one of the following values: NotStarted, InProgress, Success, Failed, All.</span></span>

`Get-SPOUserAndContentMoveState -MoveState <value>`

<span data-ttu-id="21d56-159">Sie können auch hinzufügen der `-Verbose` Parameter ausführlichere Beschreibung des Status verschieben.</span><span class="sxs-lookup"><span data-stu-id="21d56-159">You can also add the `-Verbose` parameter for more verbose descriptions of the move state.</span></span>

## <a name="user-experience"></a><span data-ttu-id="21d56-160">Benutzererfahrung</span><span class="sxs-lookup"><span data-stu-id="21d56-160">User Experience</span></span>

<span data-ttu-id="21d56-p110">Benutzer OneDrive sollte minimalen Unterbrechung bemerken, wenn ihre OneDrive in einen anderen Geo Speicherort verschoben wird. Neben dem eine kurze schreibgeschützten Zustand beim Verschieben bleiben vorhandene Verknüpfungen und Berechtigungen ordnungsgemäß ausgeführt, wenn die Verschiebung abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="21d56-p110">Users of OneDrive should notice minimal disruption if their OneDrive is moved to a different geo location. Aside from a brief read-only state during the move, existing links and permissions will continue to work as expected once the move is completed.</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="21d56-163">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="21d56-163">OneDrive for Business</span></span>

<span data-ttu-id="21d56-p111">Während der Verschiebevorgang ausgeführt wird ist OneDrive für den Benutzer schreibgeschützt festgelegt. Wenn die Verschiebung abgeschlossen ist, wird der Benutzer auf ihre OneDrive am neuen Speicherort Geo umgeleitet, wenn sie das Startprogramm für Office 365-app oder einem Webbrowser zu OneDrive navigieren.</span><span class="sxs-lookup"><span data-stu-id="21d56-p111">While the move is in progress the user’s OneDrive is set to read-only. Once the move is completed, the user is directed to their OneDrive in the new geo location when they navigate to OneDrive the Office 365 app launcher or a web browser.</span></span>

### <a name="permissions-on-onedrive-content"></a><span data-ttu-id="21d56-166">Berechtigungen für OneDrive-Inhalte</span><span class="sxs-lookup"><span data-stu-id="21d56-166">Permissions on OneDrive content</span></span>

<span data-ttu-id="21d56-167">Benutzer mit Berechtigungen zur OneDrive-Inhalt werden weiterhin haben Zugriff auf die Inhalte beim Verschieben und abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="21d56-167">Users with permissions to OneDrive content will continue to have access to the content during the move and after it’s complete.</span></span>

### <a name="onedrive-sync-client"></a><span data-ttu-id="21d56-168">OneDrive-Synchronisierungsclient</span><span class="sxs-lookup"><span data-stu-id="21d56-168">OneDrive Sync Client</span></span> 

<span data-ttu-id="21d56-p112">OneDrive-Synchronisierungsclient erkennt automatisch und nahtlos übertragen am neuen Speicherort OneDrive synchronisiert wird, sobald die OneDrive Geo Verschiebung abgeschlossen ist. Der Benutzer muss nicht-Anmeldung erneut oder eine andere Aktion ausführen.</span><span class="sxs-lookup"><span data-stu-id="21d56-p112">The OneDrive sync client will automatically detect and seamlessly transfer syncing to the new OneDrive location once the OneDrive geo move is complete. The user does not need to sign-in again or take any other action.</span></span>

<span data-ttu-id="21d56-171">Wenn ein Benutzer eine Datei aktualisiert, während die OneDrive Geo Verschiebung ausgeführt wird, der Sync-Client benachrichtigt werden, wenn Dateiuploads ausstehen während des Verschiebens ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="21d56-171">If a user updates a file while the OneDrive geo move is in progress, the sync client will notify them that file uploads are pending while the move is underway.</span></span>

### <a name="sharing-links"></a><span data-ttu-id="21d56-172">Freigeben von links</span><span class="sxs-lookup"><span data-stu-id="21d56-172">Sharing links</span></span> 

<span data-ttu-id="21d56-173">Bei OneDrive Geo verschieben Abschluss, die vorhandenen freigegebenen Links für die Dateien, die verschoben wurden, werden automatisch am neuen Speicherort Geo umgeleitet.</span><span class="sxs-lookup"><span data-stu-id="21d56-173">Upon OneDrive geo move completion, the existing shared links for the files that were moved will automatically redirect to the new geo location.</span></span>

### <a name="onenote-experience"></a><span data-ttu-id="21d56-174">OneNote-Erfahrung</span><span class="sxs-lookup"><span data-stu-id="21d56-174">OneNote Experience</span></span> 

<span data-ttu-id="21d56-p113">OneNote Win32-Clients und UWP (Universal) App erkennt automatisch und nahtlos synchronisieren Notizbücher am neuen Speicherort OneDrive nach Abschluss der OneDrive Geo verschieben. Der Benutzer muss nicht-Anmeldung erneut oder eine andere Aktion ausführen. Das Symbol nur angezeigt, die dem Benutzer handelt es sich Notizbuch Sync fehlschlagen würde, wenn OneDrive Geo Verschiebevorgang ausgeführt wird. Diese Erfahrung ist in den folgenden OneNote-Client-Versionen verfügbar:</span><span class="sxs-lookup"><span data-stu-id="21d56-p113">OneNote win32 client and UWP (Universal) App will automatically detect and seamlessly sync notebooks to the new OneDrive location once OneDrive geo move is complete. The user does not need to sign-in again or take any other action. The only visible indicator to the user is notebook sync would fail when OneDrive geo move is in progress. This experience is available on the following OneNote client versions:</span></span>

-   <span data-ttu-id="21d56-179">OneNote win32 – Version 16.0.8326.2096 (und höher)</span><span class="sxs-lookup"><span data-stu-id="21d56-179">OneNote win32 – Version 16.0.8326.2096 (and later)</span></span>

-   <span data-ttu-id="21d56-180">OneNote UWP – Version 16.0.8431.1006 (und höher)</span><span class="sxs-lookup"><span data-stu-id="21d56-180">OneNote UWP – Version 16.0.8431.1006 (and later)</span></span>

-   <span data-ttu-id="21d56-181">OneNote Mobile App – Version 16.0.8431.1011 (und höher)</span><span class="sxs-lookup"><span data-stu-id="21d56-181">OneNote Mobile App – Version 16.0.8431.1011 (and later)</span></span>

### <a name="teams-app"></a><span data-ttu-id="21d56-182">Teams-app</span><span class="sxs-lookup"><span data-stu-id="21d56-182">Teams app</span></span>

<span data-ttu-id="21d56-p114">Bei OneDrive Geo verschieben Abschluss, Benutzer werden haben Zugriff auf ihre OneDrive-Dateien auf der App Teams darüber, Dateien, die per Chat aus ihrer OneDrive vor dem Verschieben Geo Teams freigegeben sind weiterhin funktionsfähig nach verschieben.</span><span class="sxs-lookup"><span data-stu-id="21d56-p114">Upon OneDrive geo move completion, users will have access to their OneDrive files on the Teams app. Additionally, files shared via Teams chat from their OneDrive prior to geo move will continue to work after move is complete.</span></span>

### <a name="onedrive-for-business-mobile-app-ios"></a><span data-ttu-id="21d56-185">OneDrive für Unternehmen Mobile App (iOS)</span><span class="sxs-lookup"><span data-stu-id="21d56-185">OneDrive for Business Mobile App (iOS)</span></span> 

<span data-ttu-id="21d56-186">Verschieben Sie nach OneDrive Geo Abschluss, und der Benutzer muss sich abmelden und dann erneut anmelden, auf die iOS Mobile App am neuen Speicherort OneDrive synchronisieren.</span><span class="sxs-lookup"><span data-stu-id="21d56-186">Upon OneDrive geo move completion, the user would need to sign out and sign in again on the iOS Mobile App to sync to the new OneDrive location.</span></span>

### <a name="existing-followed-groups-and-sites"></a><span data-ttu-id="21d56-187">Vorhandene gefolgt, Gruppen und Websites</span><span class="sxs-lookup"><span data-stu-id="21d56-187">Existing followed groups and sites</span></span>

<span data-ttu-id="21d56-p115">Beobachteter Websites und Gruppen werden in OneDrive für Unternehmen unabhängig vom Standort Geo des Benutzers angezeigt. Websites und Gruppen in einen anderen Speicherort für Geo gehostet werden in einer separaten Registerkarte geöffnet.</span><span class="sxs-lookup"><span data-stu-id="21d56-p115">Followed sites and groups will show up in the user's OneDrive for business regardless of their geo location. Sites and Groups hosted in another geo location will open in a separate tab.</span></span>
