---
title: Wiederherstellen gelöschter Elemente in einem Benutzerpostfach – Hilfe für Administratoren
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 6/29/2018
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: eb15194b-63ec-41b0-8d90-1823d3f558e4
description: 'Dieser Artikel richtet sich an Administratoren. Löscht ein Benutzer endgültig Elemente aus seinem Outlook-Postfach? Der Benutzer möchte Sie zurück, kann Sie aber nicht wiederherstellen. Möglicherweise können Sie die gelöschten Elemente wiederherstellen, wenn Sie nicht dauerhaft aus dem Postfach des Benutzers entfernt wurden. '
ms.openlocfilehash: 5ec1ba41924d773859d742bc06bbfe76582072c1
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071211"
---
# <a name="recover-deleted-items-in-a-user-mailbox---admin-help"></a>Wiederherstellen gelöschter Elemente in einem Benutzerpostfach – Hilfe für Administratoren

**Dieser Artikel richtet sich an Administratoren. Versuchen Sie, gelöschte Elemente in Ihrem eigenen Postfach wiederherzustellen?** Führen Sie einen der folgenden Schritte durch: 
- [Wiederherstellen gelöschter Elemente in Outlook für Windows](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)
- [Wiederherstellen gelöschter Elemente oder E-Mails in Outlook Online](https://support.office.com/article/c3d8fc15-eeef-4f1c-81df-e27964b7edd4)
- [Wiederherstellen gelöschter e-Mail-Nachrichten in Outlook im Web](https://support.office.com/article/a8ca78ac-4721-4066-95dd-571842e9fb11)
- [Outlook.com](https://go.microsoft.com/fwlink/p/?LinkID=623435)
   
Löscht ein Benutzer endgültig Elemente aus seinem Outlook-Postfach? Der Benutzer möchte Sie zurück, kann Sie aber nicht wiederherstellen. Möglicherweise können Sie die gelöschten Elemente wiederherstellen, wenn Sie nicht dauerhaft aus dem Postfach des Benutzers entfernt wurden. Hierzu verwenden Sie das in-Place-eDiscovery-Tool in Exchange Online, um nach gelöschten e-Mails und anderen Elementen wie Kontakten, Kalenderterminen und Aufgaben im Postfach eines Benutzers zu suchen. Wenn Sie die gelöschten Elemente finden, können Sie Sie in eine PST-Datei exportieren (auch als Outlook-Datendatei bezeichnet), die der Benutzer dann zum Wiederherstellen der Elemente in seinem Postfach verwenden kann.
  
Im folgenden finden Sie die Schritte zum Wiederherstellen gelöschter Elemente im Postfach eines Benutzers. Wie lange dauert es? Je nachdem, wie viele Elemente Sie wiederherstellen möchten, dauert es zum ersten Mal 20 oder 30 Minuten, bis alle Schritte ausgeführt wurden.
  
> [!NOTE]
> Sie müssen ein Exchange- **Administrator** oder ein **globaler Administrator** in Office 365 oder Mitglied der Rollengruppe "Organisationsverwaltung" in Exchange Online sein, um die Schritte in diesem Artikel ausführen zu können. Weitere Informationen finden Sie unter [Informationen zu Office 365-Administratorrollen](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d). 
  
## <a name="step-1-assign-yourself-ediscovery-permissions"></a>Schritt 1: Zuweisen von eDiscovery-Berechtigungen für sich selbst
<a name="step1"> </a>

Der erste Schritt besteht darin, sich selbst die erforderlichen Berechtigungen in Exchange Online zuzuweisen, damit Sie das in-Place-eDiscovery-Tool verwenden können, um das Postfach eines Benutzers zu durchsuchen. Sie müssen dies nur einmal tun. Wenn Sie in Zukunft ein anderes Postfach durchsuchen müssen, können Sie diesen Schritt überspringen.
  
1. [Where to sign in to Office 365 for business](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) mit Ihrem Firmen- oder Schulkonto an. 
    
2. Wählen Sie das App- ![Start Symbol in der oberen linken Ecke](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) des App-Start Symbols in Office 365 aus, und klicken Sie auf **Admin**.
    
3. Erweitern Sie im linken Navigationsbereich des Office 365 Admin Center den Knoten **Admin**Center, und klicken Sie dann auf **Exchange**.
    
    ![Admin Center-Liste](media/7d308eb7-ba63-4156-a845-3770facc5de4.PNG)
  
4. Klicken Sie im Exchange Admin Center auf **Berechtigungen**, und klicken Sie dann auf **Administratorrollen**.
    
5. Wählen Sie in der Listenansicht **Ermittlungsverwaltung**aus, und klicken ****![Sie dann auf](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif)Bearbeitungssymbol bearbeiten.
    
    ![Hinzufügen der Rollengruppe "Discoveryverwaltung" in der Exchange-Verwaltungskonsole](media/e5c98e93-d6a0-40c5-a143-bac956eedaa7.png)
  
6. Klicken Sie in **Rollengruppe**unter **Mitglieder**auf ****![Symbol](media/8ee52980-254b-440b-99a2-18d068de62d3.gif)hinzufügen.
    
7. Wählen Sie in **Elemente auswählen**aus der Liste der Namen aus, klicken Sie auf **Hinzufügen**, und klicken Sie dann auf **OK**.
    
    > [!NOTE]
    > Sie können auch eine Gruppe hinzufügen, von der Sie ein Mitglied sind, beispielsweise Organisationsverwaltung oder TenantAdmins. Wenn Sie eine Gruppe hinzufügen, werden anderen Mitgliedern der Gruppe die erforderlichen Berechtigungen zum Ausführen des in-Place-eDiscovery-Tools zugewiesen. 
  
8. Klicken Sie in **Rollengruppe**auf **Speichern**.
    
9. Abmelden von Office 365.
    
    Sie müssen sich abmelden, bevor Sie den nächsten Schritt starten, damit die neuen Berechtigungen wirksam werden.
    
> [!CAUTION]
> Mitglieder der Rollengruppe "Discoveryverwaltung" können auf vertrauliche Nachrichteninhalte zugreifen. Dazu gehört das Durchsuchen aller Postfächer in Ihrer Organisation, die Vorschau der Suchergebnisse (und andere Postfachelemente), das Kopieren der Ergebnisse in ein Discovery-Postfach und das Exportieren der Suchergebnisse in eine PST-Datei. 
  
[Return to top](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-2-search-the-users-mailbox-for-deleted-items"></a>Schritt 2: Durchsuchen des Postfachs des Benutzers nach gelöschten Elementen
<a name="step2"> </a>

Wenn Sie eine in-Place-eDiscovery-Suche ausführen, wird der Ordner "Wiederherstellbare Elemente" im Postfach, den Sie durchsuchen, automatisch in die Suche eingeschlossen. Im Ordner "Wiederherstellbare Elemente" werden endgültig gelöschte Elemente gespeichert, bis Sie aus dem Postfach gelöscht werden. Wenn ein Element also nicht bereinigt wurde, sollte es mithilfe des in-Place eDiscovery-Tools gefunden werden können.
  
1. [Where to sign in to Office 365 for business](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) mit Ihrem Firmen- oder Schulkonto an. 
    
2. Wählen Sie das App- ![Start Symbol in der oberen linken Ecke](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) des App-Start Symbols in Office 365 aus, und klicken Sie auf **Admin**.
    
3. Erweitern Sie im linken Navigationsbereich des Office 365 Admin Center **Administrator**, und klicken Sie dann auf **Exchange**.
    
4. Klicken Sie im Exchange Admin Center auf **Compliance-Verwaltung**, klicken Sie **in- &amp; situ-eDiscovery-Aufbewahrung**, und klicken](media/8ee52980-254b-440b-99a2-18d068de62d3.gif)Sie dann auf **Neues**![Add-Symbol.
    
    ![Klicken Sie in der Exchange-Verwaltungskonsole auf der Seite "Kompatibilitätsverwaltung" auf in-situ-eDiscovery und halten](media/9d9ff0f5-b9be-45b8-8b5e-6037a856b0a8.png)
  
5. Geben Sie auf der Seite **Name und Beschreibung** einen Namen für die Suche ein (beispielsweise den Namen des Benutzers, für den Sie e-Mails wiederherstellen), eine optionale Beschreibung, und klicken Sie dann auf **weiter**.
    
6. Klicken Sie auf der Seite **Postfächer** auf **zu durchsuchende Postfächer angeben**, und klicken](media/8ee52980-254b-440b-99a2-18d068de62d3.gif)Sie dann auf Add-Symbol **Hinzufügen**![.
    
    ![Klicken Sie auf zu durchsuchende Postfächer angeben, um ein spezifische-Postfach zu durchsuchen](media/83879a40-5e5c-49a8-be3b-c0023d197588.png)
  
7. Suchen Sie den Namen des Benutzers, für den Sie die gelöschten e-Mails wiederherstellen, und wählen Sie ihn aus, klicken Sie auf **Hinzufügen**, und klicken Sie dann auf **OK**.
    
8. Klicken Sie auf **Weiter**.
    
    Die Seite **Suchabfrage** wird angezeigt. Hier definieren Sie die Suchkriterien, die Ihnen helfen, die fehlenden Elemente im Postfach des Benutzers zu finden. 
    
9. Füllen Sie auf der Seite **Suchabfrage** die folgenden Felder aus: 
    
  - **Alle Inhalte einbeziehen** Wählen Sie diese Option aus, um den gesamten Inhalt des Postfachs des Benutzers in die Suchergebnisse einzubeziehen. Wenn Sie diese Option auswählen, können Sie keine weiteren Suchkriterien angeben. 
    
  - **Filtern basierend auf Kriterien** Wählen Sie diese Option aus, um die Suchkriterien anzugeben, einschließlich Schlüsselwörter, Start-und Enddaten, Absender-und Empfängeradressen sowie Nachrichtentypen. 
    
    ![Erstellen einer Suche basierend auf Kriterien wie Stichwörtern, Datumsbereichen, Empfängern und Nachrichtentypen](media/ee47b833-9122-46a0-85e6-fcbe25be0dd5.png)
  
|**Feld**|**Verwenden Sie dies, um...**|
|:-----|:-----|
|![Number one in a pink circle](media/a4da261d-2516-48c5-b58a-9c452b9086b8.png)           <br/> |Angeben von Schlüsselwörtern, Datumsbereichen, Empfängern und Nachrichtentypen.  <br/> |
|![Number two in a pink circle.](media/de3c1ab4-4f01-4026-b1ba-3265bdb32a89.png)           <br/> |Suchen Sie nach Nachrichten mit Schlüsselwörtern oder Phrasen, und verwenden Sie logische Operatoren wie **und** oder **oder**.  <br/> |
|![Number three in a pink circle.](media/60fa378c-6ac1-4cbd-a782-2fa7ca619dc6.png)           <br/> |Sucht nach Nachrichten, die in einem Datumsbereich gesendet oder empfangen wurden.  <br/> |
|![Number 4 in a pink circle.](media/1a0ff2ce-0942-405a-94e3-9bfeb1e5059e.png)           <br/> |Suchen Sie nach Nachrichten, die von bestimmten Personen empfangen oder gesendet wurden.  <br/> |
|![Nummer fünf in einem rosa Kreis.](media/878cc815-0165-49ba-a1ee-9236e5980403.png)           <br/> |Suchen Sie nach allen Nachrichtentypen, oder wählen Sie bestimmte aus.  <br/> |
   
    > [!TIP]
    >  Here's a few tips about how to build a search query to find missing items. Try to get as much information from the user to help you create a search query so you can find what you're looking for. >  If you not sure how to find a missing message, consider using the **Include all content** option. The search results will include all items in the user's Recoverable Items folder, including the hidden folder (called the Purges folder) that contain items that have been purged by the user. Then you can go to Step 3, copy the results to a discovery mailbox, and look at the message in the hidden folder. >  If you know approximately when the missing message was originally sent or received by the user, use the **Specify start date** and **Specify end date** options to provide a date range. This will return all messages sent or received by the user within that date range. Specifying a date range is a really good way to narrow the search results. >  If you know who sent the missing email, use the **From** box to specify this sender. >  If you want to narrow the search results to different types of mailbox items, click **Select message types**, click **Select the message types to search**, and then choose a specific message type to search for. For example, you can search only for calendar items or contacts. Here's a screenshot of the different message types you can search for; the default is to search for all message types. 
  
    Click **Next** when you've completed the **Search query** page. 
    
10. Klicken Sie auf der Seite Einstellungen für die **direkte Aufbewahrung** auf **Fertig stellen** , um die Suche zu starten. Zum Wiederherstellen gelöschter e-Mails gibt es keinen Grund, das Postfach des Benutzers zu halten. 
    
    Nachdem Sie die Suche gestartet haben, zeigt Exchange eine Schätzung der Gesamtgröße und Anzahl der Elemente an, die von der Suche basierend auf den von Ihnen angegebenen Kriterien zurückgegeben werden.
    
11. Wählen Sie die soeben erstellte Suche aus, ****![und klicken](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) Sie auf aktualisieren, um die im Detailbereich angezeigten Informationen zu aktualisieren. Der Status **Estimate succeeded** gibt an, dass die Suche abgeschlossen ist. In Exchange wird außerdem eine Schätzung der Gesamtanzahl der Elemente (und deren Größe) angezeigt, die bei der Suche basierend auf den in Schritt 9 angegebenen Suchkriterien gefunden wurden. 
    
12. Klicken Sie im Detailbereich auf **Vorschau der Suchergebnisse** , um die gefundenen Elemente anzuzeigen. Dies kann Ihnen helfen, die gesuchten Elemente zu identifizieren. Wenn Sie feststellen, welche Elemente Sie wiederherstellen möchten, fahren Sie mit Schritt 4 fort, um die Suchergebnisse in eine PST-Datei zu exportieren. 
    
    ![Klicken Sie auf Suchergebnisse anzeigen, um das Element anzuzeigen, das Sie wiederherstellen möchten.](media/a2cea921-dafa-45d6-97d4-ae45a226b8d3.png)
  
13. Wenn Sie nicht finden, wonach Sie suchen, können Sie Ihre Suchkriterien überarbeiten, indem Sie die Suche auswählen, ****![auf Bearbeitungssymbol](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif)bearbeiten und dann auf **Suchabfrage**klicken. Ändern Sie die Suchkriterien, und führen Sie die Suche erneut aus.
    
[Return to top](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="optional-step-3-copy-the-search-results-to-a-discovery-mailbox"></a>Optional Schritt 3: Kopieren der Suchergebnisse in ein Discovery-Postfach
<a name="step3"> </a>

Wenn Sie keine Elemente finden können, indem Sie eine Vorschau der Suchergebnisse anzeigen, oder wenn Sie sehen möchten, welche Elemente im Ordner "Wiederherstellbare Elemente" des Benutzers vorhanden sind, können Sie die Suchergebnisse in ein spezielles Postfach (als Discovery-Postfach bezeichnet) kopieren und dieses Postfach dann in Outlook im Web t öffnen. o zeigen Sie die tatsächlichen Elemente an. Der beste Grund zum Kopieren der Suchergebnisse ist, dass Sie die Elemente im Ordner "Wiederherstellbare Elemente" des Benutzers anzeigen können. Wahrscheinlich befindet sich das Element, das Sie wiederherstellen möchten, im Unterordner purges. 
  
1. Wechseln Sie im Exchange Admin Center zu **Compliance Management** \> **in-situ-eDiscovery &amp; -** Speicher.
    
2. Wählen Sie in der Liste der Suchvorgänge die Suche aus, die Sie in Schritt 2 erstellt haben.
    
3. Klicken Sie auf](media/c94e8591-7044-4650-a0d1-c57c0633ab4f.png)Such Suche, und klicken Sie dann in der Dropdownliste auf **Suchergebnisse kopieren** . ****![ 
    
    ![Klicken Sie auf suchen, und klicken Sie dann auf Suchergebnisse kopieren.](media/7888df82-94b4-4e44-8a53-f66854dc7c86.png)
  
4. Klicken Sie auf der Seite **Suchergebnisse kopieren** auf **Durchsuchen**.
    
    ![Kontrollkästchen bei Wiederherstellung gelöschter Elemente deaktiviert lassen](media/37f27999-a5b2-4fed-87e2-bad6dc23cdae.png)
  
5. Klicken Sie unter **Anzeige Name**auf **Discovery-Such Postfach**, und klicken Sie dann auf **OK**.
    
    ![Kopieren der Suchergebnisse in das standardmäßige Discovery-Such Postfach](media/36e8ef47-0035-4982-9ed6-426719c5f9ec.png)
  
    > [!NOTE]
    > Das Discovery-Such Postfach ist ein Standardmäßiges Ermittlungspostfach, das automatisch in Ihrer Office 365-Organisation erstellt wird. 
  
6. Klicken Sie auf der Seite **Suchergebnisse kopieren** auf **Kopieren** , um den Prozess zum Kopieren der Suchergebnisse in das Such Postfach für die Suche zu starten. 
    
    ![Klicken Sie auf Kopieren, um die Suchergebnisse in das Such Postfach für die Suche zu kopieren.](media/71307a9d-f7a1-4e01-ae37-1d49040cc3fd.png)
  
7. Klicken Sie auf](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) aktualisieren, um die Informationen über den Kopierstatus zu aktualisieren, die im Detailbereich angezeigt werden. ****![ 
    
8. Klicken Sie nach Abschluss des Kopiervorgangs auf **Öffnen** , um das Such Postfach für die Suche zu öffnen, um die Suchergebnisse anzuzeigen. 
    
    ![Klicken Sie auf öffnen, um zum Such Postfach der Suche zu wechseln, um die Suchergebnisse anzuzeigen.](media/6cc81e0f-ceed-4464-9040-79b6f920de35.png)
  
    Die Suchergebnisse, die in das Such Postfach der Suche kopiert werden, werden in einem Ordner mit demselben Namen wie die in-Place-eDiscovery-Suche abgelegt. Sie können auf einen Ordner klicken, um die Elemente in diesem Ordner anzuzeigen.
    
    ![Suchergebnisse im Discovery-Such Postfach; Elemente im Ordner "Säuberungen" können nur von einem Administrator wiederhergestellt werden.](media/2ef8e5fb-3e63-4f62-938e-307efe9f6998.gif)
  
    Wenn Sie eine Suche ausführen, wird auch der Ordner "Wiederherstellbare Elemente" des Benutzers durchsucht. Das ist der Fall, wenn Elemente im Ordner "Wiederherstellbare Elemente" die Suchkriterien erfüllen, Sie in den Suchergebnissen enthalten sind. Elemente im Ordner "Löschungen" sind Elemente, die der Benutzer dauerhaft gelöscht hat (durch Löschen eines Elements aus dem Ordner "Gelöschte Elemente" oder durch auswählen und drücken von **UMSCHALT + ENTF**. Ein Benutzer kann das Tool gelöschte Elemente wiederherstellen in Outlook oder Outlook im Web verwenden, um Elemente im Lösch Ordner wiederherzustellen. Elemente im Ordner "purges" sind Elemente, die der Benutzer mithilfe des Tools "Gelöschte Elemente wiederherstellen" gelöscht hat, oder Elemente, die Sie automatisch durch eine auf das Postfach angewendete Richtlinie gelöscht haben. In beiden Fällen kann nur ein Administrator Elemente im Ordner "Purge" wiederherstellen. 
    
    > [!TIP]
    > Wenn ein Benutzer ein gelöschtes Element nicht mithilfe des Tools "Wiederherstellbare Elemente" finden kann, aber dieses Element ist noch wiederherstellbar (was bedeutet, dass es nicht dauerhaft aus dem Postfach entfernt wurde), befindet es sich mehr als wahrscheinlich im Ordner "purges". Achten Sie also darauf, im Ordner purges nach dem gelöschten Element zu suchen, das Sie für einen Benutzer wiederherstellen möchten. 
  
[Return to top](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-4-export-the-search-results-to-a-pst-file"></a>Schritt 4: Exportieren der Suchergebnisse in eine PST-Datei
<a name="step4"> </a>

Nachdem Sie das Element gefunden haben, das Sie für einen Benutzer wiederherstellen möchten, müssen Sie im nächsten Schritt die Ergebnisse aus der in Schritt 2 ausgeführten Suche in eine PST-Datei exportieren. Der Benutzer verwendet diese PST-Datei im nächsten Schritt, um das gelöschte Element in seinem Postfach wiederherzustellen.
  
1. Wechseln Sie im Exchange Admin Center zu **Compliance Management** \> **in-situ-eDiscovery &amp; -** Speicher.
    
2. Wählen Sie in der Liste der Suchvorgänge die Suche aus, die Sie in Schritt 2 erstellt haben.
    
3. Klicken Sie auf **in eine PST-Datei exportieren**.
    
    ![Klicken Sie auf in eine PST-Datei exportieren.](media/4e59ae17-4541-43f4-a6d1-1f8b9ba9404b.png)
  
4. Wenn Sie aufgefordert werden, das eDiscovery-Export Tool zu installieren, klicken Sie auf **Ausführen**.
    
5. Klicken Sie im eDiscovery-PST-Export Tool auf **Durchsuchen** , um den Speicherort für die PST-Datei anzugeben. 
    
    ![Das eDiscovery-PST-Export Tool](media/17274d27-992e-4034-8133-8f793f554e6c.png)
  
    Sie können die Optionen zum Aktivieren der Deduplizierung ignorieren und nicht durchsuchbare Elemente einbeziehen.
    
6. Klicken Sie auf **starten** , um die PST-Datei auf Ihren Computer herunterzuladen. 
    
    Das **eDiscovery-PST-Export Tool** zeigt Statusinformationen zum Exportvorgang an. Nach Abschluss des Exports können Sie auf die Datei an dem Speicherort zugreifen, an dem Sie heruntergeladen wurde. 
    
[Return to top](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-5-restore-the-recovered-items-to-the-users-mailbox"></a>Schritt 5: Wiederherstellen der wiederhergestellten Elemente im Postfach des Benutzers
<a name="step5"> </a>

Im letzten Schritt wird die in Schritt 4 exportierte PST-Datei verwendet, um die wiederhergestellten Elemente im Postfach des Benutzers wiederherzustellen. Nachdem Sie die PST-Datei an den Benutzer gesendet haben, wird im weiteren Verlauf dieses Schritts der Benutzer zum Öffnen der PST-Datei und zum Verschieben der wiederhergestellten Elemente in einen anderen Ordner in Ihrem Postfach ausgeführt. Schrittweise Anweisungen können Sie dem Benutzer auch einen Link zu diesem Thema senden: [Öffnen und Schließen von Outlook-Datendateien (PST)](https://support.office.com/article/381b776d-7511-45a0-953a-0935c79d24f2). Oder Sie können dem Benutzer einen Link zum Abschnitt [Wiederherstellen gelöschter Elemente in ein Postfach mithilfe einer PST-Datei](recover-deleted-items-in-a-mailbox.md#restoredeleteditems) weiter unten senden und Sie bitten, diese Schritte auszuführen. 
  
 **Senden der PST-Datei an den Benutzer**
  
Der letzte Schritt, den Sie ausführen müssen, ist das Senden der PST-Datei, die in Schritt 4 für den Benutzer exportiert wurde. Hierzu gibt es verschiedene Möglichkeiten:
  
- Fügen Sie die PST-Datei an eine e-Mail-Nachricht an. Wenn Outlook so konfiguriert ist, dass PST-Dateien blockiert werden, müssen Sie die Datei komprimieren und dann an die Nachricht anfügen. Dazu gehen Sie so vor:
    
1. Navigieren Sie in Windows Explorer oder im Datei-Explorer zur PST-Datei.
    
2. Klicken Sie mit der rechten Maustaste auf die Datei, und wählen Sie dann **in** \> **komprimierten Ordner (gezippt)** senden aus. Windows erstellt eine neue ZIP-Datei und gibt ihr einen identischen Namen wie die PST-Datei.
    
3. Fügen Sie die komprimierte PST-Datei an eine e-Mail-Nachricht an, und senden Sie Sie an den Benutzer, der dann die Datei dekomprimieren kann, indem Sie darauf klickt.
    
- Kopieren Sie die PST-Datei in einen freigegebenen Ordner, auf den der Benutzer zugreifen und diesen abrufen kann.
    
Die Schritte im nächsten Abschnitt werden vom Benutzer ausgeführt, um die gelöschten Elemente in Ihrem Postfach wiederherzustellen.
  
 **Wiederherstellen gelöschter Elemente in einem Postfach mithilfe einer PST-Datei**
  
Sie müssen die Outlook-Desktop-App verwenden, um ein gelöschtes Element mithilfe einer PST-Datei wiederherzustellen. Sie können Outlook Web App oder Outlook im Web nicht verwenden, um eine PST-Datei zu öffnen.
  
1. Klicken Sie in Outlook 2013 oder Outlook 2016 auf die Registerkarte **Datei** . 
    
2. Klicken Sie auf **Export öffnen &amp; **, und klicken Sie dann auf **Outlook-Datendatei öffnen**.
    
3. Navigieren Sie zu dem Speicherort, an dem Sie die PST-Datei gespeichert haben, die Ihr Administrator gesendet hat.
    
4. Wählen Sie die PST-Datei aus, und klicken Sie dann auf **Öffnen**.
    
    Die PST-Datei wird in der linken Navigationsleiste in Outlook angezeigt.
    
    ![Die PST-Datei wird in der linken Navigationsleiste in Outlook angezeigt.](media/c9389392-d08a-4aa7-848c-4986d448b0f2.png)
  
5. Klicken Sie auf die Pfeile, um die PST-Datei und die darunter liegenden Ordner zu erweitern, um das Element zu suchen, das Sie wiederherstellen möchten.
    
    ![Suchen Sie im Ordner "purges" nach dem Element, das Sie wiederherstellen möchten.](media/d4e372d9-ac23-4e95-8639-d8da690fefa7.png)
  
    > [!TIP]
    > Suchen Sie im Ordner purges nach dem Element, das Sie wiederherstellen möchten. Dies ist ein ausgeblendeter Ordner, in den gelöschte Elemente verschoben werden. Wahrscheinlich ist das Element, das Ihr Administrator wiederhergestellt hat, in diesem Ordner. 
  
6. Klicken Sie mit der rechten Maustaste auf das Element, das Sie wiederherstellen möchten, und klicken Sie dann auf **anderen Ordner** **verschieben** \> .
    
    ![Klicken Sie auf verschieben, und wählen Sie dann anderer Ordner aus](media/090063df-2aa0-444a-8e47-abd6fe6cf7a8.png)
  
7. Klicken Sie auf **Posteingang**, und klicken Sie dann auf **OK**, um das Element in Ihren Posteingang zu verschieben.
    
    **Tipp:** Führen Sie eine der folgenden Aktionen aus, um andere Elementtypen wiederherzustellen: 
    
  - Klicken Sie zum Wiederherstellen eines Kalenderelements mit der rechten Maustaste darauf, und klicken Sie dann auf **anderen Ordner** \> **Kalender** **verschieben** \> .
    
  - Klicken Sie zum Wiederherstellen eines Kontakts mit der rechten Maustaste darauf, und klicken Sie dann auf **andere Ordner** \> **Kontakte** **verschieben** \> .
    
  - Klicken Sie zum Wiederherstellen einer Aufgabe mit der rechten Maustaste darauf, und klicken Sie dann auf **andere Ordner** \> **Aufgaben** **verschieben** \> .
    
![Auswählen eines Ordners zum Verschieben anderer Elementtypen](media/f8290131-43f2-46f1-bc07-228c2d83b96c.png)
  
    Note that calendar items, contacts, and tasks are located directly in the Purges folder, and not in a Calendar, Contacts, or Tasks subfolder. However, you can sort by **Type** to group similar types of items. 
    
8. Wenn Sie die Wiederherstellung gelöschter Elemente abgeschlossen haben, klicken Sie in der linken Navigationsleiste mit der rechten Maustaste auf die PST-Datei, und wählen Sie **"Namen der PST-Datei"** aus.
    
[Return to top](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="more-information"></a>Weitere Informationen
<a name="moreinfo"> </a>

- Möglicherweise kann ein Benutzer ein dauerhaft gelöschtes Element wiederherstellen, wenn der Aufbewahrungszeitraum für gelöschte Elemente für das Element nicht abgelaufen ist. Als Administrator haben Sie möglicherweise angegeben, wie lange Elemente im Ordner "Wiederherstellbare Elemente" für die Recovery zur Verfügung stehen. Es kann beispielsweise eine Richtlinie geben, mit der alle Elemente im Ordner "Gelöschte Elemente" eines Benutzers 30 Tage lang gelöscht werden, und eine andere Richtlinie, mit deren Hilfe Benutzer im Ordner "Wiederherstellbare Elemente" bis zu 14 Tage wiederhergestellt werden können. Nach Ablauf dieser 14 Tage können Sie jedoch mithilfe der Verfahren in diesem Thema möglicherweise ein Element im Postfach eines Benutzers wiederherstellen.
    
- Benutzer können ein gelöschtes Element wiederherstellen, wenn es nicht gelöscht wurde und wenn die Aufbewahrungsdauer für das gelöschte Element nicht abgelaufen ist. Damit Benutzer gelöschte Elemente im Postfach wiederherstellen können, verweisen Sie auf eines der folgenden Themen:
    
  - [Wiederherstellen gelöschter Elemente in Outlook für Windows](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)
    
  - [Wiederherstellen gelöschter Elemente in Outlook 2010](https://support.office.com/article/cd9dfe12-8e8c-4a21-bbbf-4bd103a3f1fe)
    
  - [Wiederherstellen gelöschter Elemente oder E-Mails in Outlook Online](https://support.office.com/article/c3d8fc15-eeef-4f1c-81df-e27964b7edd4)
    
  - [Wiederherstellen gelöschter e-Mail-Nachrichten in Outlook im Web](https://support.office.com/article/a8ca78ac-4721-4066-95dd-571842e9fb11)
    
  - [Wiederherstellen eines gelöschten Kontakts in Outlook](https://support.office.com/article/51c83288-6888-4dcd-8c99-4932daabf643)
    
  - [Wiederherstellen gelöschter e-Mail-Nachrichten in Outlook.com](https://go.microsoft.com/fwlink/p/?LinkID=623435)
    
[Nach oben](recover-deleted-items-in-a-mailbox.md#__top)
  

