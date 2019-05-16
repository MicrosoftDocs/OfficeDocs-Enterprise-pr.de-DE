---
title: Lokale Konfiguration von Skype for Business derart, dass die moderne Hybridauthentifizierung verwendet wird
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 6/4/2018
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 522d5cec-4e1b-4cc3-937f-293570717bc6
ms.collection:
- M365-security-compliance
description: Die moderne Authentifizierung ist eine Methode zur Identitätsverwaltung, die eine höhere Sicherheit bei der Benutzerauthentifizierung und-Autorisierung bietet, sowohl für lokale Server-als auch Exchange-Server vor Ort sowie für Skype for Business-Hybriden mit geteilter Domäne verfügbar ist.
ms.openlocfilehash: a6f1b64aade9cd7c2fa5b44e18e1075008676f90
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067991"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a>Lokale Konfiguration von Skype for Business derart, dass die moderne Hybridauthentifizierung verwendet wird

Die moderne Authentifizierung ist eine Methode zur Identitätsverwaltung, die eine höhere Sicherheit bei der Benutzerauthentifizierung und-Autorisierung bietet, sowohl für lokale Server-als auch Exchange-Server vor Ort sowie für Skype for Business-Hybriden mit geteilter Domäne verfügbar ist.
  
 **Wichtig** Möchten Sie mehr über die moderne Authentifizierung (MA) erfahren und warum Sie Sie lieber in Ihrem Unternehmen oder Ihrer Organisation verwenden können? In [diesem Dokument](hybrid-modern-auth-overview.md) finden Sie eine Übersicht. Wenn Sie wissen möchten, welche Skype for Business-Topologien mit MA unterstützt werden, ist dies hier dokumentiert. 
  
 **Bevor wir beginnen**, rufe ich an: 
  
- Moderne Authentifizierungs \> -MA
    
- Moderne Hybrid Authentifizierung \> HMA
    
- Exchange lokal \> Austausch
    
- Exchange Online \> Exo
    
- Skype for Business- \> SFB
    
- und Skype for Business Online \> -SFBO
    
* Wenn eine Grafik in diesem Artikel ein Objekt hat, das ' abgeblendet ' oder ' abgeblendet ' ist, bedeutet dies, dass das in grau gezeigte Element **nicht** in der MA-spezifischen Konfiguration enthalten ist. * 
  
## <a name="read-the-summary"></a>Zusammenfassung lesen

In dieser Zusammenfassung wird der Vorgang in Schritte umgesetzt, die sonst während der Ausführung verloren gehen können, und es ist gut für eine allgemeine Checkliste, um zu verfolgen, wo Sie sich gerade befinden.
  
1. Stellen Sie zuerst sicher, dass alle Voraussetzungen erfüllt sind.
    
1. Da viele **voraus** setzungen sowohl für Skype for Business als auch für Exchange gelten, [Lesen Sie den Artikelübersicht für Ihre vorab](hybrid-modern-auth-overview.md)Anforderungsliste. Führen Sie diese Schritte aus, *bevor* Sie mit den Schritten in diesem Artikel beginnen. 
    
2. Sammeln Sie die HMA-spezifischen Informationen, die Sie in einer Datei benötigen, oder OneNote.
    
3. Aktivieren Sie die moderne Authentifizierung für Exo (falls nicht bereits aktiviert).
    
4. Aktivieren Sie die moderne Authentifizierung für SFBO (falls Sie noch nicht aktiviert ist).
    
5. Aktivieren Sie die moderne Hybrid Authentifizierung für Exchange lokal.
    
6. Aktivieren Sie die moderne Hybrid Authentifizierung für Skype for Business lokal.
    
Hinweis Diese Schritte aktivieren Sie MA für SFB, SFBO, Wechsel und Exo--also alle Produkte, die an einer HMA-Konfiguration von SFB und SFBO teilnehmen können (einschließlich Abhängigkeiten von Wechsel/Exo). Anders ausgedrückt: Wenn Ihre Benutzer in einem beliebigen Teil des Hybrids erstellt/Postfächer haben (Exo + SFBO, Exo + SFB, SFBO oder-SFB), sieht Ihr fertiges Produkt wie folgt aus.
  
![In einer gemischten 6-HMA-Topologie mit Skype for Business ist Ma an allen vier möglichen Standorten an.](media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)
  
Wie Sie sehen können, gibt es vier verschiedene Stellen, um MA zu aktivieren. Für die beste Benutzererfahrung empfehlen wir, dass Sie an allen vier Standorten MA aktivieren. Wenn Sie Ma an allen Standorten nicht aktivieren können, passen Sie die Schritte so an, dass Sie MA nur an den für Ihre Umgebung erforderlichen Speicherorten aktivieren.
  
