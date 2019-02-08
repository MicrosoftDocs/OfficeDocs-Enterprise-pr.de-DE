---
title: Schützen Ihrer globalen Office 365-Administratorkonten
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 4/10/2018
ms.audience: Admin
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
description: Globaler Administratorzugriff auf Ihre Office 365-Abonnements mit dieser drei Schritte zu schützen.
ms.openlocfilehash: 41168643fb8867017865860624c8b436460fa0b8
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897518"
---
# <a name="protect-your-office-365-global-administrator-accounts"></a>Schützen Ihrer globalen Office 365-Administratorkonten

 **Zusammenfassung:** Schützen Sie Ihre Office 365-Abonnements vor Angriffen, die basierend auf die Gefährdung als globaler Administrator an. 
  
Sicherheitsverstößen gegen ein Office 365-Abonnement, einschließlich Informationen zu sammeln und Phishing-Angriffe erfolgen in der Regel durch die Anmeldeinformationen des Office 365-Konto globaler Administrator gefährden. Sicherheit in der Cloud ist eine Partnerschaft zwischen Ihnen und Microsoft:
  
- Microsoft Cloud-Dienste werden auf Grundlage von vertrauen und Sicherheit erstellt. Microsoft bietet Sie Sicherheitssteuerelemente und Funktionen, mit denen Sie Ihre Daten und Anwendungen zu schützen.
    
- Sie besitzen die Daten und Identitäten und die Verantwortung für den Schutz von ihnen, die Sicherheit Ihrer lokalen Ressourcen und die Sicherheit der Cloud-Komponenten, die Sie steuern.
    
Microsoft bietet Funktionen zum Schutz Ihrer Organisation, aber sie sind nur wirksam, wenn Sie diese verwenden. Wenn Sie sie nicht verwenden, können Sie anfällig sein. Um Ihre globalen Administratorkonten zu schützen, ist Microsoft hier Sie nähere Informationen zum zu unterstützen:
  
1. Erstellen Sie dedizierte Office 365 globaler Administrator Benutzerkonten und verwenden sie bei Bedarf.
    
2. Konfigurieren Sie mehrstufige Authentifizierung für Ihre dedizierten Office 365 globaler Administratorkonten und verwenden Sie die sicherste sekundäre Authentifizierung.
    
3. Aktivieren und Konfigurieren von Office 365-Cloud-App-Sicherheit zum Überwachen von Kontoaktivitäten verdächtigen globaler Administrator.
    
> [!NOTE]
> Obwohl in diesem Artikel auf globale Administratorkonten gerichtet ist, berücksichtigen Sie auch, ob zusätzliche Konten mit umfassende Berechtigungen für den Datenzugriff im Rahmen Ihres Abonnements, wie eDiscovery-Administrator oder Sicherheits- oder kompatibilitätsanforderungen Administratorkonten, sollte die gleiche Weise geschützt werden. 
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a>Schritt 1. Erstellen Sie dedizierte Office 365 globaler Administrator Benutzerkonten und verwenden sie bei Bedarf

Relativ wenige administrative Aufgaben wie das Zuweisen von Rollen zu Benutzerkonten, die globale Administratorrechte erforderlich sind. Aus diesem Grund statt alltägliche Benutzerkonten, die die globalen Administratorrolle zugewiesen wurden, führen Sie diese Schritte:
  
1. Ermitteln der Benutzerkonten, die die globalen Administratorrolle zugewiesen wurden. Hierzu können Sie mit diesem Befehl an der Microsoft Azure Active Directory-Modul für Windows PowerShell-Eingabeaufforderung:
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

2. Melden Sie sich bei Ihrem Office 365-Abonnement mit einem Benutzerkonto, das die globalen Administratorrolle zugewiesen wurde.
    
3. Erstellen Sie mindestens einen und bis zu fünf dedizierte Benutzerkonten globaler Administrator. **Verwendung sicherer Kennwörter mindestens 12 Zeichen lang.** Weitere Informationen finden Sie unter [Erstellen eines sicheren Kennworts](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) . Speichern Sie die Kennwörter für das neue Konto an einem sicheren Ort. 
    
4. Weisen Sie der globalen Administratorrolle für jeden der neue dedizierte globaler Administratorbenutzerkonten.
    
5. Melden Sie bei Office 365 ab.
    
6. Melden Sie sich mit einer neuen dedizierten globaler Administrator Benutzerkonten.
    
7. Für alle vorhandenen Benutzerkonten, die die globalen Administratorrolle aus Schritt 1 zugewiesen wurde:
    
  - Entfernen der globalen Administratorrolle.
    
  - Zuweisen von Administratorrollen für das Konto, das für dieses Benutzers Funktion und Verantwortung geeignet sind. Weitere Informationen zu verschiedenen Administratorrollen in Office 365 finden Sie unter [Informationen zu Office 365-Administratorrollen](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).
    
8. Melden Sie bei Office 365 ab.
    
Das Ergebnis sollte wie folgt lauten:
  
