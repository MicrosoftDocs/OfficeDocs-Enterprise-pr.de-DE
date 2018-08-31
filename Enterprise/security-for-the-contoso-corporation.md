---
title: Sicherheit für die Contoso Corporation
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 8f6f9894-5394-4110-8b0a-b8765028c10b
description: 'Zusammenfassung: Erfahren Sie, wie Contoso seine Sicherheitsanforderungen bestimmten Features in den Cloudangeboten von Microsoft zuordnete und einen Weg zur Bereitschaft für Cloudsicherheit ermittelte.'
ms.openlocfilehash: 722c01995c95c36b9975b0682858c38063f79d2c
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914830"
---
# <a name="security-for-the-contoso-corporation"></a>Sicherheit für die Contoso Corporation

 **Zusammenfassung:** Erfahren Sie, wie Contoso seine Sicherheitsanforderungen bestimmten Features in den Cloudangeboten von Microsoft zuordnete und einen Weg zur Bereitschaft für Cloudsicherheit ermittelte.
  
Contoso nimmt die Sicherheit und den Schutz seiner Informationen sehr ernst. Für die Umwandlung seiner IT-Infrastruktur in eine cloudeinschließende Infrastruktur hat sich Contoso vergewissert, dass seine lokalen Sicherheitsanforderungen in Microsofts Cloudangeboten unterstützt werden und implementiert sind.
  
## <a name="contosos-security-requirements-in-the-cloud"></a>Contosos Sicherheitsanforderungen in der Cloud

Nachfolgend finden Sie die Sicherheitsanforderungen von Contoso in der Cloud:

  
- Strenge Authentifizierung bei Cloudressourcen

    
    Zugriff auf Cloudressourcen muss authentifiziert werden, und dafür sollte nach Möglichkeit mehrstufige Authentifizierung verwendet werden.

    
- Verschlüsselung für Datenverkehr über das Internet

    
    Daten, die über das Internet gesendet werden, dürfen nicht das Nur-Text-Format aufweisen. Verwenden Sie immer HTTPS-Verbindungen, IPsec oder andere End-to-End-Datenverschlüsselungsmethoden.
    
- Verschlüsselung für Daten, die in der Cloud gespeichert sind

    
    Alle Daten, die auf Datenträgern oder an anderer Stelle in der Cloud gespeichert sind, müssen in verschlüsselter Form vorliegen.

    
- Zugriffssteuerungslisten für Zugriff mit geringsten Rechten

    
    Kontoberechtigungen für Zugriff auf Ressourcen in der Cloud und die zugehörigen Ausführungsrechte müssen den Richtlinien der geringsten Rechte entsprechen.

    
## <a name="contosos-data-sensitivity-classification"></a>Contosos Klassifizierung der Vertraulichkeit von Daten

