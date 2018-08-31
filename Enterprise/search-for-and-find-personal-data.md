---
title: Suchen und Finden personenbezogener Daten
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 2/7/2018
ms.audience: ITPro
ms.topic: overview
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- GDPR
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.custom: ''
ms.assetid: ''
description: Informationen zum Suchen und Finden personenbezogener Daten in Office 365.
ms.openlocfilehash: 8f1a293377570233e4d3ef01da9c56345768828c
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914910"
---
# <a name="search-for-and-find-personal-data"></a><span data-ttu-id="79c92-103">Suchen und Finden personenbezogener Daten</span><span class="sxs-lookup"><span data-stu-id="79c92-103">Search for and find personal data</span></span>

<span data-ttu-id="79c92-104">Personenbezogene Daten sind unter der DSGVO allgemein als Daten definiert, die sich auf eine identifizierte oder identifizierbare natürliche Person beziehen, die Einwohner der Europäischen Union (EU) ist.</span><span class="sxs-lookup"><span data-stu-id="79c92-104">Personal data is defined very broadly under the GDPR as any data that relates to an identified or identifiable natural person that is a resident of the European Union (EU).</span></span>

<span data-ttu-id="79c92-105">Artikel 4: Definitionen</span><span class="sxs-lookup"><span data-stu-id="79c92-105">Article 4 – Definitions</span></span>

> <span data-ttu-id="79c92-106">Als „personenbezogene Daten“ gelten alle Informationen über eine identifizierte oder identifizierbare natürliche Person („betroffene Person“). Eine identifizierbare natürliche Person ist eine Person, die direkt oder indirekt, insbesondere durch Zuordnung zu einer Kennung wie einem Namen, zu einer Kennnummer, zu Standortdaten, zu einer Online-Kennung oder zu einem oder mehreren besonderen Merkmalen identifiziert werden kann, die Ausdruck der physischen, physiologischen, genetischen, psychischen, wirtschaftlichen, kulturellen oder sozialen Identität dieser natürlichen Person sind.</span><span class="sxs-lookup"><span data-stu-id="79c92-106">‘personal data’ means any information relating to an identified or identifiable natural person (‘data subject’); an identifiable natural person is one who can be identified, directly or indirectly, in particular by reference to an identifier such as a name, an identification number, location data, an online identifier or to one or more factors specific to the physical, physiological, genetic, mental, economic, cultural or social identity of that natural person;</span></span>

<span data-ttu-id="79c92-107">In diesem Artikel wird veranschaulicht, wie in SharePoint Online und OneDrive for Business (was die Websites für alle Office 365-Gruppen und Microsoft Teams umfasst) gespeicherte personenbezogene Daten zu finden sind.</span><span class="sxs-lookup"><span data-stu-id="79c92-107">This article demonstrates how to find personal data stored in SharePoint Online and OneDrive for Business (which includes the sites for all Office 365 groups and Microsoft Teams).</span></span>

<span data-ttu-id="79c92-p101">Das Suchen nach personenbezogenen Daten, die der DSGVO unterliegen, basiert auf Typen vertraulicher Informationen in Office 365. Diese definieren, wie bestimmte Informationstypen, z. B. Kreditkartennummern, vom automatisierten Prozess erkannt werden. Derzeit können diese nicht zur Suche nach Daten in ruhenden Exchange-Postfächern verwendet werden. Jedoch können Typen vertraulicher Informationen mit DLP-Richtlinien verwendet werden, um personenbezogene Daten in E-Mails bei der Übertragung zu finden.</span><span class="sxs-lookup"><span data-stu-id="79c92-p101">Finding personal data subject to GDPR relies on using sensitive information types in Office 365. These define how the automated process recognizes specific information types such as health service numbers and credit card numbers. At this time these cannot be used to find data in Exchange mailboxes at rest. However, sensitive information types can be used with data loss prevention policies to find personal data in mail while in transit.</span></span>

