---
title: Verwalten von Office 365 mit Windows PowerShell für Partner mit delegierten Zugriffsberechtigungen (Delegated Access Permissions, DAP)
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
ms.custom: ''
ms.assetid: be497751-596f-431d-b256-0a89d36a47ce
description: Zusammenfassung:Syndication-Partner und Cloudlösungsanbieter (Cloud Solution Providers, CSP) können Windows PowerShell zum Verwalten von Office 365-Kundenmandanten verwenden.
ms.openlocfilehash: abbd5a0e2f288a6d6d0250cca57ec4c48a0bd88e
ms.sourcegitcommit: 1c97471f47e1869f6db684f280f9085b7c2ff59f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/18/2019
ms.locfileid: "35781775"
---
# <a name="manage-office-365-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="c9d22-103">Verwalten von Office 365 mit Windows PowerShell für Partner mit delegierten Zugriffsberechtigungen (Delegated Access Permissions, DAP)</span><span class="sxs-lookup"><span data-stu-id="c9d22-103">Manage Office 365 with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

 <span data-ttu-id="c9d22-104">**Zusammenfassung:** Syndication-Partner und Cloudlösungsanbieter (Cloud Solution Providers, CSP) können Windows PowerShell zum Verwalten von Office 365-Kundenmandanten verwenden.</span><span class="sxs-lookup"><span data-stu-id="c9d22-104">**Summary:** Syndication and Cloud Solution Provider (CSP) partners can use Windows PowerShell to manage Office 365 customer tenants.</span></span>
  
<span data-ttu-id="c9d22-105">DAP-Partner (Delegated Access Permission, delegierte Zugriffsberechtigung) sind Syndication-Partner und Cloudlösungsanbieter (Cloud Solution Providers, CSP).</span><span class="sxs-lookup"><span data-stu-id="c9d22-105">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="c9d22-106">Häufig handelt es sich um Netzwerk- oder Telekom-Anbieter für andere Unternehmen.</span><span class="sxs-lookup"><span data-stu-id="c9d22-106">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="c9d22-107">Sie bündeln Office 365-Abonnements in Serviceangeboten für ihre Kunden.</span><span class="sxs-lookup"><span data-stu-id="c9d22-107">They bundle Office 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="c9d22-108">Wenn sie ein Office 365-Abonnement verkaufen, erhalten sie automatisch AOBO-Berechtigungen (Administer On Behalf Of, Verwalten im Namen von) für die Kundenmandanten, damit sie diese verwalten und Berichte darüber erstellen können.</span><span class="sxs-lookup"><span data-stu-id="c9d22-108">When they sell an Office 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span> <span data-ttu-id="c9d22-109">Im besten Fällen ist dies im Microsoft 365 Admin Center schwierig und zeitaufwendig.</span><span class="sxs-lookup"><span data-stu-id="c9d22-109">At best, this is difficult and time consuming to do in the Microsoft 365 admin center.</span></span> <span data-ttu-id="c9d22-110">Es ist viel einfacher, administrative Aufgaben wie das Auflisten aller **TenantIds** der Kunden und ihrer Domänen oder das Identifizieren alle Benutzer in einem Kundenmandanten und deren zugewiesene Lizenzen auszuführen, indem Sie Windows PowerShell für Office 365 verwenden.</span><span class="sxs-lookup"><span data-stu-id="c9d22-110">It is much easier to do administrative tasks like listing all the customer **TenantIds** and their domains or identifying all users in a customer tenancy and what licenses they are assigned by using Windows PowerShell for Office 365.</span></span> <span data-ttu-id="c9d22-111">In einigen Fällen ist es möglich, diese Verwaltungsaufgaben nur in Windows PowerShell für Office 365 durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="c9d22-111">In some cases, it is possible to do these administrative tasks only in Windows PowerShell for Office 365.</span></span> <span data-ttu-id="c9d22-112">Nachfolgend finden Sie einige Beispiele für Szenarien, die Syndication- und CSP-Partner am häufigsten verwenden, um ihre Kundenmandanten zu verwalten:</span><span class="sxs-lookup"><span data-stu-id="c9d22-112">Here are samples of scenarios that Syndication and CSP partners most frequently use to administer their customer tenancies:</span></span>
  
## 

- [<span data-ttu-id="c9d22-113">Verwalten von Office 365-Mandanten mit Windows PowerShell für Partner mit delegierten Zugriffsberechtigungen (Delegated Access Permissions, DAP)</span><span class="sxs-lookup"><span data-stu-id="c9d22-113">Manage Office 365 tenants with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](manage-office-365-tenants-with-windows-powershell-for-delegated-access-permissio.md)
    
- [<span data-ttu-id="c9d22-114">Hinzufügen einer Domäne zu einem Kundenmandanten mit Windows PowerShell für Partner mit delegierten Zugriffsberechtigungen (Delegated Access Permission, DAP)</span><span class="sxs-lookup"><span data-stu-id="c9d22-114">Add a domain to a client tenancy with Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>](add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-pe.md)
    
- [<span data-ttu-id="c9d22-115">Verbinden mit Exchange Online-Mandanten über eine Remotesitzung von Windows PowerShell für Partner mit delegierten Zugriffsberechtigungen (Delegated Access Permissions, DAP)</span><span class="sxs-lookup"><span data-stu-id="c9d22-115">Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)
    
- [<span data-ttu-id="c9d22-116">Abrufen von Kundenberichtsdaten über Windows PowerShell für Partner mit delegierten Zugriffsberechtigungen (Delegated Access Permission, DAP)</span><span class="sxs-lookup"><span data-stu-id="c9d22-116">Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-ac.md)
    

    

