---
title: Verwalten von Office 365-Mandanten mit Windows PowerShell für Partner mit delegierten Zugriffsberechtigungen (Delegated Access Permissions, DAP)
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
ms.custom: ''
ms.assetid: f92d5116-5b66-4150-ad20-1452fc3dd712
description: 'Zusammenfassung: Verwenden Sie Windows PowerShell für Office 365 zum Verwalten von Kundenmandanten.'
ms.openlocfilehash: b38c1862a0cf2db4a751d1690686baeead8ae9ea
ms.sourcegitcommit: 1c97471f47e1869f6db684f280f9085b7c2ff59f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/18/2019
ms.locfileid: "35781855"
---
# <a name="manage-office-365-tenants-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>Verwalten von Office 365-Mandanten mit Windows PowerShell für Partner mit delegierten Zugriffsberechtigungen (Delegated Access Permissions, DAP)

 **Zusammenfassung:** Verwenden Sie Windows PowerShell für Office 365 zum Verwalten von Kundenmandanten.
  
Windows PowerShell ermöglicht es den Anbietern von Syndication-und Cloud Solution Providern (CSP), Kundenmandanten Einstellungen, die im Microsoft 365 Admin Center nicht verfügbar sind, einfach zu verwalten und zu melden. Beachten Sie, dass für das Partneradministrator Konto die Berechtigung verwalten im Namen von (AOBO) erforderlich ist, um eine Verbindung mit dem Mandanten des Kunden herzustellen.
  
DAP-Partner (Delegated Access Permission, delegierte Zugriffsberechtigung) sind Syndication-Partner und Cloudlösungsanbieter (Cloud Solution Providers, CSP). Häufig handelt es sich um Netzwerk- oder Telekom-Anbieter für andere Unternehmen. Sie bündeln Office 365-Abonnements in Serviceangeboten für ihre Kunden. Wenn sie ein Office 365-Abonnement verkaufen, erhalten sie automatisch AOBO-Berechtigungen (Administer On Behalf Of, Verwalten im Namen von) für die Kundenmandanten, damit sie diese verwalten und Berichte darüber erstellen können.
## <a name="what-do-you-need-to-know-before-you-begin"></a>Was sollten Sie wissen, bevor Sie beginnen?

Für die Verfahren in diesem Thema müssen Sie eine Verbindung mit Windows PowerShell für Office 365 herstellen. Weitere Anweisungen finden Sie unter [Verbinden mit Office 365 PowerShell](connect-to-office-365-powershell.md).
  
Sie benötigen auch die Administratoranmeldeinformationen Ihres Partnermandanten.
  
## <a name="what-do-you-want-to-do"></a>Was möchten Sie machen?

### <a name="list-all-tenant-ids"></a>Auflisten aller Mandanten-IDs

> [!NOTE]
> Wenn Sie über mehr als 500 Mandanten verfügen, fügen Sie in die Cmdlet-Syntax entweder  _-All_ oder _-MaxResultsParameter_ ein. Dies gilt für andere Cmdlets mit einer umfangreichen Ausgabe, wie z. B. **Get-MsolUser**.
  
Führen Sie den folgenden Befehl aus, um alle Kundenmandanten-IDs aufzulisten, auf die Sie Zugriff haben.
  
```
Get-MsolPartnerContract -All | Select-Object TenantId
```

Dies zeigt eine Liste aller Kundenmandanten nach **TenantId** geordnet an.
  
### <a name="get-a-tenant-id-by-using-the-domain-name"></a>Abrufen einer Mandanten-ID mithilfe des Domänennamens

Zum Abrufen der **TenantId** eines bestimmten Kundenmandanten nach Domänenname führen Sie den folgenden Befehl aus. Ersetzen Sie _<domänenname.onmicrosoft.com>_ durch den eigentlichen Domänennamen des gewünschten Kundenmandanten.
  
```
Get-MsolPartnerContract -DomainName <domainname.onmicrosoft.com> | Select-Object TenantId
```

### <a name="list-all-domains-for-a-tenant"></a>Auflisten aller Domänen für einen Mandanten

Um alle Domänen für einen einzigen Kundenmandanten aufzurufen, führen Sie den folgenden Befehl aus. Ersetzen Sie  _<customer TenantId value>_ durch den eigentlichen Wert.
  
```
Get-MsolDomain -TenantId <customer TenantId value>
```

Wenn Sie zusätzliche Domänen registriert haben, werden alle Domänen zurückgegeben, die mit der **TenantId** des Kunden verknüpft sind.
  
