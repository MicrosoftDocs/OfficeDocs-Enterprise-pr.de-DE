---
title: Entfernen oder Deaktivieren der modernen Hybridauthentifizierung aus Skype for Business und Exchange
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
description: Wenn Sie Hybrid modernen Authentifizierung (HMA) und feststellen, dass sie nicht für Ihre aktuelle Umgebung geeignet ist aktiviert haben, können Sie HMA deaktivieren. In diesem Artikel wird erläutert, wie.
ms.openlocfilehash: 802add6295edffe3ec80e70e9bd70663479ec61a
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "25359027"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a><span data-ttu-id="0523c-104">Entfernen oder Deaktivieren der modernen Hybridauthentifizierung aus Skype for Business und Exchange</span><span class="sxs-lookup"><span data-stu-id="0523c-104">Removing or disabling Hybrid Modern Authentication from Skype for Business and Exchange</span></span>

<span data-ttu-id="0523c-p102">Wenn Sie Hybrid modernen Authentifizierung (HMA) und feststellen, dass sie nicht für Ihre aktuelle Umgebung geeignet ist aktiviert haben, können Sie HMA deaktivieren. In diesem Artikel wird erläutert, wie.</span><span class="sxs-lookup"><span data-stu-id="0523c-p102">If you've enabled Hybrid Modern Authentication (HMA) only to find it's unsuitable for your current environment, you can disable HMA. This article explains how.</span></span>
  
## <a name="who-is-this-article-for"></a><span data-ttu-id="0523c-107">Wer ist für die in diesem Artikel?</span><span class="sxs-lookup"><span data-stu-id="0523c-107">Who is this article for?</span></span>

<span data-ttu-id="0523c-108">Wenn Sie haben modernen Authentifizierung in Skype für Business Online oder lokal, und/oder Exchange Online oder lokalen aktiviert und festgestellt, dass Sie HMA deaktivieren müssen, sind diese Schritte für Sie.</span><span class="sxs-lookup"><span data-stu-id="0523c-108">If you've enabled Modern Authentication in Skype for Business Online or On-premises, and/or Exchange Online or On-premises and found you need to disable HMA, these steps are for you.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0523c-109">Finden Sie im Artikel "[Skype für Business Topologien mit modernen Authentifizierung unterstützt](https://technet.microsoft.com/en-us/library/mt803262.aspx)", wenn Sie in Skype für Business Online oder lokalen befinden, haben Sie eine gemischte Topologie HMA und unterstützten Topologien betrachten, bevor Sie beginnen müssen.</span><span class="sxs-lookup"><span data-stu-id="0523c-109">See the '[Skype for Business topologies supported with Modern Authentication](https://technet.microsoft.com/en-us/library/mt803262.aspx)' article if you're in Skype for Business Online or On-premises, have a mixed-topology HMA, and need to look at supported topologies before you begin.</span></span>
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a><span data-ttu-id="0523c-110">Zum Deaktivieren des modernen Hybrid-Authentifizierung (Exchange)</span><span class="sxs-lookup"><span data-stu-id="0523c-110">How to disable Hybrid Modern Authentication (Exchange)</span></span>

1. <span data-ttu-id="0523c-111">**Lokale Exchange - Organisation**: Öffnen Sie die Exchange-Verwaltungsshell, und führen Sie die folgenden Befehle aus:</span><span class="sxs-lookup"><span data-stu-id="0523c-111">**Exchange On-premises**: Open the Exchange Management Shell and run the following commands:</span></span> 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. <span data-ttu-id="0523c-p103">**Exchange Online**: [Verbindung mit Exchange Online](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) mit Remote-PowerShell. Führen Sie den folgenden Befehl aus, um das Flag *OAuth2ClientProfileEnabled* auf "False" zu aktivieren:</span><span class="sxs-lookup"><span data-stu-id="0523c-p103">**Exchange Online**: [Connect to Exchange Online](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) with Remote PowerShell. Run the following command to turn your  *OAuth2ClientProfileEnabled*  flag to 'false':</span></span>

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a><span data-ttu-id="0523c-114">Zum Deaktivieren des modernen Hybrid-Authentifizierung (Skype für Unternehmen)</span><span class="sxs-lookup"><span data-stu-id="0523c-114">How to disable Hybrid Modern Authentication (Skype for Business)</span></span>

1. <span data-ttu-id="0523c-115">**Skype für Business lokal**: führen die folgenden Befehle in Skype für Business-Verwaltungsshell:</span><span class="sxs-lookup"><span data-stu-id="0523c-115">**Skype for Business On-premises**: Run the following commands in Skype for Business Management Shell:</span></span>

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. <span data-ttu-id="0523c-p104">**Skype für Unternehmen Online**: [Verbinden mit Skype für Unternehmen Online](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) mit Remote-PowerShell. Führen Sie den folgenden Befehl zum Deaktivieren der modernen Authentifizierung:</span><span class="sxs-lookup"><span data-stu-id="0523c-p104">**Skype for Business Online**: [Connect to Skype for Business Online](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) with Remote PowerShell. Run the following command to disable Modern Authentication:</span></span>

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

<span data-ttu-id="0523c-118">[Verknüpfung zu der modernen Authentifizierung (Übersicht)](hybrid-modern-auth-overview.md) .</span><span class="sxs-lookup"><span data-stu-id="0523c-118">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  

