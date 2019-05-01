---
title: Aktivieren der Rechteverwaltung im Office 365 Admin Center
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 5/11/2016
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 5b6d3ac7-b1ac-428e-b03e-50e882f85a6e
description: Verweist auf Themen, in denen das Aktivieren und Verwenden des Rights Management-Diensts mit Office 365 beschrieben wird.
ms.openlocfilehash: b3df1f7ff39214d5ab7ab8f5c730299c1c22f30b
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487786"
---
# <a name="activate-rights-management-in-the-office-365-admin-center"></a><span data-ttu-id="8cb5f-103">Aktivieren der Rechteverwaltung im Office 365 Admin Center</span><span class="sxs-lookup"><span data-stu-id="8cb5f-103">Activate Rights Management in the Office 365 admin center</span></span>

<span data-ttu-id="8cb5f-104">In diesem Thema werden Themen erläutert, in denen die Aktivierung und Verwendung von RMS mit Office 365 beschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="8cb5f-104">This topic points to topics that describe how to enable and use RMS with Office 365.</span></span>
  
<span data-ttu-id="8cb5f-105">Sie müssen den Rights Management Service (RMS) aktivieren, bevor Sie die IRM-Funktionen (Information Rights Management, Verwaltung von Informationsrechten) von Office 365-Anwendungen und-Diensten verwenden können.</span><span class="sxs-lookup"><span data-stu-id="8cb5f-105">You must activate the Rights Management service (RMS) before you can use the Information Rights Management (IRM) features of Office 365 applications and services.</span></span> <span data-ttu-id="8cb5f-106">Nachdem Sie RMS aktiviert haben, kann Ihre Organisation wichtige Dokumente und e-Mails mithilfe von Azure RMS schützen.</span><span class="sxs-lookup"><span data-stu-id="8cb5f-106">After you activate RMS, your organization can start to protect important documents and emails by using Azure RMS.</span></span> <span data-ttu-id="8cb5f-107">Diese Information Protection-Lösung kann alle Dateitypen schützen und in Clientanwendungen wie Excel, Microsoft Word und andere, Exchange Online und SharePoint Online und Server wie Microsoft Exchange und Microsoft SharePoint integrieren.</span><span class="sxs-lookup"><span data-stu-id="8cb5f-107">This information protection solution can protect all file types and integrates with client applications like Excel, Microsoft Word, and others, Exchange Online and SharePoint Online, and servers such as Microsoft Exchange and Microsoft SharePoint.</span></span>
  
> [!TIP]
> <span data-ttu-id="8cb5f-108">Wenn Sie nicht sicher sind, ob Sie Rechteverwaltung benötigen, überprüfen Sie, ob Ihre Organisation eines oder mehrere [dieser geschäftlichen Probleme oder Anforderungen](https://docs.microsoft.com/rights-management/understand-explore/azure-rms-problems-it-solves)hat, und sehen Sie sich einige [Beispiele für Rechteverwaltung in Aktion an](https://docs.microsoft.com/rights-management/understand-explore/what-admins-users-see).</span><span class="sxs-lookup"><span data-stu-id="8cb5f-108">If you're not sure whether you need Rights Management, check whether your organization has one or more of [these business problems or requirements](https://docs.microsoft.com/rights-management/understand-explore/azure-rms-problems-it-solves), and see some [examples of Rights Management in action](https://docs.microsoft.com/rights-management/understand-explore/what-admins-users-see).</span></span> 
  
<span data-ttu-id="8cb5f-109">Verwenden Sie die folgenden Links, um weitere Informationen zu RMS zu erhalten:</span><span class="sxs-lookup"><span data-stu-id="8cb5f-109">Use these links for more information on RMS:</span></span>
  
- <span data-ttu-id="8cb5f-110">Weitere Informationen zu RMS finden Sie unter [Was ist Azure Rights Management](https://docs.microsoft.com/rights-management/understand-explore/what-is-azure-rms).</span><span class="sxs-lookup"><span data-stu-id="8cb5f-110">To learn more about RMS, see [What is Azure Rights Management](https://docs.microsoft.com/rights-management/understand-explore/what-is-azure-rms).</span></span>
    
- <span data-ttu-id="8cb5f-111">Weitere Informationen zu RMS finden Sie unter [Overview of Azure Rights Management](https://docs.microsoft.com/rights-management/understand-explore/azure-rights-management).</span><span class="sxs-lookup"><span data-stu-id="8cb5f-111">If you're new to RMS, see [Overview of Azure Rights Management](https://docs.microsoft.com/rights-management/understand-explore/azure-rights-management).</span></span>
    
- <span data-ttu-id="8cb5f-112">Eine Übersicht über die Bereitstellungsschritte finden Sie unter [Azure Rights Management Deployment Roadmap](https://docs.microsoft.com/rights-management/plan-design/deployment-roadmap).</span><span class="sxs-lookup"><span data-stu-id="8cb5f-112">For an overview of the deployment steps see the [Azure Rights Management deployment roadmap](https://docs.microsoft.com/rights-management/plan-design/deployment-roadmap).</span></span>
    
- <span data-ttu-id="8cb5f-113">Anweisungen zum Aktivieren von RMS für Office 365 finden Sie unter [Aktivieren der Azure-Rechteverwaltung](https://technet.microsoft.com/library/jj658941.aspx).</span><span class="sxs-lookup"><span data-stu-id="8cb5f-113">For instructions about activating RMS for Office 365, see [Activating Azure Rights Management](https://technet.microsoft.com/library/jj658941.aspx).</span></span>
    
- <span data-ttu-id="8cb5f-114">Sind Sie über den Unterschied zwischen Azure RMS und IRM in Office verwirrt?</span><span class="sxs-lookup"><span data-stu-id="8cb5f-114">Confused about the difference between Azure RMS and IRM in Office?</span></span> <span data-ttu-id="8cb5f-115">Sie benötigen Hilfe zu anderen Nutzungsbedingungen für Rechteverwaltung?</span><span class="sxs-lookup"><span data-stu-id="8cb5f-115">Want help with other Rights Management terms?</span></span> <span data-ttu-id="8cb5f-116">Weitere Informationen finden Sie unter [Terminologie für Rechteverwaltung](https://technet.microsoft.com/library/dn595132.aspx).</span><span class="sxs-lookup"><span data-stu-id="8cb5f-116">See [Terminology for Rights Management](https://technet.microsoft.com/library/dn595132.aspx).</span></span>
    

