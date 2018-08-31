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
# <a name="privileged-access-management-in-office-365"></a><span data-ttu-id="1d9ea-103">Berechtigungen zugreifen Management in Office 365</span><span class="sxs-lookup"><span data-stu-id="1d9ea-103">Privileged access management in Office 365</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1d9ea-104">In diesem Thema wird die Bereitstellung und Konfiguration Anleitungen für Öffentliche Beta Features derzeit sind nur in Office 365 E5 und erweiterte Compliance-SKUs behandelt.</span><span class="sxs-lookup"><span data-stu-id="1d9ea-104">This topic covers deployment and configuration guidance for public beta features only currently available in Office 365 E5 and Advanced Compliance SKUs.</span></span>

<span data-ttu-id="1d9ea-p101">Access privilegierten Management ermöglicht die Differenzierte Sicherung Access Steuerung privilegierten Administratoraufgaben in Office 365.  Es kann Schützen Ihrer Organisation aus Verstöße, die vorhandenen privilegierten Administratorkonten stehende Zugriff auf vertrauliche Daten oder Zugriff auf wichtige Konfigurationseinstellungen verwenden können. Nach der Aktivierung der Verwaltung von Systemzugriff benötigen Benutzer anfordern Just-in-Time-Zugriff mit erhöhten Rechten und privilegierten über einen Genehmigungsworkflow Aufgaben, die hochgradig bezogenen und Zeit gebunden ist. Dadurch können Benutzer Just-in-ausreichend-zugreifen zum Ausführen der Aufgabe zur hand, ohne zu riskieren Belichtung vertrauliche Daten oder wichtige Konfigurationseinstellungen. Aktivieren der Systemzugriff Management in Office 365 aktivieren Ihrer Organisation mit 0 (null) stehende Berechtigungen Betrieb und stellen eine Ebene Verteidigung gegen Sicherheitslücken haftbar gemacht werden, aufgrund von solchen stehende Verwaltungszugriff bereit.</span><span class="sxs-lookup"><span data-stu-id="1d9ea-p101">Privileged access management allows granular access control over privileged admin tasks in Office 365.  It can help protect your organization from breaches that may use existing privileged admin accounts with standing access to sensitive data or access to critical configuration settings. After enabling privileged access management, users will need to request just-in-time access to complete elevated and privileged tasks through an approval workflow that is highly scoped and time-bound. This gives users just-enough-access to perform the task at hand, without risking exposure of sensitive data or critical configuration settings. Enabling privileged access management in Office 365 will enable your organization to operate with zero standing privileges and provide a layer of defense against vulnerabilities arising because of such standing administrative access.</span></span> 

<span data-ttu-id="1d9ea-110">In diesem Thema wird führen Sie durch Aktivieren und Konfigurieren von Systemzugriff Management in Office 365-Organisation und dienen als Leitfaden zum anfordern, genehmigen und Verwaltung des Features.</span><span class="sxs-lookup"><span data-stu-id="1d9ea-110">This topic will guide you through enabling and configuring privileged access management in your Office 365 organization and serve as a reference guide for requesting, approving, and managing the feature.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="1d9ea-111">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="1d9ea-111">Before you begin</span></span>

### <a name="limited-functionality"></a><span data-ttu-id="1d9ea-112">Eingeschränkte Funktionalität</span><span class="sxs-lookup"><span data-stu-id="1d9ea-112">Limited functionality</span></span>
<span data-ttu-id="1d9ea-p102">Während der public Beta privilegierten Access Management-Features sind nur verfügbar über [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) in Office 365. Berechtigungen auf Management behandelt die Aufgabendefinitionen auf der Ebene der Exchange-Verwaltungs-Cmdlets zugreifen. In Zukunft Office 365 releases Systemzugriff Features werden über das Administratorportal zur Verfügung stehen und andere Office 365 Arbeitslasten Dienste umfasst.</span><span class="sxs-lookup"><span data-stu-id="1d9ea-p102">During the public beta, privileged access management features are only available through [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) in Office 365. Privileged access management covers the task definitions at the level of Exchange management cmdlets. In future Office 365 releases, privileged access features will be available through the admin portal and will cover other Office 365 workloads services.</span></span>

