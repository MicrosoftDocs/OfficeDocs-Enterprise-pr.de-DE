---
title: Entfernen oder Deaktivieren der modernen Hybridauthentifizierung aus Skype for Business und Exchange
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/3/2017
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 5a91b9e3-1508-475b-93e0-710fa5d5cd2d
ms.collection:
- M365-security-compliance
description: Wenn Sie die hybride moderne Authentifizierung (HMA) aktiviert haben, um zu ermitteln, ob Sie für Ihre aktuelle Umgebung ungeeignet ist, können Sie HMA deaktivieren. In diesem Artikel wird erläutert, wie.
ms.openlocfilehash: 91373adf590ad9a69880de20897795ced23d98b8
ms.sourcegitcommit: c8acfa57a22d7d055500f2e8b84a9ef252c70e82
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2019
ms.locfileid: "36493322"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a><span data-ttu-id="26e40-104">Entfernen oder Deaktivieren der modernen Hybridauthentifizierung aus Skype for Business und Exchange</span><span class="sxs-lookup"><span data-stu-id="26e40-104">Removing or disabling Hybrid Modern Authentication from Skype for Business and Exchange</span></span>

<span data-ttu-id="26e40-105">Wenn Sie die hybride moderne Authentifizierung (HMA) aktiviert haben, um zu ermitteln, ob Sie für Ihre aktuelle Umgebung ungeeignet ist, können Sie HMA deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="26e40-105">If you've enabled Hybrid Modern Authentication (HMA) only to find it's unsuitable for your current environment, you can disable HMA.</span></span> <span data-ttu-id="26e40-106">In diesem Artikel wird erläutert, wie.</span><span class="sxs-lookup"><span data-stu-id="26e40-106">This article explains how.</span></span>
  
## <a name="who-is-this-article-for"></a><span data-ttu-id="26e40-107">An wen richtet sich dieser Artikel?</span><span class="sxs-lookup"><span data-stu-id="26e40-107">Who is this article for?</span></span>

<span data-ttu-id="26e40-108">Wenn Sie die moderne Authentifizierung in Skype for Business Online oder lokal und/oder Exchange Online oder lokal aktiviert haben und festgestellt haben, dass Sie HMA deaktivieren müssen, sind diese Schritte für Sie erforderlich.</span><span class="sxs-lookup"><span data-stu-id="26e40-108">If you've enabled Modern Authentication in Skype for Business Online or On-premises, and/or Exchange Online or On-premises and found you need to disable HMA, these steps are for you.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="26e40-109">Lesen Sie den Artikel "[Skype for Business Topologien mit moderner Authentifizierung unterstützt](https://technet.microsoft.com/en-us/library/mt803262.aspx)", wenn Sie sich in Skype for Business Online oder lokal befinden, eine HMA mit gemischten Topologien haben und unterstützte Topologien suchen müssen, bevor Sie beginnen.</span><span class="sxs-lookup"><span data-stu-id="26e40-109">See the '[Skype for Business topologies supported with Modern Authentication](https://technet.microsoft.com/en-us/library/mt803262.aspx)' article if you're in Skype for Business Online or On-premises, have a mixed-topology HMA, and need to look at supported topologies before you begin.</span></span>
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a><span data-ttu-id="26e40-110">Deaktivieren der modernen Hybrid Authentifizierung (Exchange)</span><span class="sxs-lookup"><span data-stu-id="26e40-110">How to disable Hybrid Modern Authentication (Exchange)</span></span>

1. <span data-ttu-id="26e40-111">**Exchange lokal**: Öffnen Sie das Exchange-Verwaltungsshell, und führen Sie die folgenden Befehle aus:</span><span class="sxs-lookup"><span data-stu-id="26e40-111">**Exchange On-premises**: Open the Exchange Management Shell and run the following commands:</span></span> 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. <span data-ttu-id="26e40-112">**Exchange Online**: [Verbinden mit Exchange Online](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) mit Remote-PowerShell.</span><span class="sxs-lookup"><span data-stu-id="26e40-112">**Exchange Online**: [Connect to Exchange Online](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) with Remote PowerShell.</span></span> <span data-ttu-id="26e40-113">Führen Sie den folgenden Befehl aus, um die *OAuth2ClientProfileEnabled* -Kennzeichnung auf "false" zu verwandeln:</span><span class="sxs-lookup"><span data-stu-id="26e40-113">Run the following command to turn your  *OAuth2ClientProfileEnabled*  flag to 'false':</span></span>

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a><span data-ttu-id="26e40-114">Deaktivieren der modernen Hybrid Authentifizierung (Skype for Business)</span><span class="sxs-lookup"><span data-stu-id="26e40-114">How to disable Hybrid Modern Authentication (Skype for Business)</span></span>

1. <span data-ttu-id="26e40-115">**Skype for Business lokal**: führen Sie die folgenden Befehle in Skype for Business-Verwaltungsshell aus:</span><span class="sxs-lookup"><span data-stu-id="26e40-115">**Skype for Business On-premises**: Run the following commands in Skype for Business Management Shell:</span></span>

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. <span data-ttu-id="26e40-116">**Skype for Business Online**: [Verbinden mit Skype for Business Online](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) mit Remote-PowerShell.</span><span class="sxs-lookup"><span data-stu-id="26e40-116">**Skype for Business Online**: [Connect to Skype for Business Online](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) with Remote PowerShell.</span></span> <span data-ttu-id="26e40-117">Führen Sie den folgenden Befehl aus, um die moderne Authentifizierung zu deaktivieren:</span><span class="sxs-lookup"><span data-stu-id="26e40-117">Run the following command to disable Modern Authentication:</span></span>

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

<span data-ttu-id="26e40-118">[Link zurück zur modernen Authentifizierung (Übersicht](hybrid-modern-auth-overview.md) ).</span><span class="sxs-lookup"><span data-stu-id="26e40-118">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  

