---
title: Verbinden mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/13/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: 'Zusammenfassung: Stellen Sie mithilfe von Office 365 PowerShell eine Verbindung mit Ihrer Office 365-Organisation her, um Admin Center-Aufgaben über die Befehlszeile auszuführen.'
ms.openlocfilehash: 96ad47e6f60d6e098deffb48c56b4004d732b033
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844256"
---
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="fb6a5-103">Verbinden mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="fb6a5-103">Connect to Office 365 PowerShell</span></span>

<span data-ttu-id="fb6a5-104">Mit Office 365 PowerShell können Sie Ihre Office 365-Einstellungen über die Befehlszeile verwalten.</span><span class="sxs-lookup"><span data-stu-id="fb6a5-104">Office 365 PowerShell lets you manage your Office 365 settings from the command line.</span></span> <span data-ttu-id="fb6a5-105">Das Herstellen einer Verbindung mit Office 365 PowerShell ist ein einfacher Vorgang, bei dem Sie die erforderliche Software installieren und dann eine Verbindung mit Ihrer Office 365-Organisation herstellen.</span><span class="sxs-lookup"><span data-stu-id="fb6a5-105">Connecting to Office 365 PowerShell is a simple process where you install the required software and then connect to your Office 365 organization.</span></span> 

<span data-ttu-id="fb6a5-106">Es gibt zwei Versionen des PowerShell-Moduls, mit denen Sie die Verbindung zu Office 365 herstellen und Benutzerkonten, Gruppen und Lizenzen verwalten:</span><span class="sxs-lookup"><span data-stu-id="fb6a5-106">There are two versions of the PowerShell module that you use to connect to Office 365 and administer user accounts, groups, and licenses:</span></span>

- <span data-ttu-id="fb6a5-107">Azure Active Directory PowerShell für Graph (Cmdlets enthalten **AzureAD** in ihrem Namen)</span><span class="sxs-lookup"><span data-stu-id="fb6a5-107">Azure Active Directory PowerShell for Graph (cmdlets include **AzureAD** in their name)</span></span>
- <span data-ttu-id="fb6a5-108">Microsoft Azure Active Directory-Modul für Windows PowerShell (Cmdlets enthalten **MSol** in ihrem Namen)</span><span class="sxs-lookup"><span data-stu-id="fb6a5-108">Microsoft Azure Active Directory Module for Windows PowerShell (cmdlets include **MSol** in their name)</span></span> 

<span data-ttu-id="fb6a5-109">Zum Zeitpunkt des Erscheinens dieses Artikels ersetzt das Azure Active Directory PowerShell für Graph-Modul nicht vollständig die Funktionen in den Cmdlets des Microsoft Azure Active Directory-Moduls für Windows PowerShell für Benutzer-, Gruppen- und Lizenzverwaltung.</span><span class="sxs-lookup"><span data-stu-id="fb6a5-109">As of the date of this article, the Azure Active Directory PowerShell for Graph module does not completely replace the functionality in the cmdlets of Microsoft Azure Active Directory Module for Windows PowerShell module for user, group, and license administration.</span></span> <span data-ttu-id="fb6a5-110">In vielen Fällen müssen Sie beide Versionen verwenden.</span><span class="sxs-lookup"><span data-stu-id="fb6a5-110">In many cases, you need to use both versions.</span></span> <span data-ttu-id="fb6a5-111">Sie können problemlos beide Versionen auf demselben Computer installieren.</span><span class="sxs-lookup"><span data-stu-id="fb6a5-111">You can safely install both versions on the same computer.</span></span>

## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="fb6a5-112">Was sollten Sie wissen, bevor Sie beginnen?</span><span class="sxs-lookup"><span data-stu-id="fb6a5-112">What do you need to know before you begin?</span></span>