### <a name="connecting-to-exchange-online-powershell"></a><span data-ttu-id="1d9ea-116">Herstellen einer Verbindung zu Exchange Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="1d9ea-116">Connecting to Exchange Online PowerShell</span></span>
<span data-ttu-id="1d9ea-117">Die Schritte zur Konfiguration in diesem Thema führt Sie durch die Aktivierung und Verwendung von Systemzugriff in Office 365 mit Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1d9ea-117">The configuration steps in this topic will walk you through enabling and using privileged access in Office 365 using Exchange Online PowerShell.</span></span> 

<span data-ttu-id="1d9ea-118">Führen Sie die Schritte zum Verbinden mit Exchange Online PowerShell mit den Anmeldeinformationen Ihres Office 365 zur Aktivierung und Konfiguration für Ihre Organisation Systemzugriff [Connect to Exchange Online PowerShell mehrstufige Authentifizierung verwenden](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell?view=exchange-ps) .</span><span class="sxs-lookup"><span data-stu-id="1d9ea-118">Follow the steps in [Connect to Exchange Online PowerShell using Multi-Factor authentication](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell?view=exchange-ps) to connect to Exchange Online PowerShell with your Office 365 credentials to enable and configure privileged access for your organization.</span></span>

> [!NOTE]
> <span data-ttu-id="1d9ea-p103">Sie müssen nicht die mehrstufige Authentifizierung für Office 365-Organisation mit den Schritten um Systemzugriff zu ermöglichen, während eine Verbindung mit Exchange Online PowerShell aktivieren. Herstellen einer Verbindung mit Multi-Factor Authentication erstellt ein OAuth-Token, das vom Systemzugriff für die Anmeldung Ihre Anforderungen verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="1d9ea-p103">You do not need to enable multi-factor authentication for your Office 365 organization to use the steps to enable privileged access while connecting to Exchange Online PowerShell. Connecting with multi-factor authentication creates an OAuth token that is used by privileged access for signing your requests.</span></span>

## <a name="enable-and-configure-privileged-access-management"></a><span data-ttu-id="1d9ea-121">Aktivieren und Konfigurieren der Verwaltung von Systemzugriff</span><span class="sxs-lookup"><span data-stu-id="1d9ea-121">Enable and configure privileged access management</span></span>

### <a name="step-1---create-an-approvers-group"></a><span data-ttu-id="1d9ea-122">Schritt 1: Erstellen einer genehmigenden Person Gruppe</span><span class="sxs-lookup"><span data-stu-id="1d9ea-122">Step 1 - Create an approver's group</span></span>
<span data-ttu-id="1d9ea-p104">Wählen Sie in Office 365-Admin-Portal **Gruppen** > **Gruppe hinzufügen**, erstellen Sie anschließend eine e-Mail-aktivierte Sicherheitsgruppe für die standardmäßige privilegierten Zugriff genehmigende Personen. Nach Abschluss des Vorgangs, wählen Sie **Hinzufügen** zum Erstellen und speichern Sie die Gruppe der genehmigenden Person aus.</span><span class="sxs-lookup"><span data-stu-id="1d9ea-p104">From Office 365 Admin Portal, select **Groups** > **Add a group**, then create a mail enabled security group for the default privileged access approvers. When complete, select **Add** to create and save the approver group.</span></span>

![Systemzugriff genehmigende Personen Bildschirm in Office 365-Verwaltungsportals](media/privileged-access-approvers-ui.png)

> [!NOTE] 
> <span data-ttu-id="1d9ea-p105">Zu diesem Zeitpunkt dürfen nur Benutzer mit Administratorrechten Anforderungen von Office 365 privilegierten Zugriff zu genehmigen. Jeder Benutzer, der Teil der Gruppe der genehmigenden Personen ist wird in zukünftigen Genehmigen von zugriffsanforderungen sein.</span><span class="sxs-lookup"><span data-stu-id="1d9ea-p105">At this time, only users with administrative access are allowed to approve requests from Office 365 priviledged access. In future any user who is part of the Approvers’ group will be able to approve access requests.</span></span>

