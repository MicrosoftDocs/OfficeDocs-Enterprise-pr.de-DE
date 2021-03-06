---
title: "Verfügbares Diagramm - Microsoft Exchange 2013-Plattformoptionen"
ms.author: v-suboh
author: v-suboh
ms.date: 12/16/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 129f4e45-647e-4cf1-92a6-4d86d8396e73
description: "Dieser Artikel ist eine leicht zugängliche Textversion des Diagramms namensMicrosoft Exchange 2013-Plattformoptionen, das unter Technische Diagramme verfügbar ist."
---

# Verfügbares Diagramm - Microsoft Exchange 2013-Plattformoptionen

Dieser Artikel ist eine leicht zugängliche Textversion des Diagramms namens "Microsoft Exchange 2013-Plattformoptionen, das unter [Technische Diagramme](http://go.microsoft.com/fwlink/?LinkID=519139) verfügbar ist.
  
Dieses Poster beschreibt, was Unternehmensentscheidungsträger (Business Decision Makers, BDMs) und -architekten über Exchange Online- und Exchange Server-Bereitstellungen wissen müssen. Es umfasst Folgendes:
  
- Vergleich von vier verfügbaren Plattformoptionen für Exchange 2013: Exchange Online (Office 365), Exchange Hybrid, Exchange Server On-Premises und Provider-Hosted Exchange.
    
- Beschreibungen von drei neuen oder aktualisierten Funktionen in Exchange 2013.
    
## Vergleich von vier verschiedenen Bereitstellungen für die Exchange 2013-Plattform

Der Vergleich stellt Informationen zu den einzelnen Bereitstellungsoptionen in den folgenden Bereichen bereit:
  
- Übersicht der verschiedenen Bereitstellungsfeatures
    
- Vorteile des Implementierens der einzelnen Bereitstellungsoptionen
    
- Lizenzierungsanforderungen
    
- Erforderliche Architekturaufgaben
    
- Verantwortlichkeiten der IT-Experten für das Implementieren der einzelnen Bereitstellungsoptionen
    
### Übersicht

#### Exchange Online (Office 365)

Sie gewinnen Effizienz und senken die Kosten mit Office 365.
  
Das begleitende Diagramm zeigt Exchange Online mit einem Azure Active Directory-Mandanten, der Kontonamen und Kennwörter zwischen der lokalen Active Directory-Domänendienste (AD DS)-Umgebung und dem Azure Active Directory-Mandanten synchronisiert. Active Directory-Verbunddienste (AD FS) ist für einmaliges Anmelden (Single Sign-On) erforderlich.
  
Beschreibung der Features und Funktionen:
  
- Der Betrieb von Servern und Serversoftware erfolgt durch Microsoft.
    
- Umfangreiche Funktionen von Exchange Server 2013 als cloudbasierter Dienst.
    
- Immer aktuell mit den neuesten Features.
    
- Exchange Online Protection (EOP) ist zum Schutz vor Spam/Malware enthalten.
    
- Integrierte hohe Verfügbarkeit mit 99,9 % Service Level Agreement (SLA).
    
- Verzeichnissynchronisierung einschließlich Kennwörter zwischen den lokalen Active Directory-Domänendienste (AD DS) und dem Azure Active Directory-Mandanten. Active Directory-Verbunddienste (AD FS) ist für einmalige Anmeldung (Single Sign-On) erforderlich.
    
#### Exchange Hybrid

Sie können die Vorteile von Office 365 nutzen, während Sie Exchange Server lokal beibehalten.
  
Das begleitende Diagramm zeigt Office 365 mit Exchange Online. Einige Benutzer arbeiten lokal und einige arbeiten online. Außerdem zeigt es einen Azure Active Directory-Mandanten, der Kontonamen und Kennwörter zwischen der lokalen Active Directory-Domänendienste (AD DS)-Umgebung und dem Azure Active Directory-Mandanten synchronisiert.
  
Beschreibung von Features und Funktionen:
  
- Einige Benutzer arbeiten lokal und einige arbeiten online. Außerdem nutzen die Benutzer gemeinsam den gleichen E-Mail-Adressbereich.
    
- Nutzt Ihre vorhandene Exchange Server-Infrastruktur.
    
