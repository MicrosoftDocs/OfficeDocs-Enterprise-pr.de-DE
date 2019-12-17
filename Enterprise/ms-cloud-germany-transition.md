---
title: Migration von Microsoft Cloud Germany (Microsoft Cloud Deutschland) zu Office 365-Diensten in den neuen deutschen Rechenzentrumsregionen
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/09/2019
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: 'Zusammenfassung: Die Migration von Microsoft Cloud Germany (Microsoft Cloud Deutschland) zu Office 365-Diensten in den neuen deutschen Rechenzentrumsregionen verstehen.'
ms.openlocfilehash: 95edbeeb79549957ff49afa8b8a96160945b0f20
ms.sourcegitcommit: 77b8fd702d3a1010d3906d4024d272ad2097f54f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2019
ms.locfileid: "39962442"
---
# <a name="migration-from-microsoft-cloud-germany-microsoft-cloud-deutschland-to-office-365-services-in-the-new-german-datacenter-regions"></a>Migration von Microsoft Cloud Germany (Microsoft Cloud Deutschland) zu Office 365-Diensten in den neuen deutschen Rechenzentrumsregionen


>[!Note]
>Dieser Artikel gilt nur für berechtigte Kunden von Microsoft Cloud Germany/Deutschland.
>

## <a name="cloud-service-offerings-in-germany"></a>Cloud-Serviceangebote in Deutschland

Im August 2018 haben wir unsere Absicht angekündigt, die gesamte Microsoft-Cloud – Azure, Office 365, Dynamics 365 und Power Platform – aus neuen Cloud-Regionen in Deutschland bereitzustellen, um die digitale Transformation unserer Kunden besser zu ermöglichen. Wir haben im August 2019 angekündigt, dass wir nun die neuen Cloud-Regionen in Deutschland öffnen. Wir haben die Verfügbarkeit von Azure im August angekündigt und Office 365 wurde im Dezember verfügbar.  Dynamics 365 und Power Platform werden voraussichtlich im ersten Quartal 2020 verfügbar sein.  

Die neuen Regionen sind so konzipiert, dass sie den sich ständig ändernden Anforderungen der deutschen Kunden mit ihrer erweiterter Flexibilität, den neuesten intelligenten Cloud-Diensten und der unbegrenzten Konnektivität zu unserem weltweiten Cloud-Netzwerk sowie der Datenhaltung in Deutschland gerecht werden.

## <a name="moving-to-the-new-german-regions"></a>Umstieg auf die neuen deutschen Regionen

