---
title: Hinzufügen von vielen Benutzern gleichzeitig zu Office 365 - Admin-Hilfe
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365P_AddUsersCSV
- O365M_AddUsersCSV
- O365E_AddUsersCSV
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOP150
- MOE150
- MED150
- GMA150
- MBS150
- GEA150
- BCS160
ms.assetid: 1f5767ed-e717-4f24-969c-6ea9d412ca88
description: 'Informationen Sie zum Hinzufügen von mehreren Benutzern zu Office 365 für Unternehmen aus einer Liste in eine Kalkulationstabelle oder anderen CSV-Datei formatiert. Sehen Sie ein Video auf YouTube, die erklärt, wie Office 365 Konten hinzugefügt. Am Ende dieser Prozess wird jeder Benutzer mit einem Konto an ein Office 365-Postfach verfügen. '
ms.openlocfilehash: 1f91821ee552b59201ca01bdbce7edc0406929d6
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540769"
---
# <a name="add-several-users-at-the-same-time-to-office-365---admin-help"></a>Hinzufügen von vielen Benutzern gleichzeitig zu Office 365 - Admin-Hilfe

Jede Person in Ihrem Team benötigt ein Benutzerkonto an, bevor sie anmelden und Zugriff auf Office 365-Dienste, wie e-Mail- und Büro können. Wenn Sie viele Benutzer verfügen, können Sie ihre Konten aus einer Excel-Tabelle oder einer anderen Datei im CSV-Format gespeichert alle gleichzeitig hinzufügen. [Welche CSV-Format nicht sicher ist?](add-several-users-at-the-same-time.md#__toc316652088)
  
## <a name="add-multiple-users-to-office-365-in-the-office-365-admin-center"></a>Hinzufügen von mehreren Benutzern zu Office 365 in Office 365 Administrationscenter

1. Melden Sie sich mit Ihrem Geschäfts- oder Schulkonto bei Office 365 an. 
    
2. Wählen Sie im Office 365 Administrationscenter **Benutzer** \> **aktive Benutzer**.
    
    ![Wählen Sie in der Verwaltungskonsole und aktive Benutzer](media/12086d98-a8b4-4c48-89cf-b78ad8058ff1.png)
  
3. Wählen Sie in der **Weitere** Dropdown-Liste **Importieren Sie mehrere Benutzer**aus.
    
4. Klicken Sie im Bereich **mehrere Benutzer importieren** können Sie optional eine CSV-Beispieldatei mit oder ohne Beispieldaten ausgefüllt herunterladen. 
    
    ![Wählen Sie in der weitere Dropdown-Liste importieren von mehreren Benutzern](media/77df8a4a-fd00-4fbe-bf1c-d234fc1d5e93.png)
  
    Die Kalkulationstabelle muss die **genauen dieselben Spaltenüberschriften** wie das Beispiel eine enthalten (Benutzername, Vorname usw....). Wenn Sie die Vorlage verwenden, öffnen Sie es in einem Text-Bearbeitungstool wie Notepad ein, und berücksichtigen Sie alle Daten in Zeile 1 allein verlassen und nur eingeben von Daten in den Zeilen 2 und unter. 
    
    Die Kalkulationstabelle muss auch Werte für den Benutzernamen (wie bob@contoso.com) und einen Anzeigenamen für jeden Benutzer (wie Bob Kelly) enthalten. 
    
  ```
  User Name,First Name,Last Name,Display Name,Job Title,Department,Office Number,Office Phone,Mobile Phone,Fax,Address,City,State or Province,ZIP or Postal Code,Country or Region
  chris@contoso.com,Chris,Green,Chris Green,IT Manager,Information Technology,123451,123-555-1211,123-555-6641,123-555-9821,1 Microsoft way,Redmond,Wa,98052,United States
  ben@contoso.com,Ben,Andrews,Ben Andrews,IT Manager,Information Technology,123452,123-555-1212,123-555-6642,123-555-9822,1 Microsoft way,Redmond,Wa,98052,United States
  david@contoso.com,David,Longmuir,David Longmuir,IT Manager,Information Technology,123453,123-555-1213,123-555-6643,123-555-9823,1 Microsoft way,Redmond,Wa,98052,United States
  cynthia@contoso.com,Cynthia,Carey,Cynthia Carey,IT Manager,Information Technology,123454,123-555-1214,123-555-6644,123-555-9824,1 Microsoft way,Redmond,Wa,98052,United States
  melissa@contoso.com,Melissa,MacBeth,Melissa MacBeth,IT Manager,Information Technology,123455,123-555-1215,123-555-6645,123-555-9825,1 Microsoft way,Redmond,Wa,98052,United States
  
  ```

5. Geben Sie einen Pfad in das Feld ein, oder wählen Sie **Durchsuchen** , navigieren Sie zum Speicherort CSV-Datei, und wählen **Überprüfen**.
    
    ![Die CSV-Datei wird überprüft.](media/a43d49db-b2ab-4200-8ddf-0bc846ac6fe5.png)
  
    Wenn Probleme mit der Datei vorhanden sind, wird das Problem in der Systemsteuerung angezeigt. Sie können auch eine Protokolldatei herunterladen.
    
6. **Festlegen von Benutzeroptionen für** im Dialogfeld können Sie festlegen der Anmeldestatus und auswählen die-Lizenz, die allen Benutzern zugewiesen werden. 
    
7. Klicken Sie im Dialogfeld **Ansicht das Ergebnis** die Möglichkeit, sendet die Ergebnisse auf sich selbst oder andere Benutzer (Kennwörter werden im nur-Text), und Sie können sehen, wie viele Benutzer erstellt wurden, und einige der neuen Benutzer zuweisen weitere Lizenzen erwerben möchten. 
    
## <a name="watch-the-video"></a>Video ansehen
<a name="bk_preview"> </a>

 Sehen Sie sich ein kurzes Video, das Sie in Massen veranschaulicht Benutzer hinzufügen. 
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/f4e7f161-8ae6-4264-a429-9297b539a8de?autoplay=false]
  
