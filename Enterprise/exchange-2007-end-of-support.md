---
title: Ende der Unterstützung für Exchange 2007 – Roadmap
ms.author: dstrome
author: dstrome
manager: laurawi
ms.date: 1/31/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.assetid: c3024358-326b-404e-9fe6-b618e54d977d
description: Am 11. April 2017 wurde Exchange Server 2007 am Ende des Supports unterstützt. Wenn Sie die Migration von Exchange 2007 zu Office 365 oder Exchange 2016 noch nicht begonnen haben, können Sie mit der Planung beginnen.
ms.openlocfilehash: 08796407e41fcc249da709267301de94fc359f36
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067611"
---
# <a name="exchange-2007-end-of-support-roadmap"></a>Ende der Unterstützung für Exchange 2007 – Roadmap

Am **11. April 2017**wurde Exchange Server 2007 am Ende des Supports unterstützt. Wenn Sie die Migration von Exchange 2007 zu Office 365 oder Exchange 2016 noch nicht begonnen haben, können Sie mit der Planung beginnen. 
  
## <a name="what-does-end-of-support-mean"></a>Was bedeutet End-of-Support?

Exchange Server hat, wie fast alle Microsoft-Produkte, einen Supportlebenszyklus, in dem wir neue Features, Bugfixes, Sicherheitsfixes usw. bereitstellen. Dieser Lebenszyklus dauert in der Regel 10 Jahre ab dem Datum der ersten Version des Produkts, und das Ende dieses Lebenszyklus wird als Ende des Supports des Produkts bezeichnet. Seit Exchange 2007 das Ende der Unterstützung am 11. April 2017 erreicht hat, bietet Microsoft nicht mehr Folgendes an:
  
- Technischer Support für Probleme, die auftreten können;
    
- Fehlerbehebungen für erkannte Probleme, die die Stabilität und Benutzerfreundlichkeit des Servers beeinträchtigen können
    
- Sicherheitsfixes für erkannte Schwachstellen, die den Server anfällig für Sicherheitsverstöße machen können;
    
- Zeitzonenaktualisierungen.
    
Die Installation von Exchange 2007 wird nach diesem Datum fortgesetzt. Aufgrund der oben aufgeführten Änderungen wird jedoch dringend empfohlen, dass Sie so bald wie möglich eine Migration von Exchange 2007 durchführen.
  
Weitere Informationen zu Office 2007-Servern, die sich am Ende des Supports befinden, finden Sie unter [Planen des Upgrades von Office 2007-Servern und-Produkten](upgrade-from-office-2007-servers-and-products.md).
  
## <a name="what-are-my-options"></a>Was sind meine Optionen?

Nachdem Exchange 2007 den Support beendet hat, wird dringend empfohlen, sich mit den Optionen vertraut zu machen und einen Migrationsplan vorzubereiten. Sie können:
  
- Migrieren zu Office 365 mithilfe von Cutover-, Staging-oder Hybrid Migrationen;
    
- Migrieren Sie Ihre Exchange 2007-Server zu einer neueren Version von Exchange auf Ihren lokalen Servern.
    
In den folgenden Abschnitten werden die einzelnen Optionen detaillierter erläutert.
  
### <a name="migrate-to-office-365"></a>Migrieren zu Office 365

Die Migration Ihrer e-Mails zu Office 365 ist die beste und einfachste Option, die Ihnen bei der Pensionierung Ihrer Exchange 2007-Bereitstellung hilft. Mit einer Migration zu Office 365 können Sie einen einzelnen Hop von der 10-jährigen Technologie zu den neuesten Features machen, wie etwa:
  
- Compliance-Funktionen wie Aufbewahrungsrichtlinien, in-situ-und Gerichtsverfahren, in-situ-eDiscovery und vieles mehr;
    
- Office 365-Gruppen;
    
- Fokussierter Posteingang;
    
- Analysieren von Analysen;
    
- Rest-APIs für den programmgesteuerten Zugriff auf e-Mails, Kalender, Kontakte usw.
    
Office 365 erhält auch neue Features und Erfahrungen zuerst, und Sie und Ihre Benutzer können Sie normalerweise sofort verwenden. Zusätzlich zu den neuen Features müssen Sie sich keine Gedanken machen:
  
