---
title: Sichern von SharePoint Online-Websites und -Dateien
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Strat_O365_Enterprise
- Ent_Architecture
ms.assetid: 1d51bd87-17bf-457c-b698-61821de3afa0
description: "Zusammenfassung: Konfigurationsempfehlungen für den Schutz von Dateien in SharePoint Online und Office 365."
ms.openlocfilehash: a8ba632d9bc24e272a649f5790824323f889bdc0
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2018
---
# <a name="secure-sharepoint-online-sites-and-files"></a>Sichern von SharePoint Online-Websites und -Dateien

 **Zusammenfassung:** Konfigurationsempfehlungen für den Schutz von Dateien in SharePoint Online und Office 365.
  
Dieser Artikel enthält Empfehlungen, wie Sie SharePoint Online-Teamwebsites und den Dateischutz so konfigurieren, dass sowohl Sicherheit als auch einfache Zusammenarbeit sichergestellt sind. In diesem Artikel werden vier verschiedene Konfigurationen definiert, beginnend mit einer öffentlichen Website in Ihrer Organisation mit sehr offenen Freigaberichtlinien. Mit jeder weiteren Konfiguration wird der Schutz jeweils erheblich verbessert, gleichzeitig wird aber auch der Zugriff und die Zusammenarbeit auf die für die Benutzer relevanten Ressourcen eingeschränkt. Verwenden Sie diese Empfehlungen als Ausgangspunkt, und passen Sie die Konfigurationen entsprechend den Bedürfnissen Ihrer Organisation an. 
  
Die Konfigurationen in diesem Artikel sind auf die Microsoft-Empfehlungen für drei Schutzebenen für Daten, Identitäten und Geräte ausgerichtet:
  
- Basisschutz
    
- Schutz sensibler Daten
    
- Schutz streng vertraulicher Daten
    
Weitere Informationen zu diesen Ebenen und Funktionen, die für jede Ebene empfohlen werden, finden Sie in den folgenden Ressourcen. 
  
