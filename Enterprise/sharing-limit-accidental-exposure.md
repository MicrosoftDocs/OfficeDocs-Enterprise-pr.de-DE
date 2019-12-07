---
title: Begrenzen der versehentlichen Exposition
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Priority
description: Erfahren Sie, wie Sie die versehentliche Exposition von Informationen bei der Freigabe von Dateien für Gäste begrenzen.
ms.openlocfilehash: 3a5a99e96207e407f15abb17d9e1903c8ba52339
ms.sourcegitcommit: 7e65640fb1a86858a95c9ef0edbb58d0f171c5ee
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/06/2019
ms.locfileid: "39886474"
---
# <a name="limit-accidental-exposure-to-files-when-sharing-with-guests"></a>Einschränken des Risikos der versehentlichen Gefährdung von Dateien bei der Freigabe für Gäste

Bei der Freigabe von Dateien und Ordnern für Gäste gibt es eine Vielzahl an Optionen, um das Risiko zu minimieren, dass vertrauliche Informationen versehentlich freigegeben werden. Sie können aus den Optionen in diesem Artikel wählen, um die Anforderungen Ihrer Organisation optimal zu erfüllen.

## <a name="use-best-practices-for-anyone-links"></a>Bewährte Methoden für „Jeder“-Links verwenden

Wenn Personen in Ihrer Organisation eine Freigabe ohne Authentifizierung vornehmen müssen, Sie jedoch befürchten, dass nicht authentifizierte Gäste Inhalte ändern, lesen Sie [Bewährte Methoden für die Freigabe ohne Authentifizierung](best-practices-anonymous-sharing.md), um Anleitungen zum Arbeiten mit der Freigabe ohne Authentifizierung in Ihrer Organisation zu erhalten.

## <a name="turn-off-anyone-links"></a>Deaktivieren von "Jeder"-Links

Wir empfehlen, die *Jeder*-Links für den entsprechenden Inhalt aktiviert zu lassen, da dies die einfachste Freigabemöglichkeit ist und das Risiko reduziert, dass Benutzer andere Lösungen außerhalb der Kontrolle Ihrer IT-Abteilung suchen. *Jeder*-Links können an andere weitergeleitet werden, aber Dateizugriff ist nur für diejenigen möglich, die den Link haben.

Wenn Gäste sich beim Zugreifen auf Inhalte in SharePoint, Gruppen oder Teams authentifizieren sollen, können Sie die *Jeder*-Freigabe deaktivieren. Das verhindert, dass Benutzer Inhalte ohne Authentifizierung freigeben.

Wenn Sie die *Jeder*-Links deaktivieren, können Benutzer Elemente weiterhin mit *Bestimmte Personen*-Links für Gäste freigeben. In diesem Fall müssen alle Gäste sich authentifizieren, bevor sie auf die freigegebenen Inhalte zugreifen können.

Je nach Ihren Anforderungen können Sie *Jeder*-Links für bestimmte Sites oder für Ihre gesamte Organisation deaktivieren.

So deaktivieren Sie *Jeder*-Links für Ihre Organisation
1. Klicken Sie im SharePoint Admin Center links in der Navigation auf **Freigabe**.
2. Legen Sie für die SharePoint-Einstellungen für die externe Freigabe **Neue und vorhandene Gäste** fest.</br>
   ![Screenshot der SharePoint-Site-Einstellungen für die externe Freigabe](media/sharepoint-organization-external-sharing-controls-new-users.png)
3. Klicken Sie auf **Speichern**.

So deaktivieren Sie *Jeder*-Links für eine Site
1. Erweitern Sie im SharePoint Admin Center links in der Navigation **Sites** und klicken Sie auf **Aktive Sites**.
2. Wählen Sie die Site des soeben erstellten Teams aus.
3. Klicken Sie im Menüband auf **Freigabe**. 
4. Vergewissern Sie sich, dass die Freigabe auf **Neue und vorhandene Gäste** festgelegt ist.</br>
   ![Screenshot der SharePoint-Site-Einstellungen für die externe Freigabe](media/sharepoint-site-external-sharing-settings.png)
5. Wenn Sie Änderungen vorgenommen haben, klicken Sie auf **Speichern**.

## <a name="domain-filtering"></a>Domänenfilter

Sie können Zulassungs- oder Ablehnungslisten für Domänen verwenden, um zu bestimmen, aus welchen Domänen Ihre Benutzer Gäste einladen können.

Mit einer Zulassungsliste können Sie eine Liste der Domänen angeben, aus denen die Benutzer in Ihrer Organisation Gäste einladen können. Gasteinladungen zu anderen Domänen werden blockiert. Wenn Ihre Organisation nur mit Gästen aus einer Liste bestimmter Domänen zusammenarbeitet, können Sie diese Funktion verwenden, um die Freigabe für andere Domänen zu verhindern.

