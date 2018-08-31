---
title: Verwalten von Office 365-Endpunkten
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 7/18/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 99cab9d4-ef59-4207-9f2b-3728eb46bf9a
description: Einige Netzwerke dienen zum Einschränken des Zugriffs auf das Internet, um sicherzustellen, dass die Liste der Office 365-Endpunkten Computern Netzwerke wie diese Office 365 zugreifen können, die Netzwerk- und Proxyeinstellungen Administratoren zum Verwalten der Liste der FQDNs, URLs müssen und IP-Adressen, bilden. Erreichen von Office 365 können diese Notwendigkeit, Proxyserver oder der Firewall-Regeln und PAC-Dateien, um die Netzwerkanfragen wird sichergestellt hinzugefügt werden soll.
ms.openlocfilehash: 0396174719adc7794a1d6bb4b1f950bfe4603996
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540852"
---
# <a name="managing-office-365-endpoints"></a><span data-ttu-id="5d254-104">Verwalten von Office 365-Endpunkten</span><span class="sxs-lookup"><span data-stu-id="5d254-104">Managing Office 365 endpoints</span></span>

## <a name="office-365-network-connectivity"></a><span data-ttu-id="5d254-105">Office 365-Netzwerkkonnektivität</span><span class="sxs-lookup"><span data-stu-id="5d254-105">Office 365 network connectivity</span></span>

 <span data-ttu-id="5d254-p102">Verbindungen mit Office 365 bestehen große Menge, vertrauenswürdigen Netzwerk-Anforderungen, die am besten ausführen, wenn sie über eine geringer Latenz Ausgang gemacht sind, die in der Nähe der Benutzer ist. Einige Office 365-Verbindungen profitieren von der die Verbindung zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="5d254-p102">Connections to Office 365 consist of high volume, trusted network requests that perform best when they're made over a low-latency egress that is near the user. Some Office 365 connections can benefit from optimizing the connection.</span></span> 
  
1. <span data-ttu-id="5d254-108">Sicherstellen die Firewall Listen können für eine Verbindung zu Office 365-Endpunkten zulassen.</span><span class="sxs-lookup"><span data-stu-id="5d254-108">Ensure your firewall allow lists allow for connectivity to Office 365 endpoints.</span></span>
    
2. <span data-ttu-id="5d254-109">Verwenden Sie Ihre Proxy-Infrastruktur, um Internetkonnektivität für Platzhalter und unveröffentlichte Ziele zu erlauben.</span><span class="sxs-lookup"><span data-stu-id="5d254-109">Use your proxy infrastructure to allow Internet connectivity to wildcard and unpublished destinations.</span></span>
    
3. <span data-ttu-id="5d254-110">Verwalten Sie eine optimale Umkreisnetzwerkkonfiguration.</span><span class="sxs-lookup"><span data-stu-id="5d254-110">Maintain an optimal perimeter network configuration.</span></span>
    