### <a name="step-2---enable-privileged-access-in-office-365"></a><span data-ttu-id="1d9ea-128">Schritt 2: Aktivieren von Systemzugriff in Office 365</span><span class="sxs-lookup"><span data-stu-id="1d9ea-128">Step 2 - Enable privileged access in Office 365</span></span>
<span data-ttu-id="1d9ea-129">Systemzugriff muss explizit aktiviert werden mit der Standardgruppe genehmigende Person sowie eine Reihe von Systemkonten, die Sie aus der Systemzugriff Management Zugriffssteuerung ausgeschlossen werden möchten.</span><span class="sxs-lookup"><span data-stu-id="1d9ea-129">Privileged access needs to be explicitly turned on with the default approver group and including a set of system accounts that you’d want to be excluded from the privileged access management access control.</span></span> 

<span data-ttu-id="1d9ea-130">Führen Sie den folgenden Befehl in Exchange Online PowerShell Systemzugriff aktivieren und der genehmigenden Person Gruppe zuweisen:</span><span class="sxs-lookup"><span data-stu-id="1d9ea-130">Run the following command in Exchange Online PowerShell to enable privileged access and to assign the approver's group:</span></span>
```
Enable-ElevatedAccessControl -AdminGroup '<default approver group>' -SystemAccounts @('<systemAccountUPN1>','<systemAccountUPN2>')
```
<span data-ttu-id="1d9ea-131">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="1d9ea-131">Example:</span></span>
```
Enable-ElevatedAccessControl -AdminGroup 'pamapprovers@fabrikam.onmicrosoft.com' -SystemAccounts @('sys1@fabrikamorg.onmicrosoft.com', sys2@fabrikamorg.onmicrosoft.com')
```

> [!NOTE]
> <span data-ttu-id="1d9ea-132">Systemkonten, dass das Feature um sicherzustellen, dass bestimmte der Automatisierung innerhalb Ihrer Organisation zur Verfügung gestellt wird ohne Abhängigkeit an Systemzugriff arbeiten können, aber es wird empfohlen, dass solche Ausschlüsse außergewöhnliche werden und die zulässigen genehmigt und überwacht werden sollte Führen Sie regelmäßige.</span><span class="sxs-lookup"><span data-stu-id="1d9ea-132">System accounts feature is made available to ensure certain automations within your organizations can work without dependency on privileged access, however it is recommended that such exclusions be exceptional and those allowed should be approved and audited regularly.</span></span>

### <a name="step-3---create-an-approval-policy"></a><span data-ttu-id="1d9ea-133">Schritt 3: Erstellen Sie eine Richtlinie für die Genehmigung</span><span class="sxs-lookup"><span data-stu-id="1d9ea-133">Step 3 - Create an approval policy</span></span>
<span data-ttu-id="1d9ea-p106">Eine Genehmigung Richtlinie können Sie die Genehmigung von bestimmten Anforderungen an einzelne Aufgaben bezogenen definieren. Die Typ von Genehmigungsoptionen werden **automatisch** oder **manuell**.</span><span class="sxs-lookup"><span data-stu-id="1d9ea-p106">An approval policy allows you to define the specific approval requirements scoped at individual tasks. The approval type options are **Auto** or **Manual**.</span></span> 

<span data-ttu-id="1d9ea-136">Führen Sie den folgenden Befehl in Exchange Online PowerShell, um eine Genehmigung zu definieren:</span><span class="sxs-lookup"><span data-stu-id="1d9ea-136">Run the following command in Exchange Online PowerShell to define an approval policy:</span></span>
```
New-ElevatedAccessApprovalPolicy -Task 'Exchange\<exchange management cmdlet name>' -ApprovalType <Manual, Auto> -ApproverGroup '<default/custom approver group>'
```
<span data-ttu-id="1d9ea-137">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="1d9ea-137">Example:</span></span>
```
New-ElevatedAccessApprovalPolicy -Task 'Exchange\New-MoveRequest' -ApprovalType Manual -ApproverGroup 'mbmanagers@fabrikamorg.onmicrosoft.com'
```

## <a name="using-privileged-access-in-your-office-365-organization"></a><span data-ttu-id="1d9ea-138">Verwenden von Systemzugriff in Office 365-Organisation</span><span class="sxs-lookup"><span data-stu-id="1d9ea-138">Using privileged access in your Office 365 organization</span></span>

