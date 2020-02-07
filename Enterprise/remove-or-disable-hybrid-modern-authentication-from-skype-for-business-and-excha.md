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
f1.keywords:
- NOCSH
description: Wenn Sie die hybride moderne Authentifizierung (HMA) aktiviert haben, um zu ermitteln, ob Sie für Ihre aktuelle Umgebung ungeeignet ist, können Sie HMA deaktivieren. In diesem Artikel wird erläutert, wie.
ms.openlocfilehash: 27d6616d1323c310129010a782b30da020258f1b
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844066"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a>Entfernen oder Deaktivieren der modernen Hybridauthentifizierung aus Skype for Business und Exchange

*Dieser Artikel gilt sowohl für Office 365 Enterprise als auch Microsoft 365 Enterprise*.

Wenn Sie die hybride moderne Authentifizierung (HMA) aktiviert haben, um zu ermitteln, ob Sie für Ihre aktuelle Umgebung ungeeignet ist, können Sie HMA deaktivieren. In diesem Artikel wird erläutert, wie.
  
## <a name="who-is-this-article-for"></a>An wen richtet sich dieser Artikel?

Wenn Sie die moderne Authentifizierung in Skype for Business Online oder lokal und/oder Exchange Online oder lokal aktiviert haben und festgestellt haben, dass Sie HMA deaktivieren müssen, sind diese Schritte für Sie erforderlich.

> [!IMPORTANT]
> Lesen Sie den Artikel "[Skype for Business Topologien mit moderner Authentifizierung unterstützt](https://technet.microsoft.com/library/mt803262.aspx)", wenn Sie sich in Skype for Business Online oder lokal befinden, eine HMA mit gemischten Topologien haben und unterstützte Topologien suchen müssen, bevor Sie beginnen.
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a>Deaktivieren der modernen Hybrid Authentifizierung (Exchange)

1. **Exchange lokal**: Öffnen Sie das Exchange-Verwaltungsshell, und führen Sie die folgenden Befehle aus: 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. **Exchange Online**: [Verbinden mit Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) mit Remote-PowerShell. Führen Sie den folgenden Befehl aus, um die *OAuth2ClientProfileEnabled* -Kennzeichnung auf "false" zu verwandeln:

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a>Deaktivieren der modernen Hybrid Authentifizierung (Skype for Business)

1. **Skype for Business lokal**: führen Sie die folgenden Befehle in Skype for Business-Verwaltungsshell aus:

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. **Skype for Business Online**: [Verbinden mit Skype for Business Online](https://docs.microsoft.com/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) mit Remote-PowerShell. Führen Sie den folgenden Befehl aus, um die moderne Authentifizierung zu deaktivieren:

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

[Link zurück zur modernen Authentifizierung (Übersicht](hybrid-modern-auth-overview.md) ). 
  

