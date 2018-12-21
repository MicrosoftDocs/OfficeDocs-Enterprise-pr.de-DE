---
title: Exchange 2010 Ende Unterstützung-Wegweiser
ms.author: dstrome
author: dstrome
manager: laurawi
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.assetid: e150e7b9-c432-4c8d-a0ae-c11847129a7d
description: Exchange 2010 nähert Ablauf des Supports. Verwenden Sie diese Planung Roadmap als Leitfaden zum Vorbereiten des Upgrades auf Exchange Online oder eine neuere Version von Exchange Server lokal.
ms.openlocfilehash: d9dcc2120f549c55fedc78483689dbded0a4464f
ms.sourcegitcommit: b45ad32a0a421d9834424e02838b6f941c259b9b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2018
ms.locfileid: "27382696"
---
# <a name="exchange-2010-end-of-support-roadmap"></a>Exchange 2010 Ende Unterstützung-Wegweiser

Klicken Sie auf **14 Januar 2020**wird Exchange Server 2010 Ablauf des Supports erreichen. Wenn Sie nicht bereits die Migration von Exchange 2010 nach Office 365 oder Exchange 2016 angefangen haben, ist nun die Zeit zum Starten der Planung.

## <a name="what-does-end-of-support-mean"></a>Welche funktioniert Ende Mittelwert Support?

Exchange-Server hat einen Supportlebenszyklus während der wir neue Features, Fehlerbehebungen, Sicherheitspatches und So weiter stellen wie fast alle Microsoft-Produkte. Dieser Lebenszyklus dauert in der Regel für zehn Jahren ab dem Zeitpunkt der ersten Version des Produkts, und das Ende dieser Lebenszyklus wird als das Produkt Ablauf des Supports bezeichnet. Wenn Exchange 2010 dessen Ablauf des Supports auf 14 Januar 2020 erreicht stellt Microsoft nicht mehr zur Verfügung:

- Technischen Support für Probleme, die auftreten können.
- Fehlerbehebungen für Probleme, die ermittelt werden und kann, die die Stabilität und Verwendbarkeit des Servers auswirken;
- Sicherheitsupdates für Sicherheitsrisiken, werden erkannt und, die möglicherweise den Server anfällig für Sicherheitslücken;
- Zeitzone aktualisiert.

Die Installation von Exchange 2010 wird weiterhin nach diesem Datum ausgeführt. Allerdings wird aufgrund der oben aufgeführten Änderungen, dringend empfohlen, dass Sie so bald wie möglich aus Exchange 2010 migrieren.