- [Identität- und Geräteschutz für Office 365](microsoft-cloud-it-architecture-resources.md#BKMK_O365IDP)
    
- [Lösungen zum Schutz von Dateien in Office 365](microsoft-cloud-it-architecture-resources.md#BKMK_O365fileprotect)
    
## <a name="capability-overview"></a>Funktionsübersicht

Empfehlungen für SharePoint Online-Teamwebsites greifen auf eine Vielzahl von Office 365-Funktionen zurück. Für streng vertrauliche Websites wird Azure Information Protection empfohlen. Dieser Dienst ist in Enterprise Mobility + Security (EMS) enthalten. 
  
Die folgende Abbildung zeigt die empfohlenen Konfigurationen für vier SharePoint Online-Teamwebsites.
  
![Empfohlene Konfiguration für die SharePoint-Websites](images/ad0dcd70-f6f5-465c-8d16-1889481ca07a.png)
  
Erläuterung der Abbildung:
  
- Basisschutz umfasst zwei Optionen für SharePoint Online-Teamwebsites: eine öffentliche Website und eine private Website. Öffentliche Websites können von allen Benutzern in einer Organisation ermittelt werden, und alle haben Zugriff darauf. Private Websites können nur von Mitgliedern der Website ermittelt werden, und nur diese haben Zugriff darauf. Beide Websitekonfigurationen lassen die Freigabe für Personen außerhalb der Gruppe zu. 
    
- Websites mit der Schutzebene „Sensibel“ und „Streng vertraulich“ sind private Websites, bei denen der Zugriff auf Mitglieder bestimmter Gruppen beschränkt ist.
    
- Office 365-Bezeichnungen dienen zum Klassifizieren von Daten mit der benötigten Schutzebene. Jede der SharePoint Online-Teamwebsites ist so konfiguriert, dass Dateien in Dokumentbibliotheken automatisch mit einer Standardbezeichnung für die Website bezeichnet werden. Entsprechend den vier Websitekonfigurationen sind die Bezeichnungen in diesem Beispiel „Intern öffentlich“, „Privat“, „Sensibel“ und „Streng vertraulich“. Benutzer können die Bezeichnungen ändern, aber diese Konfiguration stellt sicher, dass alle Dateien eine Standardbezeichnung erhalten.
    
- Richtlinien zur Verhinderung von Datenverlust sind für die Office 365-Bezeichnungen „Sensibel“ und „Streng vertraulich“ konfiguriert, um zu warnen oder Benutzer daran zu hindern, diese Dateitypen außerhalb der Organisation zu senden.
    
- Für Websites, die mit streng vertraulichem Schutz konfiguriert sind, verschlüsselt und erteilt Azure Information Protection  Berechtigungen für Dateien.
    
## <a name="tenant-wide-settings-for-sharepoint-online-and-onedrive-for-business"></a>Mandantenweite Einstellungen für SharePoint Online und OneDrive for Business

SharePoint Online und OneDrive for Business enthalten mandantenweite Einstellungen, die alle Websites und Benutzer betreffen. Einige dieser Einstellungen können auch auf Websiteebene angepasst werden, um sie restriktiver (aber nicht weniger restriktiv) zu machen. In diesem Abschnitt werden mandantenweite Einstellungen beschrieben, die sich auf Sicherheit und Zusammenarbeit auswirken. 
  
### <a name="sharing"></a>Freigabe

Für diese Lösung empfehlen wir die folgenden mandantenweiten Einstellungen:
  
- Beibehalten der Standardfreigaberichtlinie, die alle Freigabetypen für alle Arten von Konten zulässt, einschließlich anonymer Freigabe.
    
- Festlegen eines Ablaufdatums für anonyme Links, falls gewünscht.
    
- Ändern des Standardlinktyps für die Freigabe in „Intern“. Dies verhindert versehentliche Datenlecks außerhalb Ihrer Organisation.
    
Das Zulassen der externe Freigabe mag zwar kontraintuitiv erscheinen, dennoch bietet dieser Ansatz mehr Kontrolle über die Dateifreigabe als das Senden von Dateien per E-Mail. SharePoint Online und Outlook arbeiten zusammen, um eine sichere Zusammenarbeit an Dateien zu ermöglichen. 
  
- Standardmäßig gibt Outlook einen Link zu einer Datei frei, anstatt die Datei per E-Mail zu senden. 
    
- SharePoint Online und OneDrive for Business erleichtern das Freigeben von Links zu Dateien für Mitwirkende sowohl innerhalb als auch außerhalb Ihrer Organisation.
    
Außerdem stehen Ihnen Kontrollfunktionen zur Verfügung, mit denen Sie die externe Freigabe steuern können. Sie verfügen beispielsweise über folgende Möglichkeiten:
  
- Deaktivieren eines anonymen Gastlinks
    
- Widerrufen des Benutzerzugriffs auf eine Website
    
- Anzeigen, wer Zugriff auf eine bestimmte Website oder ein Dokument hat
    
- Festlegen eines Ablaufdatums für anonyme Freigabelinks (Mandanteneinstellung)
    
- Einschränken, wer außerhalb Ihrer Organisation freigeben kann (Mandanteneinstellung)
    
### <a name="use-external-sharing-together-with-data-loss-prevention-dlp"></a>Verwenden von externer Freigabe zusammen mit Verhinderung von Datenverlust (DLP)

Wenn Sie die externe Freigabe nicht zulassen, stehen Benutzern mit einer Geschäftsanforderung alternative Tools und Methoden zur Verfügung. Microsoft empfiehlt, die externe Freigabe mit DLP-Richtlinien zu kombinieren, um sensible und streng vertrauliche Dateien zu schützen.
  
### <a name="device-access-settings"></a>Gerätezugriffseinstellungen

Mithilfe von Gerätezugriffseinstellungen für SharePoint Online und OneDrive for Business können Sie bestimmen, ob der Zugriff auf den Browser beschränkt ist (die Dateien können nicht heruntergeladen werden) oder ob der Zugriff ganz blockiert ist. Diese Einstellungen stehen derzeit in der First Release zur Verfügung und gelten mandantenweit. In Kürze wird die Möglichkeit verfügbar sein, Gerätezugriffsrichtlinien auf Websiteebene zu konfigurieren. Für diese Lösung wird empfohlen, keine mandantenweit geltenden Gerätezugriffseinstellungen zu verwenden.
  
Informationen zum Verwenden von Gerätezugriffseinstellungen in der First Release finden Sie hier: [Einrichten der Standard- oder First Release-Optionen in Office 365]((https://support.office.com/article/Set-up-the-Standard-or-First-Release-options-in-Office-365-3B3ADFA4-1777-4FF0-B606-FB8732101F47)).
  
### <a name="onedrive-for-business"></a>OneDrive for Business

Besuchen Sie diese Einstellungen, um zu entscheiden, ob Sie die Standardeinstellungen für OneDrive for Business-Websites ändern möchten. Aktuell werden die Freigabe- und Gerätezugriffseinstellungen aus dem SharePoint Online Admin Center dupliziert und gelten für beide Umgebungen.
  
## <a name="sharepoint-team-site-configuration"></a>Konfiguration von SharePoint-Teamwebsites

In der folgenden Tabelle wird die Konfiguration für jede der zuvor in diesem Artikel beschriebenen Teamwebsites zusammengefasst. Verwenden Sie diese Konfigurationen als Ausgangsempfehlungen, und passen Sie die Websitetypen und Konfigurationen entsprechend den Bedürfnissen Ihrer Organisation an. Nicht jede Organisation benötigt jeden Websitetyp. Nur eine kleine Anzahl von Organisationen erfordert die Schutzebene „streng vertraulich“.
  
||||||
|:-----|:-----|:-----|:-----|:-----|
||**Basisschutz 1** <br/> |**Basisschutz 2** <br/> |**Schutz sensibler Daten** <br/> |**Streng vertraulich** <br/> |
|Beschreibung  <br/> |Offene Ermittlung und Zusammenarbeit innerhalb der Organisation.  <br/> |Private Website und Gruppe, Freigabe außerhalb der Gruppe zulässig.  <br/> |Isolierte Website, für die Zugriffsebenen durch Mitgliedschaft in bestimmten Gruppen definiert sind. Die Freigabe ist nur für Mitglieder dieser Website zulässig. Die DLP warnt Benutzer bei dem Versuch, Dateien außerhalb der Organisation zu senden.  <br/> |Isolierte Website + Dateiverschlüsselung und Berechtigungen mit Azure Information Protection. Die DLP verhindert, dass Benutzer Dateien außerhalb der Organisation senden.  <br/> |
|Private oder öffentliche Teamwebsite  <br/> |Öffentlich  <br/> |Privat  <br/> |Privat  <br/> |Privat  <br/> |
|Wer hat Zugriff?  <br/> |Alle Benutzer in der Organisation, einschließlich B2B-Benutzer und Gäste.  <br/> |Nur Mitglieder der Website. Andere Personen können Zugriff anfordern.  <br/> |Nur Mitglieder der Website. Andere Personen können Zugriff anfordern.  <br/> |Nur Mitglieder. Andere Personen können keinen Zugriff anfordern.  <br/> |
|Freigabekontrollen auf Websiteebene  <br/> |Freigabe für beliebige Personen zulässig. Standardeinstellungen.  <br/> |Freigabe für beliebige Personen zulässig. Standardeinstellungen.  <br/> |Mitglieder können den Zugriff auf die Website nicht freigeben.  <br/> Nichtmitglieder können den Zugriff auf die Website anfordern, aber diese Anforderungen müssen von einem Websiteadministrator bearbeitet werden.  <br/> |Mitglieder können den Zugriff auf die Website nicht freigeben.  <br/> Nichtmitglieder können keinen Zugriff auf die Website oder Inhalte anfordern.  <br/> |
|Gerätezugriffssteuerungen auf Websiteebene  <br/> |Keine zusätzlichen Steuerungen.  <br/> |Keine zusätzlichen Steuerungen.  <br/> |In Kürze sind Steuerungen auf Websiteebene verfügbar, die verhindern, dass Benutzer Dateien auf nicht kompatible oder nicht der Domäne beigetretene Geräte herunterladen. Von allen anderen Geräten aus ist nur Browserzugriff zulässig.  <br/> |In Kürze sind Steuerelemente auf Websiteebene verfügbar, die blockieren, dass Benutzer Dateien auf nicht kompatible oder nicht der Domäne beigetretene Geräte herunterladen.  <br/> |
|Office 365-Bezeichnungen  <br/> |Intern öffentlich  <br/> |Privat  <br/> |Vertraulich  <br/> |Streng vertraulich  <br/> |
|DLP-Richtlinien  <br/> |||Benutzer werden gewarnt, wenn sie Dateien mit der Bezeichnung „Sensibel“ an Empfänger außerhalb der Organisation senden.  <br/> Um die externe Freigabe von sensiblen Datentypen wie z. B. Kreditkartennummern oder anderen persönlichen Daten zu blockieren, können Sie zusätzliche DLP-Richtlinien für diese Datentypen konfigurieren (einschließlich benutzerdefinierter Datentypen, die Sie selbst konfigurieren).  <br/> |Benutzer werden daran gehindert, Dateien mit der Bezeichnung „Streng vertraulich“ an Empfänger außerhalb der Organisation zu senden. Sie können es Benutzern ermöglichen, dies durch Angabe einer Rechtfertigung zu überschreiben, einschließlich der Person, für die sie die Datei freigeben.  <br/> |
|Azure Information Protection  <br/> ||||Azure Information Protection wird zum automatischen Verschlüsseln von Dateien und zum Erteilen von Berechtigungen für diese verwendet. Dieser Schutz ist mit den Dateien verbunden und bleibt auch dann erhalten, falls sie verloren gehen.  <br/> Office 365 kann keine Dateien lesen, die mit Azure Information Protection verschlüsselt wurden. Darüber hinaus können DLP-Richtlinien nur auf die Metadaten (einschließlich Bezeichnungen) angewendet werden, aber nicht auf den Inhalt dieser Dateien (z. B. Kreditkartennummern in Dateien).  <br/> |
   
Die Schritte zum Bereitstellen der vier verschiedenen Typen von SharePoint Online-Teamwebsites in dieser Lösung finden Sie unter [Bereitstellen von Websites für den Schutz auf drei Ebenen](deploy-sharepoint-online-sites-for-three-tiers-of-protection.md). Die Schritte zur Erstellung einer Entwicklungs-/Testumgebung finden Sie unter [Sichern von SharePoint Online-Websites in einer Entwicklungs-/Testumgebung](secure-sharepoint-online-sites-in-a-dev-test-environment.md). 
  
## <a name="office-365-classification-and-labels"></a>Office 365-Klassifizierung und -Bezeichnungen

Die Verwendung von Office 365-Bezeichnungen wird für Umgebungen mit sensiblen Daten empfohlen. Nachdem Sie Office 365-Bezeichnungen konfiguriert und bereitgestellt haben, haben Sie folgende Möglichkeiten:
  
- Sie können eine Standardbezeichnung auf eine Dokumentbibliothek in einer SharePoint Online-Teamwebsite anwenden, sodass alle Dokumente in dieser Bibliothek mit der Standardbezeichnung versehen werden. 
    
- Sie können Bezeichnungen automatisch auf Inhalt anwenden, wenn er bestimmten Bedingungen entspricht.
    
- Sie können DLP-Richtlinien anwenden, die auf Office 365-Bezeichnungen basieren.
    
- Personen in Ihrer Organisation können eine Bezeichnung manuell auf Inhalte in Outlook im Web, Outlook 2010 und höher, OneDrive for Business, SharePoint Online und Office 365-Gruppen anwenden. Benutzer wissen häufig am besten, mit welcher Art von Inhalten sie arbeiten, sodass sie sie klassifizieren und die entsprechende DLP-Richtlinie anwenden lassen können.
    
![Empfohlene Konfiguration für die SharePoint-Websites](images/7fed0126-ab4a-4480-922c-681970642339.png)
  
Wie dargestellt, umfasst diese Lösung die Erstellung der folgenden Bezeichnungen:
  
- Streng vertraulich
    
- Vertraulich
    
- Privat
    
- Intern öffentlich
    
Die Bezeichnungen sind den empfohlenen Websites in den Abbildungen und Diagrammen weiter oben in diesem Artikel zugeordnet. Diese Lösung empfiehlt die Konfiguration von DLP-Richtlinien, um Informationslecks bei Dateien zu verhindern, die als sensibel oder streng vertraulich klassifiziert sind.
  
Die Schritte zum Konfigurieren von Office 365-Bezeichnungen und DLP-Richtlinien in dieser Lösung finden Sie unter [Schützen von SharePoint Online-Dateien mit Office 365 Etiketten und DLP](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md).
  
## <a name="azure-information-protection"></a>Azure Information Protection

Verwenden Sie Azure Information Protection zum Anwenden von Bezeichnungen und Schutzfunktionen, die die Dateien unabhängig von ihrem Standort begleiten. Für diese Lösung empfehlen wir, eine bereichsbezogene Azure Information Protection-Richtlinie und die Bezeichnung „Streng vertraulich“ zu verwenden, um Dateien, die Schutz der höchsten Ebene benötigen, zu verschlüsseln und Berechtigungen für sie zu erteilen. 
  
Beachten Sie Folgendes: Wenn Azure Information Protection-Verschlüsselung auf Dateien in Office 365 angewendet wird, kann der Dienst den Inhalt dieser Dateien nicht verarbeiten. Gemeinsame Dokumenterstellung, eDiscovery, Suche, Delve und andere Features für die Zusammenarbeit funktionieren nicht. DLP-Richtlinien können nur mit den Metadaten (einschließlich Office 365-Bezeichnungen) funktionieren, aber nicht mit den Inhalten dieser Dateien (wie Kreditkartennummern in Dateien).
  
![Azure Information Protection ist in Azure konfiguriert, und es werden Beschriftungen in der Client-Symbolleiste angezeigt](images/1266a7a0-5078-49ab-bbf1-b0cf41451f62.png)
  
Erläuterung der Abbildung:
  
- Azure Information Protection-Richtlinien und -Bezeichnungen werden im Microsoft Azure-Portal konfiguriert. Es wird empfohlen, eine untergeordnete Bezeichnung einer bereichsbezogenen Azure Information Protection-Richtlinie zu konfigurieren.
    
- Azure Information Protection-Bezeichnungen werden als Symbolleiste **Information Protection** in Office-Anwendungen angezeigt.
    
### <a name="adding-permissions-for-external-users"></a>Hinzufügen von Berechtigungen für externe Benutzer

Es gibt zwei Möglichkeiten, wie Sie externen Benutzern Zugriff auf Dateien gewähren können, die mit Azure Information Protection geschützt sind. In beiden Fällen benötigen die externen Benutzer ein Azure AD-Konto. Wenn externe Benutzer kein Mitglied einer Organisation sind, die Azure Active Directory verwendet, können sie auf dieser Registrierungsseite ein Azure AD-Konto als Einzelperson beantragen: [(https://aka.ms/aip-signup)]((https://aka.ms/aip-signup)).
  
- Hinzufügen von externen Benutzern zu einer Azure AD-Gruppe, die zum Konfigurieren des Schutzes für eine Bezeichnung verwendet wird
    
     Sie müssen zuerst das Konto als B2B-Benutzer in Ihrem Verzeichnis hinzufügen. Das [Zwischenspeichern der Gruppenmitgliedschaft durch Azure Rights Management](https://docs.microsoft.com/information-protection/plan-design/prepare#group-membership-caching-by-azure-rights-management) kann einige Stunden dauern. Bei dieser Methode werden Berechtigungen für alle vorhandenen Dateien erteilt, die mit der Bezeichnung geschützt sind (sogar Dateien, die geschützt wurden, bevor ein Benutzer der Azure AD-Gruppe hinzugefügt wird).
    
- Direktes Hinzufügen von externen Benutzern zum Bezeichnungsschutz
    
     Sie können alle Benutzer aus einer Organisation (z. B. „Fabrikam.com“), eine Azure AD-Gruppe (z. B. eine Finanzgruppe innerhalb einer Organisation) oder einen einzelnen Benutzer hinzufügen. Beispielsweise können Sie ein externes Team von Aufsichtsbeamten zum Schutz für eine Bezeichnung hinzufügen. Bei dieser Methode werden Berechtigungen für Dateien, die mit der Bezeichnung geschützt sind, erst erteilt, nachdem die externe Entität dem Schutz hinzugefügt wurde.
    
### <a name="deploying-and-using-azure-information-protection"></a>Bereitstellen und Verwenden von Azure Information Protection

Die Schritte zum Konfigurieren von Azure Information Protection in dieser Lösung finden Sie unter [Schützen von SharePoint Online-Dateien mit Azure Information Protection](protect-sharepoint-online-files-with-azure-information-protection.md).
  
## <a name="see-also"></a>Weitere Artikel

[Microsoft-Sicherheitsleitfaden für politische Kampagnen, gemeinnützigen Organisationen und andere agile Organisationen](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[Sicherheitslösungen](security-solutions.md)
  
[Cloudakzeptanz und Hybridlösungen](cloud-adoption-and-hybrid-solutions.md)
  
[Sichern von SharePoint Online-Websites in einer Entwicklungs-/Testumgebung](secure-sharepoint-online-sites-in-a-dev-test-environment.md)



