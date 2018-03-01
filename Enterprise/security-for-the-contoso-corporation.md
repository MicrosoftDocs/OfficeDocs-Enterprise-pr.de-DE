---
title: "Sicherheit für die Contoso Corporation"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 8f6f9894-5394-4110-8b0a-b8765028c10b
description: "Zusammenfassung: Erfahren Sie, wie Contoso seine Sicherheitsanforderungen bestimmten Features in den Cloudangeboten von Microsoft zuordnete und einen Weg zur Bereitschaft für Cloudsicherheit ermittelte."
ms.openlocfilehash: f8df7f6437159aefe88851a22cc8da8b19c3838c
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="security-for-the-contoso-corporation"></a><span data-ttu-id="29c3a-103">Sicherheit für die Contoso Corporation</span><span class="sxs-lookup"><span data-stu-id="29c3a-103">Security for the Contoso Corporation</span></span>

 <span data-ttu-id="29c3a-104">**Zusammenfassung:** Erfahren Sie, wie Contoso seine Sicherheitsanforderungen bestimmten Features in den Cloudangeboten von Microsoft zuordnete und einen Weg zur Bereitschaft für Cloudsicherheit ermittelte.</span><span class="sxs-lookup"><span data-stu-id="29c3a-104">**Summary:** Understand how Contoso mapped their security requirements to features in Microsoft's cloud offerings and determined a path to cloud security readiness.</span></span>
  
<span data-ttu-id="29c3a-p101">Contoso nimmt die Sicherheit und den Schutz seiner Informationen sehr ernst. Für die Umwandlung seiner IT-Infrastruktur in eine cloudeinschließende Infrastruktur hat sich Contoso vergewissert, dass seine lokalen Sicherheitsanforderungen in Microsofts Cloudangeboten unterstützt werden und implementiert sind.</span><span class="sxs-lookup"><span data-stu-id="29c3a-p101">Contoso is serious about their information security and protection. When transitioning their IT infrastructure to a cloud-inclusive one, they made sure that their on-premises security requirements were supported and implemented in Microsoft's cloud offerings.</span></span>
  
## <a name="contosos-security-requirements-in-the-cloud"></a><span data-ttu-id="29c3a-107">Contosos Sicherheitsanforderungen in der Cloud</span><span class="sxs-lookup"><span data-stu-id="29c3a-107">Contoso's security requirements in the cloud</span></span>

<span data-ttu-id="29c3a-108">Nachfolgend finden Sie die Sicherheitsanforderungen von Contoso in der Cloud:
</span><span class="sxs-lookup"><span data-stu-id="29c3a-108">Here are Contoso's security requirements for the cloud:</span></span>
  
- <span data-ttu-id="29c3a-109">Strenge Authentifizierung bei Cloudressourcen
</span><span class="sxs-lookup"><span data-stu-id="29c3a-109">Strong authentication to cloud resources</span></span>
    
    <span data-ttu-id="29c3a-110">Zugriff auf Cloudressourcen muss authentifiziert werden, und dafür sollte nach Möglichkeit mehrstufige Authentifizierung verwendet werden.
</span><span class="sxs-lookup"><span data-stu-id="29c3a-110">Cloud resource access must be authenticated and, where possible, leverage multi-factor authentication.</span></span>
    
- <span data-ttu-id="29c3a-111">Verschlüsselung für Datenverkehr über das Internet
</span><span class="sxs-lookup"><span data-stu-id="29c3a-111">Encryption for traffic across the Internet</span></span>
    
    <span data-ttu-id="29c3a-p102">Daten, die über das Internet gesendet werden, dürfen nicht das Nur-Text-Format aufweisen. Verwenden Sie immer HTTPS-Verbindungen, IPsec oder andere End-to-End-Datenverschlüsselungsmethoden.</span><span class="sxs-lookup"><span data-stu-id="29c3a-p102">No data sent across the Internet is in plain text form. Always use HTTPS connections, IPsec, or other end-to-end data encryption methods.</span></span>
    