Anhand der Informationen aus Microsofts Data Classification Toolkit (Toolkit zur Datenklassifizierung) [Data Classification Toolkit](https://msdn.microsoft.com/library/hh204743.aspx) hat Contoso seine Daten analysiert und die folgenden Stufen festgelegt.
  
|**Stufe 1: Geringer Geschäftswert**|**Stufe 2: Mittlerer Geschäftswert**|**Stufe 3: Hoher Geschäftswert**|
|:-----|:-----|:-----|
|Daten sind verschlüsselt und nur für authentifizierte Benutzer verfügbar  <br/> Dies gilt für alle Daten, die lokal und in cloudbasierten Speichern und Arbeitslasten gespeichert sind, z. B. Office 365. Daten werden verschlüsselt, während sie sich im Dienst und im Übergang zwischen dem Dienst und Clientgeräten befinden.  <br/> Beispiele für die Daten der Stufe 1 sind normale Geschäftskommunikation (E-Mail) und Dateien für Mitarbeiter in der Verwaltung, im Vertrieb oder im Kundendienst.
  <br/> |Stufe 1 plus strenger Authentifizierung und Schutz vor Datenverlust  <br/> Eine starke Authentifizierung umfasst eine mehrstufige Authentifizierung mit SMS-Validierung. Durch eine Verhinderung von Datenverlust wird sichergestellt, dass vertrauliche oder kritische Informationen das lokale Netzwerk nicht verlassen.  <br/> Beispiele für Daten der Stufe 2 sind Finanz- und rechtliche Informationen sowie Forschungs- und Entwicklungsdaten für neue Produkte.
  <br/> |Stufe 2 plus höchstmöglicher Verschlüsselung, Authentifizierung und Überwachung  <br/> Die höchstmögliche, den regionalen Regelungen entsprechende Verschlüsselung für gespeicherte Daten oder Daten in der Cloud kombiniert mit mehrstufiger Authentifizierung über Smartcards und präzise Überwachung und Benachrichtigung.  <br/> Beispiele für Daten der Stufe 3 sind personenbezogene Kunden- und Partnerdaten sowie technische Produktspezifikationen und proprietäre Fertigungsverfahren.
  <br/> |
   
## <a name="mapping-microsoft-cloud-offerings-and-features-to-contosos-data-levels"></a>Zuordnung von Microsoft-Cloudangeboten und -Features zu Contosos Datenstufen

Die folgende Tabelle zeigt die Zuordnung der Datenstufen von Contoso zu Features in den Cloudangeboten von Microsoft:
  
||**SaaS**|**Azure PaaS**|**Azure IaaS**|
|:-----|:-----|:-----|:-----|
|Stufe 1: Geringer Geschäftswert
  <br/> | HTTPS für alle Verbindungen <br/>  Verschlüsselung im Ruhezustand <br/> | Nur HTTPS-Verbindungen zulässig <br/>  Dateien verschlüsseln, die in Azure gespeichert sind
 <br/> | HTTPS oder IPsec für Serverzugriff erfordern <br/>  Azure Disk Encryption
 <br/> |
|Stufe 2: Mittlerer Geschäftswert
  <br/> | Mehrstufige Azure AD-Authentifizierung (MFA) mit SMS
 <br/> | Azure Key Vault für Verschlüsselungsschlüssel verwenden <br/>  Azure AD-MFA mit SMS
 <br/> | MFA (Multi-Factor Authentication) mit SMS
 <br/> |
|Stufe 3: Hoher Geschäftswert
  <br/> | Azure RMS (Rights Management Service) <br/>  Azure AD-MFA mit Smartcards <br/>  Bedingter Intune-Zugriff
 <br/> | Azure RMS <br/>  Azure AD-MFA mit Smartcards <br/> | MFA mit Smartcards
 <br/> |
   
## <a name="contosos-information-policies"></a>Contosos Datenrichtlinien

In der folgenden Tabelle sind die Informationsrichtlinien von Contoso aufgeführt.
  
||**Access**|**Datenaufbewahrung**|**Schutz von Daten**|
|:-----|:-----|:-----|:-----|
|Stufe 1: Geringer Geschäftswert
  <br/> | Zugriff auf alles zulassen
 <br/> |6 Monate  <br/> |Verschlüsselung verwenden  <br/> |
|Stufe 2: Mittlerer Geschäftswert
  <br/> | Zugriff für Mitarbeiter, Subunternehmer und Partner von Contoso zulassen <br/>  MFA, TLS und MAM verwenden
 <br/> |2 Jahre  <br/> |Hashwerte für Datenintegrität verwenden
  <br/> |
|Stufe 3: Hoher Geschäftswert
  <br/> | Zugriff für Manager und Führungskräfte in Technik und Fertigung zulassen <br/>  RMS nur mit verwalteten Netzwerkgeräten
 <br/> |7 Jahre
  <br/> |Digitale Signaturen für Nachweisbarkeit (Unleugbarkeit) verwenden
  <br/> |
   
## <a name="contosos-path-to-cloud-security-readiness"></a>Contosos Weg zur Cloudsicherheit

Contoso verwendet die folgenden Schritte, um seine Sicherheit für die Microsoft-Cloud vorzubereiten:
  
1. Optimieren der Administratorkonten für die Cloud
    
    Bei Contoso wurde eine umfassende Überprüfung der vorhandenen Windows Server AD-Administratorkonten vorgenommen und eine Reihe von Cloud-Administratorkonten und -gruppen eingerichtet.

    
2. Ausführen der Analyse für Datenklassifizierung in drei Stufen
    
    Contoso hat eine sorgfältige Überprüfung vorgenommen und die drei Stufen bestimmt, anhand denen die Microsoft-Features für Cloudangebote festgelegt wurden, mit denen Contosos wertvollste Daten zu schützen sind.
    
3. Bestimmen von Zugriffs-, Aufbewahrungs- und Datensicherungsrichtlinien für Datenstufen
    
    Auf Basis der Datenstufen hat Contoso ausführliche Anforderungen festgelegt, die dazu verwendet werden, zukünftige IT-Arbeitslasten zu qualifizieren, die in die Cloud verschoben werden.

    
## <a name="contosos-use-of-office-365-security-best-practices"></a>Verwenden von bewährten Methoden für die Sicherheit in Office 365 bei Contoso

Gemäß den bewährten Methoden für die Sicherheit in Office 365 haben Sicherheitsadministratoren und die IT-Abteilung bei Contoso Folgendes bereitgestellt:
  
- **Dedizierte globale Administratorkonten mit sicheren Kennwörtern**
    
    Statt die globale Administratorrolle Standardbenutzerkonten zuzuweisen, wurden bei Contoso drei, dedizierte globale Administratorkonten mit sicheren Kennwörtern erstellt. Das Anmelden mit einem globalen Administratorkonto wird nur für bestimmte Verwaltungsaufgaben ausgeführt, und die Kennwörter sind nur festgelegten Mitarbeitern bekannt. Die Contoso-Sicherheitsadministratoren haben die Administratorrollen entsprechend der Position und dem Verantwortungsbereich des IT-Mitarbeiters den jeweiligen Konten zugewiesen.
    
    Weitere Informationen finden Sie unter [Informationen zu Office 365-Administratorrollen](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d).
    
- **Mehrstufige Authentifizierung für wichtige Benutzerkonten**
    
    Bei der mehrstufigen Authentifizierung wird eine zusätzliche Sicherheitsstufe zum Anmeldevorgang hinzugefügt, indem Benutzer aufgefordert werden, Ihre Identität nach korrekter Eingabe des Kennworts per Telefonanruf, Textnachricht oder App-Benachrichtigung auf Ihrem Smartphone zu bestätigen. Mit der mehrstufigen Authentifizierung sind Office 365-Benutzerkonten vor nicht autorisierter Anmeldung geschützt, selbst wenn ein Kontokennwort kompromittiert wird.
    
  - Zum Schutz vor einer Kompromittierung des Office 365-Abonnements wird bei Contoso die mehrstufige Authentifizierung für alle drei globale Administratorkonten aktiviert.
    
  - Zum Schutz vor Phishingangriffen, bei denen die Anmeldeinformationen einer vertrauenswürdigen Person in der Organisation kompromittiert und böswillige E-Mails gesendet werden, wurde bei Contoso die mehrstufige Authentifizierung für alle Benutzerkonten für Manager aktiviert, einschließlich Führungskräfte.
    
    Weitere Informationen finden Sie unter [Planen der mehrstufigen Authentifizierung für Office 365-Bereitstellungen](https://support.office.com/article/Plan-for-multifactor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba).
    
- **Advanced Security Management (ASM)**
    
    ASM verwendet konfigurierte Richtlinien für die Überwachung abweichender Aktivitäten. Contoso-Sicherheitsadministratoren richten Benachrichtigungen mit ASM ein, sodass IT-Administratoren bei anomalen oder riskanten Benutzeraktivitäten benachrichtigt werden, z. B. beim Download von großen Datenmengen, mehreren nicht erfolgreichen Anmeldeversuchen oder Anmeldungen von unbekannten oder gefährlichen IP-Adressen.
    
    Weitere Informationen finden Sie unter [Übersicht über Advanced Security Management in Office 365 ](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).
    
- **Sicherer E-Mail-Fluss und Postfachüberwachungsprotokollierung**
    
    Zum Schutz vor unbekannter Malware, Viren und böswilligen URLs, die per E-Mail gesendet werden, verwenden die Contoso-Sicherheitsexperten Exchange Online Protection und Advanced Threat Protection (ATP). Bei Contoso wurde außerdem die Postfachüberwachungsprotokollierung aktiviert, um zu bestimmen, wer sich bei Benutzerpostfächern angemeldet und Nachrichten gesendet hat, sowie andere Aktivitäten zu überwachen, die vom Benutzerpostfach, einem delegierten Benutzer oder einem Administrator durchgeführt wurden.
    
    Weitere Informationen finden Sie unter: 
    
  - [Antispamschutz für Office 365-E-Mails](https://support.office.com/article/Office-365-Email-AntiSpam-Protection-6a601501-a6a8-4559-b2e7-56b59c96a586)
    
  - [Advanced Threat Protection für sichere Anlagen und sichere Links](https://technet.microsoft.com/library/mt148491.aspx)
    
  - [Aktivieren der Postfachüberwachung in Office 365](https://go.microsoft.com/fwlink/p/?LinkID=626109)
    
- **Verhinderung von Datenverlust**
    
    Bei Contoso wurden vertrauliche Daten identifiziert und Richtlinien zur Verhinderung von Datenverlust für Exchange Online, SharePoint Online und OneDrive konfiguriert, um zu verhindern, dass Benutzer versehentlich oder absichtlich die Daten freigeben können. 
    
    Weitere Informationen finden Sie unter [Übersicht über die Richtlinien zur Verhinderung von Datenverlust](https://support.office.com/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e).
    
## <a name="see-also"></a>Siehe auch

[Contoso in der Microsoft-Cloud](contoso-in-the-microsoft-cloud.md)
  
[Ressourcen zur Cloud-IT-Architektur von Microsoft](microsoft-cloud-it-architecture-resources.md)

[Enterprise-Cloud-Roadmap von Microsoft: Ressourcen für IT-Entscheidungsträger](https://sway.com/FJ2xsyWtkJc2taRD)
  
[Bewährte Methoden für die Sicherheit in Office 365](https://support.office.com/article/Security-best-practices-for-Office-365-9295e396-e53d-49b9-ae9b-0b5828cdedc3)




