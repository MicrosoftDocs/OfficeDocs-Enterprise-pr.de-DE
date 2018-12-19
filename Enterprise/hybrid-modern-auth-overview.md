---
title: Hybride modernen Authentifizierung (Übersicht) und Voraussetzungen für die Verwendung mit lokalen Skype für Geschäfts- und Exchange Server
ms.author: tracyp
ms.reviewer: smithre4
author: MSFTTracyP
manager: laurawi
ms.date: 10/02/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.assetid: ef753b32-7251-4c9e-b442-1a5aec14e58d
description: Moderne Authentifizierung ist eine Methode über die identitätsverwaltung, die sicherere Benutzerauthentifizierung und-Autorisierung bietet. Es steht für hybridbereitstellungen von Skype für Business Server lokal und Exchange Server lokal als auch Skype für Business Hybriden Split-Domäne. Dieser Artikel enthält Links zu verwandte Dokumente zu den Voraussetzungen, Setup/Deaktivieren der modernen Authentifizierung, und einige der zugehörigen Client (z. B. Outlook und Skype-Clients) Informationen.
ms.openlocfilehash: c10e5660d43ccce50497fccfd9d830d31ac07d55
ms.sourcegitcommit: c5761d3c41aa2d26815f0d24c73dbcd53ab37957
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2018
ms.locfileid: "27371109"
---
# <a name="hybrid-modern-authentication-overview-and-prerequisites-for-using-it-with-on-premises-skype-for-business-and-exchange-servers"></a>Hybride modernen Authentifizierung (Übersicht) und Voraussetzungen für die Verwendung mit lokalen Skype für Geschäfts- und Exchange Server

Moderne Authentifizierung ist eine Methode über die identitätsverwaltung, die sicherere Benutzerauthentifizierung und-Autorisierung bietet. Es ist für Office 365-hybridbereitstellungen Skype für Business Server lokal und Exchange Server lokal als auch, geteilte Domäne Skype für Business Hybriden verfügbar. Dieser Artikel enthält Links zu verwandte Dokumente zu den Voraussetzungen, Setup/Deaktivieren der modernen Authentifizierung, und einige der zugehörigen Client (z. B. Outlook und Skype-Clients) Informationen. 
  
