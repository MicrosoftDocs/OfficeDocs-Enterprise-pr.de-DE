---
title: Lokale hybride modernen Authentifizierung zum Konfigurieren von Skype für Unternehmen
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 6/4/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 522d5cec-4e1b-4cc3-937f-293570717bc6
description: Moderne Authentifizierung ist eine Methode über die identitätsverwaltung, die sicherere Benutzerauthentifizierung und-Autorisierung bietet, ist für Skype für Business Server lokal und Exchange Server lokal als auch Split-Domäne Skype für Business Hybriden verfügbar.
ms.openlocfilehash: 48ce10022e384ec88b88c0e8ec038bf201adc707
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541071"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a><span data-ttu-id="bff7f-103">Lokale hybride modernen Authentifizierung zum Konfigurieren von Skype für Unternehmen</span><span class="sxs-lookup"><span data-stu-id="bff7f-103">How to configure Skype for Business on-premises to use Hybrid Modern Authentication</span></span>

<span data-ttu-id="bff7f-104">Moderne Authentifizierung ist eine Methode über die identitätsverwaltung, die sicherere Benutzerauthentifizierung und-Autorisierung bietet, ist für Skype für Business Server lokal und Exchange Server lokal als auch Split-Domäne Skype für Business Hybriden verfügbar.</span><span class="sxs-lookup"><span data-stu-id="bff7f-104">Modern Authentication, is a method of identity management that offers more secure user authentication and authorization, is available for Skype for Business server on-premises and Exchange server on-premises, as well as split-domain Skype for Business hybrids.</span></span>
  
 <span data-ttu-id="bff7f-p101">**Wichtige** Möchten Sie wissen, Weitere Informationen zu modernen Authentifizierung (MA) und warum empfiehlt sich möglicherweise für die Verwendung in Ihrer Firma oder Organisation? [In diesem Dokument](hybrid-modern-auth-overview.md) finden Sie eine Übersicht überprüfen. Wenn Sie benötigen, welche Skype wissen für Business Topologien mit MA, unterstützt werden, die hier dokumentiert ist!</span><span class="sxs-lookup"><span data-stu-id="bff7f-p101">**Important** Would you like to know more about Modern Authentication (MA) and why you might prefer to use it in your company or organization? Check [this document](hybrid-modern-auth-overview.md) for an overview. If you need to know what Skype for Business topologies are supported with MA, that's documented here!</span></span> 
  
 <span data-ttu-id="bff7f-108">**Bevor wir beginnen**, rufen Sie:</span><span class="sxs-lookup"><span data-stu-id="bff7f-108">**Before we begin**, I call:</span></span> 
  
- <span data-ttu-id="bff7f-109">Moderne Authentifizierung \> MA</span><span class="sxs-lookup"><span data-stu-id="bff7f-109">Modern Authentication \> MA</span></span>
    
- <span data-ttu-id="bff7f-110">Hybride modernen Authentifizierung \> HMA</span><span class="sxs-lookup"><span data-stu-id="bff7f-110">Hybrid Modern Authentication \> HMA</span></span>
    
- <span data-ttu-id="bff7f-111">Der lokale Exchange \> EXCH</span><span class="sxs-lookup"><span data-stu-id="bff7f-111">Exchange on-premises \> EXCH</span></span>
    
- <span data-ttu-id="bff7f-112">Exchange Online \> EXO</span><span class="sxs-lookup"><span data-stu-id="bff7f-112">Exchange Online \> EXO</span></span>
    
- <span data-ttu-id="bff7f-113">Skype für Business lokal \> SFB</span><span class="sxs-lookup"><span data-stu-id="bff7f-113">Skype for Business on-premises \> SFB</span></span>
    
- <span data-ttu-id="bff7f-114">und Skype für Unternehmen Online \> SFBO</span><span class="sxs-lookup"><span data-stu-id="bff7f-114">and Skype for Business Online \> SFBO</span></span>
    
<span data-ttu-id="bff7f-115">Darüber hinaus \* besitzt eine Grafik in diesem Artikel ein Objekt, das "grau" 'abgeblendet' oder hat, die bedeutet, das Element in Grau **ist nicht** enthalten in MA-spezifische Konfiguration dargestellt dass.</span><span class="sxs-lookup"><span data-stu-id="bff7f-115">Also,  \*if a graphic in this article has an object that's 'grayed-out' or 'dimmed' that means the element shown in gray **is not** included in MA-specific configuration.</span></span> * 
  
