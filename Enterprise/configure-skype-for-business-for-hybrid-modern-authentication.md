---
title: Lokale hybride modernen Authentifizierung zum Konfigurieren von Skype für Unternehmen
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 6/4/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 522d5cec-4e1b-4cc3-937f-293570717bc6
description: Moderne Authentifizierung ist eine Methode über die identitätsverwaltung, die sicherere Benutzerauthentifizierung und-Autorisierung bietet, ist für Skype für Business Server lokal und Exchange Server lokal als auch Split-Domäne Skype für Business Hybriden verfügbar.
ms.openlocfilehash: 48ce10022e384ec88b88c0e8ec038bf201adc707
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541071"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a>Lokale hybride modernen Authentifizierung zum Konfigurieren von Skype für Unternehmen

Moderne Authentifizierung ist eine Methode über die identitätsverwaltung, die sicherere Benutzerauthentifizierung und-Autorisierung bietet, ist für Skype für Business Server lokal und Exchange Server lokal als auch Split-Domäne Skype für Business Hybriden verfügbar.
  
 **Wichtige** Möchten Sie wissen, Weitere Informationen zu modernen Authentifizierung (MA) und warum empfiehlt sich möglicherweise für die Verwendung in Ihrer Firma oder Organisation? [In diesem Dokument](hybrid-modern-auth-overview.md) finden Sie eine Übersicht überprüfen. Wenn Sie benötigen, welche Skype wissen für Business Topologien mit MA, unterstützt werden, die hier dokumentiert ist! 
  
 **Bevor wir beginnen**, rufen Sie: 
  
- Moderne Authentifizierung \> MA
    
- Hybride modernen Authentifizierung \> HMA
    
- Der lokale Exchange \> EXCH
    
- Exchange Online \> EXO
    
- Skype für Business lokal \> SFB
    
- und Skype für Unternehmen Online \> SFBO
    
Darüber hinaus * besitzt eine Grafik in diesem Artikel ein Objekt, das "grau" 'abgeblendet' oder hat, die bedeutet, das Element in Grau **ist nicht** enthalten in MA-spezifische Konfiguration dargestellt dass. * 
  
## <a name="read-the-summary"></a>Lesen Sie die Zusammenfassung

Diese Zusammenfassung macht den Prozess in Schritte, die möglicherweise während der Ausführung andernfalls verloren abrufen, und eignet sich für eine allgemeine Checkliste nachverfolgen, wo Sie in dem Prozess befinden.
  
1. Stellen Sie zunächst sicher, dass Sie alle erforderlichen Komponenten erfüllen.
    
1. Seit vielen **Voraussetzungen** gelten für beide Skype für Unternehmen und Exchange, [finden Sie in dem Artikel für die Bereitstellungsprüfliste Voraussetzung](hybrid-modern-auth-overview.md). Führen Sie diese *vor dem* Beginn der Schritte in diesem Artikel. 
    
2. Sammeln Sie die HMA-spezifische Informationen, die Sie in einer Datei oder OneNote benötigen.
    
3. Aktivieren Sie auf modernen Authentifizierung für EXO (sofern sie nicht bereits aktiviert ist).
    
4. Aktivieren Sie auf modernen Authentifizierung für SFBO (sofern sie nicht bereits aktiviert ist).
    
5. Moderne Hybrid-Authentifizierung für lokale Exchange-Organisation zu aktivieren.
    
6. Aktivieren der modernen Hybrid-Authentifizierung für Skype für Business lokal.
    
Hinweis: Diese Schritte MA für SFB, SFBO, EXCH und EXO – d. h., alle Produkte aktivieren, die in einer Konfiguration HMA SFB und SFBO (einschließlich Abhängigkeiten von EXCH/EXO) teilnehmen können. Anders ausgedrückt, wird, wenn die Benutzer sich in befinden / Postfächer in einem Teil des der Hybrid (EXO + SFBO, EXO + SFB, EXCH + SFBO, oder EXCH + SFB erstellten), Ihre Fertigprodukt wie folgt aussehen:
  
![Eine gemischte 6 Skype für Business HMA Topologie verfügt über Verwaltungs-Agent für alle vier mögliche Speicherorte.](media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)
  
Wie Sie, dass es gibt vier unterschiedliche Standorten sehen können auf Verwaltungs-Agent zu aktivieren. Die beste benutzerumgebung wird empfohlen, dass Sie in diesen Speicherorten alle vier-Verwaltungs-Agent zu aktivieren. Wenn Sie MA in alle Speicherorte einschalten ist nicht möglich, passen Sie die Schritte aus, damit Sie nur in den Speicherorten-Verwaltungs-Agent zu aktivieren, die für Ihre Umgebung erforderlich sind.
  