- <span data-ttu-id="29c3a-114">Verschlüsselung für Daten, die in der Cloud gespeichert sind
</span><span class="sxs-lookup"><span data-stu-id="29c3a-114">Encryption for data at rest in the cloud</span></span>
    
    <span data-ttu-id="29c3a-115">Alle Daten, die auf Datenträgern oder an anderer Stelle in der Cloud gespeichert sind, müssen in verschlüsselter Form vorliegen.
</span><span class="sxs-lookup"><span data-stu-id="29c3a-115">All data stored on disks or elsewhere in the cloud must be in an encrypted form.</span></span>
    
- <span data-ttu-id="29c3a-116">Zugriffssteuerungslisten für Zugriff mit geringsten Rechten
</span><span class="sxs-lookup"><span data-stu-id="29c3a-116">ACLs for least privilege access</span></span>
    
    <span data-ttu-id="29c3a-117">Kontoberechtigungen für Zugriff auf Ressourcen in der Cloud und die zugehörigen Ausführungsrechte müssen den Richtlinien der geringsten Rechte entsprechen.
</span><span class="sxs-lookup"><span data-stu-id="29c3a-117">Account permissions to access resources in the cloud and what they are allowed to do must follow least-privilege guidelines.</span></span>
    
## <a name="contosos-data-sensitivity-classification"></a><span data-ttu-id="29c3a-118">Contosos Klassifizierung der Vertraulichkeit von Daten</span><span class="sxs-lookup"><span data-stu-id="29c3a-118">Contoso's data sensitivity classification</span></span>

