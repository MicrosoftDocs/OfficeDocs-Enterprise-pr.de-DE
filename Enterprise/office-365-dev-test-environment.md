---
title: Office 365-Entwicklungs-/Testumgebung
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/11/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 4f6035b8-2da3-4cf9-9657-5284d6364f7a
description: 'Zusammenfassung: Verwenden Sie diese Testumgebungsanleitung, um ein Office 365-Testabonnement für Analysen oder Entwicklungs-/Testumgebungen zu erstellen.'
ms.openlocfilehash: 07922965acfbd23f0f48094fda8b18bf0b66ef38
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2018
---
# <a name="office-365-devtest-environment"></a><span data-ttu-id="cee7c-103">Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="cee7c-103">Office 365 dev/test environment</span></span>

 <span data-ttu-id="cee7c-104">**Zusammenfassung:** Verwenden Sie diese Testumgebungsanleitung, um ein Office 365-Testabonnement für Analysen oder Entwicklungs-/Testumgebungen zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="cee7c-104">**Summary:** Use this Test Lab Guide to create an Office 365 trial subscription for evaluation or dev/test.</span></span>
  
<span data-ttu-id="cee7c-p101">Sie können ein Office 365-Testabonnement verwenden und eine Office 365-Entwicklungs-/Testumgebung für Anwendungen erstellen oder Features und Funktionen von Office 365 demonstrieren. Es gibt zwei Versionen:</span><span class="sxs-lookup"><span data-stu-id="cee7c-p101">You can use an Office 365 trial subscription and create an Office 365 dev/test environment for applications or to demonstrate features and capabilities of Office 365. There are two versions:</span></span>
  
- <span data-ttu-id="cee7c-107">Die einfache Office 365-Entwicklungs-/Testumgebung besteht aus einem Office 365-Testabonnement, auf das Sie von Ihrem Hauptcomputer aus zugreifen.</span><span class="sxs-lookup"><span data-stu-id="cee7c-107">The lightweight Office 365 dev/test environment consists of an Office 365 trial subscription that you access from your main computer.</span></span>
    
    <span data-ttu-id="cee7c-p102">Verwenden Sie diese Umgebung, wenn Sie schnell ein Feature demonstrieren möchten. Führen Sie für die einfache Office 365-Entwicklungs-/Testumgebungen nur die Schritte in Phase 2 und 3 dieses Artikels durch.</span><span class="sxs-lookup"><span data-stu-id="cee7c-p102">Use this environment when you want to quickly demonstrate a feature. For the lightweight Office 365 dev/test environment, complete phases 2 and 3 of this article.</span></span>
    
- <span data-ttu-id="cee7c-p103">Die simulierte Office 365-Entwicklungs-/Testunternehmensumgebung besteht aus einem Office 365-Testabonnement und einem vereinfachtem Organisationsintranet mit Internetverbindung, das in Microsoft Azure-Infrastrukturdiensten gehostet wird. Sie können diese Konfiguration vollständig in der Microsoft-Cloud erstellen.</span><span class="sxs-lookup"><span data-stu-id="cee7c-p103">The simulated enterprise Office 365 dev/test environment consists of an Office 365 trial subscription and a simplified organization intranet connected to the Internet, which is hosted in Microsoft Azure infrastructure services. You can build this configuration completely in the Microsoft cloud.</span></span>
    
    <span data-ttu-id="cee7c-p104">Verwenden Sie diese Umgebung, wenn Sie ein Feature oder eine App in einer Umgebung demonstrieren möchten,die einem gewöhnlichen Organisationsnetzwerk mit Internetverbindung ähnelt, oder für Features, für die diese Art von Umgebung erforderlich ist. Führen Sie für die simulierte Office 365-Entwicklungs-/Testunternehmensumgebung die Schritte in Phasen 1, 2 und 3 dieses Artikels durch.</span><span class="sxs-lookup"><span data-stu-id="cee7c-p104">Use this environment when you want to demonstrate a feature or an app in an environment that resembles a typical organization network connected to the Internet, or for features that require this type of environment. For the simulated enterprise Office 365 dev/test environment, complete phases 1, 2, and 3 of this article.</span></span>
    
