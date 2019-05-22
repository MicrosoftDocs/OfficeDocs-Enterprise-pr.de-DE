---
title: Lokale Konfiguration von Exchange Server derart, dass die moderne Hybridauthentifizierung verwendet wird
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 11/16/2018
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: cef3044d-d4cb-4586-8e82-ee97bd3b14ad
ms.collection:
- M365-security-compliance
description: Die hybride moderne Authentifizierung (HMA) ist eine Methode zur Identitätsverwaltung, die eine sicherere Benutzerauthentifizierung und-Autorisierung bietet und für lokale Exchange Server-hybridbereitstellungen verfügbar ist.
ms.openlocfilehash: c86d794d0952faf59a724976fa2a180084646baa
ms.sourcegitcommit: ffa5c7a2d0e1eaa40b84ea1e9fb6992d1f05aa86
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/21/2019
ms.locfileid: "34332622"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a>Lokale Konfiguration von Exchange Server derart, dass die moderne Hybridauthentifizierung verwendet wird

Die hybride moderne Authentifizierung (HMA) ist eine Methode zur Identitätsverwaltung, die eine sicherere Benutzerauthentifizierung und-Autorisierung bietet und für lokale Exchange Server-hybridbereitstellungen verfügbar ist.
  
## <a name="fyi"></a>FYI

Bevor wir beginnen, rufe ich Folgendes auf:
  
- Hybride moderne \> Authentifizierung HMA
    
- Lokaler \> Exchange-Austausch
    
- Exchange Online \> Exo
    
*Wenn eine Grafik in diesem Artikel ein Objekt enthält, das "abgeblendet" oder "abgeblendet" ist, bedeutet das, dass das in Grau dargestellte Element nicht in HMA-spezifischer Konfiguration enthalten ist* . 
  
## <a name="enabling-hybrid-modern-authentication"></a>Aktivieren der modernen Hybrid Authentifizierung

HMA aktivieren bedeutet:
  
1. Sicherstellen, dass Sie die Voraussetzungen erfüllen, bevor Sie beginnen.
    
1. Da viele **voraus** setzungen sowohl für Skype for Business als auch für Exchange, die [hybride moderne Authentifizierungs Übersicht und die Voraussetzungen für die Verwendung mit lokalen Skype for Business-und Exchange-Servern](hybrid-modern-auth-overview.md)gemeinsam sind. Tun Sie dies, bevor Sie einen der Schritte in diesem Artikel beginnen.
    
2. Hinzufügen von lokalen Webdienst-URLs als Dienstprinzipalnamen (Service Principal Names, SPNs) in Azure AD.
    
3. Sicherstellen, dass alle virtuellen Verzeichnisse für HMA aktiviert sind
    
4. Überprüfen des EvoSTS-Authentifizierungs Server Objekts
    
5. Aktivieren von HMA in "interaktives".
    
 **Hinweis:** Unterstützt Ihre Office-Version MA? Erfahren Sie [, wie die moderne Authentifizierung für Office 2013-und Office 2016-Client-apps funktioniert](modern-auth-for-office-2013-and-2016.md).
  
## <a name="make-sure-you-meet-all-the-pre-reqs"></a>Stellen Sie sicher, dass Sie alle Pre-reqs erfüllen.

Da viele Voraussetzungen sowohl für Skype for Business als auch für Exchange gelten, überprüfen Sie die Übersicht über die [moderne Hybrid Authentifizierung und die Voraussetzungen für die Verwendung mit lokalen Skype for Business-und Exchange-Servern](hybrid-modern-auth-overview.md). Tun Sie dies, *bevor* Sie einen der Schritte in diesem Artikel beginnen. 
  
## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a>Hinzufügen von lokalen Webdienst-URLs als SPNs in Azure AD

Führen Sie die Befehle aus, die ihre lokalen Webdienst-URLs als Azure AD SPNs zuweisen. SPNs werden von Clientcomputern und-Geräten während der Authentifizierung und Autorisierung verwendet. Alle URLs, die zum Herstellen einer Verbindung zwischen lokalen und Azure-Active Directory (AAD) verwendet werden können, müssen in Aad registriert sein (Dies umfasst sowohl interne als auch externe Namespaces).
  
Sammeln Sie zunächst alle URLs, die Sie in Aad hinzufügen müssen. Führen Sie diese Befehle lokal aus:
  
```powershell
Get-MapiVirtualDirectory | FL server,*url*
Get-WebServicesVirtualDirectory | FL server,*url*
Get-ActiveSyncVirtualDirectory | FL server,*url*
Get-OABVirtualDirectory | FL server,*url*
```
    
Stellen Sie sicher, dass die URLs, mit denen Clients eine Verbindung herstellen können, als HTTPS-Dienstprinzipalnamen in Aad aufgeführt werden.
  
1. Stellen Sie zuerst eine Verbindung mit Aad mit [diesen Anweisungen](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell)her. 

 **Hinweis:** Sie müssen die Option Connect-MsolService von dieser Seite verwenden, um den folgenden Befehl verwenden zu können. 
    
2. Geben Sie für Ihre Exchange-bezogenen URLs den folgenden Befehl ein:
    
```powershell
Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | select -ExpandProperty ServicePrincipalNames
```

Notieren Sie sich (und Screenshot für einen späteren Vergleich) die Ausgabe dieses Befehls, die eine https:// *autodiscover.yourdomain.com* -und https://- *Mail.yourdomain.com* -URL enthalten sollte, aber meistens aus SPNs besteht, die mit beginnen 00000002-0000-0ff1-ce00-000000000000/. Wenn es https://-URLs von Ihrem Lokal gibt, die fehlen, müssen Sie diese spezifischen Einträge zu dieser Liste hinzufügen. 
  