<span data-ttu-id="79c92-112">Während Sie also derzeit die Inhaltssuche nicht zur Suche nach personenbezogenen Daten in ruhenden Exchange Online-Postfächern verwenden können, können Sie die Typen vertraulicher Informationen, die Sie für DSGVO zusammenstellen, zur Suche und zum Schutz persönlicher Informationen beim Versenden per E-Mail nutzen.</span><span class="sxs-lookup"><span data-stu-id="79c92-112">So, while you can’t currently use Content Search to find personal data at rest in Exchange Online mailboxes, you can use the sensitive information types you curate for GDPR to find and protect personal information as it is sent through email.</span></span>

## <a name="use-content-search-to-find-personal-data"></a><span data-ttu-id="79c92-113">Verwenden der Inhaltssuche zum Suchen nach personenbezogenen Daten</span><span class="sxs-lookup"><span data-stu-id="79c92-113">Use Content Search to find personal data</span></span>

<span data-ttu-id="79c92-p102">Microsoft empfiehlt einen dreistufigen Ansatz zum Suchen nach personenbezogenen Daten in Office 365. Der Rest des Themas bietet Hilfestellung für jede dieser Stufen.</span><span class="sxs-lookup"><span data-stu-id="79c92-p102">Microsoft recommends a three-stage approach to finding personal data in Office 365. The rest of this topic provides guidance for each of these stages.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="79c92-116"><strong>Schritt</strong></span><span class="sxs-lookup"><span data-stu-id="79c92-116"><strong>Step</strong></span></span></th>
<th align="left"><span data-ttu-id="79c92-117"><strong>Beschreibung</strong></span><span class="sxs-lookup"><span data-stu-id="79c92-117"><strong>Description</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><span data-ttu-id="79c92-118">1. Suchen nach Typen vertraulicher Informationen</span><span class="sxs-lookup"><span data-stu-id="79c92-118">1. Search for sensitive information types</span></span></p></td>
<td align="left"><p><span data-ttu-id="79c92-p103">Verwenden Sie als Erstes Typen vertraulicher Informationen, um personenbezogene Daten zu finden. Erstellen Sie eine Abfrage der Inhaltssuche für jeden Typ vertraulicher Informationen. Führen Sie die Abfrage aus, und analysieren Sie die Ergebnisse.</span><span class="sxs-lookup"><span data-stu-id="79c92-p103">Start by using sensitive information types to find personal data. Create a Content Search query for each sensitive information type. Run the query and analyze the results.</span></span></p>
<span data-ttu-id="79c92-122">Fügen Sie der Abfrage ggf. Parameter hinzu, um die falsch positiven Ergebnisse zu verringern:</span><span class="sxs-lookup"><span data-stu-id="79c92-122">If needed, add parameters to the query to reduce false positives:</span></span> <li><span data-ttu-id="79c92-123">Anzahlbereich</span><span class="sxs-lookup"><span data-stu-id="79c92-123">Count range</span></span></li>
    <li><span data-ttu-id="79c92-124">Konfidenzbereich</span><span class="sxs-lookup"><span data-stu-id="79c92-124">Confidence range</span></span></li>
    <li><span data-ttu-id="79c92-125">Andere Eigenschaften oder Operatoren für komplexere Abfragen</span><span class="sxs-lookup"><span data-stu-id="79c92-125">Other properties or operators for more complex queries</span></span></li>
