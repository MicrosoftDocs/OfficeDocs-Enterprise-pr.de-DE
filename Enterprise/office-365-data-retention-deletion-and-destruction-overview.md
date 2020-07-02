---
title: Aufbewahren, Löschen und Zerstören von Daten in Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
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
f1.keywords:
- NOCSH
description: Eine Übersicht über Microsoft-Richtlinien für Microsoft 365 bezüglich Datenaufbewahrung, Löschung und Vernichtung.
ms.openlocfilehash: 256d1e5236d9c9050517b492db00cd26a602be8d
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998429"
---
# <a name="data-retention-deletion-and-destruction-in-microsoft-365"></a>Aufbewahren, Löschen und Zerstören von Daten in Microsoft 365

Microsoft verfügt über eine Richtlinie zur Datenverarbeitung für Microsoft 365, die angibt, wie lange Kundendaten nach dem Löschen aufbewahrt werden. Es gibt im Allgemeinen zwei Szenarien, in denen Kundendaten gelöscht werden:

- **Aktive Löschung**: der Mandant verfügt über ein aktives Abonnement, und ein Benutzer oder Administrator löscht Daten, oder Administratoren löschen einen Benutzer.
- **Passive Löschung**: das Mandanten Abonnement wird beendet.

## <a name="data-retention"></a>Datenaufbewahrung

In der folgenden Tabelle sind die maximalen Daten Aufbewahrungs Intervalle nach Datenkategorie und Klassifizierung für jedes dieser Lösch Szenarien dargestellt:

| Datenkategorie | Datenklassifikation | Beschreibung | Beispiele | Aufbewahrungszeitraum |
|-----------------|-----------------|-----------------|----------------------------------|-------------------------------|
| Kundendaten | Kunden Inhalte| Inhalte, die von Administratoren und Benutzern direkt bereitgestellt/erstellt wurden <br><br> Enthält alle Text-, Sound-, Video-, Bilddateien und Software, die in Microsoft-Rechenzentren erstellt und gespeichert werden, wenn die Dienste in Microsoft 365 verwendet werden. | Beispiele für die am häufigsten verwendeten Microsoft 365-Anwendungen, mit denen Benutzerdaten erstellen können, sind Word, Excel, PowerPoint, Outlook und OneNote. <br><br> Kunden Inhalte enthalten auch kundeneigene/bereitgestellte Geheimnisse (Kennwörter, Zertifikate, Verschlüsselungsschlüssel, Speicherschlüssel) | **Aktives Lösch Szenario:** höchstens 30 Tage <br><br> **Szenario für passive Löschung:** höchstens 180 Tage |
| Kundendaten | Identifizierbare Informationen für Endbenutzer (EUII) | Daten, mit denen der Benutzer eines Microsoft-Diensts identifiziert oder verwendet werden kann. EUII enthält keine Kunden Inhalte. | Benutzername oder Anzeigename (Domäne \ Benutzername) <br><br> Benutzerprinzipalname (Name@Domain) <br><br>  Benutzerspezifische IP-Adressen | **Aktives Lösch Szenario:** höchstens 180 Tage (nur eine mandantenadministrator Aktion) <br><br> **Szenario für passive Löschung:** höchstens 180 Tage |
| Persönliche Daten <br> (Daten sind nicht in Kundendaten enthalten) | Pseudonyme Bezeichner für Endbenutzer (EUPI) | Ein von Microsoft erstellter Bezeichner, der mit dem Benutzer eines Microsoft-Diensts verbunden ist. In Kombination mit anderen Informationen, beispielsweise einer Zuordnungstabelle, identifiziert EUPI den Endbenutzer <br><br> EUPI enthält keine vom Kunden hochgeladenen oder erstellten Informationen. | Benutzer-GUIDs, PUIDs oder SIDs <br><br> Sitzungs-IDs | **Aktives Lösch Szenario:** höchstens 30 Tage <br><br> **Szenario für passive Löschung:** höchstens 180 Tage |

## <a name="subscription-retention"></a>Abonnement Aufbewahrung

Im Ausdruck eines aktiven Abonnements kann ein Abonnent auf Kundendaten zugreifen, diese extrahieren oder löschen, die in Microsoft 365 gespeichert sind. Wenn ein kostenpflichtiges Abonnement endet oder beendet wird, behält Microsoft die in Microsoft 365 gespeicherten Kundendaten in einem Konto mit begrenzter Funktion für 90 Tage bei, damit der Abonnent die Daten extrahieren kann. Nachdem der Aufbewahrungszeitraum von 90 Tagen abgelaufen ist, deaktiviert Microsoft das Konto und löscht die Kundendaten. Microsoft deaktiviert nicht mehr als 180 Tage nach Ablauf oder Beendigung eines Abonnements für Microsoft 365 das Konto und löscht alle Kundendaten aus dem Konto. Sobald die maximale Beibehaltungsdauer für alle Daten verstrichen ist, werden die Daten kommerziell nicht wiederherstellbar gemacht.

Für eine ﻿kostenlose Testversion wechselt Ihr Konto in den meisten Ländern und Regionen in den Kulanz Status für 30 Tage. Innerhalb dieser Nachfrist können Sie Microsoft 365 kaufen. Wenn Sie sich entscheiden, Microsoft 365 nicht zu kaufen, können Sie entweder Ihre Testversion kündigen oder die Nachfrist ablaufen und Ihre Testkontoinformationen und -daten löschen lassen.

## <a name="expedited-deletion"></a>Beschleunigtes löschen

Für jedes Abonnement kann ein Abonnent den Microsoft-Support kontaktieren und eine beschleunigte Abonnement-deprovisionierung anfordern. In diesem Prozess werden alle Benutzerdaten drei Tage nach dem Eingeben des von Microsoft bereitgestellten Sperrcodes durch den Administrator gelöscht. Dies umfasst Daten in SharePoint Online und Exchange Online unterhalten oder in inaktiven Postfächern gespeichert.

Weitere Informationen zur beschleunigten Deaktivierung finden Sie unter [kündigen Ihres Abonnements](https://docs.microsoft.com/microsoft-365/commerce/subscriptions/cancel-your-subscription).

## <a name="related-links"></a>Links zu verwandten Themen

- [Zerstörung von Daten](office-365-data-destruction.md)
- [Unveränderbarkeit in Office 365](office-365-data-immutability.md)
- [Löschen von Exchange Online-Daten](office-365-exchange-online-data-deletion.md)
- [Löschen von SharePoint Online-Daten](office-365-sharepoint-online-data-deletion.md)
- [Löschen von Skype for Business-Daten](office-365-skype-data-deletion.md)