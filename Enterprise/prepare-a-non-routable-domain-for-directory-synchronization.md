---
title: Vorbereiten von Domänen nicht-routingfähigen für Directory-Synchronisierung
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365E_SetupDirSyncLocalDir
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: e7968303-c234-46c4-b8b0-b5c93c6d57a7
description: Hier erfahren Sie, wie Sie vorgehen, wenn Sie verfügen über eine nicht Routale Domäne Ihre lokalen Benutzer zugeordnet ist, bevor Sie mit Office 365 synchronisieren.
ms.openlocfilehash: 62779ba879522177ba15a491644ab42f5961ece0
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540991"
---
# <a name="prepare-a-non-routable-domain-for-directory-synchronization"></a><span data-ttu-id="9ec11-103">Vorbereiten von Domänen nicht-routingfähigen für Directory-Synchronisierung</span><span class="sxs-lookup"><span data-stu-id="9ec11-103">Prepare a non-routable domain for directory synchronization</span></span>
<span data-ttu-id="9ec11-p101">Wenn Sie Ihr lokales Verzeichnis mit Office 365 synchronisieren eine überprüfte Domäne in Azure Active Directory haben. Nur die User Principal Names (UPN), die mit der lokalen Domäne verknüpft sind, werden synchronisiert. Allerdings werden alle UPN, die eine nicht-routingfähigen Domäne, z. B. Local (wie billa@contoso.local), enthält zu synchronisiert eine. Domäne "onmicrosoft.com" (wie billa@contoso.onmicrosoft.com).</span><span class="sxs-lookup"><span data-stu-id="9ec11-p101">When you synchronize your on-premises directory with Office 365 you have to have a verified domain in Azure Active Directory. Only the User Principal Names (UPN) that are associated with the on-premises domain are synchronized. However, any UPN that contains an non-routable domain, for example .local (like billa@contoso.local), will be synchronized to an .onmicrosoft.com domain (like billa@contoso.onmicrosoft.com).</span></span> 

<span data-ttu-id="9ec11-107">Wenn Sie bereits eine Local-Domäne für Ihre Benutzerkonten in Active Directory wird empfohlen, dass Sie diese, um eine überprüften Domäne (wie billa@contoso.com) verwenden, um ordnungsgemäß Synchronisierung mit Office 365-Domäne ändern.</span><span class="sxs-lookup"><span data-stu-id="9ec11-107">If you currently use a .local domain for your user accounts in Active Directory it's recommended that you change them to use a verified domain (like billa@contoso.com) in order to properly sync with your Office 365 domain.</span></span>
  
## <a name="what-if-i-only-have-a-local-on-premises-domain"></a><span data-ttu-id="9ec11-108">Was geschieht, wenn nur eine Local lokale Domäne ist vorhanden?</span><span class="sxs-lookup"><span data-stu-id="9ec11-108">What if I only have a .local on-premises domain?</span></span>

<span data-ttu-id="9ec11-p102">Das neueste Tool, das Sie verwenden können, für die Synchronisierung Ihrer Active Directory und Azure Active Directory heißt Azure Active Directory verbinden. Weitere Informationen finden Sie unter [Integration von Ihrer lokalen Identitäten mit Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=624168).</span><span class="sxs-lookup"><span data-stu-id="9ec11-p102">The most recent tool you can use for synchronizing your Active Directory to Azure Active Directory is named Azure AD Connect. For more information, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=624168).</span></span>
  
