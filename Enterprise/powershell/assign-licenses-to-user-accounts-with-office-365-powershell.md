---
title: Zuweisen von Lizenzen zu Benutzerkonten mit Office 365 PowerShell
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
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
description: "Erläutert, wie Office 365 PowerShell zuweisen eine Office 365-Lizenz nicht lizenzierten Benutzern."
ms.openlocfilehash: 8a7ad7b4586ccdef95430f9c4cc9c4d6e9360070
ms.sourcegitcommit: f10e47df0dca4a241659f33061db5217ebc3401e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2018
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="9a03f-103">Zuweisen von Lizenzen zu Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="9a03f-103">Assign licenses to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="9a03f-104">**Zusammenfassung:**  Erläutert, wie Office 365 PowerShell zuweisen eine Office 365-Lizenz nicht lizenzierten Benutzern.</span><span class="sxs-lookup"><span data-stu-id="9a03f-104">**Summary:**  Explains how to use Office 365 PowerShell assign an Office 365 license to unlicensed users.</span></span>
  
<span data-ttu-id="9a03f-p101">Lizenzieren von Benutzerkonten in Office 365 ist wichtig, da Benutzer keine Office 365-Dienste verwendet werden, bis ihr Konto lizenziert wurden. Office 365 PowerShell können Sie nicht lizenzierten Konten, insbesondere mehrere Konten effizient Lizenzen zuweisen.</span><span class="sxs-lookup"><span data-stu-id="9a03f-p101">Licensing user accounts in Office 365 is important, because users can't use any Office 365 services until their account has been licensed. You can use Office 365 PowerShell to efficiently assign licenses to unlicensed accounts, especially multiple accounts.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="9a03f-107">Bevor Sie beginnen:</span><span class="sxs-lookup"><span data-stu-id="9a03f-107">Before you begin</span></span>
<span data-ttu-id="9a03f-108"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="9a03f-108"></span></span>

