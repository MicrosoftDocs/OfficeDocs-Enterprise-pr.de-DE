---
title: Ende der Unterstützung für Exchange 2007 – Roadmap
ms.author: dstrome
author: dstrome
manager: laurawi
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.assetid: c3024358-326b-404e-9fe6-b618e54d977d
description: Exchange Server 2007 wird auf 11 April 2017 Ende erreicht. Wenn Sie nicht bereits die Migration von Exchange 2007 zu Office 365 oder Exchange 2016 angefangen haben, ist nun die Zeit zum Starten der Planung.
ms.openlocfilehash: 4bb8933977c280b4bfaa686e858fc818a1dc4ace
ms.sourcegitcommit: a9c84d02e94c99ff6b1099b4a9ae695be08210e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2018
ms.locfileid: "21169807"
---
# <a name="exchange-2007-end-of-support-roadmap"></a>Ende der Unterstützung für Exchange 2007 – Roadmap

Exchange Server 2007 wird auf **11 April 2017**Ende erreicht. Wenn Sie nicht bereits die Migration von Exchange 2007 zu Office 365 oder Exchange 2016 angefangen haben, ist nun die Zeit zum Starten der Planung. 
  
## <a name="what-does-end-of-support-mean"></a>Welche funktioniert Ende Mittelwert Support?

Exchange-Server hat einen Supportlebenszyklus während der wir neue Features, Fehlerbehebungen, Sicherheitspatches und So weiter stellen wie fast alle Microsoft-Produkte. Dieser Lebenszyklus dauert in der Regel für zehn Jahren ab dem Zeitpunkt der ersten Version des Produkts, und das Ende dieser Lebenszyklus wird als das Produkt Ablauf des Supports bezeichnet. Da Exchange 2007 den Ablauf des Supports auf 11 April 2017, Microsoft stellt keine erreicht:
  
- Technischen Support für Probleme, die auftreten können.
    
- Fehlerbehebungen für Probleme, die ermittelt werden und kann, die die Stabilität und Verwendbarkeit des Servers auswirken;
    
- Sicherheitsupdates für Sicherheitsrisiken, werden erkannt und, die möglicherweise den Server anfällig für Sicherheitslücken;
    
- Zeitzone aktualisiert.
    
Die Installation von Exchange 2007 wird weiterhin nach diesem Datum ausgeführt. Allerdings wird aufgrund der oben aufgeführten Änderungen, dringend empfohlen, dass Sie so bald wie möglich von Exchange 2007 migrieren.
  
Weitere Informationen zu Office 2007-Server den Ablauf des Supports fast finden Sie unter [Planen des Upgrades von Office 2007-Servern und Produkte](upgrade-from-office-2007-servers-and-products.md).
  
## <a name="what-are-my-options"></a>Welche Optionen sind?

Nun, da Exchange 2007 den Ablauf des Supports erreicht hat, wird dringend empfohlen, dass Sie Ihre Optionen und eines Migrationsplans vorbereiten. Sie können:
  
- Migrieren Sie zu Office 365 mit ü, mehrstufige oder hybridmigration;
    
- Migrieren von Ihren Exchange 2007-Servern zu einer neueren Version von Exchange auf Ihren lokalen Servern.
    
In den folgenden Abschnitten machen Sie sich jede Option ausführlich aus.
  
### <a name="migrate-to-office-365"></a>Migrieren zu Office 365

Migration Ihrer e-Mails zu Office 365 ist die Option bewährte und einfachste Stilllegung der Exchange 2007-Bereitstellung erleichtern. Mit einer Migration zu Office 365 können Sie nur einen Hop aus 10 Jahre Technologie Stand der Technik-Features wie vornehmen:
  
- Compliance-Funktionen wie etwa Aufbewahrungsrichtlinien, die In-Place und Aufbewahrung für eventuelle Rechtsstreitigkeiten, Compliance-eDiscovery und vieles mehr;
    
- Office 365-Gruppen;
    
- Fokussierte Posteingang;
    
- Eingegangen Analytics;
    
- REST-APIs für den programmgesteuerten Zugriff auf e-Mail, Kalender, Kontakte und usw.
    
Office 365 auch ruft neue Features und Erfahrungen erste und Sie und Ihre Benutzer können in der Regel Mal sofort verwendet. Zusätzlich zu den neuen Features müssen Sie dafür sorgen:
  
