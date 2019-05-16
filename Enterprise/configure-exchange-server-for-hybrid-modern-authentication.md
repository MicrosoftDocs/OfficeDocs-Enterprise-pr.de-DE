---
title: Lokale Konfiguration von Exchange Server derart, dass die moderne Hybridauthentifizierung verwendet wird
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 11/16/2018
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: cef3044d-d4cb-4586-8e82-ee97bd3b14ad
ms.collection:
- M365-security-compliance
description: Hybrid modern Authentication (HMA) ist eine Methode zur Identitätsverwaltung, die eine sicherere Benutzerauthentifizierung und-Autorisierung bietet und für lokale Exchange Server-hybridbereitstellungen verfügbar ist.
ms.openlocfilehash: 98a47f9527b3922767bfd8240790d7cfdeb14936
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068041"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a><span data-ttu-id="99a38-103">Lokale Konfiguration von Exchange Server derart, dass die moderne Hybridauthentifizierung verwendet wird</span><span class="sxs-lookup"><span data-stu-id="99a38-103">How to configure Exchange Server on-premises to use Hybrid Modern Authentication</span></span>

<span data-ttu-id="99a38-104">Hybrid modern Authentication (HMA) ist eine Methode zur Identitätsverwaltung, die eine sicherere Benutzerauthentifizierung und-Autorisierung bietet und für lokale Exchange Server-hybridbereitstellungen verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="99a38-104">Hybrid Modern Authentication (HMA), is a method of identity management that offers more secure user authentication and authorization, and is available for Exchange server on-premises hybrid deployments.</span></span>
  
## <a name="fyi"></a><span data-ttu-id="99a38-105">FYI</span><span class="sxs-lookup"><span data-stu-id="99a38-105">FYI</span></span>

<span data-ttu-id="99a38-106">Bevor wir beginnen, rufe ich an:</span><span class="sxs-lookup"><span data-stu-id="99a38-106">Before we begin, I call:</span></span>
  
- <span data-ttu-id="99a38-107">Moderne Hybrid Authentifizierung \> HMA</span><span class="sxs-lookup"><span data-stu-id="99a38-107">Hybrid Modern Authentication \> HMA</span></span>
    
- <span data-ttu-id="99a38-108">Exchange lokal \> Austausch</span><span class="sxs-lookup"><span data-stu-id="99a38-108">Exchange on-premises \> EXCH</span></span>
    
- <span data-ttu-id="99a38-109">Exchange Online \> Exo</span><span class="sxs-lookup"><span data-stu-id="99a38-109">Exchange Online \> EXO</span></span>
    
<span data-ttu-id="99a38-110">*Wenn eine Grafik in diesem Artikel ein Objekt enthält, das "abgeblendet" oder "abgeblendet" ist, bedeutet dies, dass das in grau gezeigte Element nicht in der HMA-spezifischen Konfiguration enthalten ist* .</span><span class="sxs-lookup"><span data-stu-id="99a38-110">Also,  *if a graphic in this article has an object that's 'grayed-out' or 'dimmed' that means the element shown in gray is not included in HMA-specific configuration*  .</span></span> 
  
## <a name="enabling-hybrid-modern-authentication"></a><span data-ttu-id="99a38-111">Aktivieren der modernen Hybrid Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="99a38-111">Enabling Hybrid Modern Authentication</span></span>

<span data-ttu-id="99a38-112">Turning HMA on Means:</span><span class="sxs-lookup"><span data-stu-id="99a38-112">Turning HMA on means:</span></span>
  
1. <span data-ttu-id="99a38-113">Sicherstellen, dass Sie die PreReqs erfüllen, bevor Sie beginnen.</span><span class="sxs-lookup"><span data-stu-id="99a38-113">Being sure you meet the prereqs before you begin.</span></span>
    
1. <span data-ttu-id="99a38-114">Da viele **voraus** setzungen sowohl für Skype for Business als auch für Exchange, die [moderne Hybrid Authentifizierungs Übersicht und die Voraussetzungen für die Verwendung mit lokalen Skype for Business-und Exchange-Servern](hybrid-modern-auth-overview.md)gelten.</span><span class="sxs-lookup"><span data-stu-id="99a38-114">Since many **prerequisites** are common for both Skype for Business and Exchange, [Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers](hybrid-modern-auth-overview.md).</span></span> <span data-ttu-id="99a38-115">Führen Sie diese Schritte aus, bevor Sie mit den Schritten in diesem Artikel beginnen.</span><span class="sxs-lookup"><span data-stu-id="99a38-115">Do this before you begin any of the steps in this article.</span></span>
    