### <a name="requesting-elevation-authorization-to-execute-tasks"></a><span data-ttu-id="1d9ea-139">Anfordern von Elevation Autorisierung zum Ausführen von Aufgaben</span><span class="sxs-lookup"><span data-stu-id="1d9ea-139">Requesting elevation authorization to execute tasks</span></span>
<span data-ttu-id="1d9ea-p107">Aktiviert, privilegierten Zugriff erfordert Genehmigungen für das Ausführen aller Aufgaben, die eine Genehmigung zugeordnete Richtlinie definiert wurde. Benutzer müssen zum Ausführen von Aufgaben, die eine Genehmigung Richtlinie müssen anfordern und zugriffsgenehmigung, um die erforderlichen Berechtigungen zum Ausführen der Aufgabe lassen erteilt werden.</span><span class="sxs-lookup"><span data-stu-id="1d9ea-p107">Once enabled, privileged access requires approvals for executing any task that has an associated approval policy defined. Users needing to execute tasks included in the an approval policy must request and be granted access approval in order to have permissions necessary to execute the task.</span></span>

<span data-ttu-id="1d9ea-142">Führen Sie den folgenden Befehl in Exchange Online PowerShell zum Erstellen und senden eine Aufforderung zur Genehmigung an die Gruppe der genehmigenden Person:</span><span class="sxs-lookup"><span data-stu-id="1d9ea-142">Run the following command in Exchange Online PowerShell to create and submit an approval request to the approver's group:</span></span>
```
New-ElevatedAccessRequest -Task 'Exchange\<exchange management cmdlet name>' -Reason '<appropriate reason>' -DurationHours <duration in hours>
```
<span data-ttu-id="1d9ea-143">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="1d9ea-143">Example:</span></span>
```
New-ElevatedAccessRequest -Task 'Exchange\New-MoveRequest' -Reason 'Attempting to fix the user mailbox error' -DurationHours 4
```
### <a name="view-status-of-elevation-requests"></a><span data-ttu-id="1d9ea-144">Anzeigen des Status der Elevation-Anforderungen</span><span class="sxs-lookup"><span data-stu-id="1d9ea-144">View status of elevation requests</span></span>
<span data-ttu-id="1d9ea-145">Nach dem Erstellen einer genehmigungsanforderung kann Elevation Anforderungsstatus überprüft werden mithilfe der zugeordnete mit Anforderung-ID</span><span class="sxs-lookup"><span data-stu-id="1d9ea-145">After an approval request is created, elevation request status can be reviewed using the associated with request ID.</span></span>

<span data-ttu-id="1d9ea-146">Führen Sie den folgenden Befehl in Exchange Online PowerShell, um eine Anforderung Genehmigungsstatus für eine bestimmte Anforderung ID anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="1d9ea-146">Run the following command in Exchange Online PowerShell to view a approval request status for a specific request ID:</span></span>
```
Get-ElevatedAccessRequest -Identity <request ID> | select RequestStatus
```
<span data-ttu-id="1d9ea-147">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="1d9ea-147">Example:</span></span>
```
Get-ElevatedAccessRequest -Identity 28560ed0-419d-4cc3-8f5b-603911cbd450 | select RequestStatus
```

### <a name="approving-an-elevation-authorization-request"></a><span data-ttu-id="1d9ea-148">Eine Erhöhung Autorisierung Anforderung genehmigen</span><span class="sxs-lookup"><span data-stu-id="1d9ea-148">Approving an elevation authorization request</span></span>
<span data-ttu-id="1d9ea-149">Wenn eine Aufforderung zur Genehmigung erstellt wird, Mitglied der Gruppe relevanten genehmigende Person erhält eine e-Mail-Benachrichtigung und genehmigen die Anforderung der Anforderung ID zugeordnet werden kann</span><span class="sxs-lookup"><span data-stu-id="1d9ea-149">When an approval request is created, members of the relevant approver group will receive an email notification and can approve the request associated with the request ID.</span></span> 

