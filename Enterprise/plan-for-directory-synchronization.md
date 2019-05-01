---
title: Planen der Verzeichnissynchronisierung für Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MOE150
- MET150
ms.assetid: d3577c90-dda5-45ca-afb0-370d2889b10f
description: Beschreibt die Verzeichnissynchronisierung mit Office 365, Active Directory Cleanup und Azure Active Directory Connect.
ms.openlocfilehash: 1a7c63f699c51c829aaab5b70cb6a1a203bca3be
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2019
ms.locfileid: "33492081"
---
# <a name="plan-for-directory-synchronization-for-office-365"></a>Planen der Verzeichnissynchronisierung für Office 365

Je nach geschäftlichem Bedarf und den technischen Anforderungen ist die Verzeichnissynchronisierung die häufigste Wahl für Unternehmenskunden, die zu Office 365 wechseln. Mit der Verzeichnissynchronisierung können Identitäten im lokalen Active Directory verwaltet werden, und alle Aktualisierungen dieser Identität werden mit Office 365 synchronisiert.
  
Bei der Planung einer Implementierung der Verzeichnissynchronisierung, einschließlich der Verzeichnis Vorbereitung, und den Anforderungen und Funktionen des Azure Active Directory müssen Sie einige Punkte beachten. Die Verzeichnis Vorbereitung umfasst einige Bereiche. Sie schließen Attributaktualisierungen, Überwachung und die Planung der Domänencontrollerplatzierung ein. Planungsanforderungen und-Funktionen beinhalten das Bestimmen der erforderlichen Berechtigungen, die Planung von Szenarien mit mehreren Gesamtstrukturen/Verzeichnissen, die Kapazitätsplanung und die bidirektionale Synchronisierung.
  
## <a name="office-365-identity-models"></a>Office 365-Identitäts Modelle

Office 365 verwendet zwei Haupt Authentifizierungs-und Identitäts Modelle: Cloud-Authentifizierung und Verbundauthentifizierung.
  
### <a name="cloud-authentication"></a>Cloud-Authentifizierung

