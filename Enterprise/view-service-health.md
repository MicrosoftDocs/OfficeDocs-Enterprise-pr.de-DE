---
title: Überprüfen des Office 365-Dienststatus
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- O365P_ServiceHealthModern
- O365M_ServiceHealthModern
- O365E_ViewStatusServices
- O365E_ServiceHealthModern
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- BCS160
- IWA160
ms.assetid: 932ad3ad-533c-418a-b938-6e44e8bc33b0
description: Sehen Sie sich den Status von Office 365-Diensten an, bevor Sie den Support anrufen, um festzustellen, ob eine Unterbrechung eines aktiven Diensts vorliegt.
ms.openlocfilehash: 67595bddaed23222d09c0e7f6f5353b764722f83
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071221"
---
# <a name="how-to-check-office-365-service-health"></a><span data-ttu-id="2826a-103">Überprüfen des Office 365-Dienststatus</span><span class="sxs-lookup"><span data-stu-id="2826a-103">How to check Office 365 service health</span></span>

<span data-ttu-id="2826a-104">Sie können den Status von Office 365, Yammer, Microsoft Dynamics CRM und Microsoft Intune Cloud Services auf der Office 365-**Dienststatus**-Seite im [Microsoft 365 Admin Center](https://admin.microsoft.com) einsehen.</span><span class="sxs-lookup"><span data-stu-id="2826a-104">You can view the health of Office 365, Yammer, Microsoft Dynamics CRM, and Microsoft Intune cloud services on the Office 365 \*\* Service health \*\* page in the admin center.</span></span> <span data-ttu-id="2826a-105">Wenn bei einem Clouddienst Probleme auftreten, können Sie den Dienststatus überprüfen, um festzustellen, ob es sich um ein bekanntes Problem handelt, für das bereits an einer Lösung gearbeitet wird, bevor Sie den Support anrufen oder Zeit für die Problembehandlung aufwenden.</span><span class="sxs-lookup"><span data-stu-id="2826a-105">If you are experiencing problems with a cloud service, you can check the service health to determine whether this is a known issue with a resolution in progress before you call support or spend time troubleshooting.</span></span> 

<span data-ttu-id="2826a-106">Wenn Sie sich nicht im Serviceportal anmelden können, können Sie auf der [Dienststatus-Seite](https://status.office365.com) nach bekannten Problemen suchen, die Sie daran hindern, sich bei Ihrem Mandanten anzumelden.</span><span class="sxs-lookup"><span data-stu-id="2826a-106">If you are unable to sign in to the service portal, you can use the [service status page](https://status.office365.com) to check for known issues preventing you from logging into your tenant.</span></span>
  
### <a name="how-to-check-service-health"></a><span data-ttu-id="2826a-107">Überprüfen des Dienststatus</span><span class="sxs-lookup"><span data-stu-id="2826a-107">How to check service health</span></span>

1. <span data-ttu-id="2826a-108">Wechseln Sie zu [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage), und melden Sie sich mit einem Administratorkonto an.</span><span class="sxs-lookup"><span data-stu-id="2826a-108">Go to [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage) and sign in with an admin account.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="2826a-p102">Personen, denen die Rolle eines globalen Administrators oder Serviceadministrators zugewiesen ist, können den Dienststatus anzeigen. Damit Exchange-, SharePoint- und Skype for Business-Administratoren den Dienststatus anzeigen können, muss ihnen auch die Rolle des Dienstadministrators zugewiesen sein.</span><span class="sxs-lookup"><span data-stu-id="2826a-p102">People who are assigned the global admin or service administrator role can view service health. To allow Exchange, SharePoint, and Skype for Business admins to view service health, they must also be assigned the Service admin role.</span></span>
  
2. <span data-ttu-id="2826a-111">Zum Anzeigen des Dienststatus wechseln Sie im Admin Center zu**Status** > **Dienststatus**, oder klicken Sie auf dem **Startdashboard** auf die **Dienststatuskarte**.</span><span class="sxs-lookup"><span data-stu-id="2826a-111">To open service health, in the admin center, go to Health  Service health, or click the Service health card on the Home dashboard.</span></span> <span data-ttu-id="2826a-112">Die Dashboardkarte gibt an, ob ein Problem mit einem aktiven Dienst vorliegt, und stellt einen Link zur Seite mit Dienststatusdetails bereit.</span><span class="sxs-lookup"><span data-stu-id="2826a-112">The dashboard card indicates whether there is an active service issue and links to the detailed service health page.</span></span>
    
    ![Dashboardkarte für Dienststatus](media/8ae3de43-7bd5-4ee9-90ed-8b5ba5f9b474.png)
  
3. <span data-ttu-id="2826a-114">Der Status der einzelnen Clouddienste wird in einem Tabellenformat mit einem Symbol zur Angabe möglicher Status angezeigt.</span><span class="sxs-lookup"><span data-stu-id="2826a-114">The health state of each cloud service is shown in a table format with an icon to indicate possible states.</span></span>
    
> [!TIP]
> <span data-ttu-id="2826a-115">Sie können den Dienststatus auch mithilfe der [Office 365 Admin-App](https://go.microsoft.com/fwlink/p/?linkid=627216) auf Ihrem mobilen Gerät anzeigen. Dies ist eine hervorragende Möglichkeit, mit Pushbenachrichtigungen auf dem Laufenden zu bleiben.</span><span class="sxs-lookup"><span data-stu-id="2826a-115">You can also use the [Office 365 Admin app](https://go.microsoft.com/fwlink/p/?linkid=627216) on your mobile device to view Service health, which is a great way to stay current with push notifications.</span></span> 
  
### <a name="view-details-of-posted-service-health"></a><span data-ttu-id="2826a-116">Anzeigen von Details des veröffentlichten Dienststatus</span><span class="sxs-lookup"><span data-stu-id="2826a-116">View details of posted service health</span></span>

<span data-ttu-id="2826a-117">In der Standardansicht werden alle Dienste und ihr aktueller Status angezeigt.</span><span class="sxs-lookup"><span data-stu-id="2826a-117">In the default view, all services and their current health state are displayed.</span></span> <span data-ttu-id="2826a-118">Wenn Sie die Ansicht nach Diensten filtern möchten, die aktuell einen Vorfall aufweisen, wählen Sie **Vorfälle** in der schattierten Leiste auf der linken Seite aus.</span><span class="sxs-lookup"><span data-stu-id="2826a-118">To filter your view to services currently experiencing an incident, select **Incidents** from the shaded bar on the left.</span></span> <span data-ttu-id="2826a-119">Bei Auswahl von **Empfehlungen** werden nur Dienste angezeigt, für die derzeit eine Empfehlung angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="2826a-119">Selecting **Advisories** will show only services that currently have an advisory posted.</span></span> <span data-ttu-id="2826a-120">Wenn Sie in der Ansicht **Alle Dienste** auf den angezeigten Dienststatus klicken, wird eine Zusammenfassungsansicht der Empfehlung bzw. des Vorfalls geöffnet.</span><span class="sxs-lookup"><span data-stu-id="2826a-120">From the **All services** view, clicking the displayed service state will open a summary view of the advisory or incident.</span></span> 
  
![Ansicht der aktuellen Probleme unter "Dienststatus"](media/f829a3af-1aca-4dc2-97eb-15d805349b24.png)
  
<span data-ttu-id="2826a-122">Die Empfehlungs- oder Vorfallzusammenfassung enthält folgende Informationen:</span><span class="sxs-lookup"><span data-stu-id="2826a-122">The advisory or incident summary provides the following information:</span></span> 
  
![Ein Screenshot, der die Felder in einer Empfehlung kennzeichnet.](media/0dd6065c-1381-4a5c-8ca0-854c3e043a5c.png)
  
1. <span data-ttu-id="2826a-124">Eine Problem-ID und eine zusammenfassende Beschreibung des Problems.</span><span class="sxs-lookup"><span data-stu-id="2826a-124">An issue identifier and summary statement of the problem.</span></span>
    
2. <span data-ttu-id="2826a-p105">Der aktuelle Status. Eine Erläuterung der einzelnen möglichen Statusarten finden Sie unter den Statusdefinitionen in diesem Artikel.</span><span class="sxs-lookup"><span data-stu-id="2826a-p105">The current status. See status definitions in this article for an explanation of each potential status.</span></span>
    
3. <span data-ttu-id="2826a-127">Eine Beschreibung, wie sich dieses Problem auf Benutzer auswirken kann.</span><span class="sxs-lookup"><span data-stu-id="2826a-127">A description of how this issue can affect users.</span></span>
    
4. <span data-ttu-id="2826a-p106">Der Zeitpunkt, zu dem das Problem begonnen hat, und der Zeitpunkt der letzten Aktualisierung der Nachricht zum Dienststatus. Während der gesamten Dauer eines Problems werden häufig Nachrichten veröffentlicht, um Sie über die Fortschritte beim Anwenden einer Lösung zu informieren.</span><span class="sxs-lookup"><span data-stu-id="2826a-p106">The time that the issue was started and the last time that the service health message was updated. Throughout the duration of an issue we post frequent messages to let you know the progress that we're making in applying a solution.</span></span>
    
5. <span data-ttu-id="2826a-130">Klicken Sie auf den Link **Details anzeigen**, um weitere Details zum Problem anzuzeigen, einschließlich des Verlaufs aller veröffentlichten Nachrichten während des Arbeitens an einer Lösung.</span><span class="sxs-lookup"><span data-stu-id="2826a-130">Select the **Show details** link to see more details about the issue, including the history of all messages posted while we work on a solution.</span></span> 
    
### <a name="translate-service-health-details"></a><span data-ttu-id="2826a-131">Übersetzen von Dienststatusdetails</span><span class="sxs-lookup"><span data-stu-id="2826a-131">Translate service health details</span></span>

<span data-ttu-id="2826a-p107">Da Erläuterungen zum Dienststatus in Echtzeit veröffentlicht werden, sind sie nicht automatisch in Ihre Sprache übersetzt, und die Details eines Dienstereignisses sind nur in Englisch angegeben. Zum Übersetzen der Erläuterung führen Sie die folgenden Schritte aus: </span><span class="sxs-lookup"><span data-stu-id="2826a-p107">Because service health explanations are posted in real-time, they are not automatically translated to your language and the details of a service event are in English only. To translate the explanation, follow these steps:</span></span>
  
1. <span data-ttu-id="2826a-134">Wechseln Sie zu [Translator](https://www.bing.com/translator/).</span><span class="sxs-lookup"><span data-stu-id="2826a-134">Go to [Translator](https://www.bing.com/translator/).</span></span>
    
2. <span data-ttu-id="2826a-p108">Wählen Sie auf der Seite **Dienststatus** einen Vorfall oder eine Empfehlung aus. Kopieren Sie unter **Details anzeigen** den Text zum Problem.</span><span class="sxs-lookup"><span data-stu-id="2826a-p108">On the **Service health** page, select an incident or advisory. Under **Show details**, copy the text about the issue.</span></span>
    
3. <span data-ttu-id="2826a-137">Fügen Sie den Text in Translator ein, und klicken Sie auf **Übersetzen**.</span><span class="sxs-lookup"><span data-stu-id="2826a-137">In Translator, paste the text and choose **Translate**.</span></span>
    
### <a name="definitions"></a><span data-ttu-id="2826a-138">Definitionen</span><span class="sxs-lookup"><span data-stu-id="2826a-138">Definitions</span></span>

<span data-ttu-id="2826a-p109">Die meiste Zeit werden Dienste als fehlerfrei und ohne weitere Informationen angezeigt. Wenn bei einem Dienst ein Problem vorliegt, wird das Problem entweder als eine Empfehlung oder als ein Vorfall angegeben, und der aktuelle Status wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="2826a-p109">Most of the time services will appear as healthy with no further information. When a service is having a problem, the issue is identified as either an advisory or an incident and shows a current status.</span></span>
  
> [!TIP]
> <span data-ttu-id="2826a-p110">Geplante Wartungsereignisse werden im Dienststatus nicht angezeigt. Sie können geplante Wartungsereignisse verfolgen, indem Sie sich mit dem **Nachrichtencenter** auf dem neuesten Stand halten. Filtern Sie nach Nachrichten, für dieeine geplante Änderung als Kategorie angegeben ist, um herauszufinden, wann die Änderung stattfinden soll, welche Auswirkungen sie hat und wie Sie Vorbereitungen dafür treffen können. Weitere Details finden Sie unter [Nachrichtencenter in Office 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093).</span><span class="sxs-lookup"><span data-stu-id="2826a-p110">Planned maintenance events aren't shown in service health. You can track planned maintenance events by staying up to date with the **Message center**. Filter to messages categorized as Plan for change to find out when the change is going to happen, its effect, and how to prepare for it. See [Message center in Office 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093) for more details.</span></span> 
  
### <a name="incidents-and-advisories"></a><span data-ttu-id="2826a-145">Vorfälle und Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="2826a-145">Incidents and advisories</span></span>

|||
|:-----|:-----|
|![Infosymbol für Empfehlung](media/a7f5fd21-c760-4948-9bc1-50f7c8070e28.png)|<span data-ttu-id="2826a-p111">Wenn für einen Dienst eine Empfehlung angezeigt wird, wissen wir von einem Problem, das sich auf einige Benutzer auswirkt, doch ist der Dienst weiterhin verfügbar. Bei einer Empfehlung gibt es häufig eine Umgehung für das Problem und das Problem tritt ggf. nur zeitweilig auf oder ist in Hinsicht auf Umfang und Auswirkungen auf Benutzer eingeschränkt.</span><span class="sxs-lookup"><span data-stu-id="2826a-p111">If a service has an advisory shown, we are aware of a problem that is affecting some users, but the service is still available. In an advisory, there is often a workaround to the problem and the problem may be intermittent or is limited in scope and user impact.</span></span>  <br/> |
|![Ausrufezeichensymbol für Vorfall](media/a636db57-6083-44dc-bbd5-556850804f17.png)|<span data-ttu-id="2826a-p112">Wenn für einen Dienst ein aktiver Vorfall angezeigt wird, handelt es sich ein kritisches Problem und der Dienst oder eine wichtige Funktion des Diensts ist nicht verfügbar. Beispielsweise können Benutzer keine E-Mails senden und empfangen oder sich nicht anmelden. Vorfälle haben erkennbare Auswirkungen für die Benutzer. Tritt ein Vorfall ein, stellen wir Updates zur Untersuchung, Abhilfemaßnahmen und Lösungsbestätigungen im Dashboard zur Dienstintegrität bereit.</span><span class="sxs-lookup"><span data-stu-id="2826a-p112">If a service has an active incident shown, it's a critical issue and the service or a major function of the service is unavailable. For example, users may be unable to send and receive email or unable to sign-in. Incidents will have noticeable impact to users. When there is an incident in progress, we will provide updates regarding the investigation, mitigation efforts, and confirmation of resolution in the Service health dashboard.</span></span>  <br/> |
   
### <a name="status-definitions"></a><span data-ttu-id="2826a-154">Statusdefinitionen</span><span class="sxs-lookup"><span data-stu-id="2826a-154">Status definitions</span></span>

|<span data-ttu-id="2826a-155">**Status**</span><span class="sxs-lookup"><span data-stu-id="2826a-155">**Status**</span></span>|<span data-ttu-id="2826a-156">**Definition**</span><span class="sxs-lookup"><span data-stu-id="2826a-156">**Definition**</span></span>|
|:-----|:-----|
|<span data-ttu-id="2826a-157">**Wird untersucht**</span><span class="sxs-lookup"><span data-stu-id="2826a-157">**Investigating**</span></span> | <span data-ttu-id="2826a-158">Uns ist ein potenzielles Problem bekannt, und wir sammeln weitere Informationen dazu, was vor sich geht und welche Auswirkungen es hat.</span><span class="sxs-lookup"><span data-stu-id="2826a-158">We're aware of a potential issue and are gathering more information about what's going on and the scope of impact.</span></span> |
|<span data-ttu-id="2826a-159">**Dienstbeeinträchtigung**</span><span class="sxs-lookup"><span data-stu-id="2826a-159">**Service degradation**</span></span> | <span data-ttu-id="2826a-p113">Wir haben bestätigt, dass ein Problem vorliegt, das eine Auswirkung auf die Verwendung eines Diensts oder Features haben kann. Dieser Status wird möglicherweise angezeigt, wenn ein Dienst langsamer als gewöhnlich ausgeführt wird, zeitweilige Unterbrechungen auftreten oder ein Feature nicht funktioniert.</span><span class="sxs-lookup"><span data-stu-id="2826a-p113">We've confirmed that there is an issue that may affect use of a service or feature. You might see this status if a service is performing more slowly than usual, there are intermittent interruptions, or if a feature isn't working, for example.</span></span> |
|<span data-ttu-id="2826a-162">**Dienstunterbrechung**</span><span class="sxs-lookup"><span data-stu-id="2826a-162">**Service interruption**</span></span> | <span data-ttu-id="2826a-p114">Dieser Status wird angezeigt, wenn wir feststellen, dass sich ein Problem auf den Zugriff der Benutzer auf den Dienst auswirkt. In diesem Fall ist das Problem schwerwiegend und kann konsistent reproduziert werden.</span><span class="sxs-lookup"><span data-stu-id="2826a-p114">You'll see this status if we determine that an issue affects the ability for users to access the service. In this case, the issue is significant and can be reproduced consistently.</span></span> |
|<span data-ttu-id="2826a-165">**Dienst wird wiederhergestellt**</span><span class="sxs-lookup"><span data-stu-id="2826a-165">**Restoring service**</span></span> | <span data-ttu-id="2826a-166">Die Ursache des Problems wurde erkannt, wir wissen, welche Behebungsmaßnahme zu ergreifen ist, und sind dabei, den Dienst wieder in einen fehlerfreien Zustand zu versetzen.</span><span class="sxs-lookup"><span data-stu-id="2826a-166">The cause of the issue has been identified, we know what corrective action to take, and are in the process of bringing the service back to a healthy state.</span></span> |
|<span data-ttu-id="2826a-167">**Erweiterte Wiederherstellung**</span><span class="sxs-lookup"><span data-stu-id="2826a-167">**Extended recovery**</span></span> | <span data-ttu-id="2826a-p115">Dieser Status gibt an, dass eine Behebungsmaßnahme durchgeführt wird, um den Dienst für die Mehrzahl der Benutzer wiederherzustellen, es dauert jedoch einige Zeit, bis alle betroffenen Systeme erreicht sind. Dieser Status wird möglicherweise auch angezeigt, wenn wir eine temporäre Korrektur vorgenommen haben, um die Auswirkungen zu verringern, während wir an der Bereitstellung einer dauerhaften Lösung arbeiten.</span><span class="sxs-lookup"><span data-stu-id="2826a-p115">This status indicates that corrective action is in progress to restore service to most users but will take some time to reach all the affected systems. You might also see this status if we've made a temporary fix to reduce impact while we wait to apply a permanent fix.</span></span> |
|<span data-ttu-id="2826a-170">**Untersuchung angehalten**</span><span class="sxs-lookup"><span data-stu-id="2826a-170">**Investigation suspended**</span></span> | <span data-ttu-id="2826a-p116">Dieser Status wird angezeigt, wenn unsere detaillierte Untersuchung eines potenziellen Problems dazu führt, dass Kunden um Angabe zusätzlicher Informationen für eine weitere Untersuchung gebeten werden. Wenn Ihre Unterstützung erforderlich ist, informieren wir Sie, welche Daten oder Protokolle wir benötigen.</span><span class="sxs-lookup"><span data-stu-id="2826a-p116">If our detailed investigation of a potential issue results in a request for additional information from customers to allow us to investigate further, you'll see this status. If we need you to act, we'll let you know what data or logs we need.</span></span> |
|<span data-ttu-id="2826a-173">**Dienst wiederhergestellt**</span><span class="sxs-lookup"><span data-stu-id="2826a-173">**Service restored**</span></span> | <span data-ttu-id="2826a-p117">Wir haben bestätigt, dass durch die Behebungsmaßnahme das zugrunde liegende Problem gelöst und der Dienst wieder in einen fehlerfreien Zustand versetzt wurde. Informationen zur Fehlerursache finden Sie unter den Problemdetails.</span><span class="sxs-lookup"><span data-stu-id="2826a-p117">We've confirmed that corrective action has resolved the underlying problem and the service has been restored to a healthy state. To find out what went wrong, view the issue details.</span></span> |
|<span data-ttu-id="2826a-176">**Vorfallnachsorgebericht veröffentlicht**</span><span class="sxs-lookup"><span data-stu-id="2826a-176">**Post-incident report published**</span></span> | <span data-ttu-id="2826a-177">Wir haben für ein bestimmtes Problem einen Beitrag veröffentlicht, der Informationen zu den Ursachen sowie nächste Schritte umfasst, um sicherzustellen, dass ein ähnliches Problem nicht wieder auftritt.</span><span class="sxs-lookup"><span data-stu-id="2826a-177">We’ve published a Post Incident Report for a specific issue that includes root cause information and next steps to ensure a similar issue doesn’t reoccur.</span></span> |
   
## <a name="history"></a><span data-ttu-id="2826a-178">Ereignisprotokoll</span><span class="sxs-lookup"><span data-stu-id="2826a-178">History</span></span>

<span data-ttu-id="2826a-179">Der Dienststatus zeigt den aktuellen Status sowie den Verlauf aller Empfehlungen und Vorfälle für Dienste, die Ihren Mandanten in den letzten 30 Tagen betroffen haben.</span><span class="sxs-lookup"><span data-stu-id="2826a-179">Service health lets you look at current health status and view the history of any service advisories and incidents in the past 30 days.</span></span> <span data-ttu-id="2826a-180">Zum Anzeigen des früheren Status aller Dienste wählen Sie auf der Seite **Dienststatus** die Option **Verlauf anzeigen** aus.</span><span class="sxs-lookup"><span data-stu-id="2826a-180">To view the past health of all services, select **View history** on the **Service health** page.</span></span> 
  
![Anzeigen des Links zum Statusverlauf](media/12a3e484-1eb4-497f-8cab-8064bccc2ef5.png)
  
<span data-ttu-id="2826a-182">Es wird eine Liste aller Nachrichten zum Dienststatus angezeigt, die im ausgewählten Zeitraum veröffentlicht wurden (siehe unten).</span><span class="sxs-lookup"><span data-stu-id="2826a-182">A list of all service health messages posted in the selected timeframe is displayed, as shown below:</span></span>
  
![Anzeigen des Dienststatusverlaufs](media/5ed20247-121c-4abe-9fe7-9025e26a2d0e.png)
  
<span data-ttu-id="2826a-184">Sie können den Statusverlauf entweder für die letzten 7 Tage oder die letzten 30 Tage anzeigen.</span><span class="sxs-lookup"><span data-stu-id="2826a-184">You may view the health history for either the last 7 days or last 30 days.</span></span> <span data-ttu-id="2826a-185">Wählen Sie eine beliebige Zeile aus, um weitere Details zu diesem Problem anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="2826a-185">Select any row to view more details about that issue.For more information about our commitment to uptime, see Transparent operations from Office 365.</span></span>
  
<span data-ttu-id="2826a-186">Weitere Informationen über unsere Verpflichtung zur Verfügbarkeit finden Sie unter [Transparente Vorgänge in Office 365](https://go.microsoft.com/fwlink/?linkid=848695).</span><span class="sxs-lookup"><span data-stu-id="2826a-186">Select any row to view more details about that issue.For more information about our commitment to uptime, see [Transparent operations from Office 365](https://go.microsoft.com/fwlink/?linkid=848695).</span></span>
  
## <a name="leave-feedback"></a><span data-ttu-id="2826a-187">Feedback geben</span><span class="sxs-lookup"><span data-stu-id="2826a-187">Leave feedback</span></span>

<span data-ttu-id="2826a-p120">Unser Ziel ist es sicherzustellen, dass die Informationen, die wir Ihnen zu einem laufenden Problem geben, aktuell, präzise und nützlich sind. Wenn Sie uns mitteilen möchten, inwieweit wir dieses Ziel erreichen, wählen Sie eine Sternebewertung aus. Nachdem Sie eine Bewertung mit 1 bis 5 Sternen abgegeben haben, können Sie uns Feedback zu bestimmten Details geben. Anhand Ihres Feedbacks können wir unser Dienststatussystem weiter optimieren.</span><span class="sxs-lookup"><span data-stu-id="2826a-p120">Our goal is to make sure that the information we provide to you about an ongoing issue is timely, accurate, and useful. To tell us how we're doing, select a star rating. After you give us a score from 1 to 5 stars, you can give feedback on any specific details. We'll use your feedback to fine-tune our service health system.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2826a-192">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="2826a-192">See also</span></span>

[<span data-ttu-id="2826a-193">Teams-Aktivitätsberichte im Microsoft 365 Admin Center</span><span class="sxs-lookup"><span data-stu-id="2826a-193">Activity Reports in the Office 365 admin center</span></span>](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)