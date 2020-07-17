---
title: Beheben von Problemen mit der Verzeichnissynchronisierung für Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
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
ms.openlocfilehash: d9e390a7230499f724ebbdae592264a850dd9418
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998033"
---
# <a name="fixing-problems-with-directory-synchronization-for-microsoft-365"></a><span data-ttu-id="82ad3-103">Beheben von Problemen mit der Verzeichnissynchronisierung für Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="82ad3-103">Fixing problems with directory synchronization for Microsoft 365</span></span>

<span data-ttu-id="82ad3-104">Mithilfe der Verzeichnissynchronisierung können Sie weiterhin Benutzer und Gruppen lokal verwalten und Änderungen, Ergänzungen und Löschungen in der Cloud synchronisieren.</span><span class="sxs-lookup"><span data-stu-id="82ad3-104">With directory synchronization, you can continue to manage users and groups on-premises and synchronize additions, deletions, and changes to the cloud.</span></span> <span data-ttu-id="82ad3-105">Das Setup ist jedoch etwas kompliziert, und es kann mitunter schwierig sein, die Problemursachen zu finden.</span><span class="sxs-lookup"><span data-stu-id="82ad3-105">But setup is a little complicated and it can sometimes be difficult to identify the source of problems.</span></span> <span data-ttu-id="82ad3-106">Wir verfügen über Ressourcen, mit denen Sie mögliche Probleme aufspüren und beheben können.</span><span class="sxs-lookup"><span data-stu-id="82ad3-106">We have resources to help you identify potential issues and fix them.</span></span>
  
## <a name="how-do-i-know-if-something-is-wrong"></a><span data-ttu-id="82ad3-107">Wie kann ich feststellen, ob ein Fehler vorliegt?</span><span class="sxs-lookup"><span data-stu-id="82ad3-107">How do I know if something is wrong?</span></span>

<span data-ttu-id="82ad3-108">Der erste Hinweis darauf, dass etwas nicht stimmt, ist, wenn die Dirsync-Status Kachel im Microsoft 365 Admin Center angibt, dass ein Problem vorliegt.</span><span class="sxs-lookup"><span data-stu-id="82ad3-108">The first indication that something is wrong is when the DirSync Status tile in the Microsoft 365 admin center indicates there is a problem.</span></span>
  
<span data-ttu-id="82ad3-109">Außerdem erhalten Sie eine e-Mail (an die Alternative e-Mail und an Ihre Administrator-e-Mail) von Microsoft 365, die angibt, dass Ihr Mandant Verzeichnis Synchronisierungsfehler festgestellt hat.</span><span class="sxs-lookup"><span data-stu-id="82ad3-109">You will also receive a mail (to the alternate email and to your admin email) from Microsoft 365 that indicates your tenant has encountered directory synchronization errors.</span></span> <span data-ttu-id="82ad3-110">Ausführliche Informationen finden Sie unter [Identifizieren von Verzeichnis Synchronisierungsfehlern in Microsoft 365](identify-directory-synchronization-errors.md).</span><span class="sxs-lookup"><span data-stu-id="82ad3-110">For details see [Identify directory synchronization errors in Microsoft 365](identify-directory-synchronization-errors.md).</span></span>
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a><span data-ttu-id="82ad3-111">Wie erhalte ich das Azure Active Directory Connect-Tool?</span><span class="sxs-lookup"><span data-stu-id="82ad3-111">How do I get Azure Active Directory Connect tool?</span></span>

