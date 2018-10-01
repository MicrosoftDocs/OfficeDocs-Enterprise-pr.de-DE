---
title: Zusätzliche Office 365-IP-Adressen und -URLs, die nicht in den Webdiensten enthalten sind
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 9/13/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- MOM160
- BCS160
ms.assetid: ''
description: 'Zusammenfassung: In den neuen Endpunkt-Webdiensten ist eine kleine Anzahl von Endpunkten für bestimmte Szenarien nicht enthalten.'
hideEdit: true
ms.openlocfilehash: 4711f9b9560b0fab6d18700fcf3e933150861946
ms.sourcegitcommit: 0f98c342f80ffa21ec35bbf4ae5619b5e3271da5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/14/2018
ms.locfileid: "23977350"
---
# <a name="additional-office-365-ip-addresses-and-urls-not-included-in-the-web-services"></a>Zusätzliche Office 365-IP-Adressen und -URLs, die nicht in den Webdiensten enthalten sind

Einige Netzwerkendpunkte wurden früher veröffentlicht, aber nicht in die Webdienste aufgenommen. Der Webdienstbereich besteht aus Netzwerkendpunkten, die für die Konnektivität eines Endbenutzers von Office 365 über ein Unternehmens-Umkreisnetzwerk hinweg erforderlich sind. Dies umfasst aktuell die folgenden Punkte nicht:

1. Netzwerkkonnektivität, die möglicherweise zwischen einem Microsoft-Rechenzentrum und einem Kundennetzwerk erforderlich ist (eingehender Server-Netzwerkdatenverkehr in Hybridbereitstellungen)
2. Netzwerkkonnektivität von Servern in einem Kundennetzwerk über das Umkreisnetzwerk des Unternehmens hinweg (ausgehender Server-Netzwerkdatenverkehr)
3. Ungewöhnliche Szenarien für Netzwerkkonnektivitäts-Anforderungen eines Benutzers
4. Konnektivitätsanforderung für DNS-Auflösung (unten nicht aufgeführt)
5. Vertrauenswürdige Websites von Internet Explorer oder Microsoft Edge

Abgesehen von DNS sind alle diese Punkte für die meisten Benutzer optional, es sei denn, Sie müssen das bestimmte beschriebene Szenario berücksichtigen.