### <a name="get-a-mapping-of-all-tenants-and-registered-domains"></a>Abrufen einer Zuordnung aller Mandanten und registrierten Domänen

Die vorherigen Befehle von Windows PowerShell für Office 365 haben Ihnen gezeigt, wie Sie entweder die Mandanten-IDs oder die Domänen, jedoch nicht beides gleichzeitg abrufen können. Außerdem geben sie die Zuordnung von Mandanten-ID und Domäne nicht an. Dieser Befehl generiert eine Liste aller Kundenmandanten-IDs und ihrer Domänen.
  
```
$Tenants = Get-MsolPartnerContract -All; $Tenants | foreach {$Domains = $_.TenantId; Get-MsolDomain -TenantId $Domains | fl @{Label="TenantId";Expression={$Domains}},name}
```

### <a name="get-all-users-for-a-tenant"></a>Abrufen aller Benutzer für einen Mandanten

Hierdurch werden der **UserPrincipalName**, der **DisplayName** und der Status **isLicensed** für alle Benutzer eines bestimmten Mandanten angezeigt. Ersetzen Sie _<customer TenantId value>_ durch den eigentlichen Wert.
  
```
Get-MsolUser -TenantID <customer TenantId value>
```

### <a name="get-all-details-about-a-user"></a>Abrufen aller Details eines Benutzers

Wenn Sie alle Eigenschaften eines bestimmten Benutzers anzeigen möchten, führen Sie den folgenden Befehl aus:  Ersetzen Sie _<customer TenantId value>_ und _<user principal name value>_ durch die eigentlichen Werte.
  
```
Get-MsolUser -TenantId <customer TenantId value> -UserPrincipalName <user principal name value>
```

### <a name="add-users-set-options-and-assign-licenses"></a>Hinzufügen von Benutzern, Festlegen von Optionen und Zuweisen von Lizenzen

Die Massenerstellung, -konfiguration und -lizenzierung von Office 365-Benutzern kann mit Windows PowerShell für Office 365 besonders effizient durchgeführt werden. Bei diesem Verfahren, das nur zwei Schritte umfasst, erstellen Sie zuerst Einträge für alle hinzuzufügenden Benutzer in einer CSV-Datei und importieren diese Datei dann mithilfe von Windows PowerShell für Office 365. 
  
#### <a name="create-a-csv-file"></a>Erstellen einer CSV-Datei

Erstellen Sie eine CSV-Datei anhand dieses Formats:
  
-  `UserPrincipalName,FirstName,LastName,DisplayName,Password,TenantId,UsageLocation,LicenseAssignment`
    
Dabei gilt:
  
- **UsageLocation**: Der Wert hierfür ist der zweistellige ISO-Länder-/Regionscode des Benutzers. Die Länder-/Regioinscodes finden Sie auf der[ISO-Online-Browserplattform](https://go.microsoft.com/fwlink/p/?LinkId=532703). Der Code für die Vereinigten Staaten lautet z. B. „US", der Code für Brasilien „BR". 
    
- **LicenseAssignment**: Der Wert hierfür verwendet das folgende Format: `syndication-account:<PROVISIONING_ID>`. Wenn Sie Kundenmandantenbenutzern zum Beispiel O365_Business_Premium-Lizenzen zuweisen, sieht der Wert **LicenseAssignment** wie folgt aus: **syndication-account:O365_Business_Premium**. Sie finden die PROVISIONING_IDs im Syndication-Partnerportal, auf das Sie als Syndication- oder CSP-Partner Zugriff haben.
    
#### <a name="import-the-csv-file-and-create-the-users"></a>Importieren der CSV-Datei und Erstellen der Benutzer

Nachdem Sie die CSV-Datei erstellt haben, führen Sie den folgenden Befehl zum Erstellen von Benutzerkonten mit nicht ablaufenden Kennwörtern aus. Der Benutzer muss das Kennwort beim ersten Anmelden ändern, und es weist ihm die ausgewählte Lizenz zu. Achten Sie darauf, dass Sie den richtigen Namen der CSV-Datei angeben.
  
```
Import-Csv .\FILENAME.CSV | foreach {New-MsolUser -UserPrincipalName $_.UserPrincipalName -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -Password $_.Password -UsageLocation $_.UsageLocation -LicenseAssignment $_.LicenseAssignment -ForceChangePassword:$true -PasswordNeverExpires:$true -TenantId $_.TenantId}
```

## <a name="see-also"></a>Siehe auch

#### 

[Hilfe für Partner](https://go.microsoft.com/fwlink/p/?LinkId=533477)

