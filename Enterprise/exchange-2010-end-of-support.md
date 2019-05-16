---
title: Roadmap für Exchange 2010 Ende der Unterstützung
ms.author: dstrome
author: dstrome
manager: laurawi
ms.date: 1/31/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.assetid: e150e7b9-c432-4c8d-a0ae-c11847129a7d
description: Exchange 2010 nähert sich der Unterstützung. Verwenden Sie diese Planungs Roadmap als Leitfaden, um das Upgrade auf Exchange Online oder eine neuere Version von Exchange Server lokal vorzubereiten.
ms.openlocfilehash: f0ff6551f9ef2c0ed57baabacc04293e83d25e13
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067571"
---
# <a name="exchange-2010-end-of-support-roadmap"></a>Roadmap für Exchange 2010 Ende der Unterstützung

Am **14. Januar 2020**wird Exchange Server 2010 das Ende der Unterstützung erreichen. Wenn Sie die Migration von Exchange 2010 zu Office 365 oder Exchange 2016 noch nicht begonnen haben, können Sie mit der Planung beginnen.

## <a name="what-does-end-of-support-mean"></a>Was bedeutet End-of-Support?

Exchange Server hat, wie fast alle Microsoft-Produkte, einen Supportlebenszyklus, in dem wir neue Features, Bugfixes, Sicherheitsfixes usw. bereitstellen. Dieser Lebenszyklus dauert in der Regel 10 Jahre ab dem Datum der ersten Version des Produkts, und das Ende dieses Lebenszyklus wird als Ende des Supports des Produkts bezeichnet.
Wenn Exchange 2010 am Ende der Unterstützung am 14. Januar 2020, stellt Microsoft Folgendes nicht mehr bereit:

- Technischer Support für Probleme, die auftreten können;
- Fehlerbehebungen für erkannte Probleme, die die Stabilität und Benutzerfreundlichkeit des Servers beeinträchtigen können
- Sicherheitsfixes für erkannte Schwachstellen, die den Server anfällig für Sicherheitsverstöße machen können;
- Zeitzonenaktualisierungen.

Die Installation von Exchange 2010 wird nach diesem Datum fortgesetzt. Aufgrund der oben aufgeführten Änderungen wird jedoch dringend empfohlen, dass Sie so bald wie möglich eine Migration von Exchange 2010 durchführen.

