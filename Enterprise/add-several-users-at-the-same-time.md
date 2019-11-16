---
title: Gleichzeitiges Hinzufügen mehrerer Benutzer zu Office 365 - Administratorhilfe
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.date: 6/29/2018
audience: Admin
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
description: 'In diesem Artikel erfahren Sie, wie Sie Office 365 für Unternehmen aus einer Liste in einer Tabellenkalkulation oder einer anderen CSV-formatierten Datei mehrere Benutzer hinzufügen können. Sehen Sie sich ein Video auf YouTube an, in dem das Hinzufügen von Konten zu Office 365 erläutert wird. Am Ende dieses Prozesses verfügt jeder Benutzer mit einem Konto über ein Office 365 Postfach. '
ms.openlocfilehash: a719b2626eada8abe225a6951af4a2d292667856
ms.sourcegitcommit: 8027254ab4b9ed44a5b0c336f714049859f93f3d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2019
ms.locfileid: "38030729"
---
# <a name="add-several-users-at-the-same-time-to-office-365---admin-help"></a><span data-ttu-id="2b726-105">Gleichzeitiges Hinzufügen mehrerer Benutzer zu Office 365 – Administratorhilfe</span><span class="sxs-lookup"><span data-stu-id="2b726-105">Add several users at the same time to Office 365 - Admin Help</span></span>

