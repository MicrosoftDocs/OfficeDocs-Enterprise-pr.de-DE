---
title: Hinzufügen einer Domäne zu einem Kundenmandanten mit Windows PowerShell für Partner mit delegierten Zugriffsberechtigungen (Delegated Access Permission, DAP)
ms.author: chrfox
author: chrfox
manager: laurawi
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
ms.custom: ''
ms.assetid: f49b4d24-9aa0-48a6-95dd-6bae9cf53d2c
description: 'Zusammenfassung: Verwenden Sie Windows PowerShell für Office 365 zum Hinzufügen eines alternativen Domänennamens zu einem vorhandenen Kundenmandanten.'
ms.openlocfilehash: 85cddd28b72a3b03e9157a28c3fd1dc101a167e0
ms.sourcegitcommit: 29f937b7430c708c9dbec23bdc4089e86c37c225
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2019
ms.locfileid: "31001778"
---
# <a name="add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-permission-dap-partners"></a><span data-ttu-id="8296c-103">Hinzufügen einer Domäne zu einem Kundenmandanten mit Windows PowerShell für Partner mit delegierten Zugriffsberechtigungen (Delegated Access Permission, DAP)</span><span class="sxs-lookup"><span data-stu-id="8296c-103">Add a domain to a client tenancy with Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>

 <span data-ttu-id="8296c-104">**Zusammenfassung:** Verwenden Sie Windows PowerShell für Office 365 zum Hinzufügen eines alternativen Domänennamens zu einem vorhandenen Kundenmandanten.</span><span class="sxs-lookup"><span data-stu-id="8296c-104">**Summary:** Use Windows PowerShell for Office 365 to add an alternate domain name to an existing customer tenant.</span></span>
  
<span data-ttu-id="8296c-105">Mit Windows PowerShell für Office 365 können Sie schneller als mit dem Microsoft 365 Admin Center neue Domänen erstellen und sie einem Kundenmandanten zuweisen.</span><span class="sxs-lookup"><span data-stu-id="8296c-105">You can create and associate new domains with your customer's tenancy with Windows PowerShell for Office 365 faster than using the Office 365 admin center.</span></span>
  
<span data-ttu-id="8296c-106">DAP-Partner (Delegated Access Permission, delegierte Zugriffsberechtigung) sind Syndication-Partner und Cloudlösungsanbieter (Cloud Solution Providers, CSP).</span><span class="sxs-lookup"><span data-stu-id="8296c-106">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="8296c-107">Häufig handelt es sich um Netzwerk- oder Telekom-Anbieter für andere Unternehmen.</span><span class="sxs-lookup"><span data-stu-id="8296c-107">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="8296c-108">Sie bündeln Office 365-Abonnements in Serviceangeboten für ihre Kunden.</span><span class="sxs-lookup"><span data-stu-id="8296c-108">They bundle Office 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="8296c-109">Wenn sie ein Office 365-Abonnement verkaufen, erhalten sie automatisch AOBO-Berechtigungen (Administer On Behalf Of, Verwalten im Namen von) für die Kundenmandanten, damit sie diese verwalten und Berichte darüber erstellen können.</span><span class="sxs-lookup"><span data-stu-id="8296c-109">When they sell an O365_W14_2nd subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="8296c-110">Was sollten Sie wissen, bevor Sie beginnen?</span><span class="sxs-lookup"><span data-stu-id="8296c-110">What do you need to know before you begin?</span></span>

<span data-ttu-id="8296c-111">UNRESOLVED_TOKEN_VAL(GENL_O365_PowerShell_BeforeYouBegin)</span><span class="sxs-lookup"><span data-stu-id="8296c-111">UNRESOLVED_TOKEN_VAL(GENL_O365_PowerShell_BeforeYouBegin)</span></span>
  
<span data-ttu-id="8296c-112">Sie benötigen außerdem die folgenden Informationen:</span><span class="sxs-lookup"><span data-stu-id="8296c-112">You also need the following information:</span></span>
  
