---
title: Office 365 zwischen Mandanten für die Zusammenarbeit
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 6/28/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- MOE150
ms.assetid: eb45fd8b-1d5d-4b0c-9c5a-479dbb176e7d
description: Hier erfahren Sie, wie Office 365 für die Zusammenarbeit über Mandanten und Organisationen hinweg funktioniert.
ms.openlocfilehash: 932c837f9dc09dd0469a17ad4e6a05f09966d29c
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540785"
---
# <a name="office-365-inter-tenant-collaboration"></a>Office 365 zwischen Mandanten für die Zusammenarbeit

In diesem Artikel werden verschiedene Möglichkeiten für die Zusammenarbeit zwischen zwei Office 365-Mandanten. Es ist für Office 365-Administratoren vorgesehen.
  
Nehmen Sie an, dass zwei Organisationen, Fabrikam und Contoso, jeweils ein Office 365 für Unternehmen Mandanten verwendet und sie an mehreren Projekten zusammenarbeiten möchten. von denen einige für kurze Zeit ausgeführt und von denen einige laufende. Aktivieren Fabrikam und Contoso kann wie ihre Personen und Teams effektiver zusammenarbeiten über ihre verschiedenen Office 365-Mandanten auf sichere Weise? Office 365, zusammen mit Azure Active Directory B2B für die Zusammenarbeit, bietet verschiedene Optionen. In diesem Artikel werden mehrere wichtige Szenarios, die "Fabrikam" und "Contoso" in Betracht ziehen können.
  
Office 365 für die Zusammenarbeit zwischen Mandanten Optionen zählen die Verwendung von eines zentralen Speicherorts für Dateien und Unterhaltungen, Freigeben von Kalendern, eine Unterhaltung mit Sofortnachrichten, Audio-Video-Anrufe für Kommunikation und sicheren Zugriff auf Ressourcen und Anwendungen. Verwenden Sie zum Auswählen von Lösungen und erfahren mehr in den folgenden Tabellen.
  
## <a name="exchange-online-collaboration-options"></a>Exchange Online Optionen für die Zusammenarbeit

