---
title: Verbinden mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/30/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: 'Zusammenfassung: Stellen Sie mithilfe von Office 365 PowerShell eine Verbindung mit Ihrer Office 365-Organisation her, um Admin Center-Aufgaben über die Befehlszeile auszuführen.'
ms.openlocfilehash: c5bf5204d8ca1c8db35635f080031838e9fbea03
ms.sourcegitcommit: 86a740dccf273d679a8938e11e60d2a497c01689
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2019
ms.locfileid: "37328153"
---
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="fc1dc-103">Verbinden mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="fc1dc-103">Connect to Office 365 PowerShell</span></span>

 <span data-ttu-id="fc1dc-104">**Zusammenfassung:** Stellen Sie mithilfe von Office 365 PowerShell eine Verbindung mit Ihrer Office 365-Organisation her, um Verwaltungsaufgaben über die Befehlszeile auszuführen.</span><span class="sxs-lookup"><span data-stu-id="fc1dc-104">**Summary:** Connect to your Office 365 organization using Office 365 PowerShell to perform administration tasks from the command line.</span></span>
  
<span data-ttu-id="fc1dc-105">Mit Office 365 PowerShell können Sie Ihre Office 365-Einstellungen über die Befehlszeile verwalten.</span><span class="sxs-lookup"><span data-stu-id="fc1dc-105">Office 365 PowerShell lets you manage your Office 365 settings from the command line.</span></span> <span data-ttu-id="fc1dc-106">Das Herstellen einer Verbindung mit Office 365 PowerShell ist ein einfacher Vorgang, bei dem Sie die erforderliche Software installieren und dann eine Verbindung mit Ihrer Office 365-Organisation herstellen.</span><span class="sxs-lookup"><span data-stu-id="fc1dc-106">Connecting to  O365_PowerShell is a simple three-step process where you install the required software, run the required software, and then connect to your O365_W14_2nd organization.</span></span> 

<span data-ttu-id="fc1dc-107">Es gibt zwei Versionen des PowerShell-Moduls, mit denen Sie die Verbindung zu Office 365 herstellen und Benutzerkonten, Gruppen und Lizenzen verwalten:</span><span class="sxs-lookup"><span data-stu-id="fc1dc-107">There are two versions of the PowerShell module that you use to connect to Office 365 and administer user accounts, groups, and licenses:</span></span>

- <span data-ttu-id="fc1dc-108">Azure Active Directory PowerShell für Graph (Cmdlets enthalten **AzureAD** in ihrem Namen)</span><span class="sxs-lookup"><span data-stu-id="fc1dc-108">Azure Active Directory PowerShell for Graph (cmdlets include **AzureAD** in their name)</span></span> 
- <span data-ttu-id="fc1dc-109">Microsoft Azure Active Directory-Modul für Windows PowerShell (Cmdlets enthalten **MSol** in ihrem Namen)</span><span class="sxs-lookup"><span data-stu-id="fc1dc-109">Microsoft Azure Active Directory Module for Windows PowerShell (cmdlets include **MSol** in their name)</span></span> 

<span data-ttu-id="fc1dc-110">Zum Zeitpunkt des Erscheinens dieses Artikels ersetzt das Azure Active Directory PowerShell für Graph-Modul nicht vollständig die Funktionen in den Cmdlets des Microsoft Azure Active Directory-Moduls für Windows PowerShell für Benutzer-, Gruppen- und Lizenzverwaltung.</span><span class="sxs-lookup"><span data-stu-id="fc1dc-110">As of the date of this article, the Azure Active Directory PowerShell for Graph module does not completely replace the functionality in the cmdlets of Microsoft Azure Active Directory Module for Windows PowerShell module for user, group, and license administration.</span></span> <span data-ttu-id="fc1dc-111">In vielen Fällen müssen Sie beide Versionen verwenden.</span><span class="sxs-lookup"><span data-stu-id="fc1dc-111">In many cases, you need to use both versions.</span></span> <span data-ttu-id="fc1dc-112">Sie können problemlos beide Versionen auf demselben Computer installieren.</span><span class="sxs-lookup"><span data-stu-id="fc1dc-112">You can safely install both versions on the same computer.</span></span>

