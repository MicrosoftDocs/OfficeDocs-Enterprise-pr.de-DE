---
title: Anzeigen lizenzierter und nicht lizenzierter Benutzer mit Office 365 PowerShell
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
- O365ITProTrain
- Ent_Office_Other
- DecEntMigration
- PowerShell
ms.assetid: e4ee53ed-ed36-4993-89f4-5bec11031435
description: "Erläutert das Verwenden von Office 365 PowerShell zum Anzeigen von lizenzierten und nicht lizenzierten Benutzerkonten."
ms.openlocfilehash: aa8c38864f3abf98f1aa5c8149db08506c6f7668
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2017
---
# <a name="view-licensed-and-unlicensed-users-with-office-365-powershell"></a><span data-ttu-id="d97ce-103">Anzeigen lizenzierter und nicht lizenzierter Benutzer mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d97ce-103">View licensed and unlicensed users with Office 365 PowerShell</span></span>

<span data-ttu-id="d97ce-104">**Zusammenfassung:** Erläutert das Verwenden von Office 365 PowerShell zum Anzeigen von lizenzierten und nicht lizenzierten Benutzerkonten.</span><span class="sxs-lookup"><span data-stu-id="d97ce-104">Explains how to use Office 365 PowerShell to view licensed and unlicensed user accounts.</span></span>
  
<span data-ttu-id="d97ce-p101">Benutzerkonten in Ihrer Office 365-Organisation sind möglicherweise einige, alle oder keine der verfügbaren Lizenzen aus den Lizenzierungsplänen zugewiesen, die in Ihrer Organisation verfügbar sind. Mit Office 365 PowerShell können Sie lizenzierte und nicht lizenzierte Benutzer in Ihrer Organisation schnell finden.</span><span class="sxs-lookup"><span data-stu-id="d97ce-p101">User accounts in your Office 365 organization may have some, all, or none of the available licenses assigned to them from the licensing plans that are available in your organization. You can use Office 365 PowerShell to quickly find the licensed and unlicensed users in your organization.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="d97ce-107">Bevor Sie beginnen:</span><span class="sxs-lookup"><span data-stu-id="d97ce-107">Before you begin</span></span>

