---
title: Allgemeine häufig gestellte Fragen zur Datenverschiebung
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 09/05/2018
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 1f01bc6f-5d37-4d14-bdd3-9d94a1e23e14
description: Hier finden Sie Antworten auf allgemeine Fragen zum Bewegen von Kern Daten in ein neues Datacenter Geo.
ms.openlocfilehash: 29706f49ee0faf8c535b50843f224b7b1b2a372e
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067899"
---
# <a name="data-move-general-faq"></a>Allgemeine häufig gestellte Fragen zur Datenverschiebung

Hier finden Sie Antworten auf allgemeine Fragen zum Bewegen von Kern Daten in ein neues Datacenter Geo.
  
## <a name="what-customers-are-eligible-to-request-a-move"></a>Welche Kunden sind berechtigt, eine Verschiebung anzufordern?
  
Vorhandene Office 365-kommerzielle Kunden, die ein Land ausgewählt haben, das für das neue Datencenter Geo qualifiziert ist, können eine Verschiebung anfordern.  Das Programm ist nur für Mandanten mit einem berechtigten Ländercode vorhanden, der dem Office 365-Mandanten zugeordnet ist, um die Kernkunden Daten in Rest für berechtigte Arbeitsauslastungen in das entsprechende Office 365 Datacenter Geo zu migrieren.  Weitere Informationen finden Sie auf der Seite " [How to Request Your Data Move](request-your-data-move.md) ".   

## <a name="how-do-we-define-core-customer-data"></a>Wie definieren wir zentrale Kundendaten?
 