2. <span data-ttu-id="99a38-116">Hinzufügen von lokalen Webdienst-URLs als Dienstprinzipalnamen (SPNs) in Azure AD.</span><span class="sxs-lookup"><span data-stu-id="99a38-116">Adding on-premises web service URLs as Service Principal Names (SPNs) in Azure AD.</span></span>
    
3. <span data-ttu-id="99a38-117">Sicherstellen, dass alle virtuellen Verzeichnisse für HMA aktiviert sind</span><span class="sxs-lookup"><span data-stu-id="99a38-117">Ensuring all Virtual Directories are enabled for HMA</span></span>
    
4. <span data-ttu-id="99a38-118">Suchen nach dem EvoSTS-Auth-Server Objekt</span><span class="sxs-lookup"><span data-stu-id="99a38-118">Checking for the EvoSTS Auth Server object</span></span>
    
5. <span data-ttu-id="99a38-119">Aktivieren von HMA in der über Schaltung</span><span class="sxs-lookup"><span data-stu-id="99a38-119">Enabling HMA in EXCH.</span></span>
    
 <span data-ttu-id="99a38-120">**Hinweis** Unterstützt Ihre Office-Version MA?</span><span class="sxs-lookup"><span data-stu-id="99a38-120">**Note** Does your version of Office support MA?</span></span> <span data-ttu-id="99a38-121">Erfahren Sie [, wie die moderne Authentifizierung für Office 2013-und Office 2016-Client-apps funktioniert](modern-auth-for-office-2013-and-2016.md).</span><span class="sxs-lookup"><span data-stu-id="99a38-121">See [How modern authentication works for Office 2013 and Office 2016 client apps](modern-auth-for-office-2013-and-2016.md).</span></span>
  
## <a name="make-sure-you-meet-all-the-pre-reqs"></a><span data-ttu-id="99a38-122">Stellen Sie sicher, dass Sie alle Prä-reqs</span><span class="sxs-lookup"><span data-stu-id="99a38-122">Make sure you meet all the pre-reqs</span></span>

<span data-ttu-id="99a38-123">Da viele der Voraussetzungen sowohl für Skype for Business als auch für Exchange gelten, lesen Sie die Übersicht über die [moderne Hybrid Authentifizierung und die Voraussetzungen für die Verwendung mit lokalen Skype for Business-und Exchange-Servern](hybrid-modern-auth-overview.md).</span><span class="sxs-lookup"><span data-stu-id="99a38-123">Since many prerequisites are common for both Skype for Business and Exchange, review [Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers](hybrid-modern-auth-overview.md).</span></span> <span data-ttu-id="99a38-124">Führen Sie diese Schritte aus, *bevor* Sie mit den Schritten in diesem Artikel beginnen.</span><span class="sxs-lookup"><span data-stu-id="99a38-124">Do this  *before*  you begin any of the steps in this article.</span></span> 
  
## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a><span data-ttu-id="99a38-125">Hinzufügen von lokalen Webdienst-URLs als SPNs in Azure AD</span><span class="sxs-lookup"><span data-stu-id="99a38-125">Add on-premises web service URLs as SPNs in Azure AD</span></span>

<span data-ttu-id="99a38-126">Führen Sie die Befehle aus, die ihre lokalen Webdienst-URLs als Azure AD-SPNs zuweisen.</span><span class="sxs-lookup"><span data-stu-id="99a38-126">Run the commands that assign your on-premises web service URLs as Azure AD SPNs.</span></span> <span data-ttu-id="99a38-127">SPNs werden von Clientcomputern und-Geräten während der Authentifizierung und Autorisierung verwendet.</span><span class="sxs-lookup"><span data-stu-id="99a38-127">SPNs are used by client machines and devices during authentication and authorization.</span></span> <span data-ttu-id="99a38-128">Alle URLs, die zum Herstellen einer Verbindung von lokal zu Azure Active Directory (AAD) verwendet werden können, müssen in Aad registriert werden (Dies umfasst sowohl interne als auch externe Namespaces).</span><span class="sxs-lookup"><span data-stu-id="99a38-128">All the URLs that might be used to connect from on-premises to Azure Active Directory (AAD) must be registered in AAD (this includes both internal and external namespaces).</span></span>
  
