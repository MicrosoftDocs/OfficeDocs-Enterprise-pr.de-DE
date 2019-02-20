---
title: Tools zum Verwalten von Office 365-Konten
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 5/3/2018
ms.audience: Admin
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
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
description: 'Erfahren Sie, welche Tools Sie zum Verwalten Ihrer Office 365-Benutzer verwenden müssen, und wie Sie die Benutzeridentitäten verwalten können. '
ms.openlocfilehash: 0fa515d89afa3abe4b0fe936b297156b20890b0f
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085364"
---
# <a name="tools-to-manage-office-365-accounts"></a>Tools zum Verwalten von Office 365-Konten

Sie können Office 365-Benutzer je nach Konfiguration auf verschiedene Arten verwalten. Sie können Benutzer im Office 365 Admin Center, in Windows PowerShell, im lokalen Verzeichnis oder im Azure Active Directory-Verwaltungsportal verwalten. Sobald Sie Office 365 erwerben, können Sie mit dem Admin Center und der Windows PowerShell Konten verwalten. Bei der Verwaltung von Cloud-Identitäten verfügt jede Person in Ihrer Organisation über eine separate Benutzer-ID und ein Kennwort für Office 365. Wenn Sie in Ihre lokale Infrastruktur integrieren und Benutzerkonten mit Office 365 synchronisieren möchten, können Sie Azure Active Directory Connect verwenden, um die Synchronisierung von Identitäten bereitzustellen und optional eine Kennwortsynchronisierung oder eine vollständige Funktionalität für einmaliges Anmelden.
  
## <a name="plan-for-where-and-how-you-will-manage-your-user-accounts"></a>Planen, wo und wie Sie Ihre Benutzerkonten verwalten

Wo und wie Sie Ihre Benutzerkonten verwalten können, hängt vom Identitätsmodell ab, das Sie für Ihre Office 365 verwenden möchten. Die beiden Gesamt Modelle sind Cloud-Authentifizierung und Verbundauthentifizierung.
  
### <a name="cloud-authentication"></a>Cloud-Authentifizierung

