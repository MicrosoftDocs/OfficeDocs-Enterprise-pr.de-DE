---
title: Verbinden mit allen Office 365-Diensten in einem einzigen Windows PowerShell-Fenster
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
- LIL_Placement
- Ent_Office_Other
- O365ITProTrain
- DecEntMigration
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: 'Zusammenfassung: Verbinden Sie Windows PowerShell mit allen Office 365-Diensten in einem einzelnen Windows PowerShell-Fenster.'
ms.openlocfilehash: 28016342fff77e33bd18369ae08b773ecea32644
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2017
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="c99a1-103">Verbinden mit allen Office 365-Diensten in einem einzigen Windows PowerShell-Fenster</span><span class="sxs-lookup"><span data-stu-id="c99a1-103">Connect to all Office 365 services in a single Windows PowerShell window</span></span>

 <span data-ttu-id="c99a1-104">**Zusammenfassung:** Anstelle von Verwalten von verschiedenen Office 365-Diensten in separaten Fenstern von PowerShell-Konsole, können Sie eine Verbindung mit allen Office 365-Diensten und über einzelne Konsolenfenster verwalten.</span><span class="sxs-lookup"><span data-stu-id="c99a1-104">**Summary:** Instead of managing different Office 365 services in separate PowerShell console windows, you can connect to all Office 365 services and manage them from single console window.</span></span>
  
