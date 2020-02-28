---
title: Gleichzeitiges Hinzufügen mehrerer Benutzer zu Office 365 - Administratorhilfe
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365P_AddUsersCSV
- O365M_AddUsersCSV
- O365E_AddUsersCSV
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
ms.openlocfilehash: 0d0416662bf4934d3373f1ab7ac23c8055ad3098
ms.sourcegitcommit: 6ad59ab24a5dc8d27f448ca7fe4f6bdf7ab28066
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/27/2020
ms.locfileid: "42316014"
---
# <a name="add-several-users-at-the-same-time-to-office-365---admin-help"></a><span data-ttu-id="8b38b-105">Gleichzeitiges Hinzufügen mehrerer Benutzer zu Office 365 – Administratorhilfe</span><span class="sxs-lookup"><span data-stu-id="8b38b-105">Add several users at the same time to Office 365 - Admin Help</span></span>

<span data-ttu-id="8b38b-p102">Jedes Mitglied in Ihrem Team benötigt ein Benutzerkonto, bevor es sich anmelden und auf Office 365-Dienste wie E-Mail und Office zugreifen kann. Wenn das Team viele Personen umfasst, können Sie deren Konten aus einer Excel-Tabelle oder einer anderen, im CSV-Format gespeicherten, Datei gleichzeitig hinzufügen. [Was ist eine CSV-Datei?](add-several-users-at-the-same-time.md#__toc316652088)</span><span class="sxs-lookup"><span data-stu-id="8b38b-p102">Each person on your team needs a user account before they can sign in and access Office 365 services, such as email and Office. If you have a lot of people, you can add their accounts all at once from an Excel spreadsheet or other file saved in CSV format. [Not sure what CSV format is?](add-several-users-at-the-same-time.md#__toc316652088)</span></span>
  
> [!NOTE] 
> <span data-ttu-id="8b38b-109">Wenn Sie das neue Microsoft 365 Admin Center nicht verwenden, können Sie es aktivieren, indem Sie den Umschalter **Das neue Admin Center** am oberen Rand der Startseite auswählen.</span><span class="sxs-lookup"><span data-stu-id="8b38b-109">If you're not using the new Microsoft 365 admin center, you can turn it on by selecting the **Try the new admin center** toggle located at the top of the Home page.</span></span>

## <a name="add-multiple-users-to-office-365-in-the-microsoft-365-admin-center"></a><span data-ttu-id="8b38b-110">Hinzufügen von mehreren Benutzern zu Office 365 im Microsoft 365 Admin Center</span><span class="sxs-lookup"><span data-stu-id="8b38b-110">Add multiple users to Office 365 in the Microsoft 365 admin center</span></span>

1. <span data-ttu-id="8b38b-111">Melden Sie sich mit Ihrem Geschäfts- oder Schulkonto bei Office 365 an.</span><span class="sxs-lookup"><span data-stu-id="8b38b-111">Sign in to Office 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="8b38b-112">Wählen Sie im Admin Center **Benutzer** \> **Aktive Benutzer** aus.</span><span class="sxs-lookup"><span data-stu-id="8b38b-112">In the admin center, choose **Users** \> **Active users**.</span></span>

3. <span data-ttu-id="8b38b-113">Wählen Sie **mehrere Benutzer hinzufügen**aus.</span><span class="sxs-lookup"><span data-stu-id="8b38b-113">Select **Add multiple users**.</span></span>

4. <span data-ttu-id="8b38b-114">Im Bereich **Mehrere Benutzer importieren** können Sie eine CSV-Beispieldatei mit oder ohne eingetragene Beispieldaten optional herunterladen.</span><span class="sxs-lookup"><span data-stu-id="8b38b-114">On the **Import multiple users** panel, you can optionally download a sample CSV file with or without sample data filled in.</span></span> 
    
    <span data-ttu-id="8b38b-115">Ihre Tabelle muss **dieselben Spaltenüberschriften** wie die Beispieltabelle enthalten ("Benutzername", "Vorname" usw.). Wenn Sie die Vorlage verwenden, öffnen Sie sie in einem Textbearbeitungstool, z. B. Editor. Sie sollten nach Möglichkeit alle Daten in Zeile 1 beibehalten und Daten nur in Zeile 2 und die Zeilen darunter eingeben.</span><span class="sxs-lookup"><span data-stu-id="8b38b-115">Your spreadsheet needs to include the **exact same column headings** as the sample one (User Name, First Name, etc...). If you use the template, open it in a text editing tool, like Notepad, and consider leaving all the data in row 1 alone, and only entering data in rows 2 and below.</span></span> 
    
    <span data-ttu-id="8b38b-116">Darüber hinaus muss Ihre Tabelle für jeden Benutzer Werte für den Benutzernamen (wie "berend@contoso.com") und einen Anzeigenamen (wie "Berend Klein") enthalten.</span><span class="sxs-lookup"><span data-stu-id="8b38b-116">Your spreadsheet also needs to include values for the user name (like bob@contoso.com) and a display name (like Bob Kelly) for each user.</span></span> 
    
  ```
  User Name,First Name,Last Name,Display Name,Job Title,Department,Office Number,Office Phone,Mobile Phone,Fax,Address,City,State or Province,ZIP or Postal Code,Country or Region
  chris@contoso.com,Chris,Green,Chris Green,IT Manager,Information Technology,123451,123-555-1211,123-555-6641,123-555-9821,1 Microsoft way,Redmond,Wa,98052,United States
  ben@contoso.com,Ben,Andrews,Ben Andrews,IT Manager,Information Technology,123452,123-555-1212,123-555-6642,123-555-9822,1 Microsoft way,Redmond,Wa,98052,United States
  david@contoso.com,David,Longmuir,David Longmuir,IT Manager,Information Technology,123453,123-555-1213,123-555-6643,123-555-9823,1 Microsoft way,Redmond,Wa,98052,United States
  cynthia@contoso.com,Cynthia,Carey,Cynthia Carey,IT Manager,Information Technology,123454,123-555-1214,123-555-6644,123-555-9824,1 Microsoft way,Redmond,Wa,98052,United States
  melissa@contoso.com,Melissa,MacBeth,Melissa MacBeth,IT Manager,Information Technology,123455,123-555-1215,123-555-6645,123-555-9825,1 Microsoft way,Redmond,Wa,98052,United States
  
  ```

5. <span data-ttu-id="8b38b-117">Geben Sie in dem Feld einen Dateipfad ein, oder wählen Sie **Durchsuchen** aus, um zum Speicherort der CSV-Datei zu navigieren. Wählen Sie dann **Überprüfen** aus.</span><span class="sxs-lookup"><span data-stu-id="8b38b-117">Enter a file path into the box, or choose **Browse** to browse to the CSV file location, then choose **Verify**.</span></span>
  
    <span data-ttu-id="8b38b-p103">Wenn es Probleme mit der Datei gibt, wird eine entsprechende Meldung angezeigt. Sie können auch eine Protokolldatei herunterladen.</span><span class="sxs-lookup"><span data-stu-id="8b38b-p103">If there are problems with the file, the problem is displayed in the panel. You can also download a log file.</span></span>
    
5. <span data-ttu-id="8b38b-120">Im Dialogfeld **Benutzeroptionen festlegen** können Sie den Anmeldestatus festlegen und die Produktlizenz auswählen, die allen Benutzern zugewiesen werden soll.</span><span class="sxs-lookup"><span data-stu-id="8b38b-120">On the **Set user options** dialog you can set the sign-in status and choose the product license that will be assigned to all users.</span></span> 
    
6. <span data-ttu-id="8b38b-121">Im Dialogfeld **Ergebnisse anzeigen** können Sie auswählen, ob die Ergebnisse an Sie selbst oder an andere Benutzer (Kennwörter im Nur-Text-Format) gesendet werden sollen. Außerdem können Sie sehen, wie viele Benutzer erstellt wurden und ob Sie weitere Lizenzen erwerben müssen, um sie einigen der neuen Benutzer zuzuweisen.</span><span class="sxs-lookup"><span data-stu-id="8b38b-121">On the **View your result** dialog you can choose to send the results to either yourself or other users (passwords will be in plain text) and you can see how many users were created, and if you need to purchase more licenses to assign to some of the new users.</span></span> 

## <a name="next-steps"></a><span data-ttu-id="8b38b-122">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="8b38b-122">Next steps</span></span>
<span data-ttu-id="8b38b-123"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="8b38b-123"><a name="bk_preview"> </a></span></span>

- <span data-ttu-id="8b38b-124">Da diese Personen nun über Konten verfügen, müssen Sie [Office 365 oder Office 2016 auf einem PC oder Mac herunterladen und installieren oder neu installieren](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658).</span><span class="sxs-lookup"><span data-stu-id="8b38b-124">Now that these people have accounts, they need to [Download and install or reinstall Office 365 or Office 2016 on a PC or Mac](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658).</span></span> <span data-ttu-id="8b38b-125">Jede Person in Ihrem Team kann Office 365 auf bis zu fünf PCs oder Macs installieren.</span><span class="sxs-lookup"><span data-stu-id="8b38b-125">Each person on your team can install Office 365 on up to 5 PCs or Macs.</span></span> 
    
- <span data-ttu-id="8b38b-126">Jede Person kann auch [Office-Apps und e-Mail auf einem mobilen Gerät](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f) auf bis zu 5 Tablets und 5 Telefonen wie iPhones, iPads und Android-Telefone und-Tablets einrichten.</span><span class="sxs-lookup"><span data-stu-id="8b38b-126">Each person can also [Set up Office apps and email on a mobile device](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f) on up to 5 tablets and 5 phones, such as iPhones, iPads, and Android phones and tablets.</span></span> <span data-ttu-id="8b38b-127">Hiermit können Office-Dateien von praktisch überall aus bearbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="8b38b-127">This way they can edit Office files from anywhere.</span></span> 
    
    <span data-ttu-id="8b38b-128">Weitere Informationen finden Sie unter [Set up Office 365 für Unternehmen](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) for a End-to-End List of the Setup Steps.</span><span class="sxs-lookup"><span data-stu-id="8b38b-128">See [Set up Office 365 for business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) for an end-to-end list of the setup steps.</span></span> 
    
## <a name="more-information-about-how-to-add-users-to-office-365"></a><span data-ttu-id="8b38b-129">Weitere Informationen dazu, wie Sie Benutzer zu Office 365 hinzufügen</span><span class="sxs-lookup"><span data-stu-id="8b38b-129">More information about how to add users to Office 365</span></span>
<span data-ttu-id="8b38b-130"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="8b38b-130"><a name="bk_preview"> </a></span></span>

### <a name="not-sure-what-csv-format-is"></a><span data-ttu-id="8b38b-131">Was ist eine CSV-Datei?</span><span class="sxs-lookup"><span data-stu-id="8b38b-131">Not sure what CSV format is?</span></span>
<span data-ttu-id="8b38b-132"><a name="__toc316652088"> </a></span><span class="sxs-lookup"><span data-stu-id="8b38b-132"><a name="__toc316652088"> </a></span></span>

<span data-ttu-id="8b38b-p106">Eine CSV-Datei ist eine Datei mit durch Kommas getrennten Werten. Sie können eine Datei wie diese mit einem beliebigen Text-Editor oder Tabellenkalkulationsprogramm wie beispielsweise Excel erstellen oder bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="8b38b-p106">A CSV file is a file with comma separated values. You can create or edit a file like this with any text editor or spreadsheet program, such as Excel.</span></span>
  
<span data-ttu-id="8b38b-p107">Sie können [diese Beispieltabelle](https://www.microsoft.com/download/details.aspx?id=45485) als Ausgangspunkt herunterladen. Denken Sie daran, dass bei Office 365 in der ersten Zeile Spaltenüberschriften stehen müssen. Ersetzen Sie die Überschriften deshalb nicht durch ein anderes Element.</span><span class="sxs-lookup"><span data-stu-id="8b38b-p107">You can download [this sample spreadsheet](https://www.microsoft.com/download/details.aspx?id=45485) as a starting point. Remember that Office 365 requires column headings in the first row so don't replace them with something else.</span></span> 
  
<span data-ttu-id="8b38b-137">Speichern Sie die Datei unter einem neuen Namen, und geben Sie das Format "CSV" an.</span><span class="sxs-lookup"><span data-stu-id="8b38b-137">Save the file with a new name, and specify CSV format.</span></span>
  
![Ein Bild, das zeigt, wie eine Datei in Excel im CSV-Format gespeichert wird](media/35a86ebe-63ab-4b4d-9a92-e177de33ebae.png)
  
<span data-ttu-id="8b38b-p108">Beim Speichern der Datei werden Sie wahrscheinlich darüber informiert, dass einige Features in Ihrer Arbeitsmappe verloren gehen, wenn Sie die Datei im CSV-Format speichern. Dies geht in Ordnung. Klicken Sie auf **Ja**, um den Vorgang fortzusetzen.</span><span class="sxs-lookup"><span data-stu-id="8b38b-p108">When you save the file, you'll probably get a prompt that some features in your workbook will be lost if you save the file in CSV format. This is okay. Click **Yes** to continue.</span></span> 
  
![Eine Abbildung der Eingabeaufforderung, die in Excel möglicherweise angezeigt wird und fragt, ob Sie die Datei tatsächlich im CSV-Format speichern möchten](media/51032a81-690c-45ef-bfc5-09ea7f790e98.png)
  
### <a name="tips-for-formatting-your-spreadsheet"></a><span data-ttu-id="8b38b-143">Tipps zum Formatieren Ihrer Tabelle</span><span class="sxs-lookup"><span data-stu-id="8b38b-143">Tips for formatting your spreadsheet</span></span>
<span data-ttu-id="8b38b-144"><a name="__toc314595848"> </a></span><span class="sxs-lookup"><span data-stu-id="8b38b-144"><a name="__toc314595848"> </a></span></span>

- <span data-ttu-id="8b38b-p109">**Benötige ich dieselben Spaltenüberschriften wie in der Beispieltabelle?** Ja. Die erste Zeile der Beispieltabelle enthält die Spaltenüberschriften. Diese Überschriften sind erforderlich. Erstellen Sie für jeden Benutzer, den Sie Office 365 hinzufügen möchten, eine Zeile unter der Überschrift. Wenn Sie eine der Spaltenüberschriften hinzufügen, ändern oder löschen, kann Office 365 Benutzer anhand der Informationen in der Datei möglicherweise nicht erstellen.</span><span class="sxs-lookup"><span data-stu-id="8b38b-p109">**Do I need the same column headings as in the sample spreadsheet?** Yes. The sample spreadsheet contains column headings in the first row. These headings are required. For each user you want to add to Office 365, create a row under the heading. If you add, change, or delete any of the column headings, Office 365 might not be able to create users from the information in the file.</span></span> 
    
- <span data-ttu-id="8b38b-p110">**Was kann ich tun, wenn ich nicht über alle Informationen verfüge, die bei jedem Benutzer erforderlich sind?** Der Benutzername und der Anzeigename sind unbedingt erforderlich; Sie können keinen neuen Benutzer ohne diese Angaben hinzufügen. Falls Ihnen einige der anderen Informationen fehlen, wie beispielsweise das Fax, können Sie ein Leerzeichen plus das von Ihnen verwendete Trennzeichen eingeben und so festlegen, dass das Feld leer bleiben soll.</span><span class="sxs-lookup"><span data-stu-id="8b38b-p110">**What if I don't have all the information required for each user?** The user name and display name are required, and you cannot add a new user without this information. If you don't have some of the other information, such as the fax, you can use a space plus a comma to indicate that the field should remain blank.</span></span> 
    
- <span data-ttu-id="8b38b-p111">\*\* How small or large can the spreadsheet be? \*\* The spreadsheet must have at least two rows. One is for the column headings (the user data column label) and one for the user. You cannot have more than 251 rows. If you need to import more than 250 users, you can create more than one spreadsheet.</span><span class="sxs-lookup"><span data-stu-id="8b38b-p111">\*\* How small or large can the spreadsheet be? \*\* The spreadsheet must have at least two rows. One is for the column headings (the user data column label) and one for the user. You cannot have more than 251 rows. If you need to import more than 250 users, you can create more than one spreadsheet.</span></span> 
    
- <span data-ttu-id="8b38b-p112">\*\* What languages can I use? \*\* When you create your spreadsheet, you can enter user data column labels in any language or characters, but you must not change the order of the labels, as shown in the sample. You can then make entries into the fields, using any language or characters, and save your file in a Unicode or UTF-8 format.</span><span class="sxs-lookup"><span data-stu-id="8b38b-p112">\*\* What languages can I use? \*\* When you create your spreadsheet, you can enter user data column labels in any language or characters, but you must not change the order of the labels, as shown in the sample. You can then make entries into the fields, using any language or characters, and save your file in a Unicode or UTF-8 format.</span></span> 
    
- <span data-ttu-id="8b38b-p113">**Was geschieht, wenn ich Benutzer aus verschiedenen Ländern oder Regionen hinzufüge?** Erstellen Sie eine separate Tabelle für jeden Bereich. Sie müssen den Assistenten "Massenhinzufügung von Benutzern" mit jeder Tabelle schrittweise durchlaufen. Geben Sie dabei einen einzigen Standort für alle Benutzer an, die in der Datei, mit der Sie arbeiten, enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="8b38b-p113">**What if I'm adding users from different countries or regions?** Create a separate spreadsheet for each area. You'll need to step through the Bulk add users wizard which each spreadsheet, giving a single location of all users included in the file that you're working with.</span></span> 
    
- <span data-ttu-id="8b38b-p114">**Bestehen Beschränkungen bei der Anzahl der Zeichen, die ich verwenden kann?** Die folgende Tabelle zeigt die Beschriftungen für Benutzerdatenspalten sowie die maximale Zeichenanzahl für jedes Element der Beispieltabelle.</span><span class="sxs-lookup"><span data-stu-id="8b38b-p114">**Is there a limit to the number of characters I can use?** The following table shows the user data column labels and the maximum character length for each in the sample spreadsheet.</span></span> 
    
|<span data-ttu-id="8b38b-167">**Beschriftung für Benutzerdatenspalte**</span><span class="sxs-lookup"><span data-stu-id="8b38b-167">**User data column label**</span></span>|<span data-ttu-id="8b38b-168">**Maximale Zeichenanzahl**</span><span class="sxs-lookup"><span data-stu-id="8b38b-168">**Maximum character length**</span></span>|
|:-----|:-----|
|<span data-ttu-id="8b38b-169">Benutzername (erforderlich)</span><span class="sxs-lookup"><span data-stu-id="8b38b-169">User Name (Required)</span></span>  <br/> |<span data-ttu-id="8b38b-170">79, einschließlich des at-Zeichens (@), im Format "Name@Domäne.\<#60;Erweiterung\>".</span><span class="sxs-lookup"><span data-stu-id="8b38b-170">79 including the at sign (@), in the format name@domain.\<extension\>.</span></span> <span data-ttu-id="8b38b-171">Der Alias des Benutzers darf 50 Zeichen nicht überschreiten, und der Domänenname darf 48 Zeichen nicht überschreiten.</span><span class="sxs-lookup"><span data-stu-id="8b38b-171">The user's alias cannot exceed 50 characters, and the domain name cannot exceed 48 characters.</span></span>  <br/> |
|<span data-ttu-id="8b38b-172">Vorname</span><span class="sxs-lookup"><span data-stu-id="8b38b-172">First Name</span></span>  <br/> |<span data-ttu-id="8b38b-173">64</span><span class="sxs-lookup"><span data-stu-id="8b38b-173">64</span></span>  <br/> |
|<span data-ttu-id="8b38b-174">Nachname</span><span class="sxs-lookup"><span data-stu-id="8b38b-174">Last Name</span></span>  <br/> |<span data-ttu-id="8b38b-175">64</span><span class="sxs-lookup"><span data-stu-id="8b38b-175">64</span></span>  <br/> |
|<span data-ttu-id="8b38b-176">Anzeigename (erforderlich)</span><span class="sxs-lookup"><span data-stu-id="8b38b-176">Display Name (required)</span></span>  <br/> |<span data-ttu-id="8b38b-177">256</span><span class="sxs-lookup"><span data-stu-id="8b38b-177">256</span></span>  <br/> |
|<span data-ttu-id="8b38b-178">Position</span><span class="sxs-lookup"><span data-stu-id="8b38b-178">Job Title</span></span>  <br/> |<span data-ttu-id="8b38b-179">64</span><span class="sxs-lookup"><span data-stu-id="8b38b-179">64</span></span>  <br/> |
|<span data-ttu-id="8b38b-180">Abteilung</span><span class="sxs-lookup"><span data-stu-id="8b38b-180">Department</span></span>  <br/> |<span data-ttu-id="8b38b-181">64</span><span class="sxs-lookup"><span data-stu-id="8b38b-181">64</span></span>  <br/> |
|<span data-ttu-id="8b38b-182">Büronummer</span><span class="sxs-lookup"><span data-stu-id="8b38b-182">Office Number</span></span>  <br/> |<span data-ttu-id="8b38b-183">128</span><span class="sxs-lookup"><span data-stu-id="8b38b-183">128</span></span>  <br/> |
|<span data-ttu-id="8b38b-184">Rufnummer</span><span class="sxs-lookup"><span data-stu-id="8b38b-184">Office Phone</span></span>  <br/> |<span data-ttu-id="8b38b-185">64</span><span class="sxs-lookup"><span data-stu-id="8b38b-185">64</span></span>  <br/> |
|<span data-ttu-id="8b38b-186">Mobiltelefon</span><span class="sxs-lookup"><span data-stu-id="8b38b-186">Mobile Phone</span></span>  <br/> |<span data-ttu-id="8b38b-187">64</span><span class="sxs-lookup"><span data-stu-id="8b38b-187">64</span></span>  <br/> |
|<span data-ttu-id="8b38b-188">Fax</span><span class="sxs-lookup"><span data-stu-id="8b38b-188">Fax</span></span>  <br/> |<span data-ttu-id="8b38b-189">64</span><span class="sxs-lookup"><span data-stu-id="8b38b-189">64</span></span>  <br/> |
|<span data-ttu-id="8b38b-190">Adresse</span><span class="sxs-lookup"><span data-stu-id="8b38b-190">Address</span></span>  <br/> |<span data-ttu-id="8b38b-191">1023</span><span class="sxs-lookup"><span data-stu-id="8b38b-191">1023</span></span>  <br/> |
|<span data-ttu-id="8b38b-192">Ort</span><span class="sxs-lookup"><span data-stu-id="8b38b-192">City</span></span>  <br/> |<span data-ttu-id="8b38b-193">128</span><span class="sxs-lookup"><span data-stu-id="8b38b-193">128</span></span>  <br/> |
|<span data-ttu-id="8b38b-194">Bundesland oder Kanton</span><span class="sxs-lookup"><span data-stu-id="8b38b-194">State or Province</span></span>  <br/> |<span data-ttu-id="8b38b-195">128</span><span class="sxs-lookup"><span data-stu-id="8b38b-195">128</span></span>  <br/> |
|<span data-ttu-id="8b38b-196">PLZ</span><span class="sxs-lookup"><span data-stu-id="8b38b-196">ZIP or Postal Code</span></span>  <br/> |<span data-ttu-id="8b38b-197">40</span><span class="sxs-lookup"><span data-stu-id="8b38b-197">40</span></span>  <br/> |
|<span data-ttu-id="8b38b-198">Land oder Region</span><span class="sxs-lookup"><span data-stu-id="8b38b-198">Country or Region</span></span>  <br/> |<span data-ttu-id="8b38b-199">128</span><span class="sxs-lookup"><span data-stu-id="8b38b-199">128</span></span>  <br/> |
   
### <a name="still-having-problems-when-adding-users-to-office-365"></a><span data-ttu-id="8b38b-200">Gibt es weiterhin Probleme beim Hinzufügen von Benutzern zu Office 365?</span><span class="sxs-lookup"><span data-stu-id="8b38b-200">Still having problems when adding users to Office 365?</span></span>

- <span data-ttu-id="8b38b-p116">**Überprüfen Sie sorgfältig, ob die Tabelle richtig formatiert wurde.** Überprüfen Sie, ob die Spaltenüberschriften mit den Überschriften in der Beispieldatei übereinstimmen. Vergewissern Sie sich, dass Sie die Regeln für die maximale Zeichenanzahl eingehalten haben und dass jedes Feld durch ein Trennzeichen getrennt ist.</span><span class="sxs-lookup"><span data-stu-id="8b38b-p116">**Double-check that the spreadsheet is formatted correctly.** Check the column headings to make sure they match the headings in the sample file. Make sure you're following the rules for character lengths and that each field is separated by a comma.</span></span> 
    
- <span data-ttu-id="8b38b-204">**Wenn die neuen Benutzer nicht sofort in Office 365 angezeigt werden, warten Sie einige Minuten.**</span><span class="sxs-lookup"><span data-stu-id="8b38b-204">**If you don't see the new users in Office 365 right away, wait a few minutes.**</span></span> <span data-ttu-id="8b38b-205">Es kann eine Weile dauern, bis Änderungen alle Dienste in Office 365 durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="8b38b-205">It can take a little while for changes to go across all the services in Office 365.</span></span> 
    
## <a name="related-articles"></a><span data-ttu-id="8b38b-206">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="8b38b-206">Related articles</span></span>

[<span data-ttu-id="8b38b-207">Hinzufügen von einzelnen Benutzern oder Massenhinzufügen von Benutzern zu Office 365</span><span class="sxs-lookup"><span data-stu-id="8b38b-207">Add users individually or in bulk to Office 365</span></span>](https://docs.microsoft.com/office365/admin/add-users/add-users)




