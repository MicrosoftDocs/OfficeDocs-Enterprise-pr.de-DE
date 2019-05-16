---
title: Zugängliches Diagramm – Internetwebsites in Microsoft Azure für SharePoint 2013
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 71636974-fb99-487c-ac67-f15e9401acba
description: Dieser Artikel ist eine barrierefreie Textversion des Diagramms „Internetsites für SharePoint 2013 in Microsoft Azure“.
ms.openlocfilehash: 1d18ad73502c7e21c1c0825e3e56e4faac2a4a09
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068641"
---
# <a name="accessible-diagram---internet-sites-in-microsoft-azure-for-sharepoint-2013"></a>Zugängliches Diagramm – Internetwebsites in Microsoft Azure für SharePoint 2013

**Zusammenfassung:** Dieser Artikel ist eine barrierefreie Textversion des Diagramms mit dem Namen Internet Sites in Microsoft Azure für SharePoint 2013.
  
In diesem Poster wird beschrieben und veranschaulicht, wie öffentlich zugängliche Websites im Internet von der Elastizität in der Cloud und Azure AD für Kundenkonten profitieren. Es gibt sechs verschiedene Szenarien, die beschreiben, wie Internetsites von Azure profitieren:  
  
- Entwurf und Dimensionierung der Farmtopologie  
    
- Feinabstimmung für Azure  
    
- Auswahl des Active Directory-Modells  
    
- Entwurf für die Identitätsverwaltung, Zonen und Authentifizierung  
    
- Entwurf von Websites und URLs für die websiteübergreifende Veröffentlichung  
    
- Entwurf der Azure-Umgebung  
    
## <a name="design-and-size-the-farm-topology"></a>Entwurf und Dimensionierung der Farmtopologie

Verwenden Sie die Informationen zur Topologie, Kapazität und Leistung von SharePoint 2013 auf TechNet, um die Farmtopologie zu entwerfen. 
  
Stellen Sie sicher, dass die von Ihnen entworfene Farm die Kapazitäts- und Leistungsziele erfüllt.  
  
### <a name="example-medium-internet-sites-farm-85-page-views-per-second"></a>Beispiel: Mittelgroße Internetsitefarm (ca. 85 Seitenaufrufe pro Sekunde)

Diese Farm bietet eine fehlertolerante SharePoint 2013-Such Farmtopologie, die für einen Korpus optimiert ist, der 3,4 Millionen Elemente enthält. 
  
In der Beispiel Farm werden 100-200-Dokumente pro Sekunde abhängig von der Sprache verarbeitet, und es werden 85-Seitenaufrufe pro Sekunde und 100 Abfragen pro Sekunde unterstützt. 
  
Das zugehörige Diagramm zeigt eine mittelgroße Internetsitefarm mit drei Arten von Servern:  
  
- Webserver 
    
- Anwendungsserver 
    
- Datenbankserver 
    
#### <a name="web-servers"></a>Webserver

Im Abschnitt „Web-Server“ gibt es drei Webserver: Host A, Host B und Host C. Jeder Webserver enthält einen verteilten Cache, Benutzerprofile, verwaltete Metadaten und Abfrageverarbeitungsfunktionen. Sie enthalten auch ein Indexpartitionsreplikat, das auf jedem der Server vorhanden ist.   
  
Zum horizontalen Skalieren können Sie einen zusätzlichen Webserver mit den gleichen Funktionen hinzufügen. Dadurch werden weitere 28 Seitenansichten pro Sekunde ermöglicht.  
  
#### <a name="application-servers"></a>Anwendungsserver

Im Abschnitt „Anwendungsserver“ gibt es drei Anwendungsserver: Host D, Host E und Host F. Host D enthält Komponenten zur Durchforstung, Verwaltung, Analyse und Inhaltsverarbeitung. Host E enthält Komponenten zur Durchforstung, Verwaltung und Inhaltsverarbeitung. Host F enthält Komponenten zur Durchforstung und Inhaltsverarbeitung.  
  
Zum horizontalen Skalieren können Sie einen Anwendungsserver mit einer Durchforstungs- und Inhaltsverarbeitungskomponente hinzufügen. Dadurch wird die Verarbeitung von 40 weiteren Dokumenten pro Sekunde ermöglicht.  
  
#### <a name="database-servers"></a>Datenbankserver

