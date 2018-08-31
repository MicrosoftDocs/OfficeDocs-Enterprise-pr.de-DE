---
title: Entfernen oder Deaktivieren der modernen Hybrid-Authentifizierung von Skype für Unternehmen und Exchange
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
ms.openlocfilehash: fff9599641630386183ab9e1a0b8f597f0ba6e5b
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540963"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a>Entfernen oder Deaktivieren der modernen Hybrid-Authentifizierung von Skype für Unternehmen und Exchange

Wenn Sie Hybrid modernen Authentifizierung (HMA) und feststellen, dass sie nicht für Ihre aktuelle Umgebung geeignet ist aktiviert haben, können Sie HMA deaktivieren. In diesem Artikel wird erläutert, wie.
  
## <a name="who-is-this-article-for"></a>Wer ist für die in diesem Artikel?

Wenn Sie haben modernen Authentifizierung in Skype für Business Online oder lokal, und/oder Exchange Online oder lokalen aktiviert und festgestellt, dass Sie HMA deaktivieren müssen, sind diese Schritte für Sie.
  
 **Wichtige** Finden Sie im Artikel " [Skype für Business Topologien mit modernen Authentifizierung unterstützt](https://technet.microsoft.com/en-us/library/mt803262.aspx)", wenn Sie in Skype für Business Online oder lokalen befinden, haben Sie eine gemischte Topologie HMA und unterstützten Topologien betrachten, bevor Sie beginnen müssen.
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a>Zum Deaktivieren des modernen Hybrid-Authentifizierung (Exchange)

1. **Lokale Exchange - Organisation**: Öffnen Sie die Exchange-Verwaltungsshell, und führen Sie den folgenden Befehl aus. 
    
1. Set-OrganizationConfig-OAuth2ClientProfileEnabled $false
    
2. Set-AuthServer-Identity EvoSTS - IsDefaultAuthorizationEndpoint $false
    
2. **Exchange Online**: Verbindung mit Exchange Online mit Remote-PowerShell. Führen Sie den folgenden Befehl aus, um das Flag *OAuth2ClientProfileEnabled* auf "False" zu aktivieren. 
    
1. Set-OrganizationConfig-OAuth2ClientProfileEnabled: $false
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a>Zum Deaktivieren des modernen Hybrid-Authentifizierung (Skype für Unternehmen)

1. **Skype für Business lokal**: führen die folgenden Befehle in Skype für Business-Verwaltungsshell.
    
1. "Set-csoauthconfiguration" - ClientAuthorizationOAuthServerIdentity ""
    
2. **Skype für Unternehmen Online**: Verbinden mit Skype für Unternehmen Online mit Remote-PowerShell. Führen Sie den folgenden Befehl zum Deaktivieren der modernen Authentifizierung. 
    
1. "Set-csoauthconfiguration" - ClientAdalAuthOverride nicht zulässig
    
[Verknüpfung zu der modernen Authentifizierung (Übersicht)](hybrid-modern-auth-overview.md) . 
  

