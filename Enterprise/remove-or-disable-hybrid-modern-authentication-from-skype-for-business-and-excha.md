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
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a>Entfernen oder Deaktivieren der modernen Hybridauthentifizierung aus Skype for Business und Exchange

Wenn Sie Hybrid modernen Authentifizierung (HMA) und feststellen, dass sie nicht für Ihre aktuelle Umgebung geeignet ist aktiviert haben, können Sie HMA deaktivieren. In diesem Artikel wird erläutert, wie.
  
## <a name="who-is-this-article-for"></a>Wer ist für die in diesem Artikel?

Wenn Sie haben modernen Authentifizierung in Skype für Business Online oder lokal, und/oder Exchange Online oder lokalen aktiviert und festgestellt, dass Sie HMA deaktivieren müssen, sind diese Schritte für Sie.

> [!IMPORTANT]
> Finden Sie im Artikel "[Skype für Business Topologien mit modernen Authentifizierung unterstützt](https://technet.microsoft.com/en-us/library/mt803262.aspx)", wenn Sie in Skype für Business Online oder lokalen befinden, haben Sie eine gemischte Topologie HMA und unterstützten Topologien betrachten, bevor Sie beginnen müssen.
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a>Zum Deaktivieren des modernen Hybrid-Authentifizierung (Exchange)

1. **Lokale Exchange - Organisation**: Öffnen Sie die Exchange-Verwaltungsshell, und führen Sie die folgenden Befehle aus: 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. **Exchange Online**: [Verbindung mit Exchange Online](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) mit Remote-PowerShell. Führen Sie den folgenden Befehl aus, um das Flag *OAuth2ClientProfileEnabled* auf "False" zu aktivieren:

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a>Zum Deaktivieren des modernen Hybrid-Authentifizierung (Skype für Unternehmen)

1. **Skype für Business lokal**: führen die folgenden Befehle in Skype für Business-Verwaltungsshell:

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. **Skype für Unternehmen Online**: [Verbinden mit Skype für Unternehmen Online](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) mit Remote-PowerShell. Führen Sie den folgenden Befehl zum Deaktivieren der modernen Authentifizierung:

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

[Verknüpfung zu der modernen Authentifizierung (Übersicht)](hybrid-modern-auth-overview.md) . 
  

