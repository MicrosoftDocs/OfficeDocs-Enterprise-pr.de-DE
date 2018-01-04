---
title: "Hinzufügen einer Domäne zu einem Kundenmandanten mit Windows PowerShell für Partner mit delegierten Zugriffsberechtigungen (Delegated Access Permission, DAP)"
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
ms.assetid: f49b4d24-9aa0-48a6-95dd-6bae9cf53d2c
description: "Zusammenfassung: Verwenden Sie Windows PowerShell für Office 365 zum Hinzufügen eines alternativen Domänennamens zu einem vorhandenen Kundenmandanten."
ms.openlocfilehash: 182750a5706dbb23c6207c6bd63334cbf2a2a795
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2017
---
# <a name="add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-permission-dap-partners"></a>Hinzufügen einer Domäne zu einem Kundenmandanten mit Windows PowerShell für Partner mit delegierten Zugriffsberechtigungen (Delegated Access Permission, DAP)

 **Zusammenfassung:** Verwenden Sie Windows PowerShell für Office 365 zum Hinzufügen eines alternativen Domänennamens zu einem vorhandenen Kundenmandanten.
  
Mit Windows PowerShell für Office 365 können Sie schneller als mit der Office 365 Admin Center neue Domänen erstellen und sie einem Kundenmandanten zuweisen.
  
DAP-Partner (Delegated Access Permission, delegierte Zugriffsberechtigung) sind Syndication-Partner und Cloudlösungsanbieter (Cloud Solution Providers, CSP). Häufig handelt es sich um Netzwerk- oder Telekom-Anbieter für andere Unternehmen. Sie bündeln Office 365-Abonnements in Serviceangeboten für ihre Kunden. Wenn sie ein Office 365-Abonnement verkaufen, erhalten sie automatisch AOBO-Berechtigungen (Administer On Behalf Of, Verwalten im Namen von) für dieKundenmandanten, damit sie diese verwalten und Berichte darüber erstellen können.
## <a name="what-do-you-need-to-know-before-you-begin"></a>Was sollten Sie wissen, bevor Sie beginnen?

UNRESOLVED_TOKEN_VAL(GENL_O365_PowerShell_BeforeYouBegin)
  
Sie benötigen außerdem die folgenden Informationen:
  
- Sie benötigen den vollqualifizierten Domänennamen (FQDN), den der Kunde verwenden möchte.
    
- Sie benötigen die **TenantId** des Kunden.
    