Mit einer Ablehnungsliste können Sie eine Liste der Domänen angeben, aus denen die Benutzer in Ihrer Organisation Gäste nicht einladen können. Gasteinladungen zu den aufgelisteten Domänen werden blockiert. Dies kann hilfreich sein, wenn Sie beispielsweise Konkurrenten haben, die nicht Gäste in Ihrer Organisation werden sollen.

Die Zulassungs- und Ablehnungslisten wirken sich nur auf die Freigabe für authentifizierte Gäste aus. Benutzer können weiterhin für Gäste aus verbotenen Domänen freigeben, indem sie *Jeder*-Links verwenden, wenn Sie diese nicht deaktiviert haben. Für optimale Ergebnisse in Bezug auf die Zulassungs- und Ablehnungslisten für Domänen, ziehen Sie die Deaktivierung von *Jeder*-Links wie oben beschrieben in Betracht.

So richten Sie eine Zulassungs- oder Ablehnungsliste für die Gastfreigabe ein
1. Klicken Sie im SharePoint Admin Center links in der Navigation auf **Freigabe**.
2. Aktivieren Sie unter **Erweiterte Einstellungen für externe Freigabe** das Kontrollkästchen **Externe Freigabe nach Domäne einschränken**.
3. Klicken Sie auf **Domänen hinzufügen**.
4. Wählen Sie aus, ob Domänen blockiert werden sollen, geben Sie die Domänen ein, und klicken Sie auf **OK**.</br>
   ![Screenshot der SharePoint-Einstellung „Einschränken der externen Freigabe mithilfe von Domänen“](media/sharepoint-sharing-block-domain.png)
5. Klicken Sie auf **Speichern**.

Wenn Sie die Freigabe mithilfe von Domänen auf einer höheren Ebene als SharePoint und OneDrive einschränken möchten, [lassen Sie Einladungen in Azure Active Directory für B2B-Benutzer aus bestimmten Organisationen zu oder blockieren Sie sie](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list). (Sie müssen die [SharePoint- und OneDrive-Integration mit Azure AD B2B Preview](https://docs.microsoft.com/sharepoint/sharepoint-azureb2b-integration-preview) konfigurieren, damit diese Einstellungen für SharePoint und OneDrive wirksam sind.)

## <a name="limit-guest-sharing-of-files-folders-and-sites-to-specified-security-groups"></a>Einschränken der Freigabe von Dateien, Ordnern und Sites für Gäste auf die angegebenen Sicherheitsgruppen

Sie können die Freigabe von Dateien, Ordnern und Sites für Gäste auf Mitglieder einer spezifischen Sicherheitsgruppe einschränken. Dies ist nützlich, wenn Sie die Gastfreigabe aktivieren möchten, aber mit einem Genehmigungsworkflow oder einem Anforderungsprozess.

So schränken Sie die Gastfreigabe auf Mitglieder einer Sicherheitsgruppe ein
1. Klicken Sie im SharePoint Admin Center links in der Navigation auf **Freigabe**.
2. Folgen Sie unter **Andere Einstellungen** dem Link **Externe Freigabe für bestimmte Sicherheitsgruppen einschränken**.
3. Aktivieren Sie unter **Wer kann außerhalb Ihrer Organisation freigeben** ein oder beide Kontrollkästchen: a. **Erlauben Sie nur ausgewählten Sicherheitsgruppen die Freigabe für authentifizierte externe Benutzer**, um eine Sicherheitsgruppe anzugeben, die für authentifizierte Benutzer freigeben kann. b. **Erlauben Sie nur ausgewählten Sicherheitsgruppen die Freigabe für authentifizierte externe Benutzer und Verwendung anonymer Links**, um eine Sicherheitsgruppe anzugeben, die für authentifizierte Benutzer und über „Jeder“-Links freigeben kann. b.
4. Klicken Sie auf **OK**.

Dies wirkt sich auf Dateien, Ordner und Sites, aber nicht auf Office 365-Gruppen oder -Teams aus. Wenn Mitglieder Gäste zu einer privaten Office 365-Gruppe oder einem privaten Team in Microsoft Teams einladen, wird die Einladung zur Genehmigung an den Gruppen- oder Teambesitzer gesendet.

## <a name="see-also"></a>Siehe auch

[Erstellen einer sicheren Umgebung für die Gastfreigabe](create-a-secure-guest-sharing-environment.md)

[Bewährte Methoden zum Freigeben von Dateien und Ordnern für anonyme Benutzer](best-practices-anonymous-sharing.md)