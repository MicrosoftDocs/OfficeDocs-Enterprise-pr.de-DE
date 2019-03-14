---
title: Entfernen oder Deaktivieren der modernen Hybrid Authentifizierung von Skype for Business und Exchange
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 11/3/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 5a91b9e3-1508-475b-93e0-710fa5d5cd2d
ms.collection:
- M365-security-compliance
description: Wenn Sie die moderne Hybrid Authentifizierung (HMA) aktiviert haben, um festzustellen, dass Sie nicht für Ihre aktuelle Umgebung geeignet ist, können Sie HMA deaktivieren. In diesem Artikel wird erläutert, wie.
ms.openlocfilehash: 4df044a8243bc6016f71c31d5b5cba7db901be98
ms.sourcegitcommit: 1d84e2289fc87717f8a9cd12c68ab27c84405348
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2019
ms.locfileid: "30372842"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a><span data-ttu-id="a94f8-104">Entfernen oder Deaktivieren der modernen Hybrid Authentifizierung von Skype for Business und Exchange</span><span class="sxs-lookup"><span data-stu-id="a94f8-104">Removing or disabling Hybrid Modern Authentication from Skype for Business and Exchange</span></span>

<span data-ttu-id="a94f8-105">Wenn Sie die moderne Hybrid Authentifizierung (HMA) aktiviert haben, um festzustellen, dass Sie nicht für Ihre aktuelle Umgebung geeignet ist, können Sie HMA deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="a94f8-105">If you've enabled Hybrid Modern Authentication (HMA) only to find it's unsuitable for your current environment, you can disable HMA.</span></span> <span data-ttu-id="a94f8-106">In diesem Artikel wird erläutert, wie.</span><span class="sxs-lookup"><span data-stu-id="a94f8-106">This article explains how.</span></span>
  
## <a name="who-is-this-article-for"></a><span data-ttu-id="a94f8-107">Für wen eignet sich dieser Artikel?</span><span class="sxs-lookup"><span data-stu-id="a94f8-107">Who is this article for?</span></span>

<span data-ttu-id="a94f8-108">Wenn Sie moderne Authentifizierung in Skype for Business Online oder lokal und/oder Exchange Online oder lokal aktiviert haben und festgestellt haben, dass Sie HMA deaktivieren müssen, sind diese Schritte für Sie bestimmt.</span><span class="sxs-lookup"><span data-stu-id="a94f8-108">If you've enabled Modern Authentication in Skype for Business Online or On-premises, and/or Exchange Online or On-premises and found you need to disable HMA, these steps are for you.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a94f8-109">Weitere Informationen finden Sie im Artikel "[unterstützte Skype for Business-Topologien mit moderner Authentifizierung](https://technet.microsoft.com/en-us/library/mt803262.aspx)", wenn Sie in Skype for Business Online oder lokal arbeiten, über eine HMA mit einer gemischten Topologie verfügen und sich die unterstützten Topologien ansehen müssen, bevor Sie beginnen.</span><span class="sxs-lookup"><span data-stu-id="a94f8-109">See the '[Skype for Business topologies supported with Modern Authentication](https://technet.microsoft.com/en-us/library/mt803262.aspx)' article if you're in Skype for Business Online or On-premises, have a mixed-topology HMA, and need to look at supported topologies before you begin.</span></span>
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a><span data-ttu-id="a94f8-110">Deaktivieren der modernen Hybrid Authentifizierung (Exchange)</span><span class="sxs-lookup"><span data-stu-id="a94f8-110">How to disable Hybrid Modern Authentication (Exchange)</span></span>

1. <span data-ttu-id="a94f8-111">**Exchange lokal**: Öffnen Sie die Exchange-Verwaltungsshell, und führen Sie die folgenden Befehle aus:</span><span class="sxs-lookup"><span data-stu-id="a94f8-111">**Exchange On-premises**: Open the Exchange Management Shell and run the following commands:</span></span> 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. <span data-ttu-id="a94f8-112">**Exchange Online**: [Herstellen einer Verbindung mit Exchange Online](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) mit Remote-PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a94f8-112">**Exchange Online**: [Connect to Exchange Online](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) with Remote PowerShell.</span></span> <span data-ttu-id="a94f8-113">Führen Sie den folgenden Befehl aus, um das *OAuth2ClientProfileEnabled* -Flag auf "false" zu setzen:</span><span class="sxs-lookup"><span data-stu-id="a94f8-113">Run the following command to turn your  *OAuth2ClientProfileEnabled*  flag to 'false':</span></span>

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a><span data-ttu-id="a94f8-114">Deaktivieren der modernen Hybrid Authentifizierung (Skype for Business)</span><span class="sxs-lookup"><span data-stu-id="a94f8-114">How to disable Hybrid Modern Authentication (Skype for Business)</span></span>

1. <span data-ttu-id="a94f8-115">**Skype for Business**: führen Sie die folgenden Befehle in der Skype for Business-Verwaltungsshell aus:</span><span class="sxs-lookup"><span data-stu-id="a94f8-115">**Skype for Business On-premises**: Run the following commands in Skype for Business Management Shell:</span></span>

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. <span data-ttu-id="a94f8-116">**Skype for Business Online**: [Herstellen einer Verbindung mit Skype for Business Online](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) mit Remote-PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a94f8-116">**Skype for Business Online**: [Connect to Skype for Business Online](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) with Remote PowerShell.</span></span> <span data-ttu-id="a94f8-117">Führen Sie den folgenden Befehl aus, um die moderne Authentifizierung zu deaktivieren:</span><span class="sxs-lookup"><span data-stu-id="a94f8-117">Run the following command to disable Modern Authentication:</span></span>

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

<span data-ttu-id="a94f8-118">[Link zurück zur Übersicht über die moderne Authentifizierung](hybrid-modern-auth-overview.md) .</span><span class="sxs-lookup"><span data-stu-id="a94f8-118">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  