Im Abschnitt „Datenbankserver“ gibt es zwei Server: Host G und Host H. Aus Gründen der Fehlertoleranz laufen die Server auf verbundenen Hosts.  
  
Host G enthält alle SharePoint-Datenbanken. Dazu gehören unter anderem die Suchverwaltungsdatenbank, Linkdatenbank, zwei Durchforstungsdatenbanken und eine Analysedatenbank. Host H enthält alle SharePoint-Datenbanken. Dazu gehören redundante Kopien aller Datenbanken mit SQL-Clustering, Spiegelung oder SQL Server 2012 AlwaysOn.  
  
## <a name="fine-tune-for-azure"></a>Feinabstimmung für Azure

Die SharePoint-Farm muss möglicherweise für Verfügbarkeitssätze auf der Azure-Plattform optimiert werden. Um eine hohe Verfügbarkeit aller Komponenten sicherzustellen, vergewissern Sie sich, dass alle Serverrollen identisch konfiguriert sind.    
  
In der Beispieltopologie im Diagramm liegt folgende Situation vor:  
  
- Die Webserver und Datenbankserver sind identisch konfiguriert.  
    
- Die drei Anwendungsserver sind nicht identisch konfiguriert. Diese Serverrollen benötigen eine Optimierung für Verfügbarkeitssätze in Azure.   
    
### <a name="before"></a>Vor

Im oberen Bereich des Diagramms sehen Sie die SharePoint-Farm vor der Optimierung für Verfügbarkeitssätze in Azure. Im Diagramm sind die drei Host-Anwendungsserver nicht identisch konfiguriert. Die Anzahl der Komponenten wird durch die Leistungs- und Kapazitätsziele für die Farm bestimmt. Die drei Server sind folgendermaßen konfiguriert:  
  
- Für den Anwendungsserver Host D wurden Rollen zur Durchforstung, Verwaltung, Analyse und Inhaltsverarbeitung konfiguriert.  
    
- Für den Anwendungsserver Host E wurden Rollen zur Durchforstung, Verwaltung und Inhaltsverarbeitung konfiguriert.  
    
- Für den Anwendungsserver Host F wurden Rollen zur Durchforstung und Inhaltsverarbeitung konfiguriert.  
    
### <a name="after"></a>Nach

In diesem Teil des Diagramms sehen Sie die SharePoint-Farm nach der Optimierung für Verfügbarkeitssätze in Azure. Für die Anpassung dieser Architektur an Azure werden die vier Komponenten auf alle drei Server repliziert. Dies erhöht die Anzahl der Komponenten über die Leistungs-und Kapazitätsvorgaben hinaus. Der Vorteil besteht darin, dass dieser Entwurf für Hochverfügbarkeit aller vier Komponenten auf der Azure-Plattform sorgt, wenn diese drei virtuellen Computer einem Verfügbarkeitssatz zugewiesen werden. 
  
Für alle drei Server wurden Rollen zur Durchforstung, Verwaltung, Analyse und Inhaltsverarbeitung konfiguriert.  
  
## <a name="choose-the-active-directory-model"></a>Auswahl des Active Directory-Modells

Alle SharePoint-Lösungen erfordern Windows Active Directory-Domänendienste (AD DS). Derzeit sind zwei Optionen für SharePoint-Lösungen in Azure verfügbar.   
  
- Option 1: dedizierte Domäne – Sie können eine dedizierte und isolierte Domäne für Azure bereitstellen, um eine SharePoint-Farm zu unterstützen. Dies ist eine gute Wahl für öffentlich zugängliche Internetwebsites. 
    
- Option 2: Erweitern der lokalen Domäne über eine Standort-zu-Standort-VPN-Verbindung. Wenn Sie die lokale Domäne über eine Standort-zu-Standort-VPN-Verbindung erweitern, greifen Benutzer auf die SharePoint-Farm zu, als ob Sie lokal gehostet würde. Sie können Ihre vorhandenen Active Directory-und DNS-Implementierungen nutzen. 
    
## <a name="design-for-identity-management-zones-and-authentication"></a>Entwurf für die Identitätsverwaltung, Zonen und Authentifizierung

### <a name="design-for-accounts-and-authentication"></a>Entwurf für Konten und Authentifizierung

Bestimmen Sie, welche Konten verwaltet werden und welche Art der Authentifizierung verwendet werden soll.  
  
