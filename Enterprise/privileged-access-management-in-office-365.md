---
title: Berechtigungen zugreifen Management in Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 7/13/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Strat_O365_IP
ms.custom: Ent_Solutions
ms.assetid: ''
description: Verwenden Sie in diesem Thema erfahren Sie mehr über die Systemzugriff Management-Funktion in Office 365
ms.openlocfilehash: 22286d4f91ffa0bd3c49f028681d20e36d14283d
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915390"
---
# <a name="privileged-access-management-in-office-365"></a>Berechtigungen zugreifen Management in Office 365

> [!IMPORTANT]
> In diesem Thema wird die Bereitstellung und Konfiguration Anleitungen für Öffentliche Beta Features derzeit sind nur in Office 365 E5 und erweiterte Compliance-SKUs behandelt.

Access privilegierten Management ermöglicht die Differenzierte Sicherung Access Steuerung privilegierten Administratoraufgaben in Office 365.  Es kann Schützen Ihrer Organisation aus Verstöße, die vorhandenen privilegierten Administratorkonten stehende Zugriff auf vertrauliche Daten oder Zugriff auf wichtige Konfigurationseinstellungen verwenden können. Nach der Aktivierung der Verwaltung von Systemzugriff benötigen Benutzer anfordern Just-in-Time-Zugriff mit erhöhten Rechten und privilegierten über einen Genehmigungsworkflow Aufgaben, die hochgradig bezogenen und Zeit gebunden ist. Dadurch können Benutzer Just-in-ausreichend-zugreifen zum Ausführen der Aufgabe zur hand, ohne zu riskieren Belichtung vertrauliche Daten oder wichtige Konfigurationseinstellungen. Aktivieren der Systemzugriff Management in Office 365 aktivieren Ihrer Organisation mit 0 (null) stehende Berechtigungen Betrieb und stellen eine Ebene Verteidigung gegen Sicherheitslücken haftbar gemacht werden, aufgrund von solchen stehende Verwaltungszugriff bereit. 

In diesem Thema wird führen Sie durch Aktivieren und Konfigurieren von Systemzugriff Management in Office 365-Organisation und dienen als Leitfaden zum anfordern, genehmigen und Verwaltung des Features. 

## <a name="before-you-begin"></a>Bevor Sie beginnen

### <a name="limited-functionality"></a>Eingeschränkte Funktionalität
Während der public Beta privilegierten Access Management-Features sind nur verfügbar über [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) in Office 365. Berechtigungen auf Management behandelt die Aufgabendefinitionen auf der Ebene der Exchange-Verwaltungs-Cmdlets zugreifen. In Zukunft Office 365 releases Systemzugriff Features werden über das Administratorportal zur Verfügung stehen und andere Office 365 Arbeitslasten Dienste umfasst.

### <a name="connecting-to-exchange-online-powershell"></a>Herstellen einer Verbindung zu Exchange Online PowerShell
Die Schritte zur Konfiguration in diesem Thema führt Sie durch die Aktivierung und Verwendung von Systemzugriff in Office 365 mit Exchange Online PowerShell. 

Führen Sie die Schritte zum Verbinden mit Exchange Online PowerShell mit den Anmeldeinformationen Ihres Office 365 zur Aktivierung und Konfiguration für Ihre Organisation Systemzugriff [Connect to Exchange Online PowerShell mehrstufige Authentifizierung verwenden](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell?view=exchange-ps) .

> [!NOTE]
> Sie müssen nicht die mehrstufige Authentifizierung für Office 365-Organisation mit den Schritten um Systemzugriff zu ermöglichen, während eine Verbindung mit Exchange Online PowerShell aktivieren. Herstellen einer Verbindung mit Multi-Factor Authentication erstellt ein OAuth-Token, das vom Systemzugriff für die Anmeldung Ihre Anforderungen verwendet wird.

## <a name="enable-and-configure-privileged-access-management"></a>Aktivieren und Konfigurieren der Verwaltung von Systemzugriff

### <a name="step-1---create-an-approvers-group"></a>Schritt 1: Erstellen einer genehmigenden Person Gruppe
Wählen Sie in Office 365-Admin-Portal **Gruppen** > **Gruppe hinzufügen**, erstellen Sie anschließend eine e-Mail-aktivierte Sicherheitsgruppe für die standardmäßige privilegierten Zugriff genehmigende Personen. Nach Abschluss des Vorgangs, wählen Sie **Hinzufügen** zum Erstellen und speichern Sie die Gruppe der genehmigenden Person aus.

