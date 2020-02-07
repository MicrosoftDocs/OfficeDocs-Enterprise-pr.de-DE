---
title: Administrative Zugriffssteuerungen in Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
f1.keywords:
- NOCSH
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: 'Zusammenfassung: eine Übersicht über die administrativen Zugriffssteuerungen von Office 365 und die Datenkategorisierung.'
ms.openlocfilehash: f902b123b26f2c71cb6597f66fc47142e2f2b44c
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844536"
---
# <a name="administrative-access-controls-in-office-365"></a>Administrative Zugriffssteuerungen in Office 365 

Microsoft hat stark in Systeme und Steuerelemente investiert, die die meisten Office 365 Vorgänge automatisieren und den Zugriff auf Kunden Inhalte durch Microsoft absichtlich einschränken. Der Dienst wird von den Menschen verwaltet, und die Software betreibt den Dienst. Dadurch kann Microsoft Office 365 skalieren und die Risiken interner Bedrohungen für Kunden Inhalte verwalten.

Standardmäßig verfügen die Microsoft-Techniker über keine ständigen Administratorrechte und keinen ständigen Zugriff auf Kundeninhalte in Office 365. Ein Microsoft-Techniker kann für einen begrenzten Zeitraum begrenzten, überwachten und gesicherten Zugriff auf die Inhalte eines Kunden haben. Der Zugriff ist nur für Dienstvorgänge erforderlich und nur, wenn er von einem Mitglied von Microsoft Senior Management genehmigt wurde. Für Kunden Lockbox-lizenzierte Kunden bietet der Kunde Zugriffsgenehmigung für die Inhalte an, die auf Office 365 gehostet werden.

Microsoft stellt Onlinedienste bereit, die mehrere Formen der Cloud-Zustellung verwenden:

- **Öffentliche Clouds:** Enthält mehr mandantenversionen von Office 365, Azure und anderen Diensten, die in Nordamerika, Südamerika, Europa, Asien, Australien usw. gehostet werden.
- **Nationale Clouds:** Umfasst alle souveränen und von Drittanbietern betriebenen Clouds außerhalb der Vereinigten Staaten (mit Ausnahme der zuvor erwähnten), wie Office 365 in China (betrieben von 21Vianet) und Office 365 in Deutschland (betrieben von Microsoft, aber unter einem Modell, in dem ein deutscher Daten Treuhänder, die Deutsche Telekom) den Zugriff von Microsoft auf Kundendaten und-Systeme steuert und überwacht, die Kundendaten enthalten.
- **Öffentliche Clouds:** Umfasst Office 365-und Azure-Dienste, die für US-amerikanische Regierungskunden verfügbar sind.

Für die Zwecke dieses Artikels umfassen Office 365 Dienste Folgendes:

