---
title: 'Gewusst wie: Überprüfen von Office 365-Dienststatus'
ms.author: kfollis
author: kfollis
manager: scotv
ms.date: 6/15/2018
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365P_ServiceHealthModern
- O365M_ServiceHealthModern
- O365E_ViewStatusServices
- O365E_ServiceHealthModern
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
- IWA160
ms.assetid: 932ad3ad-533c-418a-b938-6e44e8bc33b0
description: Zeigen Sie den Status des Office 365-Dienste vor dem Aufruf von Support, um herauszufinden, ob es eine Unterbrechung Active-Dienst ist
ms.openlocfilehash: d01fe8e269ace922ab92cca779d6f8fea8b6802e
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540783"
---
# <a name="how-to-check-office-365-service-health"></a><span data-ttu-id="c5650-103">Gewusst wie: Überprüfen von Office 365-Dienststatus</span><span class="sxs-lookup"><span data-stu-id="c5650-103">How to check Office 365 service health</span></span>

<span data-ttu-id="c5650-p101">Sie können die Integrität der Office 365, Yammer, Microsoft Dynamics CRM und Intune Microsoft Cloud Services anzeigen, klicken Sie auf der Office 365 ** Health Service ** Seite in der Verwaltungskonsole. Wenn Sie Probleme mit einer Cloud-Dienst sind, können Sie den Dienststatus, um zu bestimmen, ob dies ein bekanntes Problem mit einer Auflösung ausgeführt, ist bevor Sie Support anrufen oder Zeit zur Problembehandlung ausgeben überprüfen.</span><span class="sxs-lookup"><span data-stu-id="c5650-p101">You can view the health of Office 365, Yammer, Microsoft Dynamics CRM, and Microsoft Intune cloud services on the Office 365 ** Service health ** page in the admin center. If you are experiencing problems with a cloud service, you can check the service health to determine whether this is a known issue with a resolution in progress before you call support or spend time troubleshooting.</span></span> 
  
### <a name="how-to-check-service-health"></a><span data-ttu-id="c5650-106">Gewusst wie: Überprüfen des Dienststatus</span><span class="sxs-lookup"><span data-stu-id="c5650-106">How to check service health</span></span>

1. <span data-ttu-id="c5650-107">Wechseln Sie zu [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage) und melden Sie sich mit einem Konto des Farmadministrators ein.</span><span class="sxs-lookup"><span data-stu-id="c5650-107">Go to [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage) and sign in with an admin account.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="c5650-p102">Personen, die der Administratorrolle oder globaler Administrator zugewiesen sind, können Dienststatus anzeigen. Damit Exchange, SharePoint und Skype für Business-Admins Dienststatus anzeigen können, müssen sie auch die Dienst-Administratorrolle zugewiesen werden.</span><span class="sxs-lookup"><span data-stu-id="c5650-p102">People who are assigned the global admin or service administrator role can view service health. To allow Exchange, SharePoint, and Skype for Business admins to view service health, they must also be assigned the Service admin role.</span></span> 
  
2. <span data-ttu-id="c5650-p103">Um Dienststatus, im Administrationscenter zu öffnen, wechseln Sie zur **Integrität** \> **Dienststatus**, oder klicken Sie auf den Dienststatus auf das Dashboard Home Karte. Die Karte Dashboard gibt an, ob es ein Problem Active-Dienst und Links zu der Seite Detaillierte Health ist.</span><span class="sxs-lookup"><span data-stu-id="c5650-p103">To open service health, in the admin center, go to **Health** \> **Service health**, or click the Service health card on the Home dashboard. The dashboard card indicates whether there is an active service issue and links to the detailed service health page.</span></span>
    
    ![Dashboard-Karte finden Sie Dienststatus](media/8ae3de43-7bd5-4ee9-90ed-8b5ba5f9b474.png)
  