- Der FQDN muss bei einer Registrierungsstelle für Internetdomänennamen, wie z. B. GoDaddy, registriert sein. Weitere Informationen für die öffentliche Registrierung eines Domänennamens finden Sie unter [Erwerben eines Domänennamens](https://go.microsoft.com/fwlink/p/?LinkId=532541).
    
- Sie müssen wissen, wie Sie einen TXT-Eintrag zur registrierten DNS-Zone für die DNS-Registrierungsstelle hinzufügen. Weitere Informationen zum Hinzufügen eines TXT-Eintrags finden Sie unter [Hinzufügen eines TXT-Eintrags zur Überprüfung](https://go.microsoft.com/fwlink/p/?LinkId=532542). Wenn Sie diese Verfahren nicht durchführen können, müssen Sie die für die DNS-Registrierungsstelle anwendbaren Verfahren ermitteln.
    
## <a name="create-domains"></a>Erstellen von Domänen

 Ihre Kunden werden Sie wahrscheinlich bitten, weitere Domänen für ihren Mandanten zu erstellen, da sie die Standarddomäne<Domäne>.onmicrosoft.comwahrscheinlich nicht als primären Domäne verwenden möchten, um ihr Unternehmen im Internet weltweit zu repräsentieren. Dieses Verfahren leitet Sie durch die Schritte zum Erstellen einer neuen Domäne, die Sie mit dem Kundenmandanten verknüpfen können.
  
> [!NOTE]
> Um einige dieser Verfahren ausführen zu können, muss in dem Partneradministratorkonto, mit dem Sie sich anmelden, die Einstellung **Administratorzugriff auf von Ihnen unterstützte Unternehmen zuweisen** auf **Vollständige Verwaltung** festgelegt sein. Diese Einstellung finden Sie in den Details des Administratorkontos in der Office 365 Admin Center. Weitere Informationen zum Verwalten von Partneradministratorrollen finden Sie unter[Partner: Anbieten von delegierter Administration](https://go.microsoft.com/fwlink/p/?LinkId=532435). 
  
### <a name="create-the-domain-in-azure-active-directory"></a>Erstellen Sie die Domäne in Azure Active Directory

Dieser Befehl erstellt die Domäne in Azure Active Directory, ordnet sie jedoch nicht der öffentlich registrierten Domäne zu. Dies erfolgt, sobald Sie in Microsoft Office 365 für Unternehmen nachgewiesen haben, dass Sie Besitzer der öffentlich registrierten Domäne sind.
  
```
New-MsolDomain -TenantId <customer TenantId> -Name <FQDN of new domain>
```

### <a name="get-the-data-for-the-dns-txt-verification-record"></a>Abrufen der Daten für den DNS-TXT-Überprüfungseintrag

 Office 365 generiert die spezifischen Daten, die Sie in den DNS-TXT-Überprüfungseintrag einfügen müssen. Führen Sie diesen Befehl aus, um die Daten abzurufen.
  
```
Get-MsolDomainVerificationDNS -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

Dadurch erhalten Sie die folgende Ausgabe:
  
 `Label: domainname.com`
  
 `Text: MS=ms########`
  
 `Ttl: 3600`
  
> [!NOTE]
> Sie benötigen diesen Text, um den TXT-Eintrag in der öffentlich registrierten DNS-Zone zu erstellen. Stellen Sie sicher, dass Sie ihn kopieren und speichern. 
  
### <a name="add-a-txt-record-to-the-publically-registered-dns-zone"></a>Hinzufügen eines TXT-Eintrags zur öffentlich registrierten DNS-Zone

Bevor Office 365 Datenverkehr verarbeitet, der an den öffentlich registrierten Domänennamen gerichtet ist, müssen Sie nachweisen, dass Sie die Domäne besitzen und über Administratorberechtigungen hierfür verfügen. Sie weisen nach, dass Sie die Domäne besitzen, indem Sie einen TXT-Eintrag in der Domäne erstellen. Ein TXT-Eintrag hat keine Auswirkungen auf die Domäne, und er kann gelöscht werden, nachdem die Besitzrechte an der Domäne nachgewiesen wurden. Um die TXT-Einträge zu erstellen, gehen Sie wie unter [Hinzufügen eines TXT-Eintrags zur Überprüfung](https://go.microsoft.com/fwlink/p/?LinkId=532542) beschrieben vor. Wenn Sie diese Verfahren nicht durchführen können, müssen Sie die für die DNS-Registrierungsstelle anwendbaren Verfahren ermitteln.
  
Bestätigen Sie die erfolgreiche Erstellung des TXT-Eintrags über Nslookup. Verwenden Sie die folgende Syntax.
  
```
nslookup -type=TXT <FQDN of registered domain>
```

Dadurch erhalten Sie die folgende Ausgabe:
  
 `Non-authoritative answer:`
  
 `FQDN of the registered domain`
  
 `text=MS=ms########`
  
### <a name="validate-domain-ownership-in-office-365"></a>Überprüfen des Domänenbesitzes in Office 365

In diesem letzten Schritt führen Sie in Office 365 die Überprüfung durch, dass Sie Besitzer der öffentlich registrierten Domäne sind. Nach diesem Schritt verarbeitet Office 365 den an die neue Domäne gerichteten Datenverkehr. Um das Erstellen und Registrieren der neuen Domäne abzuschließen, führen Sie den folgenden Befehl aus. 
  
```
Confirm-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

Dieser Befehl gibt keine Ausgabe zurück. Um sicherzustellen, dass dies funktioniert hat, führen Sie den folgenden Befehl aus.
  
```
Get-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

Dadurch wird in etwa Folgendes zurückgegeben
  
||||
|:-----|:-----|:-----|
| `Name` <br/> | `Status` <br/> | `Authentication` <br/> |
| `FQDN of new domain` <br/> | `Verified` <br/> | `Managed` <br/> |
   
## <a name="see-also"></a>Siehe auch

#### 

[Hilfe für Partner](https://go.microsoft.com/fwlink/p/?LinkID=533477)