![Systemzugriff genehmigende Personen Bildschirm in Office 365-Verwaltungsportals](media/privileged-access-approvers-ui.png)

> [!NOTE] 
> Zu diesem Zeitpunkt dürfen nur Benutzer mit Administratorrechten Anforderungen von Office 365 privilegierten Zugriff zu genehmigen. Jeder Benutzer, der Teil der Gruppe der genehmigenden Personen ist wird in zukünftigen Genehmigen von zugriffsanforderungen sein.

### <a name="step-2---enable-privileged-access-in-office-365"></a>Schritt 2: Aktivieren von Systemzugriff in Office 365
Systemzugriff muss explizit aktiviert werden mit der Standardgruppe genehmigende Person sowie eine Reihe von Systemkonten, die Sie aus der Systemzugriff Management Zugriffssteuerung ausgeschlossen werden möchten. 

Führen Sie den folgenden Befehl in Exchange Online PowerShell Systemzugriff aktivieren und der genehmigenden Person Gruppe zuweisen:
```
Enable-ElevatedAccessControl -AdminGroup '<default approver group>' -SystemAccounts @('<systemAccountUPN1>','<systemAccountUPN2>')
```
Beispiel:
```
Enable-ElevatedAccessControl -AdminGroup 'pamapprovers@fabrikam.onmicrosoft.com' -SystemAccounts @('sys1@fabrikamorg.onmicrosoft.com', sys2@fabrikamorg.onmicrosoft.com')
```

> [!NOTE]
> Systemkonten, dass das Feature um sicherzustellen, dass bestimmte der Automatisierung innerhalb Ihrer Organisation zur Verfügung gestellt wird ohne Abhängigkeit an Systemzugriff arbeiten können, aber es wird empfohlen, dass solche Ausschlüsse außergewöhnliche werden und die zulässigen genehmigt und überwacht werden sollte Führen Sie regelmäßige.

### <a name="step-3---create-an-approval-policy"></a>Schritt 3: Erstellen Sie eine Richtlinie für die Genehmigung
Eine Genehmigung Richtlinie können Sie die Genehmigung von bestimmten Anforderungen an einzelne Aufgaben bezogenen definieren. Die Typ von Genehmigungsoptionen werden **automatisch** oder **manuell**. 

Führen Sie den folgenden Befehl in Exchange Online PowerShell, um eine Genehmigung zu definieren:
```
New-ElevatedAccessApprovalPolicy -Task 'Exchange\<exchange management cmdlet name>' -ApprovalType <Manual, Auto> -ApproverGroup '<default/custom approver group>'
```
Beispiel:
```
New-ElevatedAccessApprovalPolicy -Task 'Exchange\New-MoveRequest' -ApprovalType Manual -ApproverGroup 'mbmanagers@fabrikamorg.onmicrosoft.com'
```

## <a name="using-privileged-access-in-your-office-365-organization"></a>Verwenden von Systemzugriff in Office 365-Organisation

### <a name="requesting-elevation-authorization-to-execute-tasks"></a>Anfordern von Elevation Autorisierung zum Ausführen von Aufgaben
Aktiviert, privilegierten Zugriff erfordert Genehmigungen für das Ausführen aller Aufgaben, die eine Genehmigung zugeordnete Richtlinie definiert wurde. Benutzer müssen zum Ausführen von Aufgaben, die eine Genehmigung Richtlinie müssen anfordern und zugriffsgenehmigung, um die erforderlichen Berechtigungen zum Ausführen der Aufgabe lassen erteilt werden.

Führen Sie den folgenden Befehl in Exchange Online PowerShell zum Erstellen und senden eine Aufforderung zur Genehmigung an die Gruppe der genehmigenden Person:
```
New-ElevatedAccessRequest -Task 'Exchange\<exchange management cmdlet name>' -Reason '<appropriate reason>' -DurationHours <duration in hours>
```
Beispiel:
```
New-ElevatedAccessRequest -Task 'Exchange\New-MoveRequest' -Reason 'Attempting to fix the user mailbox error' -DurationHours 4
```
### <a name="view-status-of-elevation-requests"></a>Anzeigen des Status der Elevation-Anforderungen
Nach dem Erstellen einer genehmigungsanforderung kann Elevation Anforderungsstatus überprüft werden mithilfe der zugeordnete mit Anforderung-ID

Führen Sie den folgenden Befehl in Exchange Online PowerShell, um eine Anforderung Genehmigungsstatus für eine bestimmte Anforderung ID anzuzeigen:
```
Get-ElevatedAccessRequest -Identity <request ID> | select RequestStatus
```
Beispiel:
```
Get-ElevatedAccessRequest -Identity 28560ed0-419d-4cc3-8f5b-603911cbd450 | select RequestStatus
```