[Cloud Identity](about-office-365-identity.md) -erstellen und Verwalten von Benutzern im [Microsoft 365 Admin Center](https://admin.microsoft.com)können Sie auch Windows PowerShell oder Azure Active Directory verwenden, um Ihre Benutzer zu verwalten.
  
[Kennworthash Synchronisierung mit nahtlosem einmaligem Anmelden](about-office-365-identity.md) – die einfachste Möglichkeit zum Aktivieren der Authentifizierung für lokale Verzeichnisobjekte in Azure AD. Mit Password Hash Sync (PHS) synchronisieren Sie Ihre lokalen Active Directory-Benutzerkonto Objekte mit Office 365 und verwalten Ihre Benutzer lokal.
  
[Pass-Through-Authentifizierung mit nahtlosem einmaligem Anmelden](about-office-365-identity.md) – bietet eine einfache Kennwortüberprüfung für Azure AD-Authentifizierungsdienste mit einem Software-Agent, der auf einem oder mehreren lokalen Servern läuft, um die Benutzer direkt mit dem lokales Active Directory.
  
### <a name="federated-authentication"></a>Verbundauthentifizierung

[Verbundidentität mit Active Directory-Verbunddiensten AD FS](about-office-365-identity.md) – in erster Linie für große Unternehmensorganisationen mit komplexeren Authentifizierungsanforderungen werden lokale Verzeichnisobjekte mit Office 365 synchronisiert, und Benutzerkonten werden lokal verwaltet.
  
[Authentifizierungs-und Identitätsanbieter von Drittanbietern](about-office-365-identity.md) -lokale Verzeichnisobjekte können mit Office 365 synchronisiert werden, und der Zugriff auf die Cloud-Ressource wird in erster Linie von einem Drittanbieter (Identity Provider, IDP) verwaltet.
  
## <a name="active-directory-cleanup"></a>Active Directory-Bereinigung

Um einen nahtlosen Übergang zu Office 365 mithilfe der Synchronisierung sicherzustellen, wird dringend empfohlen, dass Sie Ihre Active Directory-Gesamtstruktur vorbereiten, bevor Sie mit der Bereitstellung der Office 365-Verzeichnissynchronisierung beginnen.
  
Wenn Sie die [Verzeichnissynchronisierung in Office 365 einrichten](set-up-directory-synchronization.md), können Sie [das IdFix-Tool herunterladen und ausführen](install-and-run-idfix.md). Sie können das IdFix-Tool verwenden, um die [Verzeichnisbereinigung](prepare-directory-attributes-for-synch-with-idfix.md)zu unterstützen.
  
Die Verzeichnisbereinigung sollte sich auf die folgenden Aufgaben konzentrieren:

- Entfernen Sie doppelte **proxyAddress** -und **userPrincipalName** -Attribute.
- Aktualisieren Sie leere und ungültige **userPrincipalName** -Attribute mit gültigen **userPrincipalName** -Attributen.
- Entfernen Sie ungültige und fragwürdige Zeichen im **angegebenen**Namen, Nachnamen ( **SN** ), **sAMAccountName**, **DisplayName**, **Mail**, **proxyAddresses**, mailNickname und **userPrincipalName** **** Attribute. Ausführliche Informationen zum Vorbereiten von Attributen finden Sie unter [Liste der Attribute, die vom Azure Active Directory-Synchronisierungs Tool synchronisiert werden](https://go.microsoft.com/fwlink/p/?LinkId=396719).

    > [!NOTE]
    > Hierbei handelt es sich um dieselben Attribute, die von Azure AD Connect synchronisiert werden. 
  
## <a name="multi-forest-deployment-considerations"></a>Überlegungen zur Bereitstellung mit mehreren Gesamtstrukturen

Verwenden Sie für mehrere Gesamtstrukturen und SSO-Optionen die [benutzerdefinierte Installation von Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).
  
Wenn Ihre Organisation über mehrere Gesamtstrukturen für die Authentifizierung (Logon-Gesamtstrukturen) verfügt, wird Folgendes empfohlen:
  
- **Bewerten der Konsolidierung der Gesamtstrukturen** Im Allgemeinen ist für die Verwaltung mehrerer Gesamtstrukturen mehr Aufwand erforderlich. Wenn Ihre Organisation keine Sicherheitseinschränkungen aufweist, die separate Gesamtstrukturen erfordern, sollten Sie die Vereinfachung der lokalen Umgebung erwägen.
- **Nur in der Gesamtstruktur der primären Anmeldung verwenden.** Erwägen Sie die Bereitstellung von Office 365 nur in ihrer primären Logon-Gesamtstruktur für die erstmalige Einführung von Office 365. 

Wenn Sie die Active Directory-Bereitstellung mit mehreren Gesamtstrukturen nicht konsolidieren können oder andere Verzeichnisdienste zur Verwaltung von Identitäten verwenden, können Sie diese mithilfe von Microsoft oder einem Partner synchronisieren.
  
Weitere Informationen finden Sie unter [Verzeichnissynchronisierung mit mehreren Gesamtstrukturen und Szenario mit einmaligem Anmelden](https://go.microsoft.com/fwlink/p/?LinkId=525321).
  
## <a name="directory-integration-tools"></a>Verzeichnis Integrationstools

Bei der Verzeichnissynchronisierung handelt es sich um die Synchronisierung von Verzeichnisobjekten (Benutzern, Gruppen und Kontakten) von Ihrer lokalen Active Directory-Umgebung zur Office 365-Verzeichnisinfrastruktur. Eine Liste der verfügbaren Tools und deren Funktionen finden Sie unter [Directory-Integrationstools](https://go.microsoft.com/fwlink/p/?LinkID=510956) . Das empfohlene Tool ist [Azure Active Directory Connect](https://go.microsoft.com/fwlink/?LinkId=525323).
  
Wenn Benutzerkonten zum ersten Mal mit dem Office 365-Verzeichnis synchronisiert werden, werden Sie als nicht aktiviert markiert. Sie können keine e-Mails senden oder empfangen, und Sie nutzen keine Abonnementlizenzen. Wenn Sie bereit sind, Office 365-Abonnements bestimmten Benutzern zuzuweisen, müssen Sie Sie auswählen und aktivieren, indem Sie eine gültige Lizenz zuweisen.
  
Die Verzeichnissynchronisierung ist für die folgenden Features und Funktionen erforderlich:
  
- SSO
- Skype-Koexistenz
- Exchange-hybridbereitstellung, einschließlich:
  - Vollständig gemeinsam genutzte globale Adressliste (GAL) zwischen Ihrer lokalen Exchange-Umgebung und Office 365.
  - Synchronisierung von GAL-Informationen aus unterschiedlichen E-Mail-Systemen.
  - Die Möglichkeit zum Hinzufügen von Benutzern zu Office 365-Dienst angeboten und zum Entfernen von Benutzern. Dies erfordert Folgendes:
  - Die bidirektionale Synchronisierung muss beim Einrichten der Verzeichnissynchronisierung konfiguriert werden. Standardmäßig schreiben Verzeichnissynchronisierungstools nur Verzeichnisinformationen in die Cloud. Wenn Sie die bidirektionale Synchronisierung konfigurieren, aktivieren Sie die Write-Back-Funktionalität, sodass eine begrenzte Anzahl von Objektattributen aus der Cloud kopiert und dann wieder in Ihr lokales Active Directory geschrieben wird. Write-Back wird auch als Exchange-Hybrid Modus bezeichnet. 
  - Lokale Exchange-hybridbereitstellung
  - Die Möglichkeit, einige Benutzerpostfächer in Office 365 zu verschieben, während andere Benutzerpostfächer lokal gespeichert werden.
  - Sichere Absender und blockierte Absender werden in Office 365 repliziert.
  - Grundlegende Delegierung und Funktion zum Senden von E-Mails im Auftrag.
  - Sie verfügen über eine integrierte lokale Smartcard-oder mehrstufige Authentifizierungslösung.
- Synchronisierung von Fotos, Miniaturansichten, Konferenzräumen und Sicherheitsgruppen