Finden Sie im [Thema Skype für Unternehmen mit MA Supportability](https://technet.microsoft.com/en-us/library/mt803262.aspx) für unterstützte Topologien. 
  
 **Wichtige** Überprüfen Sie, dass Sie alle erforderlichen Komponenten erfüllt, bevor Sie beginnen. Diese Informationen finden Sie [hier](hybrid-modern-auth-overview.md).
  
## <a name="collect-all-hma-specific-info-youll-need"></a>Sammeln Sie alle HMA-spezifische Informationen, die Sie benötigen

Nachdem Sie, die sich vergewissert haben Sie erfüllen modernen-Authentifizierung verwenden, um die [erforderlichen Komponenten](hybrid-modern-auth-overview.md) (siehe Hinweis oben), erstellen Sie eine Datei, um die Informationen zum Konfigurieren von HMA in den folgenden Schritten müssen halten. Die Beispiele in diesem Artikel verwendet: 
  
- **SIP/SMTP-Domäne**
    
  - Z. B. "contoso.com" (wird mit Office 365 Verbund)
    
- **Mandanten-ID**
    
  - Die GUID, die Ihre Office 365-Mandanten (bei der Anmeldung von contoso.onmicrosoft.com) darstellt.
    
- **SFB 2015 CU5 Webdienst-URLs**
    
Sie benötigen des internen und externen Webdienst-URL für alle SfB 2015 Pools bereitgestellt. Um diese zu erhalten, führen Sie den folgenden von Skype für Business-Verwaltungsshell aus:
  
Get-CsService - WebServer | Select-Object PoolFqdn, InternalFqdn, Externerfqdn | FL
  
- Interne z. B.:https://lyncwebint01.contoso.com
    
- Kurs extern:https://lyncwebext01.contoso.com
    
Wenn Sie einen Standard Edition-Server verwenden, wird die interne URL leer sein. In diesem Fall verwenden Sie den Pool-Fqdn für die interne URL.
  
## <a name="turn-on-modern-authentication-for-exo"></a>Aktivieren der modernen Authentifizierung für EXO

Befolgen Sie die Anweisungen hier: [Exchange Online: zum Aktivieren des Mandanten für moderne Authentifizierung von.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)
  
## <a name="turn-on-modern-authentication-for-sfbo"></a>Aktivieren der modernen Authentifizierung für SFBO

Befolgen Sie die Anweisungen hier: [Skype für Business Online: Aktivieren Ihres Mandanten für die Authentifizierung modernen](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).
  
## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a>Aktivieren der Hybrid modernen Authentifizierung für Exchange lokal

Befolgen Sie die Anweisungen hier: [Exchange Server lokal Hybrid modernen-Authentifizierung konfigurieren](configure-exchange-server-for-hybrid-modern-authentication.md).
  
## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a>Aktivieren Sie für Business lokal modernen Hybrid-Authentifizierung für Skype

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a>Hinzufügen von lokalen web Service URLs als Dienstprinzipalnamen (SPNs) in Azure AD

Jetzt müssen Sie Befehle ausführen, um die URLs (zuvor gesammelten) als Dienstprinzipale in SFBO hinzufügen.
  
 **Hinweis** Service Dienstprinzipalnamen (SPNs) Identifizieren von Webdiensten und zuordnen, ein Sicherheitsprinzipal (beispielsweise ein Kontonamen oder eine Gruppe), damit der Dienst auf den Namen eines autorisierten Benutzers übernehmen kann. Clients authentifiziert sich gegenüber einem Server stellen Informationen, die in enthaltenen Dienstprinzipalnamen (SPNs) verwenden. 
  
1. Schließen Sie zuerst AAD mit [diese Anweisungen](https://docs.microsoft.com/en-us/powershell/azure/active-directory/install-adv2?view=azureadps-2.0).
    
2. Führen Sie diesen Befehl lokal, um eine Liste der Webdienst-URLs SFB abzurufen.
    
  - Get-MsolServicePrincipal - AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Select - ExpandProperty ServicePrincipalNames
    
    Beachten Sie, dass die AppPrincipalId mit "00000004" beginnt. Dies entspricht Skype für Business Online.
    
    Nehmen Sie notieren (und Screenshot für den späteren Vergleich) die Ausgabe dieses Befehls wird ein SE und WS-URL enthalten bestehen hauptsächlich aus Dienstprinzipalnamen (SPNs), die mit 00000004-0000-0ff1-ce00-000000000000 beginnen /.
    
3. Wenn die interne **oder** externe URLs aus lokalen SFB nicht vorhanden sind (beispielsweise https://lyncwebint01.contoso.com und https://lyncwebext01.contoso.com) werden muss, die bestimmte Datensätze zu dieser Liste hinzufügen. 
    
    Achten Sie darauf, dass *die Beispiel-URLs* , unten, durch den tatsächlichen URLs in die Befehle zum Hinzufügen ersetzen! 
    
  - $x = Get-MsolServicePrincipal - AppPrincipalId 00000004-0000-0ff1-ce00-000000000000
    
  - $x.ServicePrincipalnames.Add (" *https://lyncwebint01.contoso.com/* ") 
    
  - $x.ServicePrincipalnames.Add (" *https://lyncwebext01.contoso.com/* ") 
    
  - Set-MSOLServicePrincipal - AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 - ServicePrincipalNames $x.ServicePrincipalNames
    
4. Stellen Sie sicher, dass Ihre neue Datensätze hinzugefügt wurden, mithilfe des Befehls Get-MsolServicePrincipal aus Schritt 2 erneut aus, und Durchsuchen Sie die Ausgabe. Vergleichen Sie die Liste / Screenshot vor der neuen Liste der Dienstprinzipalnamen (SPNs) (können Sie auch die neue Liste Screenshot für Ihre Unterlagen). Wenn Sie erfolgreich waren, sehen Sie die beiden neuen URLs in der Liste. Wechseln von unserem Beispiel, die Liste der SPNs wird enthalten nun die bestimmte URLs https://lyncweb01.contoso.com und https://autodiscover.contoso.com.
    
### <a name="create-the-evosts-auth-server-object"></a>Erstellen Sie das EvoSTS Auth-Server-Objekt

Führen Sie den folgenden Befehl in der Skype für Business-Verwaltungsshell.
  
- "New-csoauthserver"-Identity EvoSTS - Metadaten-URL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml - AcceptSecurityIdentifierInformation $true-Typ AzureAD
    
### <a name="enable-hybrid-modern-authentication"></a>Aktivieren der modernen Hybrid-Authentifizierung

Dies ist der Schritt, der tatsächlich MA wird aktiviert. Die oben beschriebenen Schritte können vorausschauendes ausgeführt werden, ohne den Ablauf der Client-Authentifizierung. Wenn Sie den authentifizierungsfluss ändern möchten, führen Sie diesen Befehl in der Skype für Business-Verwaltungsshell. 
  
- "Set-csoauthconfiguration" - ClientAuthorizationOAuthServerIdentity evoSTS
    
## <a name="verify"></a>„Bestätigen“,

Nachdem Sie HMA aktivieren, wird nächsten Anmeldung des Clients den neuen Auth Fluss verwenden. Beachten Sie, dass auf HMA einschalten eine erneute Authentifizierung für Clients ausgelöst werden nicht. Die Clients erneut authentifizieren basierend auf der Lebensdauer des Auth Token und/oder der Zertifikate, die sie besitzen.
  
Um zu testen, dass HMA funktionsfähig ist, nachdem Sie es aktiviert haben, melden Sie sich einen Test SFB Windows-Client, und klicken Sie auf 'Meine Anmeldeinformationen löschen'. Melden Sie sich erneut an. Der Client sollte jetzt den modernen Auth Ablauf verwenden und Ihren Benutzernamen enthalten ein **Office 365** -Aufforderung nun für eine "Arbeit"oder"Schule" Konto gesehen rechts, bevor der Client den Server kontaktiert und meldet an. 
  
Sie sollten auch die Konfigurationsinformationen für Skype für Business-Clients für eine "OAuth Behörde" überprüfen. Hierzu auf dem Clientcomputer halten Sie die STRG-Taste gedrückt, zur selben Zeit, die Sie der Skype Business Symbol in der Windows-Taskleiste mit der rechten Maustaste. Klicken Sie im angezeigten Menü auf Konfigurationsinformationen. Suchen Sie im Fenster "Skype für Konfigurationsinformationen Business", das auf dem Desktop angezeigt wird, für die folgenden:
  
![Die Konfigurationsinformationen für einen Skype für Business Client mithilfe der modernen Authentifizierung zeigt eine Lync und EWS OAUTH Autorität URL der https://login.windows.net/common/oauth2/authorize.](media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png)
  
Sie sollten auch halten Sie die STRG-Taste zur selben Zeit Sie rechten Maustaste auf das Symbol für den Outlook-Client (auch in der Benachrichtigungen über die Windows-Taskleiste) klicken, und klicken Sie auf 'Verbindungsstatus'. Suchen Sie nach der Client-SMTP-Adresse gegen eine Authn Art von ' Bearer\*', darstellt, das Bearer Token in OAuth verwendet.
  
## <a name="related-articles"></a>Verwandte Artikel

[Verknüpfung zu der modernen Authentifizierung (Übersicht)](hybrid-modern-auth-overview.md) . 
  
Müssen Sie wissen, wie Sie modernen Authentifizierung (ADAL) für Ihre Skype für Business Clients verwenden? Wir haben die Schritte [hier](https://technet.microsoft.com/en-us/library/mt710548.aspx).
  
Möchten Sie um diese Schritte zu lesen, wenn sie für Exchange Server angezeigt werden, lokalen, ohne SFB ausgeführt? Diese Schritte sind hier verfügbar.
  

