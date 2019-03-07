---
title: Übersicht über die moderne Hybrid Authentifizierung und Voraussetzungen für die Verwendung mit lokalen Skype for Business-und Exchange-Servern
ms.author: tracyp
ms.reviewer: smithre4
author: MSFTTracyP
manager: laurawi
ms.date: ''
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.assetid: ef753b32-7251-4c9e-b442-1a5aec14e58d
ms.collection:
- M365-security-compliance
description: Die moderne Authentifizierung ist eine Methode zur Identitätsverwaltung, die eine sicherere Benutzerauthentifizierung und Autorisierung bietet. Es steht für hybridbereitstellungen von lokalen Skype for Business Server-und Exchange Server-lokalen sowie für geteilte Skype for Business-Hybriden zur Verfügung. Dieser Artikel enthält Links zu verwandten Dokumenten zu Voraussetzungen, zum Einrichten/deaktivieren moderner Authentifizierung und zu einigen der zugehörigen Clients (ex. Outlook-und Skype-Clients).
ms.openlocfilehash: 26efa77e3c98c0395188e6ca7a2f65cd3b8b939e
ms.sourcegitcommit: 19f0deee26b6cf2eef316c742054572bb9d98b84
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2019
ms.locfileid: "30458345"
---
# <a name="hybrid-modern-authentication-overview-and-prerequisites-for-using-it-with-on-premises-skype-for-business-and-exchange-servers"></a>Übersicht über die moderne Hybrid Authentifizierung und Voraussetzungen für die Verwendung mit lokalen Skype for Business-und Exchange-Servern

Die moderne Authentifizierung ist eine Methode zur Identitätsverwaltung, die eine sicherere Benutzerauthentifizierung und Autorisierung bietet. Es steht für Office 365 Hybrid-Bereitstellungen von lokalen Skype for Business Server-und Exchange Server-lokalen sowie für geteilte Skype for Business-Hybriden zur Verfügung. Dieser Artikel enthält Links zu verwandten Dokumenten zu Voraussetzungen, zum Einrichten/deaktivieren moderner Authentifizierung und zu einigen der zugehörigen Clients (ex. Outlook-und Skype-Clients). 
  