- [Was ist die moderne Authentifizierung?](hybrid-modern-auth-overview.md#BKMK_WhatisModAuth)
    
- [Was ändert, wenn ich modernen Authentifizierung verwenden?](hybrid-modern-auth-overview.md#BKMK_WhatChanges)
    
- [Überprüfen des Status modernen Authentifizierung Ihrer lokalen Umgebung](hybrid-modern-auth-overview.md#BKMK_CheckStatus)
    
- [Erfüllen Sie modernen Authentifizierung Anforderungen?](hybrid-modern-auth-overview.md#BKMK_MeetPrereq)
    
- [Was muss ich wissen, bevor ich beginne?](hybrid-modern-auth-overview.md#BKMK_Whatelse)
    
- [Liste der URLs modernen Authentifizierung](hybrid-modern-auth-overview.md#BKMK_URLListforMA)
    
## <a name="what-is-modern-authentication"></a>Was ist die moderne Authentifizierung?
<a name="BKMK_WhatisModAuth"> </a>

Bei der Kommunikation über die Kommunikation zwischen einem Client (z. B. Laptop oder Ihr Telefon) und einem Server, der Begriff "Modernen Authentication" von Microsoft verwendet.
  
Moderne Authentifizierung ist ein übergeordneter Begriff für eine Kombination von Authentifizierung und Autorisierungsmethoden als auch einige Sicherheitsmaßnahmen, die Zugriffsrichtlinien verwenden, denen Sie möglicherweise bereits mit vertraut. Sie enthält:
  
- **Authentifizierungsmethoden**: Multi-Factor Authentication; Client zertifikatbasierte Authentifizierung; und die Active Directory-Authentifizierung-Bibliothek ( [ADAL](https://technet.microsoft.com/en-us/library/mt710548.aspx)).
    
- **Autorisierungsmethoden**: Microsoft Implementierung der Open Authorization (OAuth). 
    
- **Bedingte Zugriffsrichtlinien**: Mobile Application Management (MAM) und Azure Active Directory bedingten Zugriff. 
    
Verwalten von Benutzeridentitäten mit modernen Authentifizierung ermöglicht Administratoren viele verschiedene Tools verwenden, wenn es darum geht, Sichern von Ressourcen und sicherere Methoden über die identitätsverwaltung für beide lokale (Exchange und Skype für Unternehmen bietet), Exchange hybrid , und Skype für Geschäftsszenarien Hybrid/Split-Domäne.
  
Beachten Sie, dass, da Skype für Unternehmen eng mit Exchange funktioniert, wird das Anmeldung Verhalten Skype für Business-Client, die Benutzern angezeigt werden durch den modernen Authentifizierung Status der Exchange vorzunehmen. Dies gilt auch wenn Sie einen Skype für Business geteilte Domäne hybride verfügen. Der Typ des für die Business-Hybridumgebung, die die Verwendung der modernen Authentifizierung unterstützt Skype wird ebenfalls häufig aufgerufen eine "Split-Domäne" (in einer geteilten-Domäne, haben Sie Skype für Business Online und Skype für Business auf Prem und Benutzer in beiden Orten befinden).
  
> [!IMPORTANT]
> Wussten Sie, dass ab August 2017 alle neue Office 365-Mandanten, die online enthalten von Skype für Unternehmen und Exchange online modernen Authentifizierung standardmäßig aktiviert haben? Vorhandene Mandanten wird keine Änderung im Standardzustand MA haben, aber alle neue Mandanten automatisch den erweiterten Satz von Identity-Features, denen Sie sehen oben aufgelisteten unterstützen. Um Ihre MA Status online für Skype für Unternehmen zu überprüfen, können Sie Skype für Business online-PowerShell mit globaler Administrator-Anmeldeinformationen verwenden. Führen Sie `Get-CsOAuthConfiguration` So überprüfen Sie die Ausgabe des - ClientADALAuthOverride. Wenn - ClientADALAuthOverride 'Ihre modernen Authentifizierung zulässig ist' ist aktiviert. 
  
## <a name="what-changes-when-i-use-modern-authentication"></a>Was ändert, wenn ich modernen Authentifizierung verwenden?
<a name="BKMK_WhatChanges"> </a>

Bei modernen Authentifizierung mit lokalen Skype für Business oder Exchange Server verwenden, Sie sind weiterhin *Authentifizieren von* Benutzern: lokal, aber die Geschichte des *Autorisieren von* deren Zugriff auf Ressourcen (wie Dateien oder -e-Mails) ändert. Dies ist deshalb, obwohl modernen Authentifizierung über die Kommunikation von Client und Server, die Schritte beim Konfigurieren der MA Ergebnis in EvoSTS (ein Sicherheitstokendienst von Azure Active Directory verwendet) ist für Skype als Authentifizierungsserver für Geschäfts- und Exchange Server lokal festgelegt. 
  
Die Änderung EvoSTS können Ihre lokale Server nutzen OAuth (tokenausstellung) für die Autorisierung Ihre Clients und kann Ihre lokalen Verwendung Sicherheitsmethoden allgemeine in der Cloud (wie Multi-Factor Authentication). Darüber hinaus gibt die EvoSTS Token, mit die Benutzer Zugriff auf Ressourcen ohne Angabe von ihr Kennwort als Teil der Anforderung anfordern können. Unabhängig davon, wo Ihre Benutzer verwaltet werden (Online oder lokale), und unabhängig davon, welche Position die erforderliche Ressourcen hostet, werden EvoSTS der Kern Autorisieren von Benutzern und Clients nach modernen-Authentifizierung konfiguriert ist.
  
Es folgt ein Beispiel der ich Bedeutung. Wenn Skype für Business-Client auf Exchange Server um Kalenderinformationen im Auftrag eines Benutzers zu erhalten Zugriff muss, wird das Active Directory Authentifizierung Library (ADAL) dazu verwendet. ADAL eine Codebibliothek dient gesicherte Ressourcen in Ihrem Verzeichnis mithilfe von Sicherheitstoken OAuth-Clientanwendungen zur Verfügung zu stellen. ADAL funktioniert mit OAuth Ansprüche überprüfen und zum Austauschen von Token (statt Kennwörter), um einem Benutzerzugriff auf eine Ressource gewähren. In der Vergangenheit die Behörde in einer Transaktion wie diesem – der Server, der weiß, wie Benutzeransprüche zu überprüfen und die erforderlichen Token ausstellen--wurden möglicherweise ein Sicherheitstokendienst lokaler oder sogar Active Directory Federation Services. Allerdings zentralisiert modernen Authentifizierung Behörde mit Azure Active Directory (AD Azure) in der Cloud.
  
Dies bedeutet auch, die, obwohl Exchange Server- und Skype für Geschäftsbereichen vollständig möglicherweise lokale, werden der autorisieren Server online und Ihrer lokalen Umgebung benötigen die Möglichkeit zum Erstellen und Verwalten einer Verbindungs mit Ihrem Büro 365-Abonnement in der Cloud (und die Azure Active Directory-Instanz, die Ihr Abonnement als Verzeichnis verwendet).
  
Was wird nicht geändert? Ob Sie sich in einer hybriden Split-Domäne oder Skype für Geschäfts- und Exchange Server lokal befinden, müssen alle Benutzer zunächst *lokale* authentifizieren. Zeigen in einer Hybrid-Implementierung der Authentifizierung modernen Lyncdiscovery und Autodiscovery auf Ihrem lokalen Server. 
  
> [!IMPORTANT]
> Wenn Sie die spezifischen Skype für Business Topologien mit MA wissen müssen, ist [hier rechts dokumentiert](https://technet.microsoft.com/en-us/library/mt803262.aspx).
  
## <a name="check-the-modern-authentication-status-of-your-on-premises-environment"></a>Überprüfen des Status modernen Authentifizierung Ihrer lokalen Umgebung
<a name="BKMK_CheckStatus"> </a>

Da moderne Authentifizierung den autorisierungsserver verwendet ändert, wenn Services OAuth/S2S nutzen, müssen Sie wissen, ob modernen Authentifizierung für Ihre Skype für Geschäfts- und Exchange-Umgebung aktiviert oder deaktiviert ist. Sie können den Status auf Ihrem Exchange oder Skype für geschäftliche Server lokal, überprüfen, durch Ausführen der `Get-CSOAuthConfiguration` in PowerShell Command. Wenn der Befehl eine leere 'OAuthServers'-Eigenschaft zurückgegeben wird, ist moderne Authentifizierung deaktiviert.
  
## <a name="do-you-meet-modern-authentication-prerequisites"></a>Erfüllen Sie modernen Authentifizierung Anforderungen?

Vergewissern Sie sich, und überprüfen Sie diese Elemente aus der Liste aus, bevor Sie fortfahren:
  
- **Skype für bestimmte Business**
    
  - Alle Server benötigen SFB Server 2015 CU5 oder höher
    
  - **Ausnahme** - Ausfallsicherheit Branch Appliance (SBA) kann auf die aktuelle Version (basierend auf dem Lync 2013) 
    
  - Die SIP-Domäne wird als Federated Domäne in Office 365 hinzugefügt.
    
  - Alle SFB Front-Ends für das Internet zu Office 365-Authentifizierung URLs (TCP 443) ausgehende Verbindungen benötigen und bekannten Zertifikatsstamm CRLs (TCP 80) in Zeilen 56 und 125 des Abschnitts "Microsoft 365 allgemeine und Office Online" [aufgelistet, Office 365-URLs und IP- Adressbereiche](urls-and-ip-address-ranges.md).
    
 **Hinweis** Wenn Ihre Skype für geschäftliche Front-End-Server einen Proxyserver für den Internetzugriff verwenden, muss die verwendete Proxy-Server-IP-Adresse und Port Nummer im Konfigurationsabschnitt der Datei web.config für jeden Front-End eingegeben werden. 
  
- C:\Programme\Microsoft Files\Skype für Business Server 2015\Web Components\Web ticket\int\web.config
    
- C:\Programme\Microsoft Files\Skype für Business Server 2015\Web Components\Web ticket\ext\web.config
    
```xml
<system.identityModel.services>
  <system.net>
    <defaultProxy>
      <proxy
        proxyaddress="http://192.168.100.60:8080"
        bypassonlocal="true" />
    </defaultProxy>
  </system.net>
</system.identityModel.services>
```
    
> [!IMPORTANT]
> Achten Sie darauf, um den RSS-feed für [Office 365-URLs und IP-Adressbereiche](urls-and-ip-address-ranges.md) , mit den neuesten Listen der erforderlichen URLs auf dem Laufenden zu abonnieren. 
  
- **Exchange Server bestimmte**
    
  - Verwenden Sie entweder Exchange Server 2013 CU19 und nach-oben, oder Exchange Server 2016 CU8 und nach oben.
    
  - Es ist kein Exchange Server 2010 in der Umgebung aus.
    
  - SSL-Verschiebung ist nicht konfiguriert. SSL-Beendigung und erneute Verschlüsselung wird unterstützt.
    
  - In Ihrer Umgebung eine Proxy-Server-Infrastruktur, damit Server zum Internet herstellen dürfen nutzt, der Ereignisprozedur werden Sie sicher, dass alle Exchange-Server den Proxy-Server in der [InternetWebProxy](https://technet.microsoft.com/en-us/library/bb123716%28v=exchg.160%29.aspx) -Eigenschaft definiert ist.
    
- **Anforderungen an Exchange-Client und Protokoll**
  
  - Die folgenden Clients unterstützen moderne Authentifizierung:

  |**Clients**|**Primäre Protokoll**|**Hinweise**|
  |:-----|:-----|:-----|
  |Outlook 2013 und Outlook 2016  <br/> |MAPI über HTTP  <br/> |MAPI über HTTP muss innerhalb von Exchange aktiviert sein, damit modernen Authentifizierung mit dieser Clients (in der Regel aktiviert oder "true" für neue Installationen von Exchange 2013 Service Pack 1 und höher); verwenden können. Weitere Informationen finden Sie unter [wie modernen Funktionsweise der Authentifizierung für apps für Office 2013 und Office 2016 Client](https://docs.microsoft.com/en-us/office365/enterprise/modern-auth-for-office-2013-and-2016).  <br/> Stellen Sie sicher, dass Sie den mindestens erforderlichen Build von Outlook ausgeführt werden; finden Sie die [neuesten Updates für Versionen von Outlook, die Windows Installer (MSI) verwenden](https://docs.microsoft.com/en-us/officeupdates/outlook-updates-msi).  <br/> |
  |Outlook 2016 für Mac  <br/> |Exchange-Webdienste  <br/> |  <br/> |
  |Outlook für iOS und Android  <br/> |  <br/> |Weitere Informationen finden Sie unter [Using Hybrid modernen Authentifizierung mit Outlook für iOS und Android](https://docs.microsoft.com/en-us/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) .  <br/> |
  |Exchange ActiveSync-Clients (z. B. iOS11 Mail)  <br/> |Exchange ActiveSync  <br/> |Für Exchange ActiveSync-Clients, moderne-Authentifizierung unterstützen, müssen Sie das Profil, um wechseln von Standardauthentifizierung zur modernen Authentifizierung erstellen.  <br/> |

- **Allgemeine erforderliche Komponenten**
    
  - Wenn Sie AD FS verwenden, müssen Sie Windows 2012 R2 AD FS 3.0 und höher für den Verbund
    
  - Ihre Identität Konfigurationen werden die Typen von AAD verbinden unterstützt (z. B. Hash kennwortsynchronisierung, Pass-Through-Authentifizierung, unterstützt von Office 365 STS lokal, et cetera.)
    
  - Sie haben AAD verbinden, konfiguriert und für Benutzerreplikation und Synchronisierung funktioniert.
    
  - Sie haben sichergestellt, dass diese Hybrid zwischen Ihrer lokalen und Office 365 funktioniert:
    
  - Offizielle Unterstützung für Anweisung für Exchange Hybrid besagt, dass Sie aktuelle CU oder aktuellen CU - 1 sein müssen.
    
  - Stellen Sie sicher, dass beide eines Testbenutzers: lokal als auch eines Testbenutzers Hybrid in Office 365 verwaltet können sich anmelden, der Skype für Business desktop Client (sofern Sie modernen Authentifizierung mit Skype verwenden möchten) und Microsoft Outlook (falls Sie also mit modernen Authentifizierung verwenden möchten Exchange).
    
## <a name="what-else-do-i-need-to-know-before-i-begin"></a>Was muss ich wissen, bevor ich beginne?
<a name="BKMK_Whatelse"> </a>

1. Alle Szenarien für lokale Server umfassen einrichten modernen Authentifizierung lokale (tatsächlich für Skype für Unternehmen gibt es eine Liste der unterstützte Topologien ist), sodass der Server für die Authentifizierung und Autorisierung befindet sich in der Microsoft-Cloud ( AAD des Sicherheitstokendienst, "EvoSTS" bezeichnet), und Aktualisieren von Azure Active Directory (AAD) über die URLs oder von Ihrer lokalen Installation von entweder Skype für Geschäftskunden und Exchange verwendeten Namespaces. Aus diesem Grund übernehmen lokalen Servern eine Microsoft-Cloud-Abhängigkeit. Durch diese Aktion konnte konfigurieren 'Hybrid Auth' berücksichtigt werden.
    
2. Dieser Artikel verweist, an andere Personen, die Sie wählen unterstützen modernen authentifizierungstopologien (nur für Skype für Unternehmen erforderlich) und Vorgehensweisen unterstützt der Gliederung die Einrichtungsschritte-Artikel oder können Sie die Schritte zum Deaktivieren der modernen Authentifizierung für Exchange lokal und Skype für Business lokal. Bevorzugte dieser Seite in Ihrem Browser, wenn Sie vorhaben, eine Home-Basis für die Verwendung von modernen Authentifizierung in der Server-Umgebung benötigen.
    
## <a name="list-of-modern-authentication-urls"></a>Liste der URLs modernen Authentifizierung
<a name="BKMK_URLListforMA"> </a>

- [Zum Konfigurieren von Exchange Server lokal modernen-Authentifizierung](configure-exchange-server-for-hybrid-modern-authentication.md)
    
- [Für Business Topologien mit modernen Authentifizierung unterstützt Skype](https://technet.microsoft.com/en-us/library/mt803262.aspx)
    
- [Lokale modernen-Authentifizierung zum Konfigurieren von Skype für Unternehmen](configure-skype-for-business-for-hybrid-modern-authentication.md)
    
- [Entfernen oder Deaktivieren der modernen Hybridauthentifizierung aus Skype for Business und Exchange](remove-or-disable-hybrid-modern-authentication-from-skype-for-business-and-excha.md)
    