> [!NOTE]
> <span data-ttu-id="cee7c-p105">Sie können diesen Artikel auch ausdrucken, um die bestimmten Werte zu notieren, die Sie für diese Umgebung in den kommenden 30 Tage des Office 365-Testabonnements benötigen. Sie können das Testabonnement einfach um weitere 30 Tage verlängern. Für eine dauerhafte Entwicklungs-/Testumgebung erstellen Sie ein neues bezahltes Abonnement mit einer kleinen Anzahl von Lizenzen.</span><span class="sxs-lookup"><span data-stu-id="cee7c-p105">You might want to print this article to record the specific values that you will need for this environment over the 30 days of the Office 365 trial subscription. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
![Testumgebungsanleitungen in der Microsoft Cloud](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="cee7c-118">Klicken Sie [hier](http://aka.ms/catlgstack), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in der Microsoft Cloud zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="cee7c-118">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-the-base-configuration-in-azure"></a><span data-ttu-id="cee7c-119">Phase 1: Erstellen der Basiskonfiguration in Azure</span><span class="sxs-lookup"><span data-stu-id="cee7c-119">Phase 1: Create the base configuration in Azure</span></span>

<span data-ttu-id="cee7c-120">Befolgen Sie die Anweisungen unter [Basiskonfiguration der Entwicklungs-/Testumgebung](base-configuration-dev-test-environment.md)</span><span class="sxs-lookup"><span data-stu-id="cee7c-120">Follow the instructions in [Base Configuration dev/test environment](base-configuration-dev-test-environment.md).</span></span>
  
<span data-ttu-id="cee7c-p106">Sie benötigen ein Azure-Abonnement. Sie können die [kostenlose Testversion von Azure](https://azure.microsoft.com/pricing/free-trial/) für diese Konfiguration verwenden. Wenn Sie über ein MSDN- oder Visual Studio-Abonnement verfügen, lesen Sie die Informationen unter [Monatliche Azure-Gutschrift für Visual Studio-Abonnenten](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span><span class="sxs-lookup"><span data-stu-id="cee7c-p106">You will need an Azure subscription. You can use the [Azure Free Trialhttps://azure.microsoft.com/pricing/free-trial/](https://azure.microsoft.com/pricing/free-trial/) for this configuration. If you have an MSDN or Visual Studio subscription, see [Monthly Azure credit for Visual Studio subscribershttps://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span></span>
  
<span data-ttu-id="cee7c-124">Nachfolgend sehen Sie die daraus resultierende Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="cee7c-124">Here is the resulting configuration.</span></span>
  
![Die Basiskonfiguration der Entwicklungs-/ Testumgebung in Azure](images/63108214-f716-46ae-9974-072ff15b44a2.png)
  
<span data-ttu-id="cee7c-126">Diese Konfiguration besteht aus virtuellen DC1-, APP1- und CLIENT1-Computern in einem Subnetz eines virtuellen Azure-Netzwerks.</span><span class="sxs-lookup"><span data-stu-id="cee7c-126">This configuration consists of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
  
## <a name="phase-2-create-an-office-365-trial-subscription"></a><span data-ttu-id="cee7c-127">Phase 2: Erstellen eines Office 365-Testabonnements</span><span class="sxs-lookup"><span data-stu-id="cee7c-127">Phase 2: Create an Office 365 trial subscription</span></span>

<span data-ttu-id="cee7c-128">Für das Office 365 E5-Testabonnement benötigen Sie zunächst einen fiktiven Unternehmensnamen und ein neues Microsoft-Konto.</span><span class="sxs-lookup"><span data-stu-id="cee7c-128">To start your Office 365 E5 trial subscription, you first need a fictitious company name and a new Microsoft account.</span></span>
  
1. <span data-ttu-id="cee7c-p107">Es wird empfohlen, eine Variante von „Contoso“ als Unternehmensnamen zu verwenden. Dies ist ein fiktives Unternehmen, das von Microsoft in Beispielen verwendet wird. Notieren Sie hier Ihren fiktiven Unternehmensnamen: ![](./images/Common_Images/TableLine.png).</span><span class="sxs-lookup"><span data-stu-id="cee7c-p107">We recommend that you use a variant of the company name Contoso for your company name, which is a fictitious company used in Microsoft sample content, but it isn’t required. Record your fictitious company name here: _____________________________________![](./images/Common_Images/TableLine.png)</span></span>
    
2. <span data-ttu-id="cee7c-p108">Wenn Sie sich für ein neues Microsoft-Konto registrieren möchten, wechseln Sie zu [https://outlook.com](https://outlook.com), und erstellen Sie ein Konto mit neuem E-Mail-Konto und neuer E-Mail-Adresse. Dieses Konto wird für die Registrierung für Office 365 verwendet.</span><span class="sxs-lookup"><span data-stu-id="cee7c-p108">To sign up for a new Microsoft account, go to  https://outlook.com https://outlook.com  and create an account with a new email account and address. You will use this account to sign up for Office 365.</span></span>
    
  - <span data-ttu-id="cee7c-133">Notieren Sie hier den Vor- und Nachnamen des Kontos: ![](./images/Common_Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="cee7c-133">Record the first and last name of your new account here: _______________________________![](./images/Common_Images/TableLine.png)</span></span>
    
  - <span data-ttu-id="cee7c-134">Notieren Sie hier die neue E-Mail-Kontoadresse: ![](./images/Common_Images/TableLine.png)@outlook.com</span><span class="sxs-lookup"><span data-stu-id="cee7c-134">Record the new email account address here: _____________________________@outlook.com</span></span>
    
### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a><span data-ttu-id="cee7c-135">Registrieren für ein Office 365 E5-Testabonnement</span><span class="sxs-lookup"><span data-stu-id="cee7c-135">Sign up for an Office 365 E5 trial subscription</span></span>

1. <span data-ttu-id="cee7c-136">Öffnen Sie für die einfache Office 365-Entwicklungs-/Testumgebung den Internetbrowser auf Ihrem Computer, und gehen Sie zu [https://aka.ms/e5trial](https://aka.ms/e5trial). </span><span class="sxs-lookup"><span data-stu-id="cee7c-136">For the lightweight Office 365 dev/test environment, open the Internet browser on your computer and go to  https://aka.ms/e5trial https://aka.ms/e5trial .</span></span> 
    
    <span data-ttu-id="cee7c-137">Stellen Sie für die simulierte Office 365-Entwicklungs-/Testumgebung über das Azure-Portal eine Verbindung mit CLIENT1 mit dem CORP\User1-Konto her.</span><span class="sxs-lookup"><span data-stu-id="cee7c-137">For the simulated enterprise Office 365 dev/test environment, connect to CLIENT1 with the CORP\User1 account from the Azure portal.</span></span>

    <span data-ttu-id="cee7c-138">Führen Sie vom Startbildschirm Microsoft Edge aus, und wechseln Sie zu [https://aka.ms/e5trial](https://aka.ms/e5trial).</span><span class="sxs-lookup"><span data-stu-id="cee7c-138">From the Start screen, run Microsoft Edge and go to [https://aka.ms/e5trial](https://aka.ms/e5trial).</span></span>
    
2. <span data-ttu-id="cee7c-139">Geben Sie auf der Seite **Willkommen, Grundlegendes zu Ihrer Person** die folgenden Informationen an:</span><span class="sxs-lookup"><span data-stu-id="cee7c-139">On the **Welcome, let’s get to know you** page, specify:</span></span>
    
  - <span data-ttu-id="cee7c-140">Tatsächlicher Standort</span><span class="sxs-lookup"><span data-stu-id="cee7c-140">Your physical location</span></span>
    
  - <span data-ttu-id="cee7c-141">Vor- und Nachname des neuen Microsoft-Kontos</span><span class="sxs-lookup"><span data-stu-id="cee7c-141">The first and last name of your new Microsoft account</span></span>
    
  - <span data-ttu-id="cee7c-142">Die neue E-Mail-Kontoadresse</span><span class="sxs-lookup"><span data-stu-id="cee7c-142">Your new email account address</span></span>
    
  - <span data-ttu-id="cee7c-143">Telefonnummer geschäftlich</span><span class="sxs-lookup"><span data-stu-id="cee7c-143">A business phone number</span></span>
    
  - <span data-ttu-id="cee7c-144">Fiktiver Unternehmensname</span><span class="sxs-lookup"><span data-stu-id="cee7c-144">Your fictional company name</span></span>
    
  - <span data-ttu-id="cee7c-145">Unternehmensgröße zwischen 250-999 Mitarbeitern</span><span class="sxs-lookup"><span data-stu-id="cee7c-145">An organization size of 250-999 people</span></span>
    
3. <span data-ttu-id="cee7c-146">Klicken Sie auf **Nur noch ein Schritt**.</span><span class="sxs-lookup"><span data-stu-id="cee7c-146">Click **Just one more step**.</span></span>
    
4. <span data-ttu-id="cee7c-147">Geben Sie auf der Seite **Benutzer-ID erstellen** einen Benutzernamen auf Grundlage der neuen E-Mail-Adresse, den fiktiven Unternehmensnamen nach dem @-Zeichen (entfernen Sie alle Leerzeichen im Namen) und dann (zweimal) ein Kennwort für dieses neue Office 365-Konto ein. </span><span class="sxs-lookup"><span data-stu-id="cee7c-147">On the **Create your user ID** page, type a user name based on your new email address, your fictional company after the @ sign (remove all spaces in the name), then a password (twice) for this new Office 365 account.</span></span>
    
    <span data-ttu-id="cee7c-148">Notieren Sie das verwendete Kennwort, und bewahren Sie es an einem sicheren Ort auf.</span><span class="sxs-lookup"><span data-stu-id="cee7c-148">Record the password that you typed in a secure location.</span></span>
    
    <span data-ttu-id="cee7c-149">Notieren Sie hier den fiktiven Unternehmensnamen, der im Folgenden **Organisationsname** genannt wird: ![](./images/Common_Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="cee7c-149">Record your fictional company name, to be referred to as the **organization name**, here: ________________________________________</span></span>
    
5. <span data-ttu-id="cee7c-150">Klicken Sie auf **Mein Konto erstellen**.</span><span class="sxs-lookup"><span data-stu-id="cee7c-150">Click **Create my account**.</span></span>
    
6. <span data-ttu-id="cee7c-p109">Geben Sie auf der Seite **Ich bin kein Roboter** die Rufnummer eines SMS-fähigen Mobiltelefons, und klicken Sie dann auf **SMS an mich**.</span><span class="sxs-lookup"><span data-stu-id="cee7c-p109">On the **Prove. You’re. Not. A. Robot.** page, type the phone number of your text-capable phone, and then click **Text me**.</span></span>
    
7. <span data-ttu-id="cee7c-153">Geben Sie den Verifizierungscode ein, den Sie per SMS erhalten haben, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="cee7c-153">Type the verification code from the received text message, and then click **Next**.</span></span>
    
8. <span data-ttu-id="cee7c-154">Notieren Sie hier die URL der Anmeldeseite (auswählen und kopieren): ![](./images/Common_Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="cee7c-154">Record the sign-in page URL here (select and copy): ___________________________________________![](./images/Common_Images/TableLine.png)</span></span>
    
9. <span data-ttu-id="cee7c-155">Notieren Sie hier die Benutzer-ID (auswählen und kopieren): ![](./images/Common_Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="cee7c-155">Record the user ID here (select and copy): __________________________________.onmicrosoft.com</span></span>
    
    <span data-ttu-id="cee7c-156">Dieser Wert wird **Name des globalen Office 365-Administrators** genannt.</span><span class="sxs-lookup"><span data-stu-id="cee7c-156">This value will  be referred to as the **Office 365 global administrator name**.</span></span>
    
10. <span data-ttu-id="cee7c-157">Wenn **Alle Schritte wurden abgeschlossen.** angezeigt wird, klicken Sie darauf.</span><span class="sxs-lookup"><span data-stu-id="cee7c-157">When you see **You’re ready to go**, click it.</span></span>
    
11. <span data-ttu-id="cee7c-158">Warten Sie auf der nächsten Seite, bis die Einrichtung von Office 365 abgeschlossen ist und alle Kacheln verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="cee7c-158">On the next page, wait until Office 365 completes setting up and all the tiles under Collaborate with Office Online are visible.</span></span>
    
<span data-ttu-id="cee7c-159">Nun sollte die Hauptseite des Office 365-Portals angezeigt werden, über die Sie auf Office Online-Dienste und das Office 365 Admin Center zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="cee7c-159">You should see main Office 365 portal page from which you can access Office Online services and the Office 365 Admin center.</span></span>
  
<span data-ttu-id="cee7c-160">So sieht die resultierende Konfiguration für die simulierte Office 365-Entwicklungs-/Testunternehmensumgebung aus.</span><span class="sxs-lookup"><span data-stu-id="cee7c-160">For the simulated enterprise Office 365 dev/test environment, here is your resulting configuration.</span></span>
  
![Die Office 365-Entwicklungs-/Testumgebung](images/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
<span data-ttu-id="cee7c-162">Diese Konfiguration besteht aus: </span><span class="sxs-lookup"><span data-stu-id="cee7c-162">This configuration consists of:</span></span> 
  
- <span data-ttu-id="cee7c-163">Den virtuellen DC1-, APP1- und CLIENT1-Computern in einem Subnetz eines virtuellen Azure-Netzwerks</span><span class="sxs-lookup"><span data-stu-id="cee7c-163">The DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
    
- <span data-ttu-id="cee7c-164">Einem Office 365 E5-Testabonnement</span><span class="sxs-lookup"><span data-stu-id="cee7c-164">An Office 365 E5 Trial Subscription.</span></span>
    
## <a name="phase-3-configure-your-office-365-trial-subscription"></a><span data-ttu-id="cee7c-165">Phase 3: Konfigurieren des Office 365-Testabonnements</span><span class="sxs-lookup"><span data-stu-id="cee7c-165">Phase 3: Configure your Office 365 trial subscription</span></span>

<span data-ttu-id="cee7c-166">In dieser Phase konfigurieren Sie das Office 365-Abonnement mit zusätzlichen Benutzern und SharePoint Online-Teamwebsites.</span><span class="sxs-lookup"><span data-stu-id="cee7c-166">In this phase, you configure your Office 365 subscription with additional users and SharePoint Online team sites.</span></span>
  
<span data-ttu-id="cee7c-167">Fügen Sie zunächst vier neue Benutzer hinzu, und weisen Sie ihnen E5-Lizenzen zu.</span><span class="sxs-lookup"><span data-stu-id="cee7c-167">First, you add four new users and assign them E5 licenses.</span></span>
  
<span data-ttu-id="cee7c-168">Befolgen Sie die Anweisungen unter [Verbinden mit Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) zum Installieren der PowerShell-Module und Verbinden mit dem neuen Office 365-Abonnement von:</span><span class="sxs-lookup"><span data-stu-id="cee7c-168">Use the instructions in [Connect to Office 365 PowerShellhttps://technet.microsoft.com/library/dn975125.aspx](https://technet.microsoft.com/library/dn975125.aspx) to install the PowerShell modules and connect to your new Office 365 subscription from:</span></span>
  
- <span data-ttu-id="cee7c-169">Ihrem Computer aus (für die einfache Office 365-Entwicklungs-/Testunternehmensumgebung).</span><span class="sxs-lookup"><span data-stu-id="cee7c-169">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="cee7c-170">Dem virtuellen Computer CLIENT1 aus (für die simulierte Office 365-Entwicklungs-/Testumgebung).</span><span class="sxs-lookup"><span data-stu-id="cee7c-170">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
 <span data-ttu-id="cee7c-171">Geben Sie in das Dialogfeld „Windows PowerShell Credential Request“ den Namen des globalen Office 365-Administrators (z. B. „jdoe@contosotoycompany.onmicrosoft.com“) und sein Kennwort ein.</span><span class="sxs-lookup"><span data-stu-id="cee7c-171">In the Windows PowerShell Credential Request dialog box, type the Office  365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password.</span></span>
  
<span data-ttu-id="cee7c-172">Geben Sie den Namen Ihrer Organisation (z. B. „contosotoycompany“) und den zweistelligen Ländercode für Ihren Standort ein. Führen Sie dann über die Eingabeaufforderung des Windows Azure Active Directory-Moduls für Windows PowerShell die folgenden Befehle aus:</span><span class="sxs-lookup"><span data-stu-id="cee7c-172">Fill in your organization name (example: contosotoycompany), the two-character country code for your location, and then run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "user2@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 2" -FirstName User -LastName 2 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```
> [!TIP]
> <span data-ttu-id="cee7c-173">Klicken Sie [hier](https://gallery.technet.microsoft.com/PowerShell-commands-for-fe3d7a34), um eine Textdatei zu erhalten, die alle PowerShell-Befehle in diesem Artikel enthält.</span><span class="sxs-lookup"><span data-stu-id="cee7c-173">Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-fe3d7a34) to get a text file that contains all of the PowerShell commands in this article.</span></span>

<span data-ttu-id="cee7c-174">Notieren Sie das generierte Kennwort für das Konto „Benutzer 2“ aus der **New-MsolUser**-Befehlsanzeige, und bewahren Sie es an einem sicheren Ort auf.</span><span class="sxs-lookup"><span data-stu-id="cee7c-174">From the display of the **New-MsolUser** command, note the generated password for the User 2 account and record it in a safe location.</span></span>
  
<span data-ttu-id="cee7c-175">Führen Sie über die „Windows Azure Active Directory-Modul für Windows PowerShell“-Eingabeaufforderung die folgenden Befehle aus:</span><span class="sxs-lookup"><span data-stu-id="cee7c-175">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user3@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 3" -FirstName User -LastName 3 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="cee7c-176">Notieren Sie das generierte Kennwort für das Konto „Benutzer 3“ aus der **New-MsolUser**-Befehlsanzeige, und bewahren Sie es an einem sicheren Ort auf.</span><span class="sxs-lookup"><span data-stu-id="cee7c-176">From the display of the **New-MsolUser** command, note the generated password for the User 3 account and record it in a safe location.</span></span>
  
<span data-ttu-id="cee7c-177">Führen Sie über die „Windows Azure Active Directory-Modul für Windows PowerShell“-Eingabeaufforderung die folgenden Befehle aus:</span><span class="sxs-lookup"><span data-stu-id="cee7c-177">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user4@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 4" -FirstName User -LastName 4 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="cee7c-178">Notieren Sie das generierte Kennwort für das Konto „Benutzer 4“ aus der **New-MsolUser**-Befehlsanzeige, und bewahren Sie es an einem sicheren Ort auf.</span><span class="sxs-lookup"><span data-stu-id="cee7c-178">From the display of the **New-MsolUser** command, note the generated password for the User 4 account and record it in a safe location.</span></span>
  
<span data-ttu-id="cee7c-179">Führen Sie über die „Windows Azure Active Directory-Modul für Windows PowerShell“-Eingabeaufforderung die folgenden Befehle aus:</span><span class="sxs-lookup"><span data-stu-id="cee7c-179">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user5@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 5" -FirstName User -LastName 5 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="cee7c-180">Notieren Sie das generierte Kennwort für das Konto „Benutzer 5“ aus der **New-MsolUser**-Befehlsanzeige, und bewahren Sie es an einem sicheren Ort auf.</span><span class="sxs-lookup"><span data-stu-id="cee7c-180">From the display of the **New-MsolUser** command, note the generated password for the User 5 account and record it in a safe location.</span></span>
  
<span data-ttu-id="cee7c-181">Im nächsten Schritt erstellen Sie drei neue SharePoint Online-Teamwebsites für die Abteilungen Sales, Produktion und Support.</span><span class="sxs-lookup"><span data-stu-id="cee7c-181">Next, you create three new SharePoint Online team sites for the Sales, Production, and Support departments.</span></span>
  
### <a name="create-three-new-sharepoint-online-team-sites"></a><span data-ttu-id="cee7c-182">Erstellen von drei neuen SharePoint Online-Teamwebsites</span><span class="sxs-lookup"><span data-stu-id="cee7c-182">Create three new SharePoint Online team sites</span></span>

1. <span data-ttu-id="cee7c-183">Installieren Sie die [SharePoint Online-Verwaltungsshell](https://go.microsoft.com/fwlink/p/?LinkId=255251) (die x64-Version).</span><span class="sxs-lookup"><span data-stu-id="cee7c-183">Install the [SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251) (the x64 version).</span></span>
    
2. <span data-ttu-id="cee7c-184">Klicken Sie auf **Start**, geben Sie **sharepoint** ein, und klicken Sie dann auf **SharePoint Online-Verwaltungsshell**.</span><span class="sxs-lookup"><span data-stu-id="cee7c-184">Click **Start**, type **sharepoint**, and then click **SharePoint Online Management Shell**.</span></span>
    
3. <span data-ttu-id="cee7c-185">Geben Sie den Namen Ihrer Organisation ein (Beispiel: contosotoycompany), und führen Sie dann über die Eingabeaufforderung der SharePoint Online-Verwaltungsshell die folgenden Befehle aus, um eine Verbindung mit dem SharePoint Online-Dienst herzustellen.</span><span class="sxs-lookup"><span data-stu-id="cee7c-185">Fill in your organization name (example: contosotoycompany), and then run the following commands from the SharePoint Online Management Shell prompt to connect to the SharePoint Online service</span></span>
```
$orgName="<organization name>"
$spURL="https://" + $orgName + "-admin.sharepoint.com"
Connect-SPOService -Url $spURL
```

4. <span data-ttu-id="cee7c-186">Geben Sie in das Dialogfeld **Microsoft SharePoint Online Management Shell** den Namen des globalen Office 365-Administrators (z. B. „jdoe@contosotoycompany.onmicrosoft.com“) und sein Kennwort ein, und klicken Sie auf **Anmelden**.</span><span class="sxs-lookup"><span data-stu-id="cee7c-186">In the **Microsoft SharePoint Online Management Shell** dialog box, type the Office  365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="cee7c-187">Geben Sie zum Erstellen von drei neuen Teamwebsites (Sales, Produktion und Support) den Namen des globalen Office 365-Administrators ein, und führen dann über die Eingabeaufforderung der SharePoint Online-Verwaltungsshell die folgenden Befehle aus:</span><span class="sxs-lookup"><span data-stu-id="cee7c-187">To create three new team sites (Sales, Production, and Support), fill in the Office  365 global administrator name, and then run the following commands from the SharePoint Online Management Shell prompt:</span></span>
    
  ```
  $owner = "<global administrator account name>"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/sales"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Sales site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/production"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Production site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/support"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Support site collection" -Template "STS#0"
  ```

6. <span data-ttu-id="cee7c-188">Führen Sie diesen Befehl aus, um die URLs der neuen Websites abzurufen:</span><span class="sxs-lookup"><span data-stu-id="cee7c-188">Run this command to list the URLs of these new sites:</span></span>
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

7. <span data-ttu-id="cee7c-189">Geben Sie im Internet Explorer die URL der Website „Produktion“ ein, um die standardmäßige SharePoint Online-Teamwebsite für die Abteilung „Produktion“ anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="cee7c-189">In Internet Explorer, enter the URL of the Production site to see the default SharePoint Online team site for the Production department.</span></span>
    
## <a name="record-values-for-future-reference"></a><span data-ttu-id="cee7c-190">Notieren von Werten für zukünftige Verwendung</span><span class="sxs-lookup"><span data-stu-id="cee7c-190">Record values for future reference</span></span>

<span data-ttu-id="cee7c-191">Notieren Sie die folgenden Werte für die Arbeit mit oder Bereitstellen von zusätzlichen Leitfäden für Test Lab in dieser Testumgebung:</span><span class="sxs-lookup"><span data-stu-id="cee7c-191">Record these values for working with or deploying additional Test Lab Guides in this test environment:</span></span>
  
- <span data-ttu-id="cee7c-192">Name des globalen Office 365-Administrators: ![](./images/Common_Images/TableLine.png).onmicrosoft.com (aus Schritt 9 von Phase 2)</span><span class="sxs-lookup"><span data-stu-id="cee7c-192">Office 365 global administrator name: ____________________________________.onmicrosoft.com (from step 9 of Phase 2)</span></span>
    
    <span data-ttu-id="cee7c-193">Notieren Sie auch das Kennwort für dieses Konto, und bewahren Sie es an einem sicheren Ort auf.</span><span class="sxs-lookup"><span data-stu-id="cee7c-193">Also record the password for this account in a secure location.</span></span>
    
- <span data-ttu-id="cee7c-194">Organisationsname für das Testabonnement: ![](./images/Common_Images/TableLine.png) (aus Schritt 4 von Phase 2)</span><span class="sxs-lookup"><span data-stu-id="cee7c-194">Your trial subscription organization name: _______________________________________________ (from step 4 of Phase 2)</span></span>
    
- <span data-ttu-id="cee7c-195">Führen Sie über die „Windows Azure Active Directory-Modul für Windows PowerShell“-Eingabeaufforderung den folgenden Befehl aus, um die Konten für Benutzer 2, Benutzer 3, Benutzer 4 und Benutzer 5 anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="cee7c-195">To list the accounts for User 2, User 3, User 4, and User 5, run the following command from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
    
  ```
  Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName
  ```

    <span data-ttu-id="cee7c-196">Notieren Sie hier die Kontonamen:</span><span class="sxs-lookup"><span data-stu-id="cee7c-196">Record the account names here:</span></span>
    
  - <span data-ttu-id="cee7c-197">Kontoname für Benutzer 2: benutzer2@![](./images/Common_Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="cee7c-197">User 2 account name: user2@_______________________________________________.onmicrosoft.com</span></span>
    
  - <span data-ttu-id="cee7c-198">Kontoname für Benutzer 3: benutzer3@![](./images/Common_Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="cee7c-198">User 3 account name: user3@_______________________________________________.onmicrosoft.com</span></span>
    
  - <span data-ttu-id="cee7c-199">Kontoname für Benutzer 4: benutzer4@![](./images/Common_Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="cee7c-199">User 4 account name: user4@_______________________________________________.onmicrosoft.com</span></span>
    
  - <span data-ttu-id="cee7c-200">Kontoname für Benutzer 5: benutzer5@![](./images/Common_Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="cee7c-200">User 5 account name: user5@_______________________________________________.onmicrosoft.com</span></span>
    
    <span data-ttu-id="cee7c-201">Notieren Sie auch die Kennwörter für diese Konten, und bewahren Sie sie an einem sicheren Ort auf.</span><span class="sxs-lookup"><span data-stu-id="cee7c-201">Also record the passwords for these accounts in a secure location.</span></span>
    
- <span data-ttu-id="cee7c-202">Führen Sie über die Eingabeaufforderung der SharePoint Online-Verwaltungsshell den folgenden Befehl aus, um die URLs für die Teamwebsites „Sales“, „Produktion“ und „Support“ anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="cee7c-202">To list the URLs for the Sales, Production, and Support team sites, run the following command from the SharePoint Online Management Shell prompt:</span></span>
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

  - <span data-ttu-id="cee7c-203">URL der Website „Produktion“: https://![](./images/Common_Images/TableLine.png).sharepoint.com/sites/produktion</span><span class="sxs-lookup"><span data-stu-id="cee7c-203">Production site URL:  https://______________________________________________.sharepoint.com/sites/production</span></span>
    
  - <span data-ttu-id="cee7c-204">URL der Website „Sales“: https://![](./images/Common_Images/TableLine.png).sharepoint.com/sites/sales</span><span class="sxs-lookup"><span data-stu-id="cee7c-204">Sales site URL: https://______________________________________________.sharepoint.com/sites/sales</span></span>
    
  - <span data-ttu-id="cee7c-205">URL der Website „Support“: https://![](./images/Common_Images/TableLine.png).sharepoint.com/sites/support</span><span class="sxs-lookup"><span data-stu-id="cee7c-205">Support site URL: https://______________________________________________.sharepoint.com/sites/support</span></span>
    
## <a name="next-steps"></a><span data-ttu-id="cee7c-206">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="cee7c-206">Next steps</span></span>

<span data-ttu-id="cee7c-207">Verwenden Sie die folgenden zusätzlichen Artikel in Ihrer Office 365-Entwicklungs-/Testumgebung:</span><span class="sxs-lookup"><span data-stu-id="cee7c-207">Use these additional articles in your Office 365 dev/test environment:</span></span>
  
- [<span data-ttu-id="cee7c-208">Verzeichnissynchronisierung für die Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="cee7c-208">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="cee7c-209">Multi-Factor Authentication für die Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="cee7c-209">Multi-factor authentication for your Office 365 dev/test environment</span></span>](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="cee7c-210">Verbundidentität für Ihre Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="cee7c-210">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="cee7c-211">Cloud App Security für Ihre Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="cee7c-211">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="cee7c-212">Advanced Threat Protection für die Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="cee7c-212">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="cee7c-213">Advanced eDiscovery für die Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="cee7c-213">Advanced eDiscovery for your Office 365 dev/test environment</span></span>](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="cee7c-214">Schutz vertraulicher Dateien in Office 365-Entwicklungs-/-Testumgebungen</span><span class="sxs-lookup"><span data-stu-id="cee7c-214">Sensitive file protection in the Office 365 dev/test environment</span></span>](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="cee7c-215">Isolierte SharePoint Online-Teamwebsite in Ihrer Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="cee7c-215">Isolated SharePoint Online team site dev/test environment</span></span>](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
- [<span data-ttu-id="cee7c-216">Datenklassifizierung und -kennzeichnung in Office 365-Entwicklungs-/-Testumgebungen</span><span class="sxs-lookup"><span data-stu-id="cee7c-216">Data classification and labeling in the Office 365 dev/test environment</span></span>](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
<span data-ttu-id="cee7c-217">Erweitern Sie Ihre Office 365-Entwicklungs-/Testumgebung um zusätzliche Microsoft-Cloudangebote:</span><span class="sxs-lookup"><span data-stu-id="cee7c-217">Extend your Office 365 dev/test environment to include additional Microsoft cloud offerings:</span></span>
  
- [<span data-ttu-id="cee7c-218">Die Microsoft 365 Enterprise-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="cee7c-218">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
    
- [<span data-ttu-id="cee7c-219">Office 365- und Dynamics 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="cee7c-219">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
    
## <a name="see-also"></a><span data-ttu-id="cee7c-220">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="cee7c-220">See Also</span></span>

- [<span data-ttu-id="cee7c-221">Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz</span><span class="sxs-lookup"><span data-stu-id="cee7c-221">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
- [<span data-ttu-id="cee7c-222">Office 365- und Dynamics 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="cee7c-222">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
  
- [<span data-ttu-id="cee7c-223">Cloudakzeptanz und Hybridlösungen</span><span class="sxs-lookup"><span data-stu-id="cee7c-223">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


