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
description: 'Zusammenfassung: Beschreibt die IPv6-Unterstützung in Microsoft Office 365-Komponenten und in Office 365 Government-angeboten.'
ms.openlocfilehash: 82af5c7659b3c16c8e92b45b65b6868a404eca23
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487752"
---
# <a name="ipv6-support-in-office-365-services"></a>IPv6-Unterstützung in Office 365-Diensten

 **Zusammenfassung**: Beschreibt die IPv6-Unterstützung in Microsoft Office 365-Komponenten und in Office 365 Government-angeboten.
  
Office 365 unterstützt sowohl IPv6 als auch IPv4; nicht alle Office 365-Features sind jedoch vollständig mit IPv6 aktiviert. Dies führt dazu, dass Sie IPv4 und IPv6 verwenden müssen, um eine Verbindung mit Office 365 herzustellen. Wenn Sie Ihren ausgehenden Datenverkehr zu Office 365 filtern, finden Sie im Artikel [office 365-URLs und IP-Adressbereiche](urls-and-ip-address-ranges.md)eine vollständige Liste der von Office 365 unterStützten IPv6-Adressen. Nachdem Ihr Netzwerk konfiguriert ist und die entsprechenden IPv6-Adressen zugelassen sind, können Sie den [Office 365 IPv6-Testplan](https://go.microsoft.com/fwlink/?LinkId=293447) aus dem Microsoft Download Center herunterladen.
  
||
|:-----|
| Dieser Artikel ist Teil der [Netzwerkplanung und Leistungsoptimierung für Office 365](https://aka.ms/tune).|

## <a name="ipv6-support-in-office-365-subscription-service"></a>IPv6-Unterstützung im Office 365-Abonnementdienst

### <a name="exchange-online-and-ipv6"></a>Exchange Online und IPv6

Wenn das Programm, mit dem Sie eine Verbindung mit Exchange Online herstellen, IPv6 unterstützt, wird IPv6 standardmäßig in drahtgebundenen und drahtlosen Netzwerken verwendet. Wenn Sie die Kommunikation mit Exchange Online steuern möchten, verwenden Sie die IP-Adressbereiche in [Office 365-URLs und IP-Adressbereichen](urls-and-ip-address-ranges.md).
  
### <a name="sharepoint-online-and-ipv6"></a>SharePoint Online und IPv6

 **Office 365 Government G1/G3/G4/K1** Wenn das Programm, mit dem Sie eine Verbindung mit SharePoint Online herstellen, IPv6 unterstützt, wird standardmäßig versucht, IPv6 zu verwenden.
  
 **Öffentliche mehrinstanzenfähige Cloud** Microsoft aktiviert SharePoint Online IPv6 auf Ihre Anfrage. Sie müssen die in CIDR notierten IP-Adressen für die DNS-Infrastruktur Ihrer Organisation bereitstellen. Beachten Sie, dass diese DNS-Infrastruktur von anderen Organisationen für die Aktivierung von IPv6 für Ihren Mandanten nicht gemeinsam genutzt werden kann. Wenn IPv6 aktiviert ist und das Programm, mit dem Sie eine Verbindung mit SharePoint Online herstellen, IPv6 unterstützt, wird standardmäßig IPv6 verwendet.
  
Wenn das Programm, mit dem Sie eine Verbindung mit SharePoint Online herstellen, IPv6 unterstützt, wird IPv6 standardmäßig in drahtgebundenen und drahtlosen Netzwerken verwendet. Wenn Sie die Kommunikation mit SharePoint Online steuern möchten, verwenden Sie die IP-Adressbereiche in [Office 365-URLs und IP-Adressbereichen](urls-and-ip-address-ranges.md).
  
 **Office 365 Government G1/G3/G4/K1** Wenn das Programm, mit dem Sie eine Verbindung mit SharePoint Online herstellen, IPv6 unterstützt, wird standardmäßig versucht, IPv6 zu verwenden.
  
### <a name="skype-for-business-and-ipv6"></a>Skype for Business und IPv6

Bitte beachten Sie, dass IPv6 in Skype for Business nicht unterstützt wird und nicht mehr aktiviert werden kann.
  
### <a name="exchange-online-protection-and-ipv6"></a>Exchange Online Protection und IPv6

Exchange Online Protection (EOP) unterstützt IPv6, wenn die Übertragung über das Transport Layer Security Protocol erfolgt. Verwenden Sie für den EOP-Bereich [Office 365-URLs und IP-Adressbereiche](urls-and-ip-address-ranges.md).
  
### <a name="ipv6-support-for-office-365-government-offerings"></a>IPv6-Unterstützung für Office 365 Government-Angebote

Office 365 IPv6-Unterstützung für staatliche Angebote entspricht dem Office of Management and Budget (OMB) Memorandum for Chief Information Officers of Executive Departments and Agencies, sowie der Bundesregierung Einführung von Internet Protocol Version 6 (IPv6 Memorandum. [Microsoft Office 365 für Government](https://go.microsoft.com/fwlink/p/?LinkId=325414) ist ein mandantenfähiger Dienst, der US-Regierungsdaten in einer getrennten Community-Cloud speichert. Wie bei anderen Office 365-angeboten bietet das Programm Produktivitäts-und Zusammenarbeitsdienste, einschließlich Exchange Online, Skype for Business, SharePoint Online und Office Professional Plus. 

Das Microsoft Office 365 Government-Angebot gilt nur für 2013 und höher. Weitere Informationen zu den Government-Angeboten von Office 365 finden Sie unter [Ankündigung von office 365 für Government: A US Government Community Cloud](https://go.microsoft.com/fwlink/p/?LinkId=325414). International Traffic in Arms Regulations (ITAR) ist eine Reihe von US-Regierungsverordnungen, die den Export und Import von verteidigungsbezogenen Artikeln und Diensten in der [US-Munitions Liste (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415)steuern. 

Microsoft Office 365 für Unternehmen bietet dedizierte Hosting-Services für Microsoft-Produktivitätslösungen, die die Anforderungen an Sicherheit, Datenschutz und behördliche Vorschriften für US-AMERIKAnische Bundesbehörden unterstützen, die Federal Information Security erfordern. Management (FISMA) Zertifizierung und kommerzielle Entitäten, die ITAR unterliegen.
  
## <a name="things-to-consider-when-using-ipv6-and-office-365"></a>Zu berücksichtigende Aspekte bei der Verwendung von IPv6 und Office 365

Es wird empfohlen, IPv6 nicht zu deaktivieren. Weitere Informationen finden Sie in diesem [Artikel](https://support.microsoft.com/help/929852/guidance-for-configuring-ipv6-in-windows-for-advanced-users). Berücksichtigen Sie Folgendes, um zu bestimmen, welche IP-Versionen in Ihrem Netzwerk verwendet werden:
  
- Wenn die Anzeige des Befehls **ipconfig** an der Eingabezeile die Zeilen mit der Bezeichnung "IPv6-Adresse" oder "temporäre IPv6-Adresse" enthält, haben Sie IPv6 in Ihrer Umgebung.

- Wenn alle IPv6-Adressen mit "FE80" beginnen und den Zeilen mit dem Namen "Link-lokale IPv6-Adresse" entsprechen, haben Sie in Ihrer Umgebung keinen IPv6.

Diese Überlegungen können für Ihr Netzwerk gelten:
  
- Der öffentliche Abonnementdienst unterstützt den Erwerb per Kreditkarte nicht über IPv6. Dies gilt nicht für die Government Community Cloud (GCC), da Regierungen eine Enterprise Agreement (EA)-Lizenzierung haben.

- Einige RMS-Szenarien (Rights Management Services) werden von IPv6 nicht unterstützt.

- IPv6 unterstützt BlackBerry ® Enterprise Server (BES) nicht, da BlackBerry IPv6 nicht unterstützt.

- Wenn Sie Active Directory-Verbunddienste (AD FS) mit Office 365 verwenden, wird die Werbung für Ihren AD FS-Netzwerkendpunkt an Office 365 mithilfe von IPv6 nicht unterstützt. Sie sollten beim Verwenden von Exchange Online keine AAAA-Einträge in den AD FS-DNS-Eintrag aufnehmen. 

Mit diesem kurzen Link gelangen Sie wieder hierher zurück: [https://aka.ms/o365ip6](https://aka.ms/o365ip6)
  
## <a name="see-also"></a>Siehe auch

[Roadmap für IPv6-lernPläne](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/gg250710(v%3dws.10))
  
[IPv6 Survival Guide](https://social.technet.microsoft.com/wiki/contents/articles/1728.ipv6-survival-guide.aspx)