<span data-ttu-id="1d9ea-150">Führen Sie den folgenden Befehl in Exchange Online PowerShell, um eine Erhöhung Autorisierung Anforderung genehmigen:</span><span class="sxs-lookup"><span data-stu-id="1d9ea-150">Run the following command in Exchange Online PowerShell to approve an elevation authorization request:</span></span>
```
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```
<span data-ttu-id="1d9ea-151">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="1d9ea-151">Example:</span></span>
```
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```
### <a name="denying-an-elevation-authorization-request"></a><span data-ttu-id="1d9ea-152">Das Verweigern einer Erhöhung Autorisierung Anforderung</span><span class="sxs-lookup"><span data-stu-id="1d9ea-152">Denying an elevation authorization request</span></span>
<span data-ttu-id="1d9ea-153">Wenn eine Aufforderung zur Genehmigung erstellt wird, können Mitglieder der Gruppe relevanten genehmigende Person die Anforderung der Anforderung ID zugeordnet verweigern.</span><span class="sxs-lookup"><span data-stu-id="1d9ea-153">When an approval request is created, members of the relevant approver group can deny the request associated with the request ID.</span></span> 

<span data-ttu-id="1d9ea-154">Führen Sie den folgenden Befehl in Exchange Online PowerShell, um eine Erhöhung Autorisierung Anforderung zu verweigern:</span><span class="sxs-lookup"><span data-stu-id="1d9ea-154">Run the following command in Exchange Online PowerShell to deny an elevation authorization request:</span></span>
```
Deny-ElevatedAccessRequest -RequestId <request id> -Comment '<denial comment>'
```
<span data-ttu-id="1d9ea-155">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="1d9ea-155">Example:</span></span>
```
Deny-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<denial comment>'
```

### <a name="running-the-task"></a><span data-ttu-id="1d9ea-156">Ausführen des Tasks</span><span class="sxs-lookup"><span data-stu-id="1d9ea-156">Running the task</span></span>
<span data-ttu-id="1d9ea-p108">Nachdem die Zustimmung eingeholt wurde, der anfordernde Benutzer kann den beabsichtigten Vorgang ausführen und Systemzugriff autorisieren und Ausführen die Aufgabe im Auftrag eines Benutzers wird. Die Genehmigung bleibt gültig für den angeforderten Dauer (Dauer der Standardwert lautet 4 Stunden), in dem die anfordernde Person die vorgesehene Aufgabe mehrmals führen kann. Alle solchen Ausführungen sind angemeldet und für Sicherheit und Compliance Überwachung zur Verfügung gestellt.</span><span class="sxs-lookup"><span data-stu-id="1d9ea-p108">After approval is granted, the requesting user can execute the intended task and privileged access will authorize and execute the task on users’ behalf. The approval remains valid for the requested duration (default duration is 4 hours), during which the requester can execute the intended task multiple times. All such executions are logged and made available for security and compliance auditing.</span></span> 

### <a name="disable-privileged-access-in-office-365"></a><span data-ttu-id="1d9ea-160">Deaktivieren Sie Systemzugriff in Office 365</span><span class="sxs-lookup"><span data-stu-id="1d9ea-160">Disable privileged access in Office 365</span></span>
<span data-ttu-id="1d9ea-p109">Bei Bedarf können Sie Systemzugriff Management in Office 365 deaktivieren. Deaktivieren von Berechtigungen wird Access keine zugehörigen Genehmigung Richtlinien oder eine genehmigende Person Gruppen gelöscht.</span><span class="sxs-lookup"><span data-stu-id="1d9ea-p109">If needed, you can disable privileged access management in Office 365. Disabling privileged access does not delete any associated approval policies or approver groups.</span></span>

<span data-ttu-id="1d9ea-163">Führen Sie den folgenden Befehl in Exchange Online Powershell, um Systemzugriff zu deaktivieren:</span><span class="sxs-lookup"><span data-stu-id="1d9ea-163">Run the following command in Exchange Online Powershell to disable privileged access:</span></span>

```
Disable-ElevatedAccessControl
```
## <a name="managed-access-to-microsoft-graph-in-microsoft-azure"></a><span data-ttu-id="1d9ea-164">Zugriff auf Microsoft Graph in Microsoft Azure verwaltete</span><span class="sxs-lookup"><span data-stu-id="1d9ea-164">Managed access to Microsoft Graph in Microsoft Azure</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1d9ea-165">Dieser Abschnitt enthält Informationen zu einem Feature derzeit nur in der Vorschau.</span><span class="sxs-lookup"><span data-stu-id="1d9ea-165">This section covers details about a feature currently available only in preview.</span></span>

