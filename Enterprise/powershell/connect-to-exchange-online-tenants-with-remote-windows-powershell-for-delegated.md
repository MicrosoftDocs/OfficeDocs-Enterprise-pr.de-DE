---
title: "Verbinden mit Exchange Online-Mandanten über eine Remotesitzung von Windows PowerShell für Partner mit delegierten Zugriffsberechtigungen (Delegated Access Permissions, DAP)"
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: 
ms.assetid: ae5f1a87-8b77-4f93-a1b8-56f800aeb283
description: 'Zusammenfassung: Verwenden Sie eine Remotesitzung von Windows PowerShell, um eine Verbindung mit Exchange Online anhand des DelegatedOrg-Parameters herzustellen.'
ms.openlocfilehash: 857c97e5d3374f293b98298419932af4ce2dfa19
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2018
---
# <a name="connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="95447-103">Verbinden mit Exchange Online-Mandanten über eine Remotesitzung von Windows PowerShell für Partner mit delegierten Zugriffsberechtigungen (Delegated Access Permissions, DAP)</span><span class="sxs-lookup"><span data-stu-id="95447-103">Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

 <span data-ttu-id="95447-104">**Zusammenfassung:** Verwenden Sie eine Remotesitzung von Windows PowerShell, um eine Verbindung mit Exchange Online anhand des _DelegatedOrg_-Parameters herzustellen.</span><span class="sxs-lookup"><span data-stu-id="95447-104">**Summary:** Use remote Windows PowerShell to connect to Exchange Online by using the _DelegatedOrg_ parameter.</span></span>
  
<span data-ttu-id="95447-p101">Mit Remote-Windows PowerShell können Sie die Exchange Online-Einstellungen über die Befehlszeile verwalten. Sie verwenden Windows PowerShell auf dem lokalen Computer und stellen eine Remotesitzung mit Exchange Online her. Dies ist ein Verfahren mit drei Schritten: Zuerst geben Sie Ihre Exchange Online-Anmeldeinformationen ein, dann geben Sie die erforderlichen Verbindungseinstellungen an, und zum Schluss importieren Sie die Exchange Online-Cmdlets in Ihre lokale Windows PowerShell-Sitzung, um Sie dafür verwenden zu können.</span><span class="sxs-lookup"><span data-stu-id="95447-p101">Remote Windows PowerShell lets you manage your Exchange Online settings from the command line. You use Windows PowerShell on your local computer to create a remote session to Exchange Online. It's a three-step process where you enter your Exchange Online credentials, provide the required connection settings, and then import the Exchange Online cmdlets into your local Windows PowerShell session so that you can use them.</span></span>
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="95447-108">Was sollten Sie wissen, bevor Sie beginnen?</span><span class="sxs-lookup"><span data-stu-id="95447-108">What do you need to know before you begin?</span></span>