- Erwerb und Wartung von Hardware;
    
- Bezahlen für das Heizen und kühlen Ihrer Server;
    
- Aktualisierung der Sicherheits-, Produkt-und Zeit Zonen Korrekturen auf dem neuesten Stand
    
- Verwalten von Speicher und Software zur Unterstützung von Compliance-Anforderungen
    
- Upgrade auf eine neue Version von Exchange-Sie sind immer auf der neuesten Version von Exchange in Office 365.
    
#### <a name="how-should-i-migrate-to-office-365"></a>Wie sollte ich zu Office 365 migrieren?

Je nach Organisation haben Sie einige Optionen, die Ihnen bei der Verwaltung von Office 365 helfen. Bei der Auswahl einer Migrationsoption müssen Sie einige Dinge berücksichtigen, wie beispielsweise die Anzahl der zu verschiebenden Sitze oder Postfächer, die Dauer der Migration und die Notwendigkeit einer nahtlosen Integration zwischen Ihrer lokalen Installation und Office 365 während die Migration. In dieser Tabelle sind die Migrationsoptionen und die wichtigsten Faktoren aufgeführt, die bestimmen, welche Methode Sie verwenden.
  
| |
|**Migrationsoption**|**Organisationsgröße**|**Duration**|
|:-----|:-----|:-----|
|Übernahmemigration  <br/> |Weniger als 150 Sitze  <br/> |Woche oder kleiner  <br/> |
|Mehrstufige Migration  <br/> |Mehr als 150 Sitze  <br/> |Einige Wochen  <br/> |
|Vollständige Hybrid Migration  <br/> |Mehrere hundert bis Tausende von sitzen  <br/> |Ein paar Monate oder mehr  <br/> |
   