|**Freigabeziel**|**Administrative Aktion**|**Gewusst wie-Informationen**|
|:-----|:-----|:-----|
|Kalenderfreigabe für eine andere Office 365-Organisation  <br/> |Administratoren können unterschiedliche Zugriffsebenen Kalender in Exchange Online, um Unternehmen die Zusammenarbeit mit anderen Unternehmen und die Zeitpläne (Frei/Gebucht-Kalenderinformationen) freigeben Benutzer können mit anderen zulassen einrichten  <br/> |[Freigabe in Exchange Online](https://technet.microsoft.com/en-us/library/jj916670%28v=exchg.150%29.aspx) <br/> [Organisationsbeziehungen in Exchange Online](https://technet.microsoft.com/en-us/library/jj916658%28v=exchg.150%29.aspx) <br/> [Erstellen einer Organisationsbeziehung in Exchange Online](https://technet.microsoft.com/en-us/library/jj916671%28v=exchg.150%29.aspx) <br/> [Ändern und organisationsbeziehung in Exchange Online](https://technet.microsoft.com/en-us/library/jj916659%28v=exchg.150%29.aspx) <br/> [Entfernen einer organisationsbeziehung in Exchange Online](https://technet.microsoft.com/en-us/library/jj916657%28v=exchg.150%29.aspx) <br/> [Freigeben von Kalendern mit externen Benutzern](https://support.office.com/article/fb00dd4e-2d5f-4e8d-8ff4-94b2cf002bdd) <br/> |
|Steuern Sie, wie Benutzer ihre Kalender mit Personen außerhalb Ihrer Organisation freigeben  <br/> |Administratoren gelten Freigaberichtlinien für Postfächer von Benutzern zu steuern, wer mit gemeinsam genutzt werden können und die Zugriffsebene erteilt  <br/> |[Freigaberichtlinien in Exchange Online](https://technet.microsoft.com/en-us/library/jj916673%28v=exchg.150%29.aspx) <br/> [Erstellen einer Freigaberichtlinie in Exchange Online](https://technet.microsoft.com/en-us/library/jj916676%28v=exchg.150%29.aspx) <br/> [Anwenden von Freigaberichtlinien auf Postfächer in Exchange Online](https://technet.microsoft.com/en-us/library/jj916672%28v=exchg.150%29.aspx) <br/> [Ändern, deaktivieren oder Entfernen einer Freigaberichtlinie in Exchange Online](https://technet.microsoft.com/en-us/library/jj916674%28v=exchg.150%29.aspx) <br/> |
|Konfigurieren von sicheren e-Mail-Kanälen und steuern Nachrichtenübermittlung mit Partnerorganisationen  <br/> |Administratoren erstellen Verbinder um Sicherheit für e-Mail-Austausch mit einer Partnerorganisation oder Dienstanbieter zu übernehmen. Die Connectors erzwingen Verschlüsselung über Transport Layer Security (TLS) sowie zulassen Einschränkungen auf Domänennamen oder IP-Adresse ranges Ihre Partner senden e-Mails aus.  <br/> |[Wie Exchange Online mithilfe von TLS E-Mail-Verbindungen in Office 365 sichert](https://technet.microsoft.com/en-us/library/mt163898.aspx) <br/> [Configure mail flow using connectors in Office 365](https://technet.microsoft.com/en-us/library/ms.exch.eac.connectorselection%28v=exchg.150%29.aspx) <br/> [Remotedomänen in Exchange Online](https://technet.microsoft.com/en-us/library/jj966211%28v=exchg.150%29.aspx) <br/> [Connector für die sichere Nachrichtenübermittlung mit einer Partnerorganisation einrichten](https://technet.microsoft.com/en-us/library/dn751021%28v=exchg.150%29.aspx) <br/> [Bewährte Methoden für die Nachrichtenübermittlung für Exchange Online und Office 365 (Übersicht)](https://technet.microsoft.com/en-us/library/0e6cd9d5-ad3e-418a-8ea9-3bf33332c491%28v=exchg.150%29) <br/> |
   
## <a name="sharepoint-online-and-onedrive-for-business-collaboration-options"></a>SharePoint Online und OneDrive for Business Optionen für die Zusammenarbeit

|**Gemeinsames Nutzen von Zielen**|**Administrative Aktion**|**Gewusst wie-Informationen**|
|:-----|:-----|:-----|
|Freigeben von Websites und Dokumenten für externe Benutzer  <br/> |Administratoren Konfigurieren der Freigabe an den Mandanten oder Websitesammlungsebene für Microsoft-Konto authentifiziert, Arbeit oder Schule berücksichtigt authentifizierte oder Gast Konten  <br/> |
  [Verwalten der externen Freigabe für Ihre SharePoint-Online-Umgebung](https://support.office.com/en-US/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85?ui=en-US&amp;rs=en-US&amp;ad=US) <br/> [Eingeschränkte Domänen Freigabe in Office 365 SharePoint Online und OneDrive für Unternehmen](https://support.office.com/en-US/article/Restricted-Domains-Sharing-in-Office-365-SharePoint-Online-and-OneDrive-for-Business-5d7589cd-0997-4a00-a2ba-2320ec49c4e9) <br/> [Verwenden Sie SharePoint Online als extranet Lösung Business-to-Business (B2B)](https://support.office.com/article/7b087413-165a-4e94-8871-4393e0b9c037) <br/> |
|Nachverfolgen und Steuern des externe Freigabe für Endbenutzer  <br/> |OneDrive für Unternehmen Dateibesitzer und SharePoint Online Endbenutzer Website und Freigabe von Dokumenten zu konfigurieren sowie Benachrichtigungen zum Nachverfolgen Freigabe herstellen  <br/> |[Konfigurieren von Benachrichtigungen für externe Freigabe für OneDrive für Unternehmen](https://support.office.com/en-US/article/Configure-notifications-for-external-sharing-for-OneDrive-for-Business-b640c693-f170-4227-b8c1-b0a7e0fa876b) <br/> [Freigeben von SharePoint-Dateien oder Ordner in Office 365](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) <br/> |
   
## <a name="skype-for-business-collaboration-options"></a>Skype für Optionen für die Zusammenarbeit

|**Freigabeziel**|**Administrative Aktion**|**Gewusst wie-Informationen**|
|:-----|:-----|:-----|
|Skype für Online Business - Instant Messaging, Anrufe und Anwesenheit mit anderen Skype für Unternehmensbenutzer  <br/> |Administratoren können aktivieren ihrer Skype Business Online Benutzer Sofortnachrichten, Audio-Video-Anrufe tätigen und Anwesenheitsinformationen mit Benutzern in einer anderen Office 365-Mandanten.  <br/> |[Zulassen, dass Benutzer wenden Sie sich an externe Skype für Unternehmensbenutzer](https://support.office.com/article/b414873a-0059-4cd5-aea1-e5d0857dbc94) <br/> |
|Skype für Online Business - Sofortnachrichten, Anrufe und Anwesenheitsinformationen mit Benutzern Skype (Consumer)  <br/> |Administratoren können ihre Skype Business Online Benutzer Sofortnachrichten aktivieren, Anrufe tätigen und Anwesenheitsinformationen mit Benutzern Skype (Consumer).  <br/> |[Können Sie Skype für Unternehmensbenutzer Skype-Kontakte hinzufügen](https://support.office.com/article/08666236-1894-42ae-8846-e49232bbc460) <br/> |
   
## <a name="azure-ad-b2b-collaboration-options"></a>Azure AD B2B Zusammenarbeit-Optionen

|**Freigabeziel**|**Administrative Aktion**|**Gewusst wie-Informationen**|
|:-----|:-----|:-----|
|Zusammenarbeit von Azure AD B2B - durch Hinzufügen von externen Benutzern zu einer Gruppe im Verzeichnis der Organisation von Inhalten  <br/> |Fügen Sie ein globaler Administrator für eine Office 365-Mandanten Personen in ihrem Verzeichnis Teilnahme an einer anderen Office 365-Mandanten einladen kann diese externen Benutzer zu einer Gruppe hinzu, und gewähren Sie Zugriff auf Inhalte, wie SharePoint-Websites und Bibliotheken für die Gruppe.  <br/> |[Was ist Azure AD B2B Zusammenarbeit Preview?](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b) <br/> [Azure AD-B2B: Neue Updates erleichtern Cross-Business Zusammenarbeitstools während](https://blogs.technet.microsoft.com/enterprisemobility/2017/02/01/azure-ad-b2b-new-updates-make-cross-business-collab-easy/) <br/> [Externe Freigabe von Office 365 und Azure Active Directory B2B Zusammenarbeit](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-o365-external-user) <br/> [Azure Active Directory B2B Zusammenarbeit API und Anpassung](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-api) <br/> [Azure AD und Identity anzeigen: Azure AD-B2B für die Zusammenarbeit (Business, Business](https://channel9.msdn.com/Series/Azure-AD-Identity/AzureADB2B) <br/> |
   
## <a name="office-365-collaboration-options"></a>Optionen für die Zusammenarbeit von Office 365

|**Freigabeziel**|**Administrative Aktion**|**Gewusst wie-Informationen**|
|:-----|:-----|:-----|
|Office 365-Gruppen - E-Mail, Kalender, OneNote und gemeinsam genutzte Dateien an einem zentralen Ort  <br/> |Gruppen werden in Essentials Business, Business Premium, Schulung und die Pläne Enterprise E1, E3 und E5 unterstützt. Personen in einer Office 365-Mandanten können erstellen Sie eine Gruppe und einladen von Personen in einer anderen Office 365-Mandanten als Gastbenutzer. Gilt für Dynamics CRM sowie ein.  <br/> |[Informieren Sie sich über Office 365-Gruppen](https://support.office.com/article/b565caa1-5c40-40ef-9915-60fdb2d97fa2) <br/> [Gast Access in Office 365-Gruppen](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6) <br/> [Bereitstellen von Office 365-Gruppen](https://technet.microsoft.com/en-us/library/dn896591.aspx) <br/> |
   
## <a name="yammer-collaboration-options"></a>Yammer-Optionen für die Zusammenarbeit

|**Freigabeziel**|**Administrative Aktion**|**Gewusst wie-Informationen**|
|:-----|:-----|:-----|
|Yammer - Zusammenarbeit werden durch eine Enterprise social-Mittel  <br/> |Es sei denn, durch den ein Yammer-Administrator die Möglichkeit zum Erstellen von externer Gruppen deaktiviert ist, können Benutzer externe Gruppen für die Zusammenarbeit in Yammer über Unterhaltungen, die Möglichkeit, like und führen die Beiträge, Dateien freigeben und online chat erstellen.  <br/> |[Erstellen und Verwalten von externen Gruppen in Yammer](https://support.office.com/article/9ccd15ce-0efc-4dc1-81bc-4a424ab6f92a) <br/> |
   
## <a name="teams-collaboration-options"></a>Optionen für die Zusammenarbeit von Teams

|**Freigabeziel**|**Administrative Aktion**|**Gewusst wie-Informationen**|
|:-----|:-----|:-----|
|Zusammenarbeit in Teams mit Benutzern außerhalb des Unternehmens  <br/> |Ein globaler Administrator für die Office 365-Mandanten einladen muss externen Zusammenarbeit im Team aktivieren. Globale Administratoren und Team Besitzer werden nun jede Person mit einer e-Mail-Adresse für die Zusammenarbeit im Team einladen können.  <br/> Administratoren können auch verwalten und zum Bearbeiten von Gäste in ihre Mandanten bereits vorhanden.  <br/> |[Gastzugriff erlauben](https://docs.microsoft.com/en-us/microsoftteams/teams-dependencies) <br/> [Aktivieren Sie oder Deaktivieren der Gastzugriff, in Teams](https://docs.microsoft.com/en-us/microsoftteams/set-up-guests) <br/> [Verwenden von PowerShell zum Steuerelement Gast Access](https://docs.microsoft.com/en-us/microsoftteams/guest-access-powershell) <br/> [Gast Access Prüfliste](https://docs.microsoft.com/en-us/microsoftteams/guest-access-checklist) <br/> [Anzeigen von Gastbenutzern](https://docs.microsoft.com/en-us/microsoftteams/view-guests) <br/> [Gast Benutzerinformationen bearbeiten](https://docs.microsoft.com/en-us/microsoftteams/edit-guests-information) <br/> |
|Team Besitzer können einladen und Zusammenarbeit Gäste in ihren Teams verwalten.  <br/> |Team Besitzer enthalten zusätzliche Steuerelemente in ihren Teams Gäste möglich:  <br/> |[Hinzufügen von Gästen](https://support.office.com/en-us/article/teams-and-channels-df38ae23-8f85-46d3-b071-cb11b9de5499?ui=en-US&amp;rs=en-US&amp;ad=US#bkmk_addingguests&amp;ID0EAABAAA=Add_guests) <br/> [Einem Team Gastsystem hinzufügen](https://docs.microsoft.com/en-us/microsoftteams/add-guests) <br/> [Verwalten des Zugriffs von Gast in Teams](https://docs.microsoft.com/en-us/microsoftteams/manage-guests) <br/> [Anzeigen Sie, die in einem Team oder in einem Kanal wird](https://support.office.com/en-us/article/see-who-s-on-a-team-or-in-a-channel-5c6be9be-9c45-4a0f-a1a0-f332b23cb6b7?ui=en-US&amp;rs=en-US&amp;ad=US) <br/> |
|Gäste aus anderen Mandanten mit anderen Mitarbeitern zusammenarbeiten und Teams Inhalt angezeigt  <br/> |Keine.  <br/> |[Die Access-Erfahrung Gast](https://docs.microsoft.com/en-us/microsoftteams/guest-experience) <br/> |
   
## <a name="points-to-be-aware-of-about-office-365-inter-tenant-collaboration"></a>Verweist auf Informationen zu Office 365 zwischen Mandanten Zusammenarbeit Beachten

### <a name="sharing-of-user-accounts-licenses-subscriptions-and-storage"></a>Freigabe von Benutzerkonten, Lizenzen, Abonnements und Speicher

Jede Organisation verwaltet einen eigenen Benutzerkonten, Identitäten, Sicherheitsgruppen, Abonnements, Lizenzen und Speicher. Personen verwenden Features zur Zusammenarbeit in Office 365 zusammen mit der Freigabe von Richtlinien und Sicherheitseinstellungen für den Zugriff auf die benötigten Informationen und gleichzeitig die Kontrolle von Unternehmensressourcen.
  
- **Von Benutzerkonten:** Konten nicht gemeinsam genutzt werden und Konten können nicht zwischen den Mandanten oder Partitionen in der lokalen Active Directory-Verzeichnisdienste dupliziert werden. 
    
- **Lizenzen &amp; Abonnements:** In Office 365 lizenziert Pläne Lizenzieren von (auch gewählte SKUs oder Office 365-Pläne) gewähren des Benutzerzugriffs auf Office 365-Dienste, die für diese Pläne definiert sind. 
    
- **Speicher:** In Office 365-Pläne sind softwarebeschränkungen und-Grenzen für SharePoint Online getrennt vom Speichergrenzwerte verwaltet. Speichergrenzwerte für Postfächer sind eingerichtet und verwaltet mithilfe von Exchange Online. In beiden Fällen kann nicht Speicher cross-Mandanten gemeinsam genutzt werden. 
    
### <a name="can-we-share-domain-namespaces-across-office-365-tenants"></a>Können wir Domänen-Namespaces in Office 365-Mandanten gemeinsam?

Nein. Vanity-Domänen wie fabrikam.com oder tailspintoys.com werden nur verknüpft ist und zur Zeit mit einem Mandanten verwendet. Jeder Mandant muss über einen eigenen Namespace verfügen. UPN, SMTP und SIP-Namespaces werden nicht konstant freigegeben.
  
### <a name="what-about-hybrid-components-and-office-365-inter-tenant-collaboration"></a>Was geschieht mit Hybrid-Komponenten und Office 365 zwischen Mandanten Zusammenarbeit?

Lokale hybride Komponenten, wie ein Exchange-Organisation und Azure Active Directory verbinden, können nicht auf mehrere Mandanten aufgeteilt werden.
  

