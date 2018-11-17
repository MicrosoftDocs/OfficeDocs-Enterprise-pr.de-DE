---
title: Lokale Konfiguration von Exchange Server derart, dass die moderne Hybridauthentifizierung verwendet wird
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 11/16/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: cef3044d-d4cb-4586-8e82-ee97bd3b14ad
description: 'Hybride modernen Authentifizierung (HMA), ist eine Methode über die identitätsverwaltung, die bietet sicherere Benutzerauthentifizierung und-Autorisierung und für hybridbereitstellungen in Exchange Server: lokal verfügbar ist.'
ms.openlocfilehash: df5ea03b06ee1c101b03e19c7acb445c9543586b
ms.sourcegitcommit: 45633b7034ee98d0cd833db9743f283b638237f4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "26547157"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a><span data-ttu-id="3d7a2-103">Lokale Konfiguration von Exchange Server derart, dass die moderne Hybridauthentifizierung verwendet wird</span><span class="sxs-lookup"><span data-stu-id="3d7a2-103">How to configure Exchange Server on-premises to use Hybrid Modern Authentication</span></span>

<span data-ttu-id="3d7a2-104">Hybride modernen Authentifizierung (HMA), ist eine Methode über die identitätsverwaltung, die bietet sicherere Benutzerauthentifizierung und-Autorisierung und für hybridbereitstellungen in Exchange Server: lokal verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="3d7a2-104">Hybrid Modern Authentication (HMA), is a method of identity management that offers more secure user authentication and authorization, and is available for Exchange server on-premises hybrid deployments.</span></span>
  
## <a name="fyi"></a><span data-ttu-id="3d7a2-105">FYI</span><span class="sxs-lookup"><span data-stu-id="3d7a2-105">FYI</span></span>

<span data-ttu-id="3d7a2-106">Bevor wir beginnen, rufen Sie:</span><span class="sxs-lookup"><span data-stu-id="3d7a2-106">Before we begin, I call:</span></span>
  
- <span data-ttu-id="3d7a2-107">Hybride modernen Authentifizierung \> HMA</span><span class="sxs-lookup"><span data-stu-id="3d7a2-107">Hybrid Modern Authentication \> HMA</span></span>
    
- <span data-ttu-id="3d7a2-108">Der lokale Exchange \> EXCH</span><span class="sxs-lookup"><span data-stu-id="3d7a2-108">Exchange on-premises \> EXCH</span></span>
    
- <span data-ttu-id="3d7a2-109">Exchange Online \> EXO</span><span class="sxs-lookup"><span data-stu-id="3d7a2-109">Exchange Online \> EXO</span></span>
    
<span data-ttu-id="3d7a2-110">Auch *Wenn eine Grafik in diesem Artikel ein Objekt hat, ist "grau" oder "abgeblendet", bedeutet dies, dass das Element grau dargestellt in HMA-spezifische Konfiguration nicht enthalten ist* .</span><span class="sxs-lookup"><span data-stu-id="3d7a2-110">Also,  *if a graphic in this article has an object that's 'grayed-out' or 'dimmed' that means the element shown in gray is not included in HMA-specific configuration*  .</span></span> 
  
## <a name="enabling-hybrid-modern-authentication"></a><span data-ttu-id="3d7a2-111">Aktivieren der modernen Hybrid-Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="3d7a2-111">Enabling Hybrid Modern Authentication</span></span>

<span data-ttu-id="3d7a2-112">Aktivieren der HMA bedeutet:</span><span class="sxs-lookup"><span data-stu-id="3d7a2-112">Turning HMA on means:</span></span>
  
1. <span data-ttu-id="3d7a2-113">Wird sicher, dass Sie die Prereqs erfüllen, bevor Sie beginnen.</span><span class="sxs-lookup"><span data-stu-id="3d7a2-113">Being sure you meet the prereqs before you begin.</span></span>
    