Die bestehenden Kunden von Microsoft Cloud Germany (Microsoft Cloud Deutschland) können nun mit der Migration ihrer Office 365, Dynamics 365 Customer Engagement und Power Platform BI beginnen.  Der erste Schritt besteht darin, [sich für die von Microsoft geleiteten Migration in unsere neuen deutschen Rechenzentrumsregionen anzumelden](https://aka.ms/office365germanymoveoptin).

Die Migrationen für Organisationen, die sich für den von Microsoft geleiteten Ansatz anmelden, werden voraussichtlich in 2020 durchgeführt. Als Ergebnis der Migration werden die wichtigsten Kundendaten und -abonnements in die neuen deutschen Regionen verschoben. 

Die folgenden Dienste werden als Teil des von Microsoft geleiteten Ansatzes migriert:

- Azure Active Directory
- Exchange Online
- Exchange Online Protection
- SharePoint Online
- OneDrive for Business
- Skype for Business Online

Während der Migration von Microsoft Cloud Deutschland in die deutschen Rechenzentrumsregionen werden bestehende Skype for Business Online Kunden auf Microsoft Teams umgestellt. Weitere Informationen finden Sie unter [Erste Schritte mit dem Upgrade von Microsoft Teams](https://aka.ms/SkypeToTeams-Home).

- Office 365-Gruppen
- Dynamics 365 / Power Platform

Die Voraussetzungen und Auswirkungen der Migration für diese Dienste sind im Artikel [Dynamics 365 Customer Engagement](https://aka.ms/D365ceOptIn) beschrieben.

## <a name="how-to-prepare-for-migration-to-office-365-services-in-the-new-german-datacenter-regions"></a>Wie Sie sich auf die Migration auf Office 365-Dienste in den neuen deutschen Rechenzentrumsregionen vorbereiten können

Der erste Schritt besteht darin, Microsoft zu benachrichtigen, damit wir Ihre Berechtigung zum Migrieren Ihres Abonnements und der Daten aus der Microsoft-Cloud Deutschland auf Office 365-Dienste in den neuen deutschen Rechenzentrumsregionen haben.  Anweisungen hierzu finden Sie im [Abonnementsprozess](ms-cloud-germany-migration-opt-in.md).

- Alle migrierenden Kunden müssen die Konnektivität zum weltweiten [Office 365-URLs und -IP-Adressen](urls-and-ip-address-ranges.md), die die neuen deutschen Rechenzentrumsregionen umfassen, überprüfen.
- Überprüfen Sie die Beschreibung der Office 365-Plattformdienste, um zu verstehen, welche Funktionen und Dienste nach der Fertigstellung in der Region für Ihre Organisation verfügbar werden. 
- Im Rahmen der Migration werden bezahlte Abonnements überführt.  Testabonnements können nicht migriert werden.

Mandantenmigrationen werden als Back-End-Dienste ausgeführt, wobei nur minimale Kundeninteraktionen erforderlich sind.  Alle weiteren vom Kunden geleiteten Aufgaben und der allgemeine Stand der Migration werden während des Migrationsprozesses über das Message Center mitgeteilt.  Zu den Aufgaben zählen beispielsweise durch Kunden verwaltete DNS-Updates oder die Neukonfiguration des Hybrid-Setups für Kunden von Exchange-Hybridlösungen.

## <a name="customer-experience-during-the-migration-to-office-365-services-in-the-new-german-datacenter-regions"></a>Die Kundenerfahrung während der Migration auf Office 365-Dienste in den neuen deutschen Rechenzentrumsregionen

Mandantenmigrationen sind so angelegt, dass sie nur minimale Auswirkungen auf Endkunden und Administratoren haben.  Allerdings gibt es Überlegungen für jede Workload.  

### <a name="azure-active-directory"></a>Azure Active Directory

Office-/ Dynamics-Abonnements von Microsoft Cloud Deutschland werden mit der Azure Active Directory-Verlagerung (Azure AD) in die Region Deutschland umgestellt. Die Organisation wird dann aktualisiert, um die neuen weltweiten Dienstabonnements zu widerspiegeln. Während des kurzen Übertragungsprozesses für das Abonnement werden Änderungen an Abonnements blockiert.

### <a name="exchange-online"></a>Exchange Online

Exchange Online Hybrid-Kunden müssen den Hybrid-Konfigurationsassistenten erneut ausführen, um die Konfiguration vor Ort gegen Microsoft Cloud Germany vor der Umstellung zu aktualisieren und die HCW nach der Bereinigung gegen den weltweiten Service erneut auszuführen. Für Kunden mit benutzerdefinierten Domänen werden ggf. weitere DNS-Updates erforderlich sein.

Postfächer werden als Back-End-Prozess migriert. Benutzer in Ihrer Organisation befinden sich während des Übergangs entweder in Microsoft Cloud Deutschland oder in der Region Deutschland und sind Teil derselben Exchange-Organisation (GAL).

### <a name="exchange-online-protection"></a>Exchange Online Protection

Die Backend-Funktionen von Exchange Online Protection werden in die neue Region Deutschland kopiert.

### <a name="sharepoint-online"></a>SharePoint Online

Nach Abschluss der SharePoint Online-Migration in die Region Deutschland werden Datenindizes neu erstellt. Funktionen, die von Suchindizes abhängig sind, können betroffen sein, bis die Neuindizierung abgeschlossen ist.

Vorhandene SharePoint.de-URLs werden für übertragene Organisationen beibehalten.

### <a name="onedrive-for-business"></a>OneDrive for Business

Nach Abschluss der OneDrive for Business-Migration in die Region Deutschland werden Datenindizes neu erstellt. Funktionen, die von Suchindizes abhängig sind, können betroffen sein, bis die Neuindizierung abgeschlossen ist.

### <a name="skype-for-business-online"></a>Skype for Business Online

Bestehende Skype für Business Online Kunden werden auf Microsoft Teams umgestellt. Weitere Informationen finden Sie unter [https://aka.ms/SkypeToTeams-Home](https://aka.ms/SkypeToTeams-Home).


## <a name="key-differences-between-microsoft-cloud-germany-microsoft-cloud-deutschland-and-office-365-services-in-the-new-german-datacenter-regions"></a>Wichtigste Unterschiede zwischen Microsoft Cloud Germany (Microsoft Cloud Deutschland) und Office 365-Diensten in den neuen deutschen Rechenzentrumsregionen


|| Microsoft Cloud Deutschland | Office 365-Dienste in den neuen deutschen Rechenzentrumsregionen |
|:-------|:-----|:-----|
| Microsoft 365-Dienste, die mit nur einem Office 365-Mandanten als Abonnement verfügbar sind | 15 Dienste (siehe Bezug) | 29 Dienste (siehe Bezug) |
| Neue Features | Es sind keine neuen Features verfügbar. | Neue Funktionen werden in Übereinstimmung mit den globalen Office 365-Diensten bereitgestellt. |
| Datentreuhänder | Ja | Nein |
| Mandantenübergreifende Zusammenarbeit mit Office 365-Mandanten weltweit | Nein | Ja |
| Kundendatenhaltung | Kundendaten werden nur in deutschen Rechenzentren gespeichert. | Die folgenden Kundendaten werden von Microsoft ausschließlich in Deutschland gespeichert: Exchange Online-Postfachinhalte (E-Mail-Text, Kalendereinträge und der Inhalt von E-Mail-Anlagen), SharePoint Online-Websiteinhalte und die Dateien, die auf dieser Website gespeichert sind, und Dateien, die in OneDrive for Business hochgeladen wurden. |
| Geltende Nutzungsbedingungen | [Onlinedienstbedingungen](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=46) mit [Zusatz](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=64) | [Onlinedienstbedingungen](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=46) |
||||

## <a name="frequently-asked-questions"></a>Häufig gestellte Fragen

### <a name="is-migration-required"></a>Ist die Migration erforderlich?

Microsoft bietet eine Mandantenmigration für Office 365 von Microsoft Cloud Deutschland zu Office 365-Diensten in den neuen deutschen Rechenzentrumsregionen ohne Aufpreis.  Wir empfehlen Ihnen dringend, sich für die Migration zu den neuen deutschen Rechenzentrumsregionen anzumelden, aber wir werden weiterhin die erforderlichen Sicherheitsupdates für die Region „Microsoft Cloud Deutschland“ bereitstellen.  

Office 365-Dienste in den neuen deutschen Rechenzentrumsregionen bieten zusätzliche Vorteile:

- Sie bieten marktgerechte Preise für [Azure](https://azure.microsoft.com/pricing/calculator/), [Office 365](https://www.microsoft.com/microsoft-365/business/compare-more-office-365-for-business-plans), [Dynamics 365 Customer Engagement](https://dynamics.microsoft.com/pricing/)und [Power BI](https://powerbi.microsoft.com/pricing/). 
- Sie sind mit einem globalen Microsoft-Netzwerk verbunden und bieten hunderte von Netzwerk-Edge-Websites, Peering-Standorten und Übergabepunkte, um überall auf der Welt eine sichere Benutzererfahrung zu bieten. 
- Sie helfen Ihnen, die Anforderungen an die lokale Kundendatenverwaltung innerhalb Deutschlands zu erfüllen. 
- Sie bieten unser umfassendes globales Cloud-Angebot, einschließlich der neuesten Version unserer Dienste und neuer Funktionen wie Microsoft Teams und Multi-Geo in Office 365. Sie vergleichen Produkte nach Region für [Azure](https://azure.microsoft.com/global-infrastructure/services/?products=all&regions=germany-non-regional,germany-central,germany-north,germany-northeast,germany-west-central), [Office 365](https://products.office.com/de-DE/where-is-your-data-located) und [Dynamics 365](https://docs.microsoft.com/dynamics365/get-started/availability).
- Sie bieten die vollständige Funktionalität, Sicherheit auf Unternehmensniveau und umfassende Funktionen, die Kunden bei der Einhaltung behördlicher Vorschriften unterstützen. 
- Sie sind im Rahmen vorhandener Verträge für Onlinedienstleistungen verfügbar.

#### <a name="what-is-the-service-availability-between-the-different-office-365-cloud-service-offerings"></a>Wie hoch ist die Dienstverfügbarkeit der verschiedenen Office 365-Clouddienstangebote?

Die folgenden 15 Dienste sind im Clouddienstangebot von Microsoft Cloud Germany (Microsoft Cloud Deutschland) verfügbar.  Microsoft Cloud Germany werden keine neuen Dienste hinzufügen.

1. Exchange Online
2. Kunden-Lockbox (Exchange Online)
3. Gruppen (moderne Gruppen)
4. Delve-Profil
5. Exchange Online Protection
6. Advanced Threat Protection, ATP
7. Advanced eDiscovery
8. Advanced Data Governance
9. SharePoint Online
10. Kunden-Lockbox (SharePoint Online)
11. OneDrive for Business
12. Skype for Business
13. Word Online, Excel Online, PowerPoint, OneNote, Visio Online
14. Office 365 ProPlus
15. Outlook Mobile

Derzeit sind 29 Dienste als Bestandteil von Office 365-Diensten in den neuen deutschen Rechenzentrumsregionen verfügbar.  In Übereinstimmung mit den globalen Office 365-Diensten werden fortlaufend neue Features und Dienste bereitgestellt.

1. Exchange Online
2. Kunden-Lockbox (Exchange Online)
3. Gruppen (moderne Gruppen)
4. Delve-Profil
5. MyAnalytics
6. Workplace Analytics
7. Exchange Online Protection
8. Advanced Threat Protection, ATP
9. Advanced eDiscovery
10. Advanced Security Management
11. Verwaltung von Informationsrechten
12. Advanced Data Governance
13. SharePoint Online
14. Kunden-Lockbox (SharePoint Online)
15. OneDrive for Business
16. Microsoft Stream
17. Skype for Business (während der Migration erfolgt ein Umstieg zu Microsoft Teams)
18. Cloud PBX
19. PSTN-Konferenzen
20. PSTN-Anrufe
21. Microsoft Teams
22. Administrator-Berichte/ Verwendungsberichte
23. Word Online, Excel Online, PowerPoint, OneNote und Visio Online
24. Planner
25. Sway
26. Office 365 ProPlus
27. Outlook Mobile
28. EMS E3 (Azure Active Directory Premium P1 + Intune + Rights Management Service)
29. Yammer Online

### <a name="when-will-migration-happen"></a>Wann wird die Migration durchgeführt?

#### <a name="azure"></a>Azure 

Sie können [die Migration von](https://docs.microsoft.com/azure/germany/germany-migration-main) Azure-Ressourcen zu einer anderen Region bereits starten. Wenn Sie über Azure mit Office 365, Dynamics 365 und/oder Power BI verfügen, führen Sie die folgenden Schritte aus.

#### <a name="office-365"></a>Office 365

[Melden Sie sich an](https://aka.ms/office365germanymoveoptin) für die von Microsoft geleiteten Migration noch heute. Wenn wir bereit sind, Ihre Migration zu starten, werden wir Sie über das [Message Center](https://docs.microsoft.com/office365/admin/manage/message-center?view=o365-worldwide) im Microsoft 365 Admin Center informieren.

#### <a name="dynamics-365-and-power-bi"></a>Dynamics 365 und Power BI

Melden Sie sich für die von Microsoft geleiteten Migration für [Dynamics 365 Customer Engagement](https://aka.ms/D365ceOptIn) und [Power BI](https://aka.ms/pbioptin) noch heute an. Wenn wir bereit sind, Ihre Migration zu starten, werden wir Sie über das [Message Center](https://docs.microsoft.com/office365/admin/manage/message-center?view=o365-worldwide) im Microsoft 365 Admin Center informieren.

### <a name="will-the-price-change-for-the-office-services-that-i-use"></a>Werden die Preise für die von mir verwendeten Office-Dienste geändert?

Ja, die Preise in den globalen Microsoft-Cloudbereichen (einschließlich der neuen Rechenzentrumsregionen) sind im Allgemeinen niedriger.

### <a name="how-do-i-get-help-from-microsoft-to-migrate-to-a-new-region-or-answer-support-questions"></a>Wie erhalte ich Hilfe von Microsoft, um zu einer neuen Region zu migrieren, oder Antworten auf meine Support-Fragen?

Wenn Sie Fragen haben, können Sie uns wie folgt oder über Ihren Partner kontaktieren:

- Für Azure können Sie [neue Supportanfragen](https://portal.microsoftazure.de/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/newsupportrequest) im Azure-Portal senden.
- Für Office 365 übermitteln Sie uns Ihre Fragen über den Link „Benötigen Sie Hilfe?“ im [Microsoft 365 Admin Center](https://portal.office.de/).
- Für Dynamics 365 Customer Engagement- und Power BI-Kunden, die auch Office 365 besitzen, senden Sie uns Ihre Fragen über „Benötigen Sie Hilfe?“ im [Microsoft 365 Admin Center](https://portal.office.de/). Die Dynamics 365 Customer Engagement-Supportoptionen befinden sich [hier](https://docs.microsoft.com/dynamics365/get-started/support/). Die Power BI-Supportoptionen befinden sich [hier](https://powerbi.microsoft.com/support/).

## <a name="more-information"></a>Weitere Informationen

- [Hilfe zur Microsoft Cloud Deutschland-Migration Assistance](https://aka.ms/germanymigrateassist)
- [So können Sie sich für die Migration anmelden](https://aka.ms/office365germanymoveoptin)
- [Informationen zum Dynamics 365-Migrationsprogramm](https://aka.ms/D365ceOptIn)
- [Informationen zum Power BI-Migrationsprogramm](https://aka.ms/pbioptin)
- [URLs und IP-Adressbereiche für Office 365](https://aka.ms/o365endpoints)
- [Office 365 Hybrid-Konfigurationsassistent](https://aka.ms/HybridWizard)
- [Erste Schritte mit dem Upgrade von Microsoft Teams](https://aka.ms/SkypeToTeams-Home)