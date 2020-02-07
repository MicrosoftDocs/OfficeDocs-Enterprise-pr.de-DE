---
title: Administrative Zugriffssteuerungen in Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
f1.keywords:
- NOCSH
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: 'Zusammenfassung: eine Übersicht über die administrativen Zugriffssteuerungen von Office 365 und die Datenkategorisierung.'
ms.openlocfilehash: f902b123b26f2c71cb6597f66fc47142e2f2b44c
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844536"
---
# <a name="administrative-access-controls-in-office-365"></a><span data-ttu-id="eac5c-103">Administrative Zugriffssteuerungen in Office 365</span><span class="sxs-lookup"><span data-stu-id="eac5c-103">Administrative Access Controls in Office 365</span></span> 

<span data-ttu-id="eac5c-104">Microsoft hat stark in Systeme und Steuerelemente investiert, die die meisten Office 365 Vorgänge automatisieren und den Zugriff auf Kunden Inhalte durch Microsoft absichtlich einschränken.</span><span class="sxs-lookup"><span data-stu-id="eac5c-104">Microsoft has invested heavily in systems and controls that automate most Office 365 operations while intentionally limiting access to customer content by Microsoft.</span></span> <span data-ttu-id="eac5c-105">Der Dienst wird von den Menschen verwaltet, und die Software betreibt den Dienst.</span><span class="sxs-lookup"><span data-stu-id="eac5c-105">Humans govern the service, and software operates the service.</span></span> <span data-ttu-id="eac5c-106">Dadurch kann Microsoft Office 365 skalieren und die Risiken interner Bedrohungen für Kunden Inhalte verwalten.</span><span class="sxs-lookup"><span data-stu-id="eac5c-106">This enables Microsoft to manage Office 365 at scale and manage the risks of internal threats to customer content.</span></span>

<span data-ttu-id="eac5c-107">Standardmäßig verfügen die Microsoft-Techniker über keine ständigen Administratorrechte und keinen ständigen Zugriff auf Kundeninhalte in Office 365.</span><span class="sxs-lookup"><span data-stu-id="eac5c-107">By default, Microsoft engineers have zero standing administrative privileges and zero standing access to customer content in Office 365.</span></span> <span data-ttu-id="eac5c-108">Ein Microsoft-Techniker kann für einen begrenzten Zeitraum begrenzten, überwachten und gesicherten Zugriff auf die Inhalte eines Kunden haben.</span><span class="sxs-lookup"><span data-stu-id="eac5c-108">A Microsoft engineer can have limited, audited, and secured access to a customer's content for a limited amount of time.</span></span> <span data-ttu-id="eac5c-109">Der Zugriff ist nur für Dienstvorgänge erforderlich und nur, wenn er von einem Mitglied von Microsoft Senior Management genehmigt wurde.</span><span class="sxs-lookup"><span data-stu-id="eac5c-109">Access is only when necessary for service operations and only when approved by a member of Microsoft senior management.</span></span> <span data-ttu-id="eac5c-110">Für Kunden Lockbox-lizenzierte Kunden bietet der Kunde Zugriffsgenehmigung für die Inhalte an, die auf Office 365 gehostet werden.</span><span class="sxs-lookup"><span data-stu-id="eac5c-110">For Customer Lockbox licensed customers, the customer provides access approval to their content hosted on Office 365.</span></span>

<span data-ttu-id="eac5c-111">Microsoft stellt Onlinedienste bereit, die mehrere Formen der Cloud-Zustellung verwenden:</span><span class="sxs-lookup"><span data-stu-id="eac5c-111">Microsoft provides online services using multiple forms of cloud delivery:</span></span>

