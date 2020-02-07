---
title: Tools zum Verwalten von Office 365-Konten
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: 98ca5b3f-f720-4d8e-91be-fe656548a25a
description: 'In diesem Artikel erfahren Sie, welche Tools für die Verwaltung Ihrer Office 365 Benutzer und wie Sie verwenden können, hängt davon ab, wie Sie Benutzeridentitäten verwalten. '
ms.openlocfilehash: 0cfb1496dd97eb932afc4e90a6d9469289332c2d
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843716"
---
# <a name="tools-to-manage-office-365-accounts"></a>Tools zum Verwalten von Office 365-Konten

Je nach Konfiguration können Sie Office 365 Benutzer auf verschiedene Arten verwalten. Sie können Benutzer im [Microsoft 365 Admin Center](https://admin.microsoft.com), Windows PowerShell, im lokalen Verzeichnis oder im Azure Active Directory-Verwaltungsportal verwalten. Sobald Sie Office 365 erworben haben, können Admin Center und Windows PowerShell zum Verwalten von Konten verwendet werden. Bei der Verwaltung von Cloud-Identitäten verfügt jede Person in Ihrer Organisation über eine separate Benutzer-ID und ein Kennwort für Office 365. Wenn Sie in Ihre lokale Infrastruktur integrieren möchten und Benutzerkonten mit Office 365 synchronisiert werden sollen, können Sie Azure Active Directory Connect verwenden, um die Synchronisierung von Identitäten bereitzustellen und optional eine Kennwortsynchronisierung oder eine vollständige Funktionalität für einmaliges Anmelden
  
## <a name="plan-for-where-and-how-you-will-manage-your-user-accounts"></a>Planen, wo und wie Sie Ihre Benutzerkonten verwalten können

Wo und wie Sie Ihre Benutzerkonten verwalten können, hängt vom Identitätsmodell ab, das Sie für Ihre Office 365 verwenden möchten. Die beiden Gesamt Modelle sind die Cloud-Authentifizierung und die Verbundauthentifizierung.
  
### <a name="cloud-authentication"></a>Cloud-Authentifizierung

- Cloud-Authentifizierung – erstellen und Verwalten von Benutzern im Admin Center können Sie auch Windows PowerShell oder Azure-Active Directory verwenden, um Ihre Benutzer zu verwalten. 
    
- Kennworthash Synchronisierung mit nahtlosem einmaligem Anmelden – die einfachste Möglichkeit zum Aktivieren der Authentifizierung für lokale Verzeichnisobjekte in Azure AD. Mit Password Hash Sync (PHS) synchronisieren Sie Ihre lokalen Active Directory Benutzerkontenobjekte mit Office 365 und verwalten Ihre Benutzer lokal. 
    
- Pass-Through-Authentifizierung mit nahtlosem einmaligem Anmelden – bietet eine einfache Kennwortüberprüfung für Azure AD Authentifizierungsdienste mit einem Software-Agent, der auf einem oder mehreren lokalen Servern läuft, um die Benutzer direkt mit Ihrem lokalen Active zu validieren. Directory. 
    
### <a name="federated-authentication"></a>Verbundauthentifizierung

- Optionen für die Verbundauthentifizierung: in erster Linie für große Unternehmensorganisationen mit komplexeren Authentifizierungsanforderungen werden lokale Verzeichnisobjekte mit Office 365 synchronisiert, und Benutzerkonten werden lokal verwaltet. 
    
- [Drittanbieter Authentifizierung und Identitätsanbieter](about-office-365-identity.md) – lokale Verzeichnisobjekte können mit Office 365 synchronisiert werden, und der Zugriff auf Cloud-Ressourcen wird in erster Linie von einem Drittanbieter-Identitätsanbieter (IDP) verwaltet. 
    
## <a name="managing-accounts"></a>Verwalten von Konten

Bei der Entscheidung, wie Ihre Organisation Konten erstellen und verwalten soll, sollten Sie Folgendes berücksichtigen:
  
- Die Verzeichnis Synchronisierungssoftware muss auf Servern in Ihrer lokalen Umgebung installiert sein, um die Identitäten zwischen Office 365 und dem lokalen Verzeichnis zu verbinden.
    
- Für eine beliebige Verzeichnissynchronisierungsoption, einschließlich SSO-Optionen, müssen ihre lokalen Verzeichnisattribute den Standards entsprechen. Die Besonderheiten der Attribute, die in Ihrem Verzeichnis verwendet werden und welche Bereinigung (falls vorhanden) erforderlich ist, werden in [Prepare to Bereitstellen von Benutzern über die Verzeichnissynchronisierung für Office 365](prepare-for-directory-synchronization.md)beschrieben. Informationen zum Verwenden von IdFix zum Automatisieren der Verzeichnisbereinigung finden Sie unter [herunterladen und Ausführen des Office 365 IdFix-Tools](install-and-run-idfix.md) . 
    
- Planen der Erstellung Office 365 Konten
    
    In der folgenden Tabelle sind die verschiedenen Kontenverwaltungstools aufgeführt.
    
|**Option**|**Hinweise**|
|:-----|:-----|
|Admin Center  <br/> |[Hinzufügen von Benutzern einzeln oder in loser Schüttung zur Office 365-Administratorhilfe](https://support.office.com/article/1970f7d6-03b5-442f-b385-5880b9c256ec) <br/>  Stellt eine einfache Weboberfläche zum Hinzufügen und Ändern von Benutzerkonten bereit.  <br/>  Kann nicht zum Ändern von Benutzern verwendet werden, wenn die Verzeichnissynchronisierung aktiviert ist (Standort-und Lizenzzuweisung können festgelegt werden).  <br/>  Kann nicht mit SSO-Optionen verwendet werden.  <br/> |
|Windows PowerShell  <br/> |[Verwalten von Office 365 mit Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=698471) <br/>  Ermöglicht Ihnen das Hinzufügen von Benutzern in Massen Benutzern mithilfe eines Windows PowerShell Skripts.  <br/>  Kann zum Zuweisen von Standort und Lizenzen zu Konten verwendet werden, unabhängig davon, wie die Konten erstellt werden.  <br/> |
|Massenimport  <br/> |[Gleichzeitiges Hinzufügen mehrerer Benutzer zu Office 365 – Hilfe für Administratoren](add-several-users-at-the-same-time.md) <br/>  Ermöglicht das Importieren einer CSV-Datei zum Hinzufügen einer Gruppe von Benutzern zu Office 365.  <br/>  Kann nicht mit SSO-Optionen verwendet werden.  <br/> |
|Azure Active Directory  <br/> |Sie erhalten eine ﻿kostenlose Version von Azure Active Directory mit Ihrem Office 365-Abonnement. Sie können Funktionen wie das Zurücksetzen von Self-Service-Kennwörtern für Cloud-Benutzer und die Anpassung der Seiten der Anmelde-und Zugriffs Konsole mithilfe der kostenlosen Edition ausführen. Um eine erweiterte Funktionalität zu erhalten, können Sie ein Upgrade auf die Basic Edition oder die Premium Edition durchführen. Die Liste der unterstützten Features finden Sie unter [Azure Active Directory Editions](https://go.microsoft.com/fwlink/p/?LinkId=698465) .  <br/> |
|Verzeichnissynchronisierung  <br/> |[Integrieren Ihrer lokalen Identitäten in Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkID=624168) <br/>  Verwenden Sie für die Verzeichnissynchronisierung mit oder ohne Kennwortsynchronisierung [Azure AD Connect with Express Settings](https://go.microsoft.com/fwlink/p/?LinkID=698537).  <br/>  Verwenden Sie für mehrere Gesamtstrukturen und SSO-Optionen die [benutzerdefinierte Installation von Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).  <br/>  Stellt die Infrastruktur bereit, die zum Aktivieren von SSO erforderlich ist.  <br/>  Für viele Hybrid Szenarien erforderlich:  <br/>  Mehrstufige Migration  <br/>  Hybrid Exchange  <br/>  Synchronisiert Sicherheits-und e-Mail-aktivierte Gruppen aus Ihrem lokalen Verzeichnis.  <br/> |
   
- Unabhängig davon, wie Sie die Benutzerkonten Office 365 hinzufügen möchten, müssen Sie mehrere Konto Funktionen wie das Zuweisen von Lizenzen, die Angabe des Standorts usw. verwalten. Diese Features können langfristig über das Admin Center verwaltet werden, oder Sie können auch [Benutzerkonten mit Office 365 PowerShell erstellen](https://go.microsoft.com/fwlink/p/?LinkId=717083).
    
    Wenn Sie alle Benutzer über das Admin Center hinzufügen und verwalten möchten, geben Sie den Standort an, und weisen Sie gleichzeitig mit dem Erstellen des Office 365 Kontos Lizenzen zu. Daher ist nicht viel Planung erforderlich.
    
    > [!IMPORTANT]
    > Das Erstellen von Konten in Office 365 ohne Zuweisen einer Lizenz (beispielsweise zu SharePoint Online) bedeutet, dass der Kontobesitzer das Office 365 Portal anzeigen kann, aber nicht auf alle Dienste im Abonnement des Unternehmens zugreifen kann. Nachdem Sie einen Standort und die Lizenz zugewiesen haben, wird das Konto auf den Dienst oder die Dienste repliziert, die Sie zugewiesen haben. Der Benutzer kann sich bei seinem Konto anmelden und die Ihnen zugewiesenen Dienste verwenden. 
  
## <a name="next-steps"></a>Nächste Schritte

[Office 365-Integration in lokale Umgebungen](office-365-integration.md)
  
## <a name="see-also"></a>Siehe auch

[Verwalten von Benutzerkonten in Office 365](https://support.office.com/article/3204162b-0b6c-4838-8a11-394b9bfd31de.aspx)
  

