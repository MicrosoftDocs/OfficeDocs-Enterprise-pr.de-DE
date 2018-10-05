---
title: Beheben von Problemen bei der Verzeichnissynchronisierung für Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: Beschreibt häufige Ursachen von Problemen mit der verzeichnissynchronisierung in Office 365 und bietet eine Reihe neuer Methoden Problembehebung und beheben Sie diese.
ms.openlocfilehash: a1ccf7aa8c6d450cdd3d658ef0bc8d9ed6d25753
ms.sourcegitcommit: 6a4611bb474c783efd361890fe6f41c26c5aeeb3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2018
ms.locfileid: "25405128"
---
# <a name="fixing-problems-with-directory-synchronization-for-office-365"></a><span data-ttu-id="3e11a-103">Beheben von Problemen bei der Verzeichnissynchronisierung für Office 365</span><span class="sxs-lookup"><span data-stu-id="3e11a-103">Fixing problems with directory synchronization for Office 365</span></span>

<span data-ttu-id="3e11a-p101">Mit der verzeichnissynchronisierung können Sie weiterhin Verwalten von Benutzern und Gruppen: lokal und Ergänzungen hinzufügen, löschen und Änderungen in die Cloud zu synchronisieren. Aber Setup ein wenig kompliziert wird, und es manchmal schwierig sein kann, die Quelle der Probleme zu identifizieren. Wir haben die Ressourcen, die Ihnen bei der Ermittlung möglicher Probleme zu identifizieren und beheben Sie sie.</span><span class="sxs-lookup"><span data-stu-id="3e11a-p101">With directory synchronization, you can continue to manage users and groups on-premises and synchronize additions, deletions, and changes to the cloud. But setup is a little complicated and it can sometimes be difficult to identify the source of problems. We have resources to help you identify potential issues and fix them.</span></span>
  
## <a name="how-do-i-know-if-something-is-wrong"></a><span data-ttu-id="3e11a-107">Wie weiß ich, wenn etwas falsch ist?</span><span class="sxs-lookup"><span data-stu-id="3e11a-107">How do I know if something is wrong?</span></span>

<span data-ttu-id="3e11a-108">Der erste Hinweis darauf, dass etwas falsch ist ist, wenn die Kachel Dirsync-Status in Office 365 Administrationscenter gibt an, dass ein Fehler auftritt:</span><span class="sxs-lookup"><span data-stu-id="3e11a-108">The first indication that something is wrong is when the DirSync Status tile in the Office 365 admin center indicates there is a problem:</span></span>
  