- [Exchange Online](https://docs.microsoft.com/Exchange/exchange-online)
- [Exchange Online Protection](https://docs.microsoft.com/Office365/SecurityCompliance/eop/exchange-online-protection-overview)
- [SharePoint Online](https://docs.microsoft.com/sharepoint/sharepoint-online)
- [OneDrive for Business](https://docs.microsoft.com/OneDrive/onedrive)
- [Skype for Business](https://docs.microsoft.com/SkypeForBusiness/skype-for-business-online)
- [Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/Teams-overview)
- [Yammer](https://docs.microsoft.com/yammer/yammer-landing-page)

## <a name="office-365-access-controls"></a>Office 365 von Zugriffssteuerungen

Für Zugriffs Steuerungszwecke kategorisiert Microsoft Office 365 Daten als Kundendaten oder andere Datentypen.

### <a name="customer-data"></a>Kundendaten

Kundendaten sind alle Daten, die von oder im Auftrag eines Kunden bei der Verwendung von Office 365 Diensten bereitgestellt werden. Dies sind Kunden Inhalte, die von Office 365 Benutzern direkt erstellt oder hochgeladen werden, einschließlich:

- E-Mails
- SharePoint Online Inhalt
- Sofortnachrichten
- Kalenderelemente
- Dokumente
- Kontakte
- Endbenutzer-identifizierbare Informationen (EUII) (Daten, die für einen Benutzer eindeutig sind oder die mit einem einzelnen Benutzer verknüpft sind, aber keine Kunden Inhalte enthalten).

### <a name="other-types-of-data"></a>Andere Datentypen

Zu den anderen Datentypen gehören:

- **Kontodaten:** Enthält administrative Daten (Informationen, die von Administratoren bei der Registrierung oder beim Kauf von Diensten bereitgestellt werden) und Zahlungsdaten (Informationen zu Zahlungsinstrumenten wie Kreditkartendetails).
- **Organisatorisch identifizierbare Informationen:** Enthält Daten, die zum Identifizieren eines Mandanten, zur Verwendung und nicht zum Verknüpfen mit einem einzelnen Benutzer oder zum Einschließen in Kunden Inhalte verwendet werden.
- **System Metadaten:** Enthält Dienstprotokolle, die Konfigurationseinstellungen, Systemstatus, Microsoft-IP-Adressen und technische Informationen zu Abonnements und Mandanten enthalten.

Microsoft hat Zugriffssteuerungsmechanismen eingerichtet, um sicherzustellen, dass niemand ungenehmigten Zugriff auf Kundendaten oder Zugriffssteuerungsdaten hat. Zugriffssteuerungsdaten verwalten den Zugriff auf andere Daten oder Funktionen in der Umgebung, einschließlich Zugriff auf Kunden Inhalte oder EUII, Microsoft-Kennwörter, Sicherheitszertifikate und andere Authentifizierungs bezogene Daten. Zugriffssteuerungsmechanismen schützen auch den nicht genehmigten physischen, logischen oder Remotezugriff auf die Office 365 Produktionsumgebung.

Microsoft verwendet drei Kategorien von Zugriffs Steuerelementen für Betriebs Office 365:

- Isolierungs Steuerelemente
- Personalsteuer Elemente
- Technologie Steuerelemente

Wenn diese Steuerelemente kombiniert werden, können Sie böswillige Aktionen in Office 365 verhindern und erkennen. Zusätzlich zu den von Microsoft verwendeten Isolierungs-, Personal-und Technologie Steuerelementen gibt es eine vierte Kategorie von Steuerelementen: die von Kunden implementierten.

Office 365 ermöglicht Ihnen die Verwaltung von Daten auf die gleiche Weise, wie Daten in lokalen Umgebungen verwaltet werden. Die Person, die eine Organisation für Office 365 anmeldet, wird automatisch zu einem globalen Administrator. Der globale Administrator hat Zugriff auf alle Features in Verwaltungs Portalen und kann Folgendes:

- Erstellen oder Bearbeiten von Benutzern
- Zuweisen von Administratorrollen zu anderen Benutzern
- Zurücksetzen von Benutzerkennwörtern
- Verwalten von Benutzerlizenzen
- Verwalten von Domänen
- Genehmigen von Kunden-Lockbox-Anforderungen

Es wird empfohlen, dass jede Organisation mindestens zwei Administratorkonten konfiguriert. Für große Unternehmensorganisationen empfehlen wir spezialisierte Administratorkonten, die unterschiedliche Funktionen bedienen.

Informationen zum Zuweisen von Administratorrollen und-Berechtigungen finden Sie unter [Zuweisen von Administratorrollen in Office 365](https://support.office.com/article/Assigning-admin-roles-in-Office-365-eac4d046-1afd-4f1a-85fc-8219c79e1504) und [Office 365 Administratorrollen](https://support.office.com/article/Permissions-in-Office-365-DA585EEA-F576-4F55-A1E0-87090B6AAA9D).

## <a name="related-links"></a>Links zu verwandten Themen

- [Isolierungs Steuerelemente](office-365-isolation-controls.md)
- [Personalsteuer Elemente](office-365-personnel-controls.md)
- [Technologie Steuerelemente](office-365-technology-controls.md)
- [Überwachung und Überprüfung von Zugriffssteuerungen](office-365-monitoring-and-auditing-access-controls.md)
- [Yammer Enterprise-Zugriffssteuerungen](office-365-yammer-enterprise-access-controls.md)