3. <span data-ttu-id="c5650-113">Der Zustand der einzelnen Cloud-Dienste wird in einem Tabellenformat mit einem Symbol an, dass möglichen Zuständen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c5650-113">The health state of each cloud service is shown in a table format with an icon to indicate possible states.</span></span>
    
> [!TIP]
> <span data-ttu-id="c5650-114">Sie können auch die [Office 365 Admin app](https://go.microsoft.com/fwlink/p/?linkid=627216) auf dem mobilen Gerät Dienststatus, anzeigen, eine hervorragende Möglichkeit zum mit Push-Benachrichtigungen auf dem laufenden ist.</span><span class="sxs-lookup"><span data-stu-id="c5650-114">You can also use the [Office 365 Admin app](https://go.microsoft.com/fwlink/p/?linkid=627216) on your mobile device to view Service health, which is a great way to stay current with push notifications.</span></span> 
  
### <a name="view-details-of-posted-service-health"></a><span data-ttu-id="c5650-115">Anzeigen der Details gebuchten Dienststatus</span><span class="sxs-lookup"><span data-stu-id="c5650-115">View details of posted service health</span></span>

<span data-ttu-id="c5650-p104">In der Standardansicht werden alle Dienste und deren aktuellem Integritätsanalyse Status angezeigt. Wählen Sie zum Filtern der Ansicht zu Diensten, die derzeit einen Vorfall auftritt **Vorfälle** aus der schattierten häufig verwendete Hyperlinks auf der linken Seite. Auswählen von **Ratschläge** werden nur die Dienste angezeigt, die derzeit eine Empfehlung veröffentlicht haben. Aus der Ansicht **alle Dienste** wird durch Klicken auf den angezeigten Dienststatus eine Zusammenfassungsansicht der Empfehlung oder Vorfall geöffnet.</span><span class="sxs-lookup"><span data-stu-id="c5650-p104">In the default view, all services and their current health state are displayed. To filter your view to services currently experiencing an incident, select **Incidents** from the shaded bar on the left. Selecting **Advisories** will show only services that currently have an advisory posted. From the **All services** view, clicking the displayed service state will open a summary view of the advisory or incident.</span></span> 
  
![Anzeigen der aktuellen Probleme in Dienststatus](media/f829a3af-1aca-4dc2-97eb-15d805349b24.png)
  
<span data-ttu-id="c5650-121">Die Empfehlung oder Zusammenfassung des Vorfalls bietet die folgende Informationen:</span><span class="sxs-lookup"><span data-stu-id="c5650-121">The advisory or incident summary provides the following information:</span></span> 
  
![Ein Screenshot Beschriften der Felder in einem Dienst Empfehlung](media/0dd6065c-1381-4a5c-8ca0-854c3e043a5c.png)
  
1. <span data-ttu-id="c5650-123">Ein Problem-ID und Zusammenfassung-Anweisung des Problems.</span><span class="sxs-lookup"><span data-stu-id="c5650-123">An issue identifier and summary statement of the problem.</span></span>
    
2. <span data-ttu-id="c5650-p105">Der aktuelle Status. Finden Sie unter Statusdefinitionen in diesem Artikel finden Sie eine Erläuterung der einzelnen möglichen Status.</span><span class="sxs-lookup"><span data-stu-id="c5650-p105">The current status. See status definitions in this article for an explanation of each potential status.</span></span>
    
3. <span data-ttu-id="c5650-126">Eine Beschreibung des wie dieses Problem Benutzer auswirken kann.</span><span class="sxs-lookup"><span data-stu-id="c5650-126">A description of how this issue can affect users.</span></span>
    
4. <span data-ttu-id="c5650-p106">Die Zeit, die das Problem gestartet wurde und dem Zeitpunkt der letzten, die die Dienst Health Nachricht aktualisiert wurde. Im Verlauf des ein Problem bereitstellen wir häufige Nachrichten, damit Sie den Fortschritt zu wissen, den wir vornehmen, bei der Anwendung einer Lösung.</span><span class="sxs-lookup"><span data-stu-id="c5650-p106">The time that the issue was started and the last time that the service health message was updated. Throughout the duration of an issue we post frequent messages to let you know the progress that we're making in applying a solution.</span></span>
    
5. <span data-ttu-id="c5650-129">Wählen Sie den Link **Details anzeigen** , finden weitere Informationen zu dem Problem, einschließlich des Verlaufs aller Nachrichten veröffentlicht wurden, während wir an einer Lösung arbeiten.</span><span class="sxs-lookup"><span data-stu-id="c5650-129">Select the **Show details** link to see more details about the issue, including the history of all messages posted while we work on a solution.</span></span> 
    
### <a name="translate-service-health-details"></a><span data-ttu-id="c5650-130">Übersetzen von Dienstdetails Integrität</span><span class="sxs-lookup"><span data-stu-id="c5650-130">Translate service health details</span></span>

<span data-ttu-id="c5650-p107">Da Service Health Erklärungen in Echtzeit gebucht, sie werden nicht automatisch in Ihrer Sprache übersetzt, und die Details eines Ereignisses Service nur in Englisch sind. Um die Erklärung zu übersetzen, gehen Sie folgendermaßen vor:</span><span class="sxs-lookup"><span data-stu-id="c5650-p107">Because service health explanations are posted in real-time, they are not automatically translated to your language and the details of a service event are in English only. To translate the explanation, follow these steps:</span></span>
  
1. <span data-ttu-id="c5650-133">Wechseln Sie zur [Übersetzer](https://www.bing.com/translator/).</span><span class="sxs-lookup"><span data-stu-id="c5650-133">Go to [Translator](https://www.bing.com/translator/).</span></span>
    
2. <span data-ttu-id="c5650-p108">Wählen Sie auf der Seite **Dienststatus** eine Vorfall oder Empfehlung aus. Kopieren Sie den Text zu dem Problem, klicken Sie unter **Details anzeigen**.</span><span class="sxs-lookup"><span data-stu-id="c5650-p108">On the **Service health** page, select an incident or advisory. Under **Show details**, copy the text about the issue.</span></span>
    
3. <span data-ttu-id="c5650-136">Klicken Sie im Translator fügen Sie den Text, und wählen Sie **Übersetzen**.</span><span class="sxs-lookup"><span data-stu-id="c5650-136">In Translator, paste the text and choose **Translate**.</span></span>
    
### <a name="definitions"></a><span data-ttu-id="c5650-137">Definitionen</span><span class="sxs-lookup"><span data-stu-id="c5650-137">Definitions</span></span>

<span data-ttu-id="c5650-p109">Die meisten Dienste Zeit werden ohne weitere Informationen wie fehlerfrei angezeigt. Wenn ein Dienst ein Problem aufgetreten ist, wird das Problem wird als eine Empfehlung oder ein Vorfall identifiziert und zeigt den aktuellen Status.</span><span class="sxs-lookup"><span data-stu-id="c5650-p109">Most of the time services will appear as healthy with no further information. When a service is having a problem, the issue is identified as either an advisory or an incident and shows a current status.</span></span>
  
> [!TIP]
> <span data-ttu-id="c5650-p110">Geplante Wartung Ereignisse in Dienststatus nicht angezeigt werden. Sie können geplante Wartung Ereignisse verfolgen, indem Sie mit der **Nachrichtencenter**Stand bleiben. Filtern von Nachrichten als Änderung planen, um zu ermitteln, wann die Änderung erfolgen soll, dessen Effekt und wie es bei der Vorbereitung kategorisiert. Einzelheiten finden Sie unter [Nachrichtencenter in Office 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093) .</span><span class="sxs-lookup"><span data-stu-id="c5650-p110">Planned maintenance events aren't shown in service health. You can track planned maintenance events by staying up to date with the **Message center**. Filter to messages categorized as Plan for change to find out when the change is going to happen, its effect, and how to prepare for it. See [Message center in Office 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093) for more details.</span></span> 
  
### <a name="incidents-and-advisories"></a><span data-ttu-id="c5650-144">Vorfälle und Ratschläge</span><span class="sxs-lookup"><span data-stu-id="c5650-144">Incidents and advisories</span></span>

|||
|:-----|:-----|
|![Informationssymbol für Empfehlung](media/a7f5fd21-c760-4948-9bc1-50f7c8070e28.png)|<span data-ttu-id="c5650-p111">Wenn ein Dienst eine Empfehlung angezeigt wurde, sollten Sie ein Problem, das einige Benutzer beeinflusst werden, aber der Dienst ist weiterhin verfügbar. In einer Empfehlung ist häufig eine Abhilfe für dieses Problem, und das Problem möglicherweise zeitweilig oder wird im Bereich und Benutzer Auswirkungen begrenzt.</span><span class="sxs-lookup"><span data-stu-id="c5650-p111">If a service has an advisory shown, we are aware of a problem that is affecting some users, but the service is still available. In an advisory, there is often a workaround to the problem and the problem may be intermittent or is limited in scope and user impact.</span></span>  <br/> |
|![Symbol für Vorfall Ausrufezeichen](media/a636db57-6083-44dc-bbd5-556850804f17.png)|<span data-ttu-id="c5650-p112">Weist ein Dienst auf einen aktiven Vorfall dargestellt, es ist ein kritisches Problem, und der Dienst oder eine der Hauptfunktionen des Diensts ist nicht verfügbar. Beispielsweise Benutzer möglicherweise keine e-Mails senden und empfangen oder -Anmeldung nicht möglich Vorfälle müssen bedeutende Auswirkung auf Benutzer. Wenn ein Vorfall in Bearbeitung vorhanden ist, bieten wir Updates bezüglich der Untersuchung, Abhilfemaßnahmen und Bestätigung der Lösung im Dashboard Health Service.</span><span class="sxs-lookup"><span data-stu-id="c5650-p112">If a service has an active incident shown, it's a critical issue and the service or a major function of the service is unavailable. For example, users may be unable to send and receive email or unable to sign-in. Incidents will have noticeable impact to users. When there is an incident in progress, we will provide updates regarding the investigation, mitigation efforts, and confirmation of resolution in the Service health dashboard.</span></span>  <br/> |
   
### <a name="status-definitions"></a><span data-ttu-id="c5650-153">Statusdefinitionen</span><span class="sxs-lookup"><span data-stu-id="c5650-153">Status definitions</span></span>

<span data-ttu-id="c5650-154">| |</span><span class="sxs-lookup"><span data-stu-id="c5650-154"></span></span>
|<span data-ttu-id="c5650-155">**Status**</span><span class="sxs-lookup"><span data-stu-id="c5650-155">**Status**</span></span>|<span data-ttu-id="c5650-156">**Definition**</span><span class="sxs-lookup"><span data-stu-id="c5650-156">**Definition**</span></span>|
|:-----|:-----|
|<span data-ttu-id="c5650-157">Untersuchen von</span><span class="sxs-lookup"><span data-stu-id="c5650-157">Investigating</span></span>  <br/> |<span data-ttu-id="c5650-158">Wir wissen, ein potenzielles Problem und Weitere Informationen über was passiert, und der Bereich der Auswirkungen gesammelt werden.</span><span class="sxs-lookup"><span data-stu-id="c5650-158">We're aware of a potential issue and are gathering more information about what's going on and the scope of impact.</span></span>  <br/> |
|<span data-ttu-id="c5650-159">Dienstbeeinträchtigung</span><span class="sxs-lookup"><span data-stu-id="c5650-159">Service degradation</span></span>  <br/> |<span data-ttu-id="c5650-p113">Wir haben bestätigt, dass ein Problem, die Verwendung des Diensts oder einer Funktion beeinflussen können. Dieser Status wird möglicherweise angezeigt, wenn ein Dienst langsamer als gewöhnlich durchführt, stehen Ihnen zeitweilige unterbrochen wird, oder wenn ein Feature funktionsfähig ist.</span><span class="sxs-lookup"><span data-stu-id="c5650-p113">We've confirmed that there is an issue that may affect use of a service or feature. You might see this status if a service is performing more slowly than usual, there are intermittent interruptions, or if a feature isn't working, for example.</span></span>  <br/> |
|<span data-ttu-id="c5650-162">Unterbrechung des Dienstes</span><span class="sxs-lookup"><span data-stu-id="c5650-162">Service interruption</span></span>  <br/> |<span data-ttu-id="c5650-p114">Dieser Status wird angezeigt, wenn Sie also feststellen, dass ein Problem wirkt sich die Möglichkeit für Benutzer den Zugriff auf Dienste auf. In diesem Fall das Problem ist von Bedeutung und durchgängig reproduzieren kann.</span><span class="sxs-lookup"><span data-stu-id="c5650-p114">You'll see this status if we determine that an issue affects the ability for users to access the service. In this case, the issue is significant and can be reproduced consistently.</span></span>  <br/> |
|<span data-ttu-id="c5650-165">Wiederherstellen von Diensten</span><span class="sxs-lookup"><span data-stu-id="c5650-165">Restoring service</span></span>  <br/> |<span data-ttu-id="c5650-166">Die Ursache des Problems wurde erkannt, wir wissen, welche Maßnahmen zum Erfassen, und es werden gerade verwenden aus der Dienst wieder in einem fehlerfreien Status befinden.</span><span class="sxs-lookup"><span data-stu-id="c5650-166">The cause of the issue has been identified, we know what corrective action to take, and are in the process of bringing the service back to a healthy state.</span></span>  <br/> |
|<span data-ttu-id="c5650-167">Erweiterte Wiederherstellung</span><span class="sxs-lookup"><span data-stu-id="c5650-167">Extended recovery</span></span>  <br/> |<span data-ttu-id="c5650-p115">Dieser Status gibt an, dass die Maßnahme ist noch in Arbeit wiederherstellen Service für die meisten Benutzer jedoch dauert einige Zeit in allen betroffenen Systemen zu erreichen. Dieser Status wird möglicherweise auch angezeigt, wenn wir eine temporäre Auswirkungen verringern, während eine endgültige Lösung anwenden gewartet beheben vorgenommen haben.</span><span class="sxs-lookup"><span data-stu-id="c5650-p115">This status indicates that corrective action is in progress to restore service to most users but will take some time to reach all the affected systems. You might also see this status if we've made a temporary fix to reduce impact while we wait to apply a permanent fix.</span></span>  <br/> |
|<span data-ttu-id="c5650-170">Untersuchung angehalten</span><span class="sxs-lookup"><span data-stu-id="c5650-170">Investigation suspended</span></span>  <br/> |<span data-ttu-id="c5650-p116">Wenn eine Anforderung für zusätzliche Informationen von Kunden an uns weiter untersuchen ermöglichen die detaillierte Untersuchung auf ein potenzielles Problem führt, wird dieser Status wird angezeigt. Wenn wir fungieren sollen, müssen wir Sie wissen, welche Daten oder Protokolle wir benötigen lassen.</span><span class="sxs-lookup"><span data-stu-id="c5650-p116">If our detailed investigation of a potential issue results in a request for additional information from customers to allow us to investigate further, you'll see this status. If we need you to act, we'll let you know what data or logs we need.</span></span>  <br/> |
|<span data-ttu-id="c5650-173">Dienst wiederhergestellt</span><span class="sxs-lookup"><span data-stu-id="c5650-173">Service restored</span></span>  <br/> |<span data-ttu-id="c5650-p117">Wir haben bestätigt, dass Maßnahme aufgelöst wurde das zugrunde liegende Problem und den Dienst in einem fehlerfreien Zustand wiederhergestellt wurde. Um herauszufinden, welche Fehler aufgetreten sind, können zeigen Sie das Problemdetails an.</span><span class="sxs-lookup"><span data-stu-id="c5650-p117">We've confirmed that corrective action has resolved the underlying problem and the service has been restored to a healthy state. To find out what went wrong, view the issue details.</span></span>  <br/> |
   
## <a name="history"></a><span data-ttu-id="c5650-176">„Verlauf“</span><span class="sxs-lookup"><span data-stu-id="c5650-176">History</span></span>

<span data-ttu-id="c5650-p118">Dienststatus können Sie sehen Sie sich den aktuellen Status und Anzeigen des Verlaufs von Dienst Ratschläge und Vorfälle in den letzten 30 Tagen. Um die letzten Integrität aller Dienste anzuzeigen, wählen Sie auf der Seite **Dienststatus** **Historie anzeigen** aus.</span><span class="sxs-lookup"><span data-stu-id="c5650-p118">Service health lets you look at current health status and view the history of any service advisories and incidents in the past 30 days. To view the past health of all services, select **View history** on the **Service health** page.</span></span> 
  
![Link zum Gesundheitsdaten anzeigen](media/12a3e484-1eb4-497f-8cab-8064bccc2ef5.png)
  
<span data-ttu-id="c5650-180">Eine Liste aller Service Health Nachrichten in der ausgewählten Zeitrahmen gebucht wird angezeigt, wie unten dargestellt:</span><span class="sxs-lookup"><span data-stu-id="c5650-180">A list of all service health messages posted in the selected timeframe is displayed, as shown below:</span></span>
  
![Ansicht Service Gesundheitsdaten](media/5ed20247-121c-4abe-9fe7-9025e26a2d0e.png)
  
<span data-ttu-id="c5650-p119">Sie können die Gesundheitsdaten für die letzten 7 Tage oder der letzten 30 Tagen anzeigen. Wählen Sie eine Zeile aus, um weitere Informationen zu diesem Problem anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="c5650-p119">You may view the health history for either the last 7 days or last 30 days. Select any row to view more details about that issue.</span></span>
  
<span data-ttu-id="c5650-184">Weitere Informationen zu unserem Engagement für Betriebszeit finden Sie unter [Transparent Vorgänge von Office 365](https://go.microsoft.com/fwlink/?linkid=848695).</span><span class="sxs-lookup"><span data-stu-id="c5650-184">For more information about our commitment to uptime, see [Transparent operations from Office 365](https://go.microsoft.com/fwlink/?linkid=848695).</span></span>
  
## <a name="leave-feedback"></a><span data-ttu-id="c5650-185">Lassen Sie feedback</span><span class="sxs-lookup"><span data-stu-id="c5650-185">Leave feedback</span></span>

<span data-ttu-id="c5650-p120">Unser Ziel besteht darin, sicherzustellen, dass die Informationen, die wir Ihnen zu einer laufenden Problem bereitstellen rechtzeitige, genauer und hilfreicher ist. Um uns mitzuteilen wie wir tun, wählen Sie eine Bewertung Stern. Nachdem Sie uns eine Bewertung von 1 auf 5 Sterne gewähren möchten, können Sie auf eine beliebige spezifische Details Feedback. Ihr Feedback verwenden wir um unser Service Health System zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="c5650-p120">Our goal is to make sure that the information we provide to you about an ongoing issue is timely, accurate, and useful. To tell us how we're doing, select a star rating. After you give us a score from 1 to 5 stars, you can give feedback on any specific details. We'll use your feedback to fine-tune our service health system.</span></span>
  
![Feedbackformular für Health Dienstproblemen](media/fd083fdb-fde8-47b4-9136-b90d1d003864.png)
  
## <a name="see-also"></a><span data-ttu-id="c5650-191">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="c5650-191">See also</span></span>

[<span data-ttu-id="c5650-192">Berichte im Office 365 Administrationscenter</span><span class="sxs-lookup"><span data-stu-id="c5650-192">Activity Reports in the Office 365 admin center</span></span>](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)

