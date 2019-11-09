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
- SPO_Content
search.appverid:
- MET150
- MOE150
ms.assetid: eb45fd8b-1d5d-4b0c-9c5a-479dbb176e7d
description: Erfahren Sie, wie die Zusammenarbeit zwischen Mandanten und Organisationen in Office 365 funktioniert.
ms.openlocfilehash: b232cd2202f1b4e13102fd33ba545cfdcbb2edfe
ms.sourcegitcommit: 89ecf793443963b4c87cf1033bf0284cbfb83d9a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2019
ms.locfileid: "38078174"
---
# <a name="office-365-inter-tenant-collaboration"></a>Zusammenarbeit zwischen Office 365-Mandanten

In diesem Artikel werden verschiedene Möglichkeiten für die Zusammenarbeit zwischen zwei Office 365-Mandanten beschrieben. Dieser Artikel richtet sich an Office 365-Administratoren.
  
Angenommen, zwei Organisationen, Fabrikam und Contoso, verfügen jeweils über einen Office 365 Business-Mandanten und möchten an mehreren Projekten zusammenarbeiten. Einige dieser Projekte haben einen begrenzten Zeitrahmen und andere sind fortlaufend. Wie können Fabrikam und Contoso ihren Mitarbeitern und Teams eine effektivere Zusammenarbeit zwischen den verschiedenen Office 365-Mandanten auf sichere Weise ermöglichen? Office 365 bietet in Verbindung mit der Azure Active Directory B2B-Zusammenarbeit mehrere Optionen. In diesem Artikel werden einige wichtige Szenarien beschrieben, die Fabrikam und Contoso in Betracht ziehen können.
  
Die Optionen für die Zusammenarbeit zwischen Office 365-Mandanten umfassen die Verwendung eines zentralen Speicherorts für Dateien und Unterhaltungen, die Freigabe von Kalendern, die Verwendung von Chatnachrichten, Audio-/Videoanrufe für die Kommunikation und das Sichern des Zugriffs auf Ressourcen und Anwendungen. In den folgenden Tabellen können Sie Lösungen auswählen und auf weitere Informationen zugreifen.
  
## <a name="exchange-online-collaboration-options"></a>Optionen für die Zusammenarbeit in Exchange Online

