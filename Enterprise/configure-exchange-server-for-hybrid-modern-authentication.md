---
title: Konfigurieren von Exchange Server für die Verwendung der modernen Hybrid Authentifizierung
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 11/16/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: cef3044d-d4cb-4586-8e82-ee97bd3b14ad
ms.collection:
- M365-security-compliance
description: Hybrid modern Authentication (HMA) ist eine Methode zur Identitätsverwaltung, die eine sicherere Benutzerauthentifizierung und-Autorisierung bietet und für lokale Exchange Server-hybridbereitstellungen verfügbar ist.
ms.openlocfilehash: 364f95bbbc06f477d258ed55a8711864e7a87e69
ms.sourcegitcommit: 1d84e2289fc87717f8a9cd12c68ab27c84405348
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2019
ms.locfileid: "30372862"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a>Konfigurieren von Exchange Server für die Verwendung der modernen Hybrid Authentifizierung

Hybrid modern Authentication (HMA) ist eine Methode zur Identitätsverwaltung, die eine sicherere Benutzerauthentifizierung und-Autorisierung bietet und für lokale Exchange Server-hybridbereitstellungen verfügbar ist.
  
## <a name="fyi"></a>FYI

Bevor wir beginnen, rufe ich an:
  
- Moderne Hybrid Authentifizierung \> HMA
    
- Exchange lokal \> Austausch
    
- Exchange Online \> Exo
    
*Wenn eine Grafik in diesem Artikel ein Objekt enthält, das "abgeblendet" oder "abgeblendet" ist, bedeutet dies, dass das in grau gezeigte Element nicht in der HMA-spezifischen Konfiguration enthalten ist* . 
  
## <a name="enabling-hybrid-modern-authentication"></a>Aktivieren der modernen Hybrid Authentifizierung

Turning HMA on Means:
  
1. Sicherstellen, dass Sie die PreReqs erfüllen, bevor Sie beginnen.
    
1. Da viele **voraus** setzungen sowohl für Skype for Business als auch für Exchange, die [moderne Hybrid Authentifizierungs Übersicht und die Voraussetzungen für die Verwendung mit lokalen Skype for Business-und Exchange-Servern](hybrid-modern-auth-overview.md)gelten. Führen Sie diese Schritte aus, bevor Sie mit den Schritten in diesem Artikel beginnen.
    
2. Hinzufügen von lokalen Webdienst-URLs als Dienstprinzipalnamen (SPNs) in Azure AD.
    
3. Sicherstellen, dass alle virtuellen Verzeichnisse für HMA aktiviert sind
    
4. Suchen nach dem EvoSTS-Auth-Server Objekt
    
5. Aktivieren von HMA in der über Schaltung
    
 **Hinweis** Unterstützt Ihre Office-Version MA? Erfahren Sie [, wie die moderne Authentifizierung für office 2013-und office 2016-Client-apps funktioniert](modern-auth-for-office-2013-and-2016.md).
  
## <a name="make-sure-you-meet-all-the-pre-reqs"></a>Stellen Sie sicher, dass Sie alle Prä-reqs

Da viele der Voraussetzungen sowohl für Skype for Business als auch für Exchange gelten, lesen Sie die Übersicht über die [moderne Hybrid Authentifizierung und die Voraussetzungen für die Verwendung mit lokalen Skype for Business-und Exchange-Servern](hybrid-modern-auth-overview.md). Führen Sie diese Schritte aus, *bevor* Sie mit den Schritten in diesem Artikel beginnen. 
  
## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a>Hinzufügen von lokalen Webdienst-URLs als SPNs in Azure AD

Führen Sie die Befehle aus, die ihre lokalen Webdienst-URLs als Azure AD-SPNs zuweisen. SPNs werden von Clientcomputern und-Geräten während der Authentifizierung und Autorisierung verwendet. Alle URLs, die zum Herstellen einer Verbindung von lokal zu Azure Active Directory (AAD) verwendet werden können, müssen in AAD registriert werden (Dies umfasst sowohl interne als auch externe Namespaces).
  
Sammeln Sie zunächst alle URLs, die Sie in AAD hinzufügen müssen. Führen Sie die folgenden Befehle lokal aus:
  
```powershell
Get-MapiVirtualDirectory | FL server,*url*
Get-WebServicesVirtualDirectory | FL server,*url*
Get-ActiveSyncVirtualDirectory | FL server,*url*
Get-OABVirtualDirectory | FL server,*url*
```
    
Stellen Sie sicher, dass die URLs, mit denen eine Verbindung hergestellt werden kann, als HTTPS-Dienstprinzipalnamen in AAD aufgeführt werden.
  
1. Stellen Sie zunächst eine Verbindung mit AAD her, um [diese Anweisungen](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell)zu erhalten. 

 **Hinweis** Sie müssen auf dieser Seite die Option Connect-MsolService verwenden, um den folgenden Befehl verwenden zu können. 
    
2. Geben Sie für Ihre Exchange-bezogenen URLs den folgenden Befehl ein:
    
```powershell
Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | select -ExpandProperty ServicePrincipalNames
```

Notieren Sie sich (und Screenshot für den späteren Vergleich) die Ausgabe dieses Befehls, der eine https:// *autodiscover.yourdomain.com* -und https:// *Mail.yourdomain.com* -URL enthalten sollte, aber meistens aus SPNs besteht, die mit 00000002-0000-0ff1-ce00-000000000000/. Wenn Ihre lokalen https://-URLs fehlen, müssen wir diese Datensätze dieser Liste hinzufügen. 
  
