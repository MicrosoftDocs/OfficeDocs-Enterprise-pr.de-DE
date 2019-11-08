---
title: Überwachung und Berichterstellung in Microsoft Cloud Services
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
- M365-analytics
description: Eine Übersicht über die Überwachungs-und Berichtsfunktionen in Office 365, Microsoft 365 und Service Assurance.
ms.openlocfilehash: 545c1224a5c7fc181028be555b14deeff6048ca9
ms.sourcegitcommit: 9eb68633728cc78e9906dab222edbf9977b17e21
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "38035635"
---
# <a name="auditing-and-reporting-in-microsoft-cloud-services"></a>Überwachung und Berichterstellung in Microsoft Cloud Services

## <a name="introduction"></a>Einführung

Microsoft Cloud Services umfassen mehrere Überwachungs-und Berichtsfunktionen, die Sie zum Nachverfolgen von Benutzer-und Verwaltungsaktivitäten innerhalb Ihres Mandanten verwenden können, Beispiele umfassen Änderungen an Exchange Online und SharePoint Online Mandanten Konfigurationseinstellungen sowie von Benutzern vorgenommene Änderungen an Dokumenten und anderen Elementen. Sie können Überwachungsinformationen und Berichte, die in Microsoft-Cloud-Diensten verfügbar sind, verwenden, um die Benutzerfreundlichkeit effektiver zu verwalten, Risiken zu minimieren und Compliance-Verpflichtungen zu erfüllen.

## <a name="security--compliance-centers"></a>Sicherheits #a0 Compliance Center

