---
title: Office 365 von Datenvernichtung
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: Eine Übersicht über Microsoft-Richtlinien zur Wiederverwendung, Entsorgung oder Vernichtung von Office 365 Datenträgern und Servern im Rechenzentrum.
ms.openlocfilehash: 41971cc690d0e1560f2cf7f5bc3ad544e8dab5c6
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067418"
---
# <a name="office-365-data-destruction"></a>Office 365 von Datenvernichtung

## <a name="physical-data-destruction"></a>Physische Datenvernichtung

Microsoft verfügt über Datenverarbeitung von Standard Richtlinien, die die Wiederverwendung und Entsorgung von Laufwerken sowie fehlgeschlagene oder nicht abziehende Server behandeln. Vor der Wiederverwendung von Office 365-Laufwerken führt Microsoft einen physikalischen Säuberungsprozess durch, der mit dem National Institute of Standards and Technology Special Publication 800-88 ([NIST SP 800-88-Richtlinien für die Medien Desinfektion](http://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-88r1.pdf)) konsistent ist. Da alle Laufwerke in Office 365 mithilfe der BitLocker-Verschlüsselung auf Datenträgerebene verschlüsselt werden, ist NIST SP 800-88-konforme Löschung technisch nicht erforderlich. Dennoch führt Microsoft diesen Prozess aus.

Fehlerhafte Datenträger, die in Office 365-Rechenzentren verwendet werden, werden physisch zerstört und über den ISO-Prozess überwacht. Asset Type bestimmt die entsprechenden Entsorgungsmethoden. Bei Festplatten, die nicht gelöscht werden können, verwendet Microsoft einen Vernichtungsprozess, um die Medien zu zerstören und die Wiederherstellung von Informationen zu verunmöglichen. Beispielsweise werden Datenträger physisch zerstört, pulverisiert oder verbrannt. Microsoft behält alle Datensätze der Zerstörung bei und führt einen ähnlichen Säuberungsvorgang auf Servern durch, die in Office 365 wieder verwendet werden. Diese Richtlinien umfassen sowohl die elektronische als auch die physische Bereinigung.

Jedes Rechenzentrum verwendet einen physischen Vernichtungsprozess vor Ort, um seine Datenträger zu entsorgen. Sichere Lagerplätze für Speichermedien, die für die Datenträger Entsorgung bestimmt sind, befinden sich in jedem Bereich des Rechenzentrums. Jede sichere bin-Station verfügt über Überwachung der Videoüberwachung. Sobald ein Abfallbehälter eine Kapazität von etwa 50% erreicht, kontaktiert das Team der Websitedienste das Team für die physische Sicherheit, um die Entfernung zu koordinieren. Websitedienste-Mitarbeiter und ein Sicherheitsbüro entfernen Sie den sicheren Entsorgungsplatz, und legen Sie ihn in einem festgelegten sicheren Speicherbereich ab. Richtlinien und Verfahren für die Handhabung von Datenträgern während der Entsorgung werden routinemäßig getestet, einschließlich Verfahren zur Sicherstellung des Zustands von Maschinen zur Vernichtung genehmigt.

Beim Daten Vernichtungsvorgang werden Datenträger in einer Weise gelöscht, die mit NIST 800-88 (sofern möglich) konform ist und dann in einen industriellen Shredder eingefügt und physisch abgerissen wird. Microsoft behält die Verantwortung für Objekte, die das Rechenzentrum mit NIST SP 800-88 konsistente Bereinigung/Bereinigung, Zerstörung von Objekten, Verschlüsselung, exakte Inventarisierung, Nachverfolgung und Schutz der Aufbewahrungskette während des Transports verlassen. Dieser Prozess wird über das Fernsehen mit geschlossenem stromkreisüberwacht, und nach Abschluss des Vorgangs wird ein Vernichtungs Zertifikat ausgestellt.

Microsoft verwendet Daten Löschungs Einheiten von " [Extreme Protocol Solutions](http://www.enterprisedataerasure.com/) " (EPS). EPS-Software unterstützt NIST SP 800-88 Anforderungen für die Bereinigung und Bereinigung/sichere Löschung. Vor der Bereinigung oder Vernichtung wird ein Inventar vom Microsoft Asset Manager erstellt. Wenn ein Lieferant für die Vernichtung verwendet wird, stellt der Anbieter ein Vernichtungs Zertifikat für jedes zerstörte Objekt bereit, das vom Vermögensverwalter überprüft wird.

## <a name="virtual-data-destruction"></a>Zerstörung virtueller Daten

Microsoft verfügt über Richtlinien und Verfahren für die Datenverarbeitung, die eine effektive virtuelle Vernichtung von Daten zum Schutz vor der Möglichkeit verhindern, dass Daten zwischen Dienst Mandanten ungeeignet freigegeben werden oder nach dem Löschen im Dienst zugänglich sind. Daten, die aus dem Dienst in einem Mandanten gelöscht werden, sind für einen anderen Dienst Mandanten nicht zugänglich, auch wenn einer der zugrunde liegenden physischen Speichers neu zugewiesen wird. Dies ist ein Ergebnis der verschärften Effekte von mehreren Virtualisierungs-und Fragmentierungs Technologien, die zum Skalieren virtueller Umgebungen verwendet werden, dem aktiven Löschverhalten von Anwendungen innerhalb der einzelnen Dienst Mandanten (beispielsweise [Seiten Löschung](https://docs.microsoft.com/office365/securitycompliance/office-365-exchange-online-data-deletion#page-zeroing)) und der erforderlichen Verschlüsselungsprozesse für Medien-und Anwendungsinhalte