Die folgenden Abschnitte enthalten eine Übersicht über diese Methoden. Auschecken entscheiden Sie sich für [einen Migrationspfad](https://support.office.com/en-us/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27) , um die Details der einzelnen Methoden zu erfahren. 
  
#### <a name="cutover-migration"></a>Übernahmemigration

Eine Cutover Migration ist eine, bei der Sie zu einem vordefinierten Datum und einer bestimmten Uhrzeit alle ihre Postfächer, Verteilergruppen, Kontakte usw. zu Office 365 migrieren. Wenn Sie fertig sind, schließen Sie Ihre lokalen Exchange-Server, und beginnen Sie mit der Verwendung von Office 365 exklusiv.
  
Die Cutover-Migrationsmethode eignet sich hervorragend für kleine Organisationen, die nicht über sehr viele Postfächer verfügen, schnell zu Office 365 und nicht mit einigen der Komplexitäten der anderen Methoden umgehen möchten. Aber es ist auch etwas begrenzt, da es in einer Woche oder weniger abgeschlossen werden sollte und dass Benutzer Ihre Outlook-Profile neu konfigurieren müssen. Während die Cutover-Migration bis zu 2.000 Postfächer verarbeiten kann, wird dringend empfohlen, maximal 150 Postfächer mit dieser Methode zu migrieren. Wenn Sie versuchen, mehr als 150 Postfächer zu migrieren, können Sie die Zeit für die Übertragung aller Postfächer vor dem Stichtag nicht überschreiten, und Ihr IT-Supportmitarbeiter kann überlastet werden, um Benutzer neu zu konfigurieren.
  
Wenn Sie eine Cutover Migration durchführen möchten, sollten Sie Folgendes in Betracht ziehen:
  
- Office 365 muss mit Outlook Anywhere über TCP-Anschluss 443 eine Verbindung zu Ihren Exchange 2007-Servern herstellen.
    
- Alle lokalen Postfächer werden in Office 365 verschoben.
    
- Sie benötigen ein lokales Administratorkonto, das Zugriff auf den Inhalt der Postfächer Ihrer Benutzer hat;
    
- Die akzeptierten Exchange 2007-Domänen, die Sie in Office 365 verwenden möchten, müssen im Dienst als verifizierte Domänen hinzugefügt werden.
    
- Zwischen dem Start der Migration und dem Beginn der Abschlussphase synchronisiert Office 365 regelmäßig die Office 365-und lokalen Postfächer. Auf diese Weise können Sie die Migration abschließen, ohne sich Gedanken darüber machen zu müssen, dass e-Mails in Ihren lokalen Postfächern hinterlassen werden.
    
- Benutzer erhalten neue temporäre Kennwörter für Ihr Office 365-Konto, die Sie ändern müssen, wenn Sie sich zum ersten Mal bei ihren Postfächern anmelden;
    
- Sie benötigen eine Office 365-Lizenz, die Exchange Online für jedes Benutzerpostfach umfasst, das Sie migrieren;
    
- Benutzer müssen auf jedem Ihrer Geräte ein neues Outlook-Profil einrichten und Ihre e-Mails erneut herunterladen. Die Menge an e-Mails, die Outlook herunterlädt, kann variieren. Weitere Informationen finden Sie unter [Ändern der Menge von e-Mails, die offline bleiben sollen](https://support.office.com/en-us/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&amp;rs=en-US&amp;ad=US&amp;fromAR=1).
    
Weitere Informationen zur Migration von Cutover finden Sie unter:
  
- [Wissenswertes zu einer Übernahmemigration von E-Mails zu Office 365](https://support.office.com/en-us/article/What-you-need-to-know-about-a-cutover-email-migration-to-Office-365-961978ef-f434-472d-a811-1801733869da)
    
- [Durchführen einer Cutover Migration von e-Mails zu Office 365](https://support.office.com/en-us/article/Perform-a-cutover-migration-of-email-to-Office-365-9496e93c-1e59-41a8-9bb3-6e8df0cd81b4)
    
#### <a name="staged-migration"></a>Mehrstufige Migration

Eine phasenweise Migration ist eine, bei der Sie ein paar hundert oder ein paar tausend Postfächer haben, die Sie zu Office 365 migrieren möchten, eine Woche oder mehr benötigen, um die Migration abzuschließen, und keine der erweiterten Hybrid Migrations Features wie freigegebene Frei/Gebucht-Kalenderinformationen benötigen. rmationen.
  
Die stufenweise Migration eignet sich für Organisationen, die mehr Zeit benötigen, um ihre Postfächer zu Office 365 zu migrieren, aber dennoch die Migration innerhalb weniger Wochen abschließen möchten. Sie können Postfächer in Batches migrieren, um zu steuern, wie viele und welche Postfächer zu einem bestimmten Zeitpunkt migriert werden. Sie können beispielsweise Postfächer von Benutzern in derselben Abteilung Stapeln, um sicherzustellen, dass Sie alle gleichzeitig verschoben werden. Sie können auch Führungskräfte-Postfächer bis zum letzten Batch verlassen. Wie bei Cutover-Migrationen müssen Ihre Benutzer Ihre Outlook-Profile neu erstellen.
  
Wenn Sie sich Gedanken über eine phasenweise Migration machen, finden Sie hier einige Punkte, die Sie berücksichtigen sollten:
  
- Office 365 muss mit Outlook Anywhere über TCP-Anschluss 443 eine Verbindung zu Ihren Exchange 2007-Servern herstellen.
    
- Sie benötigen ein lokales Administratorkonto, das Zugriff auf den Inhalt der Postfächer Ihrer Benutzer hat;
    
- Die akzeptierten Exchange 2007-Domänen, die Sie in Office 365 verwenden möchten, müssen im Dienst als verifizierte Domänen hinzugefügt werden.
    
- Sie müssen eine CSV-Datei mit dem vollständigen Namen und der e-Mail-Adresse jedes Postfachs erstellen, das in einem Batch migriert werden soll. Außerdem müssen Sie für jedes Postfach, das Sie migrieren, ein neues Kennwort hinzufügen und dann Ihr Kennwort an jeden Benutzer senden. Der Benutzer wird aufgefordert, das Kennwort bei der ersten Anmeldung bei seinem neuen Office 365-Postfach zu ändern.
    
- Zwischen dem Start des Migrationsbatches und dem Beginn der Abschlussphase synchronisiert Office 365 regelmäßig die im Batch enthaltenen Office 365-und lokalen Postfächer. Auf diese Weise können Sie die Migration abschließen, ohne sich Gedanken darüber machen zu müssen, dass e-Mails in Ihren lokalen Postfächern hinterlassen werden.
    
- Benutzer erhalten neue temporäre Kennwörter für Ihr Office 365-Konto, die Sie ändern müssen, wenn Sie sich zum ersten Mal bei Ihrem Postfach anmelden.
    
- Sie benötigen eine Office 365-Lizenz, die Exchange Online für jedes Benutzerpostfach umfasst, das Sie migrieren;
    
- Benutzer müssen auf jedem Ihrer Geräte ein neues Outlook-Profil einrichten und Ihre e-Mails erneut herunterladen. Die Menge an e-Mails, die Outlook herunterlädt, kann variieren. Weitere Informationen finden Sie unter [Ändern der Menge von e-Mails, die offline bleiben sollen](https://support.office.com/en-us/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&amp;rs=en-US&amp;ad=US&amp;fromAR=1).
    
Weitere Informationen zur bereitgestellten Migration finden Sie unter:
  
- [Wichtige Informationen zur mehrstufigen E-Mail-Migration zu Office 365](https://support.office.com/en-us/article/What-you-need-to-know-about-a-staged-email-migration-to-Office-365-7e2c82be-5f3d-4e36-bc6b-e5b4d411e207)
    
- [Durchführen einer stufenweisen Migration von e-Mails zu Office 365](https://support.office.com/en-us/article/Perform-a-staged-migration-of-email-to-Office-365-83bc0b69-de47-4cc4-a57d-47e478e4894e)
    
#### <a name="full-hybrid"></a>Vollhybrid

Eine vollständige Hybrid Migration ist eine, in der Ihre Organisation viele hundert, bis zu Zehntausende von Postfächern hat und Sie einige oder alle in Office 365 verschieben möchten. Da diese Migrationen in der Regel längerfristig sind, ermöglichen Hybrid Migrationen Folgendes:
  
- Anzeigen von lokalen Benutzern die Frei/Gebucht-Kalenderinformationen für Benutzer in Office 365 und umgekehrt;
    
- Siehe eine vereinheitlichte globale Adressliste, die Empfänger sowohl in lokal als auch in Office 365 enthält.
    
- Anzeigen vollständiger Outlook-empfängerkarten für alle Benutzer, unabhängig davon, ob Sie lokal oder in Office 365 sind;
    
- Sichere e-Mail-Kommunikation zwischen lokalen Exchange-Servern und Office 365 mit TLS und Zertifikaten;
    
- Behandeln Sie Nachrichten, die zwischen lokalen Exchange-Servern und Office 365 gesendet werden, als intern, sodass Sie folgende Möglichkeiten haben:
    
  - Ordnungsgemäß ausgewertet und verarbeitet von Transport-und Compliance-Agents für interne Nachrichten;
    
  - Antispam-Filter umgehen.
    
Vollständige Hybrid Migrationen eignen sich am besten für Organisationen, die sich für viele Monate oder länger in einer Hybrid Konfiguration aufhalten. Sie erhalten die weiter oben in diesem Abschnitt aufgeführten Features sowie die Verzeichnissynchronisierung, bessere integrierte Compliance-Funktionen und die Möglichkeit, Postfächer mithilfe von Online-Postfachverschiebungen zu und von Office 365 zu verschieben. Office 365 wird zu einer Erweiterung Ihrer lokalen Organisation.
  
Wenn Sie eine vollständige Hybrid Migration durchführen möchten, sollten Sie Folgendes in Betracht ziehen:
  
- Vollständige Hybrid Migrationen sind nicht für alle Arten von Organisationen geeignet. Aufgrund der Komplexität vollständiger Hybrid Migrationen können Organisationen mit weniger als ein paar hundert Postfächern normalerweise keine Vorteile erkennen, die den Aufwand und die Kosten für die Einrichtung eines solchen Typs rechtfertigen. Wenn dies wie Ihre Organisation klingt, empfehlen wir Ihnen dringend, stattdessen Cutover oder inszenierte Migrationen zu erwägen.
    
- Sie müssen mindestens einen Exchange 2013-Server in Ihrer Exchange 2007-Organisation bereitstellen, um als "hybridserver" zu fungieren. Dieser Server kommuniziert mit Office 365 im Namen Ihrer Exchange 2007-Server;
    
- Office 365 muss mit Outlook Anywhere über TCP-Anschluss 443 eine Verbindung mit dem "hybridserver" herstellen.
    
- Sie müssen die Verzeichnissynchronisierung mit Azure Active Directory Connect (AADConnect) zwischen Ihren lokalen Active Directory-Servern und Office 365 einrichten.
    
- Benutzer können sich mit demselben Benutzernamen und Kennwort bei Ihrem Office 365-Postfach anmelden, wenn Sie sich beim lokalen Netzwerk anmelden (erfordert Azure Active Directory Connect mit Kennwortsynchronisierung und/oder Active Directory-Verbunddienste).
    
- Sie benötigen eine Office 365-Lizenz, die Exchange Online für jedes Benutzerpostfach umfasst, das Sie migrieren;
    
- Benutzer müssen auf den meisten Geräten kein neues Outlook-Profil einrichten (einige ältere Android-Telefone benötigen möglicherweise ein neues Profil) und müssen Ihre e-Mails nicht erneut herunterladen.
    
Wenn eine vollständige Hybrid Migration für Sie geeignet ist, sehen Sie sich die folgenden Ressourcen an, die Ihnen bei der Migration helfen:
  
- [Exchange-Bereitstellungs-Assistent](https://aka.ms/exdeploy)
    
- [Hybridbereitstellungen in Exchange Server](https://technet.microsoft.com/en-us/library/jj200581%28v=exchg.150%29.aspx)
    
- [Assistent für die Hybridkonfiguration](https://technet.microsoft.com/en-us/library/hh529921%28v=exchg.150%29.aspx)
    
- [FAQs zum Assistenten für die Hybridkonfiguration](https://technet.microsoft.com/en-us/library/mt488940%28v=exchg.150%29.aspx)
    
- [Voraussetzungen für die Hybridbereitstellung](https://technet.microsoft.com/en-us/library/hh534377%28v=exchg.150%29.aspx)
    
### <a name="migrate-to-a-newer-version-of-exchange-server"></a>Migrieren zu einer neueren Version von Exchange Server

Obwohl wir fest davon ausgehen, dass Sie durch die Migration zu Office 365 den bestmöglichen Nutzen und die Benutzerfreundlichkeit erzielen können, wissen wir, dass einige Organisationen ihre e-Mails lokal aufbewahren müssen. Dies kann auf regulatorische Anforderungen hinweisen, um sicherzustellen, dass Daten nicht in einem Rechenzentrum in einem anderen Land gespeichert werden, und so weiter. Wenn Sie Ihre e-Mails lokal beibehalten möchten, können Sie Ihre Exchange 2007-Umgebung zu Exchange 2010, Exchange 2013 oder Exchange 2016 migrieren.
  
Es wird empfohlen, zu Exchange 2016 zu migrieren, wenn Sie nicht zu Office 365 migrieren können. Exchange 2016 enthält alle Features und Fortschritte, die in früheren Versionen von Exchange enthalten sind, und entspricht den verfügbaren Funktionen von Office 365 (obwohl einige Features nur in Office 365 verfügbar sind). Sehen Sie sich die folgenden Dinge an:
  
|**Exchange-Release**|**Features**|
|:-----|:-----|
|Exchange 2010  <br/> | Rollenbasierte Zugriffssteuerung (Berechtigungen ohne ACLs)  <br/>  Outlook Web Access-Postfachrichtlinien  <br/>  Möglichkeit zum Freigeben von frei/gebucht-und Delegieren von Kalendern zwischen Organisationen  <br/> |
|Exchange 2013  <br/> | *Features von Exchange 2010 und...*  <br/>  Vereinfachte Architektur reduziert die Anzahl der Serverrollen auf drei (Postfach, Client Zugriff, Edge-Transport)  <br/>  Richtlinien zur Verhinderung von Datenverlust (DLP), die dazu beitragen, vertrauliche Informationen nicht zu verlieren  <br/>  Deutlich verbesserte Outlook Web App-Umgebung  <br/> |
|Exchange 2016  <br/> | *Features von Exchange 2013 und...*  <br/>  Weitere vereinfachte Serverrollen nur für Postfach-und Edge-Transport  <br/>  Verbesserte DLP zusammen mit Integration in SharePoint  <br/>  Verbesserte Ausfallsicherheit von Datenbanken  <br/>  Online Dokument Zusammenarbeit  <br/> |
   
#### <a name="which-version-should-i-migrate-to"></a>Zu welcher Version soll ich migrieren?

Es wird empfohlen, dass Sie zunächst davon ausgehen, dass Sie zu Exchange 2016 migrieren. Verwenden Sie dann die folgenden Informationen, um Ihre Annahme zu bestätigen oder um Exchange 2016 auszuschließen. Wenn Sie aus einem oder einem anderen Grund nicht zu Exchange 2016 migrieren können, führen Sie den gleichen Vorgang mit Exchange 2013 aus.
  
|**Berücksichtigt**|**Weitere Informationen**|
|:-----|:-----|
|Ende der Support Termine  <br/> | Wie bei Exchange 2007 hat jede Version von Exchange ein eigenes Ende des Support-Datums:  <br/> **Exchange 2010** -Januar 2020  <br/> **Exchange 2013** -April 2023  <br/> **Exchange 2016** -Oktober 2025  <br/>  Je früher das Datum des Support Endes, desto schneller müssen Sie eine weitere Migration durchführen. Januar 2020 ist viel näher, als Sie denken!  <br/> |
|Migrationspfad zu Exchange 2010 und 2013  <br/> |Hier sind die allgemeinen Phasen für die Migration zu Exchange 2010 oder Exchange 2013:  <br/> Installieren von Exchange 2010 oder 2013 in Ihrer vorhandenen Exchange 2007-Organisation Verschiebungs Dienste und andere Infrastruktur zu Exchange 2010 oder 2013 Verschieben von Postfächern und öffentlichen Ordnern in Exchange 2010 oder 2013 decommission Rest Exchange 2007 Servers |
|Migrationspfad zu Exchange 2016  <br/> |Hier sind die allgemeinen Phasen für die Migration zu Exchange 2016:  <br/> Installieren von Exchange 2013 in Ihre vorhandene Exchange 2007-Organisation Verschiebungs Dienste und andere Infrastruktur zu Exchange 2013 Verschieben von Postfächern und öffentlichen Ordnern zu Exchange 2013 decommission verbleibende Exchange 2007-Server installieren Exchange 2016 in Ihre vorhandene Exchange 2013-Organisation. Verschieben Sie Postfächer, öffentliche Ordner, Dienste und andere Infrastrukturen zu Exchange 2016 (Order does not matter). Außerbetriebnahme der restlichen Exchange 2013-Server [!NOTE]> > Migration von Exchange 2013 zu Exchange 2016 ist einfach. Beide Versionen weisen fast die gleichen Hardwareanforderungen auf. Dies und die Tatsache, dass diese Versionen so kompatibel sind, bedeuten, dass Sie einen Server, den Sie für Exchange 2013 erworben haben, neu erstellen und Exchange 2016 darauf installieren können. Bei Online Postfachverschiebungen bemerken die meisten Benutzer nie, dass Ihr Postfach vom Server verschoben und dann wieder zurückgegeben wird, nachdem Sie es mit Exchange 2016 neu erstellt haben.           |
|Koexistenz der Version  <br/> | Bei der Migration zu:  <br/> **Exchange 2016** Exchange 2016 kann nicht in einer Organisation installiert werden, die einen Exchange 2007-Server enthält. Sie müssen zunächst zu Exchange 2010 oder 2013 migrieren (es wird dringend empfohlen, Exchange 2013), alle Exchange 2007-Server zu entfernen und dann zu Exchange 2016 zu migrieren.  <br/> **Exchange 2010 oder Exchange 2013** Sie können Exchange 2010 oder Exchange 2013 in einer vorhandenen Exchange 2007-Organisation installieren. Auf diese Weise können Sie einen oder mehrere Exchange 2010-oder 2013-Server installieren und Ihre Migration durchführen.  <br/> |
|Serverhardware  <br/> | Die Server Hardwareanforderungen wurden von Exchange 2007 geändert. Sie müssen sicherstellen, dass die verwendete Hardware kompatibel ist. Weitere Informationen zu den Hardwareanforderungen für jede Version finden Sie hier:  <br/> [System Anforderungen für Exchange 2016](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx) <br/> [System Anforderungen für Exchange 2013](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx) <br/> [System Anforderungen für Exchange 2010](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.141%29.aspx) <br/>  Sie werden feststellen, dass Sie mit den deutlichen Verbesserungen der Exchange-Leistung und der erhöhten Rechenleistung und Speicherkapazität auf neueren Servern wahrscheinlich weniger Server benötigen, um die gleiche Anzahl von Postfächern zu unterstützen.  <br/> |
|Betriebssystemversion  <br/> | Die mindestens unterstützten Betriebssystemversionen für jede Version sind:  <br/> **Exchange 2016** Windows Server 2012  <br/> **Exchange 2013** Windows Server 2008 R2 SP1  <br/> **Exchange 2010** Windows Server 2008 SP2  <br/>  Weitere Informationen zur Betriebssystemunterstützung finden Sie unter [Exchange supportable Matrix](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).  <br/> |
|Funktionsebene der Active Directory-Gesamtstruktur  <br/> | Die mindestens unterstützten Active Directory-Gesamtstrukturfunktionsebenen für jede Version sind:  <br/> **Exchange 2016** Windows Server 2008 R2 SP1  <br/> **Exchange 2013** Windows Server 2003  <br/> **Exchange 2010** Windows Server 2003  <br/>  Weitere Informationen zur Unterstützung der Funktionsebene der Gesamtstruktur finden Sie in der [Exchange-Unterstützungs Matrix](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).  <br/> |
|Office-Clientversionen  <br/> | Die mindestens unterstützten Office-Clientversionen für jede Version sind:  <br/> **Exchange 2016** Office 2010 (mit den neuesten Updates)  <br/> **Exchange 2013** Office 2007 SP3  <br/> **Exchange 2010** Office 2003  <br/>  Weitere Informationen zum Office-Client Support finden Sie unter [Exchange supportable Matrix](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).  <br/> |
   
#### <a name="how-do-i-migrate"></a>Wie kann ich migrieren?

Wenn Sie sich entschieden haben, Ihre e-Mails lokal aufzubewahren, können Sie die folgenden Ressourcen verwenden, um Sie bei der Migration zu unterstützen:
  
- [Exchange-Bereitstellungs-Assistent](https://aka.ms/exdeploy)
    
- Änderungen am Active Directory-Schema für Exchange [2016](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.150%29.aspx), [2010](https://www.microsoft.com/download/en/details.aspx?displaylang=en&amp;id=5401)
    
- System Anforderungen für Exchange [2016](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx), [2010](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.141%29.aspx)
    
- Voraussetzungen für Exchange [2016](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.150%29.aspx), [2010](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.141%29.aspx)
    
## <a name="what-if-i-need-help"></a>Was geschieht, wenn ich Hilfe benötige?

Wenn Sie zu Office 365 migrieren, sind Sie möglicherweise berechtigt, unseren Microsoft-Dienst für "Service" zu verwenden. In diesem Artikel finden Sie bewährte Methoden, Tools und Ressourcen, um die Migration zu Office 365 so reibungslos wie möglich zu gestalten. Am besten haben Sie einen echten Supporttechniker, der Sie durch die Migration führt, von der Planung und dem Entwurf bis hin zur Migration Ihres letzten Postfachs. Wenn Sie mehr über schneller Informationen wissen möchten, sehen Sie sich die [Microsoft](https://fasttrack.microsoft.com/)-Einführung an.
  
Wenn bei der Migration zu Office 365 Probleme auftreten und Sie nicht mit der Übertragung oder mit ihrer Migration zu einer neueren Version von Exchange Server arbeiten, helfen wir Ihnen gerne. Hier finden Sie einige Ressourcen, die Sie verwenden können:
  
- [Technische Community](https://social.technet.microsoft.com/Forums/office/en-US/home?category=exchangeserver)
    
- [Support für Kunden](https://support.microsoft.com/en-us/gp/support-options-for-business)
    
## <a name="related-topics"></a>Verwandte Themen

[Ressourcen für das Upgrade Ihrer Office 2007-Server und-Clients](upgrade-from-office-2007-servers-and-products.md)
  
[Office-Ruhestands Gruppe (Microsoft Tech Community)](https://go.microsoft.com/fwlink/?linkid=842065)
  

