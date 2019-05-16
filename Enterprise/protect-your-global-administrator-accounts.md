---
title: Schützen Ihrer globalen Office 365-Administratorkonten
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 4/10/2018
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
description: Schützen Sie den globalen Administratorzugriff auf Ihr Office 365-Abonnement mit diesen drei Schritten.
ms.openlocfilehash: bb1b19a7ac0ec8e32c23303e8acf2b7ee42f0532
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071021"
---
# <a name="protect-your-office-365-global-administrator-accounts"></a>Schützen Ihrer globalen Office 365-Administratorkonten

 **Zusammenfassung:** Schützen Sie Ihr Office 365-Abonnement vor Angriffen, die auf der Gefährdung durch ein globales Administratorkonto basieren. 
  
Sicherheitsverstöße gegen ein Office 365-Abonnement, einschließlich Informationen zum Sammeln und Phishing-Angriffen, werden in der Regel durch Kompromittierung der Anmeldeinformationen eines globalen Administratorkontos von Office 365 durchgeführt. Sicherheit in der Cloud ist eine Partnerschaft zwischen Ihnen und Microsoft:
  
- Microsoft Cloud Services basieren auf der Grundlage von Vertrauen und Sicherheit. Microsoft stellt Sicherheitskontrollen und-Funktionen zur Verfügung, mit denen Sie Ihre Daten und Anwendungen schützen können.
    
- Sie besitzen Ihre Daten und Identitäten und die Verantwortung für den Schutz, die Sicherheit Ihrer lokalen Ressourcen und die Sicherheit von Cloud-Komponenten, die Sie steuern.
    
Microsoft bietet Funktionen zum Schutz Ihrer Organisation, Sie sind jedoch nur dann wirksam, wenn Sie Sie verwenden. Wenn Sie Sie nicht verwenden, sind Sie möglicherweise anfällig für Angriffe. Um Ihre globalen Administratorkonten zu schützen, steht Ihnen Microsoft mit detaillierten Anweisungen zur Verfügung:
  
1. Erstellen Sie dedizierte globale Administratorkonten für Office 365, und verwenden Sie Sie nur bei Bedarf.
    
2. Konfigurieren Sie die mehrstufige Authentifizierung für ihre dedizierten Office 365-globalen Administratorkonten, und verwenden Sie die stärkste Form der sekundären Authentifizierung.
    
3. Aktivieren und konfigurieren Sie die Office 365 Cloud App Security, um die Aktivität verdächtiger globaler Administratorkonten zu überwachen.
    
> [!NOTE]
> Obwohl dieser Artikel auf globale Administratorkonten ausgerichtet ist, sollten Sie auch berücksichtigen, ob zusätzliche Konten mit weit reichenden Berechtigungen für den Zugriff auf die Daten in Ihrem Abonnement wie eDiscovery-Administrator oder Sicherheit oder Compliance Administratorkonten sollten auf die gleiche Weise geschützt werden. 
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a>Schritt 1: Erstellen Sie dedizierte globale Administratorkonten für Office 365, und verwenden Sie Sie nur bei Bedarf.

Es gibt relativ wenige Verwaltungsaufgaben, wie das Zuweisen von Rollen zu Benutzerkonten, die globale Administratorrechte erfordern. Führen Sie daher anstelle der täglichen Benutzerkonten, denen die Rolle "globaler Administrator" zugewiesen wurde, die folgenden Schritte aus:
  
1. Bestimmen Sie den Satz von Benutzerkonten, denen die Rolle globaler Administrator zugewiesen wurde. Sie können dies mit diesem Befehl an der Microsoft Azure Active Directory-Modul für Windows PowerShell-Eingabeaufforderungen tun:
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

2. Melden Sie sich bei Ihrem Office 365-Abonnement mit einem Benutzerkonto an, dem die Rolle "globaler Administrator" zugewiesen wurde.
    
3. Erstellen Sie mindestens eine und maximal fünf dedizierte globale Administrator-Benutzerkonten. **Verwenden Sie sichere Kennwörter, die mindestens 12 Zeichen lang sind.** Weitere Informationen finden Sie unter [Erstellen eines sicheren Kennworts](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) . Speichern Sie die Kennwörter für die neuen Konten an einem sicheren Ort. 
    
4. Weisen Sie die globale Administratorrolle jedem der neuen dedizierten Benutzerkonten für globale Administratoren zu.
    
5. Abmelden von Office 365.
    
6. Melden Sie sich mit einem der neuen dedizierten globalen Administrator-Benutzerkonten an.
    
7. Für jedes vorhandene Benutzerkonto, dem die Rolle "globaler Administrator" aus Schritt 1 zugewiesen wurde:
    
  - Entfernen Sie die Rolle globaler Administrator.
    
  - Weisen Sie dem Konto Administratorrollen zu, die für die Aufgaben Funktion und Verantwortlichkeit dieses Benutzers geeignet sind. Weitere Informationen zu den verschiedenen Administratorrollen in Office 365 finden Sie unter Informationen [zu Office 365-Administratorrollen](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).
    
