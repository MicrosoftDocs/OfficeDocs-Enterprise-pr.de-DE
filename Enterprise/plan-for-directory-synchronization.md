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
search.appverid:
- MOE150
- MET150
ms.assetid: d3577c90-dda5-45ca-afb0-370d2889b10f
description: Beschreibt die Directory-Synchronisierung mit Office 365, Active Directory-Bereinigung und Azure Active Directory-Connect-Tool.
ms.openlocfilehash: cc2a2ca050facaf53f0a235898c31ae7aaeff4ae
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540878"
---
# <a name="plan-for-directory-synchronization-for-office-365"></a>Planen der Verzeichnissynchronisierung für Office 365
Je nach unternehmensanforderung und technische Anforderungen ist verzeichnissynchronisierung die am häufigsten verwendeten provisioning Wahl für Unternehmenskunden, die nach Office 365 verschieben möchten. Directory-Synchronisierung ermöglicht Identitäten im lokalen Active Directory verwaltet werden, und alle Updates dieser Identität zu Office 365 synchronisiert werden.
  
Es gibt einige Dinge im Hinterkopf behalten, wenn Sie eine Implementierung der verzeichnissynchronisierung, einschließlich verzeichnisvorbereitung, und die Anforderungen und Funktionen von Azure Active Directory planen. Directory-Vorbereitung wird ein paar Bereiche behandelt. Dazu gehören Attribut Updates, Überwachung und Domänencontroller-Platzierung planen. Planen der Anforderungen und Funktionen auch das Ermitteln der Berechtigungen, die Planung für Multiforest Verzeichnis/Szenarien, kapazitätsplanung und bidirektionale Synchronisierung erforderlich sind.
  
## <a name="office-365-identity-models"></a>Modelle für Office 365-Identität
Office 365 verwendet zwei Haupt-Authentifizierung und Identität Modelle: Authentifizierung und Verbundauthentifizierung cloud.
  
### <a name="cloud-authentication"></a>Cloud-Authentifizierung
[Cloudidentität](about-office-365-identity.md) - erstellen und Verwalten von Benutzern in Office 365 Administrationscenter, Sie können Windows PowerShell oder Azure Active Directory auch verwenden, um Benutzer zu verwalten. 
  
[Kennworthash synchronisieren mit nahtlos einmaliges Anmelden](about-office-365-identity.md) – die einfachste Möglichkeit zum Aktivieren der Authentifizierung für lokale-Directory-Objekte in Azure Active Directory. Mit Hash kennwortsynchronisierung (PBS) Ihre lokale Active Directory User Account-Objekten mit Office 365 synchronisieren und Ihre lokalen Benutzer verwalten. 
  
[Pass-Through-Authentifizierung mit nahtlos einmaliges Anmelden](about-office-365-identity.md) - Geschäftstyp ein einfaches Kennwort für Azure AD-Authentifizierungsdienste mithilfe eines Software-Agents, die auf einem oder mehreren lokalen Servern ausgeführt für die Überprüfung der Benutzer direkt mit Ihrer lokale Active Directory. 
  
### <a name="federated-authentication"></a>Verbundauthentifizierung
[Federated Identity mit Active Directory Federation Services AD FS](about-office-365-identity.md) - lokale in erster Linie für große Unternehmen mit komplexen Anforderungen für die Authentifizierung, Verzeichnisobjekte mit Office 365 synchronisiert werden und sind von Benutzerkonten Verwaltete lokale. 
  
[Authentifizierung und Identität Drittanbieter](about-office-365-identity.md) - lokalen Verzeichnis Objekte möglicherweise auf Office 365 synchronisiert und Ressourcenzugriff cloud wird hauptsächlich von einem Drittanbieter-STS-Anbieter (IdP) verwaltet. 
  
## <a name="active-directory-cleanup"></a>Active Directory-Bereinigung
Um einen reibungslosen Übergang zu Office 365 sicherzustellen mithilfe der Synchronisierung, empfohlen dringend, dass Ihre Active Directory-Gesamtstruktur vorbereiten, bevor Sie Ihre Office 365 Directory Synchronization Bereitstellung beginnen.
  
Wenn ist Sie die [verzeichnissynchronisierung in Office 365 einrichten](set-up-directory-synchronization.md), über die Schritte zum [herunterladen und Ausführen des IdFix-Tools](install-and-run-idfix.md). Das IdFix-Tool können Sie um den [verzeichnisbereinigung](prepare-directory-attributes-for-synch-with-idfix.md)zu unterstützen.
  
Directory-Bereinigung sollten sich auf die folgenden Aufgaben konzentrieren:

