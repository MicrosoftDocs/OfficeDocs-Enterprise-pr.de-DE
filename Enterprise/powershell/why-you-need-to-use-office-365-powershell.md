---
title: Warum Sie Office 365 PowerShell verwenden müssen
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/11/2019
audience: ITPro
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Office_Other
ms.assetid: b3209b1a-40c7-4ede-8e78-8a88bb2adc8a
description: 'Zusammenfassung: Verstehen Sie, warum Sie aus Effizienzgründen oder aus Notwendigkeit Office 365 PowerShell zum Verwalten von Office 365 verwenden müssen.'
ms.openlocfilehash: 66782a9165c76c7e1d506e40fa1cacd6db0c6724
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2019
ms.locfileid: "38747444"
---
# <a name="why-you-need-to-use-office-365-powershell"></a><span data-ttu-id="aa873-103">Warum Sie Office 365 PowerShell verwenden müssen</span><span class="sxs-lookup"><span data-stu-id="aa873-103">Why you need to use Office 365 PowerShell</span></span>

<span data-ttu-id="aa873-104">Mit dem Microsoft 365 Admin Center können Sie nicht nur Ihre Office 365-Benutzerkonten und-Lizenzen verwalten, sondern auch Ihre Office 365-Serverprodukte verwalten: Exchange, Skype for Business Online und SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="aa873-104">With the Microsoft 365 admin center, you can not only manage your Office 365 user accounts and licenses, but you can also manage your Office 365 server products: Exchange, Skype for Business Online, and SharePoint Online.</span></span> <span data-ttu-id="aa873-105">Sie können diese Elemente jedoch auch mit Office 365 PowerShell-Befehlen verwalten, die eine Befehlszeilen- und Skriptsprachenumgebung für Geschwindigkeit, Automatisierung und zusätzliche Funktionen nutzen.</span><span class="sxs-lookup"><span data-stu-id="aa873-105">However, you can also manage these elements with Office 365 PowerShell commands, taking advantage of a command-line and scripting language environment for speed, automation, and additional capability.</span></span>
  
<span data-ttu-id="aa873-106">In diesem Artikel werden die Möglichkeiten erläutert, die Sie bei der Verwendung von Office 365 PowerShell zum Verwalten von Office 365 haben.</span><span class="sxs-lookup"><span data-stu-id="aa873-106">In this article, we'll show you these ways in which you can use Office 365 PowerShell to manage Office 365.</span></span>
  
- <span data-ttu-id="aa873-107">Office 365 PowerShell kann zusätzliche Informationen aufdecken, die Sie mit dem Microsoft 365 Admin Center nicht sehen können.</span><span class="sxs-lookup"><span data-stu-id="aa873-107">Office 365 PowerShell can reveal additional information that you cannot see with the Microsoft 365 admin center</span></span>
    
- <span data-ttu-id="aa873-108">Office 365 weist Features auf, die Sie nur mithilfe von Office 365 PowerShell konfigurieren können</span><span class="sxs-lookup"><span data-stu-id="aa873-108">Office 365 has features that you can only configure by using Office 365 PowerShell</span></span>
    
- <span data-ttu-id="aa873-109">Office 365 PowerShell eignet sich hervorragend zum Ausführen von Massenvorgängen.</span><span class="sxs-lookup"><span data-stu-id="aa873-109">Office 365 PowerShell is great at performing bulk operations</span></span>
    
- <span data-ttu-id="aa873-110">Office 365 PowerShell eignet sich hervorragend zum Filtern von Daten</span><span class="sxs-lookup"><span data-stu-id="aa873-110">Office 365 PowerShell is great at filtering data</span></span>
    
- <span data-ttu-id="aa873-111">Office 365 PowerShell erleichtert das Drucken oder Speichern von Daten.</span><span class="sxs-lookup"><span data-stu-id="aa873-111">Office 365 PowerShell makes it easy to print or save data</span></span>
    
- <span data-ttu-id="aa873-112">Office 365 PowerShell ermöglicht eine Verwaltung über Serverprodukte hinweg</span><span class="sxs-lookup"><span data-stu-id="aa873-112">Office 365 PowerShell lets you manage across server products</span></span>
    
<span data-ttu-id="aa873-p102">Bevor Sie beginnen, müssen Sie verstehen, dass es sich bei Office 365 PowerShell um einen Satz von Modulen für Windows PowerShell, eine Befehlszeilenumgebung für Windows-basierte Dienste und -Plattformen handelt. Diese Umgebung erstellt eine Befehlszeilensprache, die mit zusätzlichen Modulen erweitert werden kann und eine Möglichkeit zum Ausführen einfacher oder komplexer Befehle oder Skripts bietet. Nachdem Sie beispielsweise die Office 365 PowerShell-Module installiert und mit Ihrem Office 365-Abonnement verbunden haben, können Sie diesen Befehl ausführen, um alle Benutzerpostfächer für Microsoft Exchange Online aufzulisten:</span><span class="sxs-lookup"><span data-stu-id="aa873-p102">Before you begin, understand that Office 365 PowerShell is a set of modules for Windows PowerShell, a command-line environment for Windows-based services and platforms. This environment creates a command shell language that can be extended with additional modules and provides a way to execute simple or complex commands or scripts. For example, after you install the Office 365 PowerShell modules and connect to your Office 365 subscription, you can run this command to list all of the user mailboxes for Microsoft Exchange Online:</span></span>
  
```powershell
Get-Mailbox
```

<span data-ttu-id="aa873-116">Das erhalten der Liste der Postfächer kann auch problemlos über das Microsoft 365 Admin Center erfolgen, aber die Anzahl der Elemente in allen Listen für alle Websites für alle Ihre Webanwendungen kann nicht einfach ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="aa873-116">Getting the list of mailboxes can also be easily done using the Microsoft 365 admin center, but counting the number of items in all of the lists for all of the sites for all of your web apps cannot be easily done.</span></span>
  
<span data-ttu-id="aa873-117">Beachten Sie, dass Office 365 PowerShell darauf ausgelegt ist, ihre Fähigkeit zum Verwalten von Office 365 zu erweitern und zu verbessern, statt das Microsoft 365 Admin Center zu ersetzen.</span><span class="sxs-lookup"><span data-stu-id="aa873-117">Please note that Office 365 PowerShell is designed to augment and enhance your ability to manage Office 365, not to replace the Microsoft 365 admin center.</span></span> <span data-ttu-id="aa873-118">Als Office 365 Administrator müssen Sie sich mit der Verwendung von Office 365 PowerShell mindestens vertraut machen, da es einige Konfigurationsverfahren gibt, die nur mit Office 365 PowerShell-Befehlen ausgeführt werden können.</span><span class="sxs-lookup"><span data-stu-id="aa873-118">As an Office 365 administrator, you must become at least comfortable with using Office 365 PowerShell because there are some configuration procedures that can only be done with Office 365 PowerShell commands.</span></span> <span data-ttu-id="aa873-119">In diesen Fällen müssen Sie sich mit den folgenden Themen vertraut machen:</span><span class="sxs-lookup"><span data-stu-id="aa873-119">In these cases, you will be required to understand how to:</span></span>
  
- <span data-ttu-id="aa873-120">Installation der Office 365 PowerShell-Module (nur einmal pro Administratorcomputer).</span><span class="sxs-lookup"><span data-stu-id="aa873-120">Install the Office 365 PowerShell modules (done only once for each administrator computer).</span></span>
    
- <span data-ttu-id="aa873-121">Verbinden mit Ihrem Office 365-Abonnement (einmal pro PowerShell-Sitzung).</span><span class="sxs-lookup"><span data-stu-id="aa873-121">Connect to your Office 365 subscription (done once for each PowerShell session).</span></span>
    
- <span data-ttu-id="aa873-122">Zusammentragen der erforderlichen Informationen zum Ausführen der erforderlichen Office 365 PowerShell-Befehle.</span><span class="sxs-lookup"><span data-stu-id="aa873-122">Gather the information needed to run the required Office 365 PowerShell commands.</span></span>
    
- <span data-ttu-id="aa873-123">Erfolgreiches Ausführen der Office 365 PowerShell-Befehle.</span><span class="sxs-lookup"><span data-stu-id="aa873-123">Run the Office 365 PowerShell commands successfully.</span></span>
    