<span data-ttu-id="9ec11-p103">Verbinden von Azure Active Directory synchronisiert UPN und das Kennwort des Benutzers, damit Benutzer sich anmelden können sich mit denselben Anmeldeinformationen lokalen Verwendung. Azure Active Directory verbinden synchronisiert jedoch nur Benutzer auf Domänen, die von Office 365 überprüft werden. Dies bedeutet, dass die Domäne auch von Azure Active Directory überprüft worden ist, da Office 365 Identitäten von Azure Active Directory verwaltet werden. Anders ausgedrückt, muss die Domäne einen gültigen Internet-Domänennamen (z. B. .com, org, .net, US usw.) sein. Wenn der internen Active Directory nur eine nicht-routingfähigen Domäne (beispielsweise Local) verwendet wird, darf nicht dies möglicherweise die überprüfte Domäne übereinstimmen, die Sie in Office 365. Sie können dieses Problem beheben, indem Sie entweder die primäre Domäne in Ihre lokale Active Directory ändern oder durch eine oder mehrere UPN-Suffixe hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="9ec11-p103">Azure AD Connect synchronizes your users' UPN and password so that users can sign in with the same credentials they use on-premises. However, Azure AD Connect only synchronizes users to domains that are verified by Office 365. This means that the domain also is verified by Azure Active Directory because Office 365 identities are managed by Azure Active Directory. In other words, the domain has to be a valid Internet domain (for example, .com, .org, .net, .us, etc.). If your internal Active Directory only uses a non-routable domain (for example, .local), this can't possibly match the verified domain you have on Office 365. You can fix this issue by either changing your primary domain in your on premises Active Directory, or by adding one or more UPN suffixes.</span></span>
  
### <a name="change-your-primary-domain"></a><span data-ttu-id="9ec11-117">**Ändern Sie Ihre primäre Domäne**</span><span class="sxs-lookup"><span data-stu-id="9ec11-117">**Change your primary domain**</span></span>

