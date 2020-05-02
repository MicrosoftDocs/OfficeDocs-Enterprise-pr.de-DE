---
title: Abrufen von Kundenberichtsdaten über Windows PowerShell für Partner mit delegierten Zugriffsberechtigungen (Delegated Access Permission, DAP)
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 893e5275-30b3-433f-8ecd-644f78f513e2
description: 'Zusammenfassung: Verwenden Sie Windows PowerShell für Microsoft Exchange Online remote, um Berichte von einzelnen Kundenmandanten abzurufen.'
ms.openlocfilehash: e3e6b0ac86e2ee6479378d2eecc0c8b3cfbb6096
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004548"
---
# <a name="retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="17143-103">Abrufen von Kundenberichtsdaten über Windows PowerShell für Partner mit delegierten Zugriffsberechtigungen (Delegated Access Permission, DAP)</span><span class="sxs-lookup"><span data-stu-id="17143-103">Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

 <span data-ttu-id="17143-104">**Zusammenfassung:** Verwenden Sie Windows PowerShell für Microsoft Exchange Online remote, um Berichte von einzelnen Kundenmandanten abzurufen.</span><span class="sxs-lookup"><span data-stu-id="17143-104">**Summary:** Use remote Windows PowerShell for Microsoft Exchange Online to retrieve reports from individual customer tenants.</span></span>
  
<span data-ttu-id="17143-p101">Syndication-Partner und Cloudlösungsanbieter (Cloud Solution Providers, CSP) kann auf die Daten der Kundenmandantenberichte direkt über eine Windows PowerShell für Exchange Online PowerShell-Remotesitzung zugreifen. Auf diese Weise können Partner die Berichtsdaten sammeln und speichern und anschließend andere Vorgänge damit durchführen. Nachdem Sie eine Remoteverbindung hergestellt haben, entspricht das Abrufen von Berichtsdaten zu einem Kundenmandanten dem Ausführen eines Cmdlets für einen Kundenmandanten.</span><span class="sxs-lookup"><span data-stu-id="17143-p101">Syndication and Cloud Solution Provider (CSP) partners can access the data that makes up customer tenant reports directly via remoteWindows PowerShell for Exchange Online PowerShell. This lets partners collect and save the reporting data and then perform other operations on it. After you open a remote connection, retrieving reporting data about a customer tenancy is identical to running any cmdlet against a customer tenancy.</span></span>
  
<span data-ttu-id="17143-p102">In diesem Artikel verwenden Sie Windows PowerShell für Exchange Online remote zum Verbinden mit einem einzelnen Kundenmandanten und zum Abrufen eines Berichts. In der Standardeinstellung unterstützt Windows PowerShell das Aggregieren von Daten aus mehreren Kundenmandanten nicht. Die mit diesem Verfahren abgerufenen Berichte sind nur für die  _DelegatedOrg_ bestimmt, mit er Sie eine Verbindung herstellen.</span><span class="sxs-lookup"><span data-stu-id="17143-p102">In this article, you use remoteWindows PowerShell for Exchange Online to connect to a single customer tenancy and retrieve a report. By default, Windows PowerShell does not support aggregating reporting data from multiple customer tenancies. The reports you retrieve with this procedure are only for the  _DelegatedOrg_ that you connect to.</span></span>
  
 
## <a name="before-you-begin"></a><span data-ttu-id="17143-111">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="17143-111">Before you begin</span></span>

- <span data-ttu-id="17143-p103">Sie müssen eine Verbindung zu Ihrem Exchange Online-Mandanten mithilfe von Windows PowerShell remote erstellen. Anweisungen hierzu finden Sie unter [Verbinden mit Exchange Online-Mandanten über eine Remotesitzung von Windows PowerShell für Partner mit delegierten Zugriffsberechtigungen (Delegated Access Permissions, DAP)](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md).</span><span class="sxs-lookup"><span data-stu-id="17143-p103">You need to connect to your Exchange Online tenant by using remote Windows PowerShell. For instructions, see [Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)</span></span>
    
## <a name="run-the-get-stalemailboxreport-sample"></a><span data-ttu-id="17143-114">Ausführen des Get-StaleMailboxReport-Beispiels</span><span class="sxs-lookup"><span data-stu-id="17143-114">Run the Get-StaleMailboxReport sample</span></span>

<span data-ttu-id="17143-115">Führen Sie nach dem Öffnen einer Remotesitzung mit Exchange Online diesen Befehl zum Abrufen von **Get-StaleMailboxReport** für den Datumsbereich 25.03.2015 bis 31.03.2015 aus.</span><span class="sxs-lookup"><span data-stu-id="17143-115">After you have opened a remote session to Exchange Online, run this command to retrieve the **Get-StaleMailboxReport** for the date range 03/25/2015 through 03/31/2015.</span></span>
  
```
Get-StaleMailboxReport -StartDate 03/25/2015 -EndDate 03/31/2015
```

<span data-ttu-id="17143-p104">Es stehen zahlreiche andere Berichterstellungs-Cmdlets für Exchange Online, Lync Online und SharePoint Online sowie andere für die Verfolgung von Nachrichten zur Verfügung, die Sie verwenden können. Weitere Informationen zu den verfügbaren Berichterstellungs-Cmdlets und zum Office 365 Reporting-Webdienst finden Sie in den Themen des folgenden Abschnitts.</span><span class="sxs-lookup"><span data-stu-id="17143-p104">There are many other reporting cmdlets available for Exchange Online, Lync Online, and SharePoint Online as well as others for message tracing that you can use. To find out more about the available reporting cmdlets and the Office 365 Reporting web service, see the topics in the following section.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="17143-118">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="17143-118">See also</span></span>

#### 

[<span data-ttu-id="17143-119">Office 365-Berichterstattungswebdienst</span><span class="sxs-lookup"><span data-stu-id="17143-119">Office 365 Reporting web service</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[<span data-ttu-id="17143-120">Cmdlets für die Berichterstellung in Exchange Online</span><span class="sxs-lookup"><span data-stu-id="17143-120">Reporting cmdlets in Exchange Online</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=526430)
  
[<span data-ttu-id="17143-121">Hilfe für Partner</span><span class="sxs-lookup"><span data-stu-id="17143-121">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)

