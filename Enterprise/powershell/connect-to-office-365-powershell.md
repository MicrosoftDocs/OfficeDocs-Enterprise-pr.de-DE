---
title: Verbinden mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/20/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: 'Zusammenfassung: Verbinden Sie mit Office 365-Organisation mithilfe von PowerShell für Office 365 Admin Center Aufgaben über die Befehlszeile ausführen.'
ms.openlocfilehash: 96406fbc23adadbf77a3cd02f8c167081f908977
ms.sourcegitcommit: c3869a332512dd1cc25cd5a92a340050f1da0418
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/20/2018
ms.locfileid: "20720401"
---
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="2710e-103">Verbinden mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="2710e-103">Connect to Office 365 PowerShell</span></span>

 <span data-ttu-id="2710e-104">**Zusammenfassung:** Verbinden Sie mit Office 365-Organisation mit Office 365 PowerShell Verwaltungsaufgaben über die Befehlszeile ausführen.</span><span class="sxs-lookup"><span data-stu-id="2710e-104">**Summary:** Connect to your Office 365 organization using Office 365 PowerShell to perform administration tasks from the command line.</span></span>
  
<span data-ttu-id="2710e-p101">Office 365 PowerShell können Sie Ihre Office 365-Einstellungen über die Befehlszeile zu verwalten. Herstellen einer Verbindung mit Office 365 PowerShell ist ein einfacher dreistufiger Prozess, in dem Sie Installieren der erforderlichen Software, die erforderliche Software ausführen und dann verbinden mit Office 365-Organisation.</span><span class="sxs-lookup"><span data-stu-id="2710e-p101">Office 365 PowerShell lets you to manage your Office 365 settings from the command line. Connecting to Office 365 PowerShell is a simple three-step process where you install the required software, run the required software, and then connect to your Office 365 organization.</span></span> 

  
> [!TIP]
> <span data-ttu-id="2710e-p102">**Neue PowerShell?** Finden Sie ein [video Overview of PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), bereitgestellt von LinkedIn Learning.</span><span class="sxs-lookup"><span data-stu-id="2710e-p102">**New to PowerShell?** See a [video Overview of PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), brought to you by LinkedIn Learning.</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="2710e-109">Was sollten Sie wissen, bevor Sie beginnen?</span><span class="sxs-lookup"><span data-stu-id="2710e-109">What do you need to know before you begin?</span></span>

- <span data-ttu-id="2710e-110">Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten</span><span class="sxs-lookup"><span data-stu-id="2710e-110">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="2710e-111">Sie können folgende Versionen von Windows verwenden:</span><span class="sxs-lookup"><span data-stu-id="2710e-111">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="2710e-112">10 Windows, Windows 8.1, Windows 8 oder Windows 7 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="2710e-112">Windows 10, Windows 8.1, Windows 8 or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="2710e-113">WindowsServer 2016, Windows Server 2012 R2, WindowsServer 2012 oder Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="2710e-113">Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>
    
    > [!NOTE]
    ><span data-ttu-id="2710e-p103">Verwenden Sie eine 64-Bit-Version von Windows. Unterstützung für 32-Bit-Version, die Microsoft Azure Active Directory-Modul für Windows PowerShell wurde im Oktober des 2014 eingestellt.</span><span class="sxs-lookup"><span data-stu-id="2710e-p103">Use a 64-bit version of Windows. Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
