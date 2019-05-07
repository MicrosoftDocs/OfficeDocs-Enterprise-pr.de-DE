---
title: Verbinden mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/16/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: 'Zusammenfassung: Stellen Sie mithilfe von Office 365 PowerShell eine Verbindung mit Ihrer Office 365-Organisation her, um Aufgaben des Verwaltungs Centers über die Befehlszeile auszuführen.'
ms.openlocfilehash: 4c70f067558773ce7e2a6e27bab78f5c64965872
ms.sourcegitcommit: 0516a15c72f4bc8423a1d8112fd4d3e5f69896c8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2019
ms.locfileid: "33639776"
---
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="543e8-103">Verbinden mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="543e8-103">Connect to Office 365 PowerShell</span></span>

 <span data-ttu-id="543e8-104">**Zusammenfassung:** Stellen Sie mithilfe von Office 365 PowerShell eine Verbindung mit Ihrer Office 365-Organisation her, um Verwaltungsaufgaben über die Befehlszeile auszuführen.</span><span class="sxs-lookup"><span data-stu-id="543e8-104">**Summary:** Connect to your Office 365 organization using Office 365 PowerShell to perform administration tasks from the command line.</span></span>
  
<span data-ttu-id="543e8-105">Mit Office 365 PowerShell können Sie Ihre Office 365-Einstellungen über die Befehlszeile verwalten.</span><span class="sxs-lookup"><span data-stu-id="543e8-105">Office 365 PowerShell lets you manage your Office 365 settings from the command line.</span></span> <span data-ttu-id="543e8-106">Das Herstellen einer Verbindung mit Office 365 PowerShell ist ein einfacher Vorgang, bei dem Sie die erforderliche Software installieren und dann eine Verbindung mit Ihrer Office 365-Organisation herstellen.</span><span class="sxs-lookup"><span data-stu-id="543e8-106">Connecting to Office 365 PowerShell is a simple process where you install the required software and then connect to your Office 365 organization.</span></span> 

<span data-ttu-id="543e8-107">Es gibt zwei Versionen des PowerShell-Moduls, die Sie zum Herstellen einer Verbindung mit Office 365 und zum Verwalten von Benutzerkonten, Gruppen und Lizenzen verwenden:</span><span class="sxs-lookup"><span data-stu-id="543e8-107">There are two versions of the PowerShell module that you use to connect to Office 365 and administer user accounts, groups, and licenses:</span></span>

- <span data-ttu-id="543e8-108">Azure Active Directory PowerShell für Graph (Cmdlets schließen **AzureAD** in Ihrem Namen ein)</span><span class="sxs-lookup"><span data-stu-id="543e8-108">Azure Active Directory PowerShell for Graph (cmdlets include **AzureAD** in their name)</span></span> 
- <span data-ttu-id="543e8-109">Microsoft Azure Active Directory-Modul für Windows PowerShell (Cmdlets schließen **MSol** in Ihrem Namen ein)</span><span class="sxs-lookup"><span data-stu-id="543e8-109">Microsoft Azure Active Directory Module for Windows PowerShell (cmdlets include **MSol** in their name)</span></span> 

<span data-ttu-id="543e8-110">Ab dem Datum dieses Artikels ersetzt das Modul Azure Active Directory PowerShell für Graph nicht vollständig die Funktionalität in den Cmdlets des Microsoft Azure Active Directory-Moduls für Windows PowerShell-Modul für Benutzer-, Gruppen-und Lizenzverwaltung. .</span><span class="sxs-lookup"><span data-stu-id="543e8-110">As of the date of this article, the Azure Active Directory PowerShell for Graph module does not completely replace the functionality in the cmdlets of Microsoft Azure Active Directory Module for Windows PowerShell module for user, group, and license administration.</span></span> <span data-ttu-id="543e8-111">In vielen Fällen müssen beide Versionen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="543e8-111">In many cases, you need to use both versions.</span></span> <span data-ttu-id="543e8-112">Beide Versionen können problemlos auf demselben Computer installiert werden.</span><span class="sxs-lookup"><span data-stu-id="543e8-112">You can safely install both versions on the same computer.</span></span>

> [!TIP]
> <span data-ttu-id="543e8-113">**Neu bei PowerShell?**</span><span class="sxs-lookup"><span data-stu-id="543e8-113">**New to PowerShell?**</span></span> <span data-ttu-id="543e8-114">Sehen Sie sich eine [Video Übersicht über PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx)an, die Ihnen von LinkedIn Learning präsentiert wird.</span><span class="sxs-lookup"><span data-stu-id="543e8-114">See a [video Overview of PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), brought to you by LinkedIn Learning.</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="543e8-115">Was sollten Sie wissen, bevor Sie beginnen?</span><span class="sxs-lookup"><span data-stu-id="543e8-115">What do you need to know before you begin?</span></span>