<span data-ttu-id="9ec11-p104">Ändern Sie Ihre primäre Domäne in einer Domäne, die Sie in Office 365, beispielsweise "contoso.com" überprüft haben. Jeder Benutzer mit der Domäne contoso.local klicken Sie dann auf "contoso.com" aktualisiert. Weitere Informationen finden Sie unter [Domäne umbenennen Funktionsweise](https://go.microsoft.com/fwlink/p/?LinkId=624174). Dies ist ein sehr Vorgang, jedoch und eine einfachere Lösung [Hinzufügen UPN Suffixe und Aktualisieren von Benutzern für diese](prepare-a-non-routable-domain-for-directory-synchronization.md#bk_register), wie im folgenden Abschnitt dargestellt.</span><span class="sxs-lookup"><span data-stu-id="9ec11-p104">Change your primary domain to a domain you have verified in Office 365, for example, contoso.com. Every user that has the domain contoso.local is then updated to contoso.com. For instructions, see [How Domain Rename Works](https://go.microsoft.com/fwlink/p/?LinkId=624174). This is a very involved process, however, and an easier solution is to [Add UPN suffixes and update your users to them](prepare-a-non-routable-domain-for-directory-synchronization.md#bk_register), as shown in the following section.</span></span>
  
### <a name="add-upn-suffixes-and-update-your-users-to-them"></a><span data-ttu-id="9ec11-122">**UPN-Suffixen hinzufügen und Aktualisieren von Benutzern für diese**</span><span class="sxs-lookup"><span data-stu-id="9ec11-122">**Add UPN suffixes and update your users to them**</span></span>

<span data-ttu-id="9ec11-p105">Sie können das Local Problem lösen durch die Registrierung neue UPN-Suffix oder Suffixe in Active Directory und die Domäne (oder Domänen) übereinstimmen, die Sie in Office 365 überprüft. Nachdem Sie das neue Suffix registrieren, aktualisieren Sie den Benutzer UPNs der Local mit den neuen Domänennamen für Beispiel ersetzen, damit ein Benutzerkonto billa@contoso.com aussieht.</span><span class="sxs-lookup"><span data-stu-id="9ec11-p105">You can solve the .local problem by registering new UPN suffix or suffixes in Active Directory to match the domain (or domains) you verified in Office 365. After you register the new suffix, you update the user UPNs to replace the .local with the new domain name for example so that a user account looks like billa@contoso.com.</span></span>
  
<span data-ttu-id="9ec11-125">Nachdem Sie die Verwendung die überprüfte Domäne UPNs aktualisiert haben, können Sie Ihre lokale Active Directory mit Office 365 synchronisieren.</span><span class="sxs-lookup"><span data-stu-id="9ec11-125">After you have updated the UPNs to use the verified domain,you are ready to synchronize your on-premises Active Directory with Office 365.</span></span>
  
 <span data-ttu-id="9ec11-126">**Schritt 1: Fügen Sie das neue UPN-Suffix hinzu**</span><span class="sxs-lookup"><span data-stu-id="9ec11-126">**Step 1: Add the new UPN suffix**</span></span>
  
1. <span data-ttu-id="9ec11-127">Auf dem Server, die auf Active Directory-Domänendienste (AD DS) ausgeführt wird, wählen Sie im Server-Manager **Tools** \> **Active Directory-Domänen und -Vertrauensstellungen**.</span><span class="sxs-lookup"><span data-stu-id="9ec11-127">On the server that Active Directory Domain Services (AD DS) runs on, in the Server Manager choose **Tools** \> **Active Directory Domains and Trusts**.</span></span>
    
    <span data-ttu-id="9ec11-128">**Oder, falls Sie nicht über Windows Server 2012 verfügen**</span><span class="sxs-lookup"><span data-stu-id="9ec11-128">**Or, if you don't have Windows Server 2012**</span></span>
    
    <span data-ttu-id="9ec11-129">Drücken Sie die **Windows-Taste + R** , öffnen Sie das Dialogfeld **Ausführen** , und geben Sie in Domain.msc, und wählen Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="9ec11-129">Press **Windows key + R** to open the **Run** dialog, and then type in Domain.msc, and then choose **OK**.</span></span>
    
    ![Wählen Sie Active Directory-Domänen und -Vertrauensstellungen.](media/46b6e007-9741-44af-8517-6f682e0ac974.png)
  
2. <span data-ttu-id="9ec11-131">Das Fenster **Active Directory-Domänen und-Vertrauensstellungen** Maustaste auf **Active Directory-Domänen und -Vertrauensstellungen**, und wählen Sie dann auf **Eigenschaften**.</span><span class="sxs-lookup"><span data-stu-id="9ec11-131">On the **Active Directory Domains and Trusts** window, right-click **Active Directory Domains and Trusts**, and then choose **Properties**.</span></span>
    
    ![Mit der rechten Maustaste Active Directory-Domänen und -Vertrauensstellungen, und wählen Sie Eigenschaften](media/39d20812-ffb5-4ba9-8d7b-477377ac360d.png)
  
3. <span data-ttu-id="9ec11-133">Klicken Sie auf der Registerkarte **Benutzerprinzipalnamen-Suffixe** im Feld **Alternative UPN-Suffixe** Geben Sie Ihre neue UPN-Suffix oder Suffixe, und wählen Sie dann **Hinzufügen** \> **Übernehmen**.</span><span class="sxs-lookup"><span data-stu-id="9ec11-133">On the **UPN Suffixes** tab, in the **Alternative UPN Suffixes** box, type your new UPN suffix or suffixes, and then choose **Add** \> **Apply**.</span></span>
    
    ![Hinzufügen eines neuen UPN-Suffixes](media/a4aaf919-7adf-469a-b93f-83ef284c0915.PNG)
  
    <span data-ttu-id="9ec11-135">Wählen Sie **OK** , wenn Sie das Hinzufügen von Suffixe fertig sind.</span><span class="sxs-lookup"><span data-stu-id="9ec11-135">Choose **OK** when you're done adding suffixes.</span></span> 
    
 <span data-ttu-id="9ec11-136">**Schritt 2: Ändern Sie das UPN-Suffix für vorhandene Benutzer**</span><span class="sxs-lookup"><span data-stu-id="9ec11-136">**Step 2: Change the UPN suffix for existing users**</span></span>
  
1. <span data-ttu-id="9ec11-137">Auf dem Server, die auf Active Directory-Domänendienste (AD DS) ausgeführt wird, wählen Sie im Server-Manager **Tools** \> **Active Directory Active Directory-Benutzer und-Computer**.</span><span class="sxs-lookup"><span data-stu-id="9ec11-137">On the server that Active Directory Domain Services (AD DS) runs on, in the Server Manager choose **Tools** \> **Active Directory Active Directory Users and Computers**.</span></span>
    
    <span data-ttu-id="9ec11-138">**Oder, falls Sie nicht über Windows Server 2012 verfügen**</span><span class="sxs-lookup"><span data-stu-id="9ec11-138">**Or, if you don't have Windows Server 2012**</span></span>
    
    <span data-ttu-id="9ec11-139">Drücken Sie die **Windows-Taste + R** , öffnen Sie das Dialogfeld **Ausführen** , und geben Sie in den Befehl DSA.msc ein, und klicken Sie dann auf **OK**</span><span class="sxs-lookup"><span data-stu-id="9ec11-139">Press **Windows key + R** to open the **Run** dialog, and then type in Dsa.msc, and then click **OK**</span></span>
    
2. <span data-ttu-id="9ec11-140">Wählen Sie einen Benutzer mit der rechten Maustaste, und wählen Sie dann auf **Eigenschaften**.</span><span class="sxs-lookup"><span data-stu-id="9ec11-140">Select a user, right-click, and then choose **Properties**.</span></span>
    
3. <span data-ttu-id="9ec11-141">Klicken Sie auf der Registerkarte **Konto** in der Dropdownliste UPN-Suffix wählen Sie das neue UPN-Suffix, und wählen Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="9ec11-141">On the **Account** tab, in the UPN suffix drop-down list, choose the new UPN suffix, and then choose **OK**.</span></span>
    
    ![Fügen Sie neue UPN-Suffix für einen Benutzer hinzu](media/54876751-49f0-48cc-b864-2623c4835563.png)
  
4. <span data-ttu-id="9ec11-143">Führen Sie diese Schritte für jeden Benutzer.</span><span class="sxs-lookup"><span data-stu-id="9ec11-143">Complete these steps for every user.</span></span>
    
    <span data-ttu-id="9ec11-144">Alternativ können Sie gleichzeitig aktualisieren des UPN Suffixe [können Sie auch Windows PowerShell, um das UPN-Suffix für alle Benutzer zu ändern](prepare-a-non-routable-domain-for-directory-synchronization.md#BK_Posh).</span><span class="sxs-lookup"><span data-stu-id="9ec11-144">Alternately you can bulk update the UPN suffixes [You can also use Windows PowerShell to change the UPN suffix for all users](prepare-a-non-routable-domain-for-directory-synchronization.md#BK_Posh).</span></span>
    
### <a name="you-can-also-use-windows-powershell-to-change-the-upn-suffix-for-all-users"></a><span data-ttu-id="9ec11-145">**Sie können Windows PowerShell auch so ändern Sie das UPN-Suffix für alle Benutzer verwenden.**</span><span class="sxs-lookup"><span data-stu-id="9ec11-145">**You can also use Windows PowerShell to change the UPN suffix for all users**</span></span>

<span data-ttu-id="9ec11-p106">Wenn Sie viele Benutzer aktualisiert haben, ist es einfacher, Windows PowerShell verwenden. Das folgende Beispiel verwendet die Cmdlets [Get-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312) und [Set-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624313) , um alle contoso.local Suffixe in "contoso.com" zu ändern.</span><span class="sxs-lookup"><span data-stu-id="9ec11-p106">If you have a lot of users to update, it is easier to use Windows PowerShell. The following example uses the cmdlets [Get-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312) and [Set-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624313) to change all contoso.local suffixes to contoso.com.</span></span> 

<span data-ttu-id="9ec11-148">Führen Sie die folgenden Windows PowerShell-Befehle, um alle contoso.local Suffixe auf "contoso.com" zu aktualisieren:</span><span class="sxs-lookup"><span data-stu-id="9ec11-148">Run the following Windows PowerShell commands to update all contoso.local suffixes to contoso.com:</span></span>
    
  ```
  $LocalUsers = Get-ADUser -Filter {UserPrincipalName -like '*contoso.local'} -Properties userPrincipalName -ResultSetSize $null
  ```

  ```
  $LocalUsers | foreach {$newUpn = $_.UserPrincipalName.Replace("contoso.local","contoso.com"); $_ | Set-ADUser -UserPrincipalName $newUpn}
  ```
<span data-ttu-id="9ec11-149">Finden Sie unter [Active Directory Windows PowerShell-Modul](https://go.microsoft.com/fwlink/p/?LinkId=624314) erhalten Sie weitere Informationen zum Verwenden von Windows PowerShell in Active Directory.</span><span class="sxs-lookup"><span data-stu-id="9ec11-149">See [Active Directory Windows PowerShell module](https://go.microsoft.com/fwlink/p/?LinkId=624314) to learn more about using Windows PowerShell in Active Directory.</span></span> 

