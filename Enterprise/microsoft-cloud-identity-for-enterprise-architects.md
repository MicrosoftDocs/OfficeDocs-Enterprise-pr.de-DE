---
title: "Microsoft-Cloud-Identität für Enterprise-Architekten"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 7/19/2017
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Priority
ms.collection:
- Ent_O365
- Ent_O365_Visuals
ms.custom:
- DecEntMigration
- O365ITProTrain
- Strat_O365_Enterprise
- Ent_Architecture
ms.assetid: d27b5085-7325-4ab9-9d9a-438908a65d2c
description: "Zusammenfassung: Entwerfen Sie Ihre Identitätslösung für Microsoft Cloud-Dienste und -Plattformen."
---

# Microsoft-Cloud-Identität für Enterprise-Architekten

 **Zusammenfassung:** Entwerfen Sie Ihre Identitätslösung für Microsoft Cloud-Dienste und -Plattformen.
  
Dieser Artikel beschreibt, was IT-Architekten über das Entwerfen der Identität für Organisationen wissen müssen, die Microsoft Cloud-Dienste und -Plattformen verwenden. Sie können diesen Artikel auch als fünfseitiges Poster anzeigen und im Tabloid-Format (auch bekannt als Ledger, 11 x 17 oder A3) drucken.
  