<span data-ttu-id="fb6a5-113">Sie können folgende Versionen von Windows verwenden:</span><span class="sxs-lookup"><span data-stu-id="fb6a5-113">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="fb6a5-114">Windows 10, Windows 8.1, Windows 8 oder Windows 7 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="fb6a5-114">Windows 10, Windows 8.1, Windows 8, or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="fb6a5-115">Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 oder Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="fb6a5-115">Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>

    > [!NOTE]
    > <span data-ttu-id="fb6a5-116">Sie müssen PowerShell 5.1 oder höher verwenden.</span><span class="sxs-lookup"><span data-stu-id="fb6a5-116">You must use PowerShell version 5.1 or later.</span></span> <span data-ttu-id="fb6a5-117">Für Windows 8.1, Windows 8, Windows 7 Service Pack 1 (SP1), Windows Server 2012 R2, Windows Server 2012 und Windows Server 2008 R2 SP1 laden Sie [Windows Management Framework 5.1](https://www.microsoft.com/download/details.aspx?id=54616) herunter. und installieren Sie es.</span><span class="sxs-lookup"><span data-stu-id="fb6a5-117">For Windows 8.1, Windows 8, Windows 7 Service Pack 1 (SP1), Windows Server 2012 R2, Windows Server 2012, and Windows Server 2008 R2 SP1, download and install the [Windows Management Framework 5.1](https://www.microsoft.com/download/details.aspx?id=54616).</span></span> 
    
    > [!NOTE]
    ><span data-ttu-id="fb6a5-118">Verwenden Sie eine 64-Bit-Version von Windows.</span><span class="sxs-lookup"><span data-stu-id="fb6a5-118">Use a 64-bit version of Windows.</span></span> <span data-ttu-id="fb6a5-119">Die Unterstützung für die 32-Bit-Version des Microsoft Azure Active Directory-Moduls für Windows PowerShell wurde im Oktober 2014 eingestellt.</span><span class="sxs-lookup"><span data-stu-id="fb6a5-119">Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
<span data-ttu-id="fb6a5-120">Diese Verfahren sind für Benutzer vorgesehen, die Mitglieder einer Office 365-Administratorrolle sind.</span><span class="sxs-lookup"><span data-stu-id="fb6a5-120">These procedures are intended for users who are members of an Office 365 admin role.</span></span> <span data-ttu-id="fb6a5-121">Weitere Informationen finden Sie unter [Informationen zu Administratorrollen von Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span><span class="sxs-lookup"><span data-stu-id="fb6a5-121">For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="fb6a5-122">Herstellen einer Verbindung mit dem Azure Active Directory PowerShell für Graph-Modul</span><span class="sxs-lookup"><span data-stu-id="fb6a5-122">Connect with the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="fb6a5-123">Befehle im [Azure Active Directory PowerShell für Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)-Modul haben **AzureAD** in ihrem Cmdlet-Namen.</span><span class="sxs-lookup"><span data-stu-id="fb6a5-123">Commands in the [Azure Active Directory PowerShell for Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) module have **AzureAD** in their cmdlet name.</span></span>

<span data-ttu-id="fb6a5-124">Verwenden Sie für Verfahren, welche die neuen Cmdlets im Azure Active Directory PowerShell für Graph-Modul benötigen, die nachstehenden Schritte zum Installieren des Moduls und Herstellen einer Verbindung mit Ihrem Office 365-Abonnement.</span><span class="sxs-lookup"><span data-stu-id="fb6a5-124">For procedures that require the new cmdlets in the Azure Active Directory PowerShell for Graph module, use these steps to install the module and connect to your Office 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="fb6a5-125">Informationen zur Unterstützung für verschiedene Versionen von Microsoft Windows finden Sie unter [Azure Active Directory PowerShell für Graph-Modul](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span><span class="sxs-lookup"><span data-stu-id="fb6a5-125">See [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) for information about the support for different versions of Microsoft Windows.</span></span>
>

### <a name="step-1-install-required-software"></a><span data-ttu-id="fb6a5-126">Schritt 1: Installieren der erforderlichen Software</span><span class="sxs-lookup"><span data-stu-id="fb6a5-126">Step 1: Install required software</span></span>

<span data-ttu-id="fb6a5-p106">Diese Schritte sind auf Ihrem Computer nur einmal erforderlich, nicht jedes Mal, wenn Sie eine Verbindung herstellen. Allerdings müssen Sie wahrscheinlich in regelmäßigen Abständen neuere Versionen der Software installieren.</span><span class="sxs-lookup"><span data-stu-id="fb6a5-p106">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1. <span data-ttu-id="fb6a5-129">Öffnen Sie eine Windows PowerShell-Eingabeaufforderung mit erhöhten Rechten (d. h., führen Sie Windows PowerShell als Administrator aus).</span><span class="sxs-lookup"><span data-stu-id="fb6a5-129">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="fb6a5-130">Führen Sie im Befehlsfenster **Administrator: Windows PowerShell** den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="fb6a5-130">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```powershell
  Install-Module -Name AzureAD
  ```

<span data-ttu-id="fb6a5-131">Falls Sie gefragt werden, ob Sie ein Modul aus einem nicht vertrauenswürdigen Repository installieren möchten: Geben Sie **Y** ein, und drücken Sie die EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="fb6a5-131">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="fb6a5-132">Schritt 2: Herstellen einer Verbindung mit Azure AD für Ihr Office 365-Abonnement</span><span class="sxs-lookup"><span data-stu-id="fb6a5-132">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="fb6a5-133">Wenn Sie eine Verbindung mit Azure AD für Ihr Office 365-Abonnement mit einem Kontonamen und Kennwort oder mit mehrstufiger Authentifizierung (Multi-Factor Authentication, MFA) herstellen möchten, führen Sie einen dieser Befehle an einer Windows PowerShell-Eingabeaufforderung aus (sie muss nicht über erhöhte Rechte verfügen).</span><span class="sxs-lookup"><span data-stu-id="fb6a5-133">To connect to Azure AD for your Office 365 subscription with an account name and password or with multi-factor authentication (MFA), run one of these commands from a Windows PowerShell command prompt (it does not have to be elevated).</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="fb6a5-134">**Office 365-Cloud**</span><span class="sxs-lookup"><span data-stu-id="fb6a5-134">**Office 365 cloud**</span></span> | <span data-ttu-id="fb6a5-135">**Befehl**</span><span class="sxs-lookup"><span data-stu-id="fb6a5-135">**Command**</span></span> |
| <span data-ttu-id="fb6a5-136">Office 365 weltweit (+GCC)</span><span class="sxs-lookup"><span data-stu-id="fb6a5-136">Office 365 Worldwide (+GCC)</span></span> | `Connect-AzureAD` |
| <span data-ttu-id="fb6a5-137">Office 365, betrieben von 21Vianet</span><span class="sxs-lookup"><span data-stu-id="fb6a5-137">Office 365 operated by 21 Vianet</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| <span data-ttu-id="fb6a5-138">Office 365 Deutschland</span><span class="sxs-lookup"><span data-stu-id="fb6a5-138">Office 365 Germany</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| <span data-ttu-id="fb6a5-139">Office 365 U.S. Government DoD und Office 365 U.S. Government GCC High</span><span class="sxs-lookup"><span data-stu-id="fb6a5-139">Office 365 U.S. Government DoD and Office 365 U.S. Government GCC High</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

<span data-ttu-id="fb6a5-140">Geben Sie im Dialogfeld**Anmelden bei Ihrem Konto** den Benutzernamen und das Kennwort für Ihr Office 365-Geschäfts-, Schul- oder Unikonto ein, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="fb6a5-140">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="fb6a5-141">Wenn Sie MFA verwenden, befolgen Sie die Anweisungen in den zusätzlichen Dialogfeldern, um weitere Authentifizierungsinformationen, z. B. einen Überprüfungscode, bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="fb6a5-141">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>

<span data-ttu-id="fb6a5-142">Nach dem Herstellen der Verbindung können Sie die Cmdlets für das [Azure Active Directory PowerShell für Graph-Modul](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) verwenden.</span><span class="sxs-lookup"><span data-stu-id="fb6a5-142">After connecting, you can use the cmdlets for the [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="fb6a5-143">Herstellen einer Verbindung mit dem Microsoft Azure Active Directory-Modul für Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="fb6a5-143">Connect with the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="fb6a5-144">Die Befehle im Microsoft Azure Active Directory-Modul für Windows PowerShell enthalten **Msol** in ihrem Cmdlet-Namen.</span><span class="sxs-lookup"><span data-stu-id="fb6a5-144">Commands in the Microsoft Azure Active Directory Module for Windows PowerShell have **Msol** in their cmdlet name.</span></span>

>[!Note]
><span data-ttu-id="fb6a5-145">PowerShell Core unterstützt nicht das Microsoft Azure Active Directory-Modul für Windows PowerShell und Cmdlets mit **Msol** im Namen.</span><span class="sxs-lookup"><span data-stu-id="fb6a5-145">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="fb6a5-146">Um diese Cmdlets weiterhin verwenden zu können, müssen Sie sie über Windows PowerShell ausführen.</span><span class="sxs-lookup"><span data-stu-id="fb6a5-146">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>
    
### <a name="step-1-install-required-software"></a><span data-ttu-id="fb6a5-147">Schritt 1: Installieren der erforderlichen Software</span><span class="sxs-lookup"><span data-stu-id="fb6a5-147">Step 1: Install required software</span></span>

<span data-ttu-id="fb6a5-p108">Diese Schritte sind auf Ihrem Computer nur einmal erforderlich, nicht jedes Mal, wenn Sie eine Verbindung herstellen. Allerdings müssen Sie wahrscheinlich in regelmäßigen Abständen neuere Versionen der Software installieren.</span><span class="sxs-lookup"><span data-stu-id="fb6a5-p108">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="fb6a5-150">Installieren Sie die 64-Bit-Version des Microsoft Online Services-Anmeldeassistenten: [Microsoft Online Services-Anmeldeassistent für IT-Experten RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span><span class="sxs-lookup"><span data-stu-id="fb6a5-150">Install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="fb6a5-151">Installieren Sie das Microsoft Azure Active Directory-Modul für Windows PowerShell mit den folgenden Schritten:</span><span class="sxs-lookup"><span data-stu-id="fb6a5-151">Install the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="fb6a5-152">Öffnen Sie eine Windows PowerShell-Eingabeaufforderung mit erhöhten Rechten (d. h., führen Sie Windows PowerShell als Administrator aus).</span><span class="sxs-lookup"><span data-stu-id="fb6a5-152">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
  - <span data-ttu-id="fb6a5-153">Führen Sie den Befehl**Install-Module MSOnline** aus.</span><span class="sxs-lookup"><span data-stu-id="fb6a5-153">Run the **Install-Module MSOnline** command.</span></span>
  - <span data-ttu-id="fb6a5-154">Wenn Sie zum Installieren des NuGet-Anbieters aufgefordert werden, geben Sie **Y** ein, und drücken Sie die EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="fb6a5-154">If prompted to install the NuGet provider, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="fb6a5-155">Wenn Sie aufgefordert werden, das Modul von PSGallery zu installieren, geben Sie **Y** ein, und drücken Sie die EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="fb6a5-155">If prompted to install the module from PSGallery, type **Y** and press ENTER.</span></span>
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="fb6a5-156">Schritt 2: Herstellen einer Verbindung mit Azure AD für Ihr Office 365-Abonnement</span><span class="sxs-lookup"><span data-stu-id="fb6a5-156">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="fb6a5-157">Wenn Sie eine Verbindung mit Azure AD für Ihr Office 365-Abonnement mit einem Kontonamen und Kennwort oder mit mehrstufiger Authentifizierung (Multi-Factor Authentication, MFA) herstellen möchten, führen Sie einen dieser Befehle an einer Windows PowerShell-Eingabeaufforderung aus (sie muss nicht über erhöhte Rechte verfügen).</span><span class="sxs-lookup"><span data-stu-id="fb6a5-157">To connect to Azure AD for your Office 365 subscription with an account name and password or with multi-factor authentication (MFA), run one of these commands from a Windows PowerShell command prompt (it does not have to be elevated).</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="fb6a5-158">**Office 365-Cloud**</span><span class="sxs-lookup"><span data-stu-id="fb6a5-158">**Office 365 cloud**</span></span> | <span data-ttu-id="fb6a5-159">**Befehl**</span><span class="sxs-lookup"><span data-stu-id="fb6a5-159">**Command**</span></span> |
| <span data-ttu-id="fb6a5-160">Office 365 weltweit (+GCC)</span><span class="sxs-lookup"><span data-stu-id="fb6a5-160">Office 365 Worldwide (+GCC)</span></span> | `Connect-MsolService` |
| <span data-ttu-id="fb6a5-161">Office 365, betrieben von 21Vianet</span><span class="sxs-lookup"><span data-stu-id="fb6a5-161">Office 365 operated by 21 Vianet</span></span> | `Connect-MsolService -AzureEnvironment AzureChinaCloud` |
| <span data-ttu-id="fb6a5-162">Office 365 Deutschland</span><span class="sxs-lookup"><span data-stu-id="fb6a5-162">Office 365 Germany</span></span> | `Connect-MsolService -AzureEnvironment AzureGermanyCloud` |
| <span data-ttu-id="fb6a5-163">Office 365 U.S. Government DoD und Office 365 U.S. Government GCC High</span><span class="sxs-lookup"><span data-stu-id="fb6a5-163">Office 365 U.S. Government DoD and Office 365 U.S. Government GCC High</span></span> | `Connect-MsolService -AzureEnvironment USGovernment` |
|||

<span data-ttu-id="fb6a5-164">Geben Sie im Dialogfeld**Anmelden bei Ihrem Konto** den Benutzernamen und das Kennwort für Ihr Office 365-Geschäfts-, Schul- oder Unikonto ein, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="fb6a5-164">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="fb6a5-165">Wenn Sie MFA verwenden, befolgen Sie die Anweisungen in den zusätzlichen Dialogfeldern, um weitere Authentifizierungsinformationen, z. B. einen Überprüfungscode, bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="fb6a5-165">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>

### <a name="how-do-you-know-this-worked"></a><span data-ttu-id="fb6a5-166">Woher wissen Sie, dass dieses Verfahren erfolgreich war?</span><span class="sxs-lookup"><span data-stu-id="fb6a5-166">How do you know this worked?</span></span>

<span data-ttu-id="fb6a5-167">Wenn Sie keine Fehlermeldungen erhalten, wurde die Verbindung erfolgreich hergestellt.</span><span class="sxs-lookup"><span data-stu-id="fb6a5-167">If you don't receive any errors, you connected successfully.</span></span> <span data-ttu-id="fb6a5-168">Ein schneller Test ist die Ausführung eines Office 365-Cmdlets, z. B. **Get-MsolUser**, und die Betrachtung der Ergebnisse.</span><span class="sxs-lookup"><span data-stu-id="fb6a5-168">A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="fb6a5-169">Wenn Sie Fehlermeldungen erhalten, überprüfen Sie die folgenden Anforderungen:</span><span class="sxs-lookup"><span data-stu-id="fb6a5-169">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="fb6a5-170">**Ein häufig auftretendes Problem ist ein falsches Kennwort**.</span><span class="sxs-lookup"><span data-stu-id="fb6a5-170">**A common problem is an incorrect password**.</span></span> <span data-ttu-id="fb6a5-171">Führen Sie Schritt 2 erneut aus,</span><span class="sxs-lookup"><span data-stu-id="fb6a5-171">Run Step 2 again.</span></span> <span data-ttu-id="fb6a5-172">und achten Sie auf den Benutzernamen und das Kennwort, die Sie eingeben.</span><span class="sxs-lookup"><span data-stu-id="fb6a5-172">and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="fb6a5-173">**Das Microsoft Azure Active Directory-Modul für Windows PowerShell setzt voraus, dass das Feature Microsoft .NET Framework 3.5.* x* auf Ihrem Computer aktiviert ist\**. Es ist wahrscheinlich, dass auf Ihrem Computer eine neuere Version installiert ist (z. B. 4 oder 4.5*x\*), aber die Abwärtskompatibilität mit älteren Versionen von .NET Framework kann aktiviert oder deaktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="fb6a5-173">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5.* x* feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5.* x*), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled.</span></span> <span data-ttu-id="fb6a5-174">Weitere Informationen hierzu finden Sie in den folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="fb6a5-174">For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="fb6a5-175">Informationen zu Windows Server 2012 oder Windows Server 2012 R2 finden Sie unter [Aktivieren von .NET Framework 3.5 mithilfe des Assistenten zum Hinzufügen von Rollen und Features](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span><span class="sxs-lookup"><span data-stu-id="fb6a5-175">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="fb6a5-176">Informationen zu Windows 7 oder Windows Server 2008 R2 finden Sie unter[Das Azure Active Directory-Modul für Windows PowerShell kann nicht geöffnet werden](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span><span class="sxs-lookup"><span data-stu-id="fb6a5-176">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>

  - <span data-ttu-id="fb6a5-177">Informationen zu Windows 10, Windows 8.1 und Windows 8 finden Sie unter [Installieren von .NET Framework 3.5 unter Windows 10, Windows 8.1 und Windows 8](https://docs.microsoft.com/dotnet/framework/install/dotnet-35-windows-10)</span><span class="sxs-lookup"><span data-stu-id="fb6a5-177">For Windows 10, Windows 8.1, and Windows 8, see [Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8](https://docs.microsoft.com/dotnet/framework/install/dotnet-35-windows-10)</span></span>

  
- <span data-ttu-id="fb6a5-178">**Möglicherweise ist Ihre Version des Microsoft Azure Active Directory-Moduls für Windows PowerShell veraltet.**</span><span class="sxs-lookup"><span data-stu-id="fb6a5-178">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.**</span></span> <span data-ttu-id="fb6a5-179">Um dies zu überprüfen, führen Sie den folgenden Befehl in Office 365 PowerShell oder im Microsoft Azure Active Directory-Modul für Windows PowerShell aus:</span><span class="sxs-lookup"><span data-stu-id="fb6a5-179">To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```powershell
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="fb6a5-180">Wenn die zurückgegebene Versionsnummer niedriger als der Wert 1.0.8070.2 ist, deinstallieren Sie das Microsoft Azure Active Directory-Modul für Windows PowerShell, und installieren Sie die neueste Version über den Link in Schritt 1.</span><span class="sxs-lookup"><span data-stu-id="fb6a5-180">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install the latest version from the link in Step 1.</span></span>
    
- <span data-ttu-id="fb6a5-181">**Wenn Sie einen Verbindungsfehler erhalten, finden Sie in diesem Thema weitere Informationen:** [Fehler "Connect-MsolService: Ausnahme vom Typ ausgelöst"](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span><span class="sxs-lookup"><span data-stu-id="fb6a5-181">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="fb6a5-182">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="fb6a5-182">See also</span></span>

- [<span data-ttu-id="fb6a5-183">Verwalten von Office 365 mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="fb6a5-183">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="fb6a5-184">Erste Schritte mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="fb6a5-184">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="fb6a5-185">Verbinden mit allen Office 365-Diensten in einem einzigen Windows PowerShell-Fenster</span><span class="sxs-lookup"><span data-stu-id="fb6a5-185">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
