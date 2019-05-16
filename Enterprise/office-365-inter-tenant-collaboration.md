---
title: Zusammenarbeit zwischen Office 365-Mandanten
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 11/08/2018
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-collaboration
- M365-subscription-management
search.appverid:
- MET150
- MOE150
ms.assetid: eb45fd8b-1d5d-4b0c-9c5a-479dbb176e7d
description: Erfahren Sie, wie Office 365 Collaboration über Mandanten und Organisationen hinweg funktioniert.
ms.openlocfilehash: cedeab08cf6daf3817179bcf770eda6598361e67
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069671"
---
# <a name="office-365-inter-tenant-collaboration"></a>Zusammenarbeit zwischen Office 365-Mandanten

In diesem Artikel werden verschiedene Möglichkeiten zur Zusammenarbeit zwischen zwei Office 365-Mandanten beschrieben. Sie ist für Office 365-Administratoren vorgesehen.
  
Angenommen, zwei Organisationen, Fabrikam und Contoso, haben jeweils einen Office 365 for Business-Mandanten und möchten in mehreren Projekten zusammenarbeiten; Einige davonlaufen für eine begrenzte Zeit, von denen einige fortlaufend sind. Wie können Fabrikam und Contoso ihren Mitarbeitern und Teams die sichere Zusammenarbeit in ihren verschiedenen Office 365-Mandanten ermöglichen? Office 365 bietet in Verbindung mit Azure Active Directory B2B-Zusammenarbeit mehrere Optionen. In diesem Artikel werden verschiedene wichtige Szenarien beschrieben, die Fabrikam und Contoso berücksichtigen können.
  
Die Optionen für die intermandanten Zusammenarbeit von Office 365 umfassen die Verwendung eines zentralen Speicherorts für Dateien und Unterhaltungen, das Freigeben von Kalendern, das Verwenden von Sofortnachrichten, Audio/Video-Anrufe zur Kommunikation und das Sichern des Zugriffs auf Ressourcen und Anwendungen. Verwenden Sie die folgenden Tabellen, um Lösungen auszuwählen und weitere Informationen zu erhalten.
  
## <a name="exchange-online-collaboration-options"></a>Optionen für die Zusammenarbeit in Exchange Online