3. Wenn Ihre internen und externen MAPI/http-, EWS-, ActiveSync-, OAB-und autodiscover-Datensätze in dieser Liste nicht angezeigt werden, müssen Sie Sie mithilfe des folgenden Befehls`mail.corp.contoso.com`hinzufügen (`owa.contoso.com`die Beispiel-URLs sind ' ' und ' ', aber Sie **ersetzen die Beispiel-URLs durch eigene** ) : <br/>
```powershell
$x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000   
$x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
$x.ServicePrincipalnames.Add("https://owa.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
 
4. Stellen Sie sicher, dass Ihre neuen Datensätze hinzugefügt wurden, indem Sie den Befehl Get-MsolServicePrincipal aus Schritt 2 erneut ausführen und die Ausgabe durchsuchen. Vergleichen Sie die Liste/Screenshot von vor mit der neuen Liste von SPNs (Sie können auch die neue Liste für Ihre Datensätze Screenshot). Wenn Sie erfolgreich waren, werden die beiden neuen URLs in der Liste angezeigt. In unserem Beispiel enthält die Liste der SPNs nun die spezifischen URLs `https://mail.corp.contoso.com` und. `https://owa.contoso.com` 
  
## <a name="verify-virtual-directories-are-properly-configured"></a>Überprüfen der ordnungsgemäßen Konfiguration virtueller Verzeichnisse

Überprüfen Sie nun, ob OAuth in Exchange in allen virtuellen Verzeichnissen, die Outlook möglicherweise verwendet, ordnungsgemäß aktiviert ist, indem Sie die folgenden Befehle ausführen:

```powershell
Get-MapiVirtualDirectory | FL server,*url*,*auth* 
Get-WebServicesVirtualDirectory | FL server,*url*,*oauth*
Get-OABVirtualDirectory | FL server,*url*,*oauth*
Get-AutoDiscoverVirtualDirectory | FL server,*oauth*
```

Überprüfen Sie die Ausgabe, um sicherzustellen, dass **OAuth** auf jedem dieser VDirs aktiviert ist, es sieht in etwa wie folgt aus (und der wichtigste Aspekt ist "OAuth"); 

```powershell
Get-MapiVirtualDirectory | fl server,*url*,*auth*
```

```
Server                        : EX1
InternalUrl                   : https://mail.contoso.com/mapi
ExternalUrl                   : https://mail.contoso.com/mapi
IISAuthenticationMethods      : {Ntlm, OAuth, Negotiate}
InternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
ExternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
```
  
Wenn OAuth auf einem beliebigen Server und einem der vier virtuellen Verzeichnisse fehlt, müssen Sie es mithilfe der entsprechenden Befehle hinzufügen, bevor Sie fortfahren.
  
## <a name="confirm-the-evosts-auth-server-object-is-present"></a>Bestätigen, dass das EvoSTS-Authentifizierungs Server Objekt vorhanden ist

Kehren Sie zu dem lokalen Exchange-Verwaltungsshell für diesen letzten Befehl zurück. Jetzt können Sie überprüfen, ob Ihr lokal über einen Eintrag für den evoSTS-Authentifizierungsanbieter verfügt:
  
```powershell
Get-AuthServer | where {$_.Name -eq "EvoSts"}
```

Ihre Ausgabe sollte eine AuthServer des Namens EvoSts und der Status "Enabled" sollte true aufweisen. Wenn dies nicht angezeigt wird, sollten Sie die neueste Version des Assistenten für die Hybrid Konfiguration herunterladen und ausführen.
  
 **Wichtiger Hinweis** Wenn Sie Exchange 2010 in Ihrer Umgebung durchführen, wird der EvoSTS-Authentifizierungsanbieter nicht erstellt. 
  
## <a name="enable-hma"></a>HMA aktivieren

Führen Sie den folgenden Befehl in der lokalen Exchange-Verwaltungsshell aus:

```powershell
Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true  
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```
    
## <a name="verify"></a>Überprüfen

Nachdem Sie HMA aktiviert haben, verwendet die nächste Anmeldung eines Clients den neuen auth-Fluss. Beachten Sie, dass durch das Aktivieren von HMA keine erneute Authentifizierung für einen beliebigen Client ausgelöst wird. Die Clients authentifizieren sich erneut basierend auf der Lebensdauer der Authentifizierungstoken und/oder certs, die Sie besitzen.
  
Sie sollten auch die STRG-Taste gleichzeitig gedrückt halten, indem Sie mit der rechten Maustaste auf das Symbol für den Outlook-Client (auch im Windows-Benachrichtigungs Fach) klicken und auf "Verbindungs Status" klicken. Suchen Sie die SMTP-Adresse des Clients anhand eines "authn"-Typs von "\*Bearer", der das in OAuth verwendete Bearer-Token darstellt.
  
 **Hinweis:** Sie müssen Skype for Business mit HMA konfigurieren? Sie benötigen zwei Artikel: eine, die [Unterstützte Topologien](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)auflistet, und eine, die zeigt, [wie Sie die Konfiguration durchführen](configure-skype-for-business-for-hybrid-modern-authentication.md).
  

## <a name="related-topics"></a>Verwandte Themen

[Übersicht über die moderne Hybrid Authentifizierung und Voraussetzungen für die Verwendung mit lokalen Skype for Business und Exchange-Servern](hybrid-modern-auth-overview.md) 
  