- [Cloud Authentication](about-office-365-identity.md#cloud-authentication) – erstellen und Verwalten von Benutzern im Office 365 Admin Center können Sie auch Windows PowerShell oder Azure Active Directory verwenden, um Ihre Benutzer zu verwalten. 
    
- [Kennworthash Synchronisierung mit nahtlosem einmaligem Anmelden](about-office-365-identity.md) – die einfachste Möglichkeit zum Aktivieren der Authentifizierung für lokale Verzeichnisobjekte in Azure AD. Mit Password Hash Sync (PHS) synchronisieren Sie Ihre lokalen Active Directory-Benutzerkonto Objekte mit Office 365 und verwalten Ihre Benutzer lokal. 
    
- [Pass-Through-Authentifizierung mit nahtlosem einmaligem Anmelden](about-office-365-identity.md) – bietet eine einfache Kennwortüberprüfung für Azure AD-Authentifizierungsdienste mit einem Software-Agent, der auf einem oder mehreren lokalen Servern läuft, um die Benutzer direkt mit dem lokales Active Directory. 
    
### <a name="federated-authentication"></a>Verbundauthentifizierung

- [Optionen für die Verbundauthentifizierung](about-office-365-identity.md#federated-authentication-options) – in erster Linie für große Unternehmensorganisationen mit komplexeren Authentifizierungsanforderungen werden lokale Verzeichnisobjekte mit Office 365 synchronisiert, und Benutzerkonten werden lokal verwaltet. 
    
- [Authentifizierungs-und Identitätsanbieter von Drittanbietern](about-office-365-identity.md) -lokale Verzeichnisobjekte können mit Office 365 synchronisiert werden, und der Zugriff auf die Cloud-Ressource wird in erster Linie von einem Drittanbieter (Identity Provider, IDP) verwaltet. 
    
## <a name="managing-accounts"></a>Verwalten von Konten

Berücksichtigen Sie beim Festlegen der Art und Weise, in der Ihre Organisation Konten erstellt und verwaltet, Folgendes:
  
- Die Software für die Verzeichnissynchronisierung muss auf Servern in Ihrer lokalen Umgebung installiert werden, um die Identitäten zwischen Office 365 und Ihrem lokalen Verzeichnis zu verbinden.
    
- Jede Verzeichnissynchronisierungsoption, einschließlich SSO-Optionen, erfordert, dass Ihre lokalen Verzeichnisattribute den Standards entsprechen. Die Einzelheiten der Attribute, die in Ihrem Verzeichnis verwendet werden und welche Bereinigung (falls vorhanden) erforderlich sind, werden unter [Prepare to Provision users Through Directory Synchronization to Office 365](prepare-for-directory-synchronization.md)beschrieben. Anweisungen zur Verwendung von IdFix zum Automatisieren der Verzeichnisbereinigung finden Sie unter [Install and Run the Office 365 IdFix Tool](install-and-run-idfix.md) . 
    
- Planen Sie, wie Sie Office 365-Konten erstellen.
    
    In der folgenden Tabelle sind die verschiedenen Kontenverwaltungstools aufgeführt.
    
|**Option**|**Hinweise**|
|:-----|:-----|
|Office 365 admin center  <br/> |[Hinzufügen von einzelnen Benutzern oder Massenhinzufügen von Benutzern zu Office 365 - Administratorhilfe](https://support.office.com/article/1970f7d6-03b5-442f-b385-5880b9c256ec) <br/>  Stellt eine einfache Weboberfläche zum Hinzufügen und Ändern von Benutzerkonten bereit.  <br/>  Kann nicht zum Ändern von Benutzern verwendet werden, wenn die Verzeichnissynchronisierung aktiviert ist (Speicherort und Lizenzzuweisung können festgelegt werden).  <br/>  Kann nicht mit SSO-Optionen verwendet werden.  <br/> |
|Windows PowerShell  <br/> |[Verwalten von Office 365 mit der Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=698471) <br/>  Ermöglicht Ihnen das Hinzufügen von Benutzern in Massen Benutzern mithilfe eines Windows PowerShell-Skripts.  <br/>  Kann verwendet werden, um Standort und Lizenzen für Konten zuzuweisen, unabhängig davon, wie die Konten erstellt werden.  <br/> |
|Massenimport  <br/> |[Gleichzeitiges Hinzufügen mehrerer Benutzer zu Office 365 – Hilfe für Administratoren](add-several-users-at-the-same-time.md) <br/>  Ermöglicht Ihnen das Importieren einer CSV-Datei, um eine Benutzergruppe zu Office 365 hinzuzufügen.  <br/>  Kann nicht mit SSO-Optionen verwendet werden.  <br/> |
|Azure Active Directory  <br/> |Sie erhalten eine ﻿kostenlose Version von Azure Active Directory mit Ihrem Office 365-Abonnement. Sie können Funktionen wie Self-Service-Kennwortzurücksetzung für Cloud-Benutzer und Anpassung der Anmelde-und Zugriffsbereich-Seiten mithilfe der Free Edition ausführen. Um eine erweiterte Funktionalität zu erhalten, können Sie ein Upgrade auf die Basic Edition oder die Premium Edition durchführen. Die Liste der unterstützten Funktionen finden Sie unter [Azure Active Directory Editions](https://go.microsoft.com/fwlink/p/?LinkId=698465) .<br/> |
|Verzeichnissynchronisierung  <br/> |[Integrieren Ihrer lokalen Identitäten in Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkID=624168) <br/>  Für die Verzeichnissynchronisierung mit oder ohne Kennwortsynchronisierung verwenden Sie [Azure AD Connect mit Express-Einstellungen](https://go.microsoft.com/fwlink/p/?LinkID=698537).  <br/>  Verwenden Sie für mehrere Gesamtstrukturen und SSO-Optionen die [benutzerdefinierte Installation von Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).  <br/>  Stellt die Infrastruktur bereit, die zum Aktivieren von SSO erforderlich ist.  <br/>  Für viele Hybrid Szenarien erforderlich:  <br/>  Mehrstufige Migration  <br/>  Hybrid Exchange  <br/>  Synchronisiert Sicherheits- und E-Mail-aktivierte Gruppen über Ihr lokales Verzeichnis.  <br/> |
   
- Unabhängig davon, wie Sie die Benutzerkonten zu Office 365 hinzufügen möchten, müssen Sie mehrere Konto Funktionen verwalten, beispielsweise Lizenzen zuweisen, Speicherort angeben usw. Diese Funktionen können langfristig über das Office 365 Admin Center verwaltet werden, oder Sie können auch [Benutzerkonten mit office 365 PowerShell erstellen](https://go.microsoft.com/fwlink/p/?LinkId=717083).
    
    Wenn Sie alle Ihre Benutzer über das Office 365 Admin Center hinzufügen und verwalten möchten, geben Sie den Speicherort an und weisen gleichzeitig Lizenzen zu, um das Office 365-Konto zu erstellen. Daher ist nicht viel Planung erforderlich.
    
    > [!IMPORTANT]
    > Das Erstellen von Konten in Office 365 ohne Zuweisen einer Lizenz (beispielsweise zu SharePoint Online) bewirkt, dass der Kontobesitzer das Office 365-Portal anzeigen kann, aber keinen Zugriff auf die Dienste innerhalb Ihres Unternehmens-Abonnements hat. Nachdem Sie einen Standort und eine Lizenz zugewiesen haben, wird das Konto in den Dienst oder die Dienste repliziert, die Sie zugeordnet haben. Der Benutzer kann sich bei seinem Konto anmelden und die Ihnen zugewiesenen Dienste verwenden. 
  
## <a name="next-steps"></a>Nächste Schritte

[Verwenden der eigenen Domäne für die Integration in lokale E-Mail, z. B. mit Verzeichnisdiensten](office-365-integration.md)
  
## <a name="see-also"></a>Siehe auch

[Verwalten von Benutzerkonten in Office 365](https://support.office.com/article/3204162b-0b6c-4838-8a11-394b9bfd31de.aspx)
  

