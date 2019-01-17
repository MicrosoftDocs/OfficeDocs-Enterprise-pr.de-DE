---
title: IPv6-Unterstützung in Office 365-Diensten
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/10/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: c08786fb-298e-437c-8222-dab7625fc815
description: 'Zusammenfassung: Beschreibung von IPv6-Unterstützung in Microsoft Office 365-Komponenten und in Office 365 Government angeboten.'
ms.openlocfilehash: 82af5c7659b3c16c8e92b45b65b6868a404eca23
ms.sourcegitcommit: c5ee713709d76f519cb77de0e12c435d8409f571
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2019
ms.locfileid: "28327357"
---
# <a name="ipv6-support-in-office-365-services"></a>IPv6-Unterstützung in Office 365-Diensten

 **Zusammenfassung**: Beschreibt die IPv6-Unterstützung in Microsoft Office 365-Komponenten und in Office 365 Government angeboten.
  
Office 365 unterstützt sowohl IPv4 als auch IPv6. nicht alle Office 365-Features sind jedoch vollständig mit IPv6 aktiviert. Dies bedeutet, dass Sie sowohl IPv4 als auch IPv6 verwenden müssen, Verbindung mit Office 365. Wenn Sie Ihre ausgehenden Datenverkehr zu Office 365 filtern, kann die vollständige Liste der IPv6-Adressen, die von Office 365 unterstützt werden im Artikel [Office 365-URLs und IP-Adressbereiche](urls-and-ip-address-ranges.md)gefunden werden. Nachdem Sie Ihr Netzwerk konfiguriert ist und die entsprechenden IPv6-Adressen zulässig ist, können Sie die [Office 365-IPv6-Testplan](https://go.microsoft.com/fwlink/?LinkId=293447) aus dem Microsoft Download Center herunterladen.
  
||
|:-----|
| Dieser Artikel ist Teil der [Planung von Netzwerk und zur leistungsoptimierung für Office 365](https://aka.ms/tune).|

## <a name="ipv6-support-in-office-365-subscription-service"></a>IPv6-Unterstützung in Office 365-Abonnement-Dienst

### <a name="exchange-online-and-ipv6"></a>Exchange Online und IPv6

Wenn das Programm, das Sie verwenden, um eine Verbindung zu Exchange Online herstellen, IPv6 unterstützt, wird standardmäßig auf verkabelten und drahtlose Netzwerke IPv6 verwendet. Wenn Sie für die Kommunikation mit Exchange Online steuern möchten, verwenden Sie die IP-Adressbereiche in [Office 365-URLs und IP-Adressbereiche](urls-and-ip-address-ranges.md).
  
### <a name="sharepoint-online-and-ipv6"></a>SharePoint Online und IPv6

 **Office 365 Government G1/G3/G4/K1** Wenn das Programm, das Sie mit SharePoint Online herstellen, IPv6 unterstützt, wird versucht, IPv6 standardmäßig verwendet.
  
 **Öffentliche mit mehreren Mandanten cloud** Microsoft ermöglicht SharePoint Online IPv6 auf Ihre Anforderung. Sie müssen angeben, dass die CIDR aus IP-Adressen für die DNS-Infrastruktur Ihres Unternehmens gebildet. Beachten Sie, dass diese DNS-Infrastruktur von anderen Organisationen für IPv6 für Ihre Mandanten aktiviert werden nicht beibehalten. Nachdem IPv6 und das Programm, das Sie mit SharePoint Online herstellen, IPv6 unterstützt aktiviert ist, wird standardmäßig IPv6 verwendet.
  
Wenn das Programm, das Sie mit SharePoint Online herstellen, IPv6 unterstützt, wird standardmäßig auf verkabelten und drahtlose Netzwerke IPv6 verwendet. Wenn Sie für die Kommunikation mit SharePoint Online steuern möchten, verwenden Sie die IP-Adressbereiche in [Office 365-URLs und IP-Adressbereiche](urls-and-ip-address-ranges.md).
  
 **Office 365 Government G1/G3/G4/K1** Wenn das Programm, das Sie mit SharePoint Online herstellen, IPv6 unterstützt, wird versucht, IPv6 standardmäßig verwendet.
  
### <a name="skype-for-business-and-ipv6"></a>Skype für Unternehmen und IPv6

Beachten Sie bitte IPv6 Skype für Unternehmen wird nicht unterstützt und kann nicht mehr aktiviert werden.
  
### <a name="exchange-online-protection-and-ipv6"></a>Exchange Online Protection und IPv6

Exchange Online Protection (EOP) unterstützt IPv6, bei die Übertragung über Transport Layer Security-Protokoll. Verwenden Sie für den Bereich EOP [Office 365-URLs und IP-Adressbereiche](urls-and-ip-address-ranges.md).
  
### <a name="ipv6-support-for-office-365-government-offerings"></a>IPv6-Unterstützung in Angeboten für Office 365 für Behörden

IPv6-Unterstützung für Office 365 für Behörden Dienstangebote konform Vereinbarung Budget (OMB) und der Office of Management für Leiter Informationen Führungskräfte des Executive Abteilungen und Behörden sowie die Federal Behörden Annahme von Internetprotokoll Version 6 (IPv6 ) Vereinbarung. [Microsoft Office 365 für Behörden](https://go.microsoft.com/fwlink/p/?LinkId=325414) ist ein mit mehreren Mandanten-Dienst, der ein separater Community-Cloud der US-Regierung Daten speichert. Wie andere Office 365-Dienstangebote bereitstellt es Teamproduktivität und Dienste, einschließlich Exchange Online, Skype für Unternehmen, SharePoint Online und Office Professional Plus. 

Die Microsoft Office 365-Dienstangebote Behörden gelten nur für 2013 oder höher. Weitere Informationen zu den Office 365-Dienstangebote Behörden, finden Sie unter [Ankündigung von Office 365 für Behörden: eine US-Regierung Community-Cloud](https://go.microsoft.com/fwlink/p/?LinkId=325414). International Datenverkehr in Waffen Vorschriften (ITAR) ist eine Reihe von US behördlichen Vorschriften, die steuern, den Export und Import von Defense Artikeln und Dienste auf den [Vereinigten Staaten Munition Liste (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415). 

Microsoft Office 365 für Unternehmen bietet dedizierte Hostingdienste für Microsoft-produktivitätslösungen, die die Sicherheit, Datenschutz und gesetzliche Vorschriften und Richtlinien für uns federal Behörden erfordern Federal Information Security unterstützen Verwaltung (FISMA) Zertifizierung und kommerziellen Entitäten Betreff zu ITAR.
  
## <a name="things-to-consider-when-using-ipv6-and-office-365"></a>Erwägungen bei der Verwendung von IPv6 und Office 365

Es wird empfohlen, dass Sie IPv6 nicht deaktivieren. Weitere Informationen finden Sie unter in diesem [Artikel Anweisungen](https://support.microsoft.com/help/929852/guidance-for-configuring-ipv6-in-windows-for-advanced-users). Um zu bestimmen, welche Versionen der IP-Netzwerk verwendet werden, berücksichtigen Sie Folgendes ein:
  
- Wenn die Anzeige des **IPConfig** -Befehls an der Eingabeaufforderung Zeilen namens "IPv6-Adresse" oder "Temporäre IPv6-Adresse" enthält, müssen Sie in Ihrer Umgebung IPv6.

- Wenn alle IPv6-Adressen mit "fe80" beginnen und in Zeilen namens "Verbindungslokale IPv6-Adresse" entsprechen, müssen Sie nicht IPv6 in Ihrer Umgebung.

Die folgenden Überlegungen gelten möglicherweise für Ihr Netzwerk:
  
- Der öffentliche Abonnementdienst unterstützt keine Kreditkartenkäufe über IPv6. Dies gilt nicht für die Government Community Cloud (GCC), da Regierungen EA-Lizenzen (Enterprise Agreement) besitzen.

- Einige RMS-Szenarien (Rights Management Services, Rechteverwaltungsdienste) werden von IPv6 nicht unterstützt.

- BlackBerry® Enterprise Server (BES) wird von IPv6 nicht unterstützt werden, da BlackBerry IPv6 nicht unterstützt.

- Wenn Sie Active Directory-Verbunddienste (AD FS) mit Office 365 verwenden, wird Werbung Ihrer AD FS-Netzwerk-Endpunkt zu Office 365 verwenden IPv6 nicht unterstützt. Sie sollten nicht AAAA-Einträge im AD FS-DNS-Eintrag enthalten, wenn Sie Exchange Online verwenden. 

Mit diesem kurzen Link gelangen Sie wieder hierher zurück: [https://aka.ms/o365ip6](https://aka.ms/o365ip6)
  
## <a name="see-also"></a>Siehe auch

[IPv6-Lern-Roadmap](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/gg250710(v%3dws.10))
  
[IPv6-Grundlagen](https://social.technet.microsoft.com/wiki/contents/articles/1728.ipv6-survival-guide.aspx)