- [Was ist die moderne Authentifizierung?](hybrid-modern-auth-overview.md#BKMK_WhatisModAuth)
    
- [Was ändert sich, wenn ich die moderne Authentifizierung verwende?](hybrid-modern-auth-overview.md#BKMK_WhatChanges)
    
- [Überprüfen des modernen Authentifizierungsstatus Ihrer lokalen Umgebung](hybrid-modern-auth-overview.md#BKMK_CheckStatus)
    
- [Erfüllen Sie die Voraussetzungen für moderne Authentifizierung?](hybrid-modern-auth-overview.md#BKMK_MeetPrereq)
    
- [Was muss ich noch wissen, bevor ich beginne?](hybrid-modern-auth-overview.md#BKMK_Whatelse)
    
- [Liste der modernen Authentifizierungs-URLs](hybrid-modern-auth-overview.md#BKMK_URLListforMA)
    
## <a name="what-is-modern-authentication"></a>Was ist die moderne Authentifizierung?
<a name="BKMK_WhatisModAuth"> </a>

Bei der Kommunikation zwischen einem Client (beispielsweise Ihrem Laptop oder Ihrem Telefon) und einem Server verwendet Microsoft den Begriff "moderne Authentifizierung".
  
Die moderne Authentifizierung ist ein Überbegriff für eine Kombination aus Authentifizierungs-und Autorisierungsmethoden sowie einige Sicherheitsmaßnahmen, die auf Zugriffsrichtlinien basieren, die Sie möglicherweise bereits kennen. Sie umfasst Folgendes:
  
- **Authentifizierungsmethoden**: mehrstufige Authentifizierung; Client zertifikatbasierte Authentifizierung; und die Active Directory-AuthentifizierungsBibliothek ( [Adal](https://technet.microsoft.com/en-us/library/mt710548.aspx)).
    
- **Autorisierungsmethoden**: Microsoft-Implementierung der Open Authorization (OAuth). 
    
- **Richtlinien für bedingten Zugriff**: Mobile Application Management (MAM) und Azure Active Directory-bedingter Zugriff. 
    
Das Verwalten von Benutzeridentitäten mit moderner Authentifizierung gibt Administratoren viele verschiedene Tools, die bei der Sicherung von Ressourcen verwendet werden können, und bietet sicherere Methoden zur Identitätsverwaltung sowohl für lokale (Exchange als auch Skype for Business), Exchange Hybrid und Skype for Business-Szenarien mit Hybrid-und geteilten Domänen.
  
Beachten Sie, dass das Anmeldeverhalten von Skype for Business-Client Benutzern, da Skype for Business eng mit Exchange arbeitet, durch den modernen Authentifizierungsstatus von Exchange beeinflusst wird. Dies gilt auch, wenn Sie eine hybride Skype for Business Split-Domain haben. Außerdem wird die Art der Skype for Business-hybride, die die Verwendung der modernen Authentifizierung unterstützt, häufig als "geteilte Domäne" bezeichnet (in einer geteilten Domäne haben Sie sowohl Skype for Business Online als auch Skype for Business auf-Prem, und Benutzer werden an beiden Standorten verwaltet).
  
> [!IMPORTANT]
> Wussten Sie, dass ab August 2017 alle neuen Office 365-Mandanten, die Skype for Business Online und Exchange Online verwenden, die moderne Authentifizierung standardmäßig aktiviert haben? Bereits vorhandene Mandanten haben keine Änderung im Standardstatus MA, aber alle neuen Mandanten unterstützen automatisch den erweiterten Satz von Identitätsfeatures, die oben aufgeführt sind. Um Ihren Status für Skype for Business Online zu überprüfen, können Sie Skype for Business Online PowerShell mit globalen Administratoranmeldeinformationen verwenden. Ausführen `Get-CsOAuthConfiguration` , um die Ausgabe von-ClientADALAuthOverride zu überprüfen. Wenn-ClientADALAuthOverride "zulässig" ist, ist Ihre moderne Authentifizierung eingeschaltet. 
  
## <a name="what-changes-when-i-use-modern-authentication"></a>Was ändert sich, wenn ich die moderne Authentifizierung verwende?
<a name="BKMK_WhatChanges"> </a>

Wenn Sie moderne Authentifizierung mit lokalem Skype for Business oder Exchange Server verwenden, *Authentifizieren* Sie Benutzer weiterhin lokal, aber die Geschichte der *Autorisierung* des Zugriffs auf Ressourcen (wie Dateien oder e-Mails) ändert sich. Obwohl bei der modernen Authentifizierung die Client-und Server Kommunikation durchgeführt wird, führen die Schritte beim Konfigurieren von MA dazu, dass evoSTS (ein von Azure AD verwendeter sicherheitsTokendienst) als AuthentifizierungsServer für Skype for Business und Exchange Server festgelegt wird. 
  
Die Änderung an evoSTS ermöglicht Ihren lokalen Servern das Nutzen von OAuth (Token Emission) für die Autorisierung Ihrer Clients und ermöglicht auch, dass Ihre lokalen Sicherheitsmethoden in der Cloud gemeinsam nutzen (wie mehrstufige Authentifizierung). Darüber hinaus gibt der evoSTS Token heraus, mit denen Benutzer Zugriff auf Ressourcen anfordern können, ohne Ihr Kennwort als Teil der Anforderung anzugeben. Unabhängig davon, wo Ihre Benutzer (von Online oder lokal) verwaltet werden, und unabhängig davon, an welchem Speicherort die erforderliche Ressource gehostet wird, wird EvoSTS der Kern der Autorisierung von Benutzern und Clients, nachdem die moderne Authentifizierung konfiguriert wurde.
  
Hier sehen Sie ein Beispiel dafür, was ich meine. Wenn der Skype for Business-Client auf Exchange Server zugreifen muss, um Kalenderinformationen im Namen eines Benutzers abzurufen, wird die Active Directory-AuthentifizierungsBibliothek (ADAL) dazu verwendet. ADAL ist eine Codebibliothek, mit der gesicherte Ressourcen in Ihrem Verzeichnis für Clientanwendungen mit OAuth-Sicherheitstoken zur Verfügung gestellt werden. ADAL verwendet OAuth zum Überprüfen von Anspruchs-und Exchange-Token (anstelle von Kennwörtern), um einem Benutzer Zugriff auf eine Ressource zu gewähren. In der Vergangenheit war die Autorität in einer Transaktion wie dieser--der Server, der die Benutzeranforderungen überprüfen und die erforderlichen Token ausgeben kann--möglicherweise ein sicherheitsTokendienst oder sogar Active Directory-Verbunddienste. Die moderne Authentifizierung zentralisiert diese Autorität jedoch mit Azure Active Directory (Azure AD) in der Cloud.
  
Auch wenn Ihre Exchange-Server und Skype for Business-Umgebungen möglicherweise vollständig lokal sind, ist der autorisierungsserver Online, und Ihre lokale Umgebung muss die Möglichkeit haben, eine Verbindung mit Ihrem Office herzustellen und zu verwalten. 365-Abonnement in der Cloud (und die Azure Active Directory-Instanz, die Ihr Abonnement als Verzeichnis verwendet).
  
Was ändert sich nicht? Unabhängig davon, ob Sie sich in einer geteilten Domäne oder mit Skype for Business und Exchange Server on-premises befinden, müssen sich alle Benutzer zuerst *lokal* authentifizieren. In einer hybriden Implementierung der modernen Authentifizierung zeigen Lyncdiscovery und AutoDiscovery auf Ihren lokalen Server. 
  
> [!IMPORTANT]
> Wenn Sie die spezifischen Skype for Business-Topologien kennen müssen, die mit MA unterstützt werden, ist dies [hier dokumentiert](https://technet.microsoft.com/en-us/library/mt803262.aspx).
  
## <a name="check-the-modern-authentication-status-of-your-on-premises-environment"></a>Überprüfen des modernen Authentifizierungsstatus Ihrer lokalen Umgebung
<a name="BKMK_CheckStatus"> </a>

Da die moderne Authentifizierung den autorisierungsserver ändert, der verwendet wird, wenn Dienste OAuth/S2S nutzen, müssen Sie wissen, ob die moderne Authentifizierung für Ihre Skype for Business-und Exchange-Umgebung ein-oder ausgeschaltet ist. Sie können den Status auf Ihren Exchange-oder Skype for Business-Servern lokal überprüfen, indem Sie `Get-CSOAuthConfiguration` den Befehl in PowerShell ausführen. Wenn der Befehl eine leere ' OAuthServers '-Eigenschaft zurückgibt, wird die moderne Authentifizierung deaktiviert.
  
## <a name="do-you-meet-modern-authentication-prerequisites"></a>Erfüllen Sie die Voraussetzungen für moderne Authentifizierung?

Überprüfen und überprüfen Sie diese Elemente aus der Liste, bevor Sie fortfahren:
  
- **Speziell für Skype for Business**
    
  - Alle Server benötigen SFB Server 2015 CU5 oder höher
    
  - **Exception** -Survivable Branch Appliance (SBA) kann in der aktuellen Version sein (basierend auf lync 2013) 
    
  - Ihre SIP-Domäne wird als Verbunddomäne in Office 365 hinzugefügt.
    
  - Alle SFB-Front-Ends müssen über ausgehende Verbindungen zum Internet, zu Office 365-Authentifizierungs-URLs (TCP 443) und bekannte Zertifikatstamm CRLs (TCP 80) verfügen, die in den Zeilen 56 und 125 des Abschnitts "Microsoft 365 Common and Office Online" von [office 365 URLs und IP aufgeführt sind. Adressbereiche](urls-and-ip-address-ranges.md).
    
 **Hinweis** Wenn Ihre Skype for Business-Front-End-Server einen Proxy Server für den Internet Zugriff verwenden, muss die verwendete Proxy Server-IP und-Nummer im Konfigurationsabschnitt der Datei Web. config für jedes Front-End eingegeben werden. 
  
- C:\Program Files\Skype for Business Server 2015 \ Web Components\Web ticket\int\web.config
    
- C:\Program Files\Skype for Business Server 2015 \ Web Components\Web ticket\ext\web.config
    
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
> Achten Sie darauf, den RSS-Feed für [Office 365-URLs und IP-Adressbereiche](urls-and-ip-address-ranges.md) zu abonnieren, um mit den aktuellen Auflistungen der erforderlichen URLs auf dem neuesten Stand zu bleiben. 
  
- **Exchange Server-spezifisch**
    
  - Sie verwenden entweder Exchange Server 2013 KU19 und up oder Exchange Server 2016 KU8 und up.
    
  - In der Umgebung gibt es keine Exchange Server 2010.
    
  - SSL-abLadung ist nicht konfiguriert. SSL-Terminierung und erneute Verschlüsselung wird unterstützt.
    
  - Falls Ihre Umgebung eine Proxy Server-Infrastruktur verwendet, damit die Server eine Verbindung mit dem Internet herstellen können, stellen Sie sicher, dass auf allen Exchange-Servern der Proxy Server in der [para internetweb](https://technet.microsoft.com/en-us/library/bb123716%28v=exchg.160%29.aspx) -Eigenschaft definiert ist.
    
- **Exchange-Client-und-Protokollanforderungen**
  
  - Die folgenden Clients unterstützen die moderne Authentifizierung:

  |**Clients**|**Primäres Protokoll**|**Hinweise**|
  |:-----|:-----|:-----|
  |Outlook 2013 und Outlook 2016  <br/> |MAPI über HTTP  <br/> |MAPI über HTTP muss in Exchange aktiviert sein, damit die moderne Authentifizierung mit diesen Clients (in der Regel für neue Installationen von Exchange 2013 Service Pack 1 und höher) aktiviert werden kann. Weitere Informationen finden Sie unter [Funktionsweise der modernen Authentifizierung für office 2013-und office 2016-Client-apps](https://docs.microsoft.com/en-us/office365/enterprise/modern-auth-for-office-2013-and-2016).  <br/> Stellen Sie sicher, dass Sie die erforderliche Mindestversion von Outlook erstellen. Lesen Sie [die neuesten Updates für Outlook-Versionen, die Windows Installer (MSI) verwenden](https://docs.microsoft.com/en-us/officeupdates/outlook-updates-msi).  <br/> |
  |Outlook 2016 für Mac  <br/> |Exchange-Webdienste  <br/> |  <br/> |
  |Outlook für iOS und Android  <br/> |  <br/> |Weitere Informationen finden Sie unter [Verwenden der modernen Hybrid Authentifizierung mit Outlook für IOS und Android](https://docs.microsoft.com/en-us/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) .  <br/> |
  |Exchange ActiveSync-Clients (z. b. iOS11-Mail)  <br/> |Exchange ActiveSync  <br/> |Für Exchange ActiveSync-Clients, die die moderne Authentifizierung unterstützen, müssen Sie das Profil neu erstellen, um von der Standardauthentifizierung zur modernen Authentifizierung zu wechseln.  <br/> |

- **Allgemeine Voraussetzungen**
    
  - Wenn Sie ADFS verwenden, sollten Sie Windows 2012 R2 ADFS 3,0 und höher für den Verbund haben.
    
  - Ihre Identitäts Konfigurationen sind alle Typen, die von AAD Connect (beispielsweise Kennworthash Synchronisierung, Pass-Through-Authentifizierung, lokale STS, unterstützt von Office 365 usw.) unterstützt werden.
    
  - Sie haben AAD Connect konfiguriert und funktionieren für die Benutzerreplikation und-Synchronisierung.
    
  - Sie haben überprüft, ob Hybrid mit dem klassischen Exchange-Hybrid Topologiemodus zwischen Ihrer lokalen und der Office 365-Umgebung konfiguriert ist. Offizielle Support-Anweisung für Exchange Hybrid sagt, dass Sie entweder die aktuelle CU-oder Current-CU-1 haben müssen.
    
    > [!Note]
    > Die moderne Hybrid Authentifizierung wird mit dem [Hybrid-Agent](https://docs.microsoft.com/exchange/hybrid-deployment/hybrid-agent)nicht unterstützt.
    
  - Stellen Sie sicher, dass sowohl ein lokale Testbenutzer als auch ein in Office 365 verwalteter Hybrid Testbenutzer sich beim Skype for Business-Desktop Client anmelden können (wenn Sie die moderne Authentifizierung mit Skype verwenden möchten) und Microsoft Outlook (wenn Sie dies wünschen, verwenden Sie die moderne Authentifizierung mit Exchange).
    
## <a name="what-else-do-i-need-to-know-before-i-begin"></a>Was muss ich noch wissen, bevor ich beginne?
<a name="BKMK_Whatelse"> </a>

1. Bei allen Szenarien für lokale Server muss die moderne Authentifizierung lokal eingerichtet werden (tatsächlich gibt es für Skype for Business eine Liste der unterstützten Topologien), sodass der Server, der für die Authentifizierung und Autorisierung zuständig ist, sich in der Microsoft-Cloud befindet ( AAD-Sicherheitstokendienst, "evoSTS" genannt) und Aktualisieren von Azure Active Directory (AAD) zu den URLs oder Namespaces, die von Ihrer lokalen Installation von Skype for Business oder Exchange verwendet werden. Daher übernehmen lokale Server eine Microsoft-Cloud-Abhängigkeit. Diese Aktion kann als "Hybrid Authentifizierung" konfiguriert werden.
    
2. Dieser Artikel enthält Links zu anderen, die Sie bei der Auswahl unterstützter moderner Authentifizierungs Topologien (nur für Skype for Business erforderlich) und Artikel mit Vorgehensweisen zur Beschreibung der Einrichtungsschritte oder zur Deaktivierung der modernen Authentifizierung für Exchange lokal unterstützen. und Skype for Business vor Ort. Favorit diese Seite in Ihrem Browser, wenn Sie eine Basis für die Verwendung der modernen Authentifizierung in Ihrer Server Umgebung benötigen.
    
## <a name="list-of-modern-authentication-urls"></a>Liste der modernen Authentifizierungs-URLs
<a name="BKMK_URLListforMA"> </a>

- [Konfigurieren von Exchange Server für die Verwendung der modernen Authentifizierung](configure-exchange-server-for-hybrid-modern-authentication.md)
    
- [Unterstützte Skype for Business-Topologien mit moderner Authentifizierung](https://technet.microsoft.com/en-us/library/mt803262.aspx)
    
- [Konfigurieren von Skype for Business lokal für die Verwendung der modernen Authentifizierung](configure-skype-for-business-for-hybrid-modern-authentication.md)
    
- [Entfernen oder Deaktivieren der modernen Hybrid Authentifizierung von Skype for Business und Exchange](remove-or-disable-hybrid-modern-authentication-from-skype-for-business-and-excha.md)
    