#### <a name="accounts-for-site-developers-and-authors"></a>Konten für Website-Entwickler und -Autoren

- Fügen Sie der Domäne in Azure Konten hinzu.  
    
- Verwenden Sie lokal die Active Directory-Verbunddienste (AD FS), um die internen Konten mit der Domäne in Azure zu verbinden.  
    
- Wenn der Entwurf eine Standort-zu-Standort-VPN-Verbindung enthält, verwenden Sie die internen Konten.  
    
#### <a name="accounts-for-customers"></a>Konten für Kunden

- Verwenden Sie Azure Active Directory.  
    
- Verwenden Sie einen anderen SAML-basierten Anbieter.  
    
### <a name="design-for-zones"></a>Entwurf für Zonen

In SharePoint 2013 wird die Identitätsverwaltung bei der Konfiguration der Zonen und Authentifizierung berücksichtigt.  
  
Dieser Entwurf bietet eine klare Trennung zwischen Kundenkonten und allen anderen Konten.  
  
- Verwenden Sie diesen Entwurf, wenn Sie Kundenkonten komplett anders als die internen Konten für Autoren und Website-Entwickler behandeln möchten.  
    
- Mithilfe dieses Designs können Sie Zonenrichtlinien verwenden, um Aktionen des Kunden innerhalb einer Webanwendung zu beschränken.  
    
- Dieser Entwurf führt zu verschiedenen URLs für Kundenkonten und interne Konten.  
    
In diesem Beispiel: 
  
- Konfigurieren Sie die Standardzone für interne Konten.  
    
- Konfigurieren Sie die Extranetzone für den authentifizierten Kundenzugriff. Verwenden Sie Azure Active Directory (AD) für Kundenkonten, oder verwenden Sie einen anderen SAML-basierten Anbieter.  
    
- Konfigurieren Sie die Internetzone für den anonymen Zugriff.   
    
Verwenden Sie kein zwei Zonen Design, in dem alle authentifizierten Benutzer für die Verwendung der Standardzone konfiguriert sind. 
  
Das zugehörige Diagramm zeigt einen Drei-Zonen-Entwurf mit Trennung von internen und Kundenkonten.   
  
Besucher und Kunden greifen über Webanwendungen in einer der beiden Zonen auf den Azure AD-Mandanten in der SharePoint-2013-Farm zu. Die beiden Zonen sind: 
  
- Zone: Internet für anonyme Benutzer  
    
- Zone: Extranet für authentifizierte Benutzer  
    
Benutzer mit internen Konten greifen über AD DS auf den Azure Active Directory-Mandanten zu und in der lokalen Umgebung durch den VPN-Tunnel zu Azure AD auf AD FS. Die Standardzone bietet Windows-Authentifizierung (NTLM).  
  
### <a name="design-for-connecting-to-azure-ad"></a>Entwurf für das Herstellen einer Verbindung mit Azure AD

 Azure AD bietet Identitätsverwaltungs- und Zugriffssteuerungsfunktionen für Clouddienste. Zu den Funktionen zählen ein cloudbasierter Speicher für Verzeichnisdaten und eine Kerngruppe von Identitätsdiensten, einschließlich Anmeldungsprozessen, Authentifizierungsdiensten und AD FS. Die in Azure AD enthaltenen Identitätsdienste lassen sich problemlos in Ihre lokalen AD DS-Bereitstellungen integrieren und unterstützen andere Identitätsanbieter umfassend. 
  
Das zugehörige Diagramm zeigt das folgende Szenario:  
  
Bei der Integration von SharePoint 2013 mit Azure Active Directory dient ein Azure-zugriffssteuerungsdienst (ACS) für zwei Zwecke: 
  
-   Azure AD verwendet SAML 2.0 und SharePoint funktioniert nur mit SAML 1.1. ACS versteht beide Formate und fungiert als Vermittler zum Transformieren der Tokenformate zwischen SharePoint und Azure AD.   
    
- ACS ersetzt die Notwendigkeit des Identitätsanbieter-Sicherheitstokendiensts (IP-STS) für dieses SAML-Szenario.  
    
Weitere Informationen finden Sie in der TechNet-Bibliothek unter „Konfigurieren von Azure AD mit SharePoint 2013“.  
  
