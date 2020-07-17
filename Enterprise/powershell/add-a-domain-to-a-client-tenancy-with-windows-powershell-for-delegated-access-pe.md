---
title: Hinzufügen einer Domäne zu einem Kundenmandanten mit Windows PowerShell für Partner mit delegierten Zugriffsberechtigungen (Delegated Access Permission, DAP)
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: f49b4d24-9aa0-48a6-95dd-6bae9cf53d2c
description: 'Zusammenfassung: Verwenden Sie Windows PowerShell für Microsoft 365, um einen alternativen Domänennamen zu einem vorhandenen Kundenmandanten hinzuzufügen.'
ms.openlocfilehash: 6ba706c1fc0b2e2b43687ac582a40f36a2a3387c
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997361"
---
# <a name="add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-permission-dap-partners"></a><span data-ttu-id="26c22-103">Hinzufügen einer Domäne zu einem Kundenmandanten mit Windows PowerShell für Partner mit delegierten Zugriffsberechtigungen (Delegated Access Permission, DAP)</span><span class="sxs-lookup"><span data-stu-id="26c22-103">Add a domain to a client tenancy with Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>

<span data-ttu-id="26c22-104">Sie können neue Domänen mit dem Mandanten Ihres Kunden mit Windows PowerShell für Microsoft 365 schneller als mit dem Microsoft 365 Admin Center erstellen und zuordnen.</span><span class="sxs-lookup"><span data-stu-id="26c22-104">You can create and associate new domains with your customer's tenancy with Windows PowerShell for Microsoft 365 faster than using the Microsoft 365 admin center.</span></span>
  
<span data-ttu-id="26c22-105">DAP-Partner (Delegated Access Permission, delegierte Zugriffsberechtigung) sind Syndication-Partner und Cloudlösungsanbieter (Cloud Solution Providers, CSP).</span><span class="sxs-lookup"><span data-stu-id="26c22-105">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="26c22-106">Häufig handelt es sich um Netzwerk- oder Telekom-Anbieter für andere Unternehmen.</span><span class="sxs-lookup"><span data-stu-id="26c22-106">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="26c22-107">Sie bündeln Microsoft 365-Abonnements für Ihre Kunden in ihren Dienst angeboten.</span><span class="sxs-lookup"><span data-stu-id="26c22-107">They bundle Microsoft 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="26c22-108">Wenn Sie ein Microsoft 365-Abonnement verkaufen, werden Ihnen automatisch Administratoren im Namen von (AOBO) Berechtigungen für den Kundenmandanten erteilt, damit Sie den Kundenmandanten verwalten und melden können.</span><span class="sxs-lookup"><span data-stu-id="26c22-108">When they sell a Microsoft 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="26c22-109">Was sollten Sie wissen, bevor Sie beginnen?</span><span class="sxs-lookup"><span data-stu-id="26c22-109">What do you need to know before you begin?</span></span>

