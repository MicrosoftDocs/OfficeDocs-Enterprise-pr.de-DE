---
title: "Hochverfügbarkeit der Verbundauthentifizierung, Phase 5 Konfigurieren der Verbundauthentifizierung für Office 365"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 0f1dbf52-5bff-44cc-a264-1b48641af98f
description: "Zusammenfassung: Konfigurieren Sie Azure AD Connect für die Verbundauthentifizierung mit hoher Verfügbarkeit für Office 365 in Microsoft Azure."
ms.openlocfilehash: 2c23ffa2e9f033018c5cc1fd016fb4ed76535605
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="high-availability-federated-authentication-phase-5-configure-federated-authentication-for-office-365"></a><span data-ttu-id="e8314-103">Hochverfügbarkeit der Verbundauthentifizierung, Phase 5: Konfigurieren der Verbundauthentifizierung für Office 365</span><span class="sxs-lookup"><span data-stu-id="e8314-103">High availability federated authentication Phase 5: Configure federated authentication for Office 365</span></span>

 <span data-ttu-id="e8314-104">**Zusammenfassung:** Konfigurieren Sie Azure AD Connect für die Verbundauthentifizierung mit hoher Verfügbarkeit für Office 365 in Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="e8314-104">**Summary:** Configure Azure AD Connect for your high availability federated authentication for Office 365 in Microsoft Azure.</span></span>
 
<span data-ttu-id="e8314-p101">In dieser Phase der Bereitstellung der hohen Verfügbarkeit für Verbundauthentifizierung für Office 365 in Azure-Infrastrukturdiensten rufen Sie ein Zertifikat, das von einer öffentlichen Zertifizierungsstelle ausgestellt wurde, ab, installieren das Zertifikat. Dann überprüfen Sie Ihre Konfiguration und installieren Azure AD Connect auf dem DirSync-Server und führen es aus. Azure AD Connect konfiguriert Ihr Office 365-Abonnement und Ihre AD FS- und Webanwendungsproxy-Server für die Verbundauthentifizierung.</span><span class="sxs-lookup"><span data-stu-id="e8314-p101">In this final phase of deploying high availability federated authentication for Office 365 in Azure infrastructure services, you get and install a certificate issued by a public certification authority, verify your configuration, and then install and run Azure AD Connect on the DirSync server. Azure AD Connect configures your Office 365 subscription and your Active Directory Federation Services (AD FS) and web application proxy servers for federated authentication.</span></span>
  
<span data-ttu-id="e8314-107">Eine Übersicht über alle Phasen finden Sie unter [Bereitstellen der Verbundauthentifizierung mit Hochverfügbarkeit für Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md).</span><span class="sxs-lookup"><span data-stu-id="e8314-107">See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="get-a-public-certificate-and-copy-it-to-the-dirsync-server"></a><span data-ttu-id="e8314-108">Abrufen eines öffentlichen Zertifikats und kopieren des Zertifikats auf den DirSync-Server</span><span class="sxs-lookup"><span data-stu-id="e8314-108">Get a public certificate and copy it to the DirSync server</span></span>

<span data-ttu-id="e8314-109">Rufen Sie ein digitales Zertifikat von einer öffentlichen Zertifizierungsstelle mit den folgenden Eigenschaften ab:</span><span class="sxs-lookup"><span data-stu-id="e8314-109">Get a digital certificate from a public certification authority with the following properties:</span></span>
  
- <span data-ttu-id="e8314-110">Ein X.509-Zertifikat, das zum Erstellen von SSL-Verbindungen geeignet ist.</span><span class="sxs-lookup"><span data-stu-id="e8314-110">An X.509 certificate suitable for creating SSL connections.</span></span>
    
- <span data-ttu-id="e8314-111">Die erweiterte Eigenschaft „Alternativer Antragstellername (SAN)“ ist auf den FQDN des Verbunddiensts festgelegt (z. B. „fs.contoso.com“)</span><span class="sxs-lookup"><span data-stu-id="e8314-111">The Subject Alternative Name (SAN) extended property is set to your federation service FQDN (example: fs.contoso.com).</span></span>
    
