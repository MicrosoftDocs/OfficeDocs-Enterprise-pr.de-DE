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
# <a name="how-to-check-office-365-service-health"></a>Überprüfen des Office 365-Dienststatus

Sie können den Status von Office 365, Yammer, Microsoft Dynamics CRM und Microsoft Intune Cloud Services auf der Office 365-**Dienststatus**-Seite im [Microsoft 365 Admin Center](https://admin.microsoft.com) einsehen. Wenn bei einem Clouddienst Probleme auftreten, können Sie den Dienststatus überprüfen, um festzustellen, ob es sich um ein bekanntes Problem handelt, für das bereits an einer Lösung gearbeitet wird, bevor Sie den Support anrufen oder Zeit für die Problembehandlung aufwenden. 

Wenn Sie sich nicht im Serviceportal anmelden können, können Sie auf der [Dienststatus-Seite](https://status.office365.com) nach bekannten Problemen suchen, die Sie daran hindern, sich bei Ihrem Mandanten anzumelden.
  
### <a name="how-to-check-service-health"></a>Überprüfen des Dienststatus

1. Wechseln Sie zu [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage), und melden Sie sich mit einem Administratorkonto an. 
    
    > [!NOTE]
    > Personen, denen die Rolle eines globalen Administrators oder Serviceadministrators zugewiesen ist, können den Dienststatus anzeigen. Damit Exchange-, SharePoint- und Skype for Business-Administratoren den Dienststatus anzeigen können, muss ihnen auch die Rolle des Dienstadministrators zugewiesen sein.
  
2. Zum Anzeigen des Dienststatus wechseln Sie im Admin Center zu**Status** > **Dienststatus**, oder klicken Sie auf dem **Startdashboard** auf die **Dienststatuskarte**. Die Dashboardkarte gibt an, ob ein Problem mit einem aktiven Dienst vorliegt, und stellt einen Link zur Seite mit Dienststatusdetails bereit.
    
    ![Dashboardkarte für Dienststatus](media/8ae3de43-7bd5-4ee9-90ed-8b5ba5f9b474.png)
  
3. Der Status der einzelnen Clouddienste wird in einem Tabellenformat mit einem Symbol zur Angabe möglicher Status angezeigt.
    
> [!TIP]
> Sie können den Dienststatus auch mithilfe der [Office 365 Admin-App](https://go.microsoft.com/fwlink/p/?linkid=627216) auf Ihrem mobilen Gerät anzeigen. Dies ist eine hervorragende Möglichkeit, mit Pushbenachrichtigungen auf dem Laufenden zu bleiben. 
  
### <a name="view-details-of-posted-service-health"></a>Anzeigen von Details des veröffentlichten Dienststatus

In der Standardansicht werden alle Dienste und ihr aktueller Status angezeigt. Wenn Sie die Ansicht nach Diensten filtern möchten, die aktuell einen Vorfall aufweisen, wählen Sie **Vorfälle** in der schattierten Leiste auf der linken Seite aus. Bei Auswahl von **Empfehlungen** werden nur Dienste angezeigt, für die derzeit eine Empfehlung angegeben ist. Wenn Sie in der Ansicht **Alle Dienste** auf den angezeigten Dienststatus klicken, wird eine Zusammenfassungsansicht der Empfehlung bzw. des Vorfalls geöffnet. 
  
![Ansicht der aktuellen Probleme unter "Dienststatus"](media/f829a3af-1aca-4dc2-97eb-15d805349b24.png)
  
Die Empfehlungs- oder Vorfallzusammenfassung enthält folgende Informationen: 
  
![Ein Screenshot, der die Felder in einer Empfehlung kennzeichnet.](media/0dd6065c-1381-4a5c-8ca0-854c3e043a5c.png)
  
1. Eine Problem-ID und eine zusammenfassende Beschreibung des Problems.
    
2. Der aktuelle Status. Eine Erläuterung der einzelnen möglichen Statusarten finden Sie unter den Statusdefinitionen in diesem Artikel.
    
3. Eine Beschreibung, wie sich dieses Problem auf Benutzer auswirken kann.
    
4. Der Zeitpunkt, zu dem das Problem begonnen hat, und der Zeitpunkt der letzten Aktualisierung der Nachricht zum Dienststatus. Während der gesamten Dauer eines Problems werden häufig Nachrichten veröffentlicht, um Sie über die Fortschritte beim Anwenden einer Lösung zu informieren.
    
5. Klicken Sie auf den Link **Details anzeigen**, um weitere Details zum Problem anzuzeigen, einschließlich des Verlaufs aller veröffentlichten Nachrichten während des Arbeitens an einer Lösung. 
    
### <a name="translate-service-health-details"></a>Übersetzen von Dienststatusdetails

Da Erläuterungen zum Dienststatus in Echtzeit veröffentlicht werden, sind sie nicht automatisch in Ihre Sprache übersetzt, und die Details eines Dienstereignisses sind nur in Englisch angegeben. Zum Übersetzen der Erläuterung führen Sie die folgenden Schritte aus: 
  
1. Wechseln Sie zu [Translator](https://www.bing.com/translator/).
    
2. Wählen Sie auf der Seite **Dienststatus** einen Vorfall oder eine Empfehlung aus. Kopieren Sie unter **Details anzeigen** den Text zum Problem.
    
3. Fügen Sie den Text in Translator ein, und klicken Sie auf **Übersetzen**.
    
### <a name="definitions"></a>Definitionen

Die meiste Zeit werden Dienste als fehlerfrei und ohne weitere Informationen angezeigt. Wenn bei einem Dienst ein Problem vorliegt, wird das Problem entweder als eine Empfehlung oder als ein Vorfall angegeben, und der aktuelle Status wird angezeigt.
  
> [!TIP]
> Geplante Wartungsereignisse werden im Dienststatus nicht angezeigt. Sie können geplante Wartungsereignisse verfolgen, indem Sie sich mit dem **Nachrichtencenter** auf dem neuesten Stand halten. Filtern Sie nach Nachrichten, für dieeine geplante Änderung als Kategorie angegeben ist, um herauszufinden, wann die Änderung stattfinden soll, welche Auswirkungen sie hat und wie Sie Vorbereitungen dafür treffen können. Weitere Details finden Sie unter [Nachrichtencenter in Office 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093). 
  
### <a name="incidents-and-advisories"></a>Vorfälle und Empfehlungen

|||
|:-----|:-----|
|![Infosymbol für Empfehlung](media/a7f5fd21-c760-4948-9bc1-50f7c8070e28.png)|Wenn für einen Dienst eine Empfehlung angezeigt wird, wissen wir von einem Problem, das sich auf einige Benutzer auswirkt, doch ist der Dienst weiterhin verfügbar. Bei einer Empfehlung gibt es häufig eine Umgehung für das Problem und das Problem tritt ggf. nur zeitweilig auf oder ist in Hinsicht auf Umfang und Auswirkungen auf Benutzer eingeschränkt.  <br/> |
|![Ausrufezeichensymbol für Vorfall](media/a636db57-6083-44dc-bbd5-556850804f17.png)|Wenn für einen Dienst ein aktiver Vorfall angezeigt wird, handelt es sich ein kritisches Problem und der Dienst oder eine wichtige Funktion des Diensts ist nicht verfügbar. Beispielsweise können Benutzer keine E-Mails senden und empfangen oder sich nicht anmelden. Vorfälle haben erkennbare Auswirkungen für die Benutzer. Tritt ein Vorfall ein, stellen wir Updates zur Untersuchung, Abhilfemaßnahmen und Lösungsbestätigungen im Dashboard zur Dienstintegrität bereit.  <br/> |
   
### <a name="status-definitions"></a>Statusdefinitionen

|**Status**|**Definition**|
|:-----|:-----|
|**Wird untersucht** | Uns ist ein potenzielles Problem bekannt, und wir sammeln weitere Informationen dazu, was vor sich geht und welche Auswirkungen es hat. |
|**Dienstbeeinträchtigung** | Wir haben bestätigt, dass ein Problem vorliegt, das eine Auswirkung auf die Verwendung eines Diensts oder Features haben kann. Dieser Status wird möglicherweise angezeigt, wenn ein Dienst langsamer als gewöhnlich ausgeführt wird, zeitweilige Unterbrechungen auftreten oder ein Feature nicht funktioniert. |
|**Dienstunterbrechung** | Dieser Status wird angezeigt, wenn wir feststellen, dass sich ein Problem auf den Zugriff der Benutzer auf den Dienst auswirkt. In diesem Fall ist das Problem schwerwiegend und kann konsistent reproduziert werden. |
|**Dienst wird wiederhergestellt** | Die Ursache des Problems wurde erkannt, wir wissen, welche Behebungsmaßnahme zu ergreifen ist, und sind dabei, den Dienst wieder in einen fehlerfreien Zustand zu versetzen. |
|**Erweiterte Wiederherstellung** | Dieser Status gibt an, dass eine Behebungsmaßnahme durchgeführt wird, um den Dienst für die Mehrzahl der Benutzer wiederherzustellen, es dauert jedoch einige Zeit, bis alle betroffenen Systeme erreicht sind. Dieser Status wird möglicherweise auch angezeigt, wenn wir eine temporäre Korrektur vorgenommen haben, um die Auswirkungen zu verringern, während wir an der Bereitstellung einer dauerhaften Lösung arbeiten. |
|**Untersuchung angehalten** | Dieser Status wird angezeigt, wenn unsere detaillierte Untersuchung eines potenziellen Problems dazu führt, dass Kunden um Angabe zusätzlicher Informationen für eine weitere Untersuchung gebeten werden. Wenn Ihre Unterstützung erforderlich ist, informieren wir Sie, welche Daten oder Protokolle wir benötigen. |
|**Dienst wiederhergestellt** | Wir haben bestätigt, dass durch die Behebungsmaßnahme das zugrunde liegende Problem gelöst und der Dienst wieder in einen fehlerfreien Zustand versetzt wurde. Informationen zur Fehlerursache finden Sie unter den Problemdetails. |
|**Vorfallnachsorgebericht veröffentlicht** | Wir haben für ein bestimmtes Problem einen Beitrag veröffentlicht, der Informationen zu den Ursachen sowie nächste Schritte umfasst, um sicherzustellen, dass ein ähnliches Problem nicht wieder auftritt. |
   
## <a name="history"></a>Ereignisprotokoll

Der Dienststatus zeigt den aktuellen Status sowie den Verlauf aller Empfehlungen und Vorfälle für Dienste, die Ihren Mandanten in den letzten 30 Tagen betroffen haben. Zum Anzeigen des früheren Status aller Dienste wählen Sie auf der Seite **Dienststatus** die Option **Verlauf anzeigen** aus. 
  
![Anzeigen des Links zum Statusverlauf](media/12a3e484-1eb4-497f-8cab-8064bccc2ef5.png)
  
Es wird eine Liste aller Nachrichten zum Dienststatus angezeigt, die im ausgewählten Zeitraum veröffentlicht wurden (siehe unten).
  
![Anzeigen des Dienststatusverlaufs](media/5ed20247-121c-4abe-9fe7-9025e26a2d0e.png)
  
Sie können den Statusverlauf entweder für die letzten 7 Tage oder die letzten 30 Tage anzeigen. Wählen Sie eine beliebige Zeile aus, um weitere Details zu diesem Problem anzuzeigen.
  
Weitere Informationen über unsere Verpflichtung zur Verfügbarkeit finden Sie unter [Transparente Vorgänge in Office 365](https://go.microsoft.com/fwlink/?linkid=848695).
  
## <a name="leave-feedback"></a>Feedback geben

Unser Ziel ist es sicherzustellen, dass die Informationen, die wir Ihnen zu einem laufenden Problem geben, aktuell, präzise und nützlich sind. Wenn Sie uns mitteilen möchten, inwieweit wir dieses Ziel erreichen, wählen Sie eine Sternebewertung aus. Nachdem Sie eine Bewertung mit 1 bis 5 Sternen abgegeben haben, können Sie uns Feedback zu bestimmten Details geben. Anhand Ihres Feedbacks können wir unser Dienststatussystem weiter optimieren.
  
## <a name="see-also"></a>Siehe auch

[Teams-Aktivitätsberichte im Microsoft 365 Admin Center](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)