<span data-ttu-id="99a38-129">Sammeln Sie zunächst alle URLs, die Sie in Aad hinzufügen müssen.</span><span class="sxs-lookup"><span data-stu-id="99a38-129">First, gather all the URLs that you need to add in AAD.</span></span> <span data-ttu-id="99a38-130">Führen Sie die folgenden Befehle lokal aus:</span><span class="sxs-lookup"><span data-stu-id="99a38-130">Run these commands on-premises:</span></span>
  
```powershell
Get-MapiVirtualDirectory | FL server,*url*
Get-WebServicesVirtualDirectory | FL server,*url*
Get-ActiveSyncVirtualDirectory | FL server,*url*
Get-OABVirtualDirectory | FL server,*url*
```
    
<span data-ttu-id="99a38-131">Stellen Sie sicher, dass die URLs, mit denen eine Verbindung hergestellt werden kann, als HTTPS-Dienstprinzipalnamen in Aad aufgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="99a38-131">Ensure the URLs clients may connect to are listed as HTTPS service principal names in AAD.</span></span>
  
1. <span data-ttu-id="99a38-132">Stellen Sie zunächst eine Verbindung mit Aad her, um [diese Anweisungen](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell)zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="99a38-132">First, connect to AAD with [these instructions](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span></span> 

 <span data-ttu-id="99a38-133">**Hinweis** Sie müssen auf dieser Seite die Option Connect-MsolService verwenden, um den folgenden Befehl verwenden zu können.</span><span class="sxs-lookup"><span data-stu-id="99a38-133">**Note** You need to use the Connect-MsolService option from this page to be able to use the command below.</span></span> 
    
2. <span data-ttu-id="99a38-134">Geben Sie für Ihre Exchange-bezogenen URLs den folgenden Befehl ein:</span><span class="sxs-lookup"><span data-stu-id="99a38-134">For your Exchange related URLs, type the following command:</span></span>
    
```powershell
Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | select -ExpandProperty ServicePrincipalNames
```

<span data-ttu-id="99a38-135">Notieren Sie sich (und Screenshot für den späteren Vergleich) die Ausgabe dieses Befehls, der eine https:// *autodiscover.yourdomain.com* -und https:// *Mail.yourdomain.com* -URL enthalten sollte, aber meistens aus SPNs besteht, die mit 00000002-0000-0ff1-ce00-000000000000/.</span><span class="sxs-lookup"><span data-stu-id="99a38-135">Take note of (and screenshot for later comparison) the output of this command, which should include an https://  *autodiscover.yourdomain.com*  and https://  *mail.yourdomain.com*  URL, but mostly consist of SPNs that begin with 00000002-0000-0ff1-ce00-000000000000/.</span></span> <span data-ttu-id="99a38-136">Wenn Ihre lokalen https://-URLs fehlen, müssen wir diese Datensätze dieser Liste hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="99a38-136">If there are https:// URLs from your on-premises that are missing we will need to add those specific records to this list.</span></span> 
  
3. <span data-ttu-id="99a38-137">Wenn Ihre internen und externen MAPI/http-, EWS-, ActiveSync-, OAB-und autodiscover-Datensätze in dieser Liste nicht angezeigt werden, müssen Sie Sie mithilfe des folgenden Befehls`mail.corp.contoso.com`hinzufügen (`owa.contoso.com`die Beispiel-URLs sind ' ' und ' ', aber Sie würden **die Beispiel-URLs durch ihre eigenen ersetzen** ) :</span><span class="sxs-lookup"><span data-stu-id="99a38-137">If you don't see your internal and external MAPI/HTTP, EWS, ActiveSync, OAB and Autodiscover records in this list, you must add them using the command below (the example URLs are '`mail.corp.contoso.com`' and '`owa.contoso.com`', but you'd **replace the example URLs with your own** ):</span></span> <br/>
```powershell
$x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000   
$x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
$x.ServicePrincipalnames.Add("https://owa.contoso.com/")
$x.ServicePrincipalnames.Add("https://eas.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
 
4. <span data-ttu-id="99a38-138">Überprüfen Sie, ob Ihre neuen Datensätze hinzugefügt wurden, indem Sie den Befehl Get-MsolServicePrincipal erneut aus Schritt 2 ausführen und die Ausgabe durchsuchen.</span><span class="sxs-lookup"><span data-stu-id="99a38-138">Verify your new records were added by running the Get-MsolServicePrincipal command from step 2 again, and looking through the output.</span></span> <span data-ttu-id="99a38-139">Vergleichen Sie die Liste/den Screenshot von before mit der neuen Liste der SPNs (Sie können auch die neue Liste für Ihre Einträge Screenshot).</span><span class="sxs-lookup"><span data-stu-id="99a38-139">Compare the list / screenshot from before to the new list of SPNs (you may also screenshot the new list for your records).</span></span> <span data-ttu-id="99a38-140">Wenn Sie erfolgreich waren, werden die beiden neuen URLs in der Liste angezeigt.</span><span class="sxs-lookup"><span data-stu-id="99a38-140">If you were successful, you will see the two new URLs in the list.</span></span> <span data-ttu-id="99a38-141">In diesem Beispiel enthält die Liste der SPNs nun die spezifischen URLs `https://mail.corp.contoso.com` und. `https://owa.contoso.com`</span><span class="sxs-lookup"><span data-stu-id="99a38-141">Going by our example, the list of SPNs will now include the specific URLs  `https://mail.corp.contoso.com`  and  `https://owa.contoso.com`.</span></span> 
  
