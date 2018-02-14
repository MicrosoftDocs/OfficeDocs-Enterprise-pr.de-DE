---
title: Entfernen von Lizenzen von Benutzerkonten mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: "Erläutert, wie Office 365 PowerShell zum Entfernen von Office 365-Lizenzen, die Benutzern zuvor zugewiesen wurden."
ms.openlocfilehash: c02d5a6cac029ce9beb8077da98418734d935ded
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2018
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a><span data-ttu-id="389b7-103">Entfernen von Lizenzen von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="389b7-103">Remove licenses from user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="389b7-104">**Zusammenfassung:** Erläutert, wie Office 365 PowerShell zum Entfernen von Office 365-Lizenzen, die Benutzern zuvor zugewiesen wurden.</span><span class="sxs-lookup"><span data-stu-id="389b7-104">**Summary:** Explains how to use Office 365 PowerShell to remove Office 365 licenses that were previously assigned to users.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="389b7-105">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="389b7-105">Before you begin</span></span>

- <span data-ttu-id="389b7-p101">Für die Verfahren in diesem Thema müssen Sie eine Verbindung mit Office 365 PowerShell herstellen. Weitere Anweisungen finden Sie unter [Verbinden mit Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="389b7-p101">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="389b7-108">Zum Anzeigen der Lizenzinformationen Plan ( **AccountSkuID** ) in Ihrer Organisation finden Sie in den folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="389b7-108">To view the licensing plan ( **AccountSkuID** ) information in your organization, see the following topics:</span></span>
    
  - [<span data-ttu-id="389b7-109">Anzeigen von Lizenzen und Diensten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="389b7-109">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="389b7-110">Anzeigen von Lizenz- und Dienstdetails für Konten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="389b7-110">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
- <span data-ttu-id="389b7-111">Bei Verwendung des **Get-MsolUser**-Cmdlets ohne den _-All_-Parameter werden nur die ersten 500 Konten zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="389b7-111">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="389b7-112">Die Kurzfassung (Anweisungen ohne Erläuterungen)</span><span class="sxs-lookup"><span data-stu-id="389b7-112">The short version (instructions without explanations)</span></span>
<span data-ttu-id="389b7-113"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="389b7-113"></span></span>

<span data-ttu-id="389b7-p102">In diesem Abschnitt werden die Verfahren kurz und bündig erläutert. Wenn Sie Fragen haben oder weitere Informationen benötigen, können Sie den Rest des Themas lesen.</span><span class="sxs-lookup"><span data-stu-id="389b7-p102">This section presents the procedures without fanfare or superfluous explanation. If you have questions or want more information, you can read rest of the topic.</span></span>
  
<span data-ttu-id="389b7-116">Verwenden Sie die folgende Syntax, um Lizenzen von einem vorhandenen Benutzerkonto zu entfernen:</span><span class="sxs-lookup"><span data-stu-id="389b7-116">To remove licenses from an existing user account, use the following syntax:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

<span data-ttu-id="389b7-117">Dieses Beispiel entfernt die `litwareinc:ENTERPRISEPACK` Lizenz aus dem Benutzerkonto BelindaN@litwareinc.com (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="389b7-117">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user account BelindaN@litwareinc.com.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="389b7-118">Verwenden Sie eine der folgenden Methoden, um Lizenzen von einer Gruppe von vorhandenen lizenzierten Benutzern zu entfernen,:</span><span class="sxs-lookup"><span data-stu-id="389b7-118">To remove licenses from a group of existing licensed users, use either of the following methods:</span></span>
  
- <span data-ttu-id="389b7-119">**Filtern die anhand eines vorhandenen Attributs Konto Konten** Verwenden Sie dazu die folgende Syntax:</span><span class="sxs-lookup"><span data-stu-id="389b7-119">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
```
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="389b7-120">Dieses Beispiel entfernt die `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) Lizenzen von allen Konten für Benutzer in der Abteilung "Sales" in den USA.</span><span class="sxs-lookup"><span data-stu-id="389b7-120">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licenses from all accounts for users in the Sales department in the United States.</span></span>
    
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- <span data-ttu-id="389b7-121">**Verwenden einer Liste spezieller Konten** Führen Sie dazu die folgenden Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="389b7-121">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="389b7-122">Erstellen und speichern Sie eine Textdatei wie die folgende, die in jeder Zeile ein Konto enthält:</span><span class="sxs-lookup"><span data-stu-id="389b7-122">Create and save a text file that contains one account on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. <span data-ttu-id="389b7-123">Verwenden Sie folgende Syntax:</span><span class="sxs-lookup"><span data-stu-id="389b7-123">Use the following syntax:</span></span>
    
  ```
  Get-Content "<FileNameAndPath>" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
  ```

<span data-ttu-id="389b7-124">Dieses Beispiel entfernt die `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) Lizenz von Benutzerkonten in der Textdatei C:\My Documents\Accounts.txt definiert.</span><span class="sxs-lookup"><span data-stu-id="389b7-124">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user accounts defined in the text file C:\My Documents\Accounts.txt.</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  ```

<span data-ttu-id="389b7-125">Verwenden Sie die folgende Syntax, um Lizenzen von allen vorhandenen Benutzerkonten zu entfernen:</span><span class="sxs-lookup"><span data-stu-id="389b7-125">To remove licenses from all existing user accounts, use the following syntax:</span></span>
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="389b7-126">Dieses Beispiel entfernt die `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) Lizenz aus allen vorhandenen Benutzerkonten lizenziert.</span><span class="sxs-lookup"><span data-stu-id="389b7-126">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from all existing licensed user accounts.</span></span>
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="389b7-127">Die Langfassung (Anweisungen mit detaillierten Erläuterungen)</span><span class="sxs-lookup"><span data-stu-id="389b7-127">The long version (instructions with detailed explanations)</span></span>
<span data-ttu-id="389b7-128"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="389b7-128"></span></span>

<span data-ttu-id="389b7-p103">Nichts dauert ewig sowie enthält Office 365-Lizenzen: früher oder später es kommt der Zeitpunkt, Sie eine Lizenz von einem Benutzerkonto zu entfernen müssen. Der Benutzer ist vielleicht Urlaub wechseln; der Benutzer benötigt möglicherweise nicht mehr die Lizenz; Vielleicht - umfasst offensichtlich eine beliebige Anzahl von Gründe, warum Sie möglicherweise eine Benutzerlizenz entfernen möchten.</span><span class="sxs-lookup"><span data-stu-id="389b7-p103">Nothing lasts forever, and that includes Office 365 licenses: sooner or later, there will come a time when you need to remove a license from a user account. Maybe the user is going on leave; maybe the user no longer needs the license; maybe - well, there are obviously any number of reasons why you might want to remove a user license.</span></span>
  
<span data-ttu-id="389b7-p104">Bevor wir weiter es ist wichtig wechseln, beachten Sie, dass Sie nun erfordert eine Lizenz entfernen, entfernen Sie die Lizenz: deaktivieren alle Dienste für eine Lizenz ist nicht dasselbe wie eine Lizenz entfernen. Nehmen wir beispielsweise an, dass wir alle unsere Office 365-Lizenzen verwendet haben; Anders ausgedrückt, es gibt keine Lizenzen verfügbar ist. Sie beschließen, führen das Verfahren unter [Deaktivieren des Zugriffs auf Services mit Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md) , um alle Dienste, beispielsweise für Belinda Newman Konto zu deaktivieren. Nachdem wir gemacht, wie viele Lizenzen haben wir für uns verfügbaren? Haben richtig gehört: 0 (null). Ja, das Verfahren in diesem Thema wird *Deaktivieren* aller Dienste auf dem Belindas Lizenz, aber nicht deaktiviert (d. h., delete) die Lizenz selbst. Die Lizenz noch gültig sein, und es noch Belinda Newman zugewiesen. Er wird nicht nur diese Lizenz Zugriff auf eine beliebige Office 365-Dienste verwenden kann.</span><span class="sxs-lookup"><span data-stu-id="389b7-p104">Before we go any further it's important to note that removing a license requires you to, well, remove the license: disabling all the services on a license is not the same thing as removing a license. For example, suppose we've used up all our Office 365 licenses; in other words, we have no licenses available whatsoever. You decide to follow the procedure in [Disable access to services with Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md) to disable all the services, say, on Belinda Newman's account. After we do that, how many licenses will we have available to us? That's right: zero. Yes, the procedure from that topic will *disable*  all the services on Belinda's license, but it will not disable (i.e., delete) the license itself. The license will still be valid, and it will still be assigned to Belinda Newman. She just won't be able to use that license to access any Office 365 services.</span></span>
  
<span data-ttu-id="389b7-p105">Und das ist wichtig: Wenn Sie einem Benutzer eine Lizenz entziehen möchten müssen Sie tatsächlich *Entfernen* der Lizenz. Deaktivieren alle Dienste wird verhindert, dass des Benutzers anmelden bei Office 365, aber er wird nicht seine Lizenz frei. Wenn eine Lizenz wieder zu übernehmen, die aktuell, die einem Benutzer zugewiesen ist, müssen Sie einen Befehl ähnlich, einen Befehl ausführen, die den _RemoveLicenses_ -Parameter verwendet, um die Belinda zuvor zugewiesene Lizenz tatsächlich entfernt, werden soll:</span><span class="sxs-lookup"><span data-stu-id="389b7-p105">And that's important: if you want to remove a license from a user you must actually  *remove*  the license. Disabling all the services will prevent the user from logging on to Office 365, but it won't free up his or her license. If you want to take back a license that's currently assigned to a user you need to run a command similar to this one, a command that uses the _RemoveLicenses_ parameter to actually remove the license previously assigned to Belinda:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="389b7-142">Führen Sie diesen Befehl aus, und Belinda Newman wird nicht mehr zur Verwendung von Office 365 lizenziert.</span><span class="sxs-lookup"><span data-stu-id="389b7-142">Run that command, and Belinda Newman will no longer be licensed to use Office 365.</span></span>
  
> [!NOTE]
> <span data-ttu-id="389b7-p106">Wie Sie sehen können, wenn Sie den _RemoveLicenses_ -Parameter verwenden, den Sie den Namen der zu entfernenden Lizenz angeben müssen. Wenn Sie nicht sicher sind, welche Lizenzierungsplan verwendet wurde, um dem Benutzer nur führen Sie einen Befehl wie folgt eine Lizenz zuweisen:`Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Format-List DisplayName,Licenses`</span><span class="sxs-lookup"><span data-stu-id="389b7-p106">As you can see, when you use the  _RemoveLicenses_ parameter you need to specify the name of the license to be removed. If you aren't sure which licensing plan was used to assign a license to the user just run a command like this:  `Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Format-List DisplayName,Licenses`</span></span>
  
<span data-ttu-id="389b7-145">Um sich zu vergewissern, ob die Lizenz tatsächlich entfernt wurde, überprüfen Sie das betreffende Konto mit dem Cmdlet "Get-MsolUser":</span><span class="sxs-lookup"><span data-stu-id="389b7-145">To verify that the license really was removed, use the Get-MsolUser to check the user account in question:</span></span>
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

<span data-ttu-id="389b7-146">Wenn alles planmäßig verlaufen, Eigenschaft der Belindas **"islicensed"** wird jetzt so eingestellt werden `False`:</span><span class="sxs-lookup"><span data-stu-id="389b7-146">If everything went according to plan, Belinda's **isLicensed** property will now be set to `False`:</span></span>
  
```
UserPrincipalName            DisplayName         isLicensed
-----------------            -----------         ----------
BelindaN@litwareinc.com      Newman, Belinda     False
```

<span data-ttu-id="389b7-p107">Löschen des Benutzerkontos ist eine weitere Möglichkeit, um eine Lizenz freizugeben. Weitere Informationen finden Sie unter [Löschen und Wiederherstellen von Benutzerkonten mit Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="389b7-p107">Another way to free up a license is by deleting the user account. For more information, see [Delete and restore user accounts with Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="389b7-149">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="389b7-149">See also</span></span>

<span data-ttu-id="389b7-150">In den folgenden zusätzlichen Themen finden Sie weitere Informationen zum Verwalten von Benutzern mit Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="389b7-150">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="389b7-151">Erstellen von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="389b7-151">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="389b7-152">Löschen und Wiederherstellen von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="389b7-152">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="389b7-153">Blockieren von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="389b7-153">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="389b7-154">Zuweisen von Lizenzen zu Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="389b7-154">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="389b7-155">Weitere Informationen zu den in diesen Verfahren Thema verwendeten Cmdlets finden Sie unter den folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="389b7-155">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="389b7-156">Get-Content</span><span class="sxs-lookup"><span data-stu-id="389b7-156">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [<span data-ttu-id="389b7-157">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="389b7-157">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="389b7-158">Set-MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="389b7-158">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="389b7-159">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="389b7-159">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="389b7-160">Where-Object</span><span class="sxs-lookup"><span data-stu-id="389b7-160">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
## <a name="new-to-office-365"></a><span data-ttu-id="389b7-161">Neu bei Office 365?</span><span class="sxs-lookup"><span data-stu-id="389b7-161">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   