- Langsame Migration vom lokalen Exchange zu Exchange Online, ganz nach Ihrem Zeitplan.
    
- Integration in andere Office 365-Anwendungen, einschließlich Lync Online und SharePoint Online.
    
#### Exchange Server (lokal)

Sie können Ihre eigene Exchange Server 2013-Infrastruktur entwerfen und verwalten.
  
Das begleitende Diagramm zeigt eine Exchange Server-Infrastruktur mit einer lokalen Active Directory-Domänendienste (AD DS)-Umgebung, in der Benutzer lokal arbeiten.
  
Beschreibung von Features und Funktionen:
  
- Größtmögliche Kontrolle und Anpassung Ihrer Konfiguration.
    
- Keine Abhängigkeit beim Beibehalten der Sitzungsaffinität auf der Lastenausgleichsebene.
    
- Einfache hohe Verfügbarkeit und Websitezuverlässigkeit mit Datenbankverfügbarkeitsgruppen (Database Availability Groups, DAGs).
    
- Verwaltete Verfügbarkeit, die es Ihnen ermöglicht, eine großartige Benutzererfahrung beizubehalten.
    
- Nutzen der vorhandenen Hardware- und Speicherinfrastruktur.
    
#### Provider-Hosted Exchange

Sie können Ihre Exchange Server-Arbeitslast an einen Exchange Server-Lösungsanbieter outsourcen.
  
Das begleitende Diagramm zeigt eine Exchange Server-Umgebung, die von einem Anbieter betrieben und verwaltet wird.
  
Beschreibung von Features und Funktionen:
  
- Der Betrieb von Servern und Serversoftware erfolgt durch Ihren Anbieter.
    
- Planung, Größenanpassung, Skalierung und Wartung der Exchange Server-Infrastruktur werden an Ihren Anbieter delegiert.
    
- Dienstwartung erfolgt durch Ihren Anbieter.
    
- Die Exchange-Funktionen sind auf die von Ihrem Anbieter bereitgestellte Softwareversion beschränkt.
    
### Vorteile des Implementierens der einzelnen Bereitstellungsoptionen

#### Exchange Online (Office 365)

Diese Bereitstellungsoption eignet sich am besten für:
  
- Organisationen, die Betriebskosten für lokale Exchange-Bereitstellungen senken möchten.
    
- Organisationen, die andere Office 365-Angebote nutzen möchten, zum Beispiel SharePoint Online und Lync Online.
    
#### Exchange Hybrid

Diese Bereitstellungsoption eignet sich am besten für:
  
- Durchführen einer Migration von Exchange (lokal) zu Exchange Online.
    
- Unterstützen von Remotestandorten ohne Investitionen in eine Zweigstelleninfrastruktur.
    
- Multinationale Unternehmen mit Filialen, die Daten am Standort benötigen.
    
#### Exchange Server (lokal)

Diese Bereitstellungsoption eignet sich am besten für:
  
- Hoch angepasste Lösungen.
    
- Ältere Lösungen mit Drittanbieterkomponenten, die auf Hardware und Software angewiesen sind, die nicht von Exchange Online unterstützt werden.
    
- Organisationen, die behördlichen Regelungen unterliegen, die lokale Daten benötigen.
    
- Organisationen, die die Kontrolle über die gesamte Plattform und Lösung behalten möchten.
    
#### Provider-Hosted Exchange

Diese Bereitstellungsoption eignet sich am besten für:
  
- Organisationen, die Exchange Server-Funktionen benötigen, die Bereitstellung und Wartung aber outsourcen möchten.
    
- Organisationen, die persönliche Supportoptionen benötigen.
    
- Angepasste Lösungen und Integration in benutzerdefinierte, vom Anbieter bereitgestellte Anwendungen.
    
- Ältere Lösungen mit Drittanbieterkomponenten, die von Hardware und Software abhängen, die nicht von Exchange Online unterstützt werden.
    
### Lizenzanforderungen

In der folgenden Tabelle werden die Lizenzanforderungen für die einzelnen Bereitstellungsoptionen aufgelistet.
  