<p><span data-ttu-id="79c92-126">Ändern Sie ggf. einen Typ vertraulicher Informationen, um die Genauigkeit für Ihre Organisation zu verbessern:</span><span class="sxs-lookup"><span data-stu-id="79c92-126">If necessary, modify a sensitive information type to improve accuracy for your organization:</span></span></p>
<p><li><span data-ttu-id="79c92-127">Passen Sie den Zuverlässigkeitsgrad direkt in den XML-Daten an.</span><span class="sxs-lookup"><span data-stu-id="79c92-127">Adjust the confidence level directly in the XML.</span></span></li></p>
<p><li><span data-ttu-id="79c92-128">Fügen Sie Schlüsselwörter hinzu.</span><span class="sxs-lookup"><span data-stu-id="79c92-128">Add key words.</span></span></li></p>
<p><li><span data-ttu-id="79c92-129">Passen Sie die Näherungsanforderungen für Schlüsselwörter an.</span><span class="sxs-lookup"><span data-stu-id="79c92-129">Adjust the proximity requirements for keywords.</span></span></li></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="79c92-130">2. Verwenden von Keyword Query Language (KQL), um zusätzliche personenbezogene Daten in Ihrer Umgebung zu finden</span><span class="sxs-lookup"><span data-stu-id="79c92-130">2. Use Keyword Query Language (KQL) to find additional personal data in your environment</span></span></p></td>
<td align="left"><p><span data-ttu-id="79c92-131">Für die Suche nach Daten, die nicht in Typen vertraulicher Informationen enthalten sind, erstellen Sie benutzerdefinierte Abfragen mit der Abfragesprache KQL.</span><span class="sxs-lookup"><span data-stu-id="79c92-131">To find data not included in sensitive information types, use the KQL query language to develop custom queries.</span></span></p>
<p><span data-ttu-id="79c92-132">Testen Sie die Ergebnisse dieser Suchvorgänge, und passen Sie die KQL-Abfragezeichenfolge an, bis Sie das erwartete Ergebnis erzielen.</span><span class="sxs-lookup"><span data-stu-id="79c92-132">Test the results of these searches and adjust the KQL query string until you achieve the expected result.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="79c92-133">3. Erstellen neuer benutzerdefinierter Typen vertraulicher Informationen mithilfe der KQL-Abfragen</span><span class="sxs-lookup"><span data-stu-id="79c92-133">3. Create new custom sensitive information types using the KQL queries</span></span></p></td>
<td align="left"><span data-ttu-id="79c92-p104">Nachdem Sie die KQL-Abfragen zum Suchen nach Zieldaten optimiert haben, erstellen Sie neue benutzerdefinierte Typen vertraulicher Informationen mit diesen Abfragen. Sie können diese benutzerdefinierten Typen vertraulicher Informationen dann mit der Inhaltssuche, in DLP-Richtlinien und anderen Tools sowie in anderen KQL-Abfragen verwenden.</span><span class="sxs-lookup"><span data-stu-id="79c92-p104">After optimizing KQL queries to find target data, create new custom sensitive information types using these queries. You can then use these custom sensitive information types with Content Search, in DLP policies and other tools, and within other KQL queries.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="79c92-p105">In Kürze können Sie Typen vertraulicher Informationen auf einer neuen Benutzeroberfläche im Security & Compliance Center erstellen und ändern. Sie können dynamisch die übereinstimmenden Ergebnisse sehen und die Typen vertraulicher Informationen nach Ihren Bedürfnissen optimieren.</span><span class="sxs-lookup"><span data-stu-id="79c92-p105">Coming soon — You'll be able to create and modify sensitive information types in a new user interface in the Security and Compliance Center. You can dynamically see matching results and tune sensitive information types to meet your needs.</span></span>

## <a name="search-for-sensitive-information-types-using-content-search"></a><span data-ttu-id="79c92-138">Suchen nach Typen vertraulicher Informationen mit der Inhaltssuche</span><span class="sxs-lookup"><span data-stu-id="79c92-138">Search for sensitive information types using Content Search</span></span>

<span data-ttu-id="79c92-p106">Beginnen Sie die Suche nach personenbezogenen Daten mit den Typen vertraulicher Informationen, die in Office 365 enthalten sind. Diese sind im Security & Compliance Center unter „Klassifizierung“ aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="79c92-p106">Begin searching for personal data by using the sensitive information types that are included with Office 365. These are listed in the Security and Compliance Center under Classification.</span></span>

<span data-ttu-id="79c92-p107">Dieses Thema enthält eine Liste der aktuellen Typen vertraulicher Informationen, die für Bürger in der Europäischen Union gelten. Verwenden Sie diese als Ausgangspunkt. Überprüfen Sie das Security & Compliance Center häufig auf neue Ergänzungen, die im Zusammenhang mit der DSGVO hilfreich sind.</span><span class="sxs-lookup"><span data-stu-id="79c92-p107">This topic includes a list of current sensitive information types that apply to citizens in the European Union. Use these as a starting point. Check Security and Compliance Center frequently for new additions that can help with GDPR compliance.</span></span>

