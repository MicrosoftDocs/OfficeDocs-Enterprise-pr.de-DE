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
description: Hier finden Sie Antworten auf allgemeine Fragen zum Verschieben von Kern Daten in ein neues Rechenzentrum Geo.
ms.openlocfilehash: fe0392040f4a78d32e682e4f013db7a8ba49ebd5
ms.sourcegitcommit: 1c97471f47e1869f6db684f280f9085b7c2ff59f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/18/2019
ms.locfileid: "35782325"
---
# <a name="data-move-general-faq"></a>Allgemeine häufig gestellte Fragen zur Datenverschiebung

Hier finden Sie Antworten auf allgemeine Fragen zum Verschieben von Kern Daten in ein neues Rechenzentrum Geo.
  
## <a name="what-customers-are-eligible-to-request-a-move"></a>Welche Kunden sind berechtigt, eine Verlagerung anzufordern?
  
Vorhandene Office 365 Geschäftskunden, die ein Land ausgewählt haben, das für das neue Datencenter Geo berechtigt ist, können eine Verlagerung anfordern.  Das Programm besteht nur für Mandanten mit einem berechtigten Landescode, der dem Office 365 Mandanten zugewiesen ist, um die wichtigsten Kundendaten im Ruhezustand für berechtigte Arbeitsauslastungen an das entsprechende Office 365 Datacenter Geo zu migrieren.  Lesen Sie die Informationen unter Vorgehens [Weise zum Anfordern ihrer Datenverlagerung](request-your-data-move.md) , um die Berechtigung für das Land zu bestätigen.   

## <a name="how-do-we-define-core-customer-data"></a>Wie definieren wir die wichtigsten Kundendaten?
 