- <span data-ttu-id="8296c-113">Sie benötigen den vollqualifizierten Domänennamen (FQDN), den der Kunde verwenden möchte.</span><span class="sxs-lookup"><span data-stu-id="8296c-113">You need the fully qualified domain name (FQDN) that your customer wants.</span></span>
    
- <span data-ttu-id="8296c-114">Sie benötigen die **TenantId** des Kunden.</span><span class="sxs-lookup"><span data-stu-id="8296c-114">You need the customer's **TenantId**.</span></span>
    
- <span data-ttu-id="8296c-p102">Der FQDN muss bei einer Registrierungsstelle für Internetdomänennamen, wie z. B. GoDaddy, registriert sein. Weitere Informationen für die öffentliche Registrierung eines Domänennamens finden Sie unter [Erwerben eines Domänennamens](https://go.microsoft.com/fwlink/p/?LinkId=532541).</span><span class="sxs-lookup"><span data-stu-id="8296c-p102">The FQDN must be registered with an Internet domain name service (DNS) registrar, such as GoDaddy. For more information on how to publically register a domain name, see [How to buy a domain name](https://go.microsoft.com/fwlink/p/?LinkId=532541).</span></span>
    
- <span data-ttu-id="8296c-p103">Sie müssen wissen, wie Sie einen TXT-Eintrag zur registrierten DNS-Zone für die DNS-Registrierungsstelle hinzufügen. Weitere Informationen zum Hinzufügen eines TXT-Eintrags finden Sie unter [Hinzufügen eines TXT-Eintrags zur Überprüfung](https://go.microsoft.com/fwlink/p/?LinkId=532542). Wenn Sie diese Verfahren nicht durchführen können, müssen Sie die für die DNS-Registrierungsstelle anwendbaren Verfahren ermitteln.</span><span class="sxs-lookup"><span data-stu-id="8296c-p103">You need to know how to add a TXT record to the registered DNS zone for your DNS registrar. For more information on how to add a TXT record, see [Create DNS records at any DNS hosting provider for Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542). If those procedures don't work for you, you will need to find the procedures for your DNS registrar.</span></span>
    
## <a name="create-domains"></a><span data-ttu-id="8296c-120">Erstellen von Domänen</span><span class="sxs-lookup"><span data-stu-id="8296c-120">Create domains</span></span>

 <span data-ttu-id="8296c-p104">Ihre Kunden werden Sie wahrscheinlich bitten, weitere Domänen für ihren Mandanten zu erstellen, da sie die Standarddomäne<Domäne>.onmicrosoft.comwahrscheinlich nicht als primären Domäne verwenden möchten, um ihr Unternehmen im Internet weltweit zu repräsentieren. Dieses Verfahren leitet Sie durch die Schritte zum Erstellen einer neuen Domäne, die Sie mit dem Kundenmandanten verknüpfen können.</span><span class="sxs-lookup"><span data-stu-id="8296c-p104">Your customers will likely ask you to create additional domains to associate with their tenancy because they don't want the default <domain>.onmicrosoft.com domain to be the primary one that represents their corporate identities to the world. This procedure walks you through creating a new domain associated with your customer's tenancy.</span></span>
  
> [!NOTE]
> <span data-ttu-id="8296c-p105">Um einige dieser Verfahren ausführen zu können, muss in dem Partneradministratorkonto, mit dem Sie sich anmelden, die Einstellung **Administratorzugriff auf von Ihnen unterstützte Unternehmen zuweisen** auf **Vollständige Verwaltung** festgelegt sein. Diese Einstellung finden Sie in den Details des Administratorkontos in der Office 365 Admin Center. Weitere Informationen zum Verwalten von Partneradministratorrollen finden Sie unter[Partner: Anbieten von delegierter Administration](https://go.microsoft.com/fwlink/p/?LinkId=532435).</span><span class="sxs-lookup"><span data-stu-id="8296c-p105">To perform some of these operations, the partner administrator account you sign in with must be set to **Full administration** for the **Assign administrative access to companies you support** setting found in the details of the admin account in the Office 365 admin center. For more information on managing partner administrator roles, see[Partners: Offer delegated administration](https://go.microsoft.com/fwlink/p/?LinkId=532435).</span></span> 
  
### <a name="create-the-domain-in-azure-active-directory"></a><span data-ttu-id="8296c-125">Erstellen Sie die Domäne in Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="8296c-125">Create the domain in Azure Active Directory</span></span>

<span data-ttu-id="8296c-126">Dieser Befehl erstellt die Domäne in Azure Active Directory, ordnet sie jedoch nicht der öffentlich registrierten Domäne zu.</span><span class="sxs-lookup"><span data-stu-id="8296c-126">This command creates the domain in Azure Active Directory but does not associate it with the publically registered domain.</span></span> <span data-ttu-id="8296c-127">Dies erfolgt, sobald Sie in Microsoft Office 365 für Unternehmen nachgewiesen haben, dass Sie Besitzer der öffentlich registrierten Domäne sind.</span><span class="sxs-lookup"><span data-stu-id="8296c-127">That comes when you prove that you own the publically registered domain to Microsoft Office 365 for enterprises.</span></span>
  
```
New-MsolDomain -TenantId <customer TenantId> -Name <FQDN of new domain>
```

### <a name="get-the-data-for-the-dns-txt-verification-record"></a><span data-ttu-id="8296c-128">Abrufen der Daten für den DNS-TXT-Überprüfungseintrag</span><span class="sxs-lookup"><span data-stu-id="8296c-128">Get the data for the DNS TXT verification record</span></span>

 <span data-ttu-id="8296c-p107">Office 365 generiert die spezifischen Daten, die Sie in den DNS-TXT-Überprüfungseintrag einfügen müssen. Führen Sie diesen Befehl aus, um die Daten abzurufen.</span><span class="sxs-lookup"><span data-stu-id="8296c-p107">Office 365 will generate the specific data that you need to place into the DNS TXT verification record. To get the data, run this command.</span></span>
  
```
Get-MsolDomainVerificationDNS -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

<span data-ttu-id="8296c-131">Dadurch erhalten Sie die folgende Ausgabe:</span><span class="sxs-lookup"><span data-stu-id="8296c-131">This will give you output like:</span></span>
  
 `Label: domainname.com`
  
 `Text: MS=ms########`
  
 `Ttl: 3600`
  
> [!NOTE]
> <span data-ttu-id="8296c-132">Sie benötigen diesen Text, um den TXT-Eintrag in der öffentlich registrierten DNS-Zone zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="8296c-132">You will need this text to create the TXT record in the publically registered DNS zone.</span></span> <span data-ttu-id="8296c-133">Stellen Sie sicher, dass Sie ihn kopieren und speichern.</span><span class="sxs-lookup"><span data-stu-id="8296c-133">Be sure to copy and save it.</span></span> 
  
### <a name="add-a-txt-record-to-the-publically-registered-dns-zone"></a><span data-ttu-id="8296c-134">Hinzufügen eines TXT-Eintrags zur öffentlich registrierten DNS-Zone</span><span class="sxs-lookup"><span data-stu-id="8296c-134">Add a TXT record to the publically registered DNS zone</span></span>

<span data-ttu-id="8296c-135">Bevor Office 365 Datenverkehr verarbeitet, der an den öffentlich registrierten Domänennamen gerichtet ist, müssen Sie nachweisen, dass Sie die Domäne besitzen und über Administratorberechtigungen hierfür verfügen.</span><span class="sxs-lookup"><span data-stu-id="8296c-135">Before Office 365 will start accepting traffic that is directed to the publically registered domain name, you must prove that you own and have administrator permissions to the domain.</span></span> <span data-ttu-id="8296c-136">Sie weisen nach, dass Sie die Domäne besitzen, indem Sie einen TXT-Eintrag in der Domäne erstellen.</span><span class="sxs-lookup"><span data-stu-id="8296c-136">You prove you own the domain by creating a TXT record in the domain.</span></span> <span data-ttu-id="8296c-137">Ein TXT-Eintrag hat keine Auswirkungen auf die Domäne, und er kann gelöscht werden, nachdem die Besitzrechte an der Domäne nachgewiesen wurden.</span><span class="sxs-lookup"><span data-stu-id="8296c-137">A TXT record doesn't do anything in your domain, and it can be deleted after your ownership of the domain is established.</span></span> <span data-ttu-id="8296c-138">Um die TXT-Einträge zu erstellen, gehen Sie wie unter [Hinzufügen eines TXT-Eintrags zur Überprüfung](https://go.microsoft.com/fwlink/p/?LinkId=532542) beschrieben vor.</span><span class="sxs-lookup"><span data-stu-id="8296c-138">To create the TXT records, follow the procedures at [Create DNS records at any DNS hosting provider for Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542).</span></span> <span data-ttu-id="8296c-139">Wenn Sie diese Verfahren nicht durchführen können, müssen Sie die für die DNS-Registrierungsstelle anwendbaren Verfahren ermitteln.</span><span class="sxs-lookup"><span data-stu-id="8296c-139">If those procedures don't work for you , you need to find the procedures for your DNS registrar.</span></span>
  
<span data-ttu-id="8296c-p110">Bestätigen Sie die erfolgreiche Erstellung des TXT-Eintrags über Nslookup. Verwenden Sie die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="8296c-p110">Confirm the successful creation of the TXT record via nslookup. Follow this syntax.</span></span>
  
```
nslookup -type=TXT <FQDN of registered domain>
```

<span data-ttu-id="8296c-142">Dadurch erhalten Sie die folgende Ausgabe:</span><span class="sxs-lookup"><span data-stu-id="8296c-142">This will give you output like:</span></span>
  
 `Non-authoritative answer:`
  
 `FQDN of the registered domain`
  
 `text=MS=ms########`
  
### <a name="validate-domain-ownership-in-office-365"></a><span data-ttu-id="8296c-143">Überprüfen des Domänenbesitzes in Office 365</span><span class="sxs-lookup"><span data-stu-id="8296c-143">Validate domain ownership in Office 365</span></span>

<span data-ttu-id="8296c-p111">In diesem letzten Schritt führen Sie in Office 365 die Überprüfung durch, dass Sie Besitzer der öffentlich registrierten Domäne sind. Nach diesem Schritt verarbeitet Office 365 den an die neue Domäne gerichteten Datenverkehr. Um das Erstellen und Registrieren der neuen Domäne abzuschließen, führen Sie den folgenden Befehl aus.</span><span class="sxs-lookup"><span data-stu-id="8296c-p111">In this last step, you validate to Office 365 that you own the publically registered domain. After this step, Office 365 will begin accepting traffic routed to the new domain name. To complete the domain creation and registration process, run this command.</span></span> 
  
```
Confirm-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

<span data-ttu-id="8296c-147">Dieser Befehl gibt keine Ausgabe zurück. Um sicherzustellen, dass dies funktioniert hat, führen Sie den folgenden Befehl aus.</span><span class="sxs-lookup"><span data-stu-id="8296c-147">This command won't return any output, so to confirm that this worked, run this command.</span></span>
  
```
Get-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

<span data-ttu-id="8296c-148">Dadurch wird in etwa Folgendes zurückgegeben</span><span class="sxs-lookup"><span data-stu-id="8296c-148">This will return something like this</span></span>
  
||||
|:-----|:-----|:-----|
| `Name` <br/> | `Status` <br/> | `Authentication` <br/> |
| `FQDN of new domain` <br/> | `Verified` <br/> | `Managed` <br/> |
   
## <a name="see-also"></a><span data-ttu-id="8296c-149">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="8296c-149">See also</span></span>

#### 

[<span data-ttu-id="8296c-150">Hilfe für Partner</span><span class="sxs-lookup"><span data-stu-id="8296c-150">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)

