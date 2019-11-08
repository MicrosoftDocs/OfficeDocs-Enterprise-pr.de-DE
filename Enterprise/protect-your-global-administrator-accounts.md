---
title: Schützen Ihrer globalen Office 365-Administratorkonten
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 5/16/2019
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Strat_O365_IP
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 6b4ded77-ac8d-42ed-8606-c014fd947560
description: Schützen Sie den globalen Administratorzugriff auf Ihr Office 365 Abonnement.
ms.openlocfilehash: a75cab61c5b59ebd1b085829cfa20365f20443c9
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "38031610"
---
# <a name="protect-your-office-365-global-administrator-accounts"></a>Schützen Ihrer globalen Office 365-Administratorkonten

 **Zusammenfassung:** Schützen Sie Ihr Office 365-Abonnement vor Angriffen basierend auf der Gefährdung durch ein globales Administratorkonto. 
  
Sicherheitsverletzungen eines Office 365 Abonnements, einschließlich Informationen zum Sammeln und Phishing-Angriffen, werden in der Regel durch Kompromittierung der Anmeldeinformationen eines Office 365 globalen Administratorkontos ausgeführt. Sicherheit in der Cloud ist eine Partnerschaft zwischen Ihnen und Microsoft:
  
- Microsoft-Cloud-Dienste basieren auf einem Fundament aus Vertrauen und Sicherheit. Microsoft stellt Ihnen Sicherheitssteuerelemente und Funktionen zur Verfügung, die Sie beim Schutz Ihrer Daten und Anwendungen unterstützen.
    
- Sie besitzen Ihre Daten und Identitäten sowie die Verantwortung für den Schutz, die Sicherheit Ihrer lokalen Ressourcen und die Sicherheit der von Ihnen kontrollierten Cloud-Komponenten.
    
Microsoft bietet Funktionen zum Schutz Ihrer Organisation, Sie sind jedoch nur wirksam, wenn Sie Sie verwenden. Wenn Sie diese nicht verwenden, sind Sie möglicherweise anfällig für Angriffe. Um Ihre globalen Administratorkonten zu schützen, steht Ihnen Microsoft für detaillierte Anweisungen zur Verfügung:
  
1. Erstellen Sie dedizierte Office 365 globale Administratorkonten, und verwenden Sie Sie nur bei Bedarf.
    
2. Konfigurieren Sie die mehrstufige Authentifizierung für ihre dedizierten Office 365 globalen Administratorkonten, und verwenden Sie die stärkste Form der sekundären Authentifizierung.
    
> [!NOTE]
> Obwohl sich dieser Artikel auf globale Administratorkonten konzentriert, sollten Sie berücksichtigen, ob zusätzliche Konten mit umfangreichen Berechtigungen für den Zugriff auf die Daten in Ihrem Abonnement wie eDiscovery-Administrator oder Sicherheits-oder Kompatibilitäts Administrator Konten sollte auf die gleiche Weise geschützt werden. 
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a>Schritt 1: Erstellen dedizierter Office 365 globaler Administratorkonten und verwenden nur bei Bedarf

Es gibt relativ wenige administrative Aufgaben wie das Zuweisen von Rollen zu Benutzerkonten, die globale Administratorrechte erfordern. Führen Sie daher die folgenden Schritte aus, anstatt alltägliche Benutzerkonten zu verwenden, denen die globale Administratorrolle zugewiesen wurde:
  
1. Bestimmen Sie die Gruppe von Benutzerkonten, denen die globale Administratorrolle zugewiesen wurde. Sie können dies mit dem Befehl Azure Active (Azure AD) Directory PowerShell for Graph tun:
  
  ```
  Get-AzureADDirectoryRole | where { $_.DisplayName -eq "Company Administrator" } | Get-AzureADDirectoryRoleMember | Ft DisplayName
  ```

2. Melden Sie sich bei Ihrem Office 365 Abonnement mit einem Benutzerkonto an, dem die globale Administratorrolle zugewiesen wurde.
    
3. Erstellen Sie mindestens ein und maximal fünf dedizierte Benutzerkonten für globale Administratoren. **Verwenden Sie sichere Kennwörter, die mindestens 12 Zeichen lang sind.** Weitere Informationen finden Sie unter [Erstellen eines sicheren Kennworts](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) . Speichern Sie die Kennwörter für die neuen Konten an einem sicheren Ort. 
    
4. Weisen Sie jedem der neuen dedizierten globalen Administratorbenutzerkonten die globale Administratorrolle zu.
    
5. Abmelden bei Office 365.
    
