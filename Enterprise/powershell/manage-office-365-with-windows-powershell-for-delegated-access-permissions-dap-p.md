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
ms.openlocfilehash: 22fd26fb89d15cc036d52ed49ec61319c7e13a52
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230481"
---
# <a name="manage-microsoft-365-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="20698-103">Verwalten von Microsoft 365 mit Windows PowerShell für Partner mit Delegierten Zugriffsberechtigungen (Delegated Access Permission, DAP)</span><span class="sxs-lookup"><span data-stu-id="20698-103">Manage Microsoft 365 with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

<span data-ttu-id="20698-104">*Dieser Artikel bezieht sich sowohl auf Microsoft 365 Enterprise als auch auf Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="20698-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="20698-105">DAP-Partner (Delegated Access Permission, delegierte Zugriffsberechtigung) sind Syndication-Partner und Cloudlösungsanbieter (Cloud Solution Providers, CSP).</span><span class="sxs-lookup"><span data-stu-id="20698-105">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="20698-106">Häufig handelt es sich um Netzwerk- oder Telekom-Anbieter für andere Unternehmen.</span><span class="sxs-lookup"><span data-stu-id="20698-106">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="20698-107">Sie bündeln Microsoft 365-Abonnements für Ihre Kunden in ihren Dienst angeboten.</span><span class="sxs-lookup"><span data-stu-id="20698-107">They bundle Microsoft 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="20698-108">Wenn Sie ein Microsoft 365-Abonnement verkaufen, werden Ihnen automatisch Administratoren im Namen von (AOBO) Berechtigungen für den Kundenmandanten erteilt, damit Sie den Kundenmandanten verwalten und melden können.</span><span class="sxs-lookup"><span data-stu-id="20698-108">When they sell a Microsoft 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span> <span data-ttu-id="20698-109">Im besten Fällen ist dies im Microsoft 365 Admin Center schwierig und zeitaufwendig.</span><span class="sxs-lookup"><span data-stu-id="20698-109">At best, this is difficult and time consuming to do in the Microsoft 365 admin center.</span></span> <span data-ttu-id="20698-110">Es ist viel einfacher, administrative Aufgaben auszuführen, wie das Auflisten aller Kunden- **TenantIds** und deren Domänen oder das Identifizieren aller Benutzer in einer Mandantschaft und welche Lizenzen Ihnen mithilfe von PowerShell für Microsoft 365 zugewiesen werden.</span><span class="sxs-lookup"><span data-stu-id="20698-110">It is much easier to do administrative tasks like listing all the customer **TenantIds** and their domains or identifying all users in a customer tenancy and what licenses they are assigned by using PowerShell for Microsoft 365.</span></span> <span data-ttu-id="20698-111">In einigen Fällen ist es möglich, diese administrativen Aufgaben nur in PowerShell für Microsoft 365 auszuführen.</span><span class="sxs-lookup"><span data-stu-id="20698-111">In some cases, it is possible to do these administrative tasks only in PowerShell for Microsoft 365.</span></span> <span data-ttu-id="20698-112">Nachfolgend finden Sie einige Beispiele für Szenarien, die Syndication- und CSP-Partner am häufigsten verwenden, um ihre Kundenmandanten zu verwalten:</span><span class="sxs-lookup"><span data-stu-id="20698-112">Here are samples of scenarios that Syndication and CSP partners most frequently use to administer their customer tenancies:</span></span>
  
## 

- [<span data-ttu-id="20698-113">Verwalten von Microsoft 365-Mandanten mit Windows PowerShell für Partner mit Delegierten Zugriffsberechtigungen (Delegated Access Permission, DAP)</span><span class="sxs-lookup"><span data-stu-id="20698-113">Manage Microsoft 365 tenants with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](manage-office-365-tenants-with-windows-powershell-for-delegated-access-permissio.md)
    
- [<span data-ttu-id="20698-114">Hinzufügen einer Domäne zu einem Kundenmandanten mit Windows PowerShell für Partner mit delegierten Zugriffsberechtigungen (Delegated Access Permission, DAP)</span><span class="sxs-lookup"><span data-stu-id="20698-114">Add a domain to a client tenancy with Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>](add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-pe.md)
    
- [<span data-ttu-id="20698-115">Verbinden mit Exchange Online-Mandanten über eine Remotesitzung von Windows PowerShell für Partner mit delegierten Zugriffsberechtigungen (Delegated Access Permissions, DAP)</span><span class="sxs-lookup"><span data-stu-id="20698-115">Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)
    
- [<span data-ttu-id="20698-116">Abrufen von Kundenberichtsdaten über Windows PowerShell für Partner mit delegierten Zugriffsberechtigungen (Delegated Access Permission, DAP)</span><span class="sxs-lookup"><span data-stu-id="20698-116">Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-ac.md)
    

    