<span data-ttu-id="aa873-p104">Nachdem Sie diese grundlegenden Fähigkeiten erlernt haben, müssen Sie Ihre Postfachbenutzer nicht mit dem Befehl **Get-Mailbox** auflisten, und Sie müssen nicht verstehen, wie ein neuer Befehl wie der vorherige erstellt wird, um alle Elemente in allen Listen für alle Standorte für alle Web-Apps zu zählen. Microsoft und die Community von Office 365-Administratoren können Ihnen bei Bedarf dabei behilflich sein.</span><span class="sxs-lookup"><span data-stu-id="aa873-p104">After learning these basic skills, you are not required to list your mailbox users with **Get-Mailbox** command, nor are you required to understand how to create a new command like the previous one to count all the items in all the lists for all of the sites for all of your web apps. Microsoft and the community of Office 365 administrators can help you with that as needed.</span></span>
  
## <a name="office-365-powershell-can-reveal-additional-information-that-you-cannot-see-with-the-microsoft-365-admin-center"></a><span data-ttu-id="aa873-126">Office 365 PowerShell kann zusätzliche Informationen aufdecken, die Sie mit dem Microsoft 365 Admin Center nicht sehen können.</span><span class="sxs-lookup"><span data-stu-id="aa873-126">Office 365 PowerShell can reveal additional information that you cannot see with the Microsoft 365 admin center</span></span>

<span data-ttu-id="aa873-127">Im Microsoft 365 Admin Center werden viele nützliche Informationen angezeigt, aber das bedeutet nicht, dass alle möglichen Informationen angezeigt werden, die auf Benutzer, Lizenzen, Postfächern und Websites gespeichert Office 365.</span><span class="sxs-lookup"><span data-stu-id="aa873-127">The Microsoft 365 admin center displays a lot of useful information, but that doesn't mean that it displays all the possible information that Office 365 stores on users, licenses, mailboxes, and sites.</span></span> <span data-ttu-id="aa873-128">Im folgenden finden Sie ein Beispiel für **Benutzer und Gruppen** im Microsoft 365 Admin Center:</span><span class="sxs-lookup"><span data-stu-id="aa873-128">Here is an example for **users and groups** in the Microsoft 365 admin center:</span></span>
  
![Beispiel für die Anzeige von Benutzern und Gruppen im Microsoft 365 Admin Center.](media/o365-powershell-users-and-groups.png)
  
<span data-ttu-id="aa873-130">Hier werden für zahlreiche Zwecke die benötigten Informationen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="aa873-130">For many purposes, this displays the information you need to know.</span></span> <span data-ttu-id="aa873-131">Es kann jedoch vorkommen, dass Sie mehr benötigen.</span><span class="sxs-lookup"><span data-stu-id="aa873-131">However, there are times when you need more.</span></span> <span data-ttu-id="aa873-132">Beispielsweise hängen Office 365 Lizenzierung (und die Office 365 Funktionen, die einem Benutzer zur Verfügung stehen) teilweise vom geografischen Standort dieses Benutzers ab.</span><span class="sxs-lookup"><span data-stu-id="aa873-132">For example, Office 365 licensing (and the Office 365 features available to a user) depend in part on that user's geographic location.</span></span> <span data-ttu-id="aa873-133">Die Richtlinien und Features, die Sie auf einen Benutzer erweitern können, der in den USA lebt, sind möglicherweise nicht die gleichen Richtlinien und Features, die Sie auf einen Benutzer erweitern können der in Indien oder in Belgien lebt.</span><span class="sxs-lookup"><span data-stu-id="aa873-133">The policies and features you can extend to a user who lives in the United States might not be the same as the policies and features you can extend to a user who lives in India or in Belgium.</span></span> <span data-ttu-id="aa873-134">Sie können das Microsoft 365 Admin Center verwenden, um den geografischen Standort eines Benutzers mit den folgenden Schritten zu ermitteln:</span><span class="sxs-lookup"><span data-stu-id="aa873-134">You can use the Microsoft 365 admin center to determine a user's geographic location with these steps:</span></span>
  
1. <span data-ttu-id="aa873-135">Doppelklicken Sie auf den **Anzeigenamen** des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="aa873-135">Double-click the user's **Display Name**.</span></span>
    
2. <span data-ttu-id="aa873-136">Klicken Sie im Bereich "Benutzereigenschaften" auf **Details**.</span><span class="sxs-lookup"><span data-stu-id="aa873-136">In the user properties display pane, click **details**.</span></span>
    
3. <span data-ttu-id="aa873-137">Klicken Sie unter "Details" auf **Zusätzliche Details**.</span><span class="sxs-lookup"><span data-stu-id="aa873-137">In the details display, click **additional details**.</span></span>
    
4. <span data-ttu-id="aa873-138">Führen Sie einen Bildlauf nach unten bis zu **Land oder Region** aus.</span><span class="sxs-lookup"><span data-stu-id="aa873-138">Scroll down until you see the heading **Country or region**:</span></span>
    
     ![Beispiel für die Regionsinformationen für einen Benutzer im Microsoft 365 Admin Center.](media/o365-powershell-usage-location.png)
  
5. <span data-ttu-id="aa873-140">Notieren Sie den Anzeigenamen des Benutzers auf einem Blatt Papier, oder kopieren ihn in Editor.</span><span class="sxs-lookup"><span data-stu-id="aa873-140">Write the user's display name and location on a piece of paper, or copy and paste it into Notepad.</span></span> 
    
<span data-ttu-id="aa873-p107">Sie müssen diese Vorgehensweise für jeden Benutzer wiederholen. Bei zahlreichen Benutzern kann dies eine mühsame Aufgabe sein. Mit Office 365 PowerShell können Sie diese Informationen für alle Benutzer mit dem folgenden Befehl anzeigen:</span><span class="sxs-lookup"><span data-stu-id="aa873-p107">You must repeat this procedure for each user. For many users, this can be a tedious task. With Office 365 PowerShell, you can display this information for all of your users with the following command:</span></span>
  
```powershell
Get-MsolUser | Select DisplayName, UsageLocation
```