Die wichtigsten Kundendaten beziehen sich auf eine Teilmenge der Kundendaten, die in den [Microsoft Online Services-Bedingungen](https://go.microsoft.com/fwlink/p/?LinkID=249048)definiert sind: 
- Exchange Online-Postfachinhalt (e-Mail-Text, Kalendereinträge und der Inhalt von e-Mail-Anlagen)
- SharePoint Online-Websiteinhalt und die auf dieser Website gespeicherten Dateien
- Hochgeladene Dateien in OneDrive for Business 

## <a name="at-what-point-is-my-migration-complete-so-that-my-tenants-core-customer-data-is-being-stored-at-rest-in-my-new-geo"></a>An welchem Punkt wird meine Migration abgeschlossen, damit die Stammkunden Daten meines Mandanten in meinem neuen Geo gespeichert werden?

Aufgrund der freigegebenen Abhängigkeiten zwischen Exchange Online und SharePoint Online/OneDrive for Business kann eine Migration erst dann als abgeschlossen betrachtet werden, wenn beide Dienste migriert werden.  Exchange Online und SharePoint Online/OneDrive for Business migrieren häufig zu unterschiedlichen Zeiten und unabhängig voneinander.  Mandantenadministratoren erhalten eine Bestätigung im Nachrichten Center, wenn jede Dienst Migration abgeschlossen ist, und können die Daten Standort Karte im Admin Center jederzeit anzeigen, um die wichtigsten Kundendaten am Rest-Standort für jeden Dienst zu bestätigen.

## <a name="will-my-tenant-automatically-be-moved-to-the-new-datacenter-geo"></a>Wird mein Mandant automatisch in das neue Datencenter Geo verschoben?
 
Es gibt zwei Aktionen, die Sie als mandantenadministrator ausführen können.

- Opt-in.Melden Sie sich beim Office 365 Move-Programm an, und erhalten Sie einen festgelegten Stichtag für ihre Dienste zur Migration von Kernkunden Daten im Rest zum neuen Datacenter Geo.Anweisungen dazu, wie Sie sich für das Programm anmelden, finden Sie auf der Seite " [How to Request Your Data Move](request-your-data-move.md) ".
- Keine Aktion ausführen.Nehmen Sie keine Aktion vor, was dazu führt, dass Microsoft Ihre Kernkunden Daten im Laufe der Zeit im Rahmen der Dienstverwaltung und-Optimierung zu Ihrem neuen Rechenzentrum bewegen kann.Ihre Daten können nur potenziell zu Ihrem neuen Datacenter Geo, nicht zu einem anderen Geo, verschoben werden.Wir benachrichtigen über das Nachrichten Center, wenn eine solche Dienstverwaltung verschoben wurde.

## <a name="how-do-you-make-sure-my-customer-data-is-safe-during-the-move-and-that-i-wont-experience-downtime"></a>Wie stellen Sie sicher, dass meine Kundendaten während des Umzugs sicher sind und dass ich keine Ausfallzeiten erlebe?
  
Bei Datenverschiebungen handelt es sich um einen Back-End-Dienstvorgang mit minimalen Auswirkungen auf die Endbenutzer. Features, die beeinträchtigt werden können, werden [während und nach der Datenverschiebung](during-and-after-your-data-move.md)aufgeführt. Wir halten uns an die [Microsoft Online Services-Vereinbarung zum Service Level (SLA)](https://go.microsoft.com/fwlink/p/?LinkId=523897) für die Verfügbarkeit, sodass Kunden für die Vorbereitung oder Überwachung während des Umzugs nichts benötigen. 
  
Alle Office 365-Dienste führen die gleichen Versionen in den Rechenzentren aus, sodass Sie eine konsistente Funktionalität sicherstellen können. Der Dienst wird vollständig unterstützt.
  
## <a name="what-is-the-impact-of-having-different-services-located-in-different-geos"></a>Welche Auswirkungen haben unterschiedliche Dienste in verschiedenen GEOSS?

Einige der Office 365-Dienste können sich für einige vorhandene Kunden und für Kunden, die sich in der Mitte des Verschiebungsprozesses befinden, in unterschiedlichen GEOSS befinden.  Unsere Dienste werden unabhängig voneinander ausgeführt, und es gibt keine Auswirkungen auf die Benutzerfreundlichkeit, wenn dies der Fall ist.Für Daten Residency-Zwecke kann eine Mandanten Migration jedoch erst dann als abgeschlossen betrachtet werden, wenn sowohl Exchange Online als auch SharePoint Online/OneDrive for Business zu demselben Datacenter Geo migriert werden.
  
## <a name="will-new-office-365-customers-be-automatically-provisioned-in-the-new-datacenter-geos"></a>Werden neue Office 365-Kunden automatisch im neuen Datencenter GEOS eingerichtet?
  
Ja. Sobald ein neues Datacenter Geo verfügbar ist, haben neue Office 365 for Business-Kunden, die während der Registrierung ein Land ausgewählt haben, das für das neue Geo als Land geeignet ist, ihre Kernkunden Daten im neuen Datacenter Geo gespeichert.
  
 ## <a name="where-is-my-core-customer-data-is-located"></a>Wo befinden sich meine wichtigsten Kundendaten?

Mandantenadministratoren können die Daten Standort Karte im Admin Center jederzeit anzeigen, um die wichtigsten Kundendaten am Rest-Standort für jeden Dienst, insbesondere für Ihren Mandanten, zu bestätigen.Außerdem veröffentlichen wir den Standort von Datacenter GEOS, Rechenzentren und Speicherort von Office 365-Kundendaten im [ Office 365 Interactive Datacenter Maps](https://office.com/datamaps) als Referenz für die aktuellen Standard Kundendaten an Rest-Standorten für neue Mandanten.  Sie können den Speicherort Ihrer Kundendaten im Rest über den Abschnitt Datenspeicherort unter Ihrem Organisationsprofil im Office 365 Admin Center überprüfen.  
 
## <a name="when-will-i-be-able-to-request-a-move"></a>Wann kann ich eine Verschiebung anfordern?
  
Weitere Informationen finden Sie auf der Seite [Gewusst wie: Anfordern der Datenverschiebung](request-your-data-move.md) für unterstützte Zeiträume für Ihr Datacenter Geo.
  
## <a name="how-can-i-request-to-be-moved"></a>Wie kann ich eine Verschiebung anfordern?
  
Berechtigte Kunden sehen eine Seite in Ihrem [Office 365-Administrator Portal](https://portal.office.com/). Informationen dazu, wie Sie eine Verschiebung anfordern, finden Sie unter [So fordern Sie die Datenverschiebung](request-your-data-move.md) an. 
  
## <a name="can-i-change-my-selection-after-requesting-a-move"></a>Kann ich meine Auswahl ändern, nachdem ich eine Verschiebung angefordert habe?
  
Es ist nicht möglich, Sie zu entfernen, nachdem Sie Ihre Anfrage übermittelt haben.
  
## <a name="what-happens-if-i-do-not-request-a-move-before-the-deadline"></a>Was geschieht, wenn ich vor Ablauf des Termins keine Verschiebung beantrage?
  
 Möglicherweise können wir eine Anforderung ausnahmsweise akzeptieren, um Ihrem Mandanten einen zugesicherten Termin zu gewähren, um die Verschiebung abzuschließen.Wenden  Sie sich an den [Office 365-Support](https://go.microsoft.com/fwlink/p/?LinkID=522459) , um die Anforderung zu stellen.  Bedenken Sie, dass einige Arbeitsauslastungen möglicherweise auch ohne eine Opt-in-Anforderung zu Ihrem neuen geografischen Standort verschoben werden, da Microsoft in der Lage ist, ihre Kernkunden Daten im Rahmen der Dienstverwaltung und-Optimierung im Laufe der Zeit in Ihr neues Datacenter zu verschieben.Ihre Daten können nur potenziell zu Ihrem neuen Datacenter Geo, nicht zu einem anderen Geo, verschoben werden.  Wir benachrichtigen über das Nachrichten Center, wenn eine solche Dienstverwaltung verschoben wurde.
  
 ## <a name="what-if-i-want-to-move-my-data-in-order-to-get-better-network-performance"></a>Was geschieht, wenn meine Daten verschoben werden sollen, um eine bessere Netzwerkleistung zu erzielen?
  
Die Nähe zu einem Office 365-Datencenter ist keine Garantie für eine bessere Netzwerkleistung. Es gibt zahlreiche Faktoren und Komponenten, die sich auf die Netzwerkleistung zwischen dem Endbenutzer und dem Office 365-Dienst auswirken. Weitere Informationen zu dieser und Leistungsoptimierung finden Sie unter [Netzwerkplanung und Leistungsoptimierung für Office 365](network-planning-and-performance.md).
  
 ## <a name="do-all-the-services-move-their-data-on-the-same-day"></a>Verschieben alle Dienste Ihre Daten am selben Tag?
 
Jeder Dienst wird unabhängig voneinander verschoben, und die Daten werden wahrscheinlich zu unterschiedlichen Zeiten verschoben.
  
 ## <a name="can-i-choose-when-i-want-my-data-to-be-moved"></a>Kann ich auswählen, wann meine Daten verschoben werden sollen?
 
 Kunden können kein bestimmtes Datum auswählen, Sie können ihre Verschiebung nicht verschieben, und wir können kein bestimmtes Datum oder einen bestimmten Zeitraum für die Verschiebungen freigeben.
  
 ## <a name="can-you-share-when-my-data-will-be-be-moved"></a>Können Sie freigeben, wenn meine Daten verschoben werden?
  
Datenverschiebungen sind ein Back-End-Vorgang mit minimalen Auswirkungen auf die Endbenutzer. Die Komplexität, Genauigkeit und Skalierung, mit der Datenverschiebungen in einer Global betriebenen und automatisierten Umgebung durchgeführt werden müssen, untersagen uns, wenn eine Datenverschiebung für Ihren Mandanten oder einen anderen einzelnen Mandanten abgeschlossen werden soll. Kunden erhalten eine Bestätigung im Nachrichten Center pro teilnehmenden Dienst, wenn die Datenverschiebung abgeschlossen ist. 
  
 ## <a name="what-happens-if-users-access-services-while-the-data-is-being-moved"></a>Was geschieht, wenn Benutzer während der Verschiebung der Daten auf Dienste zugreifen?

Sehen Sie [während und nach der Datenverschiebung](during-and-after-your-data-move.md) eine vollständige Liste der Features, die während der Datenverschiebung für jeden Dienst eingeschränkt werden können. 
  
 ## <a name="how-do-i-know-the-move-is-complete"></a>Woher weiß ich, dass die Verschiebung abgeschlossen ist?
  
Sehen Sie sich das Office 365-Nachrichten Center an, um zu bestätigen, dass die Verschiebung der einzelnen Dienst Daten abgeschlossen ist. Wenn die Daten der einzelnen Dienste verschoben werden, wird ein Abschlusshinweis bereitgestellt, sodass Sie drei Abschlussbenachrichtigungen erhalten: jeweils eine für Exchange Online, SharePoint Online und Skype for Business Online.  Sie können den Speicherort Ihrer Kundendaten auch über den Abschnitt Datenspeicherort unter Ihrem Organisationsprofil im Office 365 Admin Center überprüfen.  
  
## <a name="i-am-an-office-365-customer-in-one-of-the-new-datacenter-geos-but-when-i-signed-up-i-selected-a-different-country-how-can-i-be-moved-to-the-new-datacenter-geo"></a>Ich bin ein Office 365-Kunde in einem der neuen Datencenter GEOSS, aber als ich mich angemeldet habe, habe ich ein anderes Land ausgewählt. Wie kann ich zum neuen Datencenter Geo verschoben werden?

Es ist nicht möglich, das mit Ihrem Mandanten verknüpfte Anmelde Land zu ändern. Stattdessen müssen Sie einen neuen Office 365-Mandanten mit einem neuen Abonnement erstellen und Ihre Benutzer und Daten manuell in den neuen Mandanten verschieben.
  
## <a name="what-happens-if-we-are-in-process-of-email-data-migration-to-office-365-during-the-exchange-online-move"></a>Was geschieht, wenn die e-Mail-Datenmigration zu Office 365 während der Exchange Online-Verschiebung erfolgt?

Dies ist ein sehr häufiges Szenario und wird vollständig unterstützt.  Die Cloud-Migration zwischen dem Datencenter GEOS stört keine lokalen Cloud-Postfachmigrationen.
  
 ## <a name="can-i-pilot-some-users"></a>Kann ich einige Benutzer pilotieren?
  
Sie können einen separaten Testmandanten erstellen, um die Konnektivität zu testen, aber der Testmandant kann nicht mit Ihrem vorhandenen Mandanten kombiniert werden.

## <a name="i-dont-want-to-wait-for-microsoft-to-move-my-data-can-i-just-create-a-new-tenant-and-move-myself"></a>Ich möchte nicht warten, bis Microsoft meine Daten verschiebt. Kann ich einen neuen Mandanten erstellen und mich selbst verschieben?
  
Ja, der Prozess ist jedoch nicht so nahtlos, als ob Microsoft die Datenverschiebung ausführen würde.
  
Wenn Sie einen neuen Mandanten erstellen, nachdem das neue Datencenter Geo verfügbar ist, wird der neue Mandant in der neuen Geo gehostet. Dieser neue Mandant ist vollständig von Ihrem vorherigen Mandanten getrennt, und Sie sind für das Verschieben aller Benutzerpostfächer, Websiteinhalte, Domänennamen und anderer Daten verantwortlich. Beachten Sie, dass der Mandantenname nicht von einem Mandanten zu einem anderen verschoben werden kann. Es wird empfohlen, dass Sie auf das von Microsoft bereitgestellte Verschiebungs Programm warten, da wir alle Einstellungen, Daten und Abonnements für Ihre Benutzer verschieben.
  
 ## <a name="im-not-ready-to-be-moved-can-i-pick-a-specific-move-date"></a>Ich bin nicht bereit, verschoben zu werden, kann ich einen bestimmten Verschiebungs Termin wählen?
  
Nein, es ist nicht möglich, zu ändern, wann die wichtigsten Kundendaten des Diensts verschoben werden.
  
 ## <a name="my-customer-data-has-already-been-moved-to-a-new-datacenter-geo-can-i-move-back"></a>Meine Kundendaten wurden bereits in ein neues Datacenter Geo verschoben. Kann ich zurückkehren?
 
Nein, dies ist nicht möglich. Kunden, die in neue Geo-Rechenzentren verschoben wurden, können nicht zurück verschoben werden. Als Kunde in einer Geo-Umgebung erleben Sie dieselben Dienst-, Leistungs-und Sicherheitskontrollen wie zuvor.  [Office 365 Multi Geo](https://aka.ms/multi-geo) steht einigen Kunden als Add-on zur Verfügung und ermöglicht es einem einzelnen Mandanten, mehrere Satelliten-GEOSS zu erstellen und Benutzerdaten in diese GEOS mit Daten Wohnsitz Zusagen zu verschieben.
  
 ## <a name="do-the-new-datacenter-geos-use-the-same-versions-of-office-365-services-as-the-current-datacenter-geos"></a>Verwenden die neuen Datencenter GEOSS die gleichen Versionen von Office 365 Services wie das aktuelle Datacenter GEOS?

Ja.
  
## <a name="will-office-365-tenants-hosted-in-the-new-datacenters-be-available-to-users-outside-of-the-country"></a>Werden Office 365-Mandanten, die in den neuen Datencentern gehostet werden, Benutzern außerhalb des Landes zur Verfügung gestellt?
  
A. Ja. Microsoft unterhält ein umfangreiches globales Netzwerk mit öffentlichen Internetverbindungen an mehr als 130 Standorten in 35 Ländern weltweit mit Peering-Vereinbarungen mit mehr als 2.700 Internetdienstanbietern (ISPs). Benutzer können von überall im Internet auf die Datencenter zugreifen.

## <a name="my-tenant-is-configured-for-office-365-multi-geohttpsakamsmulti-geo--can-i-still-enroll-in-my-tenant-in-the-office-365-move-program-to-change-my-default-geo-and-move-any-user-not-in-a-satellite-region-to-the-new-default-geo"></a>Mein Mandant ist für [Office 365 Multi Geo](https://aka.ms/multi-geo)konfiguriert.  Kann ich mich noch in meinem Mandanten im Office 365 Move-Programm anmelden, um meine Standard-Geo zu ändern und einen beliebigen Benutzer, der sich nicht in einer Satelliten Region befindet, auf den neuen Standard Geo zu verschieben?

Ja, Ihr Mandant ist berechtigt, sich anzumelden.  Wir werden alle Exo-Postfächer von Ihrer aktuellen Standard-Geo-Daten in Ihr neues lokales Datencenter Geo verschieben.  In Multi-Geo-Satelliten Regionen konfigurierte Exo-Postfächer werden nicht verschoben, um weiterhin die Satelliten Gebietsdaten-Residency zu respektieren, wie Sie es beabsichtigt haben.  SharePoint Online und OneDrive for Business können nicht als Teil des Move-Programms zur neuen Datencenter-geografischen Migration migriert werden, obwohl Sie OneDrive für Business-Freigaben so konfigurieren können, dass Sie über das Multi-Geo-Programm in eine beliebige Region wechseln.
  
## <a name="related-topics"></a>Verwandte Themen

[Moving Core Data to New Office 365 Datacenter GEOS](moving-data-to-new-datacenter-geos.md)

[Anfordern der Datenverschiebung](request-your-data-move.md)

[Office 365 Multi Geo](https://aka.ms/multi-geo)

[Office 365 Interactive Datacenter-Zuordnung](https://office.com/datamaps)

[Office 365-Unterstützung](https://go.microsoft.com/fwlink/p/?LinkID=522459)

[Neues Datencenter GEOS für Microsoft Dynamics CRM Online](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[Azure-Dienste nach Region](https://azure.microsoft.com/en-us/regions/)
