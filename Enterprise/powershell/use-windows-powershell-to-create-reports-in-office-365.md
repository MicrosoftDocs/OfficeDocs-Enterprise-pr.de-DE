---
title: Verwenden von PowerShell zum Erstellen von Berichten für Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- seo-marvel-apr2020
ms.assetid: 1ea4d4ec-af89-496f-9678-701867f5a6fc
description: 'Zusammenfassung: Verwenden Sie PowerShell für Microsoft 365 zum Erstellen von Berichten, die im Microsoft 365 Admin Center nicht erstellt werden können.'
ms.openlocfilehash: d2d03d6ac170fef95352a2aabf6cd27176202a1e
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605317"
---
# <a name="use-powershell-to-create-reports-for-microsoft-365"></a><span data-ttu-id="64725-103">Verwenden von PowerShell zum Erstellen von Berichten für Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="64725-103">Use PowerShell to create reports for Microsoft 365</span></span>

<span data-ttu-id="64725-104">*Dieser Artikel gilt sowohl für Microsoft 365 Enterprise als auch für Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="64725-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="64725-105">Im Microsoft 365 Admin Center stehen zahlreiche Berichte zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="64725-105">There are many different reports available in the Microsoft 365 admin center.</span></span> <span data-ttu-id="64725-106">Allerdings sind die Informationen in diesen Berichten in einigen Fällen nicht ausreichend.</span><span class="sxs-lookup"><span data-stu-id="64725-106">However, these reports only provide so much information and sometimes you need more.</span></span> <span data-ttu-id="64725-107">Dies ist der Zeitpunkt, zu dem Sie PowerShell für Microsoft 365 benötigen.</span><span class="sxs-lookup"><span data-stu-id="64725-107">That's when you need PowerShell for Microsoft 365</span></span>
  
<span data-ttu-id="64725-108">In diesen Artikeln wird beschrieben, wie Sie mithilfe von PowerShell für Microsoft 365 Informationen von Ihrem Microsoft 365-Mandanten erhalten:</span><span class="sxs-lookup"><span data-stu-id="64725-108">These articles that describe how to use PowerShell for Microsoft 365 to obtain information from your Microsoft 365 tenant:</span></span>
  
- <span data-ttu-id="64725-109">Erste Schritte mit der Berichterstellung mithilfe von PowerShell für Microsoft 365:</span><span class="sxs-lookup"><span data-stu-id="64725-109">Getting started with reporting using PowerShell for Microsoft 365:</span></span>
    
  - [<span data-ttu-id="64725-110">PowerShell für Microsoft 365 kann zusätzliche Informationen aufdecken, die Sie mit dem Admin Center nicht sehen können.</span><span class="sxs-lookup"><span data-stu-id="64725-110">PowerShell for Microsoft 365 can reveal additional information that you cannot see with the Admin center</span></span>](https://technet.microsoft.com/library/dn568034.aspx#reveal)
    
  - [<span data-ttu-id="64725-111">PowerShell für Microsoft 365 eignet sich hervorragend zum Filtern von Daten</span><span class="sxs-lookup"><span data-stu-id="64725-111">PowerShell for Microsoft 365 is great at filtering data</span></span>](https://technet.microsoft.com/library/dn568034.aspx#filter)
    
  - [<span data-ttu-id="64725-112">PowerShell für Microsoft 365 erleichtert das Drucken oder Speichern von Daten</span><span class="sxs-lookup"><span data-stu-id="64725-112">PowerShell for Microsoft 365 makes it easy to print or save data</span></span>](https://technet.microsoft.com/library/dn568034.aspx#printsave)
    
- <span data-ttu-id="64725-113">Berichte für Benutzerkonten und Lizenzen:</span><span class="sxs-lookup"><span data-stu-id="64725-113">Reports for user accounts and licenses:</span></span>
    
  - [<span data-ttu-id="64725-114">Anzeigen von Microsoft 365-Lizenzen und-Diensten mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="64725-114">View Microsoft 365 licenses and services with PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="64725-115">Anzeigen von Microsoft 365 lizenzierten und nicht lizenzierten Benutzern mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="64725-115">View Microsoft 365 licensed and unlicensed users with PowerShell</span></span>](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
    
  - [<span data-ttu-id="64725-116">Anzeigen von Microsoft 365-Konto Lizenz-und-Dienstdetails mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="64725-116">View Microsoft 365 account license and service details with PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
  - [<span data-ttu-id="64725-117">Anzeigen von Microsoft 365-Benutzerkonten mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="64725-117">View Microsoft 365 user accounts with PowerShell</span></span>](view-user-accounts-with-office-365-powershell.md)
    
- <span data-ttu-id="64725-118">Berichte für SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="64725-118">Reports for SharePoint Online:</span></span>
    
  - [<span data-ttu-id="64725-119">Erste Schritte mit der SharePoint Online-Verwaltungsshell</span><span class="sxs-lookup"><span data-stu-id="64725-119">Get started with SharePoint Online Management Shell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)
    
  - [<span data-ttu-id="64725-120">Verwalten von SharePoint Online-Websitegruppen mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="64725-120">Manage SharePoint Online site groups with PowerShell</span></span>](https://technet.microsoft.com/library/122f4099-c78d-4cce-bab0-4343b04596ae.aspx)
    
- <span data-ttu-id="64725-121">Berichte für Exchange Online:</span><span class="sxs-lookup"><span data-stu-id="64725-121">Reports for Exchange Online:</span></span>
    
  - [<span data-ttu-id="64725-122">Anzeigen Exchange Online Postfachinformationen mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="64725-122">Display Exchange Online mailbox information with PowerShell</span></span>](https://technet.microsoft.com/library/13843002-56ca-4b75-81c5-84386522b01b.aspx)
    
  - [<span data-ttu-id="64725-123">Anzeigen von Exchange Online-Berichten mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="64725-123">Display Exchange Online reports with PowerShell</span></span>](https://technet.microsoft.com/library/4873a063-9fc4-4ed9-826a-6e935fef61d4.aspx)
    
## <a name="related-topics"></a><span data-ttu-id="64725-124">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="64725-124">Related topics</span></span>

[<span data-ttu-id="64725-125">Verwalten von Microsoft 365 mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="64725-125">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="64725-126">Erste Schritte mit PowerShell für Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="64725-126">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="64725-127">Verwalten von SharePoint Online mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="64725-127">Manage SharePoint Online with PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
  
[<span data-ttu-id="64725-128">Verwalten von Microsoft 365-Benutzerkonten, -Lizenzen und -Gruppen mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="64725-128">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