> [!NOTE]
> <span data-ttu-id="aa873-144">Für diesen Befehl müssen Sie das [Windows Azure Active Directory-Modul](https://docs.microsoft.com/powershell/module/Azuread/?view=azureadps-2.0) installieren.</span><span class="sxs-lookup"><span data-stu-id="aa873-144">This command requires you to install the [Windows Azure Active Directory module](https://docs.microsoft.com/powershell/module/Azuread/?view=azureadps-2.0).</span></span> 
  
<span data-ttu-id="aa873-145">Nachfolgend sehen Sie ein Beispiel der Anzeige:</span><span class="sxs-lookup"><span data-stu-id="aa873-145">Here is an example of the display:</span></span>
  
```powershell
DisplayName                               UsageLocation
-----------                               -------------
Bonnie Kearney                            GB
Fabrice Canel                             BR
Brian Johnson (TAILSPIN)                  US
Anne Wallace                              US
Alex Darrow                               US
David Longmuir                            BR
```

> [!TIP]
>  <span data-ttu-id="aa873-146">Die Interpretation dieses Office 365 PowerShell-Befehls ist:  Alle Benutzer im aktuellen Office 365-Abonnement abrufen (**Get-MsolUser**), dabei jedoch für jeden Benutzer jeweils nur Namen und Standort anzeigen (**Select DisplayName, UsageLocation**)</span><span class="sxs-lookup"><span data-stu-id="aa873-146">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription ( **Get-MsolUser** ), but only display the name and location for each user ( **Select DisplayName, UsageLocation** ).</span></span>
  
<span data-ttu-id="aa873-p108">Da Office 365 PowerShell eine Befehlszeilensprache unterstützt, können Sie die vom Befehl **Get-MSolUser** abgerufenen Informationen weiter bearbeiten. Sie möchten vielleicht die Benutzer anhand ihres Standorts sortieren, alle brasilianischen oder alle amerikanischen Benutzer zusammen gruppieren usw. Hier ist der Befehl:</span><span class="sxs-lookup"><span data-stu-id="aa873-p108">Because Office 365 PowerShell supports a command shell language, you can further manipulate the information obtained from the **Get-MSolUser** command. For example, maybe you'd like to sort these users by their location, grouping all the Brazilian users together, all the United States users together, etc. Here is the command:</span></span>
  
```powershell
Get-MsolUser | Select DisplayName, UsageLocation | Sort UsageLocation, DisplayName
```

<span data-ttu-id="aa873-149">Nachfolgend sehen Sie ein Beispiel der Anzeige:</span><span class="sxs-lookup"><span data-stu-id="aa873-149">Here is an example of the display:</span></span>
  
```powershell
DisplayName                                 UsageLocation
-----------                                 -------------
David Longmuir                              BR
Fabrice Canel                               BR
Bonnie Kearney                              GB
Alex Darrow                                 US
Anne Wallace                                US
Brian Johnson (TAILSPIN)                    US
```

> [!TIP]
>  <span data-ttu-id="aa873-150">Die Interpretation dieses Office 365 PowerShell-Befehls ist:  Alle Benutzer im aktuellen Office 365-Abonnement abrufen, dabei jedoch für jeden Benutzer jeweils nur Namen und Standort anzeigen und die Benutzerliste vorrangig nach Standort und dann erst nach Namen sortieren (**Sort UsageLocation, DisplayName**)</span><span class="sxs-lookup"><span data-stu-id="aa873-150">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription, but only display the name and location for each user and sort them first by their location, and then their names ( **Sort UsageLocation, DisplayName** ).</span></span>
  
<span data-ttu-id="aa873-p109">Sie können auch eine zusätzliche Filterung verwenden. Wenn Sie beispielsweise nur Informationen zu Benutzern in Brasilien anzeigen möchten, verwenden Sie den folgenden Befehl:</span><span class="sxs-lookup"><span data-stu-id="aa873-p109">You can also employ additional filtering. For example, if you only want to see information about users based in Brazil, use this command:</span></span>
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq "BR"} | Select DisplayName, UsageLocation 
```

<span data-ttu-id="aa873-153">Nachfolgend sehen Sie ein Beispiel der Anzeige:</span><span class="sxs-lookup"><span data-stu-id="aa873-153">Here is an example of the display:</span></span>
  
```powershell
DisplayName                                           UsageLocation
-----------                                           -------------
David Longmuir                                        BR
Fabrice Canel                                         BR
```

> [!TIP]
>  <span data-ttu-id="aa873-154">Die Interpretation dieses Office 365 PowerShell-Befehls ist:  Alle Benutzer im aktuellen Office 365-Abonnement abrufen, deren Standort Brasilien ist (**Where {$\_.UsageLocation -eq "BR"}**), und für jeden Benutzer Namen und Standort anzeigen</span><span class="sxs-lookup"><span data-stu-id="aa873-154">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription whose location is Brazil ( **Where {$\_.UsageLocation -eq "BR"}** ), then display the name and location for each user.</span></span>
  
 <span data-ttu-id="aa873-155">**Ein kurzer Hinweis zu größeren Domänen**</span><span class="sxs-lookup"><span data-stu-id="aa873-155">**A Quick Note Regarding Larger Domains**</span></span>
  
<span data-ttu-id="aa873-p110">Wenn Sie eine sehr große Domäne mit Zehntausenden von Benutzers haben, könnte dies bei einigen Beispielen in diesem Artikel zu "Einschränkungen" kommen. Je nach Computerleistung und verfügbarer Bandbreite möchten Sie zu viel auf einmal. Für große Organisationen bietet es sich daher an, einige dieser Office 365 PowerShell-Befehle auf zwei Befehle aufzuteilen. Dieser einer Befehle gibt beispielsweise alle Benutzerkonten zurück und zeigt den Namen und Standort für jedes Konto an:</span><span class="sxs-lookup"><span data-stu-id="aa873-p110">If you have a very large domain with tens of thousands of users, trying some of the examples we show in this article could lead to "throttling." That means that, based on things like computing power and available network bandwidth, you're trying to do a little too much at one time. Because of that, larger organizations might want to split some of these Office 365 PowerShell commands into two commands. For example, this one command returns all the user accounts and shows the name and location for each:</span></span>
  
```powershell
Get-MsolUser | Select DisplayName, UsageLocation
```

<span data-ttu-id="aa873-p111">Das funktioniert auch gut bei kleineren Domänen. In großen Organisationen müssen Sie den Befehl möglicherweise in zwei Befehle aufteilen: Ein Befehl zum Speichern der Benutzerkontoinformationen in einer Variablen und ein anderer Befehl zum Anzeigen der erforderlichen Informationen. Es folgt ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="aa873-p111">That works great for smaller domains. In a large organization, however, you might need to split that into two commands: one command to store the user account information in a variable and another command to display the needed information. Here is an example:</span></span>
  
```powershell
$x = Get-MsolUser
$x | Select DisplayName, UsageLocation
```


<span data-ttu-id="aa873-163">Die Interpretation dieses Satzes von Office 365 PowerShell-Befehlen ist:</span><span class="sxs-lookup"><span data-stu-id="aa873-163">The interpretation of this set of Office 365 PowerShell commands is:</span></span>
- <span data-ttu-id="aa873-164">Alle Benutzer im aktuellen Office 365-Abonnement abrufen und die Informationen in einer Variablen mit dem Namen "$x" speichern (**$x = Get-MsolUser**).</span><span class="sxs-lookup"><span data-stu-id="aa873-164">Get all of the users in the current Office 365 subscription and store the information in a variable named $x ( **$x = Get-MsolUser** ).</span></span>
- <span data-ttu-id="aa873-165">Den Inhalt der Variablen „$x“ anzeigen, dabei aber für jeden Benutzer nur Namen und Standort einschließen (**$x | Select DisplayName, UsageLocation**)</span><span class="sxs-lookup"><span data-stu-id="aa873-165">Display the contents of the variable $x, but only include the name and location for each user ( **$x | Select DisplayName, UsageLocation** ).</span></span>
  
## <a name="office-365-has-features-that-you-can-only-configure-with-office-365-powershell"></a><span data-ttu-id="aa873-166">Office 365 weist Features auf, die Sie nur mithilfe von Office 365 PowerShell konfigurieren können</span><span class="sxs-lookup"><span data-stu-id="aa873-166">Office 365 has features that you can only configure with Office 365 PowerShell</span></span>

<span data-ttu-id="aa873-167">Das Microsoft 365 Admin Center soll den Zugriff auf die am häufigsten oder bedeutsamsten administrativen Aufgaben ermöglichen, die für die meisten Personen gelten.</span><span class="sxs-lookup"><span data-stu-id="aa873-167">The Microsoft 365 admin center is intended to provide access to the most common or meaningful administrative tasks that apply to most people.</span></span> <span data-ttu-id="aa873-168">Das heißt, das Microsoft 365 Admin Center wurde so konzipiert, dass der typische Administrator mithilfe des Tools die am häufigsten verwendeten Verwaltungsaufgaben ausführen kann.</span><span class="sxs-lookup"><span data-stu-id="aa873-168">In other words, the Microsoft 365 admin center was designed so that the typical administrator could use the tool to carry out the most common management tasks.</span></span> <span data-ttu-id="aa873-169">Mit dieser Definition bedeutet dies, dass es einige Aufgaben gibt, die nicht mithilfe des Microsoft 365 Admin Center ausgeführt werden können.</span><span class="sxs-lookup"><span data-stu-id="aa873-169">By this definition, that means that there are some tasks that can't be completed by using the Microsoft 365 admin center.</span></span>
  
<span data-ttu-id="aa873-170">Das Skype for Business Online Admin Center bietet beispielsweise ein paar Optionen zum Erstellen benutzerdefinierter Besprechungseinladungen:</span><span class="sxs-lookup"><span data-stu-id="aa873-170">For example, the Skype for Business Online Admin center provides a few options for creating custom meeting invitations:</span></span>
  
![Beispiel für die Anzeige von benutzerdefinierten Besprechungseinladungen im Skype for Business Online Admin Center](media/o365-powershell-meeting-invitation.png)
  
<span data-ttu-id="aa873-p113">Mit diesen Einstellungen können Sie Besprechungseinladungen eine gewisse persönliche Note und Professionalität verleihen. Besprechungskonfigurationseinstellungen erlauben Ihnen jedoch mehr, als einfach benutzerdefinierte Besprechungseinladungen zu erstellen. Besprechungen ermöglichen standardmäßig beispielsweise Folgendes:</span><span class="sxs-lookup"><span data-stu-id="aa873-p113">With these settings, you can add a touch of personalization and professionalism to meeting invitations. However, there's more to meeting configuration settings than simply creating custom meeting invitations. For example, by default, meetings allow:</span></span>
  
- <span data-ttu-id="aa873-175">anonymen Benutzern, automatischen Zugang zu jeder Besprechung zu erhalten</span><span class="sxs-lookup"><span data-stu-id="aa873-175">Anonymous users to gain automatic entrance to each meeting.</span></span>
    
- <span data-ttu-id="aa873-176">Teilnehmern, die Besprechung aufzuzeichnen.</span><span class="sxs-lookup"><span data-stu-id="aa873-176">Attendees to record the meeting.</span></span>
    
- <span data-ttu-id="aa873-177">das Festlegen aller Benutzer in Ihrer Organisation als Referenten, wenn sie an der Besprechung teilnehmen.</span><span class="sxs-lookup"><span data-stu-id="aa873-177">All users from your organization to be designated as presenters when they join the meeting.</span></span>
    
<span data-ttu-id="aa873-p114">Diese Einstellungen sind im Skype for Business Online Admin Center nicht verfügbar. Sie können sie jedoch über Office 365 PowerShell steuern. Nachfolgend sehen Sie einen Befehl, der diese drei Einstellungen deaktiviert:</span><span class="sxs-lookup"><span data-stu-id="aa873-p114">These settings are not available from the Skype for Business Online Admin center. However, you can control them from Office 365 PowerShell. Here is a command that disables these three settings:</span></span>
  
```powershell
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $False -AllowConferenceRecording $False -DesignateAsPresenter "None"
```

> [!NOTE]
> <span data-ttu-id="aa873-181">Für diesen Befehl müssen Sie das [Skype for Business Online PowerShell-Modul](https://www.microsoft.com/download/details.aspx?id=39366) installieren.</span><span class="sxs-lookup"><span data-stu-id="aa873-181">This command requires that you install the [Skype for Business Online PowerShell Module ](https://www.microsoft.com/download/details.aspx?id=39366).</span></span> 
  
> [!TIP]
>  <span data-ttu-id="aa873-182">Die Interpretation dieses Office 365 PowerShell-Befehls ist:  Deaktivieren Sie für die Einstellungen für neue Skype for Business Online-Besprechungen (**Set-CsMeetingConfiguration**), die Möglichkeit, dass anonyme Benutzer automatischen Zugang zu Besprechungen erhalten (**-AdmitAnonymousUsersByDefault $False**), deaktivieren Sie die Möglichkeit, dass Teilnehmer Besprechungen aufzeichnen (**-AllowConferenceRecording $False**), und legen Sie nicht alle Benutzer aus Ihrer Organisation als Referenten fest ( **-DesignateAsPresenter "None"**).</span><span class="sxs-lookup"><span data-stu-id="aa873-182">The interpretation of this Office 365 PowerShell command is: For the settings for new Skype for Business Online meetings ( **Set-CsMeetingConfiguration** ), disable allowing anonymous users to gain automatic entrance to meetings ( **-AdmitAnonymousUsersByDefault $False** ), disable the ability for attendees to record meetings ( **-AllowConferenceRecording $False** ), and do not designate all users from your organization as presenters ( **-DesignateAsPresenter "None"** ).</span></span>
  
<span data-ttu-id="aa873-183">Wenn Sie Ihre Meinung ändern und diese Standardeinstellungen wiederherstellen möchten (alle aktiviert), führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="aa873-183">If you change your mind and want to restore these default settings (all of them enabled), run this command:</span></span>
  
```powershell
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $True -AllowConferenceRecording $True -DesignateAsPresenter "Company"
```

<span data-ttu-id="aa873-p115">Dies ist nur ein Beispiel. Es gibt weitere Beispiele, deshalb müssen Sie, als Office 365-Administrator, mit dem Ausführen von Office 365 PowerShell-Befehlen vertraut sein.</span><span class="sxs-lookup"><span data-stu-id="aa873-p115">This is just one example. There are others, which is why you, as an Office 365 administrator, need to be comfortable with running Office 365 PowerShell commands.</span></span>
  
## <a name="office-365-powershell-is-great-at-carrying-out-bulk-operations"></a><span data-ttu-id="aa873-186">Office 365 PowerShell überzeugt beim Ausführen von Massenoperationen</span><span class="sxs-lookup"><span data-stu-id="aa873-186">Office 365 PowerShell is great at carrying out bulk operations</span></span>

<span data-ttu-id="aa873-187">Historisch gesehen sind visuelle Schnittstellen wie das Microsoft 365 Admin Center besonders wertvoll, wenn Sie einen einzelnen Vorgang ausführen müssen.</span><span class="sxs-lookup"><span data-stu-id="aa873-187">Historically, visual interfaces like the Microsoft 365 admin center are most valuable when you have a single operation to perform.</span></span> <span data-ttu-id="aa873-188">Wenn Sie beispielsweise ein Benutzerkonto deaktivieren müssen, können Sie das Microsoft 365 Admin Center verwenden, um ein CheckBox-Steuerelement schnell zu finden und zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="aa873-188">For example, if you need to disable one user account, you can use the Microsoft 365 admin center to quickly locate and clear a checkbox.</span></span> <span data-ttu-id="aa873-189">Dies kann einfacher sein als einen ähnlichen Vorgang in Office 365 PowerShell durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="aa873-189">This can be simpler than performing a similar operation in Office 365 PowerShell.</span></span>
  
<span data-ttu-id="aa873-190">Wenn Sie jedoch viele Dinge oder einige ausgewählte Dinge in einer großen Menge anderer Dinge ändern müssen, ist das Microsoft 365 Admin Center möglicherweise nicht die beste Nutzung ihrer Zeit.</span><span class="sxs-lookup"><span data-stu-id="aa873-190">But if you have to change many things or some selected things within a large set of other things, the Microsoft 365 admin center might not be the best use of your time.</span></span> <span data-ttu-id="aa873-191">Wenn Sie beispielsweise das Präfix für Tausende von Telefonnummern ändern oder einen bestimmten Benutzer, Ken Myers, von all Ihren SharePoint Online Websites entfernen mussten, wie würden Sie dies im Microsoft 365 Admin Center tun?</span><span class="sxs-lookup"><span data-stu-id="aa873-191">For example, if you had to change the prefix on thousands of phone numbers or you needed to remove a specific user, Ken Myer, from all of your SharePoint Online sites, how would you do that in the Microsoft 365 admin center?</span></span>
  
<span data-ttu-id="aa873-192">Beim zweiten Beispiel haben Sie mehrere Hundert SharePoint Online-Standorte und wissen nicht einmal, bei welchen Ken Meyer ein Mitglied ist.</span><span class="sxs-lookup"><span data-stu-id="aa873-192">For the latter example, you have several hundred SharePoint Online sites and you don't know even know which ones of which Ken Meyer is a member.</span></span> <span data-ttu-id="aa873-193">Das bedeutet, dass Sie am Microsoft 365 Admin Center beginnen und dann dieses Verfahren für jeden Standort ausführen müssen:</span><span class="sxs-lookup"><span data-stu-id="aa873-193">That means you'll have to start at the Microsoft 365 admin center and then perform this procedure for each site:</span></span>
  
1. <span data-ttu-id="aa873-194">Klicken Sie auf die **URL** des Standorts.</span><span class="sxs-lookup"><span data-stu-id="aa873-194">Click the **URL** of the site.</span></span>
    
2. <span data-ttu-id="aa873-195">Klicken Sie im Feld **Websitesammlungs-Eigenschaften** auf den Link **Websiteadresse**, um die Website zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="aa873-195">In the **site collection properties** box, click the **Web Site Address** link to open the site.</span></span>
    
3. <span data-ttu-id="aa873-196">Klicken Sie auf der Website auf **Freigabe**.</span><span class="sxs-lookup"><span data-stu-id="aa873-196">On the site, click **Share**.</span></span>
    
4. <span data-ttu-id="aa873-197">Klicken Sie im Dialogfeld **Freigabe** auf den Link, der Ihnen alle Benutzer mit Berechtigungen für die Website zeigt:</span><span class="sxs-lookup"><span data-stu-id="aa873-197">In the **Share** dialog box click the link that shows you all the users who have permissions to the site:</span></span>
    
     ![Beispiel der Anzeige der Mitglieder einer SharePoint Online-Website im SharePoint Online Admin Center.](media/o365-powershell-view-permissions.png)
  
5. <span data-ttu-id="aa873-199">Klicken Sie im Dialogfeld **Freigegeben für** auf **Erweitert**.</span><span class="sxs-lookup"><span data-stu-id="aa873-199">In the **Shared With** dialog box, click **Advanced**.</span></span>
    
6. <span data-ttu-id="aa873-200">Führen Sie in der Liste der Benutzer einen Bildlauf nach unten zu Ken Myer durch, wählen Sie ihn aus (angenommen, dass er Berechtigungen für diese Website besitzt), und klicken Sie dann auf **Benutzerberechtigungen entfernen**.</span><span class="sxs-lookup"><span data-stu-id="aa873-200">Scroll down the list of users, find and select Ken Myer (assuming he has permissions to the site), and then click **Remove User Permissions**.</span></span>
    
<span data-ttu-id="aa873-201">Dies kann bei mehreren Hundert Seiten lange dauern.</span><span class="sxs-lookup"><span data-stu-id="aa873-201">This can take a long time for several hundred sites.</span></span>
  
<span data-ttu-id="aa873-202">Die Alternative besteht darin, Office 365 PowerShell und den folgenden Befehl zum Entfernen von Ken Myer von allen Standorten zu verwenden:</span><span class="sxs-lookup"><span data-stu-id="aa873-202">The alternative is to use Office 365 PowerShell and the following command to remove Ken Myer from all of your sites:</span></span>
  
```powershell
Get-SPOSite | ForEach {Remove-SPOUser -Site $_.Url -LoginName "kenmyer@litwareinc.com"}
```

> [!NOTE]
> <span data-ttu-id="aa873-203">Für diesen Befehl müssen Sie [eine Verbindung mit SharePoint Online PowerShell herstellen](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span><span class="sxs-lookup"><span data-stu-id="aa873-203">This command requires that you install the [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span> 
  
> [!TIP]
>  <span data-ttu-id="aa873-204">Die Interpretation dieses Office 365 PowerShell-Befehls ist: Alle SharePoint-Websites im aktuellen Office 365-Abonnement abrufen (**Get-SPOSite**) und Ken Meyer für jede Website aus der Liste der Benutzer mit Zugriffsberechtigung entfernen (**ForEach {Remove-SPOUser -Site $\_.Url -LoginName "kenmyer@litwareinc.com"}**)</span><span class="sxs-lookup"><span data-stu-id="aa873-204">The interpretation of this Office 365 PowerShell command is:  Get all of the SharePoint sites in the current Office 365 subscription ( **Get-SPOSite** ) and for each site, remove Ken Meyer from the list of users who can access it ( **ForEach {Remove-SPOUser -Site $\_.Url -LoginName "kenmyer@litwareinc.com"}** ).</span></span>
  
<span data-ttu-id="aa873-205">Da Office 365 angewiesen wird, Ken Meyer von jedem Standort, einschließlich derer, in denen er keinen Zugriff hat, zu entfernen, werden für die Standorte, an denen er derzeit nicht über Zugriff verfügt, Fehlermeldungen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="aa873-205">Because we are telling Office 365 to remove Ken Meyer from every site, including those in which he does not have access, the display of this command will show errors for those sites in which he does not currently have access.</span></span> <span data-ttu-id="aa873-206">Wir können eine zusätzliche Bedingung für diesen Befehl verwenden, um Ken Meyer nur von den Standorten zu entfernen, an denen er in der Anmeldeliste vorhanden ist, die aufgeführten Fehler richten jedoch an den Standorten selbst keinen Schaden an.</span><span class="sxs-lookup"><span data-stu-id="aa873-206">We can use an additional condition on this command to remove Key Meyer only from the sites that have him in their login list, but the listed errors cause no harm to the sites themselves.</span></span> <span data-ttu-id="aa873-207">Dieser Befehl kann einige Minuten dauern, bis Hunderte von Websites ausgeführt werden, statt Stunden lang über das Microsoft 365 Admin Center zu arbeiten.</span><span class="sxs-lookup"><span data-stu-id="aa873-207">This command might take a few minutes to run against hundreds of sites, rather than hours of working through the Microsoft 365 admin center.</span></span>
  
<span data-ttu-id="aa873-p120">Nachfolgend finden Sie ein weiteres Beispiel für eine Massenoperation. Verwenden Sie diesen Befehl, um Bonnie Kearney, einen neuen SharePoint-Administrator, zu allen Standorten in der Organisation hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="aa873-p120">Here is another bulk operation example. Use this command to add Bonnie Kearney, a new SharePoint administrator, to all of the sites in the organization:</span></span>
  
```powershell
Get-SPOSite | ForEach {Add-SPOUser -Site $_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}
```

> [!TIP]
>  <span data-ttu-id="aa873-210">Die Interpretation dieses Office 365 PowerShell-Befehls ist: Alle SharePoint-Websites im aktuellen Office 365-Abonnement abrufen und den Anmeldenamen von Bonnie Kearney für jede Website zur Gruppe „Mitglieder" hinzufügen, um ihr Zugriff zu gewähren (**Each {Add-SPOUser -Site $\_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}**)</span><span class="sxs-lookup"><span data-stu-id="aa873-210">The interpretation of this Office 365 PowerShell command is:  Get all of the SharePoint sites in the current Office 365 subscription and for each site, allow Bonnie Kearney access by adding her login name to the Members group of the site ( **ForEach {Add-SPOUser -Site $\_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}** ).</span></span>
  
## <a name="office-365-powershell-is-great-at-filtering-data"></a><span data-ttu-id="aa873-211">Office 365 PowerShell eignet sich bestens zum Filtern von Daten</span><span class="sxs-lookup"><span data-stu-id="aa873-211">Office 365 PowerShell is great at filtering data</span></span>

<span data-ttu-id="aa873-212">Das Microsoft 365 Admin Center bietet verschiedene Möglichkeiten zum Filtern Ihrer Daten, um eine gezielte Teilmenge von Informationen schnell und einfach zu finden.</span><span class="sxs-lookup"><span data-stu-id="aa873-212">The Microsoft 365 admin center provides several different ways to filter your data to quickly and easily locate a targeted subset of information.</span></span> <span data-ttu-id="aa873-213">Mit Exchange können Sie beispielsweise leicht nach praktisch jeder Eigenschaft eines Benutzerpostfachs filtern.</span><span class="sxs-lookup"><span data-stu-id="aa873-213">For example, Exchange makes it easy to filter on practically any property of a user mailbox.</span></span> <span data-ttu-id="aa873-214">Nachfolgend sehen Sie beispielsweise die Liste der Postfächer aller Benutzer, die in Bloomington wohnen:</span><span class="sxs-lookup"><span data-stu-id="aa873-214">For example, here is the list of mailboxes for all the users who live in the city of Bloomington:</span></span>
  
![Beispiel für eine erweiterte Suche im Microsoft 365 Admin Center für die Liste der Postfächer für alle Benutzer, die in der Stadt Bloomington Leben.](media/o365-powershell-advanced-search.png)
  
<span data-ttu-id="aa873-p122">Im Exchange Admin Center können Sie auch Filterkriterien kombinieren. Sie können beispielsweise nach den Postfächern aller in Bloomington lebenden Personen suchen, die zudem in der Finanzabteilung arbeiten.</span><span class="sxs-lookup"><span data-stu-id="aa873-p122">The Exchange Admin center also lets you combine filter criteria. For example, you can find the mailboxes for all the people who live in Bloomington and who work in the Finance department.</span></span> 
  
<span data-ttu-id="aa873-p123">Es gibt jedoch Einschränkungen dafür, was mit dem Exchange Admin Center alles möglich ist. Vielleicht möchten Sie beispielsweise die Postfächer aller in Bloomington oder San Diego lebenden Personen suchen oder die Postfächer aller Personen, die nicht in Bloomington leben.</span><span class="sxs-lookup"><span data-stu-id="aa873-p123">However, there are limitations to what you can do in the Exchange Admin center. For example, maybe you'd like to find the mailboxes of people who live in Bloomington or San Diego, or the mailboxes for all the people who don't live in Bloomington.</span></span> 
  
<span data-ttu-id="aa873-220">Mit Office 365 PowerShell können Sie mit dem folgenen Befehl eine Liste der Postfächer aller in Bloomington oder San Diego lebenden Personen abrufen:</span><span class="sxs-lookup"><span data-stu-id="aa873-220">With Office 365 PowerShell, you can get a list of mailboxes for all the people who live in the cities of Bloomington or San Diego with this command:</span></span>
  
```powershell
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and ($_.City -eq "San Diego" -or $_.City -eq "Bloomington")} | Select DisplayName, City
```

<span data-ttu-id="aa873-221">Nachfolgend sehen Sie ein Beispiel der Anzeige:</span><span class="sxs-lookup"><span data-stu-id="aa873-221">Here is an example of the display:</span></span>
  
```powershell
DisplayName                              City
-----------                              ----
Alex Darrow                              San Diego
Bonnie Kearney                           San Diego
Julian Isla                              Bloomington
Rob Young                                Bloomington
```

> [!TIP]
>  <span data-ttu-id="aa873-222">Die Interpretation dieses Office 365 PowerShell-Befehls ist: Alle Benutzer im aktuellen Office 365-Abonnement abrufen, die ein Postfach in San Diego oder ein Postfach in Bloomington haben (**Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and ($\_.City -eq "San Diego" -or $\_.City -eq "Bloomington")}**), und für jeden dieser Benutzer jeweils Namen und Stadt anzeigen (**Select DisplayName, City**)</span><span class="sxs-lookup"><span data-stu-id="aa873-222">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription who have a mailbox in the cities of either San Diego or Bloomington ( **Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and ($\_.City -eq "San Diego" -or $\_.City -eq "Bloomington")}** ), then display the name and city for each ( **Select DisplayName, City** ).</span></span>
  
<span data-ttu-id="aa873-223">Verwenden Sie den folgenden Befehl, um alle Postfächer von Benutzern aufzuführen, die überall leben, nur nicht in Bloomington:</span><span class="sxs-lookup"><span data-stu-id="aa873-223">To list all the mailboxes for people who live anywhere except Bloomington, here is the command:</span></span>
  
```powershell
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and $_.City -ne "Bloomington"} | Select DisplayName, City
```

<span data-ttu-id="aa873-224">Nachfolgend sehen Sie ein Beispiel der Anzeige:</span><span class="sxs-lookup"><span data-stu-id="aa873-224">Here is an example of the display:</span></span>
  
```powershell
DisplayName                               City
-----------                               ----
MOD Administrator                         Redmond
Alex Darrow                               San Diego
Allie Bellew                              Bellevue
Anne Wallace                              Louisville
Aziz Hassouneh                            Cairo
Belinda Newman                            Charlotte
Bonnie Kearney                            San Diego
David Longmuir                            Waukesha
Denis Dehenne                             Birmingham
Garret Vargas                             Seattle
Garth Fort                                Tulsa
Janet Schorr                              Bellevue
```

> [!TIP]
>  <span data-ttu-id="aa873-225">Die Interpretation dieses Office 365 PowerShell-Befehls ist: Alle Benutzer im aktuellen Office 365-Abonnement abrufen, deren Postfach sich nicht in Bloomington befindet (**Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and $\_.City -ne "Bloomington"}**), und für jeden dieser Benutzer jeweils Namen und Stadt anzeigen</span><span class="sxs-lookup"><span data-stu-id="aa873-225">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription who have a mailbox not located in the city of Bloomington ( **Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and $\_.City -ne "Bloomington"}** ), then display the name and city for each.</span></span>
  
<span data-ttu-id="aa873-p124">Sie können auch Platzhalterzeichen in Ihren Office 365 PowerShell-Filtern verwenden, um eine Übereinstimmung mit einem Teil eines Namens zu suchen. Angenommen, Sie suchen nach einem Benutzerkonto, und Sie können sich nur daran erinnern, dass der Nachname Anderson oder vielleicht Henderson oder vielleicht aber auch Jorgenson war.</span><span class="sxs-lookup"><span data-stu-id="aa873-p124">You can also use wildcard characters in your Office 365 PowerShell filters to match part of a name. For example, suppose you're looking for a user account, and all you can remember is that their last name was Anderson, or maybe Henderson, or maybe it was Jorgenson.</span></span>
  
<span data-ttu-id="aa873-228">Sie können den Benutzer im Microsoft 365 Admin Center nachverfolgen, indem Sie das Such Tool verwenden und drei verschiedene Suchvorgänge ausführen:</span><span class="sxs-lookup"><span data-stu-id="aa873-228">You could track down that user in the Microsoft 365 admin center by using the search tool and carrying out three different searches:</span></span>
  
- <span data-ttu-id="aa873-229">Eine für  *Anderson*</span><span class="sxs-lookup"><span data-stu-id="aa873-229">One for  *Anderson*</span></span> 
    
- <span data-ttu-id="aa873-230">Eine für  *Henderson*</span><span class="sxs-lookup"><span data-stu-id="aa873-230">One for  *Henderson*</span></span> 
    
- <span data-ttu-id="aa873-231">Und eine für  *Jorgenson*</span><span class="sxs-lookup"><span data-stu-id="aa873-231">One for  *Jorgenson*</span></span> 
    
<span data-ttu-id="aa873-p125">Da alle drei Namen auf "son" enden, können Sie Office 365 PowerShell anweisen, alle Benutzer anzuzeigen, deren Name auf "son" endet. Hier ist der Befehl:</span><span class="sxs-lookup"><span data-stu-id="aa873-p125">Because all three of these names end in "son", you can tell Office 365 PowerShell to display all the users whose name ends in "son". Here is the command:</span></span>
  
```powershell
Get-User -Filter '{LastName -like "*son"}'
```

> [!TIP]
>  <span data-ttu-id="aa873-p126">Die Interpretation dieses Office 365 PowerShell-Befehls ist: Alle Benutzer im aktuellen Office 365-Abonnement abrufen, aber einen Filter verwenden, damit nur die Benutzer aufgeführt werden, deren Nachname auf "son" endet (**-Filter '{LastName -like "\*son"}'**). Das \* steht für einen beliebigen Satz von Zeichen, im Falle des Nachnamens der Benutzer um Buchstaben.</span><span class="sxs-lookup"><span data-stu-id="aa873-p126">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription, but use a filter that only lists the users whose last names end in "son" ( **-Filter '{LastName -like "\*son"}'** ). The \* stands for any set of characters, which are letters in the case of the user's last name.</span></span>
  
## <a name="office-365-powershell-makes-it-easy-to-print-or-save-data"></a><span data-ttu-id="aa873-236">Office 365 PowerShell erleichtert das Drucken oder Speichern von Daten</span><span class="sxs-lookup"><span data-stu-id="aa873-236">Office 365 PowerShell makes it easy to print or save data</span></span>

<span data-ttu-id="aa873-237">Im Microsoft 365 Admin Center können Sie Listen mit Daten anzeigen.</span><span class="sxs-lookup"><span data-stu-id="aa873-237">The Microsoft 365 admin center lets you view lists of data.</span></span> <span data-ttu-id="aa873-238">Nachfolgend sehen Sie ein Beispiel im Skype for Business Online Admin Center, bei dem eine Liste von Benutzern angezeigt wird, die für Skype for Business Online aktiviert wurden.</span><span class="sxs-lookup"><span data-stu-id="aa873-238">Here is an example of the Skype for Business Online Admin center displaying a list of users who have been enabled for Skype for Business Online:</span></span>
  
![Beispiel für das Skype for Business Online Admin Center, in dem eine Liste von Benutzern angezeigt wird, die für Skype for Business Online aktiviert wurden.](media/o365-powershell-lync-users.png)
  
<span data-ttu-id="aa873-240">Um diese Informationen in einer Datei zu speichern, müssen Sie sie kopieren und in ein Dokument oder in Excel einfügen.</span><span class="sxs-lookup"><span data-stu-id="aa873-240">To save that information to a file, you must copy and paste it into a document or Excel.</span></span> <span data-ttu-id="aa873-241">Für das Kopieren ist auf jeden Fall eine zusätzliche Formatierung erforderlich.</span><span class="sxs-lookup"><span data-stu-id="aa873-241">In either case, the copy might require additional formatting.</span></span> <span data-ttu-id="aa873-242">Darüber hinaus bietet das Microsoft 365 Admin Center keine Möglichkeit, die angezeigte Liste direkt zu drucken.</span><span class="sxs-lookup"><span data-stu-id="aa873-242">Additionally, the Microsoft 365 admin center does not provide a way to directly print the displayed list.</span></span>
  
<span data-ttu-id="aa873-p129">Glücklicherweise können Sie Office 365 PowerShell verwenden, um die Liste nicht nur anzuzeigen, sondern sie auch in einer Datei zu speichern, damit sie problemlos in Excel importiert werden kann. Nachfolgend sehen Sie einen Beispielbefehl, um Skype for Business Online-Benutzerdaten in einer CSV-Datei (durch Trennzeichen getrennte Datei) zu speichern, die einfach als Tabelle in ein Excel-Arbeitsblatt importiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="aa873-p129">Fortunately, you can use Office 365 PowerShell to not only display the list, but save it to a file that can be easily imported into Excel. Here is an example command to save Skype for Business Online user data to a comma-separated values (CSV) file, a file that can be easily imported as a table in an Excel worksheet:</span></span>
  
```powershell
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Export-Csv -Path "C:\Logs\SfBUsers.csv" -NoTypeInformation
```

<span data-ttu-id="aa873-245">Nachfolgend sehen Sie ein Beispiel der Anzeige:</span><span class="sxs-lookup"><span data-stu-id="aa873-245">Here is an example of the display:</span></span>
  
![Beispiel für eine Tabelle, die in ein Excel-Arbeitsblatt importiert wurde, mit Skype for Business Online-Benutzerdaten, die als CSV-Datei gespeichert wurden.](media/o365-powershell-data-in-excel.png)
  
> [!TIP]
>  <span data-ttu-id="aa873-247">Die Interpretation dieses Office 365 PowerShell-Befehls ist:  Alle Skype for Business Online-Benutzer im aktuellen Office 365-Abonnement abrufen (**Get-CsOnlineUser**), dabei nur den Benutzernamen, den UPN und den Standort abrufen (**Select DisplayName, UserPrincipalName, UsageLocation**) und anschließend diese Informationen in einer CSV-Datei unter „C:\\Logs\\SfBUsers.csv" speichern (**Export-Csv -Path "C:\\Logs\\SfBUsers.csv" -NoTypeInformation**)</span><span class="sxs-lookup"><span data-stu-id="aa873-247">The interpretation of this Office 365 PowerShell command is: Get all of the Skype for Business Online users in the current Office 365 subscription ( **Get-CsOnlineUser** ), obtain only the user name, UPN, and location ( **Select DisplayName, UserPrincipalName, UsageLocation** ), and then save that information in CSV file named C:\\Logs\\SfBUsers.csv ( **Export-Csv -Path "C:\\Logs\\SfBUsers.csv" -NoTypeInformation** ).</span></span>
  
<span data-ttu-id="aa873-p130">Sie können auch Optionen verwenden, um diese Liste als XML-Datei oder als HTML-Seite zu speichern. Mit zusätzlichen PowerShell-Befehlen könnten Sie die Datei direkt als Excel-Datei mit beliebigen benutzerdefinierten Formatierungen speichern.</span><span class="sxs-lookup"><span data-stu-id="aa873-p130">You can also use options to save this list as an XML file or as an HTML page. In fact, with additional PowerShell commands, you could save it directly as an Excel file, with any custom formatting you desire.</span></span> 
  
<span data-ttu-id="aa873-p131">Sie können die Ausgabe eines Office 365 PowerShell-Befehls, der eine Liste anzeigt, auch direkt an den Standarddrucker in Windows senden. Nachfolgend sehen Sie einen Beispielbefehl:</span><span class="sxs-lookup"><span data-stu-id="aa873-p131">You can also send the output of an Office 365 PowerShell command that displays a list directly to the default printer in Windows. Here is an example command:</span></span>
  
```powershell
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Out-Printer
```

<span data-ttu-id="aa873-252">Das gedruckte Dokument sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="aa873-252">Here's what your printed document will look like:</span></span>
  
![Beispiel eines gedruckten Dokuments, das die Ausgabe eines Office 365 PowerShell-Befehls war, der direkt an den Standarddrucker in Windows ausgegeben wurde.](media/o365-powershell-printed-data.png)
  
> [!TIP]
>  <span data-ttu-id="aa873-254">Die Interpretation dieses Office 365 PowerShell-Befehls ist:  Alle Skype for Business Online-Benutzer im aktuellen Office 365-Abonnement abrufen, nur den Benutzernamen, den Benutzer und den Ort abrufen und diese Informationen dann an den Standard-Windows-Drucker senden ( **Out-Printer** ).</span><span class="sxs-lookup"><span data-stu-id="aa873-254">The interpretation of this Office 365 PowerShell command is:  Get all of the Skype for Business Online users in the current Office 365 subscription, obtain only the user name, UPN, and location, and then send that information to the default Windows printer ( **Out-Printer** ).</span></span>
  
<span data-ttu-id="aa873-255">Das gedruckte Dokument weist dieselbe einfache Formatierung wie die Anzeige innerhalb des Office 365 PowerShell-Befehlsfensters auf, nachdem Sie jedoch einen Office 365 PowerShell-Befehl erstellt haben, um die gewünschten Informationen aufzulisten, fügen Sie nur **| Out-Printer** am Ende des Befehls hinzu, um eine Hardcopy zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="aa873-255">The printed document has the same simple formatting as the display within the Office 365 PowerShell command window, but once you have created an Office 365 PowerShell command to list what you need, you just add **| Out-Printer** to the end of the command to get a hard copy to work from.</span></span>
  
## <a name="office-365-powershell-lets-you-manage-across-server-products"></a><span data-ttu-id="aa873-256">Office 365 PowerShell ermöglicht eine Verwaltung über Serverprodukte hinweg</span><span class="sxs-lookup"><span data-stu-id="aa873-256">Office 365 PowerShell lets you manage across server products</span></span>

<span data-ttu-id="aa873-p132">Die unterschiedlichen Komponenten, aus denen Office 365 besteht, sind so konzipiert, dass sie zusammenarbeiten. Angenommen, Sie fügen einen neuen Benutzer zu Office 365 hinzu und geben dabei Informationen wie die Abteilung und Telefonnummer des Benutzers an. Diese Informationen stehen Ihnen anschließend zur Verfügung, wenn Sie mithilfe eines der Office 365-Serverprodukte auf die Benutzerinformationen zugreifen: Skype for Business Online, Exchange oder SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="aa873-p132">The different components that make up Office 365 are designed to work together. For example, suppose you add a new user to Office 365 and, when you do, you specify such information as the user's department and phone number. That information will then be available if you access the user's information using any of the Office 365 server products: Skype for Business Online, Exchange, or SharePoint Online.</span></span>
  
<span data-ttu-id="aa873-p133">Hierbei handelt es sich um allgemeine Informationen, die für die ganze Produktsuite gleich sind. Produktspezifische Informationen, wie die zu einem Exchange-Benutzerpostfach, sind in der Regel nicht in der gesamten Suite verfügbar. Wenn Sie beispielsweise wissen möchten, ob das Postfach eines Benutzers aktiviert ist oder nicht, sind diese Informationen nur im Exchange Admin Center verfügbar.</span><span class="sxs-lookup"><span data-stu-id="aa873-p133">But that's for common information that spans the suite of products. Product-specific information-for example, information about a user's Exchange mailbox-is typically not available across the suite. For example, if you want to know if a user's mailbox is enabled or not, that information is available only in the Exchange Admin center.</span></span> 
  
<span data-ttu-id="aa873-263">Angenommen, Sie möchten einen Bericht erstellen, in dem die folgenden Informationen für alle Benutzer enthalten sind:</span><span class="sxs-lookup"><span data-stu-id="aa873-263">Suppose you'd like to make a report that shows the following information for all your users:</span></span>
  
- <span data-ttu-id="aa873-264">Den Anzeigenamen des Benutzers</span><span class="sxs-lookup"><span data-stu-id="aa873-264">The user's display name</span></span>
    
- <span data-ttu-id="aa873-265">Ob der Benutzer für Office 365 lizenziert ist</span><span class="sxs-lookup"><span data-stu-id="aa873-265">Whether the user is licensed for Office 365</span></span>
    
- <span data-ttu-id="aa873-266">Ob das Exchange-Postfach des Benutzers aktiviert wurde</span><span class="sxs-lookup"><span data-stu-id="aa873-266">Whether the user's Exchange mailbox has been enabled</span></span>
    
- <span data-ttu-id="aa873-267">Ob der Benutzer für Skype for Business Online aktiviert ist</span><span class="sxs-lookup"><span data-stu-id="aa873-267">Whether the user is enabled for Skype for Business Online</span></span>
    
<span data-ttu-id="aa873-268">Sie können derzeit nicht das Microsoft 365 Admin Center verwenden, um einen solchen Bericht problemlos zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="aa873-268">You currently cannot use the Microsoft 365 admin center to easily produce such a report.</span></span> <span data-ttu-id="aa873-269">Stattdessen müssen Sie ein separates Dokument erstellen, um die Informationen wie ein Excel-Arbeitsblatt zu speichern, und alle Benutzernamen und Lizenzierungsinformationen aus dem Microsoft 365 Admin Center abrufen, Postfachinformationen aus dem Exchange Admin Center abrufen, Skype for Business Online-Informationen aus dem Skype for Business Online Admin Center und Sortieren und kombinieren diese Informationen.</span><span class="sxs-lookup"><span data-stu-id="aa873-269">Instead, you'll have to create a separate document to store the information, like an Excel worksheet, and get all the user names and licensing information from the Microsoft 365 admin center, get mailbox information from the Exchange Admin center, get Skype for Business Online information from the Skype for Business Online Admin center, and then collate and combine that information.</span></span>
  
<span data-ttu-id="aa873-270">Die Alternative besteht darin, ein Office 365 PowerShell-Skript zu verwenden, das diesen Bericht für Sie kompiliert.</span><span class="sxs-lookup"><span data-stu-id="aa873-270">The alternative is to use an Office 365 PowerShell script to compile that report for you.</span></span>
  
<span data-ttu-id="aa873-p135">Das folgende Beispielskript ist komplizierter als die bisher in diesem Artikel gezeigten Befehle. Es zeigt jedoch das Potenzial der Verwendung von Office 365 PowerShell zum Erstellen von Ansichten von Informationen, die andernfalls nur sehr schwer zu erstellen sind. Nachfolgend sehen Sie das Skript, das die erforderliche Liste kompilieren und anzeigen kann:</span><span class="sxs-lookup"><span data-stu-id="aa873-p135">The following example script is more complicated than the commands you have seen so far in this article. But, it shows the potential of using Office 365 PowerShell to create views of information that are very difficult to do otherwise. Here is the script that can compile and display the needed list:</span></span>
  
```powershell
$x = Get-MsolUser