|||||
|:-----|:-----|:-----|:-----|
| **Zeile** | **Zweck** | **Ziel** | **Typ** |
| 1  | [Importdienst](https://support.office.com/article/use-network-upload-to-import-your-organization-pst-files-to-office-365-103f940c-0468-4e1a-b527-cc8ad13a5ea6) für PST- und Dateierfassung | Informationen zu weiteren Anforderungen finden Sie unter [Importdienst](https://support.office.com/article/use-network-upload-to-import-your-organization-pst-files-to-office-365-103f940c-0468-4e1a-b527-cc8ad13a5ea6). | Ungewöhnliches ausgehendes Szenario |
| 2  | [Microsoft Support- und Wiederherstellungs-Assistent für Office 365](https://diagnostics.office.com/#/) – Überprüfen der Benutzeranmeldeinformationen für einmaliges Anmelden. Quelle: <br> ```o365diagnosticsbasic-eus.cloudapp.net (104.211.54.99)``` <br> ```o365diagnosticworker-eus.cloudapp.net (104.211.54.134)```  | Lokaler Sicherheitstokendienst | Eingehender Serverdatenverkehr |
| 3  | Azure AD Connect (mit SSO-Option) – WinRM und Remote PowerShell | STS-Kundenumgebung (AD FS Server und AD FS Proxy) \| TCP-Ports 80 und 443 | Eingehender Serverdatenverkehr |
| 4  | STS wie AD FS-Proxyserver (nur Kunden mit Partnerverbund) | Kunden-STS (wie etwa AD FS Proxy) \| Ports TCP 443 oder TCP 49443 mit ClientTLS | Eingehender Serverdatenverkehr |
| 5  | [Integration von Exchange Online Unified Messaging/SBC](https://technet.microsoft.com/library/jj673565.aspx) | Bidirektional zwischen lokalem Session Border Controller und *.um.outlook.com | Nur ausgehender Serverdatenverkehr |
| 6  | [Exchange Hybrid](https://docs.microsoft.com/exchange/exchange-deployment-assistant)-Funktionen für Koexistenz, wie etwa Teilen der Frei/Gebucht-Informationen. | Lokale Exchange-Kundenserver | Eingehender Serverdatenverkehr |
| 7  | [Exchange Hybrid](https://docs.microsoft.com/exchange/exchange-deployment-assistant)-Proxyauthentifizierung | Lokaler STS von Kunden | Eingehender Serverdatenverkehr |
| 8  | Zum Konfigurieren von [Exchange-Hybridbereitstellungen](https://docs.microsoft.com/exchange/exchange-deployment-assistant) mit dem Exchange-Hybridkonfigurations-Assistenten verwendet. <br> Hinweis: Diese Endpunkte sind nur für die Konfiguration von Exchange-Hybridbereitstellungen erforderlich  | ```domains.live.com``` an den TCP-Ports 80 und 443, nur für den Exchange 2010 SP3-Hybridkonfigurations-Assistenten erforderlich. | Nur ausgehender Serverdatenverkehr |
| 9  | Der AutoDetect-Dienst wird in[Exchange-Hybridszenarien](https://docs.microsoft.com/exchange/exchange-deployment-assistant) mit [der modernen Hybridauthentifizierung mit Outlook für iOS und Android](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) verwendet. <BR> <BR> ```*.acompli.net``` <BR> ```*.outlookmobile.us``` <BR> <BR> ```52.125.128.0/20``` <BR> ```52.127.96.0/23``` <BR> | Lokale Exchange-Kundenserver an TCP-Port 443 | Eingehender Serverdatenverkehr |
| 10  | **FQDNs für Authentifizierung und Identität** <br> Für ordnungsgemäße Funktion muss sich der FQDN ```secure.aadcdn.microsoftonline-p.com``` in der Zone "Vertrauenswürdige Sites" von Internet Explorer (IE) oder Edge des Clients befinden. |  | Vertrauenswürdige Sites |
| 11  |  **FQDNs für Microsoft Teams** <br> Wenn Sie Internet Explorer oder Microsoft Edge verwenden, müssen Sie Cookies von Erst- und Drittanbietern aktivieren und die FQDNs für Teams zu Ihren vertrauenswürdigen Sites hinzufügen. Dies muss zusätzlich zu den oben aufgeführten Werten für FQDNs, CDNs und Telemetrie für die gesamte Suite erfolgen. Weitere Informationen finden Sie unter [Bekannte Probleme bei Microsoft Teams](https://docs.microsoft.com/microsoftteams/known-issues). |  | Vertrauenswürdige Sites |
| 12  |  **FQDNs für SharePoint Online und OneDrive for Business** <br> Für eine ordnungsgemäße Funktion müssen sich alle FQDNs von ".sharepoint.com" mit "\<tenant>" im FQDN in der Zone "Vertrauenswürdige Sites" des IE oder Edge Ihres Clients befinden. Sie müssen diese Endpunkte über die oben aufgelisteten, für die gesamte Suite gültigen FQDNs, CDNs und Telemetriewerte hinaus hinzufügen. |  | Vertrauenswürdige Sites |
| 13  | **Yammer**  <br> Yammer steht nur im Browser zur Verfügung und erfordert die Übergabe des authentifizierten Benutzers durch einen Proxy. Alle Yammer-FQDNs müssen sich für eine ordnungsgemäße Funktion in der Zone "Vertrauenswürdige Sites" des IE oder Edge Ihres Clients befinden. |  | Vertrauenswürdige Sites |

## <a name="related-topics"></a>Verwandte Themen

[Verwalten von Office 365-Endpunkten](managing-office-365-endpoints.md)
  
[Problembehandlung bei Office 365-Verbindungen](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d.aspx)
  
[Clientkonnektivität](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
  
[Netzwerke für die Inhaltsübermittlung](https://support.office.com/article/content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)
  
[IP-Bereiche von Microsoft Azure-Rechenzentren](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Öffentlicher Microsoft IP-Bereich](https://www.microsoft.com/download/details.aspx?id=53602)