[![Miniaturbild für Microsoft-Cloud-Identitätsmodell](images/ffa145a1-97e6-4c36-b08b-01c4a4ae8b9b.png)
  
](https://www.microsoft.com/download/details.aspx?id=54431)
  
![PDF-Datei](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=524586) |![Visio-Datei](images/ITPro_Other_VisioIcon.jpg)[Visio](https://download.microsoft.com/download/2/3/8/238228E6-9017-4F6C-BD3C-5559E6708F82/MSFT_cloud_architecture_identity.vsd) |![Seite mit Versionen in zusätzlichen Sprachen anzeigen](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[Weitere Sprachen](https://www.microsoft.com/download/details.aspx?id=54431)
  
Sie sehen auch alle Modelle der [Ressourcen zur Cloud-IT-Architektur von Microsoft](microsoft-cloud-it-architecture-resources.md) und können[Microsoft Enterprise Cloud Roadmap: Resources for IT Decision Makers](https://aka.ms/cloudarchitecture) durchsuchen.
  
> [!NOTE]
> Dieser Artikel spiegelt die Version vom Januar 2016 des Posters **Microsoft-Cloud-Identität für Enterprise-Architekten** wider. Er enthält nicht die Änderungen für die Posterversion vom April 2016.
  
## Entwerfen von Identität für die Microsoft-Cloud

Durch das Integrieren von Identitäten in die Microsoft-Cloud erhalten Sie Zugriff auf eine Vielzahl von Diensten und Cloud-Plattformoptionen. Es gibt zwei Hauptoptionen:
  
- Sie können in Microsoft Azure Active Directory (AD) integrieren. Dies umfasst das Synchronisieren Ihrer lokalen Konten mit Azure AD, der Identitätsanbieter für die Microsoft-Cloud.
    
- Sie können Ihre lokale Active Directory Domain Services (AD DS)-Umgebung auf virtuelle Computer erweitern, die unter Microsoft Azure-Infrastrukturdiensten ausgeführt werden.
    
![Optionen beim Entwerfen von Identitäten in der Cloud](images/08277e96-e4d2-43cb-a56f-a11c7647881a.png)
  
 **Abbildung 1: Optionen beim Entwerfen von Identitäten in der Cloud**
  
Abbildung 1 zeigt Azure AD als Identitätsanbieter für Microsoft SaaS-Dienste (Software as a Service) und Azure PaaS-Anwendungen (Platform as a Service) und wie Geschäftsanwendungen lokale AD DS verwenden können. 
  
### Azure Active Directory

Microsoft Azure AD ist der in der Cloud gehostete Identitäts- und Zugriffsverwaltungsdienst von Microsoft. Es befindet sich im Zentrum der Microsoft-Cloud-Dienste und -Plattformen. Das Integrieren in Azure AD ermöglicht den Zugriff auf alle Microsoft SaaS-Dienste mit Ihrem aktuellen Benutzerkonten und Kennwörtern. Diese Integration stellt außerdem eine Cloud-basierte Identität für Azure PaaS-Anwendungen bereit. 
  
> [!NOTE]
> Azure AD ist kein Ersatz für lokale AD DS für große Organisationen oder für Windows-basierte virtuelle Computer, die unter Azure-IaaS (Infrastructure as a Service) ausgeführt werden. 
  
Es gibt drei Azure AD-Editionen: Kostenlos, Basic und Premium. 
  
||||
|:-----|:-----|:-----|
|**Kostenlos** <br/> |**Basic** <br/> |**Premium** <br/> |
| Verwalten von Benutzerkonten <br/>  Synchronisieren mit lokalen Verzeichnissen <br/>  Einmaliges Anmelden in Azure, Office 365 und Tausenden von anderen gängigen SaaS-Anwendungen, z. B. Salesforce, Workday, Concur, DocuSign, Google Apps, Box, ServiceNow, Dropbox und mehr <br/> | Enthält alle Features der kostenlosen Edition plus: <br/>  Unternehmensbranding <br/>  Gruppenbasierter Anwendungszugriff <br/>  Zurücksetzen von Kennwörtern durch den Benutzer <br/>  Unternehmens-SLA von 99,9 % <br/> | Enthält alle Features der kostenlosen und der Basic-Edition plus: <br/>  Gruppenverwaltung durch den Benutzer <br/>  Erweiterte Sicherheitsberichte und Warnungen <br/>  Mehrstufige Authentifizierung <br/>  Zurücksetzen von Kennwörtern mit Write-Back in lokale AD DS <br/>  Bidirektionale Synchronisierung mit dem Azure AD Connect-Tool <br/>  Azure AD-Anwendungsproxy <br/>  Microsoft Forefront Identity Manager (MIM) <br/> |
   
Weitere Informationen zu Versionen finden Sie unter [Azure Active Directory-Editionen](https://go.microsoft.com/fwlink/p/?LinkId=524280).
  
### Option 1: Integration in Azure Active Directory

Die meisten Organisationen synchronisieren einen Standardsatz aus Objekten und Attributen mit ihrem Azure AD-Mandanten. Das Azure AD Connect-Tool synchronisiert Ihre Konten zwischen den lokalen AD DS und einem Azure AD-Mandanten.
  
![Integrieren in Azure AD](images/3ce05e49-2cb6-4cdc-99ab-d96c5bd12fe8.png)
  
 **Abbildung 2: Integrieren in Azure AD**
  
Abbildung 2 zeigt, wie das Azure AD Connect-Tool AD DS-Änderungen abruft und an Ihren Azure AD-Mandanten sendet. In diesem Fall ist Ihr Azure AD-Mandant ein in der Cloud gehostetes Duplikat unverzichtbarer Inhalte aus dem lokalen Verzeichnis.
  
Viele Organisationen verwenden AD DS als lokalen Identitätsanbieter. Sie können lokal einen anderen Typ von Identitätsanbieter (z. B. einen, der LDAP verwendet) verwenden und diesen mit Azure AD synchronisieren.
  
### Option 2: Erweitern von AD DS auf Azure

Das Erweitern von AD DS auf virtuelle Computer, auf denen Azure-Infrastrukturdienste ausgeführt werden, unterstützt andere Lösungen und Anwendungen als die Synchronisierung mit Azure AD. Es folgen zwei:
  
- Unterstützt die Cloud-basierten Lösungen, die die NTLM- oder Kerberos-Authentifizierung oder virtuelle Computer in der AD DS-Domäne erfordern.
    
- Fügt weiteres Integrationspotenzial für Cloud-Dienste und -Anwendungen für Microsoft Cloud-Dienste und -Plattformen hinzu.
    
![Erweitern von AD DS in Azure](images/4675cf17-962c-4840-b1dc-bbd1d8894a27.png)
  
 **Abbildung 3: Erweitern von AD DS auf Azure**
  
Abbildung 3 zeigt einen AD DS-Domänencontroller, der mit einem virtuellen Azure-Netzwerk über ein lokales VPN-Gerät und ein Azure VPN-Gateway verbunden ist. Das virtuelle Azure-Netzwerk enthält Server für eine LOB-Anwendung und eigene AD DS-Domänencontroller.
  
### Weitere Informationen

- [Das Synchronisieren Ihres Verzeichnisses mit Office 365 ist ein Kinderspiel](https://go.microsoft.com/fwlink/p/?LinkId=524281)
    
- [Infografik: Cloud-Identitäts- und Zugriffsverwaltung](https://go.microsoft.com/fwlink/p/?LinkId=524282)
    
- [Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524283)
    
## Integrieren der lokalen AD DS-Konten in Microsoft Azure AD

Durch die Synchronisierung Ihrer lokalen AD DS-Konten mit Azure AD können Ihre Benutzer ihre lokalen AD DS-Konten für den Zugriff auf Folgendes verwenden:
  
- Alle Microsoft-SaaS-Dienste (Office 365, Microsoft Intune und Dynamics CRM Online)
    
- Die in Azure PaaS ausgeführten Anwendungen
    
Es gibt zwei Möglichkeiten zum Konfigurieren dieser Integration:
  
- Verzeichnis- und Kennwortsynchronisierung
    
- Verbund und einmaliges Anmelden
    
Beginnen Sie mit der einfachsten Option, die Ihren Anforderungen entspricht. Sie können bei Bedarf zwischen diesen Optionen wechseln.
  
> [!NOTE]
> Das Verwenden von Nur-Cloud-Konten (ohne Integration in die lokalen AD DS) wird für große Organisationen nicht empfohlen. 
  
### Verzeichnis- und Kennwortsynchronisierung

Dies ist die einfachste Option und erfordert nur einen Server, der das Azure AD Connect-Tool ausführt. 
  
![Konfiguration für die Verzeichnis- und Kennwortsynchronisierung](images/e7dcfe8f-dab5-461e-89cc-d7a48f58dc0f.png)
  
 **Abbildung 4: Konfiguration für die Verzeichnis- und Kennwortsynchronisierung**
  
Abbildung 4 zeigt ein lokales oder privates Cloud-Rechenzentrum mit einem AD DS-Domänencontroller. Ein Server, auf dem das Azure AD Connect-Tool ausgeführt wird, synchronisiert die Liste der Kontonamen mit Azure AD.
  
Mit dieser Option geschieht Folgendes:
  
- Benutzerkonten werden von Ihren lokalen AD DS (oder einem anderen Identitätsanbieter) mit Ihrem Azure AD-Mandanten synchronisiert. Das lokale Verzeichnis bleibt die maßgebliche Quelle für Konten, und Sie verwalten alle Kontoänderungen von dort aus.
    
- Azure AD führt alle Authentifizierungen für Microsoft SaaS-basierte Dienste und Azure PaaS-Anwendungen aus.
    
- Sie können auch die Synchronisierung für mehrere AD DS-Gesamtstrukturen konfigurieren.
    
Mit Kennwortsynchronisierung:
  
- Benutzer werden aufgefordert, ein Kennwort einzugeben, wenn sie auf Cloud-Dienste zugreifen. Dabei handelt es sich um dasselbe Kennwort, das sie für lokale Ressourcen verwenden.
    
- Benutzerkennwörter werden nie als Klartext an Azure AD gesendet. Stattdessen wird ein Hash des Kennworts verwendet. Der Kennworthash kann kryptografisch nicht entschlüsselt oder durch Reverse Engineering zurückentwickelt werden, um das Klartextkennwort zu erhalten. 
    
Mit mehrstufiger Authentifizierung (Multi-Factor Authentication, MFA):
  
- Sie können die mit Office 365 angeboten grundlegenden MFA-Features nutzen.
    
- Azure PaaS-Anwendungsentwickler können den Azure-Dienst für die mehrstufige Authentifizierung nutzen.
    
Verzeichnissynchronisation bietet keine Integration in lokale MFA-Lösungen.
  
### Verbund und einmaliges Anmelden

Diese Option erfordert zusätzliche Server und Infrastruktur. 
  
![Erforderliche Server für die Verbundauthentifzierung](images/1e54f0d2-e650-4eb5-957f-4f1d3c44da16.png)
  
 **Abbildung 5: Erforderliche Server für die Verbundauthentifzierung**
  
Abbildung 5 zeigt die Komponenten für die Verbundauthentifizierung. Azure AD kontaktiert einen Webanwendungsproxy, der die Authentifizierungsanforderung an einen AD FS-Server (Active Directory Federation Services) weiterleitet, der die Anforderung zur Auswertung und Antwort an einen AD DS-Domänencontroller weiterleitet. Ein Server, auf dem das Azure AD Connect-Tool ausgeführt wird, synchronisiert die Liste der Kontonamen aus AD DS mit Azure AD.
  
Der Verbund stellt diese zusätzlichen Unternehmensfunktionen bereit:
  
- Alle Authentifizierungsanfragen, die an Azure AD gesendet werden, werden an den lokalen Identitätsanbieter über AD FS weitergeleitet und dort ausgeführt.
    
- Funktioniert mit Microsoft-fremden Identitätsanbietern.
    
- Die Synchronisierung von Kennworthashes kann als Anmeldungssicherung für die Verbundanmeldung fungieren (z. B. wenn die Verbundauthentifizierung fehlschlägt).
    
Verwenden Sie den Verbund in folgenden Fällen:
  
- Einmaliges Anmelden ist erforderlich. Mit dem einmaligen Anmelden werden Benutzer nicht aufgefordert, beim Zugriff auf einen Cloud-Dienst Anmeldeinformationen (Benutzername oder Kennwort) einzugeben.
    
- AD FS wurde bereits bereitgestellt.
    
- Sie verwenden einen Identitätsdrittanbieter.
    
- Sie verwenden Forefront Identity Manager 2010 R2 (bietet keine Unterstützung für die Synchronisierung von Kennworthashes).
    
- Sie haben eine integrierte lokale Smartcard oder eine andere MFA-Lösung.
    
- Sie benötigen Anmeldungsüberwachung und/oder Deaktivierung von Konten.
    
- Ihre Organisation benötigt Clientanmeldeeinschränkungen basierend auf Netzwerkspeicherort oder Arbeitsstunden.
    
- Sie müssen die Federal Information Processing Standards (FIPS) einhalten.
    
Die Verbundauthentifizierung erfordert eine größere Investition in die lokale Infrastruktur.
  
- Der Internetzugriff auf die lokalen Servern über eine Unternehmensfirewall muss möglich sein. Microsoft empfiehlt die Verwendung von Web Application Proxy-Servern, die in Ihrer Netzwerkumgebung bereitgestellt werden.
    
- Erfordert Hardware, Lizenzen und Betrieb für AD FS-Server, AD FS-Proxy- oder Web Application Proxy-Server, Firewalls und Lastenausgleich. 
    
- Verfügbarkeit und Leistung sind wichtig, um sicherzustellen, dass Benutzer auf Office 365 und andere Cloud-Anwendungen zugreifen können.
    
### Weitere Informationen

- [Das Synchronisieren Ihres Verzeichnisses mit Office 365 ist ein Kinderspiel](https://go.microsoft.com/fwlink/p/?LinkId=524281)
    
- [Vorbereiten der Bereitstellung von Benutzern über die Verzeichnissynchronisierung in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=524284)
    
- [Mehrstufige Authentifizierung für Office 365](https://go.microsoft.com/fwlink/p/?LinkID=392012)
    
- [Mehrstufige Azure-Authentifizierung](https://go.microsoft.com/fwlink/p/?LinkId=524285)
    
- [TechEd 2014: Verzeichnisintegration: Erstellen eines Verzeichnis mit Active Directory und Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524286)
    
## Erweitern von AD DS auf Azure

Das Erweitern von AD DS auf Azure ist der erste Schritt zur Unterstützung der LOB-Anwendungen, die auf virtuellen Computern in Azure-Infrastrukturdiensten ausgeführt werden, und stellt Folgendes bereit:
  
- Unterstützung für Cloud-basierte Lösungen, die die NTLM- oder Kerberos-Authentifizierung oder virtuelle Computer in der AD DS-Domäne erfordern.
    
- Zusätzliches Integrationspotenzial für Cloud-Dienste und -Anwendungen. Kann jederzeit hinzugefügt werden.
    
![Erweitern von AD DS zu einem virtuellen Azure-Netzwerk](images/9fe2e27d-7fc8-441a-a694-1db4b9f6d03f.png)
  
 **Abbildung 6: Erweitern von AD DS auf ein virtuelles Azure-Netzwerk**
  
Abbildung 6 zeigt ein lokales oder privates Cloud-Rechenzentrum, bei dem AD DS mit einem virtuellen Azure-Netzwerk über eine Site-to-Site-VPN oder ExpressRoute-Verbindung verbunden ist. Das virtuelle Azure-Netzwerk enthält Server für eine LOB-Anwendung und eigene AD DS-Domänencontroller. Diese Konfiguration ist eine Hybridbereitstellung aus lokalen AD DS und Azure-Infrastrukturdiensten. Sie erfordert Folgendes:
  
- ein virtuelles Azure-Netzwerk.
    
- Eine Verbindung zwischen einem VPN-Gerät oder -Router und einem Azure VPN-Gateway.
    
- Das Verwenden eines Teils Ihres lokalen IP-Adressraums für die virtuellen Computer im virtuellen Netzwerk.
    
- Das Bereitstellen von mindestens einem Domänencontroller im virtuellen Netzwerk, der als Server für den globalen Katalog dient (verringert den ausgehenden Datenverkehr über die VPN-Verbindung).
    
Diese Identitätsarchitektur unterstützt eine andere Gruppe von Lösungen und Abwendungen im Vergleich zur Synchronisierung mit Azure AD.
  
### Optionen für die lokale Verbindung zu Azure

Um Ihr lokales Netzwerk mit einem virtuellen Azure-Netzwerk zu verbinden, können Sie Folgendes verwenden:
  
- Eine Site-to-Site-VPN-Verbindung, die 1 bis 10 Sites (einschließlich anderer virtueller Azure-Netzwerke) mit einem einzelnen virtuellen Azure-Netzwerk verbinden kann.
    
- ExpressRoute, eine private, sichere WAN-Verbindung zu Azure über ein Partnernetzwerk und einen Rechenzentrums-Dienstanbieter. ExpressRoute-Verbindungen können verbesserte Zuverlässigkeit, höhere Bandbreite und geringere Latenzen bieten.
    
### Weitere Informationen

- [Standortübergreifende Konnektivität für virtuelle Netzwerke](https://go.microsoft.com/fwlink/p/?LinkId=524293)
    
- [ExpressRoute - Technische Übersicht](https://go.microsoft.com/fwlink/?LinkID=392081)
    
- [Richtlinien für die Bereitstellung von Windows Server Active Directory auf virtuellen Computern in Azure](https://go.microsoft.com/fwlink/p/?LinkId=524295)
    
## Integrieren von Anwendungen in Cloud-Identitäten

Beim Entwerfen und Entwickeln von Anwendungen, die in der Cloud ausgeführt werden, sollten Sie auf die Konsistenz der Benutzererfahrung für den Authentifizierungsprozess achten, einschließlich den erforderlichen Anmeldeinformationen. Wenn Sie z. B. Windows-Anmeldeinformationen für Azure AD oder erweiterte AD DS verwenden, stellen Sie sicher, dass sich Benutzer schnell authentifizieren und auf ihre Aufgaben konzentrieren können.
  
![Integrieren von Anwendungen in Cloud-Identitäten](images/1e6304b0-fa15-4f80-a3b4-7507a28808ae.png)
  
 **Abbildung 7: Integrieren von Anwendungen in Cloud-Identitäten**
  
Abbildung 7 zeigt drei Optionen für die Integration Ihrer Anwendung in Cloud-Identitäten.
  
1. Registrieren Sie Ihre in der Cloud gehosteten Anwendungen bei Azure AD.
    
    Informationen finden Sie im MSDN-Artikel [Integrieren von Anwendungen in Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524303). Auf diese Weise können Sie Azure AD zum Authentifizieren des Zugriffs auf Ihre PaaS-Anwendung verwenden und es Benutzern oder Administratoren ermöglichen, Rechte für den Zugriff auf Anwendungsinhalte von anderen Cloud-Diensten aus, z. B. Office 365, zu gewähren. Weitere Details und Codebeispiele finden Sie im MSDN-Artikel [Authentifizierungsszenarien für Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524304). 
    
2. Anwendungen, die eine programmgesteuerte Authentifizierung für den Zugriff auf eine Anwendung benötigen, die durch AD SD, AD FS unter Windows Server 2012 R2 oder Azure AD gesichert ist, können Folgendes verwenden:
    
  - Die [Azure AD-Diagramm-API](https://go.microsoft.com/fwlink/p/?LinkId=524305)
    
  - [Active Directory-Authentifizierungsbibliothek (ADAL)](https://go.microsoft.com/fwlink/p/?LinkID=524297)
    
    Die Azure AD-Diagramm-API unterstützt OAuth und OpenID Connect. Sie funktioniert auch mit PaaS-Anwendungen.
    
3. Konfigurieren Sie lokale Anwendungen oder LOB-Anwendungen, die auf virtuellen Computern in einem virtuellen Azure-Netzwerk ausgeführt werden, für die direkte Verwendung der Windows-Authentifizierung (NTLM oder Kerberos). Dies bietet die beste Lösung für Benutzer und erfordert den geringsten Konfigurationsaufwand für Serveranwendungsentwickler.
    
### Beispiel für die Anwendungsintegration

Eine Organisation erstellt eine ASP.NET-Anwendung, die einen REST-Endpunkt bereitstellt, von dem andere Anwendungen die neuesten Vertriebsdaten abrufen können. Der Zugriff auf diesen REST-Endpunkt wird mit Azure AD gesichert. Anwendungen müssen Anmeldeinformationen bereitstellen, die von Azure AD authentifiziert werden können, bevor die ASP.NET-Anwendung die angeforderten Daten sendet. Andere Entwickler in der Organisation können ihre eigenen Anwendungen schreiben, in denen die Vertriebsdaten aus dem REST-Endpunkt verwendet werden.
  
Zum Authentifizieren bei Azure AD und zum Abrufen von Daten verwaltet ADAL den Benutzerauthentifizierungsprozess und übergibt das Zugriffstoken an die Anwendung, sodass es für den Zugriff auf die Vertriebsdaten verwendet werden kann. ADAL entfernt einen großen Teil der Komplexität des Abrufens und Analysierens von Token, OAuth-Abläufen und anderen Elementen. ADAL ist eine weitere Technologielösung, die sich schnell verändert, sodass Entwickler die aktuelle Version auf NuGet suchen sollten.
  
## Bereitstellen von Verzeichniskomponenten in Azure

Sie können Verzeichniskomponenten, z. B. Server für die Synchronisierung von Kennwörtern oder Verbundauthentifizierung, in einem virtuellen Azure-Netzwerk statt in einem lokalen Rechenzentrum bereitstellen. Bedenken Sie die Vorteile, insbesondere, wenn Sie planen, AD DS auf Azure zu erweitern.
  
Es folgen die Verzeichniskomponenten, die in einem virtuellen Azure-Netzwerk eingesetzt werden können:
  
- Azure AD Connect-Tool
    
- Komponenten der Verbundauthentifizierung
    
- Eine eigenständige AD DS-Umgebung
    
### AD Connect-Tool

Das Azure AD Connect-Tool kann in der Cloud in einem virtuellen Azure-Netzwerk gehostet werden. Bedenken Sie diese Vorteile der Bereitstellung dieser Arbeitslast in Azure:
  
- Potenziell schnellere Bereitstellung und niedrigere Betriebskosten
    
- Erhöhte Verfügbarkeit
    
![In Azure-Infrastrukturdiensten ausgeführtes AD Connect-Tool](images/97593481-e06a-4e34-b8b5-cc63acb5f9f1.png)
  
 **Abbildung 8: Das AD Connect-Tool unter Azure**
  
Abbildung 8 zeigt das AD Connect-Tool, das auf einem virtuellen Computer in einem virtuellen Azure-Netzwerk ausgeführt wird und einen lokalen AD DS-Domänencontroller nach Kontoänderungen abfragt und diese Änderungen dann an Office 365 sendet. Diese Lösung funktioniert mit:
  
- Office 365-Diensten.
    
- Azure PaaS-Anwendungen, die über das Internet verfügbar sind.
    
- LOB-Anwendungen in Azure, die von lokalen Umgebungen aus über die Site-to-Site-VPN- oder ExpressRoute-Verbindung verfügbar sind.
    
Weitere Informationen finden Sie unter [Integrieren Ihrer lokalen Identitäten in Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).
  
### Infrastruktur der Verbundauthentifizierung

Wenn Sie AD FS noch nicht lokal bereitgestellt haben, sollten Sie diese Vorteile der Bereitstellung dieser Arbeitsbelastung in Azure bedenken:
  
- Bietet Autonomie für die Authentifizierung bei Cloud-Diensten (keine lokalen Abhängigkeiten)
    
- Reduziert Server und Tools, die lokal gehostet werden
    
- Verwendet ein Site-to-Site-VPN-Gateway auf einem Failovercluster mit zwei Knoten für die Verbindung mit Azure (neu)
    
- Verwendet ACLs, um sicherzustellen, dass Web Application Proxy-Server nur mit AD FS, nicht direkt mit Domänencontrollern oder anderen Servern kommunizieren können
    
![Bereitstellen einer Infrastruktur für die Verbundauthentifizierung in Azure](images/4e023dd4-b9fb-403a-a8eb-069b56d7a65e.png)
  
 **Abbildung 9: Bereitstellen einer Infrastruktur für die Verbundauthentifizierung in Azure**
  
Abbildung 9 zeigt eine Reihe von lokalen Domänencontrollern, die AD DS-Informationen mit einer Reihe von Domänencontrollern in einem virtuellen Azure-Netzwerk replizieren. Das auf einem Server im virtuellen Azure-Netzwerk ausgeführte Azure AD Connect-Tool fragt den lokalen Domänencontroller nach Änderungen ab und sendet diese Änderungen an Azure AD. Eingehende Authentifizierungsanforderungen an Azure AD von Microsoft SaaS-Diensten, Azure PaaS-Anwendungen und anderen Cloud-Anwendungen werden an einen externen Lastenausgleich weitergeleitet, der die Anforderung an eine Gruppe von Web Application Proxy-Servern weiterleitet. Die Web Application Proxy-Server leiten die Anforderung an einen internen Lastenausgleich weiter, der die Anforderung an eine Gruppe von AD FS-Servern weiterleitet. Die AD FS-Server leiten dann die Anforderung an einen Domänencontroller weiter, um die gesendeten Anmeldeinformationen zu überprüfen.
  
 Diese Lösung funktioniert mit:
  
- Programme, die Kerberos erfordern
    
- Alle Microsoft SaaS-Dienste
    
- Anwendungen in Azure, die das Internet nutzen
    
- Anwendungen in Azure IaaS oder PaaS, die Authentifizierung mit einer Gruppe von Konten in den AD DS Ihrer Organisation erfordern
    
Weitere Informationen finden Sie unter [Integrieren Ihrer lokalen Identitäten in Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).
  
### Eigenständige AD DS-Umgebung in einem virtuellen Azure-Netzwerk

Sie müssen eine Cloud-Anwendung nicht immer in Ihre lokale Umgebung integrieren. Eine eigenständige AD DS-Domäne in einem virtuellen Azure-Netzwerk unterstützt beispielsweise Anwendungen, die öffentlich zugänglich sind, z. B. Internetwebsites.
  
![Eine eigenständige AD DS-Umgebung für eine serverbasierte Anwendung](images/98c7349f-535d-4c9b-8de4-e580f6d573d4.png)
  
 **Abbildung 10: Eine eigenständige AD DS-Umgebung für eine serverbasierte Anwendung**
  
Abbildung 10 zeigt ein virtuelles Azure-Netzwerk, das eine Reihe von AD DS-Servern hostet, die AD DS- und DNS-Dienste mit einer Reihe von Servern bereitstellt, die eine Anwendung hosten. Diese Lösung funktioniert mit:
  
- Websites und Anwendungen, die das Internet nutzen
    
- Anwendungen, die NTLM- oder Kerberos-Authentifizierung erfordern
    
- Anwendungen, die auf Windows-basierten Servern, die AD DS erfordern, ausgeführt werden
    
Weitere Informationen finden Sie unter [Integrieren Ihrer lokalen Identitäten in Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).
  
## See Also

#### 

[Ressourcen zur Cloud-IT-Architektur von Microsoft](microsoft-cloud-it-architecture-resources.md)
#### 

[Enterprise-Cloud-Roadmap von Microsoft: Ressourcen für IT-Entscheidungsträger](https://sway.com/FJ2xsyWtkJc2taRD)