<span data-ttu-id="2b726-p102">Jedes Mitglied in Ihrem Team benötigt ein Benutzerkonto, bevor es sich anmelden und auf Office 365-Dienste wie E-Mail und Office zugreifen kann. Wenn das Team viele Personen umfasst, können Sie deren Konten aus einer Excel-Tabelle oder einer anderen, im CSV-Format gespeicherten, Datei gleichzeitig hinzufügen. [Was ist eine CSV-Datei?](add-several-users-at-the-same-time.md#__toc316652088)</span><span class="sxs-lookup"><span data-stu-id="2b726-p102">Each person on your team needs a user account before they can sign in and access Office 365 services, such as email and Office. If you have a lot of people, you can add their accounts all at once from an Excel spreadsheet or other file saved in CSV format. [Not sure what CSV format is?](add-several-users-at-the-same-time.md#__toc316652088)</span></span>
  
## <a name="add-multiple-users-to-office-365-in-the-microsoft-365-admin-center"></a><span data-ttu-id="2b726-109">Hinzufügen von mehreren Benutzern zu Office 365 im Microsoft 365 Admin Center</span><span class="sxs-lookup"><span data-stu-id="2b726-109">Add multiple users to Office 365 in the Microsoft 365 admin center</span></span>

1. <span data-ttu-id="2b726-110">Melden Sie sich mit Ihrem Geschäfts- oder Schulkonto bei Office 365 an.</span><span class="sxs-lookup"><span data-stu-id="2b726-110">Sign in to Office 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="2b726-111">Wählen Sie im Admin Center **Benutzer** \> **Aktive Benutzer** aus.</span><span class="sxs-lookup"><span data-stu-id="2b726-111">In the admin center, choose **Users** \> **Active users**.</span></span>
    
    ![Wählen Sie im Admin Center Benutzer und dann aktive Benutzer aus.](media/12086d98-a8b4-4c48-89cf-b78ad8058ff1.png)
  
    
3. <span data-ttu-id="2b726-113">Im Bereich **Mehrere Benutzer importieren** können Sie eine CSV-Beispieldatei mit oder ohne eingetragene Beispieldaten optional herunterladen.</span><span class="sxs-lookup"><span data-stu-id="2b726-113">On the **Import multiple users** panel, you can optionally download a sample CSV file with or without sample data filled in.</span></span> 
    
    ![In the More drop-down, choose Import multiple users](media/77df8a4a-fd00-4fbe-bf1c-d234fc1d5e93.png)
  
    <span data-ttu-id="2b726-115">Ihre Tabelle muss **dieselben Spaltenüberschriften** wie die Beispieltabelle enthalten ("Benutzername", "Vorname" usw.). Wenn Sie die Vorlage verwenden, öffnen Sie sie in einem Textbearbeitungstool, z. B. Editor. Sie sollten nach Möglichkeit alle Daten in Zeile 1 beibehalten und Daten nur in Zeile 2 und die Zeilen darunter eingeben.</span><span class="sxs-lookup"><span data-stu-id="2b726-115">Your spreadsheet needs to include the **exact same column headings** as the sample one (User Name, First Name, etc...). If you use the template, open it in a text editing tool, like Notepad, and consider leaving all the data in row 1 alone, and only entering data in rows 2 and below.</span></span> 
    
    <span data-ttu-id="2b726-116">Darüber hinaus muss Ihre Tabelle für jeden Benutzer Werte für den Benutzernamen (wie "berend@contoso.com") und einen Anzeigenamen (wie "Berend Klein") enthalten.</span><span class="sxs-lookup"><span data-stu-id="2b726-116">Your spreadsheet also needs to include values for the user name (like bob@contoso.com) and a display name (like Bob Kelly) for each user.</span></span> 
    
  ```
  User Name,First Name,Last Name,Display Name,Job Title,Department,Office Number,Office Phone,Mobile Phone,Fax,Address,City,State or Province,ZIP or Postal Code,Country or Region
  chris@contoso.com,Chris,Green,Chris Green,IT Manager,Information Technology,123451,123-555-1211,123-555-6641,123-555-9821,1 Microsoft way,Redmond,Wa,98052,United States
  ben@contoso.com,Ben,Andrews,Ben Andrews,IT Manager,Information Technology,123452,123-555-1212,123-555-6642,123-555-9822,1 Microsoft way,Redmond,Wa,98052,United States
  david@contoso.com,David,Longmuir,David Longmuir,IT Manager,Information Technology,123453,123-555-1213,123-555-6643,123-555-9823,1 Microsoft way,Redmond,Wa,98052,United States
  cynthia@contoso.com,Cynthia,Carey,Cynthia Carey,IT Manager,Information Technology,123454,123-555-1214,123-555-6644,123-555-9824,1 Microsoft way,Redmond,Wa,98052,United States
  melissa@contoso.com,Melissa,MacBeth,Melissa MacBeth,IT Manager,Information Technology,123455,123-555-1215,123-555-6645,123-555-9825,1 Microsoft way,Redmond,Wa,98052,United States
  
  ```

4. <span data-ttu-id="2b726-117">Geben Sie in dem Feld einen Dateipfad ein, oder wählen Sie **Durchsuchen** aus, um zum Speicherort der CSV-Datei zu navigieren. Wählen Sie dann **Überprüfen** aus.</span><span class="sxs-lookup"><span data-stu-id="2b726-117">Enter a file path into the box, or choose **Browse** to browse to the CSV file location, then choose **Verify**.</span></span>
    
    ![Your CSV file is verified](media/a43d49db-b2ab-4200-8ddf-0bc846ac6fe5.png)
  
    <span data-ttu-id="2b726-p103">Wenn es Probleme mit der Datei gibt, wird eine entsprechende Meldung angezeigt. Sie können auch eine Protokolldatei herunterladen.</span><span class="sxs-lookup"><span data-stu-id="2b726-p103">If there are problems with the file, the problem is displayed in the panel. You can also download a log file.</span></span>
    
5. <span data-ttu-id="2b726-121">Im Dialogfeld **Benutzeroptionen festlegen** können Sie den Anmeldestatus festlegen und die Produktlizenz auswählen, die allen Benutzern zugewiesen werden soll.</span><span class="sxs-lookup"><span data-stu-id="2b726-121">On the **Set user options** dialog you can set the sign-in status and choose the product license that will be assigned to all users.</span></span> 
    
6. <span data-ttu-id="2b726-122">Im Dialogfeld **Ergebnisse anzeigen** können Sie auswählen, ob die Ergebnisse an Sie selbst oder an andere Benutzer (Kennwörter im Nur-Text-Format) gesendet werden sollen. Außerdem können Sie sehen, wie viele Benutzer erstellt wurden und ob Sie weitere Lizenzen erwerben müssen, um sie einigen der neuen Benutzer zuzuweisen.</span><span class="sxs-lookup"><span data-stu-id="2b726-122">On the **View your result** dialog you can choose to send the results to either yourself or other users (passwords will be in plain text) and you can see how many users were created, and if you need to purchase more licenses to assign to some of the new users.</span></span> 
    
## <a name="watch-the-video"></a><span data-ttu-id="2b726-123">Video ansehen</span><span class="sxs-lookup"><span data-stu-id="2b726-123">Watch the video</span></span>
<span data-ttu-id="2b726-124"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="2b726-124"></span></span>

 <span data-ttu-id="2b726-125">Schauen Sie sich ein kurzes Video an, in dem gezeigt wird, wie eine Massenhinzufügung von Benutzern erfolgt.</span><span class="sxs-lookup"><span data-stu-id="2b726-125">Watch a short video that shows you how to bulk add users.</span></span> 
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/f4e7f161-8ae6-4264-a429-9297b539a8de?autoplay=false]
  
## <a name="next-steps"></a><span data-ttu-id="2b726-126">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="2b726-126">Next steps</span></span>
<span data-ttu-id="2b726-127"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="2b726-127"></span></span>

- <span data-ttu-id="2b726-128">Da diese Personen nun über Konten verfügen, müssen Sie [Office 365 oder Office 2016 auf einem PC oder Mac herunterladen und installieren oder neu installieren](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658).</span><span class="sxs-lookup"><span data-stu-id="2b726-128">Now that these people have accounts, they need to [Download and install or reinstall Office 365 or Office 2016 on a PC or Mac](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658).</span></span> <span data-ttu-id="2b726-129">Jede Person in Ihrem Team kann Office 365 auf bis zu fünf PCs oder Macs installieren.</span><span class="sxs-lookup"><span data-stu-id="2b726-129">Each person on your team can install Office 365 on up to 5 PCs or Macs.</span></span> 
    