|**Bereitstellungsoption**|**Lizenzanforderungen**|
|:-----|:-----|
|Exchange Online (Office 365)  <br/> |Abonnementmodell  <br/> |
|Exchange Hybrid  <br/> | Office 365 - Abonnementmodell <br/>  Lokal - es gelten alle lokalen Lizenzen (überprüfen Sie Lizenzen für Exchanges Server (lokal)) <br/>  Hybrid-Serverlizenz* <br/> |
|Exchange Server (lokal)  <br/> | Serverbetriebssystem <br/>  Exchange 2013-Serverlizenz <br/>  Exchange 2013-Clientzugriffslizenz <br/> |
|Provider-Hosted Exchange  <br/> |Kosten basieren auf der Vereinbarung mit dem Anbieter  <br/> |
   
### Architekturaufgaben

In diesem Abschnitt werden die Architekturaufgaben für die einzelnen Bereitstellungsoptionen aufgelistet.
  
#### Exchange Online (Office 365)

- Planen und Entwerfen der Verzeichnissynchronisierung.
    
- Sicherstellen der Netzwerkkapazität und -konnektivität über Firewalls, Proxyserver, Gateways und WAN-Links hinweg.
    
#### Exchange Hybrid

Zusätzlich zu den Architekturaufgaben für die Office 365- und die lokale Umgebung:
  
- Entscheiden, ob die einmalige Anmeldung (Single-Sign On) bereitgestellt werden soll.
    
- Entscheiden, ob eingehende Internet-E-Mails durch eine lokale Organisation oder durch Exchange Online Protection weitergeleitet werden sollen.
    
#### Exchange Server (lokal)

- Entwerfen der Exchange-Topologie.
    
- Planen der Kapazität für Serverhardware.
    
- Entwerfen der Mitteilungsweiterleitungstopologie.
    
- Entwerfen des Lastenausgleichs für Clientzugriffsserver.
    
- Planen der hohen Verfügbarkeit mithilfe von Datenbankverfügbarkeitsgruppen.
    
#### Provider-Hosted Exchange

Sicherstellen, dass die Netzwerkkapazität und -verfügbarkeit über Firewalls, Proxyserver, Gateways und WAN-Links hinweg für Ihren Anbieter zur Verfügung stehen.
  
### Verantwortlichkeiten von IT-Experten

In diesem Abschnitt werden die Verantwortlichkeiten der IT-Experten für die einzelnen Bereitstellungsoptionen aufgelistet.
  
#### Exchange Online (Office 365)

- Implementieren des Verzeichnissynchronisierungsplans.
    
- Planen und Implementieren interner und externer DNS-Datensätze sowie des entsprechenden Routings.
    
- Konfigurieren des Proxyservers oder der Firewall für die Office 365-IP-Adress- und -URL-Anforderungen.
    
- Verwalten der Benutzerkonten und der Exchange Online-Einstellungen.
    
#### Exchange Hybrid

Zusätzlich zu den Verantwortlichkeiten der IT-Experten für die Office 365- und die lokale Umgebung:
  
- Konfigurieren von Active Directory-Verbunddienste (AD FS) für die einmalige Anmeldung (Single-Sign On) (falls gewünscht).
    
- Konfigurieren von Exchange-Zertifikaten für die sichere Kommunikation zwischen Exchange 2013-Servern und Office 365.
    
- Konfigurieren von DNS-Datensätzen für den gewünschten Pfad für eingehende Internet-E-Mails.
    
#### Exchange Server (lokal)

- Konfigurieren der erforderlichen Zertifikate für Exchange-Dienste.
    
- Bereitstellen der Server.
    
- Implementieren der Exchange-Nachrichtenroutingtopologie.
    
- Implementieren von Datenbankverfügbarkeitsgruppen.
    
- Aktualisieren und Warten von Exchange-Servern.
    
- Je nach Nutzung ggf. Hinzufügen oder Entfernen von Servern.
    
#### Provider-Hosted Exchange

Zu den Verantwortlichkeiten des Anbieter gehören folgende:
  
- System- und Dienstwartung.
    
- Feature-Rollouts.
    
- Datenschutz und Notfallwiederherstellung.
    
Die Verantwortlichkeiten der IT-Mitarbeiter Ihrer Organisation umfassen das Erstellen und Verwalten von Benutzerkonten.
  
