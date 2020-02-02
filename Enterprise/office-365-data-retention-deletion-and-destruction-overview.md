---
title: Aufbewahren, Löschen und Zerstören von Daten in Office 365
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
description: Eine Übersicht über die Microsoft-Richtlinien für Office 365 zur Aufbewahrung, Löschung und Vernichtung von Daten.
ms.openlocfilehash: 93093e3688d0f8ae399a4e021deaaf4b7ed5cecf
ms.sourcegitcommit: 4f465f690c6563cfa9f6029d3e7e9e3cace96671
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41658332"
---
# <a name="data-retention-deletion-and-destruction-in-office-365"></a>Aufbewahren, Löschen und Zerstören von Daten in Office 365

Microsoft verfügt über eine Standard Richtlinie für die Datenverarbeitung für Office 365, die angibt, wie lange Kundendaten nach dem Löschen aufbewahrt werden. Es gibt im Allgemeinen zwei Szenarien, in denen Kundendaten gelöscht werden:

- **Aktive Löschung**: der Mandant verfügt über ein aktives Abonnement, und ein Benutzer oder Administrator löscht Daten, oder Administratoren löschen einen Benutzer.
- **Passive Löschung**: das Mandanten Abonnement wird beendet.

## <a name="data-retention"></a>Datenaufbewahrung

In der folgenden Tabelle sind die maximalen Daten Aufbewahrungs Intervalle nach Datenkategorie und Klassifizierung für jedes dieser Lösch Szenarien dargestellt:

| Datenkategorie | Datenklassifikation | Beschreibung | Beispiele | Aufbewahrungszeitraum |
|-----------------|-----------------|-----------------|----------------------------------|-------------------------------|
| Kundendaten | Kunden Inhalte| Inhalte, die von Administratoren und Benutzern direkt bereitgestellt/erstellt wurden <br><br> Enthält alle Text-, Sound-, Video-, Bilddateien und Software, die in Microsoft-Rechenzentren erstellt und gespeichert werden, wenn die Dienste in Office 365 verwendet werden. | Beispiele für die am häufigsten verwendeten Office 365 Anwendungen, die Benutzern das Erstellen von Daten ermöglichen, sind Word, Excel, PowerPoint, Outlook und OneNote. <br><br> Kunden Inhalte enthalten auch kundeneigene/bereitgestellte Geheimnisse (Kennwörter, Zertifikate, Verschlüsselungsschlüssel, Speicherschlüssel) | **Aktives Lösch Szenario:** höchstens 30 Tage <br><br> **Szenario für passive Löschung:** höchstens 180 Tage |
| Kundendaten | Identifizierbare Informationen für Endbenutzer (EUII) | Daten, mit denen der Benutzer eines Microsoft-Diensts identifiziert oder verwendet werden kann. EUII enthält keine Kunden Inhalte. | Benutzername oder Anzeigename (Domäne \ Benutzername) <br><br> Benutzerprinzipalname (Name@Domain) <br><br>  Benutzerspezifische IP-Adressen | **Aktives Lösch Szenario:** höchstens 180 Tage (nur eine mandantenadministrator Aktion) <br><br> **Szenario für passive Löschung:** höchstens 180 Tage |
| Persönliche Daten <br> (Daten sind nicht in Kundendaten enthalten) | Pseudonyme Bezeichner für Endbenutzer (EUPI) | Ein von Microsoft erstellter Bezeichner, der mit dem Benutzer eines Microsoft-Diensts verbunden ist. In Kombination mit anderen Informationen, beispielsweise einer Zuordnungstabelle, identifiziert EUPI den Endbenutzer <br><br> EUPI enthält keine vom Kunden hochgeladenen oder erstellten Informationen. | Benutzer-GUIDs, PUIDs oder SIDs <br><br> Sitzungs-IDs | **Aktives Lösch Szenario:** höchstens 30 Tage <br><br> **Szenario für passive Löschung:** höchstens 180 Tage |

## <a name="subscription-retention"></a>Abonnement Aufbewahrung

In der Laufzeit eines aktiven Abonnements kann ein Abonnent auf Kundendaten zugreifen, diese extrahieren oder löschen, die in Office 365 gespeichert sind. Wenn ein kostenpflichtiges Abonnement endet oder beendet wird, behält Microsoft die in Office 365 gespeicherten Kundendaten in einem Konto mit begrenzter Funktion für 90 Tage, damit der Abonnent die Daten extrahieren kann. Nachdem der Aufbewahrungszeitraum von 90 Tagen abgelaufen ist, deaktiviert Microsoft das Konto und löscht die Kundendaten. Nicht länger als 180 Tage nach Ablauf oder Beendigung eines Abonnements für Office 365 deaktiviert Microsoft das Konto und löscht alle Kundendaten aus dem Konto. Sobald die maximale Beibehaltungsdauer für alle Daten verstrichen ist, werden die Daten kommerziell nicht wiederherstellbar gemacht.

Für eine ﻿kostenlose Testversion wechselt Ihr Konto in den meisten Ländern und Regionen in den Kulanz Status für 30 Tage. Während dieser Kulanzzeit können Sie Office 365 erwerben. Wenn Sie Office 365 nicht kaufen möchten, können Sie entweder Ihre Testversion abbrechen oder die Kulanzfrist ablaufen lassen, und Ihre Test Kontoinformationen und-Daten werden gelöscht.

## <a name="expedited-deletion"></a>Beschleunigtes löschen

Für jedes Abonnement kann ein Abonnent den Microsoft-Support kontaktieren und eine beschleunigte Abonnement-deprovisionierung anfordern. In diesem Prozess werden alle Benutzerdaten drei Tage nach dem Eingeben des von Microsoft bereitgestellten Sperrcodes durch den Administrator gelöscht. Dies umfasst Daten in SharePoint Online und Exchange Online unterhalten oder in inaktiven Postfächern gespeichert.

Weitere Informationen zur beschleunigten Deaktivierung finden Sie unter [Cancel Office 365](https://docs.microsoft.com/office365/admin/subscriptions-and-billing/cancel-your-subscription).

## <a name="related-links"></a>Links zu verwandten Themen

- [Zerstörung von Daten](office-365-data-destruction.md)
- [Unveränderbarkeit in Office 365](office-365-data-immutability.md)
- [Löschen von Exchange Online-Daten](office-365-exchange-online-data-deletion.md)
- [Löschen von SharePoint Online-Daten](office-365-sharepoint-online-data-deletion.md)
- [Löschen von Skype for Business-Daten](office-365-skype-data-deletion.md)