- <span data-ttu-id="9a03f-p102">Für die Verfahren in diesem Thema müssen Sie eine Verbindung mit Office 365 PowerShell herstellen. Weitere Anweisungen finden Sie unter [Verbinden mit Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="9a03f-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="9a03f-p103">Verwenden Sie das Cmdlet " **Get-MsolAccountSku** ", um die verfügbaren lizenzierungspläne und die Anzahl der verfügbaren Lizenzen in den verschiedenen Plänen in Ihrer Organisation anzuzeigen. Die Anzahl der verfügbaren Lizenzen in den verschiedenen Plänen ist **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. Weitere Informationen zur Lizenzierung Pläne, Lizenzen und Diensten finden Sie unter [Lizenzen anzeigen und-Dienste mit Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="9a03f-p103">Use the **Get-MsolAccountSku** cmdlet to view the available licensing plans and the number of available licenses in each plan in your organization. The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. For more information about licensing plans, licenses, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="9a03f-114">Führen Sie den Befehl aus, um die nicht lizenzierten Konten in Ihrer Organisation zu suchen,`Get-MsolUser -All -UnlicensedUsersOnly`</span><span class="sxs-lookup"><span data-stu-id="9a03f-114">To find the unlicensed accounts in your organization, run the command  `Get-MsolUser -All -UnlicensedUsersOnly`</span></span>
    
- <span data-ttu-id="9a03f-p104">Sie können nur für Benutzerkonten Lizenzen zuweisen, die die **usagelocation-Wert angegeben** -Eigenschaft auf einen gültigen ISO 3166-1 Alpha-2-Ländercode festgelegt haben. Beispielsweise uns für die USA und FR für Frankreich. Einige Office 365-Dienste sind in bestimmten Ländern nicht verfügbar. Weitere Informationen finden Sie unter [About Lizenz Einschränkungen](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span><span class="sxs-lookup"><span data-stu-id="9a03f-p104">You can assign licenses only to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. Some Office 365 services aren't available in certain countries. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
    <span data-ttu-id="9a03f-p105">Führen Sie den Befehl aus, um Konten suchen, die nicht über ein **usagelocation-Wert angegeben** Wert verfügen, `Get-MsolUser -All | where {$_.UsageLocation -eq $null}`. Um den **usagelocation-Wert angegeben** Wert für ein Konto festzulegen, verwenden Sie die Syntax `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`. Beispielsweise `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`.</span><span class="sxs-lookup"><span data-stu-id="9a03f-p105">To find accounts that don't have a **UsageLocation** value, run the command `Get-MsolUser -All | where {$_.UsageLocation -eq $null}`. To set the **UsageLocation** value on an account, use the syntax `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`. For example,  `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`.</span></span>
    
- <span data-ttu-id="9a03f-122">Wenn Sie das Cmdlet **Get-MsolUser** ohne Verwenden der `-All` -Parameter, die nur die ersten 500 Benutzerkonten zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="9a03f-122">If you use the **Get-MsolUser** cmdlet without using the `-All` parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="9a03f-123">Die Kurzfassung (Anweisungen ohne Erläuterungen)</span><span class="sxs-lookup"><span data-stu-id="9a03f-123">The short version (instructions without explanations)</span></span>
<span data-ttu-id="9a03f-124"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="9a03f-124"></span></span>

<span data-ttu-id="9a03f-p106">In diesem Abschnitt werden die Verfahren ohne ausführliche Erläuterung. Wenn Sie Fragen haben oder Weitere Informationen wünschen, können Sie den Rest des Themas lesen.</span><span class="sxs-lookup"><span data-stu-id="9a03f-p106">This section presents the procedures without detailed explanation. If you have questions or want more information, you can read rest of the topic.</span></span>
  
<span data-ttu-id="9a03f-127">Wenn Sie einem Benutzer eine Lizenz zuweisen möchten, verwenden Sie die folgende Syntax in Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="9a03f-127">To assign a license to a user, use the following syntax in Office 365 PowerShell:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="9a03f-128">In diesem Beispiel wird eine Lizenz aus der `litwareinc:ENTERPRISEPACK` Lizenzierungsplan (Office 365 Enterprise E3) für den nicht lizenzierten Benutzer `belindan@litwareinc.com`.</span><span class="sxs-lookup"><span data-stu-id="9a03f-128">This example assigns a license from the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan to the unlicensed user `belindan@litwareinc.com`.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="9a03f-129">Wenn Sie mehreren nicht lizenzierten Benutzern eine Lizenz zuweisen möchten, verwenden Sie die folgende Syntax:</span><span class="sxs-lookup"><span data-stu-id="9a03f-129">To assign a license to many unlicensed users, use the following syntax:</span></span>
  
```
$x = Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>]; $x | foreach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```

 <span data-ttu-id="9a03f-130">**Notizen**</span><span class="sxs-lookup"><span data-stu-id="9a03f-130">**Notes**</span></span>
  
- <span data-ttu-id="9a03f-131">Sie können einem Benutzer nicht mehrere Lizenzen aus dem gleichen Lizenzierungsplan zuweisen.</span><span class="sxs-lookup"><span data-stu-id="9a03f-131">You can't assign multiple licenses to a user from the same licensing plan.</span></span>
    
- <span data-ttu-id="9a03f-132">Wenn Sie nicht über genügend verfügbaren Lizenzen verfügen, werden die Lizenzen für Benutzer in der Reihenfolge zugewiesen, die sie vom Cmdlet **Get-MsolUser** zurückgegeben werden, bis die verfügbaren Lizenzen Neige zur.</span><span class="sxs-lookup"><span data-stu-id="9a03f-132">If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
    
<span data-ttu-id="9a03f-133">In diesem Beispiel wird die Lizenzen aus der `litwareinc:ENTERPRISEPACK` Lizenzierungsplan (Office 365 Enterprise E3) für alle nicht lizenzierten Benutzer.</span><span class="sxs-lookup"><span data-stu-id="9a03f-133">This example assigns licenses from the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan to all unlicensed users.</span></span>
  
```
$AllUn = Get-MsolUser -All -UnlicensedUsersOnly; $AllUn | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

<span data-ttu-id="9a03f-134">In diesem Beispiel werden dieselben Lizenzen den nicht lizenzierten Benutzern in der Vertriebsabteilung in den USA zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="9a03f-134">This example assigns those same licenses to unlicensed users in the Sales department in the United States.</span></span>
  
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly; $USSales | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="9a03f-135">Die Langfassung (Anweisungen mit detaillierten Erläuterungen)</span><span class="sxs-lookup"><span data-stu-id="9a03f-135">The long version (instructions with detailed explanations)</span></span>
<span data-ttu-id="9a03f-136"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="9a03f-136"></span></span>

<span data-ttu-id="9a03f-p107">Wie im Artikel [lizenzierte und nicht lizenzierten Benutzer mit Office 365 PowerShell anzeigen](view-licensed-and-unlicensed-users-with-office-365-powershell.md)bereits erwähnt, ist es möglich, dass Benutzer über gültige Office 365-Benutzerkonten verfügen, aber wer haben keine Office 365-Lizenz ausgestellt. Das bedeutet, dass gültiges Konto oder kein gültiges Konto, die Benutzer nicht bei Office 365 anmelden können. Und wenn Sie sich nicht anmelden können, Sie können nicht nutzen aller Office 365-Dienste.</span><span class="sxs-lookup"><span data-stu-id="9a03f-p107">As noted in the article [View licensed and unlicensed users with Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md), it's possible to have users who have valid Office 365 user accounts, but who have not been issued an Office 365 license. That means that, valid account or no valid account, those users will not be able to log on to Office 365. And if you can't log on, you can't take advantage of any Office 365 services.</span></span>
  
<span data-ttu-id="9a03f-140">Im genannten Artikel wird auch darauf hingewiesen, dass mit dem folgenden Befehl eine Liste nicht lizenzierter Benutzerkonten zurückgegeben werden kann:</span><span class="sxs-lookup"><span data-stu-id="9a03f-140">The aforementioned article also noted that we can return a list of unlicensed user accounts by running this command:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="9a03f-141">Dieser Befehl gibt Informationen über alle Benutzer, die derzeit nicht für Office 365 lizenziert sind:</span><span class="sxs-lookup"><span data-stu-id="9a03f-141">That command returns information about any users who are not currently licensed for Office 365:</span></span>
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  False
```

<span data-ttu-id="9a03f-p108">Wie Sie sehen können, haben wir einen nicht lizenzierten Benutzer: Belinda Newman. Wie gehen wir zum Zuweisen von Belinda einer Office 365-Lizenzvertrags?</span><span class="sxs-lookup"><span data-stu-id="9a03f-p108">As you can see, we have one unlicensed user: Belinda Newman. So how do we go about assigning Belinda an Office 365 license?</span></span>
  
<span data-ttu-id="9a03f-144">Zunächst einmal werden wir das Cmdlet " **Get-MsolAccountSku** " im Artikel [Lizenzen anzeigen und-Dienste mit Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md)beschriebene ausführen:</span><span class="sxs-lookup"><span data-stu-id="9a03f-144">For starters, we're going to run the **Get-MsolAccountSku** cmdlet discussed in the article [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md):</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="9a03f-145">Dieser Befehl gibt Daten wie diese zurück:</span><span class="sxs-lookup"><span data-stu-id="9a03f-145">That command returns data similar to this:</span></span>
  
```
AccountSkuId               ActiveUnits    WarningUnits   ConsumedUnits
------------               -----------    ------------   -------------
litwareinc:ENTERPRISEPACK  25             0              24
```

<span data-ttu-id="9a03f-p109">Warum ausführen wir **Get-MsolAccountSku** ? ("Sku", für den Fall, dass Sie wissen möchten, ist kurz für "SKU." Für unsere Zwecke, die gerade Business sprechen ist-für "Produkt".) Es gibt zwei Gründe, warum es **Get-MsolAccountSku**ausgeführt wurde. Zunächst müssen wir stellen Sie sicher, dass wir tatsächlich eine Lizenz zuweisen Belinda haben. Haben wir keinerlei Lizenzen, die wir ihr zuweisen können? So bestimmen Sie, dass wir nehmen Sie den Wert der **ActiveUnits** -Eigenschaft (25) und die Werte der **WarningUnits** (0) und Eigenschaften **ConsumedUnits** (24 subtrahiert):</span><span class="sxs-lookup"><span data-stu-id="9a03f-p109">Why did we run **Get-MsolAccountSku** ? ("Sku," in case you're wondering, is short for "stock-keeping unit." For our purposes, that's just business-speak for "product.") There are two reasons why we ran **Get-MsolAccountSku**. First, we need to make sure we actually have a license to assign Belinda. Do we have any licenses we can assign her? To determine that, we take the value of **ActiveUnits** property (25) and subtract the values of the **WarningUnits** (0) and **ConsumedUnits** (24) properties:</span></span>
  
 `25 - 0 - 24 = 1`
  
<span data-ttu-id="9a03f-p110">Die **ActiveUnits** -Eigenschaft gibt an, wie viele Lizenzen wir erworben haben, und der kombinierte Wert **WarningUnits** und **ConsumedUnits** gibt an, wie viele Lizenzen gerade verwendet werden. Wenn wir die Anzahl der Lizenzen, die bereits subtrahiert für gesprochen, von der Anzahl der Lizenzen, die wir erworben haben, wissen wir, wie viele Lizenzen noch verfügbar sind. Wie Glück sie besitzen, haben wir eine Lizenz für den Vertrieb verfügbar:</span><span class="sxs-lookup"><span data-stu-id="9a03f-p110">The **ActiveUnits** property tells us how many licenses we've purchased, and the combined value of **WarningUnits** and **ConsumedUnits** tells us how many licenses are currently in use. If we subtract the number of licenses already spoken for from the number of licenses we purchased, we'll know how many licenses are still available. As luck would have it, we have one license available for distribution:</span></span>
  
 `25 - 0 - 24 = 1`
  
<span data-ttu-id="9a03f-p111">Zweitens, um Belinda eine neue Lizenz zuweisen wir wissen den Namen des unsere Lizenzierungsplan müssen (d. h., müssen wir die **AccountSkuId** wissen). In diesem Fall ist, die einfach: Wir haben nur eine einzelne Lizenzierungsplan ( `litwareinc:ENTERPRISEPACK`). Beachten Sie jedoch, dass es für eine Organisation mehrere lizenzierungspläne möglich ist. In diesem Fall würde **Get-MsolAccountSku** zwei unterschiedliche **AccountSkuIds**zurückgeben, und müssen Sie den richtigen Lizenzierungsplan wählen Sie bei der Zuweisung von Lizenzen. Jetzt werden jedoch wir einfachsten Fall festgelegt, und davon ausgegangen, dass wir nur einen Lizenzierungsplan haben.</span><span class="sxs-lookup"><span data-stu-id="9a03f-p111">Second, in order to assign Belinda a new license we need to know the name of our licensing plan (that is, we need to know the **AccountSkuId** ). In this case, that's easy: we only have a single licensing plan ( `litwareinc:ENTERPRISEPACK`). Note, however, that it's possible for an organization to have multiple licensing plans. In that case, **Get-MsolAccountSku** would return two different **AccountSkuIds**, and you would need to pick the appropriate licensing plan when assigning licenses. For now, though, we're going to stick with the simplest case, and assume we have just one licensing plan.</span></span>
  
<span data-ttu-id="9a03f-p112">*Klicken Sie dann so wie wir Belinda Newman eine neue Lizenz zuweisen?* So:</span><span class="sxs-lookup"><span data-stu-id="9a03f-p112">So then how  *do*  we assign Belinda Newman a new license? Like this:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "BelindaN@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="9a03f-162">Ist Sie Schritte: Rufen Sie einfach das **Set-MsolUserLicense** -Cmdlet, um sicherzustellen, dass Sie den Parameter _UserPrincipalName_ für den Benutzer und den richtigen Lizenzierungsplan angeben.</span><span class="sxs-lookup"><span data-stu-id="9a03f-162">That's also you have to do: just call the **Set-MsolUserLicense** cmdlet, making sure that you specify the _UserPrincipalName_ parameter for the user and the appropriate licensing plan.</span></span>
  
<span data-ttu-id="9a03f-163">Wenn **Set-MsolUserLicense** abgeschlossen ist, wird etwa Folgendes sehen Sie auf dem Bildschirm angezeigt:</span><span class="sxs-lookup"><span data-stu-id="9a03f-163">When **Set-MsolUserLicense** finishes running, you'll see something similar to this onscreen:</span></span>
  
 `PS C:\\windows\\system32>`
  
<span data-ttu-id="9a03f-p113">Es wird nicht mit anderen Worten, aussehen wie etwas geschehen ist. Zum bestätigen, dass der Benutzer eine Lizenz zugewiesen wurde, führen Sie einen Befehl ähnlich dem folgenden:</span><span class="sxs-lookup"><span data-stu-id="9a03f-p113">In other words, it won't look like anything has happened. To verify that the user has been assigned a license, run a command like the following:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.com"
```

<span data-ttu-id="9a03f-166">Wenn alles erwartungsgemäß funktioniert, sollten Sie sehen, dass die Eigenschaft von Belindas "islicensed" nun auf True festgelegt ist:</span><span class="sxs-lookup"><span data-stu-id="9a03f-166">If everything worked as expected, you should see that Belinda's isLicensed property is now set to True:</span></span>
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  True
```

> [! Sicherheitshinweis]<span data-ttu-id="9a03f-p114"> gute Frage: Was passiert, wenn ein Fehler aufgetreten und haben versucht, einem Benutzer eine Lizenz zuweisen, die bereits über eine Lizenz verfügt? Erhalten Sie zwei Lizenzen zu einem einzelnen Benutzer erteilen? > Die schnelle Antwort? No; Office 365 wird nicht mehr als eine Lizenz für den gleichen Benutzer zuweisen kann. (Das ist sicherlich mehr als eine Lizenz aus den gleichen Lizenzierungsplan,.) Wenn Sie versuchen, das Ihre Befehl schlägt fehl, wobei die folgende Fehlermeldung angezeigt: > `Set-MsolUserLicense : Unable to assign this license because it is invalid. Use the Get-MsolAccountSku cmdlet to retrieve a list of valid licenses.`> zugegebenermaßen, wird diese Fehlermeldung geringfügig irreführende: die Lizenz nicht wirklich ungültig ist, wird nur zu einem Benutzer zugewiesen wird, die bereits *verfügt über* eine Lizenz. Aber reserviert, Fehlermeldung wichtig ist, dass ein Benutzer mit mehreren Lizenzen landen wird nicht.</span><span class="sxs-lookup"><span data-stu-id="9a03f-p114"> Good question: what if you made a mistake and tried to assign a license to a user who already has a license? Will you end up giving two licenses to a single user? > The quick answer? No; Office 365 won't let you assign more than one license to the same user. (Well, more than one license from the same licensing plan, that is.) If you try to do that your command will fail with the following error message: >  `Set-MsolUserLicense : Unable to assign this license because it is invalid. Use the Get-MsolAccountSku cmdlet to retrieve a list of valid licenses.`> Admittedly, that error message is a tiny bit misleading: the license isn't really invalid, it's just being assigned to a user who already  *has*  a license. But, error message aside, the important thing is that one user won't end up with multiple licenses.</span></span>
  
<span data-ttu-id="9a03f-p115">Wie Sie gerade gesehen haben, ist es sehr einfach zu verwendenden Office 365 PowerShell einen einzelnen Benutzer eine Lizenz zugewiesen. Führt zu einer offensichtlichen Frage: wäre es nicht genauso einfach, vielleicht sogar noch einfacher, um das Office 365 Administrationscenter verwenden, um einen einzelnen Benutzer eine Lizenz zugewiesen? Nun, vielleicht; Dies hängt, teilweise gibt an, ob Sie besser damit vertraut, mithilfe von Windows PowerShell oder komfortabler im Office 365 Admin Center sind. In der Windows PowerShell das beste, ist jedoch, wenn Sie mehrere Lizenzen für mehrere Benutzer zuweisen möchten. Mit diesem Befehl weist beispielsweise eine Office 365-Lizenz zu einer der Benutzer, die nicht bereits über eine Lizenz verfügen:</span><span class="sxs-lookup"><span data-stu-id="9a03f-p115">As you've just seen, it's very easy to use Office 365 PowerShell to assign a single license to a single user. And that leads to an obvious question: wouldn't it be just as easy, maybe even easier, to use the Office 365 admin center to assign a single license to a single user? Well, maybe; that depends, in part, on whether you're more comfortable using Windows PowerShell or more comfortable using the Office 365 admin center. Where Windows PowerShell really shines, however, is when you need to assign multiple licenses to multiple users. For example, this command assigns an Office 365 license to any of your users that don't already have a license:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="9a03f-p116">Im vorstehenden Befehl verwenden wir **Get-MsolUser** und der _UnlicensedUsersOnly_ -Parameter, um eine Auflistung aller nicht lizenzierter Benutzerkonten zurückzugeben. Wir übergeben dieser Auflistung dann an das Cmdlet **Set-MsolUserLicense** ; **Set-MsolUserLicense** weist wiederum eine Lizenz (übernommen aus der `litwareinc:ENTERPRISEPACK` Lizenzierungsplan) für jeden Benutzer in der Auflistung.</span><span class="sxs-lookup"><span data-stu-id="9a03f-p116">In the preceding command, we use **Get-MsolUser** and the _UnlicensedUsersOnly_ parameter to return a collection of all the unlicensed user accounts. We then pass that collection to the **Set-MsolUserLicense** cmdlet; in turn, **Set-MsolUserLicense** assigns a license (taken from the `litwareinc:ENTERPRISEPACK` licensing plan) to each user in the collection.</span></span>
  
<span data-ttu-id="9a03f-p117">AH, aber was passiert, wenn haben Sie 5 nicht lizenzierten Benutzer jedoch nur eine Lizenz verfügbar? In diesem Fall erhalten **Set-MsolUserLicense** verfügbare Lizenz für dem ersten Benutzer, die von **Get-MsolUser**zurückgegeben. **Set-MsolUserLicense** wird dann verlässliche versucht, die anderen vier Benutzer eine Lizenz zuweisen, aber alle vier dieser Versuche fehl und die folgende Fehlermeldung angezeigt:</span><span class="sxs-lookup"><span data-stu-id="9a03f-p117">Ah, but what if you have 5 unlicensed users but only one available license? In that case **Set-MsolUserLicense** will give the available license to the first user returned by **Get-MsolUser**. **Set-MsolUserLicense** will then dutifully try to assign a license to the other four users, but all four of those attempts will fail along with the following error message:</span></span>
  
 `Set-MsolUserLicense : Unable to assign this license because the number of allowed licenses have been assigned.`
  
<span data-ttu-id="9a03f-p118">Set-MsolUserLicense wird nicht mit anderen Worten, fehl. Stattdessen weisen sie, wie viele Lizenzen wie möglich. Nur dann fehl.</span><span class="sxs-lookup"><span data-stu-id="9a03f-p118">In other words, Set-MsolUserLicense won't just fail. Instead, it will assign as many licenses as it can. Only then will it fail.</span></span>
  
<span data-ttu-id="9a03f-p119">Versuchen Sie ein weiteres Beispiel an. Vielleicht möchten Sie alle Benutzer in der Abteilung Sales eine Lizenz zuweisen. Kein Problem:</span><span class="sxs-lookup"><span data-stu-id="9a03f-p119">Let's try another example. Maybe you'd like to assign a license to all the users in the Sales department. No problem:</span></span>
  
```
Get-MsolUser -All -Department "Sales" | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="9a03f-189">Oder wenn Sie wirklich raffiniert sein und Fehlermeldungen sowie die Verarbeitungslast auf dem Rechner auf einem Minimum halten möchten, weisen Sie einfach den nicht lizenzierten Benutzern aus der Sales-Abteilung eine Lizenz zu:</span><span class="sxs-lookup"><span data-stu-id="9a03f-189">Or, if you want to get really fancy, and if you want to keep error messages and computing processing to a minimum, just assigned a license to unlicensed users from the Sales department:</span></span>
  
```
Get-MsolUser -All -Department "Sales" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="9a03f-p120">Nachdem alle besteht keine Points Lizenzbenutzer, die bereits über eine Lizenz verfügen möchten. Wie bereits erwähnt, ist nicht möglich.</span><span class="sxs-lookup"><span data-stu-id="9a03f-p120">After all, there's no point trying to license users who already have a license. As we've already seen, that won't work.</span></span>
  
<span data-ttu-id="9a03f-p121">Hier ist ein weiteres Beispiel. Vielleicht möchten Sie alle Benutzer der USA lizenzieren, die derzeit nicht über ein Office 365-Lizenz verfügen. In diesem Fall:</span><span class="sxs-lookup"><span data-stu-id="9a03f-p121">Here's another example. Maybe you'd like to license all the US users who don't currently have an Office 365 license. In that case:</span></span>
  
```
Get-MsolUser -All -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="9a03f-195">Und so weiter und so weiter.</span><span class="sxs-lookup"><span data-stu-id="9a03f-195">And so on and so on.</span></span>
  
> [!NOTE]
> <span data-ttu-id="9a03f-p122">Wie lange dauert es, einen Befehl auszuführen, der für alle nicht lizenzierten Benutzer sagen, Lizenzen ausgibt? Das ist schwierig zu sagen: das hängt alles von der Anzahl der Benutzer die Geschwindigkeit der Verbindung zum Netzwerk muss. Wenn Sie ein paar Hundert Benutzern-Lizenz verfügen, dadurch Sie nach vernünftigem Ermessen schnell gelangen wird (d. h., sollte nicht dauert länger als ein oder zwei Minuten). Wenn Sie haben werden 10.000 Benutzer um die Lizenz zu offensichtlich etwas länger dauern. Aber nicht in der Nähe so lange dauert 10.000 Benutzern Lizenzen zuweisen, indem Sie im Office 365 Admin Center.</span><span class="sxs-lookup"><span data-stu-id="9a03f-p122">How long does it take to run a command that, say, issues licenses to all your unlicensed users? That's difficult to say: it depends on everything from the number of users you have to the speed of your network connection. If you have a couple hundred users to license this will go reasonably quickly (that is, it shouldn't take more than a minute or two). If you have 10,000 users to license it will obviously take a little longer. But nowhere near as long as it would take to assign licenses to 10,000 users by using the Office 365 admin center.</span></span> 
  
<span data-ttu-id="9a03f-p123">Als wir zu diesem Thema sind, sollten Sie sich für Achten Sie beim Zuweisen von Lizenzen Sie müssen: Wenn ein Benutzer keinen Wert für die Eigenschaft **usagelocation-Wert angegeben** konfiguriert nicht möglich, die diesem Benutzer eine Office 365-Lizenz zuweisen. Stattdessen erhalten eine Fehlermeldung wie die folgende Sie:</span><span class="sxs-lookup"><span data-stu-id="9a03f-p123">As long as we're on the subject, here's something you need to watch out for when assigning licenses: if a user does not have a value configured for the **UsageLocation** property you won't be able to assign that user an Office 365 license. Instead, you'll get an error message similar to this:</span></span>
  
 `Set-MsolUserLicense : You must provide a required property: Parameter name: UsageLocation`
  
<span data-ttu-id="9a03f-p124">Etwas Kreisverkehrs verwenden weist diese Fehlermeldung uns, dass der betreffende Benutzer ein **usagelocation-Wert angegeben**nicht zugewiesen wurde. Wie Sie vielleicht, ist die **usagelocation-Wert angegeben** -Eigenschaft (die gibt an, die Region oder jedes Land, in dem der Benutzer in der Regel Office 365 verwendet) äußerst wichtig. Warum? Dies liegt daran die für einen Benutzer verfügbaren Dienste nicht nur lizenzierungspakets abhängen, das Sie aber auch auf, in dem der Benutzer befindet sich erworben haben: aufgrund von lokalen Richtlinien und Vorschriften, einige Dienste möglicherweise nicht für einige Benutzer verfügbar. Wenn ein Benutzer ein **usagelocation-Wert angegeben**hat, kann Office 365 nicht wissen, welche Dienste rechtskräftig für diesen Benutzer verfügbar gemacht werden können. Daher Office 365 kann nicht bieten keine Dienste, die diesem Benutzer mindestens nicht, bis der **usagelocation-Wert angegeben** angegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="9a03f-p124">In somewhat-roundabout fashion, this error message tells us that the user in question has not been assigned a **UsageLocation**. As you might have guessed, the **UsageLocation** property (which indicates the region or country where the user typically uses Office 365) is extremely important. Why? That's because the services available to a user depend not only on the licensing pack that you purchased but also on where the user lives: due to local rules and regulations, some services might not be available to some users. If a user doesn't have a **UsageLocation**, Office 365 has no way of knowing which services can legally be exposed to that user. Therefore, Office 365 can't offer any services to that user, at least not until the **UsageLocation** has been specified.</span></span>
  
> [!NOTE]
> <span data-ttu-id="9a03f-p125">Wenn Sie ein Benutzerkonto konfigurieren wissen Sie sofort Wenn Lizenz Einschränkungen den angegebenen Teil der ganzen Welt zugeordnet sind. Beispielsweise, wenn Sie die **usagelocation-Wert angegeben** für einen lizenzierten Benutzer Iran ändern ( `IR`), der Befehl schlägt fehl, mit dieser Fehlermeldung: `Set-MsolUser : Unable to update license for this user. One or more of the assigned service plans is not available in this user's country. Prohibited Service Plans: EXCHANGE_S_ENTERPRISE, SHAREPOINTENTERPRISE, SHAREPOINTWAC, MCOSTANDARD, OFFICESUBSCRIPTION, RMS_S_ENTERPRISE. Specific service plans can be disabled for a user by using the licenseoptions parameter.`> Dies liegt daran Office 365 nicht für Benutzer im Iran derzeit verfügbar ist. Weitere Informationen finden Sie unter [About Lizenz Einschränkungen](https://go.microsoft.com/fwlink/p/?LinkId=691730). Office 365 wird zum, die zwei Buchstaben Ländercodes erzeugt, von der International Organization for Standardization (ISO) verwendet. Diese Codes finden Sie auf der [ISO-Website](https://go.microsoft.com/fwlink/p/?LinkId=84073).</span><span class="sxs-lookup"><span data-stu-id="9a03f-p125">When you configure a user account you'll know immediately if there are any license restrictions associated with the specified part of the world. For example, if you change the **UsageLocation** for a licensed user to Iran ( `IR`), the command will fail with this error message: `Set-MsolUser : Unable to update license for this user. One or more of the assigned service plans is not available in this user's country. Prohibited Service Plans: EXCHANGE_S_ENTERPRISE, SHAREPOINTENTERPRISE, SHAREPOINTWAC, MCOSTANDARD, OFFICESUBSCRIPTION, RMS_S_ENTERPRISE. Specific service plans can be disabled for a user by using the licenseoptions parameter.`> That's because Office 365 is not currently available to users in Iran. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730). Incidentally, Office 365 uses the two-letter country codes produced by the International Organization for Standardization (ISO). You can find those codes on the [ISO web site](https://go.microsoft.com/fwlink/p/?LinkId=84073).</span></span> 
  
<span data-ttu-id="9a03f-214">Wenn Sie überprüfen möchten besteht aus ein bestimmten Benutzer ein **usagelocation-Wert angegeben** , können Sie einen Befehl wie den folgenden verwenden:</span><span class="sxs-lookup"><span data-stu-id="9a03f-214">If you want to verify that a given user has a **UsageLocation** you can use a command similar to this one:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.com" | Select-Object UsageLocation
```

<span data-ttu-id="9a03f-215">Alternativ können Sie eine Liste aller Benutzer zurückgegeben, die nicht mit dem folgenden Befehl ein **usagelocation-Wert angegeben** haben:</span><span class="sxs-lookup"><span data-stu-id="9a03f-215">Alternatively, you can return a list of all the users who don't have a **UsageLocation** by using this command:</span></span>
  
```
Get-MsolUser -All | Where-Object {$_.UsageLocation -eq $null}
```

> [!NOTE]
> <span data-ttu-id="9a03f-p126">Wenn Sie einer Lizenz für einen Benutzer diesen Benutzer zuweisen, wird standardmäßig Zugriff auf alle Office 365-Dienste erhalten, die über Zugriff auf Ihre Organisation verfügt. Angenommen, wenn Sie Lizenzen für Office 365 Enterprise E3 erworben haben, wird Ihre neu lizenzierten Benutzer automatisch Zugriff auf Dienste wie Exchange Online, Skype für Business Online und SharePoint Online erteilt werden. Wenn Sie ein Benutzer Zugriff auf diese Dienste beschränken möchten (beispielsweise sollten Sie einen Benutzer den Zugriff auf SharePoint Online, wird jedoch *nicht* zu Exchange Online und Skype für Business Online) dann finden Sie im Artikel [Disable-Zugriff auf Dienste mit Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="9a03f-p126">When you assign a license to a user that user will, by default, be given access to all the Office 365 services that your organization has access to. For example, if you purchased licenses for Office 365 Enterprise E3, your newly-licensed user will automatically be granted access to services like Exchange Online, Skype for Business Online, and SharePoint Online. If you would prefer to limit a user's access to those services (for example, you might want a user to have access to SharePoint Online but  *not*  to Exchange Online and Skype for Business Online) then see the article [Disable access to services with Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md).</span></span> 
  
## <a name="new-to-office-365"></a><span data-ttu-id="9a03f-219">Neu bei Office 365?</span><span class="sxs-lookup"><span data-stu-id="9a03f-219">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="9a03f-220">Weitere Artikel</span><span class="sxs-lookup"><span data-stu-id="9a03f-220">See Also</span></span>
<span data-ttu-id="9a03f-221"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="9a03f-221"></span></span>

<span data-ttu-id="9a03f-222">In den folgenden zusätzlichen Themen finden Sie weitere Informationen zum Verwalten von Benutzern mit Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="9a03f-222">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="9a03f-223">Erstellen von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="9a03f-223">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="9a03f-224">Löschen und Wiederherstellen von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="9a03f-224">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="9a03f-225">Blockieren von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="9a03f-225">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="9a03f-226">Entfernen von Lizenzen von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="9a03f-226">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="9a03f-227">Weitere Informationen zu den in diesen Verfahren Thema verwendeten Cmdlets finden Sie unter den folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="9a03f-227">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="9a03f-228">Get-MsolAccountSku</span><span class="sxs-lookup"><span data-stu-id="9a03f-228">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [<span data-ttu-id="9a03f-229">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="9a03f-229">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="9a03f-230">Set-MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="9a03f-230">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="9a03f-231">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="9a03f-231">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="9a03f-232">Select-Object</span><span class="sxs-lookup"><span data-stu-id="9a03f-232">Select-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [<span data-ttu-id="9a03f-233">Where-Object</span><span class="sxs-lookup"><span data-stu-id="9a03f-233">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