- Erwerb und die Wartung von Hardware;
    
- Bezahlung für Heizung und Kühlung Servern;
    
- Halten auf dem aktuellen Stand auf Sicherheit, Produkt- und Zeitzone Fixes;
    
- Verwalten von Speicher und Software zur Unterstützung von Compliance-Bestimmungen;
    
- Durchführen eines Upgrades auf eine neue Version von Exchange - befinden Sie sich immer auf die neueste Version von Exchange in Office 365.
    
#### <a name="how-should-i-migrate-to-office-365"></a>Wie sollte der Migration zu Office 365?

Abhängig von Ihrer Organisation müssen Sie einige Optionen, die helfen Ihnen, zu Office 365 erhalten möchten. Bei der Auswahl einer Option für die Migration müssen Sie berücksichtigen sollten Sie einige Dinge wie die Anzahl der Arbeitsplätze oder Postfächer, die Sie verschieben möchten, wie lange die Migration bis zum letzten soll und gibt an, ob Sie eine nahtlose Integration zwischen Ihrer lokalen Installation und Office 365 während benötigen die Migration. Diese Tabelle zeigt die Migrationsoptionen und die wichtigsten Faktoren, die bestimmen, welche Methode müssen Sie verwenden möchten.
  
| |
|**Die Option für Migration**|**Größe der Organisation**|**Gültigkeitsdauer**|
|:-----|:-----|:-----|
|Übernahmemigration  <br/> |Weniger als 150 Arbeitsplätzen  <br/> |Eine Woche oder weniger  <br/> |
|Mehrstufige Migration  <br/> |Mehr als 150 Arbeitsplätzen  <br/> |Ein paar Wochen  <br/> |
|Vollständige hybridmigration  <br/> |Mehrere hundert auf Tausenden von Arbeitsplätzen  <br/> |Mindestens ein paar Monaten  <br/> |
   