- <span data-ttu-id="eac5c-112">**Öffentliche Clouds:** Enthält mehr mandantenversionen von Office 365, Azure und anderen Diensten, die in Nordamerika, Südamerika, Europa, Asien, Australien usw. gehostet werden.</span><span class="sxs-lookup"><span data-stu-id="eac5c-112">**Public Clouds:** Includes multi-tenant versions of Office 365, Azure, and other services hosted in North America, South America, Europe, Asia, Australia, etc.</span></span>
- <span data-ttu-id="eac5c-113">**Nationale Clouds:** Umfasst alle souveränen und von Drittanbietern betriebenen Clouds außerhalb der Vereinigten Staaten (mit Ausnahme der zuvor erwähnten), wie Office 365 in China (betrieben von 21Vianet) und Office 365 in Deutschland (betrieben von Microsoft, aber unter einem Modell, in dem ein deutscher Daten Treuhänder, die Deutsche Telekom) den Zugriff von Microsoft auf Kundendaten und-Systeme steuert und überwacht, die Kundendaten enthalten.</span><span class="sxs-lookup"><span data-stu-id="eac5c-113">**National Clouds:** Includes all sovereign and third party-operated clouds outside of the United States (except ones noted previously), such as Office 365 in China (operated by 21Vianet), and Office 365 in Germany (operated by Microsoft, but under a model in which a German data trustee, Deutsche Telekom, controls and monitors Microsoft's access to Customer Data and systems that contain Customer Data).</span></span>
- <span data-ttu-id="eac5c-114">**Öffentliche Clouds:** Umfasst Office 365-und Azure-Dienste, die für US-amerikanische Regierungskunden verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="eac5c-114">**Government Clouds:** Includes Office 365 and Azure services that are available to United States government customers.</span></span>

<span data-ttu-id="eac5c-115">Für die Zwecke dieses Artikels umfassen Office 365 Dienste Folgendes:</span><span class="sxs-lookup"><span data-stu-id="eac5c-115">For purposes of this article, Office 365 services include:</span></span>

- [<span data-ttu-id="eac5c-116">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="eac5c-116">Exchange Online</span></span>](https://docs.microsoft.com/Exchange/exchange-online)
- [<span data-ttu-id="eac5c-117">Exchange Online Protection</span><span class="sxs-lookup"><span data-stu-id="eac5c-117">Exchange Online Protection</span></span>](https://docs.microsoft.com/Office365/SecurityCompliance/eop/exchange-online-protection-overview)
- [<span data-ttu-id="eac5c-118">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="eac5c-118">SharePoint Online</span></span>](https://docs.microsoft.com/sharepoint/sharepoint-online)
- [<span data-ttu-id="eac5c-119">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="eac5c-119">OneDrive for Business</span></span>](https://docs.microsoft.com/OneDrive/onedrive)
- [<span data-ttu-id="eac5c-120">Skype for Business</span><span class="sxs-lookup"><span data-stu-id="eac5c-120">Skype for Business</span></span>](https://docs.microsoft.com/SkypeForBusiness/skype-for-business-online)
- [<span data-ttu-id="eac5c-121">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="eac5c-121">Microsoft Teams</span></span>](https://docs.microsoft.com/MicrosoftTeams/Teams-overview)
- [<span data-ttu-id="eac5c-122">Yammer</span><span class="sxs-lookup"><span data-stu-id="eac5c-122">Yammer</span></span>](https://docs.microsoft.com/yammer/yammer-landing-page)

## <a name="office-365-access-controls"></a><span data-ttu-id="eac5c-123">Office 365 von Zugriffssteuerungen</span><span class="sxs-lookup"><span data-stu-id="eac5c-123">Office 365 Access Controls</span></span>

<span data-ttu-id="eac5c-124">Für Zugriffs Steuerungszwecke kategorisiert Microsoft Office 365 Daten als Kundendaten oder andere Datentypen.</span><span class="sxs-lookup"><span data-stu-id="eac5c-124">For access control purposes, Microsoft categorizes Office 365 data as Customer data or other types of data.</span></span>

### <a name="customer-data"></a><span data-ttu-id="eac5c-125">Kundendaten</span><span class="sxs-lookup"><span data-stu-id="eac5c-125">Customer data</span></span>

<span data-ttu-id="eac5c-126">Kundendaten sind alle Daten, die von oder im Auftrag eines Kunden bei der Verwendung von Office 365 Diensten bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="eac5c-126">Customer data is all data provided by or on behalf of a customer when using Office 365 services.</span></span> <span data-ttu-id="eac5c-127">Dies sind Kunden Inhalte, die von Office 365 Benutzern direkt erstellt oder hochgeladen werden, einschließlich:</span><span class="sxs-lookup"><span data-stu-id="eac5c-127">This is customer content directly created or uploaded by Office 365 users, including:</span></span>

- <span data-ttu-id="eac5c-128">E-Mails</span><span class="sxs-lookup"><span data-stu-id="eac5c-128">Emails</span></span>
- <span data-ttu-id="eac5c-129">SharePoint Online Inhalt</span><span class="sxs-lookup"><span data-stu-id="eac5c-129">SharePoint Online content</span></span>
- <span data-ttu-id="eac5c-130">Sofortnachrichten</span><span class="sxs-lookup"><span data-stu-id="eac5c-130">Instant messages</span></span>
- <span data-ttu-id="eac5c-131">Kalenderelemente</span><span class="sxs-lookup"><span data-stu-id="eac5c-131">Calendar items</span></span>
- <span data-ttu-id="eac5c-132">Dokumente</span><span class="sxs-lookup"><span data-stu-id="eac5c-132">Documents</span></span>
- <span data-ttu-id="eac5c-133">Kontakte</span><span class="sxs-lookup"><span data-stu-id="eac5c-133">Contacts</span></span>
- <span data-ttu-id="eac5c-134">Endbenutzer-identifizierbare Informationen (EUII) (Daten, die für einen Benutzer eindeutig sind oder die mit einem einzelnen Benutzer verknüpft sind, aber keine Kunden Inhalte enthalten).</span><span class="sxs-lookup"><span data-stu-id="eac5c-134">End-user identifiable information (EUII) (data that is unique to a user or that is linkable to an individual user but does not include customer content).</span></span>

### <a name="other-types-of-data"></a><span data-ttu-id="eac5c-135">Andere Datentypen</span><span class="sxs-lookup"><span data-stu-id="eac5c-135">Other types of data</span></span>

<span data-ttu-id="eac5c-136">Zu den anderen Datentypen gehören:</span><span class="sxs-lookup"><span data-stu-id="eac5c-136">Other types of data include:</span></span>

- <span data-ttu-id="eac5c-137">**Kontodaten:** Enthält administrative Daten (Informationen, die von Administratoren bei der Registrierung oder beim Kauf von Diensten bereitgestellt werden) und Zahlungsdaten (Informationen zu Zahlungsinstrumenten wie Kreditkartendetails).</span><span class="sxs-lookup"><span data-stu-id="eac5c-137">**Account data:** Includes administrative data (information provided by administrators when they sign-up or purchase services), and payment data (information about payment instruments, such as credit card details).</span></span>
- <span data-ttu-id="eac5c-138">**Organisatorisch identifizierbare Informationen:** Enthält Daten, die zum Identifizieren eines Mandanten, zur Verwendung und nicht zum Verknüpfen mit einem einzelnen Benutzer oder zum Einschließen in Kunden Inhalte verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="eac5c-138">**Organizationally identifiable information:** Includes data used to identify a tenant, usage data, and not linkable to an individual user or included in customer content.</span></span>
- <span data-ttu-id="eac5c-139">**System Metadaten:** Enthält Dienstprotokolle, die Konfigurationseinstellungen, Systemstatus, Microsoft-IP-Adressen und technische Informationen zu Abonnements und Mandanten enthalten.</span><span class="sxs-lookup"><span data-stu-id="eac5c-139">**System metadata:** Includes service logs that contain configuration settings, system status, Microsoft IP addresses, and technical information about subscriptions and tenants.</span></span>

<span data-ttu-id="eac5c-140">Microsoft hat Zugriffssteuerungsmechanismen eingerichtet, um sicherzustellen, dass niemand ungenehmigten Zugriff auf Kundendaten oder Zugriffssteuerungsdaten hat.</span><span class="sxs-lookup"><span data-stu-id="eac5c-140">Microsoft has established access control mechanisms to ensure that no one has unapproved access to Customer Data or access control data.</span></span> <span data-ttu-id="eac5c-141">Zugriffssteuerungsdaten verwalten den Zugriff auf andere Daten oder Funktionen in der Umgebung, einschließlich Zugriff auf Kunden Inhalte oder EUII, Microsoft-Kennwörter, Sicherheitszertifikate und andere Authentifizierungs bezogene Daten.</span><span class="sxs-lookup"><span data-stu-id="eac5c-141">Access control data manages access to other types of data or functions within the environment, including access to customer content or EUII, Microsoft passwords, security certificates, and other authentication-related data.</span></span> <span data-ttu-id="eac5c-142">Zugriffssteuerungsmechanismen schützen auch den nicht genehmigten physischen, logischen oder Remotezugriff auf die Office 365 Produktionsumgebung.</span><span class="sxs-lookup"><span data-stu-id="eac5c-142">Access control mechanisms also guard against unapproved physical, logical, or remote access to the Office 365 production environment.</span></span>

<span data-ttu-id="eac5c-143">Microsoft verwendet drei Kategorien von Zugriffs Steuerelementen für Betriebs Office 365:</span><span class="sxs-lookup"><span data-stu-id="eac5c-143">There are three categories of access controls used by Microsoft for operating Office 365:</span></span>

- <span data-ttu-id="eac5c-144">Isolierungs Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="eac5c-144">Isolation Controls</span></span>
- <span data-ttu-id="eac5c-145">Personalsteuer Elemente</span><span class="sxs-lookup"><span data-stu-id="eac5c-145">Personnel Controls</span></span>
- <span data-ttu-id="eac5c-146">Technologie Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="eac5c-146">Technology Controls</span></span>

<span data-ttu-id="eac5c-147">Wenn diese Steuerelemente kombiniert werden, können Sie böswillige Aktionen in Office 365 verhindern und erkennen.</span><span class="sxs-lookup"><span data-stu-id="eac5c-147">When combined, these controls help prevent and detect malicious actions in Office 365.</span></span> <span data-ttu-id="eac5c-148">Zusätzlich zu den von Microsoft verwendeten Isolierungs-, Personal-und Technologie Steuerelementen gibt es eine vierte Kategorie von Steuerelementen: die von Kunden implementierten.</span><span class="sxs-lookup"><span data-stu-id="eac5c-148">In addition to the isolation, personnel, and technology controls used by Microsoft, there is a fourth category of controls: those implemented by customers.</span></span>

<span data-ttu-id="eac5c-149">Office 365 ermöglicht Ihnen die Verwaltung von Daten auf die gleiche Weise, wie Daten in lokalen Umgebungen verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="eac5c-149">Office 365 allows you to manage data the same way data is managed in on-premises environments.</span></span> <span data-ttu-id="eac5c-150">Die Person, die eine Organisation für Office 365 anmeldet, wird automatisch zu einem globalen Administrator.</span><span class="sxs-lookup"><span data-stu-id="eac5c-150">The person who signs up an organization for Office 365 automatically becomes a global administrator.</span></span> <span data-ttu-id="eac5c-151">Der globale Administrator hat Zugriff auf alle Features in Verwaltungs Portalen und kann Folgendes:</span><span class="sxs-lookup"><span data-stu-id="eac5c-151">The global admin has access to all features in Management Portals and can:</span></span>

- <span data-ttu-id="eac5c-152">Erstellen oder Bearbeiten von Benutzern</span><span class="sxs-lookup"><span data-stu-id="eac5c-152">Create or edit users</span></span>
- <span data-ttu-id="eac5c-153">Zuweisen von Administratorrollen zu anderen Benutzern</span><span class="sxs-lookup"><span data-stu-id="eac5c-153">Assign admin roles to others</span></span>
- <span data-ttu-id="eac5c-154">Zurücksetzen von Benutzerkennwörtern</span><span class="sxs-lookup"><span data-stu-id="eac5c-154">Reset user passwords</span></span>
- <span data-ttu-id="eac5c-155">Verwalten von Benutzerlizenzen</span><span class="sxs-lookup"><span data-stu-id="eac5c-155">Manage user licenses</span></span>
- <span data-ttu-id="eac5c-156">Verwalten von Domänen</span><span class="sxs-lookup"><span data-stu-id="eac5c-156">Manage domains</span></span>
- <span data-ttu-id="eac5c-157">Genehmigen von Kunden-Lockbox-Anforderungen</span><span class="sxs-lookup"><span data-stu-id="eac5c-157">Approve Customer Lockbox requests</span></span>

<span data-ttu-id="eac5c-158">Es wird empfohlen, dass jede Organisation mindestens zwei Administratorkonten konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="eac5c-158">We recommend that each organization configure at least two admin accounts.</span></span> <span data-ttu-id="eac5c-159">Für große Unternehmensorganisationen empfehlen wir spezialisierte Administratorkonten, die unterschiedliche Funktionen bedienen.</span><span class="sxs-lookup"><span data-stu-id="eac5c-159">For large enterprise organizations, we recommend specialized admin accounts that serve different functions.</span></span>

<span data-ttu-id="eac5c-160">Informationen zum Zuweisen von Administratorrollen und-Berechtigungen finden Sie unter [Zuweisen von Administratorrollen in Office 365](https://support.office.com/article/Assigning-admin-roles-in-Office-365-eac4d046-1afd-4f1a-85fc-8219c79e1504) und [Office 365 Administratorrollen](https://support.office.com/article/Permissions-in-Office-365-DA585EEA-F576-4F55-A1E0-87090B6AAA9D).</span><span class="sxs-lookup"><span data-stu-id="eac5c-160">For information about assigning admin roles and permissions, see [Assigning admin roles in Office 365](https://support.office.com/article/Assigning-admin-roles-in-Office-365-eac4d046-1afd-4f1a-85fc-8219c79e1504) and [About Office 365 admin roles](https://support.office.com/article/Permissions-in-Office-365-DA585EEA-F576-4F55-A1E0-87090B6AAA9D).</span></span>

## <a name="related-links"></a><span data-ttu-id="eac5c-161">Links zu verwandten Themen</span><span class="sxs-lookup"><span data-stu-id="eac5c-161">Related Links</span></span>

- [<span data-ttu-id="eac5c-162">Isolierungs Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="eac5c-162">Isolation Controls</span></span>](office-365-isolation-controls.md)
- [<span data-ttu-id="eac5c-163">Personalsteuer Elemente</span><span class="sxs-lookup"><span data-stu-id="eac5c-163">Personnel Controls</span></span>](office-365-personnel-controls.md)
- [<span data-ttu-id="eac5c-164">Technologie Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="eac5c-164">Technology Controls</span></span>](office-365-technology-controls.md)
- [<span data-ttu-id="eac5c-165">Überwachung und Überprüfung von Zugriffssteuerungen</span><span class="sxs-lookup"><span data-stu-id="eac5c-165">Monitoring and Auditing Access Controls</span></span>](office-365-monitoring-and-auditing-access-controls.md)
- [<span data-ttu-id="eac5c-166">Yammer Enterprise-Zugriffssteuerungen</span><span class="sxs-lookup"><span data-stu-id="eac5c-166">Yammer Enterprise Access Controls</span></span>](office-365-yammer-enterprise-access-controls.md)