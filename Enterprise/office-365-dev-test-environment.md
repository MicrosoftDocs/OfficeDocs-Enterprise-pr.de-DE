---
title: Office 365-Entwicklungs-/Testumgebung
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/02/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 4f6035b8-2da3-4cf9-9657-5284d6364f7a
description: 'Zusammenfassung: Verwenden Sie diese Testumgebungsanleitung, um ein Office 365-Testabonnement für Analysen oder Entwicklungs-/Testumgebungen zu erstellen.'
ms.openlocfilehash: 06ffed9ab4b41c5e164cfadb951181a3406c67a3
ms.sourcegitcommit: 1c97471f47e1869f6db684f280f9085b7c2ff59f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/18/2019
ms.locfileid: "35781935"
---
# <a name="office-365-devtest-environment"></a><span data-ttu-id="65fb0-103">Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="65fb0-103">Office 365 dev/test environment</span></span>

 <span data-ttu-id="65fb0-104">**Zusammenfassung:** Verwenden Sie diese Testumgebungsanleitung, um ein Office 365-Testabonnement für Analysen oder Entwicklungs-/Testumgebungen zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="65fb0-104">**Summary:** Use this Test Lab Guide to create an Office 365 trial subscription for evaluation or dev/test.</span></span>
  
<span data-ttu-id="65fb0-p101">Sie können ein Office 365-Testabonnement verwenden und eine Office 365-Entwicklungs-/Testumgebung für Anwendungen erstellen oder Features und Funktionen von Office 365 demonstrieren. Es gibt zwei Versionen:</span><span class="sxs-lookup"><span data-stu-id="65fb0-p101">You can use an Office 365 trial subscription and create an Office 365 dev/test environment for applications or to demonstrate features and capabilities of Office 365. There are two versions:</span></span>
  
- <span data-ttu-id="65fb0-107">Die einfache Office 365-Entwicklungs-/Testumgebung besteht aus einem Office 365-Testabonnement, auf das Sie von Ihrem Hauptcomputer aus zugreifen.</span><span class="sxs-lookup"><span data-stu-id="65fb0-107">The lightweight Office 365 dev/test environment consists of an Office 365 trial subscription that you access from your main computer.</span></span>
    
    <span data-ttu-id="65fb0-p102">Verwenden Sie diese Umgebung, wenn Sie schnell ein Feature demonstrieren möchten. Führen Sie für die einfache Office 365-Entwicklungs-/Testumgebungen nur die Schritte in Phase 2 und 3 dieses Artikels durch.</span><span class="sxs-lookup"><span data-stu-id="65fb0-p102">Use this environment when you want to quickly demonstrate a feature. For the lightweight Office 365 dev/test environment, complete only phases 2 and 3 of this article.</span></span>
    
- <span data-ttu-id="65fb0-p103">Die simulierte Office 365-Entwicklungs-/Testunternehmensumgebung besteht aus einem Office 365-Testabonnement und einem vereinfachtem Organisationsintranet mit Internetverbindung, das in Microsoft Azure-Infrastrukturdiensten gehostet wird. Sie können diese Konfiguration vollständig in der Microsoft-Cloud erstellen.</span><span class="sxs-lookup"><span data-stu-id="65fb0-p103">The simulated enterprise Office 365 dev/test environment consists of an Office 365 trial subscription and a simplified organization intranet connected to the Internet, which is hosted in Microsoft Azure infrastructure services. You can build this configuration completely in the Microsoft cloud.</span></span>
    
    <span data-ttu-id="65fb0-p104">Verwenden Sie diese Umgebung, wenn Sie ein Feature oder eine App in einer Umgebung demonstrieren möchten,die einem gewöhnlichen Organisationsnetzwerk mit Internetverbindung ähnelt, oder für Features, für die diese Art von Umgebung erforderlich ist. Führen Sie für die simulierte Office 365-Entwicklungs-/Testunternehmensumgebung die Schritte in Phasen 1, 2 und 3 dieses Artikels durch.</span><span class="sxs-lookup"><span data-stu-id="65fb0-p104">Use this environment when you want to demonstrate a feature or an app in an environment that resembles a typical organization network connected to the Internet, or for features that require this type of environment. For the simulated enterprise Office 365 dev/test environment, complete phases 1, 2, and 3 of this article.</span></span>
    