<span data-ttu-id="1d9ea-p110">Verwaltete Zugriff auf Microsoft Graph in Microsoft Azure ist ein Dienst, der einen fein abgestufte Grad von Kontrolle über ihre Office 365-Daten ausüben Organisationen unterstützt. Dieses System ermöglicht Anwendungsentwickler Insights mit diesen Daten eingehen.</span><span class="sxs-lookup"><span data-stu-id="1d9ea-p110">Managed access to Microsoft Graph in Microsoft Azure is a service that helps organizations exert a granular level of control over their Office 365 data. This system allows application developers to forge insights with that data.</span></span> 

<span data-ttu-id="1d9ea-p111">In diesem System verwendet Zugriff auf Office 365 mit Berechtigungen zur Kontrolle über ihre Daten durch den Genehmigungsworkflow bereichsbezogenen Zugriff auf Office 365-Daten mit Admin Aufsicht assert. Anforderungen für Daten ist in Anwendungen werden installiert und benötigen Zugriff auf Office 365-Daten.</span><span class="sxs-lookup"><span data-stu-id="1d9ea-p111">This system uses Office 365 privileged access to assert control over their data through its approval workflow, allowing scoped access to Office 365 data with admin oversight. Requests for data come in when applications are installed and require access to Office 365 data.</span></span>

### <a name="view-request-details"></a><span data-ttu-id="1d9ea-170">Die Anforderungsdetails anzeigen</span><span class="sxs-lookup"><span data-stu-id="1d9ea-170">View request details</span></span>
<span data-ttu-id="1d9ea-171">Anzeigen der Details der Access-Anforderungen für Office 365-Daten.</span><span class="sxs-lookup"><span data-stu-id="1d9ea-171">View details of the access requests for Office 365 data.</span></span>

<span data-ttu-id="1d9ea-172">Führen Sie den folgenden Befehl im Exchange Online Powershell, um Datenanfragen anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="1d9ea-172">Run the following command in Exchange Online Powershell to view data requests:</span></span>
```
Get-ElevatedAccessRequest | where {$_.RequestedAccess -like '*Data Access Request*'} | select RequestorUPN, Service, RequestedAccess | fl
```
<span data-ttu-id="1d9ea-173">Beispiel für die Ausgabe:</span><span class="sxs-lookup"><span data-stu-id="1d9ea-173">Example output:</span></span>
```
RequestorUPN    : admin@contoso.com
Service         : Office365
RequestedAccess : Data Access Request
```

### <a name="approve-data-access-requests"></a><span data-ttu-id="1d9ea-174">Genehmigen von datenzugriffsanforderungen</span><span class="sxs-lookup"><span data-stu-id="1d9ea-174">Approve data access requests</span></span>
<span data-ttu-id="1d9ea-175">Alle datenzugriffsanforderungen können über die standardmäßigen Systemzugriff Genehmigung Cmdlets genehmigt werden.</span><span class="sxs-lookup"><span data-stu-id="1d9ea-175">All data access requests can be approved through the standard privileged access approval cmdlets.</span></span>

<span data-ttu-id="1d9ea-176">Führen Sie den folgenden Befehl in Exchange Online Powershell, um alle Daten Anforderungen für bestimmte Requestor genehmigen:</span><span class="sxs-lookup"><span data-stu-id="1d9ea-176">Run the following command in Exchange Online Powershell to approve all data requests for specific requestor:</span></span>

```
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```
<span data-ttu-id="1d9ea-177">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="1d9ea-177">Example:</span></span>
```
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```