4. <span data-ttu-id="5d254-111">[Sicherstellen, dass Sie die bestmögliche Konnektivität optimal nutzen](https://aka.ms/o365perfprinciples).</span><span class="sxs-lookup"><span data-stu-id="5d254-111">[Ensure you're getting the best connectivity](https://aka.ms/o365perfprinciples).</span></span>
    
5. <span data-ttu-id="5d254-112">Lesen Sie [Office 365 Network Connectivity Prinzipien](office-365-network-connectivity-principles.md) , um die Konnektivität Prinzipien für die sichere Verwaltung von Office 365-Datenverkehr und erste die bestmögliche Leistung zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="5d254-112">Read [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md) to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance.</span></span> 
    
![Herstellen einer Verbindung mit Office 365, durch Firewalls und Proxys.](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)
  
## <a name="update-your-firewalls-outbound-allow-lists"></a><span data-ttu-id="5d254-114">Update die Firewall des ausgehenden Listen zulassen</span><span class="sxs-lookup"><span data-stu-id="5d254-114">Update your firewall's outbound allow lists</span></span>

<span data-ttu-id="5d254-p103">Sie können Ihr Netzwerk optimieren, indem alle vertrauenswürdigen Netzwerk-Anforderungen für Office 365 direkt über die Firewall senden, und alle zusätzlichen Ebene Paketinspektion umgehen oder in Bearbeitung. Dies reduziert langsam von Wartezeit sowie Ihrer kapazitätsanforderungen Umkreisnetzwerk. Am einfachsten auswählen, welche Netzwerk fordert als vertrauenswürdig ist unsere vordefinierte PAC Dateien auf der Registerkarte **Proxies** oben verwenden.</span><span class="sxs-lookup"><span data-stu-id="5d254-p103">You can optimize your network by sending all trusted Office 365 network requests directly through your firewall, bypassing all additional packet level inspection or processing. This reduces slow performance from latency and reduces your perimeter capacity requirements. The easiest way to choose which network requests to trust is to use our pre-built PAC files on the **Proxies** tab above.</span></span> 
  
<span data-ttu-id="5d254-p104">Wenn Ihre Firewall ausgehenden Datenverkehr blockiert, Sie alle IP-sicherzustellen möchten und FQDNs als **erforderlich** , in der [XML-Datei](https://go.microsoft.com/fwlink/?LinkId=533185) aufgelistet sind in der Zulassungsliste enthalten. Erkennen Sie, dass alle Dienste erfordern die Verwendung von einige 3. Party-Dienste. Wir nicht IP-Adressen für diese 3. Partei-Diensten wie etwa Zertifikat Anbietern von Content Delivery Networks DNS-Anbieter bereitgestellt und so weiter. Für vollständige Funktionalität von Office 365 müssen Sie möglicherweise alle vom Office 365 angefordert werden, unabhängig davon wie viele Informationen wir veröffentlichen das Ziel Ziele zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="5d254-p104">If your firewall blocks outbound traffic, you'll want to ensure all of the IP and FQDNs listed as **Required** in this [XML file](https://go.microsoft.com/fwlink/?LinkId=533185) are on the allow list. Recognize all services require the use of some 3rd party services. We don't provide IP addresses for these 3rd party services such as certificate providers, Content Delivery Networks, DNS providers, and so on. For full Office 365 functionality, you must be able to reach all destinations requested by Office 365 regardless of how much information we publish about the destination.</span></span> 
  
<span data-ttu-id="5d254-122">Viele Ziele müssen keine IP-Adresse veröffentlicht oder als Platzhalterdomäne mit keine bestimmten vollqualifizierten Domänennamen aufgeführt sind, verwenden Sie diese Funktionalität müssen Sie auflösen diese Netzwerk-Anfragen an die aktuelle IP-Adresse angefordert wird und Senden der Netzwerk-Anforderung über das Internet.</span><span class="sxs-lookup"><span data-stu-id="5d254-122">Many destinations do not have an IP address published or are listed as a wildcard domain with no specific fully qualified domain name, to use this functionality you must be able to resolve these network requests to the current IP address being requested and send the network request over the Internet.</span></span>
  
<span data-ttu-id="5d254-p105">Automatisieren des Upgradevorgangs mithilfe einer Firewalls, die analysiert die XML-Datei in Ihrem Auftrag und aktualisiert die Regeln automatisch basierend auf dem Dienste oder Features, dass Sie direkt über die Firewall weiterleiten möchten. Sie können auch das Tool [Azure Bereich](https://azurerange.azurewebsites.net/) verwenden, das von der Community erstellt wurde und analysiert den XML-Code für Sie mit den Exportoptionen für die Konfiguration der Cisco XE Route oder ACL-Liste, nur-Text oder CSV.</span><span class="sxs-lookup"><span data-stu-id="5d254-p105">Automate your process by using a firewall that parses the XML file on your behalf and updates your rules automatically based on the services or features you plan to route directly through your firewall. You can also use the [Azure Range](https://azurerange.azurewebsites.net/) tool that has been built by the community and parses the XML for you with export options for Cisco XE Route or ACL list configuration, plain text, or CSV.</span></span> 
  
<span data-ttu-id="5d254-125">Eine ausführlicheren Erläuterung der Ziele Netzwerk ist auf unserer [Website Verweis](urls-and-ip-address-ranges.md) sowie über unseren [RSS-basierte Änderungsprotokoll](https://go.microsoft.com/fwlink/p/?linkid=236301) verfügbar, sodass Sie Änderungen abonnieren können.</span><span class="sxs-lookup"><span data-stu-id="5d254-125">A longer explanation of the network destinations is available on our [reference site](urls-and-ip-address-ranges.md) as well through our [RSS based change log](https://go.microsoft.com/fwlink/p/?linkid=236301) so you can subscribe to changes.</span></span> 
  
<span data-ttu-id="5d254-126"><a name="pacfiles"> </a></span><span class="sxs-lookup"><span data-stu-id="5d254-126"></span></span>
## <a name="configure-outbound-paths-with-pac-files"></a><span data-ttu-id="5d254-127">Konfigurieren Sie ausgehende Pfade mit PAC-Dateien</span><span class="sxs-lookup"><span data-stu-id="5d254-127">Configure outbound paths with PAC files</span></span>

<span data-ttu-id="5d254-p106">Verwenden Sie PAC oder WPAD-Dateien zum Verwalten von Netzwerk-Anfragen, die mit Office 365 zugeordnet sind, jedoch nicht über ein IP-Adresse verfügen. Typische Netzwerk-Anforderungen, die über ein Proxy oder zum Umkreisnetzwerk-Gerät gesendet werden, ein zusätzlichen Latenz entstehen. Während Proxyauthentifizierung der größten Tax anfallen, können andere Dienste wie Reputation-Suche und versucht, Pakete prüfen benutzerfreundlich verursachen. Darüber hinaus benötigen diese Perimeter Network Geräte genügend Kapazität, um alle Netzwerkanfragen zu verarbeiten. Es wird empfohlen, die Proxy oder Prüfung Infrastruktur für die direkte Anforderungen von Office 365-Netzwerk zu umgehen.</span><span class="sxs-lookup"><span data-stu-id="5d254-p106">Use PAC or WPAD files to manage network requests that are associated with Office 365 but don't have an IP address provided. Typical network requests that are sent through a proxy or perimeter device incur additional latency. While proxy authentication incurs the largest tax, other services such as reputation lookup and attempts to inspect packets can cause a poor user experience. Additionally, these perimeter network devices need enough capacity to process all of the network requests. We recommend bypassing your proxy or inspection infrastructure for direct Office 365 network requests.</span></span>
  
<span data-ttu-id="5d254-p107">Verwenden Sie eines der unsere PAC-Dateien als Ausgangspunkt, um zu bestimmen, welche den Netzwerkverkehr zu einem Proxy gesendet werden, und das an eine Firewall gesendet werden. Wenn Sie PAC oder WPAD Dateien, lesen diesen Beitrag zur [Bereitstellung von PAC-Dateien](https://blogs.technet.microsoft.com/undocumentedfeatures/2016/04/06/deploying-the-office-365-proxy-pac-to-manage-your-users/) von einem unsere Berater für Office 365 nicht vertraut sind. Sie sollten diese als Ausgangspunkt überprüfen und bearbeiten, um entsprechend Ihrer Umgebung.</span><span class="sxs-lookup"><span data-stu-id="5d254-p107">Use one of our PAC files as a starting place to determine what network traffic will be sent to a proxy and which will be sent to a firewall. If you're new to PAC or WPAD files, read this post about [deploying PAC files](https://blogs.technet.microsoft.com/undocumentedfeatures/2016/04/06/deploying-the-office-365-proxy-pac-to-manage-your-users/) from one of our Office 365 consultants. You'll want to review these as a starting place and edit to suit your environment.</span></span> 
  
 <span data-ttu-id="5d254-136">**PAC-Dateien 7/10/2018 aktualisiert**.</span><span class="sxs-lookup"><span data-stu-id="5d254-136">**PAC files updated 7/10/2018**.</span></span> 
  
### <a name="1---pac-file-separates-required-internet-fqdns-from-known-office-365-fqdn"></a><span data-ttu-id="5d254-137">#1 - PAC-Datei: trennt Internet FQDNs von bekannten Office 365-FQDN erforderlich.</span><span class="sxs-lookup"><span data-stu-id="5d254-137">#1 - PAC file: Separates required Internet FQDNs from known Office 365 FQDN.</span></span>

<span data-ttu-id="5d254-p108">Im erste Beispiel wird eine Demonstration der unsere empfohlene Vorgehensweise bei der Verwaltung von Endpunkten über das Internet nur. Umgeht den Proxy für Office 365-Ziele geleitet, wo die IP-Adresse wird veröffentlicht und sendet verbleibenden Netzwerk Anforderungen an den Proxy.</span><span class="sxs-lookup"><span data-stu-id="5d254-p108">The first example is a demonstration of our recommended approach to managing endpoints over the Internet only. Bypasses the proxy for Office 365 destinations where the IP address is published and sends remaining network requests to the proxy.</span></span>
  
<span data-ttu-id="5d254-140">Codeausschnitt:</span><span class="sxs-lookup"><span data-stu-id="5d254-140">Code snippet:</span></span>
  
```
// JavaScript source code
//July 2018 - Updates go live 1st August2018
//This PAC file contains all FQDNs needed for all services and splits the traffic between those which Microsoft can provide IPs for (so can be sent through a managed firewall with conditional access if desired) and those which IPs cannot be provided for, so need to go to an unrestricted proxy or egress. 
//Due to the use of wildcards, some extra logic is provided to send traffic to the proxy before a 'direct' wildcard is hit.
//Includes Core ProPlus URLs but not Office Mobile/IPAD/IOS/ANDROID fqdns from https://support.office.com/en-gb/article/Network-requests-in-Office-365-ProPlus-eb73fcd1-ca88-4d02-a74b-2dd3a9f3364d
//Every Effort is made to ensure 100% accuracy but this PAC should be used as an example and cross-checked with your needs and the Office 365 URL &amp; IP page
//Intended only for Worldwide Office 365 instances, which the vast majority of customers will be using
function FindProxyForURL(url, host)
{
    // Define proxy server
    var proxyserver = "PROXY 10.10.10.10:8080";
    var proxyserver2 = "PROXY 10.10.10.11:8080";
    // Make host lowercase
    var lhost = host.toLowerCase();
    host = lhost;
    //Catch explicit FQDNs which need the proxy but are covered under wildcarded FQDNs which have IPs. This has to be done first before the wildcard is hit
    if ((shExpMatch(host, "quicktips.skypeforbusiness.com"))    
        || (shExpMatch(host, "*.um.outlook.com"))
        || (shExpMatch(host, "r3.res.office365.com"))
        || (shExpMatch(host, "r3.res.outlook.com"))
        || (shExpMatch(host, "r4.res.office365.com"))
        || (shExpMatch(host, "xsi.outlook.com"))
        || (shExpMatch(host, "r1.res.office365.com")))
    {
        return proxyserver;
    }
        //Send FQDNs which Microsoft provide IPs for direct, so they can be sent via a firewall
    else if ((isPlainHostName(host))
    || (shExpMatch(host, "*.aria.microsoft.com"))    
    || (shExpMatch(host, "*.dc.trouter.io"))
    || (shExpMatch(host, "*.lync.com"))
    || (shExpMatch(host, "*.manage.office.com"))
    || (shExpMatch(host, "*.office365.com"))
    || (shExpMatch(host, "*.onenote.com"))
    || (shExpMatch(host, "*.outlook.com"))
    || (shExpMatch(host, "*.outlook.office.com"))
    || (shExpMatch(host, "*.portal.cloudappsecurity.com"))
    || (shExpMatch(host, "*.protection.office.com"))
    || (shExpMatch(host, "*.sharepoint.com"))
    || (shExpMatch(host, "*.skype.com"))
    || (shExpMatch(host, "*.skypeforbusiness.com"))
    || (shExpMatch(host, "*.svc.ms"))
    || (shExpMatch(host, "*.teams.microsoft.com"))
    || (shExpMatch(host, "*.yammer.com"))
    || (shExpMatch(host, "*.yammerusercontent.com"))    
    || (shExpMatch(host, "*broadcast.officeapps.live.com"))
    || (shExpMatch(host, "*excel.officeapps.live.com"))
    || (shExpMatch(host, "*onenote.officeapps.live.com"))
    || (shExpMatch(host, "*powerpoint.officeapps.live.com"))
    || (shExpMatch(host, "*view.officeapps.live.com"))
    || (shExpMatch(host, "*visio.officeapps.live.com"))
    || (shExpMatch(host, "*word-edit.officeapps.live.com"))
    || (shExpMatch(host, "*word-view.officeapps.live.com"))
    || (shExpMatch(host, "admin.microsoft.com"))    
    || (shExpMatch(host, "account.office.net"))
    || (shExpMatch(host, "adminwebservice.microsoftonline.com"))
    || (shExpMatch(host, "agent.office.net"))
    || (shExpMatch(host, "api.login.microsoftonline.com"))
    || (shExpMatch(host, "api.passwordreset.microsoftonline.com"))
    || (shExpMatch(host, "apc.delve.office.com"))
    || (shExpMatch(host, "aus.delve.office.com"))
    || (shExpMatch(host, "autologon.microsoftazuread-sso.com"))  
    || (shExpMatch(host, "becws.microsoftonline.com"))
    || (shExpMatch(host, "browser.pipe.aria.microsoft.com"))  
    || (shExpMatch(host, "can.delve.office.com"))
    || (shExpMatch(host, "ccs.login.microsoftonline.com"))
    || (shExpMatch(host, "ccs-sdf.login.microsoftonline.com"))
    || (shExpMatch(host, "clientconfig.microsoftonline-p.net"))
    || (shExpMatch(host, "clientlog.portal.office.com"))
    || (shExpMatch(host, "companymanager.microsoftonline.com"))
    || (shExpMatch(host, "cus-000.tasks.osi.office.net"))
    || (shExpMatch(host, "delve.office.com"))
    || (shExpMatch(host, "device.login.microsoftonline.com"))    
    || (shExpMatch(host, "ea-000.tasks.osi.office.net"))
    || (shExpMatch(host, "eur.delve.office.com"))
    || (shExpMatch(host, "eus-zzz.tasks.osi.office.net"))
    || (shExpMatch(host, "gbr.delve.office.com"))    
    || (shExpMatch(host, "hip.microsoftonline-p.net"))
    || (shExpMatch(host, "hipservice.microsoftonline.com"))
    || (shExpMatch(host, "home.office.com"))
    || (shExpMatch(host, "ind.delve.office.com"))
    || (shExpMatch(host, "jpn.delve.office.com"))
    || (shExpMatch(host, "kor.delve.office.com"))
    || (shExpMatch(host, "lam.delve.office.com"))
    || (shExpMatch(host, "login.microsoft.com"))
    || (shExpMatch(host, "login.microsoftonline.com"))
    || (shExpMatch(host, "login.microsoftonline-p.com"))
    || (shExpMatch(host, "login.windows.net"))
    || (shExpMatch(host, "logincert.microsoftonline.com"))
    || (shExpMatch(host, "loginex.microsoftonline.com"))
    || (shExpMatch(host, "login-us.microsoftonline.com"))     
    || (shExpMatch(host, "manage.office.com"))
    || (shExpMatch(host, "mobile.pipe.aria.microsoft.com"))
    || (shExpMatch(host, "nam.delve.office.com"))
    || (shExpMatch(host, "neu-000.tasks.osi.office.net"))
    || (shExpMatch(host, "nexus.microsoftonline-p.com"))
    || (shExpMatch(host, "nexus.officeapps.live.com"))
    || (shExpMatch(host, "nexusrules.officeapps.live.com"))
    || (shExpMatch(host, "office.live.com"))
    || (shExpMatch(host, "officeapps.live.com"))
    || (shExpMatch(host, "passwordreset.microsoftonline.com"))
    || (shExpMatch(host, "portal.microsoftonline.com"))
    || (shExpMatch(host, "portal.office.com"))
    || (shExpMatch(host, "protection.office.com"))
    || (shExpMatch(host, "provisioningapi.microsoftonline.com"))
    || (shExpMatch(host, "scsinstrument-ss-us.trafficmanager.net"))   
    || (shExpMatch(host, "scsquery-ss-asia.trafficmanager.net")) 
    || (shExpMatch(host, "scsquery-ss-eu.trafficmanager.net")) 
    || (shExpMatch(host, "scsquery-ss-us.trafficmanager.net"))
    || (shExpMatch(host, "sea-000.tasks.osi.office.net"))    
    || (shExpMatch(host, "stamp2.login.microsoftonline.com"))
    || (shExpMatch(host, "suite.office.net"))    
    || (shExpMatch(host, "tasks.office.com"))
    || (shExpMatch(host, "teams.microsoft.com"))
    || (shExpMatch(host, "testconnectivity.microsoft.com"))
    || (shExpMatch(host, "webshell.suite.office.com"))
    || (shExpMatch(host, "weu-000.tasks.osi.office.net"))
    || (shExpMatch(host, "wus-000.tasks.osi.office.net"))
    || (shExpMatch(host, "www.office.com")))
      
    {
        return "DIRECT";
    }
    else
        // Send all unknown IP traffic to Proxy for unrestricted access. This section is not necessary if you have a catchall for all other traffic to go to an unfiltered proxy. 
        //However the fqdns required, but for which we dont have IPs for, are listed here incase you need an explicit list.
   if          ((shExpMatch(host, "*.aadrm.com"))
        || (shExpMatch(host, "*.adhybridhealth.azure.com")) 
        || (shExpMatch(host, "*.adl.windows.com"))   
        || (shExpMatch(host, "*.api.microsoftstream.com"))      
        || (shExpMatch(host, "*.assets-yammer.com"))   
        || (shExpMatch(host, "*.azureedge.net"))            
        || (shExpMatch(host, "*.azurerms.com"))
        || (shExpMatch(host, "*.cloudapp.net"))
        || (shExpMatch(host, "*.entrust.net")) 
        || (shExpMatch(host, "*.geotrust.com"))   
        || (shExpMatch(host, "*.helpshift.com"))   
        || (shExpMatch(host, "*.hockeyapp.net"))    
        || (shExpMatch(host, "*.localytics.com"))    
        || (shExpMatch(host, "*.log.optimizely.com"))    
        || (shExpMatch(host, "*.microsoft.com"))
        || (shExpMatch(host, "*.microsoftonline.com"))
        || (shExpMatch(host, "*.microsoftonline-p.com"))
        || (shExpMatch(host, "*.microsoftonline-p.net"))
        || (shExpMatch(host, "*.msecnd.net"))
        || (shExpMatch(host, "*.msedge.net"))      
        || (shExpMatch(host, "*.msocdn.com")) 
        || (shExpMatch(host, "*.mstea.ms"))    
        || (shExpMatch(host, "*.notification.api.microsoftstream.com")) 
        || (shExpMatch(host, "*.o365weve.com"))     
        || (shExpMatch(host, "*.office.com"))   
        || (shExpMatch(host, "*.office.net"))
        || (shExpMatch(host, "*.omniroot.com"))
        || (shExpMatch(host, "*.onmicrosoft.com"))
        || (shExpMatch(host, "*.phonefactor.net"))
        || (shExpMatch(host, "*.public-trust.com"))
        || (shExpMatch(host, "*.search.production.apac.trafficmanager.net"))
        || (shExpMatch(host, "*.search.production.emea.trafficmanager.net"))
        || (shExpMatch(host, "*.search.production.us.trafficmanager.net"))
        || (shExpMatch(host, "*.secure.skypeassets.com"))  
        || (shExpMatch(host, "*.sfbassets.com"))
        || (shExpMatch(host, "*.sharepointonline.com"))
        || (shExpMatch(host, "*.sway.com"))
        || (shExpMatch(host, "*.symcb.com"))
        || (shExpMatch(host, "*.teams.microsoft.com"))  
        || (shExpMatch(host, "*.tenor.com"))  
        || (shExpMatch(host, "*.symcd.com"))     
        || (shExpMatch(host, "*.users.storage.live.com"))
        || (shExpMatch(host, "*.verisign.com"))
        || (shExpMatch(host, "*.verisign.net"))
        || (shExpMatch(host, "*.windows.net"))
        || (shExpMatch(host, "*cdn.onenote.net"))
        || (shExpMatch(host, "account.activedirectory.windowsazure.com"))
        || (shExpMatch(host, "ad.atdmt.com"))
        || (shExpMatch(host, "admin.onedrive.com"))
        || (shExpMatch(host, "ajax.aspnetcdn.com"))
        || (shExpMatch(host, "aka.ms"))
        || (shExpMatch(host, "amp.azure.net"))
        || (shExpMatch(host, "api.microsoftstream.com"))
        || (shExpMatch(host, "apis.live.net"))  
        || (shExpMatch(host, "apps.identrust.com"))  
        || (shExpMatch(host, "assets.onestore.ms"))
        || (shExpMatch(host, "auth.gfx.ms"))
        || (shExpMatch(host, "cacerts.digicert.com"))        
        || (shExpMatch(host, "cdn.odc.officeapps.live.com"))  
        || (shExpMatch(host, "cdn.onenote.net"))
        || (shExpMatch(host, "cdn.optimizely.com")) 
        || (shExpMatch(host, "cert.int-x3.letsencrypt.org"))
        || (shExpMatch(host, "client.hip.live.com"))
        || (shExpMatch(host, "connect.facebook.net"))        
        || (shExpMatch(host, "crl.globalsign.com"))
        || (shExpMatch(host, "crl.globalsign.net"))
        || (shExpMatch(host, "crl.identrust.com"))    
        || (shExpMatch(host, "crl3.digicert.com"))  
        || (shExpMatch(host, "crl4.digicert.com"))
        || (shExpMatch(host, "cus-odc.officeapps.live.com"))              
        || (shExpMatch(host, "cus-roaming.officeapps.live.com"))
        || (shExpMatch(host, "dc.services.visualstudio.com"))
        || (shExpMatch(host, "domains.live.com"))
        || (shExpMatch(host, "ea-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "ea-roaming.officeapps.live.com"))          
        || (shExpMatch(host, "ecn.dev.virtualearth.net "))   
        || (shExpMatch(host, "eus2-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "eus2-roaming.officeapps.live.com"))             
        || (shExpMatch(host, "eus-odc.officeapps.live.com"))         
        || (shExpMatch(host, "eus-www.sway-cdn.com"))
        || (shExpMatch(host, "eus-www.sway-extensions.com"))        
        || (shExpMatch(host, "firstpartyapps.oaspapps.com"))
        || (shExpMatch(host, "g.live.com"))
        || (shExpMatch(host, "groupsapi2-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi3-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi4-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi-prod.outlookgroups.ms"))   
        || (shExpMatch(host, "isrg.trustid.ocsp.identrust.com"))   
        || (shExpMatch(host, "liverdcxstorage.blob.core.windowsazure.com"))
        || (shExpMatch(host, "management.azure.com"))        
        || (shExpMatch(host, "mem.gfx.ms"))
        || (shExpMatch(host, "mrodevicemgr.officeapps.live.com"))      
        || (shExpMatch(host, "ncus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "ncus-roaming.officeapps.live.com"))                
        || (shExpMatch(host, "neu-000.ocws.officeapps.live.com")) 
        || (shExpMatch(host, "neu-odc.officeapps.live.com"))         
        || (shExpMatch(host, "neu-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "nexus.officeapps.live.com"))
        || (shExpMatch(host, "nexusrules.officeapps.live.com"))
        || (shExpMatch(host, "nps.onyx.azure.net"))
        || (shExpMatch(host, "ocsa.officeapps.live.com"))
        || (shExpMatch(host, "ocsp.digicert.com"))
        || (shExpMatch(host, "ocspx.digicert.com"))
        || (shExpMatch(host, "ocsp.globalsign.com"))
        || (shExpMatch(host, "ocsp.int-x3.letsencrypt.org"))
        || (shExpMatch(host, "ocsp.msocsp.com"))       
        || (shExpMatch(host, "ocsp2.globalsign.com"))
        || (shExpMatch(host, "ocsredir.officeapps.live.com"))
        || (shExpMatch(host, "ocws.officeapps.live.com"))
        || (shExpMatch(host, "odc.officeapps.live.com"))  
        || (shExpMatch(host, "officecdn.microsoft.com.edgekey.net"))            
        || (shExpMatch(host, "officecdn.microsoft.com.edgesuite.net"))              
        || (shExpMatch(host, "ols.officeapps.live.com"))  
        || (shExpMatch(host, "oneclient.sfx.ms"))
        || (shExpMatch(host, "outlook.uservoice.com"))
        || (shExpMatch(host, "platform.linkedin.com"))
        || (shExpMatch(host, "policykeyservice.dc.ad.msft.net"))
        || (shExpMatch(host, "prod.firstpartyapps.oaspapps.com.akadns.net")) 
        || (shExpMatch(host, "r1.res.office365.com"))
        || (shExpMatch(host, "r3.res.office365.com"))
        || (shExpMatch(host, "r4.res.office365.com"))
        || (shExpMatch(host, "s.ytimg.com"))
        || (shExpMatch(host, "scus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "scus-odc.officeapps.live.com"))         
        || (shExpMatch(host, "scus-roaming.officeapps.live.com"))                 
        || (shExpMatch(host, "sea-odc.officeapps.live.com"))         
        || (shExpMatch(host, "sea-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "secure.globalsign.com"))
        || (shExpMatch(host, "site-cdn.onenote.net"))
        || (shExpMatch(host, "skydrive.wns.windows.com"))
        || (shExpMatch(host, "skypemaprdsitus.trafficmanager.net"))   
        || (shExpMatch(host, "spoprod-a.akamaihd.net"))  
        || (shExpMatch(host, "ssw.live.com"))
        || (shExpMatch(host, "staffhub.ms"))
        || (shExpMatch(host, "staffhub.uservoice.com"))
        || (shExpMatch(host, "storage.live.com"))
        || (shExpMatch(host, "sway.com")) 
        || (shExpMatch(host, "teams.microsoft.com"))              
        || (shExpMatch(host, "telemetry.remoteapp.windowsazure.com"))         
        || (shExpMatch(host, "telemetryservice.firstpartyapps.oaspapps.com"))    
        || (shExpMatch(host, "web.microsoftstream.com"))         
        || (shExpMatch(host, "weu-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "weu-odc.officeapps.live.com"))         
        || (shExpMatch(host, "weu-roaming.officeapps.live.com"))
        || (shExpMatch(host, "wu.client.hip.live.com"))
        || (shExpMatch(host, "wus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "wus-firstpartyapps.oaspapps.com"))  
        || (shExpMatch(host, "wus-odc.officeapps.live.com"))         
        || (shExpMatch(host, "wus-roaming.officeapps.live.com"))
        || (shExpMatch(host, "wus-www.sway-cdn.com"))
        || (shExpMatch(host, "wus-www.sway-extensions.com"))   
        || (shExpMatch(host, "www.digicert.com"))
        || (shExpMatch(host, "www.google-analytics.com"))
        || (shExpMatch(host, "www.onedrive.com"))
        || (shExpMatch(host, "www.remoteapp.windowsazure.com"))
        || (shExpMatch(host, "www.youtube.com"))
        || (shExpMatch(host, "xsi.outlook.com")))
        
    {
        return proxyserver;
    }
    //Catchall for all other traffic to another proxy 
else return proxyserver;
}

```

### <a name="2---pac-file-connect-to-office-365-over-the-internet-and-expressroute"></a><span data-ttu-id="5d254-141">#2 – PAC-Datei: Verbinden mit Office 365 über das Internet und ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="5d254-141">#2 - PAC file: Connect to Office 365 over the Internet and ExpressRoute</span></span>
<span data-ttu-id="5d254-142"><a name="bkmk_inet-aer"> </a></span><span class="sxs-lookup"><span data-stu-id="5d254-142"></span></span>

<span data-ttu-id="5d254-p109">Im zweite Beispiel wird eine Demonstration der unsere empfohlene Vorgehensweise zum Verwalten von Verbindungen, wenn Circuits ExpressRoute und im Internet verfügbar sind. Sendet ExpressRoute angekündigt Ziele der Netzfrequenz ExpressRoute und Internet nur Ziele an den Proxy angekündigt.</span><span class="sxs-lookup"><span data-stu-id="5d254-p109">The second example is a demonstration of our recommended approach to managing connections when ExpressRoute and Internet circuits are available. Sends ExpressRoute advertised destinations to the ExpressRoute circuit and Internet only advertised destinations to the proxy.</span></span>
  
<span data-ttu-id="5d254-145">Codeausschnitt:</span><span class="sxs-lookup"><span data-stu-id="5d254-145">Code snippet:</span></span>
  
```
// JavaScript source code
//July 2018 Update
// Consolidated FQDNs of URLS which are reachable via Microsoft peering over ExpressRoute. All other traffic sent to a proxy in this example. 
//Every Effort is made to ensure 100% accuracy but this PAC should be used as an example and cross-checked with your traffic flow needs and the Office 365 URL &amp; IP page. 
//Intended only for Worldwide Office 365 instances, which the vast majority of customers will be using
//PAC presumes all Office 365 BGP communities/route filters are allowed.
function FindProxyForURL(url, host)
{
    // Define proxy server
    var proxyserver = "PROXY 10.10.10.10:8080";
    // Make host lowercase
    var lhost = host.toLowerCase();
    host = lhost;
    //SUB-FQDNs of ExpressRoutable wildcards which need to be explicitly sent to the proxy at the top of the PAC because they arent ER routable
    if ((shExpMatch(host, "xsi.outlook.com"))
        || (shExpMatch(host, "r3.res.outlook.com"))
        || (shExpMatch(host, "quicktips.skypeforbusiness.com"))
        || (shExpMatch(host, "*.um.outlook.com")))                  
    {
        return proxyserver;
    }
        //EXPRESS ROUTE DIRECT
    else if ((isPlainHostName(host))  
            || (shExpMatch(host, "*.aria.microsoft.com"))             
            || (shExpMatch(host, "*.dc.trouter.io"))
            || (shExpMatch(host, "*.lync.com"))
            || (shExpMatch(host, "*.manage.office.com"))
            || (shExpMatch(host, "*.outlook.com"))
            || (shExpMatch(host, "*.outlook.office.com"))
            || (shExpMatch(host, "*.portal.cloudappsecurity.com"))
            || (shExpMatch(host, "*.protection.office.com"))
            || (shExpMatch(host, "*.protection.outlook.com"))
            || (shExpMatch(host, "*.sharepoint.com")) 
            || (shExpMatch(host, "*.skype.com")) 
            || (shExpMatch(host, "*.skypeforbusiness.com")) 
            || (shExpMatch(host, "*.svc.ms"))   
            || (shExpMatch(host, "*.teams.microsoft.com"))  
            || (shExpMatch(host, "*broadcast.officeapps.live.com"))
            || (shExpMatch(host, "*excel.officeapps.live.com"))
            || (shExpMatch(host, "*onenote.officeapps.live.com"))
            || (shExpMatch(host, "*powerpoint.officeapps.live.com"))
            || (shExpMatch(host, "*view.officeapps.live.com"))                                 
            || (shExpMatch(host, "*visio.officeapps.live.com"))
            || (shExpMatch(host, "*word-edit.officeapps.live.com"))
            || (shExpMatch(host, "*word-view.officeapps.live.com"))
            || (shExpMatch(host, "account.office.net"))
            || (shExpMatch(host, "adminwebservice.microsoftonline.com"))
            || (shExpMatch(host, "agent.office.net"))  
            || (shExpMatch(host, "apc.delve.office.com"))
            || (shExpMatch(host, "api.login.microsoftonline.com"))
            || (shExpMatch(host, "api.passwordreset.microsoftonline.com"))
            || (shExpMatch(host, "aus.delve.office.com"))
            || (shExpMatch(host, "autologon.microsoftazuread-sso.com")) 
            || (shExpMatch(host, "becws.microsoftonline.com"))
            || (shExpMatch(host, "browser.pipe.aria.microsoft.com"))  
            || (shExpMatch(host, "can.delve.office.com")) 
            || (shExpMatch(host, "ccs.login.microsoftonline.com"))  
            || (shExpMatch(host, "ccs-sdf.login.microsoftonline.com"))
            || (shExpMatch(host, "clientconfig.microsoftonline-p.net"))
            || (shExpMatch(host, "companymanager.microsoftonline.com"))
            || (shExpMatch(host, "delve.office.com"))
            || (shExpMatch(host, "device.login.microsoftonline.com"))
            || (shExpMatch(host, "domains.live.com")) 
            || (shExpMatch(host, "eur.delve.office.com"))
            || (shExpMatch(host, "gbr.delve.office.com"))
            || (shExpMatch(host, "hip.microsoftonline-p.net"))
            || (shExpMatch(host, "hipservice.microsoftonline.com"))
            || (shExpMatch(host, "home.office.com"))
            || (shExpMatch(host, "ind.delve.office.com"))
            || (shExpMatch(host, "jpn.delve.office.com"))
            || (shExpMatch(host, "kor.delve.office.com"))
            || (shExpMatch(host, "lam.delve.office.com"))
            || (shExpMatch(host, "login.microsoft.com"))
            || (shExpMatch(host, "login.microsoftonline.com"))
            || (shExpMatch(host, "login.microsoftonline-p.net"))
            || (shExpMatch(host, "login.windows.net"))
            || (shExpMatch(host, "logincert.microsoftonline.com"))
            || (shExpMatch(host, "loginex.microsoftonline.com"))
            || (shExpMatch(host, "login-us.microsoftonline.com"))
            || (shExpMatch(host, "manage.office.com"))
            || (shExpMatch(host, "mobile.pipe.aria.microsoft.com"))
            || (shExpMatch(host, "nam.delve.office.com"))
            || (shExpMatch(host, "nexus.microsoftonline-p.net"))
            || (shExpMatch(host, "office.live.com")) 
            || (shExpMatch(host, "officeapps.live.com")) 
            || (shExpMatch(host, "outlook.office365.com")) 
            || (shExpMatch(host, "passwordreset.microsoftonline.com"))
            || (shExpMatch(host, "portal.office.com"))
            || (shExpMatch(host, "protection.office.com"))
            || (shExpMatch(host, "provisioningapi.microsoftonline.com"))
            || (shExpMatch(host, "scsinstrument-ss-us.trafficmanager.net")) 
            || (shExpMatch(host, "scsquery-ss-asia.trafficmanager.net"))
            || (shExpMatch(host, "scsquery-ss-eu.trafficmanager.net")) 
            || (shExpMatch(host, "scsquery-ss-us.trafficmanager.net"))  
            || (shExpMatch(host, "signup.microsoft.com"))
            || (shExpMatch(host, "smtp.office365.com"))  
            || (shExpMatch(host, "stamp2.login.microsoftonline.com"))
            || (shExpMatch(host, "suite.office.net")) 
            || (shExpMatch(host, "teams.microsoft.com")) 
            || (shExpMatch(host, "webshell.suite.office.com")) 
            || (shExpMatch(host, "www.office.com")))             
       
    {
        return "DIRECT";
    }
        //Catchall for all other traffic to proxy
    else
    {
        return proxyserver;
    }
}

```

### <a name="3---pac-file-manage-all-office-365-destinations-collectively"></a><span data-ttu-id="5d254-146">#3 – PAC-Datei: alle Office 365 Ziele gemeinsam verwalten</span><span class="sxs-lookup"><span data-stu-id="5d254-146">#3 - PAC file: Manage all Office 365 destinations collectively</span></span>
<span data-ttu-id="5d254-147"><a name="bkmk_inet-direct"> </a></span><span class="sxs-lookup"><span data-stu-id="5d254-147"></span></span>

<span data-ttu-id="5d254-p110">Im dritte Beispiel veranschaulicht zusenden alle Netzwerk mit Office 365, ein einziges Ziel zugeordnet ist. Dies wird häufig verwendet, um alle Prüfung der Anforderungen für Office 365-Netzwerk zu umgehen und bietet, dass Sie ein Format, in dem alle Endpunkte veröffentlichten, Liste im Format PAC für Ihre Anpassung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="5d254-p110">The third example demonstrates sending all network requests associated with Office 365 to a single destination. This is commonly used to bypass all inspection of Office 365 network requests and offers you a format where all published endpoints are in list in the PAC format to use for your customization.</span></span>
  
<span data-ttu-id="5d254-150">Codeausschnitt:</span><span class="sxs-lookup"><span data-stu-id="5d254-150">Code snippet:</span></span>
  
```
// JavaScript source code
//July 2018 Update new URLS go live 1st August 2018 -
//Consolidated FQDNs required to access Office 365 - All services including optional components covered and elements covered under wildcards removed. 
//Some repeated domains have been consoliodated into unpublished wildcards in order to keep the file as small as possible.
//Includes Core ProPlus URLs but not Office Mobile/IPAD/IOS/ANDROID fqdns from https://support.office.com/en-gb/article/Network-requests-in-Office-365-ProPlus-eb73fcd1-ca88-4d02-a74b-2dd3a9f3364d
//Every Effort is made to ensure 100% accuracy but this PAC should be used as an example and cross-checked with your needs and the Office 365 URL &amp; IP page
//Intended only for Worldwide Office 365 instances, which the vast majority of customers will be using
function FindProxyForURL(url, host)
{
    // Define proxy server
    var proxyserver = "PROXY 10.10.10.10:8080";
    // Make host lowercase
    var lhost = host.toLowerCase();
    host = lhost;
   if  ((shExpMatch(host, "*.aadrm.com"))
        || (shExpMatch(host, "*.adhybridhealth.azure.com"))
        || (shExpMatch(host, "*.adl.windows.com"))
        || (shExpMatch(host, "*.api.microsoftstream.com"))  
        || (shExpMatch(host, "*.assets-yammer.com"))
        || (shExpMatch(host, "autologon.microsoftazuread-sso.com"))  
        || (shExpMatch(host, "*.azureedge.net"))   
        || (shExpMatch(host, "*.azurerms.com"))
        || (shExpMatch(host, "*.cloudapp.net")) 
        || (shExpMatch(host, "*.dc.trouter.io"))
        || (shExpMatch(host, "*.entrust.net")) 
        || (shExpMatch(host, "*.geotrust.com"))
        || (shExpMatch(host, "*.helpshift.com"))
        || (shExpMatch(host, "*.hockeyapp.net"))       
        || (shExpMatch(host, "*.localytics.com"))
        || (shExpMatch(host, "*.log.optimizely.com"))     
        || (shExpMatch(host, "*.lync.com"))
        || (shExpMatch(host, "*.microsoft.com"))
        || (shExpMatch(host, "*.microsoftonline.com"))
        || (shExpMatch(host, "*.microsoftonline-p.com"))
        || (shExpMatch(host, "*.microsoftonline-p.net"))
        || (shExpMatch(host, "*.msecnd.net"))
        || (shExpMatch(host, "*.msedge.net"))
        || (shExpMatch(host, "*.msocdn.com"))
        || (shExpMatch(host, "*.mstea.ms"))
        || (shExpMatch(host, "*.o365weve.com"))
        || (shExpMatch(host, "*.office.com"))
        || (shExpMatch(host, "*.office.net"))
        || (shExpMatch(host, "*.office365.com"))
        || (shExpMatch(host, "*.omniroot.com"))
        || (shExpMatch(host, "*.onenote.com"))
        || (shExpMatch(host, "*.onmicrosoft.com"))
        || (shExpMatch(host, "*.outlook.com"))
        || (shExpMatch(host, "*.phonefactor.net")) 
        || (shExpMatch(host, "*.portal.cloudappsecurity.com"))
        || (shExpMatch(host, "*.public-trust.com"))
        || (shExpMatch(host, "*.search.production.apac.trafficmanager.net"))
        || (shExpMatch(host, "*.search.production.emea.trafficmanager.net"))
        || (shExpMatch(host, "*.search.production.us.trafficmanager.net"))
        || (shExpMatch(host, "*.secure.skypeassets.com"))
        || (shExpMatch(host, "*.sfbassets.com"))  
        || (shExpMatch(host, "*.sharepoint.com"))
        || (shExpMatch(host, "*.sharepointonline.com"))
        || (shExpMatch(host, "*.skype.com"))
        || (shExpMatch(host, "*.skypeforbusiness.com"))
        || (shExpMatch(host, "*.svc.ms")) 
        || (shExpMatch(host, "*.sway.com"))
        || (shExpMatch(host, "*.symcb.com"))
        || (shExpMatch(host, "*.symcd.com"))
        || (shExpMatch(host, "*.tenor.com"))
        || (shExpMatch(host, "*.users.storage.live.com"))
        || (shExpMatch(host, "*.verisign.com"))
        || (shExpMatch(host, "*.verisign.net"))
        || (shExpMatch(host, "*.windows.net"))
        || (shExpMatch(host, "*.yammer.com"))
        || (shExpMatch(host, "*.yammerusercontent.com"))         
        || (shExpMatch(host, "*broadcast.officeapps.live.com"))
        || (shExpMatch(host, "*cdn.onenote.net"))
        || (shExpMatch(host, "*excel.officeapps.live.com"))
        || (shExpMatch(host, "*onenote.officeapps.live.com"))
        || (shExpMatch(host, "*powerpoint.officeapps.live.com"))
        || (shExpMatch(host, "*view.officeapps.live.com"))
        || (shExpMatch(host, "*visio.officeapps.live.com"))
        || (shExpMatch(host, "*word-edit.officeapps.live.com"))
        || (shExpMatch(host, "*word-view.officeapps.live.com"))    
        || (shExpMatch(host, "account.activedirectory.windowsazure.com"))
        || (shExpMatch(host, "ad.atdmt.com"))
        || (shExpMatch(host, "admin.onedrive.com"))
        || (shExpMatch(host, "ajax.aspnetcdn.com"))
        || (shExpMatch(host, "aka.ms"))
        || (shExpMatch(host, "amp.azure.net"))
        || (shExpMatch(host, "api.microsoftstream.com"))
        || (shExpMatch(host, "apis.live.net"))
        || (shExpMatch(host, "apps.identrust.com")) 
        || (shExpMatch(host, "assets.onestore.ms"))
        || (shExpMatch(host, "auth.gfx.ms"))
        || (shExpMatch(host, "cacerts.digicert.com"))    
        || (shExpMatch(host, "cdn.odc.officeapps.live.com"))  
        || (shExpMatch(host, "cdn.onenote.net"))
        || (shExpMatch(host, "cdn.optimizely.com"))
        || (shExpMatch(host, "cert.int-x3.letsencrypt.org"))
        || (shExpMatch(host, "client.hip.live.com"))     
        || (shExpMatch(host, "connect.facebook.net"))
        || (shExpMatch(host, "crl.globalsign.com"))
        || (shExpMatch(host, "crl.globalsign.net"))
        || (shExpMatch(host, "crl.identrust.com"))    
        || (shExpMatch(host, "crl3.digicert.com"))  
        || (shExpMatch(host, "crl4.digicert.com"))
        || (shExpMatch(host, "cus-odc.officeapps.live.com"))              
        || (shExpMatch(host, "cus-roaming.officeapps.live.com"))      
        || (shExpMatch(host, "dc.services.visualstudio.com"))
        || (shExpMatch(host, "domains.live.com"))
        || (shExpMatch(host, "ea-000.ocws.officeapps.live.com")) 
        || (shExpMatch(host, "ea-roaming.officeapps.live.com"))           
        || (shExpMatch(host, "ecn.dev.virtualearth.net"))
        || (shExpMatch(host, "eus2-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "eus2-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "eus-odc.officeapps.live.com"))              
        || (shExpMatch(host, "eus-www.sway-cdn.com"))
        || (shExpMatch(host, "eus-www.sway-extensions.com"))
        || (shExpMatch(host, "firstpartyapps.oaspapps.com"))
        || (shExpMatch(host, "g.live.com"))
        || (shExpMatch(host, "groupsapi2-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi3-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi4-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "isrg.trustid.ocsp.identrust.com"))
        || (shExpMatch(host, "liverdcxstorage.blob.core.windowsazure.com"))
        || (shExpMatch(host, "management.azure.com"))
        || (shExpMatch(host, "mem.gfx.ms"))
        || (shExpMatch(host, "mrodevicemgr.officeapps.live.com"))               
        || (shExpMatch(host, "ncus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "ncus-roaming.officeapps.live.com"))                 
        || (shExpMatch(host, "neu-000.ocws.officeapps.live.com")) 
        || (shExpMatch(host, "neu-odc.officeapps.live.com"))              
        || (shExpMatch(host, "neu-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "nexus.officeapps.live.com"))
        || (shExpMatch(host, "nexusrules.officeapps.live.com"))
        || (shExpMatch(host, "nps.onyx.azure.net"))   
        || (shExpMatch(host, "ocsa.officeapps.live.com"))
        || (shExpMatch(host, "ocsp.digicert.com"))
        || (shExpMatch(host, "ocsp.globalsign.com"))
        || (shExpMatch(host, "ocsp.int-x3.letsencrypt.org"))
        || (shExpMatch(host, "ocsp.msocsp.com"))     
        || (shExpMatch(host, "ocsp2.globalsign.com")) 
        || (shExpMatch(host, "ocspx.digicert.com"))
        || (shExpMatch(host, "ocsredir.officeapps.live.com"))
        || (shExpMatch(host, "ocws.officeapps.live.com"))
        || (shExpMatch(host, "odc.officeapps.live.com"))  
        || (shExpMatch(host, "office.live.com"))
        || (shExpMatch(host, "officeapps.live.com"))
        || (shExpMatch(host, "officecdn.microsoft.com.edgekey.net"))              
        || (shExpMatch(host, "officecdn.microsoft.com.edgesuite.net"))
        || (shExpMatch(host, "ols.officeapps.live.com"))  
        || (shExpMatch(host, "oneclient.sfx.ms"))
        || (shExpMatch(host, "outlook.uservoice.com"))
        || (shExpMatch(host, "platform.linkedin.com"))
        || (shExpMatch(host, "policykeyservice.dc.ad.msft.net"))
        || (shExpMatch(host, "prod.firstpartyapps.oaspapps.com.akadns.net"))
        || (shExpMatch(host, "s.ytimg.com"))
        || (shExpMatch(host, "s0.assets-yammer.com"))  
        || (shExpMatch(host, "scsinstrument-ss-us.trafficmanager.net")) 
        || (shExpMatch(host, "scsquery-ss-asia.trafficmanager.net"))
        || (shExpMatch(host, "scsquery-ss-eu.trafficmanager.net")) 
        || (shExpMatch(host, "scsquery-ss-us.trafficmanager.net")) 
        || (shExpMatch(host, "scus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "scus-odc.officeapps.live.com"))         
        || (shExpMatch(host, "scus-roaming.officeapps.live.com"))                 
        || (shExpMatch(host, "sea-odc.officeapps.live.com"))              
        || (shExpMatch(host, "sea-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "secure.globalsign.com"))
        || (shExpMatch(host, "site-cdn.onenote.net"))
        || (shExpMatch(host, "skydrive.wns.windows.com"))
        || (shExpMatch(host, "skypemaprdsitus.trafficmanager.net"))
        || (shExpMatch(host, "spoprod-a.akamaihd.net"))
        || (shExpMatch(host, "ssw.live.com"))
        || (shExpMatch(host, "staffhub.ms"))
        || (shExpMatch(host, "staffhub.uservoice.com"))    
        || (shExpMatch(host, "storage.live.com"))
        || (shExpMatch(host, "telemetry.remoteapp.windowsazure.com"))
        || (shExpMatch(host, "telemetryservice.firstpartyapps.oaspapps.com"))
        || (shExpMatch(host, "web.microsoftstream.com"))   
        || (shExpMatch(host, "weu-000.ocws.officeapps.live.com")) 
        || (shExpMatch(host, "weu-odc.officeapps.live.com"))              
        || (shExpMatch(host, "weu-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "wu.client.hip.live.com"))
        || (shExpMatch(host, "wus-000.ocws.officeapps.live.com"))  
        || (shExpMatch(host, "wus-firstpartyapps.oaspapps.com"))  
        || (shExpMatch(host, "wus-odc.officeapps.live.com"))              
        || (shExpMatch(host, "wus-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "wus-www.sway-cdn.com"))
        || (shExpMatch(host, "wus-www.sway-extensions.com"))        
        || (shExpMatch(host, "www.digicert.com"))
        || (shExpMatch(host, "www.google-analytics.com"))
        || (shExpMatch(host, "www.onedrive.com"))
        || (shExpMatch(host, "www.remoteapp.windowsazure.com"))
        || (shExpMatch(host, "www.youtube.com")))
    {
        return proxyserver;
    }
        //Catchall for all other traffic to another proxy
    else return "PROXY 10.10.10.11:8080";
}

```

### <a name="use-custom-scripts-or-manually-create-your-own-pac-files"></a><span data-ttu-id="5d254-151">Verwenden Sie benutzerdefinierte Skripts oder manuell erstellen Sie eigener PAC-Dateien</span><span class="sxs-lookup"><span data-stu-id="5d254-151">Use custom scripts or manually create your own PAC files</span></span>
<span data-ttu-id="5d254-152"><a name="pacfiles_manual"> </a></span><span class="sxs-lookup"><span data-stu-id="5d254-152"></span></span>

<span data-ttu-id="5d254-p111">Wenn Sie bereits erstellt haben etwas Sie verlassen freigeben möchten eine Notiz in den Kommentaren Nachfolgend einige weitere Tools aus der Community. None oder von Microsoft verwaltet und zu diesem Zweck hier bereitgestellten der Community, Tools verwiesen, die in diesem Artikel offiziell werden, unterstützt.</span><span class="sxs-lookup"><span data-stu-id="5d254-p111">Here's a few more tools from the community, if you've built something you'd like to share leave a note in the comments. None of the community tools referenced in this article are officially supported or maintained by Microsoft and are provided here for your convenience.</span></span>
  
- <span data-ttu-id="5d254-p112">Dies ist das älteste Community generierte Tool zur Verwaltung den Prozess, ein Tool von einem Mitglied der Office 365-Community erstellt. Es folgt Link zum [herunterladen](https://gallery.technet.microsoft.com/Office-365-Proxy-Pac-60fb28f7).</span><span class="sxs-lookup"><span data-stu-id="5d254-p112">This is the oldest community generated tool to help manage the process, a tool built by a member of the Office 365 community. Here is link to [download](https://gallery.technet.microsoft.com/Office-365-Proxy-Pac-60fb28f7).</span></span>
    
- <span data-ttu-id="5d254-157">Machbarkeitsstudie mit exportierbar Firewallregeln: [Microsoft Cloud IP-API](https://mscloudips.azurewebsites.net/).</span><span class="sxs-lookup"><span data-stu-id="5d254-157">Proof of Concept with exportable firewall rules: [Microsoft Cloud IP API](https://mscloudips.azurewebsites.net/).</span></span>
    
- <span data-ttu-id="5d254-158">IT-Praktyk: [RSS-Konvertierung](https://gallery.technet.microsoft.com/Convert-the-RSS-channel-5efe18b7) und [XML-Konvertierung](https://gallery.technet.microsoft.com/Convert-the-O365IPAddresses-9890d896).</span><span class="sxs-lookup"><span data-stu-id="5d254-158">From IT Praktyk: [RSS conversion](https://gallery.technet.microsoft.com/Convert-the-RSS-channel-5efe18b7) and [XML conversion](https://gallery.technet.microsoft.com/Convert-the-O365IPAddresses-9890d896).</span></span>
    
- <span data-ttu-id="5d254-159">Von Peter Abele: [herunterladen](https://gallery.technet.microsoft.com/How-to-create-an-up-to-b1fc33f3).</span><span class="sxs-lookup"><span data-stu-id="5d254-159">From Peter Abele: [Download](https://gallery.technet.microsoft.com/How-to-create-an-up-to-b1fc33f3).</span></span>
    
- <span data-ttu-id="5d254-p113">Verwenden Sie die Netzwerkanalyse um zu bestimmen, welches Netzwerk fordert sollte der Proxy-Infrastruktur zu umgehen. Die am häufigsten verwendeten FQDNs verwendet, um Kunden Proxys umgehen, aufgrund der Lautstärke des Netzwerkdatenverkehrs gesendet und Empfangen von diesen Endpunkten sind.</span><span class="sxs-lookup"><span data-stu-id="5d254-p113">Use your network analysis to determine which network requests should bypass your proxy infrastructure. The most common FQDNs used to bypass customer proxies include the following due to the volume of network traffic sent and received from these endpoints.</span></span>
    
  ```
  outlook.office365.com
  outlook.office.com
  <tenant-name>.sharepoint.com
  <tenant-name>-my.sharepoint.com
  <tenant-name>-<app>.sharepoint.com
  *.Lync.com
  
  ```

- <span data-ttu-id="5d254-162">Stellen Sie sicher, dass alle Netzwerk-Anforderungen, die direkt an die Firewall gesendet einen entsprechenden Eintrag in der Firewall Liste, um die Anforderung durchlaufen ermöglichen zulassen verfügen.</span><span class="sxs-lookup"><span data-stu-id="5d254-162">Ensure any network requests being sent to your firewall directly have a corresponding entry in the firewall allow list to allow the request to go through.</span></span>
    
## <a name="perimeter-network-integration"></a><span data-ttu-id="5d254-163">Umkreisnetzwerk Netzwerkintegration</span><span class="sxs-lookup"><span data-stu-id="5d254-163">Perimeter network integration</span></span>
<span data-ttu-id="5d254-164"><a name="BKMK_Perimeter"> </a></span><span class="sxs-lookup"><span data-stu-id="5d254-164"></span></span>

<span data-ttu-id="5d254-165">Wussten Sie schon Microsofts WAN ist eine der in der ganzen Welt der größten Backbones?</span><span class="sxs-lookup"><span data-stu-id="5d254-165">Did you know Microsoft's WAN is one of the largest backbones in the world?</span></span>
  
<span data-ttu-id="5d254-p114">Es ist true, dieses umfassende Netzwerk ist Office 365 und unsere anderen unabhängig von Ihrem Speicherort in der ganzen Welt arbeiten, die Sie Clouddiensten macht. Unser Netzwerk besteht aus hoher Bandbreite, Latenz, Failover-fähigen Links mit Tausenden von Route Meilen privat Besitzer dunkel Fiber und Multi-TBit-Verbindungen zwischen Rechenzentren und Edge-Knoten alle zu erleichtern, unsere Clouddienste zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="5d254-p114">It's true, this massive network is what makes Office 365 and our other cloud services work regardless of where in the world you are. Our network consists of high bandwidth, low latency, fail-over capable links with thousands of route miles of privately owned dark fiber, and multi-Terabit connections between datacenters and edge nodes, all to make it easier to use our cloud services.</span></span>
  
<span data-ttu-id="5d254-p115">Mit einem Netzwerk wie folgt möchten Sie die Geräte Ihrer Organisation so bald wie möglich mit unserem Netzwerk verbinden. Mit über 2500 Internetdienstanbieter Peers Beziehungen sollte Global und 70 Points of Presence, aus dem Netzwerk für unsere erste nahtlos. Es kann nicht lohnt, sich ein paar Minuten und stellen Sie sicher, dass bei Ihrem Internetdienstanbieter Peers Beziehung ist die am besten geeignete [Nachfolgend finden Sie einige Beispiele für](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__) des guten und nicht so gut Peers Hand und Nachteile auf Ihr Netzwerk.</span><span class="sxs-lookup"><span data-stu-id="5d254-p115">With a network like this, you want your organization's devices to connect to our network as soon as possible. With over 2500 ISP peering relationships globally and 70 points of presence, getting from your network to ours should be seamless. It can't hurt to spend a few minutes making sure your ISP's peering relationship is the most optimal, [here's a few examples](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__) of good and not so good peering hand-offs to our network.</span></span> 
  
<span data-ttu-id="5d254-p116">Sie können manuell oder automatisch die Geräte in Ihrem Netzwerk zum Verarbeiten von Office 365 Anwendung Netzwerk Anforderungen je nach Ihrer Geräte optimal konfigurieren. Welche Änderungen bei der Konfiguration Sie Office 365 Netzwerkdatenverkehr optimal behandeln müssen, hängt von Ihrer Umgebung. Office 365 Netzwerk Anforderungen von Netzwerkkonfigurationen bietet Vorteile, die Folgendes ermöglichen:</span><span class="sxs-lookup"><span data-stu-id="5d254-p116">You can manually or automatically configure the devices on your network to optimally handle Office 365 application network requests, depending on your equipment. What configuration changes you need to make to optimally handle Office 365 network traffic will depend on your environment. Office 365 network requests may benefit from network configurations that allow the following:</span></span>
  
- <span data-ttu-id="5d254-174">Priorität über weniger wichtige den Netzwerkdatenverkehr.</span><span class="sxs-lookup"><span data-stu-id="5d254-174">Priority over less critical network traffic.</span></span>
    
- <span data-ttu-id="5d254-p117">Weiterleitung an einen lokalen Ausgang zur Vermeidung von Backhauling über eine langsame WAN Link beim Nutzen der Vorteile von der verfügbaren Latenz im Microsoft-Netzwerk. [Hier ist eine gute Beschreibung](https://blogs.technet.microsoft.com/onthewire/2017/05/03/office-365-connectivity-guidance-part-2/) basierend auf Kundenprojekte.</span><span class="sxs-lookup"><span data-stu-id="5d254-p117">Routing to a local egress to avoid backhauling over a slow WAN link while taking advantage of the low latency available on the Microsoft network. [Here's a good discussion](https://blogs.technet.microsoft.com/onthewire/2017/05/03/office-365-connectivity-guidance-part-2/) based on customer engagements.</span></span> 
    
- <span data-ttu-id="5d254-177">Bei Verwendung des DNS in der Nähe einer lokalen Ausgang um sicherzustellen, dass die Netzwerk-Anforderung, die bewirkt, die lokalen Ausgang dass eingeht am nächstgelegenen Microsoft Speicherort Peers.</span><span class="sxs-lookup"><span data-stu-id="5d254-177">Using DNS near a local egress to ensure the network request that leaves the local egress arrives at the nearest Microsoft peering location.</span></span>
    
- <span data-ttu-id="5d254-178">Ausschluss von Tiefe Paketinspektion oder anderen intensive Netzwerkpakete verarbeitet, um die Wartezeit bei vertikaler Skalierung erfüllen.</span><span class="sxs-lookup"><span data-stu-id="5d254-178">Exclusion from deep packet inspection or other intensive network packet processing to meet latency requirements at scale.</span></span>
    
<span data-ttu-id="5d254-p118">Moderne Netzwerkgeräte enthalten Funktionen zum Verwalten von Netzwerk-Anforderungen für vertrauenswürdige Anwendungen wie etwa Office 365 anders als generischen, nicht vertrauenswürdigen Internet-Datenverkehr. Mit der neuen Querformat SD-WAN-Lösungen kann eine solche Differenzierung Datenverkehr und Pfad Auswahl auch mit der veränderbaren Zustand des Netzwerks, wie etwa Punkt in Zeiten, Latenz oder Leistung der verschiedenen Connectivity Pfade Aufklärung durchgeführt werden zwischen dem Benutzer und der Cloud.</span><span class="sxs-lookup"><span data-stu-id="5d254-p118">Modern network devices include capabilities to manage network requests for trusted applications such as Office 365 differently than generic, untrusted Internet traffic. With the emerging landscape of SD-WAN solutions, such differentiation of traffic and path selection can also be performed with awareness of the changing state of the network, such as point in time availability, latency or performance of various connectivity paths between the user and the cloud.</span></span>
  
<span data-ttu-id="5d254-181">Weitere Anleitungen zum Planen der Netzwerkkonfiguration finden Sie unter [Netzwerk- und Migration für Office 365 planen](network-and-migration-planning.md), [Behandlung von Leistungsproblemen Plan für Office 365](performance-troubleshooting-plan.md)und [Prüfliste für die bereitstellungsplanung für Office 365](deployment-planning-checklist.md) .</span><span class="sxs-lookup"><span data-stu-id="5d254-181">See [Network and migration planning for Office 365](network-and-migration-planning.md), [Performance troubleshooting plan for Office 365](performance-troubleshooting-plan.md), and [Deployment planning checklist for Office 365](deployment-planning-checklist.md) for additional guidance on planning your network configuration.</span></span> 
  
### <a name="to-implement-this-scenario"></a><span data-ttu-id="5d254-182">Zum Implementieren dieses Szenarios:</span><span class="sxs-lookup"><span data-stu-id="5d254-182">To implement this scenario:</span></span>

<span data-ttu-id="5d254-p119">Wenden Sie sich Ihr Netzwerk Lösung oder Dienstanbieter Wenn Sie Office 365-URL können und IP-Definitionen von XML in lokalen (für den Benutzer), geringe Kosten zu vereinfachen Netzwerk Ausgang für Office 365-Datenverkehr, dessen Priorität relativ zu anderen Applikationen verwalten und Anpassen der Der Netzwerkpfad für Office 365-Verbindungen in Microsoft-Netzwerk je nach netzwerkbedingungen ändern. Einige Lösungen herunterladen und Automatisierung von Office 365-URL und IP-XMLs Definition in ihren Stapeln.</span><span class="sxs-lookup"><span data-stu-id="5d254-p119">Check with your network solution or service provider if they can use Office 365 URL and IP definitions from XML to facilitate local (to the user), low overhead network egress for Office 365 traffic, manage its priority relative to other applications and adjust the network path for Office 365 connections into Microsoft network depending on changing network conditions. Some solutions download and automate Office 365 URL and IP XMLs definition in their stacks.</span></span>
  
<span data-ttu-id="5d254-185">Stellen Sie unbedingt sicher, dass die implementierte Lösung erforderlichen Maß an Flexibilität, entsprechende Geo-Redundanz der Netzwerkpfad für Office 365-Datenverkehr und Änderungen an Office 365-URLs und IP-Adressen ausgelegt ist, wie sie veröffentlicht werden.</span><span class="sxs-lookup"><span data-stu-id="5d254-185">Always ensure that the implemented solution has necessary degree of resiliency, appropriate geo-redundancy of the network path for Office 365 traffic and accommodates changes to Office 365 URLs and IPs as they become published.</span></span>
  
## <a name="web-service"></a><span data-ttu-id="5d254-186">Webdienst</span><span class="sxs-lookup"><span data-stu-id="5d254-186">Web service</span></span>
<span data-ttu-id="5d254-187"><a name="webservice"> </a></span><span class="sxs-lookup"><span data-stu-id="5d254-187"></span></span>

<span data-ttu-id="5d254-p120">Zur einfacheren besser identifizieren und Office 365-Netzwerkverkehr zu unterscheiden, veröffentlicht ein neuen Webdienst Office 365-Endpunkten, die ausgewertet werden soll, konfigurieren und bleiben Sie auf den neuesten Stand mit Änderungen erleichtern. Diese neuen Webdienst (jetzt in der Vorschau), wird schließlich die Listen von Endpunkten im Artikel [Office 365-URLs und IP-Adressbereichen](urls-and-ip-address-ranges.md) zusammen mit den RSS-Feed und XML-Versionen dieser Daten ersetzen. Diese Format der Endpunktdaten werden voraussichtlich auf 2 Oktober 2018 im Laufe der Zeit.</span><span class="sxs-lookup"><span data-stu-id="5d254-p120">To help you better identify and differentiate Office 365 network traffic, a new web service publishes Office 365 endpoints, making it easier for you to evaluate, configure, and stay up to date with changes. This new web service (now in preview), will eventually replace the lists of endpoints in the [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md) article, along with the RSS and XML versions of that data. These format of endpoint data are planned to be phased out on October 2, 2018.</span></span> 
  
<span data-ttu-id="5d254-191">Als einem Kunden oder einer Netzwerk Umkreisnetzwerk Gerätehersteller können Sie für den neuen REST basierenden Webdienst für die Office 365-IP-Adresse und den FQDN-Einträge erstellen.</span><span class="sxs-lookup"><span data-stu-id="5d254-191">As a customer or a network perimeter device vendor, you can build against the new REST-based web service for the Office 365 IP address and FQDN entries.</span></span>
  
- <span data-ttu-id="5d254-192">Verwenden Sie für die neueste Version von Office 365-URLs und IP-Adressbereiche, [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="5d254-192">For the latest version of the Office 365 URLs and IP address ranges, use [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
    
- <span data-ttu-id="5d254-193">Verwenden Sie für die Daten auf der Office 365-URLs und IP-Adressbereiche Seite für Firewalls und Proxyserver, [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="5d254-193">For the data on the Office 365 URLs and IP address ranges page for firewalls and proxy servers, use [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
    
- <span data-ttu-id="5d254-194">Wenn Sie die neuesten Änderungen erhalten möchten, verwenden Sie [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="5d254-194">To get the latest changes, use [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
    
<span data-ttu-id="5d254-195">Ein Kunde können Sie diesen Webdienst zu verwenden:</span><span class="sxs-lookup"><span data-stu-id="5d254-195">As a customer, you can use this web service to:</span></span> 
  
- <span data-ttu-id="5d254-196">Aktualisieren Sie PowerShell-Skripts, die Office 365-Endpunktdaten abrufen und Ändern der Formatierung für Ihre Netzwerkgeräte.</span><span class="sxs-lookup"><span data-stu-id="5d254-196">Update your PowerShell scripts to obtain Office 365 endpoint data and modify any formatting for your networking devices.</span></span>
    
- <span data-ttu-id="5d254-197">Anhand dieser Informationen zum Aktualisieren von PAC-Dateien auf Clientcomputern bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="5d254-197">Use this information to update PAC files deployed to client computers.</span></span>
    
<span data-ttu-id="5d254-198">Als ein Netzwerk Umkreisnetzwerk Gerätehersteller können Sie diesen Webdienst zu verwenden:</span><span class="sxs-lookup"><span data-stu-id="5d254-198">As a network perimeter device vendor, you can use this web service to:</span></span> 
  
- <span data-ttu-id="5d254-199">Erstellen Sie und Testen Sie der Gerätesoftware, um der Liste für automatisierte Konfiguration herunterzuladen.</span><span class="sxs-lookup"><span data-stu-id="5d254-199">Create and test device software to download the list for automated configuration.</span></span> 
    
- <span data-ttu-id="5d254-200">Überprüfen Sie die aktuelle Version.</span><span class="sxs-lookup"><span data-stu-id="5d254-200">Check for the current version.</span></span>
    
- <span data-ttu-id="5d254-201">Rufen Sie die aktuellen Änderungen.</span><span class="sxs-lookup"><span data-stu-id="5d254-201">Get the current changes.</span></span>
    
<span data-ttu-id="5d254-202">In den folgenden Abschnitten wird beschrieben, die Vorschau für diesen Webdienst, die über einen Zeitraum, bis der Dienst erhältlich ist unterschiedlich sein kann.</span><span class="sxs-lookup"><span data-stu-id="5d254-202">The following sections describe the preview of this web service, which might change over time until the service is generally available.</span></span> 
  
<span data-ttu-id="5d254-203">Die Daten auf den Webdienst auf dem aktuellen Stand sind und es sind weitere Änderungen an den Webdienst-URLs vornehmen nicht Vorhaben oder Datenschema vor der Veröffentlichung allgemeine Verfügbarkeit für diesen Webdienst zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="5d254-203">The data on the web service is up to date and we are not planning to make further changes to the web service URLs or returned data schema before the general availability release of this web service.</span></span>
  
<span data-ttu-id="5d254-204">Weitere Informationen finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="5d254-204">For additional information, see:</span></span>
  
- [<span data-ttu-id="5d254-205">Ankündigung Blogbeitrag in Office 365 Tech-Community-Forum</span><span class="sxs-lookup"><span data-stu-id="5d254-205">Announcement blog post in the Office 365 Tech Community Forum</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
    
- [<span data-ttu-id="5d254-206">Office 365 Tech Community-Forum für Fragen zur Verwendung der Webdienste</span><span class="sxs-lookup"><span data-stu-id="5d254-206">Office 365 Tech Community Forum for questions about use of the web services</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)
    
### <a name="common-parameters"></a><span data-ttu-id="5d254-207">Allgemeine Parameter</span><span class="sxs-lookup"><span data-stu-id="5d254-207">Common parameters</span></span>

<span data-ttu-id="5d254-208">Diese Parameter sind über alle Webdienstmethoden gemeinsam:</span><span class="sxs-lookup"><span data-stu-id="5d254-208">These parameters are common across all the web service methods:</span></span>
  
- <span data-ttu-id="5d254-p121">**Format CSV = | JSON** -Abfragezeichenfolgen-Parameter fest. Standardmäßig wird das Format der zurückgegebenen Daten JSON. Schließen Sie diese optionale Parameter, um die Daten in einer durch Trennzeichen getrennten Werten (CSV) Format zurückgeben ein.</span><span class="sxs-lookup"><span data-stu-id="5d254-p121">**format=CSV | JSON** - Query string parameter. By default, the returned data format is JSON. Include this optional parameter to return the data in comma-separated values (CSV) format.</span></span> 
    
- <span data-ttu-id="5d254-p122">**ClientRequestId** - Abfragezeichenfolgen-Parameter fest. Eine erforderliche GUID, die Sie für die Zuordnung für Client-Sitzung zu generieren. Sie sollten eine GUID für jeden Clientcomputer erstellen, die den Webdienst aufruft. Verwenden Sie nicht die GUIDs in den folgenden Beispielen dargestellt, da sie in der Zukunft vom Webdienst blockiert werden können. GUID-Format ist Xxxxxxxx-Xxxx-Xxxx-Xxxx-Xxxxxxxxxxxx, wobei x eine hexadezimale Zahl darstellt. Um eine GUID generieren möchten, verwenden Sie den PowerShell-Befehl [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) .</span><span class="sxs-lookup"><span data-stu-id="5d254-p122">**ClientRequestId** - Query string parameter. A required GUID that you generate for client session association. You should generate a GUID for each client machine that calls the web service. Do not use the GUIDs shown in the following examples because they may be blocked by the web service in the future. GUID format is xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx, where x represents a hexadecimal number. To generate a GUID, use the [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell command.</span></span> 
    
### <a name="version-web-method"></a><span data-ttu-id="5d254-218">Version-Webmethode</span><span class="sxs-lookup"><span data-stu-id="5d254-218">Version web method</span></span>

<span data-ttu-id="5d254-p123">Microsoft Office 365-IP-Adresse und FQDN-Einträge am Ende eines jeden Monat und gelegentlich nicht genügend Cycle für aktualisiert betriebsbereit oder Anforderungen unterstützt. Die Daten für jede Instanz veröffentlichte werden eine Versionsnummer zugewiesen. Die Version-Web-Methode können Sie die für die neueste Version für jede Instanz der Office 365-Abfragen. Es wird empfohlen, dass die Version täglich, oder höchstens, stündlich zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="5d254-p123">Microsoft updates the Office 365 IP address and FQDN entries at the end of each month and occasionally out of cycle for operational or support requirements. The data for each published instance is assigned a version number. The version web method lets you poll for the latest version for each Office 365 service instance. We recommend you check the version daily, or at the most, hourly.</span></span>
  
<span data-ttu-id="5d254-223">Es gibt einen Parameter für die Version-Webmethode:</span><span class="sxs-lookup"><span data-stu-id="5d254-223">There is one parameter for the version web method:</span></span>
  
- <span data-ttu-id="5d254-p124">**AllVersions = True** -Abfragezeichenfolgen-Parameter fest. Standardmäßig ist die zurückgegebene Version der neuesten. Schließen Sie diese optionale Parameter um anzufordern, dass alle Versionen veröffentlichten ein.</span><span class="sxs-lookup"><span data-stu-id="5d254-p124">**AllVersions=true** - Query string parameter. By default, the version returned is the latest. Include this optional parameter to request all published versions.</span></span> 
    
- <span data-ttu-id="5d254-p125">**Instanz** - Route-Parameter. Dieser optionale Parameter gibt die Instanz, um die Version für zurückzugeben. Wenn Length angegeben, werden alle Instanzen zurückgegeben. Gültige Instanzen sind: weltweit, China, Deutschland, USGovDoD, USGovGCCHigh</span><span class="sxs-lookup"><span data-stu-id="5d254-p125">**Instance** - Route parameter. This optional parameter specifies the instance to return the version for. If omitted, all instances are returned. Valid instances are: Worldwide, China, Germany, USGovDoD, USGovGCCHigh</span></span> 
    
<span data-ttu-id="5d254-p126">Das Ergebnis der Version-Webmethode möglicherweise einen einzelnen Datensatz oder ein Array von Datensätzen. Die Elemente der einzelnen Datensätze sind:</span><span class="sxs-lookup"><span data-stu-id="5d254-p126">The result from the version web method may be a single record or an array of records. The elements of each record are:</span></span>
  
- <span data-ttu-id="5d254-233">Instanz - den kurzen Namen des der Office 365-Dienstinstanz.</span><span class="sxs-lookup"><span data-stu-id="5d254-233">instance - The short name of the Office 365 service instance.</span></span>
    
- <span data-ttu-id="5d254-234">neueste - die neueste Version für Endpunkte der angegebenen Instanz.</span><span class="sxs-lookup"><span data-stu-id="5d254-234">latest - The latest version for endpoints of the specified instance.</span></span>
    
- <span data-ttu-id="5d254-p127">Versionen – eine Liste mit allen früheren Versionen für die angegebene Instanz. Dieses Element ist nur aufgenommen, wenn der Parameter AllVersions "true" ist.</span><span class="sxs-lookup"><span data-stu-id="5d254-p127">versions - A list of all previous versions for the specified instance. This element is only included if the AllVersions parameter is true.</span></span>
   
#### <a name="examples"></a><span data-ttu-id="5d254-237">Beispiele:</span><span class="sxs-lookup"><span data-stu-id="5d254-237">Examples:</span></span>
  
<span data-ttu-id="5d254-238">In Beispiel 1 Anforderungs-URI: ** <span>Https:</span>//endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span><span class="sxs-lookup"><span data-stu-id="5d254-238">Example 1 request URI: **<span>https:</span>//endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span></span>
  
<span data-ttu-id="5d254-p128">Dieser URI Gibt die neueste Version der einzelnen Office 365-Dienstinstanzen zurück. Beispiel-Ergebnis:</span><span class="sxs-lookup"><span data-stu-id="5d254-p128">This URI returns the latest version of each Office 365 service instance. Example result:</span></span>
  
```
[
 {
  "instance": "Worldwide", 
  "latest": "2018063000"
 },
 {
  "instance": "USGovDoD", 
  "latest": "2018063000"
 },
 {
  "instance": "USGovGCCHigh",
  "latest": "2018063000"
 },
 {
  "instance": "China",
  "latest": "2018063000"
 },
 {
  "instance": "Germany",
  "latest": "2018063000"
 }
] 
```

> [!IMPORTANT]
> <span data-ttu-id="5d254-p129">Die GUID für den Parameter ClientRequestID in dieser URIs sind nur ein Beispiel. Zum Testen des Web service URIs out, Ihre eigene GUID zu generieren. Die GUIDs in diesen Beispielen gezeigt können vom Webdienst in der Zukunft blockiert werden.</span><span class="sxs-lookup"><span data-stu-id="5d254-p129">The GUID for the ClientRequestID parameter in these URIs are only an example. To try the web service URIs out, generate your own GUID. The GUIDs shown in these examples may be blocked by the web service in the future.</span></span> 
  
<span data-ttu-id="5d254-244">In Beispiel 2 Anforderungs-URI: ** <span>Https:</span>//endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span><span class="sxs-lookup"><span data-stu-id="5d254-244">Example 2 request URI: **<span>https:</span>//endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span></span>
  
<span data-ttu-id="5d254-p130">Dieser URI wird die aktuelle Version der angegebenen Instanz von Office 365-Dienst zurück. Beispiel-Ergebnis:</span><span class="sxs-lookup"><span data-stu-id="5d254-p130">This URI returns the latest version of the specified Office 365 service instance. Example result:</span></span>
  
```
{
 "instance": "Worldwide",
 "latest": "2018063000"
}
```

<span data-ttu-id="5d254-247">Beispiel 3 Anforderungs-URI: ** <span>Https:</span>//endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId = b10c5ed1-bad1-445f-b386-b919946339a7**</span><span class="sxs-lookup"><span data-stu-id="5d254-247">Example 3 request URI: **<span>https:</span>//endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span></span>
  
<span data-ttu-id="5d254-p131">Dieser URI zeigt die Ausgabe im CSV-Format. Beispiel-Ergebnis:</span><span class="sxs-lookup"><span data-stu-id="5d254-p131">This URI shows output in CSV format. Example result:</span></span>
  
```
instance,latest
Worldwide,2018063000
```

<span data-ttu-id="5d254-250">Beispiel 4 Anforderungs-URI: ** <span>Https:</span>//endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId = b10c5ed1-bad1-445f-b386-b919946339a7**</span><span class="sxs-lookup"><span data-stu-id="5d254-250">Example 4 request URI: **<span>https:</span>//endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span></span>
  
<span data-ttu-id="5d254-p132">Dieser URI zeigt alle bisherigen Versionen, die für die Office 365 weltweit Suchdienstinstanz veröffentlicht wurden. Beispiel-Ergebnis:</span><span class="sxs-lookup"><span data-stu-id="5d254-p132">This URI shows all prior versions that have been published for the Office 365 worldwide service instance. Example result:</span></span>
  
```
{
  "instance": "Worldwide",
  "latest": "2018063000",
  "versions": [
    "2018063000",
    "2018062000"
  ]
}
```

### <a name="endpoints-web-method"></a><span data-ttu-id="5d254-253">Endpunkte Web-Methode</span><span class="sxs-lookup"><span data-stu-id="5d254-253">Endpoints web method</span></span>

<span data-ttu-id="5d254-p133">Die Endpunkte Webmethode gibt alle Datensätze für IP-Adressbereiche und URLs, die Office 365-Dienst bilden. Parameter für die Webmethode Endpunkte sind:</span><span class="sxs-lookup"><span data-stu-id="5d254-p133">The endpoints web method returns all records for IP address ranges and URLs that make up the Office 365 service. Parameters for the endpoints web method are:</span></span>
  
- <span data-ttu-id="5d254-p134">**ServiceAreas** - Abfragezeichenfolgen-Parameter fest. Eine durch Trennzeichen getrennte Liste der Dienstbereiche. Gültige Elemente werden gängige, Exchange, SharePoint, Skype. Da gemeinsame Dienst Bereich Elemente Voraussetzung für alle anderen Dienstbereiche sind, wird Sie von der Webdienst immer aufzunehmen. Wenn Sie diesen Parameter nicht angeben, werden alle Servicebereiche zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="5d254-p134">**ServiceAreas** - Query string parameter. A comma-separated list of service areas. Valid items are Common,Exchange,SharePoint,Skype. Because Common service area items are a prerequisite for all other service areas, the web service will always include them. If you do not include this parameter, all service areas are returned.</span></span> 
    
- <span data-ttu-id="5d254-p135">**TenantName** - Abfragezeichenfolgen-Parameter fest. Name Ihrer Office 365-Mandanten. Der Webdienst erhält Ihre bereitgestellten Namen und fügt es in Teilen von URLs, die den Mandantennamen enthalten. Wenn Sie einen Mandantennamen nicht angeben, haben die Teile der URLs das Platzhalterzeichen (\*).</span><span class="sxs-lookup"><span data-stu-id="5d254-p135">**TenantName** - Query string parameter. Your Office 365 tenant name. The web service takes your provided name and inserts it in parts of URLs that include the tenant name. If you don't provide a tenant name, those parts of URLs have the wildcard character (\*).</span></span> 
    
- <span data-ttu-id="5d254-p136">**NoIPv6** - Abfragezeichenfolgen-Parameter fest. Diese Option, um auf true gesetzt ausschließen IPv6-Adressen aus der Ausgabe beispielsweise, wenn Sie IPv6 in Ihrem Netzwerk nicht verwenden.</span><span class="sxs-lookup"><span data-stu-id="5d254-p136">**NoIPv6** - Query string parameter. Set this to true to exclude IPv6 addresses from the output, for example, if you don't use IPv6 in your network.</span></span> 
    
- <span data-ttu-id="5d254-p137">**Instanz** - Route-Parameter. Dieser erforderliche Parameter gibt die Instanz, um die Endpunkte für zurückzugeben. Gültige Instanzen sind: weltweit, China, Deutschland, USGovDoD, USGovGCCHigh.</span><span class="sxs-lookup"><span data-stu-id="5d254-p137">**Instance** - Route parameter. This required parameter specifies the instance to return the endpoints for. Valid instances are: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span></span> 
    
<span data-ttu-id="5d254-p138">Das Ergebnis der Endpunkte Web-Methode wird ein Array von Datensätzen mit jeder Datensatz einen Endpunkt Satz darstellt. Die Elemente für jeden Datensatz sind:</span><span class="sxs-lookup"><span data-stu-id="5d254-p138">The result from the endpoints web method is an array of records with each record representing an endpoint set. The elements for each record are:</span></span>
  
- <span data-ttu-id="5d254-272">ID - legen Sie die unveränderlich ID-Nummer des Endpunkts.</span><span class="sxs-lookup"><span data-stu-id="5d254-272">id - The immutable id number of the endpoint set.</span></span>
    
- <span data-ttu-id="5d254-273">ServiceArea - Servicebereich, die dies gehört: Allgemein, Exchange, SharePoint oder Skype.</span><span class="sxs-lookup"><span data-stu-id="5d254-273">serviceArea - The service area that this is part of: Common, Exchange, SharePoint, or Skype.</span></span>
    
- <span data-ttu-id="5d254-p139">Legen Sie URLs - URLs für den Endpunkt. Ein JSON-Array von DNS-Einträgen. Weggelassen, wenn leer.</span><span class="sxs-lookup"><span data-stu-id="5d254-p139">urls - URLs for the endpoint set. A JSON array of DNS records. Omitted if blank.</span></span>
    
- <span data-ttu-id="5d254-p140">TcpPorts - legen Sie TCP-Ports für den Endpunkt. Alle Ports Elemente werden als eine durch Trennzeichen getrennte Liste der oder Portbereiche getrennt durch ein Bindestrich (-) formatiert. Ports gelten für alle IP-Adressen und alle URLs, insofern Endpunkt für die Kategorie festgelegt. Weggelassen, wenn leer.</span><span class="sxs-lookup"><span data-stu-id="5d254-p140">tcpPorts - TCP ports for the endpoint set. All ports elements are formatted as a comma-separated list of ports or port ranges separated by a dash character (-). Ports apply to all IP addresses and all URLs in that endpoint set for that category. Omitted if blank.</span></span>
    
- <span data-ttu-id="5d254-p141">UdpPorts - UDP-Ports für die IP-Adressbereiche in den folgenden Endpunkt. Weggelassen, wenn leer.</span><span class="sxs-lookup"><span data-stu-id="5d254-p141">udpPorts - UDP ports for the IP address ranges in this endpoint set. Omitted if blank.</span></span>
    
- <span data-ttu-id="5d254-p142">IP-Adressen - die IP-Adressbereiche, die die mit diesem Endpunkt festlegen, wie die aufgeführten TCP oder UDP-Ports zugeordnet. Weggelassen, wenn leer.</span><span class="sxs-lookup"><span data-stu-id="5d254-p142">ips - The IP address ranges associated with this endpoint set as associated with the listed TCP or UDP ports. Omitted if blank.</span></span>
    
- <span data-ttu-id="5d254-p143">Kategorie - legen Sie die Konnektivität Kategorie für den Endpunkt. Gültige Werte sind optimieren, zulassen und Standard. Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="5d254-p143">category - The connectivity category for the endpoint set. Valid values are Optimize, Allow, and Default. Required.</span></span>
    
- <span data-ttu-id="5d254-288">ExpressRoute - True oder false zurück, wenn diese Sammlung Endpunkt über ExpressRoute weitergeleitet wird.</span><span class="sxs-lookup"><span data-stu-id="5d254-288">expressRoute - True or False if this endpoint set is routed over ExpressRoute.</span></span>
    
- <span data-ttu-id="5d254-p144">erforderlich - true zurück, wenn dieser Endpunkt Satz erforderlich, eine Verbindung zwischen für Office 365 unterstützt werden müssen. Weggelassen, wenn false.</span><span class="sxs-lookup"><span data-stu-id="5d254-p144">required - True if this endpoint set is required to have connectivity for Office 365 to be supported. Omitted if false.</span></span>
    
- <span data-ttu-id="5d254-p145">Notes - für optionale Endpunkte dieser Text wird beschrieben, Office 365-Funktionalität, wenn IP-Adressen fehlen oder URLs in diesen Endpunkt Set auf Netzwerkebene kann nicht zugegriffen werden. Weggelassen, wenn leer.</span><span class="sxs-lookup"><span data-stu-id="5d254-p145">notes - For optional endpoints, this text describes Office 365 functionality that will be missing if IP addresses or URLs in this endpoint set cannot be accessed at the network layer. Omitted if blank.</span></span>
    
#### <a name="examples"></a><span data-ttu-id="5d254-293">Beispiele:</span><span class="sxs-lookup"><span data-stu-id="5d254-293">Examples:</span></span>
  
<span data-ttu-id="5d254-294">In Beispiel 1 Anforderungs-URI: ** <span>Https:</span>//endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span><span class="sxs-lookup"><span data-stu-id="5d254-294">Example 1 request URI: **<span>https:</span>//endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span></span>
  
<span data-ttu-id="5d254-p146">Dieser URI Ruft alle Endpunkte für die Instanz der Office 365 weltweit für alle Arbeitslasten ab. Beispiel Ergebnis ist einen Auszug aus der Ausgabe angezeigt:</span><span class="sxs-lookup"><span data-stu-id="5d254-p146">This URI obtains all endpoints for the Office 365 worldwide instance for all workloads. Example result showing an excerpt of the output:</span></span>
  
```
[ 
 { 
  "id": 1, 
  "serviceArea": "Exchange", 
  "serviceAreaDisplayName": "Exchange Online", 
  "urls": 
   [ 
    "*.protection.outlook.com" 
   ], 
  "ips": 
   [ 
    "2a01:111:f403::/48", "23.103.132.0/22", "23.103.136.0/21", "23.103.198.0/23", "23.103.212.0/22", "40.92.0.0/14", "40.107.0.0/17", "40.107.128.0/18", "52.100.0.0/14", "213.199.154.0/24", "213.199.180.128/26", "94.245.120.64/26", "207.46.163.0/24", "65.55.88.0/24", "216.32.180.0/23", "23.103.144.0/20", "65.55.169.0/24", "207.46.100.0/24", "2a01:111:f400:7c00::/54", "157.56.110.0/23", "23.103.200.0/22", "104.47.0.0/17", "2a01:111:f400:fc00::/54", "157.55.234.0/24", "157.56.112.0/24", "52.238.78.88/32" 
   ], 
  "tcpPorts": "443", 
  "expressRoute": true, 
  "category": "Allow" 
 }, 
 { 
  "id": 2, 
  "serviceArea": "Exchange", 
  "serviceAreaDisplayName": "Exchange Online", 
  "urls": 
   [ 
    "*.mail.protection.outlook.com" 
   ],
...
```

<span data-ttu-id="5d254-297">Zusätzliche Endpunkt legt sind nicht in diesem Beispiel enthalten.</span><span class="sxs-lookup"><span data-stu-id="5d254-297">Additional endpoint sets are not included in this example.</span></span>
  
<span data-ttu-id="5d254-298">In Beispiel 2 Anforderungs-URI: ** <span>Https:</span>//endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId = b10c5ed1-bad1-445f-b386-b919946339a7**</span><span class="sxs-lookup"><span data-stu-id="5d254-298">Example 2 request URI: **<span>https:</span>//endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span></span>
  
<span data-ttu-id="5d254-299">Dieses Beispiel ruft Endpunkte für die Office 365 weltweit Instanz für Exchange Online und nur Abhängigkeiten.</span><span class="sxs-lookup"><span data-stu-id="5d254-299">This example obtains endpoints for the Office 365 Worldwide instance for Exchange Online and dependencies only.</span></span>
  
<span data-ttu-id="5d254-300">Die Ausgabe Beispiel 2 ist ähnlich wie in Beispiel 1, außer dass die Ergebnisse nicht für Business Online Endpunkte für SharePoint Online oder Skype umfassen.</span><span class="sxs-lookup"><span data-stu-id="5d254-300">The output for example 2 is similar to example 1 except that the results will not include endpoints for SharePoint Online or Skype for Business Online.</span></span>
  
### <a name="changes-web-method"></a><span data-ttu-id="5d254-301">Änderungen web-Methode</span><span class="sxs-lookup"><span data-stu-id="5d254-301">Changes web method</span></span>

<span data-ttu-id="5d254-p147">Die Änderungen Web-Methode gibt den neuesten Updates, die veröffentlicht wurden. Dies ist üblicherweise des vorherigen Monats Änderungen an URLs und IP-Adressbereiche.</span><span class="sxs-lookup"><span data-stu-id="5d254-p147">The changes web method returns the most recent updates that have been published. This is typically the previous month's changes to IP address ranges and URLs.</span></span>
  
> [!NOTE]
> <span data-ttu-id="5d254-304">Daten aus der Änderungen API sollte richtig sind in der Vorschau und verwendeten für die Entwicklung und Test nur.</span><span class="sxs-lookup"><span data-stu-id="5d254-304">Data from the changes API is accurate in the preview and should be used for development and testing only.</span></span> 
  
<span data-ttu-id="5d254-305">Der Parameter für die Änderungen Webmethode ist:</span><span class="sxs-lookup"><span data-stu-id="5d254-305">The parameter for the changes web method is:</span></span>
  
- <span data-ttu-id="5d254-p148">**Version** - URL erforderlich Route-Parameter. Die Version, die derzeit implementiert haben, und die Änderungen seit dieser Version anzeigen möchten. Das Format lautet YYYYMMDDNN.</span><span class="sxs-lookup"><span data-stu-id="5d254-p148">**Version** - Required URL route parameter. The version that you have currently implemented, and you want to see the changes since that version. The format is YYYYMMDDNN.</span></span> 
    
<span data-ttu-id="5d254-p149">Das Ergebnis der Änderungen Web-Methode wird ein Array von Datensätzen mit jeder Datensatz, der eine Änderung in einer bestimmten Version der Endpunkte darstellt. Die Elemente für jeden Datensatz sind:</span><span class="sxs-lookup"><span data-stu-id="5d254-p149">The result from the changes web method is an array of records with each record representing a change in a specific version of the endpoints. The elements for each record are:</span></span>
  
- <span data-ttu-id="5d254-311">ID - die unveränderlich-Id des Datensatzes ändern.</span><span class="sxs-lookup"><span data-stu-id="5d254-311">id - The immutable id of the change record.</span></span>
    
- <span data-ttu-id="5d254-p150">EndpointSetId - die ID des Endpunkts festlegen-Eintrag, der geändert wird. Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="5d254-p150">endpointSetId - The ID of the endpoint set record that is changed. Required.</span></span>
    
- <span data-ttu-id="5d254-314">Disposition - Dies kann entweder der ändern, hinzufügen oder entfernen und beschreibt, was die Änderung an den Endpunkt Set-Datensatz haben.</span><span class="sxs-lookup"><span data-stu-id="5d254-314">disposition - This can be either of change, add, or remove and describes what the change did to the endpoint set record.</span></span>
    
- <span data-ttu-id="5d254-p151">Version - die Version der veröffentlichten Endpunkt festgelegt, in dem die Änderung eingeführt wurde. Versionsnummern sind erforderlich, um einen einzelnen Tag veröffentlicht werden mehrere Versionen des Formats YYYYMMDDNN, wobei NN eine natürliche Zahl erhöht ist, wenn vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="5d254-p151">version - The version of the published endpoint set in which the change was introduced. Version numbers are of the format YYYYMMDDNN, where NN is a natural number incremented if there are multiple versions required to be published on a single day.</span></span>
    
- <span data-ttu-id="5d254-p152">frühere - legen Sie eine Unterstruktur mit ausführlichen Informationen zu vorherigen Werte der geänderten Elemente für den Endpunkt. Dadurch werden nicht für neu hinzugefügte Endpunkt Gruppen enthalten sein. Enthält TcpPorts, UdpPorts, ExpressRoute, Kategorie, die erforderlich sind, Notizen.</span><span class="sxs-lookup"><span data-stu-id="5d254-p152">previous - A substructure detailing previous values of changed elements on the endpoint set. This will not be included for newly added endpoint sets. Includes tcpPorts, udpPorts, ExpressRoute, category, required, notes.</span></span>
    
- <span data-ttu-id="5d254-p153">Current – eine Unterstruktur mit ausführlichen Informationen zu aktualisierten Werte von Elementen auf der Endpoinset ändert. Enthält TcpPorts, UdpPorts, ExpressRoute, Kategorie, die erforderlich sind, Notizen.</span><span class="sxs-lookup"><span data-stu-id="5d254-p153">current - A substructure detailing updated values of changes elements on the endpoinset. Includes tcpPorts, udpPorts, ExpressRoute, category, required, notes.</span></span>
    
- <span data-ttu-id="5d254-p154">Add - Sammlungen legen Sie eine Sub-Struktur mit ausführlichen Informationen zu Elementen, Endpunkt hinzugefügt werden soll. Weggelassen, wenn keine Ergänzungen vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="5d254-p154">add - A sub structure detailing items to be added to endpoint set collections. Omitted if there are no additions.</span></span>
    
  - <span data-ttu-id="5d254-324">EffectiveDate - definiert die Daten, die bei die Ergänzungen werden live im Dienst.</span><span class="sxs-lookup"><span data-stu-id="5d254-324">effectiveDate - Defines the data when the additions will be live in the service.</span></span>
    
  - <span data-ttu-id="5d254-325">IP-Adressen - Elemente in das Array von IP-Adressen hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="5d254-325">ips - Items to be added to the ips array.</span></span>
    
  - <span data-ttu-id="5d254-326">URLs-Elemente, die Urls Array hinzugefügt werden soll.</span><span class="sxs-lookup"><span data-stu-id="5d254-326">urls- Items to be added to the urls array.</span></span>
    
- <span data-ttu-id="5d254-p155">Remove - legen Sie eine Unterstruktur mit ausführlichen Informationen zu Elementen, die vom Endpunkt entfernt werden. Weggelassen, wenn keine entfernungen vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="5d254-p155">remove - A substructure detailing items to be removed from the endpoint set. Omitted if there are no removals.</span></span>
    
  - <span data-ttu-id="5d254-329">IP-Adressen - Elemente aus dem Array von IP-Adressen entfernt werden soll.</span><span class="sxs-lookup"><span data-stu-id="5d254-329">ips - Items to be removed from the ips array.</span></span>
    
  - <span data-ttu-id="5d254-330">URLs-Elemente aus dem Array Urls entfernt werden soll.</span><span class="sxs-lookup"><span data-stu-id="5d254-330">urls- Items to be removed from the urls array.</span></span>
    
 <span data-ttu-id="5d254-331">**Beispiele:**</span><span class="sxs-lookup"><span data-stu-id="5d254-331">**Examples:**</span></span>
  
<span data-ttu-id="5d254-332">In Beispiel 1 Anforderungs-URI: ** <span>Https:</span>//endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span><span class="sxs-lookup"><span data-stu-id="5d254-332">Example 1 request URI: **<span>https:</span>//endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span></span>
  
<span data-ttu-id="5d254-p156">Fordert alle vorherige Änderungen an der Office 365 weltweit-Dienstinstanz an. Beispiel-Ergebnis:</span><span class="sxs-lookup"><span data-stu-id="5d254-p156">This requests all previous changes to the Office 365 worldwide service instance. Example result:</span></span>
  
```
[ 
 { 
  "id": 424, 
  "endpointSetId": 32, 
  "disposition": "Change", 
  "version": "2018062700", 
  "remove": 
   { 
    "urls": 
     [ 
      "*.api.skype.com", "skypegraph.skype.com" 
     ] 
   } 
 }, 
 { 
  "id": 426, 
  "endpointSetId": 31, 
  "disposition": "Change", 
  "version": "2018062700", 
  "add": 
   { 
    "effectiveDate": "20180609", 
    "ips": 
     [ 
      "51.140.203.190/32" 
     ]
   },
  "remove": 
   { 
    "ips": 
     [
...

```

<span data-ttu-id="5d254-335">In Beispiel 2 Anforderungs-URI: ** <span>Https:</span>//endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span><span class="sxs-lookup"><span data-stu-id="5d254-335">Example 2 request URI: **<span>https:</span>//endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span></span>
  
<span data-ttu-id="5d254-p157">Dies fordert Änderungen seit der angegebenen Version der Office 365 weltweit Instanz. In diesem Fall wird die angegebene Version die neuesten. Beispiel-Ergebnis:</span><span class="sxs-lookup"><span data-stu-id="5d254-p157">This requests changes since the specified version to the Office 365 Worldwide instance. In this case, the version specified is the latest. Example result:</span></span>
  
```
[
  {
    "id":3,
    "endpointSetId":33,
    "changeDescription":"Removing old IP prefixes",
    "disposition":"Change",
    "version":"2018031301",
    "remove":{
      "ips":["65.55.127.0/24","66.119.157.192/26","66.119.158.0/25",
      "111.221.76.128/25","111.221.77.0/26","207.46.5.0/24"]
    }
  },
  {
    "id":4,
    "endpointSetId":45,
    "changeDescription":"Removing old IP prefixes",
    "disposition":"Change",
    "version":"2018031301",
    "remove":{
      "ips":["13.78.93.8/32","40.113.87.220/32","40.114.149.220/32",
      "40.117.100.83/32","40.118.214.164/32","104.208.31.113/32"]
    }
  }
]

```

### <a name="example-powershell-script"></a><span data-ttu-id="5d254-339">Beispiel-PowerShell-Skript</span><span class="sxs-lookup"><span data-stu-id="5d254-339">Example PowerShell Script</span></span>

<span data-ttu-id="5d254-p158">Nachfolgend finden Sie ein PowerShell-Skript, das ausgeführt werden kann, um festzustellen, ob Aktionen, die Sie für die aktualisierten Daten durchführen müssen, sind. Dieses Skript überprüft die Versionsnummer für die Office 365 weltweit Instanz Endpunkte. Wenn eine Änderung vorliegt, heruntergeladen die Endpunkte und Filter für die Kategorie Endpunkte "Zulassen" und "Optimieren". Außerdem verwendet eine eindeutige ClientRequestId mehrere Aufrufe und speichert die neueste Version in eine temporäre Datei gefunden wurde. Sie sollten dieses Skript einmal pro Stunde aufrufen, um zu prüfen, ob ein Version-Update.</span><span class="sxs-lookup"><span data-stu-id="5d254-p158">Here is a PowerShell script that you can run to see if there are actions you need to take for updated data. This script checks the version number for the Office 365 Worldwide instance endpoints. When there is a change, it downloads the endpoints and filters for the "Allow" and "Optimize" category endpoints. It also uses a unique ClientRequestId across multiple calls and saves the latest version found in a temporary file. You should call this script once an hour to check for a version update.</span></span>
  
```
# webservice root URL
$ws = "https://endpoints.office.com"
# path where client ID and latest version number will be stored
$datapath = $Env:TEMP + "\endpoints_clientid_latestversion.txt"
# fetch client ID and version if data file exists; otherwise create new file
if (Test-Path $datapath) {
    $content = Get-Content $datapath
    $clientRequestId = $content[0]
    $lastVersion = $content[1]
}
else {
    $clientRequestId = [GUID]::NewGuid().Guid
    $lastVersion = "0000000000"
    @($clientRequestId, $lastVersion) | Out-File $datapath
}
# call version method to check the latest version, and pull new data if version number is different
$version = Invoke-RestMethod -Uri ($ws + "/version/Worldwide?clientRequestId=" + $clientRequestId)
if ($version.latest -gt $lastVersion) {
    Write-Host "New version of Office 365 worldwide commercial service instance endpoints detected"
    
    # write the new version number to the data file
    @($clientRequestId, $version.latest) | Out-File $datapath
    # invoke endpoints method to get the new data
    $endpointSets = Invoke-RestMethod -Uri ($ws + "/endpoints/Worldwide?clientRequestId=" + $clientRequestId)
    # filter results for Allow and Optimize endpoints, and transform these into custom objects with port and category
    $flatUrls = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $urls = $(if ($endpointSet.urls.Count -gt 0) { $endpointSet.urls } else { @() })
        $urlCustomObjects = @()
        if ($endpointSet.category -in ("Allow", "Optimize")) {
            $urlCustomObjects = $urls | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    url      = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $urlCustomObjects
    }
    $flatIps = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $ips = $(if ($endpointSet.ips.Count -gt 0) { $endpointSet.ips } else { @() })
        # IPv4 strings have dots while IPv6 strings have colons
        $ip4s = $ips | Where-Object { $_ -like '*.*' }
        
        $ipCustomObjects = @()
        if ($endpointSet.category -in ("Allow", "Optimize")) {
            $ipCustomObjects = $ip4s | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    ip = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $ipCustomObjects
    }
    Write-Output "IPv4 Firewall IP Address Ranges"
    ($flatIps.ip | Sort-Object -Unique) -join "," | Out-String
    Write-Output "URLs for Proxy Server"
    ($flatUrls.url | Sort-Object -Unique) -join "," | Out-String
    # TODO Call Send-MailMessage with new endpoints data
}
else {
    Write-Host "Office 365 worldwide commercial service instance endpoints are up-to-date"
}
```

### <a name="example-python-script"></a><span data-ttu-id="5d254-345">Beispielskript Python</span><span class="sxs-lookup"><span data-stu-id="5d254-345">Example Python Script</span></span>

<span data-ttu-id="5d254-p159">Hier ist ein Python-Skript, mit Python 3.6.3 erhält folgende auf Windows 10, die Sie ausführen können, um festzustellen, ob es Aktionen, die Sie für die aktualisierten Daten durchführen müssen sind, getestet. Dieses Skript überprüft die Versionsnummer für die Office 365 weltweit Instanz Endpunkte. Wenn eine Änderung vorliegt, heruntergeladen die Endpunkte und Filter für die Kategorie Endpunkte "Zulassen" und "Optimieren". Außerdem verwendet eine eindeutige ClientRequestId mehrere Aufrufe und speichert die neueste Version in eine temporäre Datei gefunden wurde. Sie sollten dieses Skript einmal pro Stunde aufrufen, um zu prüfen, ob ein Version-Update.</span><span class="sxs-lookup"><span data-stu-id="5d254-p159">Here is a Python script, tested with Python 3.6.3 on Windows 10, that you can run to see if there are actions you need to take for updated data. This script checks the version number for the Office 365 Worldwide instance endpoints. When there is a change, it downloads the endpoints and filters for the "Allow" and "Optimize" category endpoints. It also uses a unique ClientRequestId across multiple calls and saves the latest version found in a temporary file. You should call this script once an hour to check for a version update.</span></span>
  
```
import json
import os
import urllib.request
import uuid
# helper to call the webservice and parse the response
def webApiGet(methodName, instanceName, clientRequestId):
    ws = "https://endpoints.office.com"
    requestPath = ws + '/' + methodName + '/' + instanceName + '?clientRequestId=' + clientRequestId
    request = urllib.request.Request(requestPath)
    with urllib.request.urlopen(request) as response:
        return json.loads(response.read().decode())
# path where client ID and latest version number will be stored
datapath = os.environ['TEMP'] + '\endpoints_clientid_latestversion.txt'
# fetch client ID and version if data exists; otherwise create new file
if os.path.exists(datapath):
    with open(datapath, 'r') as fin:
        clientRequestId = fin.readline().strip()
        latestVersion = fin.readline().strip()
else:
    clientRequestId = str(uuid.uuid4())
    latestVersion = '0000000000'
    with open(datapath, 'w') as fout:
        fout.write(clientRequestId + '\n' + latestVersion)
# call version method to check the latest version, and pull new data if version number is different
version = webApiGet('version', 'Worldwide', clientRequestId)
if version['latest'] > latestVersion:
    print('New version of Office 365 worldwide commercial service instance endpoints detected')
    # write the new version number to the data file
    with open(datapath, 'w') as fout:
        fout.write(clientRequestId + '\n' + version['latest'])
    # invoke endpoints method to get the new data
    endpointSets = webApiGet('endpoints', 'Worldwide', clientRequestId)
    # filter results for Allow and Optimize endpoints, and transform these into tuples with port and category
    flatUrls = []
    for endpointSet in endpointSets:
        if endpointSet['category'] in ('Optimize', 'Allow'):
            category = endpointSet['category']
            urls = endpointSet['urls'] if 'urls' in endpointSet else []
            tcpPorts = endpointSet['tcpPorts'] if 'tcpPorts' in endpointSet else ''
            udpPorts = endpointSet['udpPorts'] if 'udpPorts' in endpointSet else ''
            flatUrls.extend([(category, url, tcpPorts, udpPorts) for url in urls])
    flatIps = []
    for endpointSet in endpointSets:
        if endpointSet['category'] in ('Optimize', 'Allow'):
            ips = endpointSet['ips'] if 'ips' in endpointSet else []
            category = endpointSet['category']
            # IPv4 strings have dots while IPv6 strings have colons
            ip4s = [ip for ip in ips if '.' in ip]
            tcpPorts = endpointSet['tcpPorts'] if 'tcpPorts' in endpointSet else ''
            udpPorts = endpointSet['udpPorts'] if 'udpPorts' in endpointSet else ''
            flatIps.extend([(category, ip, tcpPorts, udpPorts) for ip in ip4s])
    print('IPv4 Firewall IP Address Ranges')
    print(','.join(sorted(set([ip for (category, ip, tcpPorts, udpPorts) in flatIps]))))
    print('URLs for Proxy Server')
    print(','.join(sorted(set([url for (category, url, tcpPorts, udpPorts) in flatUrls]))))
    
    # TODO send mail (e.g. with smtplib/email modules) with new endpoints data
else:
    print('Office 365 worldwide commercial service instance endpoints are up-to-date')
```

### <a name="web-service-interface-versioning"></a><span data-ttu-id="5d254-351">Versionsverwaltung für Web Service-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5d254-351">Web Service interface versioning</span></span>

<span data-ttu-id="5d254-p160">Updates für die Parameter oder Ergebnisse für diese Webdienstmethoden möglicherweise in Zukunft erforderlich. Nachdem die allgemeine Verfügbarkeit Version von Webdiensten veröffentlicht wurde, wird Microsoft angemessener Weise voraus Material Aktualisierungen an den Webdienst zu stellen. Wenn Microsoft davon ausgeht, dass ein Update Änderungen an Clients mithilfe des Webdiensts erforderlich ist, wird Microsoft die vorherige Version (wieder eine Version) des mindestens zwölf (12) Monate nach der Veröffentlichung der neuen Version verfügbaren Webdiensts beibehalten. Kunden, die nicht während dieser Zeit aktualisieren möglicherweise nicht auf den Webdienst und die zugehörigen Methoden zugreifen. Kunden müssen sicherstellen, dass Clients des Webdiensts weiterhin fehlerfrei arbeiten, wenn die folgenden Änderungen an der Web Service-Schnittstelle Signatur vorgenommen werden:</span><span class="sxs-lookup"><span data-stu-id="5d254-p160">Updates to the parameters or results for these web service methods may be required in the future. After the general availability version of these web services is published, Microsoft will make reasonable efforts to provide advance notice of material updates to the web service. When Microsoft believes that an update will require changes to clients using the web service, Microsoft will keep the previous version (one version back) of the web service available for at least twelve (12) months after the release of the new version. Customers who do not upgrade during that time may be unable to access the web service and its methods. Customers must ensure that clients of the web service continue working without error if the following changes are made to the web service interface signature:</span></span>
  
- <span data-ttu-id="5d254-357">Hinzufügen eines neuen optionalen Parameters an eine vorhandene Webmethode, die keinen von ältere Clients bereitgestellt werden und nicht das Ergebnis beeinflussen empfängt eine ältere Client.</span><span class="sxs-lookup"><span data-stu-id="5d254-357">Adding a new optional parameter to an existing web method that doesn't have to be provided by older clients and doesn't impact the result an older client receives.</span></span>
    
- <span data-ttu-id="5d254-358">Hinzufügen eines benannten Attributs in einem der Antwort REST Elemente oder zusätzliche Spalten für die CSV-Antwort.</span><span class="sxs-lookup"><span data-stu-id="5d254-358">Adding a new named attribute in one of the response REST items or additional columns to the response CSV.</span></span>
    
- <span data-ttu-id="5d254-359">Hinzufügen einer neuen Webmethode mit einem neuen Namen, die nicht durch die ältere Clients aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="5d254-359">Adding a new web method with a new name that is not called by the older clients.</span></span>
    
## <a name="faq"></a><span data-ttu-id="5d254-360">Häufig gestellte Fragen</span><span class="sxs-lookup"><span data-stu-id="5d254-360">FAQ</span></span>

<span data-ttu-id="5d254-361">Administrator häufig gestellte Fragen zu Konnektivität:</span><span class="sxs-lookup"><span data-stu-id="5d254-361">Frequently-asked administrator questions about connectivity:</span></span>
  
### <a name="how-do-i-submit-a-question"></a><span data-ttu-id="5d254-362">Wie übermittle ich eine Frage?</span><span class="sxs-lookup"><span data-stu-id="5d254-362">How do I submit a question?</span></span>

<span data-ttu-id="5d254-p161">Klicken Sie auf den Link unten, um anzugeben, ob der Artikel hilfreich war und übermitteln Sie weiteren Fragen zu. Wir das Feedback überwachen und mit der am häufigsten gestellten Fragen Hier aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="5d254-p161">Click the link at the bottom to indicate if the article was helpful or not and submit any additional questions. We monitor the feedback and update the questions here with the most frequently asked.</span></span>
  
### <a name="when-is-the-xml-file-updated"></a><span data-ttu-id="5d254-365">Wann wird die XML-Datei aktualisiert?</span><span class="sxs-lookup"><span data-stu-id="5d254-365">When is the XML file updated?</span></span>

<span data-ttu-id="5d254-p162">Wenn neue Endpunkte angekündigt sind, besteht in der Regel ein Tag 30 + Puffer bevor sie effektive sind und Netzwerk-Anfragen Wechsel zu diesen zu beginnen. Dieser Puffer wird sichergestellt, dass Kunden und Partnern haben die Möglichkeit, ihre Systeme zu aktualisieren. FQDN und IP-Präfix Ergänzungen und entfernungen werden in der XML-Datei zur selben Zeit als die Ansage, was bedeutet, dass ein neuer FQDN 30 Tage vor der Verwendung in der XML-Datei sein wird verarbeitet. Da wir Senden von Netzwerkanfragen an Endpunkten, die wir entfernen möchten beenden, bevor Sie ihre Löschung Ankündigung, wenn wir den Endpunkt aus der XML-Code zur selben Zeit als die Ansage entfernen wird noch nicht verwendet.</span><span class="sxs-lookup"><span data-stu-id="5d254-p162">When new endpoints are announced, there is usually a 30+ day buffer before they are effective and network requests begin going to them. This buffer is to ensure customers and partners have an opportunity to update their systems. FQDN and IP prefix additions and removals are processed in the XML file at the same time as the announcement, meaning a new FQDN will be in the XML file 30 days before use. Since we stop sending network requests to endpoints we're removing prior to announcing their removal, when we remove the endpoint from the XML at the same time as the announcement it is already unused.</span></span>
  
### <a name="how-can-i-be-notified-of-changes"></a><span data-ttu-id="5d254-370">Wie kann ich Änderungen werden benachrichtigt?</span><span class="sxs-lookup"><span data-stu-id="5d254-370">How can I be notified of changes?</span></span>
<span data-ttu-id="5d254-371"><a name="bkmk_changes"> </a></span><span class="sxs-lookup"><span data-stu-id="5d254-371"></span></span>

<span data-ttu-id="5d254-p163">Office 365-Endpunkten werden am Ende des jeden Monat mit 30 Tage veröffentlicht. Gelegentlich treten Änderungen mehr als einmal pro Monat oder mit der Zeiträume, die Benachrichtigung. Wenn ein Endpunkt hinzugefügt wird, wird das aktuelle Datum in den [RSS-feed](https://go.microsoft.com/fwlink/p/?linkid=236301) aufgeführten das Datum nach dem Netzwerk-Anfragen an den Endpunkt gesendet werden. Wenn Sie neue RSS-sind, wird hier wie [über Outlook abonnieren](https://go.microsoft.com/fwlink/p/?LinkId=532416) , oder Sie [haben den RSS-feed per e-Mail an Sie Updates](https://go.microsoft.com/fwlink/p/?LinkId=532417)können.</span><span class="sxs-lookup"><span data-stu-id="5d254-p163">Office 365 endpoints are published at the end of each month with 30 days notice. Occasionally changes will occur more than once a month or with shorter notice periods. When an endpoint is added, the effective date listed in the [RSS feed](https://go.microsoft.com/fwlink/p/?linkid=236301) is the date after which network requests will be sent to the endpoint. If you're new to RSS, here is how to [subscribe via Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) or you can [have the RSS feed updates emailed to you](https://go.microsoft.com/fwlink/p/?LinkId=532417).</span></span>
  
### <a name="how-do-i-read-the-rss-change-log"></a><span data-ttu-id="5d254-376">Wie Lese ich, dass die RSS Protokoll ändern?</span><span class="sxs-lookup"><span data-stu-id="5d254-376">How do I read the RSS change log?</span></span>
<span data-ttu-id="5d254-377"><a name="bkmk_changes"> </a></span><span class="sxs-lookup"><span data-stu-id="5d254-377"></span></span>

<span data-ttu-id="5d254-p164">Nachdem Sie den RSS-feed abonnieren, Sie können analysieren, die Informationen selbst oder mit einem Skript. Die folgende Tabelle beschreibt das Format des RSS-Feed o erleichtern.</span><span class="sxs-lookup"><span data-stu-id="5d254-p164">After you subscribe to the RSS feed, you can parse the information yourself or with a script. The following table describes the format of the RSS feed o make it easier.</span></span>
  
|<span data-ttu-id="5d254-380">**Abschnitt**</span><span class="sxs-lookup"><span data-stu-id="5d254-380">**Section**</span></span>|<span data-ttu-id="5d254-381">**Teil 1**</span><span class="sxs-lookup"><span data-stu-id="5d254-381">**Part 1**</span></span>|<span data-ttu-id="5d254-382">**Teil 2**</span><span class="sxs-lookup"><span data-stu-id="5d254-382">**Part 2**</span></span>|<span data-ttu-id="5d254-383">**Teil 3**</span><span class="sxs-lookup"><span data-stu-id="5d254-383">**Part 3**</span></span>|<span data-ttu-id="5d254-384">**Teil 4**</span><span class="sxs-lookup"><span data-stu-id="5d254-384">**Part 4**</span></span>|<span data-ttu-id="5d254-385">**Teil 5**</span><span class="sxs-lookup"><span data-stu-id="5d254-385">**Part 5**</span></span>|<span data-ttu-id="5d254-386">**Teil 6**</span><span class="sxs-lookup"><span data-stu-id="5d254-386">**Part 6**</span></span>|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="5d254-387">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="5d254-387">**Description**</span></span> <br/> |<span data-ttu-id="5d254-388">Anzahl</span><span class="sxs-lookup"><span data-stu-id="5d254-388">Count</span></span>  <br/> |<span data-ttu-id="5d254-389">Datum nach dem Sie Netzwerk-Anfragen an den Endpunkt gesendet werden erwarten können.</span><span class="sxs-lookup"><span data-stu-id="5d254-389">Date after which you can expect network requests to be sent to the endpoint.</span></span>  <br/> |<span data-ttu-id="5d254-390">Grundlegende Beschreibung des Features oder Diensts, die den Endpunkt erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="5d254-390">Basic description of the feature or service that requires the endpoint.</span></span>  <br/> |<span data-ttu-id="5d254-391">Können Sie mit diesem Endpunkt auf eine Verbindung ExpressRoute neben dem Internet verbinden?</span><span class="sxs-lookup"><span data-stu-id="5d254-391">Can you connect to this endpoint on an ExpressRoute Circuit in addition to the internet?</span></span>  <br/> |<span data-ttu-id="5d254-392">**Ja** – Sie können eine Verbindung mit diesem Endpunkt im Internet und die ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="5d254-392">**Yes** - you can connect to this endpoint on both the internet and ExpressRoute.</span></span>  <br/> <span data-ttu-id="5d254-393">**Nein** – Sie können nur an diesen Endpunkt im Internet verbinden.</span><span class="sxs-lookup"><span data-stu-id="5d254-393">**No** - you can only connect to this endpoint on the internet.</span></span>  <br/> |<span data-ttu-id="5d254-394">Das Ziel-FQDN oder die IP-Bereich hinzugefügt oder entfernt wird.</span><span class="sxs-lookup"><span data-stu-id="5d254-394">The destination FQDN or IP range being added or removed.</span></span>  <br/> |
|<span data-ttu-id="5d254-395">**Beispiel**</span><span class="sxs-lookup"><span data-stu-id="5d254-395">**Example**</span></span> <br/> |<span data-ttu-id="5d254-396">1 /</span><span class="sxs-lookup"><span data-stu-id="5d254-396">1/</span></span>  <br/> |<span data-ttu-id="5d254-397">[Effektiven Xx/Xx/Xxx.</span><span class="sxs-lookup"><span data-stu-id="5d254-397">[Effective xx/xx/xxx.</span></span>  <br/> |<span data-ttu-id="5d254-398">Erforderlich: \<Beschreibung\>.</span><span class="sxs-lookup"><span data-stu-id="5d254-398">Required: \<description\>.</span></span>  <br/> |<span data-ttu-id="5d254-399">ExpressRoute:</span><span class="sxs-lookup"><span data-stu-id="5d254-399">ExpressRoute:</span></span>  <br/> |<span data-ttu-id="5d254-400">\<Ja/Nein\>.</span><span class="sxs-lookup"><span data-stu-id="5d254-400">\<Yes/No\>.</span></span>  <br/> |<span data-ttu-id="5d254-401">\<FQDN und IP-Adresse\>],</span><span class="sxs-lookup"><span data-stu-id="5d254-401">\<FQDN/IP\>],</span></span>  <br/> |
   
<span data-ttu-id="5d254-402">Einige andere Features, beachten Sie, dass jeder Eintrag einen gemeinsamen Satz von Trennzeichen verfügt:</span><span class="sxs-lookup"><span data-stu-id="5d254-402">A couple other things to note, every entry has a common set of delimiters:</span></span>
  
- <span data-ttu-id="5d254-403">**/**-nach der Anzahl der</span><span class="sxs-lookup"><span data-stu-id="5d254-403">**/** - after the count</span></span> 
    
- <span data-ttu-id="5d254-404">**[** - den Eintrag für die Anzahl an</span><span class="sxs-lookup"><span data-stu-id="5d254-404">**[** - to indicate the entry for the count</span></span> 
    
- <span data-ttu-id="5d254-p165">**.** -zwischen jedem distinct Abschnitt des Eintrags verwendet</span><span class="sxs-lookup"><span data-stu-id="5d254-p165">**.** - used in between each distinct section of the entry</span></span> 
    
- <span data-ttu-id="5d254-407">**],** – an das Ende einer einzelnen Eintrag anzuzeigen</span><span class="sxs-lookup"><span data-stu-id="5d254-407">**],** - to indicate the end of a single entry</span></span> 
    
- <span data-ttu-id="5d254-p166">**].** -An das Ende des alle Einträge</span><span class="sxs-lookup"><span data-stu-id="5d254-p166">**].** - To indicate the end of all the entries</span></span> 
    
### <a name="how-do-i-determine-the-location-of-my-tenant"></a><span data-ttu-id="5d254-410">Ermitteln den Speicherort der meine Mandanten</span><span class="sxs-lookup"><span data-stu-id="5d254-410">How do I determine the location of my tenant?</span></span>

 <span data-ttu-id="5d254-411">**Mandanten Speicherort** ist am besten mit unserem [Datacenter zuordnen](https://o365datacentermap.azurewebsites.net/)bestimmt.</span><span class="sxs-lookup"><span data-stu-id="5d254-411">**Tenant location** is best determined using our [datacenter map](https://o365datacentermap.azurewebsites.net/).</span></span>
  
### <a name="am-i-peering-appropriately-with-microsoft"></a><span data-ttu-id="5d254-412">Verwende ich entsprechend mit Microsoft peering?</span><span class="sxs-lookup"><span data-stu-id="5d254-412">Am I peering appropriately with Microsoft?</span></span>

 <span data-ttu-id="5d254-413">**Peering Speicherorte** werden in [peering mit Microsoft](https://www.microsoft.com/peering)ausführlicher beschrieben.</span><span class="sxs-lookup"><span data-stu-id="5d254-413">**Peering locations** are described in more detail in [peering with Microsoft](https://www.microsoft.com/peering).</span></span>
  
<span data-ttu-id="5d254-p167">Mit über 2500 Internetdienstanbieter Peers Beziehungen sollte Global und 70 Points of Presence, aus dem Netzwerk für unsere erste nahtlos. Es kann nicht lohnt, sich ein paar Minuten und stellen Sie sicher, dass bei Ihrem Internetdienstanbieter Peers Beziehung ist die am besten geeignete [Nachfolgend finden Sie einige Beispiele für](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__) des guten und nicht so gut Peers Hand und Nachteile auf Ihr Netzwerk.</span><span class="sxs-lookup"><span data-stu-id="5d254-p167">With over 2500 ISP peering relationships globally and 70 points of presence, getting from your network to ours should be seamless. It can't hurt to spend a few minutes making sure your ISP's peering relationship is the most optimal, [here's a few examples](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__) of good and not so good peering hand-offs to our network.</span></span> 
  
### <a name="how-do-i-determine-which-ip-addresses-to-accept-over-expressroute"></a><span data-ttu-id="5d254-416">Ermitteln der IP-Adressen über ExpressRoute akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="5d254-416">How do I determine which IP addresses to accept over ExpressRoute?</span></span>

 <span data-ttu-id="5d254-417">**Routen ExpressRoute akzeptiert** werden durch [Microsoft IP-Adressbereiche](https://www.microsoft.com/download/details.aspx?id=53602) und der bestimmten Office 365 [BGP Communitys](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099)definiert.</span><span class="sxs-lookup"><span data-stu-id="5d254-417">**Accepted ExpressRoute routes** are defined by [Microsoft's IP ranges](https://www.microsoft.com/download/details.aspx?id=53602) and the specific Office 365 [BGP communities](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099).</span></span>
  
### <a name="how-do-i-determine-which-endpoints-i-need"></a><span data-ttu-id="5d254-418">Welche Endpunkte ermitteln ich muss?</span><span class="sxs-lookup"><span data-stu-id="5d254-418">How do I determine which endpoints I need?</span></span>

<span data-ttu-id="5d254-p168">Wir hinzufügen regelmäßig neue Features und Dienste auf die Office 365-Suite, erweitern die Konnektivität Querformat. Wenn Sie die E3 oder E5 SKU abonniert haben, ist die einfache Art, bedenken sollten die Liste der Endpunkte, die Sie alle von ihnen vollständigen Funktionalität für die Suite zu erhalten. Wenn Sie eine dieser SKUs abonniert werden nicht ist der Unterschied im Hinblick auf die Anzahl der Endpunkte minimal.</span><span class="sxs-lookup"><span data-stu-id="5d254-p168">We regularly add new features and services to the Office 365 suite, expanding the connectivity landscape. If you're subscribed to the E3 or E5 SKU, the simple way to think about the list of endpoints is that you need all of them to get full functionality for the suite. If you aren't subscribed to either of these SKUs the difference is minimal in terms of the number of endpoints.</span></span>
  
<span data-ttu-id="5d254-422">Lesen Sie [Office 365 Network Connectivity Prinzipien](office-365-network-connectivity-principles.md) erhalten weitere Informationen zu Office 365 Endpunkt Kategorien und die Konnektivität Prinzipien für die sichere Verwaltung von Office 365-Datenverkehr und erste die bestmögliche Leistung zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="5d254-422">Read [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md) to get more information on Office 365 endpoint categories, and to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance.</span></span> 
  
<span data-ttu-id="5d254-p169">In der folgenden Abbildung sehen Sie ein Beispiel für einen Teil der FQDN-Tabelle im Abschnitt Office Online. Die Zeilen werden nach Features und Unterschiede in Connectivity organisiert. Geben Sie die ersten beiden Zeilen an Office Online nutzt die Endpunkte markiert in die Office 365-Authentifizierung und Identität und Portal erforderlich und einem freigegebenen Abschnitte. Dies ist normalerweise für einen Dienst in Office 365 auf diesen gemeinsamen Diensten verlassen. Gibt die dritte Zeile an Clientcomputer muss erreichen \*. officeapps.live.com Office Online und der vierten Zeile mit gibt Computer muss auch erreichen \*. cdn.office.net zum Verwenden von Office Online.</span><span class="sxs-lookup"><span data-stu-id="5d254-p169">In the image below, you can see an example from a portion of the FQDN table in the Office Online section. The rows are organized by feature and differences in connectivity. The first two rows indicate Office Online relies on the endpoints marked Required in the Office 365 Authentication and Identity and portal and shared sections. This is typical for a service within Office 365 to rely on these shared services. The third row indicates client computers must be able to reach \*.officeapps.live.com to use Office Online and the fourth row indicates computers must also be able to reach \*.cdn.office.net to use Office Online.</span></span>
  
<span data-ttu-id="5d254-428">Obwohl beide drei Zeile und vier erforderlich sind, um Office Online verwenden, haben sie getrennt wurde, um darauf hinzuweisen, dass das Ziel unterscheidet:</span><span class="sxs-lookup"><span data-stu-id="5d254-428">Even though both row three and four are required to use Office Online, they've been separated to indicate the destination is different:</span></span>
  
1. <span data-ttu-id="5d254-429">\*. officeapps.live.com kein CDN darstellt, Bedeutung Anforderungen an diesem Namespace gehen direkt an einem Microsoft-Rechenzentrum.</span><span class="sxs-lookup"><span data-stu-id="5d254-429">\*.officeapps.live.com does not represent a CDN, meaning requests to this namespace will go directly to a Microsoft datacenter.</span></span>
    
2. <span data-ttu-id="5d254-430">\*. officeapps.live.com ExpressRoute Circuits mit Microsoft Peering erreichbar ist.</span><span class="sxs-lookup"><span data-stu-id="5d254-430">\*.officeapps.live.com is accessible on ExpressRoute circuits using Microsoft Peering.</span></span>
    
3. <span data-ttu-id="5d254-431">Office Online zugeordneten IP-Adressen und \*. officeapps.live.com können anhand dieser Link gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="5d254-431">The IP addresses associated with Office Online and \*.officeapps.live.com can be found by following this link.</span></span>
    
4. <span data-ttu-id="5d254-432">\*. cdn.office.net stellt ein CDN von Akamai gehostet werden, gehen Bedeutung Anforderungen an diesem Namespace an einem Akamai-Rechenzentrum.</span><span class="sxs-lookup"><span data-stu-id="5d254-432">\*.cdn.office.net represents a CDN hosted by Akamai, meaning requests to this namespace will go to an Akamai datacenter.</span></span>
    
5. <span data-ttu-id="5d254-433">\*. cdn.office.net kann nicht auf ExpressRoute Circuits zugegriffen werden.</span><span class="sxs-lookup"><span data-stu-id="5d254-433">\*.cdn.office.net is not accessible on ExpressRoute circuits.</span></span>
    
6. <span data-ttu-id="5d254-434">Office Online zugeordneten IP-Adressen und \*. cdn.office.net sind nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="5d254-434">The IP addresses associated with Office Online and \*.cdn.office.net are not available.</span></span>
    
![Screenshot der Seite Endpunkte](media/42b487f3-24f3-48fe-9885-f97aae3194f3.png)
  
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a><span data-ttu-id="5d254-436">Benötige ich Netzwerk Anforderungen an IP-Adressen nicht in der veröffentlichten Liste anzeigen, ich für den Zugriff auf diese?</span><span class="sxs-lookup"><span data-stu-id="5d254-436">I see network requests to IP addresses not on the published list, do I need to provide access to them?</span></span>
<span data-ttu-id="5d254-437"><a name="bkmk_MissingIP"> </a></span><span class="sxs-lookup"><span data-stu-id="5d254-437"></span></span>

<span data-ttu-id="5d254-p170">Wir stellen nur IP-Adressen für die Office 365-Servern, die Sie direkt über das Internet oder ExpressRoute weitergeleitet werden. Dies ist nicht für eine umfassende Liste aller IP-Adressen für die Netzwerk-Anfragen angezeigt werden. Sie sehen die Netzwerk-Anforderungen an Microsoft und Drittanbieter-Besitzer, nicht aufgehoben, IP-Adressen. Diese IP-Adressen sind dynamisch generierte oder auf eine Weise, die kurzer Hinweis verhindert, dass bei einer Änderung verwaltet. Wenn die Firewall Access basierend auf die FQDNs für diese Netzwerk-Anfragen zulassen ist nicht möglich, verwenden Sie eine PAC oder WPAD-Datei, um die Anforderungen zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="5d254-p170">We only provide IP addresses for the Office 365 servers you should route directly to over the Internet or ExpressRoute. This isn't a comprehensive list of all IP addresses you'll see network requests for. You'll see network requests to Microsoft and third-party owned, unpublished, IP addresses. These IP addresses are dynamically generated or managed in a way that prevents timely notice when they change. If your firewall can't allow access based on the FQDNs for these network requests, use a PAC or WPAD file to manage the requests.</span></span>
  
<span data-ttu-id="5d254-443">Sehen Sie, dass Office 365 eine IP-Adresse zugeordnet, die Sie auf Weitere Informationen wünschen?</span><span class="sxs-lookup"><span data-stu-id="5d254-443">See an IP associated with Office 365 that you want more information on?</span></span>
  
1. <span data-ttu-id="5d254-444">Überprüfen Sie, ob die IP-Adresse in einem größeren veröffentlichte Bereich mit einem [CIDR-Rechner](http://jodies.de/ipcalc)mit enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="5d254-444">Check if the IP address is included in a larger published range using a [CIDR calculator](http://jodies.de/ipcalc).</span></span>
    
2. <span data-ttu-id="5d254-p171">Sehen Sie, wenn ein Partner die IP-Adresse mit einer [Whois-Abfrage](https://dnsquery.org/)besitzt. Wenn es sich um Microsoft gehören ist, kann es eine interne Partner sein.</span><span class="sxs-lookup"><span data-stu-id="5d254-p171">See if a partner owns the IP with a [whois query](https://dnsquery.org/). If it's Microsoft owned, it may be an internal partner.</span></span>
    
3. <span data-ttu-id="5d254-p172">Überprüfen Sie das Zertifikat, und in einem Browser eine Verbindung mit der IP-Adresse mit *HTTPS://\<IP-Adresse\> * , überprüfen Sie die Domänen aufgeführtes Dokument das Zertifikat zu verstehen, welche Domänen die IP-Adresse zugeordnet sind. Wenn sie eine Microsoft gehören IP-Adresse und nicht in der Liste der Office 365-IP-Adressen, wahrscheinlich die IP-Adresse ist ist ein Microsoft CDN wie *MSOCDN.NET* oder einer anderen Microsoft-Domäne ohne veröffentlichten IP-Informationen zugeordnet. Wenn Sie, dass die Domäne des Zertifikats eine ist, auf dem Forderung wir so Listen Sie die IP-Adresse finden, informieren Sie uns.</span><span class="sxs-lookup"><span data-stu-id="5d254-p172">Check the certificate, in a browser connect to the IP address using  *HTTPS://\<IP_ADDRESS\>*  , check the domains listed on the certificate to understand what domains are associated with the IP address. If it's a Microsoft owned IP address and not on the list of Office 365 IP addresses, it's likely the IP address is associated with a Microsoft CDN such as  *MSOCDN.NET*  or another Microsoft domain without published IP information. If you do find the domain on the certificate is one where we claim to list the IP address, please let us know.</span></span> 
    
### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a><span data-ttu-id="5d254-450">Warum werden Namen wie nsatc.net oder akadns.net in die Microsoft-Domänennamen angezeigt?</span><span class="sxs-lookup"><span data-stu-id="5d254-450">Why do I see names such as nsatc.net or akadns.net in the Microsoft domain names?</span></span>
<span data-ttu-id="5d254-451"><a name="bkmk_akamai"> </a></span><span class="sxs-lookup"><span data-stu-id="5d254-451"></span></span>

<span data-ttu-id="5d254-p173">Office 365 und andere Microsoft-Dienste verwenden Sie mehrere Drittanbieter-Diensten wie etwa Akamai und MarkMonitor um Ihr Office 365 zu verbessern. Erteilen Sie die beste Erfahrung beibehalten, um möglich ist, diese Dienste in der Zukunft zu ändern. Auf diese Weise, veröffentlichen Sie häufig über den CNAME-Eintrag, die auf einer dritten Besitzer der Domäne, einen Datensatz oder IP-Adresse verweist. Drittanbieter-Domänen können Inhalte wie ein CDN hosten oder hosten sie möglicherweise einen Dienst wie eine geografische Datenverkehr-Verwaltungsdienst. Wenn Sie Verbindungen mit dritte angezeigt wird, sind sie in der Form eine Umleitung oder Weiterleitung, keine anfängliche Anforderung vom Client. Einige Kunden benötigen, um sicherzustellen, dass diese Art der Weiterleitung und Umleitung übergeben, ohne explizit hinzufügen, mit denen die lange Liste von potenziellen FQDNs Dienste von Drittanbietern möglicherweise zulässig ist.</span><span class="sxs-lookup"><span data-stu-id="5d254-p173">Office 365 and other Microsoft services use several third-party services such as Akamai and MarkMonitor to improve your Office 365 experience. To keep giving you the best experience possible, we may change these services in the future. In doing so, we often publish the CNAME record which points to a third party owned domain, A record, or IP address. Third party domains may host content, such as a CDN, or they may host a service, such as a geographical traffic management service. When you see connections to these third parties, they're in the form of a redirect or referral, not an initial request from the client. Some customers need to ensure this form of referral and redirection is allowed to pass without explicitly adding the long list of potential FQDNs third party services may use.</span></span>
  
<span data-ttu-id="5d254-p174">Die Liste der Dienste unterliegt jederzeit ändern. Die Dienste derzeit unter anderem:</span><span class="sxs-lookup"><span data-stu-id="5d254-p174">The list of services is subject to change at any time. Some of the services currently in use include:</span></span>
  
<span data-ttu-id="5d254-p175">[MarkMonitor](https://www.markmonitor.com/) in Gebrauch Anfragen angezeigt, die enthalten \* \*. nsatc.net\* . Dieser Dienst bietet Domain Namensschutz und Überwachung zum Schutz vor böswilligen Verhalten.</span><span class="sxs-lookup"><span data-stu-id="5d254-p175">[MarkMonitor](https://www.markmonitor.com/) is in use when you see requests that include  *\*.nsatc.net*  . This service provides domain name protection and monitoring to protect against malicious behavior.</span></span> 
  
<span data-ttu-id="5d254-p176">[ExactTarget](https://www.marketingcloud.com/) in Gebrauch finden Sie unter Anforderungen an \* \*. exacttarget.com\* . Dieser Dienst bietet e-Mail-Link Management und Überwachung vor böswilligen Verhalten.</span><span class="sxs-lookup"><span data-stu-id="5d254-p176">[ExactTarget](https://www.marketingcloud.com/) is in use when you see requests to  *\*.exacttarget.com*  . This service provides email link management and monitoring against malicious behavior.</span></span> 
  
<span data-ttu-id="5d254-p177">[Akamai](https://www.akamai.com/) wird verwendet, wenn Anforderungen angezeigt wird, die einen der folgenden FQDNs enthalten. Dieser Dienst bietet Geo-DNS und Content Delivery Network Services.</span><span class="sxs-lookup"><span data-stu-id="5d254-p177">[Akamai](https://www.akamai.com/) is in use when you see requests that include one of the following FQDNs. This service offers geo-DNS and content delivery network services.</span></span> 
  
```
*.akadns.net
*.akam.net
*.akamai.com
*.akamai.net
*.akamaiedge.net
*.akamaihd.net
*.akamaized.net
*.edgekey.net
*.edgesuite.net

```

### <a name="what-are-the-three-types-of-office-365-endpoints"></a><span data-ttu-id="5d254-466">Was sind die drei Typen von Office 365-Endpunkten?</span><span class="sxs-lookup"><span data-stu-id="5d254-466">What are the three types of Office 365 endpoints?</span></span>
<span data-ttu-id="5d254-467"><a name="bkmk_akamai"> </a></span><span class="sxs-lookup"><span data-stu-id="5d254-467"></span></span>

- <span data-ttu-id="5d254-p178">Sie Verbinden mit Drittanbieter-Dienste aus, um grundlegende Internetdienste wie DNS-Lookups und Abruf von Inhalten CDN abrufen. Sie verbinden sich auch mit Drittanbieter-Dienste für Integrationen wie Integrieren von YouTube-Videos in OneNote-Notizbüchern.</span><span class="sxs-lookup"><span data-stu-id="5d254-p178">You connect to third-party services to retrieve basic internet services such as DNS lookups and CDN content retrieval. You also connect to third-party services for integrations such as incorporating YouTube videos in your OneNote notebooks.</span></span>
    
- <span data-ttu-id="5d254-p179">Sie Verbinden mit sekundären Services gehostet und Ausführen von Microsoft wie edgeknoten, mit die Ihre Anforderung Netzwerk Microsofts globale Netzwerk am nächsten Internetspeicherort auf Ihrem Computer eingeben können. Als dritte größten Netzwerk weltweit wird dies Ihre Erfahrung Konnektivität verbessert. Sie verbinden sich auch mit Microsoft Azure-Diensten wie etwa Azure Media-Dienste die verwendet werden, von einer Vielzahl von Office 365-Dienste.</span><span class="sxs-lookup"><span data-stu-id="5d254-p179">You connect to secondary services hosted and run by Microsoft such as edge nodes that enable your network request to enter Microsoft's global network at the closest internet location to your computer. As the third largest network on the planet, this improves your connectivity experience. You also connect to Microsoft Azure services such as Azure Media Services which are used by a variety of Office 365 services.</span></span>
    
- <span data-ttu-id="5d254-p180">Sie Verbinden mit den primären Office 365-Diensten wie etwa die Exchange Online Postfachserver oder die Skype für Online Business Server, auf dem Ihre eindeutigen und proprietären Daten befinden. Herstellen einer Verbindung mit den primären Office 365-Diensten FQDN oder die IP-Adresse und Internet- oder ExpressRoute Circuits verwenden können. Sie können nur mit der dritten und sekundären Services mithilfe von FQDNs auf eine Internet-Verbindung verbinden.</span><span class="sxs-lookup"><span data-stu-id="5d254-p180">You connect to primary Office 365 services such as the Exchange Online mailbox server or the Skype for Business Online server where your unique and proprietary data lives. You can connect to the primary Office 365 services by FQDN or IP address and use internet or ExpressRoute circuits. You can only connect to the third party and secondary services using FQDNs on an internet circuit.</span></span>
    
<span data-ttu-id="5d254-p181">Das folgende Diagramm zeigt die Unterschiede zwischen diesen Dienst Bereichen. In diesem Diagramm hat das lokalen Kundennetzwerk in der unteren linken Ecke mehrere Netzwerkgeräte bei der Verwaltung von Netzwerkkonnektivität. Konfigurationen wie diese werden für Unternehmenskunden. Wenn Ihr Netzwerk verfügt nur über eine Firewall zwischen den Clientcomputern und dem Internet, das ebenfalls unterstützt wird, und Sie sollten sicherstellen, dass Ihre Firewall FQDNs und Platzhalter in der Liste zulassen-Regeln unterstützen kann.</span><span class="sxs-lookup"><span data-stu-id="5d254-p181">The following diagram shows the differences between these service areas. In this diagram, the customer on-premises network in the lower left has multiple network devices to assist in managing network connectivity. Configurations like this one are common for enterprise customers. If your network only has a firewall between your client computers and the internet, that's supported as well, and you'll want to ensure your firewall can support FQDNs and wildcards in the allow list rules.</span></span>
  
<span data-ttu-id="5d254-480">Lesen Sie [Office 365 Network Connectivity Prinzipien](office-365-network-connectivity-principles.md) erhalten weitere Informationen zu Office 365 Endpunkt Kategorien und die Konnektivität Prinzipien für die sichere Verwaltung von Office 365-Datenverkehr und erste die bestmögliche Leistung zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="5d254-480">Read [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md) to get more information on Office 365 endpoint categories, and to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance.</span></span> 
  
![Zeigt die drei verschiedenen Typen von Netzwerkendpunkte bei Verwendung von Office 365](media/6582bcfa-11ba-4ac2-9b69-14bef0437670.png)
  
### <a name="i-cant-or-dont-want-to-use-any-third-party-service"></a><span data-ttu-id="5d254-482">Ich kann nicht oder keine Dienste von Drittanbietern verwenden möchten</span><span class="sxs-lookup"><span data-stu-id="5d254-482">I can't or don't want to use any third-party service</span></span>
<span data-ttu-id="5d254-483"><a name="bkmk_thirdparty"> </a></span><span class="sxs-lookup"><span data-stu-id="5d254-483"></span></span>

<span data-ttu-id="5d254-p182">Office 365 ist eine Suite-Funktion über das Internet integrierten Dienste, Zuverlässigkeit und Verfügbarkeit Versprechen basieren auf viele standard Internetdienste zur Verfügung stehen. Standardmäßige Internetdienste wie DNS, CRL und CDNs muss beispielsweise erreichbar zu Office 365 verwenden, wie sie mit den meisten modernen Internetdienste erreichbar sein müssen.</span><span class="sxs-lookup"><span data-stu-id="5d254-p182">Office 365 is a suite of services built to function over the internet, the reliability and availability promises are based on many standard internet services being available. For example, standard internet services such as DNS, CRL, and CDNs must be reachable to use Office 365 just as they must be reachable to use most modern internet services.</span></span>
  
<span data-ttu-id="5d254-p183">Zusätzlich zu diesen grundlegenden Internetdienste sind Drittanbieter-Dienste, die nur verwendet werden, um Funktionalität zu integrieren. Beispielsweise kann die Giphy.com innerhalb von Microsoft-Teams mit Kunden nahtlos in Teams GIF-Dateien enthalten. In ähnlicher Weise werden YouTube und Flickr Drittanbieter-Dienste, die verwendet werden, um nahtlos Video und Bildern in Office-Clients aus dem Internet zu integrieren. Während dies für die Integration erforderlich sind, sind sie in der Office 365-Endpunkten Artikel als optional markiert bedeutet, dass die Basisfunktionalität des Diensts weiterhin ausgeführt werden, wenn der Endpunkt nicht zugänglich ist.</span><span class="sxs-lookup"><span data-stu-id="5d254-p183">In addition to these basic internet services, there are third-party services that are only used to integrate functionality. For example, using Giphy.com within Microsoft Teams allows customers to seamlessly include Gifs within Teams. Similarly, YouTube and Flickr are third-party services that are used to seamlessly integrate video and images into Office clients from the internet. While these are needed for integration, they're marked as optional in the Office 365 endpoints article which means core functionality of the service will continue to function if the endpoint isn't accessible.</span></span>
  
<span data-ttu-id="5d254-490">Wenn Sie versuchen, Office 365 verwendet und tätiges, dass die Dienste von Drittanbietern nicht zugänglich sind sollten Sie um [sicherzustellen, dass alle FQDNs gekennzeichnet, erforderlich oder optional in diesem Artikel über die Proxy und Firewall zulässig sind](urls-and-ip-address-ranges.md).</span><span class="sxs-lookup"><span data-stu-id="5d254-490">If you're attempting to use Office 365 and are finding third party services aren't accessible you'll want to [ensure all FQDNs marked required or optional in this article are allowed through the proxy and firewall](urls-and-ip-address-ranges.md).</span></span>
  
### <a name="i-cant-or-dont-want-to-use-any-secondary-services"></a><span data-ttu-id="5d254-491">Ich kann nicht oder keine sekundären Dienste verwenden möchten</span><span class="sxs-lookup"><span data-stu-id="5d254-491">I can't or don't want to use any secondary services</span></span>
<span data-ttu-id="5d254-492"><a name="bkmk_secondary"> </a></span><span class="sxs-lookup"><span data-stu-id="5d254-492"></span></span>

<span data-ttu-id="5d254-p184">Sekundäre Dienste sind Microsoft-Dienste, die in Office 365-Steuerelement fallen nicht. Dies sind die Elemente wie die edgenetzwerk sowie die Azure Media-Dienste und Azure Content Delivery Networks. Dies sind alle erforderlichen Office 365 verwendet und erreichbar sein müssen.</span><span class="sxs-lookup"><span data-stu-id="5d254-p184">Secondary services are Microsoft services that don't fall within Office 365 control. These are things like the edge network, Azure Media Services, and Azure Content Delivery Networks. These are all required to use Office 365 and must be reachable.</span></span>
  
<span data-ttu-id="5d254-496">Wenn Sie versuchen, Office 365 verwendet und tätiges, dass die Dienste von Drittanbietern nicht zugänglich sind sollten Sie um [sicherzustellen, dass alle FQDNs gekennzeichnet, erforderlich oder optional in diesem Artikel über die Proxy und Firewall zulässig sind](urls-and-ip-address-ranges.md).</span><span class="sxs-lookup"><span data-stu-id="5d254-496">If you're attempting to use Office 365 and are finding third party services aren't accessible you'll want to [ensure all FQDNs marked required or optional in this article are allowed through the proxy and firewall](urls-and-ip-address-ranges.md).</span></span>
  
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a><span data-ttu-id="5d254-497">Wie blockieren Sie Zugriff auf Microsoft Consumer-Dienste</span><span class="sxs-lookup"><span data-stu-id="5d254-497">How do I block access to Microsoft's consumer services?</span></span>
<span data-ttu-id="5d254-498"><a name="bkmk_consumer"> </a></span><span class="sxs-lookup"><span data-stu-id="5d254-498"></span></span>

<span data-ttu-id="5d254-p185">Einschränken des Zugriffs auf unsere Consumer-Dienste auf eigenes Risiko durchgeführt werden sollte, nur zuverlässiger Block Consumer Services zum Einschränken des Zugriffs auf die *login.live.com* FQDN. Dieser FQDN wird durch eine Breite Palette von Leistungspaket nicht Consumer-Diensten wie etwa MSDN und TechNet verwendet. Einschränken des Zugriffs auf diesen FQDN kann dazu führen, dass der Notwendigkeit Ausnahmen für die Regel zum Netzwerkanfragen mit diesen Diensten auch eingeschlossen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="5d254-p185">Restricting access to our consumer services should be done at your own risk, the only reliable way to block consumer services is to restrict access to the  *login.live.com*  FQDN. This FQDN is used by a broad set of services including non-consumer services such as MSDN, TechNet, and others. Restricting access to this FQDN may result in the need to also include exceptions to the rule for network requests associated with these services.</span></span> 
  
<span data-ttu-id="5d254-502">Beachten Sie, dass Blockieren des Zugriffs auf die Microsoft Consumer Services allein die Möglichkeit für eine Person in Ihrem Netzwerk zu Exfiltrate Informationen über Office 365-Mandanten oder anderen Dienst zu verhindern, dass werden nicht beibehalten.</span><span class="sxs-lookup"><span data-stu-id="5d254-502">Keep in mind that blocking access to the Microsoft consumer services alone won't prevent the ability for someone on your network to exfiltrate information using an Office 365 tenant or other service.</span></span>
  
## <a name="related-topics"></a><span data-ttu-id="5d254-503">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="5d254-503">Related Topics</span></span>

[<span data-ttu-id="5d254-504">Microsoft Azure-Rechenzentrum IP-Adressbereiche</span><span class="sxs-lookup"><span data-stu-id="5d254-504">Microsoft Azure Datacenter IP Ranges</span></span>](https://www.microsoft.com/download/details.aspx?id=41653)
  
[<span data-ttu-id="5d254-505">Microsoft öffentliche IP-Speicherplatz</span><span class="sxs-lookup"><span data-stu-id="5d254-505">Microsoft Public IP Space</span></span>](https://www.microsoft.com/download/details.aspx?id=53602)
  
[<span data-ttu-id="5d254-506">Anforderungen an die Netzwerkinfrastruktur für Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="5d254-506">Network infrastructure requirements for Microsoft Intune</span></span>](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[<span data-ttu-id="5d254-507">Power BI und ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="5d254-507">Power BI and ExpressRoute</span></span>](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[<span data-ttu-id="5d254-508">URLs und IP-Adressbereiche von Office 365</span><span class="sxs-lookup"><span data-stu-id="5d254-508">Office 365 URLs and IP address ranges</span></span>](urls-and-ip-address-ranges.md)
  
[<span data-ttu-id="5d254-509">Verwalten von ExpressRoute für Office 365-Diensten</span><span class="sxs-lookup"><span data-stu-id="5d254-509">Managing ExpressRoute for Office 365 connectivity</span></span>](managing-expressroute-for-connectivity.md)
  
[<span data-ttu-id="5d254-510">Office 365 Network Connectivity Prinzipien</span><span class="sxs-lookup"><span data-stu-id="5d254-510">Office 365 Network Connectivity Principles</span></span>](office-365-network-connectivity-principles.md)
  