|**Freigabeziel**|**Administratoraktion**|**Informationen zur Vorgehensweise**|
|:-----|:-----|:-----|
|Kalenderfreigabe für eine andere Office 365-Organisation  <br/> |Administratoren können verschiedene Ebenen des Kalenderzugriffs in Exchange Online einrichten, sodass Unternehmen mit anderen Unternehmen zusammenarbeiten und die Benutzer Terminpläne (Frei/Gebucht-Informationen) für andere Personen freigeben können.  <br/> |[Freigabe in Exchange Online](https://technet.microsoft.com/library/jj916670%28v=exchg.150%29.aspx) <br/> [Organisationsbeziehungen in Exchange Online](https://technet.microsoft.com/library/jj916658%28v=exchg.150%29.aspx) <br/> [Erstellen einer Organisationsbeziehung in Exchange Online](https://technet.microsoft.com/library/jj916671%28v=exchg.150%29.aspx) <br/> [Ändern einer Organisationsbeziehung in Exchange Online](https://technet.microsoft.com/library/jj916659%28v=exchg.150%29.aspx) <br/> [Entfernen einer Organisationsbeziehung in Exchange Online](https://technet.microsoft.com/library/jj916657%28v=exchg.150%29.aspx) <br/> [Freigeben von Kalendern für externe Benutzer](https://support.office.com/article/fb00dd4e-2d5f-4e8d-8ff4-94b2cf002bdd) <br/> |
|Steuern, wie Benutzer ihre Kalender für Personen außerhalb Ihrer Organisation freigeben können  <br/> |Administratoren wenden Freigaberichtlinien auf Postfächer von Benutzern an, um zu steuern, für welche Personen diese freigegeben und welche Zugriffsebene erteilt werden kann.  <br/> |[Freigaberichtlinien in Exchange Online](https://technet.microsoft.com/library/jj916673%28v=exchg.150%29.aspx) <br/> [Erstellen einer Freigaberichtlinie in Exchange Online](https://technet.microsoft.com/library/jj916676%28v=exchg.150%29.aspx) <br/> [Anwenden von Freigaberichtlinien auf Postfächer in Exchange Online](https://technet.microsoft.com/library/jj916672%28v=exchg.150%29.aspx) <br/> [Ändern, Deaktivieren oder Entfernen einer Freigaberichtlinie in Exchange Online](https://technet.microsoft.com/library/jj916674%28v=exchg.150%29.aspx) <br/> |
|Konfigurieren sicherer E-Mail-Kanäle und Steuern des Nachrichtenflusses mit Partnerorganisationen  <br/> |Administratoren erstellen Connectors, um Sicherheit auf den E-Mail-Austausch mit einer Partnerorganisation oder einem Dienstanbieter anzuwenden. Die Connectors erzwingen Verschlüsselung über TLS (Transport Layer Security) und ermöglichen Einschränkungen für Domänennamen oder IP-Adressbereiche, von denen die Partner E-Mails senden können.  <br/> |[Wie Exchange Online mithilfe von TLS E-Mail-Verbindungen in Office 365 sichert](https://technet.microsoft.com/library/mt163898.aspx) <br/> [Konfigurieren des Nachrichtenflusses mit Connectors in Office 365](https://technet.microsoft.com/library/ms.exch.eac.connectorselection%28v=exchg.150%29.aspx) <br/> [Remotedomänen in Exchange Online](https://technet.microsoft.com/library/jj966211%28v=exchg.150%29.aspx) <br/> [Einrichten von Connectors für sicheren Nachrichtenfluss mit einer Partnerorganisation](https://technet.microsoft.com/library/dn751021%28v=exchg.150%29.aspx) <br/> [Bewährte Methoden für die Nachrichtenübermittlung für Exchange Online und Office 365 (Übersicht)](https://technet.microsoft.com/library/0e6cd9d5-ad3e-418a-8ea9-3bf33332c491%28v=exchg.150%29) <br/> |
   
## <a name="sharepoint-online-and-onedrive-for-business-collaboration-options"></a>Optionen für die Zusammenarbeit in SharePoint Online und OneDrive for Business

|**Freigabeziele**|**Administratoraktion**|**Informationen zur Vorgehensweise**|
|:-----|:-----|:-----|
|Freigeben von Websites und Dokumenten für externe Benutzer  <br/> |Administratoren konfigurieren die Freigabe auf Mandantenebene oder auf Websitesammlungsebene für authentifizierte Microsoft-Konten, authentifizierte Geschäfts-, Schul- oder Unikonten oder Gastkonten.  <br/> |[Verwalten der externen Freigabe für Ihre SharePoint-Online-Umgebung](https://support.office.com/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85?ui=en-US&amp;rs=en-US&amp;ad=US) <br/> [Eingeschränkte Domänenfreigabe in Office 365 SharePoint Online und OneDrive for Business](https://support.office.com/article/Restricted-Domains-Sharing-in-Office-365-SharePoint-Online-and-OneDrive-for-Business-5d7589cd-0997-4a00-a2ba-2320ec49c4e9) <br/> [Verwenden von SharePoint Online als Business-to-Business-Extranetlösung](https://support.office.com/article/7b087413-165a-4e94-8871-4393e0b9c037) <br/> |
|Nachverfolgen und Steuern der externen Freigabe für Endbenutzer  <br/> |OneDrive for Business-Dateibesitzer und SharePoint Online-Endbenutzer konfigurieren die Freigabe von Websites und Dokumenten und richten Benachrichtigungen zum Nachverfolgen der Freigabe ein.  <br/> |[Konfigurieren von Benachrichtigungen für externe Freigaben für OneDrive for Business](https://support.office.com/article/Configure-notifications-for-external-sharing-for-OneDrive-for-Business-b640c693-f170-4227-b8c1-b0a7e0fa876b) <br/> [Freigeben von SharePoint-Dateien oder -Ordnern in Office 365](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) <br/> |
   
## <a name="skype-for-business-collaboration-options"></a>Optionen für die Zusammenarbeit in Skype for Business

|**Freigabeziel**|**Administratoraktion**|**Informationen zur Vorgehensweise**|
|:-----|:-----|:-----|
|Skype for Business Online – Chatnachrichten, Anrufe und Anwesenheitsinformationen für andere Skype for Business-Benutzer  <br/> |Administratoren können für Skype for Business Online-Benutzer Chatnachrichten, Audio-/Videoanrufe und die Anzeige von Anwesenheitsinformationen für Benutzer in einem anderen Office 365-Mandanten aktivieren.  <br/> |[Zulassen, dass Benutzer externe Skype for Business-Benutzer kontaktieren](https://support.office.com/article/b414873a-0059-4cd5-aea1-e5d0857dbc94) <br/> |
|Skype for Business Online – Chatnachrichten, Anrufe und Anwesenheitsinformationen für Skype-Benutzer (Privatkunden)  <br/> |Administratoren können für Skype for Business Online-Benutzer Chatnachrichten, Anrufe und die Anzeige von Anwesenheitsinformationen für Skype-Benutzer (Privatkunden) aktivieren.  <br/> |[Zulassen, dass Skype for Business-Benutzer Skype-Kontakte hinzufügen](https://support.office.com/article/08666236-1894-42ae-8846-e49232bbc460) <br/> |
   
## <a name="azure-ad-b2b-collaboration-options"></a>Optionen für die Zusammenarbeit in Azure Active Directory B2B

|**Freigabeziel**|**Administratoraktion**|**Informationen zur Vorgehensweise**|
|:-----|:-----|:-----|
|Azure Active Directory B2B-Zusammenarbeit – Inhaltsfreigabe durch Hinzufügen externer Benutzer zu einer Gruppe im Verzeichnis einer Organisation  <br/> |Ein globaler Administrator für einen Office 365-Mandanten kann Personen in einem anderen Office 365-Mandanten zur Teilnahme am Verzeichnis einladen, diese externen Benutzer zu einer Gruppe hinzufügen und der Gruppe Zugriff auf Inhalte wie SharePoint-Websites und Bibliotheken gewähren.  <br/> |[Informationen zur Vorschau der Azure AD B2B-Zusammenarbeit](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b) <br/> [Azure Active Directory B2B: Neue Updates erleichtern die unternehmensübergreifende Zusammenarbeit](https://blogs.technet.microsoft.com/enterprisemobility/2017/02/01/azure-ad-b2b-new-updates-make-cross-business-collab-easy/) <br/> [Externe Office 365-Freigaben und Azure Active Directory B2B-Zusammenarbeit](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-o365-external-user) <br/> [Azure Active Directory B2B-Zusammenarbeit: API und Anpassung](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-api) <br/> [Azure AD und Identity Show: Azure AD B2B-Zusammenarbeit (Business-to-Business)](https://channel9.msdn.com/Series/Azure-AD-Identity/AzureADB2B) <br/> |
   
## <a name="office-365-collaboration-options"></a>Optionen für die Zusammenarbeit in Office 365

|**Freigabeziel**|**Administratoraktion**|**Informationen zur Vorgehensweise**|
|:-----|:-----|:-----|
|Office 365-Gruppen – E-Mail, Kalender, OneNote und freigegebene Dateien an einem zentralen Ort  <br/> |Gruppen werden in Business Essentials und Business Premium sowie den Plänen Enterprise E1, E3 und E5 unterstützt. Personen in einem Office 365-Mandanten können eine Gruppe erstellen und Personen in einem anderen Office 365-Mandanten als Gastbenutzer einladen. Dies gilt auch für Dynamics CRM.  <br/> |[Weitere Informationen zu Office 365-Gruppen](https://support.office.com/article/b565caa1-5c40-40ef-9915-60fdb2d97fa2) <br/> [Gastzugriff in Office 365-Gruppen](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6) <br/> [Bereitstellen von Office 365-Gruppen](https://technet.microsoft.com/library/dn896591.aspx) <br/> |
   
## <a name="yammer-collaboration-options"></a>Optionen für die Zusammenarbeit in Yammer

|**Freigabeziel**|**Administratoraktion**|**Informationen zur Vorgehensweise**|
|:-----|:-----|:-----|
|Yammer – Zusammenarbeit über ein soziales Medium des Unternehmens  <br/> |Sofern die Möglichkeit zum Erstellen externer Gruppen nicht vom Yammer-Administrator deaktiviert wird, können Benutzer externe Gruppen für die Zusammenarbeit in Yammer über Unterhaltungen, die Möglichkeit zum Bewerten und Folgen für Beiträge, das Freigeben von Dateien und Onlinechats erstellen.  <br/> |[Erstellen und Verwalten von externen Gruppen in Yammer](https://support.office.com/article/9ccd15ce-0efc-4dc1-81bc-4a424ab6f92a) <br/> |
   
## <a name="teams-collaboration-options"></a>Optionen für die Zusammenarbeit in Teams

|**Freigabeziel**|**Administratoraktion**|**Informationen zur Vorgehensweise**|
|:-----|:-----|:-----|
|Zusammenarbeit in Teams Benutzern außerhalb Ihrer Organisation  <br/> |Ein globaler Administrator des einladenden Office 365-Mandanten muss die externe Zusammenarbeit in Teams ermöglichen. Globale Administratoren und Teambesitzer können nun jeden Gast, der über eine E-Mail-Adresse verfügt, einladen, um in Teams zusammenzuarbeiten.  <br/> Administratoren können auch bereits in Ihrem Mandanten vorhandene Gäste verwalten und bearbeiten.  <br/> |[Autorisieren des Gastzugriffs](https://docs.microsoft.com/microsoftteams/teams-dependencies) <br/> [Aktivieren und Deaktivieren des Gastzugriffs in Teams](https://docs.microsoft.com/microsoftteams/set-up-guests) <br/> [Verwenden von PowerShell zum Steuern des Gastzugriffs](https://docs.microsoft.com/microsoftteams/guest-access-powershell) <br/> [Checkliste für den Gastzugriff](https://docs.microsoft.com/microsoftteams/guest-access-checklist) <br/> [Anzeigen von Gastbenutzern](https://docs.microsoft.com/microsoftteams/view-guests) <br/> [Bearbeiten von Gastbenutzerinformationen](https://docs.microsoft.com/microsoftteams/edit-guests-information) <br/> |
|Teambesitzer können Gäste einladen und verwalten, wie sie innerhalb Ihrer Teams mit ihnen zusammenarbeiten.  <br/> |Teambesitzer haben außerdem Kontrolle darüber, was die Gäste in ihren Teams tun können.  <br/> |[Hinzufügen von Gästen](https://support.office.com/article/teams-and-channels-df38ae23-8f85-46d3-b071-cb11b9de5499?ui=en-US&amp;rs=en-US&amp;ad=US#bkmk_addingguests&amp;ID0EAABAAA=Add_guests) <br/> [Hinzufügen eines Gasts zu einem Team](https://docs.microsoft.com/microsoftteams/add-guests) <br/> [Verwalten des Gastzugriffs in Microsoft Teams](https://docs.microsoft.com/microsoftteams/manage-guests) <br/> [Anzeigen, wer in einem Team oder Kanal ist](https://support.office.com/article/see-who-s-on-a-team-or-in-a-channel-5c6be9be-9c45-4a0f-a1a0-f332b23cb6b7?ui=en-US&amp;rs=en-US&amp;ad=US) <br/> |
|Gäste anderer Mandanten können Inhalte in Teams anzeigen und mit anderen Mitgliedern zusammenarbeiten.  <br/> |Keine.  <br/> |[Gastzugriff](https://docs.microsoft.com/microsoftteams/guest-experience) <br/> |

## <a name="power-bi-collaboration-options"></a>Optionen für die Zusammenarbeit in Power BI

|**Freigabeziel**|**Administratoraktion**|**Informationen zur Vorgehensweise**|
|:-----|:-----|:-----|
|Power BI ermöglicht externen Gastbenutzern, über Links freigegebene Inhalte zu nutzen. Dies ermöglicht es Benutzern, Inhalte auf sichere Art und Weise über Organisationsgrenzen hinweg zu verteilen.<br/> | Der Power BI-Administrator kann steuern, ob Benutzer externe Benutzer einladen können, Inhalte von innerhalb der Organisation anzuzeigen. <br/> |[Verteilen von Power BI-Inhalten an externe Gastbenutzer mit Azure Active Directory B2B](https://docs.microsoft.com/power-bi/service-admin-azure-ad-b2b) <br/> |
 
## <a name="points-to-be-aware-of-about-office-365-inter-tenant-collaboration"></a>Zu beachtende Punkte für eine Zusammenarbeit zwischen Office 365-Mandanten

### <a name="sharing-of-user-accounts-licenses-subscriptions-and-storage"></a>Gemeinsame Nutzung (Freigabe) von Benutzerkonten, Lizenzen, Abonnements und Speicher

Jede Organisation verwalte ihre eigenen Benutzerkonten, Identitäten, Sicherheitsgruppen, Abonnements, Lizenzen und Speicher. Personen verwenden die Zusammenarbeitsfeatures in Office 365 zusammen mit Freigaberichtlinien und Sicherheitseinstellungen, um Zugriff auf benötigte Informationen zu bieten und gleichzeitig die Kontrolle über die Unternehmensressourcen zu behalten.
  
- **Benutzerkonten:** Es ist nicht möglich, Konten zwischen den Mandanten oder Partitionen in den lokalen Active Directory-Verzeichnisdiensten freizugeben oder zu duplizieren. 
    
- **Lizenzen &amp; Abonnements:** In Office 365 erhalten Benutzer über Lizenzen aus Lizenzplänen (auch als SKUs oder Office 365-Pläne bezeichnet) Zugriff auf die Office 365-Dienste, die für diese Pläne definiert sind. 
    
- **Speicher:** In Office 365-Plänen werden Softwarelimits und -beschränkungen für SharePoint Online und Speicherbegrenzungen für Postfächer getrennt verwaltet. Speicherbegrenzungen für Postfächer werden mit Exchange Online eingerichtet und verwaltet. In beiden Fällen kann Speicher nicht von mehreren Mandanten gemeinsam genutzt werden. 
    
### <a name="can-we-share-domain-namespaces-across-office-365-tenants"></a>Können Domänen-Namespaces von Office 365-Mandanten gemeinsam genutzt werden?

Nein. Benutzerdefinierte Domänen, z. B. „fabrikam.com“ oder „tailspintoys.com“, können nur jeweils einem Mandanten zugeordnet sein und von diesem verwendet werden. Jeder Mandant muss einen eigenen Namespace haben; UPN-, SMTP- und SIP-Namespaces können nicht von Mandanten gemeinsam genutzt werden.
  
### <a name="what-about-hybrid-components-and-office-365-inter-tenant-collaboration"></a>Wie steht es mit Hybridkomponenten und Zusammenarbeit zwischen Office 365-Mandanten?

Lokale Hybridkomponenten, z. B. eine Exchange-Organisation und Azure AD Connect, können nicht auf mehrere Mandanten aufgeteilt werden.
  