## <a name="verify-virtual-directories-are-properly-configured"></a><span data-ttu-id="99a38-142">Sicherstellen, dass virtuelle Verzeichnisse ordnungsgemäß konfiguriert sind</span><span class="sxs-lookup"><span data-stu-id="99a38-142">Verify Virtual Directories are Properly Configured</span></span>

<span data-ttu-id="99a38-143">Vergewissern Sie sich nun, dass OAuth in Exchange in allen virtuellen Verzeichnissen, die Outlook möglicherweise verwendet, ordnungsgemäß aktiviert ist, indem Sie die folgenden Befehle ausführen:</span><span class="sxs-lookup"><span data-stu-id="99a38-143">Now verify OAuth is properly enabled in Exchange on all of the Virtual Directories Outlook might use by running the following commands:</span></span>

```powershell
Get-MapiVirtualDirectory | FL server,*url*,*auth* 
Get-WebServicesVirtualDirectory | FL server,*url*,*oauth*
Get-OABVirtualDirectory | FL server,*url*,*oauth*
Get-AutoDiscoverVirtualDirectory | FL server,*oauth*
```

<span data-ttu-id="99a38-144">Überprüfen Sie die Ausgabe, um sicherzustellen, dass **OAuth** auf jedem dieser VDirs aktiviert ist, sieht es ungefähr wie folgt aus (und das wichtigste, was Sie sehen können, ist "OAuth");</span><span class="sxs-lookup"><span data-stu-id="99a38-144">Check the output to make sure **OAuth** is enabled on each of these VDirs, it will look something like this (and the key thing to look at is 'OAuth');</span></span> 

```powershell
Get-MapiVirtualDirectory | fl server,*url*,*auth*
```

```
Server                        : EX1
InternalUrl                   : https://mail.contoso.com/mapi
ExternalUrl                   : https://mail.contoso.com/mapi
IISAuthenticationMethods      : {Ntlm, OAuth, Negotiate}
InternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
ExternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
```
  
<span data-ttu-id="99a38-145">Wenn OAuth auf einem Server und einem der vier virtuellen Verzeichnisse fehlt, müssen Sie ihn mithilfe der entsprechenden Befehle hinzufügen, bevor Sie fortfahren.</span><span class="sxs-lookup"><span data-stu-id="99a38-145">If OAuth is missing from any server and any of the four virtual directories then you need to add it using the relevant commands before proceeding.</span></span>
  
## <a name="confirm-the-evosts-auth-server-object-is-present"></a><span data-ttu-id="99a38-146">Bestätigen, dass das EvoSTS-Auth-Server Objekt vorhanden ist</span><span class="sxs-lookup"><span data-stu-id="99a38-146">Confirm the EvoSTS Auth Server Object is Present</span></span>

<span data-ttu-id="99a38-147">Kehren Sie zur lokalen Exchange-Verwaltungsshell für diesen letzten Befehl zurück.</span><span class="sxs-lookup"><span data-stu-id="99a38-147">Return to the on-premises Exchange Management Shell for this last command.</span></span> <span data-ttu-id="99a38-148">Jetzt können Sie überprüfen, ob Ihr lokales ein Eintrag für den evoSTS-Authentifizierungsanbieter ist:</span><span class="sxs-lookup"><span data-stu-id="99a38-148">Now you can validate that your on-premises has an entry for the evoSTS authentication provider:</span></span>
  
```powershell
Get-AuthServer | where {$_.Name -eq "EvoSts"}
```