## <a name="design-sites-and-urls-for-cross-site-publishing"></a>Entwurf von Websites und URLs für die websiteübergreifende Veröffentlichung

Für die Veröffentlichung wird ein Entwurf mit einer Webanwendung empfohlen.  
  
- Websites zur Dokumenterstellung und zur Veröffentlichung sind in derselben Webanwendung.  
    
- Zur Veröffentlichung von Objekten wird die websiteübergreifende Veröffentlichung verwendet.  
    
Verwenden Sie pfadbasierte und hostbenannte Websitesammlungen.  
  
- Eine Stammwebsitesammlung ist erforderlich. Erstellen Sie diese Website als pfadbasierte Website.  
    
- Erstellen Sie alle anderen Websitesammlungen als hostbenannte Websitesammlungen.  
    
Webanwendung und Stammwebsite-URLs  
  
- Verwenden Sie einen internen Namen für die URL der Webanwendung. SharePoint verwendet den Namen des lokalen Computers als Standardnamen, sofern kein anderer Name angegeben wird. Sie können einen Domänennamen verwenden, der für die interne Netzwerkumgebung reserviert ist.   
    
- SharePoint weist bei der Erstellung der Webanwendung eine nicht standardmäßige Portnummer zu. Verwenden Sie diese Portnummer statt Port 80 oder Port 443. Oder verwenden Sie eine andere nicht standardmäßige Portnummer.  
    
- Verwenden Sie denselben Namen und dieselbe Portnummer für die Stammwebsitesammlung, bei der es sich um eine pfadbasierte Websitesammlung handelt.  
    
Das zugehörige Diagramm zeigt Anwendungspooldienste, z. B. Suchen in Websitesammlungen mithilfe von Webanwendungen. Die gezeigt Websitesammlung enthält:  
  
- Pfadbasierte Websitesammlung unter http://internal:8000 (Stammwebsite). 
    
- Crawl: Websitesammlungen mit Hostnamen an einer Adresse wie https://authoring.contoso.com:8000. 
    
- Abfragen: 2 separate hostbenannte Websitesammlungen, die unter Adresse wie etwa den folgenden zu finden sind:  
    
  - http://www.contoso.com 
    
  - https://secure.contoso.com 
    
  - http://www.contoso.com:8000 
    
  - http://assets.contoso.com 
    
  - https://secureassets.contoso.com 
    
  - http://assets.contoso.com:8000 
    
## <a name="design-the-azure-environment"></a>Entwurf der Azure-Umgebung

Diese Beispielarchitektur umfasst folgende Elemente:  
  
- Eine Standort-zu-Standort-VPN-Verbindung ist optional und weitet die lokale Windows AD DS- und DNS-Umgebung auf das virtuelle Netzwerk in Azure aus.  
    
- Verwenden Sie zur Unterstützung der SharePoint-Farm optional eine dedizierte Domäne in Azure.  
    
- Server werden entsprechend der Rolle auf Azure-Clouddienste verteilt.  
    
- Verfügbarkeitssätze garantieren eine hohe Verfügbarkeit identisch konfigurierten Serverrollen.   
    
Weitere Informationen finden Sie im folgenden TechNet-Artikel: Azure-Architekturen für SharePoint-Lösungen.  
  
Das zugehörige Diagramm zeigt ein Beispiel einer lokalen Umgebung, die mit einem virtuellen Azure-Netzwerk verbunden wird.    
  
Die lokalen Umgebung (ein optionales Element der Azure-Umgebung) umfasst die folgenden Komponenten:  
  
- Windows Server 2012 RRAS  
    
- AD DS 
    
- Ein VPN-Gateway von Windows Server und AD DS zum aktiven VPN-Gateway-Subnetz  
    
Die virtuelle Azure-Netzwerkumgebung umfasst die folgenden Komponenten:  
  
- Das aktive VPN-Gateway-Subnetz (überlappend mit der lokalen Umgebung, falls zutreffend)  
    
- Clouddienst, der AD DS- und DNS-Verfügbarkeitssätze umfasst (zwei Server)  
    
- Clouddienst, der die Verfügbarkeitssätze der Front-End-Server (drei SharePoint Server) und die Verfügbarkeitssätze des App-Servers enthält (drei SharePoint Server)  
    
- Clouddienst, der die beiden Verfügbarkeitssätze für die Datenbanken enthält.  
    