8. Abmelden von Office 365.
    
Das Ergebnis sollte:
  
- Die einzigen Benutzerkonten in Ihrem Abonnement, die über die Berechtigungen eines globalen Administrators verfügen, befinden sich im neuen Satz der dedizierten Konten für globale Administratoren. Überprüfen Sie dies mit dem folgenden PowerShell-Befehl:
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

- Alle anderen normalen Benutzerkonten für die Verwaltung Ihres Abonnements verfügen über Administratorrollen, die ihren beruflichen Zuständigkeiten zugewiesen sind.
    
Ab diesem Moment melden Sie sich mit den dedizierten globalen Administratorkonten nur für Aufgaben an, die globale Administratorrechte erfordern. Alle anderen Office 365-Administration müssen durch Zuweisen von anderen Administratorrollen zu Benutzerkonten erfolgen.
  
> [!NOTE]
> Ja, dies erfordert zusätzliche Schritte, um sich als alltägliches Benutzerkonto abzumelden und sich mit einem dedizierten globalen Administratorkonto anzumelden. Dies muss jedoch nur gelegentlich für globale Administrator Vorgänge erfolgen. Bedenken Sie, dass das Wiederherstellen Ihres Office 365-Abonnements nach einer Verletzung globaler Administratorkonten viele weitere Schritte erfordert. 
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-secondary-authentication"></a>Schritt 2: Konfigurieren Sie die mehrstufige Authentifizierung für ihre dedizierten Office 365-globalen Administratorkonten, und verwenden Sie die stärkste Form der sekundären Authentifizierung.

Multi-Factor Authentication (MFA) für Ihre globalen Administratorkonten erfordert zusätzliche Informationen über den Kontonamen und das Kennwort hinaus. Office 365 unterstützt diese Überprüfungsmethoden:
  
- Ein Telefonanruf
    
- Ein zufällig generierter Passcode
    
- Eine Smartcard (virtuell oder physisch)
    
- Ein biometrisches Gerät
    
Wenn Sie ein kleines Unternehmen sind, das Benutzerkonten verwendet, die nur in der Cloud gespeichert sind (das Cloud-Identitätsmodell), verwenden Sie die folgenden Schritte zum Konfigurieren von MFA mithilfe eines Telefonanrufs oder eines Textnachrichten-Überprüfungscodes, der an ein Smartphone gesendet wird:
  
1. [Aktivieren Sie MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).
    
2. Richten Sie die Überprüfung in [zwei Schritten für Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) ein, um jedes dedizierte globale Administratorkonto für Telefonanrufe oder Textnachrichten als Überprüfungsmethode zu konfigurieren. 
    
Wenn Sie eine größere Organisation sind, die ein Office 365-Hybrid Identitätsmodell verwendet, haben Sie weitere Überprüfungsoptionen. Wenn die Sicherheitsinfrastruktur für eine stärkere sekundäre Authentifizierungsmethode bereits vorhanden ist, führen Sie die folgenden Schritte aus:
  
1. [Aktivieren Sie MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).
    
2. [Richten Sie die Überprüfung in zwei Schritten für Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) ein, um jedes dedizierte globale Administratorkonto für die entsprechende Überprüfungsmethode zu konfigurieren. 
    
Wenn die Sicherheitsinfrastruktur für die gewünschte stärkere Überprüfungsmethode nicht vorhanden und für Office 365 MFA funktioniert, wird dringend empfohlen, dass Sie dedizierte globale Administratorkonten mit MFA mithilfe eines Telefonanrufs oder einer Textnachricht konfigurieren. Überprüfungscode, der für Ihre globalen Administratorkonten an ein Smartphone gesendet wird, als vorläufige Sicherheitsmaßnahme. Lassen Sie Ihre dedizierten globalen Administratorkonten nicht ohne zusätzlichen Schutz durch MFA.
  
Weitere Informationen finden Sie unter [Planen der mehrstufigen Authentifizierung für Office 365-Bereitstellungen](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba).
  
Informationen zum Herstellen einer Verbindung mit Office 365-Diensten mit MFA und PowerShell finden Sie in [diesem Artikel](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/).
  
## <a name="step-3-monitor-for-suspicious-global-administrator-account-activity"></a>Schritt 3: Überwachung der Aktivität verdächtiger globaler Administratorkonten

Mit Office 365 Cloud App Security können Sie Richtlinien erstellen, die Sie über verdächtiges Verhalten in Ihrem Abonnement informieren. Cloud App Security ist in Office 365 E5 integriert, steht aber auch als separater Dienst zur Verfügung. Wenn Sie beispielsweise nicht über Office 365 E5 verfügen, können Sie einzelne Cloud-App-Sicherheits Lizenzen für die Benutzerkonten erwerben, denen die Rollen "globaler Administrator", "Sicherheitsadministrator" und "Compliance-Administrator" zugewiesen sind.
  