- Die einzige Benutzerkonten im Rahmen Ihres Abonnements mit der globalen Administratorrolle sind die neuen Satz von dedizierten globalen Administratorkonten. Überprüfen Sie dies mit dem folgenden PowerShell-Befehl aus:
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

- Alle anderen normalen Benutzerkonten für die Verwaltung Ihres Abonnements verfügen über Administratorrollen, die ihren beruflichen Zuständigkeiten zugewiesen sind.
    
Aus ab diesem Zeitpunkt melden Sie sich mit den dedizierten globalen Administratorkonten nur für Aufgaben vorgestellt, die globale Administratorrechte erforderlich. Alle anderen Office 365-Verwaltung muss durch Zuweisen von anderen Administratorrollen zu Benutzerkonten erfolgen.
  
> [!NOTE]
> Ja, dies ist erforderlich, zusätzliche Schritte zum als Ihr Benutzerkonto alltägliche abmelden und melden Sie sich mit einem dedizierten globale Administratorkonto ein. Aber dies nur gelegentlich für globaler Administrator Vorgänge ausgeführt werden soll. Erwägen Sie, Ihre Office 365-Abonnements wiederherstellen, nachdem eine globaler Administrator Konto Verletzung viel weitere Schritte erforderlich sind. 
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-secondary-authentication"></a>Schritt 2. Konfigurieren Sie mehrstufige Authentifizierung für Ihre dedizierten Office 365 globaler Administratorkonten und verwenden Sie die sicherste sekundäre Authentifizierung

Mehrstufige Authentifizierung (mehrstufiger Authentifizierung das) für Ihre globalen Administratorkonten benötigt zusätzliche Informationen über den Kontonamen und das Kennwort. Office 365 unterstützt die folgenden Überprüfungsmethoden:
  
- Ein Telefonanruf
    
- Ein zufällig generierter Passcode
    
- Eine Smartcard (virtuell oder physisch)
    
- Ein biometrisches Gerät
    
Wenn Sie ein kleines Unternehmen, das mithilfe von Benutzerkonten in der Cloud (Identitätsmodell Cloud) gespeichert sind, verwenden Sie folgende Schritte aus, um mithilfe eines Telefonanrufs oder einen Text-Nachricht gesendet, um ein Smartphone Überprüfungscode mehrstufiger Authentifizierung das konfigurieren:
  
1. [Mehrstufiger Authentifizierung das Aktivieren](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).
    
2. [Einrichten der Überprüfung für Office 365 – Schritt 2](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) zum Konfigurieren der einzelnen dediziert globale Administratorkonto ein Telefonanruf oder Textnachricht als die Überprüfungsmethode. 
    
Wenn Sie einer größeren Organisation, die ein Office 365-Identität Hybridmodell verwendet wird sind, müssen Sie weitere Überprüfungsoptionen für die. Wenn Sie die Sicherheitsinfrastruktur für sekundäre stärkere Authentifizierungsmethode vorhanden, verwenden Sie folgende Schritte aus:
  
1. [Mehrstufiger Authentifizierung das Aktivieren](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).
    
2. [Einrichten der Überprüfung für Office 365 – Schritt 2](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) zum Konfigurieren der einzelnen dediziert globalen Administratorkonto für die entsprechenden Überprüfungsmethode. 
    
Wenn die Sicherheitsinfrastruktur für die gewünschte stärkere Überprüfungsmethode nicht und Funktionsweise von Office 365 mehrstufiger Authentifizierung das ist, wird dringend empfohlen, Sie dedizierte globale Administratorkonten mit mehrstufiger Authentifizierung das Konfigurieren mithilfe eines Telefongesprächs oder einer Textnachricht Überprüfungscode an einem Smartphone für Ihre globalen Administratorkonten als Sicherheitsmaßnahme vorläufige gesendet. Lassen Sie Ihre dedizierten globalen Administratorkonten nicht ohne zusätzliche Schutz von mehrstufiger Authentifizierung das bereitgestellt.
  
Weitere Informationen finden Sie unter [Planen der mehrstufigen Authentifizierung für Office 365-Bereitstellungen](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba).
  
Zum Verbinden mit Office 365-Diensten mit mehrstufiger Authentifizierung das und PowerShell finden Sie unter [in diesem Artikel](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/).
  
## <a name="step-3-monitor-for-suspicious-global-administrator-account-activity"></a>Schritt 3. Monitor für Kontoaktivitäten verdächtigen globaler administrator

Office 365-Cloud-App-Sicherheit können Sie die Richtlinien erstellen, um Sie verdächtige Verhalten, das im Rahmen Ihres Abonnements zu benachrichtigen. Cloud App-Sicherheit in Office 365 E5 integriert ist, aber es ist auch als separater Dienst verfügbar. Wenn Sie nicht über Office 365 E5 verfügen, können Sie beispielsweise einzelne Cloud App-Sicherheit Lizenzen für die Benutzerkonten erwerben, die die globaler Administrator Sicherheitsadministrator und Compliance-Administratorrollen zugewiesen sind.
  
