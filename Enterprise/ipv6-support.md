---
title: IPv6-Unterstützung in Office 365-Diensten
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/12/2017
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
ms.openlocfilehash: 74752988803728ef4c319e368150b90f7e5d2599
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223127"
---
# <a name="ipv6-support-in-office-365-services"></a><span data-ttu-id="2097f-103">IPv6-Unterstützung in Office 365-Diensten</span><span class="sxs-lookup"><span data-stu-id="2097f-103">IPv6 support in Office 365 services</span></span>

 <span data-ttu-id="2097f-104">**Zusammenfassung**: Beschreibt die IPv6-Unterstützung in Microsoft Office 365-Komponenten und in Office 365 Government angeboten.</span><span class="sxs-lookup"><span data-stu-id="2097f-104">**Summary**: Describes IPv6 support in Microsoft Office 365 components and in Office 365 government offerings.</span></span>
  
<span data-ttu-id="2097f-p101">Office 365 unterstützt sowohl IPv4 als auch IPv6. nicht alle Office 365-Features sind jedoch vollständig mit IPv6 aktiviert. Dies bedeutet, dass Sie sowohl IPv4 als auch IPv6 verwenden müssen, Verbindung mit Office 365. Wenn Sie Ihre ausgehenden Datenverkehr zu Office 365 filtern, kann die vollständige Liste der IPv6-Adressen, die von Office 365 unterstützt werden im Artikel [Office 365-URLs und IP-Adressbereiche](https://go.microsoft.com/fwlink/?LinkId=293744)gefunden werden. Nachdem Sie Ihr Netzwerk konfiguriert ist und die entsprechenden IPv6-Adressen zulässig ist, können Sie die [Office 365-IPv6-Testplan](https://go.microsoft.com/fwlink/?LinkId=293447) aus dem Microsoft Download Center herunterladen.</span><span class="sxs-lookup"><span data-stu-id="2097f-p101">Office 365 supports both IPv6 and IPv4; however, not all Office 365 features are fully enabled with IPv6. This means that you must use both IPv4 and IPv6 to connect to Office 365. If you are filtering your outbound traffic to Office 365, the full list of IPv6 addresses that are supported by Office 365 can be found in the article [Office 365 URLs and IP address ranges](https://go.microsoft.com/fwlink/?LinkId=293744). After your network is configured and the appropriate IPv6 addresses are allowed, you can download the [Office 365 IPv6 test plan](https://go.microsoft.com/fwlink/?LinkId=293447) from the Microsoft Download Center.</span></span>
  
||
|:-----|
| <span data-ttu-id="2097f-109">Dieser Artikel ist Teil der [Planung von Netzwerk und zur leistungsoptimierung für Office 365](https://aka.ms/tune).</span><span class="sxs-lookup"><span data-stu-id="2097f-109">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

## <a name="ipv6-support-in-office-365-subscription-service"></a><span data-ttu-id="2097f-110">IPv6-Unterstützung in Office 365-Abonnement-Dienst</span><span class="sxs-lookup"><span data-stu-id="2097f-110">IPv6 support in Office 365 subscription service</span></span>

### <a name="exchange-online-and-ipv6"></a><span data-ttu-id="2097f-111">Exchange Online und IPv6</span><span class="sxs-lookup"><span data-stu-id="2097f-111">Exchange Online and IPv6</span></span>

<span data-ttu-id="2097f-p102">Wenn das Programm, das Sie verwenden, um eine Verbindung zu Exchange Online herstellen, IPv6 unterstützt, wird standardmäßig auf verkabelten und drahtlose Netzwerke IPv6 verwendet. Wenn Sie für die Kommunikation mit Exchange Online steuern möchten, verwenden Sie die IP-Adressbereiche in [Office 365-URLs und IP-Adressbereiche](https://go.microsoft.com/fwlink/?LinkId=293744).</span><span class="sxs-lookup"><span data-stu-id="2097f-p102">If the program that you use to connect to Exchange Online supports IPv6, it will use IPv6 by default on both wired and wireless networks. If you want to control communications to Exchange Online, use the IP address ranges in [Office 365 URLs and IP address ranges](https://go.microsoft.com/fwlink/?LinkId=293744).</span></span>
  
### <a name="sharepoint-online-and-ipv6"></a><span data-ttu-id="2097f-114">SharePoint Online und IPv6</span><span class="sxs-lookup"><span data-stu-id="2097f-114">SharePoint Online and IPv6</span></span>

 <span data-ttu-id="2097f-115">**Office 365 Government G1/G3/G4/K1** Wenn das Programm, das Sie mit SharePoint Online herstellen, IPv6 unterstützt, wird versucht, IPv6 standardmäßig verwendet.</span><span class="sxs-lookup"><span data-stu-id="2097f-115">**Office 365 Government G1/G3/G4/K1** If the program that you use to connect to SharePoint Online supports IPv6, it will attempt to use IPv6 by default.</span></span>
  
 <span data-ttu-id="2097f-p103">**Öffentliche mit mehreren Mandanten cloud** Microsoft ermöglicht SharePoint Online IPv6 auf Ihre Anforderung. Sie müssen angeben, dass die CIDR aus IP-Adressen für die DNS-Infrastruktur Ihres Unternehmens gebildet. Beachten Sie, dass diese DNS-Infrastruktur von anderen Organisationen für IPv6 für Ihre Mandanten aktiviert werden nicht beibehalten. Nachdem IPv6 und das Programm, das Sie mit SharePoint Online herstellen, IPv6 unterstützt aktiviert ist, wird standardmäßig IPv6 verwendet.</span><span class="sxs-lookup"><span data-stu-id="2097f-p103">**Public multi-tenant cloud** Microsoft enables SharePoint Online IPv6 at your request. You need to provide the CIDR notated IP addresses for your organization's DNS infrastructure. Keep in mind that this DNS infrastructure can't be shared by other organizations for IPv6 to be enabled for your tenant. After IPv6 is enabled, if the program that you use to connect to SharePoint Online supports IPv6, it uses IPv6 by default.</span></span>
  
<span data-ttu-id="2097f-p104">Wenn das Programm, das Sie mit SharePoint Online herstellen, IPv6 unterstützt, wird standardmäßig auf verkabelten und drahtlose Netzwerke IPv6 verwendet. Wenn Sie für die Kommunikation mit SharePoint Online steuern möchten, verwenden Sie die IP-Adressbereiche in [Office 365-URLs und IP-Adressbereiche](https://go.microsoft.com/fwlink/?LinkId=293744).</span><span class="sxs-lookup"><span data-stu-id="2097f-p104">If the program that you use to connect to SharePoint Online supports IPv6, it will use IPv6 by default on both wired and wireless networks. If you want to control communications to SharePoint Online, use the IP address ranges in [Office 365 URLs and IP address ranges](https://go.microsoft.com/fwlink/?LinkId=293744).</span></span>
  
 <span data-ttu-id="2097f-122">**Office 365 Government G1/G3/G4/K1** Wenn das Programm, das Sie mit SharePoint Online herstellen, IPv6 unterstützt, wird versucht, IPv6 standardmäßig verwendet.</span><span class="sxs-lookup"><span data-stu-id="2097f-122">**Office 365 Government G1/G3/G4/K1** If the program that you use to connect to SharePoint Online supports IPv6, it will attempt to use IPv6 by default.</span></span>
  
### <a name="skype-for-business-and-ipv6"></a><span data-ttu-id="2097f-123">Skype für Unternehmen und IPv6</span><span class="sxs-lookup"><span data-stu-id="2097f-123">Skype for Business and IPv6</span></span>

<span data-ttu-id="2097f-p105">Microsoft wird IPv6 für Skype für Unternehmen auf Ihre Anforderung in der öffentlichen Cloud mit mehreren Mandanten und in Office 365 Government G1/G3/G4/K1 Abonnements aktivieren. Nachdem sie aktiviert ist, wenn das Programm, das Sie mit Skype für Unternehmen herstellen, IPv6 unterstützt, wird standardmäßig IPv6 verwendet. Wenn Sie für die Kommunikation mit Skype für Unternehmen steuern möchten, verwenden Sie die IP-Adressbereiche in [Office 365-URLs und IP-Adressbereiche](https://go.microsoft.com/fwlink/?LinkId=293744).</span><span class="sxs-lookup"><span data-stu-id="2097f-p105">Microsoft will enable IPv6 for Skype for Business at your request in the public multi-tenant cloud and in Office 365 Government G1/G3/G4/K1 subscriptions. After it's enabled, if the program that you use to connect to Skype for Business supports IPv6, it will use IPv6 by default. If you want to control communications to Skype for Business, use the IP address ranges in [Office 365 URLs and IP address ranges](https://go.microsoft.com/fwlink/?LinkId=293744).</span></span>
  
<span data-ttu-id="2097f-127">Beachten Sie bitte IPv6 steht nicht in allen Regionen und Microsoft möglicherweise nicht für Ihre Mandanten zu diesem Zeitpunkt aktivieren.</span><span class="sxs-lookup"><span data-stu-id="2097f-127">Please be aware IPv6 is not available in all regions and Microsoft may not be able to activate it for your Tenant at this time.</span></span>
  
### <a name="exchange-online-protection-and-ipv6"></a><span data-ttu-id="2097f-128">Exchange Online Protection und IPv6</span><span class="sxs-lookup"><span data-stu-id="2097f-128">Exchange Online Protection and IPv6</span></span>

<span data-ttu-id="2097f-p106">Exchange Online Protection (EOP) unterstützt IPv6, bei die Übertragung über Transport Layer Security-Protokoll. Verwenden Sie für den Bereich EOP [Office 365-URLs und IP-Adressbereiche](https://go.microsoft.com/fwlink/?LinkId=293744).</span><span class="sxs-lookup"><span data-stu-id="2097f-p106">Exchange Online Protection (EOP) supports IPv6 if the transmission occurs over Transport Layer Security Protocol. For the EOP range, use [Office 365 URLs and IP address ranges](https://go.microsoft.com/fwlink/?LinkId=293744).</span></span>
  
### <a name="ipv6-support-for-office-365-government-offerings"></a><span data-ttu-id="2097f-131">IPv6-Unterstützung in Angeboten für Office 365 für Behörden</span><span class="sxs-lookup"><span data-stu-id="2097f-131">IPv6 support for Office 365 government offerings</span></span>

<span data-ttu-id="2097f-p107">IPv6-Unterstützung für Office 365 für Behörden Dienstangebote konform Vereinbarung Budget (OMB) und der Office of Management für Leiter Informationen Führungskräfte des Executive Abteilungen und Behörden sowie die Federal Behörden Annahme von Internetprotokoll Version 6 (IPv6 ) Vereinbarung. [Microsoft Office 365 für Behörden](https://go.microsoft.com/fwlink/p/?LinkId=325414) ist ein mit mehreren Mandanten-Dienst, der ein separater Community-Cloud der US-Regierung Daten speichert. Wie andere Office 365-Dienstangebote bereitstellt es Teamproduktivität und Dienste, einschließlich Exchange Online, Skype für Unternehmen, SharePoint Online und Office Professional Plus. Die Microsoft Office 365-Dienstangebote Behörden gelten nur für 2013 oder höher. Weitere Informationen zu den Office 365-Dienstangebote Behörden, finden Sie unter [Ankündigung von Office 365 für Behörden: eine US-Regierung Community-Cloud](https://go.microsoft.com/fwlink/p/?LinkId=325414). International Datenverkehr in Waffen Vorschriften (ITAR) ist eine Reihe von US behördlichen Vorschriften, die steuern, den Export und Import von Defense Artikeln und Dienste auf den [Vereinigten Staaten Munition Liste (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415). Microsoft Office 365 für Unternehmen bietet dedizierte Hostingdienste für Microsoft-produktivitätslösungen, die die Sicherheit, Datenschutz und gesetzliche Vorschriften und Richtlinien für uns federal Behörden erfordern Federal Information Security unterstützen Verwaltung (FISMA) Zertifizierung und kommerziellen Entitäten Betreff zu ITAR.</span><span class="sxs-lookup"><span data-stu-id="2097f-p107">Office 365 IPv6 support for government offerings conforms to the Office of Management and Budget (OMB) Memorandum for Chief Information Officers of Executive Departments and Agencies, as well as the Federal Government Adoption of Internet Protocol Version 6 (IPv6) memorandum. [Microsoft Office 365 for Government](https://go.microsoft.com/fwlink/p/?LinkId=325414) is a multi-tenant service that stores US government data in a segregated community cloud. Like other Office 365 offerings, it provides productivity and collaboration services, including Exchange Online, Skype for Business, SharePoint Online, and Office Professional Plus. The Microsoft Office 365 government offerings apply only for 2013 and later. For more information about the Office 365 government offerings, see [Announcing Office 365 for Government: A US Government Community Cloud](https://go.microsoft.com/fwlink/p/?LinkId=325414). International Traffic in Arms Regulations (ITAR) is a set of US government regulations that control the export and import of defense-related articles and services on the [United States Munitions List (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415). Microsoft Office 365 for Enterprises provides dedicated hosting services for Microsoft productivity solutions that support the security, privacy, and regulatory compliance requirements for US federal agencies requiring Federal Information Security Management (FISMA) certification and commercial entities subject to ITAR.</span></span>
  
## <a name="things-to-consider-when-using-ipv6-and-office-365"></a><span data-ttu-id="2097f-139">Erwägungen bei der Verwendung von IPv6 und Office 365</span><span class="sxs-lookup"><span data-stu-id="2097f-139">Things to consider when using IPv6 and Office 365</span></span>

<span data-ttu-id="2097f-p108">Es wird empfohlen, dass Sie IPv6 nicht deaktivieren. Weitere Informationen finden Sie unter [IPv6 für Microsoft Windows: häufig gestellte Fragen](https://go.microsoft.com/fwlink/p/?LinkId=325418). Um zu bestimmen, welche Versionen der IP-Netzwerk verwendet werden, berücksichtigen Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="2097f-p108">We recommend that you do not disable IPv6. For more information, see [IPv6 for Microsoft Windows: Frequently Asked Questions](https://go.microsoft.com/fwlink/p/?LinkId=325418). To determine what IP versions are being used on your network, consider the following:</span></span>
  
- <span data-ttu-id="2097f-143">Wenn die Anzeige des IPConfig-Befehls an der Eingabeaufforderung Zeilen namens "IPv6-Adresse" oder "Temporäre IPv6-Adresse" enthält, müssen Sie in Ihrer Umgebung IPv6.</span><span class="sxs-lookup"><span data-stu-id="2097f-143">If the display of the IPConfig command at the command prompt contains rows named "IPv6 Address" or "Temporary IPv6 Address," you have IPv6 in your environment.</span></span>

- <span data-ttu-id="2097f-144">Wenn alle IPv6-Adressen mit "fe80" beginnen und in Zeilen namens "Verbindungslokale IPv6-Adresse" entsprechen, müssen Sie nicht IPv6 in Ihrer Umgebung.</span><span class="sxs-lookup"><span data-stu-id="2097f-144">If all the IPv6 addresses begin with "fe80" and correspond to rows named "Link-Local IPv6 Address," you don't have IPv6 in your environment.</span></span>

<span data-ttu-id="2097f-145">Die folgenden Überlegungen gelten möglicherweise für Ihr Netzwerk:</span><span class="sxs-lookup"><span data-stu-id="2097f-145">These considerations might apply to your network:</span></span>
  
- <span data-ttu-id="2097f-p109">Der öffentliche Abonnementdienst unterstützt keine Kreditkartenkäufe über IPv6. Dies gilt nicht für die Government Community Cloud (GCC), da Regierungen EA-Lizenzen (Enterprise Agreement) besitzen.</span><span class="sxs-lookup"><span data-stu-id="2097f-p109">The public subscription service does not support purchase by credit card over IPv6. This does not apply to the Government Community Cloud (GCC) because governments have Enterprise Agreement (EA) licensing.</span></span>

- <span data-ttu-id="2097f-148">Einige RMS-Szenarien (Rights Management Services, Rechteverwaltungsdienste) werden von IPv6 nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="2097f-148">IPv6 does not support some Rights Management Services (RMS) scenarios.</span></span>

- <span data-ttu-id="2097f-149">BlackBerry® Enterprise Server (BES) wird von IPv6 nicht unterstützt werden, da BlackBerry IPv6 nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="2097f-149">IPv6 does not support BlackBerry® Enterprise Server (BES) because BlackBerry doesn't support IPv6.</span></span>

<span data-ttu-id="2097f-150">Nachfolgend finden Sie ein kurzer Link, zurückkehren verwendet werden können:[https://aka.ms/o365ip6](https://aka.ms/o365ip6)</span><span class="sxs-lookup"><span data-stu-id="2097f-150">Here's a short link you can use to come back: [https://aka.ms/o365ip6](https://aka.ms/o365ip6)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2097f-151">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="2097f-151">See also</span></span>

[<span data-ttu-id="2097f-152">Microsoft-Technologie-Positionspapier</span><span class="sxs-lookup"><span data-stu-id="2097f-152">Microsoft Technology Position Paper</span></span>](https://go.microsoft.com/fwlink/p/?linkid=525743)
  
[<span data-ttu-id="2097f-153">TCP/IP-v4 und v6</span><span class="sxs-lookup"><span data-stu-id="2097f-153">TCP/IP v4 and v6</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=211898)
  
[<span data-ttu-id="2097f-154">IPv6-Grundlagen</span><span class="sxs-lookup"><span data-stu-id="2097f-154">IPv6 Survival Guide</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=237480)