Weitere Informationen zu Office 2010-Servern, die sich am Ende des Supports befinden, finden Sie unter [Ressourcen zum Upgrade von Office 2010-Servern und-Clients](https://docs.microsoft.com/en-us/office365/enterprise/upgrade-from-office-2010-servers-and-products).

## <a name="what-are-my-options"></a>Was sind meine Optionen?

Da Exchange 2010 das Ende des Supports erreicht, ist dies eine gute Zeit, um Ihre Optionen zu erkunden und einen Migrationsplan vorzubereiten. Sie können:

- Vollständige Migration zu Office 365. Migrieren Sie Postfächer mit Cutover, minimaler Hybrid-oder vollständiger Hybrid Migration, und entfernen Sie dann lokale Exchange-Server und Active Directory.
- Migrieren Sie Ihre Exchange 2010-Server zu Exchange 2016 auf Ihren lokalen Servern.

> [!IMPORTANT]
> Wenn sich Ihre Organisation für die Migration von Postfächern zu Office 365 entschieden hat, aber Dirsync oder Azure AD Connect beibehalten soll, um weiterhin Benutzerkonten aus dem lokalen Active Directory zu verwalten, müssen Sie mindestens einen lokalen Exchange-Server aufbewahren. Wenn der letzte Exchange-Server entfernt wurde, können Sie in Exchange Online keine Änderungen an Exchange-Empfängern vornehmen. Der Grund dafür ist, dass die Autoritäts Quelle in Ihrem lokalen Active Directory verbleibt und Änderungen vorgenommen werden müssen. In diesem Szenario haben Sie folgende Möglichkeiten:

- (**Empfohlen**) Wenn Sie Ihre Postfächer zu Office 365 migrieren und Ihre Server bis zum 14. Januar 2020 aktualisieren können, verwenden Sie Exchange 2010 zum Herstellen einer Verbindung mit Office 365 und zum Migrieren von Postfächern. Migrieren Sie als nächstes Exchange 2010 zu Exchange 2016, und setzen Sie die restlichen Exchange 2010-Server außer Betrieb.
- Wenn Sie die Postfachmigration und das lokale Server Upgrade bis zum 14. Januar 2020 nicht abschließen können, aktualisieren Sie zuerst Ihre lokalen Exchange 2010-Server auf Exchange 2016, und verwenden Sie dann Exchange 2016, um eine Verbindung mit Office 365 herzustellen und Postfächer zu migrieren.

> [!NOTE]
> Während ein wenig komplizierter ist, können Sie auch Postfächer zu Office 365 migrieren, während Sie Ihre lokalen Exchange 2010-Server zu Exchange 2016 migrieren.

In den folgenden Abschnitten werden die einzelnen Optionen detaillierter erläutert.

## <a name="migrate-to-office-365"></a>Migrieren zu Office 365

Die Migration Ihrer e-Mails zu Office 365 ist die beste und einfachste Option, die Ihnen bei der Pensionierung Ihrer Exchange 2010-Bereitstellung hilft. Mit einer Migration zu Office 365 können Sie einen einzelnen Hop von der alten Technologie zu State-of-the-Art-Features wie:

- Compliance-Funktionen wie Aufbewahrungsrichtlinien, in-situ-und Gerichtsverfahren, in-situ-eDiscovery und vieles mehr;
- Microsoft Teams;
- Power BI;
- Fokussierter Posteingang;
- Analysieren von Analysen;

Office 365 erhält auch neue Features und Erfahrungen zuerst, und Sie und Ihre Benutzer können Sie normalerweise sofort verwenden. Zusätzlich zu den neuen Features müssen Sie sich keine Gedanken machen:

- Erwerb und Wartung von Hardware;
- Bezahlen für das Heizen und kühlen Ihrer Server;
- Aktualisierung der Sicherheits-, Produkt-und Zeit Zonen Korrekturen auf dem neuesten Stand
- Verwalten von Speicher und Software zur Unterstützung von Compliance-Anforderungen
- Upgrade auf eine neue Version von Exchange-Sie sind immer auf der neuesten Version von Exchange in Office 365.

### <a name="how-should-i-migrate-to-office-365"></a>Wie sollte ich zu Office 365 migrieren?

Je nach Organisation haben Sie einige Optionen, die Ihnen bei der Verwaltung von Office 365 helfen. Bei der Auswahl einer Migrationsoption müssen Sie einige Dinge berücksichtigen, wie beispielsweise die Anzahl der zu verschiebenden Sitze oder Postfächer, die Dauer der Migration und die Notwendigkeit einer nahtlosen Integration zwischen Ihrer lokalen Installation und Office 365 während die Migration. In dieser Tabelle sind die Migrationsoptionen und die wichtigsten Faktoren aufgeführt, die bestimmen, welche Methode Sie verwenden.

| **Migrationsoption**     | **Organisationsgröße** | **Duration**        |
|--------------------------|-----------------------|---------------------|
| Übernahmemigration        | Weniger als 150 Sitze  | Woche oder kleiner      |
| Minimale Hybrid Migration | Weniger als 150 Sitze  | Wenige Wochen oder weniger |
| Vollständige Hybrid Migration    | Mehr als 150 Sitze   | Ein paar Wochen oder mehr |

Die folgenden Abschnitte enthalten eine Übersicht über diese Methoden. Auschecken entscheiden Sie sich für [einen Migrationspfad](https://support.office.com/en-us/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27) , um die Details der einzelnen Methoden zu erfahren.

### <a name="cutover-migration"></a>Übernahmemigration

Eine Cutover Migration ist eine, bei der Sie zu einem vordefinierten Datum und einer bestimmten Uhrzeit alle ihre Postfächer, Verteilergruppen, Kontakte usw. zu Office 365 migrieren. Wenn Sie fertig sind, schließen Sie Ihre lokalen Exchange-Server, und beginnen Sie mit der Verwendung von Office 365 exklusiv.

Die Cutover-Migrationsmethode eignet sich hervorragend für kleine Organisationen, die nicht über sehr viele Postfächer verfügen, schnell zu Office 365 und nicht mit einigen der Komplexitäten der anderen Methoden umgehen möchten. Aber es ist auch etwas begrenzt, da es in einer Woche oder weniger abgeschlossen werden sollte und dass Benutzer Ihre Outlook-Profile neu konfigurieren müssen. Während die Cutover-Migration bis zu 2.000 Postfächer verarbeiten kann, wird dringend empfohlen, maximal 150 Postfächer mit dieser Methode zu migrieren. Wenn Sie versuchen, mehr als 150 Postfächer zu migrieren, können Sie die Zeit für die Übertragung aller Postfächer vor dem Stichtag nicht überschreiten, und Ihr IT-Supportmitarbeiter kann überlastet werden, um Benutzer neu zu konfigurieren.

Wenn Sie eine Cutover Migration durchführen möchten, sollten Sie Folgendes in Betracht ziehen:

- Office 365 muss mit Outlook Anywhere über TCP-Anschluss 443 eine Verbindung zu Ihren Exchange 2010-Servern herstellen.
- Alle lokalen Postfächer werden in Office 365 verschoben.
- Sie benötigen ein lokales Administratorkonto, das Zugriff auf den Inhalt der Postfächer Ihrer Benutzer hat;
- Die akzeptierten Exchange 2010-Domänen, die Sie in Office 365 verwenden möchten, müssen im Dienst als verifizierte Domänen hinzugefügt werden.
- Zwischen dem Start der Migration und dem Beginn der Abschlussphase synchronisiert Office 365 regelmäßig die Office 365-und lokalen Postfächer. Auf diese Weise können Sie die Migration abschließen, ohne sich Gedanken darüber machen zu müssen, dass e-Mails in Ihren lokalen Postfächern hinterlassen werden.
- Benutzer erhalten neue temporäre Kennwörter für Ihr Office 365-Konto, die Sie ändern müssen, wenn Sie sich zum ersten Mal bei ihren Postfächern anmelden;
- Sie benötigen eine Office 365-Lizenz, die Exchange Online für jedes Benutzerpostfach umfasst, das Sie migrieren;
- Benutzer müssen auf jedem Ihrer Geräte ein neues Outlook-Profil einrichten und Ihre e-Mails erneut herunterladen. Die Menge an e-Mails, die Outlook herunterlädt, kann variieren. Weitere Informationen finden Sie unter [Ändern der Menge von e-Mails, die offline bleiben sollen](https://support.office.com/en-us/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&rs=en-US&ad=US&fromAR=1).

Weitere Informationen zur Migration von Cutover finden Sie unter:

- [Was Sie über eine Cutover-e-Mail-Migration zu Office 365 wissen müssen](https://support.office.com/en-us/article/What-you-need-to-know-about-a-cutover-email-migration-to-Office-365-961978ef-f434-472d-a811-1801733869da)
- [Durchführen einer Cutover Migration von e-Mails zu Office 365](https://support.office.com/en-us/article/Perform-a-cutover-migration-of-email-to-Office-365-9496e93c-1e59-41a8-9bb3-6e8df0cd81b4)

### <a name="minimal-hybrid-migration"></a>Minimale Hybrid Migration

Bei einer minimalen Hybrid-oder Express Migration handelt es sich um ein paar hundert Postfächer, die Sie zu Office 365 migrieren möchten, die Migration innerhalb weniger Wochen abschließen und keine der erweiterten Hybrid Migrationsfunktionen wie freigegebener frei/gebucht-Kalender benötigen. Informationen.

Die minimale Hybrid Migration eignet sich hervorragend für Organisationen, die mehr Zeit benötigen, um ihre Postfächer zu Office 365 zu migrieren, aber dennoch die Migration innerhalb weniger Wochen abschließen möchten. Sie erhalten einige Vorteile der fortgeschrittenen vollständigen Hybrid Migration ohne viele der Komplexitäten. Sie können steuern, wie viele und welche Postfächer zu einem bestimmten Zeitpunkt migriert werden. Office 365-Postfächer werden mit dem Benutzernamen und den Kennwörtern Ihrer lokalen Konten erstellt. und im Gegensatz zu Cutover-Migrationen müssen Ihre Benutzer Ihre Outlook-Profile nicht neu erstellen.

Wenn Sie eine minimale Hybrid Migration durchführen möchten, sollten Sie Folgendes beachten:

- Sie müssen eine einmalige Verzeichnissynchronisierung zwischen Ihren lokalen Active Directory-Servern und Office 365 durchführen.
- Benutzer können sich bei Ihrem Office 365-Postfach mit demselben Benutzernamen und Kennwort anmelden, die Sie bei der Migration Ihres Postfachs verwendet haben;
- Sie benötigen eine Office 365-Lizenz, die Exchange Online für jedes Benutzerpostfach umfasst, das Sie migrieren;
- Benutzer müssen auf den meisten Geräten kein neues Outlook-Profil einrichten (einige ältere Android-Telefone benötigen möglicherweise ein neues Profil) und müssen Ihre e-Mails nicht erneut herunterladen.

Weitere Informationen zur minimalen Hybrid Migration finden Sie unter [use minimal Hybrid to Quick migrate Exchange mailboxes to Office 365](https://support.office.com/article/Use-Minimal-Hybrid-to-quickly-migrate-Exchange-mailboxes-to-Office-365-fdecceed-0702-4af3-85be-f2a0013937ef)

### <a name="full-hybrid"></a>Vollhybrid

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

- Vollständige Hybrid Migrationen sind nicht für alle Arten von Organisationen geeignet. Aufgrund der Komplexität vollständiger Hybrid Migrationen können Organisationen mit weniger als ein paar hundert Postfächern normalerweise keine Vorteile erkennen, die den Aufwand und die Kosten für die Einrichtung eines solchen Typs rechtfertigen. Wenn dies wie Ihre Organisation klingt, empfehlen wir Ihnen dringend, stattdessen Cutover oder minimale Hybrid Migrationen zu erwägen.
- Sie müssen die Verzeichnissynchronisierung mit Azure Active Directory Connect (AADConnect) zwischen Ihren lokalen Active Directory-Servern und Office 365 einrichten.
- Benutzer können sich mit demselben Benutzernamen und Kennwort bei Ihrem Office 365-Postfach anmelden, wenn Sie sich beim lokalen Netzwerk anmelden (erfordert Azure Active Directory Connect mit Kennwortsynchronisierung und/oder Active Directory-Verbunddienste).
- Sie benötigen eine Office 365-Lizenz, die Exchange Online für jedes Benutzerpostfach umfasst, das Sie migrieren;
- Benutzer müssen auf den meisten Geräten kein neues Outlook-Profil einrichten (einige ältere Android-Telefone benötigen möglicherweise ein neues Profil) und müssen Ihre e-Mails nicht erneut herunterladen.

> [!IMPORTANT]
> Wenn sich Ihre Organisation für die Migration von Postfächern zu Office 365 entschieden hat, aber Dirsync oder Azure AD Connect beibehalten soll, um weiterhin Benutzerkonten aus dem lokalen Active Directory zu verwalten, müssen Sie mindestens einen lokalen Exchange-Server aufbewahren. Wenn der letzte Exchange-Server entfernt wurde, können Sie in Exchange Online keine Änderungen an Exchange-Empfängern vornehmen. Der Grund dafür ist, dass die Autoritäts Quelle in Ihrem lokalen Active Directory verbleibt und Änderungen vorgenommen werden müssen.

Wenn eine vollständige Hybrid Migration für Sie geeignet ist, sehen Sie sich die folgenden Ressourcen an, die Ihnen bei der Migration helfen:

- [Exchange-Bereitstellungs-Assistent](https://aka.ms/exdeploy)
- [Hybridbereitstellungen in Exchange Server](https://technet.microsoft.com/en-us/library/jj200581%28v=exchg.150%29.aspx)
- [Assistent für die Hybridkonfiguration](https://technet.microsoft.com/en-us/library/hh529921%28v=exchg.150%29.aspx)
- [FAQs zum Assistenten für die Hybridkonfiguration](https://technet.microsoft.com/en-us/library/mt488940%28v=exchg.150%29.aspx)
- [Voraussetzungen für die Hybridbereitstellung](https://technet.microsoft.com/en-us/library/hh534377%28v=exchg.150%29.aspx)

## <a name="upgrade-to-a-newer-version-of-exchange-server-on-premises"></a>Aktualisieren auf eine neuere Version von Exchange Server lokal

Wir sind zwar der festen Überzeugung, dass Sie durch die vollständige Migration zu Office 365 den bestmöglichen Nutzen und die optimale Benutzererfahrung erzielen können, aber wir wissen, dass einige Organisationen einige Exchange-Server lokal beibehalten müssen. Dies kann auf regulatorische Anforderungen hinweisen, um sicherzustellen, dass Daten nicht in einem Rechenzentrum in einem anderen Land gespeichert werden, oder es kann sein, dass Sie über eindeutige Einstellungen oder Anforderungen verfügen, die in der Cloud nicht erfüllt werden können, oder es könnte einfach sein, dass Sie Exchange Verwalten von Cloud-Postfächern, da Active Directory weiterhin lokal verwendet wird. In jedem Fall, für den Sie Exchange lokal auswählen oder beibehalten müssen, sollten Sie sicherstellen, dass Ihre Exchange 2010-Umgebung auf mindestens Exchange 2013 oder Exchange 2016 aktualisiert wurde und Exchange 2010 vor Ablauf des Support Datums entfernt wurde.

Für eine optimale Benutzerfreundlichkeit wird empfohlen, dass Sie die verbleibende lokale Umgebung auf Exchange 2016 aktualisieren. Sie müssen Exchange Server 2013 nicht installieren, wenn Sie von Exchange Server 2010 direkt zu Exchange Server 2016 wechseln möchten.

Exchange 2016 enthält alle Features und Fortschritte, die in früheren Versionen von Exchange enthalten sind, und entspricht den verfügbaren Funktionen von Office 365 (obwohl einige Features nur in Office 365 verfügbar sind). Sehen Sie sich die folgenden Dinge an:

| **Exchange-Release**                     | **Features**                                                                                                                                                                                                                                         |
|------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Exchange 2013                            | Vereinfachte Architektur reduziert die Anzahl der Serverrollen auf drei (Postfach, Client Zugriff, Edge-Transport)                                                                                                                                        |
|                                          | Richtlinien zur Verhinderung von Datenverlust (DLP), die dazu beitragen, vertrauliche Informationen nicht zu verlieren                                                                                                                                                                |
|                                          | Deutlich verbesserte Outlook Web App-Umgebung                                                                                                                                                                                                    |
| Exchange 2016                            | *Features von Exchange 2013 und...*                                                                                                                                                                                                                   |
|                                          | Weitere vereinfachte Serverrollen nur für Postfach-und Edge-Transport                                                                                                                                                                                   |
|                                          | Verbesserte DLP zusammen mit Integration in SharePoint                                                                                                                                                                                                  |
|                                          | Verbesserte Ausfallsicherheit von Datenbanken                                                                                                                                                                                                                         |
|                                          | Online Dokument Zusammenarbeit                                                                                                                                                                                                                        |

| **Berücksichtigt**                        | **Weitere Informationen**                                                                                                                                                                                                                                        |
|------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Ende der Support Termine                     | Wie bei Exchange 2010 hat jede Version von Exchange ein eigenes Ende des Support-Datums:                                                                                                                                                                        |
|                                          | **Exchange 2013** -April 2023                                                                                                                                                                                                                       |
|                                          | **Exchange 2016** -Oktober 2025                                                                                                                                                                                                                     |
|                                          | Je früher das Datum des Support Endes, desto schneller müssen Sie eine weitere Migration durchführen. April 2023 ist viel näher, als Sie denken!                                                                                                                 |
| Migrationspfad zu Exchange 2013 oder 2016  | Der Migrationspfad von Exchange 2010 zu einer neueren Version ist identisch, unabhängig davon, ob Sie Exchange 2013 oder Exchange 2016 wählen:                                                                                                                              |
|                                          | Installieren von Exchange 2013 oder 2016 in Ihrer vorhandenen Exchange 2010-Organisation Verschiebungs Dienste und andere Infrastruktur zu Exchange 2013 oder 2016 Verschieben von Postfächern und öffentlichen Ordnern in Exchange 2013 oder 2016 decommission Rest Exchange 2010 Servers  |
| Koexistenz der Version                      | Bei der Migration zu Exchange 2013 oder Exchange 2016 können Sie eine der beiden Versionen in einer vorhandenen Exchange 2010-Organisation installieren. Auf diese Weise können Sie einen oder mehrere Exchange 2013-oder Exchange 2016-Server installieren und Ihre Migration durchführen.             |
| Serverhardware                          | Die Server Hardwareanforderungen wurden von Exchange 2010 geändert. Sie müssen sicherstellen, dass die verwendete Hardware kompatibel ist. Weitere Informationen zu den Hardwareanforderungen für jede Version finden Sie hier:                                      |
|                                          | [System Anforderungen für Exchange 2016](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx)                                                                                                                                      |
|                                          | [System Anforderungen für Exchange 2013](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx)                                                                                                                                      |
|                                          | Sie werden feststellen, dass Sie mit den deutlichen Verbesserungen der Exchange-Leistung und der erhöhten Rechenleistung und Speicherkapazität auf neueren Servern wahrscheinlich weniger Server benötigen, um die gleiche Anzahl von Postfächern zu unterstützen.                       |
| Betriebssystemversion                 | Die mindestens unterstützten Betriebssystemversionen für jede Version sind:                                                                                                                                                                                |
|                                          | **Exchange 2016** Windows Server 2012                                                                                                                                                                                                                |
|                                          | **Exchange 2013** Windows Server 2008 R2 SP1                                                                                                                                                                                                         |
|                                          | Weitere Informationen zur Betriebssystemunterstützung finden Sie unter [Exchange supportable Matrix](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).                                                                        |
| Funktionsebene der Active Directory-Gesamtstruktur | Die mindestens unterstützten Active Directory-Gesamtstrukturfunktionsebenen für jede Version sind:                                                                                                                                                                |
|                                          | **Exchange 2016** Windows Server 2008 R2 SP1                                                                                                                                                                                                         |
|                                          | **Exchange 2013** Windows Server 2003                                                                                                                                                                                                                |
|                                          | Weitere Informationen zur Unterstützung der Funktionsebene der Gesamtstruktur finden Sie in der [Exchange-Unterstützungs Matrix](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).                                                                 |
| Office-Clientversionen                   | Die mindestens unterstützten Office-Clientversionen für jede Version sind:                                                                                                                                                                                   |
|                                          | **Exchange 2016** Office 2010 (mit den neuesten Updates)                                                                                                                                                                                              |
|                                          | **Exchange 2013** Office 2007 SP3                                                                                                                                                                                                                    |
|                                          | Weitere Informationen zum Office-Client Support finden Sie unter [Exchange supportable Matrix](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).                                                                           |

Sie können die folgenden Ressourcen verwenden, um Sie bei der Migration zu unterstützen:

- [Exchange-Bereitstellungs-Assistent](https://aka.ms/exdeploy)
- Änderungen am Active Directory-Schema für Exchange [2016](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.150%29.aspx)
- System Anforderungen für Exchange [2016](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx)
- Voraussetzungen für Exchange [2016](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.150%29.aspx)

## <a name="what-if-i-need-help"></a>Was geschieht, wenn ich Hilfe benötige?

Wenn Sie zu Office 365 migrieren, sind Sie möglicherweise berechtigt, unseren Microsoft-Dienst für "Service" zu verwenden. In diesem Artikel finden Sie bewährte Methoden, Tools und Ressourcen, um die Migration zu Office 365 so reibungslos wie möglich zu gestalten. Am besten haben Sie einen echten Supporttechniker, der Sie durch die Migration führt, von der Planung und dem Entwurf bis hin zur Migration Ihres letzten Postfachs. Wenn Sie mehr über schneller Informationen wissen möchten, sehen Sie sich die [Microsoft](https://fasttrack.microsoft.com/)-Einführung an.

Wenn bei der Migration zu Office 365 Probleme auftreten und Sie nicht mit der Übertragung oder mit ihrer Migration zu einer neueren Version von Exchange Server arbeiten, helfen wir Ihnen gerne. Hier finden Sie einige Ressourcen, die Sie verwenden können:

- [Technische Community](https://social.technet.microsoft.com/Forums/office/en-US/home?category=exchangeserver)
- [Support für Kunden](https://support.microsoft.com/en-us/gp/support-options-for-business)

## <a name="related-topics"></a>Verwandte Themen

[Ressourcen für das Upgrade von Office 2010-Servern und-Clients](https://docs.microsoft.com/en-us/office365/enterprise/upgrade-from-office-2010-servers-and-products)

[Office-Ruhestands Gruppe (Microsoft Tech Community)](https://go.microsoft.com/fwlink/?linkid=842065)