## <a name="getting-help-and-providing-feedback"></a><span data-ttu-id="1d9ea-178">Abrufen von Hilfe und Feedback</span><span class="sxs-lookup"><span data-stu-id="1d9ea-178">Getting help and providing feedback</span></span>
<span data-ttu-id="1d9ea-p112">Wir wissen, dass während der Betaphase öffentliche Sie möglicherweise auf einen gelegentliche Fehler stoßen oder Feedback und Vorschläge, wie wir Systemzugriff Management verbessern können. Wir schätzen Ihr Feedback und Fördern Sie es mit uns in Kontakt freigeben:</span><span class="sxs-lookup"><span data-stu-id="1d9ea-p112">We recognize that during the public beta you may come across an occasional bug or have feedback and suggestions on how we can improve privileged access management. We value your feedback and encourage you to share it with us:</span></span>
- <span data-ttu-id="1d9ea-181">Veröffentlichen Sie Ihr Feedback Ad Vorschläge in der [Gruppe für Office-Vorschau Yammer](https://www.yammer.com/officeenterprisenda/#/threads/inGroup?type=in_group&feedId=14435206).</span><span class="sxs-lookup"><span data-stu-id="1d9ea-181">Post your feedback ad suggestions in the [Office Preview Yammer Group](https://www.yammer.com/officeenterprisenda/#/threads/inGroup?type=in_group&feedId=14435206).</span></span>
- <span data-ttu-id="1d9ea-182">Ihre Fehlerberichte unter Bereichspfad "Office 365 privilegierten Zugriff verwalten" auf die [Office Preview VSO](https://office-previews.visualstudio.com/previews)-Datei.</span><span class="sxs-lookup"><span data-stu-id="1d9ea-182">File your bug reports under area path “Office 365 Privileged Access Management” on the [Office Preview VSO](https://office-previews.visualstudio.com/previews).</span></span>

## <a name="frequently-asked-questions"></a><span data-ttu-id="1d9ea-183">Häufig gestellte Fragen</span><span class="sxs-lookup"><span data-stu-id="1d9ea-183">Frequently asked questions</span></span>

### <a name="what-skus-do-i-need-to-use-privileged-access-in-office-365"></a><span data-ttu-id="1d9ea-184">Welche SKUs Systemzugriff in Office 365 verwenden, müssen?</span><span class="sxs-lookup"><span data-stu-id="1d9ea-184">What SKUs do I need to use privileged access in Office 365?</span></span>
<span data-ttu-id="1d9ea-185">Access privilegierten Management in Office 365 ist derzeit nur für Kunden mit E5 und erweiterte Compliance-SKUs verfügbar.</span><span class="sxs-lookup"><span data-stu-id="1d9ea-185">Privileged access management in Office 365 is currently only available for customers with E5 and Advanced Compliance SKUs.</span></span>

### <a name="when-will-privileged-access-be-available-for-office-365-workloads-beyond-exchange"></a><span data-ttu-id="1d9ea-186">Wann wird Systemzugriff für Office 365-Arbeitslasten außerhalb Exchange verfügbar sein?</span><span class="sxs-lookup"><span data-stu-id="1d9ea-186">When will privileged access be available for Office 365 workloads beyond Exchange?</span></span>
<span data-ttu-id="1d9ea-p113">Wir möchten dieses Feature in anderen Office 365-Arbeitslasten bald anbieten. Wenn wir zur Freigabe einer Zeitskala bereit sind, wird sie der Übersicht über die Office 365 verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="1d9ea-p113">We plan to offer this feature in other Office 365 workloads soon. When we’re ready to share a timeline, it will be available through the Office 365 roadmap.</span></span>

### <a name="how-is-this-different-from-azure-active-directorys-privileged-identity-management"></a><span data-ttu-id="1d9ea-189">Wo liegt der Unterschied von Azure Active Directory privilegierten Identity Management?</span><span class="sxs-lookup"><span data-stu-id="1d9ea-189">How is this different from Azure Active Directory’s Privileged Identity Management?</span></span>
<span data-ttu-id="1d9ea-p114">Berechtigungen auf Management in Office 365 und [Azure AD privilegierten Identitätsmanagement](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure) Ergänzung miteinander durch den Zugriff steuern Just-in-Time-Zugriff in anderen Bereichen zugreifen. Zusammen bieten sie einen stabilen Satz von Steuerelementen für den Schutz Ihrer Daten.</span><span class="sxs-lookup"><span data-stu-id="1d9ea-p114">Privileged access management in Office 365 and [Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure) complement each other by providing access control with just-in-time access at different scopes. Together they provide a robust set of controls for protecting your data.</span></span>

<span data-ttu-id="1d9ea-p115">Access privilegierten Management in Office 365 definiert und bezogenen auf Aufgabenebene, während auf der Rollenebene Azure AD privilegierten Identitätsmanagement angewendet, die Möglichkeit wird, mehrere Aufgaben ausgeführt werden kann.  Azure AD privilegierten Identity Management in erster Linie ermöglicht die Verwaltung von Zugriffe für AD-Rollen und Rollengruppen beim Berechtigungen Access Management in Office 365 wird die auf Vorgangsebene angewendet.</span><span class="sxs-lookup"><span data-stu-id="1d9ea-p115">Privileged access management in Office 365 can be defined and scoped at the task level, while Azure AD Privileged Identity Management applies at the role level with the ability to execute multiple tasks.  Azure AD Privileged Identity Management primarily allows managing accesses for AD roles and role groups while privileged access management in Office 365 is applied at the task level.</span></span>

 - <span data-ttu-id="1d9ea-194">**Aktivieren Berechtigungen Management in Office 365 beim bereits mit Azure AD privilegierten Identitätsmanagement zugreifen:** Systemzugriff Management in Office 365 hinzufügen kann, stellen eine andere differenzierte Ebene des Schutzes und audit-Funktionen für den privilegierten Zugriff auf Office 365-Daten.</span><span class="sxs-lookup"><span data-stu-id="1d9ea-194">**Enabling privileged access management in Office 365 while already using Azure AD Privileged Identity Management:** Adding privileged access management in Office 365 can provide another granular layer of protection and audit capabilities for privileged access to Office 365 data.</span></span>

- <span data-ttu-id="1d9ea-195">**Aktivieren der Azure AD privilegierten Identitätsmanagement bei Verwendung von bereits privilegierten Access Management in Office 365:**  Hinzufügen von Azure AD privilegierten Identitätsmanagement zu Berechtigungen kann Access Management in Office 365 privilegierten Zugriff auf Daten außerhalb von Office 365 erweitern, die in erster Linie nach Rolle oder die Identität eines Benutzers definiert ist.</span><span class="sxs-lookup"><span data-stu-id="1d9ea-195">**Enabling Azure AD Privileged Identity Management while already using privileged access management in Office 365:**  Adding Azure AD Privileged Identity Management to privileged access management in Office 365 can extend privileged access to data outside of Office 365 that’s primarily defined by a user’s role or identity.</span></span> 

### <a name="do-i-need-to-be-a-global-admin-to-manage-privileged-access-in-office-365"></a><span data-ttu-id="1d9ea-196">Müssen ein globaler Administrator Systemzugriff in Office 365 verwalten werden?</span><span class="sxs-lookup"><span data-stu-id="1d9ea-196">Do I need to be a Global Admin to manage privileged access in Office 365?</span></span>
<span data-ttu-id="1d9ea-p116">Bei der Vorschau müssen Sie globaler Administrator-Berechtigung zum Systemzugriff in Office 365 verwalten können. Benutzer, die in einer genehmigenden Personen Gruppe enthaltenen müssen ein globaler Administrator überprüfen und Genehmigen von Anfragen werden.</span><span class="sxs-lookup"><span data-stu-id="1d9ea-p116">During the preview you need to have Global Admin privilege to be able to manage privileged access in Office 365. Users who are included in an approvers’ group don't need to be a Global Admin to review and approve requests.</span></span> 

### <a name="how-is-privileged-access-management-in-office-365-related-to-customer-lockbox"></a><span data-ttu-id="1d9ea-199">Wie wird Systemzugriff Management in Office 365 im Zusammenhang mit Kunden Lockbox?</span><span class="sxs-lookup"><span data-stu-id="1d9ea-199">How is privileged access management in Office 365 related to Customer Lockbox?</span></span>
<span data-ttu-id="1d9ea-p117">[Kunden-Lockbox](https://support.office.com/article/Office-365-Customer-Lockbox-Requests-36f9cdd1-e64c-421b-a7e4-4a54d16440a2) ermöglicht ein Maß an Steuerung des Zugriffs für Organisationen, die für den Zugriff auf Daten von ihrem Dienstanbieter, d. h. Microsoft. Access privilegierten Management in Office 365 differenzierte Zugriffssteuerung innerhalb einer Organisation für alle Office 365 privilegierten Vorgänge ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="1d9ea-p117">[Customer Lockbox](https://support.office.com/article/Office-365-Customer-Lockbox-Requests-36f9cdd1-e64c-421b-a7e4-4a54d16440a2) allows a level of access control for organizations for access to to data by their service provider, i.e. Microsoft. Privileged access management in Office 365 allows granular access control within an organization for all Office 365 privileged tasks.</span></span>