Das [Office 365 Security #a0 Compliance Center](https://protection.office.com), das [Microsoft 365 Security Center](https://security.microsoft.com)und das [Microsoft 365 Compliance Center](https://compliance.microsoft.com) sind One-Stop-Portale zum Schutz von Daten in Ihrer Organisation und umfassen viele Überwachungs-und Berichtsfunktionen. Diese Center unterstützen Sie bei Ihren Datenschutz-oder Compliance-Anforderungen sowie bei der Überwachung von Benutzer-und Administratoraktivitäten. Sie können auf diese Center über Ihr Abonnement-Administratorkonto zugreifen.

Diese Zentren umfassen Navigationsbereiche für den Zugriff auf mehrere Features:

- **Warnungen:** Ermöglicht es Ihnen, Warnungen zu verwalten, sicherheitsbezogene Warnungen anzuzeigen und erweiterte Warnungen mit [Office 365 Cloud-App-Sicherheit](https://docs.microsoft.com/cloud-app-security/what-is-cloud-app-security)zu verwalten.
- **Berechtigungen:** Ermöglicht Ihnen das [Zuweisen von Berechtigungen](https://support.office.com/article/Give-users-access-to-the-Office-365-Security-Compliance-Center-2cfce2c8-20c5-47f9-afc4-24b059c1bd76) wie Compliance-Administrator, eDiscovery-Manager und andere Personen in Ihrer Organisation, damit diese Aufgaben in diesen Zentren ausführen können. Sie weisen den meisten Features in jedem Center Berechtigungen zu, andere Berechtigungen müssen jedoch über das Exchange Admin Center und das SharePoint Admin Center konfiguriert werden.
- **Threat Management:** Ermöglicht Ihnen das Erstellen und Anwenden von Geräteverwaltungsrichtlinien mit [Office 365 Verwaltung mobiler Geräte](https://support.office.com/article/Overview-of-Mobile-Device-Management-for-Office-365-faa7d8e5-645d-4d59-839c-c8d4c1869e4a), das Einrichten von [Datenverlust Verhinderung](https://support.office.com/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e) (DLP)-Richtlinien für Ihre Organisation, das Konfigurieren von e-Mail-Filterung, Antischadsoftware, DomainKeys Identified Mail (DKIM), sichere Anlagen, sichere Links und OAuth-apps.
- **Datensteuerung:** Ermöglicht Ihnen das [Importieren von e-Mail-oder SharePoint-Daten aus anderen Systemen in Office 365](https://support.office.com/article/Import-PST-files-or-SharePoint-data-to-Office-365-ba688e0a-0fcb-4bd7-8e57-2b669564ea84), [Konfigurieren von archivpostfächern](https://support.office.com/article/Enable-archive-mailboxes-in-the-Office-365-Security-Compliance-Center-268a109e-7843-405b-bb3d-b9393b2342ce)und Festlegen von [Aufbewahrungsrichtlinien](https://docs.microsoft.com/microsoft-365/compliance/retention-policies) für e-Mails und andere Inhalte in Ihrer Organisation.
- **Suche #a0 Untersuchung:** Bietet [Inhaltssuche](https://support.office.com/article/Run-a-Content-Search-in-the-Office-365-Security-Compliance-Center-61852fd9-fe8a-4880-a339-cb19ed3bff4a), [Überwachungsprotokoll](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c), Quarantäne und [eDiscovery Case Management](https://support.office.com/article/Manage-eDiscovery-cases-in-the-Office-365-Security-Compliance-Center-edea80d6-20a7-40fb-b8c4-5e8c8395f6da) -Tools, um schnell in Aktivitäten in Exchange Online Postfächern, Gruppen und öffentlichen Ordnern, SharePoint Online und OneDrive für Unternehmen zu bohren.
- **Berichte:** Ermöglicht den schnellen Zugriff auf [Berichte](https://support.office.com/article/Reports-in-the-Office-365-Security-Compliance-Center-7acd33ce-1ec8-49fb-b625-43bac7b58c5a) für SharePoint Online, OneDrive für Unternehmen, Exchange Online und Azure AD.
- **Dienst Assurance:** Enthält Informationen darüber, wie Microsoft die Sicherheit, den Datenschutz und die Einhaltung globaler Standards für Office 365, Azure, Microsoft Dynamics CRM Online, Microsoft InTune und andere Cloud-Dienste aufrecht erhält. Enthält auch Zugriff auf Drittanbieter-ISO-, SOC-und andere Überwachungsberichte sowie überprüfte Steuerelemente, die Details zu den verschiedenen Steuerelementen bereitstellen, die von Drittanbieter-Prüfern von Office 365 getestet und überprüft wurden.

## <a name="service-assurance"></a>Dienst Assurance

Viele Organisationen in regulierten Branchen unterliegen umfassenden Compliance-Anforderungen. Um eigene Risikobewertungen durchführen zu können, benötigen Kunden häufig ausführliche Informationen dazu, wie Office 365 die Sicherheit und den Datenschutz Ihrer Daten gewährleistet. Microsoft setzt sich für die Sicherheit und den Datenschutz von Kundendaten in seinen Cloud-Diensten und für die Erzielung von Kunden Vertrauen ein, indem es eine transparente Ansicht seiner Vorgänge und einen einfachen Zugriff auf unabhängige Konformitätsberichte und-Bewertungen bereitstellt.

Service Assurance bietet Transparenz der Vorgänge und Informationen darüber, wie Microsoft die Sicherheit, den Datenschutz und die Compliance von Kundendaten in Office 365 aufrecht erhält. Sie umfasst Überwachungsberichte von Drittanbietern zusammen mit einer Bibliothek mit Whitepapers, FAQs und anderen Materialien zu Office 365 Themen wie Datenverschlüsselung, Datenausfall Sicherheit, Sicherheitsproblemverwaltung und vielem mehr. Kunden können diese Informationen verwenden, um Ihre eigenen regulatorischen Risikobewertungen durchzuführen. Compliance Officer können der Rolle "Dienst Assurance-Benutzer" zuweisen, damit Benutzer Zugriff auf die Dienst Assurance erhalten. Der mandantenadministrator kann auch externen Benutzern wie unabhängigen Prüfern Zugriff auf Informationen im Service Assurance-Dashboard über das [Microsoft Cloud Service Trust Portal](https://aka.ms/STP) (STP) bereitstellen. Ausführliche Informationen zum Zugriff auf STP finden Sie unter [Erste Schritte mit dem Dienst Vertrauensstellungs Portal für Office 365 für Unternehmen-, Azure-und Dynamics CRM Online-Abonnements](https://aka.ms/STPHelp).

## <a name="onedrive-for-business-admin-center"></a>OneDrive für Unternehmen Admin Center

Mit dem Microsoft OneDrive Admin Center können Sie die OneDrive für Unternehmen Einstellungen Ihrer Organisation schnell und einfach an einer zentralen Stelle verwalten. Um das OneDrive Admin Center verwenden zu können, ist der Zugriff auf onedrive.com erforderlich. Sie müssen auch ein globaler Administrator für Ihre Organisation oder ein benutzerdefinierter Administrator mit der SharePoint-Administratorrolle sein. Greifen Sie auf das OneDrive für Unternehmen admin [https://admin.onedrive.com](https://admin.onedrive.com/)Center unter.

Zu den wichtigsten Features gehört ein Compliance-Bereich, der Administratoren Links zum entsprechenden Management Center für wichtige Szenarien wie das Durchsuchen des Überwachungsprotokolls, das Arbeiten mit DLP, Aufbewahrung, eDiscovery und Warnungen bereitstellt.

## <a name="related-links"></a>Links zu verwandten Themen

- [eDiscovery und Suchfunktionen](office-365-ediscovery-and-search-features.md)
- [Berichtsfeatures in Office 365](office-365-reporting-features.md)
- [Office 365-Verwaltungsaktivitäts-API](office-365-management-activity-api.md)
- [Office 365-Postfachmigrationen](office-365-mailbox-migrations.md)
- [Interne Protokollierung für Office 365 Engineering](office-365-internal-logging.md)