- Entfernen Sie doppelte **ProxyAddress** und **UserPrincipalName** -Attribute.
- Aktualisieren leerer und ungültiger Vorkommen des Attributs **userPrincipalName** mit einem gültigen Wert für **userPrincipalName**.
- Entfernen Sie ungültige und fragwürdige Zeichen in der **Vorname**, Nachname ( **sn** ), **sAMAccountName**, **DisplayName**, **e-Mail**, **ProxyAddresses**, **MailNickname**und **userPrincipalName** Attribute. Ausführliche Informationen zum Vorbereiten der Attribute finden Sie unter [Liste der Attribute, die von Azure Active Directory-Synchronisierungstool synchronisiert werden](https://go.microsoft.com/fwlink/p/?LinkId=396719).
    
    > [!NOTE]
    > Dies sind die gleichen Attribute, die Azure AD-Connect synchronisiert wird. 
  
## <a name="multiforest-deployment-considerations"></a>Überlegungen zur Gesamtstrukturbereitstellung
Verwenden Sie für mehrere Gesamtstrukturen und SSO-Optionen [benutzerdefinierte Installation von Azure Active Directory verbinden](https://go.microsoft.com/fwlink/p/?LinkId=698430).
  
Wenn Ihre Organisation mehrere Gesamtstrukturen für die Authentifizierung (Anmeldung Gesamtstrukturen) verfügt, sollten Sie unbedingt Folgendes:
  
- **Bewerten Ihrer Gesamtstrukturen konsolidieren.** Im Allgemeinen ist mehr Aufwand erforderlich, um mehrere Gesamtstrukturen zu verwalten. Wenn Ihre Organisation Sicherheit Integritätsregeln zugeordnet, die die Notwendigkeit für unterschiedlichen Gesamtstrukturen festlegen sind, sollten Sie Ihre lokale Umgebung vereinfachen.
- **Derzeit nur in der primären anmeldegesamtstruktur.** Berücksichtigen Sie die Bereitstellung von Office 365 nur in der primären anmeldegesamtstruktur bei der ersten Einführung von Office 365. 
    
Sie können Ihre Active Directory-Gesamtstrukturen nicht konsolidieren oder mit anderen Verzeichnisdiensten dem Identitäten verwalten, können Sie dies mit Hilfe von Microsoft oder einem Partner synchronisiert werden.
  
Weitere Informationen finden Sie unter [Verzeichnissynchronisierung mit mehreren Gesamtstrukturen mit Szenario für einmaliges Anmelden](https://go.microsoft.com/fwlink/p/?LinkId=525321).
  
## <a name="directory-integration-tools"></a>Tools für die Directory-integration
Directory-Synchronisierung wird die Synchronisierung von Verzeichnisobjekten (Benutzer, Gruppen und Kontakte) aus der lokalen Active Directory-Umgebung zu Office 365-Directory-Infrastruktur. Finden Sie unter [Tools Directory-Integration](https://go.microsoft.com/fwlink/p/?LinkID=510956) für eine Liste der verfügbaren Tools und deren Funktionalität. Das empfohlene zu verwendendes Tool ist [Azure Active Directory verbinden](https://go.microsoft.com/fwlink/?LinkId=525323).
  
Wenn Benutzerkonten mit Office 365-Verzeichnis zum ersten Mal synchronisiert werden, werden diese als nicht aktivierten markiert. Nicht senden oder Empfangen von e-Mails, und sie nicht Abonnementlizenzen belegen. Wenn Sie Office 365-Abonnements auf bestimmte Benutzer zuweisen möchten, müssen Sie wählen und aktivieren, indem Sie eine gültige Lizenz zuweisen.
  
Directory-Synchronisierung wird für die folgenden Features und Funktionen erforderlich:
  
- SSO
    
- Lync-Koexistenz
    
- Exchange-hybridbereitstellung, einschließlich:
    
  - Vollständig gemeinsam genutzte globale Adressliste (GAL) zwischen Ihrer lokalen Exchange-Umgebung und Office 365.
  - Synchronisierung von GAL-Informationen aus unterschiedlichen E-Mail-Systemen.
  - Die Möglichkeit zum Hinzufügen von Benutzern zu und Entfernen von Benutzern aus Office 365-Dienstangebote. Dies ist Folgendes erforderlich:
  - Bidirektionale Synchronisierung muss während des Setups Directory-Synchronisierung konfiguriert werden. Standardmäßig schreiben Directory Synchronization Tools Verzeichnisinformationen nur in der Cloud. Wenn Sie die bidirektionale Synchronisierung konfigurieren, können Sie Zurückschreiben Funktionalität, sodass eine begrenzte Anzahl von Objekten aus der Cloud kopiert und diese dann wieder in Ihre lokale Active Directory geschrieben werden. Zurückschreiben von Daten wird auch als Exchange Hybrid-Modus bezeichnet. 
  - Eine lokale Exchange-hybridbereitstellung
  - Die Möglichkeit, einige Benutzerpostfächer nach Office 365 verschieben, während andere Benutzer lokale Postfächer.
  - Sichere und blockierte Absender lokalen werden auf Office 365 repliziert.
  - Grundlegende Delegierung und Funktion zum Senden von E-Mails im Auftrag.
  - Sie haben eine integrierte lokale Smartcard oder mehrstufige authentifizierungslösung.
    
- Synchronisierung von Fotos, Miniaturansichten, Konferenzräumen und Sicherheitsgruppen