### <a name="approving-an-elevation-authorization-request"></a>Eine Erhöhung Autorisierung Anforderung genehmigen
Wenn eine Aufforderung zur Genehmigung erstellt wird, Mitglied der Gruppe relevanten genehmigende Person erhält eine e-Mail-Benachrichtigung und genehmigen die Anforderung der Anforderung ID zugeordnet werden kann 

Führen Sie den folgenden Befehl in Exchange Online PowerShell, um eine Erhöhung Autorisierung Anforderung genehmigen:
```
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```
Beispiel:
```
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```
### <a name="denying-an-elevation-authorization-request"></a>Das Verweigern einer Erhöhung Autorisierung Anforderung
Wenn eine Aufforderung zur Genehmigung erstellt wird, können Mitglieder der Gruppe relevanten genehmigende Person die Anforderung der Anforderung ID zugeordnet verweigern. 

Führen Sie den folgenden Befehl in Exchange Online PowerShell, um eine Erhöhung Autorisierung Anforderung zu verweigern:
```
Deny-ElevatedAccessRequest -RequestId <request id> -Comment '<denial comment>'
```
Beispiel:
```
Deny-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<denial comment>'
```

### <a name="running-the-task"></a>Ausführen des Tasks
Nachdem die Zustimmung eingeholt wurde, der anfordernde Benutzer kann den beabsichtigten Vorgang ausführen und Systemzugriff autorisieren und Ausführen die Aufgabe im Auftrag eines Benutzers wird. Die Genehmigung bleibt gültig für den angeforderten Dauer (Dauer der Standardwert lautet 4 Stunden), in dem die anfordernde Person die vorgesehene Aufgabe mehrmals führen kann. Alle solchen Ausführungen sind angemeldet und für Sicherheit und Compliance Überwachung zur Verfügung gestellt. 

### <a name="disable-privileged-access-in-office-365"></a>Deaktivieren Sie Systemzugriff in Office 365
Bei Bedarf können Sie Systemzugriff Management in Office 365 deaktivieren. Deaktivieren von Berechtigungen wird Access keine zugehörigen Genehmigung Richtlinien oder eine genehmigende Person Gruppen gelöscht.

Führen Sie den folgenden Befehl in Exchange Online Powershell, um Systemzugriff zu deaktivieren:

```
Disable-ElevatedAccessControl
```
## <a name="managed-access-to-microsoft-graph-in-microsoft-azure"></a>Zugriff auf Microsoft Graph in Microsoft Azure verwaltete

> [!IMPORTANT]
> Dieser Abschnitt enthält Informationen zu einem Feature derzeit nur in der Vorschau.

Verwaltete Zugriff auf Microsoft Graph in Microsoft Azure ist ein Dienst, der einen fein abgestufte Grad von Kontrolle über ihre Office 365-Daten ausüben Organisationen unterstützt. Dieses System ermöglicht Anwendungsentwickler Insights mit diesen Daten eingehen. 

In diesem System verwendet Zugriff auf Office 365 mit Berechtigungen zur Kontrolle über ihre Daten durch den Genehmigungsworkflow bereichsbezogenen Zugriff auf Office 365-Daten mit Admin Aufsicht assert. Anforderungen für Daten ist in Anwendungen werden installiert und benötigen Zugriff auf Office 365-Daten.

### <a name="view-request-details"></a>Die Anforderungsdetails anzeigen
Anzeigen der Details der Access-Anforderungen für Office 365-Daten.

Führen Sie den folgenden Befehl im Exchange Online Powershell, um Datenanfragen anzuzeigen:
```
Get-ElevatedAccessRequest | where {$_.RequestedAccess -like '*Data Access Request*'} | select RequestorUPN, Service, RequestedAccess | fl
```
Beispiel für die Ausgabe:
```
RequestorUPN    : admin@contoso.com
Service         : Office365
RequestedAccess : Data Access Request
```

### <a name="approve-data-access-requests"></a>Genehmigen von datenzugriffsanforderungen
Alle datenzugriffsanforderungen können über die standardmäßigen Systemzugriff Genehmigung Cmdlets genehmigt werden.

Führen Sie den folgenden Befehl in Exchange Online Powershell, um alle Daten Anforderungen für bestimmte Requestor genehmigen:

```
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```
Beispiel:
```
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```