6. Melden Sie sich mit einem der neuen dedizierten globalen Administrator-Benutzerkonten an.
    
7. Für jedes vorhandene Benutzerkonto, dem die globale Administratorrolle aus Schritt 1 zugewiesen wurde:
    
  - Entfernen Sie die globale Administratorrolle.
    
  - Weisen Sie dem Konto Administratorrollen zu, die für die Funktion und Verantwortung dieses Benutzers geeignet sind. Weitere Informationen zu verschiedenen Administratorrollen in Office 365 finden Sie unter [Informationen zu Office 365 Administratorrollen](https://docs.microsoft.com/office365/admin/add-users/about-admin-roles).
    
8. Abmelden bei Office 365.
    
Das Ergebnis sollte wie folgt lauten:
  
- Die einzigen Benutzerkonten in Ihrem Abonnement, die über die Berechtigungen eines globalen Administrators verfügen, befinden sich im neuen Satz der dedizierten Konten für globale Administratoren. Überprüfen Sie dies mit dem folgenden PowerShell-Befehl:
    
  ```
  Get-AzureADDirectoryRole | where { $_.DisplayName -eq "Company Administrator" } | Get-AzureADDirectoryRoleMember | Ft DisplayName
  ```

- Alle anderen normalen Benutzerkonten für die Verwaltung Ihres Abonnements verfügen über Administratorrollen, die ihren beruflichen Zuständigkeiten zugewiesen sind.
    
Ab diesem Moment melden Sie sich mit den dedizierten globalen Administratorkonten nur für Aufgaben an, die globale Administratorrechte erfordern. Alle anderen Office 365 Verwaltung müssen durch Zuweisen weiterer Verwaltungsrollen zu Benutzerkonten erfolgen.
  
> [!NOTE]
> Dafür sind zusätzliche Schritte erforderlich, um sich als alltägliches Benutzerkonto abzumelden und sich mit einem dedizierten globalen Administratorkonto anzumelden. Dies muss jedoch nur gelegentlich für globale Administrator Vorgänge erfolgen. Beachten Sie, dass die erneute Bereitstellung Ihres Office 365-Abonnements nach einem Verstoß durch ein globales Administratorkonto viel mehr Schritte erfordert.
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-secondary-authentication"></a>Schritt 2: Konfigurieren Sie die mehrstufige Authentifizierung für ihre dedizierten Office 365 globalen Administratorkonten, und verwenden Sie die stärkste Form der sekundären Authentifizierung.

Mehrstufige Authentifizierung (MFA) erfordert zusätzliche Informationen über den Kontonamen und das Kennwort hinaus. Office 365 unterstützt die folgenden Überprüfungsmethoden:
  
- Ein Telefonanruf
    
- Ein zufällig generierter Passcode
    
- Eine Smartcard (virtuell oder physisch)
    
- Ein biometrisches Gerät
    
Wenn Sie ein kleines Unternehmen sind, das Benutzerkonten verwendet, die nur in der Cloud (dem reinen Cloud-Identitätsmodell) gespeichert sind, verwenden Sie die folgenden Schritte, um MFA mithilfe eines Telefonanrufs oder eines an ein Smartphone gesendeten Textnachrichten-Bestätigungscodes zu konfigurieren:
  
1. [Aktivieren Sie MFA](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication).
    
2. [Richten Sie die Überprüfung in zwei Schritten für Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) ein, um jedes dedizierte globale Administratorkonto für einen Telefonanruf oder eine Textnachricht als Überprüfungsmethode zu konfigurieren. 
    
Wenn Sie eine größere Organisation sind, die ein Office 365 hybrides Identitätsmodell verwendet, haben Sie weitere Überprüfungsoptionen. Wenn Sie die Sicherheitsinfrastruktur bereits für eine stärkere sekundäre Authentifizierungsmethode eingerichtet haben, führen Sie die folgenden Schritte aus:
  
1. [Aktivieren Sie MFA](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication).
    
2. [Richten Sie die Überprüfung in zwei Schritten für Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) ein, um jedes dedizierte globale Administratorkonto für die entsprechende Überprüfungsmethode zu konfigurieren. 
    
Wenn die Sicherheitsinfrastruktur für die gewünschte stärkere Überprüfungsmethode für Office 365 MFA nicht vorhanden ist und funktioniert, wird dringend empfohlen, dass Sie dedizierte globale Administratorkonten mit MFA mithilfe eines Telefonanrufs oder einer Textnachricht konfigurieren. Verifizierungscode, der als Interim-Sicherheitsmaßnahme an ein Smartphone für Ihre globalen Administratorkonten gesendet wurde. Lassen Sie Ihre dedizierten globalen Administratorkonten nicht ohne den zusätzlichen Schutz, der von MFA bereitgestellt wird.
  
Weitere Informationen finden Sie unter [Planen der mehrstufigen Authentifizierung für Office 365-Bereitstellungen](https://docs.microsoft.com/office365/admin/security-and-compliance/multi-factor-authentication-plan).
  
Informationen zum Herstellen einer Verbindung mit Office 365 Diensten mit MFA und PowerShell finden Sie in [diesem Artikel](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/).


## <a name="additional-protections-for-enterprise-organizations"></a>Zusätzliche Schutzmaßnahmen für Unternehmensorganisationen

Verwenden Sie nach den Schritten 1 und 2 diese zusätzlichen Methoden, um sicherzustellen, dass ihr globales Administratorkonto und die Konfiguration, die Sie verwenden, so sicher wie möglich sind.
  
### <a name="privileged-access-workstation"></a>Workstation mit privilegiertem Zugriff

Um sicherzustellen, dass die Ausführung von äußerst privilegierten Aufgaben so sicher wie möglich ist, verwenden Sie eine privilegierte Zugriffs Arbeitsstation (PAW). Bei einer PAW handelt es sich um einen dedizierten Computer, der nur für vertrauliche Konfigurationsaufgaben wie Office 365 Konfiguration verwendet wird, die ein globales Administratorkonto erfordert. Da dieser Computer nicht täglich für das Internet-browsen oder e-Mail verwendet wird, ist er besser vor Internetangriffen und-Bedrohungen geschützt.
  
Anweisungen zum Einrichten einer Pfote finden Sie unter [https://aka.ms/cyberpaw](https://aka.ms/cyberpaw).
  
### <a name="azure-ad-privileged-identity-management"></a>Azure AD Privileged Identity Management

Anstatt ihren globalen Administratorkonten dauerhaft die globale Administratorrolle zuweisen zu müssen, können Sie Azure AD privilegierte Identitätsverwaltung (PIM) verwenden, um bei Bedarf eine Just-in-Time-Zuweisung der globalen Administratorrolle zu aktivieren, wenn Sie benötigt.
  
Statt dass Ihre globalen Administratorkonten ein dauerhafter Administrator sind, werden Sie zu berechtigten Administratoren. Die globale Administratorrolle ist inaktiv, bis Sie von jemand benötigt wird. Anschließend führen Sie einen Aktivierungsprozess aus, um dem globalen Administratorkonto die globale Administratorrolle für eine vorgegebene Zeitspanne hinzuzufügen. Wenn die Zeit abgelaufen ist, entfernt PIM die globale Administratorrolle aus dem globalen Administratorkonto.
  
Durch die Verwendung von PIM und diesen Prozess wird die Zeit erheblich verkürzt, die ihre globalen Administratorkonten anfällig für Angriffe und die Verwendung durch böswillige Benutzer sind.
  
Weitere Informationen finden Sie unter [configure Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).
  
> [!NOTE]
> PIM steht mit Azure AD Premium P2 zur Verfügung, das im Lieferumfang von Enterprise Mobility + Security (EMS) E5 enthalten ist, oder Sie können einzelne Lizenzen für Ihre globalen Administratorkonten erwerben. 
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a>Security Information and Event Management (SIEM)-Software für Office 365 Protokollierung

Siem-Software, die auf einem Server ausgeführt wird, führt Echtzeitanalysen von Sicherheitswarnungen und Ereignissen durch, die von Anwendungen und Netzwerkhardware erstellt wurden. Damit Ihr Siem-Server Office 365 Sicherheitswarnungen und-Ereignisse in seine Analyse-und Berichtsfunktionen einbeziehen kann, integrieren Sie Azure AD in Sie Seim. Siehe [integrieren von Protokollen aus Azure-Ressourcen in Ihre Siem-Systeme](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).

## <a name="next-step"></a>Nächster Schritt

Informationen zum Einrichten der Identität für Ihr Office 365-Abonnement finden Sie unter:

- [Nur Cloud-Identitäten](cloud-only-identities.md) , wenn Sie nur die Cloud verwenden
- [Vorbereiten der Verzeichnissynchronisierung](prepare-for-directory-synchronization.md) bei Verwendung der Hybrid Identität

  
## <a name="see-also"></a>Siehe auch

[Office 365 Security Roadmap](https://docs.microsoft.com/office365/securitycompliance/security-roadmap).