- <span data-ttu-id="e8314-112">Das Zertifikat muss über den privaten Schlüssel verfügen und im PFX-Format gespeichert sein.</span><span class="sxs-lookup"><span data-stu-id="e8314-112">The certificate must have the private key and be stored in PFX format.</span></span>
    
<span data-ttu-id="e8314-p102">Außerdem müssen die Computer und Geräte Ihrer Organisation der öffentlichen Zertifizierungsstelle vertrauen, die das digitale Zertifikat ausstellt. Diese Vertrauensstellung wird eingerichtet, indem ein Stammzertifikat von der öffentlichen Zertifizierungsstelle im Speicher der vertrauenswürdigen Stammzertifizierungsstellen auf Ihren Computern und Geräten installiert wird. Computer, auf denen Microsoft Windows ausgeführt wird, verfügen in der Regel über eine Reihe dieser Zertifikattypen, die von häufig verwendeten Zertifizierungsstellen verwendet werden. Wenn das Stammzertifikat von der öffentlichen Zertifizierungsstelle noch nicht installiert ist, müssen Sie dieses auf den Computern und Geräten Ihrer Organisation bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="e8314-p102">Additionally, your organization computers and devices must trust the public certification authority that is issuing the digital certificate. This trust is established by having a root certificate from the public certification authority installed in the trusted root certification authorities store on your computers and devices. Computers running Microsoft Windows typically have a set of these types of certificates installed from commonly-used certification authorities. If the root certificate from your public certification authority is not already installed, you must deploy this to the computers and devices of your organization.</span></span>
  