#### Weitere Informationen

Weitere Informationen zu Exchange Online (Office 365) finden Sie hier:
  
- [Exchange Online-Dienstbeschreibung](https://aka.ms/EXOSD)
    
- [Exchange Online-Bibliothek auf TechNet](https://aka.ms/EXOTN)
    
- [Exchange Online-Portal](https://aka.ms/EXO)
    
Weitere Informationen zu Exchange Hybrid finden Sie hier:
  
- [Exchange 2013-Hybridbereitstellungen](https://aka.ms/ExchangeHybrid). Beachten Sie, dass die Hybrid-Serverlizenz nur für die folgenden Szenarios erforderlich ist: Exchange 2010-Organisation mit Exchange 2013-Hybridserver und Exchange 2007-Organisation mit Exchange 2013- oder Exchange 2010-Hybridserver.
    
- [Office 365-Anmeldung](https://aka.ms/HybridKey)
    
- 
    
Weitere Informationen zu Exchange Server (lokal) finden Sie hier:
  
- [Exchange Server 2013-Bibliothek auf TechNet](https://aka.ms/Ex2013TN)
    
- [Exchange Server 2013-Portal](https://aka.ms/Exchange2013)
    
- [Exchange Server 2013-Architektur](https://aka.ms/Ex2013SP1ArchPoster)
    
Weitere Informationen zu Provider-Hosted Exchange finden Sie hier:
  
[Exchange Server 2013-Hosting und Lösungen mit mehreren Mandanten sowie Anleitungen](https://aka.ms/Ex2013Hosting)
  
## Beschreibung von drei neuen oder aktualisierten Features in Exchange 2013

### Exchange Online Protection

Exchange Online Protection (EOP) bietet Schutz vor Spam und Malware für jede Bereitstellung durch Schutzebenenfunktionen, die über ein globales Netzwerk mit Rechenzentren bereitgestellt wird. Auf diese Weise können Sie die Verwaltung Ihrer Messagingumgebungen vereinfachen. EOP ist in Exchange Online-Abonnements enthalten, Sie können EOP aber auch für Hybrid- und lokale Bereitstellungen nutzen.
  
Die begleitenden Diagramme zeigen Bereitstellungen für Exchange Online, Exchange Hybrid und Exchange (lokal), die die EOP-Schicht im globalen Netzwerk umfassen.
  
### Exchange Server-Bereitstellungs-Assistent

Der Exchange Server-Bereitstellungs-Assistent ist ein webbasiertes Tool, das Ihnen einige Fragen zur aktuellen Umgebung stellt und dann eine benutzerdefinierte, schrittweise Checkliste generiert, mit der Sie Exchange Server für verschiedene Szenariotypen bereitstellen können. Der Exchange Server-Bereitstellungs-Assistent erstellt eine benutzerdefinierte Bereitstellungscheckliste für Ihr Szenario, egal, ob Sie von einer vorherigen Version von Exchange zu Exchange 2013 oder Exchange Online migrieren oder eine Hybridinfrastruktur planen.
  
Der begleitende Screenshot zeigt eine Beispielcheckliste, die mithilfe des Exchange Server-Bereitstellungs-Assistenten erstellt wurde.
  
### Integration in Lync und SharePoint

Exchange Server 2013 umfasst viele Features, die in Lync Server 2013 und SharePoint Server 2013 integriert werden. Zusammen bieten diese Produkte eine umfangreiche Suite mit Features und verbessern die Zusammenarbeit in der gesamten Organisation.
  
Ein begleitendes Diagramm zeigt das Server-zu-Server-Authentifizierungsposter und enthält einen Link zum Poster.
  
- Archivierung, Beibehaltung und eDiscovery
    
- Website-Postfächer
    
- Einheitlicher Kontaktspeicher
    
- Hochauflösende Benutzerfotos
    
- Lync-Präsenz in Outlook und Outlook Web App
    
- Server-zu-Server-Authentifizierung
    
- Voicemail
    
- Besprechungsaufzeichnungen
    
- Exchange-Aufgabensynchronisierung
    
Ein begleitendes Diagramm zeigt das Exchange Server 2013 SP1-Architekturposter und enthält einen Link zum Poster.
  

