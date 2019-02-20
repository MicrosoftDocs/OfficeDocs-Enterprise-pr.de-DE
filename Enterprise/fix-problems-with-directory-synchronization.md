---
title: Beheben von Problemen bei der Verzeichnissynchronisierung für Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: Beschreibt häufige Ursachen von Problemen mit der Verzeichnissynchronisierung in Office 365 und bietet einige Methoden zur Problembehandlung und-Lösung.
ms.openlocfilehash: e83ca495ca96ac41fb2f79775c3d5970a6b538fb
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085394"
---
# <a name="fixing-problems-with-directory-synchronization-for-office-365"></a><span data-ttu-id="4d624-103">Beheben von Problemen bei der Verzeichnissynchronisierung für Office 365</span><span class="sxs-lookup"><span data-stu-id="4d624-103">Fixing problems with directory synchronization for Office 365</span></span>

<span data-ttu-id="4d624-p101">Mit der Verzeichnissynchronisierung können Sie weiterhin Benutzer und Gruppen lokal verwalten und Hinzufügungen, Löschungen und Änderungen an der Cloud synchronisieren. Das Setup ist jedoch etwas komplizierter, und es kann manchmal schwierig sein, die Ursache für Probleme zu identifizieren. Wir haben Ressourcen, die Ihnen helfen, potenzielle Probleme zu identifizieren und zu beheben.</span><span class="sxs-lookup"><span data-stu-id="4d624-p101">With directory synchronization, you can continue to manage users and groups on-premises and synchronize additions, deletions, and changes to the cloud. But setup is a little complicated and it can sometimes be difficult to identify the source of problems. We have resources to help you identify potential issues and fix them.</span></span>
  
## <a name="how-do-i-know-if-something-is-wrong"></a><span data-ttu-id="4d624-107">Woran erkenne ich, ob etwas falsch ist?</span><span class="sxs-lookup"><span data-stu-id="4d624-107">How do I know if something is wrong?</span></span>

<span data-ttu-id="4d624-108">Der erste Hinweis darauf, dass etwas falsch ist, ist, wenn die dirSync-Status Kachel im Office 365 Admin Center ein Problem angibt:</span><span class="sxs-lookup"><span data-stu-id="4d624-108">The first indication that something is wrong is when the DirSync Status tile in the Office 365 admin center indicates there is a problem:</span></span>
  