Weitere Informationen finden Sie im [Thema zur Unterstützung von Skype for Business mit MA](https://technet.microsoft.com/en-us/library/mt803262.aspx) für unterstützte Topologien. 
  
 **Wichtig** Überprüfen Sie, ob alle Voraussetzungen erfüllt sind, bevor Sie beginnen. Diese Informationen finden Sie [hier](hybrid-modern-auth-overview.md).
  
## <a name="collect-all-hma-specific-info-youll-need"></a>Sammeln aller HMA Informationen, die Sie benötigen

Nachdem Sie überprüft haben, dass Sie die [voraus](hybrid-modern-auth-overview.md) setzungen für die Verwendung der modernen Authentifizierung erfüllt haben (siehe den Hinweis oben), sollten Sie eine Datei erstellen, in der die Informationen enthalten sind, die Sie für die Konfiguration von HMA benötigen. Beispiele in diesem Artikel: 
  
- **SIP/SMTP-Domäne**
    
  - Ex. contoso.com (ist Verbund mit Office 365)
    
- **Mandanten-ID**
    
  - Die GUID, die Ihren Office 365-Mandanten darstellt (bei der Anmeldung von contoso.onmicrosoft.com).
    
- **SFB 2015 CU5-Webdienst-URLs**
    
Sie benötigen interne und externe Webdienst-URLs für alle SFB 2015-Pools, die bereitgestellt werden. Führen Sie die folgenden Schritte aus der Skype for Business-Verwaltungsshell aus, um diese zu erhalten:
  
```
Get-CsService -WebServer | Select-Object PoolFqdn, InternalFqdn, ExternalFqdn | FL
```

- Ex. Internehttps://lyncwebint01.contoso.com
    
- Ex. Externenhttps://lyncwebext01.contoso.com
    
Wenn Sie einen Standard Edition-Server verwenden, ist die interne URL leer. Verwenden Sie in diesem Fall den Pool-FQDN für die interne URL.
  
## <a name="turn-on-modern-authentication-for-exo"></a>Aktivieren der modernen Authentifizierung für Exo

Befolgen Sie die Anweisungen hier: [Exchange Online: Aktivieren des Mandanten für die moderne Authentifizierung.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)
  
## <a name="turn-on-modern-authentication-for-sfbo"></a>Aktivieren der modernen Authentifizierung für SFBO

Befolgen Sie die Anweisungen hier: [Skype for Business Online: Aktivieren Sie Ihren Mandanten für die moderne Authentifizierung](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).
  
## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a>Aktivieren der modernen Hybrid Authentifizierung für Exchange lokal

Befolgen Sie die Anweisungen hier: [Konfigurieren von Exchange Server für die Verwendung der modernen Hybrid Authentifizierung](configure-exchange-server-for-hybrid-modern-authentication.md).
  
## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a>Aktivieren der modernen Hybrid Authentifizierung für Skype for Business lokal

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a>Hinzufügen von lokalen Webdienst-URLs als SPNs in Azure AD

Nun müssen Sie Befehle ausführen, um die zuvor gesammelten URLs als Dienst Prinzipale in SFBO hinzuzufügen.
  
 **Hinweis** Dienstprinzipalnamen (SPNs) identifizieren Webdienste und ordnen Sie einem Sicherheitsprinzipal (beispielsweise einem Kontonamen oder einer Gruppe) zu, damit der Dienst im Auftrag eines autorisierten Benutzers agieren kann. Clients, die sich auf einem Server authentifizieren, verwenden Informationen, die in SPNs enthalten sind. 
  
1. Stellen Sie zunächst eine Verbindung mit Aad her, um [diese Anweisungen](https://docs.microsoft.com/en-us/powershell/azure/active-directory/overview?view=azureadps-1.0)zu erhalten.
    
2. Führen Sie diesen Befehl aus, um eine Liste der SFB-Webdienst-URLs abzurufen.

   Beachten Sie, dass die AppPrincipalId `00000004`mit beginnt. Dies entspricht Skype for Business Online.
    
   Notieren Sie sich (und Screenshot für den späteren Vergleich) die Ausgabe dieses Befehls, der eine SE-und eine WS-URL enthält, aber meistens aus SPNs `00000004-0000-0ff1-ce00-000000000000/`besteht, die mit beginnen.
    
```
Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Select -ExpandProperty ServicePrincipalNames
```
    
3. Wenn die internen **oder** externen SFB-URLs von lokal fehlen (beispielsweise, https://lyncwebint01.contoso.com und https://lyncwebext01.contoso.com) wir müssen diese Datensätze dieser Liste hinzufügen. 
    
    Stellen Sie sicher, dass Sie *die Beispiel-URLs* unten durch ihre tatsächlichen URLs in den Add-Befehlen ersetzen. 
  
```  
$x= Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000
$x.ServicePrincipalnames.Add("https://lyncwebint01.contoso.com/")
$x.ServicePrincipalnames.Add("https://lyncwebext01.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
  
4. Überprüfen Sie, ob Ihre neuen Datensätze hinzugefügt wurden, indem Sie den Befehl Get-MsolServicePrincipal erneut aus Schritt 2 ausführen und die Ausgabe durchsuchen. Vergleichen Sie die Liste/den Screenshot von before mit der neuen Liste der SPNs (Sie können auch die neue Liste für Ihre Einträge Screenshot). Wenn Sie erfolgreich waren, werden die beiden neuen URLs in der Liste angezeigt. In diesem Beispiel enthält die Liste der SPNs nun die spezifischen URLs https://lyncweb01.contoso.com und. https://lyncwebext01.contoso.com/
    
### <a name="create-the-evosts-auth-server-object"></a>Erstellen des EvoSTS-Auth-Server Objekts

Führen Sie den folgenden Befehl in der Skype for Business-Verwaltungsshell aus.
  
```
New-CsOAuthServer -Identity evoSTS -MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml -AcceptSecurityIdentifierInformation $true -Type AzureAD
```
    
### <a name="enable-hybrid-modern-authentication"></a>Aktivieren der modernen Hybrid Authentifizierung

Dies ist der Schritt, der MA aktiviert. Alle vorherigen Schritte können vorzeitig ausgeführt werden, ohne den Client Authentifizierungsablauf zu ändern. Wenn Sie den Authentifizierungs Fluss ändern möchten, führen Sie diesen Befehl in der Skype for Business-Verwaltungsshell aus. 
  
```
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity evoSTS
```
    
## <a name="verify"></a>Prüfen

Nachdem Sie HMA aktiviert haben, wird der neue Authentifizierungsablauf von der nächsten Anmeldung des Clients verwendet. Beachten Sie, dass durch das Aktivieren von HMA keine erneute Authentifizierung für einen Client ausgelöst wird. Die Clients authentifizieren sich basierend auf der Lebensdauer der auth-Token und/oder certs, die Sie besitzen.
  
Um zu testen, ob HMA funktioniert, nachdem Sie es aktiviert haben, melden Sie sich bei einem Test-SFB-Windows-Client ab, und klicken Sie auf "Meine Anmeldeinformationen löschen". Melden Sie sich erneut an. Der Client sollte jetzt den modernen Authentifizierungsablauf verwenden, und Ihre Anmeldung enthält jetzt eine **Office 365** -Ansage für ein Konto für "Arbeit oder Schule", direkt bevor der Client den Server kontaktiert und Sie einloggt. 
  
Sie sollten auch die Konfigurationsinformationen für Skype for Business-Clients für eine "OAuth Authority" überprüfen. Halten Sie dazu auf dem Clientcomputer die STRG-Taste gedrückt, und klicken Sie dann mit der rechten Maustaste auf das Skype for Business-Symbol in der Windows-Benachrichtigungsleiste. Klicken Sie im angezeigten Menü auf Konfigurationsinformationen. Suchen Sie im Fenster "Skype for Business-Konfigurationsinformationen", das auf dem Desktop angezeigt wird, nach folgendem:
  
![Die Konfigurationsinformationen eines Skype for Business-Clients mit moderner Authentifizierung zeigen eine lync-und EWS-OAUTH- https://login.windows.net/common/oauth2/authorizeAutoritäts-URL von.](media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png)
  
Sie sollten auch die STRG-Taste gleichzeitig gedrückt halten, indem Sie mit der rechten Maustaste auf das Symbol für den Outlook-Client (auch im Windows-Benachrichtigungs Fach) klicken und dann auf "Verbindungs Status" klicken. Suchen Sie nach der SMTP-Adresse des Clients gegen einen authn-Typ von\*"Bearer", der das in OAuth verwendete Bearer-Token darstellt.
  
## <a name="related-articles"></a>Verwandte Artikel

[Link zurück zur Übersicht über die moderne Authentifizierung](hybrid-modern-auth-overview.md) . 
  
Müssen Sie wissen, wie Sie die moderne Authentifizierung (Adal) für Ihre Skype for Business-Clients verwenden? Wir haben [hier](https://technet.microsoft.com/en-us/library/mt710548.aspx)Schritte.
  
Möchten Sie diese Schritte lesen, wenn Sie für Exchange Server, lokal und ohne SFB ausgeführt werden? Diese Schritte stehen hier zur Verfügung.
  