1. <span data-ttu-id="3d7a2-p101">Seit vielen **Voraussetzungen** gelten für beide Skype für Unternehmen und Exchange, [moderne Hybrid-Authentifizierung (Übersicht) und Voraussetzungen für die Verwendung mit lokalen Skype für Geschäfts- und Exchange Server](hybrid-modern-auth-overview.md). Hierzu, bevor Sie die Schritte in diesem Artikel beginnen.</span><span class="sxs-lookup"><span data-stu-id="3d7a2-p101">Since many **prerequisites** are common for both Skype for Business and Exchange, [Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers](hybrid-modern-auth-overview.md). Do this before you begin any of the steps in this article.</span></span>
    
2. <span data-ttu-id="3d7a2-116">Hinzufügen von lokalen Webdienst-URLs als Dienstprinzipalnamen (SPNs) in Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="3d7a2-116">Adding on-premises web service URLs as Service Principal Names (SPNs) in Azure AD.</span></span>
    
3. <span data-ttu-id="3d7a2-117">Sicherstellen, dass alle virtuellen Verzeichnisse für HMA aktiviert sind</span><span class="sxs-lookup"><span data-stu-id="3d7a2-117">Ensuring all Virtual Directories are enabled for HMA</span></span>
    
4. <span data-ttu-id="3d7a2-118">Überprüfen für das Objekt EvoSTS Authentifizierungsserver</span><span class="sxs-lookup"><span data-stu-id="3d7a2-118">Checking for the EvoSTS Auth Server object</span></span>
    
5. <span data-ttu-id="3d7a2-119">Aktivieren der HMA in Wechselkurs</span><span class="sxs-lookup"><span data-stu-id="3d7a2-119">Enabling HMA in EXCH.</span></span>
    
 <span data-ttu-id="3d7a2-p102">**Hinweis** Unterstützt Ihre Version von Office MA? Finden Sie unter [wie modernen Funktionsweise der Authentifizierung für apps für Office 2013 und Office 2016 Client](modern-auth-for-office-2013-and-2016.md).</span><span class="sxs-lookup"><span data-stu-id="3d7a2-p102">**Note** Does your version of Office support MA? See [How modern authentication works for Office 2013 and Office 2016 client apps](modern-auth-for-office-2013-and-2016.md).</span></span>
  
## <a name="make-sure-you-meet-all-the-pre-reqs"></a><span data-ttu-id="3d7a2-122">Stellen Sie sicher, dass Sie alle die Pre-Reqs erfüllen</span><span class="sxs-lookup"><span data-stu-id="3d7a2-122">Make sure you meet all the pre-reqs</span></span>

<span data-ttu-id="3d7a2-p103">Da viele erforderliche Komponenten für beide Skype für Unternehmen und Exchange ausgeführt werden, prüfen Sie [modernen Hybrid-Authentifizierung (Übersicht) und erforderliche Komponenten für die Verwendung mit lokalen Skype für Geschäfts- und Exchange Server](hybrid-modern-auth-overview.md). Führen Sie diese *vor dem* Beginn der Schritte in diesem Artikel.</span><span class="sxs-lookup"><span data-stu-id="3d7a2-p103">Since many prerequisites are common for both Skype for Business and Exchange, review [Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers](hybrid-modern-auth-overview.md). Do this  *before*  you begin any of the steps in this article.</span></span> 
  
## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a><span data-ttu-id="3d7a2-125">Hinzufügen von lokalen web Service URLs als Dienstprinzipalnamen (SPNs) in Azure AD</span><span class="sxs-lookup"><span data-stu-id="3d7a2-125">Add on-premises web service URLs as SPNs in Azure AD</span></span>

<span data-ttu-id="3d7a2-p104">Führen Sie die Befehle, die Ihre lokalen Web Service URLs zuweisen, wie Azure AD SPNs. Dienstprinzipalnamen (SPNs) während der Authentifizierung und Autorisierung von Clientcomputer und Geräte verwendet werden. Alle URLs, die verwendet werden können, von lokalen Azure Active Directory (AAD) herstellen müssen im AAD registriert werden (dazu gehören interne und externe Namespaces).</span><span class="sxs-lookup"><span data-stu-id="3d7a2-p104">Run the commands that assign your on-premises web service URLs as Azure AD SPNs. SPNs are used by client machines and devices during authentication and authorization. All the URLs that might be used to connect from on-premises to Azure Active Directory (AAD) must be registered in AAD (this includes both internal and external namespaces).</span></span>
  