|**Freigabeziel**|**Verwaltungsaktion**|**Vorgehensweise**|
|:-----|:-----|:-----|
|Kalenderfreigabe für eine andere Office 365-Organisation  <br/> |Administratoren können unterschiedliche Ebenen des Kalenderzugriffs in Exchange Online einrichten, damit Unternehmen mit anderen Unternehmen zusammenarbeiten und Benutzer die Zeitpläne (Frei/Gebucht-Informationen) mit anderen Benutzern teilen dürfen.  <br/> |[Freigabe in Exchange Online](https://technet.microsoft.com/en-us/library/jj916670%28v=exchg.150%29.aspx) <br/> [Organisationsbeziehungen in Exchange Online](https://technet.microsoft.com/en-us/library/jj916658%28v=exchg.150%29.aspx) <br/> [Erstellen einer Organisationsbeziehung in Exchange Online](https://technet.microsoft.com/en-us/library/jj916671%28v=exchg.150%29.aspx) <br/> [Ändern und organisieren von Beziehungen in Exchange Online](https://technet.microsoft.com/en-us/library/jj916659%28v=exchg.150%29.aspx) <br/> [Entfernen einer Organisationsbeziehung in Exchange Online](https://technet.microsoft.com/en-us/library/jj916657%28v=exchg.150%29.aspx) <br/> [Freigeben von Kalendern für externe Benutzer](https://support.office.com/article/fb00dd4e-2d5f-4e8d-8ff4-94b2cf002bdd) <br/> |
|Steuern, wie Benutzer ihre Kalender für Personen außerhalb Ihrer Organisation freigeben  <br/> |Administratoren wenden Freigaberichtlinien auf Benutzerpostfächer an, um zu steuern, für wen Sie freigegeben werden können und welche Zugriffsebene gewährt wird.  <br/> |[Freigaberichtlinien in Exchange Online](https://technet.microsoft.com/en-us/library/jj916673%28v=exchg.150%29.aspx) <br/> [Erstellen einer Freigaberichtlinie in Exchange Online](https://technet.microsoft.com/en-us/library/jj916676%28v=exchg.150%29.aspx) <br/> [Anwenden einer Freigaberichtlinie auf Postfächer in Exchange Online](https://technet.microsoft.com/en-us/library/jj916672%28v=exchg.150%29.aspx) <br/> [Ändern, deaktivieren oder Entfernen einer Freigaberichtlinie in Exchange Online](https://technet.microsoft.com/en-us/library/jj916674%28v=exchg.150%29.aspx) <br/> |
|Konfigurieren sicherer e-Mail-Kanäle und Steuern des Nachrichtenflusses mit Partnerorganisationen  <br/> |Administratoren erstellen Connectors zum Anwenden von Sicherheit auf e-Mail-Austausch mit einer Partnerorganisation oder einem Dienstanbieter. Die Connectors erzwingen die Verschlüsselung über TLS (Transport Layer Security) sowie Einschränkungen für Domänennamen oder IP-Adressbereiche, von denen Ihre Partner e-Mails senden.  <br/> |[Wie Exchange Online mithilfe von TLS E-Mail-Verbindungen in Office 365 sichert](https://technet.microsoft.com/en-us/library/mt163898.aspx) <br/> [Configure mail flow using connectors in Office 365](https://technet.microsoft.com/en-us/library/ms.exch.eac.connectorselection%28v=exchg.150%29.aspx) <br/> [Remotedomänen in Exchange Online](https://technet.microsoft.com/en-us/library/jj966211%28v=exchg.150%29.aspx) <br/> [Einrichten eines Connectors für den sicheren Nachrichtenfluss mit einer Partnerorganisation](https://technet.microsoft.com/en-us/library/dn751021%28v=exchg.150%29.aspx) <br/> [Bewährte Methoden für die Nachrichtenübermittlung für Exchange Online und Office 365 (Übersicht)](https://technet.microsoft.com/en-us/library/0e6cd9d5-ad3e-418a-8ea9-3bf33332c491%28v=exchg.150%29) <br/> |
   
## <a name="sharepoint-online-and-onedrive-for-business-collaboration-options"></a>SharePoint Online-und OneDrive for Business-Zusammenarbeitsoptionen

|**Freigabe Ziele**|**Verwaltungsaktion**|**Vorgehensweise**|
|:-----|:-----|:-----|
|Freigeben von Websites und Dokumenten für externe Benutzer  <br/> |Administratoren konfigurieren die Freigabe auf dem Mandanten oder auf Websitesammlungsebene für authentifizierte Microsoft-Konten, für Arbeits-oder Schul Konten oder Gastkonten.  <br/> |[Verwalten der externen Freigabe für Ihre SharePoint-Online-Umgebung](https://support.office.com/en-US/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85?ui=en-US&amp;rs=en-US&amp;ad=US) <br/> [Eingeschränkte Domänen Freigabe in Office 365 SharePoint Online und OneDrive for Business](https://support.office.com/en-US/article/Restricted-Domains-Sharing-in-Office-365-SharePoint-Online-and-OneDrive-for-Business-5d7589cd-0997-4a00-a2ba-2320ec49c4e9) <br/> [Verwenden von SharePoint Online als B2B-Extranetlösung (Business-to-Business)](https://support.office.com/article/7b087413-165a-4e94-8871-4393e0b9c037) <br/> |
|Nachverfolgen und Steuern der externen Freigabe für Endbenutzer  <br/> |OneDrive for Business-Dateibesitzer und SharePoint Online-Endbenutzer konfigurieren die Website-und Dokumentfreigabe und richten Benachrichtigungen zum Nachverfolgen der Freigabe ein.  <br/> |[Konfigurieren von Benachrichtigungen für die externe Freigabe für OneDrive for Business](https://support.office.com/en-US/article/Configure-notifications-for-external-sharing-for-OneDrive-for-Business-b640c693-f170-4227-b8c1-b0a7e0fa876b) <br/> [Freigeben von SharePoint-Dateien oder-Ordnern in Office 365](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) <br/> |
   
## <a name="skype-for-business-collaboration-options"></a>Skype for Business-Zusammenarbeitsoptionen

|**Freigabeziel**|**Verwaltungsaktion**|**Vorgehensweise**|
|:-----|:-----|:-----|
|Skype for Business Online-Sofortnachrichten, Anrufe und Anwesenheitsinformationen mit anderen Skype for Business-Benutzern  <br/> |Administratoren können Ihre Skype for Business Online-Benutzer in aktivieren, Audio-und Videoanrufe tätigen und die Anwesenheitsinformationen mit Benutzern in einem anderen Office 365-Mandanten anzeigen.  <br/> |[Zulassen, dass Benutzer externe Skype for Business-Benutzer kontaktieren](https://support.office.com/article/b414873a-0059-4cd5-aea1-e5d0857dbc94) <br/> |
|Skype for Business Online-Sofortnachrichten, Anrufe und Anwesenheitsinformationen für Skype-Benutzer (Consumer)  <br/> |Administratoren können Ihre Skype for Business Online-Benutzer im Chat aktivieren, Anrufe tätigen und die Anwesenheitsinformationen mit Skype-Benutzern (Consumer) anzeigen.  <br/> |[Zulassen, dass Skype for Business-Benutzer Skype-Kontakte hinzufügen](https://support.office.com/article/08666236-1894-42ae-8846-e49232bbc460) <br/> |
   
## <a name="azure-ad-b2b-collaboration-options"></a>Azure AD B2B-Zusammenarbeitsoptionen

|**Freigabeziel**|**Verwaltungsaktion**|**Vorgehensweise**|
|:-----|:-----|:-----|
|Azure AD B2B-Zusammenarbeit – Inhaltsfreigabe durch Hinzufügen externer Benutzer zu einer Gruppe im Verzeichnis einer Organisation  <br/> |Ein globaler Administrator für einen Office 365-Mandanten kann Personen in einem anderen Office 365-Mandanten einladen, an seinem Verzeichnis teilzunehmen, diese externen Benutzer zu einer Gruppe hinzuzufügen und den Zugriff auf Inhalte wie SharePoint-Websites und-Bibliotheken für die Gruppe zu gewähren.  <br/> |[Was ist die Azure AD B2B-Zusammenarbeits Vorschau?](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b) <br/> [Azure AD B2B: neue Updates machen Cross-Business-collab einfach](https://blogs.technet.microsoft.com/enterprisemobility/2017/02/01/azure-ad-b2b-new-updates-make-cross-business-collab-easy/) <br/> [Office 365-externe Freigabe und Azure Active Directory B2B-Zusammenarbeit](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-o365-external-user) <br/> [Azure Active Directory B2B-API für die Zusammenarbeit und Anpassung](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-api) <br/> [Azure AD und Identity Show: Azure AD B2B Collaboration (Business to Business](https://channel9.msdn.com/Series/Azure-AD-Identity/AzureADB2B) <br/> |
   
## <a name="office-365-collaboration-options"></a>Office 365-Zusammenarbeitsoptionen

|**Freigabeziel**|**Verwaltungsaktion**|**Vorgehensweise**|
|:-----|:-----|:-----|
|Office 365-Gruppen – e-Mail, Kalender, OneNote und freigegebene Dateien an zentraler Stelle  <br/> |Gruppen werden in den Plänen Business Essentials, Business Premium, Education und Enterprise E1, E3 und E5 unterstützt. Personen in einem Office 365-Mandanten können eine Gruppe erstellen und Personen in einem anderen Office 365-Mandanten als Gastbenutzer einladen. Gilt auch für Dynamics CRM.  <br/> |[Informationen zu Office 365-Gruppen](https://support.office.com/article/b565caa1-5c40-40ef-9915-60fdb2d97fa2) <br/> [Gastzugriff in Office 365-Gruppen](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6) <br/> [Bereitstellen von Office 365-Gruppen](https://technet.microsoft.com/en-us/library/dn896591.aspx) <br/> |
   
## <a name="yammer-collaboration-options"></a>Optionen für die Zusammenarbeit bei jammern

|**Freigabeziel**|**Verwaltungsaktion**|**Vorgehensweise**|
|:-----|:-----|:-----|
|Jammern – Zusammenarbeit über ein soziales Unternehmens Medium  <br/> |Wenn die Möglichkeit, externe Gruppen zu erstellen, nicht durch einen jammern-Administrator deaktiviert wird, können Benutzer externe Gruppen erstellen, um in jammern durch Unterhaltungen zusammenzuarbeiten, die Möglichkeit, Beiträge zu mögen und zu folgen, Dateien zu teilen und online zu chatten.  <br/> |[Erstellen und Verwalten von externen Gruppen in Yammer](https://support.office.com/article/9ccd15ce-0efc-4dc1-81bc-4a424ab6f92a) <br/> |
   
## <a name="teams-collaboration-options"></a>Teams-Zusammenarbeitsoptionen

|**Freigabeziel**|**Verwaltungsaktion**|**Vorgehensweise**|
|:-----|:-----|:-----|
|Zusammenarbeit an Teams mit externen Benutzern  <br/> |Ein globaler Administrator für den einladenden Office 365-Mandanten muss externe Zusammenarbeit in Teams aktivieren. Globale Administratoren und Teambesitzer können nun alle Personen mit einer e-Mail-Adresse einladen, in Teams zusammenzuarbeiten.  <br/> Administratoren können auch bereits in Ihrem Mandanten vorhandene Gäste verwalten und bearbeiten.  <br/> |[Autorisieren des Gastzugriffs](https://docs.microsoft.com/en-us/microsoftteams/teams-dependencies) <br/> [Aktivieren oder Deaktivieren des Gastzugriffs in Teams](https://docs.microsoft.com/en-us/microsoftteams/set-up-guests) <br/> [Verwenden von PowerShell zum Steuern des Gastzugriffs](https://docs.microsoft.com/en-us/microsoftteams/guest-access-powershell) <br/> [Checkliste für den Gastzugriff](https://docs.microsoft.com/en-us/microsoftteams/guest-access-checklist) <br/> [Anzeigen von Gastbenutzern](https://docs.microsoft.com/en-us/microsoftteams/view-guests) <br/> [Bearbeiten von Gastbenutzer Informationen](https://docs.microsoft.com/en-us/microsoftteams/edit-guests-information) <br/> |
|Team Besitzer können einladen und verwalten, wie Gäste in ihren Teams zusammenarbeiten.  <br/> |Team Besitzer haben zusätzliche Kontrolle darüber, was die Gäste in ihren Teams tun können.  <br/> |[Hinzufügen von Gästen](https://support.office.com/en-us/article/teams-and-channels-df38ae23-8f85-46d3-b071-cb11b9de5499?ui=en-US&amp;rs=en-US&amp;ad=US#bkmk_addingguests&amp;ID0EAABAAA=Add_guests) <br/> [Hinzufügen eines Gasts zu einem Team](https://docs.microsoft.com/en-us/microsoftteams/add-guests) <br/> [Verwalten des Gastzugriffs in Teams](https://docs.microsoft.com/en-us/microsoftteams/manage-guests) <br/> [Anzeigen der Personen in einem Team oder in einem Kanal](https://support.office.com/en-us/article/see-who-s-on-a-team-or-in-a-channel-5c6be9be-9c45-4a0f-a1a0-f332b23cb6b7?ui=en-US&amp;rs=en-US&amp;ad=US) <br/> |
|Gäste aus anderen Mandanten können Inhalte in Teams anzeigen und mit anderen Mitgliedern zusammenarbeiten.  <br/> |Keine.  <br/> |[Gastzugriffs Erfahrung](https://docs.microsoft.com/en-us/microsoftteams/guest-experience) <br/> |

## <a name="power-bi-collaboration-options"></a>Power BI-Zusammenarbeitsoptionen

|**Freigabeziel**|**Verwaltungsaktion**|**Vorgehensweise**|
|:-----|:-----|:-----|
|Power BI ermöglicht externen Gastbenutzern das Nutzen von Inhalten, die über Links freigegeben werden. Dadurch können Benutzer in der Organisation Inhalte auf sichere Weise in Organisationen verteilen.<br/> | Der Power BI-Administrator kann steuern, ob Benutzer externe Benutzer zum Anzeigen von Inhalten innerhalb der Organisation einladen können. <br/> |[Verteilen von Power BI-Inhalten an externe Gastbenutzer mit Azure AD B2B](https://docs.microsoft.com/en-us/power-bi/service-admin-azure-ad-b2b) <br/> |
 
## <a name="points-to-be-aware-of-about-office-365-inter-tenant-collaboration"></a>Weitere Informationen zu Office 365-Zusammenarbeitsbeziehungen zwischen Mandanten

### <a name="sharing-of-user-accounts-licenses-subscriptions-and-storage"></a>Freigabe von Benutzerkonten, Lizenzen, Abonnements und Speicher

Jede Organisation verwaltet eigene Benutzerkonten, Identitäten, Sicherheitsgruppen, Abonnements, Lizenzen und Speicher. Die Benutzer verwenden die Zusammenarbeitsfunktionen in Office 365 zusammen mit Freigaberichtlinien und Sicherheitseinstellungen, um Zugriff auf erforderliche Informationen zu gewähren und gleichzeitig die Kontrolle über die Unternehmensressourcen zu behalten.
  
- **Benutzerkonten:** Konten können nicht freigegeben werden, und Konten können nicht zwischen den Mandanten oder Partitionen in den lokalen Active Directory-Verzeichnisdiensten dupliziert werden. 
    
- **Lizenz &amp; Abonnements:** In Office 365 erteilen Lizenzen aus Lizenzierungs Plänen (auch als SKUs oder Office 365-Pläne bezeichnet) Benutzern den Zugriff auf die Office 365-Dienste, die für diese Pläne definiert sind. 
    
- **Speicher:** In Office 365-Plänen werden Softwaregrenzen und-Grenzen für SharePoint Online separat von Postfachspeicher Grenzwerten verwaltet. Die Speichergrenzwerte für Postfächer werden mithilfe von Exchange Online eingerichtet und verwaltet. In beiden Szenarien kann Speicher nicht als Cross-Mandanten freigegeben werden. 
    
### <a name="can-we-share-domain-namespaces-across-office-365-tenants"></a>Können Domänen-Namespaces in Office 365-Mandanten gemeinsam genutzt werden?

Nein. Vanity-Domänen wie fabrikam.com oder tailspintoys.com können nur mit einem Mandanten verknüpft und verwendet werden. Jeder Mandant muss einen eigenen Namespace haben; UPN-, SMTP-und SIP-Namespaces können nicht für Mandanten freigegeben werden.
  
### <a name="what-about-hybrid-components-and-office-365-inter-tenant-collaboration"></a>Was ist mit hybridkomponenten und der mandantenübergreifenden Zusammenarbeit in Office 365?

Lokale hybridkomponenten, wie eine Exchange-Organisation und Azure AD Connect, können nicht über mehrere Mandanten aufgeteilt werden.
  

