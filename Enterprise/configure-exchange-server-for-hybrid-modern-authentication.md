---
title: Lokale hybride modernen Authentifizierung zum Konfigurieren von Exchange Server
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 3/23/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: cef3044d-d4cb-4586-8e82-ee97bd3b14ad
description: 'Hybride modernen Authentifizierung (HMA), ist eine Methode über die identitätsverwaltung, die bietet sicherere Benutzerauthentifizierung und-Autorisierung und für hybridbereitstellungen in Exchange Server: lokal verfügbar ist.'
ms.openlocfilehash: 871f03b8e776c694f7378f6905259d21516f7326
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540875"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a>Lokale hybride modernen Authentifizierung zum Konfigurieren von Exchange Server

Hybride modernen Authentifizierung (HMA), ist eine Methode über die identitätsverwaltung, die bietet sicherere Benutzerauthentifizierung und-Autorisierung und für hybridbereitstellungen in Exchange Server: lokal verfügbar ist.
  
## <a name="fyi"></a>FYI

Bevor wir beginnen, rufen Sie:
  
- Hybride modernen Authentifizierung \> HMA
    
- Der lokale Exchange \> EXCH
    
- Exchange Online \> EXO
    
Auch *Wenn eine Grafik in diesem Artikel ein Objekt hat, ist "grau" oder "abgeblendet", bedeutet dies, dass das Element grau dargestellt in HMA-spezifische Konfiguration nicht enthalten ist* . 
  
## <a name="enabling-hybrid-modern-authentication"></a>Aktivieren der modernen Hybrid-Authentifizierung

Aktivieren der HMA bedeutet:
  
1. Wird sicher, dass Sie die Prereqs erfüllen, bevor Sie beginnen.
    
1. Seit vielen **Voraussetzungen** gelten für beide Skype für Unternehmen und Exchange, [moderne Hybrid-Authentifizierung (Übersicht) und Voraussetzungen für die Verwendung mit lokalen Skype für Geschäfts- und Exchange Server](hybrid-modern-auth-overview.md). Hierzu, bevor Sie die Schritte in diesem Artikel beginnen.
    
2. Hinzufügen von lokalen Webdienst-URLs als Dienstprinzipalnamen (SPNs) in Azure Active Directory.
    
3. Sicherstellen, dass alle virtuellen Verzeichnisse für HMA aktiviert sind
    
4. Überprüfen für das Objekt EvoSTS Authentifizierungsserver
    
5. Aktivieren der HMA in Wechselkurs
    
 **Hinweis** Unterstützt Ihre Version von Office MA? Finden Sie unter [wie modernen Funktionsweise der Authentifizierung für apps für Office 2013 und Office 2016 Client](modern-auth-for-office-2013-and-2016.md).
  
## <a name="make-sure-you-meet-all-the-pre-reqs"></a>Stellen Sie sicher, dass Sie alle die Pre-Reqs erfüllen

Da viele erforderliche Komponenten für beide Skype für Unternehmen und Exchange ausgeführt werden, prüfen Sie [modernen Hybrid-Authentifizierung (Übersicht) und erforderliche Komponenten für die Verwendung mit lokalen Skype für Geschäfts- und Exchange Server](hybrid-modern-auth-overview.md). Führen Sie diese *vor dem* Beginn der Schritte in diesem Artikel. 
  
## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a>Hinzufügen von lokalen web Service URLs als Dienstprinzipalnamen (SPNs) in Azure AD

Führen Sie die Befehle, die Ihre lokalen Web Service URLs zuweisen, wie Azure AD SPNs. Dienstprinzipalnamen (SPNs) während der Authentifizierung und Autorisierung von Clientcomputer und Geräte verwendet werden. Alle URLs, die verwendet werden können, von lokalen Azure Active Directory (AAD) herstellen müssen im AAD registriert werden (dazu gehören interne und externe Namespaces).
  
Sammeln Sie zuerst die URLs, die Sie benötigen, um in AAD hinzuzufügen. Diese Befehle: lokal ausführen:
  
- Get-MapiVirtualDirectory | FL-Server\*Url\*
    
- Get-WebServicesVirtualDirectory | FL-Server\*Url\*
    
- **Get-ActiveSyncVirtualDirectory | FL-Server\*Url\***
    
- Get-OABVirtualDirectory | FL-Server\*Url\*
    
Vergewissern Sie sich die URLs Clients eine Verbindung herstellen können, als HTTPS Dienstprinzipalnamen in AAD aufgeführt sind.
  