Wenn Sie Cloud App-Sicherheit in Office 365-Abonnement haben, verwenden Sie folgende Schritte aus:
  
1. Melden Sie sich bei Office 365-Portal mit einem Konto an, die Rolle des Security-Administrator oder Compliance-Administrator zugewiesen ist.
    
2. [Sicherheit in Office 365-Cloud-App zu aktivieren](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c).
    
3. Überprüfen Sie Ihre [Anomalie Erkennungsrichtlinien in Office 365-Cloud-App-Sicherheit](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6) Sie per e-Mail abweichenden Muster privilegierten administrative Aktivität benachrichtigt. 
    
Um ein Benutzerkonto hinzuzufügen, die Sicherheitsadministrator-Rolle, die mit einem dedizierten globalen Administratorkonto und mehrstufiger Authentifizierung das [Office 365 PowerShell eine Verbindung herstellen](https://technet.microsoft.com/library/dn975125.aspx#step3) , geben Sie den Benutzerprinzipalnamen des Benutzerkontos, und führen Sie diese Befehle: 
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upn -RoleName "Security Administrator"
```

Um die Compliance-Administratorrolle ein Benutzerkonto hinzuzufügen, geben Sie den Benutzerprinzipalnamen des Benutzerkontos, und führen Sie diese Befehle:
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress  $upn -RoleName "Compliance Administrator"
```

## <a name="additional-protections-for-enterprise-organizations"></a>Zusätzliche Schutzebenen für Unternehmen

Nachdem die Schritte 1 bis 3, um sicherzustellen, dass Ihre globale Administratorkonto ein, und die Konfiguration, die Sie ausführen, verwenden sie diese zusätzlichen Methoden verwenden, sind so sicher wie möglich.
  
### <a name="privileged-access-workstation-paw"></a>Systemzugriff Arbeitsstation (KRALLE)

Um sicherzustellen, dass die Ausführung von umfangreichen Tasks so sicher wie möglich ist, verwenden Sie eine KRALLE. Eine KRALLE ist einem fest zugeordneten Computer, der nur für vertrauliche Konfigurationsaufgaben, wie etwa Office 365-Konfiguration verwendet wird, die ein globales Administratorkonto erforderlich sind. Da diese Computer nicht täglich für die Suche im Internet oder per e-Mail verwendet wird, ist es besser von Internetangriffen und Bedrohungen geschützt.
  
Informationen dazu, wie Sie eine KRALLE einrichten, finden Sie unter [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw).
  
### <a name="azure-ad-privileged-identity-management-pim"></a>Identitätsmanagement Azure AD-Berechtigungen (PIM)

Azure AD PIM können Sie statt der globalen Administratorkonten dauerhaft die globalen Administratorrolle zugewiesen werden bei Bedarf, Just-in-Time-Zuweisung von der globalen Administratorrolle aktivieren, wenn es erforderlich ist.
  
Anstatt Ihre globalen Administratorkonten, wird eine permanente Admin werden sie zu auswählbaren Administratoren. Die globalen Administratorrolle ist inaktiv, bis jemand benötigen. Sie führen dann Aktivierungsprozess um das globale Administratorkonto die globalen Administratorrolle für einen festgelegten Zeitraum hinzuzufügen. Nach Ablauf die Zeit entfernt PIM die globalen Administratorrolle aus das globale Administratorkonto ein.
  
PIM verwenden und dabei erheblich verringert die Zeitdauer, die Ihre globalen Administratorkonten anfällig sind für Angriffe auf und Verwenden von böswilligen Benutzern.
  
Weitere Informationen finden Sie unter [Konfigurieren von Azure AD privilegierten Identitätsmanagement](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).
  
> [!NOTE]
> PIM steht mit Azure Active Directory Premium P2, das mit Enterprise-Mobilität + E5 Sicherheit (zur Abstimmung) enthalten ist, oder Sie können einzelne Lizenzen erwerben, für Ihre globalen Administratorkonten. 
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a>Sicherheit und Ereignissen (SIEM) Verwaltungssoftware für Office 365-Protokollierung

SIEM-Software auf einem Server ausführen Führt in Echtzeit Analyse der Sicherheitswarnungen und Ereignisse, die von Anwendungen und Netzwerkhardware erstellt. Damit Ihre SIEM Server Sicherheitshinweise für Office 365 und Ereignisse in der Analyse und Berichtsfunktionen enthalten kann, integrieren Sie diese in Ihrem System SIEM:
  
- Azure AD
    
    Weitere Informationen finden Sie unter [integrieren Protokolle von Azure Ressourcen in Ihre SIEM-Systeme](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).
    
- Office 365 Cloud App Security
    
    Weitere Informationen finden Sie unter [Integrieren Ihrer SIEM Server mit Office 365-Cloud-App-Sicherheit](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532).
    
## <a name="next-step"></a>Nächster Schritt

Finden Sie unter [bewährte Methoden für Office 365-Sicherheit](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3).
  

