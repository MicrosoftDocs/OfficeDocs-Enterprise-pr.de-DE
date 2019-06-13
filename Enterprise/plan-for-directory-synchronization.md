---
title: Hybride Identitäts-und Verzeichnissynchronisierung für Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
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
description: Beschreibt die Verzeichnissynchronisierung mit Office 365, Active Directory-Domänendienste Bereinigung und dem Azure Active Directory Connect-Tool.
ms.openlocfilehash: 31fcd8baaccabf5d3f4f0cf47c7573c43f7cd40b
ms.sourcegitcommit: 47c6156c0038745103b71f44b2a3b103c62e5d6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2019
ms.locfileid: "34102492"
---
# <a name="hybrid-identity-and-directory-synchronization-for-office-365"></a>Hybride Identitäts-und Verzeichnissynchronisierung für Office 365

Je nach geschäftlichen Anforderungen und technischen Anforderungen ist das hybride Identitätsmodell und die Verzeichnissynchronisierung die häufigste Wahl für Unternehmenskunden, die Office 365 übernehmen. Mit der Verzeichnissynchronisierung können Sie Identitäten in Ihrer Active Directory-Domänendienste (AD DS) verwalten, und alle Aktualisierungen an Benutzerkonten, Gruppen und Kontakten werden mit dem Azure Active Directory (Azure AD)-Mandanten Ihres Office 365 Abonnements synchronisiert.


>[!Note]
>Wenn AD DS Benutzerkonten zum ersten Mal synchronisiert werden, wird Ihnen nicht automatisch eine Office 365 Lizenz zugewiesen, und es kann nicht auf Office 365 Dienste wie e-Mail zugegriffen werden. Sie müssen diesen Benutzerkonten entweder einzeln oder dynamisch über eine Gruppenmitgliedschaft eine Lizenz zuweisen.
>

## <a name="authentication-for-hybrid-identity"></a>Authentifizierung für Hybrid Identität

Bei der Verwendung des Hybriden Identitätsmodells gibt es zwei Arten von Authentifizierung:

- Verwaltete Authentifizierung

  Azure AD verarbeitet den Authentifizierungsprozess mithilfe einer lokal gespeicherten Hashversion des Kennworts oder sendet die Anmeldeinformationen an einen lokalen Software-Agent, der vom lokalen AD DS authentifiziert werden soll.

- Verbundauthentifizierung

  Azure AD umleitet den Clientcomputer, der die Authentifizierung anfordert, um einen anderen Identitätsanbieter zu kontaktieren.

### <a name="managed-authentication"></a>Verwaltete Authentifizierung

Es gibt zwei Arten der verwalteten Authentifizierung:

- Kennworthash Synchronisierung (PHS)

  Azure AD führt die Authentifizierung selbst aus.

- Passthrough-Authentifizierung (PTA)

  Azure Ad die Authentifizierung AD DS durchführen.


#### <a name="password-hash-synchronization"></a>Kennworthashsynchronisierung

Mit der Kennworthash Synchronisierung (PHS) synchronisieren Sie Ihre AD DS Benutzerkonten mit Office 365 und verwalten Ihre Benutzer lokal. Hashwerte von Benutzerkennwörtern werden von Ihrem AD DS zu Azure AD synchronisiert, sodass die Benutzer das gleiche Kennwort lokal und in der Cloud haben. Dies ist die einfachste Möglichkeit zum Aktivieren der Authentifizierung für AD DS Identitäten in Azure AD. 

![](./media/plan-for-directory-synchronization/phs-authentication.png)

Wenn Kennwörter lokal geändert oder zurückgesetzt werden, werden die neuen Kennworthashs mit Azure AD synchronisiert, sodass Ihre Benutzer immer dasselbe Kennwort für Cloud-Ressourcen und lokale Ressourcen verwenden können. Die Benutzerkennwörter werden nie an Azure AD gesendet oder in Azure AD in Klartext gespeichert. Einige Premium Features von Azure AD, beispielsweise Identitätsschutz, erfordern PHS, unabhängig davon, welche Authentifizierungsmethode ausgewählt ist.
  
Weitere Informationen finden Sie unter [Auswählen von PHS](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) .
  
#### <a name="pass-through-authentication"></a>Pass-Through-Authentifizierung