- <span data-ttu-id="95447-109">Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten</span><span class="sxs-lookup"><span data-stu-id="95447-109">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="95447-110">Sie können folgende Versionen von Windows verwenden:</span><span class="sxs-lookup"><span data-stu-id="95447-110">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="95447-111">Windows 10</span><span class="sxs-lookup"><span data-stu-id="95447-111">Windows 10</span></span>
    
  - <span data-ttu-id="95447-112">Windows 8.1 oder Windows 8</span><span class="sxs-lookup"><span data-stu-id="95447-112">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="95447-113">Windows Server 2012 R2 oder Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="95447-113">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="95447-114">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="95447-114">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="95447-115">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="95447-115">Windows Server 2008 R2 SP1\*</span></span>
    
    * <span data-ttu-id="95447-p102">Sie müssen das .NET Framework 4.5.1 oder das .NET Framework 4.5 und dann entweder Windows Management Framework 4.0 oder Windows Management Framework 3.0 installieren. Weitere Informationen finden Sie in den folgenden Ressourcen:</span><span class="sxs-lookup"><span data-stu-id="95447-p102">You need to install the .NET Framework 4.5.1 or the .NET Framework 4.5 and then either the Windows Management Framework 4.0 or the Windows Management Framework 3.0 . For more information, see the following resources:</span></span>
    
  - [<span data-ttu-id="95447-118">Installieren von .NET Framework</span><span class="sxs-lookup"><span data-stu-id="95447-118">Installing the .NET Framework</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=257868)
    
  - <span data-ttu-id="95447-119">[Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) oder[Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)</span><span class="sxs-lookup"><span data-stu-id="95447-119">[Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or[Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)</span></span>
    
- <span data-ttu-id="95447-120">Informationen zu Tastenkombinationen, die möglicherweise für die Verfahren in diesem Thema gelten, finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](https://go.microsoft.com/fwlink/p/?LinkId=534017).</span><span class="sxs-lookup"><span data-stu-id="95447-120">For information about keyboard shortcuts that might apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center](https://go.microsoft.com/fwlink/p/?LinkId=534017).</span></span>
    
## 

> [!IMPORTANT]
> <span data-ttu-id="95447-p103">Dieses Verfahren ist nur fürPartner mit delegierten Zugriffsberechtigungen (Delegated Access Permission, DAP). Wenn Sie kein DAP-Partner sind, verwenden Sie dieses Verfahren nicht.</span><span class="sxs-lookup"><span data-stu-id="95447-p103">This procedure is only for Delegated Access Permission (DAP) partners. If you are not a DAP partner, do not use this procedure.</span></span> 
  
<span data-ttu-id="95447-p104">DAP-Partner sind Syndication- und Cloudlösungsanbieter-Partner (CSP-Partner). Häufig handelt es sich um Netzwerk- oder Telekom-Anbieter für andere Unternehmen. Sie bündeln Abonnements in ihren Serviceangeboten für ihre Kunden. Sie verfügen über einen Partnermandanten, dem automatisch die Berechtigung „Verwalten im Namen von" (Administer On Behalf Of, AOBO) für ihren Office 365-Kundenmandanten erteilt wird, damit sie alle ihre Kundenmandanten verwalten und Berichte dazu erstellen können.</span><span class="sxs-lookup"><span data-stu-id="95447-p104">DAP partners are Syndication and Cloud Solution Providers (CSP) partners. They are frequently network or telecom providers to other companies. They bundle subscriptions into their service offerings to their customers. They own a partner tenancy that is automatically granted Administer On Behalf Of (AOBO) permissions to their Office 365customer tenancies so they can administer and report on all of their customer tenancies.</span></span>
  
## <a name="connect-to-exchange-online"></a><span data-ttu-id="95447-127">Herstellen einer Verbindung mit Exchange Online</span><span class="sxs-lookup"><span data-stu-id="95447-127">Connect to Exchange Online</span></span>

1. <span data-ttu-id="95447-128">Öffnen Sie auf Ihrem lokalen Computer Windows PowerShell, und führen Sie dann den folgenden Befehl aus.</span><span class="sxs-lookup"><span data-stu-id="95447-128">On your local computer, open Windows PowerShell and run the following command.</span></span>
    
  ```
  $UserCredential = Get-Credential
  ```

    <span data-ttu-id="95447-129">Geben Sie im Dialogfeld **Bei Windows PowerShell anmelden** Ihren DAP-Administratorbenutzernamen und das Kennwort ein, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="95447-129">In the **Windows PowerShell Credential Request** dialog box, enter your DAP administrator user name and password, and then click **OK**.</span></span>
    
2. <span data-ttu-id="95447-130">Führen Sie den folgenden Befehl aus, wobei Sie _<customer tenant domain name>_ durch den Namen der Mandantendomäne ersetzen, mit der Sie eine Verbindung herstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="95447-130">Run the following command, replacing  _<customer tenant domain name>_ with the name of the tenant domain that you want to connect to.</span></span>
    
  ```
  $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid?DelegatedOrg=<customer tenant domain name>-Credential $UserCredential -Authentication Basic -AllowRedirection
  ```

    <span data-ttu-id="95447-p105">Der wichtigste Schritt für diesen Befehl ist anzugeben, auf welchen Kunden für die Berichtsinformationen zugegriffen werden soll. Sie geben dies durch den  _ConnectionURI_-Parameter an, für den Sie den vollqualifizierten Domänennamen (FQDN) des anfänglichen Domänennamens als Wert für den  _DelegatedOrg_-Parameter angeben. Hierdurch wird Remote-Windows PowerShell für Exchange Online PowerShell mitgeteilt, mit welchem Endpunkt Remote-Windows PowerShell eine Verbindung herstellen soll. Remote-Windows PowerShell muss mit der Office 365-Berichterstellung bei jeder Ausführung eines Berichts eine Verbindung im Kontext eines bestimmten Benutzers herstellen. Nachdem Sie diesen Kunden angegeben haben, werden alle der folgenden Befehle im Kontext dieses Kunden ausgeführt. Auf diese Weise kann der Partner auf alle verfügbaren Berichte für diesen Kunden zugreifen.</span><span class="sxs-lookup"><span data-stu-id="95447-p105">The key step in this command is specifying which customer to access for the reporting information. You do this in the  _ConnectionURI_ parameter, where you provide the FQDN of the initial domain name as the value to the _DelegatedOrg_ parameter. This tells remote Windows PowerShell for Exchange Online PowerShell remote Windows PowerShell the endpoint to connect to. remote Windows PowerShell must connect to Office 365 reporting in the context of a specific customer each time a report is run. After this customer is specified, all of the following commands are run in the context of that customer. This lets the partner to access all the available reports for this customer.</span></span>
    
3. <span data-ttu-id="95447-137">Führen Sie den folgenden Befehl aus.</span><span class="sxs-lookup"><span data-stu-id="95447-137">Run the following command.</span></span>
    
  ```
  Import-PSSession $Session
  ```

> [!NOTE]
> <span data-ttu-id="95447-p106">Es können höchstens drei Sitzungen gleichzeitig unter einem Konto ausgeführt werden. Stellen Sie sicher, dass die Remote-Windows PowerShell-Sitzung getrennt wird, wenn Sie alle Aufgaben ausgeführt haben. Wenn Sie das Windows PowerShell-Fenster schließen, ohne die Sitzung zu trennen, verbrauchen Sie möglicherweise alle Remote-Windows PowerShell-Sitzungen, die Ihnen zur Verfügung stehen, sodass Sie dann warten müssen, bis die Sitzungen abgelaufen sind. Führen Sie zum Trennen der Windows PowerShell-Remotesitzung den folgenden Befehl aus. >  `Remove-PSSession $Session`</span><span class="sxs-lookup"><span data-stu-id="95447-p106">There is a limit of three simultaneous sessions that can run under one account. Be sure to disconnect the remote Windows PowerShell session when you're finished. If you close the Windows PowerShell window without disconnecting the session, you can use up all the remote Windows PowerShell sessions available to you, and you'll need to wait for the sessions to expire. To disconnect the remote Windows PowerShell session, run the following command. >  `Remove-PSSession $Session`</span></span>
  
## <a name="how-do-you-know-this-worked"></a><span data-ttu-id="95447-142">Woher wissen Sie, dass dieses Verfahren erfolgreich war?</span><span class="sxs-lookup"><span data-stu-id="95447-142">How do you know this worked?</span></span>

<span data-ttu-id="95447-p107">Nach Schritt 3 werden die Exchange Online-Cmdlets in Ihre lokale Windows PowerShell-Sitzung importiert. Der Fortschritt des Importvorgangs wird in einer Statusanzeige dargestellt. Wenn Sie keine Fehlermeldungen erhalten, wurde die Verbindung erfolgreich hergestellt. Ein schneller Test ist die Ausführung eines Exchange Online-Cmdlets, z. B. von **Get-Mailbox**, und die Betrachtung der Ergebnisse.</span><span class="sxs-lookup"><span data-stu-id="95447-p107">After Step 3, the Exchange Online cmdlets are imported into your local Windows PowerShell session as tracked by a progress bar. If you don't receive any errors, you connected successfully. A quick test is to run an Exchange Online cmdlet—for example, **Get-Mailbox** —and see the results.</span></span>
  
<span data-ttu-id="95447-146">Wenn Sie Fehlermeldungen erhalten, überprüfen Sie die folgenden Anforderungen:</span><span class="sxs-lookup"><span data-stu-id="95447-146">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="95447-p108">Ein häufig auftretendes Problem ist ein falsches Kennwort. Führen Sie die drei Schritte erneut durch und achten Sie besonders auf die korrekte Eingabe des Benutzernamens und Kennworts in Schritt 1.</span><span class="sxs-lookup"><span data-stu-id="95447-p108">A common problem is an incorrect password. Run the three steps again and pay close attention to the user name and password you enter in Step 1.</span></span>
    
- <span data-ttu-id="95447-149">Um die Abwehr von DoS-Angriffen (Denial of Service) zu unterstützen, ist die Anzahl der offenen Windows PowerShell-Verbindungen zu Ihrer Exchange Online-Organisation auf drei beschränkt.</span><span class="sxs-lookup"><span data-stu-id="95447-149">To help prevent denial-of-service (DoS) attacks, you're limited to three open remote Windows PowerShell connections to your Exchange Online organization.</span></span>
    
- <span data-ttu-id="95447-p109">Windows PowerShell muss zum Ausführen von Skripts konfiguriert werden. Sie müssen diese Einstellung nur einmalig auf Ihrem Computer konfigurieren, und nicht bei jedem Verbindungsaufbau. Um Windows PowerShell für das Ausführen von signierten Skripts zu aktivieren, müssen Sie den folgenden Befehl in einem Windows PowerShell-Fenster mit erhöhten Rechten ausführen (ein Windows PowerShell-Fenster, das Sie durch Auswahl von **Als Administrator ausführen**) geöffnet haben.</span><span class="sxs-lookup"><span data-stu-id="95447-p109">Windows PowerShell needs to be configured to run scripts. You need to configure this setting only once on your computer, not every time you connect. To enable Windows PowerShell to run signed scripts, run the following command in an elevated Windows PowerShell window (a Windows PowerShell window you opened by selecting **Run as administrator**).</span></span>
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

- <span data-ttu-id="95447-p110">Das Benutzerkonto, mit dem Sie die Verbindung mit Exchange Online herstellen, muss für Remote-Windows PowerShell aktiviert sein. Weitere Informationen finden Sie unter [Verwalten des Remote-PowerShell-Zugriffs in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534018).</span><span class="sxs-lookup"><span data-stu-id="95447-p110">The account you use to connect to Exchange Online must be enabled for remote Windows PowerShell. For more information, see [Manage Remote PowerShell Access in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534018).</span></span>
    
- <span data-ttu-id="95447-p111">TCP-Port 80 muss zwischen dem lokalen Computer und dem Remoteserver geöffnet sein. Er ist wahrscheinlich offen, es kann jedoch vorkommen, dass Ihre Organisation eine eingeschränkte Internetzugriffsrichtlinie verfolgt.</span><span class="sxs-lookup"><span data-stu-id="95447-p111">TCP port 80 traffic needs to be open between your local computer and Exchange Online. It's probably open, but it's something to consider if your organization has a restrictive Internet access policy.</span></span>
    
## <a name="call-the-cmdlet-directly-with-invoke-command"></a><span data-ttu-id="95447-157">Direktes Aufrufen des Cmdlets mit Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="95447-157">Call the cmdlet directly with Invoke-Command</span></span>

<span data-ttu-id="95447-p112">Das Importieren einer Windows PowerShell-Remotesitzung kann ein langwieriger Vorgang sein, da alle Exchange Online-Cmdlets mit einbezogen werden. Dies kann bei der Stapelverarbeitung ein Problem sein, wenn Sie z. B. Berichte ausführen oder Massenänderungen für verschiedene Mandanten durchführen. Als Alternative zur Verwendung von **Import-PSSession** können Sie Cmdlets, die Sie verwenden möchten, direkt mit **Invoke-Command** aufrufen. Um zum Beispiel das **get-mailbox** -Cmdlet aufzurufen, ersetzen Sie `Import-PSSession $Session` mit der folgenden Syntax.</span><span class="sxs-lookup"><span data-stu-id="95447-p112">Importing a remote Windows PowerShell session can be a lengthy process because it brings in all Exchange Online cmdlets. This can be an issue in batch processing—for example, when you are running reports or making bulk changes for different tenants. As an alternative to using **Import-PSSession**, you can call cmdlets you want to use directly with **Invoke-Command**. For example, to call the **get-mailbox** cmdlet, substitute this syntax for `Import-PSSession $Session`.</span></span>
  
```
Invoke-Command -Session $Session -ScriptBlock {Get-Mailbox}
```

## <a name="more-reporting-cmdlets"></a><span data-ttu-id="95447-162">Weitere Berichterstellungs-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="95447-162">More reporting cmdlets</span></span>

<span data-ttu-id="95447-p113">Die Cmdlets, die Sie in diesem Thema verwenden, sind Windows PowerShell-Cmdlets. Weitere Informationen zu diesen Cmdlets finden Sie in den folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="95447-p113">The cmdlets that you used in this topic are Windows PowerShell cmdlets. For more information about these cmdlets, see the following topics:</span></span>
  
- [<span data-ttu-id="95447-165">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="95447-165">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
    
- [<span data-ttu-id="95447-166">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="95447-166">New-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389621)
    
- [<span data-ttu-id="95447-167">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="95447-167">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389619)
    
- [<span data-ttu-id="95447-168">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="95447-168">Remove-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389620)
    
- [<span data-ttu-id="95447-169">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="95447-169">Set-ExecutionPolicy</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389623)
    