## <a name="read-the-summary"></a><span data-ttu-id="bff7f-116">Lesen Sie die Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="bff7f-116">Read the summary</span></span>

<span data-ttu-id="bff7f-117">Diese Zusammenfassung macht den Prozess in Schritte, die möglicherweise während der Ausführung andernfalls verloren abrufen, und eignet sich für eine allgemeine Checkliste nachverfolgen, wo Sie in dem Prozess befinden.</span><span class="sxs-lookup"><span data-stu-id="bff7f-117">This summary boils the process into steps that might otherwise get lost during the execution, and is good for an overall check-list to keep track of where you are in the process.</span></span>
  
1. <span data-ttu-id="bff7f-118">Stellen Sie zunächst sicher, dass Sie alle erforderlichen Komponenten erfüllen.</span><span class="sxs-lookup"><span data-stu-id="bff7f-118">First, make sure you meet all the prerequisites.</span></span>
    
1. <span data-ttu-id="bff7f-p102">Seit vielen **Voraussetzungen** gelten für beide Skype für Unternehmen und Exchange, [finden Sie in dem Artikel für die Bereitstellungsprüfliste Voraussetzung](hybrid-modern-auth-overview.md). Führen Sie diese *vor dem* Beginn der Schritte in diesem Artikel.</span><span class="sxs-lookup"><span data-stu-id="bff7f-p102">Since many **prerequisites** are common for both Skype for Business and Exchange, [see the overview article for your pre-req checklist](hybrid-modern-auth-overview.md). Do this  *before*  you begin any of the steps in this article.</span></span> 
    
2. <span data-ttu-id="bff7f-121">Sammeln Sie die HMA-spezifische Informationen, die Sie in einer Datei oder OneNote benötigen.</span><span class="sxs-lookup"><span data-stu-id="bff7f-121">Collect the HMA-specific info you'll need in a file, or OneNote.</span></span>
    
3. <span data-ttu-id="bff7f-122">Aktivieren Sie auf modernen Authentifizierung für EXO (sofern sie nicht bereits aktiviert ist).</span><span class="sxs-lookup"><span data-stu-id="bff7f-122">Turn ON Modern Authentication for EXO (if it is not already turned on).</span></span>
    
4. <span data-ttu-id="bff7f-123">Aktivieren Sie auf modernen Authentifizierung für SFBO (sofern sie nicht bereits aktiviert ist).</span><span class="sxs-lookup"><span data-stu-id="bff7f-123">Turn ON Modern Authentication for SFBO (if it is not already turned on).</span></span>
    
5. <span data-ttu-id="bff7f-124">Moderne Hybrid-Authentifizierung für lokale Exchange-Organisation zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="bff7f-124">Turn ON Hybrid Modern Authentication for Exchange on-premises.</span></span>
    
6. <span data-ttu-id="bff7f-125">Aktivieren der modernen Hybrid-Authentifizierung für Skype für Business lokal.</span><span class="sxs-lookup"><span data-stu-id="bff7f-125">Turn ON Hybrid Modern Authentication for Skype for Business on-premises.</span></span>
    
<span data-ttu-id="bff7f-p103">Hinweis: Diese Schritte MA für SFB, SFBO, EXCH und EXO – d. h., alle Produkte aktivieren, die in einer Konfiguration HMA SFB und SFBO (einschließlich Abhängigkeiten von EXCH/EXO) teilnehmen können. Anders ausgedrückt, wird, wenn die Benutzer sich in befinden / Postfächer in einem Teil des der Hybrid (EXO + SFBO, EXO + SFB, EXCH + SFBO, oder EXCH + SFB erstellten), Ihre Fertigprodukt wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="bff7f-p103">Note These steps turn on MA for SFB, SFBO, EXCH, and EXO -- that is, all the products that can participate in a HMA configuration of SFB and SFBO (including dependencies on EXCH/EXO). In other words, if your users are homed in/have mailboxes created in any part of the Hybrid (EXO + SFBO, EXO + SFB, EXCH + SFBO, or EXCH + SFB), your finished product will look like this:</span></span>
  
![Eine gemischte 6 Skype für Business HMA Topologie verfügt über Verwaltungs-Agent für alle vier mögliche Speicherorte.](media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)
  