Kernkunden Daten ist ein Begriff, der auf eine Teilmenge von Kundendaten verweist, die in den [Microsoft Online Services-Bedingungen](https://go.microsoft.com/fwlink/p/?LinkID=249048)definiert sind: 
- Exchange Online Postfachinhalt (e-Mail-Text, Kalendereinträge und der Inhalt von e-Mail-Anlagen)
- SharePoint Online Websiteinhalt und die Dateien, die auf dieser Website gespeichert sind
- In OneDrive für Unternehmen hochgeladene Dateien 

## <a name="at-what-point-is-my-migration-complete-so-that-my-tenants-core-customer-data-is-being-stored-at-rest-in-my-new-geo"></a>An welchem Punkt ist meine Migration abgeschlossen, damit die Stammkunden Daten meines Mandanten im Rest in meinem neuen Geo gespeichert werden?

Aufgrund von gemeinsam genutzten Abhängigkeiten zwischen Exchange Online und SharePoint Online/OneDrive für Unternehmen kann eine Migration erst als abgeschlossen betrachtet werden, wenn beide Dienste migriert wurden.  Exchange Online und SharePoint Online/OneDrive für Unternehmen werden häufig zu getrennten Zeiten und unabhängig voneinander migriert.  Mandantenadministratoren erhalten eine Bestätigung im Nachrichten Center, wenn jede Dienst Migration abgeschlossen ist, und können die Datenspeicherkarte im Admin Center jederzeit anzeigen, um die wichtigsten Kundendaten am Rest-Speicherort für jeden Dienst zu bestätigen.

## <a name="will-my-tenant-automatically-be-moved-to-the-new-datacenter-geo"></a>Wird mein Mandant automatisch in das neue Rechenzentrum Geo verschoben?
 
Es gibt zwei Aktionen, die Sie als mandantenadministrator ausführen können.

- Opt-in.Registrieren Sie sich im Office 365 verschieben-Programm, und erhalten Sie eine festgelegte Frist für ihre Dienste zur Migration der Kernkunden Daten in Rest an das neue Rechenzentrum Geo.Auf der Seite Vorgehens [Weise anfordern ihrer Datenverlagerung](request-your-data-move.md) finden Sie Anweisungen zum Anmelden für das Programm.
- Keine Aktion ausführen.Keine Aktion, was dazu führt, dass Microsoft im Rahmen der Dienstverwaltung und-Optimierung im Laufe der Zeit ihre Kernkunden Daten in Ruhe auf Ihre neue Rechenzentrum-geografische Position umstellen kann.Ihre Daten können nur möglicherweise zu Ihrem neuen Geo-Rechenzentrum und nicht zu einem anderen Geo umsteigen.Wir benachrichtigen über das Nachrichten Center, wenn eine solche Dienst Verwaltungs Verlagerung abgeschlossen wurde.

## <a name="how-do-you-make-sure-my-customer-data-is-safe-during-the-move-and-that-i-wont-experience-downtime"></a>Wie stellen Sie sicher, dass meine Kundendaten während des Wechsels sicher sind und dass ich keine Ausfallzeiten erlebe?
  
Datenverschiebungen stellen einen Back-End-Dienstbetrieb mit minimalen Auswirkungen auf die Endbenutzer dar. Features, die betroffen sein können, werden in [während und nach der Datenverlagerung](during-and-after-your-data-move.md)aufgeführt. Wir halten uns an die [Vereinbarung zum Service Level (SLA) von Microsoft Online Services](https://go.microsoft.com/fwlink/p/?LinkId=523897) für die Verfügbarkeit, sodass Kunden während des Wechsels keine Vorbereitung oder Überwachung benötigen. 
  
Alle Office 365 Dienste führen die gleichen Versionen in den Rechenzentren aus, sodass Sie eine konsistente Funktionalität sicherstellen können. Ihr Dienst wird während des gesamten Prozesses vollständig unterstützt.
  
## <a name="what-is-the-impact-of-having-different-services-located-in-different-geos"></a>Wie wirkt sich die unterschiedlichen Dienste in verschiedenen GEOSS aus?

Einige der Office 365 Dienste befinden sich möglicherweise in unterschiedlichen GEOSS für einige vorhandene Kunden und für Kunden, die sich in der Mitte des Verschiebevorgangs befinden.  Unsere Dienste werden unabhängig voneinander ausgeführt, und es gibt keine Auswirkungen auf die Benutzererfahrung, wenn dies der Fall ist.Für Daten Wohnsitz Zwecke kann eine Mandanten Migration jedoch erst dann als abgeschlossen betrachtet werden, wenn sowohl Exchange Online als auch SharePoint Online/OneDrive für Unternehmen zu derselben Geo-Rechenzentrum migriert wurden.
  
## <a name="will-new-office-365-customers-be-automatically-provisioned-in-the-new-datacenter-geos"></a>Werden neue Office 365 Kunden automatisch im neuen Datencenter GEOS eingerichtet?
  
Ja. Sobald ein neues Rechenzentrums-Geo verfügbar ist, werden neue Office 365 für Geschäftskunden, die bei der Anmeldung ein Land auswählen, das für den neuen geografischen geografischen Standort berechtigt ist, ihre Kernkunden Daten in Rest im neuen Rechenzentrum-Geo speichern.
  
 ## <a name="where-is-my-core-customer-data-is-located"></a>Wo befinden sich meine Hauptkunden Daten?

Mandantenadministratoren können die Datenspeicherkarte im Admin Center jederzeit anzeigen, um die wichtigsten Kundendaten am Rest-Speicherort für jeden Dienst, speziell für Ihren Mandanten, zu bestätigen.Wir veröffentlichen auch den Speicherort von Datacenter GEOS, Rechenzentren und Speicherort Office 365 Kundendaten auf den [ Office 365 interaktiven Datencenter-Karten](https://office.com/datamaps) als Referenz für die aktuellen Standard-Stammkunden Daten an Rest-Standorten für neue Mandanten.  Sie können den Speicherort Ihrer Kundendaten im Ruhezustand über den Abschnitt Datenspeicherort unter Ihrem Organisationsprofil im Microsoft 365 Admin Center überprüfen.  
 
## <a name="when-will-i-be-able-to-request-a-move"></a>Wann kann ich eine Verlagerung anfordern?
  
Weitere Informationen finden Sie auf der Seite [Gewusst wie: anfordern ihrer Datenverlagerung](request-your-data-move.md) für unterstützte Zeitrahmen für Ihr Rechenzentrum Geo.
  
## <a name="how-can-i-request-to-be-moved"></a>Wie kann ich eine Verschiebung anfordern?
  
Für berechtigte Kunden wird eine Seite in Ihrem [Office 365 Administrator Portal](https://portal.office.com/)angezeigt. Weitere Informationen zum Anfordern einer Bewegung finden Sie unter Vorgehens [Weise anfordern der Datenverlagerung](request-your-data-move.md) . 
  
## <a name="can-i-change-my-selection-after-requesting-a-move"></a>Kann ich meine Auswahl ändern, nachdem ich eine Bewegung angefordert habe?
  
Es ist nicht möglich, Sie aus dem Prozess zu entfernen, nachdem Sie Ihre Anfrage abgesendet haben.
  
## <a name="what-happens-if-i-do-not-request-a-move-before-the-deadline"></a>Was geschieht, wenn ich vor Ablauf des Termins keine Umstellung beantrage?
  
 Möglicherweise können wir eine Anforderung ausnahmsweise annehmen, um Ihrem Mandanten einen festgelegten Termin für den Abschluss der Migration zu erteilen.Wenden  Sie sich an [Office 365 Support](https://go.microsoft.com/fwlink/p/?LinkID=522459) , um die Anforderung zu stellen.  Erinnern Sie sich daran, dass einige Arbeitsauslastungen möglicherweise auch ohne eine Opt-in-Anforderung zu Ihrem neuen Geo führen können, wenn Microsoft in der Lage ist, ihre Kernkunden Daten im Rest im Rahmen der Dienstverwaltung und-Optimierung im Laufe der Zeit auf Ihre neuen Rechenzentrum-Ressourcen zu migrieren.Ihre Daten können nur möglicherweise zu Ihrem neuen Geo-Rechenzentrum und nicht zu einem anderen Geo umsteigen.  Wir benachrichtigen über das Nachrichten Center, wenn eine solche Dienst Verwaltungs Verlagerung abgeschlossen wurde.
  
 ## <a name="what-if-i-want-to-move-my-data-in-order-to-get-better-network-performance"></a>Was geschieht, wenn ich meine Daten verlagern möchte, um eine bessere Netzwerkleistung zu erzielen?
  
Die Nähe zu einem Office 365 Rechenzentrum ist keine Garantie für eine bessere Netzwerkleistung. Es gibt viele Faktoren und Komponenten, die sich auf die Netzwerkleistung zwischen dem Endbenutzer und dem Office 365 Dienst auswirken. Weitere Informationen zu diesem Thema und zur Leistungsoptimierung finden Sie unter [Netzwerkplanung und Leistungsoptimierung für Office 365](network-planning-and-performance.md).
  
 ## <a name="do-all-the-services-move-their-data-on-the-same-day"></a>Werden die Daten von allen Diensten am gleichen Tag weiter verlagert?
 
Jeder Dienst wird unabhängig voneinander verschoben und wird seine Daten wahrscheinlich zu unterschiedlichen Zeiten verschieben.
  
 ## <a name="can-i-choose-when-i-want-my-data-to-be-moved"></a>Kann ich auswählen, wann meine Daten verschoben werden sollen?
 
 Kunden können kein bestimmtes Datum auswählen, Sie können die Verschiebung nicht verzögern, und es ist nicht möglich, ein bestimmtes Datum oder einen Zeitrahmen für die Verschiebungen freizugeben.
  
 ## <a name="can-you-share-when-my-data-will-be-be-moved"></a>Können Sie freigeben, wenn meine Daten verschoben werden?
  
Datenverschiebungen stellen einen Back-End-Vorgang mit minimalen Auswirkungen auf die Endbenutzer dar. Die Komplexität, Genauigkeit und Skalierung, bei der Datenverschiebungen in einer Global betriebenen und automatisierten Umgebung durchgeführt werden müssen, verbieten uns eine Freigabe, wenn eine Datenverschiebung für Ihren Mandanten oder einen anderen einzelnen Mandanten abgeschlossen werden soll. Kunden erhalten eine Bestätigung im Nachrichten Center pro teilnehmenden Dienst, wenn die Datenverlagerung abgeschlossen ist. 
  
 ## <a name="what-happens-if-users-access-services-while-the-data-is-being-moved"></a>Was geschieht, wenn Benutzer auf Dienste zugreifen, während die Daten verschoben werden?

Lesen Sie [während und nach der Datenverlagerung](during-and-after-your-data-move.md) eine vollständige Liste der Funktionen, die während der Datenverlagerung für jeden Dienst möglicherweise in Grenzen bleiben. 
  
 ## <a name="how-do-i-know-the-move-is-complete"></a>Woher weiß ich, dass die Migration abgeschlossen ist?
  
Sehen Sie sich das Office 365 Nachrichten Center an, um zu bestätigen, dass die Daten jedes Diensts abgeschlossen sind. Wenn die Daten jedes Diensts verschoben werden, wird ein Abschlusshinweis bereitgestellt, damit Sie drei Abschlussbenachrichtigungen erhalten: jeweils eine für Exchange Online, SharePoint Online und Skype for Business Online.  Sie können auch den Speicherort Ihrer Kundendaten im Ruhezustand über den Abschnitt Datenspeicherort unter Ihrem Organisationsprofil im Microsoft 365 Admin Center überprüfen.  
  
## <a name="i-am-an-office-365-customer-in-one-of-the-new-datacenter-geos-but-when-i-signed-up-i-selected-a-different-country-how-can-i-be-moved-to-the-new-datacenter-geo"></a>Ich bin ein Office 365 Kunde in einem der neuen Datencenter-GEOS, aber als ich mich anmeldete, habe ich ein anderes Land ausgewählt. Wie kann ich in das neue Rechenzentrum Geo verschoben werden?

Es ist nicht möglich, das mit Ihrem Mandanten verknüpfte Anmelde Land zu ändern. Stattdessen müssen Sie einen neuen Office 365 Mandanten mit einem neuen Abonnement erstellen und die Benutzer und Daten manuell in den neuen Mandanten verlagern.
  
## <a name="what-happens-if-we-are-in-process-of-email-data-migration-to-office-365-during-the-exchange-online-move"></a>Was geschieht, wenn wir im Rahmen der Exchange Online-Umstellung eine e-Mail-Datenmigration zu Office 365 durchführen?

Dies ist ein sehr häufiges Szenario und wird vollständig unterstützt.  Durch die Cloud-Migration zwischen dem Datencenter GEOS werden keine lokalen Cloud-Postfachmigrationen beeinträchtigt.
  
 ## <a name="can-i-pilot-some-users"></a>Kann ich ein Pilotprojekt für einige Benutzer durchmachen?
  
Sie können einen separaten Testmandanten erstellen, um die Konnektivität zu testen, aber der Testmandant kann auf keine Weise mit Ihrem vorhandenen Mandanten kombiniert werden.

## <a name="i-dont-want-to-wait-for-microsoft-to-move-my-data-can-i-just-create-a-new-tenant-and-move-myself"></a>Ich möchte nicht warten, bis Microsoft meine Daten verschiebt. Kann ich einfach einen neuen Mandanten erstellen und mich selbst verlagern?
  
Ja, allerdings ist der Prozess nicht so nahtlos, als ob Microsoft die Datenverlagerung durchführen würde.
  
Wenn Sie einen neuen Mandanten erstellen, nachdem der neue Datencenter-Geo verfügbar ist, wird der neue Mandant im neuen Geo gehostet. Dieser neue Mandant ist vollständig vom vorherigen Mandanten getrennt und Sie sind für das Verschieben aller Benutzerpostfächer, Websiteinhalte, Domänennamen und anderer Daten verantwortlich. Beachten Sie, dass Sie den Mandantennamen nicht von einem Mandanten in einen anderen verlagern können. Es wird empfohlen, dass Sie auf das von Microsoft bereitgestellte Verschiebungs Programm warten, da wir alle Einstellungen, Daten und Abonnements für Ihre Benutzer verschieben.
  
 ## <a name="im-not-ready-to-be-moved-can-i-pick-a-specific-move-date"></a>Kann ich nicht verschoben werden, kann ich ein bestimmtes Verschiebungsdatum auswählen?
  
Nein, es ist nicht möglich, dass Sie ändern, wenn die Hauptkunden Daten eines Diensts verschoben werden.
  
 ## <a name="my-customer-data-has-already-been-moved-to-a-new-datacenter-geo-can-i-move-back"></a>Meine Kundendaten wurden bereits in ein neues Rechenzentrum Geo verschoben. Kann ich zurückkehren?
 
Nein, dies ist nicht möglich. Kunden, die in neue Geo-Rechenzentren verschoben wurden, können nicht wieder verschoben werden. Als Kunde in einem beliebigen Geo-System haben Sie dieselben Dienst-, Leistungs-und Sicherheitskontrollen wie zuvor.  [Office 365 Multi-Geo](https://aka.ms/multi-geo) steht einigen Kunden als Add-on zur Verfügung und ermöglicht einem einzelnen Mandanten die Erstellung mehrerer Satelliten-GEOSS und das Verlegen von Benutzerdaten zu diesen GEOSS mit Daten Wohnsitz Verpflichtungen.
  
 ## <a name="do-the-new-datacenter-geos-use-the-same-versions-of-office-365-services-as-the-current-datacenter-geos"></a>Verwendet das neue Datacenter GEOS die gleichen Versionen von Office 365 Diensten wie das aktuelle Datencenter GEOS?

Ja.
  
## <a name="will-office-365-tenants-hosted-in-the-new-datacenters-be-available-to-users-outside-of-the-country"></a>Werden Office 365 Mandanten, die in den neuen Rechenzentren gehostet werden, für Benutzer außerhalb des Landes verfügbar sein?
  
A. Ja. Microsoft unterhält ein großes globales Netzwerk mit öffentlichen Internetverbindungen an mehr als 130 Standorten in 35 Ländern auf der ganzen Welt mit Peering-Vereinbarungen mit mehr als 2.700 Internetdienstanbietern (ISPs). Benutzer können auf die Rechenzentren überall dort zugreifen, wo Sie sich im Internet befinden.

## <a name="my-tenant-is-configured-for-office-365-multi-geohttpsakamsmulti-geo--can-i-still-enroll-in-my-tenant-in-the-office-365-move-program-to-change-my-default-geo-and-move-any-user-not-in-a-satellite-region-to-the-new-default-geo"></a>Mein Mandant ist für [Office 365 Multi-Geo](https://aka.ms/multi-geo)konfiguriert.  Kann ich mich noch in meinem Mandanten im Office 365 Programm "Verschiebe" anmelden, um meine Standard-Geo-Koordinaten zu ändern und alle Benutzer, die sich nicht in einer Satelliten Region befinden, in die neue Standard-Geo zu

Ja, Ihr Mandant ist berechtigt, sich anzumelden.  Wir verschieben alle Exo-Postfächer von Ihrem aktuellen Standard-Geo in Ihr neues lokales Rechenzentrum Geo.  Wir verschieben keine Exo-Postfächer, die in Multi-Geo-Satelliten Regionen konfiguriert sind, um weiterhin den Daten Wohnsitz für Satelliten Regionen wie beabsichtigt zu respektieren.  SharePoint Online und OneDrive für Unternehmen können nicht als Teil des verschieben-Programms zu dem neuen Geo-Rechenzentrum migriert werden, aber Sie können OneDrive für Unternehmen Freigaben so konfigurieren, dass Sie über das Multi-Geo-Programm in jede beliebige Region wechseln, die Sie wünschen.
  
## <a name="related-topics"></a>Verwandte Themen

[Verschieben der Kern Daten in das neue Office 365-Rechenzentrum GEOS](moving-data-to-new-datacenter-geos.md)

[Anfordern der Datenverschiebung](request-your-data-move.md)

[Office 365 Multi Geo](https://aka.ms/multi-geo)

[Office 365 interaktive Rechenzentrums Karte](https://office.com/datamaps)

[Office 365 Support](https://go.microsoft.com/fwlink/p/?LinkID=522459)

[Neues Datacenter GEOS für Microsoft Dynamics CRM Online](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[Azure-Dienste nach Region](https://azure.microsoft.com/en-us/regions/)
