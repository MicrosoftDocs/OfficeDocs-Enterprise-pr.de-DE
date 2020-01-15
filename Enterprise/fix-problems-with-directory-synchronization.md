---
title: Beheben von Problemen mit der Verzeichnissynchronisierung für Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
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
description: Beschreibt häufige Ursachen von Problemen mit der Verzeichnissynchronisierung in Office 365 und bietet ein paar Methoden, wie man diese Probleme beheben kann.
ms.openlocfilehash: 3a1cf63122be84dc3e1c60e84a9a3a488f81bc0f
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067671"
---
# <a name="fixing-problems-with-directory-synchronization-for-office-365"></a><span data-ttu-id="e77d7-103">Beheben von Problemen mit der Verzeichnissynchronisierung für Office 365</span><span class="sxs-lookup"><span data-stu-id="e77d7-103">Fixing problems with directory synchronization for Office 365</span></span>

<span data-ttu-id="e77d7-104">Mithilfe der Verzeichnissynchronisierung können Sie weiterhin Benutzer und Gruppen lokal verwalten und Änderungen, Ergänzungen und Löschungen in der Cloud synchronisieren.</span><span class="sxs-lookup"><span data-stu-id="e77d7-104">With directory synchronization, you can continue to manage users and groups on-premises and synchronize additions, deletions, and changes to the cloud.</span></span> <span data-ttu-id="e77d7-105">Das Setup ist jedoch etwas kompliziert, und es kann mitunter schwierig sein, die Problemursachen zu finden.</span><span class="sxs-lookup"><span data-stu-id="e77d7-105">But setup is a little complicated and it can sometimes be difficult to identify the source of problems.</span></span> <span data-ttu-id="e77d7-106">Wir verfügen über Ressourcen, mit denen Sie mögliche Probleme aufspüren und beheben können.</span><span class="sxs-lookup"><span data-stu-id="e77d7-106">We have resources to help you identify potential issues and fix them.</span></span>
  
## <a name="how-do-i-know-if-something-is-wrong"></a><span data-ttu-id="e77d7-107">Wie kann ich feststellen, ob ein Fehler vorliegt?</span><span class="sxs-lookup"><span data-stu-id="e77d7-107">How do I know if something is wrong?</span></span>

<span data-ttu-id="e77d7-108">Als ersten Hinweis auf eine fehlerhafte Funktionsweise zeigt die Kachel "DirSync-Status" im Microsoft 365 Admin Center an, dass ein Problem vorliegt:</span><span class="sxs-lookup"><span data-stu-id="e77d7-108">The first indication that something is wrong is when the DirSync Status tile in the Microsoft 365 admin center indicates there is a problem:</span></span>
  
