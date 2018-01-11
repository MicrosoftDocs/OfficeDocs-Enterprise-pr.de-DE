---
title: Zuweisen von benutzerspezifischen Skype for Business Online-Richtlinien mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: 
ms.assetid: 36743c86-46c2-46be-b9ed-ad9d4e85d186
description: 'Zusammenfassung: Verwenden Sie Office 365 PowerShell, um benutzerspezifische Kommunikationseinstellungen mit Skype for Business Online-Richtlinien zuzuweisen.'
ms.openlocfilehash: 7f819b619c5b3607c98c10791fe30c3944e862a4
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2018
---
# <a name="assign-per-user-skype-for-business-online-policies-with-office-365-powershell"></a><span data-ttu-id="73904-103">Zuweisen von benutzerspezifischen Skype for Business Online-Richtlinien mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="73904-103">Assign per-user Skype for Business Online policies with Office 365 PowerShell</span></span>

 <span data-ttu-id="73904-104">**Zusammenfassung:** Verwenden Sie Office 365 PowerShell, um benutzerspezifische Kommunikationseinstellungen mit Skype for Business Online-Richtlinien zuzuweisen.</span><span class="sxs-lookup"><span data-stu-id="73904-104">**Summary:** Use Office 365 PowerShell to assign per-user communication settings with Skype for Business Online policies.</span></span>
  
<span data-ttu-id="73904-105">Die Verwendung von Office 365 PowerShell ist eine effiziente Methode, um benutzerspezifische Kommunikationseinstellungen mit Skype for Business Online-Richtlinien zuzuweisen.</span><span class="sxs-lookup"><span data-stu-id="73904-105">Using Office 365 PowerShell is an efficient way to assign per-user communication settings with Skype for Business Online policies.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="73904-106">Bevor Sie beginnen:</span><span class="sxs-lookup"><span data-stu-id="73904-106">Before you begin</span></span>

<span data-ttu-id="73904-107">Bereiten Sie sich mithilfe dieser Anweisungen auf die Ausführung der Befehle vor (überspringen Sie die Schritte, die Sie bereits ausgeführt haben):</span><span class="sxs-lookup"><span data-stu-id="73904-107">Use these instructions to get set up to run the commands (skip the steps you have already completed):</span></span>
  