> [!TIP]
> <span data-ttu-id="fc1dc-113">**Neu bei PowerShell?**</span><span class="sxs-lookup"><span data-stu-id="fc1dc-113">**New to PowerShell?**</span></span> <span data-ttu-id="fc1dc-114">Sehen Sie sich ein [Video mit einer Übersicht über PowerShell](https://support.office.com/de-DE/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx) an, das Ihnen von LinkedIn Learning bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="fc1dc-114">See a [video Overview of PowerShell](https://support.office.com/de-DE/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), brought to you by LinkedIn Learning.</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="fc1dc-115">Was sollten Sie wissen, bevor Sie beginnen?</span><span class="sxs-lookup"><span data-stu-id="fc1dc-115">What do you need to know before you begin?</span></span>

- <span data-ttu-id="fc1dc-116">Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten</span><span class="sxs-lookup"><span data-stu-id="fc1dc-116">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="fc1dc-117">Sie können folgende Versionen von Windows verwenden:</span><span class="sxs-lookup"><span data-stu-id="fc1dc-117">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="fc1dc-118">Windows 10, Windows 8.1, Windows 8 oder Windows 7 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="fc1dc-118">Windows 10, Windows 8.1, Windows 8, or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="fc1dc-119">Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 oder Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="fc1dc-119">Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>

    > [!NOTE]
    > <span data-ttu-id="fc1dc-120">Sie müssen PowerShell 5.1 oder höher verwenden.</span><span class="sxs-lookup"><span data-stu-id="fc1dc-120">You must use PowerShell version 5.1 or later.</span></span> <span data-ttu-id="fc1dc-121">Für Windows 8.1, Windows 8, Windows 7 Service Pack 1 (SP1), Windows Server 2012 R2, Windows Server 2012 und Windows Server 2008 R2 SP1 laden Sie [Windows Management Framework 5.1](https://www.microsoft.com/download/details.aspx?id=54616) herunter. und installieren Sie es.</span><span class="sxs-lookup"><span data-stu-id="fc1dc-121">For Windows 8.1, Windows 8, Windows 7 Service Pack 1 (SP1), Windows Server 2012 R2, Windows Server 2012, and Windows Server 2008 R2 SP1, download and install the [Windows Management Framework 5.1](https://www.microsoft.com/download/details.aspx?id=54616).</span></span> 
    
    > [!NOTE]
    ><span data-ttu-id="fc1dc-122">Verwenden Sie eine 64-Bit-Version von Windows.</span><span class="sxs-lookup"><span data-stu-id="fc1dc-122">Use a 64-bit version of Windows.</span></span> <span data-ttu-id="fc1dc-123">Die Unterstützung für die 32-Bit-Version des Microsoft Azure Active Directory-Moduls für Windows PowerShell wurde im Oktober 2014 eingestellt.</span><span class="sxs-lookup"><span data-stu-id="fc1dc-123">Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
-  <span data-ttu-id="fc1dc-124">Diese Verfahren sind für Benutzer vorgesehen, die Mitglieder einer Office 365-Administratorrolle sind.</span><span class="sxs-lookup"><span data-stu-id="fc1dc-124">These procedures are intended for users who are members of an Office 365 admin role.</span></span> <span data-ttu-id="fc1dc-125">Weitere Informationen finden Sie unter [Informationen zu Administratorrollen von Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span><span class="sxs-lookup"><span data-stu-id="fc1dc-125">For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="fc1dc-126">Herstellen einer Verbindung mit dem Azure Active Directory PowerShell für Graph-Modul</span><span class="sxs-lookup"><span data-stu-id="fc1dc-126">First, you Connect with the Azure Active Directory PowerShell for Graph module.</span></span>

<span data-ttu-id="fc1dc-127">Befehle im [Azure Active Directory PowerShell für Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)-Modul haben **AzureAD** in ihrem Cmdlet-Namen.</span><span class="sxs-lookup"><span data-stu-id="fc1dc-127">Commands in the [Azure Active Directory PowerShell for Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) module have **AzureAD** in their cmdlet name.</span></span>

<span data-ttu-id="fc1dc-128">Verwenden Sie für Verfahren, welche die neuen Cmdlets im Azure Active Directory PowerShell für Graph-Modul benötigen, die nachstehenden Schritte zum Installieren des Moduls und Herstellen einer Verbindung mit Ihrem Office 365-Abonnement.</span><span class="sxs-lookup"><span data-stu-id="fc1dc-128">For procedures that require the new cmdlets in the Azure Active Directory V2 PowerShell modulehttps://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory, use these steps to install the module and connect to your Office 365 subscription:</span></span>

>[!Note]
><span data-ttu-id="fc1dc-129">Informationen zur Unterstützung für verschiedene Versionen von Microsoft Windows finden Sie unter [Azure Active Directory PowerShell für Graph-Modul](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span><span class="sxs-lookup"><span data-stu-id="fc1dc-129">See [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) for information about the support for different versions of Microsoft Windows.</span></span>
>

### <a name="step-1-install-required-software"></a><span data-ttu-id="fc1dc-130">Schritt 1: Installieren der erforderlichen Software</span><span class="sxs-lookup"><span data-stu-id="fc1dc-130">Step 1: Install required software</span></span>

<span data-ttu-id="fc1dc-p107">Diese Schritte sind auf Ihrem Computer nur einmal erforderlich, nicht jedes Mal, wenn Sie eine Verbindung herstellen. Allerdings müssen Sie wahrscheinlich in regelmäßigen Abständen neuere Versionen der Software installieren.</span><span class="sxs-lookup"><span data-stu-id="fc1dc-p107">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1. <span data-ttu-id="fc1dc-133">Öffnen Sie eine Windows PowerShell-Eingabeaufforderung mit erhöhten Rechten (d. h., führen Sie Windows PowerShell als Administrator aus).</span><span class="sxs-lookup"><span data-stu-id="fc1dc-133">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="fc1dc-134">Führen Sie im Befehlsfenster **Administrator: Windows PowerShell** den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="fc1dc-134">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```
  Install-Module -Name AzureAD
  ```

<span data-ttu-id="fc1dc-135">Falls Sie gefragt werden, ob Sie ein Modul aus einem nicht vertrauenswürdigen Repository installieren möchten: Geben Sie **Y** ein, und drücken Sie die EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="fc1dc-135">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="fc1dc-136">Schritt 2: Herstellen einer Verbindung mit Azure AD für Ihr Office 365-Abonnement</span><span class="sxs-lookup"><span data-stu-id="fc1dc-136">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="fc1dc-137">Wenn Sie eine Verbindung mit Azure AD für Ihr Office 365-Abonnement mit einem Kontonamen und Kennwort oder mit *mehrstufiger Authentifizierung (Multi-Factor Authentication, MFA)* herstellen möchten, führen Sie einen dieser Befehle an einer Windows PowerShell-Eingabeaufforderung aus (sie muss nicht über erhöhte Rechte verfügen).</span><span class="sxs-lookup"><span data-stu-id="fc1dc-137">To connect to Azure AD for your Office 365 subscription with an account name and password or with *multi-factor authentication (MFA)*, run one of these commands from a Windows PowerShell command prompt (it does not have to be elevated).</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="fc1dc-138">**Office 365-Cloud**</span><span class="sxs-lookup"><span data-stu-id="fc1dc-138">**Office 365 cloud**</span></span> | <span data-ttu-id="fc1dc-139">**Befehl**</span><span class="sxs-lookup"><span data-stu-id="fc1dc-139">**Command**</span></span> |
| <span data-ttu-id="fc1dc-140">Office 365 weltweit (+GCC)</span><span class="sxs-lookup"><span data-stu-id="fc1dc-140">Office 365 Worldwide (+GCC)</span></span> | `Connect-AzureAD` |
| <span data-ttu-id="fc1dc-141">Office 365, betrieben von 21Vianet</span><span class="sxs-lookup"><span data-stu-id="fc1dc-141">Office 365 operated by 21 Vianet</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| <span data-ttu-id="fc1dc-142">Office 365 Deutschland</span><span class="sxs-lookup"><span data-stu-id="fc1dc-142">Office 365 Germany</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| <span data-ttu-id="fc1dc-143">Office 365 U.S. Government DoD und Office 365 U.S. Government GCC High</span><span class="sxs-lookup"><span data-stu-id="fc1dc-143">Office 365 U.S. Government DoD and Office 365 U.S. Government GCC High</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

<span data-ttu-id="fc1dc-144">Geben Sie im Dialogfeld**Anmelden bei Ihrem Konto** den Benutzernamen und das Kennwort für Ihr Office 365-Geschäfts-, Schul- oder Unikonto ein, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="fc1dc-144">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="fc1dc-145">Wenn Sie MFA verwenden, befolgen Sie die Anweisungen in den zusätzlichen Dialogfeldern, um weitere Authentifizierungsinformationen, z. B. einen Überprüfungscode, bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="fc1dc-145">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>


<span data-ttu-id="fc1dc-146">Nach dem Herstellen der Verbindung können Sie die neuen Cmdlets für das [Azure Active Directory PowerShell für Graph-Modul](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) verwenden.</span><span class="sxs-lookup"><span data-stu-id="fc1dc-146">After connecting, you can use the new cmdlets for the [Azure Active Directory V2 PowerShell modulehttps://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="fc1dc-147">Herstellen einer Verbindung mit dem Microsoft Azure Active Directory-Modul für Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="fc1dc-147">Open the Microsoft Azure Active Directory Module for Windows PowerShell.</span></span>

<span data-ttu-id="fc1dc-148">Die Befehle im Microsoft Azure Active Directory-Modul für Windows PowerShell enthalten **Msol** in ihrem Cmdlet-Namen.</span><span class="sxs-lookup"><span data-stu-id="fc1dc-148">Commands in the Microsoft Azure Active Directory Module for Windows PowerShell have **Msol** in their cmdlet name.</span></span>
    
### <a name="step-1-install-required-software"></a><span data-ttu-id="fc1dc-149">Schritt 1: Installieren der erforderlichen Software</span><span class="sxs-lookup"><span data-stu-id="fc1dc-149">Step 1: Install required software</span></span>

<span data-ttu-id="fc1dc-p108">Diese Schritte sind auf Ihrem Computer nur einmal erforderlich, nicht jedes Mal, wenn Sie eine Verbindung herstellen. Allerdings müssen Sie wahrscheinlich in regelmäßigen Abständen neuere Versionen der Software installieren.</span><span class="sxs-lookup"><span data-stu-id="fc1dc-p108">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="fc1dc-152">Installieren Sie die 64-Bit-Version des Microsoft Online Services-Anmeldeassistenten: [Microsoft Online Services-Anmeldeassistent für IT-Experten RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span><span class="sxs-lookup"><span data-stu-id="fc1dc-152">Install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTWhttps://go.microsoft.com/fwlink/p/?LinkId=286152](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="fc1dc-153">Installieren Sie das Microsoft Azure Active Directory-Modul für Windows PowerShell mit den folgenden Schritten:</span><span class="sxs-lookup"><span data-stu-id="fc1dc-153">Install the Azure Active Directory Module for Windows PowerShell:</span></span>
    
  - <span data-ttu-id="fc1dc-154">Öffnen Sie eine Windows PowerShell-Eingabeaufforderung mit erhöhten Rechten (d. h., führen Sie Windows PowerShell als Administrator aus).</span><span class="sxs-lookup"><span data-stu-id="fc1dc-154">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
  - <span data-ttu-id="fc1dc-155">Führen Sie den Befehl**Install-Module MSOnline** aus.</span><span class="sxs-lookup"><span data-stu-id="fc1dc-155">Run the **Install-Module MSOnline** command.</span></span>
  - <span data-ttu-id="fc1dc-156">Wenn Sie zum Installieren des NuGet-Anbieters aufgefordert werden, geben Sie **Y** ein, und drücken Sie die EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="fc1dc-156">If prompted to install the NuGet provider, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="fc1dc-157">Wenn Sie aufgefordert werden, das Modul von PSGallery zu installieren, geben Sie **Y** ein, und drücken Sie die EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="fc1dc-157">If prompted to install the module from PSGallery, type **Y** and press ENTER.</span></span>
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="fc1dc-158">Schritt 2: Herstellen einer Verbindung mit Azure AD für Ihr Office 365-Abonnement</span><span class="sxs-lookup"><span data-stu-id="fc1dc-158">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="fc1dc-159">Wenn Sie eine Verbindung mit Azure AD für Ihr Office 365-Abonnement mit einem Kontonamen und Kennwort oder mit *mehrstufiger Authentifizierung (Multi-Factor Authentication, MFA)* herstellen möchten, führen Sie einen dieser Befehle an einer Windows PowerShell-Eingabeaufforderung aus (sie muss nicht über erhöhte Rechte verfügen).</span><span class="sxs-lookup"><span data-stu-id="fc1dc-159">To connect to Azure AD for your Office 365 subscription with an account name and password or with *multi-factor authentication (MFA)*, run one of these commands from a Windows PowerShell command prompt (it does not have to be elevated).</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="fc1dc-160">**Office 365-Cloud**</span><span class="sxs-lookup"><span data-stu-id="fc1dc-160">**Office 365 cloud**</span></span> | <span data-ttu-id="fc1dc-161">**Befehl**</span><span class="sxs-lookup"><span data-stu-id="fc1dc-161">**Command**</span></span> |
| <span data-ttu-id="fc1dc-162">Office 365 weltweit (+GCC)</span><span class="sxs-lookup"><span data-stu-id="fc1dc-162">Office 365 Worldwide (+GCC)</span></span> | `Connect-MsolService` |
| <span data-ttu-id="fc1dc-163">Office 365, betrieben von 21Vianet</span><span class="sxs-lookup"><span data-stu-id="fc1dc-163">Office 365 operated by 21 Vianet</span></span> | `Connect-MsolService -AzureEnvironment AzureChinaCloud` |
| <span data-ttu-id="fc1dc-164">Office 365 Deutschland</span><span class="sxs-lookup"><span data-stu-id="fc1dc-164">Office 365 Germany</span></span> | `Connect-MsolService -AzureEnvironment AzureGermanyCloud` |
| <span data-ttu-id="fc1dc-165">Office 365 U.S. Government DoD und Office 365 U.S. Government GCC High</span><span class="sxs-lookup"><span data-stu-id="fc1dc-165">Office 365 U.S. Government DoD and Office 365 U.S. Government GCC High</span></span> | `Connect-MsolService -AzureEnvironment USGovernment` |
|||

<span data-ttu-id="fc1dc-166">Geben Sie im Dialogfeld**Anmelden bei Ihrem Konto** den Benutzernamen und das Kennwort für Ihr Office 365-Geschäfts-, Schul- oder Unikonto ein, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="fc1dc-166">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="fc1dc-167">Wenn Sie MFA verwenden, befolgen Sie die Anweisungen in den zusätzlichen Dialogfeldern, um weitere Authentifizierungsinformationen, z. B. einen Überprüfungscode, bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="fc1dc-167">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>

### <a name="how-do-you-know-this-worked"></a><span data-ttu-id="fc1dc-168">Woher wissen Sie, dass dieses Verfahren erfolgreich war?</span><span class="sxs-lookup"><span data-stu-id="fc1dc-168">How do you know this worked?</span></span>

<span data-ttu-id="fc1dc-169">Wenn Sie keine Fehlermeldungen erhalten, wurde die Verbindung erfolgreich hergestellt.</span><span class="sxs-lookup"><span data-stu-id="fc1dc-169">If you don't receive any errors, you connected successfully.</span></span> <span data-ttu-id="fc1dc-170">Ein schneller Test ist die Ausführung eines Office 365-Cmdlets, z. B. **Get-MsolUser**, und die Betrachtung der Ergebnisse.</span><span class="sxs-lookup"><span data-stu-id="fc1dc-170">A quick test is to run an O365_W14_2nd cmdlet—for example, Get-MsolUser—and see the results.</span></span>
  
<span data-ttu-id="fc1dc-171">Wenn Sie Fehlermeldungen erhalten, überprüfen Sie die folgenden Anforderungen:</span><span class="sxs-lookup"><span data-stu-id="fc1dc-171">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="fc1dc-172">**Ein häufig auftretendes Problem ist ein falsches Kennwort**.</span><span class="sxs-lookup"><span data-stu-id="fc1dc-172">A common problem is an incorrect password.</span></span> <span data-ttu-id="fc1dc-173">Führen Sie Schritt 2 erneut aus,</span><span class="sxs-lookup"><span data-stu-id="fc1dc-173">Run Step 2 again.</span></span> <span data-ttu-id="fc1dc-174">und achten Sie auf den Benutzernamen und das Kennwort, die Sie eingeben.</span><span class="sxs-lookup"><span data-stu-id="fc1dc-174">Run the three steps again and pay close attention to the user name and password you enter in Step 1.</span></span>
    
- <span data-ttu-id="fc1dc-175">**Das Microsoft Azure Active Directory-Modul für Windows PowerShell setzt voraus, dass das Feature Microsoft .NET Framework 3.5.* x* auf Ihrem Computer aktiviert ist\**. Es ist wahrscheinlich, dass auf Ihrem Computer eine neuere Version installiert ist (z. B. 4 oder 4.5*x\*), aber die Abwärtskompatibilität mit älteren Versionen von .NET Framework kann aktiviert oder deaktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="fc1dc-175">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5.* x* feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5.* x*), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled.</span></span> <span data-ttu-id="fc1dc-176">Weitere Informationen hierzu finden Sie in den folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="fc1dc-176">For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="fc1dc-177">Informationen zu Windows Server 2012 oder Windows Server 2012 R2 finden Sie unter [Aktivieren von .NET Framework 3.5 mithilfe des Assistenten zum Hinzufügen von Rollen und Features](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span><span class="sxs-lookup"><span data-stu-id="fc1dc-177">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="fc1dc-178">Informationen zu Windows 7 oder Windows Server 2008 R2 finden Sie unter[Das Azure Active Directory-Modul für Windows PowerShell kann nicht geöffnet werden](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span><span class="sxs-lookup"><span data-stu-id="fc1dc-178">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>

  - <span data-ttu-id="fc1dc-179">Informationen zu Windows 10, Windows 8.1 und Windows 8 finden Sie unter [Installieren von .NET Framework 3.5 unter Windows 10, Windows 8.1 und Windows 8](https://docs.microsoft.com/de-DE/dotnet/framework/install/dotnet-35-windows-10)</span><span class="sxs-lookup"><span data-stu-id="fc1dc-179">For Windows 10, Windows 8.1, and Windows 8, see [Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8](https://docs.microsoft.com/de-DE/dotnet/framework/install/dotnet-35-windows-10)</span></span>

  
- <span data-ttu-id="fc1dc-180">**Möglicherweise ist Ihre Version des Microsoft Azure Active Directory-Moduls für Windows PowerShell veraltet.**</span><span class="sxs-lookup"><span data-stu-id="fc1dc-180">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.**</span></span> <span data-ttu-id="fc1dc-181">Um dies zu überprüfen, führen Sie den folgenden Befehl in Office 365 PowerShell oder im Microsoft Azure Active Directory-Modul für Windows PowerShell aus:</span><span class="sxs-lookup"><span data-stu-id="fc1dc-181">To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="fc1dc-182">Wenn die zurückgegebene Versionsnummer niedriger als der Wert 1.0.8070.2 ist, deinstallieren Sie das Microsoft Azure Active Directory-Modul für Windows PowerShell, und installieren Sie die neueste Version über den Link in Schritt 1.</span><span class="sxs-lookup"><span data-stu-id="fc1dc-182">If the version number returned is lower than the value 1.0.8070.2, uninstall the Azure_AD_Module and install the latest version from the link in Step 1.</span></span>
    
- <span data-ttu-id="fc1dc-183">**Wenn Sie einen Verbindungsfehler erhalten, finden Sie in diesem Thema weitere Informationen:** [Fehler "Connect-MsolService: Ausnahme vom Typ ausgelöst"](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span><span class="sxs-lookup"><span data-stu-id="fc1dc-183">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" errorhttps://go.microsoft.com/fwlink/p/?LinkId=532377](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="fc1dc-184">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="fc1dc-184">See also</span></span>

- [<span data-ttu-id="fc1dc-185">Verwalten von Office 365 mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="fc1dc-185">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="fc1dc-186">Erste Schritte mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="fc1dc-186">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="fc1dc-187">Verbinden mit allen Office 365-Diensten in einem einzigen Windows PowerShell-Fenster</span><span class="sxs-lookup"><span data-stu-id="fc1dc-187">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
- [<span data-ttu-id="fc1dc-188">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="fc1dc-188">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
- [<span data-ttu-id="fc1dc-189">Connect-MsolService</span><span class="sxs-lookup"><span data-stu-id="fc1dc-189">Connect-MsolService</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532375)

