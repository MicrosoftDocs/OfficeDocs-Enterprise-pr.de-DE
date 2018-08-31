---
title: Office 365 Deutschland Endpunkte Änderungsprotokoll
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 8/13/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
search.appverid: MOE150
ms.assetid: 980041c9-7984-44b2-95f0-af66743543a1
ms.openlocfilehash: e77d6fc3b8136f39ed75ef21b0ff417a4ad6465a
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540958"
---
# <a name="office-365-germany-endpoints-change-log"></a>Office 365 Deutschland Endpunkte Änderungsprotokoll

*Betrifft: Office 365 Admin*

## <a name="list-of-changes-to-the-endpoints-required-for-office-365-germany"></a>Liste der Änderungen an der Endpunkte für Office 365 Deutschland erforderlich

Die folgende Tabelle enthält die Änderungen an [Office 365 Deutschland Endpunkte](office-365-germany-endpoints.md).
  
|**Date**|**Änderung**|
|:-----|:-----|
|1/24/2017  <br/> |Erstveröffentlichung des Artikels.  <br/> |
|2/28/2017  <br/> |Hinzufügen von 3 FQDNs; 1 / [effektiven 4/1/2017. Erforderlich: Office 365-Portal und freigegebene. ExpressRoute: Nein. www.Office.de]; 2 / [effektiven 4/1/2017. Erforderlich: Office 365-Portal und freigegebene. ExpressRoute: Nein. Office.de], 3 / [effektiven 4/1/2017. Erforderlich: Office 365-Portal und freigegebene. ExpressRoute: Nein. officehome.msocdn.de]. Notes: Hinzufügen von zusätzlichen Portal FQDNs. 2 IP_Sets; hinzufügen 1 / [effektiven 4/1/2017. Erforderlich: Office 365-Portal und freigegebene. ExpressRoute: Nein. 51.5.245.67/32], 2 / [effektiven 4/1/2017. Erforderlich: Office 365-Portal und freigegebene. ExpressRoute: Nein. 51.4.227.178/32]. Hinweise: Zusätzliche Portal-Endpunkte hinzufügen. Hinzufügen von 2 IP_Sets; 1 / [effektiven 4/1/2017. Erforderlich: Office 365-Portal und freigegebene. ExpressRoute: Nein. 2a01:4180:2001::92], 2 / [effektiven 4/1/2017. Erforderlich: Office 365-Portal und freigegebene. ExpressRoute: Nein. 2a01:4180:2401::11f]. Hinweise: Zusätzliche Portal-Endpunkte hinzufügen.  <br/> |
|3/8/2017  <br/> |Hinzufügen von 1 FQDNs; 1 / [effektiven 3/8/2017. Erforderlich: OneDrive für Unternehmen. ExpressRoute: Nein. Spoprod-a.akamaihd.net];. Hinweise: Zusätzliche CDN-Endpunkte hinzufügen.  <br/> |
|3/31/2017  <br/> |Hinzufügen von 3 FQDNs; 1 / [effektiven 5/1/2017. Erforderlich: SharePoint Online Hybrid. \*. search.production.de.azuretrafficmanager.de], 2 / [effektiven 5/1/2017. Erforderlich: SharePoint Online Hybrid. Login.microsoftonline.de], 3 / [effektiven 5/1/2017. Erforderlich: SharePoint Online Hybrid. provisioningapi.microsoftonline.de]. Notes: Hinzufügen von Sharepoint-Hybrid FQDNs.  <br/> |
|6/1/2017  <br/> |Hinzufügen von 2 FQDNs effektiven 7/1/2017  <br/> shellprod.msocdn.de  <br/> R1.Res.Office365.com  <br/> |
|6/26/2017  <br/> |AutoErmittlung ersetzt\*. outlook.de mit Autodiscover.outlook.de und AutoErmittlung-outlook.office.de.  <br/> |
|9/29/2017  <br/> |Hinzufügen von 3 FQDNs; 1 / [effektiven 11/1/2017.  <br/> cegsignup.Microsoft.de  <br/> negsignup.Microsoft.de  <br/> \*. svc.ms  <br/> |
|1/16/2018  <br/> |Hinzufügen von 1 FQDNs; 1 / [effektiven 2/1/2018. Erforderlich: Office 365-Portal. ExpressRoute: Nein. webshell.Suite.Office.de]. Notes: Hinzufügen des FQDN des zusätzlichen für Office 365-Suite-Shell. Hinzufügen von 4 IP_Sets; 1 / [effektiven 2/1/2018. Erforderlich: Office 365-Portal. ExpressRoute: Nein. 51.5.242.163/32], 2 / [effektiven 2/1/2018. Erforderlich: Office 365-Portal. ExpressRoute: Nein. 51.4.226.115/32], 3 / [effektiven 2/1/2018. Erforderlich: Office 365-Portal. ExpressRoute: Nein. 2a01:4180:2401::33b / 4 / [effektiven 2/1/2018. Erforderlich: Office 365-Portal. ExpressRoute: Nein. 2a01:4180:2001::234 / Hinweise: Hinzufügen von zusätzlichen IP-Adressen für Office 365-Suite-Shell.  <br/> |
|2/5/2018  <br/> |Hinzufügen von 1 FQDN; 1 / [effektiven 3/1/2018. Erforderlich: Portal und freigegebene. ExpressRoute: Ja. webshell.Suite.Office.de]. Notes: Hinzufügen einer URL für Portal und freigegebene FQDNs. 2 IP_Sets; hinzufügen 1 / [effektiven 3/1/2018. Erforderlich: Portal und freigegebene. ExpressRoute: Ja. 51.5.242.163/32]., 2 / [effektiven 3/1/2018. Erforderlich: Portal und freigegebene. ExpressRoute: Ja. 51.4.226.115/32]. Hinweise: Hinzufügen von neuen Präfixen für Portal und freigegeben. Hinzufügen von 2 IP_Sets; 1 / [effektiven 3/1/2018. Erforderlich: Portal und freigegebene. ExpressRoute: Ja. 2a01:4180:2401::33b / 128]., 2 / [effektiven 3/1/2018. Erforderlich: Portal und freigegebene. ExpressRoute: Ja. 2a01:4180:2001::234 / 128]. Hinweise: Hinzufügen von neuen Präfixen für Portal und freigegeben. Hinzufügen von 1 IP_Sets; 1 / [effektiven 3/1/2018. Erforderlich: Office Online. ExpressRoute: Ja. 51.18.16.0/23]. Hinweise: Hinzufügen eines neuen Präfixes für Microsoft Office Online.  <br/> |
|3/15/2018  <br/> |Hinzufügen von 1 IP_Set; 1 / [effektiven 4/15/2018. Erforderlich: Office 365 ProPlus. ExpressRoute: Nein. 51.18.0.0/21]. Hinweise: Hinzufügen von Office 365 ProPlus-Endpunkt.  <br/> |
|7/2/2018  <br/> |Entfernen von 1 FQDN; 1 / [effektiven 8/1/2018. Erforderlich: OneDrive für Unternehmen. ExpressRoute: Nein. Login.microsoftonline.de]. Notes: Entfernen von OneDrive for Business-Endpunkt. Entfernen von 11 FQDNs; 1 / [effektiven 8/1/2018. Erforderlich: Office Mobile. ExpressRoute: Nein. https://excelps.osi.office.de/exlps/excelprint.svc/exlPrint], 2 / [effektiven 8/1/2018. Erforderlich: Office Mobile. ExpressRoute: Nein. https://wordps.osi.office.de/wrdps/wordprint.svc/wrdprint], 3 / [effektiven 8/1/2018. Erforderlich: Office Mobile. ExpressRoute: Nein. https://wordcs.osi.office.de/wordauto/wordautomation.svc/wordautomation], 4 / [effektiven 8/1/2018. Erforderlich: Office Mobile. ExpressRoute: Nein. https://wordcs.osi.office.de/wordauto/wordautomation.svc/rest], 5 / [effektiven 8/1/2018. Erforderlich: Office Mobile. ExpressRoute: Nein. https://pptps.osi.office.de/pptps/powerpointprint.svc/PptPrint], 6 / [effektiven 8/1/2018. Erforderlich: Office Mobile. ExpressRoute: Nein. https://pptcs.osi.office.de/pptauto/PowerpointAutomation.svc/PptAutomation], 7 / [effektiven 8/1/2018. Erforderlich: Office Mobile. ExpressRoute: Nein. https://pptcs.osi.office.de/pptauto/PowerpointAutomation.svc/rest], 8 / [effektiven 8/1/2018. Erforderlich: Office Mobile. ExpressRoute: Nein. https://ols.osi.office.de/], 9 / [effektiven 8/1/2018. Erforderlich: Office Mobile. ExpressRoute: Nein. https://ols.osi.office.de/olsc/OlsClient.svc/OlsClient], 10 / [effektiven 8/1/2018. Erforderlich: Office Mobile. ExpressRoute: Nein. https://excelcs.osi.office.de/xlauto/excelautomation.svc/XlAutomation], 11 / [effektiven 8/1/2018. Erforderlich: Office Mobile. ExpressRoute: Nein. https://excelcs.osi.office.de/xlauto/excelautomation.svc/rest]. Hinweise: Entfernen von Office Mobile Endpunkte.  <br/> |
   

