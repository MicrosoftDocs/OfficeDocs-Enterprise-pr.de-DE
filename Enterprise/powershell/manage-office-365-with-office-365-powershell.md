---
title: Verwalten von Microsoft 365 mit PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- O365ITProTrain
- Ent_Office_Other
- seo-marvel-apr2020
ms.assetid: 932d57c0-1520-4f0f-8ec9-9966d646480f
description: Informationen zum Verwalten von Microsoft 365-Benutzern und-Lizenzen sowie von Microsoft 365-apps mit PowerShell.
ms.openlocfilehash: ed20ec5bbe05ab0be382b87c04ba2dbc9428b4cc
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605931"
---
# <a name="manage-microsoft-365-with-powershell"></a><span data-ttu-id="fcc32-103">Verwalten von Microsoft 365 mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="fcc32-103">Manage Microsoft 365 with PowerShell</span></span>

<span data-ttu-id="fcc32-104">*Dieser Artikel gilt sowohl für Microsoft 365 Enterprise als auch für Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="fcc32-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="fcc32-105">PowerShell für Microsoft 365 ist ein leistungsfähiges Verwaltungstool, das das Microsoft 365 Admin Center ergänzt.</span><span class="sxs-lookup"><span data-stu-id="fcc32-105">PowerShell for Microsoft 365 is a powerful management tool that complements the Microsoft 365 admin center.</span></span> <span data-ttu-id="fcc32-106">Sie können beispielsweise PowerShell-Automatisierung verwenden, um mehrere Benutzerkonten und Lizenzen schneller zu verwalten und Berichte zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="fcc32-106">For example, you can use PowerShell automation to more quickly manage multiple user accounts and licenses and create reports.</span></span> <span data-ttu-id="fcc32-107">In diesem Artikel erfahren Sie, wie Sie PowerShell für Microsoft 365-Benutzer und-Lizenzen, Skype for Business Online, SharePoint Online, Exchange Online und das Security & Compliance Center verwenden.</span><span class="sxs-lookup"><span data-stu-id="fcc32-107">Learn how to use PowerShell for Microsoft 365 users and licenses, Skype for Business Online, SharePoint Online, Exchange Online, and the Security & Compliance Center.</span></span>
  
<span data-ttu-id="fcc32-108">Wählen Sie das Thema basierend auf Ihren Anforderungen aus:</span><span class="sxs-lookup"><span data-stu-id="fcc32-108">Select the topic based on your needs:</span></span>
  
- [<span data-ttu-id="fcc32-109">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="fcc32-109">Get started</span></span>](getting-started-with-office-365-powershell.md)

    <span data-ttu-id="fcc32-110">Beginnen Sie hier, wenn Sie mit PowerShell für Microsoft 365 nicht vertraut sind und die Microsoft 365-Module installieren und eine Verbindung mit Ihrem Microsoft 365-Abonnement herstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="fcc32-110">Start here if you are not familiar with PowerShell for Microsoft 365 and want to install the Microsoft 365 modules and connect to your Microsoft 365 subscription.</span></span>

- [<span data-ttu-id="fcc32-111">Benutzerkonten, Lizenzen und Gruppen</span><span class="sxs-lookup"><span data-stu-id="fcc32-111">User accounts, licenses, and groups</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)

    <span data-ttu-id="fcc32-112">Beginnen Sie hier, wenn Sie die Microsoft 365-Module installiert haben und mehr über die Verwendung von Automatisierungs Befehlen zum Verwalten von Benutzerkonten, Lizenzen und Gruppen erfahren möchten.</span><span class="sxs-lookup"><span data-stu-id="fcc32-112">Start here if you have installed the Microsoft 365 modules and want to learn more about using automation commands to manage user accounts, licenses, and groups.</span></span>

- [<span data-ttu-id="fcc32-113">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="fcc32-113">SharePoint Online</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/manage-sharepoint-online-with-office-365-powershell)

    <span data-ttu-id="fcc32-114">Beginnen Sie hier, wenn Sie die Microsoft 365-Module installiert haben und Automatisierungs Befehle verwenden möchten, um die Verwaltung von SharePoint Online durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="fcc32-114">Start here if you have installed the Microsoft 365 modules and want to use automation commands to perform management of SharePoint Online.</span></span>

- [<span data-ttu-id="fcc32-115">Exchange Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="fcc32-115">Exchange Online PowerShell</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell)

    <span data-ttu-id="fcc32-116">Beginnen Sie hier, wenn Sie die Automatisierungsbefehle zum Verwalten von Exchange Online verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="fcc32-116">Start here if you want to use automation commands to manage Exchange Online.</span></span>

- [<span data-ttu-id="fcc32-117">E-Mail-Migration</span><span class="sxs-lookup"><span data-stu-id="fcc32-117">Email migration</span></span>](use-powershell-for-email-migration-to-office-365.md)

    <span data-ttu-id="fcc32-118">Beginnen Sie hier, wenn Sie die PowerShell 365-Module installiert haben und Ihre e-Mails von vorhandenen Systemen migrieren möchten.</span><span class="sxs-lookup"><span data-stu-id="fcc32-118">Start here if you have installed the PowerShell 365 modules and want to migrate your email from existing systems.</span></span>

- [<span data-ttu-id="fcc32-119">Security & Compliance Center</span><span class="sxs-lookup"><span data-stu-id="fcc32-119">Security & Compliance Center</span></span>](https://docs.microsoft.com/powershell/exchange/office-365-scc/office-365-scc-powershell)

    <span data-ttu-id="fcc32-120">Beginnen Sie hier, wenn Sie die Automatisierungsbefehle zum Verwalten des Security & Compliance Center verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="fcc32-120">Start here if you want to use automation commands to manage the Security & Compliance Center.</span></span>

- [<span data-ttu-id="fcc32-121">Partner für Delegierte Zugriffsberechtigungen (DAP)</span><span class="sxs-lookup"><span data-stu-id="fcc32-121">Delegated Access Permissions (DAP) partners</span></span>](manage-office-365-with-windows-powershell-for-delegated-access-permissions-dap-p.md)

    <span data-ttu-id="fcc32-122">Beginnen Sie hier, wenn Sie Partner von Syndication und Cloud Solution Provider (CSP) zum Verwalten Ihrer Microsoft 365-Kundenmandanten verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="fcc32-122">Start here if you want to use Syndication and Cloud Solution Provider (CSP) partners to manage your Microsoft 365 customer tenants.</span></span>

- [<span data-ttu-id="fcc32-123">Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="fcc32-123">Skype for Business Online</span></span>](manage-skype-for-business-online-with-office-365-powershell.md)

    <span data-ttu-id="fcc32-124">Beginnen Sie hier, wenn Sie die PowerShell-Module installiert haben und die Verwaltung von Skype for Business Online durchführen möchten.</span><span class="sxs-lookup"><span data-stu-id="fcc32-124">Start here if you have installed the PowerShell modules and want to perform management of Skype for Business Online.</span></span>
