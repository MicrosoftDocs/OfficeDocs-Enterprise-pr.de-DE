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
ms.openlocfilehash: 42613b45b8395c3f81064bbc2171866bc922a657
ms.sourcegitcommit: ca4d3ec34300d7d39f1a42dc6f29a34915de5c87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/05/2018
ms.locfileid: "23831920"
---
# <a name="managing-office-365-endpoints"></a>Verwalten von Office 365-Endpunkten

## <a name="office-365-network-connectivity"></a>Office 365-Netzwerkkonnektivität

 Verbindungen mit Office 365 bestehen große Menge, vertrauenswürdigen Netzwerk-Anforderungen, die am besten ausführen, wenn sie über eine geringer Latenz Ausgang gemacht sind, die in der Nähe der Benutzer ist. Einige Office 365-Verbindungen profitieren von der die Verbindung zu optimieren. 
  
1. Sicherstellen die Firewall Listen können für eine Verbindung zu Office 365-Endpunkten zulassen.
    
2. Verwenden Sie Ihre Proxy-Infrastruktur, um Internetkonnektivität für Platzhalter und unveröffentlichte Ziele zu erlauben.
    
3. Verwalten Sie eine optimale Umkreisnetzwerkkonfiguration.
    
4. [Sicherstellen, dass Sie die bestmögliche Konnektivität optimal nutzen](https://aka.ms/o365perfprinciples).
    
5. Lesen Sie [Office 365 Network Connectivity Prinzipien](office-365-network-connectivity-principles.md) , um die Konnektivität Prinzipien für die sichere Verwaltung von Office 365-Datenverkehr und erste die bestmögliche Leistung zu verstehen. 
    
![Herstellen einer Verbindung mit Office 365, durch Firewalls und Proxys.](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)
  
## <a name="update-your-firewalls-outbound-allow-lists"></a>Update die Firewall des ausgehenden Listen zulassen

Sie können Ihr Netzwerk optimieren, indem alle vertrauenswürdigen Netzwerk-Anforderungen für Office 365 direkt über die Firewall senden, und alle zusätzlichen Ebene Paketinspektion umgehen oder in Bearbeitung. Dies reduziert langsam von Wartezeit sowie Ihrer kapazitätsanforderungen Umkreisnetzwerk. Am einfachsten auswählen, welche Netzwerk fordert als vertrauenswürdig ist unsere vordefinierte PAC Dateien auf der Registerkarte **Proxies** oben verwenden. 
  
Wenn Ihre Firewall ausgehenden Datenverkehr blockiert, Sie alle IP-sicherzustellen möchten und FQDNs als **erforderlich** , in der [XML-Datei](https://go.microsoft.com/fwlink/?LinkId=533185) aufgelistet sind in der Zulassungsliste enthalten. Erkennen Sie, dass alle Dienste erfordern die Verwendung von einige 3. Party-Dienste. Wir nicht IP-Adressen für diese 3. Partei-Diensten wie etwa Zertifikat Anbietern von Content Delivery Networks DNS-Anbieter bereitgestellt und so weiter. Für vollständige Funktionalität von Office 365 müssen Sie möglicherweise alle vom Office 365 angefordert werden, unabhängig davon wie viele Informationen wir veröffentlichen das Ziel Ziele zu erreichen. 
  
Viele Ziele müssen keine IP-Adresse veröffentlicht oder als Platzhalterdomäne mit keine bestimmten vollqualifizierten Domänennamen aufgeführt sind, verwenden Sie diese Funktionalität müssen Sie auflösen diese Netzwerk-Anfragen an die aktuelle IP-Adresse angefordert wird und Senden der Netzwerk-Anforderung über das Internet.
  
Automatisieren des Upgradevorgangs mithilfe einer Firewalls, die analysiert die XML-Datei in Ihrem Auftrag und aktualisiert die Regeln automatisch basierend auf dem Dienste oder Features, dass Sie direkt über die Firewall weiterleiten möchten. Sie können auch das Tool [Azure Bereich](https://azurerange.azurewebsites.net/) verwenden, das von der Community erstellt wurde und analysiert den XML-Code für Sie mit den Exportoptionen für die Konfiguration der Cisco XE Route oder ACL-Liste, nur-Text oder CSV. 
  
Eine ausführlicheren Erläuterung der Ziele Netzwerk ist auf unserer [Website Verweis](urls-and-ip-address-ranges.md) sowie über unseren [RSS-basierte Änderungsprotokoll](https://go.microsoft.com/fwlink/p/?linkid=236301) verfügbar, sodass Sie Änderungen abonnieren können. 
  
<a name="pacfiles"> </a>
## <a name="configure-outbound-paths-with-pac-files"></a>Konfigurieren Sie ausgehende Pfade mit PAC-Dateien

Verwenden Sie PAC oder WPAD-Dateien zum Verwalten von Netzwerk-Anfragen, die mit Office 365 zugeordnet sind, jedoch nicht über ein IP-Adresse verfügen. Typische Netzwerk-Anforderungen, die über ein Proxy oder zum Umkreisnetzwerk-Gerät gesendet werden, ein zusätzlichen Latenz entstehen. Während Proxyauthentifizierung der größten Tax anfallen, können andere Dienste wie Reputation-Suche und versucht, Pakete prüfen benutzerfreundlich verursachen. Darüber hinaus benötigen diese Perimeter Network Geräte genügend Kapazität, um alle Netzwerkanfragen zu verarbeiten. Es wird empfohlen, die Proxy oder Prüfung Infrastruktur für die direkte Anforderungen von Office 365-Netzwerk zu umgehen.
  
Verwenden Sie eines der unsere PAC-Dateien als Ausgangspunkt, um zu bestimmen, welche den Netzwerkverkehr zu einem Proxy gesendet werden, und das an eine Firewall gesendet werden. Wenn Sie PAC oder WPAD Dateien, lesen diesen Beitrag zur [Bereitstellung von PAC-Dateien](https://blogs.technet.microsoft.com/undocumentedfeatures/2016/04/06/deploying-the-office-365-proxy-pac-to-manage-your-users/) von einem unsere Berater für Office 365 nicht vertraut sind. Sie sollten diese als Ausgangspunkt überprüfen und bearbeiten, um entsprechend Ihrer Umgebung. 
  
 **PAC-Dateien 7/10/2018 aktualisiert**. 
  
### <a name="1---pac-file-separates-required-internet-fqdns-from-known-office-365-fqdn"></a>#1 - PAC-Datei: trennt Internet FQDNs von bekannten Office 365-FQDN erforderlich.

Im erste Beispiel wird eine Demonstration der unsere empfohlene Vorgehensweise bei der Verwaltung von Endpunkten über das Internet nur. Umgeht den Proxy für Office 365-Ziele geleitet, wo die IP-Adresse wird veröffentlicht und sendet verbleibenden Netzwerk Anforderungen an den Proxy.
  
Codeausschnitt:

```javascript
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

### <a name="2---pac-file-connect-to-office-365-over-the-internet-and-expressroute"></a>#2 – PAC-Datei: Verbinden mit Office 365 über das Internet und ExpressRoute
<a name="bkmk_inet-aer"> </a>

Im zweite Beispiel wird eine Demonstration der unsere empfohlene Vorgehensweise zum Verwalten von Verbindungen, wenn Circuits ExpressRoute und im Internet verfügbar sind. Sendet ExpressRoute angekündigt Ziele der Netzfrequenz ExpressRoute und Internet nur Ziele an den Proxy angekündigt.
  
Codeausschnitt:

```javascript
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

### <a name="3---pac-file-manage-all-office-365-destinations-collectively"></a>#3 – PAC-Datei: alle Office 365 Ziele gemeinsam verwalten
<a name="bkmk_inet-direct"> </a>

Im dritte Beispiel veranschaulicht zusenden alle Netzwerk mit Office 365, ein einziges Ziel zugeordnet ist. Dies wird häufig verwendet, um alle Prüfung der Anforderungen für Office 365-Netzwerk zu umgehen und bietet, dass Sie ein Format, in dem alle Endpunkte veröffentlichten, Liste im Format PAC für Ihre Anpassung verwendet werden.
  
Codeausschnitt:

```javascript
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

### <a name="use-custom-scripts-or-manually-create-your-own-pac-files"></a>Verwenden Sie benutzerdefinierte Skripts oder manuell erstellen Sie eigener PAC-Dateien
<a name="pacfiles_manual"> </a>

Wenn Sie bereits erstellt haben etwas Sie verlassen freigeben möchten eine Notiz in den Kommentaren Nachfolgend einige weitere Tools aus der Community. None oder von Microsoft verwaltet und zu diesem Zweck hier bereitgestellten der Community, Tools verwiesen, die in diesem Artikel offiziell werden, unterstützt.
  
- Dies ist das älteste Community generierte Tool zur Verwaltung den Prozess, ein Tool von einem Mitglied der Office 365-Community erstellt. Es folgt Link zum [herunterladen](https://gallery.technet.microsoft.com/Office-365-Proxy-Pac-60fb28f7).
    
- Machbarkeitsstudie mit exportierbar Firewallregeln: [Microsoft Cloud IP-API](https://mscloudips.azurewebsites.net/).
    
- IT-Praktyk: [RSS-Konvertierung](https://gallery.technet.microsoft.com/Convert-the-RSS-channel-5efe18b7) und [XML-Konvertierung](https://gallery.technet.microsoft.com/Convert-the-O365IPAddresses-9890d896).
    
- Von Peter Abele: [herunterladen](https://gallery.technet.microsoft.com/How-to-create-an-up-to-b1fc33f3).
    
- Verwenden Sie die Netzwerkanalyse um zu bestimmen, welches Netzwerk fordert sollte der Proxy-Infrastruktur zu umgehen. Die am häufigsten verwendeten FQDNs verwendet, um Kunden Proxys umgehen, aufgrund der Lautstärke des Netzwerkdatenverkehrs gesendet und Empfangen von diesen Endpunkten sind.
    
  ```
  outlook.office365.com
  outlook.office.com
  <tenant-name>.sharepoint.com
  <tenant-name>-my.sharepoint.com
  <tenant-name>-<app>.sharepoint.com
  *.Lync.com
  ```

- Stellen Sie sicher, dass alle Netzwerk-Anforderungen, die direkt an die Firewall gesendet einen entsprechenden Eintrag in der Firewall Liste, um die Anforderung durchlaufen ermöglichen zulassen verfügen.

## <a name="perimeter-network-integration"></a>Umkreisnetzwerk Netzwerkintegration
<a name="BKMK_Perimeter"> </a>

Wussten Sie schon Microsofts WAN ist eine der in der ganzen Welt der größten Backbones?
  
Es ist true, dieses umfassende Netzwerk ist Office 365 und unsere anderen unabhängig von Ihrem Speicherort in der ganzen Welt arbeiten, die Sie Clouddiensten macht. Unser Netzwerk besteht aus hoher Bandbreite, Latenz, Failover-fähigen Links mit Tausenden von Route Meilen privat Besitzer dunkel Fiber und Multi-TBit-Verbindungen zwischen Rechenzentren und Edge-Knoten alle zu erleichtern, unsere Clouddienste zu verwenden.
  
Mit einem Netzwerk wie folgt möchten Sie die Geräte Ihrer Organisation so bald wie möglich mit unserem Netzwerk verbinden. Mit über 2500 Internetdienstanbieter Peers Beziehungen sollte Global und 70 Points of Presence, aus dem Netzwerk für unsere erste nahtlos. Es kann nicht lohnt, sich ein paar Minuten und stellen Sie sicher, dass bei Ihrem Internetdienstanbieter Peers Beziehung ist die am besten geeignete [Nachfolgend finden Sie einige Beispiele für](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__) des guten und nicht so gut Peers Hand und Nachteile auf Ihr Netzwerk. 
  
Sie können manuell oder automatisch die Geräte in Ihrem Netzwerk zum Verarbeiten von Office 365 Anwendung Netzwerk Anforderungen je nach Ihrer Geräte optimal konfigurieren. Welche Änderungen bei der Konfiguration Sie Office 365 Netzwerkdatenverkehr optimal behandeln müssen, hängt von Ihrer Umgebung. Office 365 Netzwerk Anforderungen von Netzwerkkonfigurationen bietet Vorteile, die Folgendes ermöglichen:
  
- Priorität über weniger wichtige den Netzwerkdatenverkehr.
    
- Weiterleitung an einen lokalen Ausgang zur Vermeidung von Backhauling über eine langsame WAN Link beim Nutzen der Vorteile von der verfügbaren Latenz im Microsoft-Netzwerk. [Hier ist eine gute Beschreibung](https://blogs.technet.microsoft.com/onthewire/2017/05/03/office-365-connectivity-guidance-part-2/) basierend auf Kundenprojekte. 
    
- Bei Verwendung des DNS in der Nähe einer lokalen Ausgang um sicherzustellen, dass die Netzwerk-Anforderung, die bewirkt, die lokalen Ausgang dass eingeht am nächstgelegenen Microsoft Speicherort Peers.
    
- Ausschluss von Tiefe Paketinspektion oder anderen intensive Netzwerkpakete verarbeitet, um die Wartezeit bei vertikaler Skalierung erfüllen.
    
Moderne Netzwerkgeräte enthalten Funktionen zum Verwalten von Netzwerk-Anforderungen für vertrauenswürdige Anwendungen wie etwa Office 365 anders als generischen, nicht vertrauenswürdigen Internet-Datenverkehr. Mit der neuen Querformat SD-WAN-Lösungen kann eine solche Differenzierung Datenverkehr und Pfad Auswahl auch mit der veränderbaren Zustand des Netzwerks, wie etwa Punkt in Zeiten, Latenz oder Leistung der verschiedenen Connectivity Pfade Aufklärung durchgeführt werden zwischen dem Benutzer und der Cloud.
  
Weitere Anleitungen zum Planen der Netzwerkkonfiguration finden Sie unter [Netzwerk- und Migration für Office 365 planen](network-and-migration-planning.md), [Behandlung von Leistungsproblemen Plan für Office 365](performance-troubleshooting-plan.md)und [Prüfliste für die bereitstellungsplanung für Office 365](deployment-planning-checklist.md) . 
  
### <a name="to-implement-this-scenario"></a>Zum Implementieren dieses Szenarios:

Wenden Sie sich Ihr Netzwerk Lösung oder Dienstanbieter Wenn Sie Office 365-URL können und IP-Definitionen von XML in lokalen (für den Benutzer), geringe Kosten zu vereinfachen Netzwerk Ausgang für Office 365-Datenverkehr, dessen Priorität relativ zu anderen Applikationen verwalten und Anpassen der Der Netzwerkpfad für Office 365-Verbindungen in Microsoft-Netzwerk je nach netzwerkbedingungen ändern. Einige Lösungen herunterladen und Automatisierung von Office 365-URL und IP-XMLs Definition in ihren Stapeln.
  
Stellen Sie unbedingt sicher, dass die implementierte Lösung erforderlichen Maß an Flexibilität, entsprechende Geo-Redundanz der Netzwerkpfad für Office 365-Datenverkehr und Änderungen an Office 365-URLs und IP-Adressen ausgelegt ist, wie sie veröffentlicht werden.

## <a name="faq"></a>Häufig gestellte Fragen

Administrator häufig gestellte Fragen zu Konnektivität:
  
### <a name="how-do-i-submit-a-question"></a>Wie übermittle ich eine Frage?

Klicken Sie auf den Link unten, um anzugeben, ob der Artikel hilfreich war und übermitteln Sie weiteren Fragen zu. Wir das Feedback überwachen und mit der am häufigsten gestellten Fragen Hier aktualisieren.
  
### <a name="when-is-the-xml-file-updated"></a>Wann wird die XML-Datei aktualisiert?

Wenn neue Endpunkte angekündigt sind, besteht in der Regel ein Tag 30 + Puffer bevor sie effektive sind und Netzwerk-Anfragen Wechsel zu diesen zu beginnen. Dieser Puffer wird sichergestellt, dass Kunden und Partnern haben die Möglichkeit, ihre Systeme zu aktualisieren. FQDN und IP-Präfix Ergänzungen und entfernungen werden in der XML-Datei zur selben Zeit als die Ansage, was bedeutet, dass ein neuer FQDN 30 Tage vor der Verwendung in der XML-Datei sein wird verarbeitet. Da wir Senden von Netzwerkanfragen an Endpunkten, die wir entfernen möchten beenden, bevor Sie ihre Löschung Ankündigung, wenn wir den Endpunkt aus der XML-Code zur selben Zeit als die Ansage entfernen wird noch nicht verwendet.
  
### <a name="how-can-i-be-notified-of-changes"></a>Wie kann ich Änderungen werden benachrichtigt?
<a name="bkmk_changes"> </a>

Office 365-Endpunkten werden am Ende des jeden Monat mit 30 Tage veröffentlicht. Gelegentlich treten Änderungen mehr als einmal pro Monat oder mit der Zeiträume, die Benachrichtigung. Wenn ein Endpunkt hinzugefügt wird, wird das aktuelle Datum in den [RSS-feed](https://go.microsoft.com/fwlink/p/?linkid=236301) aufgeführten das Datum nach dem Netzwerk-Anfragen an den Endpunkt gesendet werden. Wenn Sie neue RSS-sind, wird hier wie [über Outlook abonnieren](https://go.microsoft.com/fwlink/p/?LinkId=532416) , oder Sie [haben den RSS-feed per e-Mail an Sie Updates](https://go.microsoft.com/fwlink/p/?LinkId=532417)können.
  
### <a name="how-do-i-read-the-rss-change-log"></a>Wie Lese ich, dass die RSS Protokoll ändern?
<a name="bkmk_changes"> </a>

Nachdem Sie den RSS-feed abonnieren, Sie können analysieren, die Informationen selbst oder mit einem Skript. Die folgende Tabelle beschreibt das Format des RSS-Feed o erleichtern.
  
|**Abschnitt**|**Teil 1**|**Teil 2**|**Teil 3**|**Teil 4**|**Teil 5**|**Teil 6**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|**Beschreibung** <br/> |Anzahl  <br/> |Datum nach dem Sie Netzwerk-Anfragen an den Endpunkt gesendet werden erwarten können.  <br/> |Grundlegende Beschreibung des Features oder Diensts, die den Endpunkt erforderlich sind.  <br/> |Können Sie mit diesem Endpunkt auf eine Verbindung ExpressRoute neben dem Internet verbinden?  <br/> |**Ja** – Sie können eine Verbindung mit diesem Endpunkt im Internet und die ExpressRoute.  <br/> **Nein** – Sie können nur an diesen Endpunkt im Internet verbinden.  <br/> |Das Ziel-FQDN oder die IP-Bereich hinzugefügt oder entfernt wird.  <br/> |
|**Beispiel** <br/> |1 /  <br/> |[Effektiven Xx/Xx/Xxx.  <br/> |Erforderlich: \<Beschreibung\>.  <br/> |ExpressRoute:  <br/> |\<Ja/Nein\>.  <br/> |\<FQDN und IP-Adresse\>],  <br/> |

Einige andere Features, beachten Sie, dass jeder Eintrag einen gemeinsamen Satz von Trennzeichen verfügt:
  
- **/**-nach der Anzahl der
- **[** - den Eintrag für die Anzahl an
- **.** -zwischen jedem distinct Abschnitt des Eintrags verwendet
- **],** – an das Ende einer einzelnen Eintrag anzuzeigen
- **].** -An das Ende des alle Einträge

### <a name="how-do-i-determine-the-location-of-my-tenant"></a>Ermitteln den Speicherort der meine Mandanten

 **Mandanten Speicherort** ist am besten mit unserem [Datacenter zuordnen](https://o365datacentermap.azurewebsites.net/)bestimmt.
  
### <a name="am-i-peering-appropriately-with-microsoft"></a>Verwende ich entsprechend mit Microsoft peering?

 **Peering Speicherorte** werden in [peering mit Microsoft](https://www.microsoft.com/peering)ausführlicher beschrieben.
  
Mit über 2500 Internetdienstanbieter Peers Beziehungen sollte Global und 70 Points of Presence, aus dem Netzwerk für unsere erste nahtlos. Es kann nicht lohnt, sich ein paar Minuten und stellen Sie sicher, dass bei Ihrem Internetdienstanbieter Peers Beziehung ist die am besten geeignete [Nachfolgend finden Sie einige Beispiele für](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__) des guten und nicht so gut Peers Hand und Nachteile auf Ihr Netzwerk. 
  
### <a name="how-do-i-determine-which-ip-addresses-to-accept-over-expressroute"></a>Ermitteln der IP-Adressen über ExpressRoute akzeptieren?

 **Routen ExpressRoute akzeptiert** werden durch [Microsoft IP-Adressbereiche](https://www.microsoft.com/download/details.aspx?id=53602) und der bestimmten Office 365 [BGP Communitys](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099)definiert.
  
### <a name="how-do-i-determine-which-endpoints-i-need"></a>Welche Endpunkte ermitteln ich muss?

Wir hinzufügen regelmäßig neue Features und Dienste auf die Office 365-Suite, erweitern die Konnektivität Querformat. Wenn Sie die E3 oder E5 SKU abonniert haben, ist die einfache Art, bedenken sollten die Liste der Endpunkte, die Sie alle von ihnen vollständigen Funktionalität für die Suite zu erhalten. Wenn Sie eine dieser SKUs abonniert werden nicht ist der Unterschied im Hinblick auf die Anzahl der Endpunkte minimal.
  
Lesen Sie [Office 365 Network Connectivity Prinzipien](office-365-network-connectivity-principles.md) erhalten weitere Informationen zu Office 365 Endpunkt Kategorien und die Konnektivität Prinzipien für die sichere Verwaltung von Office 365-Datenverkehr und erste die bestmögliche Leistung zu verstehen. 
  
In der folgenden Abbildung sehen Sie ein Beispiel für einen Teil der FQDN-Tabelle im Abschnitt Office Online. Die Zeilen werden nach Features und Unterschiede in Connectivity organisiert. Geben Sie die ersten beiden Zeilen an Office Online nutzt die Endpunkte markiert in die Office 365-Authentifizierung und Identität und Portal erforderlich und einem freigegebenen Abschnitte. Dies ist normalerweise für einen Dienst in Office 365 auf diesen gemeinsamen Diensten verlassen. Gibt die dritte Zeile an Clientcomputer muss erreichen \*. officeapps.live.com Office Online und der vierten Zeile mit gibt Computer muss auch erreichen \*. cdn.office.net zum Verwenden von Office Online.
  
Obwohl beide drei Zeile und vier erforderlich sind, um Office Online verwenden, haben sie getrennt wurde, um darauf hinzuweisen, dass das Ziel unterscheidet:
  
1. \*. officeapps.live.com kein CDN darstellt, Bedeutung Anforderungen an diesem Namespace gehen direkt an einem Microsoft-Rechenzentrum.
2. \*. officeapps.live.com ExpressRoute Circuits mit Microsoft Peering erreichbar ist.
3. Office Online zugeordneten IP-Adressen und \*. officeapps.live.com können anhand dieser Link gefunden werden.
4. \*. cdn.office.net stellt ein CDN von Akamai gehostet werden, gehen Bedeutung Anforderungen an diesem Namespace an einem Akamai-Rechenzentrum.
5. \*. cdn.office.net kann nicht auf ExpressRoute Circuits zugegriffen werden.
6. Office Online zugeordneten IP-Adressen und \*. cdn.office.net sind nicht verfügbar.

![Screenshot der Seite Endpunkte](media/42b487f3-24f3-48fe-9885-f97aae3194f3.png)
  
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a>Benötige ich Netzwerk Anforderungen an IP-Adressen nicht in der veröffentlichten Liste anzeigen, ich für den Zugriff auf diese?
<a name="bkmk_MissingIP"> </a>

Wir stellen nur IP-Adressen für die Office 365-Servern, die Sie direkt über das Internet oder ExpressRoute weitergeleitet werden. Dies ist nicht für eine umfassende Liste aller IP-Adressen für die Netzwerk-Anfragen angezeigt werden. Sie sehen die Netzwerk-Anforderungen an Microsoft und Drittanbieter-Besitzer, nicht aufgehoben, IP-Adressen. Diese IP-Adressen sind dynamisch generierte oder auf eine Weise, die kurzer Hinweis verhindert, dass bei einer Änderung verwaltet. Wenn die Firewall Access basierend auf die FQDNs für diese Netzwerk-Anfragen zulassen ist nicht möglich, verwenden Sie eine PAC oder WPAD-Datei, um die Anforderungen zu verwalten.
  
Sehen Sie, dass Office 365 eine IP-Adresse zugeordnet, die Sie auf Weitere Informationen wünschen?
  
1. Überprüfen Sie, ob die IP-Adresse in einem größeren veröffentlichte Bereich mit einem [CIDR-Rechner](http://jodies.de/ipcalc)mit enthalten ist.
2. Sehen Sie, wenn ein Partner die IP-Adresse mit einer [Whois-Abfrage](https://dnsquery.org/)besitzt. Wenn es sich um Microsoft gehören ist, kann es eine interne Partner sein.
3. Überprüfen Sie das Zertifikat, und in einem Browser eine Verbindung mit der IP-Adresse mit *HTTPS://\<IP-Adresse\> * , überprüfen Sie die Domänen aufgeführtes Dokument das Zertifikat zu verstehen, welche Domänen die IP-Adresse zugeordnet sind. Wenn sie eine Microsoft gehören IP-Adresse und nicht in der Liste der Office 365-IP-Adressen, wahrscheinlich die IP-Adresse ist ist ein Microsoft CDN wie *MSOCDN.NET* oder einer anderen Microsoft-Domäne ohne veröffentlichten IP-Informationen zugeordnet. Wenn Sie, dass die Domäne des Zertifikats eine ist, auf dem Forderung wir so Listen Sie die IP-Adresse finden, informieren Sie uns.

### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a>Warum werden Namen wie nsatc.net oder akadns.net in die Microsoft-Domänennamen angezeigt?
<a name="bkmk_akamai"> </a>

Office 365 und andere Microsoft-Dienste verwenden Sie mehrere Drittanbieter-Diensten wie etwa Akamai und MarkMonitor um Ihr Office 365 zu verbessern. Erteilen Sie die beste Erfahrung beibehalten, um möglich ist, diese Dienste in der Zukunft zu ändern. Auf diese Weise, veröffentlichen Sie häufig über den CNAME-Eintrag, die auf einer dritten Besitzer der Domäne, einen Datensatz oder IP-Adresse verweist. Drittanbieter-Domänen können Inhalte wie ein CDN hosten oder hosten sie möglicherweise einen Dienst wie eine geografische Datenverkehr-Verwaltungsdienst. Wenn Sie Verbindungen mit dritte angezeigt wird, sind sie in der Form eine Umleitung oder Weiterleitung, keine anfängliche Anforderung vom Client. Einige Kunden benötigen, um sicherzustellen, dass diese Art der Weiterleitung und Umleitung übergeben, ohne explizit hinzufügen, mit denen die lange Liste von potenziellen FQDNs Dienste von Drittanbietern möglicherweise zulässig ist.
  
Die Liste der Dienste unterliegt jederzeit ändern. Die Dienste derzeit unter anderem:
  
[MarkMonitor](https://www.markmonitor.com/) in Gebrauch Anfragen angezeigt, die enthalten * \*. nsatc.net* . Dieser Dienst bietet Domain Namensschutz und Überwachung zum Schutz vor böswilligen Verhalten.
  
[ExactTarget](https://www.marketingcloud.com/) in Gebrauch finden Sie unter Anforderungen an * \*. exacttarget.com* . Dieser Dienst bietet e-Mail-Link Management und Überwachung vor böswilligen Verhalten.
  
[Akamai](https://www.akamai.com/) wird verwendet, wenn Anforderungen angezeigt wird, die einen der folgenden FQDNs enthalten. Dieser Dienst bietet Geo-DNS und Content Delivery Network Services.
  
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

### <a name="what-are-the-three-types-of-office-365-endpoints"></a>Was sind die drei Typen von Office 365-Endpunkten?
<a name="bkmk_akamai"> </a>

- Sie Verbinden mit Drittanbieter-Dienste aus, um grundlegende Internetdienste wie DNS-Lookups und Abruf von Inhalten CDN abrufen. Sie verbinden sich auch mit Drittanbieter-Dienste für Integrationen wie Integrieren von YouTube-Videos in OneNote-Notizbüchern.
- Sie Verbinden mit sekundären Services gehostet und Ausführen von Microsoft wie edgeknoten, mit die Ihre Anforderung Netzwerk Microsofts globale Netzwerk am nächsten Internetspeicherort auf Ihrem Computer eingeben können. Als dritte größten Netzwerk weltweit wird dies Ihre Erfahrung Konnektivität verbessert. Sie verbinden sich auch mit Microsoft Azure-Diensten wie etwa Azure Media-Dienste die verwendet werden, von einer Vielzahl von Office 365-Dienste.
- Sie Verbinden mit den primären Office 365-Diensten wie etwa die Exchange Online Postfachserver oder die Skype für Online Business Server, auf dem Ihre eindeutigen und proprietären Daten befinden. Herstellen einer Verbindung mit den primären Office 365-Diensten FQDN oder die IP-Adresse und Internet- oder ExpressRoute Circuits verwenden können. Sie können nur mit der dritten und sekundären Services mithilfe von FQDNs auf eine Internet-Verbindung verbinden.

Das folgende Diagramm zeigt die Unterschiede zwischen diesen Dienst Bereichen. In diesem Diagramm hat das lokalen Kundennetzwerk in der unteren linken Ecke mehrere Netzwerkgeräte bei der Verwaltung von Netzwerkkonnektivität. Konfigurationen wie diese werden für Unternehmenskunden. Wenn Ihr Netzwerk verfügt nur über eine Firewall zwischen den Clientcomputern und dem Internet, das ebenfalls unterstützt wird, und Sie sollten sicherstellen, dass Ihre Firewall FQDNs und Platzhalter in der Liste zulassen-Regeln unterstützen kann.
  
Lesen Sie [Office 365 Network Connectivity Prinzipien](office-365-network-connectivity-principles.md) erhalten weitere Informationen zu Office 365 Endpunkt Kategorien und die Konnektivität Prinzipien für die sichere Verwaltung von Office 365-Datenverkehr und erste die bestmögliche Leistung zu verstehen. 
  
![Zeigt die drei verschiedenen Typen von Netzwerkendpunkte bei Verwendung von Office 365](media/6582bcfa-11ba-4ac2-9b69-14bef0437670.png)
  
### <a name="i-cant-or-dont-want-to-use-any-third-party-service"></a>Ich kann nicht oder keine Dienste von Drittanbietern verwenden möchten
<a name="bkmk_thirdparty"> </a>

Office 365 ist eine Suite-Funktion über das Internet integrierten Dienste, Zuverlässigkeit und Verfügbarkeit Versprechen basieren auf viele standard Internetdienste zur Verfügung stehen. Standardmäßige Internetdienste wie DNS, CRL und CDNs muss beispielsweise erreichbar zu Office 365 verwenden, wie sie mit den meisten modernen Internetdienste erreichbar sein müssen.
  
Zusätzlich zu diesen grundlegenden Internetdienste sind Drittanbieter-Dienste, die nur verwendet werden, um Funktionalität zu integrieren. Beispielsweise kann die Giphy.com innerhalb von Microsoft-Teams mit Kunden nahtlos in Teams GIF-Dateien enthalten. In ähnlicher Weise werden YouTube und Flickr Drittanbieter-Dienste, die verwendet werden, um nahtlos Video und Bildern in Office-Clients aus dem Internet zu integrieren. Während dies für die Integration erforderlich sind, sind sie in der Office 365-Endpunkten Artikel als optional markiert bedeutet, dass die Basisfunktionalität des Diensts weiterhin ausgeführt werden, wenn der Endpunkt nicht zugänglich ist.
  
Wenn Sie versuchen, Office 365 verwendet und tätiges, dass die Dienste von Drittanbietern nicht zugänglich sind sollten Sie um [sicherzustellen, dass alle FQDNs gekennzeichnet, erforderlich oder optional in diesem Artikel über die Proxy und Firewall zulässig sind](urls-and-ip-address-ranges.md).
  
### <a name="i-cant-or-dont-want-to-use-any-secondary-services"></a>Ich kann nicht oder keine sekundären Dienste verwenden möchten
<a name="bkmk_secondary"> </a>

Sekundäre Dienste sind Microsoft-Dienste, die in Office 365-Steuerelement fallen nicht. Dies sind die Elemente wie die edgenetzwerk sowie die Azure Media-Dienste und Azure Content Delivery Networks. Dies sind alle erforderlichen Office 365 verwendet und erreichbar sein müssen.
  
Wenn Sie versuchen, Office 365 verwendet und tätiges, dass die Dienste von Drittanbietern nicht zugänglich sind sollten Sie um [sicherzustellen, dass alle FQDNs gekennzeichnet, erforderlich oder optional in diesem Artikel über die Proxy und Firewall zulässig sind](urls-and-ip-address-ranges.md).
  
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a>Wie blockieren Sie Zugriff auf Microsoft Consumer-Dienste
<a name="bkmk_consumer"> </a>

Einschränken des Zugriffs auf unsere Consumer-Dienste auf eigenes Risiko durchgeführt werden sollte, nur zuverlässiger Block Consumer Services zum Einschränken des Zugriffs auf die *login.live.com* FQDN. Dieser FQDN wird durch eine Breite Palette von Leistungspaket nicht Consumer-Diensten wie etwa MSDN und TechNet verwendet. Einschränken des Zugriffs auf diesen FQDN kann dazu führen, dass der Notwendigkeit Ausnahmen für die Regel zum Netzwerkanfragen mit diesen Diensten auch eingeschlossen werden sollen.
  
Beachten Sie, dass Blockieren des Zugriffs auf die Microsoft Consumer Services allein die Möglichkeit für eine Person in Ihrem Netzwerk zu Exfiltrate Informationen über Office 365-Mandanten oder anderen Dienst zu verhindern, dass werden nicht beibehalten.
  
## <a name="related-topics"></a>Verwandte Themen

[Office 365-IP-Adresse und URL-Web service](office-365-ip-web-service.md)

[Microsoft Azure-Rechenzentrum IP-Adressbereiche](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Microsoft öffentliche IP-Speicherplatz](https://www.microsoft.com/download/details.aspx?id=53602)
  
[Anforderungen an die Netzwerkinfrastruktur für Microsoft Intune](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[Power BI und ExpressRoute](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[URLs und IP-Adressbereiche von Office 365](urls-and-ip-address-ranges.md)
  
[Verwalten von ExpressRoute für Office 365-Verbindungen](managing-expressroute-for-connectivity.md)
  
[Prinzipien von Office 365-Netzwerkverbindungen](office-365-network-connectivity-principles.md)