<span data-ttu-id="c99a1-p101">Wenn Sie zum Verwalten von Office 365 PowerShell verwenden, ist es möglich, bis zu fünf verschiedene Windows PowerShell-Sitzungen entsprechend der Office 365 Administrationscenter, SharePoint Online, Exchange Online, Skype für Business Online und die Sicherheit &amp;Compliance Center. Mit fünf unterschiedliche Verbindungsmethoden in separaten Windows PowerShell-Sitzungen konnte Ihren Desktop sieht folgendermaßen aus:</span><span class="sxs-lookup"><span data-stu-id="c99a1-p101">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Office 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, and the Security &amp; Compliance Center. With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![Fünf gleichzeitig ausgeführte Windows PowerShell-Konsolen](images/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="c99a1-p102">Dies ist nicht für die Verwaltung von Office 365, da Sie Daten zwischen diesen fünf Windows for Cross-Service-Management austauschen können nicht optimal. In diesem Thema wird beschrieben, wie eine einzelne Instanz von Windows PowerShell verwenden, Sie können aus dem Office 365, Skype für Business Online, Exchange Online, SharePoint Online und die Sicherheit verwalten &amp; Compliance Center.</span><span class="sxs-lookup"><span data-stu-id="c99a1-p102">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management. This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="c99a1-110">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="c99a1-110">Before you begin</span></span>
<span data-ttu-id="c99a1-111"><a name="BeforeYouBegin"> </a></span><span class="sxs-lookup"><span data-stu-id="c99a1-111"></span></span>

<span data-ttu-id="c99a1-112">Bevor Sie alle von Office 365 von einer einzigen Instanz von Windows PowerShell verwalten können, sollten Sie die folgenden erforderlichen Komponenten:</span><span class="sxs-lookup"><span data-stu-id="c99a1-112">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="c99a1-p103">Office 365 arbeiten oder Schule Konto ein, das Sie für diese Verfahren Anforderungen verwenden, um ein Mitglied einer Office 365-Admin-Rolle sein. Weitere Informationen finden Sie unter [Informationen zu Office 365-Administratorrollen](https://go.microsoft.com/fwlink/p/?LinkId=532367). Diese eine Voraussetzung für Office 365 PowerShell, was nicht notwendigerweise für alle anderen Office 365-Dienste.</span><span class="sxs-lookup"><span data-stu-id="c99a1-p103">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367). This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span></span>
    
- <span data-ttu-id="c99a1-116">Sie können folgende 64-Bit-Versionen von Windows verwenden:</span><span class="sxs-lookup"><span data-stu-id="c99a1-116">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="c99a1-117">Windows 10</span><span class="sxs-lookup"><span data-stu-id="c99a1-117">Windows 10</span></span>
    
  - <span data-ttu-id="c99a1-118">Windows 8.1 oder Windows 8</span><span class="sxs-lookup"><span data-stu-id="c99a1-118">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="c99a1-119">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="c99a1-119">Windows Server 2016</span></span>
    
  - <span data-ttu-id="c99a1-120">Windows Server 2012 R2 oder Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="c99a1-120">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="c99a1-121">Windows 7 Service Pack 1 (SP1)*</span><span class="sxs-lookup"><span data-stu-id="c99a1-121">Windows 7 Service Pack 1 (SP1)*</span></span>
    
  - <span data-ttu-id="c99a1-122">Windows Server 2008 R2 SP1*</span><span class="sxs-lookup"><span data-stu-id="c99a1-122">Windows Server 2008 R2 SP1*</span></span>
    
    * <span data-ttu-id="c99a1-p104">Sie müssen Microsoft .NET Framework 4.5 zu installieren. _X_ , und klicken Sie dann entweder das Windows Management Framework 3.0 oder das Windows Management Framework 4.0. Weitere Informationen finden Sie unter [Installieren von .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) und [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) oder [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span><span class="sxs-lookup"><span data-stu-id="c99a1-p104">You need to install the Microsoft .NET Framework 4.5. _x_ and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0. For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="c99a1-126">Sie müssen eine 64-Bit-Version von Windows für Business Online Modul und einen der Office 365-Module aufgrund der Anforderungen für die Skype verwenden.</span><span class="sxs-lookup"><span data-stu-id="c99a1-126">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span></span>
    
- <span data-ttu-id="c99a1-127">Sie müssen die Module installieren, die für Office 365, SharePoint Online und Skype für Business Online erforderlich sind:</span><span class="sxs-lookup"><span data-stu-id="c99a1-127">You need to install the modules that are required for Office 365, SharePoint Online, and Skype for Business Online:</span></span>
    
  - [<span data-ttu-id="c99a1-128">Microsoft Online Service Anmelde-Assistent für IT-Experten RTW</span><span class="sxs-lookup"><span data-stu-id="c99a1-128">Microsoft Online Service Sign-in Assistant for IT Professionals RTW</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=286152)
    
  - [<span data-ttu-id="c99a1-129">Windows Azure Active Directory-Modul für Windows PowerShell (64-Bit-Version)</span><span class="sxs-lookup"><span data-stu-id="c99a1-129">Windows Azure Active Directory Module for Windows PowerShell (64-bit version)</span></span>](https://go.microsoft.com/fwlink/p/?linkid=236297)
    
  - [<span data-ttu-id="c99a1-130">SharePoint Online-Verwaltungsshell</span><span class="sxs-lookup"><span data-stu-id="c99a1-130">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
    
  - [<span data-ttu-id="c99a1-131">Skype für Unternehmen Online, Windows PowerShell-Modul</span><span class="sxs-lookup"><span data-stu-id="c99a1-131">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  <span data-ttu-id="c99a1-p105">Windows PowerShell zum Ausführen von signierten Skripts für Skype für Business Online, Exchange Online und die Sicherheit konfiguriert werden muss &amp; Compliance Center. Zu diesem Zweck führen Sie den folgenden Befehl in einer Windows PowerShell-Sitzung mit erhöhten Rechten (ein Windows PowerShell-Fenster Sie öffnen, indem Sie **als Administrator ausführen**auswählen).</span><span class="sxs-lookup"><span data-stu-id="c99a1-p105">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center. To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="c99a1-134">Die Kurzfassung (Anweisungen ohne Erläuterungen)</span><span class="sxs-lookup"><span data-stu-id="c99a1-134">The short version (instructions without explanations)</span></span>
<span data-ttu-id="c99a1-135"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="c99a1-135"></span></span>

<span data-ttu-id="c99a1-p106">In diesem Abschnitt werden die Verbindungsschritte kurz und bündig erläutert. Wenn Sie Fragen haben oder weitere Informationen benötigen, können Sie den Rest des Themas lesen. Die Schrittnummern entsprechen den nummerierten Abschnitten im Rest des Themas:</span><span class="sxs-lookup"><span data-stu-id="c99a1-p106">This section presents the connection steps without in-depth explanations. If you have questions or want more information, you can read rest of the topic. The step numbers here match the step-numbered sections in the rest of the topic:</span></span>
  
1. <span data-ttu-id="c99a1-139">Öffnen Sie Windows PowerShell als Administrator (verwenden Sie **als Administrator ausführen**).</span><span class="sxs-lookup"><span data-stu-id="c99a1-139">Open Windows PowerShell as an administrator (use **Run as administrator**).</span></span>
    
2. <span data-ttu-id="c99a1-140">Führen Sie diesen Befehl, und geben Sie Ihre Office 365 Arbeit oder Schule Kontoanmeldeinformationen.</span><span class="sxs-lookup"><span data-stu-id="c99a1-140">Run this command, and enter your Office 365 work or school account credentials.</span></span>
    
  ```
  $credential = Get-Credential
  ```

3. <span data-ttu-id="c99a1-141">Führen Sie diese Befehle für die Verbindung zu Office 365.</span><span class="sxs-lookup"><span data-stu-id="c99a1-141">Run these commands to connect to Office 365.</span></span>
    
  ```
  Import-Module MsOnline
  Connect-MsolService -Credential $credential
  ```

4. <span data-ttu-id="c99a1-p107">Führen Sie diese Befehle für die Verbindung mit SharePoint Online. Ersetzen Sie _ \<Domainhost >_ durch den tatsächlichen Wert für Ihre Domäne. Beispiel für `litwareinc.onmicrosoft.com`, die _ \<Domainhost >_ Wert ist `litwareinc`.</span><span class="sxs-lookup"><span data-stu-id="c99a1-p107">Run these commands to connect to SharePoint Online. Replace  _\<domainhost>_ with the actual value for your domain. For example, for `litwareinc.onmicrosoft.com`, the  _\<domainhost>_ value is `litwareinc`.</span></span>
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. <span data-ttu-id="c99a1-p108">Führen Sie diese Befehle zum Skype für Business Online herstellen. Eine Warnung zur Erhöhung der `WSMan NetworkDelayms` Wert wird erwartet, dass beim ersten verbinden und sollte ignoriert werden.</span><span class="sxs-lookup"><span data-stu-id="c99a1-p108">Run these commands to connect to Skype for Business Online. A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="c99a1-147">Führen Sie diese Befehle für die Verbindung zu Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="c99a1-147">Run these commands to connect to Exchange Online.</span></span>
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession -DisableNameChecking
  ```

7. <span data-ttu-id="c99a1-148">Führen Sie diese Befehle für die Verbindung für die Sicherheit &amp; Compliance Center.</span><span class="sxs-lookup"><span data-stu-id="c99a1-148">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```
  $ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
  Import-PSSession $ccSession -Prefix cc
  ```
> [!NOTE]
> <span data-ttu-id="c99a1-p109">Nach Textpräfix "cc" *Alle* Sicherheit hinzugefügt &amp; Compliance Center-Cmdlet-Namen, damit Sie Cmdlets ausführen können in Exchange Online und die Sicherheit vorhanden sind, &amp; Compliance Center in der gleichen Windows PowerShell-Sitzung. Beispielsweise wird **Get-RoleGroup** **Get-CcRoleGroup** in das Wertpapier &amp; Compliance Center.</span><span class="sxs-lookup"><span data-stu-id="c99a1-p109">The text prefix "cc" is added to  *all*  Security &amp; Compliance Center cmdlet names so you can run cmdlets that exist in both Exchange Online and the Security &amp; Compliance Center in the same Windows PowerShell session. For example, **Get-RoleGroup** becomes **Get-ccRoleGroup** in the Security &amp; Compliance Center.</span></span>
  
<span data-ttu-id="c99a1-p110">Unten sehen Sie alle Befehle in einem einzigen Befehlsblock. Geben Sie den Namen Ihres Domänenhosts an, und führen Sie alle Befehle gleichzeitig aus.</span><span class="sxs-lookup"><span data-stu-id="c99a1-p110">Here are all the commands in a single block. Specify the name of your domain host, and then run them all at one time.</span></span>
  
```
$domainHost="<domain host name, such as litware for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Import-Module MsOnline
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession -DisableNameChecking
$ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
Import-PSSession $ccSession -Prefix cc
```

<span data-ttu-id="c99a1-153">Wenn Sie Windows PowerShell-Fenster schließen möchten, führen Sie diesen Befehl, um die aktiven Sitzungen zu Skype für Business Online, Exchange Online, SharePoint Online und die Sicherheit zu entfernen &amp; Compliance Center:</span><span class="sxs-lookup"><span data-stu-id="c99a1-153">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center:</span></span>
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $ccSession ; Disconnect-SPOService
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="c99a1-154">Die Langfassung (Anweisungen mit detaillierten Erläuterungen)</span><span class="sxs-lookup"><span data-stu-id="c99a1-154">The long version (instructions with detailed explanations)</span></span>
<span data-ttu-id="c99a1-155"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="c99a1-155"></span></span>

### <a name="step-1-open-windows-powershell-as-an-administrator"></a><span data-ttu-id="c99a1-156">Schritt 1: Öffnen von Windows PowerShell als Administrator</span><span class="sxs-lookup"><span data-stu-id="c99a1-156">Step 1: Open Windows PowerShell as an administrator</span></span>
<span data-ttu-id="c99a1-157"><a name="Step1"> </a></span><span class="sxs-lookup"><span data-stu-id="c99a1-157"></span></span>

<span data-ttu-id="c99a1-158">Wenn Sie Windows 10, Windows 8, Windows 8.1, 2016 für Windows Server, Windows Server 2012 R2 oder Windows Server 2012 R2 ausführen, müssen Sie dies:</span><span class="sxs-lookup"><span data-stu-id="c99a1-158">If you're running Windows 10, Windows 8, Windows 8.1, Windows Server 2016, Windows Server 2012 R2, or Windows Server 2012 R2, do this:</span></span>
  
1. <span data-ttu-id="c99a1-159">Verwenden Sie eine der folgenden Methoden zum Suchen von Verknüpfung für **Windows PowerShell**:</span><span class="sxs-lookup"><span data-stu-id="c99a1-159">Use any of these methods to find the shortcut for **Windows PowerShell**:</span></span>
    
  - <span data-ttu-id="c99a1-160">Klicken Sie auf der Startseite klicken Sie auf einen leeren Bereich, und geben Sie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c99a1-160">On the Start screen, click an empty area, and type Windows PowerShell.</span></span>
    
  - <span data-ttu-id="c99a1-p111">Drücken Sie die Windows-Taste + F, auf dem Desktop oder im Menü Start. Geben Sie in der Suche Charm Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c99a1-p111">On the desktop or the Start screen, press the Windows key+Q. In the Search charm, type Windows PowerShell.</span></span>
    
  - <span data-ttu-id="c99a1-p112">Verschieben Sie den Cursor an der oberen rechten Ecke, oder führen Sie eine streifbewegung vom rechten Rand des Bildschirms, um die Charms anzuzeigen Anzeigen von links, auf dem Desktop oder im Menü Start. Wählen Sie das Charm Suche aus, und geben Sie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c99a1-p112">On the desktop or the Start screen, move your cursor to the upper-right corner, or swipe left from the right edge of the screen to show the charms. Select the Search charm, and enter Windows PowerShell.</span></span>
    
2. <span data-ttu-id="c99a1-165">In den Suchergebnissen mit der rechten Maustaste in **Windows PowerShell**, und wählen Sie **als Administrator ausführen**.</span><span class="sxs-lookup"><span data-stu-id="c99a1-165">In the results, right-click **Windows PowerShell**, and select **Run as administrator**.</span></span>
    
3. <span data-ttu-id="c99a1-166">Wenn das Dialogfeld " **Benutzerkontensteuerung** " angezeigt wird, wählen Sie **Ja** , um sicherzustellen, dass Sie Windows PowerShell Administratoranmeldeinformationen ausführen möchten.</span><span class="sxs-lookup"><span data-stu-id="c99a1-166">If the **User Account Control** dialog box appears, select **Yes** to verify that you want to run Windows PowerShell under administrator credentials.</span></span>
    
<span data-ttu-id="c99a1-167">Wenn Sie Windows 7 SP1 (oder Windows Server 2008 R2 SP1) ausführen, müssen Sie dies:</span><span class="sxs-lookup"><span data-stu-id="c99a1-167">If you're running Windows 7 SP1 (or Windows Server 2008 R2 SP1), do this:</span></span>
  
1. <span data-ttu-id="c99a1-p113">Wählen Sie im **Startmenü** **Alle Programme** > **Zubehör** > **Windows PowerShell**. Mit der rechten Maustaste in **Windows PowerShell**, und wählen Sie dann auf **als Administrator ausführen**.</span><span class="sxs-lookup"><span data-stu-id="c99a1-p113">On the **Start** menu, select **All Programs** > **Accessories** > **Windows PowerShell**. Right-click **Windows PowerShell**, and then select **Run as administrator**.</span></span>
    
2. <span data-ttu-id="c99a1-170">Wenn das Dialogfeld " **Benutzerkontensteuerung** " angezeigt wird, wählen Sie **Ja** , um sicherzustellen, dass Sie Windows PowerShell Administratoranmeldeinformationen ausführen möchten.</span><span class="sxs-lookup"><span data-stu-id="c99a1-170">If the **User Account Control** dialog box appears, select **Yes** to verify that you want to run Windows PowerShell under administrator credentials.</span></span>
    
<span data-ttu-id="c99a1-p114">Sie müssen Windows PowerShell als Administrator ausführen. Wenn Sie nicht möchten, können Sie ihm eine Fehlermeldung wie die folgende erhalten, wenn Sie versuchen, eine der erforderlichen Module importieren.</span><span class="sxs-lookup"><span data-stu-id="c99a1-p114">You must run Windows PowerShell as an administrator. If you don't, you're going to get an error message similar to this when you try to import one of the required modules.</span></span>
  
```
The specified module 'Microsoft.Online.SharePoint.Online.PowerShell' was not loaded because no valid module file was found in any directory.
```

<span data-ttu-id="c99a1-p115">Die einzige Möglichkeit, Abhilfemaßnahmen ist, schließen Sie Windows PowerShell und starten Sie ihn als Administrator. Hier ist eine schnelle und einfache Möglichkeit zum feststellen, ob Sie Windows PowerShell als Administrator ausführen: die Aufforderung ist `PS C:\Windows\System32>`, nicht `PS C:\Users\YourUserName>`.</span><span class="sxs-lookup"><span data-stu-id="c99a1-p115">The only way to remedy the situation is to close Windows PowerShell and restart it as an administrator. Here's a quick and easy way to tell if you're running Windows PowerShell as an administrator: the prompt is  `PS C:\Windows\System32>`, not  `PS C:\Users\YourUserName>`.</span></span>

  
### <a name="step-2-create-a-windows-powershell-credentials-object"></a><span data-ttu-id="c99a1-175">Schritt 2: Erstellen eines Windows PowerShell-Anmeldeinformationsobjekts</span><span class="sxs-lookup"><span data-stu-id="c99a1-175">Step 2: Create a Windows PowerShell credentials object</span></span>
<span data-ttu-id="c99a1-176"><a name="Step2"> </a></span><span class="sxs-lookup"><span data-stu-id="c99a1-176"></span></span>

<span data-ttu-id="c99a1-p116">Das Anmeldeinformationsobjekt bietet eine verschlüsselte Möglichkeit, Ihren Benutzernamen und das Kennwort an Windows PowerShell zu übergeben. Führen Sie den folgenden Befehl in Windows PowerShell, um eine Anmeldeinformationenobjekt zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="c99a1-p116">The credentials object provides an encrypted way to pass your user name and password to Windows PowerShell. To create a credentials object, run the following command in Windows PowerShell.</span></span>
  
```
$credential = Get-Credential
```

> [!NOTE]
>  <span data-ttu-id="c99a1-p117">`$credential`ist eine Variable, die das Anmeldeinformationsobjekt gespeichert werden. Sie müssen keine nennen Sie die Variable `$credential`, aber dies vereinfacht das merken, welche Variable das Anmeldeinformationsobjekt enthält. (Und das ist wichtig, weil wir diese Variable mehrmals wieder verwendet werden.) Die auch erleichtert die für Sie unsere Beispiele, da in diesem Artikel immer verwendet `$credential` zur Darstellung des Anmeldeinformationenobjekts.</span><span class="sxs-lookup"><span data-stu-id="c99a1-p117">`$credential` is a variable that will store the credentials object. You don't have to name the variable `$credential`, but doing so makes it easier to remember which variable contains the credentials object. (And that's important, because we'll reuse this variable several times.) That will also make it easier for you to follow our examples, because this article will always use  `$credential` to represent the credentials object.</span></span>
  
<span data-ttu-id="c99a1-182">Windows PowerShell wird anschließend ein Dialogfeld angezeigt, die folgendermaßen aussieht.</span><span class="sxs-lookup"><span data-stu-id="c99a1-182">Windows PowerShell will then display a dialog box that looks like this.</span></span>
  
![Leeres Dialogfeld mit Aufforderung zu Anmeldeinformationen.](images/o365_powershell_empty_credentials_box.png)
  
<span data-ttu-id="c99a1-184">Geben Sie Ihre Arbeit oder Schule Konto Benutzernamen in das Feld **Benutzername** das Format _username@domainname_ (beispielsweise kenmyer@litwareinc.onmicrosoft.com); Geben Sie im Feld **Kennwort** Ihr Kennwort ein; und klicken Sie dann auf **OK**:</span><span class="sxs-lookup"><span data-stu-id="c99a1-184">Type your work or school account user name in the **User name** box, using the format _username@domainname_ (for example, kenmyer@litwareinc.onmicrosoft.com); type your password in the **Password** box; and then click **OK**:</span></span>
  
![Ausgefülltes Dialogfeld mit Aufforderung zu Anmeldeinformationen.](images/o365_powershell_completed_credentials_box.png)
  
<span data-ttu-id="c99a1-p118">Beachten Sie, wie häufig der Fall ist, Sie jede Art von Bestätigung nicht sehen, dass das Anmeldeinformationsobjekt erstellt wurde. (Windows PowerShell wird in der Regel bei Dinge Fehler auftreten, aber nicht immer informiert Sie Wenn Dinge rechten wechseln.) Wenn Sie möchten, um sicherzustellen, dass das Anmeldeinformationsobjekt erstellt wurde, geben Sie Folgendes in Windows PowerShell, und drücken Sie dann die EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="c99a1-p118">Note that, as is often the case, you won't see any sort of confirmation that the credentials object was created. (Windows PowerShell typically tells you when things go wrong but doesn't always tell you when things go right.) If you want to verify that the credentials object was created, type the following in Windows PowerShell and then press Enter.</span></span>
  
```
$credential
```

<span data-ttu-id="c99a1-188">Folgendes wird dann auf dem Bildschirm angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c99a1-188">You should then see something similar to this on the screen.</span></span>
  
```
UserName                               Password
--------                               --------
kenmyer@litwareinc.onmicrosoft.com     System.Security.SecureString
```

<span data-ttu-id="c99a1-p119">Eine Sache, denken Sie daran hier besteht darin, dass das Cmdlet [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618) nur das Anmeldeinformationsobjekt erstellt; nicht authentifizieren oder andernfalls stellen Sie sicher, dass der Benutzername und Kennwort eingegebene richtig sind. Nehmen wir beispielsweise an, dass Sie den Benutzernamen als kenmyer@litwareinc.onmicrosoft.com falsch eingegeben. Wenn Sie dies tun, dass **Get-Credential** ein Benutzername mit Anmeldeinformationenobjekt erstellt, und ohne zu überprüfen, um festzustellen, ob das tatsächlich ein gültiger Benutzername ist. Sie werden nicht wissen, ob Sie ein Objekt tatsächlich gültige Anmeldeinformationen erstellt haben, bis Sie tatsächlich dieses Objekt verwenden, um mit den Office 365-Diensten herstellen.</span><span class="sxs-lookup"><span data-stu-id="c99a1-p119">One thing to keep in mind here is that the [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618) cmdlet only creates the credentials object; it does not authenticate you or otherwise verify that the user name and password you supplied are correct. For example, suppose you mistyped the user name as kenmyer@litwareinc.onmicrosoft.com. If you do that, **Get-Credential** will create a credentials object using that user name, and without checking to see if that is actually a valid user name. You won't know whether you have created a truly valid credentials object until you actually use that object to try to connect to the Office 365 services.</span></span>
  
### <a name="step-3-connect-to-office-365"></a><span data-ttu-id="c99a1-192">Schritt 3: Verbinden mit Office 365</span><span class="sxs-lookup"><span data-stu-id="c99a1-192">Step 3: Connect to Office 365</span></span>
<span data-ttu-id="c99a1-193"><a name="Step3"> </a></span><span class="sxs-lookup"><span data-stu-id="c99a1-193"></span></span>

<span data-ttu-id="c99a1-194">Wir beginnen, indem es eine Verbindung zu Office 365 selbst.</span><span class="sxs-lookup"><span data-stu-id="c99a1-194">We'll start by connecting to Office 365 itself.</span></span> 
  
<span data-ttu-id="c99a1-p120">Wir müssen hier Erstes ist das Office 365-Modul (die Microsoft Azure Active Directory-Modul für Windows PowerShell) zu importieren. Zu diesem Zweck führen Sie diesen Befehl in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c99a1-p120">The first thing we need to do here is import the Office 365 module (the Microsoft Azure Active Directory Module for Windows PowerShell). To do that, run this command in Windows PowerShell.</span></span>
  
```
Import-Module MsOnline
```

<span data-ttu-id="c99a1-197">Falls Sie überprüfen möchten, ob das Modul importiert wurde, führen Sie folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="c99a1-197">If you want to verify that the module was imported, run this command.</span></span>
  
```
Get-Module
```

<span data-ttu-id="c99a1-198">An einer beliebigen Stelle in der Liste der Module, die von diesem Befehl sollte angezeigt werden, etwas zurückgegeben werden, die folgendermaßen aussieht: `Manifest 1.0 MSOnline {Add-MsolForeignGroupToRole, Add-MsolG...}`.</span><span class="sxs-lookup"><span data-stu-id="c99a1-198">Somewhere in the list of modules that are returned by this command you should see something that looks like this:  `Manifest 1.0 MSOnline {Add-MsolForeignGroupToRole, Add-MsolG...}`.</span></span>
  
<span data-ttu-id="c99a1-199">Wenn Sie finden Sie unter `MSOnline` aufgeführt, dies bedeutet, dass alles planmäßig verlaufen.</span><span class="sxs-lookup"><span data-stu-id="c99a1-199">If you see  `MSOnline` listed, that means that everything went according to plan.</span></span>
  
<span data-ttu-id="c99a1-200">Das Anmeldeinformationsobjekt erstellt (finden Sie unter [Schritt2: Erstellen einer Windows PowerShell-anmeldeinformationsobjekts](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step2)) und mit der `MsOnline` Modul geladen, wir können nun eine Verbindung zu Office 365 mithilfe der [Connect-MsolService](https://go.microsoft.com/fwlink/p/?LinkId=532375) -Cmdlet und den folgenden Befehl.</span><span class="sxs-lookup"><span data-stu-id="c99a1-200">With the credentials object created (see [Step 2: Create a Windows PowerShell credentials object](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step2)) and with the  `MsOnline` module loaded, we can now connect to Office 365 by using the [Connect-MsolService](https://go.microsoft.com/fwlink/p/?LinkId=532375) cmdlet and the following command.</span></span>
  
```
Connect-MsolService -Credential $credential
```

<span data-ttu-id="c99a1-p121">Beachten Sie, die Sie alle angeben müssen, ist das Anmeldeinformationsobjekt ( `$credential`). Basierend auf den Anmeldeinformationen, verbinden Office 365 automatisch Sie mit der richtigen Domäne. Sie müssen keinen Ihren Domänennamen angeben, wenn **Connect-MsolService**ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="c99a1-p121">Notice that all you have to provide is the credentials object ( `$credential`). Based on those credentials, Office 365 will automatically connect you to the correct domain. You do not have to specify your domain name when running **Connect-MsolService**.</span></span>
  
<span data-ttu-id="c99a1-204">So überprüfen Sie, dass Sie wirklich *sind* mit Office 365 verbunden ist, führen Sie diesen Befehl.</span><span class="sxs-lookup"><span data-stu-id="c99a1-204">To verify that you really  *are*  connected to Office 365, run this command.</span></span>
  
```
Get-MsolDomain
```

<span data-ttu-id="c99a1-205">Die Rückmeldung sollte in etwa so aussehen:</span><span class="sxs-lookup"><span data-stu-id="c99a1-205">In return, you should get back something similar to this.</span></span>
  
```
Name                         Status          Authentication
----                         ------          --------------
litwareinc.onmicrosoft.com   Verified        Managed
```

### <a name="step-4-connect-to-sharepoint-online"></a><span data-ttu-id="c99a1-206">Schritt 4: Herstellen einer Verbindung mit SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="c99a1-206">Step 4: Connect to SharePoint Online</span></span>
<span data-ttu-id="c99a1-207"><a name="Step4"> </a></span><span class="sxs-lookup"><span data-stu-id="c99a1-207"></span></span>

<span data-ttu-id="c99a1-208">Importieren Sie das SharePoint Online-Modul mit dem folgenden Befehl:</span><span class="sxs-lookup"><span data-stu-id="c99a1-208">Import the SharePoint Online module with the following command:</span></span>
  
```
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
```

<span data-ttu-id="c99a1-209">Die _DisableNameChecking_ unterdrückt diese Warnung.</span><span class="sxs-lookup"><span data-stu-id="c99a1-209">The  _DisableNameChecking_ switch suppresses this warning.</span></span>
  
```
WARNING: The names of some imported commands from the module 'Microsoft.Online.SharePoint.PowerShell' include unapproved verbs that might make them less discoverable. To find the commands with unapproved verbs, run the Import-Module command again with the Verbose parameter. For a list of approved verbs, type Get-Verb.
```

<span data-ttu-id="c99a1-p122">Um eine Verbindung mit SharePoint Online herstellen, müssen Sie zwei Datenelemente Informationen bereitstellen: Ihre Anmeldeinformationen und die URL Ihrer SharePoint Online Admin-Website. Das Webpart Anmeldeinformationen ist einfach: Wir haben, die bereits in der Variablen gespeichert `$credential` (finden Sie unter [Schritt2: Erstellen einer Windows PowerShell-anmeldeinformationsobjekts](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step2)). Wie für die URL der Website, die einfach genug, um zu bestimmen, wie gut ist Admin. Angenommen, Ihre Office 365-Domänenname ist `litwareinc.onmicrosoft.com`.</span><span class="sxs-lookup"><span data-stu-id="c99a1-p122">In order to connect to SharePoint Online, you need to supply two pieces of information: your credentials and the URL of your SharePoint Online admin site. The credentials part is easy: we've already stored that in the variable  `$credential` (see [Step 2: Create a Windows PowerShell credentials object](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step2)). As for the URL of your admin site, that's easy enough to determine, as well. Suppose your Office 365 domain name is  `litwareinc.onmicrosoft.com`.</span></span>
  
<span data-ttu-id="c99a1-214">Gehen Sie wie folgt vor, um die URL der Admin-Website zu ermitteln:</span><span class="sxs-lookup"><span data-stu-id="c99a1-214">To determine the admin site URL, do this:</span></span>
  
1. <span data-ttu-id="c99a1-215">Starten Sie mit dem Präfix `https://`.</span><span class="sxs-lookup"><span data-stu-id="c99a1-215">Start by using the prefix  `https://`.</span></span>
    
2. <span data-ttu-id="c99a1-p123">Fügen Sie den Host Domänenteil des Domänennamens hinzu. Beispiel für `litwareinc.onmicrosoft.com`, ist der Hostname der Domäne `litwareinc`. Für `contoso.onmicrosoft.com`, ist der Hostname der Domäne `contoso`.</span><span class="sxs-lookup"><span data-stu-id="c99a1-p123">Add the domain host portion of your domain name. For example, for  `litwareinc.onmicrosoft.com`, the domain host name is  `litwareinc`. For  `contoso.onmicrosoft.com`, the domain host name is  `contoso`.</span></span>
    
3. <span data-ttu-id="c99a1-219">Fügen Sie einen Bindestrich (-) gefolgt von `admin.sharepoint.com`.</span><span class="sxs-lookup"><span data-stu-id="c99a1-219">Add a hyphen (-) followed by  `admin.sharepoint.com`.</span></span>
    
<span data-ttu-id="c99a1-220">Mit anderen Worten:</span><span class="sxs-lookup"><span data-stu-id="c99a1-220">In other words:</span></span>
  
 `https://` + `litwareinc` + `-admin.sharepoint.com` = `https://litwareinc-admin.sharepoint.com`
  
<span data-ttu-id="c99a1-p124">Nachdem Sie die URL erstellt haben, klicken Sie dann können die URL und Ihre Anmeldeinformationenobjekt Sie mit SharePoint Online herstellen. Rufen Sie einfach das [Connect-SPOService](https://go.microsoft.com/fwlink/p/?LinkId=532436) -Cmdlet, mit einem Befehl wie den folgenden.</span><span class="sxs-lookup"><span data-stu-id="c99a1-p124">After you've constructed the URL, you can then use that URL and your credentials object to connect to SharePoint Online. Just call the [Connect-SPOService](https://go.microsoft.com/fwlink/p/?LinkId=532436) cmdlet, using a command similar to this one.</span></span>
  
```
Connect-SPOService -Url https://litwareinc-admin.sharepoint.com -credential $credential
```

<span data-ttu-id="c99a1-223">Um sicherzustellen, dass die Verbindung hergestellt wurde, führen Sie den folgenden Befehl in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c99a1-223">To verify that the connection has been made, run the following command in Windows PowerShell.</span></span>
  
```
Get-SPOSite
```

<span data-ttu-id="c99a1-p125">Sie sollten eine Liste aller Ihrer SharePoint Online-Websites erhalten. Es folgt ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="c99a1-p125">You should get a list of all your SharePoint Online sites. Here is an example:</span></span>
  
```
Url                                       Owner          Storage Quota
---                                       -----          -------------
http://litwareinc-public.sharepoint.com/                 1000
https://litwareinc.sharepoint.com/                       1000
https://litwareinc.sharepoint.com/search                 1000
```

<span data-ttu-id="c99a1-p126">Ihre Office 365-Befehle (derjenigen, die in beschriebenen [Schritt 3: Verbinden mit Office 365](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step3)) wird jedoch trotzdem funktionsfähig. (Führen Sie **Get-MsolUser**und überzeugen Sie sich selbst.) Dies bedeutet, dass Sie jetzt Office 365 und SharePoint Online aus der gleichen Instanz von Windows PowerShell verwalten können.</span><span class="sxs-lookup"><span data-stu-id="c99a1-p126">Your Office 365 commands (the ones described in [Step 3: Connect to Office 365](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step3)) will still work. (Try running **Get-MsolUser**, and see for yourself.) That means that you can now manage both Office 365 and SharePoint Online from the same instance of Windows PowerShell.</span></span>
  
### <a name="step-5-connect-to-skype-for-business-online"></a><span data-ttu-id="c99a1-228">Schritt 5: Herstellen einer Verbindung mit Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="c99a1-228">Step 5: Connect to Skype for Business Online</span></span>
<span data-ttu-id="c99a1-229"><a name="Step5"> </a></span><span class="sxs-lookup"><span data-stu-id="c99a1-229"></span></span>

<span data-ttu-id="c99a1-p127">Verbinden mit Skype für Business Online (und Exchange Online oder die Sicherheit &amp; Compliance Center) unterscheidet sich eine Verbindung mit Office 365 mit SharePoint Online. Dies liegt daran die Skype für Business Online und Exchange Online-Cmdlets nicht auf Ihrem Computer installierten erhalten möchten, wie die Office 365 und SharePoint Online-Cmdlets. Stattdessen werden jedes Mal, wenn Sie sich anmelden den entsprechenden Cmdlets vorübergehend an Ihren Computer kopiert. Wenn Sie sich abmelden, werden diese Cmdlets klicken Sie dann auf Ihrem Computer entfernt.</span><span class="sxs-lookup"><span data-stu-id="c99a1-p127">Connecting to Skype for Business Online (and to Exchange Online or the Security &amp; Compliance Center) is different than connecting to Office 365 or to SharePoint Online. That's because the Skype for Business Online and Exchange Online cmdlets don't get installed on your computer like the Office 365 and the SharePoint Online cmdlets do. Instead, each time you sign in, the appropriate cmdlets are temporarily copied to your computer. When you sign off, those cmdlets are then removed from your computer.</span></span>
  
<span data-ttu-id="c99a1-p128">Um mit Skype für Business Online verbinden, müssen Sie die Skype für Business Online Modul zu importieren. Zu diesem Zweck führen Sie diesen Befehl aus.</span><span class="sxs-lookup"><span data-stu-id="c99a1-p128">In order to connect to Skype for Business Online, you need to import the Skype for Business Online module. To do that, run this command.</span></span>
  
```
Import-Module SkypeOnlineConnector
```

<span data-ttu-id="c99a1-236">Beim ersten Mal wird möglicherweise die folgende Warnmeldung angezeigt, die Sie ignorieren können.</span><span class="sxs-lookup"><span data-stu-id="c99a1-236">The first time you do this, you might see the following warning message, which you can safely ignore.</span></span>
  
```
WARNING: WSMan NetworkDelayms has been set to 30000 milliseconds. The previous value was 5000 milliseconds.
WARNING: To improve the performance of the Lync Online Connector, it is recommended that the network delay be set to
30000 milliseconds (30 seconds). However, you can use Set-WinRMNetworkDelayMS to change the network delay to any
integer value.
```

<span data-ttu-id="c99a1-237">Nachdem Sie das Modul importiert haben, müssen Sie folgenden Befehl ausführen:</span><span class="sxs-lookup"><span data-stu-id="c99a1-237">After the module has been imported, run this command.</span></span>
  
```
$sfboSession = New-CsOnlineSession -Credential $credential
```

<span data-ttu-id="c99a1-p129">Wir haben eine remote-PowerShell-Sitzung erstellt. In diesem Fall also, dass wir bei einer Instanz von Windows PowerShell eine Verbindung hergestellt haben, die auf einem der Office 365-Server ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="c99a1-p129">We have created a remote PowerShell session. In this case, that means that we've connected to an instance of Windows PowerShell running on one of the Office 365 servers.</span></span> 
  
<span data-ttu-id="c99a1-p130">Obwohl es eine Verbindung zu Office 365 hergestellt haben, noch nicht wir die Skripts, Cmdlets und andere Elemente zum Verwalten von Skype für Business Online heruntergeladen. Dazu haben wir diesen Befehl ausführen.</span><span class="sxs-lookup"><span data-stu-id="c99a1-p130">Although we've made a connection to Office 365, we haven't downloaded the scripts, cmdlets, and other items needed to manage Skype for Business Online. To do that, we have to run this command.</span></span>
  
```
Import-PSSession $sfboSession
```

<span data-ttu-id="c99a1-242">Beim Importieren von Windows PowerShell-Sitzung sollte eine Statusanzeige ähnlich dem folgenden, eine Statusanzeige angezeigt werden, die alle Skype für Business Online Cmdlets, die zu importierenden an Ihren Computer meldet.</span><span class="sxs-lookup"><span data-stu-id="c99a1-242">When you import the Windows PowerShell session, you should see a progress bar similar to the following, a progress bar that reports on all the Skype for Business Online cmdlets being imported to your computer.</span></span>
  
![Lync Online-Statusanzeige.](images/o365_powershell_lync_progress_bar.png)
  
<span data-ttu-id="c99a1-244">Sobald die Statusanzeige ausgeblendet wird, sollte die Ausgabe wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="c99a1-244">When the progress bar disappears, you should then see output similar to the following.</span></span>
  
```
ModuleType Version    Name               ExportedCommands
---------- -------    ----               ----------------
Script     1.0        tmp_swc5mp4v.1ck  {Copy-CsVoicePolicy, Disabl...
```

### <a name="step-6-connect-to-exchange-online"></a><span data-ttu-id="c99a1-245">Schritt 6: Herstellen einer Verbindung mit Exchange Online</span><span class="sxs-lookup"><span data-stu-id="c99a1-245">Step 6: Connect to Exchange Online</span></span>
<span data-ttu-id="c99a1-246"><a name="Step6"> </a></span><span class="sxs-lookup"><span data-stu-id="c99a1-246"></span></span>

<span data-ttu-id="c99a1-247">Führen Sie diesen Befehl, der eine remote Windows PowerShell-Sitzung mit Exchange Online erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="c99a1-247">Run this command, which creates a remote Windows PowerShell session with Exchange Online.</span></span>
  
```
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
```

> [!NOTE]
> <span data-ttu-id="c99a1-p131">Warum ist der Befehl für die Verbindung mit Exchange Online komplizierter den Befehl zum Skype für Business Online herstellen? Es ist technisch gesehen nicht: beide Befehle führen Sie genaue das gleiche. Die Skype für Business Online Team erstellt jedoch eine eigene Cmdlet – **New CsOnlineSession** –, die ein Teil der Parameter (wie _Authentifizierung_ und _AllowRedirection_), die beim Herstellen einer Verbindung zu Exchange Online verwendet werden ausgeblendet. Anstatt Sie diese Informationen selbst eingeben, werden die _Authentifizierung_ und _AllowRedirection_ -Parameter effektiv an das Cmdlet **New-CsOnlineSession** integriert. Sie müssen diese Parameter geben Sie beim Herstellen einer Verbindung zu Exchange Online, da Exchange Online mit dem standard [New-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389621) -Cmdlet verwendet, um zu Office 365 herzustellen. Der Nachteil ist, dass Sie etwas eingeben, um Aktionen auszuführen. Der Vorteil ist, dass Sie nicht herunterladen und Installieren von Exchange Online-Modul.</span><span class="sxs-lookup"><span data-stu-id="c99a1-p131">Why is the command for connecting to Exchange Online more complicated than the command to connect to Skype for Business Online? Technically, it's not: both commands do the exact same thing. However, the Skype for Business Online team created its own cmdlet— **New-CsOnlineSession** —that hides some of the parameters (like _Authentication_ and _AllowRedirection_) that are used when connecting to Exchange Online. Instead of requiring you to type that information yourself, the  _Authentication_ and _AllowRedirection_ parameters are effectively built in to the **New-CsOnlineSession** cmdlet. You have to type those parameters when connecting to Exchange Online because Exchange Online uses the standard [New-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389621) cmdlet to connect to Office 365. The disadvantage is that you have a little more typing to do. The advantage is that you don't have to download and install an Exchange Online module.</span></span>
  
<span data-ttu-id="c99a1-255">Müssen Sie jetzt nur diese Remotesitzung importieren, genau wie haben wir mit Skype für Business Online.</span><span class="sxs-lookup"><span data-stu-id="c99a1-255">All you have to do now is import this remote session, just like we did with Skype for Business Online.</span></span>
  
```
Import-PSSession $exchangeSession -DisableNameChecking
```

<span data-ttu-id="c99a1-256">Folgendes wird auf dem Bildschirm angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c99a1-256">You should see something similar to this on the screen.</span></span>
  
```
ModuleType Version  Name             ExportedCommands
---------- -------  ----             ----------------
Script     1.0      tmp_nweiqjvl.geu {Add-AvailabilityAddressSpace...
```

<span data-ttu-id="c99a1-257">Versuchen Sie nun, diesen Befehl auszuführen.</span><span class="sxs-lookup"><span data-stu-id="c99a1-257">Now try running this command.</span></span>
  
```
Get-AcceptedDomain
```

<span data-ttu-id="c99a1-258">Wiederum sollte finden Sie Informationen über Ihre Office 365-Domänen, die in Exchange Online für e-Mail-Adressen konfiguriert sind.</span><span class="sxs-lookup"><span data-stu-id="c99a1-258">In return, you should see information about your Office 365 domains that are configured for email addresses in Exchange Online.</span></span>
  
```
Name            DomainName          DomainType      Default
----            ----------          ----------      -------
litwareinc.com  litwareinc.com      Authoritative   True
```

### <a name="step-7-connect-to-the-security-amp-compliance-center"></a><span data-ttu-id="c99a1-259">Schritt 7: Verbinden mit der Sicherheit &amp; Compliance Center</span><span class="sxs-lookup"><span data-stu-id="c99a1-259">Step 7: Connect to the Security &amp; Compliance Center</span></span>
<span data-ttu-id="c99a1-260"><a name="Step7"> </a></span><span class="sxs-lookup"><span data-stu-id="c99a1-260"></span></span>

<span data-ttu-id="c99a1-p132">Die Sicherheit &amp; Compliance Center ist ein Dienst in Office 365, die Sie zum Verwalten von Compliance-Funktionen von einem Speicherort können. Weitere Informationen finden Sie unter [Office 365 Compliance Center](http://technet.microsoft.com/library/fde83656-f136-448d-b250-6fa17b503e4e.aspx).</span><span class="sxs-lookup"><span data-stu-id="c99a1-p132">The Security &amp; Compliance Center is a service in Office 365 that lets you to manage compliance features from one location. For more information, see [Office 365 compliance center](http://technet.microsoft.com/library/fde83656-f136-448d-b250-6fa17b503e4e.aspx).</span></span>
  
<span data-ttu-id="c99a1-263">Die Verbindung Anweisungen für die Sicherheit &amp; Compliance Center sind sehr ähnlich wie die für Exchange Online, jedoch mit abwechselnd, die Sie in Kürze sehen werden.</span><span class="sxs-lookup"><span data-stu-id="c99a1-263">The connection instructions for the Security &amp; Compliance Center are very similar to those for Exchange Online, but with an added twist, which you'll see in a moment.</span></span>
  
<span data-ttu-id="c99a1-264">Führen Sie diesen Befehl, der eine remote-PowerShell-Sitzung mit der Sicherheit erstellt &amp; Compliance Center.</span><span class="sxs-lookup"><span data-stu-id="c99a1-264">Run this command, which creates a remote PowerShell session with the Security &amp; Compliance Center.</span></span>
  
```
$ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
```

<span data-ttu-id="c99a1-265">Führen Sie jetzt diesen Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="c99a1-265">Now run this command:</span></span>
  
```
Import-PSSession $ccSession -Prefix cc
```

<span data-ttu-id="c99a1-p133">Mit diesem Befehl ist erneut, den Befehl für Exchange Online sehr ähnlich. Die Option _DisableNameChecking_ ist nicht erforderlich, da es keine nicht genehmigten Verben in das Wertpapier sind &amp; Compliance Center. Aber was, dass zusätzliche `-Prefix cc` Parameter und Wert? Die abwechselnd, die wir Sie zu eingerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="c99a1-p133">Again, this command is very similar to the command for Exchange Online. The  _DisableNameChecking_ switch isn't required because there are no unapproved verbs in the Security &amp; Compliance Center. But what about that additional `-Prefix cc` parameter and value? That's the added twist we told you about.</span></span>
  
<span data-ttu-id="c99a1-p134">Exchange Online und die Sicherheit &amp; Compliance Center einige-Cmdlets, die denselben Namen haben, und geben Sie die gleiche Funktionalität freigeben. **Get-RoleGroup** ist ein Beispiel.</span><span class="sxs-lookup"><span data-stu-id="c99a1-p134">Exchange Online and the Security &amp; Compliance Center share some cmdlets that have exactly the same names and provide the same functionality. **Get-RoleGroup** is an example.</span></span>
  
<span data-ttu-id="c99a1-p135">Was passiert, wenn Sie versuchen, zwei Sitzungen zu importieren, die mit dem gleichen Namen Cmdlets enthalten? Sie kollidieren. Sie erhalten eine große gelbe Warnung angezeigt, die besagt, `WARNING: Proxy creation has been skipped for the following command:` gefolgt von der Liste der miteinander in Konflikt stehende Cmdlets, die konnte nicht importiert werden. Das Ergebnis? **Get-RoleGroup** kann in Exchange Online ausgeführt werden, da Sie es zuerst verbunden, aber **Get-RoleGroup** nicht werden, in das Wertpapier ausgeführt kann &amp; Compliance Center, da Sie verbunden es zuletzt und die miteinander in Konflikt stehende Cmdlets importieren abgelehnt.</span><span class="sxs-lookup"><span data-stu-id="c99a1-p135">So what happens if you try to import two sessions that contain cmdlets with the same name? They collide. You'll get a big yellow warning message that says,  `WARNING: Proxy creation has been skipped for the following command:` followed by the list of conflicting cmdlets that couldn't be imported. The end result? You can run **Get-RoleGroup** in Exchange Online because you connected there first, but you can't run **Get-RoleGroup** in the Security &amp; Compliance Center because you connected there last and the conflicting cmdlets refused to import.</span></span>
  
<span data-ttu-id="c99a1-p136">Die einfachste Möglichkeit für den Umgang mit diesem Problem wird die importierten Sicherheit ein Präfix für den beliebiger Text hinzugefügt &amp; Compliance Center-Cmdlets. Wir haben, mit dem _Präfix_ Parameter mit dem Wert "cc" der **Import-PSSession** -Cmdlet. Was, die für uns? Es Konflikte durch (etwas) Ändern der Sicherheits entfernt &amp; Compliance Center-Cmdlet-Namen für diese Sitzung. Alle importierten &amp; Compliance Center-Cmdlets mit "cc" jetzt im Substantiv Teil des Cmdlet-Namen starten (rechts neben der "-"). Beispielsweise wird mit dem strittigen **Get-RoleGroup** -Cmdlet **Get-CcRoleGroup** für die Sicherheit &amp; Compliance Center für Exchange Online mit **Get-RoleGroup** Konflikt nicht.</span><span class="sxs-lookup"><span data-stu-id="c99a1-p136">The easiest way to deal with this problem is to add an arbitrary text prefix to the imported Security &amp; Compliance Center cmdlets. We did that using the  _Prefix_ parameter with the value "cc" on the **Import-PSSession** cmdlet. What did that do for us? It eliminated the conflicts by (slightly) changing the Security &amp; Compliance Center cmdlet names for this session. All of the imported Security &amp; Compliance Center cmdlets now start with "cc" in the noun part of the cmdlet name (to the right of the "-"). For example, the contentious **Get-RoleGroup** cmdlet becomes **Get-ccRoleGroup** for the Security &amp; Compliance Center so it doesn't conflict with **Get-RoleGroup** for Exchange Online.</span></span>
  
<span data-ttu-id="c99a1-p137">Der Nachteil?  *Alle*  Sicherheit &amp; Compliance Center-Cmdlet-Namen, erhalten das Präfix "cc" – sogar eindeutige Cmdlets aufgeführt, die sie benötigen. **Get-ComplianceSearch** wird beispielsweise **Get-CcComplianceSearch** , obwohl es keine solche Cmdlet in Exchange Online ist. Es ist ein Bit für eine Probleme jedoch nicht allzu sehr, wenn Sie die Vorteile der Verwaltung von allen Office 365-Diensten in einer einzigen Windows PowerShell-Sitzung berücksichtigen. Denken Sie die Cmdlet-Namen für alle Prozeduren in das Wertpapier hinzufügen "cc" &amp; Compliance Center.</span><span class="sxs-lookup"><span data-stu-id="c99a1-p137">The downside?  *All*  Security &amp; Compliance Center cmdlet names receive the "cc" prefix—even unique cmdlets that don't need it. For example, **Get-ComplianceSearch** becomes **Get-ccComplianceSearch** even though there is no such cmdlet in Exchange Online. It's a bit of a pain, but not too bad when you consider the benefits of managing all Office 365 services in a single Windows PowerShell session. Just remember to add "cc" to the cmdlet names for all procedures in the Security &amp; Compliance Center.</span></span>
  
<span data-ttu-id="c99a1-288">Es sollte dann in etwa Folgendes angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="c99a1-288">If all goes well, you'll see something similar to this:</span></span>
  
```
ModuleType Version  Name             ExportedCommands
---------- -------  ----             ----------------
Script     1.0      tmp_xbbx5exr.ehm {Add-ccRoleGroupMember, Get-ccAdminAuditLogConfig, Get-ccA...
```

<span data-ttu-id="c99a1-289">Nun können Sie alle Office 365-Diensten in einer einzigen Windows PowerShell-Sitzung zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="c99a1-289">Now you are free to manage all Office 365 services in a single Windows PowerShell session.</span></span>
  
### <a name="step-8-gracefully-end-your-powershell-sessions"></a><span data-ttu-id="c99a1-290">Schritt 8: Problemloses Beenden Ihrer PowerShell-Sitzungen</span><span class="sxs-lookup"><span data-stu-id="c99a1-290">Step 8: Gracefully end your PowerShell sessions</span></span>
<span data-ttu-id="c99a1-291"><a name="Step8"> </a></span><span class="sxs-lookup"><span data-stu-id="c99a1-291"></span></span>

<span data-ttu-id="c99a1-p138">Wenn Sie nur das Windows PowerShell-Fenster schließen, wird Ihre Skype für Business Online Remoteverbindung für die nächsten 15 Minuten aktiv bleiben. Da Skype für Business Online einer Person oder einer beliebigen eine Domäne geöffnet haben, kann die Anzahl gleichzeitiger Verbindungen beschränkt ist, konnte die ein Problem sein. Mit Skype für Business Online kann ein einzelner Administrator, höchstens drei offene Verbindungen gleichzeitig, und eine Domäne kann maximal neun offenen Verbindungen haben. Wenn Sie bei Skype für Business Online anmelden, und klicken Sie dann zu beenden, ohne die Sitzung ordnungsgemäß schließen, bleibt dieser Sitzung für die nächsten 15 Minuten geöffnet. Daher ist eine weniger Verbindung können Sie oder andere Administratoren in Ihrer Domäne.</span><span class="sxs-lookup"><span data-stu-id="c99a1-p138">If you just close the Windows PowerShell window, your Skype for Business Online remote connection will remain active for the next 15 minutes or so. Because Skype for Business Online limits the number of simultaneous connections that any one person or any one domain can have open, that could be a problem. With Skype for Business Online, an individual administrator can have, at most, three open connections at one time, and a domain can have a maximum of nine open connections. If you sign in to Skype for Business Online and then exit without properly closing the session, that session remains open for the next 15 minutes or so. As a result, that's one fewer connection available to you or to other administrators in your domain.</span></span>
  
<span data-ttu-id="c99a1-p139">Stattdessen für Skype für Business Online, Exchange Online und die Sicherheit die remote-Sitzungen wir schließen &amp; Compliance Center ordnungsgemäß. Bevor wir dies tun, führen Sie diesen Befehl aus.</span><span class="sxs-lookup"><span data-stu-id="c99a1-p139">Instead, let's close the remote sessions for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center gracefully. Before we do that, run this command.</span></span>
  
```
Get-PSSession
```

<span data-ttu-id="c99a1-p140">Das Cmdlet [Get-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=532437) sollte zeigen Sie, dass Sie über mindestens drei Remotesitzungen öffnen, eine für Skype für Business Online, eine für Exchange Online und eine für die Sicherheit verfügen &amp; Compliance Center (es ist möglich möglicherweise mehr als drei Remote Sitzungen ausgeführt, je nachdem, ob Sie diese Instanz von Windows PowerShell zum Verbinden mit etwas anderes neben der Office 365-Dienste verwendet haben). Sie sollte etwa wie folgt angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="c99a1-p140">The [Get-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=532437) cmdlet should show you that you have at least three remote sessions open, one for Skype for Business Online, one for Exchange Online and one for the Security &amp; Compliance Center (it's possible you could have more than three remote sessions running, depending on whether you've used this instance of Windows PowerShell to connect to something else besides the Office 365 services). You should see something similar to the following.</span></span>
  
```
Id Name     ComputerName     State   ConfigurationName    Availability
-- ----     ------------     -----   -----------------    ------------
 1 Session1 webdir0a.onl...  Opened  Microsoft.PowerShell    Available
 2 Session2 outlook.offi...  Opened  Microsoft.Exchange      Available
 3 Session3 ps.complianc...  Opened  Microsoft.Exchange      Available
```

<span data-ttu-id="c99a1-p141">Schließen Sie diese drei Sitzungen, führen Sie diese Befehle jeweils einzeln. Der erste Befehl schließt die Skype für Business Online-Sitzung, die zweite schließt die Exchange Online-Sitzung, und die dritte schließt die Sicherheit &amp; Compliance Center-Sitzung.</span><span class="sxs-lookup"><span data-stu-id="c99a1-p141">To close these three sessions, run these commands one at a time. The first command closes the Skype for Business Online session, the second closes the Exchange Online session, and the third closes the Security &amp; Compliance Center session.</span></span>
  
```
Remove-PSSession $sfboSession
Remove-PSSession $exchangeSession
Remove-PSSession $ccSession
```

<span data-ttu-id="c99a1-303">Wenn Sie nun das **Get-PSSession** -Cmdlet ausführen, sollte Sie nichts überhaupt angezeigt werden (es sei denn, Sie andere Remotesitzungen dargelegten verwenden).</span><span class="sxs-lookup"><span data-stu-id="c99a1-303">If you now run the **Get-PSSession** cmdlet, you should see nothing at all (unless you have other remote sessions up and running).</span></span>
  
![Windows PowerShell-Konsole ohne Remotesitzungen](images/o365_powershell_no_remote_sessions.png)
  
> [!NOTE]
> <span data-ttu-id="c99a1-305">Wenn Sie alle remote-Sitzungen gleichzeitig schließen möchten, können Sie diesen Befehl verwenden: >`Get-PSSession | Remove-PSSession`</span><span class="sxs-lookup"><span data-stu-id="c99a1-305">If you'd prefer to close all your remote sessions at the same time, you can use this command: >  `Get-PSSession | Remove-PSSession`</span></span>
  
<span data-ttu-id="c99a1-306">Wenn Sie jetzt versuchen, das ein Cmdlet aus einer dieser geschlossen Sitzungen (beispielsweise **Get-CsMeetingConfiguration** in Skype für Business Online) erhalten Sie eine Fehlermeldung, die diese ähnlich ist.</span><span class="sxs-lookup"><span data-stu-id="c99a1-306">If you now try running a cmdlet from any of these closed sessions (for example, **Get-CsMeetingConfiguration** in Skype for Business Online) you'll get an error message that's similar to this one.</span></span>
  
```
Get-CsMeetingConfiguration : The term 'Get-CsMeetingConfiguration' is not recognized as the name of a cmdlet, function, script file, or operable program. Check the spelling of the name, or if a path was included, verify that the path is correct and try again.
```

<span data-ttu-id="c99a1-307">Wir erhalten diese Fehlermeldung, da die Cmdlets für Skype für Business Online, Exchange Online und die Sicherheit &amp; Compliance Center gelöscht wurden, wenn wir die remote-Sitzungen geschlossen.</span><span class="sxs-lookup"><span data-stu-id="c99a1-307">We get that error message because the cmdlets for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center were deleted when we closed the remote sessions.</span></span>
  
<span data-ttu-id="c99a1-308">Geben Sie folgenden Befehl, um die SharePoint Online-Sitzung zu schließen.</span><span class="sxs-lookup"><span data-stu-id="c99a1-308">To close the SharePoint Online session, type this command.</span></span>
  
```
Disconnect-SPOService
```

<span data-ttu-id="c99a1-309">Wenn Sie versuchen Sie nun das **Get-SPOSite** -Cmdlet ausführen, erhalten Sie eine Fehlermeldung wie folgt.</span><span class="sxs-lookup"><span data-stu-id="c99a1-309">If you now try to run the **Get-SPOSite** cmdlet, you'll get an error message like this.</span></span>
  
```
get-sposite : No connection available. Use Connect-SPOService before running this CmdLet.
```

<span data-ttu-id="c99a1-310">Sie können keine Websiteinformationen abrufen, da Sie nicht mehr mit SharePoint Online verbunden sind.</span><span class="sxs-lookup"><span data-stu-id="c99a1-310">You can't retrieve site information because you're no longer connected to SharePoint Online.</span></span>
  
<span data-ttu-id="c99a1-p142">Wie bei der Verbindung zu Office 365 Obwohl es ein **Connect-MsolService** -Cmdlet ist besteht keine entsprechende **Disconnect-MsolService** -Cmdlet. So für Office 365, schließen Sie einfach das Windows PowerShell-Fenster. Dennoch ist weiterhin empfiehlt sich, diese Schritte durchführen, damit Sie ordnungsgemäß von SharePoint Online, Skype für Business Online, Exchange Online und die Sicherheit zu trennen können der letzten &amp; Compliance Center.</span><span class="sxs-lookup"><span data-stu-id="c99a1-p142">As for your connection to Office 365, although there's a **Connect-MsolService** cmdlet, there's no corresponding **Disconnect-MsolService** cmdlet. So for Office 365, just close the Windows PowerShell window. Nevertheless, it's still a good idea to do this last so you can properly disconnect from SharePoint Online, Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center.</span></span>
  
## <a name="new-to-office-365"></a><span data-ttu-id="c99a1-314">Neu bei Office 365?</span><span class="sxs-lookup"><span data-stu-id="c99a1-314">New to Office 365?</span></span>
<span data-ttu-id="c99a1-315"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="c99a1-315"></span></span>

||
|:-----|
|<span data-ttu-id="c99a1-p143">![Das kurze Symbol für LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **neu zu Office 365?**         Entdecken Sie kostenlose video Kurse für [Office 365-Administratoren und IT-Experten](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5), bereitgestellt von LinkedIn Learning.</span><span class="sxs-lookup"><span data-stu-id="c99a1-p143">![The short icon for LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **New to Office 365?**         Discover free video courses for [Office 365 admins and IT pros](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5), brought to you by LinkedIn Learning.</span></span> |
   
## <a name="see-also"></a><span data-ttu-id="c99a1-318">See also</span><span class="sxs-lookup"><span data-stu-id="c99a1-318">See also</span></span>

#### 

[<span data-ttu-id="c99a1-319">Verwalten von Office 365 mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c99a1-319">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="c99a1-320">Erste Schritte mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c99a1-320">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="c99a1-321">Verwalten von SharePoint Online mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c99a1-321">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
  
[<span data-ttu-id="c99a1-322">Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c99a1-322">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="c99a1-323">Verwenden der Windows PowerShell zum Erstellen von Berichten in Office 365</span><span class="sxs-lookup"><span data-stu-id="c99a1-323">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)

