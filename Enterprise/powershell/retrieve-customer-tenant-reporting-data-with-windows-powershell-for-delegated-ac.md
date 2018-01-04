---
title: "Abrufen von Kundenberichtsdaten über Windows PowerShell für Partner mit delegierten Zugriffsberechtigungen (Delegated Access Permission, DAP)"
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: DecEntMigration
ms.assetid: 893e5275-30b3-433f-8ecd-644f78f513e2
description: "Zusammenfassung: Verwenden Sie Windows PowerShell für Microsoft Exchange Online remote, um Berichte von einzelnen Kundenmandanten abzurufen."
ms.openlocfilehash: 40c1dedd8fb223ea6fa478b3a5c3e716fe07dd93
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2017
---
# <a name="retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>Abrufen von Kundenberichtsdaten über Windows PowerShell für Partner mit delegierten Zugriffsberechtigungen (Delegated Access Permission, DAP)

 **Zusammenfassung:** Verwenden Sie Windows PowerShell für Microsoft Exchange Online remote, um Berichte von einzelnen Kundenmandanten abzurufen.
  
Syndication-Partner und Cloudlösungsanbieter (Cloud Solution Providers, CSP) kann auf die Daten der Kundenmandantenberichte direkt über eine Windows PowerShell für Exchange Online PowerShell-Remotesitzung zugreifen. Auf diese Weise können Partner die Berichtsdaten sammeln und speichern und anschließend andere Vorgänge damit durchführen. Nachdem Sie eine Remoteverbindung hergestellt haben, entspricht das Abrufen von Berichtsdaten zu einem Kundenmandanten dem Ausführen eines Cmdlets für einen Kundenmandanten.
  
In diesem Artikel verwenden Sie Windows PowerShell für Exchange Online remote zum Verbinden mit einem einzelnen Kundenmandanten und zum Abrufen eines Berichts. In der Standardeinstellung unterstützt Windows PowerShell das Aggregieren von Daten aus mehreren Kundenmandanten nicht. Die mit diesem Verfahren abgerufenen Berichte sind nur für die  _DelegatedOrg_ bestimmt, mit er Sie eine Verbindung herstellen.
  
Wenn Sie für alle Kundenmandanten einzelne Berichte abrufen möchten, finden Sie ein Beispielskript hierzu unter [Aggregieren von Kundenberichtsdaten über Windows PowerShell für Partner mit delegierten Zugriffsberechtigungen (Delegated Access Permission, DAP)](aggregate-customer-reporting-data-via-windows-powershell-for-delegated-access-pe.md).
  
## <a name="before-you-begin"></a>Bevor Sie beginnen:

- Sie müssen eine Verbindung zu Ihrem Exchange Online-Mandanten mithilfe von Windows PowerShell remote erstellen. Anweisungen hierzu finden Sie unter [Verbinden mit Exchange Online-Mandanten über eine Remotesitzung von Windows PowerShell für Partner mit delegierten Zugriffsberechtigungen (Delegated Access Permissions, DAP)](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md).
    
## <a name="run-the-get-stalemailboxreport-sample"></a>Ausführen des Get-StaleMailboxReport-Beispiels

Führen Sie nach dem Öffnen einer Remotesitzung mit Exchange Online diesen Befehl zum Abrufen von **Get-StaleMailboxReport** für den Datumsbereich 25.03.2015 bis 31.03.2015 aus.
  
```
Get-StaleMailboxReport -StartDate 03/25/2015 -EndDate 03/31/2015
```

Es stehen zahlreiche andere Berichterstellungs-Cmdlets für Exchange Online, Lync Online und SharePoint Online sowie andere für die Verfolgung von Nachrichten zur Verfügung, die Sie verwenden können. Weitere Informationen zu den verfügbaren Berichterstellungs-Cmdlets und zum Office 365 Reporting-Webdienst finden Sie in den Themen des folgenden Abschnitts.
  
## <a name="see-also"></a>Siehe auch

#### 

[Office 365-Berichterstattungswebdienst](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[Cmdlets für die Berichterstellung in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=526430)
  
[Hilfe für Partner](https://go.microsoft.com/fwlink/p/?LinkID=533477)