Die Pass-Through-Authentifizierung (PTA) bietet eine einfache Kennwortüberprüfung für Azure AD Authentifizierungsdienste mit einem Software-Agent, der auf einem oder mehreren lokalen Servern läuft, um die Benutzer direkt mit Ihrem AD DS zu validieren. Mit Pass-Through-Authentifizierung (PTA) synchronisieren Sie AD DS Benutzerkonten mit Office 365 und verwalten Ihre Benutzer lokal. 

![](./media/plan-for-directory-synchronization/pta-authentication.png)

PTA ermöglicht es Ihren Benutzern, sich bei lokalen und Office 365 Ressourcen und Anwendungen mit Ihrem lokalen Konto und Kennwort anzumelden. Mit dieser Konfiguration werden Benutzerkennwörter direkt für Ihr lokales AD DS überprüft, ohne dass Kennworthashs in Azure AD gespeichert werden. 

PTA richtet sich auch an Organisationen mit einer Sicherheitsanforderung, um lokale Benutzerkonto Zustände, Kennwortrichtlinien und Anmeldezeiten sofort zu erzwingen. 
  
Weitere Informationen finden Sie unter [Auswählen von PTA](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) .
  
### <a name="federated-authentication"></a>Verbundauthentifizierung

Die Verbundauthentifizierung ist in erster Linie für große Unternehmensorganisationen mit komplexeren Authentifizierungsanforderungen geeignet. AD DS Identitäten werden mit Office 365 synchronisiert, und Benutzerkonten werden lokal verwaltet. Bei der Verbundauthentifizierung haben Benutzer das gleiche Kennwort lokal und in der Cloud, und Sie müssen sich nicht erneut anmelden, um Office 365 verwenden zu können. 

Die Verbundauthentifizierung kann zusätzliche Authentifizierungsanforderungen wie Smartcard-basierte Authentifizierung oder mehrstufige Authentifizierung eines Drittanbieters unterstützen und ist in der Regel erforderlich, wenn Organisationen eine Authentifizierungsanforderung nicht nativ von Azure Ad unterstützt.
 
Weitere Informationen finden Sie unter [Choosing Federated Authentication](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) .
  
#### <a name="third-party-authentication-and-identity-providers"></a>Authentifizierungs-und Identitätsanbieter von Drittanbietern

Lokale Verzeichnisobjekte können mit Office 365 synchronisiert werden, und der Zugriff auf Cloud-Ressourcen wird in erster Linie von einem Drittanbieter-Identitätsanbieter (IDP) verwaltet. Wenn Ihre Organisation eine Drittanbieter-Verbundlösung verwendet, können Sie die Anmeldung mit dieser Lösung für Office 365 konfigurieren, vorausgesetzt, dass die Drittanbieter-Verbundlösung mit Azure AD kompatibel ist.
  
Weitere Informationen finden Sie unter [Azure AD Verbund Kompatibilität](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility) .
  
## <a name="ad-ds-cleanup"></a>AD DS Bereinigung

Um einen nahtlosen Übergang zu Office 365 mithilfe der Synchronisierung sicherzustellen, müssen Sie Ihre AD DS Gesamtstruktur vorbereiten, bevor Sie mit der Bereitstellung der Office 365-Verzeichnissynchronisierung beginnen.
  
Wenn Sie die [Verzeichnissynchronisierung in Office 365 einrichten](set-up-directory-synchronization.md), besteht einer der Schritte darin, [das Tool IdFix herunterzuladen und auszuführen](install-and-run-idfix.md). Sie können das IdFix-Tool verwenden, um die [Verzeichnisbereinigung](prepare-directory-attributes-for-synch-with-idfix.md)zu unterstützen.
  
Die Verzeichnisbereinigung sollte sich auf die folgenden Aufgaben konzentrieren:

- Entfernen Sie doppelte **proxyAddress** -und **userPrincipalName** -Attribute.
- Aktualisieren Sie leere und ungültige **userPrincipalName** -Attribute mit gültigen **userPrincipalName** -Attributen.
- Entfernen von ungültigen und fragwürdigen Zeichen im **angegebenen**Namen, Nachnamen ( **SN** ), **sAMAccountName**, **DisplayName**, **Mail**, **proxyAddresses**, mailNickname und **userPrincipalName** **** Attribute. Ausführliche Informationen zum Vorbereiten von Attributen finden Sie unter [Liste der Attribute, die mit dem Azure Active Directory Sync-Tool synchronisiert werden](https://go.microsoft.com/fwlink/p/?LinkId=396719).

    > [!NOTE]
    > Dabei handelt es sich um dieselben Attribute, die Azure AD Connect synchronisiert. 
  
## <a name="multi-forest-deployment-considerations"></a>Überlegungen zur Bereitstellung in mehreren Gesamtstrukturen

Verwenden Sie für mehrere Gesamtstrukturen und SSO-Optionen die [benutzerdefinierte Installation von Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).
  
Wenn Ihre Organisation über mehrere Gesamtstrukturen für die Authentifizierung verfügt (Anmelde Gesamtstrukturen), wird dringend Folgendes empfohlen:
  
- **Sie sollten die Gesamtstruktur konsolidieren.** Im Allgemeinen ist mehr Aufwand erforderlich, um mehrere Gesamtstrukturen beizubehalten. Wenn Ihre Organisation nicht über Sicherheitseinschränkungen verfügt, die separate Gesamtstrukturen erfordern, sollten Sie die lokale Umgebung vereinfachen.
- **Nur in der primären anmeldegesamtstruktur verwenden.** Stellen Sie Office 365 nur in der primären anmeldegesamtstruktur für die anfängliche Einführung von Office 365 bereit. 

Wenn Sie Ihre AD DS-Bereitstellung mit mehreren Gesamtstrukturen nicht konsolidieren oder andere Verzeichnisdienste zum Verwalten von Identitäten verwenden, können Sie diese möglicherweise mit der Hilfe von Microsoft oder einem Partner synchronisieren.
  
Weitere Informationen finden Sie unter [Multi-Forest Directory Sync with Single Sign-on-Szenario](https://go.microsoft.com/fwlink/p/?LinkId=525321) .
  
## <a name="features-that-are-dependent-on-directory-synchronization"></a>Funktionen, die von der Verzeichnissynchronisierung abhängig sind
  
Die Verzeichnissynchronisierung ist für die folgenden Features und Funktionen erforderlich:
  
- Azure AD nahtloses einmaliges Anmelden (Single Sign-on, SSO)
- Skype-Koexistenz
- Exchange-hybridbereitstellung, einschließlich:
  - Vollständig freigegebene globale Adressliste (GAL) zwischen Ihrer lokalen Exchange-Umgebung und Office 365.
  - Synchronisierung von GAL-Informationen aus unterschiedlichen E-Mail-Systemen.
  - Möglichkeit zum Hinzufügen von Benutzern zu Office 365 Dienst angeboten und zum Entfernen von Benutzern. Dies erfordert Folgendes:
  - Die bidirektionale Synchronisierung muss während der Verzeichnis synchronisierungseinrichtung konfiguriert werden. Standardmäßig schreiben Verzeichnissynchronisierungstools Verzeichnisinformationen nur in die Cloud. Wenn Sie die bidirektionale Synchronisierung konfigurieren, aktivieren Sie die Write-Back-Funktionalität, sodass eine beschränkte Anzahl von Objektattributen aus der Cloud kopiert und anschließend wieder in Ihre lokale AD DS geschrieben wird. Write-Back wird auch als Exchange-Hybrid Modus bezeichnet. 
  - Eine lokale Exchange-hybridbereitstellung
  - Die Möglichkeit, einige Benutzerpostfächer in Office 365 zu verschieben und gleichzeitig andere Benutzerpostfächer lokal aufzubewahren.
  - Sichere Absender und blockierte Absender lokal werden nach Office 365 repliziert.
  - Grundlegende Delegierung und Funktion zum Senden von E-Mails im Auftrag.
  - Sie verfügen über eine integrierte lokale Smartcard oder mehrstufige Authentifizierungslösung.
- Synchronisierung von Fotos, Miniaturansichten, Konferenzräumen und Sicherheitsgruppen

## <a name="next-step"></a>Nächster Schritt

Wenn Sie bereit sind, die Hybrid Identität bereitzustellen, lesen Sie [Vorbereiten der Bereitstellung von Benutzern](prepare-for-directory-synchronization.md).
  