<span data-ttu-id="79c92-144">Weitere Informationen finden Sie im Artikel: [Liste der Typen vertraulicher Informationen und wonach sie suchen](https://support.office.com/de-DE/article/What-the-sensitive-information-types-look-for-fd505979-76be-4d9f-b459-abef3fc9e86b).</span><span class="sxs-lookup"><span data-stu-id="79c92-144">Also see this article: [List of sensitive information types and what each one looks for](https://support.office.com/de-DE/article/What-the-sensitive-information-types-look-for-fd505979-76be-4d9f-b459-abef3fc9e86b).</span></span>

<span data-ttu-id="79c92-p108">Typen vertraulicher Informationen definieren, wie der automatisierte Prozess bestimmte Informationstypen wie Kreditkartennummern und Bankkontonummern erkennt. Typen vertraulicher Informationen werden auch als Bedingungen bezeichnet. Ein Typ vertraulicher Informationen wird durch ein Muster definiert, das durch einen regulären Ausdruck oder eine Funktion identifiziert werden kann. Darüber hinaus können auch belegende Hinweise wie Schlüsselwörter oder Prüfsummen zum Identifizieren eines Typs vertraulicher Informationen verwendet werden. Zuverlässigkeitsgrad und Näherung werden ebenfalls bei der Auswertung verwendet.</span><span class="sxs-lookup"><span data-stu-id="79c92-p108">Sensitive information types define how the automated process recognizes specific information types such as bank account numbers, health service numbers, and credit card numbers. Sensitive information types are also referred to as conditions. A sensitive information type is defined by a pattern that can be identified by a regular expression or a function. In addition, corroborative evidence such as keywords and checksums can be used to identify a sensitive information type. Confidence level and proximity are also used in the evaluation process.</span></span>

<span data-ttu-id="79c92-150">Zu diesem Zeitpunkt können Typen vertraulicher Informationen nicht zur Suche nach Daten in ruhenden Postfächern verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="79c92-150">At this time sensitive information types cannot be used to find data at rest in mailboxes.</span></span>

### <a name="using-content-search-with-sensitive-information-types"></a><span data-ttu-id="79c92-151">Verwenden der Inhaltssuche mit Typen vertraulicher Informationen</span><span class="sxs-lookup"><span data-stu-id="79c92-151">Using Content Search with sensitive information types</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="79c92-152"><strong>Schritt</strong></span><span class="sxs-lookup"><span data-stu-id="79c92-152"><strong>Step</strong></span></span></th>
<th align="left"><span data-ttu-id="79c92-153"><strong>Weitere Informationen</strong></span><span class="sxs-lookup"><span data-stu-id="79c92-153"><strong>More information</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd"><td align="left"><p><span data-ttu-id="79c92-154">Wechseln zur Inhaltssuche im Security & Compliance Center</span><span class="sxs-lookup"><span data-stu-id="79c92-154">Go to Content Search in the Security and Compliance Center</span></span></p></td>
<td align="left"><p><span data-ttu-id="79c92-155">Klicken Sie im linken Bereich des Security &amp; Compliance Centers auf **Suche &amp; Untersuchung** &gt; **Inhaltssuche**.</span><span class="sxs-lookup"><span data-stu-id="79c92-155">In the left pane of the Security &amp; Compliance Center, click **Search &amp; investigation** &gt; **Content search**.</span></span></p>
<p><span data-ttu-id="79c92-156">Siehe <a href="https://support.office.com/en-us/article/Run-a-Content-Search-in-the-Office-365-Security-Compliance-Center-61852fd9-fe8a-4880-a339-cb19ed3bff4a">Ausführen einer Inhaltssuche im Office 365 Security &amp; Compliance Center</a>.</span><span class="sxs-lookup"><span data-stu-id="79c92-156">See <a href="https://support.office.com/en-us/article/Run-a-Content-Search-in-the-Office-365-Security-Compliance-Center-61852fd9-fe8a-4880-a339-cb19ed3bff4a">Run a Content Search in the Office 365 Security &amp; Compliance Center</a>.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="79c92-157">Erstellen eines neuen Suchelements für jeden Typ vertraulicher Informationen</span><span class="sxs-lookup"><span data-stu-id="79c92-157">Create a new search item for each sensitive information type</span></span></p></td>
<td align="left"><p><span data-ttu-id="79c92-158">Verwenden Sie die folgende Syntax:</span><span class="sxs-lookup"><span data-stu-id="79c92-158">Use the following syntax:</span></span></p>
<blockquote>
<p><span data-ttu-id="79c92-159">SensitiveType:"&lt;Typ&gt;"</span><span class="sxs-lookup"><span data-stu-id="79c92-159">SensitiveType:”&lt;type&gt;”</span></span></p>
</blockquote>
<p><span data-ttu-id="79c92-160">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="79c92-160">For example:</span></span></p>
<blockquote>
<p><span data-ttu-id="79c92-161">SensitiveType:&quot;Französische Reisepassnummer&quot;</span><span class="sxs-lookup"><span data-stu-id="79c92-161">SensitiveType:&quot;France Passport Number&quot;</span></span></p>
</blockquote>
<p><span data-ttu-id="79c92-p109">Beschränken Sie die Suche auf SharePoint (schließt OneDrive for Business ein). Stellen Sie sicher, dass die Syntax genau stimmt und keine zusätzlichen Leerzeichen oder Tippfehler enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="79c92-p109">Scope the search to SharePoint (includes OneDrive for Business). Make sure the syntax is exact and there are no extra spaces or typos.</span></span></p>
<p><span data-ttu-id="79c92-164">Siehe <a href="https://support.office.com/de-DE/article/Form-a-query-to-find-sensitive-data-stored-on-sites-3019fbc5-7f15-4972-8d0e-dc182dc7f836">Erstellen einer Abfrage zum Auffinden auf Websites gespeicherter vertraulicher Daten</a>.</span><span class="sxs-lookup"><span data-stu-id="79c92-164">See <a href="https://support.office.com/de-DE/article/Form-a-query-to-find-sensitive-data-stored-on-sites-3019fbc5-7f15-4972-8d0e-dc182dc7f836">Form a query to find sensitive data stored on sites</a>.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="79c92-165">Überprüfen der Ergebnisse für jede Suche</span><span class="sxs-lookup"><span data-stu-id="79c92-165">Review the results for each search</span></span></p></td>
<td align="left"><p><span data-ttu-id="79c92-166">Suchen Sie nach dieser Art von Problemen, um zu ermitteln, ob die Abfragegenauigkeit eingehalten wird:</span><span class="sxs-lookup"><span data-stu-id="79c92-166">Look for these types of issues to determine if the query accuracy is on target:</span></span></p>
<p><li><span data-ttu-id="79c92-167">Viele falsch positive Ergebnisse</span><span class="sxs-lookup"><span data-stu-id="79c92-167">Many false positives</span></span></li></p>
<p><li><span data-ttu-id="79c92-168">Fehlende bekannte Instanzen von Daten</span><span class="sxs-lookup"><span data-stu-id="79c92-168">Missing known instances of data</span></span></li></p>
<p><span data-ttu-id="79c92-169">Siehe <a href="https://support.office.com/en-us/article/Export-Content-Search-results-from-the-Office-365-Security-Compliance-Center-ed48d448-3714-4c42-85f5-10f75f6a4278">Exportieren der Inhaltssuchergebnisse aus dem Office 365 Security &amp; Compliance Center</a>.</span><span class="sxs-lookup"><span data-stu-id="79c92-169">See <a href="https://support.office.com/en-us/article/Export-Content-Search-results-from-the-Office-365-Security-Compliance-Center-ed48d448-3714-4c42-85f5-10f75f6a4278">Export Content Search results from the Office 365 Security &amp; Compliance Center</a>.</span></span></p>
<p><span data-ttu-id="79c92-170">Hinweis: Wenn Sie Mozilla Firefox oder Chrome verwenden, müssen Sie möglicherweise zuerst Berichte mithilfe von Internet Explorer oder Edge herunterladen, um das erforderliche Add-In installieren zu können.</span><span class="sxs-lookup"><span data-stu-id="79c92-170">Note: if you’re using Mozilla Firefox or Chrome, you might need to first download reports using Internet Explorer or Edge in order to install the required add-in.</span></span></p></td>
</tr>
</tbody>
</table>

## <a name="sensitive-information-types-for-eu-citizen-data"></a><span data-ttu-id="79c92-171">Typen vertraulicher Informationen für Daten von EU-Bürgern</span><span class="sxs-lookup"><span data-stu-id="79c92-171">Sensitive information types for EU citizen data</span></span>

<span data-ttu-id="79c92-p110">Beginnen Sie mit diesen Typen vertraulicher Informationen. In Kürze werden zahlreiche weitere Typen vertraulicher Informationen für personenbezogene Daten in EU-Ländern verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="79c92-p110">Start with these sensitive information types. Many more sensitive information types are coming soon for personal data in EU countries.</span></span>

> <span data-ttu-id="79c92-174">Nationale belgische Nummer</span><span class="sxs-lookup"><span data-stu-id="79c92-174">Belgium National Number</span></span>
>
> <span data-ttu-id="79c92-175">Kreditkartennummer</span><span class="sxs-lookup"><span data-stu-id="79c92-175">Credit Card Number</span></span>
>
> <span data-ttu-id="79c92-176">Kroatische ID-Kartennummer</span><span class="sxs-lookup"><span data-stu-id="79c92-176">Croatia Identity Card Number</span></span>
>
> <span data-ttu-id="79c92-177">Kroatische persönliche ID-Nummer (OIB)</span><span class="sxs-lookup"><span data-stu-id="79c92-177">Croatia Personal Identification (OIB) Number</span></span>
>
> <span data-ttu-id="79c92-178">Nationale tschechische ID-Kartennummer</span><span class="sxs-lookup"><span data-stu-id="79c92-178">Czech National Identity Card Number</span></span>
>
> <span data-ttu-id="79c92-179">Dänische persönliche ID-Nummer</span><span class="sxs-lookup"><span data-stu-id="79c92-179">Denmark Personal Identification Number</span></span>
>
> <span data-ttu-id="79c92-180">EU-Debitkartennummern</span><span class="sxs-lookup"><span data-stu-id="79c92-180">EU Debit Card Number</span></span>
>
> <span data-ttu-id="79c92-181">Nationale finnische ID-Nummer</span><span class="sxs-lookup"><span data-stu-id="79c92-181">Finland National ID</span></span>
>
> <span data-ttu-id="79c92-182">Finnische Reisepassnummer</span><span class="sxs-lookup"><span data-stu-id="79c92-182">Finland Passport Number</span></span>
>
> <span data-ttu-id="79c92-183">Französische Führerscheinnummer</span><span class="sxs-lookup"><span data-stu-id="79c92-183">France Driver's License Number</span></span>
>
> <span data-ttu-id="79c92-184">Französischer Personalausweis (Carte Nationale d'Identité, CNI)</span><span class="sxs-lookup"><span data-stu-id="79c92-184">France National ID Card (CNI)</span></span>
>
> <span data-ttu-id="79c92-185">Französische Reisepassnummer</span><span class="sxs-lookup"><span data-stu-id="79c92-185">France Passport Number</span></span>
>
> <span data-ttu-id="79c92-186">Französische Sozialversicherungsnummer (INSEE)</span><span class="sxs-lookup"><span data-stu-id="79c92-186">France Social Security Number (INSEE)</span></span>
>
> <span data-ttu-id="79c92-187">Deutsche Führerscheinnummer</span><span class="sxs-lookup"><span data-stu-id="79c92-187">German Driver’s License Number</span></span>
>
> <span data-ttu-id="79c92-188">Deutsche Personalausweisnummer</span><span class="sxs-lookup"><span data-stu-id="79c92-188">Germany Identity Card Number</span></span>
>
> <span data-ttu-id="79c92-189">Deutsche Reisepassnummer</span><span class="sxs-lookup"><span data-stu-id="79c92-189">German Passport Number</span></span>
>
> <span data-ttu-id="79c92-190">Nationale griechische ID-Karte</span><span class="sxs-lookup"><span data-stu-id="79c92-190">Greece National ID Card</span></span>
>
> <span data-ttu-id="79c92-191">International Banking Account Number (IBAN)</span><span class="sxs-lookup"><span data-stu-id="79c92-191">International Banking Account Number (IBAN)</span></span>
>
> <span data-ttu-id="79c92-192">IP-Adresse</span><span class="sxs-lookup"><span data-stu-id="79c92-192">IP Address</span></span>
>
> <span data-ttu-id="79c92-193">Irische Sozialversicherungsnummer (PPS, Personal Public Service)</span><span class="sxs-lookup"><span data-stu-id="79c92-193">Ireland Personal Public Service (PPS) Number</span></span>
>
> <span data-ttu-id="79c92-194">Italienische Führerscheinnummer</span><span class="sxs-lookup"><span data-stu-id="79c92-194">Italy’s Driver’s License Number</span></span>
>
> <span data-ttu-id="79c92-195">Niederländische persönliche Identifikationsnummer (BSN, Citizen Service Number)</span><span class="sxs-lookup"><span data-stu-id="79c92-195">Netherlands Citizen’s Service (BSN) Number</span></span>
>
> <span data-ttu-id="79c92-196">Norwegische ID-Nummer</span><span class="sxs-lookup"><span data-stu-id="79c92-196">Norway Identity Number</span></span>
>
> <span data-ttu-id="79c92-197">Polnische Identitätskarte</span><span class="sxs-lookup"><span data-stu-id="79c92-197">Poland Identity Card</span></span>
>
> <span data-ttu-id="79c92-198">Nationale polnische ID-Nummer (PESEL)</span><span class="sxs-lookup"><span data-stu-id="79c92-198">Poland National ID (PESEL)</span></span>
>
> <span data-ttu-id="79c92-199">Polnische Reisepassnummer</span><span class="sxs-lookup"><span data-stu-id="79c92-199">Poland Passport</span></span>
>
> <span data-ttu-id="79c92-200">Portugiesische ID-Kartennummer (Citizen Card)</span><span class="sxs-lookup"><span data-stu-id="79c92-200">Portugal Citizen Card Number</span></span>
>
> <span data-ttu-id="79c92-201">Spanische Sozialversicherungsnummer (SSN)</span><span class="sxs-lookup"><span data-stu-id="79c92-201">Spain Social Security Number (SSN)</span></span>
>
> <span data-ttu-id="79c92-202">Nationale schwedische ID-Nummer</span><span class="sxs-lookup"><span data-stu-id="79c92-202">Sweden National ID</span></span>
>
> <span data-ttu-id="79c92-203">Schwedische Reisepassnummer</span><span class="sxs-lookup"><span data-stu-id="79c92-203">Sweden Passport Number</span></span>
>
> <span data-ttu-id="79c92-p111">UK-Führerscheinnummer</span><span class="sxs-lookup"><span data-stu-id="79c92-p111">U.K. Driver’s License Number</span></span>
>
> <span data-ttu-id="79c92-p112">Wählerverzeichnisnummer aus dem Vereinigten Königreich</span><span class="sxs-lookup"><span data-stu-id="79c92-p112">U.K. Electoral Roll Number</span></span>
>
> <span data-ttu-id="79c92-p113">UK-Gesundheitsdienstnummer</span><span class="sxs-lookup"><span data-stu-id="79c92-p113">U.K. National Health Service Number</span></span>
>
> <span data-ttu-id="79c92-p114">UK-Sozialversicherungsnummer (National Insurance Number, NINO)</span><span class="sxs-lookup"><span data-stu-id="79c92-p114">U.K. National Insurance Number (NINO)</span></span>
>
> <span data-ttu-id="79c92-p115">US-/UK-Reisepassnummer</span><span class="sxs-lookup"><span data-stu-id="79c92-p115">U.S./U.K. Passport Number</span></span>

## <a name="add-parameters-to-a-sensitive-information-type-query-to-hone-the-results"></a><span data-ttu-id="79c92-214">Hinzufügen von Parametern zu einer Abfrage für Typen vertraulicher Informationen, um die Ergebnisse zu verfeinern</span><span class="sxs-lookup"><span data-stu-id="79c92-214">Add parameters to a sensitive information type query to hone the results</span></span>

<span data-ttu-id="79c92-215">Sie können die folgenden Parameter zu einer Abfrage für Typen vertraulicher Informationen hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="79c92-215">You can add these parameters to a sensitive information type query:</span></span>

-   <span data-ttu-id="79c92-216">Anzahlbereich – Die Anzahl von Vorkommen vertraulicher Informationen, die ein Dokument aufweisen muss, damit es in die Abfrageergebnisse einbezogen wird.</span><span class="sxs-lookup"><span data-stu-id="79c92-216">Count range — define the number of occurrences of sensitive information a document needs to contain before it’s included in the query results.</span></span>

-   <span data-ttu-id="79c92-217">Konfidenzbereich – Der Grad an Konfidenz, zu dem der erkannte Typ vertraulicher Informationen ein Treffer ist. Beispiel: 85 (85%).</span><span class="sxs-lookup"><span data-stu-id="79c92-217">Confidence range — the level of confidence that the detected sensitive type is actually a match, such as 85 (85%).</span></span>

<span data-ttu-id="79c92-218">Syntax:</span><span class="sxs-lookup"><span data-stu-id="79c92-218">Syntax:</span></span>

-   <span data-ttu-id="79c92-219">SensitiveType:"\<Typ\>|\<Anzahlbereich\>|\<Konfidenzbereich\>"</span><span class="sxs-lookup"><span data-stu-id="79c92-219">SensitiveType:”\<type\>|\<count range\>|\<confidence range\>”</span></span>

<span data-ttu-id="79c92-220">Beispiele:</span><span class="sxs-lookup"><span data-stu-id="79c92-220">Examples:</span></span>

-   <span data-ttu-id="79c92-221">SensitiveType:"Kreditkartennummer|5" (nur Dokumente zurückgeben, die genau fünf Kreditkartennummern enthalten)</span><span class="sxs-lookup"><span data-stu-id="79c92-221">SensitiveType:“Credit Card Number|5” (return only documents that contain exactly five credit card numbers)</span></span>

-   <span data-ttu-id="79c92-p116">SensitiveType:"Kreditkartennummer|\*|85.." (Konfidenzbereich ist 85 % oder höher)</span><span class="sxs-lookup"><span data-stu-id="79c92-p116">SensitiveType:“Credit Card Number|\*|85..” (confidence range is 85 percent or higher)</span></span>

<span data-ttu-id="79c92-224">Hinweis: Bei "SensitiveType" wird die Groß-/Kleinschreibung beachtet, im Rest der Abfrage jedoch nicht.</span><span class="sxs-lookup"><span data-stu-id="79c92-224">Note: “SensitiveType” is case sensitive, but the rest of the query is not.</span></span>

<span data-ttu-id="79c92-p117">Sie können auch Eigenschaften und Operatoren verwenden, um zu veranschaulichen, wie Sie Abfragen optimieren können. Weitere Informationen und Beispiele finden Sie unter [Erstellen einer Abfrage zum Auffinden auf Websites gespeicherter vertraulicher Daten](https://support.office.com/de-DE/article/Form-a-query-to-find-sensitive-data-stored-on-sites-3019fbc5-7f15-4972-8d0e-dc182dc7f836).</span><span class="sxs-lookup"><span data-stu-id="79c92-p117">You can also use properties, and operators to illustrate how you can refine your queries. For more information and examples, see [Form a query to find sensitive data stored on sites](https://support.office.com/de-DE/article/Form-a-query-to-find-sensitive-data-stored-on-sites-3019fbc5-7f15-4972-8d0e-dc182dc7f836).</span></span>