<span data-ttu-id="bff7f-p104">Wie Sie, dass es gibt vier unterschiedliche Standorten sehen können auf Verwaltungs-Agent zu aktivieren. Die beste benutzerumgebung wird empfohlen, dass Sie in diesen Speicherorten alle vier-Verwaltungs-Agent zu aktivieren. Wenn Sie MA in alle Speicherorte einschalten ist nicht möglich, passen Sie die Schritte aus, damit Sie nur in den Speicherorten-Verwaltungs-Agent zu aktivieren, die für Ihre Umgebung erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="bff7f-p104">As you can see there are four different places to turn on MA! For the best user experience we recommend you turn on MA in all four of these locations. If you can't turn MA on in all these locations, adjust the steps so that you turn on MA only in the locations that are necessary for your environment.</span></span>
  
<span data-ttu-id="bff7f-132">Finden Sie im [Thema Skype für Unternehmen mit MA Supportability](https://technet.microsoft.com/en-us/library/mt803262.aspx) für unterstützte Topologien.</span><span class="sxs-lookup"><span data-stu-id="bff7f-132">See the [Supportability topic for Skype for Business with MA](https://technet.microsoft.com/en-us/library/mt803262.aspx) for supported topologies.</span></span> 
  
 <span data-ttu-id="bff7f-p105">**Wichtige** Überprüfen Sie, dass Sie alle erforderlichen Komponenten erfüllt, bevor Sie beginnen. Diese Informationen finden Sie [hier](hybrid-modern-auth-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bff7f-p105">**Important** Double-check that you've met all the prerequisites before you begin. You'll find that information [here](hybrid-modern-auth-overview.md).</span></span>
  
## <a name="collect-all-hma-specific-info-youll-need"></a><span data-ttu-id="bff7f-135">Sammeln Sie alle HMA-spezifische Informationen, die Sie benötigen</span><span class="sxs-lookup"><span data-stu-id="bff7f-135">Collect all HMA-specific info you'll need</span></span>

<span data-ttu-id="bff7f-p106">Nachdem Sie, die sich vergewissert haben Sie erfüllen modernen-Authentifizierung verwenden, um die [erforderlichen Komponenten](hybrid-modern-auth-overview.md) (siehe Hinweis oben), erstellen Sie eine Datei, um die Informationen zum Konfigurieren von HMA in den folgenden Schritten müssen halten. Die Beispiele in diesem Artikel verwendet:</span><span class="sxs-lookup"><span data-stu-id="bff7f-p106">After you've double-checked that you meet the [prerequisites](hybrid-modern-auth-overview.md) to use Modern Authentication (see the note above), you should create a file to hold the info you'll need for configuring HMA in the steps ahead. Examples used in this article:</span></span> 
  
- <span data-ttu-id="bff7f-138">**SIP/SMTP-Domäne**</span><span class="sxs-lookup"><span data-stu-id="bff7f-138">**SIP/SMTP domain**</span></span>
    
  - <span data-ttu-id="bff7f-p107">Z. B. "contoso.com" (wird mit Office 365 Verbund)</span><span class="sxs-lookup"><span data-stu-id="bff7f-p107">Ex. contoso.com (is federated with Office 365)</span></span>
    
- <span data-ttu-id="bff7f-141">**Mandanten-ID**</span><span class="sxs-lookup"><span data-stu-id="bff7f-141">**Tenant ID**</span></span>
    
  - <span data-ttu-id="bff7f-142">Die GUID, die Ihre Office 365-Mandanten (bei der Anmeldung von contoso.onmicrosoft.com) darstellt.</span><span class="sxs-lookup"><span data-stu-id="bff7f-142">The GUID that represents your Office 365 tenant (at the login of contoso.onmicrosoft.com).</span></span>
    
- <span data-ttu-id="bff7f-143">**SFB 2015 CU5 Webdienst-URLs**</span><span class="sxs-lookup"><span data-stu-id="bff7f-143">**SFB 2015 CU5 Web Service URLs**</span></span>
    
<span data-ttu-id="bff7f-p108">Sie benötigen des internen und externen Webdienst-URL für alle SfB 2015 Pools bereitgestellt. Um diese zu erhalten, führen Sie den folgenden von Skype für Business-Verwaltungsshell aus:</span><span class="sxs-lookup"><span data-stu-id="bff7f-p108">You will need internal and external web service URL's for all SfB 2015 pools deployed. To obtain these, run the following from Skype for Business Management Shell:</span></span>
  
<span data-ttu-id="bff7f-146">Get-CsService - WebServer | Select-Object PoolFqdn, InternalFqdn, Externerfqdn | FL</span><span class="sxs-lookup"><span data-stu-id="bff7f-146">Get-CsService -WebServer | Select-Object PoolFqdn, InternalFqdn, ExternalFqdn | FL</span></span>
  
- <span data-ttu-id="bff7f-p109">Interne z. B.:https://lyncwebint01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="bff7f-p109">Ex. Internal: https://lyncwebint01.contoso.com</span></span>
    
- <span data-ttu-id="bff7f-p110">Kurs extern:https://lyncwebext01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="bff7f-p110">Ex. External: https://lyncwebext01.contoso.com</span></span>
    
<span data-ttu-id="bff7f-p111">Wenn Sie einen Standard Edition-Server verwenden, wird die interne URL leer sein. In diesem Fall verwenden Sie den Pool-Fqdn für die interne URL.</span><span class="sxs-lookup"><span data-stu-id="bff7f-p111">If you are using a Standard Edition server, the internal URL will be blank. In this case, use the pool fqdn for the internal URL.</span></span>
  
## <a name="turn-on-modern-authentication-for-exo"></a><span data-ttu-id="bff7f-153">Aktivieren der modernen Authentifizierung für EXO</span><span class="sxs-lookup"><span data-stu-id="bff7f-153">Turn on Modern Authentication for EXO</span></span>

<span data-ttu-id="bff7f-154">Befolgen Sie die Anweisungen hier: [Exchange Online: zum Aktivieren des Mandanten für moderne Authentifizierung von.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)</span><span class="sxs-lookup"><span data-stu-id="bff7f-154">Follow the instructions here: [Exchange Online: How to enable your tenant for modern authentication.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)</span></span>
  
## <a name="turn-on-modern-authentication-for-sfbo"></a><span data-ttu-id="bff7f-155">Aktivieren der modernen Authentifizierung für SFBO</span><span class="sxs-lookup"><span data-stu-id="bff7f-155">Turn on Modern Authentication for SFBO</span></span>

<span data-ttu-id="bff7f-156">Befolgen Sie die Anweisungen hier: [Skype für Business Online: Aktivieren Ihres Mandanten für die Authentifizierung modernen](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).</span><span class="sxs-lookup"><span data-stu-id="bff7f-156">Follow the instructions here: [Skype for Business Online: Enable your tenant for modern authentication](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a><span data-ttu-id="bff7f-157">Aktivieren der Hybrid modernen Authentifizierung für Exchange lokal</span><span class="sxs-lookup"><span data-stu-id="bff7f-157">Turn on Hybrid Modern Authentication for Exchange on-premises</span></span>

<span data-ttu-id="bff7f-158">Befolgen Sie die Anweisungen hier: [Exchange Server lokal Hybrid modernen-Authentifizierung konfigurieren](configure-exchange-server-for-hybrid-modern-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="bff7f-158">Follow the instructions here: [How to configure Exchange Server on-premises to use Hybrid Modern Authentication](configure-exchange-server-for-hybrid-modern-authentication.md).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a><span data-ttu-id="bff7f-159">Aktivieren Sie für Business lokal modernen Hybrid-Authentifizierung für Skype</span><span class="sxs-lookup"><span data-stu-id="bff7f-159">Turn on Hybrid Modern Authentication for Skype for Business on-premises</span></span>

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a><span data-ttu-id="bff7f-160">Hinzufügen von lokalen web Service URLs als Dienstprinzipalnamen (SPNs) in Azure AD</span><span class="sxs-lookup"><span data-stu-id="bff7f-160">Add on-premises web service URLs as SPNs in Azure AD</span></span>

<span data-ttu-id="bff7f-161">Jetzt müssen Sie Befehle ausführen, um die URLs (zuvor gesammelten) als Dienstprinzipale in SFBO hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="bff7f-161">Now you'll need to run commands to add the URLs (collected earlier) as Service Principals in SFBO.</span></span>
  
 <span data-ttu-id="bff7f-p112">**Hinweis** Service Dienstprinzipalnamen (SPNs) Identifizieren von Webdiensten und zuordnen, ein Sicherheitsprinzipal (beispielsweise ein Kontonamen oder eine Gruppe), damit der Dienst auf den Namen eines autorisierten Benutzers übernehmen kann. Clients authentifiziert sich gegenüber einem Server stellen Informationen, die in enthaltenen Dienstprinzipalnamen (SPNs) verwenden.</span><span class="sxs-lookup"><span data-stu-id="bff7f-p112">**Note** Service principal names (SPNs) identify web services and associate them with a security principal (such as an account name or group) so that the service can act on the behalf of an authorized user. Clients authenticating to a server make use of information that's contained in SPNs.</span></span> 
  
1. <span data-ttu-id="bff7f-164">Schließen Sie zuerst AAD mit [diese Anweisungen](https://docs.microsoft.com/en-us/powershell/azure/active-directory/install-adv2?view=azureadps-2.0).</span><span class="sxs-lookup"><span data-stu-id="bff7f-164">First, connect to AAD with [these instructions](https://docs.microsoft.com/en-us/powershell/azure/active-directory/install-adv2?view=azureadps-2.0).</span></span>
    
2. <span data-ttu-id="bff7f-165">Führen Sie diesen Befehl lokal, um eine Liste der Webdienst-URLs SFB abzurufen.</span><span class="sxs-lookup"><span data-stu-id="bff7f-165">Run this command, on-premises, to get a list of SFB web service URLs.</span></span>
    
  - <span data-ttu-id="bff7f-166">Get-MsolServicePrincipal - AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Select - ExpandProperty ServicePrincipalNames</span><span class="sxs-lookup"><span data-stu-id="bff7f-166">Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Select -ExpandProperty ServicePrincipalNames</span></span>
    
    <span data-ttu-id="bff7f-p113">Beachten Sie, dass die AppPrincipalId mit "00000004" beginnt. Dies entspricht Skype für Business Online.</span><span class="sxs-lookup"><span data-stu-id="bff7f-p113">Notice that the AppPrincipalId begins with '00000004'. This corresponds to Skype for Business Online.</span></span>
    
    <span data-ttu-id="bff7f-169">Nehmen Sie notieren (und Screenshot für den späteren Vergleich) die Ausgabe dieses Befehls wird ein SE und WS-URL enthalten bestehen hauptsächlich aus Dienstprinzipalnamen (SPNs), die mit 00000004-0000-0ff1-ce00-000000000000 beginnen /.</span><span class="sxs-lookup"><span data-stu-id="bff7f-169">Take note of (and screenshot for later comparison) the output of this command, which will include an SE and WS URL, but mostly consist of SPNs that begin with 00000004-0000-0ff1-ce00-000000000000/.</span></span>
    
3. <span data-ttu-id="bff7f-170">Wenn die interne **oder** externe URLs aus lokalen SFB nicht vorhanden sind (beispielsweise https://lyncwebint01.contoso.com und https://lyncwebext01.contoso.com) werden muss, die bestimmte Datensätze zu dieser Liste hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="bff7f-170">If the internal **or** external SFB URLs from on-premises are missing (for example, https://lyncwebint01.contoso.com and https://lyncwebext01.contoso.com) we will need to add those specific records to this list.</span></span> 
    
    <span data-ttu-id="bff7f-171">Achten Sie darauf, dass *die Beispiel-URLs* , unten, durch den tatsächlichen URLs in die Befehle zum Hinzufügen ersetzen!</span><span class="sxs-lookup"><span data-stu-id="bff7f-171">Be sure to replace  *the example URLs*  , below, with your actual URLs in the Add commands!</span></span> 
    
  - <span data-ttu-id="bff7f-172">$x = Get-MsolServicePrincipal - AppPrincipalId 00000004-0000-0ff1-ce00-000000000000</span><span class="sxs-lookup"><span data-stu-id="bff7f-172">$x= Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000</span></span>
    
  - <span data-ttu-id="bff7f-173">$x.ServicePrincipalnames.Add (" *https://lyncwebint01.contoso.com/* ")</span><span class="sxs-lookup"><span data-stu-id="bff7f-173">$x.ServicePrincipalnames.Add(" *https://lyncwebint01.contoso.com/*  ")</span></span> 
    
  - <span data-ttu-id="bff7f-174">$x.ServicePrincipalnames.Add (" *https://lyncwebext01.contoso.com/* ")</span><span class="sxs-lookup"><span data-stu-id="bff7f-174">$x.ServicePrincipalnames.Add(" *https://lyncwebext01.contoso.com/*  ")</span></span> 
    
  - <span data-ttu-id="bff7f-175">Set-MSOLServicePrincipal - AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 - ServicePrincipalNames $x.ServicePrincipalNames</span><span class="sxs-lookup"><span data-stu-id="bff7f-175">Set-MSOLServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames</span></span>
    
4. <span data-ttu-id="bff7f-p114">Stellen Sie sicher, dass Ihre neue Datensätze hinzugefügt wurden, mithilfe des Befehls Get-MsolServicePrincipal aus Schritt 2 erneut aus, und Durchsuchen Sie die Ausgabe. Vergleichen Sie die Liste / Screenshot vor der neuen Liste der Dienstprinzipalnamen (SPNs) (können Sie auch die neue Liste Screenshot für Ihre Unterlagen). Wenn Sie erfolgreich waren, sehen Sie die beiden neuen URLs in der Liste. Wechseln von unserem Beispiel, die Liste der SPNs wird enthalten nun die bestimmte URLs https://lyncweb01.contoso.com und https://autodiscover.contoso.com.</span><span class="sxs-lookup"><span data-stu-id="bff7f-p114">Verify your new records were added by running the Get-MsolServicePrincipal command from step 2 again, and looking through the output. Compare the list / screenshot from before to the new list of SPNs (you may also screenshot the new list for your records). If you were successful, you will see the two new URLs in the list. Going by our example, the list of SPNs will now include the specific URLs https://lyncweb01.contoso.com and https://autodiscover.contoso.com.</span></span>
    
### <a name="create-the-evosts-auth-server-object"></a><span data-ttu-id="bff7f-180">Erstellen Sie das EvoSTS Auth-Server-Objekt</span><span class="sxs-lookup"><span data-stu-id="bff7f-180">Create the EvoSTS Auth Server Object</span></span>

<span data-ttu-id="bff7f-181">Führen Sie den folgenden Befehl in der Skype für Business-Verwaltungsshell.</span><span class="sxs-lookup"><span data-stu-id="bff7f-181">Run the following command in the Skype for Business Management Shell.</span></span>
  
- <span data-ttu-id="bff7f-182">"New-csoauthserver"-Identity EvoSTS - Metadaten-URL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml - AcceptSecurityIdentifierInformation $true-Typ AzureAD</span><span class="sxs-lookup"><span data-stu-id="bff7f-182">New-CsOAuthServer -Identity evoSTS -MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml -AcceptSecurityIdentifierInformation $true -Type AzureAD</span></span>
    
### <a name="enable-hybrid-modern-authentication"></a><span data-ttu-id="bff7f-183">Aktivieren der modernen Hybrid-Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="bff7f-183">Enable Hybrid Modern Authentication</span></span>

<span data-ttu-id="bff7f-p115">Dies ist der Schritt, der tatsächlich MA wird aktiviert. Die oben beschriebenen Schritte können vorausschauendes ausgeführt werden, ohne den Ablauf der Client-Authentifizierung. Wenn Sie den authentifizierungsfluss ändern möchten, führen Sie diesen Befehl in der Skype für Business-Verwaltungsshell.</span><span class="sxs-lookup"><span data-stu-id="bff7f-p115">This is the step that actually turns MA on. All the previous steps can be run ahead of time without changing the client authentication flow. When you are ready to change the authentication flow, run this command in the Skype for Business Management Shell.</span></span> 
  
- <span data-ttu-id="bff7f-187">"Set-csoauthconfiguration" - ClientAuthorizationOAuthServerIdentity evoSTS</span><span class="sxs-lookup"><span data-stu-id="bff7f-187">Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity evoSTS</span></span>
    
## <a name="verify"></a><span data-ttu-id="bff7f-188">„Bestätigen“,</span><span class="sxs-lookup"><span data-stu-id="bff7f-188">Verify</span></span>

<span data-ttu-id="bff7f-p116">Nachdem Sie HMA aktivieren, wird nächsten Anmeldung des Clients den neuen Auth Fluss verwenden. Beachten Sie, dass auf HMA einschalten eine erneute Authentifizierung für Clients ausgelöst werden nicht. Die Clients erneut authentifizieren basierend auf der Lebensdauer des Auth Token und/oder der Zertifikate, die sie besitzen.</span><span class="sxs-lookup"><span data-stu-id="bff7f-p116">Once you enable HMA, a client's next login will use the new auth flow. Note that just turning on HMA won't trigger a re-authentication for any client. The clients re-authenticate based on the lifetime of the auth tokens and/or certs they have.</span></span>
  
<span data-ttu-id="bff7f-p117">Um zu testen, dass HMA funktionsfähig ist, nachdem Sie es aktiviert haben, melden Sie sich einen Test SFB Windows-Client, und klicken Sie auf 'Meine Anmeldeinformationen löschen'. Melden Sie sich erneut an. Der Client sollte jetzt den modernen Auth Ablauf verwenden und Ihren Benutzernamen enthalten ein **Office 365** -Aufforderung nun für eine "Arbeit"oder"Schule" Konto gesehen rechts, bevor der Client den Server kontaktiert und meldet an.</span><span class="sxs-lookup"><span data-stu-id="bff7f-p117">To test that HMA is working after you've enabled it, sign out of a test SFB Windows client and be sure to click 'delete my credentials'. Sign in again. The client should now use the Modern Auth flow and your login will now include an **Office 365** prompt for a 'Work or school' account, seen right before the client contacts the server and logs you in.</span></span> 
  
<span data-ttu-id="bff7f-p118">Sie sollten auch die Konfigurationsinformationen für Skype für Business-Clients für eine "OAuth Behörde" überprüfen. Hierzu auf dem Clientcomputer halten Sie die STRG-Taste gedrückt, zur selben Zeit, die Sie der Skype Business Symbol in der Windows-Taskleiste mit der rechten Maustaste. Klicken Sie im angezeigten Menü auf Konfigurationsinformationen. Suchen Sie im Fenster "Skype für Konfigurationsinformationen Business", das auf dem Desktop angezeigt wird, für die folgenden:</span><span class="sxs-lookup"><span data-stu-id="bff7f-p118">You should also check the 'Configuration Information' for Skype for Business Clients for an 'OAuth Authority'. To do this on your client computer, hold down the CTRL key at the same time you right-click the Skype for Business Icon in the Windows Notification tray. Click Configuration Information in the menu that appears. In the 'Skype for Business Configuration Information' window that will appear on the desktop, look for the following:</span></span>
  
![Die Konfigurationsinformationen für einen Skype für Business Client mithilfe der modernen Authentifizierung zeigt eine Lync und EWS OAUTH Autorität URL der https://login.windows.net/common/oauth2/authorize.](media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png)
  
<span data-ttu-id="bff7f-p119">Sie sollten auch halten Sie die STRG-Taste zur selben Zeit Sie rechten Maustaste auf das Symbol für den Outlook-Client (auch in der Benachrichtigungen über die Windows-Taskleiste) klicken, und klicken Sie auf 'Verbindungsstatus'. Suchen Sie nach der Client-SMTP-Adresse gegen eine Authn Art von ' Bearer\*', darstellt, das Bearer Token in OAuth verwendet.</span><span class="sxs-lookup"><span data-stu-id="bff7f-p119">You should also hold down the CTRL key at the same time you right click the icon for the Outlook client (also in the Windows Notifications tray) and click 'Connection Status'. Look for the client's SMTP address against an Authn type of 'Bearer\*', which represents the bearer token used in OAuth.</span></span>
  
## <a name="related-articles"></a><span data-ttu-id="bff7f-202">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="bff7f-202">Related articles</span></span>

<span data-ttu-id="bff7f-203">[Verknüpfung zu der modernen Authentifizierung (Übersicht)](hybrid-modern-auth-overview.md) .</span><span class="sxs-lookup"><span data-stu-id="bff7f-203">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  
<span data-ttu-id="bff7f-p120">Müssen Sie wissen, wie Sie modernen Authentifizierung (ADAL) für Ihre Skype für Business Clients verwenden? Wir haben die Schritte [hier](https://technet.microsoft.com/en-us/library/mt710548.aspx).</span><span class="sxs-lookup"><span data-stu-id="bff7f-p120">Do you need to know how to use Modern Authentication (ADAL) for your Skype for Business clients? We've got steps [here](https://technet.microsoft.com/en-us/library/mt710548.aspx).</span></span>
  
<span data-ttu-id="bff7f-p121">Möchten Sie um diese Schritte zu lesen, wenn sie für Exchange Server angezeigt werden, lokalen, ohne SFB ausgeführt? Diese Schritte sind hier verfügbar.</span><span class="sxs-lookup"><span data-stu-id="bff7f-p121">Would you like to read these steps as they appear for Exchange Server, on-premises, running without SFB? Those steps are available here.</span></span>
  