1. <span data-ttu-id="73904-108">Laden Sie das [Connector-Modul für Skype for Business Online](https://www.microsoft.com/en-us/download/details.aspx?id=39366) herunter, und installieren Sie es.</span><span class="sxs-lookup"><span data-stu-id="73904-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/en-us/download/details.aspx?id=39366).</span></span>
    
2. <span data-ttu-id="73904-109">Öffnen Sie eine Windows PowerShell-Eingabeaufforderung, und führen Sie die folgenden Befehle aus:</span><span class="sxs-lookup"><span data-stu-id="73904-109">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
  ```
  Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
  ```
<span data-ttu-id="73904-110">Wenn Sie dazu aufgefordert werden, geben Sie den Namen und das Kennwort Ihres Skype for Business Online-Administratorkontos ein.</span><span class="sxs-lookup"><span data-stu-id="73904-110">When prompted, enter your Skype for Business Online administrator account name and password.</span></span>
    
## <a name="updating-external-communication-settings-for-a-user-account"></a><span data-ttu-id="73904-111">Aktualisieren externer Kommunikationseinstellungen für ein Benutzerkonto</span><span class="sxs-lookup"><span data-stu-id="73904-111">Updating external communication settings for a user account</span></span>

<span data-ttu-id="73904-p101">Angenommen, Sie möchten Einstellungen für die externe Kommunikation für ein Benutzerkonto ändern. Sie möchten z. B. festlegen, dass Alex mit Partnerbenutzern kommunizieren darf (EnableFederationAccess = True), jedoch nicht mit Windows Live-Benutzern (EnablePublicCloudAccess = False). Hierzu müssen Sie zwei Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="73904-p101">Suppose you want to change external communication settings on a user account. For example, you want to allow Alex to communicate with federated users (EnableFederationAccess is equal to True) but not with Windows Live users (EnablePublicCloudAccess equals False). To do that, you need to do two things:</span></span>
  
1. <span data-ttu-id="73904-115">Suchen Sie nach eine externe Zugriffsrichtlinie, die unsere Kriterien erfüllt.</span><span class="sxs-lookup"><span data-stu-id="73904-115">Find an external access policy that meets our criteria.</span></span>
    
2. <span data-ttu-id="73904-116">Weisen Sie Alex diese externe Zugriffsrichtlinie ist.</span><span class="sxs-lookup"><span data-stu-id="73904-116">Assign that external access policy to Alex.</span></span>
    
> [!NOTE]
>  <span data-ttu-id="73904-p102">Sie können eine benutzerdefinierte Richtlinie nicht selbst erstellen. Dies liegt daran, dass Skype for Business Online das Erstellen von benutzerdefinierten Richtlinien nicht zulässt. Stattdessen müssen Sie eine der speziell für Office 365 erstellten Richtlinien zuweisen. Zu den vorab erstellten Richtlinien gehören: 4 verschiedene Client-Richtlinien, 224 verschiedene Conferencing-Richtlinien, 5 verschiedene Wählpläne, 5 verschiedene externe Zugriffsrichtlinien, 1 gehostete Voicemail-Richtlinie und 4 verschiedene Voice-Richtlinien.</span><span class="sxs-lookup"><span data-stu-id="73904-p102">You can't create a custom policy all our own. That's because Skype for Business Online does not allow you to create custom policies. Instead, you must assign one of the policies that were created specifically for Office 365. Those pre-created policies include: 4 different client policies, 224 different conferencing policies, 5 different dial plans, 5 different external access policies, 1 hosted voicemail policy, and 4 different voice policies.</span></span>
  
<span data-ttu-id="73904-p103">Woher wissen Sie, welche externe Zugriffsrichtlinie Sie Alex zuweisen müssen? Der folgende Befehl gibt alle externen Zugriffsrichtlinien zurück, in denen „EnableFederationAccess“ auf „True“ und „EnablePublicCloudAccess“ auf „False“ festgelegt ist:</span><span class="sxs-lookup"><span data-stu-id="73904-p103">So how do you determine which external access policy to assign Alex? The following command returns all the external access policies where EnableFederationAccess is set to True and EnablePublicCloudAccess is set to False:</span></span>
  
```
Get-CsExternalAccessPolicy | Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $False}
```

<span data-ttu-id="73904-p104">Der Befehl gibt alle Richtlinien zurück, die zwei Kriterien erfüllen: Die Eigenschaft „EnableFederationAccess“ ist auf „True“ und die Richtlinie „EnablePublicCloudAccess“ auf „False“ festgelegt. Der Befehl gibt wiederum eine Richtlinie zurück – FederationOnly – die unser Kriterium erfüllt. Hier ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="73904-p104">What the command does is return all the policies that meet two criteria: the EnableFederationAccess property is set to True, and the EnablePublicCloudAccess policy is set to False. In turn, that command returns one policy that meets our criteria (FederationOnly). Here is an example:</span></span>
  
```
Identity                          : Tag:FederationOnly
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : False
EnablePublicCloudAudioVideoAccess : False
EnableOutsideAccess               : True
```

> [!NOTE]
> <span data-ttu-id="73904-p105">Die Richtlinienidentität besagt „Tag:FederationOnly“. Wie sich zeigt, ist das Präfix „Tag:“ ein Übertrag aus einer früheren Vorabversion für Microsoft Lync 2013. Beim Zuweisen von Richtlinien zu Benutzern sollten Sie das Präfix „Tag:“ löschen und nur den Richtliniennamen verwenden: FederationOnly.</span><span class="sxs-lookup"><span data-stu-id="73904-p105">The policy Identity says Tag:FederationOnly. As it turns out, the Tag: prefix is a carryover from the early pre-release work done on Microsoft Lync 2013. When it comes to assigning policies to users, you should delete the Tag: prefix and use just the policy name: FederationOnly.</span></span> 
  
<span data-ttu-id="73904-p106">Nachdem wir Sie wissen, welche Richtlinie Sie Alex zuweisen müssen, können Sie die Richtlinie mithilfe des Cmdlets [Grant-CsExternalAccessPolicy](https://go.microsoft.com/fwlink/?LinkId=523974) zuweisen: Hier ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="73904-p106">Now that you know which policy to assign to Alex, we can assign that policy by using the [Grant-CsExternalAccessPolicy](https://go.microsoft.com/fwlink/?LinkId=523974) cmdlet. Here is an example:</span></span>
  
```
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName "FederationOnly"
```

<span data-ttu-id="73904-131">Das Zuweisen einer Richtlinie ist ganz einfach: Sie geben einfach die Identität des Benutzers und den Namen der zuzuweisenden Richtlinie an.</span><span class="sxs-lookup"><span data-stu-id="73904-131">Assigning a policy is pretty simple: you simply specify the Identity of the user and the name of the policy to be assigned.</span></span> 
  
<span data-ttu-id="73904-p107">Und bei Richtlinien und Richtlinienzuweisungen sind Sie nicht darauf beschränkt, mit nur jeweils einem einzelnen Benutzerkonto zu arbeiten. Angenommen beispielsweise, Sie benötigen eine Liste aller Benutzer, die mit Partnerbenutzern und Windows Live-Benutzern kommunizieren dürfen. Wir wissen bereits, dass diesen Benutzern die externe Benutzerzugriffsrichtlinie „FederationAndPICDefault" zugewiesen wurde. Da wir dies wissen, können Sie eine Liste all dieser Benutzer anzeigen, indem Sie den folgenden einfachen Befehl ausführen:</span><span class="sxs-lookup"><span data-stu-id="73904-p107">And when it comes to policies and policy assignments, you're not limited to working with user accounts one a time. For example, suppose you need a list of all the users who are allowed to communicate with federated partners and with Windows Live users. We already know that those users have been assigned the external user access policy FederationAndPICDefault. Because we know that, you can display a list of all those users by running one simple command. Here is the command:</span></span>
  
```
Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "FederationAndPICDefault"} | Select-Object DisplayName
```

<span data-ttu-id="73904-p108">Anders gesagt, wir können alle Benutzer anzeigen, bei denen die ExternalAccessPolicy-Eigenschaft auf FederationAndPICDefault festgelegt ist. (Und zum Einschränken der am Bildschirm angezeigten Informationsmenge können Sie das Select-Object-Cmdlet verwenden, um nur die Anzeigenamen der Benutzer anzuzeigen).</span><span class="sxs-lookup"><span data-stu-id="73904-p108">In other words, show us all the users where the ExternalAccessPolicy property is set to FederationAndPICDefault. (And, in order to limit the amount of information that appears onscreen, use the Select-Object cmdlet to display show us only each user's display name.)</span></span> 
  
<span data-ttu-id="73904-139">Um alle Benutzerkonten so zu konfigurieren, dass sie die gleiche Richtlinie verwenden, geben Sie diesen Befehl ein:</span><span class="sxs-lookup"><span data-stu-id="73904-139">To configure all our user accounts to use that same policy, use this command:</span></span>
  
```
Get-CsOnlineUser | Grant-CsExternalAccessPolicy "FederationAndPICDefault"
```

<span data-ttu-id="73904-140">Dieser Befehl verwendet „Get-CsOnlineUser“, um eine Sammlung aller Benutzer zurückzugeben, die für Lync aktiviert wurden. Anschließend werden alle diese Informationen an „Grant-CsExternalAccessPolicy“ gesendet, das die Richtlinie „FederationAndPICDefault“ jedem Benutzer in der Sammlung zuweist.</span><span class="sxs-lookup"><span data-stu-id="73904-140">This command uses Get-CsOnlineUser to return a collection of all the users who have been enabled for Lync, then sends all that information to Grant-CsExternalAccessPolicy, which assigns the FederationAndPICDefault policy to each and every user in the collection.</span></span>
  
<span data-ttu-id="73904-p109">Ein weiteres Beispiel: Angenommen, Sie haben Alex zuvor die Richtlinie „FederationAndPICDefault" zugewiesen, haben aber nun Ihre Meinung geändert und möchten, dass er von der globalen externen Zugriffsrichtlinie verwaltet wird. Sie können die globale Richtlinie niemandem explizit zuweisen. Sie wird nur verwendet, wenn keine andere benutzerspezifische Richtlinie zugewiesen ist. Wenn Sie also möchten, dass Alex von der globalen Richtlinie verwaltet wird, müssen Sie die Zuweisung aller zuvor zugewiesenen benutzerspezifischen Richtlinien wieder  *aufheben*  . Hier ein Beispielbefehl:</span><span class="sxs-lookup"><span data-stu-id="73904-p109">As an additional example, suppose you've previously assigned Alex the FederationAndPICDefault policy and now you've changed your mind and would like him to be managed by the global external access policy. You can't explicitly assign the global policy to anyone. It is only used if no other per-user policy is assigned. Therefore, if we want Alex to be managed by the global policy, you need to  *unassign*  any per-user policy previously assigned to him. Here is an example command:</span></span>
  
```
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName $Null
```

<span data-ttu-id="73904-p110">Dieser Befehl legt den Namen der Alex zugewiesenen externen Zugriffsrichtlinie auf einen Nullwert ($Null) fest. Null bedeutet „nichts". Anders ausgedrückt, Alex wird keine externe Zugriffsrichtlinie zugewiesen. Wenn einem Benutzer keine externe Zugriffsrichtlinie zugewiesen ist, wird der Benutzer von der globalen Richtlinie verwaltet.</span><span class="sxs-lookup"><span data-stu-id="73904-p110">This command sets the name of the external access policy assigned to Alex to a null value ($Null). Null means "nothing". In other words, no external access policy is assigned to Alex. When no external access policy is assigned to a user, that user then gets managed by the global policy.</span></span>
  
<span data-ttu-id="73904-p111">Um ein Benutzerkonto mithilfe von Windows PowerShell zu deaktivieren, verwenden Sie die Azure Active Directory-Cmdlets zum Entfernen der Skype for Business-Lizenz von Alex. Weitere Informationen finden Sie unter [Deaktivieren des Zugriffs auf Dienste mit Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="73904-p111">To disable a user account using Windows PowerShell, use the Azure Active Directory cmdlets to remove Alex's Skype for Business Online license. For more information, see [Disable access to services with Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="73904-152">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="73904-152">See also</span></span>

#### 

[<span data-ttu-id="73904-153">Verwalten von Skype for Business Online mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="73904-153">Manage Skype for Business Online with Office 365 PowerShell</span></span>](manage-skype-for-business-online-with-office-365-powershell.md)
  
[<span data-ttu-id="73904-154">Verwalten von Office 365 mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="73904-154">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="73904-155">Erste Schritte mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="73904-155">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