<span data-ttu-id="99a38-149">In der Ausgabe sollte ein AuthServer des Namens EvoSts angezeigt werden, und der Status "Enabled" sollte true sein.</span><span class="sxs-lookup"><span data-stu-id="99a38-149">Your output should show an AuthServer of the Name EvoSts and the 'Enabled' state should be True.</span></span> <span data-ttu-id="99a38-150">Wenn dies nicht der Fall ist, sollten Sie die neueste Version des Assistenten für die Hybrid Konfiguration herunterladen und ausführen.</span><span class="sxs-lookup"><span data-stu-id="99a38-150">If you don't see this, you should download and run the most recent version of the Hybrid Configuration Wizard.</span></span>
  
 <span data-ttu-id="99a38-151">**Wichtig** Wenn Sie Exchange 2010 in Ihrer Umgebung betreiben, wird der EvoSTS-Authentifizierungsanbieter nicht erstellt.</span><span class="sxs-lookup"><span data-stu-id="99a38-151">**Important** If you're running Exchange 2010 in your environment, the EvoSTS authentication provider won't be created.</span></span> 
  
## <a name="enable-hma"></a><span data-ttu-id="99a38-152">HMA aktivieren</span><span class="sxs-lookup"><span data-stu-id="99a38-152">Enable HMA</span></span>

<span data-ttu-id="99a38-153">Führen Sie den folgenden Befehl in der Exchange-Verwaltungsshell aus:</span><span class="sxs-lookup"><span data-stu-id="99a38-153">Run the following command in the Exchange Management Shell, on-premises:</span></span>

```powershell
Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true  
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```
    
## <a name="verify"></a><span data-ttu-id="99a38-154">Prüfen</span><span class="sxs-lookup"><span data-stu-id="99a38-154">Verify</span></span>

<span data-ttu-id="99a38-155">Nachdem Sie HMA aktiviert haben, wird der neue Authentifizierungsablauf von der nächsten Anmeldung des Clients verwendet.</span><span class="sxs-lookup"><span data-stu-id="99a38-155">Once you enable HMA, a client's next login will use the new auth flow.</span></span> <span data-ttu-id="99a38-156">Beachten Sie, dass durch das Aktivieren von HMA keine erneute Authentifizierung für einen Client ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="99a38-156">Note that just turning on HMA won't trigger a re-authentication for any client.</span></span> <span data-ttu-id="99a38-157">Die Clients authentifizieren sich basierend auf der Lebensdauer der auth-Token und/oder certs, die Sie besitzen.</span><span class="sxs-lookup"><span data-stu-id="99a38-157">The clients re-authenticate based on the lifetime of the auth tokens and/or certs they have.</span></span>
  
<span data-ttu-id="99a38-158">Sie sollten auch die STRG-Taste gleichzeitig gedrückt halten, indem Sie mit der rechten Maustaste auf das Symbol für den Outlook-Client (auch im Windows-Benachrichtigungs Fach) klicken und dann auf "Verbindungs Status" klicken.</span><span class="sxs-lookup"><span data-stu-id="99a38-158">You should also hold down the CTRL key at the same time you right click the icon for the Outlook client (also in the Windows Notifications tray) and click 'Connection Status'.</span></span> <span data-ttu-id="99a38-159">Suchen Sie nach der SMTP-Adresse des Clients gegen einen "authn"-Typ von\*"Bearer", der das in OAuth verwendete Bearer-Token darstellt.</span><span class="sxs-lookup"><span data-stu-id="99a38-159">Look for the client's SMTP address against an 'Authn' type of 'Bearer\*', which represents the bearer token used in OAuth.</span></span>
  
 <span data-ttu-id="99a38-160">**Hinweis** Müssen Sie Skype for Business mit HMA konfigurieren?</span><span class="sxs-lookup"><span data-stu-id="99a38-160">**Note** Need to configure Skype for Business with HMA?</span></span> <span data-ttu-id="99a38-161">Sie benötigen zwei Artikel: eine, die die [unterstützten Topologien](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)auflistet, und eine, die Ihnen zeigt, [wie Sie die Konfiguration ausführen](configure-skype-for-business-for-hybrid-modern-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="99a38-161">You'll need two articles: One that lists [supported topologies](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported), and one that shows you [how to do the configuration](configure-skype-for-business-for-hybrid-modern-authentication.md).</span></span>
  

## <a name="related-topics"></a><span data-ttu-id="99a38-162">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="99a38-162">Related topics</span></span>

[<span data-ttu-id="99a38-163">Übersicht über die moderne Hybrid Authentifizierung und Voraussetzungen für die Verwendung mit lokalen Skype for Business-und Exchange-Servern</span><span class="sxs-lookup"><span data-stu-id="99a38-163">Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers</span></span>](hybrid-modern-auth-overview.md) 
  