![Die Kachel "DirSync-Status" in Admin Center Preview](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
<span data-ttu-id="e77d7-110">Außerdem sendet Office 365 Ihnen eine E-Mail (an die alternative und an Ihre Administrator-E-Mail-Adresse), aus der hervorgeht, dass bei Ihrem Mandanten Verzeichnissynchronisierungsfehler aufgetreten sind.</span><span class="sxs-lookup"><span data-stu-id="e77d7-110">You will also receive a mail (to the alternate email and to your admin email) from Office 365 that indicates your tenant has encountered directory synchronization errors.</span></span> <span data-ttu-id="e77d7-111">Ausführlichere Informationen hierzu finden Sie unter [Ermitteln von Fehlern bei der Verzeichnissynchronisierung in Office 365](identify-directory-synchronization-errors.md).</span><span class="sxs-lookup"><span data-stu-id="e77d7-111">[Identify directory synchronization errors in Office 365](identify-directory-synchronization-errors.md)</span></span>
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a><span data-ttu-id="e77d7-112">Wie erhalte ich das Azure Active Directory Connect-Tool?</span><span class="sxs-lookup"><span data-stu-id="e77d7-112">How do I get Azure Active Directory Connect tool?</span></span>

<span data-ttu-id="e77d7-113">Navigieren Sie im [Microsoft 365 Admin Center](https://admin.microsoft.com) zu \*\* Benutzer \*\* \> **Aktive Benutzer**.</span><span class="sxs-lookup"><span data-stu-id="e77d7-113">In the [Microsoft 365 admin center](https://admin.microsoft.com), navigate to \*\* Users \*\* \> **Active users**.</span></span> <span data-ttu-id="e77d7-114">Klicken Sie auf das Menü **Mehr**, und wählen Sie **Verzeichnissynchronisierung** aus.</span><span class="sxs-lookup"><span data-stu-id="e77d7-114">Click the **More** menu and select **Directory synchronization**.</span></span> 
  
![Wählen Sie im Menü "Mehr" die Option "Verzeichnissynchronisierung" aus.](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
<span data-ttu-id="e77d7-116">Folgen Sie den [Anweisungen im Assistenten](set-up-directory-synchronization.md), um Azure AD Connect herunterzuladen.</span><span class="sxs-lookup"><span data-stu-id="e77d7-116">Follow the [instructions in the wizard](set-up-directory-synchronization.md) to download Azure AD Connect.</span></span> 
  
<span data-ttu-id="e77d7-117">Wenn Sie weiterhin die Azure Active Directory-Synchronisierung (DirSync) verwenden, finden Sie unter dem Thema [Problembehandlung bei Fehlermeldungen zur Installation des Azure Active Directory-Synchronisierungstools und zum Konfigurations-Assistenten in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) Informationen zu den Systemanforderungen für die Installation von DirSync, den dazu erforderlichen Berechtigungen sowie zur Problembehandlung bei häufig auftretenden Fehlern.</span><span class="sxs-lookup"><span data-stu-id="e77d7-117">If you are still using Azure Active Directory Sync (DirSync), take a look at [How to troubleshoot Azure Active Directory Sync Tool installation and Configuration Wizard error messages in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) for information about the system requirements to install dirsync, the permissions you need, and how to troubleshoot common errors.</span></span> 
  
<span data-ttu-id="e77d7-118">Informationen zum Aktualisieren der Azure Active Directory-Synchronisierung auf Azure AD Connect finden Sie unter [Aktualisierungsanweisungen](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span><span class="sxs-lookup"><span data-stu-id="e77d7-118">To update from Azure Active Directory Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-office-365"></a><span data-ttu-id="e77d7-119">Beheben häufiger Ursachen von Problemen mit der Verzeichnissynchronisierung in Office 365</span><span class="sxs-lookup"><span data-stu-id="e77d7-119">Resolving common causes of problems with directory synchronization in Office 365</span></span>

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a><span data-ttu-id="e77d7-120">**Synchronisierte Objekte werden nicht angezeigt oder nicht online aktualisiert, oder ich erhalte Synchronisierungsfehlerberichte vom Dienst.**</span><span class="sxs-lookup"><span data-stu-id="e77d7-120">**Synchronized objects aren't appearing or updating online, or I'm getting synchronization error reports from the Service.**</span></span>

- [<span data-ttu-id="e77d7-121">Identitätssynchronisierung und Resilienz bei doppelten Attributen</span><span class="sxs-lookup"><span data-stu-id="e77d7-121">Identity synchronization and duplicate attribute resiliency</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a><span data-ttu-id="e77d7-122">**Ich habe eine Benachrichtigung im Admin Center oder erhalte automatisierte E-Mails mit dem Hinweis, dass kürzlich kein Synchronisierungsereignis stattgefunden hat**</span><span class="sxs-lookup"><span data-stu-id="e77d7-122">**I have an alert in the admin center, or am receiving automated emails that there hasn't been a recent synchronization event**</span></span>
- [<span data-ttu-id="e77d7-123">Behandeln von Verbindungsproblemen mit Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="e77d7-123">Troubleshoot connectivity issues with Azure AD Connect</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [<span data-ttu-id="e77d7-124">Azure AD Connect-Konten und -Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="e77d7-124">Azure AD Connect Accounts and permissions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [<span data-ttu-id="e77d7-125">Azure AD Connect-Synchronisierung: Verwalten des Azure AD-Dienstkontos</span><span class="sxs-lookup"><span data-stu-id="e77d7-125">Azure AD Connect sync: How to manage the Azure AD service account</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [<span data-ttu-id="e77d7-126">Die Verzeichnissynchronisierung mit Azure Active Directory wird beendet, oder Sie erhalten eine Warnung, die besagt, dass die Synchronisierung sich seit mehr als einem Tag nicht mehr registriert hat</span><span class="sxs-lookup"><span data-stu-id="e77d7-126">Directory synchronization to Azure Active Directory stops or you're warned that sync hasn't registered in more than a day</span></span>](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a><span data-ttu-id="e77d7-127">**Kennworthashes werden nicht synchronisiert, oder im Admin Center wird eine Warnung angezeigt, die besagt, dass kürzlich keine Kennworthashsynchronisierung stattgefunden hat**</span><span class="sxs-lookup"><span data-stu-id="e77d7-127">**Password hashes aren't synchronizing, or I'm seeing an alert in the admin center that there hasn't been a recent password hash synchronization**</span></span>
- <span data-ttu-id="e77d7-128">[Implementieren der Kennworthashsynchronisierung mit der Azure AD Connect-Synchronisierung](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)</span><span class="sxs-lookup"><span data-stu-id="e77d7-128">For more information, see [Implement password hash synchronization with Azure AD Connect sync](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization).</span></span>

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a><span data-ttu-id="e77d7-129">**Ich erhalte eine Warnung, dass das Objektkontingent überschritten ist**</span><span class="sxs-lookup"><span data-stu-id="e77d7-129">**I'm seeing an alert that Object quota exceeded**</span></span>
- <span data-ttu-id="e77d7-130">Als Hilfe zum Schutz des Dienstes wurde ein Objektkontingent integriert.</span><span class="sxs-lookup"><span data-stu-id="e77d7-130">We have a built-in object quota to help protect the service.</span></span> <span data-ttu-id="e77d7-131">Falls Sie zu viele Objekte in Ihrem Verzeichnis haben, die mit Office 365 synchronisiert werden müssen, [wenden Sie sich an den Support für Business-Produkte](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b), um Ihr Kontingent zu erhöhen.</span><span class="sxs-lookup"><span data-stu-id="e77d7-131">If you have too many objects in your directory that need to sync to Office 365, you'll have to [Contact support for business products](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) to increase your quota.</span></span>

### <a name="i-need-to-know-which-attributes-are-synchronized"></a><span data-ttu-id="e77d7-132">**Ich muss wissen, welche Attribute synchronisiert werden**</span><span class="sxs-lookup"><span data-stu-id="e77d7-132">**I need to know which attributes are synchronized**</span></span>
- <span data-ttu-id="e77d7-133">[Hier](https://go.microsoft.com/fwlink/p/?LinkId=396719) finden Sie eine Liste aller Attribute, die zwischen lokalen Verzeichnissen und der Cloud synchronisiert werden.</span><span class="sxs-lookup"><span data-stu-id="e77d7-133">You can find a list of all the attributes that are synced between on-premises and the cloud [right here](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a><span data-ttu-id="e77d7-134">**Ich kann Objekte, die mit der Cloud synchronisiert wurden, nicht verwalten oder entfernen**</span><span class="sxs-lookup"><span data-stu-id="e77d7-134">**I can't manage or remove objects that were synchronized to the cloud**</span></span>
- <span data-ttu-id="e77d7-135">Sind Sie bereit, Objekte allein in der Cloud zu verwalten?</span><span class="sxs-lookup"><span data-stu-id="e77d7-135">Are you ready to manage objects in the cloud only?</span></span> <span data-ttu-id="e77d7-136">Oder gibt es ein Objekt, das lokal gelöscht wurde und jetzt in der Cloud festhängt?</span><span class="sxs-lookup"><span data-stu-id="e77d7-136">Or is there an object that was deleted on-premises, but is stuck in the cloud?</span></span> <span data-ttu-id="e77d7-137">Anleitung zum Beheben dieser Probleme finden Sie in diesem Artikel zur [Problembehandlung bei der Synchronisierung](https://go.microsoft.com/fwlink/p/?linkid=842044) und [Unterstützung](https://go.microsoft.com/fwlink/p/?LinkId=396720).</span><span class="sxs-lookup"><span data-stu-id="e77d7-137">Take a look at this [Troubleshooting Errors during synchronization](https://go.microsoft.com/fwlink/p/?linkid=842044) and [support article](https://go.microsoft.com/fwlink/p/?LinkId=396720) for guidance on how to resolve these issues.</span></span>

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a><span data-ttu-id="e77d7-138">**Eine Fehlermeldung hat mir mitgeteilt, dass mein Unternehmen die Anzahl der Objekte, die synchronisiert werden können, überschritten hat**</span><span class="sxs-lookup"><span data-stu-id="e77d7-138">**I got an error message that my company has exceeded the number of objects that can be synchronized**</span></span>
- <span data-ttu-id="e77d7-139">Weitere Informationen zu diesem Problem finden Sie [hier](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span><span class="sxs-lookup"><span data-stu-id="e77d7-139">You can read more about this issue [here](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span></span>
   
## <a name="other-resources"></a><span data-ttu-id="e77d7-140">Weitere Ressourcen</span><span class="sxs-lookup"><span data-stu-id="e77d7-140">Other resources</span></span>

- [<span data-ttu-id="e77d7-141">Skript zum Beheben von doppelten Benutzerprinzipalnamen</span><span class="sxs-lookup"><span data-stu-id="e77d7-141">Script to fix duplicate user principal names</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [<span data-ttu-id="e77d7-142">Vorbereiten einer nicht routingfähigen Domäne (z. B. ".lokale Domäne") für die Verzeichnissynchronisierung</span><span class="sxs-lookup"><span data-stu-id="e77d7-142">How to prepare a non-routable domain for directory synchronization</span></span>](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [<span data-ttu-id="e77d7-143">Skript zum Ermitteln der Anzahl aller synchronisierten Objekte</span><span class="sxs-lookup"><span data-stu-id="e77d7-143">Script to count total synchronized objects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [<span data-ttu-id="e77d7-144">Behandeln von Problemen mit AD FS 2.0</span><span class="sxs-lookup"><span data-stu-id="e77d7-144">AD FS 2.0</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [<span data-ttu-id="e77d7-145">Verwenden von PowerShell zum Korrigieren leerer "DisplayName"-Attribute für E-Mail-aktivierte Gruppen</span><span class="sxs-lookup"><span data-stu-id="e77d7-145">Use PowerShell to fix empty DisplayName attributes for mail-enabled groups</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [<span data-ttu-id="e77d7-146">Verwenden von PowerShell zum Korrigieren von doppelten UPNs</span><span class="sxs-lookup"><span data-stu-id="e77d7-146">How to use PowerShell to fix duplicate UPN</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [<span data-ttu-id="e77d7-147">Verwenden von PowerShell zum Korrigieren von doppelten E-Mail-Adressen</span><span class="sxs-lookup"><span data-stu-id="e77d7-147">Use PowerShell to fix duplicate email addresses</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a><span data-ttu-id="e77d7-148">Diagnosetools</span><span class="sxs-lookup"><span data-stu-id="e77d7-148">Diagnostic tools</span></span>

<span data-ttu-id="e77d7-149">[IDFix-Tool](prepare-directory-attributes-for-synch-with-idfix.md) wird in einer lokalen Active Directory-Umgebung für die Suche nach und Korrektur von Identitätsobjekten und deren Attributen verwendet, um die Migration nach Office 365 vorzubereiten.</span><span class="sxs-lookup"><span data-stu-id="e77d7-149">The  IDFix Tool http://go.microsoft.com/fwlink/?LinkID=286107  is used to perform discovery and remediation of identity objects and their attributes in an on-premises Active Directory environment in preparation for migration to Office 365.</span></span> <span data-ttu-id="e77d7-150">IDFix richtet sich an Active Directory-Administratoren, die für DirSync mit dem Office 365-Dienst zuständig sind.</span><span class="sxs-lookup"><span data-stu-id="e77d7-150">IdFix is intended for the Active Directory administrators responsible for DirSync with the Office 365 service.</span></span> 

<span data-ttu-id="e77d7-151">[Herunterladen des IDFix-Tools](https://go.microsoft.com/fwlink/p/?LinkId=396718) aus dem Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="e77d7-151">[Download the IDFix tool](https://go.microsoft.com/fwlink/p/?LinkId=396718) from the Microsoft download center.</span></span>