![Die dirSync-Status Kachel in der Admin Center-Vorschau](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
<span data-ttu-id="4d624-p102">Sie erhalten auch eine e-Mail (an die Alternative e-Mail und an Ihre Administrator-e-Mail) von Office 365, die angibt, dass Ihr Mandant Verzeichnis Synchronisierungsfehler festgestellt hat. Weitere Informationen finden Sie unter [Identifizieren von Verzeichnis Synchronisierungsfehlern in Office 365](identify-directory-synchronization-errors.md).</span><span class="sxs-lookup"><span data-stu-id="4d624-p102">You will also receive a mail (to the alternate email and to your admin email) from Office 365 that indicates your tenant has encountered directory synchronization errors. For details see [Identify directory synchronization errors in Office 365](identify-directory-synchronization-errors.md).</span></span>
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a><span data-ttu-id="4d624-112">Wie erhalte ich das Azure Active Directory Connect-Tool?</span><span class="sxs-lookup"><span data-stu-id="4d624-112">How do I get Azure Active Directory Connect tool?</span></span>

<span data-ttu-id="4d624-p103">navigieren sie im Office 365 admin center zu \* \* users \* \* \> **Active users**. Klicken Sie auf das Menü **Weitere** , und wählen Sie **Verzeichnissynchronisierung**aus.</span><span class="sxs-lookup"><span data-stu-id="4d624-p103">In the Office 365 admin center, navigate to \*\* Users \*\* \> **Active users**. Click the **More** menu and select **Directory synchronization**.</span></span> 
  
![Wählen Sie im Menü mehr die Option Verzeichnissynchronisierung aus.](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
<span data-ttu-id="4d624-116">navigieren sie im alten Office 365 admin center zu **benutzer** \> , die **aktive benutzer**sind, und wählen sie neben **active Directory-synchronisierung** **einrichten** aus.</span><span class="sxs-lookup"><span data-stu-id="4d624-116">In the old Office 365 admin center, navigate to **USERS** \> **Active Users**, and select **Set up** next to **Active Directory synchronization**.</span></span> 
  
![Wählen Sie einrichten neben Active Directory-Synchronisierung](media/bd95492b-d65e-4072-a6ee-e562f5f566c3.png)
  
<span data-ttu-id="4d624-118">Folgen Sie den [Anweisungen des Assistenten](set-up-directory-synchronization.md) , um Azure AD Connect herunterzuladen.</span><span class="sxs-lookup"><span data-stu-id="4d624-118">Follow the [instructions in the wizard](set-up-directory-synchronization.md) to download Azure AD Connect.</span></span> 
  
<span data-ttu-id="4d624-119">Wenn Sie weiterhin Azure Active Directory-Synchronisierung (dirSync) verwenden, sehen Sie sich die [Problembehandlung bei Azure Active Directory Sync Tool-Installations-und Konfigurations-Assistenten Fehlermeldungen in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) an, um Informationen zu den Systemanforderungen für die Installation zu erhalten. Dirsync, die erforderlichen Berechtigungen und die Behandlung häufig auftretender Fehler.</span><span class="sxs-lookup"><span data-stu-id="4d624-119">If you are still using Azure Active Directory Sync (DirSync), take a look at [How to troubleshoot Azure Active Directory Sync Tool installation and Configuration Wizard error messages in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) for information about the system requirements to install dirsync, the permissions you need, and how to troubleshoot common errors.</span></span> 
  
<span data-ttu-id="4d624-120">Informationen zum Aktualisieren von Azure Active Directory-Synchronisierung mit Azure AD Connect finden Sie in [den Anweisungen zum Upgrade](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span><span class="sxs-lookup"><span data-stu-id="4d624-120">To update from Azure Active Directory Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-office-365"></a><span data-ttu-id="4d624-121">Beheben häufiger Ursachen von Problemen mit der Verzeichnissynchronisierung in Office 365</span><span class="sxs-lookup"><span data-stu-id="4d624-121">Resolving common causes of problems with directory synchronization in Office 365</span></span>

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a><span data-ttu-id="4d624-122">**Synchronisierte Objekte werden nicht online angezeigt oder aktualisiert, oder ich erhalte Synchronisierungsfehler Berichte vom Dienst.**</span><span class="sxs-lookup"><span data-stu-id="4d624-122">**Synchronized objects aren't appearing or updating online, or I'm getting synchronization error reports from the Service.**</span></span>

- [<span data-ttu-id="4d624-123">Identitätssynchronisierung und doppelte Attribut Ausfallsicherheit</span><span class="sxs-lookup"><span data-stu-id="4d624-123">Identity synchronization and duplicate attribute resiliency</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-office-365-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a><span data-ttu-id="4d624-124">**Ich habe eine Warnung im Office 365 Admin Center oder erhalte automatisierte e-Mails, dass kein neues Synchronisierungsereignis vorliegt.**</span><span class="sxs-lookup"><span data-stu-id="4d624-124">**I have an alert in the Office 365 admin center, or am receiving automated emails that there hasn't been a recent synchronization event**</span></span>
- [<span data-ttu-id="4d624-125">Beheben von Verbindungsproblemen mit Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="4d624-125">Troubleshoot connectivity issues with Azure AD Connect</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [<span data-ttu-id="4d624-126">Azure AD Connect-Konten und-Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="4d624-126">Azure AD Connect Accounts and permissions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [<span data-ttu-id="4d624-127">Azure AD Connect Sync: Verwalten des Azure AD-Dienstkontos</span><span class="sxs-lookup"><span data-stu-id="4d624-127">Azure AD Connect sync: How to manage the Azure AD service account</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [<span data-ttu-id="4d624-128">Die Verzeichnissynchronisierung mit Azure Active Directory wird angehalten, oder Sie werden gewarnt, dass die Synchronisierung seit mehr als einem Tag nicht registriert ist.</span><span class="sxs-lookup"><span data-stu-id="4d624-128">Directory synchronization to Azure Active Directory stops or you're warned that sync hasn't registered in more than a day</span></span>](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-office-365-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a><span data-ttu-id="4d624-129">**Kenn Wort Hashes werden nicht synchronisiert, oder es wird eine Warnung im Office 365 Admin Center angezeigt, dass es keine aktuelle Kennworthash Synchronisierung gab.**</span><span class="sxs-lookup"><span data-stu-id="4d624-129">**Password hashes aren't synchronizing, or I'm seeing an alert in the Office 365 admin center that there hasn't been a recent password hash synchronization**</span></span>
- [<span data-ttu-id="4d624-130">Implementieren der Kennworthash Synchronisierung mit Azure AD Connect Sync</span><span class="sxs-lookup"><span data-stu-id="4d624-130">Implementing password hash synchronization with Azure AD Connect sync</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a><span data-ttu-id="4d624-131">**Es wurde eine Warnung angezeigt, dass das Objekt Kontingent überschritten wurde.**</span><span class="sxs-lookup"><span data-stu-id="4d624-131">**I'm seeing an alert that Object quota exceeded**</span></span>
- <span data-ttu-id="4d624-p104">Wir verfügen über ein integriertes Objekt Kontingent, um den Dienst zu schützen. Wenn Sie zu viele Objekte in Ihrem Verzeichnis haben, die mit Office 365 synchronisiert werden müssen, müssen Sie sich an den [Support für Geschäftsprodukte wenden](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) , um Ihr Kontingent zu verlängern.</span><span class="sxs-lookup"><span data-stu-id="4d624-p104">We have a built-in object quota to help protect the service. If you have too many objects in your directory that need to sync to Office 365, you'll have to [Contact support for business products](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) to increase your quota.</span></span>

### <a name="i-need-to-know-which-attributes-are-synchronized"></a><span data-ttu-id="4d624-134">**Ich möchte wissen, welche Attribute synchronisiert sind**</span><span class="sxs-lookup"><span data-stu-id="4d624-134">**I need to know which attributes are synchronized**</span></span>
- <span data-ttu-id="4d624-135">Eine Liste aller Attribute, die zwischen lokal und der Cloud synchronisiert werden, finden Sie [hier](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span><span class="sxs-lookup"><span data-stu-id="4d624-135">You can find a list of all the attributes that are synced between on-premises and the cloud [right here](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a><span data-ttu-id="4d624-136">**Ich kann Objekte, die mit der Cloud synchronisiert wurden, nicht verwalten oder entfernen**</span><span class="sxs-lookup"><span data-stu-id="4d624-136">**I can't manage or remove objects that were synchronized to the cloud**</span></span>
- <span data-ttu-id="4d624-p105">Sind Sie bereit, Objekte nur in der Cloud zu verwalten? Oder gibt es ein Objekt, das lokal gelöscht wurde, aber in der Cloud steckt? Sehen Sie sich diese [Problem Behandlungsfehler während der Synchronisierung](https://go.microsoft.com/fwlink/p/?linkid=842044) und den [Support Artikel](https://go.microsoft.com/fwlink/p/?LinkId=396720) an, um Anleitungen zur Lösung dieser Probleme zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="4d624-p105">Are you ready to manage objects in the cloud only? Or is there an object that was deleted on-premises, but is stuck in the cloud? Take a look at this [Troubleshooting Errors during synchronization](https://go.microsoft.com/fwlink/p/?linkid=842044) and [support article](https://go.microsoft.com/fwlink/p/?LinkId=396720) for guidance on how to resolve these issues.</span></span>

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a><span data-ttu-id="4d624-140">**Ich habe die Fehlermeldung bekommen, dass mein Unternehmen die Anzahl der synchronisierbaren Objekte überschritten hat**</span><span class="sxs-lookup"><span data-stu-id="4d624-140">**I got an error message that my company has exceeded the number of objects that can be synchronized**</span></span>
- <span data-ttu-id="4d624-141">Weitere Informationen zu diesem Thema finden Sie [hier](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span><span class="sxs-lookup"><span data-stu-id="4d624-141">You can read more about this issue [here](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span></span>
   
## <a name="other-resources"></a><span data-ttu-id="4d624-142">Weitere Ressourcen</span><span class="sxs-lookup"><span data-stu-id="4d624-142">Other resources</span></span>

- [<span data-ttu-id="4d624-143">Skript zum Beheben von doppelten Benutzerprinzipalnamen (User Principal Name, UPN)</span><span class="sxs-lookup"><span data-stu-id="4d624-143">Script to fix duplicate user principal names</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [<span data-ttu-id="4d624-144">Vorbereiten einer nicht routingfähigen Domäne (wie. lokale Domäne) für die Verzeichnissynchronisierung</span><span class="sxs-lookup"><span data-stu-id="4d624-144">How to prepare a non-routable domain (such as .local domain) for directory synchronization</span></span>](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [<span data-ttu-id="4d624-145">Skript zum zählen der Gesamtzahl der synchronisierten Objekte</span><span class="sxs-lookup"><span data-stu-id="4d624-145">Script to count total synchronized objects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [<span data-ttu-id="4d624-146">Problembehandlung bei AD FS 2,0</span><span class="sxs-lookup"><span data-stu-id="4d624-146">Troubleshoot AD FS 2.0</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [<span data-ttu-id="4d624-147">Verwenden von PowerShell zum Korrigieren von leeren DisplayName-Attributen für e-Mail-aktivierte Gruppen</span><span class="sxs-lookup"><span data-stu-id="4d624-147">Use PowerShell to fix empty DisplayName attributes for mail-enabled groups</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [<span data-ttu-id="4d624-148">Verwenden von PowerShell zum Beheben von doppeltem UPN</span><span class="sxs-lookup"><span data-stu-id="4d624-148">Use PowerShell to fix duplicate UPN</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [<span data-ttu-id="4d624-149">Verwenden von PowerShell zum Beheben doppelter e-Mail-Adressen</span><span class="sxs-lookup"><span data-stu-id="4d624-149">Use PowerShell to fix duplicate email addresses</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a><span data-ttu-id="4d624-150">Diagnosetools</span><span class="sxs-lookup"><span data-stu-id="4d624-150">Diagnostic tools</span></span>

<span data-ttu-id="4d624-p106">[IDFix-Tool](prepare-directory-attributes-for-synch-with-idfix.md) dient zur Ermittlung und Behebung von Identitätsobjekten und deren Attributen in einer lokalen Active Directory-Umgebung zur Vorbereitung der Migration zu Office 365. IDFix ist für die für dirSync Verantwortlichen Active Directory-Administratoren mit dem Office 365-Dienst vorgesehen.</span><span class="sxs-lookup"><span data-stu-id="4d624-p106">[IDFix tool](prepare-directory-attributes-for-synch-with-idfix.md) is used to perform discovery and remediation of identity objects and their attributes in an on-premises Active Directory environment in preparation for migration to Office 365. IDFix is intended for the Active Directory administrators responsible for DirSync with the Office 365 service.</span></span> 

<span data-ttu-id="4d624-153">[Laden Sie das IDFix-Tool](https://go.microsoft.com/fwlink/p/?LinkId=396718) aus dem Microsoft Download Center herunter.</span><span class="sxs-lookup"><span data-stu-id="4d624-153">[Download the IDFix tool](https://go.microsoft.com/fwlink/p/?LinkId=396718) from the Microsoft download center.</span></span>