- <span data-ttu-id="543e8-116">Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten</span><span class="sxs-lookup"><span data-stu-id="543e8-116">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="543e8-117">Sie können folgende Versionen von Windows verwenden:</span><span class="sxs-lookup"><span data-stu-id="543e8-117">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="543e8-118">Windows 10, Windows 8,1, Windows 8 oder Windows 7 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="543e8-118">Windows 10, Windows 8.1, Windows 8, or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="543e8-119">Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 oder Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="543e8-119">Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>
    
    > [!NOTE]
    ><span data-ttu-id="543e8-120">Verwenden Sie eine 64-Bit-Version von Windows.</span><span class="sxs-lookup"><span data-stu-id="543e8-120">Use a 64-bit version of Windows.</span></span> <span data-ttu-id="543e8-121">Unterstützung für die 32-Bit-Version das Microsoft Azure Active Directory-Modul für Windows PowerShell wurde im Oktober 2014 eingestellt.</span><span class="sxs-lookup"><span data-stu-id="543e8-121">Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
-  <span data-ttu-id="543e8-122">Diese Verfahren sind für Benutzer gedacht, die Mitglieder einer Office 365-Administratorrolle sind.</span><span class="sxs-lookup"><span data-stu-id="543e8-122">These procedures are intended for users who are members of an Office 365 admin role.</span></span> <span data-ttu-id="543e8-123">Weitere Informationen finden Sie unter [Informationen zu Office 365-Administratorrollen](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span><span class="sxs-lookup"><span data-stu-id="543e8-123">For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="543e8-124">Herstellen einer Verbindung mit dem Azure Active Directory PowerShell für Graph-Modul</span><span class="sxs-lookup"><span data-stu-id="543e8-124">Connect with the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="543e8-125">Befehle im [Azure Active Directory PowerShell für Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) -Modul haben **AzureAD** in Ihrem Cmdlet-Namen.</span><span class="sxs-lookup"><span data-stu-id="543e8-125">Commands in the [Azure Active Directory PowerShell for Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) module have **AzureAD** in their cmdlet name.</span></span>

<span data-ttu-id="543e8-126">Verfahren, für die die neuen Cmdlets im Azure Active Directory PowerShell für Graph-Modul erforderlich sind, finden Sie in den folgenden Schritten, um das Modul zu installieren und eine Verbindung mit Ihrem Office 365-Abonnement herzustellen.</span><span class="sxs-lookup"><span data-stu-id="543e8-126">For procedures that require the new cmdlets in the Azure Active Directory PowerShell for Graph module, use these steps to install the module and connect to your Office 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="543e8-127">Informationen zur Unterstützung verschiedener Versionen von Microsoft Windows finden Sie unter [Azure Active Directory PowerShell für Graph-Modul](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) .</span><span class="sxs-lookup"><span data-stu-id="543e8-127">See [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) for information about the support for different versions of Microsoft Windows.</span></span>
>

### <a name="step-1-install-required-software"></a><span data-ttu-id="543e8-128">Schritt 1: Installieren der erforderlichen Software</span><span class="sxs-lookup"><span data-stu-id="543e8-128">Step 1: Install required software</span></span>

<span data-ttu-id="543e8-p106">Diese Schritte sind auf Ihrem Computer nur einmal erforderlich, nicht jedes Mal, wenn Sie eine Verbindung herstellen. Allerdings müssen Sie wahrscheinlich in regelmäßigen Abständen neuere Versionen der Software installieren.</span><span class="sxs-lookup"><span data-stu-id="543e8-p106">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1. <span data-ttu-id="543e8-131">Öffnen Sie eine Windows PowerShell-Eingabeaufforderung mit erhöhten Rechten (d. h., führen Sie Windows PowerShell als Administrator aus).</span><span class="sxs-lookup"><span data-stu-id="543e8-131">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="543e8-132">Führen Sie im Befehlsfenster **Administrator: Windows PowerShell** den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="543e8-132">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```
  Install-Module -Name AzureAD
  ```

<span data-ttu-id="543e8-133">Falls Sie gefragt werden, ob Sie ein Modul aus einem nicht vertrauenswürdigen Repository installieren möchten: Geben Sie **Y** ein, und drücken Sie die EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="543e8-133">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="543e8-134">Schritt 2: Herstellen einer Verbindung mit Azure AD für Ihr Office 365-Abonnement</span><span class="sxs-lookup"><span data-stu-id="543e8-134">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="543e8-135">Wenn Sie eine Verbindung mit Azure AD für Ihr Office 365-Abonnement mit einem Kontonamen und Kennwort oder mit mehrstufiger *Authentifizierung (Multi-Factor Authentication, MFA)* herstellen möchten, führen Sie einen dieser Befehle an einer Windows PowerShell-Eingabeaufforderungen aus (er muss nicht erhöht werden).</span><span class="sxs-lookup"><span data-stu-id="543e8-135">To connect to Azure AD for your Office 365 subscription with an account name and password or with *multi-factor authentication (MFA)*, run one of these commands from a Windows PowerShell command prompt (it does not have to be elevated).</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="543e8-136">**Office 365 Cloud**</span><span class="sxs-lookup"><span data-stu-id="543e8-136">**Office 365 cloud**</span></span> | <span data-ttu-id="543e8-137">**Befehl**</span><span class="sxs-lookup"><span data-stu-id="543e8-137">**Command**</span></span> |
| <span data-ttu-id="543e8-138">Office 365 Worldwide (+ gcc)</span><span class="sxs-lookup"><span data-stu-id="543e8-138">Office 365 Worldwide (+GCC)</span></span> | `Connect-AzureAD` |
| <span data-ttu-id="543e8-139">Office 365, betrieben von 21 vianet</span><span class="sxs-lookup"><span data-stu-id="543e8-139">Office 365 operated by 21 Vianet</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| <span data-ttu-id="543e8-140">Office 365 Deutschland</span><span class="sxs-lookup"><span data-stu-id="543e8-140">Office 365 Germany</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| <span data-ttu-id="543e8-141">Office 365 u.s. Government DoD und Office 365 u.s. Government gcc High</span><span class="sxs-lookup"><span data-stu-id="543e8-141">Office 365 U.S. Government DoD and Office 365 U.S. Government GCC High</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

<span data-ttu-id="543e8-142">Geben Sie im Dialogfeld in **Ihr Konto anmelden** den Benutzernamen und das Kennwort Ihres Office 365-Kontos ein, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="543e8-142">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="543e8-143">Wenn Sie MFA verwenden, befolgen Sie die Anweisungen in den zusätzlichen Dialogfeldern, um weitere Authentifizierungsinformationen wie einen Überprüfungscode bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="543e8-143">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>


<span data-ttu-id="543e8-144">Nachdem Sie eine Verbindung hergestellt haben, können Sie die neuen Cmdlets für das [Azure Active Directory PowerShell für Graph-Modul](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)verwenden.</span><span class="sxs-lookup"><span data-stu-id="543e8-144">After connecting, you can use the new cmdlets for the [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="543e8-145">Herstellen einer Verbindung mit dem Microsoft Azure Active Directory-Modul für Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="543e8-145">Connect with the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="543e8-146">Befehle im Microsoft Azure Active Directory-Modul für Windows PowerShell haben **MSOL** in Ihrem Cmdlet-Namen.</span><span class="sxs-lookup"><span data-stu-id="543e8-146">Commands in the Microsoft Azure Active Directory Module for Windows PowerShell have **Msol** in their cmdlet name.</span></span>
    
### <a name="step-1-install-required-software"></a><span data-ttu-id="543e8-147">Schritt 1: Installieren der erforderlichen Software</span><span class="sxs-lookup"><span data-stu-id="543e8-147">Step 1: Install required software</span></span>

<span data-ttu-id="543e8-p107">Diese Schritte sind auf Ihrem Computer nur einmal erforderlich, nicht jedes Mal, wenn Sie eine Verbindung herstellen. Allerdings müssen Sie wahrscheinlich in regelmäßigen Abständen neuere Versionen der Software installieren.</span><span class="sxs-lookup"><span data-stu-id="543e8-p107">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="543e8-150">Installieren Sie die 64-Bit-Version des Microsoft Online Services-Anmelde-Assistenten: [Microsoft Online Services-Anmelde-Assistent für IT-Experten RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span><span class="sxs-lookup"><span data-stu-id="543e8-150">Install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="543e8-151">Installieren Sie das Microsoft Azure Active Directory-Modul für Windows PowerShell mit den folgenden Schritten:</span><span class="sxs-lookup"><span data-stu-id="543e8-151">Install the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="543e8-152">Öffnen Sie eine Windows PowerShell-Eingabeaufforderung mit erhöhten Rechten (d. h., führen Sie Windows PowerShell als Administrator aus).</span><span class="sxs-lookup"><span data-stu-id="543e8-152">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
  - <span data-ttu-id="543e8-153">Führen Sie den **MSOnline-Befehl install-module** aus.</span><span class="sxs-lookup"><span data-stu-id="543e8-153">Run the **Install-Module MSOnline** command.</span></span>
  - <span data-ttu-id="543e8-154">Wenn Sie aufgefordert werden, den NuGet-Anbieter zu installieren, geben Sie **Y** ein, und drücken Sie die EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="543e8-154">If prompted to install the NuGet provider, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="543e8-155">Wenn Sie aufgefordert werden, das Modul von PSGallery zu installieren, geben Sie **Y** ein, und drücken Sie die EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="543e8-155">If prompted to install the module from PSGallery, type **Y** and press ENTER.</span></span>
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="543e8-156">Schritt 2: Herstellen einer Verbindung mit Azure AD für Ihr Office 365-Abonnement</span><span class="sxs-lookup"><span data-stu-id="543e8-156">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="543e8-157">Wenn Sie eine Verbindung mit Azure AD für Ihr Office 365-Abonnement mit einem Kontonamen und Kennwort oder mit mehrstufiger *Authentifizierung (Multi-Factor Authentication, MFA)* herstellen möchten, führen Sie einen dieser Befehle an einer Windows PowerShell-Eingabeaufforderungen aus (er muss nicht erhöht werden).</span><span class="sxs-lookup"><span data-stu-id="543e8-157">To connect to Azure AD for your Office 365 subscription with an account name and password or with *multi-factor authentication (MFA)*, run one of these commands from a Windows PowerShell command prompt (it does not have to be elevated).</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="543e8-158">**Office 365 Cloud**</span><span class="sxs-lookup"><span data-stu-id="543e8-158">**Office 365 cloud**</span></span> | <span data-ttu-id="543e8-159">**Befehl**</span><span class="sxs-lookup"><span data-stu-id="543e8-159">**Command**</span></span> |
| <span data-ttu-id="543e8-160">Office 365 Worldwide (+ gcc)</span><span class="sxs-lookup"><span data-stu-id="543e8-160">Office 365 Worldwide (+GCC)</span></span> | `Connect-MsolService` |
| <span data-ttu-id="543e8-161">Office 365, betrieben von 21 vianet</span><span class="sxs-lookup"><span data-stu-id="543e8-161">Office 365 operated by 21 Vianet</span></span> | `Connect-MsolService -AzureEnvironment AzureChinaCloud` |
| <span data-ttu-id="543e8-162">Office 365 Deutschland</span><span class="sxs-lookup"><span data-stu-id="543e8-162">Office 365 Germany</span></span> | `Connect-MsolService -AzureEnvironment AzureGermanyCloud` |
| <span data-ttu-id="543e8-163">Office 365 u.s. Government DoD und Office 365 u.s. Government gcc High</span><span class="sxs-lookup"><span data-stu-id="543e8-163">Office 365 U.S. Government DoD and Office 365 U.S. Government GCC High</span></span> | `Connect-MsolService -AzureEnvironment USGovernment` |
|||

<span data-ttu-id="543e8-164">Geben Sie im Dialogfeld in **Ihr Konto anmelden** den Benutzernamen und das Kennwort Ihres Office 365-Kontos ein, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="543e8-164">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="543e8-165">Wenn Sie MFA verwenden, befolgen Sie die Anweisungen in den zusätzlichen Dialogfeldern, um weitere Authentifizierungsinformationen wie einen Überprüfungscode bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="543e8-165">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>

### <a name="how-do-you-know-this-worked"></a><span data-ttu-id="543e8-166">Woher wissen Sie, dass dieses Verfahren erfolgreich war?</span><span class="sxs-lookup"><span data-stu-id="543e8-166">How do you know this worked?</span></span>

<span data-ttu-id="543e8-167">Wenn Sie keine Fehlermeldungen erhalten, wurde die Verbindung erfolgreich hergestellt.</span><span class="sxs-lookup"><span data-stu-id="543e8-167">If you don't receive any errors, you connected successfully.</span></span> <span data-ttu-id="543e8-168">Ein kurzer Test besteht darin, ein Office 365-Cmdlet auszuführen, beispielsweise **Get-MsolUser** , und die Ergebnisse anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="543e8-168">A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="543e8-169">Wenn Sie Fehlermeldungen erhalten, überprüfen Sie die folgenden Anforderungen:</span><span class="sxs-lookup"><span data-stu-id="543e8-169">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="543e8-170">**Ein häufiges Problem ist ein falsches Kennwort**.</span><span class="sxs-lookup"><span data-stu-id="543e8-170">**A common problem is an incorrect password**.</span></span> <span data-ttu-id="543e8-171">Führen Sie Schritt 2 erneut aus.</span><span class="sxs-lookup"><span data-stu-id="543e8-171">Run Step 2 again.</span></span> <span data-ttu-id="543e8-172">und achten Sie auf den Benutzernamen und das Kennwort, die Sie eingeben.</span><span class="sxs-lookup"><span data-stu-id="543e8-172">and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="543e8-173">\* *Das Microsoft Azure Active Directory-Modul für Windows PowerShell erfordert, dass Microsoft .NET Framework 3,5.* x \* Feature ist auf Ihrem Computer aktiviert \* *. Es ist wahrscheinlich, dass auf Ihrem Computer eine neuere Version installiert ist (beispielsweise 4 oder 4,5.* x \*), aber Abwärtskompatibilität mit älteren Versionen von .NET Framework kann aktiviert oder deaktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="543e8-173">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5.* x* feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5.* x*), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled.</span></span> <span data-ttu-id="543e8-174">Weitere Informationen hierzu finden Sie in den folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="543e8-174">For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="543e8-175">Informationen zu Windows Server 2012 oder Windows Server 2012 R2 finden Sie unter [Aktivieren von .NET Framework 3,5 mithilfe des Assistenten zum Hinzufügen von Rollen und Features](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span><span class="sxs-lookup"><span data-stu-id="543e8-175">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="543e8-176">Unter Windows 7 oder Windows Server 2008 R2 finden Sie Informationen zum [Öffnen des Azure Active Directory-Moduls für Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370) .</span><span class="sxs-lookup"><span data-stu-id="543e8-176">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>

  - <span data-ttu-id="543e8-177">Informationen zu Windows 10, Windows 8,1 und Windows 8 finden Sie unter [Installieren von .NET Framework 3,5 unter Windows 10, Windows 8,1 und Windows 8](https://docs.microsoft.com/en-us/dotnet/framework/install/dotnet-35-windows-10) .</span><span class="sxs-lookup"><span data-stu-id="543e8-177">For Windows 10, Windows 8.1, and Windows 8, see [Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8](https://docs.microsoft.com/en-us/dotnet/framework/install/dotnet-35-windows-10)</span></span>

  
- <span data-ttu-id="543e8-178">**Möglicherweise ist Ihre Version des Microsoft Azure Active Directory-Moduls für Windows PowerShell veraltet.**</span><span class="sxs-lookup"><span data-stu-id="543e8-178">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.**</span></span> <span data-ttu-id="543e8-179">Führen Sie den folgenden Befehl in Office 365 PowerShell oder das Microsoft Azure Active Directory-Modul für Windows PowerShell aus:</span><span class="sxs-lookup"><span data-stu-id="543e8-179">To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="543e8-180">Wenn die zurückgegebene Versionsnummer niedriger als der Wert 1.0.8070.2 ist, deinstallieren Sie das Microsoft Azure Active Directory-Modul für Windows PowerShell, und installieren Sie die neueste Version über den Link in Schritt 1.</span><span class="sxs-lookup"><span data-stu-id="543e8-180">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install the latest version from the link in Step 1.</span></span>
    
- <span data-ttu-id="543e8-181">**Wenn ein Verbindungsfehler angezeigt wird, finden Sie weitere Informationen unter diesem Thema:** [Fehler "Connect-MsolService: Exception of type"](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span><span class="sxs-lookup"><span data-stu-id="543e8-181">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="543e8-182">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="543e8-182">See also</span></span>

- [<span data-ttu-id="543e8-183">Verwalten von Office 365 mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="543e8-183">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="543e8-184">Erste Schritte mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="543e8-184">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="543e8-185">Verbinden mit allen Office 365-Diensten in einem einzigen Windows PowerShell-Fenster</span><span class="sxs-lookup"><span data-stu-id="543e8-185">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
- [<span data-ttu-id="543e8-186">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="543e8-186">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
- [<span data-ttu-id="543e8-187">Connect-MsolService</span><span class="sxs-lookup"><span data-stu-id="543e8-187">Connect-MsolService</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532375)