![Der Status der Dirsync-Kachel im Admin Center – Vorschau](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
<span data-ttu-id="3e11a-p102">Sie erhalten auch eine e-Mail-Nachrichten (um die alternative e-Mail und Ihre e-Mails Admin) von Office 365, die angibt, dass es sich bei Ihrem Mandanten verzeichnissynchronisierungsfehlern festgestellt wurden. Weitere Informationen finden Sie unter [Identifizieren von verzeichnissynchronisierungsfehlern in Office 365](identify-directory-synchronization-errors.md).</span><span class="sxs-lookup"><span data-stu-id="3e11a-p102">You will also receive a mail (to the alternate email and to your admin email) from Office 365 that indicates your tenant has encountered directory synchronization errors. For details see [Identify directory synchronization errors in Office 365](identify-directory-synchronization-errors.md).</span></span>
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a><span data-ttu-id="3e11a-112">Wie erhalte ich das Tool Azure Active Directory verbinden?</span><span class="sxs-lookup"><span data-stu-id="3e11a-112">How do I get Azure Active Directory Connect tool?</span></span>

<span data-ttu-id="3e11a-p103">Navigieren Sie in der Office 365-Verwaltungskonsole zu \*\* Benutzer \*\* \> **aktive Benutzer**. Klicken Sie auf das Menü **mehr** und aktivieren Sie **verzeichnissynchronisierung**.</span><span class="sxs-lookup"><span data-stu-id="3e11a-p103">In the Office 365 admin center, navigate to \*\* Users \*\* \> **Active users**. Click the **More** menu and select **Directory synchronization**.</span></span> 
  
![Wählen Sie im Menü Weitere Directory-Synchronisierung](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
<span data-ttu-id="3e11a-116">Navigieren Sie in der alten Office 365-Verwaltungskonsole zu **Benutzer** \> **Aktive Benutzer**, und wählen **Einrichten** , klicken Sie neben **Active Directory-Synchronisierung**.</span><span class="sxs-lookup"><span data-stu-id="3e11a-116">In the old Office 365 admin center, navigate to **USERS** \> **Active Users**, and select **Set up** next to **Active Directory synchronization**.</span></span> 
  
![Wählen Sie Set up neben Active Directory-Synchronisierung](media/bd95492b-d65e-4072-a6ee-e562f5f566c3.png)
  
<span data-ttu-id="3e11a-118">Befolgen Sie die [Anweisungen des Assistenten](set-up-directory-synchronization.md) zum Herunterladen des Azure Active Directory verbinden.</span><span class="sxs-lookup"><span data-stu-id="3e11a-118">Follow the [instructions in the wizard](set-up-directory-synchronization.md) to download Azure AD Connect.</span></span> 
  
<span data-ttu-id="3e11a-119">Wenn Sie noch Azure Active Directory-Synchronisierung (DirSync) verwenden, sehen Sie sich [Behandlung von Azure Active Directory-Synchronisierungstool Installations- und Fehlermeldungen in Office 365 Konfigurations-Assistenten für](https://go.microsoft.com/fwlink/p/?LinkId=396717) Informationen zu den Systemanforderungen installieren Dirsync, den dazu benötigten Berechtigungen und wie häufige Fehler behoben.</span><span class="sxs-lookup"><span data-stu-id="3e11a-119">If you are still using Azure Active Directory Sync (DirSync), take a look at [How to troubleshoot Azure Active Directory Sync Tool installation and Configuration Wizard error messages in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) for information about the system requirements to install dirsync, the permissions you need, and how to troubleshoot common errors.</span></span> 
  
<span data-ttu-id="3e11a-120">Um auf Azure AD-Verbinden von Azure Active Directory-Synchronisierung zu aktualisieren, finden Sie unter [den Upgradeanweisungen](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span><span class="sxs-lookup"><span data-stu-id="3e11a-120">To update from Azure Active Directory Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-office-365"></a><span data-ttu-id="3e11a-121">Beheben von allgemeinen Ursachen für Probleme mit der verzeichnissynchronisierung in Office 365</span><span class="sxs-lookup"><span data-stu-id="3e11a-121">Resolving common causes of problems with directory synchronization in Office 365</span></span>

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a><span data-ttu-id="3e11a-122">**Synchronisierte Objekte werden nicht angezeigt oder Aktualisieren von online, oder ich erhalte Synchronisierung Fehlerberichte aus dem Dienst.**</span><span class="sxs-lookup"><span data-stu-id="3e11a-122">**Synchronized objects aren't appearing or updating online, or I'm getting synchronization error reports from the Service.**</span></span>

- [<span data-ttu-id="3e11a-123">Identität Synchronisierung und Duplikat Attribut resiliency</span><span class="sxs-lookup"><span data-stu-id="3e11a-123">Identity synchronization and duplicate attribute resiliency</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=798300)

### <a name="i-have-an-alert-in-the-office-365-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a><span data-ttu-id="3e11a-124">**Ich haben eine Benachrichtigung in Office 365 Administrationscenter oder erhalte automatisierten e-Mails, dass ein aktueller Synchronisierungsereignis wurde nicht**</span><span class="sxs-lookup"><span data-stu-id="3e11a-124">**I have an alert in the Office 365 admin center, or am receiving automated emails that there hasn't been a recent synchronization event**</span></span>
- [<span data-ttu-id="3e11a-125">Behandeln von Verbindungsproblemen mit Azure Active Directory verbinden</span><span class="sxs-lookup"><span data-stu-id="3e11a-125">Troubleshoot connectivity issues with Azure AD Connect</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820597)
- [<span data-ttu-id="3e11a-126">Azure Active Directory verbinden Konten und Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="3e11a-126">Azure AD Connect Accounts and permissions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [<span data-ttu-id="3e11a-127">Azure Active Directory verbinden Sync: Gewusst wie: Verwalten des Azure AD-Dienstkontos</span><span class="sxs-lookup"><span data-stu-id="3e11a-127">Azure AD Connect sync: How to manage the Azure AD service account</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820599)
- [<span data-ttu-id="3e11a-128">Directory-Synchronisierung mit Azure Active Directory reagiert oder Sie sind darauf hingewiesen, dass Sync in mehr als einen Tag registriert noch nicht</span><span class="sxs-lookup"><span data-stu-id="3e11a-128">Directory synchronization to Azure Active Directory stops or you're warned that sync hasn't registered in more than a day</span></span>](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-office-365-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a><span data-ttu-id="3e11a-129">**Kennworthashes sind nicht synchronisiert, oder eine Warnung im Office 365 Administrationscenter, dass eine zuletzt verwendete Kennwort Hash Synchronisierung wurde nicht immer unerwünschte**</span><span class="sxs-lookup"><span data-stu-id="3e11a-129">**Password hashes aren't synchronizing, or I'm seeing an alert in the Office 365 admin center that there hasn't been a recent password hash synchronization**</span></span>
- [<span data-ttu-id="3e11a-130">Implementieren von Hash kennwortsynchronisierung mit Azure AD-Connect-Synchronisierung</span><span class="sxs-lookup"><span data-stu-id="3e11a-130">Implementing password hash synchronization with Azure AD Connect sync</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a><span data-ttu-id="3e11a-131">**Ich bin eine Benachrichtigung angezeigt, die Objekt-Kontingent überschritten**</span><span class="sxs-lookup"><span data-stu-id="3e11a-131">**I'm seeing an alert that Object quota exceeded**</span></span>
- <span data-ttu-id="3e11a-p104">Wir haben ein Kontingent integrierten-Objekts zum Schutz des Diensts. Wenn Sie zu viele Objekte in Ihrem Verzeichnis aus, die mit Office 365 synchronisiert werden müssen haben, müssen Sie auf [Kontakt für Business-Produkte unterstützen](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) Ihr Kontingent zu erhöhen.</span><span class="sxs-lookup"><span data-stu-id="3e11a-p104">We have a built-in object quota to help protect the service. If you have too many objects in your directory that need to sync to Office 365, you'll have to [Contact support for business products](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) to increase your quota.</span></span>

### <a name="i-need-to-know-which-attributes-are-synchronized"></a><span data-ttu-id="3e11a-134">**Ich möchte wissen, welche Attribute synchronisiert sind**</span><span class="sxs-lookup"><span data-stu-id="3e11a-134">**I need to know which attributes are synchronized**</span></span>
- <span data-ttu-id="3e11a-135">Finden Sie eine Liste aller Attribute, die zwischen lokalen und Cloud [hier rechts](https://go.microsoft.com/fwlink/p/?LinkId=396719)synchronisiert werden.</span><span class="sxs-lookup"><span data-stu-id="3e11a-135">You can find a list of all the attributes that are synced between on-premises and the cloud [right here](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a><span data-ttu-id="3e11a-136">**Ich kann nicht verwalten oder Entfernen von Objekten, die in der Cloud synchronisiert wurden**</span><span class="sxs-lookup"><span data-stu-id="3e11a-136">**I can't manage or remove objects that were synchronized to the cloud**</span></span>
- <span data-ttu-id="3e11a-p105">Sind Sie bereit, die Objekte in der Cloud nur verwalten? Oder ein Objekt, das lokale gelöscht wurde, aber in der Cloud steckt? Sehen Sie sich diese [Problembehandlung bei Fehlern während der Synchronisierung](https://go.microsoft.com/fwlink/p/?linkid=842044) und [Artikel zu unterstützen](https://go.microsoft.com/fwlink/p/?LinkId=396720) , Hinweise zum Beheben dieser Probleme an.</span><span class="sxs-lookup"><span data-stu-id="3e11a-p105">Are you ready to manage objects in the cloud only? Or is there an object that was deleted on-premises, but is stuck in the cloud? Take a look at this [Troubleshooting Errors during synchronization](https://go.microsoft.com/fwlink/p/?linkid=842044) and [support article](https://go.microsoft.com/fwlink/p/?LinkId=396720) for guidance on how to resolve these issues.</span></span>

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a><span data-ttu-id="3e11a-140">**Ich habe die Fehlermeldung bekommen, dass mein Unternehmen die Anzahl der synchronisierbaren Objekte überschritten hat**</span><span class="sxs-lookup"><span data-stu-id="3e11a-140">**I got an error message that my company has exceeded the number of objects that can be synchronized**</span></span>
- <span data-ttu-id="3e11a-141">Weitere Informationen zu diesem Thema [hier](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span><span class="sxs-lookup"><span data-stu-id="3e11a-141">You can read more about this issue [here](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span></span>
   
## <a name="other-resources"></a><span data-ttu-id="3e11a-142">Weitere Ressourcen</span><span class="sxs-lookup"><span data-stu-id="3e11a-142">Other resources</span></span>

- [<span data-ttu-id="3e11a-143">Skript zum Beheben von doppelten Benutzerprinzipalnamen</span><span class="sxs-lookup"><span data-stu-id="3e11a-143">Script to fix duplicate user principal names</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [<span data-ttu-id="3e11a-144">Vorbereiten eine nicht-routingfähigen Domäne (beispielsweise Local Domäne) für die verzeichnissynchronisierung</span><span class="sxs-lookup"><span data-stu-id="3e11a-144">How to prepare a non-routable domain (such as .local domain) for directory synchronization</span></span>](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [<span data-ttu-id="3e11a-145">Skript zum zählen insgesamt synchronisierte Objekte</span><span class="sxs-lookup"><span data-stu-id="3e11a-145">Script to count total synchronized objects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [<span data-ttu-id="3e11a-146">Problembehebung AD FS 2.0</span><span class="sxs-lookup"><span data-stu-id="3e11a-146">Troubleshoot AD FS 2.0</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [<span data-ttu-id="3e11a-147">Verwenden von PowerShell, DisplayName-Attribute für e-Mail-aktivierte Gruppen zu beheben.</span><span class="sxs-lookup"><span data-stu-id="3e11a-147">Use PowerShell to fix empty DisplayName attributes for mail-enabled groups</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [<span data-ttu-id="3e11a-148">Verwenden von PowerShell doppelte UPN beheben</span><span class="sxs-lookup"><span data-stu-id="3e11a-148">Use PowerShell to fix duplicate UPN</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [<span data-ttu-id="3e11a-149">Verwenden von PowerShell, doppelte e-Mail-Adressen zu beheben.</span><span class="sxs-lookup"><span data-stu-id="3e11a-149">Use PowerShell to fix duplicate email addresses</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a><span data-ttu-id="3e11a-150">Diagnosetools</span><span class="sxs-lookup"><span data-stu-id="3e11a-150">Diagnostic tools</span></span>

<span data-ttu-id="3e11a-p106">[IDFix-Tool](prepare-directory-attributes-for-synch-with-idfix.md) wird verwendet, um die Suche und Wartung der Identitätsobjekten und der zugehörigen Attribute in einer lokalen Active Directory-Umgebung im Rahmen der Vorbereitung für die Migration zu Office 365 ausführen. IDFix ist für die Active Directory-Administratoren für DirSync mit Office 365-Dienst verantwortlich vorgesehen.</span><span class="sxs-lookup"><span data-stu-id="3e11a-p106">[IDFix tool](prepare-directory-attributes-for-synch-with-idfix.md) is used to perform discovery and remediation of identity objects and their attributes in an on-premises Active Directory environment in preparation for migration to Office 365. IDFix is intended for the Active Directory administrators responsible for DirSync with the Office 365 service.</span></span> 

<span data-ttu-id="3e11a-153">[Laden Sie das IDFix-Tool](https://go.microsoft.com/fwlink/p/?LinkId=396718) , aus dem Microsoft Downloadcenter.</span><span class="sxs-lookup"><span data-stu-id="3e11a-153">[Download the IDFix tool](https://go.microsoft.com/fwlink/p/?LinkId=396718) from the Microsoft download center.</span></span>