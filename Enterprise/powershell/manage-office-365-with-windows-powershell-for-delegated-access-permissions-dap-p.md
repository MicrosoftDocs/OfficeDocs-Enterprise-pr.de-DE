---
title: Verwalten von Microsoft 365 mit Windows PowerShell für Partner mit Delegierten Zugriffsberechtigungen (Delegated Access Permission, DAP)
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: hub-page
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
ms.assetid: be497751-596f-431d-b256-0a89d36a47ce
description: 'Zusammenfassung: Partner für Syndication und Cloud Solution Provider (CSP) können Windows PowerShell zum Verwalten von Microsoft 365-Kundenmandanten verwenden.'
ms.openlocfilehash: 00e60693ad10b705765da9ed57142c893a74b034
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998221"
---
# <a name="manage-microsoft-365-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="1e810-103">Verwalten von Microsoft 365 mit Windows PowerShell für Partner mit Delegierten Zugriffsberechtigungen (Delegated Access Permission, DAP)</span><span class="sxs-lookup"><span data-stu-id="1e810-103">Manage Microsoft 365 with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

<span data-ttu-id="1e810-104">DAP-Partner (Delegated Access Permission, delegierte Zugriffsberechtigung) sind Syndication-Partner und Cloudlösungsanbieter (Cloud Solution Providers, CSP).</span><span class="sxs-lookup"><span data-stu-id="1e810-104">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="1e810-105">Häufig handelt es sich um Netzwerk- oder Telekom-Anbieter für andere Unternehmen.</span><span class="sxs-lookup"><span data-stu-id="1e810-105">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="1e810-106">Sie bündeln Microsoft 365-Abonnements für Ihre Kunden in ihren Dienst angeboten.</span><span class="sxs-lookup"><span data-stu-id="1e810-106">They bundle Microsoft 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="1e810-107">Wenn Sie ein Microsoft 365-Abonnement verkaufen, werden Ihnen automatisch Administratoren im Namen von (AOBO) Berechtigungen für den Kundenmandanten erteilt, damit Sie den Kundenmandanten verwalten und melden können.</span><span class="sxs-lookup"><span data-stu-id="1e810-107">When they sell a Microsoft 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span> <span data-ttu-id="1e810-108">Im besten Fällen ist dies im Microsoft 365 Admin Center schwierig und zeitaufwendig.</span><span class="sxs-lookup"><span data-stu-id="1e810-108">At best, this is difficult and time consuming to do in the Microsoft 365 admin center.</span></span> <span data-ttu-id="1e810-109">Es ist viel einfacher, administrative Aufgaben wie das Auflisten aller **TenantIds** der Kunden und ihrer Domänen oder das Identifizieren alle Benutzer in einem Kundenmandanten und deren zugewiesene Lizenzen auszuführen, indem Sie Windows PowerShell für Office 365 verwenden.</span><span class="sxs-lookup"><span data-stu-id="1e810-109">It is much easier to do administrative tasks like listing all the customer **TenantIds** and their domains or identifying all users in a customer tenancy and what licenses they are assigned by using Windows PowerShell for Office 365.</span></span> <span data-ttu-id="1e810-110">In einigen Fällen ist es möglich, diese Verwaltungsaufgaben nur in Windows PowerShell für Office 365 durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="1e810-110">In some cases, it is possible to do these administrative tasks only in Windows PowerShell for Office 365.</span></span> <span data-ttu-id="1e810-111">Nachfolgend finden Sie einige Beispiele für Szenarien, die Syndication- und CSP-Partner am häufigsten verwenden, um ihre Kundenmandanten zu verwalten:</span><span class="sxs-lookup"><span data-stu-id="1e810-111">Here are samples of scenarios that Syndication and CSP partners most frequently use to administer their customer tenancies:</span></span>
  
## 

- [<span data-ttu-id="1e810-112">Verwalten von Microsoft 365-Mandanten mit Windows PowerShell für Partner mit Delegierten Zugriffsberechtigungen (Delegated Access Permission, DAP)</span><span class="sxs-lookup"><span data-stu-id="1e810-112">Manage Microsoft 365 tenants with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](manage-office-365-tenants-with-windows-powershell-for-delegated-access-permissio.md)
    
- [<span data-ttu-id="1e810-113">Hinzufügen einer Domäne zu einem Kundenmandanten mit Windows PowerShell für Partner mit delegierten Zugriffsberechtigungen (Delegated Access Permission, DAP)</span><span class="sxs-lookup"><span data-stu-id="1e810-113">Add a domain to a client tenancy with Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>](add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-pe.md)
    
- [<span data-ttu-id="1e810-114">Verbinden mit Exchange Online-Mandanten über eine Remotesitzung von Windows PowerShell für Partner mit delegierten Zugriffsberechtigungen (Delegated Access Permissions, DAP)</span><span class="sxs-lookup"><span data-stu-id="1e810-114">Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)
    
- [<span data-ttu-id="1e810-115">Abrufen von Kundenberichtsdaten über Windows PowerShell für Partner mit delegierten Zugriffsberechtigungen (Delegated Access Permission, DAP)</span><span class="sxs-lookup"><span data-stu-id="1e810-115">Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-ac.md)
    

    