Weitere Informationen zu Office 2010-Servern fast den Ablauf des Supports finden Sie unter [Aktualisieren von Office 2010-Servern und Clients zu erleichtern](https://docs.microsoft.com/en-us/office365/enterprise/upgrade-from-office-2010-servers-and-products).

## <a name="what-are-my-options"></a>Welche Optionen sind?

Mit Exchange 2010 erreichen seiner Ablauf des Supports ist dies der ideale Zeitpunkt, Ihre Optionen und Vorbereiten eines Migrationsplans. Sie können:

- Migrieren Sie vollständig zu Office 365. Migrieren von Postfächern mit ü, minimale Hybrid oder vollständige hybridmigration und dann entfernen lokalen Exchange-Servern und Active Directory.
- Migrieren von Exchange 2010-Servern zu Exchange 2016 auf Ihren lokalen Servern.

> [!IMPORTANT]
> Ihrer Organisation zum Migrieren von Postfächern zu Office 365 auswählt, jedoch DirSync oder Azure AD-Connect direkten weiterhin von lokalen Active Directory-Benutzerkonten verwalten beibehalten möchte, müssen Sie mindestens eine lokale Exchange Server-Organisation beibehalten. Wenn der letzte Exchange Server entfernt wird, nicht Sie Änderungen an Exchange-Empfänger in Exchange Online vornehmen. Dies ist, da die Quelle der Behörde im lokalen Active Directory bleibt und Änderungen vorhanden getroffen werden müssen. In diesem Szenario müssen Sie die folgenden Optionen aus:

- (**Empfohlen**) Wenn können Sie Ihre Postfächer zu Office 365 migrieren und aktualisieren Ihre Server bis 14 Januar 2020, verwenden Sie Exchange 2010 um eine Verbindung mit Office 365 und Migrieren von Postfächern. Im nächsten Schritt migrieren von Exchange 2010 zu Exchange 2016 und außer Betrieb nehmen alle übrigen Exchange 2010-Servern.
- Wenn Sie die Migration von Postfächern können nicht abgeschlossen werden und der lokale Serverupgrade von 14 Januar 2020 zuerst aktualisieren Ihrer lokalen Exchange 2010-Servern auf Exchange 2016, verwenden Sie Exchange 2016 zum Verbinden mit Office 365 und Migrieren von Postfächern.

> [!NOTE]
> Während etwas komplizierter, können Sie während der Migration Ihrer lokalen Exchange 2010-Servers auf Exchange 2016 auch Postfächer zu Office 365 migrieren.

In den folgenden Abschnitten machen Sie sich jede Option ausführlich aus.

## <a name="migrate-to-office-365"></a>Migrieren zu Office 365

Migration Ihrer e-Mails zu Office 365 ist bewährte und einfachste Option, die Sie die Stilllegung der Exchange 2010-Bereitstellung unterstützen. Mit einer Migration zu Office 365 können Sie nur einen Hop von alten Technologie auf Features für die Art, wie vornehmen:

- Compliance-Funktionen wie etwa Aufbewahrungsrichtlinien, die In-Place und Aufbewahrung für eventuelle Rechtsstreitigkeiten, Compliance-eDiscovery und vieles mehr;
- Microsoft-Teams
- Power BI;
- Fokussierte Posteingang;
- Eingegangen Analytics;

Office 365 auch ruft neue Features und Erfahrungen erste und Sie und Ihre Benutzer können in der Regel Mal sofort verwendet. Zusätzlich zu den neuen Features müssen Sie dafür sorgen:

- Erwerb und die Wartung von Hardware;
- Bezahlung für Heizung und Kühlung Servern;
- Halten auf dem aktuellen Stand auf Sicherheit, Produkt- und Zeitzone Fixes;
- Verwalten von Speicher und Software zur Unterstützung von Compliance-Bestimmungen;
- Durchführen eines Upgrades auf eine neue Version von Exchange - befinden Sie sich immer auf die neueste Version von Exchange in Office 365.

### <a name="how-should-i-migrate-to-office-365"></a>Wie sollte der Migration zu Office 365?

Abhängig von Ihrer Organisation müssen Sie einige Optionen, die helfen Ihnen, zu Office 365 erhalten möchten. Bei der Auswahl einer Option für die Migration müssen Sie berücksichtigen sollten Sie einige Dinge wie die Anzahl der Arbeitsplätze oder Postfächer, die Sie verschieben möchten, wie lange die Migration bis zum letzten soll und gibt an, ob Sie eine nahtlose Integration zwischen Ihrer lokalen Installation und Office 365 während benötigen die Migration. Diese Tabelle zeigt die Migrationsoptionen und die wichtigsten Faktoren, die bestimmen, welche Methode müssen Sie verwenden möchten.

| **Die Option für Migration**     | **Größe der Organisation** | **Gültigkeitsdauer**        |
|--------------------------|-----------------------|---------------------|
| Übernahmemigration        | Weniger als 150 Arbeitsplätzen  | Eine Woche oder weniger      |
| Minimale hybridmigration | Weniger als 150 Arbeitsplätzen  | Einigen Wochen oder weniger |
| Vollständige hybridmigration    | Mehr als 150 Arbeitsplätzen   | Einigen Wochen oder mehr |

Die folgenden Abschnitte enthalten eine Übersicht über diese Methoden. Sehen Sie sich [auf einen Migrationspfad entscheiden](https://support.office.com/en-us/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27) , um die Details der einzelnen Methoden zu informieren.

### <a name="cutover-migration"></a>Übernahmemigration

Eine einstufige Migration wird, werden bei einer Überprüfung vor dem ausgewählten Datum und Uhrzeit, Sie alle Postfächer, Verteilergruppen, Kontakte und usw., Migration zu Office 365. Wenn Sie damit fertig sind, Sie Ihre lokale Exchange-Server herunterfahren und ausschließlich mithilfe von Office 365 zu starten.

Die übernahmemigration-Methode eignet sich für kleine Organisationen, die nicht über sehr viele Postfächer verfügen zu Office 365 schnell abrufen möchten, und nicht möchten, dass für den Umgang mit einiger die Komplexität der anderen Methoden. Aber es auch etwas eingeschränkt und, da es in einer Woche oder weniger abgearbeitet werden sollte, da es erfordert, dass Benutzer ihre Outlook-Profile neu konfigurieren. Während der übernahmemigration bis zu 2.000 Postfächer verarbeitet werden kann, wird dringend empfohlen, dass Sie mit dieser Methode maximal 150 Postfächer migrieren. Wenn Sie versuchen, die mehr als 150 Postfächer zu migrieren, können Sie nicht genügend Zeit für alle Postfächer zu übertragen, bevor der Deadline ausführen und Ihre Mitarbeiter abrufen können IT-Support eines Problems überlastet Benutzer konfigurieren Sie Outlook neu.

Wenn Sie beabsichtigen, dieses Ziel zu erreichen einer einstufigen Migrations hier sind einige Dinge müssen berücksichtigt werden sollten:

- Office 365 müssen Ihren Exchange 2010-Servern mithilfe von Outlook Anywhere über TCP-Port 443 herstellen.
- Alle lokalen Postfächern werden zu Office 365 verschoben werden.
- Sie benötigen eine lokale Administratorkonto, das über Lesezugriff auf den Inhalt der Postfächer der Benutzer verfügt;
- Die Exchange 2010 akzeptierte Domänen, die in Office 365 Notwendigkeit verwenden, um als überprüften Domänen im Dienst hinzugefügt werden soll;
- Zwischen dem Zeitpunkt, starten Sie die Migration und wenn Sie die Phase Fertigstellung beginnen, Office 365 wird in regelmäßigen Abständen synchronisieren der Office 365 und lokalen Postfächer. Auf diese Weise können Sie die Migration abschließen, ohne befürchten e-Mail in Ihrer lokalen Postfächer hinterlassen;
- Benutzer werden neue temporären Kennwörter für ihre Office 365-Konto eingerichtet, die sie benötigen, zu ändern, wenn sie sich bei ihren Postfächern zum ersten Mal anmelden;
- Sie benötigen eine Office 365-Lizenz, die Exchange Online für jedes Postfach des Benutzers enthält, den Sie migrieren;
- Benutzer müssen richten Sie ein neues Outlook-Profil auf jedem ihrer Geräte und ihre e-Mails erneut herunterladen. Die Menge an e-Mails, die Outlook herunterladen kann variieren. Weitere Informationen sehen Sie sich [ändern, wie viele e-Mail-Nachrichten an offline beibehalten](https://support.office.com/en-us/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&rs=en-US&ad=US&fromAR=1).

Weitere Informationen zum übernahmemigration betrachten:

- [Sie müssen über eine einstufige e-Mail-Migration zu Office 365 wissen sollten](https://support.office.com/en-us/article/What-you-need-to-know-about-a-cutover-email-migration-to-Office-365-961978ef-f434-472d-a811-1801733869da)
- [Ausführen einer einstufigen Migrations von e-Mails zu Office 365](https://support.office.com/en-us/article/Perform-a-cutover-migration-of-email-to-Office-365-9496e93c-1e59-41a8-9bb3-6e8df0cd81b4)

### <a name="minimal-hybrid-migration"></a>Minimale hybridmigration

Eine minimale Hybrid oder Express, ist Migration müssen Sie dabei ein paar Hundert Postfächer, die Sie zu Office 365 migrieren möchten, können die Migration innerhalb weniger Wochen abschließen und benötigen keine erweiterten Hybrid Migration-Features wie freigegebene Frei/Gebucht-Kalender Informationen.

Minimale hybridmigration eignet sich für Organisationen, die länger dauern ihren Postfächern zu Office 365, aber dennoch Plan für die Durchführung die Migration innerhalb weniger Wochen migrieren müssen. Sie möchten einige Vorteile der erweiterten vollständige hybridmigration ohne viele komplexe Eigenschaften. Sie können steuern, wie viele und welche, Postfächer zu einem bestimmten Zeitpunkt; migriert werden Office 365-Postfächer werden mit dem Benutzernamen und Kennwörter von ihren lokalen Konten erstellt werden. und im Gegensatz zu übernahmemigrationen, die Benutzer müssen nicht ihrer Outlook-Profile neu erstellen.

Wenn Sie beabsichtigen, dieses Ziel zu erreichen minimale hybridmigration werden hier einige Aspekte beachtet:

- Sie müssen zum Ausführen einer einmaligen verzeichnissynchronisierung zwischen Ihrer lokalen Active Directory-Server und Office 365.
- Benutzer werden möglicherweise melden Sie sich bei ihrem Office 365-Postfach mit dem gleichen Benutzernamen und das Kennwort, das sie verwendet haben, wenn ihr Postfach migriert wurde;
- Sie benötigen eine Office 365-Lizenz, die Exchange Online für jedes Postfach des Benutzers enthält, den Sie migrieren;
- Benutzer nicht müssen Sie ein neues Outlook-Profil auf die meisten ihrer Geräte einrichten (einige ältere Android-Telefone ggf. ein neues Profil) und müssen nicht erneut laden Sie ihre e-Mails.

Weitere Informationen zu minimalen hybridmigration betrachten Sie [Verwendung minimale hybride Exchange-Postfächern zu Office 365 schnell migrieren](https://support.office.com/article/Use-Minimal-Hybrid-to-quickly-migrate-Exchange-mailboxes-to-Office-365-fdecceed-0702-4af3-85be-f2a0013937ef)

### <a name="full-hybrid"></a>Vollständige hybrid

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

- Vollständige hybridmigrationen werden nicht für alle Arten von Organisationen geeignet. Aufgrund der Komplexität des vollständigen hybridmigrationen nicht Organisationen mit weniger als ein paar Hundert Postfächer in der Regel Vorteile angezeigt, die Aufwand und Kosten für erforderlich, um eine Liste einrichten zu rechtfertigen. Wenn dieses wie Ihre Organisation vorkommt, wird dringend empfohlen, dass Sie stattdessen Einstufige oder minimale hybridmigrationen berücksichtigen;
- Sie müssen zum Einrichten der verzeichnissynchronisierung zwischen Ihrer lokalen Active Directory-Server und Office 365 mit Azure Active Directory verbinden (AADConnect).
- Benutzer können ihre Office 365-Postfach mit dem gleichen Benutzernamen und Kennwort, die sie verwenden, wenn sie in das lokale Netzwerk anmelden (erfordert Azure Active Directory verbinden mit kennwortsynchronisierung und/oder Active Directory-Verbunddienste) anmelden können;
- Sie benötigen eine Office 365-Lizenz, die Exchange Online für jedes Postfach des Benutzers enthält, den Sie migrieren;
- Benutzer nicht müssen Sie ein neues Outlook-Profil auf die meisten ihrer Geräte einrichten (einige ältere Android-Telefone ggf. ein neues Profil) und müssen nicht erneut laden Sie ihre e-Mails.

> [!IMPORTANT]
> Ihrer Organisation zum Migrieren von Postfächern zu Office 365 auswählt, jedoch DirSync oder Azure AD-Connect direkten weiterhin von lokalen Active Directory-Benutzerkonten verwalten beibehalten möchte, müssen Sie mindestens eine lokale Exchange Server-Organisation beibehalten. Wenn der letzte Exchange Server entfernt wird, nicht Sie Änderungen an Exchange-Empfänger in Exchange Online vornehmen. Dies ist, da die Quelle der Behörde im lokalen Active Directory bleibt und Änderungen vorhanden getroffen werden müssen.

Wenn eine vollständige Hybrid-Migration Sounds für Sie geeigneten, sehen Sie sich die folgenden Ressourcen zur Unterstützung bei der Migration:

- [Exchange-Bereitstellungs-Assistent](https://aka.ms/exdeploy)
- [Hybridbereitstellungen in Exchange Server](https://technet.microsoft.com/en-us/library/jj200581%28v=exchg.150%29.aspx)
- [Assistent für die Hybridkonfiguration](https://technet.microsoft.com/en-us/library/hh529921%28v=exchg.150%29.aspx)
- [FAQs zum Assistenten für die Hybridkonfiguration](https://technet.microsoft.com/en-us/library/mt488940%28v=exchg.150%29.aspx)
- [Voraussetzungen für die Hybridbereitstellung](https://technet.microsoft.com/en-us/library/hh534377%28v=exchg.150%29.aspx)

## <a name="upgrade-to-a-newer-version-of-exchange-server-on-premises"></a>Durchführen eines Upgrades auf eine neuere Version von Exchange Server lokal

Während wir dringend glauben, dass Sie den Wert und Benutzer am besten erreichen können, von der Migration vollständig zu Office 365, wissen wir auch, dass in einigen Unternehmen einige lokalen Exchange-Servern zu übernehmen müssen. Aufgrund von Auflagen zu gewährleisten, Daten ist nicht in einem Rechenzentrum befindet sich in einem anderen Land oder wäre eindeutigen Einstellungen oder Anforderungen, die in der Cloud nicht erfüllt werden können, müssen Sie möglicherweise oder könnte einfach, dass die benötigten Exchange um Verwalten von Cloud-Postfächer, da Sie weiterhin lokalen Active Directory verwenden. In jedem Fall für die Sie ausgewählt oder Exchange lokal bleiben müssen, sollten Sie sicherstellen der Exchange 2010-Umgebung wird aktualisiert, um mindestens Exchange 2013 oder Exchange 2016 und Exchange 2010 vor Ablauf des Support Zeitspanne entfernt wird.

Für optimale Leistung wird empfohlen, dass die Aktualisierung der verbleibenden lokale Umgebung auf Exchange 2016. Sie müssen nicht Exchange Server 2013 installieren, wenn Sie gerade von Exchange Server 2010 zu Exchange Server 2016 wechseln möchten.

Exchange 2016 umfasst alle Features und Weiterentwicklungen, die mit früheren Versionen von Exchange enthalten, und die Erfahrung mit Office 365 verfügbar es am ehesten entspricht, (obwohl einige Features nur in Office 365 verfügbar sind). Schauen Sie sich nur einige der Aufgaben, die Sie fehlende out auf haben wurde:

| **Exchange-Version**                     | **Features**                                                                                                                                                                                                                                         |
|------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Exchange 2013                            | Reduzieren der Anzahl der Server-Rollen auf drei vereinfachte Architektur (Postfach, Clientzugriff, Edge-Transport)                                                                                                                                        |
|                                          | Datenrichtlinien von Datenverlust (DLP), die vertraulichen Informationen verloren gehen schützen                                                                                                                                                                |
|                                          | Erheblich verbesserte Outlook Web App-Leistung                                                                                                                                                                                                    |
| Exchange 2016                            | *Features von Exchange 2013 und...*                                                                                                                                                                                                                   |
|                                          | Weitere vereinfachte Serverrollen nur Postfach- und Edge-Transport                                                                                                                                                                                   |
|                                          | Verbesserte DLP zusammen mit der Integration mit SharePoint                                                                                                                                                                                                  |
|                                          | Verbesserte Datenbank von Standorten                                                                                                                                                                                                                         |
|                                          | Online-Dokument für die Zusammenarbeit                                                                                                                                                                                                                        |

| **Überlegung**                        | **Weitere Informationen**                                                                                                                                                                                                                                        |
|------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Ende des Zeitraums Unterstützung                     | Wie Exchange 2010 verfügt jede Version eines Exchange eigene Ende Support Datum:                                                                                                                                                                        |
|                                          | **Exchange 2013** – April 2023 zurück                                                                                                                                                                                                                       |
|                                          | **Exchange 2016** - Oktober 2025                                                                                                                                                                                                                     |
|                                          | Ende der Unterstützung von Datum, die früher müssen Sie die zuvor andere Migration ausführen. April 2023 ist viel näher, als man glaubt!                                                                                                                 |
| Migrationspfad für Exchange 2013 oder 2016  | Der Migrationspfad von Exchange 2010 auf eine neuere Version ist gleich, ob Sie Exchange 2013 oder Exchange 2016 auswählen:                                                                                                                              |
|                                          | Installieren von Exchange 2013 oder 2016 in Ihren vorhandenen Exchange 2010-Organisation verschieben-Diensten und anderen Infrastruktur für Exchange 2013 oder 2016 Move Postfächer und öffentlicher Ordner zu Exchange 2013 oder 2016 nehmen verbleibenden Exchange 2010-Servern  |
| Version-Koexistenz                      | Bei der Migration zu Exchange 2013 oder Exchange 2016 können Sie eine der beiden Versionen in einer vorhandenen Exchange 2010-Organisation installieren. So können Sie einen oder mehrere Exchange 2013 oder 2016 Exchange Server installieren und Ausführen der Migrations.             |
| Serverhardware                          | Hardwareanforderungen für wurden aus Exchange 2010 geändert. Sie müssen sicherstellen, dass die Hardware, die Sie verwenden möchten, kompatibel ist. Finden Sie weitere Informationen zu hardwareanforderungen für die einzelnen Versionen hier:                                      |
|                                          | [Systemanforderungen für Exchange 2016](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx)                                                                                                                                      |
|                                          | [Exchange 2013 System Requirements](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx)                                                                                                                                      |
|                                          | Sie werden feststellen, dass mit dem bedeutende Verbesserungen in Exchange-Leistung und höhere Leistung und die Speicherkapazität in neueren, Sie wahrscheinlich weniger Server unterstützt die gleiche Anzahl von Postfächern benötigen.                       |
| Betriebssystemversion                 | Die minimale unterstützte Betriebssystem-Versionen für die einzelnen Versionen sind:                                                                                                                                                                                |
|                                          | **Exchange 2016** WindowsServer 2012                                                                                                                                                                                                                |
|                                          | **Exchange 2013** Windows Server 2008 R2 SP1                                                                                                                                                                                                         |
|                                          | Weitere Informationen zur Unterstützung von Betriebssystem finden unter [Exchange Supportability Matrix](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).                                                                        |
| Active Directory-Gesamtstruktur-Funktionsebene | Die minimalen unterstützten Active Directory Gesamtstrukturfunktionsebenen für jede Version sind:                                                                                                                                                                |
|                                          | **Exchange 2016** Windows Server 2008 R2 SP1                                                                                                                                                                                                         |
|                                          | **Exchange 2013** WindowsServer 2003                                                                                                                                                                                                                |
|                                          | Weitere Informationen zur Gesamtstruktur funktionale Ebene-Unterstützung finden unter [Exchange Supportability Matrix](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).                                                                 |
| Office-Client-Versionen                   | Die minimalen unterstützten Office-Client-Versionen für die einzelnen Versionen sind:                                                                                                                                                                                   |
|                                          | **Exchange 2016** Office 2010 (mit den neuesten Updates)                                                                                                                                                                                              |
|                                          | **Exchange 2013** Office 2007 SP3                                                                                                                                                                                                                    |
|                                          | Weitere Informationen zum Office-Client-Unterstützung finden unter [Exchange Supportability Matrix](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).                                                                           |

Die folgenden Ressourcen können Sie Ihre Migration zu unterstützen:

- [Exchange-Bereitstellungs-Assistent](https://aka.ms/exdeploy)
- Active Directory-schemaänderungen für Exchange [2016](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.150%29.aspx)
- Systemanforderungen für Exchange [2016](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx)
- Voraussetzungen für Exchange [2016](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.150%29.aspx)

## <a name="what-if-i-need-help"></a>Was geschieht, wenn benötigen Sie Hilfe?

Wenn Sie zu Office 365 migrieren, möglicherweise Sie berechtigt, unsere FastTrack Microsoft-Dienst verwenden. Schnelle bietet best Practices, Tools und Ressourcen, die Ihre Migration zu Office 365 nahtlos und einfach funktioniert wie möglich gestalten. Schließlich müssen Sie eine echte Supporttechniker, die von der Planung Ihrer Migration durchgehen und zum Migrieren der letzten Postfächer entwerfen. Wenn Sie weitere Informationen zu der schnelle wissen möchten, sehen Sie sich [Schnell von Microsoft](https://fasttrack.microsoft.com/).

Wenn Sie Probleme während der Migrations zu Office 365 und Sie nicht, schnelle oder der Migration zu einer neueren Version von Exchange Server nutzen, sind wir bereit. Hier sind einige Ressourcen, die Sie verwenden können:

- [Technische-community](https://social.technet.microsoft.com/Forums/office/en-US/home?category=exchangeserver)
- [Support für Kunden](https://support.microsoft.com/en-us/gp/support-options-for-business)

## <a name="related-topics"></a>Verwandte Themen

[Ressourcen zum upgrade von Office 2010-Servern und clients](https://docs.microsoft.com/en-us/office365/enterprise/upgrade-from-office-2010-servers-and-products)

[Office Stilllegung Gruppe (Tech Center für Microsoft-Community)](https://go.microsoft.com/fwlink/?linkid=842065)