<span data-ttu-id="e8314-117">Weitere Informationen zu Zertifikatanforderungen für die Verbundauthentifizierung finden Sie unter [Voraussetzungen für die Verbundinstallation und -konfiguration](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-prerequisites#prerequisites-for-federation-installation-and-configuration).</span><span class="sxs-lookup"><span data-stu-id="e8314-117">For more information about certificate requirements for federated authentication, see [Prerequisites for federation installation and configuration](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-prerequisites#prerequisites-for-federation-installation-and-configuration).</span></span>
  
<span data-ttu-id="e8314-p103">Wenn Sie das Zertifikat erhalten, kopieren Sie es in den Ordner auf Laufwerk C: des DirSync-Servers. Geben Sie der Datei z. B. den Namen „SSL.pfx", und speichern Sie sie im Ordner „C:\\Certs" auf dem DirSync-Server.</span><span class="sxs-lookup"><span data-stu-id="e8314-p103">When you receive the certificate, copy it to a folder on the C: drive of the DirSync server. For example, name the file SSL.pfx and store it in the C:\\Certs folder on the DirSync server.</span></span>
  
## <a name="verify-your-configuration"></a><span data-ttu-id="e8314-120">Überprüfen Ihrer Konfiguration</span><span class="sxs-lookup"><span data-stu-id="e8314-120">Verify your configuration</span></span>

<span data-ttu-id="e8314-p104">Jetzt sollten Sie bereit sein, Azure AD Connect und die Verbundauthentifizierung für Office 365 zu konfigurieren. Um sicherzustellen, dass Sie bereit sind, finden Sie hier eine Checkliste:</span><span class="sxs-lookup"><span data-stu-id="e8314-p104">You should now be ready to configure Azure AD Connect and federated authentication for Office 365. To ensure that you are, here is a checklist:</span></span>
  
- <span data-ttu-id="e8314-123">Die öffentliche Domäne Ihrer Organisation wird Ihrem Office 365-Abonnement hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="e8314-123">Your organization's public domain is added to your Office 365 subscription.</span></span>
    
- <span data-ttu-id="e8314-124">Die Office 365-Benutzerkonten Ihrer Organisation sind auf den öffentlichen Domänennamen der Organisation konfiguriert und können sich erfolgreich anmelden.</span><span class="sxs-lookup"><span data-stu-id="e8314-124">Your organization's Office 365 user accounts are configured to your organization's public domain name and can successfully sign in.</span></span>
    
- <span data-ttu-id="e8314-125">Sie haben einen FQDN des Verbunddiensts basierend auf Ihrem öffentlichen Domänennamen ermittelt.</span><span class="sxs-lookup"><span data-stu-id="e8314-125">You have determined a federation service FQDN based your public domain name.</span></span>
    
- <span data-ttu-id="e8314-126">Ein öffentlicher DNS-A-Eintrag für den FQDN des Verbunddiensts zeigt auf die öffentliche IP-Adresse des Azure-Lastenausgleichs mit Internetzugriff für die Webanwendungsproxy-Server.</span><span class="sxs-lookup"><span data-stu-id="e8314-126">A public DNS A record for your federation service FQDN points to the public IP address of the Internet-facing Azure load balancer for the web application proxy servers.</span></span>
    
- <span data-ttu-id="e8314-127">Ein privater DNS-A-Eintrag für den FQDN Ihres Verbunddiensts zeigt auf die private IP-Adresse des internen Azure-Lastenausgleichs für die AD FS-Server.</span><span class="sxs-lookup"><span data-stu-id="e8314-127">A private DNS A record for your federation service FQDN points to the private IP address of the internal Azure load balancer for the AD FS servers.</span></span>
    
- <span data-ttu-id="e8314-128">Ein von einer öffentlichen Zertifizierungsstelle ausgestelltes digitales Zertifikat, das für SSL-Verbindungen mit dem SAN geeignet ist, das auf den FQDN des Verbunddiensts festgelegt ist, ist eine PFX-Datei, die auf dem DirSync-Server gespeichert ist.</span><span class="sxs-lookup"><span data-stu-id="e8314-128">A public certification authority-isssued digital certificate suitable for SSL connections with the SAN set to your federation service FQDN is a PFX file stored on your DirSync server.</span></span>
    
- <span data-ttu-id="e8314-129">Das Stammzertifikat für die öffentliche Zertifizierungsstelle wird im Speicher der vertrauenswürdigen Stammzertifizierungsstellen auf Ihren Computern und Geräten installiert.</span><span class="sxs-lookup"><span data-stu-id="e8314-129">The root certificate for the public certification authority is installed in the Trusted Root Certification Authorities store on your computers and devices.</span></span>
    
<span data-ttu-id="e8314-130">Nachfolgend finden Sie ein Beispiel für die Contoso-Organisation:</span><span class="sxs-lookup"><span data-stu-id="e8314-130">Here is an example for the Contoso organization:</span></span>
  
<span data-ttu-id="e8314-131">**Eine Beispielkonfiguration für die Verbundauthentifizierung mit Hochverfügbarkeit in Azure**</span><span class="sxs-lookup"><span data-stu-id="e8314-131">**An example configuration for a high availability federated authentication infrastructure in Azure**</span></span>

![Eine Beispielkonfiguration für die hochverfügbare Office 365-Verbundauthentifizierung in Azure](images/ac1a6a0d-0156-4407-9336-6e4cd6db8633.png)
  
## <a name="run-azure-ad-connect-to-configure-federated-authentication"></a><span data-ttu-id="e8314-133">Ausführen von Azure AD Connect zum Konfigurieren der Verbundauthentifizierung</span><span class="sxs-lookup"><span data-stu-id="e8314-133">Run Azure AD Connect to configure federated authentication</span></span>

<span data-ttu-id="e8314-134">Das Tool Azure AD Connect konfiguriert die AD FS-Server, die Webanwendungsproxy-Server und Office 365 über die folgenden Schritte für die Verbundauthentifizierung:</span><span class="sxs-lookup"><span data-stu-id="e8314-134">The Azure AD Connect tool configures the AD FS servers, the web application proxy servers, and Office 365 for federated authentication with these steps:</span></span>
  
1. <span data-ttu-id="e8314-135">Erstellen Sie eine Remotedesktopverbindung mit Ihrem DirSync-Server über ein Domänenkonto, das über lokale Administratorberechtigungen verfügt.</span><span class="sxs-lookup"><span data-stu-id="e8314-135">Create a remote desktop connection to your DirSync server with a domain account that has local administrator privileges.</span></span>
    
2. <span data-ttu-id="e8314-136">Öffnen Sie über den Desktop des DirSync-Servers Internet Explorer, und wechseln Sie zu [https://aka.ms/aadconnect](https://aka.ms/aadconnect).</span><span class="sxs-lookup"><span data-stu-id="e8314-136">From the desktop of the DirSync server, open Internet Explorer and go to [https://aka.ms/aadconnect](https://aka.ms/aadconnect).</span></span>
    
3. <span data-ttu-id="e8314-137">Klicken Sie auf der Seite **Microsoft Azure Active Directory Connect** auf **Herunterladen** und dann auf **Ausführen**.</span><span class="sxs-lookup"><span data-stu-id="e8314-137">On the **Microsoft Azure Active Directory Connect** page, click **Download**, and then click **Run**.</span></span>
    
4. <span data-ttu-id="e8314-138">Klicken Sie auf der Seite **Willkommen bei Azure AD Connect** auf **Ich stimme zu** und dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="e8314-138">On the **Welcome to Azure AD Connect** page, click **I agree**, and then click **Continue.**</span></span>
    
5. <span data-ttu-id="e8314-139">Klicken Sie auf der Seite **Express-Einstellungen** auf **Anpassen**.</span><span class="sxs-lookup"><span data-stu-id="e8314-139">On the **Express Settings** page, click **Customize**.</span></span>
    
6. <span data-ttu-id="e8314-140">Klicken Sie auf der Seite **Erforderliche Komponenten installieren** auf **Installieren**.</span><span class="sxs-lookup"><span data-stu-id="e8314-140">On the **Install required components** page, click **Install**.</span></span>
    
7. <span data-ttu-id="e8314-141">Klicken Sie auf der Seite **Benutzeranmeldung** auf **Verbund mit AD FS**, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="e8314-141">On the **User sign-in** page, click **Federation with AD FS**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="e8314-142">Geben Sie auf der Seite **Mit Azure AD verbinden** den Namen und das Kennwort eines globalen Administratorkontos für Ihr Office 365-Abonnement ein, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="e8314-142">On the **Connect to Azure AD** page, type the name and password of a global administrator account for your Office 365 subscription, and then click **Next**.</span></span>
    
9. <span data-ttu-id="e8314-143">Stellen Sie auf der Seite **Verzeichnisse verbinden** sicher, dass Ihre lokale Windows Server AD-Gesamtstruktur unter **Gesamtstruktur** ausgewählt ist, geben Sie den Namen und das Kennwort eines Domänenadministratorkontos ein, klicken Sie auf **Verzeichnis hinzufügen**, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="e8314-143">On the **Connect your directories** page, ensure that your on-premises Windows Server AD forest is selected in **Forest**, type the name and password of a domain administrator account, click **Add Directory**, and then click **Next**.</span></span>
    
10. <span data-ttu-id="e8314-144">Klicken Sie auf der Seite **Azure AD-Anmeldungskonfiguration** auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="e8314-144">On the **Azure AD sign-in configuration** page, click **Next**.</span></span>
    
11. <span data-ttu-id="e8314-145">Klicken Sie auf der Seite **Filtern von Domänen und Organisationseinheiten** auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="e8314-145">On the **Domain and OU filtering** page, click **Next**.</span></span>
    
12. <span data-ttu-id="e8314-146">Klicken Sie auf der Seite **Eindeutige Identifizierung der Benutzer** auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="e8314-146">On the **Uniquely identifying your users** page, click **Next**.</span></span>
    
13. <span data-ttu-id="e8314-147">Klicken Sie auf der Seite **Benutzer und Geräte filtern** auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="e8314-147">On the **Filter users and devices** page, click **Next**.</span></span>
    
14. <span data-ttu-id="e8314-148">Klicken Sie auf der Seite **Optionale Features** auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="e8314-148">On the **Optional features** page, click **Next**.</span></span>
    
15. <span data-ttu-id="e8314-149">Klicken Sei auf der Seite **AD FS-Farm** auf **Neue AD FS-Farm konfigurieren**.</span><span class="sxs-lookup"><span data-stu-id="e8314-149">On the **AD FS farm** page, click **Configure a new AD FS farm**.</span></span>
    
16. <span data-ttu-id="e8314-150">Klicken Sie auf **Durchsuchen**, und geben Sie den Speicherort und Namen des SSL-Zertifikats von der öffentlichen Zertifizierungsstelle an.</span><span class="sxs-lookup"><span data-stu-id="e8314-150">Click **Browse** and specify the location and name of the SSL certificate from the public certification authority.</span></span>
    
17. <span data-ttu-id="e8314-151">Geben Sie nach Aufforderung das Kennwort des Zertifikats ein, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="e8314-151">When prompted, type the certificate password, and then click **OK**.</span></span>
    
18. <span data-ttu-id="e8314-152">Überprüfen Sie, ob der **Betreffname** und der **Verbunddienstname** auf den FQDN des Verbunddiensts festgelegt sind, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="e8314-152">Verify that the **Subject Name** and **Federation Service Name** are set to your federation service FQDN, and then click **Next**.</span></span>
    
19. <span data-ttu-id="e8314-153">Geben Sie auf der Seite **AD FS-Server** den Namen des ersten AD FS-Servers (Tabelle M - Element 4 - Spalte „Name des virtuellen Computers") ein, und klicken Sie dann auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="e8314-153">On the **AD FS servers** page, type your first AD FS server's name (Table M - Item 4 - Virtual machine name column), and then click **Add**.</span></span>
    
20. <span data-ttu-id="e8314-154">Geben Sie den Namen des zweiten AD FS-Servers ein (Tabelle M - Element 5 - Spalte „Name des virtuellen Computers"), klicken Sie auf **Hinzufügen**, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="e8314-154">Type your second AD FS server's name (Table M - Item 5 - Virtual machine name column), click **Add**, and then click **Next**.</span></span>
    
21. <span data-ttu-id="e8314-155">Geben Sie auf der Seite **Webanwendungsproxy-Server** den Namen des ersten Webanwendungsproxy-Servers (Tabelle M - Element 6 - Spalte „Name des virtuellen Computers") ein, und klicken Sie dann auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="e8314-155">On the **Web Application Proxy servers** page, type your first web application proxy server's name (Table M - Item 6 - Virtual machine name column), and then click **Add**.</span></span>
    
22. <span data-ttu-id="e8314-156">Geben Sie den Namen des zweiten Webanwendungsproxy-Servers ein (Tabelle M - Element 7 - Spalte „Name des virtuellen Computers"), klicken Sie auf **Hinzufügen**, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="e8314-156">Type your second web application proxy server's name (Table M - Item 7 - Virtual machine name column), click **Add**, and then click **Next**.</span></span>
    
23. <span data-ttu-id="e8314-157">Geben Sie auf der Seite **Anmeldeinformationen des Domänenadministrators** den Benutzernamen und das Kennwort für eines Domänenadministratorkontos ein, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="e8314-157">On the **Domain Administrator credentials** page, type the user name and password of a domain administrator account, and then click **Next**.</span></span>
    
24. <span data-ttu-id="e8314-158">Geben Sie auf der Seite **AD FS-Dienstkonto** den Benutzernamen und das Kennwort für eines Unternehmensadministratorkonto ein, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="e8314-158">On the **AD FS service account** page, type the user name and password of an enterprise administrator account, and then click **Next**.</span></span>
    
25. <span data-ttu-id="e8314-159">Wählen Sie auf der Seite **Azure AD-Domäne** unter **Domäne** den DNS-Domänennamen Ihrer Organisation aus, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="e8314-159">On the **Azure AD Domain** page, in **Domain**, select your organization's DNS domain name, and then click **Next**.</span></span>
    
26. <span data-ttu-id="e8314-160">Klicken Sie auf der Seite **Bereit zur Konfiguration** auf **Installieren**.</span><span class="sxs-lookup"><span data-stu-id="e8314-160">On the **Ready to configure** page, click **Install**.</span></span>
    
27. <span data-ttu-id="e8314-p105">Klicken Sie auf der Seite **Installation ist abgeschlossen** auf **Überprüfen**. Nun sollten zwei Meldungen angezeigt werden, aus denen hervorgeht, dass sowohl die Intranet- als auch die Internetkonfiguration erfolgreich überprüft wurde.</span><span class="sxs-lookup"><span data-stu-id="e8314-p105">On the **Installation complete** page, click **Verify**. You should see two messages indicating that both the intranet and Internet configuration was successfully verified.</span></span>
    
  - <span data-ttu-id="e8314-163">In der Intranetnachricht sollte die private IP-Adresse des internen Azure-Lastenausgleichs für Ihre AD FS-Server aufgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="e8314-163">The intranet message should list the private IP address of your Azure internal load balancer for your AD FS servers.</span></span>
    
  - <span data-ttu-id="e8314-164">In der Internetnachricht sollte die öffentliche IP-Adresse des Azure-Lastenausgleichs mit Internetzugriff für Ihre Webanwendungsproxy-Server aufgeführt sein.</span><span class="sxs-lookup"><span data-stu-id="e8314-164">The Internet message should list the public IP address of your Azure Internet-facing load balancer for your web application proxy servers.</span></span>
    
28. <span data-ttu-id="e8314-165">Klicken Sie auf der Seite **Installation ist abgeschlossen** auf **Beenden**.</span><span class="sxs-lookup"><span data-stu-id="e8314-165">On the **Installation complete** page, click **Exit**.</span></span>
    
<span data-ttu-id="e8314-166">Nachfolgend sehen Sie die finale Konfiguration mit Platzhalternamen für die Server.</span><span class="sxs-lookup"><span data-stu-id="e8314-166">Here is the final configuration, with placeholder names for the servers.</span></span>
  
<span data-ttu-id="e8314-167">**Phase 5: Die finale Konfiguration für die Verbundauthentifizierungsinfrastruktur mit hoher Verfügbarkeit in Azure**</span><span class="sxs-lookup"><span data-stu-id="e8314-167">**Phase 5: The final configuration of a high availability federated authentication infrastructure in Azure**</span></span>

![Die Endkonfiguration für die hochverfügbare Office 365-Verbundauthentifizierungsinfrastruktur in Azure](images/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
<span data-ttu-id="e8314-169">Die Verbundauthentifizierungsinfrastruktur mit hoher Verfügbarkeit für Office 365 in Azure ist abgeschlossen</span><span class="sxs-lookup"><span data-stu-id="e8314-169">Your high availability federated authentication infrastructure for Office 365 in Azure is complete.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e8314-170">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="e8314-170">See Also</span></span>

[<span data-ttu-id="e8314-171">Bereitstellen der Verbundauthentifizierung mit Hochverfügbarkeit für Office 365 in Azure</span><span class="sxs-lookup"><span data-stu-id="e8314-171">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="e8314-172">Verbundidentität für Ihre Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="e8314-172">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="e8314-173">Cloudakzeptanz und Hybridlösungen</span><span class="sxs-lookup"><span data-stu-id="e8314-173">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="e8314-174">Verbundidentität für Office 365</span><span class="sxs-lookup"><span data-stu-id="e8314-174">Federated identity for Office 365</span></span>](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)


