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
ms.openlocfilehash: 20584f2cb0ecc32da9f5403c36c6af3f0287bea9
ms.sourcegitcommit: ef5447665d6ebbc79399b560c9725d74e1479f7d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/15/2020
ms.locfileid: "41122584"
---
# <a name="how-to-check-office-365-service-health"></a>Überprüfen des Office 365-Dienststatus

[![Hinweis, der Sie darüber informiert, dass sich das Admin Center ändert und Sie unter "aka.ms/aboutM365preview" weitere Details finden.](media/O365-Admin-AdminCenterChanging.png)](https://docs.microsoft.com/office365/admin/microsoft-365-admin-center-preview?view=o365-worldwide)

Sie können den Status Ihrer Microsoft-Dienste, z. B. Office im Web, Yammer, Microsoft Dynamics CRM und Microsoft Intune Cloud Services, auf der Office 365-Seite **Dienststatus** im [Admin Center](https://go.microsoft.com/fwlink/p/?linkid=2024339) einsehen. Wenn bei einem Clouddienst Probleme auftreten, können Sie den Dienststatus überprüfen, um festzustellen, ob es sich um ein bekanntes Problem handelt, für das bereits an einer Lösung gearbeitet wird, bevor Sie den Support anrufen oder Zeit für die Problembehandlung aufwenden.

Wenn Sie sich nicht im Serviceportal anmelden können, können Sie auf der [Dienststatus-Seite](https://status.office365.com) nach bekannten Problemen suchen, die Sie daran hindern, sich bei Ihrem Mandanten anzumelden.
  
### <a name="how-to-check-service-health"></a>Überprüfen des Dienststatus

1. Wechseln Sie zum Admin Center unter [https://admin.microsoft.com](https://go.microsoft.com/fwlink/p/?linkid=2024339), und melden Sie sich mit einem Administratorkonto an.

    > [!NOTE]
    > Personen, denen die Rolle eines globalen Administrators oder Serviceadministrators zugewiesen ist, können den Dienststatus anzeigen. Damit Exchange-, SharePoint- und Skype for Business-Administratoren den Dienststatus anzeigen können, muss ihnen auch die Rolle des Dienstadministrators zugewiesen sein. Weitere Informationen zu Rollen, die den Dienststatus anzeigen können, finden Sie unter [Informationen zu Administratorrollen](https://docs.microsoft.com/office365/admin/add-users/about-admin-roles?view=o365-worldwide#roles-available-in-the-microsoft-365-admin-center).
  
2. Wenn Sie das neue Admin Center nicht verwenden, wählen Sie auf der Startseite oben rechts den Umschalter **Das neue Admin Center testen** aus.

3. Zum Anzeigen des Dienststatus wechseln Sie im Admin Center zu **Status** > **Dienststatus**, oder wählen Sie auf dem **Startdashboard** die Karte **Dienststatus** aus. Die Dashboardkarte gibt an, ob ein Problem mit einem aktiven Dienst vorliegt, und stellt einen Link zur Seite mit Details zum **Dienststatus** bereit.
  
4. Der Status der einzelnen Clouddienste wird auf der Seite **Dienstatus** in einem Tabellenformat angezeigt.

   ![Ansicht der aktuellen Probleme unter "Dienststatus"](media/service-health-all-services.png)

Auf der Registerkarte **Alle Dienste** (Standardansicht) werden alle Dienste und ihr aktueller Status angezeigt. Ein Symbol und die Spalte **Status** geben den Status jedes Diensts an. Wenn Sie die Ansicht nach Diensten filtern möchten, die aktuell einen Vorfall aufweisen, wählen Sie die Registerkarte **Vorfälle** oben auf der Seite aus. Bei Auswahl der Registerkarte **Empfehlungen** werden nur Dienste angezeigt, für die derzeit eine Empfehlung angegeben ist. Auf der Registerkarte **Verlauf** wird der Verlauf von Vorfällen und Empfehlungen angezeigt, die aufgelöst wurden.

Wenn ein Problem mit einem Office 365 Dienst auftritt und auf der Seite " **Dienststatus** " nicht aufgeführt ist, informieren Sie uns darüber, indem Sie **ein Problem melden**auswählen und das kurze Formular ausfüllen. Wir werden uns mit verwandten Daten und Berichten aus anderen Organisationen beschäftigen, um zu sehen, wie weit verbreitet das Problem ist und ob es von unserem Dienst stammt. Wenn dies der Fall ist, fügen wir ihn als neuen Vorfall oder eine neue Empfehlung auf der Seite **Dienst Integrität** hinzu, auf der Sie die Lösung nachverfolgen können. Wenn es in der Liste nicht innerhalb von 30 Minuten angezeigt wird, sollten Sie sich an den Support wenden, um das Problem zu beheben.

> [!TIP]
> Sie können den Dienststatus auch mithilfe der [Office 365 Admin-App](https://go.microsoft.com/fwlink/p/?linkid=627216) auf Ihrem mobilen Gerät anzeigen. Dies ist eine hervorragende Möglichkeit, mit Pushbenachrichtigungen auf dem Laufenden zu bleiben. 
  
### <a name="view-details-of-posted-service-health"></a>Anzeigen von Details des veröffentlichten Dienststatus

Wenn Sie in der Ansicht **Alle Dienste** den Dienststatus auswählen, wird eine Zusammenfassungsansicht der Empfehlungen oder Vorfälle angezeigt.
  
![Screenshot der Dienstempfehlung](media/service-health-advisory.png)

Die Empfehlungs- oder Vorfallzusammenfassung enthält folgende Informationen:

- **Titel**: Eine Zusammenfassung des Problems.
- **Dienst**: Der Name des betroffenen Diensts.
- **ID**: Ein numerischer Bezeichner für das Problem.
- **Status**: Wie sich dieses Problem auf den Dienst auswirkt.
- **Startzeit**: Der Zeitpunkt, zu dem das Problem begann.
- **Letzte Aktualisierung**: Der Zeitpunkt der letzten Aktualisierung der Nachricht zum Dienststatus. Wir veröffentlichen häufig Nachrichten, um Sie über die Fortschritte beim Anwenden einer Lösung zu informieren.

Wählen Sie das Problem aus, um die Detailseite mit weiteren Informationen zum Problem anzuzeigen, einschließlich des [Verlaufs](#history) aller Nachrichten, die wir während unserer Arbeit an einer Lösung veröffentlicht haben.

![Screenshot mit Details zum Problem](media/service-health-advisory-detail.png)

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

### <a name="history"></a>Verlauf

Der Dienststatus zeigt den aktuellen Status sowie den Verlauf aller Empfehlungen und Vorfälle für Dienste, die Ihren Mandanten in den letzten 30 Tagen betroffen haben. Zum Anzeigen des früheren Status aller Dienste wählen Sie auf der Seite mit den Problemdetails die Option **Verlauf anzeigen** aus.
  
![Anzeigen des Links zum Statusverlauf](media/service-health-view-history.png)
  
Es wird eine Liste aller Nachrichten zum Dienststatus angezeigt, die im ausgewählten Zeitraum veröffentlicht wurden (siehe unten).
  
![Anzeigen des Dienststatusverlaufs](media/service-health-history.png)
  
Erweitern Sie eine beliebige Zeile, um weitere Details zum Problem anzuzeigen.
  
Weitere Informationen über unsere Verpflichtung zur Verfügbarkeit finden Sie unter [Transparente Vorgänge in Office 365](https://go.microsoft.com/fwlink/?linkid=848695).
  
## <a name="leave-feedback"></a>Feedback geben

Unser Ziel ist es sicherzustellen, dass die Informationen, die wir Ihnen zu einem laufenden Problem geben, aktuell, präzise und nützlich sind. Wenn Sie uns mitteilen möchten, inwieweit wir dieses Ziel erreichen, wählen Sie eine Sternebewertung aus. Nachdem Sie eine Bewertung mit 1 bis 5 Sternen abgegeben haben, können Sie uns Feedback zu bestimmten Details geben. Anhand Ihres Feedbacks können wir unser Dienststatussystem weiter optimieren.
  
## <a name="see-also"></a>Siehe auch

[Teams-Aktivitätsberichte im Microsoft 365 Admin Center](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)