- <span data-ttu-id="2b726-130">Jede Person kann auch [Office-Apps und e-Mail auf einem mobilen Gerät](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f) auf bis zu 5 Tablets und 5 Telefonen wie iPhones, iPads und Android-Telefone und-Tablets einrichten.</span><span class="sxs-lookup"><span data-stu-id="2b726-130">Each person can also [Set up Office apps and email on a mobile device](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f) on up to 5 tablets and 5 phones, such as iPhones, iPads, and Android phones and tablets.</span></span> <span data-ttu-id="2b726-131">Hiermit können Office-Dateien von praktisch überall aus bearbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="2b726-131">This way they can edit Office files from anywhere.</span></span> 
    
    <span data-ttu-id="2b726-132">Weitere Informationen finden Sie unter [Set up Office 365 für Unternehmen](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) for a End-to-End List of the Setup Steps.</span><span class="sxs-lookup"><span data-stu-id="2b726-132">See [Set up Office 365 for business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) for an end-to-end list of the setup steps.</span></span> 
    
## <a name="more-information-about-how-to-add-users-to-office-365"></a><span data-ttu-id="2b726-133">Weitere Informationen dazu, wie Sie Benutzer zu Office 365 hinzufügen</span><span class="sxs-lookup"><span data-stu-id="2b726-133">More information about how to add users to Office 365</span></span>
<span data-ttu-id="2b726-134"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="2b726-134"></span></span>

### <a name="not-sure-what-csv-format-is"></a><span data-ttu-id="2b726-135">Was ist eine CSV-Datei?</span><span class="sxs-lookup"><span data-stu-id="2b726-135">Not sure what CSV format is?</span></span>
<span data-ttu-id="2b726-136"><a name="__toc316652088"> </a></span><span class="sxs-lookup"><span data-stu-id="2b726-136"></span></span>

<span data-ttu-id="2b726-p106">Eine CSV-Datei ist eine Datei mit durch Kommas getrennten Werten. Sie können eine Datei wie diese mit einem beliebigen Text-Editor oder Tabellenkalkulationsprogramm wie beispielsweise Excel erstellen oder bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="2b726-p106">A CSV file is a file with comma separated values. You can create or edit a file like this with any text editor or spreadsheet program, such as Excel.</span></span>
  