- <span data-ttu-id="d97ce-p102">Für die Verfahren in diesem Thema müssen Sie eine Verbindung mit Office 365 PowerShell herstellen. Weitere Anweisungen finden Sie unter [Verbinden mit Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="d97ce-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="d97ce-110">Bei Verwendung des **Get-MsolUser**-Cmdlets ohne den _-All_-Parameter werden nur die ersten 500 Konten zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="d97ce-110">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="d97ce-111">Die Kurzfassung (Anweisungen ohne Erläuterungen)</span><span class="sxs-lookup"><span data-stu-id="d97ce-111">The short version (instructions without explanations)</span></span>

<span data-ttu-id="d97ce-p103">In diesem Abschnitt werden die Verfahren kurz und bündig erläutert. Wenn Sie Fragen haben oder weitere Informationen benötigen, können Sie den Rest des Themas lesen.</span><span class="sxs-lookup"><span data-stu-id="d97ce-p103">This section presents the procedures without fanfare or superfluous explanation. If you have questions or want more information, you can read rest of the topic.</span></span>
  
<span data-ttu-id="d97ce-114">Führen Sie den folgenden Befehl in Office 365 PowerShell aus, um die Liste aller Benutzerkonten mit ihrem Lizenzierungsstatus in Ihrer Organisation anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="d97ce-114">To view the list of all user accounts and their licensing status in your organization, run the following command in Office 365 PowerShell:</span></span>
  
```
Get-MsolUser -All
```

<span data-ttu-id="d97ce-115">Führen Sie den folgenden Befehl aus, um die Liste aller nicht lizenzierten Benutzerkonten in Ihrer Organisation anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="d97ce-115">To view the list of all unlicensed user accounts in your organization, run the following command:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="d97ce-116">Führen Sie den folgenden Befehl aus, um die Liste aller lizenzierten Benutzerkonten in Ihrer Organisation anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="d97ce-116">To view the list of all licensed user accounts in your organization, run the following command:</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="d97ce-117">Die Langfassung (Anweisungen mit detaillierten Erläuterungen)</span><span class="sxs-lookup"><span data-stu-id="d97ce-117">The long version (instructions with detailed explanations)</span></span>

<span data-ttu-id="d97ce-p104">Office 365-Benutzerkonten und Office 365-Lizenzen müssen sich nicht eins zu eins entsprechen: Es ist möglich, Office 365-Benutzer ohne Office 365-Lizenz zu haben, und ebenso können Sie Office 365-Lizenzen haben, die keinem Benutzer zugewiesen wurden. (Tatsächlich kann ein einzelnes Benutzerkonto sogar über *mehrere* Office 365-Lizenzen verfügen.) Wenn Sie ein neues Office 365-Benutzerkonto erstellen (wie im Artikel[Lizenzieren von Office 365-Benutzern mit Windows PowerShell]((http://technet.microsoft.com/library/0ab9fcac-e5ea-4b5b-b72c-8c92c55565ac.aspx)) beschrieben), müssen Sie dem Benutzer keine Lizenz zuweisen: Der neue Benutzer hat dann ein gültiges Konto, kann sich aber nicht bei Office 365 anmelden. Wenn er versucht sich anzumelden, wird in etwa Folgendes angezeigt:</span><span class="sxs-lookup"><span data-stu-id="d97ce-p104">Office 365 user accounts and Office 365 licenses don't need to have a one-to-one correspondence: it's possible to have Office 365 users who do not have an Office 365 license, and it's possible to have Office 365 licenses that haven't been assigned to a user. (In fact, a single user account can even have  *multiple*  Office 365 licenses.) When you create a new Office 365 user account (see the article[License Office 365 users with Windows PowerShell]((http://technet.microsoft.com/library/0ab9fcac-e5ea-4b5b-b72c-8c92c55565ac.aspx)) for more information) you don't have to assign that user a license: the new user will have a valid account, but he or she won't be able to sign in to Office 365. If they try to sign in, they'll see something similar to this:</span></span>
  
![Benutzer ohne gültige Office 365-Lizenz.](images/o365_powershell_no_license.png)
  
<span data-ttu-id="d97ce-p105">Ebenso können Sie einen Benutzer haben, der sich längere Zeit frei nimmt, beispielsweise für ein Sabbatjahr oder die Elternzeit. In einem solchen Fall könnten Sie die Lizenz des Benutzers entfernen, das Benutzerkonto aber intakt lassen (das heißt, alle Eigenschaftswerte wie Adresse und Telefonnummer beibehalten). So können Sie dessen Lizenz einem anderen Benutzer zuweisen (beispielsweise dem temporären Mitarbeiter, der die Aufgaben des abwesenden Mitarbeiters übernimmt). Wenn der Benutzer an seinen Arbeitsplatz zurückkehrt, können Sie ihm eine neue Lizenz ausstellen, und dann kann er seine Arbeit wieder aufnehmen, als wäre er nie fort gewesen.</span><span class="sxs-lookup"><span data-stu-id="d97ce-p105">Likewise, you might have a user who will be taking some extended time off, perhaps for a sabbatical or for maternity/paternity leave. In a case like that, you could remove the user's license but leave the user account intact (that is, leave all its property values, such as address and phone number, as-is). By doing that, you can assign their license to someone else (like, say, a temporary worker filling in for the person on leave). When the user returns to work you can issue them a new license and they'll be able to resume working as if they'd never been gone.</span></span>
  
<span data-ttu-id="d97ce-p106">Was einfach bedeutet, ja, Sie können Benutzer haben, die über ein Konto verfügen, aber keine Lizenzen haben. Oder umgekehrt.</span><span class="sxs-lookup"><span data-stu-id="d97ce-p106">Which simply means that, yes, you can have users who have accounts but who don't have licenses. Or vice-versa.</span></span>
  
<span data-ttu-id="d97ce-p107">Im Artikel [Anzeigen von Lizenzen und Diensten mit Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md) wird erklärt, wie Sie feststellen können, wie viele Office 365-Lizenzen Ihre Organisation erworben hat und wie viele dieser Lizenzen Benutzern zugewiesen wurden. Dies sind wichtige Informationen. Genauso wichtig ist es jedoch, zu wissen, welchen Benutzern diese Lizenzen zugewiesen wurden. In diesem Artikel erfahren Sie, wie Sie genau das herausfinden.</span><span class="sxs-lookup"><span data-stu-id="d97ce-p107">The article [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md) explains how you can determine the number of Office 365 licenses your organization has purchased as well as how many of those licenses have been assigned to users. That's important information. Equally important, however is knowing which of your users have been assigned these licenses and which ones haven't. And this article will tell you how to do just that.</span></span>
  
<span data-ttu-id="d97ce-p108">Wie Sie vielleicht wissen, gibt das **Get-MsolUser** -Cmdlet Informationen über alle Office 365-Benutzerkonten zurück. Brauchen Sie schnell Informationen zu Ihren Office 365-Benutzern? Dann führen Sie diesen Befehl in Office 365 PowerShell aus:</span><span class="sxs-lookup"><span data-stu-id="d97ce-p108">As you probably know, the **Get-MsolUser** cmdlet returns information about all your Office 365 user accounts. Need some quick info about all your Office 365 users? Then run this command in Office 365 PowerShell:</span></span>
  
```
Get-MsolUser
```

<span data-ttu-id="d97ce-135">"Get-MsolUser" gibt wiederum Daten wie die folgenden zurück:</span><span class="sxs-lookup"><span data-stu-id="d97ce-135">In turn, Get-MsolUser returns data similar to this:</span></span>
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
ZrinkaM@litwareinc.com      Zrinka Makovac                  True
BelindaN@litwareinc.com     Belinda Newman                  False
BonnieK@litwareinc.com      Bonnie Kearney                  True
FabriceC@litwareinc.com     Fabrice Canel                   True
AnneW@litwareinc.com        Anne Wallace                    True
AlexD@litwareinc.com        Alex Darrow                     True
```

<span data-ttu-id="d97ce-p109">Wie Sie sehen, bezieht sich einer der zurückgegebenen Eigenschaftswerte auf die **isLicensed** -Eigenschaft. Wenn **isLicensed** gleich `False` ist, hat dieser Benutzer keine Lizenz für Office 365. Das heißt, wenn Sie möchten, können Sie einfach durch die Liste Ihrer Benutzer blättern und diejenigen heraussuchen, bei denen die **isLicensed** -Eigenschaft den Wert `False` hat.</span><span class="sxs-lookup"><span data-stu-id="d97ce-p109">As you can see, one of the property values returned is for the **isLicensed** property. If **isLicensed** is equal to `False` that means that the user doesn't have a license for Office 365. In other words, and if you wanted to, you could simply scroll through your list of users and pick out the ones where the **isLicensed** property is set to `False`.</span></span>
  
<span data-ttu-id="d97ce-p110">Wie auch immer, das Durchblättern einer Liste von Benutzern in dem Versuch, nicht lizenzierte Benutzer herauszusuchen, funktioniert, solange die Anzahl der Benutzer relativ klein ist. Wenn Sie viele Benutzer haben, ist das Durchblättern dieser Liste aber, im besten Fall, äußerst mühevoll. (Und je nach Konfiguration von Windows PowerShell vielleicht sogar geradezu unmöglich. Das liegt daran, dass die Anzahl der Ausgabezeilen, die auf der Windows PowerShell-Konsole auf einmal angezeigt werden können, begrenzt ist.)</span><span class="sxs-lookup"><span data-stu-id="d97ce-p110">At any rate, scrolling through a list of users trying to pick out the unlicensed users works as long as you have a relatively small number of users. If you have a large number of users, however, scrolling through that list will be, at best, extremely tedious. (And, depending on how Windows PowerShell has been configured, perhaps downright impossible. That's because there's a limit to the number of lines of output that can be displayed in the Windows PowerShell console at any one time.)</span></span>
  
<span data-ttu-id="d97ce-143">Mit diesen Fakten im Hinterkopf ist es viel besser, Ihre nicht lizenzierten Benutzer stattdessen mit dem folgenden Befehl aufzulisten:</span><span class="sxs-lookup"><span data-stu-id="d97ce-143">With that in mind, a much better way to list your unlicensed users is to run this command instead:</span></span>
  
```
Get-MsolUser -UnlicensedUsersOnly
```

<span data-ttu-id="d97ce-p111">Mit diesem Befehl werden nur die Benutzer zurückgegeben, die keine Lizenz für Office 365 haben. Mit anderen Worten:</span><span class="sxs-lookup"><span data-stu-id="d97ce-p111">That command returns only those users who don't have a license for Office 365. In other words:</span></span>
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  False
```

<span data-ttu-id="d97ce-p112">Wie Sie sehen können, haben wir einen nicht lizenzierten Benutzer. Und was würden wir tun, wenn wir nur eine Liste der  *lizenzierten*  Benutzer haben wollten? Das ist etwas komplizierter, aber nur ein wenig:</span><span class="sxs-lookup"><span data-stu-id="d97ce-p112">As you can see we have one unlicensed user. And what is we only wanted a list of the  *licensed*  users? That's a tiny bit more complicated, but only the tiniest bit:</span></span>
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true}
```

<span data-ttu-id="d97ce-149">Dieser Befehl, der nach allen Benutzerkonten sucht, deren **isLicensed** -Eigenschaft den Wert `True` hat, gibt Informationen ähnlich den folgenden zurück:</span><span class="sxs-lookup"><span data-stu-id="d97ce-149">That command, which looks for all the user accounts where the **isLicensed** property is equal to `True`, returns information similar to this:</span></span>
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
ZrinkaM@litwareinc.com      Zrinka Makovac                  True
BonnieK@litwareinc.com      Bonnie Kearney                  True
FabriceC@litwareinc.com     Fabrice Canel                   True
AnneW@litwareinc.com        Anne Wallace                    True
AlexD@litwareinc.com        Alex Darrow                     True
```

<span data-ttu-id="d97ce-p113">Wie Sie sehen, werden keine Informationen für Belinda Newman zurückgegeben. Warum nicht? Richtig: weil die **isLicensed** -Eigenschaft für Belindas Konto nicht auf `True` festgelegt wurde.</span><span class="sxs-lookup"><span data-stu-id="d97ce-p113">As you can see, information is not returned for Belinda Newman. Why not? You got it: because the **isLicensed** property for Belinda's account is not set to `True`.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d97ce-153">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="d97ce-153">See also</span></span>
<span data-ttu-id="d97ce-154"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="d97ce-154"><a name="SeeAlso"> </a></span></span>

<span data-ttu-id="d97ce-155">Weitere Informationen zu den in diesen Verfahren Thema verwendeten Cmdlets finden Sie unter den folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="d97ce-155">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="d97ce-156">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="d97ce-156">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="d97ce-157">Where-Object</span><span class="sxs-lookup"><span data-stu-id="d97ce-157">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