<span data-ttu-id="3d7a2-p105">Sammeln Sie zuerst die URLs, die Sie benötigen, um in AAD hinzuzufügen. Diese Befehle: lokal ausführen:</span><span class="sxs-lookup"><span data-stu-id="3d7a2-p105">First, gather all the URLs that you need to add in AAD. Run these commands on-premises:</span></span>
  
```powershell
Get-MapiVirtualDirectory | FL server,*url*
Get-WebServicesVirtualDirectory | FL server,*url*
Get-ActiveSyncVirtualDirectory | FL server,*url*
Get-OABVirtualDirectory | FL server,*url*
```
    
<span data-ttu-id="3d7a2-131">Vergewissern Sie sich die URLs Clients eine Verbindung herstellen können, als HTTPS Dienstprinzipalnamen in AAD aufgeführt sind.</span><span class="sxs-lookup"><span data-stu-id="3d7a2-131">Ensure the URLs clients may connect to are listed as HTTPS service principal names in AAD.</span></span>
  
1. <span data-ttu-id="3d7a2-132">Schließen Sie zuerst AAD mit [diese Anweisungen](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span><span class="sxs-lookup"><span data-stu-id="3d7a2-132">First, connect to AAD with [these instructions](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span></span> 

 <span data-ttu-id="3d7a2-133">**Hinweis** Sie müssen die Option Connect-MsolService auf dieser Seite verwenden, um den unten angegebenen Befehl verwenden zu können.</span><span class="sxs-lookup"><span data-stu-id="3d7a2-133">**Note** You need to use the Connect-MsolService option from this page to be able to use the command below.</span></span> 
    
2. <span data-ttu-id="3d7a2-134">Geben den folgenden Befehl, für die Exchange-verwandter URLs:</span><span class="sxs-lookup"><span data-stu-id="3d7a2-134">For your Exchange related URLs, type the following command:</span></span>
    
```powershell
Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | select -ExpandProperty ServicePrincipalNames
```

<span data-ttu-id="3d7a2-p106">Übernehmen Sie notieren Sie (und Screenshot für den späteren Vergleich) die Ausgabe dieses Befehls sollten ein https:// *autodiscover.yourdomain.com* und https:// *Mail* URL enthalten hauptsächlich aus Dienstprinzipalnamen (SPNs), die beginnen bestehen mit 00000002-0000-0ff1-CE00-000000000000 /. Wenn https:// URLs aus dem lokalen, die fehlen vorhanden sind, müssen wir die bestimmte Datensätze zu dieser Liste hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="3d7a2-p106">Take note of (and screenshot for later comparison) the output of this command, which should include an https://  *autodiscover.yourdomain.com*  and https://  *mail.yourdomain.com*  URL, but mostly consist of SPNs that begin with 00000002-0000-0ff1-ce00-000000000000/. If there are https:// URLs from your on-premises that are missing we will need to add those specific records to this list.</span></span> 
  
3. <span data-ttu-id="3d7a2-137">Wenn Sie Ihre interne und externe MAPI/HTTP, EWS, ActiveSync, OAB und AutoErmittlung-Einträge in dieser Liste nicht angezeigt wird, müssen Sie sie über den unten angegebenen Befehl hinzufügen (im Beispiel URLs sind '`mail.corp.contoso.com`'und'`owa.contoso.com`', aber **die Beispiel-URLs durch Ihren eigenen ersetzen** ) :</span><span class="sxs-lookup"><span data-stu-id="3d7a2-137">If you don't see your internal and external MAPI/HTTP, EWS, ActiveSync, OAB and Autodiscover records in this list, you must add them using the command below (the example URLs are '`mail.corp.contoso.com`' and '`owa.contoso.com`', but you'd **replace the example URLs with your own** ):</span></span> <br/>
```powershell
$x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000   
$x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
$x.ServicePrincipalnames.Add("https://owa.contoso.com/")
$x.ServicePrincipalnames.Add("https://eas.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
 
4. <span data-ttu-id="3d7a2-p107">Stellen Sie sicher, dass Ihre neue Datensätze hinzugefügt wurden, mithilfe des Befehls Get-MsolServicePrincipal aus Schritt 2 erneut aus, und Durchsuchen Sie die Ausgabe. Vergleichen Sie die Liste / Screenshot vor der neuen Liste der Dienstprinzipalnamen (SPNs) (können Sie auch die neue Liste Screenshot für Ihre Unterlagen). Wenn Sie erfolgreich waren, sehen Sie die beiden neuen URLs in der Liste. Wechseln von unserem Beispiel, die Liste der SPNs wird enthalten nun die bestimmte URLs `https://mail.corp.contoso.com` und `https://owa.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="3d7a2-p107">Verify your new records were added by running the Get-MsolServicePrincipal command from step 2 again, and looking through the output. Compare the list / screenshot from before to the new list of SPNs (you may also screenshot the new list for your records). If you were successful, you will see the two new URLs in the list. Going by our example, the list of SPNs will now include the specific URLs  `https://mail.corp.contoso.com`  and  `https://owa.contoso.com`.</span></span> 
  
## <a name="verify-virtual-directories-are-properly-configured"></a><span data-ttu-id="3d7a2-142">Überprüfen Sie, ob die virtuellen Verzeichnisse ordnungsgemäß konfiguriert sind.</span><span class="sxs-lookup"><span data-stu-id="3d7a2-142">Verify Virtual Directories are Properly Configured</span></span>

<span data-ttu-id="3d7a2-143">Vergewissern Sie sich jetzt OAuth ordnungsgemäß aktiviert ist, Exchange auf allen virtuellen Verzeichnisse Outlook möglicherweise verwenden, indem Sie die folgenden Befehle ausführen:</span><span class="sxs-lookup"><span data-stu-id="3d7a2-143">Now verify OAuth is properly enabled in Exchange on all of the Virtual Directories Outlook might use by running the following commands:</span></span>

```powershell
Get-MapiVirtualDirectory | FL server,*url*,*auth* 
Get-WebServicesVirtualDirectory | FL server,*url*,*oauth*
Get-OABVirtualDirectory | FL server,*url*,*oauth*
Get-AutoDiscoverVirtualDirectory | FL server,*oauth*
```

<span data-ttu-id="3d7a2-144">Die Ausgabe, stellen Sie sicher, dass **OAuth** Kontrollkästchen aktiviert ist auf jedem dieser VDirs, sieht etwa wie folgt (und unbedingt betrachten "OAuth");</span><span class="sxs-lookup"><span data-stu-id="3d7a2-144">Check the output to make sure **OAuth** is enabled on each of these VDirs, it will look something like this (and the key thing to look at is 'OAuth');</span></span> 

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
  
<span data-ttu-id="3d7a2-145">Wenn OAuth aus einem beliebigen Server und vier virtuelle Verzeichnisse fehlt, müssen Sie es über die relevanten Befehle vor dem Fortfahren hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="3d7a2-145">If OAuth is missing from any server and any of the four virtual directories then you need to add it using the relevant commands before proceeding.</span></span>
  
## <a name="confirm-the-evosts-auth-server-object-is-present"></a><span data-ttu-id="3d7a2-146">Vergewissern Sie sich, dass das Objekt EvoSTS Auth Server vorhanden ist</span><span class="sxs-lookup"><span data-stu-id="3d7a2-146">Confirm the EvoSTS Auth Server Object is Present</span></span>

<span data-ttu-id="3d7a2-p108">Geben Sie an der lokalen Exchange-Verwaltungsshell für diesen letzten Befehl. Jetzt können Sie überprüfen, ob Ihre lokale enthält einen Eintrag für den EvoSTS Authentifizierungsanbieter:</span><span class="sxs-lookup"><span data-stu-id="3d7a2-p108">Return to the on-premises Exchange Management Shell for this last command. Now you can validate that your on-premises has an entry for the evoSTS authentication provider:</span></span>
  
```powershell
Get-AuthServer | where {$_.Name -eq "EvoSts"}
```

<span data-ttu-id="3d7a2-p109">Die Ausgabe sollte ein AuthServer, der den Namen EvoSts anzeigen und der Status "Aktiviert" muss auf True festgelegt sein. Wenn dies nicht angezeigt wird, sollten Sie herunterladen und Ausführen die neueste Version von the Hybrid Configuration Wizard.</span><span class="sxs-lookup"><span data-stu-id="3d7a2-p109">Your output should show an AuthServer of the Name EvoSts and the 'Enabled' state should be True. If you don't see this, you should download and run the most recent version of the Hybrid Configuration Wizard.</span></span>
  
 <span data-ttu-id="3d7a2-151">**Wichtige** Wenn Sie Exchange 2010 in Ihrer Umgebung ausführen, werden nicht EvoSTS Authentifizierungsanbieter erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="3d7a2-151">**Important** If you're running Exchange 2010 in your environment, the EvoSTS authentication provider won't be created.</span></span> 
  
## <a name="enable-hma"></a><span data-ttu-id="3d7a2-152">HMA aktivieren</span><span class="sxs-lookup"><span data-stu-id="3d7a2-152">Enable HMA</span></span>

<span data-ttu-id="3d7a2-153">Führen Sie den folgenden Befehl in der Exchange-Verwaltungsshell: lokal aus:</span><span class="sxs-lookup"><span data-stu-id="3d7a2-153">Run the following command in the Exchange Management Shell, on-premises:</span></span>

```powershell
Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true  
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```
    
## <a name="verify"></a><span data-ttu-id="3d7a2-154">„Bestätigen“,</span><span class="sxs-lookup"><span data-stu-id="3d7a2-154">Verify</span></span>

<span data-ttu-id="3d7a2-p110">Nachdem Sie HMA aktivieren, wird nächsten Anmeldung des Clients den neuen Auth Fluss verwenden. Beachten Sie, dass auf HMA einschalten eine erneute Authentifizierung für Clients ausgelöst werden nicht. Die Clients erneut authentifizieren basierend auf der Lebensdauer des Auth Token und/oder der Zertifikate, die sie besitzen.</span><span class="sxs-lookup"><span data-stu-id="3d7a2-p110">Once you enable HMA, a client's next login will use the new auth flow. Note that just turning on HMA won't trigger a re-authentication for any client. The clients re-authenticate based on the lifetime of the auth tokens and/or certs they have.</span></span>
  
<span data-ttu-id="3d7a2-p111">Sie sollten auch halten Sie die STRG-Taste zur selben Zeit Sie rechten Maustaste auf das Symbol für den Outlook-Client (auch in der Benachrichtigungen über die Windows-Taskleiste) klicken, und klicken Sie auf 'Verbindungsstatus'. Suchen Sie nach der Client-SMTP-Adresse gegen vom Typ 'Authn' von ' Bearer\*', darstellt, das Bearer Token in OAuth verwendet.</span><span class="sxs-lookup"><span data-stu-id="3d7a2-p111">You should also hold down the CTRL key at the same time you right click the icon for the Outlook client (also in the Windows Notifications tray) and click 'Connection Status'. Look for the client's SMTP address against an 'Authn' type of 'Bearer\*', which represents the bearer token used in OAuth.</span></span>
  
 <span data-ttu-id="3d7a2-p112">**Hinweis** So konfigurieren Sie Skype für Unternehmen mit HMA erforderlich? Benötigen Sie zwei Artikel: eine, die Listen der [unterstützten Topologien](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)und eine, die Sie zeigt, [wie Sie die Konfiguration vornehmen](configure-skype-for-business-for-hybrid-modern-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="3d7a2-p112">**Note** Need to configure Skype for Business with HMA? You'll need two articles: One that lists [supported topologies](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported), and one that shows you [how to do the configuration](configure-skype-for-business-for-hybrid-modern-authentication.md).</span></span>
  

## <a name="related-topics"></a><span data-ttu-id="3d7a2-162">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="3d7a2-162">Related topics</span></span>

[<span data-ttu-id="3d7a2-163">Hybride modernen Authentifizierung (Übersicht) und Voraussetzungen für die Verwendung mit lokalen Skype für Geschäfts- und Exchange Server</span><span class="sxs-lookup"><span data-stu-id="3d7a2-163">Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers</span></span>](hybrid-modern-auth-overview.md) 
  