<span data-ttu-id="82ad3-112">Navigieren Sie im [Microsoft 365 Admin Center](https://admin.microsoft.com)zu **Benutzer** \> **aktive Benutzer**.</span><span class="sxs-lookup"><span data-stu-id="82ad3-112">In the [Microsoft 365 admin center](https://admin.microsoft.com), navigate to **Users** \> **Active users**.</span></span> <span data-ttu-id="82ad3-113">Klicken Sie auf das Menü **Weitere** (drei Punkte), und wählen Sie **Verzeichnissynchronisierung**aus.</span><span class="sxs-lookup"><span data-stu-id="82ad3-113">Click the **More** menu (three dots) and select **Directory synchronization**.</span></span> 
  
<span data-ttu-id="82ad3-114">Folgen Sie den [Anweisungen im Assistenten](set-up-directory-synchronization.md), um Azure AD Connect herunterzuladen.</span><span class="sxs-lookup"><span data-stu-id="82ad3-114">Follow the [instructions in the wizard](set-up-directory-synchronization.md) to download Azure AD Connect.</span></span> 
  
<span data-ttu-id="82ad3-115">Wenn Sie weiterhin Azure Active Directory (Azure AD) Sync (Dirsync) verwenden, sehen Sie sich an, wie Sie bei der [Installation und dem Konfigurations-Assistenten für Azure Active Directory-Synchronisierungstools in Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) Informationen zu den Systemanforderungen für die Installation von DirSync, den erforderlichen Berechtigungen und zur Problembehandlung bei häufig auftretenden Fehlern anzeigen können.</span><span class="sxs-lookup"><span data-stu-id="82ad3-115">If you are still using Azure Active Directory (Azure AD) Sync (DirSync), take a look at [How to troubleshoot Azure Active Directory Sync Tool installation and Configuration Wizard error messages in Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) for information about the system requirements to install dirsync, the permissions you need, and how to troubleshoot common errors.</span></span> 
  
<span data-ttu-id="82ad3-116">Informationen zum Aktualisieren von Azure AD Sync auf Azure AD Connect finden Sie in [den Upgrade-Anweisungen](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span><span class="sxs-lookup"><span data-stu-id="82ad3-116">To update from Azure AD Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-microsoft-365"></a><span data-ttu-id="82ad3-117">Beheben häufig auftretender Ursachen von Problemen mit der Verzeichnissynchronisierung in Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="82ad3-117">Resolving common causes of problems with directory synchronization in Microsoft 365</span></span>

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a><span data-ttu-id="82ad3-118">**Synchronisierte Objekte werden nicht angezeigt oder nicht online aktualisiert, oder ich erhalte Synchronisierungsfehlerberichte vom Dienst.**</span><span class="sxs-lookup"><span data-stu-id="82ad3-118">**Synchronized objects aren't appearing or updating online, or I'm getting synchronization error reports from the Service.**</span></span>

- [<span data-ttu-id="82ad3-119">Identitätssynchronisierung und Resilienz bei doppelten Attributen</span><span class="sxs-lookup"><span data-stu-id="82ad3-119">Identity synchronization and duplicate attribute resiliency</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a><span data-ttu-id="82ad3-120">**Ich habe eine Benachrichtigung im Admin Center oder erhalte automatisierte E-Mails mit dem Hinweis, dass kürzlich kein Synchronisierungsereignis stattgefunden hat**</span><span class="sxs-lookup"><span data-stu-id="82ad3-120">**I have an alert in the admin center, or am receiving automated emails that there hasn't been a recent synchronization event**</span></span>
- [<span data-ttu-id="82ad3-121">Behandeln von Verbindungsproblemen mit Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="82ad3-121">Troubleshoot connectivity issues with Azure AD Connect</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [<span data-ttu-id="82ad3-122">Azure AD Connect-Konten und -Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="82ad3-122">Azure AD Connect Accounts and permissions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [<span data-ttu-id="82ad3-123">Azure AD Connect-Synchronisierung: Verwalten des Azure AD-Dienstkontos</span><span class="sxs-lookup"><span data-stu-id="82ad3-123">Azure AD Connect sync: How to manage the Azure AD service account</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [<span data-ttu-id="82ad3-124">Die Verzeichnissynchronisierung mit Azure Active Directory wird beendet, oder Sie erhalten eine Warnung, die besagt, dass die Synchronisierung sich seit mehr als einem Tag nicht mehr registriert hat</span><span class="sxs-lookup"><span data-stu-id="82ad3-124">Directory synchronization to Azure Active Directory stops or you're warned that sync hasn't registered in more than a day</span></span>](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a><span data-ttu-id="82ad3-125">**Kennworthashes werden nicht synchronisiert, oder im Admin Center wird eine Warnung angezeigt, die besagt, dass kürzlich keine Kennworthashsynchronisierung stattgefunden hat**</span><span class="sxs-lookup"><span data-stu-id="82ad3-125">**Password hashes aren't synchronizing, or I'm seeing an alert in the admin center that there hasn't been a recent password hash synchronization**</span></span>
- [<span data-ttu-id="82ad3-126">Implementieren der Kennworthashsynchronisierung mit der Azure AD Connect-Synchronisierung</span><span class="sxs-lookup"><span data-stu-id="82ad3-126">Implementing password hash synchronization with Azure AD Connect sync</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a><span data-ttu-id="82ad3-127">**Ich erhalte eine Warnung, dass das Objektkontingent überschritten ist**</span><span class="sxs-lookup"><span data-stu-id="82ad3-127">**I'm seeing an alert that Object quota exceeded**</span></span>
- <span data-ttu-id="82ad3-128">Als Hilfe zum Schutz des Dienstes wurde ein Objektkontingent integriert.</span><span class="sxs-lookup"><span data-stu-id="82ad3-128">We have a built-in object quota to help protect the service.</span></span> <span data-ttu-id="82ad3-129">Wenn Sie zu viele Objekte in Ihrem Verzeichnis haben, die mit Microsoft 365 synchronisiert werden müssen, müssen Sie sich an den [Support für Business-Produkte wenden](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) , um Ihr Kontingent zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="82ad3-129">If you have too many objects in your directory that need to sync to Microsoft 365, you'll have to [Contact support for business products](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) to increase your quota.</span></span>

### <a name="i-need-to-know-which-attributes-are-synchronized"></a><span data-ttu-id="82ad3-130">**Ich muss wissen, welche Attribute synchronisiert werden**</span><span class="sxs-lookup"><span data-stu-id="82ad3-130">**I need to know which attributes are synchronized**</span></span>
- <span data-ttu-id="82ad3-131">[Hier](https://go.microsoft.com/fwlink/p/?LinkId=396719) finden Sie eine Liste aller Attribute, die zwischen lokalen Verzeichnissen und der Cloud synchronisiert werden.</span><span class="sxs-lookup"><span data-stu-id="82ad3-131">You can find a list of all the attributes that are synced between on-premises and the cloud [right here](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a><span data-ttu-id="82ad3-132">**Ich kann Objekte, die mit der Cloud synchronisiert wurden, nicht verwalten oder entfernen**</span><span class="sxs-lookup"><span data-stu-id="82ad3-132">**I can't manage or remove objects that were synchronized to the cloud**</span></span>
- <span data-ttu-id="82ad3-133">Sind Sie bereit, Objekte allein in der Cloud zu verwalten?</span><span class="sxs-lookup"><span data-stu-id="82ad3-133">Are you ready to manage objects in the cloud only?</span></span> <span data-ttu-id="82ad3-134">Oder gibt es ein Objekt, das lokal gelöscht wurde und jetzt in der Cloud festhängt?</span><span class="sxs-lookup"><span data-stu-id="82ad3-134">Or is there an object that was deleted on-premises, but is stuck in the cloud?</span></span> <span data-ttu-id="82ad3-135">Anleitung zum Beheben dieser Probleme finden Sie in diesem Artikel zur [Problembehandlung bei der Synchronisierung](https://go.microsoft.com/fwlink/p/?linkid=842044) und [Unterstützung](https://go.microsoft.com/fwlink/p/?LinkId=396720).</span><span class="sxs-lookup"><span data-stu-id="82ad3-135">Take a look at this [Troubleshooting Errors during synchronization](https://go.microsoft.com/fwlink/p/?linkid=842044) and [support article](https://go.microsoft.com/fwlink/p/?LinkId=396720) for guidance on how to resolve these issues.</span></span>

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a><span data-ttu-id="82ad3-136">**Eine Fehlermeldung hat mir mitgeteilt, dass mein Unternehmen die Anzahl der Objekte, die synchronisiert werden können, überschritten hat**</span><span class="sxs-lookup"><span data-stu-id="82ad3-136">**I got an error message that my company has exceeded the number of objects that can be synchronized**</span></span>
- <span data-ttu-id="82ad3-137">Weitere Informationen zu diesem Problem finden Sie [hier](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span><span class="sxs-lookup"><span data-stu-id="82ad3-137">You can read more about this issue [here](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span></span>
   
## <a name="other-resources"></a><span data-ttu-id="82ad3-138">Weitere Ressourcen</span><span class="sxs-lookup"><span data-stu-id="82ad3-138">Other resources</span></span>

- [<span data-ttu-id="82ad3-139">Skript zum Beheben von doppelten Benutzerprinzipalnamen</span><span class="sxs-lookup"><span data-stu-id="82ad3-139">Script to fix duplicate user principal names</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [<span data-ttu-id="82ad3-140">Vorbereiten einer nicht routingfähigen Domäne (z. B. ".lokale Domäne") für die Verzeichnissynchronisierung</span><span class="sxs-lookup"><span data-stu-id="82ad3-140">How to prepare a non-routable domain (such as .local domain) for directory synchronization</span></span>](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [<span data-ttu-id="82ad3-141">Skript zum Ermitteln der Anzahl aller synchronisierten Objekte</span><span class="sxs-lookup"><span data-stu-id="82ad3-141">Script to count total synchronized objects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [<span data-ttu-id="82ad3-142">Behandeln von Problemen mit AD FS 2.0</span><span class="sxs-lookup"><span data-stu-id="82ad3-142">Troubleshoot AD FS 2.0</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [<span data-ttu-id="82ad3-143">Verwenden von PowerShell zum Korrigieren leerer "DisplayName"-Attribute für E-Mail-aktivierte Gruppen</span><span class="sxs-lookup"><span data-stu-id="82ad3-143">Use PowerShell to fix empty DisplayName attributes for mail-enabled groups</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [<span data-ttu-id="82ad3-144">Verwenden von PowerShell zum Korrigieren von doppelten UPNs</span><span class="sxs-lookup"><span data-stu-id="82ad3-144">Use PowerShell to fix duplicate UPN</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [<span data-ttu-id="82ad3-145">Verwenden von PowerShell zum Korrigieren von doppelten E-Mail-Adressen</span><span class="sxs-lookup"><span data-stu-id="82ad3-145">Use PowerShell to fix duplicate email addresses</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a><span data-ttu-id="82ad3-146">Diagnosetools</span><span class="sxs-lookup"><span data-stu-id="82ad3-146">Diagnostic tools</span></span>

<span data-ttu-id="82ad3-147">[IDFix-Tool](prepare-directory-attributes-for-synch-with-idfix.md) wird verwendet, um die Erkennung und Behebung von Identitätsobjekten und deren Attributen in einer lokalen Active Directory Umgebung in Vorbereitung auf die Migration zu Microsoft 365 durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="82ad3-147">[IDFix tool](prepare-directory-attributes-for-synch-with-idfix.md) is used to perform discovery and remediation of identity objects and their attributes in an on-premises Active Directory environment in preparation for migration to Microsoft 365.</span></span> <span data-ttu-id="82ad3-148">IDFix ist für die Active Directory Administratoren gedacht, die für die Verzeichnissynchronisierung mit dem Microsoft 365-Dienst zuständig sind.</span><span class="sxs-lookup"><span data-stu-id="82ad3-148">IDFix is intended for the Active Directory administrators responsible for directory synchronization with the Microsoft 365 service.</span></span> 

<span data-ttu-id="82ad3-149">[Herunterladen des IDFix-Tools](https://go.microsoft.com/fwlink/p/?LinkId=396718) aus dem Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="82ad3-149">[Download the IDFix tool](https://go.microsoft.com/fwlink/p/?LinkId=396718) from the Microsoft download center.</span></span>