foreach ($i in $x)
    {
      $y = Get-Mailbox -Identity $i.UserPrincipalName
      $i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled

      $y = Get-CsOnlineUser -Identity $i.UserPrincipalName
      $i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled
    }

$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB
```

<span data-ttu-id="aa873-274">Nachfolgend sehen Sie ein Beispiel der Anzeige:</span><span class="sxs-lookup"><span data-stu-id="aa873-274">Here is an example of the display:</span></span>
  
```powershell
DisplayName             IsLicensed   IsMailboxEnabled   EnabledForSfB
-----------             ----------   ----------------   --------------
Bonnie Kearney          True         True               True
Fabrice Canel           True         True               True
Brian Johnson           False        True               False
Anne Wallace            True         True               True
Alex Darrow             True         True               True
David Longmuir          True         True               True
Katy Jordan             False        True               False
Molly Dempsey           False        True               False
```

<span data-ttu-id="aa873-275">Die Interpretation dieses Office 365 PowerShell-Skripts ist:</span><span class="sxs-lookup"><span data-stu-id="aa873-275">The interpretation of this Office 365 PowerShell script is:</span></span>  
- <span data-ttu-id="aa873-276">Alle Benutzer im aktuellen Office 365-Abonnement abrufen und die Informationen in einer Variablen mit dem Namen "$x" speichern (**$x = Get-MsolUser**).</span><span class="sxs-lookup"><span data-stu-id="aa873-276">Get all of the users in the current Office 365 subscription and store the information in a variable named $x ( **$x = Get-MsolUser** ).</span></span>
- <span data-ttu-id="aa873-277">Eine Schleife starten, die über alle Benutzer in der Variablen mit dem Namen $x ausgeführt wird (**foreach ($i in $x)**).</span><span class="sxs-lookup"><span data-stu-id="aa873-277">Start a loop that runs over all the users in the variable named $x ( **foreach ($i in $x)** ).</span></span>  
- <span data-ttu-id="aa873-278">Eine Variable mit dem Namen $y definieren und die Postfachinformationen des Benutzers darin speichern (**$y = Get-Mailbox -Identity $i.UserPrincipalName**).</span><span class="sxs-lookup"><span data-stu-id="aa873-278">Define a variable named $y and store the user's mailbox information in it ( **$y = Get-Mailbox -Identity $i.UserPrincipalName** ).</span></span>
- <span data-ttu-id="aa873-279">Eine neue Eigenschaft zu den Benutzerinformationen mit dem Namen IsMailBoxEnabled hinzufügen und diese als Wert der IsMailBoxEnabled-Eigenschaft des Benutzerpostfachs hinzufügen (**$i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled**).</span><span class="sxs-lookup"><span data-stu-id="aa873-279">Add a new property to the user information named IsMailBoxEnabled and set it to the value of the IsMailBoxEnabled property of the user's mailbox ( **$i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled** ).</span></span>
- <span data-ttu-id="aa873-280">Eine Variable mit dem Namen $y definieren und die Skype for Business Online-Informationen des Benutzers darin speichern (**$y = Get-CsOnlineUser -Identity $i.UserPrincipalName**).</span><span class="sxs-lookup"><span data-stu-id="aa873-280">Define a variable named $y and store the user's Skype for Business Online information in it ( **$y = Get-CsOnlineUser -Identity $i.UserPrincipalName** ).</span></span>
- <span data-ttu-id="aa873-281">Eine neue Eigenschaft mit dem Namen EnabledForSfB zu den Benutzerinformationen hinzufügen und diese auf den Wert der Enabled-Eigenschaft der Skype_for_Business_Online-Informationen des Benutzers festlegen (**$i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled**).</span><span class="sxs-lookup"><span data-stu-id="aa873-281">Add a new property to the user information named EnabledForSfB and set it to the value of the Enabled property of the user's Skype for Business Online information ( **$i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled** ).</span></span>
- <span data-ttu-id="aa873-282">Die Benutzerliste anzeigen, dabei aber jeweils nur den Namen, den Lizenzstatus und die beiden neuen Eigenschaften einschließen, die angeben, ob das Postfach aktiviert ist und ob der jeweilige Benutzer für Skype for Business Online aktiviert ist (**$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB**)</span><span class="sxs-lookup"><span data-stu-id="aa873-282">Display the list of users, but include only their name, whether they are licensed, and the two new properties that indicate whether their mailbox is enabled and whether they are enabled for Skype for Business Online ( **$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB** ).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="aa873-283">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="aa873-283">See also</span></span>

[<span data-ttu-id="aa873-284">Erste Schritte mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="aa873-284">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="aa873-285">Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="aa873-285">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="aa873-286">Verwenden der Windows PowerShell zum Erstellen von Berichten in Office 365</span><span class="sxs-lookup"><span data-stu-id="aa873-286">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)