## <a name="next-steps"></a>Nächste Schritte
<a name="bk_preview"> </a>

- Nun, diese Personen Konten haben, müssen sie [herunterladen und installieren, oder installieren Sie Office 365 oder Office 2016 auf einem PC oder Mac neu](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658). Jede Person in Ihrem Team kann Office 365 für bis zu 5 PCs oder Macs installieren. 
    
- Jede Person kann auch die [Office-apps und e-Mail auf einem mobilen Gerät einrichten](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f) auf bis zu 5 Tablets und 5-Telefone wie iPhones, iPads, und Android-Telefonen und Tablets. Auf diese Weise können sie Office-Dateien unabhängig vom Standort bearbeiten. 
    
    Ein End-to-End-Liste der Setup-Schritte finden Sie unter [Einrichten von Office 365 für Unternehmen](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) . 
    
## <a name="more-information-about-how-to-add-users-to-office-365"></a>Weitere Informationen zum Hinzufügen von Benutzern zu Office 365
<a name="bk_preview"> </a>

### <a name="not-sure-what-csv-format-is"></a>Welche CSV-Format wissen nicht ist?
<a name="__toc316652088"> </a>

Eine CSV-Datei ist eine Datei mit kommagetrennten Werten. Sie können erstellen oder Bearbeiten einer Datei wie folgt einen beliebigen Text-Editor oder short_Excel2007, wie Excel.
  