<span data-ttu-id="29c3a-119">Anhand der Informationen aus Microsofts Data Classification Toolkit (Toolkit zur Datenklassifizierung) [Data Classification Toolkit](https://msdn.microsoft.com/library/hh204743.aspx) hat Contoso seine Daten analysiert und die folgenden Stufen festgelegt.</span><span class="sxs-lookup"><span data-stu-id="29c3a-119">Using the information in Microsoft's [Data Classification Toolkit](https://msdn.microsoft.com/library/hh204743.aspx), Contoso performed an analysis of their data and determined the following levels.</span></span>
  
|<span data-ttu-id="29c3a-120">**Stufe 1: Geringer Geschäftswert**</span><span class="sxs-lookup"><span data-stu-id="29c3a-120">**Level 1: Low business value**</span></span>|<span data-ttu-id="29c3a-121">**Stufe 2: Mittlerer Geschäftswert**</span><span class="sxs-lookup"><span data-stu-id="29c3a-121">**Level 2: Medium business value**</span></span>|<span data-ttu-id="29c3a-122">**Stufe 3: Hoher Geschäftswert**</span><span class="sxs-lookup"><span data-stu-id="29c3a-122">**Level 3: High business value**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="29c3a-123">Daten sind verschlüsselt und nur für authentifizierte Benutzer verfügbar</span><span class="sxs-lookup"><span data-stu-id="29c3a-123">Data is encrypted and available only to authenticated users</span></span>  <br/> <span data-ttu-id="29c3a-p103">Dies gilt für alle Daten, die lokal und in cloudbasierten Speichern und Arbeitslasten gespeichert sind, z. B. Office 365. Daten werden verschlüsselt, während sie sich im Dienst und im Übergang zwischen dem Dienst und Clientgeräten befinden.</span><span class="sxs-lookup"><span data-stu-id="29c3a-p103">Provided for all data stored on premises and in cloud-based storage and workloads, such as Office 365. Data is encrypted while it resides in the service and in transit between the service and client devices.</span></span>  <br/> <span data-ttu-id="29c3a-126">Beispiele für die Daten der Stufe 1 sind normale Geschäftskommunikation (E-Mail) und Dateien für Mitarbeiter in der Verwaltung, im Vertrieb oder im Kundendienst.
</span><span class="sxs-lookup"><span data-stu-id="29c3a-126">Examples of Level 1 data are normal business communications (email) and files for administrative, sales, and support workers.</span></span>  <br/> |<span data-ttu-id="29c3a-127">Stufe 1 plus strenger Authentifizierung und Schutz vor Datenverlust</span><span class="sxs-lookup"><span data-stu-id="29c3a-127">Level 1 plus strong authentication and data loss protection</span></span>  <br/> <span data-ttu-id="29c3a-p104">Eine starke Authentifizierung umfasst eine mehrstufige Authentifizierung mit SMS-Validierung. Durch eine Verhinderung von Datenverlust wird sichergestellt, dass vertrauliche oder kritische Informationen das lokale Netzwerk nicht verlassen.</span><span class="sxs-lookup"><span data-stu-id="29c3a-p104">Strong authentication includes multi-factor authentication with SMS validation. Data loss prevention ensures that sensitive or critical information does not travel outside the on-premises network.</span></span>  <br/> <span data-ttu-id="29c3a-130">Beispiele für Daten der Stufe 2 sind Finanz- und rechtliche Informationen sowie Forschungs- und Entwicklungsdaten für neue Produkte.
</span><span class="sxs-lookup"><span data-stu-id="29c3a-130">Examples of Level 2 data are financial and legal information and research and development data for new products.</span></span>  <br/> |<span data-ttu-id="29c3a-131">Stufe 2 plus höchstmöglicher Verschlüsselung, Authentifizierung und Überwachung</span><span class="sxs-lookup"><span data-stu-id="29c3a-131">Level 2 plus the highest levels of encryption, authentication, and auditing</span></span>  <br/> <span data-ttu-id="29c3a-132">Die höchstmögliche, den regionalen Regelungen entsprechende Verschlüsselung für gespeicherte Daten oder Daten in der Cloud kombiniert mit mehrstufiger Authentifizierung über Smartcards und präzise Überwachung und Benachrichtigung.</span><span class="sxs-lookup"><span data-stu-id="29c3a-132">The highest levels of encryption for data at rest and in the cloud, compliant with regional regulations, combined with multi-factor authentication with smart cards and granular auditing and alerting.</span></span>  <br/> <span data-ttu-id="29c3a-133">Beispiele für Daten der Stufe 3 sind personenbezogene Kunden- und Partnerdaten sowie technische Produktspezifikationen und proprietäre Fertigungsverfahren.
</span><span class="sxs-lookup"><span data-stu-id="29c3a-133">Examples of Level 3 data are customer and partner personally identifiable information and product engineering specifications and proprietary manufacturing techniques.</span></span>  <br/> |
   
## <a name="mapping-microsoft-cloud-offerings-and-features-to-contosos-data-levels"></a><span data-ttu-id="29c3a-134">Zuordnung von Microsoft-Cloudangeboten und -Features zu Contosos Datenstufen</span><span class="sxs-lookup"><span data-stu-id="29c3a-134">Mapping Microsoft cloud offerings and features to Contoso's data levels</span></span>

<span data-ttu-id="29c3a-135">Die folgende Tabelle zeigt die Zuordnung der Datenstufen von Contoso zu Features in den Cloudangeboten von Microsoft:</span><span class="sxs-lookup"><span data-stu-id="29c3a-135">The following table shows the mapping of Contoso's data levels to features in Microsoft's cloud offerings:</span></span>
  
||<span data-ttu-id="29c3a-136">**SaaS**</span><span class="sxs-lookup"><span data-stu-id="29c3a-136">**SaaS**</span></span>|<span data-ttu-id="29c3a-137">**Azure PaaS**</span><span class="sxs-lookup"><span data-stu-id="29c3a-137">**Azure PaaS**</span></span>|<span data-ttu-id="29c3a-138">**Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="29c3a-138">**Azure IaaS**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="29c3a-139">Stufe 1: Geringer Geschäftswert
</span><span class="sxs-lookup"><span data-stu-id="29c3a-139">Level 1: Low business value</span></span>  <br/> | <span data-ttu-id="29c3a-140">HTTPS für alle Verbindungen</span><span class="sxs-lookup"><span data-stu-id="29c3a-140">HTTPS for all connections</span></span> <br/>  <span data-ttu-id="29c3a-141">Verschlüsselung im Ruhezustand</span><span class="sxs-lookup"><span data-stu-id="29c3a-141">Encryption at rest</span></span> <br/> | <span data-ttu-id="29c3a-142">Nur HTTPS-Verbindungen zulässig</span><span class="sxs-lookup"><span data-stu-id="29c3a-142">Support only HTTPS connections</span></span> <br/>  <span data-ttu-id="29c3a-143">Dateien verschlüsseln, die in Azure gespeichert sind
</span><span class="sxs-lookup"><span data-stu-id="29c3a-143">Encrypt files stored in Azure</span></span> <br/> | <span data-ttu-id="29c3a-144">HTTPS oder IPsec für Serverzugriff erfordern</span><span class="sxs-lookup"><span data-stu-id="29c3a-144">Require HTTPS or IPsec for server access</span></span> <br/>  <span data-ttu-id="29c3a-145">Azure Disk Encryption
</span><span class="sxs-lookup"><span data-stu-id="29c3a-145">Azure disk encryption</span></span> <br/> |
|<span data-ttu-id="29c3a-146">Stufe 2: Mittlerer Geschäftswert
</span><span class="sxs-lookup"><span data-stu-id="29c3a-146">Level 2: Medium business value</span></span>  <br/> | <span data-ttu-id="29c3a-147">Mehrstufige Azure AD-Authentifizierung (MFA) mit SMS
</span><span class="sxs-lookup"><span data-stu-id="29c3a-147">Azure AD multi-factor authentication (MFA) with SMS</span></span> <br/> | <span data-ttu-id="29c3a-148">Azure Key Vault für Verschlüsselungsschlüssel verwenden</span><span class="sxs-lookup"><span data-stu-id="29c3a-148">Use Azure Key Vault for encryption keys</span></span> <br/>  <span data-ttu-id="29c3a-149">Azure AD-MFA mit SMS
</span><span class="sxs-lookup"><span data-stu-id="29c3a-149">Azure AD MFA with SMS</span></span> <br/> | <span data-ttu-id="29c3a-150">MFA (Multi-Factor Authentication) mit SMS
</span><span class="sxs-lookup"><span data-stu-id="29c3a-150">MFA with SMS</span></span> <br/> |
|<span data-ttu-id="29c3a-151">Stufe 3: Hoher Geschäftswert
</span><span class="sxs-lookup"><span data-stu-id="29c3a-151">Level 3: High business value</span></span>  <br/> | <span data-ttu-id="29c3a-152">Azure RMS (Rights Management Service)</span><span class="sxs-lookup"><span data-stu-id="29c3a-152">Azure Rights Management System (RMS)</span></span> <br/>  <span data-ttu-id="29c3a-153">Azure AD-MFA mit Smartcards</span><span class="sxs-lookup"><span data-stu-id="29c3a-153">Azure AD MFA with smart cards</span></span> <br/>  <span data-ttu-id="29c3a-154">Bedingter Intune-Zugriff
</span><span class="sxs-lookup"><span data-stu-id="29c3a-154">Intune conditional access</span></span> <br/> | <span data-ttu-id="29c3a-155">Azure RMS</span><span class="sxs-lookup"><span data-stu-id="29c3a-155">Azure RMS</span></span> <br/>  <span data-ttu-id="29c3a-156">Azure AD-MFA mit Smartcards</span><span class="sxs-lookup"><span data-stu-id="29c3a-156">Azure AD MFA with smart cards</span></span> <br/> | <span data-ttu-id="29c3a-157">MFA mit Smartcards
</span><span class="sxs-lookup"><span data-stu-id="29c3a-157">MFA with smart cards</span></span> <br/> |
   
## <a name="contosos-information-policies"></a><span data-ttu-id="29c3a-158">Contosos Datenrichtlinien</span><span class="sxs-lookup"><span data-stu-id="29c3a-158">Contoso's information policies</span></span>

<span data-ttu-id="29c3a-159">In der folgenden Tabelle sind die Informationsrichtlinien von Contoso aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="29c3a-159">The following table lists Contoso's information policies.</span></span>
  
||<span data-ttu-id="29c3a-160">**Access**</span><span class="sxs-lookup"><span data-stu-id="29c3a-160">**Access**</span></span>|<span data-ttu-id="29c3a-161">**Datenaufbewahrung**</span><span class="sxs-lookup"><span data-stu-id="29c3a-161">**Data retention**</span></span>|<span data-ttu-id="29c3a-162">**Schutz von Daten**</span><span class="sxs-lookup"><span data-stu-id="29c3a-162">**Information protection**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="29c3a-163">Stufe 1: Geringer Geschäftswert
</span><span class="sxs-lookup"><span data-stu-id="29c3a-163">Level 1: Low business value</span></span>  <br/> | <span data-ttu-id="29c3a-164">Zugriff auf alles zulassen
</span><span class="sxs-lookup"><span data-stu-id="29c3a-164">Allow access to all</span></span> <br/> |<span data-ttu-id="29c3a-165">6 Monate</span><span class="sxs-lookup"><span data-stu-id="29c3a-165">6 months</span></span>  <br/> |<span data-ttu-id="29c3a-166">Verschlüsselung verwenden</span><span class="sxs-lookup"><span data-stu-id="29c3a-166">Use encryption</span></span>  <br/> |
|<span data-ttu-id="29c3a-167">Stufe 2: Mittlerer Geschäftswert
</span><span class="sxs-lookup"><span data-stu-id="29c3a-167">Level 2: Medium business value</span></span>  <br/> | <span data-ttu-id="29c3a-168">Zugriff für Mitarbeiter, Subunternehmer und Partner von Contoso zulassen</span><span class="sxs-lookup"><span data-stu-id="29c3a-168">Allow access to Contoso employees, subcontractors, and partners</span></span> <br/>  <span data-ttu-id="29c3a-169">MFA, TLS und MAM verwenden
</span><span class="sxs-lookup"><span data-stu-id="29c3a-169">Use MFA, TLS, and MAM</span></span> <br/> |<span data-ttu-id="29c3a-170">2 Jahre</span><span class="sxs-lookup"><span data-stu-id="29c3a-170">2 years</span></span>  <br/> |<span data-ttu-id="29c3a-171">Hashwerte für Datenintegrität verwenden
</span><span class="sxs-lookup"><span data-stu-id="29c3a-171">Use hash values for data integrity</span></span>  <br/> |
|<span data-ttu-id="29c3a-172">Stufe 3: Hoher Geschäftswert
</span><span class="sxs-lookup"><span data-stu-id="29c3a-172">Level 3: High business value</span></span>  <br/> | <span data-ttu-id="29c3a-173">Zugriff für Manager und Führungskräfte in Technik und Fertigung zulassen</span><span class="sxs-lookup"><span data-stu-id="29c3a-173">Allow access to executives and leads in engineering and manufacturing</span></span> <br/>  <span data-ttu-id="29c3a-174">RMS nur mit verwalteten Netzwerkgeräten
</span><span class="sxs-lookup"><span data-stu-id="29c3a-174">RMS with managed network devices only</span></span> <br/> |<span data-ttu-id="29c3a-175">7 Jahre
</span><span class="sxs-lookup"><span data-stu-id="29c3a-175">7 years</span></span>  <br/> |<span data-ttu-id="29c3a-176">Digitale Signaturen für Nachweisbarkeit (Unleugbarkeit) verwenden
</span><span class="sxs-lookup"><span data-stu-id="29c3a-176">Use digital signatures for non-repudiation</span></span>  <br/> |
   
## <a name="contosos-path-to-cloud-security-readiness"></a><span data-ttu-id="29c3a-177">Contosos Weg zur Cloudsicherheit</span><span class="sxs-lookup"><span data-stu-id="29c3a-177">Contoso's path to cloud security readiness</span></span>

<span data-ttu-id="29c3a-178">Contoso verwendet die folgenden Schritte, um seine Sicherheit für die Microsoft-Cloud vorzubereiten:</span><span class="sxs-lookup"><span data-stu-id="29c3a-178">Contoso used the following steps to ready their security for the Microsoft cloud:</span></span>
  
1. <span data-ttu-id="29c3a-179">Optimieren der Administratorkonten für die Cloud</span><span class="sxs-lookup"><span data-stu-id="29c3a-179">Optimize administrator accounts for the cloud</span></span>
    
    <span data-ttu-id="29c3a-180">Bei Contoso wurde eine umfassende Überprüfung der vorhandenen Windows Server AD-Administratorkonten vorgenommen und eine Reihe von Cloud-Administratorkonten und -gruppen eingerichtet.
</span><span class="sxs-lookup"><span data-stu-id="29c3a-180">Contoso did an extensive review of the existing Windows Server AD administrator accounts and set up a series of cloud administrator accounts and groups.</span></span>
    
2. <span data-ttu-id="29c3a-181">Ausführen der Analyse für Datenklassifizierung in drei Stufen</span><span class="sxs-lookup"><span data-stu-id="29c3a-181">Perform data classification analysis into three levels</span></span>
    
    <span data-ttu-id="29c3a-182">Contoso hat eine sorgfältige Überprüfung vorgenommen und die drei Stufen bestimmt, anhand denen die Microsoft-Features für Cloudangebote festgelegt wurden, mit denen Contosos wertvollste Daten zu schützen sind.</span><span class="sxs-lookup"><span data-stu-id="29c3a-182">Contoso performed a careful review and determined the three levels, which was used to determine the Microsoft cloud offering features to protect Contoso's most valuable data.</span></span>
    
3. <span data-ttu-id="29c3a-183">Bestimmen von Zugriffs-, Aufbewahrungs- und Datensicherungsrichtlinien für Datenstufen</span><span class="sxs-lookup"><span data-stu-id="29c3a-183">Determine access, retention, and information protection policies for data levels</span></span>
    
    <span data-ttu-id="29c3a-184">Auf Basis der Datenstufen hat Contoso ausführliche Anforderungen festgelegt, die dazu verwendet werden, zukünftige IT-Arbeitslasten zu qualifizieren, die in die Cloud verschoben werden.
</span><span class="sxs-lookup"><span data-stu-id="29c3a-184">Based on the data levels, Contoso determined detailed requirements, which will be used to qualify future IT workloads being moved to the cloud.</span></span>
    
## <a name="contosos-use-of-office-365-security-best-practices"></a><span data-ttu-id="29c3a-185">Verwenden von bewährten Methoden für die Sicherheit in Office 365 bei Contoso</span><span class="sxs-lookup"><span data-stu-id="29c3a-185">Contoso's use of Office 365 security best practices</span></span>

<span data-ttu-id="29c3a-186">Gemäß den bewährten Methoden für die Sicherheit in Office 365 haben Sicherheitsadministratoren und die IT-Abteilung bei Contoso Folgendes bereitgestellt:</span><span class="sxs-lookup"><span data-stu-id="29c3a-186">In accordance with Office 365 security best practices, Contoso's security administrators and IT department have deployed the following:</span></span>
  
- <span data-ttu-id="29c3a-187">**Dedizierte globale Administratorkonten mit sicheren Kennwörtern**</span><span class="sxs-lookup"><span data-stu-id="29c3a-187">**Dedicated global administrator accounts with very strong passwords**</span></span>
    
    <span data-ttu-id="29c3a-p105">Statt die globale Administratorrolle Standardbenutzerkonten zuzuweisen, wurden bei Contoso drei, dedizierte globale Administratorkonten mit sicheren Kennwörtern erstellt. Das Anmelden mit einem globalen Administratorkonto wird nur für bestimmte Verwaltungsaufgaben ausgeführt, und die Kennwörter sind nur festgelegten Mitarbeitern bekannt. Die Contoso-Sicherheitsadministratoren haben die Administratorrollen entsprechend der Position und dem Verantwortungsbereich des IT-Mitarbeiters den jeweiligen Konten zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="29c3a-p105">Rather than assign the global admin role to everyday user accounts, Contoso has create three, dedicated global administrator accounts with very strong passwords. Signing in with a global administrator account is only done for specific administrative tasks and the passwords are only known to designated staff. Contoso's security administrators have assigned admin roles to accounts that are appropriate to that IT person's job function and responsibility.</span></span>
    
    <span data-ttu-id="29c3a-191">Weitere Informationen finden Sie unter [Informationen zu Office 365-Administratorrollen](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d).</span><span class="sxs-lookup"><span data-stu-id="29c3a-191">For more information, see [About Office 365 admin roles](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d).</span></span>
    
- <span data-ttu-id="29c3a-192">**Mehrstufige Authentifizierung für wichtige Benutzerkonten**</span><span class="sxs-lookup"><span data-stu-id="29c3a-192">**Multi-factor authentication (MFA) for important user accounts**</span></span>
    
    <span data-ttu-id="29c3a-p106">Bei der mehrstufigen Authentifizierung wird eine zusätzliche Sicherheitsstufe zum Anmeldevorgang hinzugefügt, indem Benutzer aufgefordert werden, Ihre Identität nach korrekter Eingabe des Kennworts per Telefonanruf, Textnachricht oder App-Benachrichtigung auf Ihrem Smartphone zu bestätigen. Mit der mehrstufigen Authentifizierung sind Office 365-Benutzerkonten vor nicht autorisierter Anmeldung geschützt, selbst wenn ein Kontokennwort kompromittiert wird.</span><span class="sxs-lookup"><span data-stu-id="29c3a-p106">MFA adds an additional layer of protection to the sign-in process by requiring users to acknowledge a phone call, text message, or an app notification on their smart phone after correctly entering their password. With MFA, Office 365 user accounts are protected against unauthorized sign-in even if an account password is compromised.</span></span>
    
  - <span data-ttu-id="29c3a-195">Zum Schutz vor einer Kompromittierung des Office 365-Abonnements wird bei Contoso die mehrstufige Authentifizierung für alle drei globale Administratorkonten aktiviert.</span><span class="sxs-lookup"><span data-stu-id="29c3a-195">To protect against a compromise of the Office 365 subscription, Contoso enabled MFA on all three global administrator accounts.</span></span>
    
  - <span data-ttu-id="29c3a-196">Zum Schutz vor Phishingangriffen, bei denen die Anmeldeinformationen einer vertrauenswürdigen Person in der Organisation kompromittiert und böswillige E-Mails gesendet werden, wurde bei Contoso die mehrstufige Authentifizierung für alle Benutzerkonten für Manager aktiviert, einschließlich Führungskräfte.</span><span class="sxs-lookup"><span data-stu-id="29c3a-196">To protect against phishing attacks, in which an attacker compromises the credentials of a trusted person in the organization and sends malicious emails, Contoso enabled MFA on all user accounts for managers, including the executive staff.</span></span>
    
    <span data-ttu-id="29c3a-197">Weitere Informationen finden Sie unter [Planen der mehrstufigen Authentifizierung für Office 365-Bereitstellungen](https://support.office.com/article/Plan-for-multifactor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba).</span><span class="sxs-lookup"><span data-stu-id="29c3a-197">For more information, see [Plan for multi-factor authentication for Office 365 Deployments](https://support.office.com/article/Plan-for-multifactor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)</span></span>
    
- <span data-ttu-id="29c3a-198">**Advanced Security Management (ASM)**</span><span class="sxs-lookup"><span data-stu-id="29c3a-198">**Advanced Security Management (ASM)**</span></span>
    
    <span data-ttu-id="29c3a-p107">ASM verwendet konfigurierte Richtlinien für die Überwachung abweichender Aktivitäten. Contoso-Sicherheitsadministratoren richten Benachrichtigungen mit ASM ein, sodass IT-Administratoren bei anomalen oder riskanten Benutzeraktivitäten benachrichtigt werden, z. B. beim Download von großen Datenmengen, mehreren nicht erfolgreichen Anmeldeversuchen oder Anmeldungen von unbekannten oder gefährlichen IP-Adressen.</span><span class="sxs-lookup"><span data-stu-id="29c3a-p107">ASM uses configured policies to monitor for anomalous activity. Contoso security administrators set up alerts with ASM so that IT administrators are notified of unusual or risky user activity, such as downloading large amounts of data, multiple failed sign-in attempts, or sign-ins from unknown or dangerous IP addresses</span></span>
    
    <span data-ttu-id="29c3a-201">Weitere Informationen finden Sie unter [Übersicht über Advanced Security Management in Office 365 ](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).</span><span class="sxs-lookup"><span data-stu-id="29c3a-201">For more information, see [Overview of Advanced Security Management in Office 365 ](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).</span></span>
    
- <span data-ttu-id="29c3a-202">**Sicherer E-Mail-Fluss und Postfachüberwachungsprotokollierung**</span><span class="sxs-lookup"><span data-stu-id="29c3a-202">**Secure email flow and mailbox audit logging**</span></span>
    
    <span data-ttu-id="29c3a-p108">Zum Schutz vor unbekannter Malware, Viren und böswilligen URLs, die per E-Mail gesendet werden, verwenden die Contoso-Sicherheitsexperten Exchange Online Protection und Advanced Threat Protection (ATP). Bei Contoso wurde außerdem die Postfachüberwachungsprotokollierung aktiviert, um zu bestimmen, wer sich bei Benutzerpostfächern angemeldet und Nachrichten gesendet hat, sowie andere Aktivitäten zu überwachen, die vom Benutzerpostfach, einem delegierten Benutzer oder einem Administrator durchgeführt wurden.</span><span class="sxs-lookup"><span data-stu-id="29c3a-p108">Contoso security specialists are using Exchange Online Protection and Advanced Threat Protection (ATP) to protect against unknown malware, viruses, and malicious URLs transmitted through emails. Contoso has also enabled mailbox audit logging to determine who has logged into user mailboxes, sent messages, and other activities performed by the mailbox owner, a delegated user, or an administrator.</span></span>
    
    <span data-ttu-id="29c3a-205">Weitere Informationen finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="29c3a-205">For more information, see:</span></span> 
    
  - [<span data-ttu-id="29c3a-206">Antispamschutz für Office 365-E-Mails</span><span class="sxs-lookup"><span data-stu-id="29c3a-206">Office 365 Email Anti-Spam Protection</span></span>](https://support.office.com/article/Office-365-Email-AntiSpam-Protection-6a601501-a6a8-4559-b2e7-56b59c96a586)
    
  - [<span data-ttu-id="29c3a-207">Advanced Threat Protection für sichere Anlagen und sichere Links</span><span class="sxs-lookup"><span data-stu-id="29c3a-207">Advanced threat protection for safe attachments and safe links</span></span>](https://technet.microsoft.com/library/mt148491.aspx)
    
  - [<span data-ttu-id="29c3a-208">Aktivieren der Postfachüberwachung in Office 365</span><span class="sxs-lookup"><span data-stu-id="29c3a-208">Enable mailbox auditing in Office 365</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=626109)
    
- <span data-ttu-id="29c3a-209">**Verhinderung von Datenverlust**</span><span class="sxs-lookup"><span data-stu-id="29c3a-209">**Data Loss Prevention (DLP)**</span></span>
    
    <span data-ttu-id="29c3a-210">Bei Contoso wurden vertrauliche Daten identifiziert und Richtlinien zur Verhinderung von Datenverlust für Exchange Online, SharePoint Online und OneDrive konfiguriert, um zu verhindern, dass Benutzer versehentlich oder absichtlich die Daten freigeben können.</span><span class="sxs-lookup"><span data-stu-id="29c3a-210">Contoso has identified its sensitive data and configured DLP policies for Exchange Online, SharePoint Online, and OneDrive to help prevent users from accidentally or intentionally sharing the data.</span></span> 
    
    <span data-ttu-id="29c3a-211">Weitere Informationen finden Sie unter [Übersicht über die Richtlinien zur Verhinderung von Datenverlust](https://support.office.com/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e).</span><span class="sxs-lookup"><span data-stu-id="29c3a-211">For more information, see [Overview of data loss prevention policies](https://support.office.com/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e).</span></span>
    
## <a name="see-also"></a><span data-ttu-id="29c3a-212">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="29c3a-212">See Also</span></span>

[<span data-ttu-id="29c3a-213">Contoso in der Microsoft-Cloud</span><span class="sxs-lookup"><span data-stu-id="29c3a-213">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="29c3a-214">Ressourcen zur Cloud-IT-Architektur von Microsoft</span><span class="sxs-lookup"><span data-stu-id="29c3a-214">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="29c3a-215">Enterprise-Cloud-Roadmap von Microsoft: Ressourcen für IT-Entscheidungsträger</span><span class="sxs-lookup"><span data-stu-id="29c3a-215">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)
  
[<span data-ttu-id="29c3a-216">Bewährte Methoden für die Sicherheit in Office 365</span><span class="sxs-lookup"><span data-stu-id="29c3a-216">Security best practices for Office 365</span></span>](https://support.office.com/article/Security-best-practices-for-Office-365-9295e396-e53d-49b9-ae9b-0b5828cdedc3)




