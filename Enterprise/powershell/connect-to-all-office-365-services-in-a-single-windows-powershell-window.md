---
title: Verbinden mit allen Office 365-Diensten in einem einzigen Windows PowerShell-Fenster
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/28/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- Ent_Office_Other
- O365ITProTrain
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: 'Zusammenfassung: Verbinden Sie Windows PowerShell mit allen Office 365-Diensten in einem einzigen Windows PowerShell-Fenster.'
ms.openlocfilehash: ae9487f48439c6f8d98f927c610e5f2af4c1b361
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069181"
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="1d943-103">Verbinden mit allen Office 365-Diensten in einem einzigen Windows PowerShell-Fenster</span><span class="sxs-lookup"><span data-stu-id="1d943-103">Connect to all Office 365 services in a single Windows PowerShell window</span></span>

 <span data-ttu-id="1d943-104">**Zusammenfassung:** Anstatt verschiedene Office 365-Dienste in separaten PowerShell-Konsolenfenstern zu verwalten, können Sie eine Verbindung mit allen Office 365-Diensten herstellen und diese über ein einzelnes Konsolenfenster verwalten.</span><span class="sxs-lookup"><span data-stu-id="1d943-104">**Summary:** Instead of managing different Office 365 services in separate PowerShell console windows, you can connect to all Office 365 services and manage them from single console window.</span></span>
  