-  <span data-ttu-id="2710e-p104">Diese Verfahren sind für Benutzer vorgesehen, die ein Office 365-Administratorrolle angehören. Weitere Informationen finden Sie unter [Informationen zu Office 365-Administratorrollen](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span><span class="sxs-lookup"><span data-stu-id="2710e-p104">These procedures are intended for users who are members of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>

## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="2710e-118">Kontaktaufnahme mit Azure Active Directory PowerShell Graph-Modul</span><span class="sxs-lookup"><span data-stu-id="2710e-118">Connect with the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="2710e-119">Befehle im Modul [Azure Active Directory PowerShell für Diagramm](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) enthalten **AzureAD** in ihrem Cmdlet-Namen.</span><span class="sxs-lookup"><span data-stu-id="2710e-119">Commands in the [Azure Active Directory PowerShell for Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) module have **AzureAD** in their cmdlet name.</span></span>

<span data-ttu-id="2710e-120">Verwenden Sie für Prozeduren, die die neuen in Azure Active Directory PowerShell-Cmdlets für Diagramm Modul erforderlich ist diese Schritte zum Installieren des Moduls und Verbinden mit Office 365-Abonnements.</span><span class="sxs-lookup"><span data-stu-id="2710e-120">For procedures that require the new cmdlets in the Azure Active Directory PowerShell for Graph module, use these steps to install the module and connect to your Office 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="2710e-121">Finden Sie Informationen über die Unterstützung für verschiedene Versionen von Microsoft Windows [Azure Active Directory-PowerShell-Modul Diagramm](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) .</span><span class="sxs-lookup"><span data-stu-id="2710e-121">See [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) for information about the support for different versions of Microsoft Windows.</span></span>
>

### <a name="step-1-install-required-software"></a><span data-ttu-id="2710e-122">Schritt 1: Installieren der erforderlichen Software</span><span class="sxs-lookup"><span data-stu-id="2710e-122">Step 1: Install required software</span></span>

<span data-ttu-id="2710e-p105">Diese Schritte sind auf Ihrem Computer nur einmal erforderlich, nicht jedes Mal, wenn Sie eine Verbindung herstellen. Allerdings müssen Sie wahrscheinlich in regelmäßigen Abständen neuere Versionen der Software installieren.</span><span class="sxs-lookup"><span data-stu-id="2710e-p105">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1. <span data-ttu-id="2710e-125">Öffnen Sie eine Windows PowerShell-Eingabeaufforderung mit erhöhten Rechten (d. h., führen Sie Windows PowerShell als Administrator aus).</span><span class="sxs-lookup"><span data-stu-id="2710e-125">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="2710e-126">Führen Sie im Befehlsfenster **Administrator: Windows PowerShell** den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="2710e-126">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```
  Install-Module -Name AzureAD
  ```

<span data-ttu-id="2710e-127">Falls Sie gefragt werden, ob Sie ein Modul aus einem nicht vertrauenswürdigen Repository installieren möchten: Geben Sie **Y** ein, und drücken Sie die EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="2710e-127">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="2710e-128">Schritt 2: Verbinden Sie mit Azure AD für Ihre Office 365-Abonnements</span><span class="sxs-lookup"><span data-stu-id="2710e-128">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="2710e-129">Führen Sie eine Verbindung mit Azure AD für Ihre Office 365 Abonnement mit einen Kontonamen und ein Kennwort oder mit *Multi-Factor Authentication (mehrstufiger Authentifizierung das)* diesen Befehl von einer Windows PowerShell-Eingabeaufforderung (es ist nicht erforderlich, werden mit erhöhten Rechten):</span><span class="sxs-lookup"><span data-stu-id="2710e-129">To connect to Azure AD for your Office 365 subscription with an account name and password or with *multi-factor authentication (MFA)* run this command from a Windows PowerShell command prompt (it does not have to be elevated):</span></span>
    
```
Connect-AzureAD
```

<span data-ttu-id="2710e-130">Klicken Sie im Dialogfeld **Anmeldung bei Ihrem Konto** Geben Sie Ihren Office 365 Arbeit oder Schule Benutzernamen und Ihr Kennwort ein, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="2710e-130">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="2710e-131">Wenn Sie mit mehrstufiger Authentifizierung das nutzen, befolgen Sie die Anweisungen in den Dialogfeldern zusätzliche Weitere Authentifizierungsinformationen, beispielsweise einen Überprüfungscode bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="2710e-131">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>
    
<span data-ttu-id="2710e-132">Nach dem anschließen, können Sie die neuen Cmdlets für die [Azure Active Directory PowerShell Graph-Modul](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)verwenden.</span><span class="sxs-lookup"><span data-stu-id="2710e-132">After connecting, you can use the new cmdlets for the [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="2710e-133">Kontaktaufnahme mit dem Microsoft Azure Active Directory-Moduls für Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2710e-133">Connect with the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="2710e-134">Befehle in der Microsoft Azure Active Directory-Modul für Windows PowerShell enthalten **Msol** in ihrem Cmdlet-Namen.</span><span class="sxs-lookup"><span data-stu-id="2710e-134">Commands in the Microsoft Azure Active Directory Module for Windows PowerShell have **Msol** in their cmdlet name.</span></span>
    
### <a name="step-1-install-required-software"></a><span data-ttu-id="2710e-135">Schritt 1: Installieren der erforderlichen Software</span><span class="sxs-lookup"><span data-stu-id="2710e-135">Step 1: Install required software</span></span>

<span data-ttu-id="2710e-p106">Diese Schritte sind auf Ihrem Computer nur einmal erforderlich, nicht jedes Mal, wenn Sie eine Verbindung herstellen. Allerdings müssen Sie wahrscheinlich in regelmäßigen Abständen neuere Versionen der Software installieren.</span><span class="sxs-lookup"><span data-stu-id="2710e-p106">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="2710e-138">Installieren Sie die 64-Bit-Version des Microsoft Online Services-Anmeldeassistenten: [Microsoft Online Services - Anmeldeassistenten für IT-Experten RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span><span class="sxs-lookup"><span data-stu-id="2710e-138">Install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="2710e-139">Installieren Sie die Microsoft Azure Active Directory-Modul für Windows PowerShell mit der folgenden Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="2710e-139">Install the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="2710e-140">Öffnen Sie eine Windows PowerShell-Eingabeaufforderung mit erhöhten Rechten (d. h., führen Sie Windows PowerShell als Administrator aus).</span><span class="sxs-lookup"><span data-stu-id="2710e-140">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
  - <span data-ttu-id="2710e-141">Führen Sie den Befehl **MSOnline Modul installieren** .</span><span class="sxs-lookup"><span data-stu-id="2710e-141">Run the **Install-Module MSOnline** command.</span></span>
  - <span data-ttu-id="2710e-142">Wenn aufgefordert, den NuGet-Anbieter installieren, geben Sie **Y** ein, und drücken Sie die EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="2710e-142">If prompted to install the NuGet provider, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="2710e-143">Wenn Sie aufgefordert werden, installieren Sie das Modul aus PSGallery, geben Sie **Y** ein, und drücken Sie die EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="2710e-143">If prompted to install the module from PSGallery, type **Y** and press ENTER.</span></span>
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="2710e-144">Schritt 2: Verbinden Sie mit Azure AD für Ihre Office 365-Abonnements</span><span class="sxs-lookup"><span data-stu-id="2710e-144">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="2710e-145">Führen Sie diesen Befehl von einer Windows PowerShell-Eingabeaufforderung (es ist nicht erforderlich, werden mit erhöhten Rechten), zum Verbinden mit Azure AD für Ihr Office 365-Abonnement mit einen Kontonamen und ein Kennwort oder mit *Multi-Factor Authentication (mehrstufiger Authentifizierung das)*:</span><span class="sxs-lookup"><span data-stu-id="2710e-145">To connect to Azure AD for your Office 365 subscription with an account name and password or with *multi-factor authentication (MFA)*, run this command from a Windows PowerShell command prompt (it does not have to be elevated):</span></span>
    
```
Connect-MsolService
```

<span data-ttu-id="2710e-146">Klicken Sie im Dialogfeld **Anmeldung bei Ihrem Konto** Geben Sie Ihren Office 365 Arbeit oder Schule Benutzernamen und Ihr Kennwort ein, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="2710e-146">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="2710e-147">Wenn Sie mit mehrstufiger Authentifizierung das nutzen, befolgen Sie die Anweisungen in den Dialogfeldern zusätzliche Weitere Authentifizierungsinformationen, beispielsweise einen Überprüfungscode bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="2710e-147">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>

    
### <a name="how-do-you-know-this-worked"></a><span data-ttu-id="2710e-148">Woher wissen Sie, dass dieses Verfahren erfolgreich war?</span><span class="sxs-lookup"><span data-stu-id="2710e-148">How do you know this worked?</span></span>

<span data-ttu-id="2710e-p107">Wenn Sie keine Fehler erhalten, verbunden Sie erfolgreich. Ein schneller Test ein Office 365-Cmdlet ausgeführt wird – beispielsweise **Get-MsolUser** – und die Ergebnisse anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="2710e-p107">If you don't receive any errors, you connected successfully. A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="2710e-151">Wenn Sie Fehlermeldungen erhalten, überprüfen Sie die folgenden Anforderungen:</span><span class="sxs-lookup"><span data-stu-id="2710e-151">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="2710e-p108">**Ein häufig auftretendes Problem ist ein falsches Kennwort**. Führen Sie Schritt 3 erneut durch, und achten Sie besonders auf die korrekte Eingabe des Benutzernamens und Kennworts.</span><span class="sxs-lookup"><span data-stu-id="2710e-p108">**A common problem is an incorrect password**. Run Step 3 again. and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="2710e-p109">* *Der Microsoft Azure Active Directory-Modul für Windows PowerShell erfordert, dass Microsoft .NET Framework 3.5.* X * Feature wird auf Ihrem Computer ** aktiviert. Ist es wahrscheinlich, dass auf Ihrem Computer eine neuere Version installiert ist (beispielsweise 4 oder 4.5.* X *), aber rückwärts Kompatibilität mit älteren Versionen von .NET Framework aktiviert oder deaktiviert werden kann. Weitere Informationen finden Sie unter den folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="2710e-p109">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5.* x* feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5.* x*), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled. For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="2710e-157">Windows Server 2012 oder Windows Server 2012 R2 finden Sie unter [.NET Framework 3.5 mithilfe der Rollen hinzufügen und den Assistenten Features aktivieren](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span><span class="sxs-lookup"><span data-stu-id="2710e-157">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="2710e-158">Windows 8 oder Windows 8.1 finden Sie unter [Installieren von .NET Framework 3.5 unter Windows 8 oder 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369)</span><span class="sxs-lookup"><span data-stu-id="2710e-158">For Windows 8 or Windows 8.1, see [Installing the .NET Framework 3.5 on Windows 8 or 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369)</span></span>
    
  - <span data-ttu-id="2710e-159">Windows 7 oder Windows Server 2008 R2 finden Sie unter [der Azure Active Directory Modul für Windows PowerShell kann nicht geöffnet werden](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span><span class="sxs-lookup"><span data-stu-id="2710e-159">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>

  - <span data-ttu-id="2710e-160">10 für Windows, Windows 8.1 und Windows 8 finden Sie unter [Installieren von .NET Framework 3.5 auf 10 Windows, Windows 8.1-und Windows 8](https://docs.microsoft.com/en-us/dotnet/framework/install/dotnet-35-windows-10)</span><span class="sxs-lookup"><span data-stu-id="2710e-160">For Windows 10, Windows 8.1, and Windows 8, see [Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8](https://docs.microsoft.com/en-us/dotnet/framework/install/dotnet-35-windows-10)</span></span>

  
- <span data-ttu-id="2710e-p110">**Ihrer Version von der Microsoft Azure Active Directory-Modul für Windows PowerShell möglicherweise nicht mehr aktuell.** Führen Sie den folgenden Befehl in Office 365 PowerShell oder der Microsoft Azure Active Directory-Modul für Windows PowerShell, um zu überprüfen:</span><span class="sxs-lookup"><span data-stu-id="2710e-p110">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.** To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="2710e-163">Wenn die Versionsnummer zurückgegeben niedriger als der Wert 1.0.8070.2 ist, deinstallieren Sie die Microsoft Azure Active Directory-Modul für Windows PowerShell, und installieren Sie die neueste Version über den Link in Schritt 1.</span><span class="sxs-lookup"><span data-stu-id="2710e-163">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install the latest version from the link in Step 1.</span></span>
    
- <span data-ttu-id="2710e-164">**Wenn Sie eine Verbindung Fehlermeldung angezeigt wird, finden Sie unter in diesem Thema:** ["Connect-MsolService: Ausnahme vom Typ ausgelöst wurde" Fehler](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span><span class="sxs-lookup"><span data-stu-id="2710e-164">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="2710e-165">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="2710e-165">See also</span></span>

- [<span data-ttu-id="2710e-166">Verwalten von Office 365 mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="2710e-166">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="2710e-167">Erste Schritte mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="2710e-167">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="2710e-168">Verbinden mit allen Office 365-Diensten in einem einzigen Windows PowerShell-Fenster</span><span class="sxs-lookup"><span data-stu-id="2710e-168">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
- [<span data-ttu-id="2710e-169">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="2710e-169">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
- [<span data-ttu-id="2710e-170">Verbinden-MsolService</span><span class="sxs-lookup"><span data-stu-id="2710e-170">Connect-MsolService</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532375)