1. Schließen Sie zuerst AAD mit [diese Anweisungen](https://docs.microsoft.com/en-us/office365/enterprise/powershell/connect-to-office-365-powershell).
    
2. Geben den folgenden Befehl, für die Exchange-verwandter URLs:
    
- Get-MsolServicePrincipal - AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | Wählen Sie - ExpandProperty ServicePrincipalNames
    
Notieren Sie (und Screenshot für den späteren Vergleich) die Ausgabe dieses Befehls, der ein https:// enthalten sollte dauern * AutoErmittlung. *Ihre Domäne* .com * und https:// *Mail* -URL, aber bestehen hauptsächlich aus Dienstprinzipalnamen (SPNs), die mit 00000002-0000-0ff1-ce00-000000000000 beginnen /. Wenn https:// URLs aus dem lokalen, die fehlen vorhanden sind, müssen wir die bestimmte Datensätze zu dieser Liste hinzufügen. 
  
3. Wenn Sie Ihre interne und externe MAPI/HTTP, EWS, ActiveSync, OAB und AutoErmittlung-Einträge in dieser Liste nicht angezeigt wird, müssen Sie sie über den unten angegebenen Befehl hinzufügen (im Beispiel URLs sind '`mail.corp.contoso.com`'und'`owa.contoso.com`', aber **die Beispiel-URLs durch Ihren eigenen ersetzen** ) : </br>
```
- $x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000   
- $x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
- $x.ServicePrincipalnames.Add("https://owa.contoso.com/")
- $x.ServicePrincipalnames.Add("https://eas.contoso.com/")
- Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
 
4. Stellen Sie sicher, dass Ihre neue Datensätze hinzugefügt wurden, mithilfe des Befehls Get-MsolServicePrincipal aus Schritt 2 erneut aus, und Durchsuchen Sie die Ausgabe. Vergleichen Sie die Liste / Screenshot vor der neuen Liste der Dienstprinzipalnamen (SPNs) (können Sie auch die neue Liste Screenshot für Ihre Unterlagen). Wenn Sie erfolgreich waren, sehen Sie die beiden neuen URLs in der Liste. Wechseln von unserem Beispiel, die Liste der SPNs wird enthalten nun die bestimmte URLs `https://mail.corp.contoso.com` und `https://owa.contoso.com`. 
  
## <a name="verify-virtual-directories-are-properly-configured"></a>Überprüfen Sie, ob die virtuellen Verzeichnisse ordnungsgemäß konfiguriert sind.

Vergewissern Sie sich jetzt OAuth ordnungsgemäß aktiviert ist, Exchange auf allen virtuellen Verzeichnisse Outlook möglicherweise verwenden, indem Sie die folgenden Befehle ausführen:

```
Get-MapiVirtualDirectory | FL server,\*url\*,\*auth\* 
Get-WebServicesVirtualDirectory | FL server,\*url\*,\*oauth\*
Get-OABVirtualDirectory | FL server,\*url\*,\*oauth\*
Get-AutoDiscoverVirtualDirectory | FL server,\*oauth\*
```

Die Ausgabe, stellen Sie sicher, dass **OAuth** Kontrollkästchen aktiviert ist auf jedem dieser VDirs, sieht etwa wie folgt (und unbedingt betrachten "OAuth"); 
  
 **[PS] C:\Windows\System32\>Get-MapiVirtualDirectory | fl-Server\*Url\*,\*Auth\***
  
 **Server: EX1**
  
 **InternalUrl:`https://mail.contoso.com/mapi`**
  
 **ExternalUrl:`https://mail.contoso.com/mapi`**
  
 **IISAuthenticationMethods: {Ntlm, OAuth, aushandeln}**
  
 **InternalAuthenticationMethods: {Ntlm, OAuth, aushandeln}**
  
 **ExternalAuthenticationMethods: {Ntlm, OAuth, aushandeln}**
  
Wenn OAuth aus einem beliebigen Server und vier virtuelle Verzeichnisse fehlt, müssen Sie es über die relevanten Befehle vor dem Fortfahren hinzufügen.
  
## <a name="confirm-the-evosts-auth-server-object-is-present"></a>Vergewissern Sie sich, dass das Objekt EvoSTS Auth Server vorhanden ist

Geben Sie an der lokalen Exchange-Verwaltungsshell für diesen letzten Befehl. Jetzt können Sie überprüfen, ob Ihre lokale enthält einen Eintrag für den EvoSTS Authentifizierungsanbieter:
  
`Get-AuthServer | where {$_.Name -eq "EvoSts"}`
    
Die Ausgabe sollte ein AuthServer, der den Namen EvoSts anzeigen und der Status "Aktiviert" muss auf True festgelegt sein. Wenn dies nicht angezeigt wird, sollten Sie herunterladen und Ausführen die neueste Version von the Hybrid Configuration Wizard.
  
 **Wichtige** Wenn Sie Exchange 2010 in Ihrer Umgebung ausführen, werden nicht EvoSTS Authentifizierungsanbieter erstellt werden. 
  
## <a name="enable-hma"></a>HMA aktivieren

Führen Sie den folgenden Befehl in der Exchange-Verwaltungsshell: lokal aus:

```
Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true  
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```
    
## <a name="verify"></a>„Bestätigen“,

Nachdem Sie HMA aktivieren, wird nächsten Anmeldung des Clients den neuen Auth Fluss verwenden. Beachten Sie, dass auf HMA einschalten eine erneute Authentifizierung für Clients ausgelöst werden nicht. Die Clients erneut authentifizieren basierend auf der Lebensdauer des Auth Token und/oder der Zertifikate, die sie besitzen.
  
Sie sollten auch halten Sie die STRG-Taste zur selben Zeit Sie rechten Maustaste auf das Symbol für den Outlook-Client (auch in der Benachrichtigungen über die Windows-Taskleiste) klicken, und klicken Sie auf 'Verbindungsstatus'. Suchen Sie nach der Client-SMTP-Adresse gegen vom Typ 'Authn' von ' Bearer\*', darstellt, das Bearer Token in OAuth verwendet.
  
 **Hinweis** So konfigurieren Sie Skype für Unternehmen mit HMA erforderlich? Benötigen Sie zwei Artikel: eine, die Listen der [unterstützten Topologien](https://technet.microsoft.com/en-us/library/mt803262.aspx)und eine, die Sie zeigt, [wie Sie die Konfiguration vornehmen](configure-skype-for-business-for-hybrid-modern-authentication.md).
  

## <a name="related-topics"></a>Verwandte Themen

[Hybride modernen Authentifizierung (Übersicht) und Voraussetzungen für die Verwendung mit lokalen Skype für Geschäfts- und Exchange Server](hybrid-modern-auth-overview.md) 
  

