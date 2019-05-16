---
title: Entfernen oder Deaktivieren der modernen Hybridauthentifizierung aus Skype for Business und Exchange
ms.author: tracyp
author: MSFTTracyP
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
description: Wenn Sie die moderne Hybrid Authentifizierung (HMA) aktiviert haben, um festzustellen, dass Sie nicht für Ihre aktuelle Umgebung geeignet ist, können Sie HMA deaktivieren. In diesem Artikel wird erläutert, wie.
ms.openlocfilehash: 011e24c546fede11177e49ce8b36599d7d81d121
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070981"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a>Entfernen oder Deaktivieren der modernen Hybridauthentifizierung aus Skype for Business und Exchange

Wenn Sie die moderne Hybrid Authentifizierung (HMA) aktiviert haben, um festzustellen, dass Sie nicht für Ihre aktuelle Umgebung geeignet ist, können Sie HMA deaktivieren. In diesem Artikel wird erläutert, wie.
  
## <a name="who-is-this-article-for"></a>Für wen eignet sich dieser Artikel?

Wenn Sie moderne Authentifizierung in Skype for Business Online oder lokal und/oder Exchange Online oder lokal aktiviert haben und festgestellt haben, dass Sie HMA deaktivieren müssen, sind diese Schritte für Sie bestimmt.

> [!IMPORTANT]
> Weitere Informationen finden Sie im Artikel "[unterstützte Skype for Business-Topologien mit moderner Authentifizierung](https://technet.microsoft.com/en-us/library/mt803262.aspx)", wenn Sie in Skype for Business Online oder lokal arbeiten, über eine HMA mit einer gemischten Topologie verfügen und sich die unterstützten Topologien ansehen müssen, bevor Sie beginnen.
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a>Deaktivieren der modernen Hybrid Authentifizierung (Exchange)

1. **Exchange lokal**: Öffnen Sie die Exchange-Verwaltungsshell, und führen Sie die folgenden Befehle aus: 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. **Exchange Online**: [Herstellen einer Verbindung mit Exchange Online](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) mit Remote-PowerShell. Führen Sie den folgenden Befehl aus, um das *OAuth2ClientProfileEnabled* -Flag auf "false" zu setzen:

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a>Deaktivieren der modernen Hybrid Authentifizierung (Skype for Business)

1. **Skype for Business**: führen Sie die folgenden Befehle in der Skype for Business-Verwaltungsshell aus:

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. **Skype for Business Online**: [Herstellen einer Verbindung mit Skype for Business Online](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) mit Remote-PowerShell. Führen Sie den folgenden Befehl aus, um die moderne Authentifizierung zu deaktivieren:

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

[Link zurück zur Übersicht über die moderne Authentifizierung](hybrid-modern-auth-overview.md) . 
  