3. Wenn Ihre internen und externen MAPI/HTTP-, EWS-, ActiveSync-, OAB-und autoDiscover-Datensätze in dieser Liste nicht angezeigt werden, müssen Sie Sie mithilfe des folgenden Befehls`mail.corp.contoso.com`hinzufügen (`owa.contoso.com`die Beispiel-URLs sind ' ' und ' ', aber Sie würden **die Beispiel-URLs durch ihre eigenen ersetzen** ) : <br/>
```powershell
$x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000   
$x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
$x.ServicePrincipalnames.Add("https://owa.contoso.com/")
$x.ServicePrincipalnames.Add("https://eas.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
 
4. Überprüfen Sie, ob Ihre neuen Datensätze hinzugefügt wurden, indem Sie den Befehl Get-MsolServicePrincipal erneut aus Schritt 2 ausführen und die Ausgabe durchsuchen. Vergleichen Sie die Liste/den Screenshot von before mit der neuen Liste der SPNs (Sie können auch die neue Liste für Ihre Einträge Screenshot). Wenn Sie erfolgreich waren, werden die beiden neuen URLs in der Liste angezeigt. In diesem Beispiel enthält die Liste der SPNs nun die spezifischen URLs `https://mail.corp.contoso.com` und. `https://owa.contoso.com` 
  
## <a name="verify-virtual-directories-are-properly-configured"></a>Sicherstellen, dass virtuelle Verzeichnisse OrdnungsGemäß konfiguriert sind

Vergewissern Sie sich nun, dass OAuth in Exchange in allen virtuellen Verzeichnissen, die Outlook möglicherweise verwendet, ordnungsgemäß aktiviert ist, indem Sie die folgenden Befehle ausführen:

```powershell
Get-MapiVirtualDirectory | FL server,*url*,*auth* 
Get-WebServicesVirtualDirectory | FL server,*url*,*oauth*
Get-OABVirtualDirectory | FL server,*url*,*oauth*
Get-AutoDiscoverVirtualDirectory | FL server,*oauth*
```

Überprüfen Sie die Ausgabe, um sicherzustellen, dass **OAuth** auf jedem dieser VDirs aktiviert ist, sieht es ungefähr wie folgt aus (und das wichtigste, was Sie sehen können, ist "OAuth"); 

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
  
Wenn OAuth auf einem Server und einem der vier virtuellen Verzeichnisse fehlt, müssen Sie ihn mithilfe der entsprechenden Befehle hinzufügen, bevor Sie fortfahren.
  
## <a name="confirm-the-evosts-auth-server-object-is-present"></a>Bestätigen, dass das EvoSTS-Auth-Server Objekt vorhanden ist

Kehren Sie zur lokalen Exchange-Verwaltungsshell für diesen letzten Befehl zurück. Jetzt können Sie überprüfen, ob Ihr lokales ein Eintrag für den evoSTS-Authentifizierungsanbieter ist:
  
```powershell
Get-AuthServer | where {$_.Name -eq "EvoSts"}
```

In der Ausgabe sollte ein AuthServer des Namens EvoSts angezeigt werden, und der Status "Enabled" sollte true sein. Wenn dies nicht der Fall ist, sollten Sie die neueste Version des Assistenten für die Hybrid Konfiguration herunterladen und ausführen.
  
 **Wichtig** Wenn Sie Exchange 2010 in Ihrer Umgebung betreiben, wird der EvoSTS-Authentifizierungsanbieter nicht erstellt. 
  
## <a name="enable-hma"></a>HMA aktivieren

Führen Sie den folgenden Befehl in der Exchange-Verwaltungsshell aus:

```powershell
Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true  
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```
    
## <a name="verify"></a>Prüfen

Nachdem Sie HMA aktiviert haben, wird der neue Authentifizierungsablauf von der nächsten Anmeldung des Clients verwendet. Beachten Sie, dass durch das Aktivieren von HMA keine erneute Authentifizierung für einen Client ausgelöst wird. Die Clients authentifizieren sich basierend auf der Lebensdauer der auth-Token und/oder certs, die Sie besitzen.
  
Sie sollten auch die STRG-Taste gleichzeitig gedrückt halten, indem Sie mit der rechten Maustaste auf das Symbol für den Outlook-Client (auch im Windows-Benachrichtigungs Fach) klicken und dann auf "Verbindungs Status" klicken. Suchen Sie nach der SMTP-Adresse des Clients gegen einen "authn"-Typ von\*"Bearer", der das in OAuth verwendete Bearer-Token darstellt.
  
 **Hinweis** Müssen Sie Skype for Business mit HMA konfigurieren? Sie benötigen zwei Artikel: eine, die die [unterstützten Topologien](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)auflistet, und eine, die Ihnen zeigt, [wie Sie die Konfiguration ausführen](configure-skype-for-business-for-hybrid-modern-authentication.md).
  

## <a name="related-topics"></a>Verwandte Themen

[Übersicht über die moderne Hybrid Authentifizierung und Voraussetzungen für die Verwendung mit lokalen Skype for Business-und Exchange-Servern](hybrid-modern-auth-overview.md) 
  