Wenn Sie über Cloud-App-Sicherheit in Ihrem Office 365-Abonnement verfügen, führen Sie die folgenden Schritte aus:
  
1. Melden Sie sich beim Microsoft 365 Admin Center mit einem Konto an, dem die Rolle "Sicherheitsadministrator" oder "Compliance-Administrator" zugewiesen ist.
    
2. [Aktivieren Sie Office 365 Cloud App Security](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c).
    
3. Überprüfung der [Anomalie-Erkennungsrichtlinien in Office 365 Cloud App Security](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6) , um Sie per e-Mail über anomale Muster der privilegierten Verwaltungsaktivität zu informieren. 
    
Wenn Sie der Sicherheits Administrator Rolle ein Benutzerkonto hinzufügen möchten, stellen Sie eine [Verbindung mit Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx#step3) mit einem dedizierten globalen Administrator Konto und MFA her, geben Sie den Benutzerprinzipalnamen des Benutzerkontos ein, und führen Sie dann die folgenden Befehle aus: 
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upn -RoleName "Security Administrator"
```

Geben Sie zum Hinzufügen eines Benutzerkontos zur Rolle "Compliance-Administrator" den Benutzerprinzipalnamen des Benutzerkontos ein, und führen Sie dann die folgenden Befehle aus:
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress  $upn -RoleName "Compliance Administrator"
```

## <a name="additional-protections-for-enterprise-organizations"></a>Zusätzliche Schutzmaßnahmen für Unternehmensorganisationen

Nach den Schritten 1-3, verwenden Sie diese zusätzlichen Methoden, um sicherzustellen, dass ihr globales Administratorkonto und die Konfiguration, die Sie verwenden, so sicher wie möglich sind.
  
### <a name="privileged-access-workstation-paw"></a>Workstation mit privilegiertem Zugriff (PAW)

Um sicherzustellen, dass die Ausführung hoch privilegierter Aufgaben so sicher wie möglich ist, verwenden Sie eine Paw. Eine Pfote ist ein dedizierter Computer, der nur für vertrauliche Konfigurationsaufgaben wie Office 365-Konfiguration verwendet wird, die ein globales Administratorkonto erfordert. Da dieser Computer nicht täglich für das Surfen im Internet oder per e-Mail verwendet wird, ist er besser vor Internetangriffen und-Bedrohungen geschützt.
  
Anweisungen zum Einrichten einer Pfote finden Sie unter [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw).
  
### <a name="azure-ad-privileged-identity-management-pim"></a>Azure AD Privileged Identity Management (PIM)

Anstatt ihren globalen Administratorkonten die globale Administratorrolle dauerhaft zuzuweisen, können Sie Azure AD PIM verwenden, um die bedarfsgerechte Zuweisung der globalen Administratorrolle bei Bedarf zu aktivieren.
  
Statt der globalen Administratorkonten, die ein permanenter admin sind, werden Sie zu geeigneten Administratoren. Die globale Administratorrolle ist inaktiv, bis jemand Sie benötigt. Anschließend führen Sie einen Aktivierungsprozess aus, um die globale Administratorrolle für eine festgelegte Zeitdauer dem globalen Administratorkonto hinzuzufügen. Wenn die Zeit abgelaufen ist, entfernt PIM die globale Administratorrolle aus dem globalen Administratorkonto.
  
Durch die Verwendung von PIM und diesem Prozess wird der Zeitraum, in dem Ihre globalen Administratorkonten anfällig für Angriffe und die Verwendung durch böswillige Benutzer sind, deutlich reduziert.
  
Weitere Informationen finden Sie unter [configure Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).
  
> [!NOTE]
> PIM ist mit Azure Active Directory Premium P2 verfügbar, das in Enterprise Mobility + Security (EMS) E5 enthalten ist, oder Sie können einzelne Lizenzen für Ihre globalen Administratorkonten erwerben. 
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a>Security Information and Event Management (SIEM)-Software für Office 365-Protokollierung

Siem-Software, die auf einem Server ausgeführt wird, führt eine Echtzeitanalyse von Sicherheitswarnungen und Ereignissen aus, die von Anwendungen und Netzwerkhardware erstellt wurden. Damit Ihr Siem-Server Office 365-Sicherheitswarnungen und-Ereignisse in seine Analyse-und Berichtfunktionen einbinden kann, integrieren Sie diese in Ihr Siem-System:
  
- Azure AD
    
    Weitere Informationen finden Sie unter [integrieren von Protokollen aus Azure-Ressourcen in Ihre Siem-Systeme](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).
    
- Office 365 Cloud App Security
    
    Weitere Informationen finden Sie unter [integrieren Ihres Siem-Servers in Office 365 Cloud App Security](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532).
    
## <a name="next-step"></a>Nächster Schritt

Weitere Informationen finden Sie unter [bewährte Methoden für die Sicherheit für Office 365](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3).
  