> [!NOTE]
> <span data-ttu-id="65fb0-p105">Sie können diesen Artikel auch ausdrucken, um die bestimmten Werte zu notieren, die Sie für diese Umgebung in den kommenden 30 Tage des Office 365-Testabonnements benötigen. Sie können das Testabonnement einfach um weitere 30 Tage verlängern. Für eine dauerhafte Entwicklungs-/Testumgebung erstellen Sie ein neues bezahltes Abonnement mit einer kleinen Anzahl von Lizenzen.</span><span class="sxs-lookup"><span data-stu-id="65fb0-p105">You might want to print this article to record the specific values that you will need for this environment over the 30 days of the Office 365 trial subscription. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
![Testumgebungsanleitungen in der Microsoft Cloud](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="65fb0-118">Klicken Sie [hier](http://aka.ms/catlgstack), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in Office 365 zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="65fb0-118">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-the-base-configuration-in-azure"></a><span data-ttu-id="65fb0-119">Phase 1: Erstellen der Basiskonfiguration in Azure</span><span class="sxs-lookup"><span data-stu-id="65fb0-119">Phase 1: Create the base configuration in Azure</span></span>

<span data-ttu-id="65fb0-120">Befolgen Sie die Anweisungen unter [Basiskonfiguration der Entwicklungs-/Testumgebung](base-configuration-dev-test-environment.md)</span><span class="sxs-lookup"><span data-stu-id="65fb0-120">Follow the instructions in [Base Configuration dev/test environment](base-configuration-dev-test-environment.md).</span></span>
  
<span data-ttu-id="65fb0-p106">Sie benötigen ein Azure-Abonnement. Sie können die [kostenlose Testversion von Azure](https://azure.microsoft.com/pricing/free-trial/) für diese Konfiguration verwenden. Wenn Sie über ein MSDN- oder Visual Studio-Abonnement verfügen, lesen Sie die Informationen unter [Monatliche Azure-Gutschrift für Visual Studio-Abonnenten](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span><span class="sxs-lookup"><span data-stu-id="65fb0-p106">You will need an Azure subscription. You can use the [Azure Free Trial](https://azure.microsoft.com/pricing/free-trial/) for this configuration. If you have an MSDN or Visual Studio subscription, see [Monthly Azure credit for Visual Studio subscribers](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span></span>
  
<span data-ttu-id="65fb0-124">Nachfolgend sehen Sie die daraus resultierende Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="65fb0-124">Here is the resulting configuration.</span></span>
  
![Die Basiskonfiguration der Entwicklungs-/ Testumgebung in Azure](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)


  
<span data-ttu-id="65fb0-126">Diese Konfiguration besteht aus virtuellen DC1-, APP1- und CLIENT1-Computern in einem Subnetz eines virtuellen Azure-Netzwerks.</span><span class="sxs-lookup"><span data-stu-id="65fb0-126">This configuration consists of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
  
## <a name="phase-2-create-an-office-365-trial-subscription"></a><span data-ttu-id="65fb0-127">Phase 2: Erstellen eines Office 365-Testabonnements</span><span class="sxs-lookup"><span data-stu-id="65fb0-127">Phase 2: Create an Office 365 trial subscription</span></span>

<span data-ttu-id="65fb0-128">Für das Office 365 E5-Testabonnement benötigen Sie zunächst einen fiktiven Unternehmensnamen und ein neues Microsoft-Konto.</span><span class="sxs-lookup"><span data-stu-id="65fb0-128">To start your Office 365 E5 trial subscription, you first need a fictitious company name and a new Microsoft account.</span></span>
  
1. <span data-ttu-id="65fb0-p107">Es wird empfohlen, eine Variante von „Contoso“ als Unternehmensnamen zu verwenden. Dies ist ein fiktives Unternehmen, das von Microsoft in Beispielen verwendet wird. Notieren Sie hier Ihren fiktiven Unternehmensnamen: ![](./media/Common-Images/TableLine.png).</span><span class="sxs-lookup"><span data-stu-id="65fb0-p107">We recommend that you use a variant of the company name Contoso for your company name, which is a fictitious company used in Microsoft sample content, but it isn't required. Record your fictitious company name here: ![](./media/Common-Images/TableLine.png)</span></span>
    
2. <span data-ttu-id="65fb0-p108">Wenn Sie sich für ein neues Microsoft-Konto registrieren möchten, wechseln Sie zu [https://outlook.com](https://outlook.com), und erstellen Sie ein Konto mit neuem E-Mail-Konto und neuer E-Mail-Adresse. Dieses Konto wird für die Registrierung für Office 365 verwendet.</span><span class="sxs-lookup"><span data-stu-id="65fb0-p108">To sign up for a new Microsoft account, go to [https://outlook.com](https://outlook.com) and create an account with a new email account and address. You will use this account to sign up for Office 365.</span></span>
    
  - <span data-ttu-id="65fb0-133">Notieren Sie hier den Vor- und Nachnamen des Kontos: ![](./media/Common-Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="65fb0-133">Record the first and last name of your new account here: ![](./media/Common-Images/TableLine.png)</span></span>
    
  - <span data-ttu-id="65fb0-134">Notieren Sie hier die neue E-Mail-Kontoadresse: ![](./media/Common-Images/TableLine.png)@outlook.com</span><span class="sxs-lookup"><span data-stu-id="65fb0-134">Record the new email account address here: ![](./media/Common-Images/TableLine.png)@outlook.com</span></span>
    
### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a><span data-ttu-id="65fb0-135">Registrieren für ein Office 365 E5-Testabonnement</span><span class="sxs-lookup"><span data-stu-id="65fb0-135">Sign up for an Office 365 E5 trial subscription</span></span>

1. <span data-ttu-id="65fb0-136">Öffnen Sie für die einfache Office 365-Entwicklungs-/Testumgebung den Internetbrowser auf Ihrem Computer, und gehen Sie zu [https://aka.ms/e5trial](https://aka.ms/e5trial). </span><span class="sxs-lookup"><span data-stu-id="65fb0-136">For the lightweight Office 365 dev/test environment, open the Internet browser on your computer and go to [https://aka.ms/e5trial](https://aka.ms/e5trial).</span></span> 
    
    <span data-ttu-id="65fb0-137">Stellen Sie für die simulierte Office 365-Entwicklungs-/Testumgebung über das Azure-Portal eine Verbindung mit CLIENT1 mit dem CORP\User1-Konto her.</span><span class="sxs-lookup"><span data-stu-id="65fb0-137">For the simulated enterprise Office 365 dev/test environment, connect to CLIENT1 with the CORP\User1 account from the Azure portal.</span></span>

    <span data-ttu-id="65fb0-138">Führen Sie vom Startbildschirm Microsoft Edge aus, und wechseln Sie zu [https://aka.ms/e5trial](https://aka.ms/e5trial).</span><span class="sxs-lookup"><span data-stu-id="65fb0-138">From the Start screen, run Microsoft Edge and go to [https://aka.ms/e5trial](https://aka.ms/e5trial).</span></span>
    
2. <span data-ttu-id="65fb0-139">Geben Sie auf der Seite **Willkommen, Grundlegendes zu Ihrer Person** die folgenden Informationen an:</span><span class="sxs-lookup"><span data-stu-id="65fb0-139">On the **Welcome, let's get to know you** page, specify:</span></span>
    
  - <span data-ttu-id="65fb0-140">Tatsächlicher Standort</span><span class="sxs-lookup"><span data-stu-id="65fb0-140">Your physical location</span></span>
    
  - <span data-ttu-id="65fb0-141">Vor- und Nachname des neuen Microsoft-Kontos</span><span class="sxs-lookup"><span data-stu-id="65fb0-141">The first and last name of your new Microsoft account</span></span>
    
  - <span data-ttu-id="65fb0-142">Die neue E-Mail-Kontoadresse</span><span class="sxs-lookup"><span data-stu-id="65fb0-142">Your new email account address</span></span>
    
  - <span data-ttu-id="65fb0-143">Telefonnummer geschäftlich</span><span class="sxs-lookup"><span data-stu-id="65fb0-143">A business phone number</span></span>
    
  - <span data-ttu-id="65fb0-144">Fiktiver Unternehmensname</span><span class="sxs-lookup"><span data-stu-id="65fb0-144">Your fictional company name</span></span>
    
  - <span data-ttu-id="65fb0-145">Unternehmensgröße zwischen 250-999 Mitarbeitern</span><span class="sxs-lookup"><span data-stu-id="65fb0-145">An organization size of 250-999 people</span></span>
    
3. <span data-ttu-id="65fb0-146">Klicken Sie auf **Nur noch ein Schritt**.</span><span class="sxs-lookup"><span data-stu-id="65fb0-146">Click **Just one more step**.</span></span>
    
4. <span data-ttu-id="65fb0-147">Geben Sie auf der Seite **Benutzer-ID erstellen** einen Benutzernamen auf Grundlage der neuen E-Mail-Adresse, den fiktiven Unternehmensnamen nach dem @-Zeichen (entfernen Sie alle Leerzeichen im Namen) und dann (zweimal) ein Kennwort für dieses neue Office 365-Konto ein. </span><span class="sxs-lookup"><span data-stu-id="65fb0-147">On the **Create your user ID** page, type a user name based on your new email address, your fictional company after the @ sign (remove all spaces in the name), then a password (twice) for this new Office 365 account.</span></span>
    
    <span data-ttu-id="65fb0-148">Notieren Sie das verwendete Kennwort, und bewahren Sie es an einem sicheren Ort auf.</span><span class="sxs-lookup"><span data-stu-id="65fb0-148">Record the password that you typed in a secure location.</span></span>
    
    <span data-ttu-id="65fb0-149">Notieren Sie hier den fiktiven Unternehmensnamen, der im Folgenden **Organisationsname** genannt wird: ![](./media/Common-Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="65fb0-149">Record your fictional company name, to be referred to as the **organization name**, here: ![](./media/Common-Images/TableLine.png)</span></span>
    
5. <span data-ttu-id="65fb0-150">Klicken Sie auf **Mein Konto erstellen**.</span><span class="sxs-lookup"><span data-stu-id="65fb0-150">Click **Create my account**.</span></span>
    
6. <span data-ttu-id="65fb0-p109">Geben Sie auf der Seite **Ich bin kein Roboter** die Rufnummer eines SMS-fähigen Mobiltelefons, und klicken Sie dann auf **SMS an mich**.</span><span class="sxs-lookup"><span data-stu-id="65fb0-p109">On the **Prove. You're. Not. A. Robot.** page, type the phone number of your text-capable phone, and then click **Text me**.</span></span>
    
7. <span data-ttu-id="65fb0-153">Geben Sie den Verifizierungscode ein, den Sie per SMS erhalten haben, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="65fb0-153">Type the verification code from the received text message, and then click **Next**.</span></span>
    
8. <span data-ttu-id="65fb0-154">Notieren Sie hier die URL der Anmeldeseite (auswählen und kopieren): ![](./media/Common-Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="65fb0-154">Record the sign-in page URL here (select and copy): ![](./media/Common-Images/TableLine.png)</span></span>
    
9. <span data-ttu-id="65fb0-155">Notieren Sie hier die Benutzer-ID (auswählen und kopieren): ![](./media/Common-Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="65fb0-155">Record the user ID here (select and copy): ![](./media/Common-Images/TableLine.png).onmicrosoft.com</span></span>
    
    <span data-ttu-id="65fb0-156">Dieser Wert wird **Name des globalen Office 365-Administrators** genannt.</span><span class="sxs-lookup"><span data-stu-id="65fb0-156">This value will be referred to as the **Office 365 global administrator name**.</span></span>
    
10. <span data-ttu-id="65fb0-157">Wenn **Alle Schritte wurden abgeschlossen.** angezeigt wird, klicken Sie darauf.</span><span class="sxs-lookup"><span data-stu-id="65fb0-157">When you see **You're ready to go**, click it.</span></span>
    
11. <span data-ttu-id="65fb0-158">Warten Sie auf der nächsten Seite, bis die Einrichtung von Office 365 abgeschlossen ist und alle Kacheln verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="65fb0-158">On the next page, wait until Office 365 completes setting up and all the tiles are available.</span></span>
    
<span data-ttu-id="65fb0-159">Nun sollte die Hauptseite des Office 365-Portals angezeigt werden, über die Sie auf Office-Dienste und das Microsoft 365 Admin Center zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="65fb0-159">You should see main Office 365 portal page from which you can access Office Online services and the Microsoft 365 Admin center.</span></span>
  
<span data-ttu-id="65fb0-160">So sieht die resultierende Konfiguration für die simulierte Office 365-Entwicklungs-/Testunternehmensumgebung aus.</span><span class="sxs-lookup"><span data-stu-id="65fb0-160">For the simulated enterprise Office 365 dev/test environment, here is your resulting configuration.</span></span>
  
![Die Office 365-Entwicklungs-/Testumgebung](media/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
<span data-ttu-id="65fb0-162">Diese Konfiguration besteht aus: </span><span class="sxs-lookup"><span data-stu-id="65fb0-162">This configuration consists of:</span></span> 
  
- <span data-ttu-id="65fb0-163">Den virtuellen DC1-, APP1- und CLIENT1-Computern in einem Subnetz eines virtuellen Azure-Netzwerks</span><span class="sxs-lookup"><span data-stu-id="65fb0-163">The DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
    
- <span data-ttu-id="65fb0-164">Einem Office 365 E5-Testabonnement</span><span class="sxs-lookup"><span data-stu-id="65fb0-164">An Office 365 E5 Trial Subscription.</span></span>
    
## <a name="phase-3-configure-your-office-365-trial-subscription"></a><span data-ttu-id="65fb0-165">Phase 3: Konfigurieren des Office 365-Testabonnements</span><span class="sxs-lookup"><span data-stu-id="65fb0-165">Phase 3: Configure your Office 365 trial subscription</span></span>

<span data-ttu-id="65fb0-166">In dieser Phase konfigurieren Sie Ihr Office 365-Abonnement mit weiteren Benutzern und weisen diesen Office 365 E5-Lizenzen zu.</span><span class="sxs-lookup"><span data-stu-id="65fb0-166">In this phase, you configure your Office 365 subscription with additional users and assign them Office 365 E5 licenses.</span></span>
  
<span data-ttu-id="65fb0-167">Befolgen Sie die Anweisungen unter [Verbinden mit Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-azure-active-directory-powershell-for-graph-module), um Ihr Office 365-Abonnement von folgenden Quellen aus mit dem Azure Active Directory PowerShell-Modul für Graph zu verbinden:</span><span class="sxs-lookup"><span data-stu-id="65fb0-167">Use the instructions in [Connect to Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-azure-active-directory-powershell-for-graph-module) to connect to your Office 365 subscription with the Azure Active Directory PowerShell for Graph module from:</span></span>
  
- <span data-ttu-id="65fb0-168">Ihrem Computer aus (für die einfache Office 365-Entwicklungs-/Testunternehmensumgebung).</span><span class="sxs-lookup"><span data-stu-id="65fb0-168">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="65fb0-169">Dem virtuellen Computer CLIENT1 aus (für die simulierte Office 365-Entwicklungs-/Testumgebung).</span><span class="sxs-lookup"><span data-stu-id="65fb0-169">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
 <span data-ttu-id="65fb0-170">Geben Sie in das Dialogfeld „Windows PowerShell Credential Request“ den Namen des globalen Office 365-Administrators (z. B. „jdoe@contosotoycompany.onmicrosoft.com“) und sein Kennwort ein.</span><span class="sxs-lookup"><span data-stu-id="65fb0-170">In the Windows PowerShell Credential Request dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password.</span></span>
  
<span data-ttu-id="65fb0-171">Geben Sie den Namen Ihrer Organisation (z. B. „contosotoycompany“), den zweistelligen Ländercode für Ihren Standort und ein gemeinsames Kontokennwort ein, und führen Sie dann die folgenden Befehle von der PowerShell-Eingabeaufforderung aus:</span><span class="sxs-lookup"><span data-stu-id="65fb0-171">Fill in your organization name (example: contosotoycompany), the two-character country code for your location, a common account password, and then run the following commands from the PowerShell prompt:</span></span>

```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$commonPW="<common user account password>"
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPW

$userUPN= "user2@" + $orgName + ".onmicrosoft.com"
New-AzureADUser -DisplayName "User 2" -GivenName User -SurName 2 -UserPrincipalName $userUPN -UsageLocation $loc -AccountEnabled $true -PasswordProfile $PasswordProfile -MailNickName "user2"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value "ENTERPRISEPREMIUM" -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign

$userUPN= "user3@" + $orgName + ".onmicrosoft.com"
New-AzureADUser -DisplayName "User 3" -GivenName User -SurName 3 -UserPrincipalName $userUPN -UsageLocation $loc -AccountEnabled $true -PasswordProfile $PasswordProfile -MailNickName "user3"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value "ENTERPRISEPREMIUM" -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign

$userUPN= "user4@" + $orgName + ".onmicrosoft.com"
New-AzureADUser -DisplayName "User 4" -GivenName User -SurName 4 -UserPrincipalName $userUPN -UsageLocation $loc -AccountEnabled $true -PasswordProfile $PasswordProfile -MailNickName "user4"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value "ENTERPRISEPREMIUM" -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

<!--
> [!TIP]
> Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-fe3d7a34) to get a text file that has all the PowerShell commands in this article.
-->

  
## <a name="phase-4-create-three-new-sharepoint-online-team-sites-optional"></a><span data-ttu-id="65fb0-172">Phase 4: Erstellen von drei neuen SharePoint Online-Teamwebsites (optional)</span><span class="sxs-lookup"><span data-stu-id="65fb0-172">Phase 4: Create three new SharePoint Online team sites (optional)</span></span>

<span data-ttu-id="65fb0-173">In dieser Phase konfigurieren Sie eine Reihe von SharePoint Online-Teamwebsites.</span><span class="sxs-lookup"><span data-stu-id="65fb0-173">In this phase, you configure a set of SharePoint Online team sites.</span></span>
  
1. <span data-ttu-id="65fb0-174">Installieren Sie die [SharePoint Online-Verwaltungsshell](https://go.microsoft.com/fwlink/p/?LinkId=255251) (die x64-Version).</span><span class="sxs-lookup"><span data-stu-id="65fb0-174">Install the [SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251) (the x64 version).</span></span>
    
2. <span data-ttu-id="65fb0-175">Klicken Sie auf **Start**, geben Sie **sharepoint** ein, und klicken Sie dann auf **SharePoint Online-Verwaltungsshell**.</span><span class="sxs-lookup"><span data-stu-id="65fb0-175">Click **Start**, type **sharepoint**, and then click **SharePoint Online Management Shell**.</span></span>
    
3. <span data-ttu-id="65fb0-176">Geben Sie den Namen Ihrer Organisation ein (Beispiel: contosotoycompany), und führen Sie dann über die Eingabeaufforderung der SharePoint Online-Verwaltungsshell die folgenden Befehle aus, um eine Verbindung mit dem SharePoint Online-Dienst herzustellen.</span><span class="sxs-lookup"><span data-stu-id="65fb0-176">Fill in your organization name (example: contosotoycompany), and then run the following commands from the SharePoint Online Management Shell prompt to connect to the SharePoint Online service</span></span>
```
$orgName="<organization name>"
$spURL="https://" + $orgName + "-admin.sharepoint.com"
Connect-SPOService -Url $spURL
```

4. <span data-ttu-id="65fb0-177">Geben Sie in das Dialogfeld **Microsoft SharePoint Online Management Shell** den Namen des globalen Office 365-Administrators (z. B. „jdoe@contosotoycompany.onmicrosoft.com“) und sein Kennwort ein, und klicken Sie auf **Anmelden**.</span><span class="sxs-lookup"><span data-stu-id="65fb0-177">In the **Microsoft SharePoint Online Management Shell** dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="65fb0-178">Geben Sie zum Erstellen von drei neuen Teamwebsites (Sales, Produktion und Support) den Namen des globalen Office 365-Administrators ein, und führen dann über die Eingabeaufforderung der SharePoint Online-Verwaltungsshell die folgenden Befehle aus:</span><span class="sxs-lookup"><span data-stu-id="65fb0-178">To create three new team sites (Sales, Production, and Support), fill in the Office 365 global administrator name, and then run the following commands from the SharePoint Online Management Shell prompt:</span></span>
    
  ```
  $owner = "<global administrator account name>"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/sales"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Sales site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/production"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Production site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/support"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Support site collection" -Template "STS#0"
  ```

6. <span data-ttu-id="65fb0-179">Führen Sie diesen Befehl aus, um die URLs der neuen Websites abzurufen:</span><span class="sxs-lookup"><span data-stu-id="65fb0-179">Run this command to list the URLs of these new sites:</span></span>
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

7. <span data-ttu-id="65fb0-180">Geben Sie im Internet Explorer die URL der Website „Produktion“ ein, um die standardmäßige SharePoint Online-Teamwebsite für die Abteilung „Produktion“ anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="65fb0-180">In Internet Explorer, enter the URL of the Production site to see the default SharePoint Online team site for the Production department.</span></span>
    
## <a name="record-values-for-future-reference"></a><span data-ttu-id="65fb0-181">Notieren von Werten für zukünftige Verwendung</span><span class="sxs-lookup"><span data-stu-id="65fb0-181">Record values for future reference</span></span>

<span data-ttu-id="65fb0-182">Notieren Sie die folgenden Werte für die Arbeit mit oder Bereitstellen von zusätzlichen Leitfäden für Test Lab in dieser Testumgebung:</span><span class="sxs-lookup"><span data-stu-id="65fb0-182">Record these values for working with or deploying additional Test Lab Guides in this test environment:</span></span>
  
- <span data-ttu-id="65fb0-183">Name des globalen Office 365-Administrators: ![](./media/Common-Images/TableLine.png).onmicrosoft.com (aus Schritt 9 von Phase 2)</span><span class="sxs-lookup"><span data-stu-id="65fb0-183">Office 365 global administrator name: ![](./media/Common-Images/TableLine.png).onmicrosoft.com (from step 9 of Phase 2)</span></span>
    
    <span data-ttu-id="65fb0-184">Notieren Sie auch das Kennwort für dieses Konto, und bewahren Sie es an einem sicheren Ort auf.</span><span class="sxs-lookup"><span data-stu-id="65fb0-184">Also record the password for this account in a secure location.</span></span>
    
- <span data-ttu-id="65fb0-185">Organisationsname für das Testabonnement: ![](./media/Common-Images/TableLine.png) (aus Schritt 4 von Phase 2)</span><span class="sxs-lookup"><span data-stu-id="65fb0-185">Your trial subscription organization name: ![](./media/Common-Images/TableLine.png) (from step 4 of Phase 2)</span></span>
    
- <span data-ttu-id="65fb0-186">Führen Sie über die „Windows Azure Active Directory-Modul für Windows PowerShell“-Eingabeaufforderung den folgenden Befehl aus, um die Konten für Benutzer 2, Benutzer 3, Benutzer 4 und Benutzer 5 anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="65fb0-186">To list the accounts for User 2, User 3, User 4, and User 5, run the following command from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
    
  ```
  Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName
  ```

    <span data-ttu-id="65fb0-187">Notieren Sie hier die Kontonamen:</span><span class="sxs-lookup"><span data-stu-id="65fb0-187">Record the account names here:</span></span>
    
  - <span data-ttu-id="65fb0-188">Kontoname für Benutzer 2: benutzer2@![](./media/Common-Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="65fb0-188">User 2 account name: user2@![](./media/Common-Images/TableLine.png).onmicrosoft.com</span></span>
    
  - <span data-ttu-id="65fb0-189">Kontoname für Benutzer 3: benutzer3@![](./media/Common-Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="65fb0-189">User 3 account name: user3@![](./media/Common-Images/TableLine.png).onmicrosoft.com</span></span>
    
  - <span data-ttu-id="65fb0-190">Kontoname für Benutzer 4: benutzer4@![](./media/Common-Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="65fb0-190">User 4 account name: user4@![](./media/Common-Images/TableLine.png).onmicrosoft.com</span></span>
    
  - <span data-ttu-id="65fb0-191">Kontoname für Benutzer 5: benutzer5@![](./media/Common-Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="65fb0-191">User 5 account name: user5@![](./media/Common-Images/TableLine.png).onmicrosoft.com</span></span>
    
    <span data-ttu-id="65fb0-192">Notieren Sie auch die Kennwörter für diese Konten, und bewahren Sie sie an einem sicheren Ort auf.</span><span class="sxs-lookup"><span data-stu-id="65fb0-192">Also record the passwords for these accounts in a secure location.</span></span>
    
- <span data-ttu-id="65fb0-193">(Optional) Führen Sie über die Eingabeaufforderung der SharePoint Online-Verwaltungsshell den folgenden Befehl aus, um die URLs für die Teamwebsites „Sales“, „Produktion“ und „Support“ anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="65fb0-193">(optional) To list the URLs for the Sales, Production, and Support team sites, run the following command from the SharePoint Online Management Shell prompt:</span></span>
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

  - <span data-ttu-id="65fb0-194">URL der Website „Produktion“: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/produktion</span><span class="sxs-lookup"><span data-stu-id="65fb0-194">Production site URL: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/production</span></span>
    
  - <span data-ttu-id="65fb0-195">URL der Website „Sales“: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/sales</span><span class="sxs-lookup"><span data-stu-id="65fb0-195">Sales site URL: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/sales</span></span>
    
  - <span data-ttu-id="65fb0-196">URL der Website „Support“: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/support</span><span class="sxs-lookup"><span data-stu-id="65fb0-196">Support site URL: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/support</span></span>
    
## <a name="next-steps"></a><span data-ttu-id="65fb0-197">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="65fb0-197">Next steps</span></span>

<span data-ttu-id="65fb0-198">Verwenden Sie die folgenden zusätzlichen Artikel in Ihrer Office 365-Entwicklungs-/Testumgebung:</span><span class="sxs-lookup"><span data-stu-id="65fb0-198">Use these additional articles in your Office 365 dev/test environment:</span></span>
  
- [<span data-ttu-id="65fb0-199">Verzeichnissynchronisierung für die Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="65fb0-199">Directory Synchronization for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="65fb0-200">Multi-Factor Authentication für die Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="65fb0-200">Multi-factor authentication for your Office 365 dev/test environment</span></span>](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="65fb0-201">Verbundidentität für Ihre Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="65fb0-201">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="65fb0-202">Advanced Threat Protection für die Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="65fb0-202">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="65fb0-203">Advanced eDiscovery für die Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="65fb0-203">Advanced eDiscovery for your Office 365 dev/test environment</span></span>](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="65fb0-204">Schutz vertraulicher Dateien in Office 365-Entwicklungs-/-Testumgebungen</span><span class="sxs-lookup"><span data-stu-id="65fb0-204">Sensitive file protection in the Office 365 dev/test environment</span></span>](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="65fb0-205">Isolierte SharePoint Online-Teamwebsite in Ihrer Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="65fb0-205">Isolated SharePoint Online team site dev/test environment</span></span>](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
- [<span data-ttu-id="65fb0-206">Datenklassifizierung und -kennzeichnung in Office 365-Entwicklungs-/-Testumgebungen</span><span class="sxs-lookup"><span data-stu-id="65fb0-206">Data classification and labeling in the Office 365 dev/test environment</span></span>](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
## <a name="see-also"></a><span data-ttu-id="65fb0-207">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="65fb0-207">See Also</span></span>

- [<span data-ttu-id="65fb0-208">Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz</span><span class="sxs-lookup"><span data-stu-id="65fb0-208">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
- [<span data-ttu-id="65fb0-209">Cloudakzeptanz und Hybridlösungen</span><span class="sxs-lookup"><span data-stu-id="65fb0-209">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


