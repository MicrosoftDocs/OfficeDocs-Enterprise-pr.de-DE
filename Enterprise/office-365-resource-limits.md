---
title: Ressourcengrenzwerte für Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: 'Zusammenfassung: Informationen zu den Ressourcen Grenzwerten für die verschiedenen Anwendungen in Office 365.'
ms.openlocfilehash: 55fa8d90c6f83c84a1e43f32cf7cd0eeafbf1274
ms.sourcegitcommit: ed4482ad35274b79d44d0f9a17be3e52d5ad0492
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "43666326"
---
# <a name="resource-limits"></a><span data-ttu-id="e5c21-103">Ressourcenbeschränkungen</span><span class="sxs-lookup"><span data-stu-id="e5c21-103">Resource Limits</span></span>

<span data-ttu-id="e5c21-104">Ressourcengrenzwerte werden mithilfe von Kontingenten (Limits) und Drosselung erzwungen.</span><span class="sxs-lookup"><span data-stu-id="e5c21-104">Resource limits are enforced using quotas (limits) and throttling.</span></span> <span data-ttu-id="e5c21-105">Azure Active Directory und die einzelnen Office 365 Dienste verwenden beides.</span><span class="sxs-lookup"><span data-stu-id="e5c21-105">Azure Active Directory and the individual Office 365 services use both.</span></span> <span data-ttu-id="e5c21-106">Grenzen sind Dienst spezifisch und ändern sich im Laufe der Zeit, wenn neue Funktionen hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="e5c21-106">Limits are service-specific and change over time as new capabilities are added.</span></span> <span data-ttu-id="e5c21-107">Ausführliche Informationen zu den aktuellen Grenzwerten für die verschiedenen Dienste finden Sie in den folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="e5c21-107">For details on the current limits for the various services, see the following topics:</span></span>

- [<span data-ttu-id="e5c21-108">Grenzwerte und Einschränkungen für Azure Active Directory Service</span><span class="sxs-lookup"><span data-stu-id="e5c21-108">Azure Active Directory service limits and restrictions</span></span>](https://docs.microsoft.com/azure/azure-resource-manager/management/azure-subscription-service-limits)
- [<span data-ttu-id="e5c21-109">Exchange Online-Begrenzungen</span><span class="sxs-lookup"><span data-stu-id="e5c21-109">Exchange Online Limits</span></span>](https://technet.microsoft.com/library/exchange-online-limits.aspx)
- [<span data-ttu-id="e5c21-110">Beschränkungen von Exchange Online Protection</span><span class="sxs-lookup"><span data-stu-id="e5c21-110">Exchange Online Protection Limits</span></span>](https://technet.microsoft.com/library/exchange-online-protection-limits.aspx)
- [<span data-ttu-id="e5c21-111">Grenzen und Grenzwerte für SharePoint Online Software</span><span class="sxs-lookup"><span data-stu-id="e5c21-111">SharePoint Online software boundaries and limits</span></span>](https://support.office.com/article/SharePoint-Online-software-boundaries-and-limits-8F34FF47-B749-408B-ABC0-B605E1F6D498)
- [<span data-ttu-id="e5c21-112">Skype for Business Grenzen</span><span class="sxs-lookup"><span data-stu-id="e5c21-112">Skype for Business Limits</span></span>](https://technet.microsoft.com/library/skype-for-business-online-limits.aspx)
- [<span data-ttu-id="e5c21-113">Jammern der Rest-API und Raten Begrenzungen</span><span class="sxs-lookup"><span data-stu-id="e5c21-113">Yammer REST API and Rate Limits</span></span>](https://developer.yammer.com/docs/rest-api-rate-limits)
- [<span data-ttu-id="e5c21-114">Dateigrößenbeschränkungen in Sway</span><span class="sxs-lookup"><span data-stu-id="e5c21-114">File Size Limits in Sway</span></span>](https://support.office.com/article/File-size-limits-in-Sway-4db21bc6-b42b-499f-9272-66e089db109f)

<span data-ttu-id="e5c21-115">Zusätzlich zu diesen Grenzwerten werden verschiedene Einschränkungs Mechanismen in Azure Active Directory und Office 365 verwendet.</span><span class="sxs-lookup"><span data-stu-id="e5c21-115">In addition to these limits, several throttling mechanisms are used throughout Azure Active Directory and Office 365.</span></span> <span data-ttu-id="e5c21-116">Die Drosselung innerhalb des Diensts ist besonders wichtig, da Netzwerkressourcen in Microsoft-Rechenzentren für die breite Palette von Kunden optimiert sind, die die Dienste nutzen.</span><span class="sxs-lookup"><span data-stu-id="e5c21-116">Throttling within the service is especially important, given that network resources in Microsoft's datacenters are optimized for the broad set of customers that use the services.</span></span> <span data-ttu-id="e5c21-117">Zu den Einschränkungs Mechanismen gehören:</span><span class="sxs-lookup"><span data-stu-id="e5c21-117">Throttling mechanisms include:</span></span>

- <span data-ttu-id="e5c21-118">Azure Active Directory und Office 365 verfügen über Einschränkungen auf Benutzerebene, die die Anzahl der Transaktionen oder gleichzeitigen Aufrufe (durch Skript oder Code) begrenzen, die von einem einzelnen Benutzer ausgeführt werden können.</span><span class="sxs-lookup"><span data-stu-id="e5c21-118">Azure Active Directory and Office 365 feature user-level throttling, which limit the number of transactions or concurrent calls (by script or code) that can be performed by a single user.</span></span>
- <span data-ttu-id="e5c21-119">Jedem Mandanten wird bei der Mandanten Erstellung eine standardmäßige PowerShell-Einschränkungsrichtlinie zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="e5c21-119">A default PowerShell throttling policy is assigned to each tenant at tenant creation.</span></span> <span data-ttu-id="e5c21-120">Diese Einstellungen wirken sich auf andere Elemente aus, beispielsweise die maximale Anzahl gleichzeitiger PowerShell-Sitzungen, die von einem einzelnen Administrator geöffnet werden können.</span><span class="sxs-lookup"><span data-stu-id="e5c21-120">These settings affect other items, such as the maximum number of simultaneous PowerShell sessions that can be opened by a single administrator.</span></span>
- <span data-ttu-id="e5c21-121">Jeder Exchange Online-Kunde verfügt über eine standardmäßige Exchange-Webdienste-Richtlinie, die für EWS-Client Vorgänge optimiert ist, sowie für Einschränkungen, die für alle Outlook-Clients gelten.</span><span class="sxs-lookup"><span data-stu-id="e5c21-121">Each Exchange Online customer has a default Exchange Web Services (EWS) policy that is tuned for EWS client operations, and throttling that applies to all Outlook clients.</span></span>