<span data-ttu-id="2b726-p107">Sie können [diese Beispieltabelle](https://www.microsoft.com/download/details.aspx?id=45485) als Ausgangspunkt herunterladen. Denken Sie daran, dass bei Office 365 in der ersten Zeile Spaltenüberschriften stehen müssen. Ersetzen Sie die Überschriften deshalb nicht durch ein anderes Element.</span><span class="sxs-lookup"><span data-stu-id="2b726-p107">You can download [this sample spreadsheet](https://www.microsoft.com/download/details.aspx?id=45485) as a starting point. Remember that Office 365 requires column headings in the first row so don't replace them with something else.</span></span> 
  
<span data-ttu-id="2b726-141">Speichern Sie die Datei unter einem neuen Namen, und geben Sie das Format "CSV" an.</span><span class="sxs-lookup"><span data-stu-id="2b726-141">Save the file with a new name, and specify CSV format.</span></span>
  
![Ein Bild, das zeigt, wie eine Datei in Excel im CSV-Format gespeichert wird](media/35a86ebe-63ab-4b4d-9a92-e177de33ebae.png)
  
<span data-ttu-id="2b726-p108">Beim Speichern der Datei werden Sie wahrscheinlich darüber informiert, dass einige Features in Ihrer Arbeitsmappe verloren gehen, wenn Sie die Datei im CSV-Format speichern. Dies geht in Ordnung. Klicken Sie auf **Ja**, um den Vorgang fortzusetzen.</span><span class="sxs-lookup"><span data-stu-id="2b726-p108">When you save the file, you'll probably get a prompt that some features in your workbook will be lost if you save the file in CSV format. This is okay. Click **Yes** to continue.</span></span> 
  
![Eine Abbildung der Eingabeaufforderung, die in Excel möglicherweise angezeigt wird und fragt, ob Sie die Datei tatsächlich im CSV-Format speichern möchten](media/51032a81-690c-45ef-bfc5-09ea7f790e98.png)
  
### <a name="tips-for-formatting-your-spreadsheet"></a><span data-ttu-id="2b726-147">Tipps zum Formatieren Ihrer Tabelle</span><span class="sxs-lookup"><span data-stu-id="2b726-147">Tips for formatting your spreadsheet</span></span>
<span data-ttu-id="2b726-148"><a name="__toc314595848"> </a></span><span class="sxs-lookup"><span data-stu-id="2b726-148"></span></span>

- <span data-ttu-id="2b726-p109">**Benötige ich dieselben Spaltenüberschriften wie in der Beispieltabelle?** Ja. Die erste Zeile der Beispieltabelle enthält die Spaltenüberschriften. Diese Überschriften sind erforderlich. Erstellen Sie für jeden Benutzer, den Sie Office 365 hinzufügen möchten, eine Zeile unter der Überschrift. Wenn Sie eine der Spaltenüberschriften hinzufügen, ändern oder löschen, kann Office 365 Benutzer anhand der Informationen in der Datei möglicherweise nicht erstellen.</span><span class="sxs-lookup"><span data-stu-id="2b726-p109">**Do I need the same column headings as in the sample spreadsheet?** Yes. The sample spreadsheet contains column headings in the first row. These headings are required. For each user you want to add to Office 365, create a row under the heading. If you add, change, or delete any of the column headings, Office 365 might not be able to create users from the information in the file.</span></span> 
    
- <span data-ttu-id="2b726-p110">**Was kann ich tun, wenn ich nicht über alle Informationen verfüge, die bei jedem Benutzer erforderlich sind?** Der Benutzername und der Anzeigename sind unbedingt erforderlich; Sie können keinen neuen Benutzer ohne diese Angaben hinzufügen. Falls Ihnen einige der anderen Informationen fehlen, wie beispielsweise das Fax, können Sie ein Leerzeichen plus das von Ihnen verwendete Trennzeichen eingeben und so festlegen, dass das Feld leer bleiben soll.</span><span class="sxs-lookup"><span data-stu-id="2b726-p110">**What if I don't have all the information required for each user?** The user name and display name are required, and you cannot add a new user without this information. If you don't have some of the other information, such as the fax, you can use a space plus a comma to indicate that the field should remain blank.</span></span> 
    
- <span data-ttu-id="2b726-p111">\*\* How small or large can the spreadsheet be? \*\* The spreadsheet must have at least two rows. One is for the column headings (the user data column label) and one for the user. You cannot have more than 251 rows. If you need to import more than 250 users, you can create more than one spreadsheet.</span><span class="sxs-lookup"><span data-stu-id="2b726-p111">\*\* How small or large can the spreadsheet be? \*\* The spreadsheet must have at least two rows. One is for the column headings (the user data column label) and one for the user. You cannot have more than 251 rows. If you need to import more than 250 users, you can create more than one spreadsheet.</span></span> 
    
- <span data-ttu-id="2b726-p112">\*\* What languages can I use? \*\* When you create your spreadsheet, you can enter user data column labels in any language or characters, but you must not change the order of the labels, as shown in the sample. You can then make entries into the fields, using any language or characters, and save your file in a Unicode or UTF-8 format.</span><span class="sxs-lookup"><span data-stu-id="2b726-p112">\*\* What languages can I use? \*\* When you create your spreadsheet, you can enter user data column labels in any language or characters, but you must not change the order of the labels, as shown in the sample. You can then make entries into the fields, using any language or characters, and save your file in a Unicode or UTF-8 format.</span></span> 
    
- <span data-ttu-id="2b726-p113">**Was geschieht, wenn ich Benutzer aus verschiedenen Ländern oder Regionen hinzufüge?** Erstellen Sie eine separate Tabelle für jeden Bereich. Sie müssen den Assistenten "Massenhinzufügung von Benutzern" mit jeder Tabelle schrittweise durchlaufen. Geben Sie dabei einen einzigen Standort für alle Benutzer an, die in der Datei, mit der Sie arbeiten, enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="2b726-p113">**What if I'm adding users from different countries or regions?** Create a separate spreadsheet for each area. You'll need to step through the Bulk add users wizard which each spreadsheet, giving a single location of all users included in the file that you're working with.</span></span> 
    
- <span data-ttu-id="2b726-p114">**Bestehen Beschränkungen bei der Anzahl der Zeichen, die ich verwenden kann?** Die folgende Tabelle zeigt die Beschriftungen für Benutzerdatenspalten sowie die maximale Zeichenanzahl für jedes Element der Beispieltabelle.</span><span class="sxs-lookup"><span data-stu-id="2b726-p114">**Is there a limit to the number of characters I can use?** The following table shows the user data column labels and the maximum character length for each in the sample spreadsheet.</span></span> 
    
|<span data-ttu-id="2b726-171">**Beschriftung für Benutzerdatenspalte**</span><span class="sxs-lookup"><span data-stu-id="2b726-171">**User data column label**</span></span>|<span data-ttu-id="2b726-172">**Maximale Zeichenanzahl**</span><span class="sxs-lookup"><span data-stu-id="2b726-172">**Maximum character length**</span></span>|
|:-----|:-----|
|<span data-ttu-id="2b726-173">Benutzername (erforderlich)</span><span class="sxs-lookup"><span data-stu-id="2b726-173">User Name (Required)</span></span>  <br/> |<span data-ttu-id="2b726-p115">79, einschließlich des at-Zeichens (@), im Format "Name@Domäne.\<#60;Erweiterung\>". Der Aliasname darf maximal 30 Zeichen umfassen und der Domänenname maximal 48 Zeichen.</span><span class="sxs-lookup"><span data-stu-id="2b726-p115">79 including the at sign (@), in the format name@domain.\<extension\>. The user's alias cannot exceed 30 characters, and the domain name cannot exceed 48 characters.</span></span>  <br/> |
|<span data-ttu-id="2b726-176">Vorname</span><span class="sxs-lookup"><span data-stu-id="2b726-176">First Name</span></span>  <br/> |<span data-ttu-id="2b726-177">64</span><span class="sxs-lookup"><span data-stu-id="2b726-177">64</span></span>  <br/> |
|<span data-ttu-id="2b726-178">Nachname</span><span class="sxs-lookup"><span data-stu-id="2b726-178">Last Name</span></span>  <br/> |<span data-ttu-id="2b726-179">64</span><span class="sxs-lookup"><span data-stu-id="2b726-179">64</span></span>  <br/> |
|<span data-ttu-id="2b726-180">Anzeigename (erforderlich)</span><span class="sxs-lookup"><span data-stu-id="2b726-180">Display Name (required)</span></span>  <br/> |<span data-ttu-id="2b726-181">256</span><span class="sxs-lookup"><span data-stu-id="2b726-181">256</span></span>  <br/> |
|<span data-ttu-id="2b726-182">Position</span><span class="sxs-lookup"><span data-stu-id="2b726-182">Job Title</span></span>  <br/> |<span data-ttu-id="2b726-183">64</span><span class="sxs-lookup"><span data-stu-id="2b726-183">64</span></span>  <br/> |
|<span data-ttu-id="2b726-184">Abteilung</span><span class="sxs-lookup"><span data-stu-id="2b726-184">Department</span></span>  <br/> |<span data-ttu-id="2b726-185">64</span><span class="sxs-lookup"><span data-stu-id="2b726-185">64</span></span>  <br/> |
|<span data-ttu-id="2b726-186">Büronummer</span><span class="sxs-lookup"><span data-stu-id="2b726-186">Office Number</span></span>  <br/> |<span data-ttu-id="2b726-187">128</span><span class="sxs-lookup"><span data-stu-id="2b726-187">128</span></span>  <br/> |
|<span data-ttu-id="2b726-188">Rufnummer</span><span class="sxs-lookup"><span data-stu-id="2b726-188">Office Phone</span></span>  <br/> |<span data-ttu-id="2b726-189">64</span><span class="sxs-lookup"><span data-stu-id="2b726-189">64</span></span>  <br/> |
|<span data-ttu-id="2b726-190">Mobiltelefon</span><span class="sxs-lookup"><span data-stu-id="2b726-190">Mobile Phone</span></span>  <br/> |<span data-ttu-id="2b726-191">64</span><span class="sxs-lookup"><span data-stu-id="2b726-191">64</span></span>  <br/> |
|<span data-ttu-id="2b726-192">Fax</span><span class="sxs-lookup"><span data-stu-id="2b726-192">Fax</span></span>  <br/> |<span data-ttu-id="2b726-193">64</span><span class="sxs-lookup"><span data-stu-id="2b726-193">64</span></span>  <br/> |
|<span data-ttu-id="2b726-194">Adresse</span><span class="sxs-lookup"><span data-stu-id="2b726-194">Address</span></span>  <br/> |<span data-ttu-id="2b726-195">1023</span><span class="sxs-lookup"><span data-stu-id="2b726-195">1023</span></span>  <br/> |
|<span data-ttu-id="2b726-196">Ort</span><span class="sxs-lookup"><span data-stu-id="2b726-196">City</span></span>  <br/> |<span data-ttu-id="2b726-197">128</span><span class="sxs-lookup"><span data-stu-id="2b726-197">128</span></span>  <br/> |
|<span data-ttu-id="2b726-198">Bundesland oder Kanton</span><span class="sxs-lookup"><span data-stu-id="2b726-198">State or Province</span></span>  <br/> |<span data-ttu-id="2b726-199">128</span><span class="sxs-lookup"><span data-stu-id="2b726-199">128</span></span>  <br/> |
|<span data-ttu-id="2b726-200">PLZ</span><span class="sxs-lookup"><span data-stu-id="2b726-200">ZIP or Postal Code</span></span>  <br/> |<span data-ttu-id="2b726-201">40</span><span class="sxs-lookup"><span data-stu-id="2b726-201">40</span></span>  <br/> |
|<span data-ttu-id="2b726-202">Land oder Region</span><span class="sxs-lookup"><span data-stu-id="2b726-202">Country or Region</span></span>  <br/> |<span data-ttu-id="2b726-203">128</span><span class="sxs-lookup"><span data-stu-id="2b726-203">128</span></span>  <br/> |
   
### <a name="still-having-problems-when-adding-users-to-office-365"></a><span data-ttu-id="2b726-204">Gibt es weiterhin Probleme beim Hinzufügen von Benutzern zu Office 365?</span><span class="sxs-lookup"><span data-stu-id="2b726-204">Still having problems when adding users to Office 365?</span></span>

- <span data-ttu-id="2b726-p116">**Überprüfen Sie sorgfältig, ob die Tabelle richtig formatiert wurde.** Überprüfen Sie, ob die Spaltenüberschriften mit den Überschriften in der Beispieldatei übereinstimmen. Vergewissern Sie sich, dass Sie die Regeln für die maximale Zeichenanzahl eingehalten haben und dass jedes Feld durch ein Trennzeichen getrennt ist.</span><span class="sxs-lookup"><span data-stu-id="2b726-p116">**Double-check that the spreadsheet is formatted correctly.** Check the column headings to make sure they match the headings in the sample file. Make sure you're following the rules for character lengths and that each field is separated by a comma.</span></span> 
    
- <span data-ttu-id="2b726-p117">\*\* If you don't see the new users in Office 365 right away, wait a few minutes. \*\* It can take a little while for changes to go across all the services in Office 365.</span><span class="sxs-lookup"><span data-stu-id="2b726-p117">\*\* If you don't see the new users in Office 365 right away, wait a few minutes. \*\* It can take a little while for changes to go across all the services in Office 365.</span></span> 
    
## <a name="add-multiple-users-to-office-365-in-the-old-admin-center"></a><span data-ttu-id="2b726-210">Hinzufügen mehrerer Benutzer zu Office 365 im alten Admin Center</span><span class="sxs-lookup"><span data-stu-id="2b726-210">Add multiple users to Office 365 in the old admin center</span></span>

1. <span data-ttu-id="2b726-211">Laden Sie [diese Beispieltabelle](https://www.microsoft.com/download/details.aspx?id=45485) herunter, und öffnen Sie sie in Excel.</span><span class="sxs-lookup"><span data-stu-id="2b726-211">Download [this sample spreadsheet](https://www.microsoft.com/download/details.aspx?id=45485) and open it in Excel.</span></span> 
    
    <span data-ttu-id="2b726-212">Ihre Tabelle muss **dieselben Spaltenüberschriften** wie die Beispieltabelle enthalten ("Benutzername", "Vorname" usw.). Wenn Sie die Vorlage verwenden, sollten Sie nach Möglichkeit alle Daten in Zeile 1 beibehalten und Daten nur in Zeile 2 und die Zeilen darunter eingeben.</span><span class="sxs-lookup"><span data-stu-id="2b726-212">Your spreadsheet needs to include the **exact same column headings** as the sample one (User Name, First Name, etc...). If you use the template, consider leaving all the data in row 1 alone, and only entering data in rows 2 and below.</span></span> 
    
    <span data-ttu-id="2b726-p118">Darüber hinaus muss Ihre Tabelle für jeden Benutzer Werte für den Benutzernamen (wie "berend@contoso.com") und einen Anzeigenamen (wie "Berend Klein") enthalten. Wenn andere Felder leer bleiben sollen, geben Sie im jeweiligen Feld ein Leerzeichen plus ein Trennzeichen ein, wie in der nachstehenden Abbildung gezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="2b726-p118">Your spreadsheet also needs to include values for the user name (like bob@contoso.com) and a display name (like Bob Kelly) for each user. To leave other fields blank, enter a space plus a comma in the field as shown in the following figure.</span></span> 
    
    ![Eine CSV-Beispieldatei mit angegebenen Leerzeilen](media/9c596ba1-1053-4687-a46c-c9359e9818c9.png)
  
    <span data-ttu-id="2b726-p119">Wenn Teammitglieder in verschiedenen Ländern arbeiten, müssen Sie für die Benutzer in jedem Land eine eigene Tabelle erstellen, beispielsweise eine Tabelle, in der jedes Teammitglied aufgelistet ist, das in den USA arbeitet, und eine andere Tabelle, in der jedes in Japan arbeitende Teammitglied aufgelistet ist. Der Grund für die verschiedenen Tabellen: Die Verfügbarkeit von Office 365 variiert von Region zu Region.</span><span class="sxs-lookup"><span data-stu-id="2b726-p119">If you have people working in different countries, you'll need to create one spreadsheet for users in each country. For example, one spreadsheet that lists everyone who works in the US, and another that lists everyone who works in Japan. This is because the availability of Office 365 services varies by region.</span></span> 
    
    <span data-ttu-id="2b726-p120">**Tipp:** Bevor Sie Office 365 viele Benutzer hinzufügen, ist es möglicherweise sinnvoll, diesen Vorgang mithilfe der Beispieltabelle zu üben. Bearbeiten Sie die Beispieltabelle mit Daten für nur ein paar Benutzer (z. B. 5 oder 10), und speichern Sie die Datei unter einem neuen Namen. Führen Sie die in diesem Verfahren beschriebenen Schritte aus, überprüfen Sie die Ergebnisse, löschen Sie dann die neuen Konten, und beginnen Sie erneut. Auf diese Weise können Sie üben, wie Sie sämtliche Daten für die jeweilige Situation bereitstellen. Sehen Sie sich auch die [Tipps zum Formatieren Ihrer Tabelle](add-several-users-at-the-same-time.md#__toc314595848) an.</span><span class="sxs-lookup"><span data-stu-id="2b726-p120">**Tip:** Before you add many users to Office 365, you might want to practice with the sample spreadsheet. For example, edit the sample spreadsheet with data for a few of your users, say 5 or 10, and save the file with a new name. Run through steps described in this procedure, check the results, and then delete the new accounts and start over again. This way you can practice getting all of the data right for your situation. Also check out [Tips for formatting your spreadsheet](add-several-users-at-the-same-time.md#__toc314595848).</span></span>
    
2. <span data-ttu-id="2b726-224">Melden Sie sich mit Ihrem Geschäfts- oder Schulkonto bei Office 365 an.</span><span class="sxs-lookup"><span data-stu-id="2b726-224">Sign in to Office 365 with your work or school account.</span></span> 
    
3. <span data-ttu-id="2b726-225">Wechseln Sie zum Admin Center.</span><span class="sxs-lookup"><span data-stu-id="2b726-225">Go to the admin center.</span></span>
    
4. <span data-ttu-id="2b726-p121">For people to use Office 365 services, they need to be assigned a license. Before continuing, you might want to check that you have enough licenses for everyone listed in your spreadsheet. Choose **Billing** \> **Subscriptions** to see if you have enough. If you need to buy more licenses, choose \*\* Change license quantity \*\*. Or, you can run the wizard and assign the licenses you have, then buy more licenses later and rerun the wizard.</span><span class="sxs-lookup"><span data-stu-id="2b726-p121">For people to use Office 365 services, they need to be assigned a license. Before continuing, you might want to check that you have enough licenses for everyone listed in your spreadsheet. Choose **Billing** \> **Subscriptions** to see if you have enough. If you need to buy more licenses, choose \*\* Change license quantity \*\*. Or, you can run the wizard and assign the licenses you have, then buy more licenses later and rerun the wizard.</span></span> 
    
5. <span data-ttu-id="2b726-p122">Wechseln Sie nun zum Assistenten "Massenhinzufügung von Benutzern": Wählen Sie **Benutzer** \> **Aktive Benutzer** aus. Wählen Sie ![Das Symbol zum Massenhinzufügen von Benutzern in Office 365](media/3481ffea-d552-4a7f-9a3b-014504e69746.png), wie in der nachstehenden Abbildung gezeigt.</span><span class="sxs-lookup"><span data-stu-id="2b726-p122">Now go to the Bulk add users wizard: choose **Users** \> **Active Users**. Choose ![The icon for adding many users to Office 365](media/3481ffea-d552-4a7f-9a3b-014504e69746.png) as shown in the following figure.</span></span> 
    
    ![Ein Bild des Abschnitts "Benutzer" des Admin Centers](media/2cd5ff86-9c0b-438e-9bb9-13b12a2675de.png)
  
    <span data-ttu-id="2b726-234">Der Assistent "Massenhinzufügung von Benutzern" wird angezeigt und führt Sie schrittweise durch den Vorgang zum Hinzufügen einer Benutzergruppe zu Office 365.</span><span class="sxs-lookup"><span data-stu-id="2b726-234">The Bulk add users wizard appears and steps you through adding a group of users to Office 365.</span></span> 
    
6. <span data-ttu-id="2b726-235">Geben Sie in Schritt 1 - "CSV-Datei auswählen" - Ihre eigene Tabelle an, wie in der nachstehenden Abbildung gezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="2b726-235">In Step 1 - Select a CSV file, specify your own spreadsheet as shown in the following figure.</span></span>
    
    ![Schritt 1 des Assistenten zur Massenhinzufügung von Benutzern - CSV-Datei auswählen](media/aeb837ed-1f86-427d-b038-c643c383829c.png)
  
7. <span data-ttu-id="2b726-237">In Schritt 2 - "Überprüfung" - informiert Sie der Assistent, ob der Inhalt der Tabelle ordnungsgemäß formatiert wurde.</span><span class="sxs-lookup"><span data-stu-id="2b726-237">In Step 2 - Verification, the wizard tells you whether the content in the spreadsheet is formatted correctly.</span></span>
    
    ![Schritt 2 des Assistenten zur Massenhinzufügung von Benutzern - Überprüfung](media/3fd3cd2c-44d4-4593-b02c-b87c176affb3.png)
  
8. <span data-ttu-id="2b726-p123">Wählen Sie in Schritt 3 - "Einstellungen" - die Option **Zulässig** aus, damit die in Ihrer Tabelle aufgelisteten Personen Office 365 nutzen können. Wählen Sie außerdem das Land aus, in dem diese Personen Office 365 nutzen werden. Denken Sie daran: Wenn einige Personen in Ihrer Organisation Office 365 in einem anderen Land nutzen werden, erstellen Sie eine separate Tabelle mit deren Namen, und führen Sie den Assistenten "Massenhinzufügung von Benutzern" erneut aus, um diese Personen hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="2b726-p123">In Step 3 - Settings, choose **Allowed** so that the people listed in your spreadsheet will be able to use Office 365. Also choose the country in which these people will use Office 365. Remember if some people in your organization are going to use Office 365 in a different country, create a separate spreadsheet with their names and run the Bulk add users wizard again to add them.</span></span> 
    
    ![Schritt 3 des Assistenten zur Massenhinzufügung von Benutzern - Einstellungen](media/ff12ad34-5d8b-4e89-a02f-d827a94095b3.png)
  
9. <span data-ttu-id="2b726-243">Auf der Seite "Lizenzen zuweisen" wird angezeigt, wie viele Lizenzen verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="2b726-243">The assign licenses page tells you how many licenses are available.</span></span> 
    
    ![Schritt 4 des Assistenten zur Massenhinzufügung von Benutzern - Lizenzen](media/161ea34c-c67e-43be-962f-029f5426ff1b.png)
  
    <span data-ttu-id="2b726-245">Sie können die Option **Buy More licenses**wählen, aber Sie verlassen den Assistenten für Massen Benutzer hinzufügen und wechseln zur **Abrechnung** im Microsoft 365 Admin Center.</span><span class="sxs-lookup"><span data-stu-id="2b726-245">You can choose **Buy more licenses**, but you'll leave the Bulk add users wizard and go to **Billing** in the Microsoft 365 admin center.</span></span> <span data-ttu-id="2b726-246">Nachdem Sie weitere Lizenzen erworben haben, müssen Sie einige Minuten warten, bis die Reihenfolge verarbeitet wurde, und dann den Assistenten für Massen Benutzer hinzufügen von Anfang an starten.</span><span class="sxs-lookup"><span data-stu-id="2b726-246">After buying more licenses, you'll have to wait a few minutes for the order to be processed and then start the Bulk add users wizard from the beginning.</span></span> 
    
    <span data-ttu-id="2b726-247">Wenn Sie keine weiteren Lizenzen erwerben, wird nicht für jede in Ihrer Tabelle aufgelistete Person ein Konto erstellt.</span><span class="sxs-lookup"><span data-stu-id="2b726-247">If you don't buy more licenses, accounts won't be created for everyone listed in your spreadsheet.</span></span> 
    
    <span data-ttu-id="2b726-248">In diesem Beispiel erwerben wir keine weiteren Lizenzen und setzen den Vorgang mit dem Assistenten "Massenhinzufügung von Benutzern" fort.</span><span class="sxs-lookup"><span data-stu-id="2b726-248">In this example, we don't buy any more licenses and continue with the Bulk add users wizard.</span></span>
    
10. <span data-ttu-id="2b726-249">Geben Sie in Schritt 5 - "Ergebnisse senden" - die E-Mail-Adressen der Personen ein, die eine E-Mail-Nachricht erhalten sollen, in der  *alle*  Office 365-Benutzernamen und temporären Kennwörter für die Personen in der Tabelle aufgelistet sind.</span><span class="sxs-lookup"><span data-stu-id="2b726-249">In Step 5 - Send Results, type the email addresses of the people who you want to get an email that lists  *all*  of the Office 365 user names and temporary passwords for the people in the spreadsheet.</span></span> 
    
    ![Schritt 5 des Assistenten zur Massenhinzufügung von Benutzern - Ergebnisse senden](media/5beeb825-4ba7-4ae0-bfb5-a1f8a785ebdb.png)
  
    <span data-ttu-id="2b726-p125">Die folgende E-Mail-Nachricht wird an alle E-Mail-Adressen gesendet, die Sie in Schritt 5 - "Ergebnisse senden" - angegeben haben. Diese E-Mail teilt mit, welche Konten erstellt wurden. Beachten Sie, dass für einige Personen kein Konto erstellt wurde, weil es nicht genügend Lizenzen gab.</span><span class="sxs-lookup"><span data-stu-id="2b726-p125">The following email is sent to all the email addresses you specified in Step 5 - Send results. This email indicates which accounts were created. Notice that accounts weren't created for some people because there weren't enough licenses.</span></span> 
    
    ![Eine Beispiel-E-Mail mit Informationen zu den Benutzeranmeldeinformationen](media/0a40c612-2078-4b5b-813e-f99bc53635a6.png)
  
    <span data-ttu-id="2b726-p126">Sie können zu einem späteren Zeitpunkt weitere Lizenzen erwerben und dann den Assistenten "Massenhinzufügung von Benutzern" mit derselben Tabelle erneut ausführen. Der Assistent überspringt die Benutzer, die bereits Konten besitzen; im Bericht mit den Ergebnissen steht "Doppelt vorhandener Benutzername". Es bedeutet, dass eine Person mit diesen Informationen bereits ein Konto besitzt.</span><span class="sxs-lookup"><span data-stu-id="2b726-p126">You can buy more licenses later and rerun the Bulk add users wizard with the same spreadsheet. The wizard skips over the users that already have accounts; on the results report, it will say "duplicate user name" to indicate someone with that information already has an account.</span></span>
    
11. <span data-ttu-id="2b726-257">Auf der letzten Seite im Assistenten "Massenhinzufügung von Benutzern" werden die Benutzernamen und temporären Kennwörter aufgelistet, wie in der nachstehenden Abbildung zu sehen ist.</span><span class="sxs-lookup"><span data-stu-id="2b726-257">The final page in the Bulk add users wizard lists the user names and temporary passwords, as shown in the following figure.</span></span>
    
    ![Schritt 6 des Assistenten zur Massenhinzufügung von Benutzern - Ergebnisse senden](media/0cd43832-071b-4b33-b57a-5d07959985ad.png)
  
12. <span data-ttu-id="2b726-p127">Nachdem Sie Benutzer zu Office 365 hinzugefügt haben, müssen Sie diesen Ihre Office 365-Kontoinformationen zukommen lassen. Verwenden Sie hierfür Ihre normale Vorgehensweise für die Übermittlung neuer Kennwörter.</span><span class="sxs-lookup"><span data-stu-id="2b726-p127">After you've added users to Office 365, you need to tell them about their Office 365 account information. Use your normal process for communicating new passwords.</span></span>
    