Die folgenden Abschnitte enthalten eine Übersicht über diese Methoden. Sehen Sie sich [auf einen Migrationspfad entscheiden](https://support.office.com/en-us/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27) , um die Details der einzelnen Methoden zu informieren. 
  
#### <a name="cutover-migration"></a>Übernahmemigration

Eine einstufige Migration wird, werden bei einer Überprüfung vor dem ausgewählten Datum und Uhrzeit, Sie alle Postfächer, Verteilergruppen, Kontakte und usw., Migration zu Office 365. Wenn Sie damit fertig sind, Sie Ihre lokale Exchange-Server herunterfahren und ausschließlich mithilfe von Office 365 zu starten.
  
Die übernahmemigration-Methode eignet sich für kleine Organisationen, die nicht über sehr viele Postfächer verfügen zu Office 365 schnell abrufen möchten, und nicht möchten, dass für den Umgang mit einiger die Komplexität der anderen Methoden. Aber es auch etwas eingeschränkt und, da es in einer Woche oder weniger abgearbeitet werden sollte, da es erfordert, dass Benutzer ihre Outlook-Profile neu konfigurieren. Während der übernahmemigration bis zu 2.000 Postfächer verarbeitet werden kann, wird dringend empfohlen, dass Sie mit dieser Methode maximal 150 Postfächer migrieren. Wenn Sie versuchen, die mehr als 150 Postfächer zu migrieren, können Sie nicht genügend Zeit für alle Postfächer zu übertragen, bevor der Deadline ausführen und Ihre Mitarbeiter abrufen können IT-Support eines Problems überlastet Benutzer konfigurieren Sie Outlook neu.
  
Wenn Sie beabsichtigen, dieses Ziel zu erreichen einer einstufigen Migrations hier sind einige Dinge müssen berücksichtigt werden sollten:
  
- Office 365 müssen Ihren Exchange 2007-Servern mit Outlook Anywhere über TCP-Port 443 herstellen.
    
- Alle lokalen Postfächern werden zu Office 365 verschoben werden.
    
- Sie benötigen eine lokale Administratorkonto, das über Lesezugriff auf den Inhalt der Postfächer der Benutzer verfügt;
    
- Exchange 2007 akzeptierte Domänen, die in Office 365 Notwendigkeit verwenden, um als überprüften Domänen im Dienst hinzugefügt werden soll;
    
- Zwischen dem Zeitpunkt, starten Sie die Migration und wenn Sie die Phase Fertigstellung beginnen, Office 365 wird in regelmäßigen Abständen synchronisieren der Office 365 und lokalen Postfächer. Auf diese Weise können Sie die Migration abschließen, ohne befürchten e-Mail in Ihrer lokalen Postfächer hinterlassen;
    
- Benutzer werden neue temporären Kennwörter für ihre Office 365-Konto eingerichtet, die sie benötigen, zu ändern, wenn sie sich bei ihren Postfächern zum ersten Mal anmelden;
    
- Sie benötigen eine Office 365-Lizenz, die Exchange Online für jedes Postfach des Benutzers enthält, den Sie migrieren;
    
- Benutzer müssen richten Sie ein neues Outlook-Profil auf jedem ihrer Geräte und ihre e-Mails erneut herunterladen. Die Menge an e-Mails, die Outlook herunterladen kann variieren. Weitere Informationen sehen Sie sich [ändern, wie viele e-Mail-Nachrichten an offline beibehalten](https://support.office.com/en-us/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&amp;rs=en-US&amp;ad=US&amp;fromAR=1).
    
Weitere Informationen zum übernahmemigration betrachten:
  
- [Wissenswertes zu einer Übernahmemigration von E-Mails zu Office 365](https://support.office.com/en-us/article/What-you-need-to-know-about-a-cutover-email-migration-to-Office-365-961978ef-f434-472d-a811-1801733869da)
    
- [Ausführen einer einstufigen Migrations von e-Mails zu Office 365](https://support.office.com/en-us/article/Perform-a-cutover-migration-of-email-to-Office-365-9496e93c-1e59-41a8-9bb3-6e8df0cd81b4)
    
#### <a name="staged-migration"></a>Mehrstufige Migration

Eine mehrstufige Migration ist, in dem Sie ein paar Hundert oder einige Tausend Postfächer, die Sie verwenden möchten, Migrieren zu Office 365, einer Woche oder mehr für die Durchführung die Migration durchführen müssen, haben und nicht müssen keine erweiterten Hybrid migrationsfeatures wie freigegebene Frei/Gebucht-Kalender info Unternehmensinformationen.
  
Mehrstufige Migration eignet sich für Organisationen, die mehr Zeit zum Migrieren von ihren Postfächern zu Office 365, jedoch weiterhin für die Durchführung die Migration innerhalb weniger Wochen planen müssen. Sie können Migrieren von Postfächern in "Batches", mit die Sie steuern, wie viele und welche können, Postfächer zu einem bestimmten Zeitpunkt migriert werden. Können Sie Postfächer von Benutzern in der gleichen Abteilung batch, z. B., um sicherzustellen, sie sind alle verschoben zur selben Zeit. Oder Sie möglicherweise executive Postfächer lassen, bis die letzten Batch. Wie mit übernahmemigrationen, die Benutzer benötigen werden, um ihre Outlook-Profile neu zu erstellen.
  
Wenn Sie beabsichtigen, dieses Ziel zu erreichen einer mehrstufigen Migrations werden hier einige Aspekte beachtet:
  
- Office 365 müssen Ihren Exchange 2007-Servern mit Outlook Anywhere über TCP-Port 443 herstellen.
    
- Sie benötigen eine lokale Administratorkonto, das über Lesezugriff auf den Inhalt der Postfächer der Benutzer verfügt;
    
- Exchange 2007 akzeptierte Domänen, die in Office 365 Notwendigkeit verwenden, um als überprüften Domänen im Dienst hinzugefügt werden soll;
    
- Sie müssen zum Erstellen einer CSV-Datei mit den vollständigen Namen und e-Mail-Adresse der einzelnen Postfächer, den Sie in einem Batch migrieren möchten. Sie müssen auch ein neues Kennwort für jedes Postfach, das Sie migrieren, und senden Sie ihr Kennwort für jeden Benutzer. Der Benutzer werden aufgefordert, das Kennwort beim ersten ändern, die sie für ihr neues Postfach für Office 365 anmelden;
    
- Zwischen dem Zeitpunkt, starten Sie den migrationsbatch, und wenn Sie die Phase Fertigstellung beginnen, Office 365 in regelmäßigen Abständen die Office 365 und lokale Postfächer im Batch enthalten synchronisieren. Auf diese Weise können Sie die Migration abschließen, ohne befürchten e-Mail in Ihrer lokalen Postfächer hinterlassen;
    
- Benutzer werden neue temporären Kennwörter für ihre Office 365-Konto eingerichtet, die sie benötigen, zu ändern, wenn sie in ihrem Postfach zum ersten Mal anmelden;
    
- Sie benötigen eine Office 365-Lizenz, die Exchange Online für jedes Postfach des Benutzers enthält, den Sie migrieren;
    
- Benutzer müssen richten Sie ein neues Outlook-Profil auf jedem ihrer Geräte und ihre e-Mails erneut herunterladen. Die Menge an e-Mails, die Outlook herunterladen kann variieren. Weitere Informationen sehen Sie sich [ändern, wie viele e-Mail-Nachrichten an offline beibehalten](https://support.office.com/en-us/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&amp;rs=en-US&amp;ad=US&amp;fromAR=1).
    
Weitere Informationen zu mehrstufigen Migration betrachten:
  
- [Sie müssen über eine mehrstufige e-Mail-Migration zu Office 365 wissen sollten](https://support.office.com/en-us/article/What-you-need-to-know-about-a-staged-email-migration-to-Office-365-7e2c82be-5f3d-4e36-bc6b-e5b4d411e207)
    
- [Durchführen einer mehrstufigen Migrations von e-Mails zu Office 365](https://support.office.com/en-us/article/Perform-a-staged-migration-of-email-to-Office-365-83bc0b69-de47-4cc4-a57d-47e478e4894e)
    
#### <a name="full-hybrid"></a>Vollständige hybrid

Eine vollständige hybridmigration ist, in denen Ihre Organisation hat Hunderte bis zu Zehntausende von Postfächern und einige oder alle zu Office 365 verschieben möchten. Da diese Art der Migration in der Regel längerfristige sind, ermöglichen das hybridmigrationen:
  
- Der lokale Benutzer die Frei/Gebucht-Informationen für Benutzer in Office 365, anzeigen und umgekehrt;
    
- Siehe eine einheitliche globale Adressliste, die Empfänger in der lokalen und Office 365 enthält;
    
- Anzeigen der vollständige Outlook Empfänger Karten für alle Benutzer, unabhängig davon, ob sie lokale sind oder in Office 365;
    
- Sichere e-Mail-Kommunikation zwischen lokalen Exchange-Servern und Office 365 mit TLS und Zertifikate;
    
- Ermöglicht es ihnen, zwischen lokalen Exchange-Servern und Office 365 als interne, gesendete Nachrichten behandeln:
    
  - Ordnungsgemäß ausgewertet und von Transport- und Compliance-Agenten für interne Nachrichten; verarbeitet werden
    
  - Anti-Spam-Filter zu umgehen.
    
Vollständige hybridmigrationen sind am besten für Organisationen, die in einer hybridkonfiguration für mehrere Monate oder mehrere bleiben erwarten. Sie erhalten die Features aufgeführt, die weiter oben in diesem Abschnitt plus Directory-Synchronisierung, besser integrierte Kompatibilitätsfeatures und die Möglichkeit zum Verschieben von Postfächern zu und von Office 365 onlinepostfachverschiebungen verwenden. Office 365 wird zu einer Nebenstelle der lokalen Organisation.
  
Wenn Sie beabsichtigen, dieses Ziel zu erreichen eine vollständige hybridmigration werden hier einige Aspekte beachtet:
  
- Vollständige hybridmigrationen werden nicht für alle Arten von Organisationen geeignet. Aufgrund der Komplexität des vollständigen hybridmigrationen nicht Organisationen mit weniger als ein paar Hundert Postfächer in der Regel Vorteile angezeigt, die Aufwand und Kosten für erforderlich, um eine Liste einrichten zu rechtfertigen. Wenn dieses wie Ihre Organisation vorkommt, wird dringend empfohlen, dass Sie stattdessen Cutover oder mehrstufige Migrationen berücksichtigen;
    
- Sie müssen mindestens einen Exchange 2013-Server in Ihrer Exchange 2007-Organisation, die als "hybridserver" fungiert bereitstellen. Dieser Server wird im Namen Ihrer Exchange 2007-Servern mit Office 365 kommunizieren;
    
- Office 365 benötigen zum Herstellen einer Verbindung mit Outlook Anywhere über TCP-Port 443; "Hybrid Servers"
    
- Sie müssen zum Einrichten der verzeichnissynchronisierung zwischen Ihrer lokalen Active Directory-Server und Office 365 mit Azure Active Directory verbinden (AADConnect).
    
- Benutzer können ihre Office 365-Postfach mit dem gleichen Benutzernamen und Kennwort, die sie verwenden, wenn sie in das lokale Netzwerk anmelden (erfordert Azure Active Directory verbinden mit kennwortsynchronisierung und/oder Active Directory-Verbunddienste) anmelden können;
    
- Sie benötigen eine Office 365-Lizenz, die Exchange Online für jedes Postfach des Benutzers enthält, den Sie migrieren;
    
- Benutzer nicht müssen Sie ein neues Outlook-Profil auf die meisten ihrer Geräte einrichten (einige ältere Android-Telefone ggf. ein neues Profil) und müssen nicht erneut laden Sie ihre e-Mails.
    
Wenn eine vollständige Hybrid-Migration Sounds für Sie geeigneten, sehen Sie sich die folgenden Ressourcen zur Unterstützung bei der Migration:
  
- [Exchange-Bereitstellungs-Assistent](https://aka.ms/exdeploy)
    
- [Hybridbereitstellungen in Exchange Server](https://technet.microsoft.com/en-us/library/jj200581%28v=exchg.150%29.aspx)
    
- [Assistent für die Hybridkonfiguration](https://technet.microsoft.com/en-us/library/hh529921%28v=exchg.150%29.aspx)
    
- [FAQs zum Assistenten für die Hybridkonfiguration](https://technet.microsoft.com/en-us/library/mt488940%28v=exchg.150%29.aspx)
    
- [Voraussetzungen für die Hybridbereitstellung](https://technet.microsoft.com/en-us/library/hh534377%28v=exchg.150%29.aspx)
    
### <a name="migrate-to-a-newer-version-of-exchange-server"></a>Migrieren Sie zu einer neueren Version von Exchange Server

Während wir dringend glauben, dass Sie den Wert und Benutzer am besten erreichen können, von der Migration zu Office 365, wissen wir auch, dass in einigen Unternehmen ihre lokalen e-Mail-behalten müssen. Möglicherweise aufgrund von behördlichen Vorschriften, um Daten zu gewährleisten ist nicht in einem Rechenzentrum befindet sich in einem anderen Land usw. gespeichert. Wenn Sie Ihre e-Mail-lokale beibehalten, können Sie Ihre Exchange 2007-Umgebung auf Exchange 2010, Exchange 2013 oder Exchange 2016 migrieren.
  
Es wird empfohlen, dass die Migration zu Exchange 2016, wenn Sie zu Office 365 migrieren können. Exchange 2016 umfasst alle Features und Weiterentwicklungen, die mit früheren Versionen von Exchange enthalten, und die Erfahrung mit Office 365 verfügbar es am ehesten entspricht, (obwohl einige Features nur in Office 365 verfügbar sind). Schauen Sie sich nur einige der Aufgaben, die Sie fehlende out auf haben wurde:
  
|**Exchange-Version**|**Funktionen**|
|:-----|:-----|
|Exchange 2010  <br/> | Role Based Access Control (Berechtigungen ohne ACLs)  <br/>  Outlook Web Access-Postfachrichtlinien  <br/>  Möglichkeit zum Freigeben von Frei/Gebucht-Informationen und Delegierung von Kalendern zwischen Organisationen  <br/> |
|Exchange 2013  <br/> | *Features von Exchange 2010 und...*  <br/>  Reduzieren der Anzahl der Server-Rollen auf drei vereinfachte Architektur (Postfach, Clientzugriff, Edge-Transport)  <br/>  Datenrichtlinien von Datenverlust (DLP), die vertraulichen Informationen verloren gehen schützen  <br/>  Erheblich verbesserte Outlook Web App-Leistung  <br/> |
|Exchange 2016  <br/> | *Features von Exchange 2013 und...*  <br/>  Weitere vereinfachte Serverrollen nur Postfach- und Edge-Transport  <br/>  Verbesserte DLP zusammen mit der Integration mit SharePoint  <br/>  Verbesserte Datenbank von Standorten  <br/>  Online-Dokument für die Zusammenarbeit  <br/> |
   
#### <a name="which-version-should-i-migrate-to"></a>Welche Version sollte ich zu migrieren?

Es wird empfohlen, dass Sie zunächst wird davon ausgegangen, dass Sie auf Exchange 2016 migriert werden sollen. Klicken Sie dann verwenden Sie die folgende Informationen zu Ihrer Annahme bestätigen oder Exchange 2016 auszuschließen. Wenn für einen oder anderen Grund Exchange 2016 migrieren können, führen Sie identisch mit Exchange 2013 verarbeiten und so weiter.
  
|**Überlegung**|**Weitere Informationen**|
|:-----|:-----|
|Ende des Zeitraums Unterstützung  <br/> | Wie Exchange 2007 verfügt jede Version eines Exchange eigene Ende Support Datum:  <br/> **Exchange 2010** – Januar 2020  <br/> **Exchange 2013** – April 2023 zurück  <br/> **Exchange 2016** - Oktober 2025  <br/>  Ende der Unterstützung von Datum, die früher müssen Sie die zuvor andere Migration ausführen. Januar 2020 ist viel näher, als man glaubt!<br/> |
|Migrationspfad für Exchange 2010 und 2013  <br/> |Es folgen die allgemeinen Phasen für die Migration zu Exchange 2010 oder Exchange 2013:  <br/> Installieren von Exchange 2010 oder 2013 in Ihren vorhandenen Exchange 2007-Organisation verschieben-Diensten und anderen Infrastruktur für Exchange 2010 oder 2013 verschieben Postfächer und öffentlicher Ordner zu Exchange 2010 oder 2013 nehmen verbleibenden Exchange 2007-Servern |
|Migrationspfad für Exchange 2016  <br/> |Es folgen die allgemeinen Phasen für die Migration zu Exchange 2016:  <br/> Installieren von Exchange 2013 in Ihren vorhandenen Exchange 2007-Organisation verschieben-Diensten und anderen Infrastruktur zum Verschieben von Exchange 2013-Postfächer und öffentlicher Ordner zu Exchange 2013 nehmen verbleibenden Exchange 2007-Servern installieren von Exchange 2016 an Ihre vorhandenen Exchange 2013-Organisation. Verschieben Sie Postfächer, Öffentliche Ordner, Dienste und andere Infrastruktur auf Exchange 2016 (Reihenfolge spielt keine Rolle). Außerbetriebnahme der verbleibenden Exchange 2013 Server > [!NOTE]> Migrieren von Exchange 2013 in Exchange 2016 ist einfach. Beide Versionen haben fast dieselben hardwareanforderungen. Dadurch, und die Tatsache, die sind diese Versionen kompatibel ist, können Sie einen Server, den Sie für Exchange 2013 gekauft neu und Installieren von Exchange 2016 darauf bedeutet. Beachten Sie auch mit onlinepostfachverschiebungen, die meisten Benutzer werden nie ihr Postfach verschoben wird den Server deaktivieren und dann wieder haben, nachdem Sie es mit Exchange 2016 erstellt haben.           |
|Version-Koexistenz  <br/> | Bei der Migration zu:  <br/> **Exchange 2016** Exchange 2016 kann nicht in einer Organisation installiert werden, die einen Exchange 2007-Server enthält. Sie müssen zunächst Migrieren zu Exchange 2010 oder 2013 (es wird dringend empfohlen Exchange 2013), entfernen alle Exchange 2007-Servern und migrieren Sie anschließend zu Exchange 2016.<br/> **Exchange 2010 oder Exchange 2013** Sie können die Exchange 2010 oder Exchange 2013 in einer vorhandenen Exchange 2007-Organisation installieren. So können Sie einen oder mehrere Exchange 2010 oder 2013-Servern installieren und Ausführen der Migrations.<br/> |
|Serverhardware  <br/> | Hardwareanforderungen für wurden von Exchange 2007 geändert. Sie müssen sicherstellen, dass die Hardware, die Sie verwenden möchten, kompatibel ist. Finden Sie weitere Informationen zu hardwareanforderungen für die einzelnen Versionen hier:<br/> [Systemanforderungen für Exchange 2016](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx) <br/> [Exchange 2013 System Requirements](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx) <br/> [Exchange 2010 – Systemanforderungen](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.141%29.aspx) <br/>  Sie werden feststellen, dass mit dem bedeutende Verbesserungen in Exchange-Leistung und höhere Leistung und die Speicherkapazität in neueren, Sie wahrscheinlich weniger Server unterstützt die gleiche Anzahl von Postfächern benötigen.  <br/> |
|Betriebssystemversion  <br/> | Die minimale unterstützte Betriebssystem-Versionen für die einzelnen Versionen sind:  <br/> **Exchange 2016** WindowsServer 2012  <br/> **Exchange 2013** Windows Server 2008 R2 SP1  <br/> **Exchange 2010** Windows Server 2008 SP2  <br/>  Weitere Informationen zur Unterstützung von Betriebssystem finden unter [Exchange Supportability Matrix](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).  <br/> |
|Active Directory-Gesamtstruktur-Funktionsebene  <br/> | Die minimalen unterstützten Active Directory Gesamtstrukturfunktionsebenen für jede Version sind:  <br/> **Exchange 2016** Windows Server 2008 R2 SP1  <br/> **Exchange 2013** WindowsServer 2003  <br/> **Exchange 2010** WindowsServer 2003  <br/>  Weitere Informationen zur Gesamtstruktur funktionale Ebene-Unterstützung finden unter [Exchange Supportability Matrix](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).  <br/> |
|Office-Client-Versionen  <br/> | Die minimalen unterstützten Office-Client-Versionen für die einzelnen Versionen sind:  <br/> **Exchange 2016** Office 2010 (mit den neuesten Updates)  <br/> **Exchange 2013** Office 2007 SP3  <br/> **Exchange 2010** Office 2003  <br/>  Weitere Informationen zum Office-Client-Unterstützung finden unter [Exchange Supportability Matrix](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).  <br/> |
   
#### <a name="how-do-i-migrate"></a>Wie migriere ich?

Wenn Sie entschieden haben, dass Sie Ihre e-Mail-lokale beibehalten möchten, können Sie die folgenden Ressourcen zur Unterstützung bei der Migration verwenden:
  
- [Exchange-Bereitstellungs-Assistent](https://aka.ms/exdeploy)
    
- Active Directory-schemaänderungen für Exchange [2016](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.150%29.aspx), [2010](https://www.microsoft.com/download/en/details.aspx?displaylang=en&amp;id=5401)
    
- Systemanforderungen für Exchange [2016](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx), [2010](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.141%29.aspx)
    
- Voraussetzungen für Exchange [2016](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.150%29.aspx), [2010](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.141%29.aspx)
    
## <a name="what-if-i-need-help"></a>Was geschieht, wenn benötigen Sie Hilfe?

Wenn Sie zu Office 365 migrieren, möglicherweise Sie berechtigt, unsere FastTrack Microsoft-Dienst verwenden. Schnelle bietet best Practices, Tools und Ressourcen, die Ihre Migration zu Office 365 nahtlos und einfach funktioniert wie möglich gestalten. Schließlich müssen Sie eine echte Supporttechniker, die von der Planung Ihrer Migration durchgehen und zum Migrieren der letzten Postfächer entwerfen. Wenn Sie weitere Informationen zu der schnelle wissen möchten, sehen Sie sich [Schnell von Microsoft](https://fasttrack.microsoft.com/).
  
Wenn Sie Probleme während der Migrations zu Office 365 und Sie nicht, schnelle oder der Migration zu einer neueren Version von Exchange Server nutzen, sind wir bereit. Hier sind einige Ressourcen, die Sie verwenden können:
  
- [Technische-community](https://social.technet.microsoft.com/Forums/office/en-US/home?category=exchangeserver)
    
- [Support für Kunden](https://support.microsoft.com/en-us/gp/support-options-for-business)
    
## <a name="related-topics"></a>Verwandte Themen

[Ressourcen zum upgrade Ihrer Office 2007-Servern und clients](upgrade-from-office-2007-servers-and-products.md)
  
[Office Stilllegung Gruppe (Tech Center für Microsoft-Community)](https://go.microsoft.com/fwlink/?linkid=842065)
  