## <a name="getting-help-and-providing-feedback"></a>Abrufen von Hilfe und Feedback
Wir wissen, dass während der Betaphase öffentliche Sie möglicherweise auf einen gelegentliche Fehler stoßen oder Feedback und Vorschläge, wie wir Systemzugriff Management verbessern können. Wir schätzen Ihr Feedback und Fördern Sie es mit uns in Kontakt freigeben:
- Veröffentlichen Sie Ihr Feedback Ad Vorschläge in der [Gruppe für Office-Vorschau Yammer](https://www.yammer.com/officeenterprisenda/#/threads/inGroup?type=in_group&feedId=14435206).
- Ihre Fehlerberichte unter Bereichspfad "Office 365 privilegierten Zugriff verwalten" auf die [Office Preview VSO](https://office-previews.visualstudio.com/previews)-Datei.

## <a name="frequently-asked-questions"></a>Häufig gestellte Fragen

### <a name="what-skus-do-i-need-to-use-privileged-access-in-office-365"></a>Welche SKUs Systemzugriff in Office 365 verwenden, müssen?
Access privilegierten Management in Office 365 ist derzeit nur für Kunden mit E5 und erweiterte Compliance-SKUs verfügbar.

### <a name="when-will-privileged-access-be-available-for-office-365-workloads-beyond-exchange"></a>Wann wird Systemzugriff für Office 365-Arbeitslasten außerhalb Exchange verfügbar sein?
Wir möchten dieses Feature in anderen Office 365-Arbeitslasten bald anbieten. Wenn wir zur Freigabe einer Zeitskala bereit sind, wird sie der Übersicht über die Office 365 verfügbar sein.

### <a name="how-is-this-different-from-azure-active-directorys-privileged-identity-management"></a>Wo liegt der Unterschied von Azure Active Directory privilegierten Identity Management?
Berechtigungen auf Management in Office 365 und [Azure AD privilegierten Identitätsmanagement](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure) Ergänzung miteinander durch den Zugriff steuern Just-in-Time-Zugriff in anderen Bereichen zugreifen. Zusammen bieten sie einen stabilen Satz von Steuerelementen für den Schutz Ihrer Daten.

Access privilegierten Management in Office 365 definiert und bezogenen auf Aufgabenebene, während auf der Rollenebene Azure AD privilegierten Identitätsmanagement angewendet, die Möglichkeit wird, mehrere Aufgaben ausgeführt werden kann.  Azure AD privilegierten Identity Management in erster Linie ermöglicht die Verwaltung von Zugriffe für AD-Rollen und Rollengruppen beim Berechtigungen Access Management in Office 365 wird die auf Vorgangsebene angewendet.

 - **Aktivieren Berechtigungen Management in Office 365 beim bereits mit Azure AD privilegierten Identitätsmanagement zugreifen:** Systemzugriff Management in Office 365 hinzufügen kann, stellen eine andere differenzierte Ebene des Schutzes und audit-Funktionen für den privilegierten Zugriff auf Office 365-Daten.

- **Aktivieren der Azure AD privilegierten Identitätsmanagement bei Verwendung von bereits privilegierten Access Management in Office 365:**  Hinzufügen von Azure AD privilegierten Identitätsmanagement zu Berechtigungen kann Access Management in Office 365 privilegierten Zugriff auf Daten außerhalb von Office 365 erweitern, die in erster Linie nach Rolle oder die Identität eines Benutzers definiert ist. 

### <a name="do-i-need-to-be-a-global-admin-to-manage-privileged-access-in-office-365"></a>Müssen ein globaler Administrator Systemzugriff in Office 365 verwalten werden?
Bei der Vorschau müssen Sie globaler Administrator-Berechtigung zum Systemzugriff in Office 365 verwalten können. Benutzer, die in einer genehmigenden Personen Gruppe enthaltenen müssen ein globaler Administrator überprüfen und Genehmigen von Anfragen werden. 

### <a name="how-is-privileged-access-management-in-office-365-related-to-customer-lockbox"></a>Wie wird Systemzugriff Management in Office 365 im Zusammenhang mit Kunden Lockbox?
[Kunden-Lockbox](https://support.office.com/article/Office-365-Customer-Lockbox-Requests-36f9cdd1-e64c-421b-a7e4-4a54d16440a2) ermöglicht ein Maß an Steuerung des Zugriffs für Organisationen, die für den Zugriff auf Daten von ihrem Dienstanbieter, d. h. Microsoft. Access privilegierten Management in Office 365 differenzierte Zugriffssteuerung innerhalb einer Organisation für alle Office 365 privilegierten Vorgänge ermöglicht.