<span data-ttu-id="1d943-105">Wenn Sie PowerShell zum Verwalten von Office 365 verwenden, können bis zu fünf verschiedene Windows PowerShell-Sitzungen gleichzeitig geöffnet sein, entsprechend dem Microsoft 365 Admin Center, SharePoint Online, Exchange Online, Skype for Business Online und der Sicherheits &amp; Compliance Center.</span><span class="sxs-lookup"><span data-stu-id="1d943-105">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Microsoft 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="1d943-106">Mit fünf verschiedenen Verbindungsmethoden in separaten Windows PowerShell-Sitzungen könnte Ihr Desktop wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="1d943-106">With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![Fünf Windows PowerShell-Konsolen, die gleichzeitig ausgeführt werden](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="1d943-108">Dies ist nicht optimal für die Verwaltung von Office 365, da Sie keine Daten zwischen diesen fünf Fenstern für die dienstübergreifende Verwaltung austauschen können.</span><span class="sxs-lookup"><span data-stu-id="1d943-108">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management.</span></span> <span data-ttu-id="1d943-109">In diesem Thema wird beschrieben, wie Sie eine einzelne Instanz von Windows PowerShell verwenden, über die Sie Office 365, Skype for Business Online, Exchange Online, SharePoint Online und &amp; das Security Compliance Center verwalten können.</span><span class="sxs-lookup"><span data-stu-id="1d943-109">This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center.</span></span>

>[!Note]
><span data-ttu-id="1d943-110">Dieser Artikel enthält derzeit nur die Befehle zum Herstellen einer Verbindung mit der Office 365 Worldwide (+ gcc)-Cloud.</span><span class="sxs-lookup"><span data-stu-id="1d943-110">This article currently only contains the commands to connect to the Office 365 Worldwide (+GCC) cloud.</span></span> <span data-ttu-id="1d943-111">Zusätzliche Hinweise enthalten Links zu Artikeln mit Informationen zum Herstellen einer Verbindung mit den anderen Office 365-Clouds.</span><span class="sxs-lookup"><span data-stu-id="1d943-111">Additional notes provide links to articles with information about connecting to the other Office 365 clouds.</span></span>
>

## <a name="before-you-begin"></a><span data-ttu-id="1d943-112">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="1d943-112">Before you begin</span></span>

<span data-ttu-id="1d943-113">Bevor Sie den gesamten Office 365 von einer einzigen Instanz von Windows PowerShell aus verwalten können, sollten Sie die folgenden Voraussetzungen berücksichtigen:</span><span class="sxs-lookup"><span data-stu-id="1d943-113">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="1d943-114">Das Office 365-Arbeits-oder Schulkonto, das Sie für diese Verfahren verwenden, muss Mitglied einer Office 365-Administratorrolle sein.</span><span class="sxs-lookup"><span data-stu-id="1d943-114">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role.</span></span> <span data-ttu-id="1d943-115">Weitere Informationen finden Sie unter [Informationen zu Office 365-Administratorrollen](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span><span class="sxs-lookup"><span data-stu-id="1d943-115">For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span> <span data-ttu-id="1d943-116">Dies ist eine Voraussetzung für Office 365 PowerShell, nicht unbedingt für alle anderen Office 365-Dienste.</span><span class="sxs-lookup"><span data-stu-id="1d943-116">This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span></span>
    
- <span data-ttu-id="1d943-117">Sie können folgende 64-Bit-Versionen von Windows verwenden:</span><span class="sxs-lookup"><span data-stu-id="1d943-117">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="1d943-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="1d943-118">Windows 10</span></span>
    
  - <span data-ttu-id="1d943-119">Windows 8.1 oder Windows 8</span><span class="sxs-lookup"><span data-stu-id="1d943-119">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="1d943-120">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="1d943-120">Windows Server 2019</span></span>
    
  - <span data-ttu-id="1d943-121">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="1d943-121">Windows Server 2016</span></span>
    
  - <span data-ttu-id="1d943-122">Windows Server 2012 R2 oder Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="1d943-122">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="1d943-123">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="1d943-123">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="1d943-124">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="1d943-124">Windows Server 2008 R2 SP1\*</span></span>
    
    <span data-ttu-id="1d943-125">\*Sie müssen Microsoft .NET Framework 4,5 installieren. *x* und dann entweder Windows Management Framework 3,0 oder Windows Management Framework 4,0.</span><span class="sxs-lookup"><span data-stu-id="1d943-125">\* You need to install the Microsoft .NET Framework 4.5.*x* and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0.</span></span> <span data-ttu-id="1d943-126">Weitere Informationen finden Sie unter [Installieren von .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) und [Windows Management Framework 3,0](https://go.microsoft.com/fwlink/p/?LinkId=272757) oder [Windows Management Framework 4,0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span><span class="sxs-lookup"><span data-stu-id="1d943-126">For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="1d943-127">Sie müssen eine 64-Bit-Version von Windows aufgrund der Anforderungen für das Skype for Business Online-Modul und eines der Office 365-Module verwenden.</span><span class="sxs-lookup"><span data-stu-id="1d943-127">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span></span>
    
- <span data-ttu-id="1d943-128">Sie müssen die Module installieren, die für Azure AD, SharePoint Online und Skype for Business Online erforderlich sind:</span><span class="sxs-lookup"><span data-stu-id="1d943-128">You need to install the modules that are required for Azure AD, SharePoint Online, and Skype for Business Online:</span></span>
    
   - [<span data-ttu-id="1d943-129">Azure Active Directory v2</span><span class="sxs-lookup"><span data-stu-id="1d943-129">Azure Active Directory V2</span></span>](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [<span data-ttu-id="1d943-130">SharePoint Online-Verwaltungsshell</span><span class="sxs-lookup"><span data-stu-id="1d943-130">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [<span data-ttu-id="1d943-131">Skype for Business Online, Windows PowerShell-Modul</span><span class="sxs-lookup"><span data-stu-id="1d943-131">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  <span data-ttu-id="1d943-132">Windows PowerShell muss so konfiguriert werden, dass signierte Skripts für Skype for Business Online, Exchange Online und das Security &amp; Compliance Center ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="1d943-132">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="1d943-133">Führen Sie dazu den folgenden Befehl in einer erhöhten Windows PowerShell-Sitzung aus (ein Windows PowerShell-Fenster, das Sie durch Auswählen von **als Administrator ausführen**öffnen).</span><span class="sxs-lookup"><span data-stu-id="1d943-133">To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a><span data-ttu-id="1d943-134">Verbindungs Schritte bei Verwendung eines Kennworts</span><span class="sxs-lookup"><span data-stu-id="1d943-134">Connection steps when using a password</span></span>

<span data-ttu-id="1d943-135">Hier sind die Schritte zum Herstellen einer Verbindung mit allen Diensten in einem einzelnen PowerShell-Fenster.</span><span class="sxs-lookup"><span data-stu-id="1d943-135">Here are the steps to connect to all the services in a single PowerShell window.</span></span>
  
1. <span data-ttu-id="1d943-136">Öffnen Sie Windows PowerShell als Administrator (verwenden Sie **als Administrator ausführen**).</span><span class="sxs-lookup"><span data-stu-id="1d943-136">Open Windows PowerShell as an administrator (use **Run as administrator**).</span></span>
    
2. <span data-ttu-id="1d943-137">Führen Sie diesen Befehl aus, und geben Sie Ihre Office 365-Arbeits-oder Schulkonto Anmeldeinformationen ein.</span><span class="sxs-lookup"><span data-stu-id="1d943-137">Run this command, and enter your Office 365 work or school account credentials.</span></span>
    
  ```
  $credential = Get-Credential
  ```

3. <span data-ttu-id="1d943-138">Führen Sie diesen Befehl aus, um eine Verbindung mit Azure Active Directory (AD) mithilfe des Azure Active Directory PowerShell für Graph-Moduls herzustellen.</span><span class="sxs-lookup"><span data-stu-id="1d943-138">Run this command to connect to Azure Active Directory (AD) using the Azure Active Directory PowerShell for Graph module.</span></span>
    
  ```
  Connect-AzureAD -Credential $credential
  ```
  
  <span data-ttu-id="1d943-139">Wenn Sie das Microsoft Azure Active Directory-Modul für Windows PowerShell verwenden, führen Sie diesen Befehl Alternativ aus.</span><span class="sxs-lookup"><span data-stu-id="1d943-139">Alternately, if you are using the Microsoft Azure Active Directory Module for Windows PowerShell module, run this command.</span></span>
      
  ```
  Connect-MsolService -Credential $credential
 ```

4. <span data-ttu-id="1d943-140">Führen Sie diese Befehle aus, um eine Verbindung mit SharePoint Online herzustellen.</span><span class="sxs-lookup"><span data-stu-id="1d943-140">Run these commands to connect to SharePoint Online.</span></span> <span data-ttu-id="1d943-141">Ersetzen _ \<Sie domainhost>_ durch den tatsächlichen Wert für Ihre Domäne.</span><span class="sxs-lookup"><span data-stu-id="1d943-141">Replace  _\<domainhost>_ with the actual value for your domain.</span></span> <span data-ttu-id="1d943-142">Beispiel: bei "litwareinc.onmicrosoft.com" lautet der _ \<Wert domainhost>_ "litwareinc".</span><span class="sxs-lookup"><span data-stu-id="1d943-142">For example, for "litwareinc.onmicrosoft.com", the  _\<domainhost>_ value is "litwareinc".</span></span>
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. <span data-ttu-id="1d943-143">Führen Sie diese Befehle aus, um eine Verbindung mit Skype for Business Online herzustellen.</span><span class="sxs-lookup"><span data-stu-id="1d943-143">Run these commands to connect to Skype for Business Online.</span></span> <span data-ttu-id="1d943-144">Bei der ersten Verbindung wird `WSMan NetworkDelayms` eine Warnung zur Erhöhung des Werts erwartet, und Sie sollten ignoriert werden.</span><span class="sxs-lookup"><span data-stu-id="1d943-144">A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="1d943-145">Führen Sie diese Befehle aus, um eine Verbindung mit Exchange Online herzustellen.</span><span class="sxs-lookup"><span data-stu-id="1d943-145">Run these commands to connect to Exchange Online.</span></span>
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession -DisableNameChecking
  ```

>[!Note]
><span data-ttu-id="1d943-146">Informationen zum Herstellen einer Verbindung mit Exchange Online für Office 365-Clouds außer weltweit finden Sie unter [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span><span class="sxs-lookup"><span data-stu-id="1d943-146">To connect to Exchange Online for Office 365 clouds other than Worldwide, see [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span></span>
>

7. <span data-ttu-id="1d943-147">Führen Sie diese Befehle aus, um eine &amp; Verbindung mit dem Security Compliance Center herzustellen.</span><span class="sxs-lookup"><span data-stu-id="1d943-147">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

>[!Note]
><span data-ttu-id="1d943-148">Informationen zum Herstellen einer Verbindung &amp; mit dem Security Compliance Center für Office 365-Clouds außer weltweit finden Sie unter [Connect to Office 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span><span class="sxs-lookup"><span data-stu-id="1d943-148">To connect to the Security &amp; Compliance Center for Office 365 clouds other than Worldwide, see [Connect to Office 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span></span>
>

<span data-ttu-id="1d943-149">Im folgenden werden alle Befehle in einem einzelnen Block angezeigt, wenn das Azure Active Directory PowerShell für Graph-Modul verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="1d943-149">Here are all the commands in a single block when using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="1d943-150">Geben Sie den Namen Ihres Domänenhosts an, und führen Sie alle Befehle gleichzeitig aus.</span><span class="sxs-lookup"><span data-stu-id="1d943-150">Specify the name of your domain host, and then run them all at one time.</span></span>
  
```
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-AzureAD -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession -DisableNameChecking
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
```

<span data-ttu-id="1d943-151">Alternativ dazu finden Sie im folgenden alle Befehle in einem einzelnen Block, wenn Sie das Microsoft Azure Active Directory-Modul für Windows PowerShell verwenden.</span><span class="sxs-lookup"><span data-stu-id="1d943-151">Alternately, here are all the commands in a single block when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span> <span data-ttu-id="1d943-152">Geben Sie den Namen Ihres Domänenhosts an, und führen Sie alle Befehle gleichzeitig aus.</span><span class="sxs-lookup"><span data-stu-id="1d943-152">Specify the name of your domain host, and then run them all at one time.</span></span>
  
```
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession -DisableNameChecking
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
```

<span data-ttu-id="1d943-153">Wenn Sie bereit sind, das Windows PowerShell-Fenster zu schließen, führen Sie diesen Befehl aus, um die aktiven Sitzungen zu Skype for Business Online, Exchange Online, SharePoint Online &amp; und dem Security Compliance Center zu entfernen:</span><span class="sxs-lookup"><span data-stu-id="1d943-153">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center:</span></span>
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $SccSession ; Disconnect-SPOService
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a><span data-ttu-id="1d943-154">Verbindungs Schritte bei Verwendung der mehrstufigen Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="1d943-154">Connection steps when using multi-factor authentication</span></span>

<span data-ttu-id="1d943-155">Hier sind alle Befehle in einem einzelnen Block, mit denen eine Verbindung mit Azure AD, SharePoint Online und Skype for Buiness mithilfe der mehrstufigen Authentifizierung in einem einzelnen Fenster mithilfe des Azure Active Directory PowerShell für Graph-Moduls hergestellt werden kann.</span><span class="sxs-lookup"><span data-stu-id="1d943-155">Here are all the commands in a single block to connect to Azure AD, SharePoint Online, and Skype for Buiness using multi-factor authentication in a single window using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="1d943-156">Geben Sie den Benutzerprinzipalnamen (UPN) eines Benutzerkontos und ihren Domänenhost Namen an, und führen Sie alle gleichzeitig aus.</span><span class="sxs-lookup"><span data-stu-id="1d943-156">Specify the user principal name (UPN) name of a user account and your domain host name, and then run them all at one time.</span></span>

````
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-AzureAD
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
````

<span data-ttu-id="1d943-157">Alternativ dazu finden Sie hier alle Befehle, wenn Sie das Microsoft Azure Active Directory-Modul für Windows PowerShell verwenden.</span><span class="sxs-lookup"><span data-stu-id="1d943-157">Alternately, here are all the commands when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span>

````
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-MsolService
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
````

<span data-ttu-id="1d943-158">Informationen zu Exchange Online und zum &amp; Security Compliance Center finden Sie in den folgenden Themen zum Herstellen einer Verbindung mit mehrstufiger Authentifizierung:</span><span class="sxs-lookup"><span data-stu-id="1d943-158">For Exchange Online and the Security &amp; Compliance Center, see the following topics to connect using multi-factor authentication:</span></span>

- [<span data-ttu-id="1d943-159">Verbinden mit Exchange Online PowerShell per mehrstufiger Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="1d943-159">Connect to Exchange Online PowerShell using multi-factor authentication</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell)
- [<span data-ttu-id="1d943-160">Herstellen einer Verbindung mit Office 365 Security & Compliance Center PowerShell mithilfe der mehrstufigen Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="1d943-160">Connect to Office 365 Security & Compliance Center PowerShell using multi-factor authentication</span></span>](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps)
 
<span data-ttu-id="1d943-161">Beachten Sie, dass in beiden Fällen eine Verbindung über separate Sitzungen des Remote-PowerShell-Moduls von Exchange Online hergestellt werden muss.</span><span class="sxs-lookup"><span data-stu-id="1d943-161">Note that in both cases, you must connect using separate sessions of the Exchange Online Remote PowerShell Module.</span></span>


## <a name="see-also"></a><span data-ttu-id="1d943-162">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="1d943-162">See also</span></span>

- [<span data-ttu-id="1d943-163">Verbinden mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="1d943-163">Connect to Office 365 PowerShell</span></span>](connect-to-office-365-powershell.md)
- [<span data-ttu-id="1d943-164">Verwalten von SharePoint Online mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="1d943-164">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
- [<span data-ttu-id="1d943-165">Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="1d943-165">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="1d943-166">Verwenden der Windows PowerShell zum Erstellen von Berichten in Office 365</span><span class="sxs-lookup"><span data-stu-id="1d943-166">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)