Sie können [Dieses Beispiel Kalkulationstabelle](https://www.microsoft.com/en-us/download/details.aspx?id=45485) als Ausgangspunkt herunterladen. Denken Sie daran, dass Office 365 erfordert, dass die Spaltenüberschriften in der ersten Zeile sie daher durch einen anderen Suchbegriff ersetzen nicht. 
  
Speichern Sie die Datei unter einem neuen Namen ein, und geben Sie CSV-Format.
  
![Ein Bild dafür, wie Sie eine Datei im CSV-Format in Excel speichern](media/35a86ebe-63ab-4b4d-9a92-e177de33ebae.png)
  
Wenn Sie die Datei speichern, erhalten Sie, dass einige Features in Ihrer Arbeitsmappe verloren gehen, wenn Sie die Datei im CSV-Format speichern wahrscheinlich eine Aufforderung. Dies ist zulässig. Klicken Sie auf **Ja,** um den Vorgang fortzusetzen. 
  
![Ein Bild der Aufforderung erhalten Sie möglicherweise aus Excel gefragt, ob Sie wirklich die Datei als CSV-Format speichern möchten.](media/51032a81-690c-45ef-bfc5-09ea7f790e98.png)
  
### <a name="tips-for-formatting-your-spreadsheet"></a>Tipps zum Formatieren der Kalkulationstabelle
<a name="__toc314595848"> </a>

- **Benötige ich dieselben Spaltenüberschriften wie in der Beispiel-Kalkulationstabelle?** Ja. Die Beispieltabelle enthält Spaltenüberschriften in der ersten Zeile. Diese Überschriften sind erforderlich. Erstellen Sie für jeden Benutzer, den Sie zu Office 365 hinzufügen möchten eine Zeile unter der Überschrift. Wenn Sie hinzufügen, ändern oder löschen Sie die Spaltenüberschriften, Office 365 zum Erstellen von Benutzern aus den Informationen in der Datei möglicherweise nicht. 
    
- **Was passiert, wenn ich alle Informationen für jeden Benutzer erforderliche besitzen?** Den Benutzernamen und den Anzeigenamen sind erforderlich, und kann nicht zum Hinzufügen eines neuen Benutzers ohne diese Informationen. Wenn Sie einige der anderen Informationen, wie das Fax besitzen können Sie ein Leerzeichen plus ein Komma verwenden, um anzugeben, dass das Feld leer bleiben soll. 
    
- ** Sein wie kleinen oder großen kann die Kalkulationstabelle? ** Die Kalkulationstabelle muss mindestens zwei Zeilen haben. Eine ist für die Spaltenüberschriften (die Benutzer Spalte Beschriftung) und einen für den Benutzer. Sie können nicht mehr als 251 Zeilen haben. Wenn Sie mehr als 250 Benutzern importieren möchten, können Sie mehr als eine Kalkulationstabelle erstellen. 
    
- ** Verwenden welche Sprachen kann ich? ** Wenn Sie die Kalkulationstabelle erstellt haben, können Sie Benutzer Daten Spaltenüberschriften in allen Sprachen oder Zeichen eingeben, aber Sie müssen die Reihenfolge der Etiketten, nicht ändern, wie im Beispiel dargestellt. Sie können dann Einträge in die Felder, stellen Sie mithilfe eines beliebigen Sprache oder Zeichen, und speichern Sie die Datei im Unicode- oder UTF-8-Format. 
    
- **Was passiert, wenn ich Benutzer aus verschiedenen Ländern oder Regionen hinzufügen bin?** Erstellen Sie ein separates Arbeitsblatt für jeden Bereich. Sie müssen das gleichzeitige schrittweise Benutzer Assistenten zum Hinzufügen von welche einzelnen Kalkulationstabelle, wenn Sie für einen einzelnen Standort aller Benutzer in der Datei enthalten, die Sie mit arbeiten. 
    
- **Besteht eine Begrenzung für die Anzahl der Zeichen kann ich verwenden?** In der folgenden Tabelle zeigt die Benutzer Daten Spaltenüberschriften und die maximale Zeichenlänge für jede in der Beispiel-Kalkulationstabelle. 
    
|**Benutzer Spalte Beschriftung**|**Maximale Zeichenlänge**|
|:-----|:-----|
|Benutzername (erforderlich)  <br/> |79 einschließlich das @-Zeichen (@), im Format name@domain. \<Erweiterung\>. Der Alias des Benutzers darf 30 Zeichen nicht überschreiten, und der Domänenname darf 48 Zeichen nicht überschreiten.  <br/> |
|Vorname  <br/> |64  <br/> |
|Nachname  <br/> |64  <br/> |
|Anzeigename (erforderlich)  <br/> |256  <br/> |
|Position  <br/> |64  <br/> |
|Abteilung  <br/> |64  <br/> |
|Geschäftliche Rufnummer  <br/> |128  <br/> |
|Telefon (geschäftlich)  <br/> |64  <br/> |
|Mobiltelefon  <br/> |64  <br/> |
|Fax-  <br/> |64  <br/> |
|Adresse  <br/> |1023  <br/> |
|Stadt  <br/> |128  <br/> |
|Bundesland oder Kanton  <br/> |128  <br/> |
|Postleitzahl  <br/> |40  <br/> |
|Land oder Region  <br/> |128  <br/> |
   
### <a name="still-having-problems-when-adding-users-to-office-365"></a>Probleme beim Hinzufügen von Benutzern zu Office 365?

- **Überprüfen Sie, dass die Kalkulationstabelle ordnungsgemäß formatiert ist.** Überprüfen Sie die Spaltenüberschriften, um sicherzustellen, dass sie die Überschriften in der Beispieldatei übereinstimmen. Stellen Sie sicher, dass Sie die Regeln für Zeichen Länge einhalten und, die jedes Feld wird durch ein Komma getrennt. 
    
- ** Wenn Sie sofort die neuen Benutzer in Office 365 sehen, warten Sie einige Minuten. ** Während bei Änderungen in allen Diensten in Office 365 wechseln kann es etwas dauern. 
    
## <a name="add-multiple-users-to-office-365-in-the-old-office-365-admin-center"></a>Hinzufügen von mehreren Benutzern zu Office 365 in der alten Office 365-Verwaltungskonsole

1. Herunterladen Sie [in diesem Beispiel Kalkulationstabelle](https://www.microsoft.com/en-us/download/details.aspx?id=45485) , und öffnen sie in Excel. 
    
    Die Kalkulationstabelle muss die **genauen dieselben Spaltenüberschriften** wie das Beispiel eine enthalten (Benutzername, Vorname usw....). Wenn Sie die Vorlage verwenden, können Sie alle Daten in Zeile 1 allein verlassen und nur eingeben von Daten in den Zeilen 2 und unter. 
    
    Die Kalkulationstabelle muss auch Werte für den Benutzernamen (wie bob@contoso.com) und einen Anzeigenamen für jeden Benutzer (wie Bob Kelly) enthalten. Um die anderen Felder leer lassen, geben Sie ein Leerzeichen plus ein Komma im Feld wie in der folgenden Abbildung dargestellt. 
    
    ![Ein Beispiel CVS-Datei, die leere Zeilen angegeben wurde](media/9c596ba1-1053-4687-a46c-c9359e9818c9.png)
  
    Wenn Sie Personen arbeiten in verschiedenen Ländern haben, müssen Sie eine Kalkulationstabelle für Benutzer in jedem Land erstellen. Beispielsweise eine Tabelle, aufgeführt sind alle Personen, die in den USA arbeitet und ein weiteres, die alle auflistet, die in Japan arbeitet. Dies ist, da die Verfügbarkeit von Office 365-Diensten nach Region variiert. 
    
    **Tipp:** Bevor Sie Office 365 viele Benutzer hinzugefügt haben, sollten Sie zum Üben mit dem Beispiel-Kalkulationstabelle. Bearbeiten Sie die Beispiel-Arbeitsblatt mit Daten für wenige Benutzer, sagen Sie 5 oder 10 und speichern Sie die Datei unter einem neuen Namen. In diesem Verfahren beschriebenen Schritte führen Sie aus, überprüfen Sie die Ergebnisse löschen Sie die neuen Konten, und starten Sie über erneut. Auf diese Weise können Sie üben, alle Daten rechts für Ihre Situation abgerufen. [Tipps zum Formatieren der Kalkulationstabelle](add-several-users-at-the-same-time.md#__toc314595848)wird auch auschecken.
    
2. Melden Sie sich mit Ihrem Geschäfts- oder Schulkonto bei Office 365 an. 
    
3. Navigieren Sie zum Office 365 Admin Center.
    
4. Für Benutzer Office 365-Dienste verwenden müssen sie eine Lizenz zugewiesen werden. Bevor Sie fortfahren sollten Sie überprüfen Sie, ob genügend Lizenzen für alle Benutzer in der Tabelle aufgeführt. Wählen Sie **Abrechnung** \> **Abonnements** , um festzustellen, ob Sie über genügend verfügen. Wenn Sie weitere Lizenzen erwerben möchten, wählen Sie ** Lizenz Menge ändern **. Alternativ können Sie den Assistenten ausführen und zuweisen die Lizenzen haben, und klicken Sie dann später auf mehr Lizenzen kaufen und den Assistenten erneut aus. 
    
5. Jetzt zu wechseln, um das gleichzeitige Benutzer Assistenten zum Hinzufügen von: Wählen Sie **Benutzer** \> **Aktive Benutzer**. Wählen Sie ![das Symbol für das Hinzufügen von vielen Benutzern zu Office 365](media/3481ffea-d552-4a7f-9a3b-014504e69746.png) wie in der folgenden Abbildung dargestellt. 
    
    ![Ein Bild des Abschnitts Benutzer von Office 365 Administrationscenter](media/2cd5ff86-9c0b-438e-9bb9-13b12a2675de.png)
  
    Das gleichzeitige Hinzufügen von Benutzern-Assistent wird angezeigt und führt Sie schrittweise durch eine Gruppe von Benutzern zu Office 365 hinzufügen. 
    
6. Wählen Sie in Schritt 1: aus einer CSV-Datei, geben Sie Ihre eigenen Kalkulationstabelle an, wie in der folgenden Abbildung dargestellt.
    
    ![Schritt 1 von das gleichzeitige Benutzer Wizard hinzufügen - Select CSV-Datei](media/aeb837ed-1f86-427d-b038-c643c383829c.png)
  
7. In Schritt 2: Überprüfen, teilt Ihnen der Assistent, ob der Inhalt in der Kalkulationstabelle ordnungsgemäß formatiert ist.
    
    ![Schritt 2 von das gleichzeitige Benutzer Wizard hinzufügen - Überprüfung](media/3fd3cd2c-44d4-4593-b02c-b87c176affb3.png)
  
8. Wählen Sie in Schritt 3 - Einstellungen, **zulässig** , so dass Personen aufgeführt, die in der Kalkulationstabelle Office 365 verwenden können. Wählen Sie auch das Land, in dem diese Personen Office 365 verwendet werden. Denken Sie daran, wenn einige Personen in Ihrer Organisation zu Office 365 in einem anderen Land verwenden, erstellen Sie ein separates Arbeitsblatt mit ihren Namen und das gleichzeitige Ausführen Hinzufügen Benutzer-Assistenten erneut aus, um sie hinzuzufügen. 
    
    ![Schritt 3 von das gleichzeitige Benutzer Wizard hinzufügen - Einstellungen](media/ff12ad34-5d8b-4e89-a02f-d827a94095b3.png)
  
9. Die Seite Lizenzen zuweisen des erfahren Sie, wie viele Lizenzen verfügbar sind. 
    
    ![Schritt 4 des Assistenten Bulk Benutzer hinzufügen - Lizenzen](media/161ea34c-c67e-43be-962f-029f5426ff1b.png)
  
    Sie können dann **auf mehr Lizenzen kaufen**, aber behalten Sie das gleichzeitige Benutzer Assistenten zum Hinzufügen von und navigieren Sie zu **Abrechnung** im Office 365 Administrationscenter. Nach mehr Lizenzen kaufen, müssen Sie warten, bis ein paar Minuten für den Auftrag verarbeitet werden, und klicken Sie dann Start das gleichzeitige Benutzer Assistenten zum Hinzufügen von vom Anfang. 
    
    Wenn Sie nicht mehr Lizenzen kaufen, werden nicht für alle Benutzer in der Tabelle aufgeführten Konten erstellt werden. 
    
    In diesem Beispiel wir noch weitere Lizenzen erwerben und fahren Sie mit der Bulk nicht Benutzer Assistent zum Hinzufügen.
    
10. Schritt 5: Senden Sie der Ergebnisse, und geben Sie die e-Mail-Adressen der Personen, die über eine e-Mail-Nachricht erhalten möchten, in der *Alle* von der Office 365-Benutzernamen und die temporären Kennwörter für Personen, die in der Kalkulationstabelle aufgelistet werden sollen. 
    
    ![Schritt 5 des das gleichzeitige Benutzer Wizard hinzufügen - Ergebnisse senden](media/5beeb825-4ba7-4ae0-bfb5-a1f8a785ebdb.png)
  
    Die folgende e-Mail wird an die e-Mail-Adressen gesendet, den Sie in Schritt 5: Senden Ergebnisse angegeben. Diese e-Mail gibt an, welche Konten erstellt wurden. Beachten Sie, dass Konten für einige Personen erstellt wurden nicht, da es waren nicht genügend Lizenzen. 
    
    ![Ein Beispiel-e-Mail mit Anmeldeinformationen von Benutzern](media/0a40c612-2078-4b5b-813e-f99bc53635a6.png)
  
    Sie können weitere Lizenzen später und erneut ausführen, die per Massenvorgang hinzufügen-Assistenten für Benutzer mit derselben Kalkulationstabelle. Der Assistent überspringt die Benutzer, die bereits für Konten; auf den Bericht der Suchergebnisse, wird es sagen Sie "doppelte Benutzername" an, dass eine Person mit diesen Informationen bereits über ein Konto verfügt.
    
11. Die letzte Seite in der Massen hinzufügen, dass Benutzer-Assistenten für den Benutzernamen und die temporären Kennwörter enthält, wie in der folgenden Abbildung dargestellt.
    
    ![Schritt 6, der das gleichzeitige Benutzer Wizard hinzufügen - Ergebnisse senden](media/0cd43832-071b-4b33-b57a-5d07959985ad.png)
  
12. Nachdem Sie Benutzer zu Office 365 hinzugefügt haben, müssen Sie sie über die Office 365-Kontoinformationen zu informieren. Verwenden Sie Ihre normalen Prozess für die Kommunikation neuer Kennwörter an.
    