<span data-ttu-id="26c22-p102">Für die Verfahren in diesem Thema müssen Sie eine Verbindung mit Windows PowerShell für Office 365 herstellen. Weitere Anweisungen finden Sie unter [Verbinden mit Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="26c22-p102">The procedures in this topic require you to connect to Windows PowerShell for Office 365. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
<span data-ttu-id="26c22-112">Sie benötigen auch die Administratoranmeldeinformationen Ihres Partnermandanten.</span><span class="sxs-lookup"><span data-stu-id="26c22-112">You also need your partner tenant administrator credentials.</span></span>
  
<span data-ttu-id="26c22-113">Sie benötigen außerdem die folgenden Informationen:</span><span class="sxs-lookup"><span data-stu-id="26c22-113">You also need the following information:</span></span>
  
- <span data-ttu-id="26c22-114">Sie benötigen den vollqualifizierten Domänennamen (FQDN), den der Kunde verwenden möchte.</span><span class="sxs-lookup"><span data-stu-id="26c22-114">You need the fully qualified domain name (FQDN) that your customer wants.</span></span>
    
- <span data-ttu-id="26c22-115">Sie benötigen die **TenantId** des Kunden.</span><span class="sxs-lookup"><span data-stu-id="26c22-115">You need the customer's **TenantId**.</span></span>
    
- <span data-ttu-id="26c22-p103">Der FQDN muss bei einer Registrierungsstelle für Internetdomänennamen, wie z. B. GoDaddy, registriert sein. Weitere Informationen für die öffentliche Registrierung eines Domänennamens finden Sie unter [Erwerben eines Domänennamens](https://go.microsoft.com/fwlink/p/?LinkId=532541).</span><span class="sxs-lookup"><span data-stu-id="26c22-p103">The FQDN must be registered with an Internet domain name service (DNS) registrar, such as GoDaddy. For more information on how to publically register a domain name, see [How to buy a domain name](https://go.microsoft.com/fwlink/p/?LinkId=532541).</span></span>
    
- <span data-ttu-id="26c22-118">Sie müssen wissen, wie Sie einen TXT-Eintrag zur registrierten DNS-Zone für die DNS-Registrierungsstelle hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="26c22-118">You need to know how to add a TXT record to the registered DNS zone for your DNS registrar.</span></span> <span data-ttu-id="26c22-119">Weitere Informationen zum Hinzufügen eines txt-Eintrags finden Sie unter [Hinzufügen von DNS-Einträgen zum Verbinden Ihrer Domäne](https://go.microsoft.com/fwlink/p/?LinkId=532542).</span><span class="sxs-lookup"><span data-stu-id="26c22-119">For more information on how to add a TXT record, see [Add DNS records to connect your domain](https://go.microsoft.com/fwlink/p/?LinkId=532542).</span></span> <span data-ttu-id="26c22-120">Wenn Sie diese Verfahren nicht durchführen können, müssen Sie die für die DNS-Registrierungsstelle anwendbaren Verfahren ermitteln.</span><span class="sxs-lookup"><span data-stu-id="26c22-120">If those procedures don't work for you, you will need to find the procedures for your DNS registrar.</span></span>
    
## <a name="create-domains"></a><span data-ttu-id="26c22-121">Erstellen von Domänen</span><span class="sxs-lookup"><span data-stu-id="26c22-121">Create domains</span></span>

 <span data-ttu-id="26c22-p105">Ihre Kunden werden Sie wahrscheinlich bitten, weitere Domänen für ihren Mandanten zu erstellen, da sie die Standarddomäne<Domäne>.onmicrosoft.comwahrscheinlich nicht als primären Domäne verwenden möchten, um ihr Unternehmen im Internet weltweit zu repräsentieren. Dieses Verfahren leitet Sie durch die Schritte zum Erstellen einer neuen Domäne, die Sie mit dem Kundenmandanten verknüpfen können.</span><span class="sxs-lookup"><span data-stu-id="26c22-p105">Your customers will likely ask you to create additional domains to associate with their tenancy because they don't want the default <domain>.onmicrosoft.com domain to be the primary one that represents their corporate identities to the world. This procedure walks you through creating a new domain associated with your customer's tenancy.</span></span>
  
> [!NOTE]
> <span data-ttu-id="26c22-124">Um einige dieser Vorgänge ausführen zu können, muss das Partneradministrator Konto, mit dem Sie sich anmelden, auf **vollständige Verwaltung** für die Einstellung **administrativer Zugriff für Unternehmen zuweisen, die Sie unterstützen** in den Details des Administratorkontos im Microsoft 365 Admin Center festgelegt sein.</span><span class="sxs-lookup"><span data-stu-id="26c22-124">To perform some of these operations, the partner administrator account you sign in with must be set to **Full administration** for the **Assign administrative access to companies you support** setting found in the details of the admin account in the Microsoft 365 admin center.</span></span> <span data-ttu-id="26c22-125">Weitere Informationen zum Verwalten von Partneradministrator Rollen finden Sie unter [Partners: Offer delegierte Administration](https://go.microsoft.com/fwlink/p/?LinkId=532435).</span><span class="sxs-lookup"><span data-stu-id="26c22-125">For more information on managing partner administrator roles, see [Partners: Offer delegated administration](https://go.microsoft.com/fwlink/p/?LinkId=532435).</span></span> 
  
### <a name="create-the-domain-in-azure-active-directory"></a><span data-ttu-id="26c22-126">Erstellen Sie die Domäne in Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="26c22-126">Create the domain in Azure Active Directory</span></span>

<span data-ttu-id="26c22-127">Dieser Befehl erstellt die Domäne in Azure Active Directory, ordnet sie jedoch nicht der öffentlich registrierten Domäne zu.</span><span class="sxs-lookup"><span data-stu-id="26c22-127">This command creates the domain in Azure Active Directory but does not associate it with the publicly registered domain.</span></span> <span data-ttu-id="26c22-128">Das kommt, wenn Sie nachweisen, dass Sie die öffentlich registrierte Domäne für Microsoft Microsoft 365 für Unternehmen besitzen.</span><span class="sxs-lookup"><span data-stu-id="26c22-128">That comes when you prove that you own the publicly registered domain to Microsoft Microsoft 365 for enterprises.</span></span>
  
```
New-MsolDomain -TenantId <customer TenantId> -Name <FQDN of new domain>
```

>[!Note]
><span data-ttu-id="26c22-129">PowerShell Core unterstützt nicht das Microsoft Azure Active Directory-Modul für Windows PowerShell und Cmdlets mit **Msol** im Namen.</span><span class="sxs-lookup"><span data-stu-id="26c22-129">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="26c22-130">Um diese Cmdlets weiterhin verwenden zu können, müssen Sie sie über Windows PowerShell ausführen.</span><span class="sxs-lookup"><span data-stu-id="26c22-130">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

### <a name="get-the-data-for-the-dns-txt-verification-record"></a><span data-ttu-id="26c22-131">Abrufen der Daten für den DNS-TXT-Überprüfungseintrag</span><span class="sxs-lookup"><span data-stu-id="26c22-131">Get the data for the DNS TXT verification record</span></span>

 <span data-ttu-id="26c22-132">Microsoft 365 generiert die spezifischen Daten, die Sie in den DNS TXT-Überprüfungs Eintrag einfügen müssen.</span><span class="sxs-lookup"><span data-stu-id="26c22-132">Microsoft 365 will generate the specific data that you need to place into the DNS TXT verification record.</span></span> <span data-ttu-id="26c22-133">Führen Sie diesen Befehl aus, um die Daten abzurufen.</span><span class="sxs-lookup"><span data-stu-id="26c22-133">To get the data, run this command.</span></span>
  
```
Get-MsolDomainVerificationDNS -TenantId <customer TenantId> -DomainName <FQDN of new domain> -Mode DnsTxtRecord
```

<span data-ttu-id="26c22-134">Dadurch erhalten Sie die folgende Ausgabe:</span><span class="sxs-lookup"><span data-stu-id="26c22-134">This will give you output like:</span></span>
  
 `Label: domainname.com`
  
 `Text: MS=ms########`
  
 `Ttl: 3600`
  
> [!NOTE]
> <span data-ttu-id="26c22-135">Sie benötigen diesen Text, um den TXT-Eintrag in der öffentlich registrierten DNS-Zone zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="26c22-135">You will need this text to create the TXT record in the publicly registered DNS zone.</span></span> <span data-ttu-id="26c22-136">Stellen Sie sicher, dass Sie ihn kopieren und speichern.</span><span class="sxs-lookup"><span data-stu-id="26c22-136">Be sure to copy and save it.</span></span> 
  
### <a name="add-a-txt-record-to-the-publically-registered-dns-zone"></a><span data-ttu-id="26c22-137">Hinzufügen eines TXT-Eintrags zur öffentlich registrierten DNS-Zone</span><span class="sxs-lookup"><span data-stu-id="26c22-137">Add a TXT record to the publically registered DNS zone</span></span>

<span data-ttu-id="26c22-138">Bevor Microsoft 365 beginnt, Datenverkehr zu akzeptieren, der an den öffentlich registrierten Domänennamen weitergeleitet wird, müssen Sie nachweisen, dass Sie Eigentümer der Domäne sind und über Administratorrechte verfügen.</span><span class="sxs-lookup"><span data-stu-id="26c22-138">Before Microsoft 365 will start accepting traffic that is directed to the publicly registered domain name, you must prove that you own and have administrator permissions to the domain.</span></span> <span data-ttu-id="26c22-139">Sie weisen nach, dass Sie die Domäne besitzen, indem Sie einen TXT-Eintrag in der Domäne erstellen.</span><span class="sxs-lookup"><span data-stu-id="26c22-139">You prove you own the domain by creating a TXT record in the domain.</span></span> <span data-ttu-id="26c22-140">Ein TXT-Eintrag hat keine Auswirkungen auf die Domäne, und er kann gelöscht werden, nachdem die Besitzrechte an der Domäne nachgewiesen wurden.</span><span class="sxs-lookup"><span data-stu-id="26c22-140">A TXT record doesn't do anything in your domain, and it can be deleted after your ownership of the domain is established.</span></span> <span data-ttu-id="26c22-141">Zum Erstellen der TXT-Einträge führen Sie die Verfahren unter [Hinzufügen von DNS-Einträgen aus, um eine Verbindung mit Ihrer Domäne herzustellen](https://go.microsoft.com/fwlink/p/?LinkId=532542).</span><span class="sxs-lookup"><span data-stu-id="26c22-141">To create the TXT records, follow the procedures at [Add DNS records to connect your domain](https://go.microsoft.com/fwlink/p/?LinkId=532542).</span></span> <span data-ttu-id="26c22-142">Wenn Sie diese Verfahren nicht durchführen können, müssen Sie die für die DNS-Registrierungsstelle anwendbaren Verfahren ermitteln.</span><span class="sxs-lookup"><span data-stu-id="26c22-142">If those procedures don't work for you , you need to find the procedures for your DNS registrar.</span></span>
  
<span data-ttu-id="26c22-p112">Bestätigen Sie die erfolgreiche Erstellung des TXT-Eintrags über Nslookup. Verwenden Sie die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="26c22-p112">Confirm the successful creation of the TXT record via nslookup. Follow this syntax.</span></span>
  
```
nslookup -type=TXT <FQDN of registered domain>
```

<span data-ttu-id="26c22-145">Dadurch erhalten Sie die folgende Ausgabe:</span><span class="sxs-lookup"><span data-stu-id="26c22-145">This will give you output like:</span></span>
  
 `Non-authoritative answer:`
  
 `FQDN of the registered domain`
  
 `text=MS=ms########`
  
### <a name="validate-domain-ownership-in-microsoft-365"></a><span data-ttu-id="26c22-146">Überprüfen des Domänenbesitzes in Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="26c22-146">Validate domain ownership in Microsoft 365</span></span>

<span data-ttu-id="26c22-147">In diesem letzten Schritt validieren Sie Microsoft 365, dass Sie die Domäne mit öffentlichem Namen besitzen.</span><span class="sxs-lookup"><span data-stu-id="26c22-147">In this last step, you validate to Microsoft 365 that you own the publically registered domain.</span></span> <span data-ttu-id="26c22-148">Nach diesem Schritt akzeptiert Microsoft 365 den Datenverkehr, der an den neuen Domänennamen weitergeleitet wird.</span><span class="sxs-lookup"><span data-stu-id="26c22-148">After this step, Microsoft 365 will begin accepting traffic routed to the new domain name.</span></span> <span data-ttu-id="26c22-149">Um das Erstellen und Registrieren der neuen Domäne abzuschließen, führen Sie den folgenden Befehl aus.</span><span class="sxs-lookup"><span data-stu-id="26c22-149">To complete the domain creation and registration process, run this command.</span></span> 
  
```
Confirm-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

<span data-ttu-id="26c22-150">Dieser Befehl gibt keine Ausgabe zurück. Um sicherzustellen, dass dies funktioniert hat, führen Sie den folgenden Befehl aus.</span><span class="sxs-lookup"><span data-stu-id="26c22-150">This command won't return any output, so to confirm that this worked, run this command.</span></span>
  
```
Get-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

<span data-ttu-id="26c22-151">Dadurch wird in etwa Folgendes zurückgegeben</span><span class="sxs-lookup"><span data-stu-id="26c22-151">This will return something like this</span></span>
  
||||
|:-----|:-----|:-----|
| `Name` <br/> | `Status` <br/> | `Authentication` <br/> |
| `FQDN of new domain` <br/> | `Verified` <br/> | `Managed` <br/> |
   
## <a name="see-also"></a><span data-ttu-id="26c22-152">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="26c22-152">See also</span></span>

#### 

[<span data-ttu-id="26c22-153">Hilfe für Partner</span><span class="sxs-lookup"><span data-stu-id="26c22-153">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)

