---
title: Anwenden von Bezeichnungen auf personenbezogene Daten in Office 365
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
ms.custom: ''
ms.assetid: ''
search.appverid:
- MET150
description: Erfahren Sie, wie Sie Office-Bezeichnungen im Rahmen Ihres DSGVO-Schutzplans verwenden können.
ms.openlocfilehash: c0058a023b807b81df42274d5e8b9408e37d505d
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914930"
---
# <a name="apply-labels-to-personal-data-in-office-365"></a><span data-ttu-id="79ccb-103">Anwenden von Bezeichnungen auf personenbezogene Daten in Office 365</span><span class="sxs-lookup"><span data-stu-id="79ccb-103">Apply labels to personal data in Office 365</span></span>

 <span data-ttu-id="79ccb-p101">Lesen Sie diese Thema, wenn Sie Office-Bezeichnungen im Rahmen Ihres DSGVO-Schutzplans verwenden. Bezeichnungen können derzeit im Office 365 Security & Compliance Center und in Azure Information Protection erstellt werden. Mit der Zeit werden diese Technologien in einer einheitlichen Bezeichnungs- und Klassifikationserfahrung zusammengeführt, damit Sie noch mehr erreichen können.</span><span class="sxs-lookup"><span data-stu-id="79ccb-p101">Use this topic if you are using Office labels as part of your GDPR protection plan. Today labels can be created in the Office 365 Security & Compliance Center and in Azure Information Protection. Over time these technologies will converge into a unified labeling and classification experience and you will be able to achieve even more.</span></span>

<span data-ttu-id="79ccb-p102">Wenn Sie Bezeichnungen zum Schutz personenbezogener Daten in Office 365 verwenden, wird empfohlen, mit Office-Bezeichnungen zu beginnen. Sie können erweiterte Datenkontrolle verwenden, um Bezeichnungen auf Grundlage von vertraulichen Informationstypen und anderen Kriterien automatisch anzuwenden. Office-Bezeichnungen können mit Verhinderung von Datenverlust (DLP) verwendet werden, um Schutz anzuwenden. Sie können in Kürze sowohl Bezeichnungen als auch vertrauliche Informationstypen mit Cloud App Security verwenden, um personenbezogene Daten zu überwachen, die in anderen SaaS-Apps gespeichert sind.</span><span class="sxs-lookup"><span data-stu-id="79ccb-p102">If you are using labels for protection of personal data in Office 365, Microsoft recommends you start with Office labels. You can use Advanced Data Governance to automatically apply labels based on sensitive information types or other criteria. You can use Office labels with data loss prevention to apply protection. You can also use labels with eDiscovery and Content Search. You’ll soon be able to use both labels and sensitive information types with Cloud App Security to monitor personal data that resides in other SaaS apps.</span></span>

<span data-ttu-id="79ccb-p103">Azure Information Protection-Bezeichnungen werden derzeit für das Anwenden von Bezeichnungen auf lokale Dateien und Dateien in anderen Clouddiensten und Anbietern empfohlen. Diese werden auch für Dateien in Office 365 empfohlen, für die die Azure RMS-Verschlüsselung (Azure Rights Management) für Schutz von Daten wie z. B. Dateien mit Betriebsgeheimnissen erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="79ccb-p103">Azure Information Protection labels are currently recommended for applying labels to files on premises and in other cloud services and providers. These are also recommended for files in Office 365 that require Azure Rights Management (Azure RMS) encryption for data protection, such as trade secret files.</span></span>

<span data-ttu-id="79ccb-p104">Zu diesem Zeitpunkt wird die Verwendung von Azure Information Protection zum Anwenden der Azure RMS-Verschlüsselung nicht für Dateien mit Daten in Office 365 empfohlen, die der DSGVO unterliegen. Office 365-Dienste können derzeit RMS-verschlüsselte Dateien nicht lesen. Aus diesem Grund kann der Dienst die vertraulichen Daten in diesen Dateien nicht finden.</span><span class="sxs-lookup"><span data-stu-id="79ccb-p104">At this time, using Azure Information Protection to apply Azure RMS encryption is not recommended for files in Office 365 with data that is subject to the GDPR. Office 365 services currently cannot read into RMS-encrypted files. Therefore, the service can’t find sensitive data in these files.</span></span>

<span data-ttu-id="79ccb-p105">Azure Information Protection-Bezeichnungen können auf E-Mails in Exchange Online angewendet werden und können mit DLP von Office 365 verwendet werden. Mit den in Kürze verfügbaren einheitlichen Klassifikations- und Bezeichnungsmodul können Sie die gleichen Bezeichnungen für E-Mails und Dateien verwenden, darunter automatisches Anwenden von Bezeichnungen auf E-Mails und Schutz von E-Mails während der Übertragung.</span><span class="sxs-lookup"><span data-stu-id="79ccb-p105">Azure Information Protection labels can be applied to mail in Exchange Online and these labels work with Office 365 data loss prevention. Coming soon with the unified classification and labeling engine you will be able to use the same labels for email and files, including automatically labeling and protecting email in transit.</span></span>

![Bezeichnungen in Office 365 und Azure Information Protection](Media/Apply-labels-to-personal-data-in-Office-365-image1.png)

<span data-ttu-id="79ccb-120">In der Abbildung sehen Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="79ccb-120">In the illustration:</span></span>

-   <span data-ttu-id="79ccb-121">Verwenden von Office 365-Bezeichnungen für personenbezogene Daten und streng geregelte Dateien sowie Dateien mit Betriebsgeheimnissen in SharePoint Online und OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="79ccb-121">Use Office 365 labels for personal data and for highly regulated & trade secret files in SharePoint Online and OneDrive for Business.</span></span>

-   <span data-ttu-id="79ccb-122">Verwenden von Azure Information Protection (AIP)-Bezeichnungen für streng geregelte Dateien sowie Dateien mit Betriebsgeheimnissen, Exchange Online-E-Mails, Dateien in anderen SaaS-Diensten, Dateien in lokalen Rechenzentren und Dateien in anderen Cloudanbietern</span><span class="sxs-lookup"><span data-stu-id="79ccb-122">Use Azure Information Protection (AIP) labels for highly regulated & trade secret files, Exchange Online email, files in other SaaS services, files in on-premises datacenters, and files in other cloud providers.</span></span>

-   <span data-ttu-id="79ccb-123">In Kürze verfügbar: beide Arten von Bezeichnungen werden in einer einheitlichen Klassifikations- und Bezeichnungserfahrung zusammengeführt.</span><span class="sxs-lookup"><span data-stu-id="79ccb-123">Coming soon: both types of labels will converge into a unified classification and labeling experience.</span></span>

## <a name="use-office-labels-and-sensitive-information-types-across-microsoft-365-for-information-protection"></a><span data-ttu-id="79ccb-124">Verwenden von Office-Bezeichnungen und vertraulichen Informationstypen in Microsoft 365 zum Schutz von Informationen</span><span class="sxs-lookup"><span data-stu-id="79ccb-124">Use Office labels and sensitive information types across Microsoft 365 for information protection</span></span>

<span data-ttu-id="79ccb-125">Die folgende Abbildung zeigt, wie Office-Bezeichnungen und vertrauliche Informationstypen in Bezeichnungsrichtlinien, DLP-Richtlinien und mit Cloud App Security-Richtlinien verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="79ccb-125">The following illustration shows how Office labels and sensitive information types can be used in label policies, data loss prevention policies, and with Cloud App Security policies.</span></span>

![Office-Bezeichnungen und vertrauliche Informationstypen](Media/Apply-labels-to-personal-data-in-Office-365-image2.png)

<span data-ttu-id="79ccb-127">Für Zwecke der Barrierefreiheit enthält die folgende Tabelle die gleichen Beispiele wie die Abbildung.</span><span class="sxs-lookup"><span data-stu-id="79ccb-127">For accessibility, the following table provides the same examples in the illustration.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="79ccb-128"><strong>Klassifikationselemente</strong></span><span class="sxs-lookup"><span data-stu-id="79ccb-128"><strong>Classification elements</strong></span></span></th>
<th align="left"><span data-ttu-id="79ccb-129"><strong>Bezeichnungsrichtlinien – 2 Beispiele</strong></span><span class="sxs-lookup"><span data-stu-id="79ccb-129"><strong>Label policies — 2 examples</strong></span></span></th>
<th align="left"><span data-ttu-id="79ccb-130"><strong>DLP-Richtlinien – 2 Beispiele</strong></span><span class="sxs-lookup"><span data-stu-id="79ccb-130"><strong>Data loss prevention policies — 2 examples</strong></span></span></th>
<th align="left"><span data-ttu-id="79ccb-131"><strong>Cloud App Security-Richtlinien für alle SaaS-Apps – 1 Beispiel</strong></span><span class="sxs-lookup"><span data-stu-id="79ccb-131"><strong>Cloud App Security policies for all SaaS apps — 1 example</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="79ccb-p106">Office-Bezeichnungen. Beispiele: „Privat“, „Öffentlich“, „Kundendaten“, „Personaldaten“, „Vertraulich“, „Streng vertraulich“</span><span class="sxs-lookup"><span data-stu-id="79ccb-p106">Office labels. Examples: Personal, Public, Customer data, HR data, Confidential, Highly confidential</span></span></td>
<td align="left"><p><span data-ttu-id="79ccb-p107">Diese Bezeichnung automatisch anwenden...</span><span class="sxs-lookup"><span data-stu-id="79ccb-p107">Auto apply this label . . .</span></span></p>
<p><span data-ttu-id="79ccb-137">Kundendaten</span><span class="sxs-lookup"><span data-stu-id="79ccb-137">Customer data</span></span></p>
<p><span data-ttu-id="79ccb-p108">... auf Dokumente, die folgenden vertraulichen Informationstypen entsprechen...</span><span class="sxs-lookup"><span data-stu-id="79ccb-p108">. . . to documents that match these sensitive information types . . .</span></span></p>
<p><span data-ttu-id="79ccb-144">&lt;Liste der Beispiele für vertrauliche Informationstypen&gt;</span><span class="sxs-lookup"><span data-stu-id="79ccb-144">&lt;list of example sensitive information types&gt;</span></span></p></td>
<td align="left"><p><span data-ttu-id="79ccb-p109">Diesen Schutz anwenden...</span><span class="sxs-lookup"><span data-stu-id="79ccb-p109">Apply this protection . . .</span></span></p>
<p><span data-ttu-id="79ccb-148">&lt;Schutz definieren&gt;</span><span class="sxs-lookup"><span data-stu-id="79ccb-148">&lt;define protection&gt;</span></span></p>
<p><span data-ttu-id="79ccb-p110">... auf Dokumente mit dieser Bezeichnung...</span><span class="sxs-lookup"><span data-stu-id="79ccb-p110">. . . to documents with this label . . .</span></span></p>
<p><span data-ttu-id="79ccb-155">Kundendaten</span><span class="sxs-lookup"><span data-stu-id="79ccb-155">Customer data</span></span></p></td>
<td align="left"><p><span data-ttu-id="79ccb-p111">Warnung, wenn Dateien mit diesen Attributen...</span><span class="sxs-lookup"><span data-stu-id="79ccb-p111">Alert when files with these attributes . . .</span></span></p>
<p><span data-ttu-id="79ccb-159">&lt;vordefiniertes PII-Attribut – oder – benutzerdefinierter Ausdruck&gt;</span><span class="sxs-lookup"><span data-stu-id="79ccb-159">&lt;predefined PII attribute -or- custom expression&gt;</span></span></p>
<p><span data-ttu-id="79ccb-p112">... in einer beliebigen genehmigten SaaS-App außerhalb der Organisation freigegeben werden</span><span class="sxs-lookup"><span data-stu-id="79ccb-p112">. . . in any sanctioned SaaS app are shared outside the organization</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="79ccb-p113">Vertrauliche Informationstypen. Beispiele: Nationale belgische Nummer, Kreditkartennummer, Kroatische ID-Kartennummer, nationale finnische ID-Nummer</span><span class="sxs-lookup"><span data-stu-id="79ccb-p113">Sensitive information types. Examples: Belgium National Number, Credit Card Number, Croatia Identity Cart Number, Finland National ID</span></span></td>
<td align="left"><p><span data-ttu-id="79ccb-p114">Diese Bezeichnungen für Benutzer zum manuellen Anwenden veröffentlichen...</span><span class="sxs-lookup"><span data-stu-id="79ccb-p114">Publish these labels for users to manually apply . . .</span></span></p>
<p><span data-ttu-id="79ccb-169">&lt;Bezeichnungen wählen&gt;</span><span class="sxs-lookup"><span data-stu-id="79ccb-169">&lt;select labels&gt;</span></span></p>
<p><span data-ttu-id="79ccb-p115">... für diese Speicherorte...</span><span class="sxs-lookup"><span data-stu-id="79ccb-p115">. . . to these locations . . .</span></span></p>
<p><span data-ttu-id="79ccb-176">&lt;alle Speicherorte oder bestimmte Speicherorte wählen&gt;</span><span class="sxs-lookup"><span data-stu-id="79ccb-176">&lt;all locations or choose specific locations&gt;</span></span></p></td>
<td align="left"><p><span data-ttu-id="79ccb-p116">Diesen Schutz anwenden...</span><span class="sxs-lookup"><span data-stu-id="79ccb-p116">Apply this protection . . .</span></span></p>
<p><span data-ttu-id="79ccb-180">&lt;Schutz definieren&gt;</span><span class="sxs-lookup"><span data-stu-id="79ccb-180">&lt;define protection&gt;</span></span></p>
<p><span data-ttu-id="79ccb-p117">... auf Dokumente, die folgenden vertraulichen Informationstypen entsprechen&gt;</span><span class="sxs-lookup"><span data-stu-id="79ccb-p117">. . . to documents that match these sensitive information types&gt;</span></span></p></td>
<td align="left"><span data-ttu-id="79ccb-185">Hinweis: In Kürze in Cloud App Security verfügbare Attribute beinhalten vertrauliche Informationstypen in Office 365 und einheitliche Bezeichnungen für Office 365 und Azure Information Protection.</span><span class="sxs-lookup"><span data-stu-id="79ccb-185">Note: Attributes coming soon to Cloud App Security include Office 365 sensitive information types and Unified labels across Office 365 and Azure Information Protection.</span></span></td>
</tr>
</tbody>
</table>

## <a name="prioritize-auto-apply-label-policies"></a><span data-ttu-id="79ccb-186">Priorisieren automatisch angewendeter Bezeichnungsrichtlinien</span><span class="sxs-lookup"><span data-stu-id="79ccb-186">Prioritize auto-apply label policies</span></span>

<span data-ttu-id="79ccb-p118">Für personenbezogene Daten, die der DSGVO unterliegen, wird empfohlen, Bezeichnungen automatisch anzuwenden, indem vertrauliche Informationstypen verwendet werden, die Sie für Ihre Umgebung bereitgestellt haben. Es ist wichtig, dass Richtlinien für das automatische Anwenden von Bezeichnungen gut konzipiert und getestet wurden, damit ein beabsichtigtes Verhalten auftritt.</span><span class="sxs-lookup"><span data-stu-id="79ccb-p118">For personal data that is subject to GDPR, Microsoft recommends auto-applying labels by using the sensitive information types you curated for your environment. It is important that auto-apply label policies are well designed and tested to ensure the intended behavior occurs.</span></span>

<span data-ttu-id="79ccb-p119">Die Reihenfolge, in der automatisch anzuwendende Richtlinien erstellt werden, sowie, ob Benutzer diese Bezeichnungen auch anwenden, wirkt sich auf das Ergebnis aus. Es ist als wichtig, die Einführung sorgfältig zu planen. Folgendes müssen Sie dazu wissen.</span><span class="sxs-lookup"><span data-stu-id="79ccb-p119">The order that auto-apply policies are created and whether users are also applying these labels affect the result. So, it is important to carefully plan the roll-out. Here’s what you need to know.</span></span>

### <a name="one-label-at-a-time"></a><span data-ttu-id="79ccb-191">Jeweils nur eine Bezeichnung</span><span class="sxs-lookup"><span data-stu-id="79ccb-191">One label at a time</span></span>

<span data-ttu-id="79ccb-192">Sie können einem Dokument jeweils nur eine Bezeichnung zuweisen.</span><span class="sxs-lookup"><span data-stu-id="79ccb-192">You can only assign one label to a document.</span></span>

### <a name="older-auto-apply-policies-win"></a><span data-ttu-id="79ccb-193">Ältere automatisch anzuwendende Richtlinien gelten zuerst</span><span class="sxs-lookup"><span data-stu-id="79ccb-193">Older auto-apply policies win</span></span>

<span data-ttu-id="79ccb-p120">Wenn es mehrere Regeln gibt, die eine automatisch anzuwendende Bezeichnung zuweisen, und der Inhalt die Bedingungen für mehrere Regeln erfüllt, wird die Bezeichnung für die älteste Regel zugewiesen. Aus diesem Grund ist es wichtig, die Richtlinien für Bezeichnungen sorgfältig zu planen, bevor Sie diese konfigurieren. Wenn für eine Organisation eine Änderung der Priorität der Richtlinien für Bezeichnungen erforderlich ist, müssen die Richtlinien gelöscht und erneut erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="79ccb-p120">If there are multiple rules that assign an auto-apply label and content meets the conditions of multiple rules, the label for the oldest rule is assigned. For this reason, it is important to plan the label policies carefully before configuring them. If an organization requires a change to the priority of the label policies, they will need to delete and recreate them.</span></span>

### <a name="manual-user-applied-labels-trump-auto-applied-labels"></a><span data-ttu-id="79ccb-197">Manuell von Benutzern angewendete Bezeichnungen sind wichtiger als automatisch angewendete Bezeichnungen</span><span class="sxs-lookup"><span data-stu-id="79ccb-197">Manual user-applied labels trump auto-applied labels</span></span>

<span data-ttu-id="79ccb-p121">Manuell von Benutzern angewendete Bezeichnungen sind wichtiger als automatisch angewendete Bezeichnungen. Richtlinien für automatisches Anwenden können keine Bezeichnung ersetzen, die bereits von einem Benutzer angewendet wurde. Benutzer können Bezeichnungen ersetzen, die automatisch angewendet wurden.</span><span class="sxs-lookup"><span data-stu-id="79ccb-p121">Manual user applied labels trump auto-applied labels. Auto-apply policies cannot replace a label that is already applied by a user. Users can replace labels that are auto-applied.</span></span>

### <a name="auto-assigned-labels-can-be-updated"></a><span data-ttu-id="79ccb-201">Automatisch zugewiesene Bezeichnungen können aktualisiert werden</span><span class="sxs-lookup"><span data-stu-id="79ccb-201">Auto-assigned labels can be updated</span></span>

<span data-ttu-id="79ccb-202">Automatisch zugewiesene Bezeichnungen können entweder durch neuere Bezeichnungsrichtlinien oder durch Aktualisierungen vorhandener Richtlinien aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="79ccb-202">Auto-assigned labels can be updated by either newer label policies or by updates to existing policies.</span></span>

<span data-ttu-id="79ccb-203">Achten Sie darauf, dass Ihr Plan für die Implementierung von Bezeichnungen Folgendes umfasst:</span><span class="sxs-lookup"><span data-stu-id="79ccb-203">Be sure your plan for implementing labels includes:</span></span>

-   <span data-ttu-id="79ccb-204">Priorisieren der Reihenfolge, in der automatisch angewendete Richtlinien erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="79ccb-204">Prioritizing the order that auto-apply policies are created.</span></span>

-   <span data-ttu-id="79ccb-p122">Ausreichend Zeit für das automatische Anwenden von Bezeichnungen, bevor diese für das manuelle Anwenden für Benutzer bereitgestellt werden. Es kann bis zu sieben Tage dauern, bis die Bezeichnungen auf alle Inhalte angewendet werden, die die Bedingungen erfüllen.</span><span class="sxs-lookup"><span data-stu-id="79ccb-p122">Allowing enough time for labels to be automatically applied before rolling these out for users to manually apply. It can take up to seven days for the labels to be applied to all content that matches the conditions.</span></span>

### <a name="example-priority-for-creating-the-auto-apply-policies"></a><span data-ttu-id="79ccb-207">Beispiel für Priorität für das Erstellen von automatisch angewendeten Richtlinien</span><span class="sxs-lookup"><span data-stu-id="79ccb-207">Example priority for creating the auto-apply policies</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="79ccb-208"><strong>Bezeichnungen</strong></span><span class="sxs-lookup"><span data-stu-id="79ccb-208"><strong>Labels</strong></span></span></th>
<th align="left"><span data-ttu-id="79ccb-209"><strong>Prioritätsreihenfolge beim Erstellen von automatisch angewendeten Richtlinien</strong></span><span class="sxs-lookup"><span data-stu-id="79ccb-209"><strong>Priority order to create auto-apply policies</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="79ccb-210">Personaldaten – Mitarbeiterdaten</span><span class="sxs-lookup"><span data-stu-id="79ccb-210">Human Resources — Employee Data</span></span></td>
<td align="left"><span data-ttu-id="79ccb-211">1</span><span class="sxs-lookup"><span data-stu-id="79ccb-211">1</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="79ccb-212">Kundendaten</span><span class="sxs-lookup"><span data-stu-id="79ccb-212">Customer Data</span></span></td>
<td align="left"><span data-ttu-id="79ccb-213">2</span><span class="sxs-lookup"><span data-stu-id="79ccb-213">2</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="79ccb-214">Streng vertraulich</span><span class="sxs-lookup"><span data-stu-id="79ccb-214">Highly Confidential</span></span></td>
<td align="left"><span data-ttu-id="79ccb-215">3</span><span class="sxs-lookup"><span data-stu-id="79ccb-215">3</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="79ccb-216">Personaldaten – Gehaltsdaten</span><span class="sxs-lookup"><span data-stu-id="79ccb-216">Human Resources — Salary Data</span></span></td>
<td align="left"><span data-ttu-id="79ccb-217">4</span><span class="sxs-lookup"><span data-stu-id="79ccb-217">4</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="79ccb-218">Vertraulich</span><span class="sxs-lookup"><span data-stu-id="79ccb-218">Confidential</span></span></td>
<td align="left"><span data-ttu-id="79ccb-219">5</span><span class="sxs-lookup"><span data-stu-id="79ccb-219">5</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="79ccb-220">Öffentlich</span><span class="sxs-lookup"><span data-stu-id="79ccb-220">Public</span></span></td>
<td align="left"><span data-ttu-id="79ccb-221">6</span><span class="sxs-lookup"><span data-stu-id="79ccb-221">6</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="79ccb-222">Privat</span><span class="sxs-lookup"><span data-stu-id="79ccb-222">Personal</span></span></td>
<td align="left"><span data-ttu-id="79ccb-223">Keine automatisch angewendete Richtlinie</span><span class="sxs-lookup"><span data-stu-id="79ccb-223">No auto-apply policy</span></span></td>
</tr>
</tbody>
</table>

## <a name="create-labels-and-auto-apply-label-policies"></a><span data-ttu-id="79ccb-224">Erstellen von Bezeichnungen und automatisch angewendeten Bezeichnungsrichtlinien</span><span class="sxs-lookup"><span data-stu-id="79ccb-224">Create labels and auto-apply label policies</span></span>

<span data-ttu-id="79ccb-225">Erstellen Sie Bezeichnungen und Richtlinien im Office 365 Security & Compliance Center.</span><span class="sxs-lookup"><span data-stu-id="79ccb-225">Create labels and policies in the Security & Compliance Center.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="79ccb-226"><strong>Schritt</strong></span><span class="sxs-lookup"><span data-stu-id="79ccb-226"><strong>Step</strong></span></span></th>
<th align="left"><span data-ttu-id="79ccb-227"><strong>Beschreibung</strong></span><span class="sxs-lookup"><span data-stu-id="79ccb-227"><strong>Description</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><span data-ttu-id="79ccb-228">Gewähren von Berechtigungen für Mitglieder Ihres Complianceteams</span><span class="sxs-lookup"><span data-stu-id="79ccb-228">Give permissions to members of your compliance team.</span></span></p></td>
<td align="left"><p><span data-ttu-id="79ccb-p123">Mitglieder Ihres Complianceteams, die Bezeichnungen erstellen möchten, benötigen Berechtigungen für die Verwendung des Security &amp; Compliance Centers. Wechseln Sie im Security & Compliance Center zu „Berechtigungen“. und ändern Sie die Mitglieder der Gruppe „Complianceadministrator“.</span><span class="sxs-lookup"><span data-stu-id="79ccb-p123">Members of your compliance team who will create labels need permissions to use the Security &amp; Compliance Center. Go to Permissions in Security and Compliance Center and modify the members of the Compliance Administrator group.</span></span></p>
<p><span data-ttu-id="79ccb-231">Weitere Informationen finden Sie unter <a href="https://support.office.com/en-ie/article/Give-users-access-to-the-Office-365-Security-Compliance-Center-2cfce2c8-20c5-47f9-afc4-24b059c1bd76">Freigeben des Benutzerzugriffs auf das Office 365 Security &amp; Compliance Center</a></span><span class="sxs-lookup"><span data-stu-id="79ccb-231">See <a href="https://support.office.com/en-ie/article/Give-users-access-to-the-Office-365-Security-Compliance-Center-2cfce2c8-20c5-47f9-afc4-24b059c1bd76">Give users access to the Office 365 Security &amp; Compliance Center</a>.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="79ccb-232">Erstellen von Office-Bezeichnungen</span><span class="sxs-lookup"><span data-stu-id="79ccb-232">Create Office labels.</span></span></p></td>
<td align="left"><span data-ttu-id="79ccb-233">Wechseln Sie im Security & Compliance Center zu „Klassifizierungen“, wählen Sie „Bezeichnungen“, und erstellen Sie die Bezeichnungen für Ihre Umgebung.</span><span class="sxs-lookup"><span data-stu-id="79ccb-233">Go to Classifications in Security and Compliance Center, choose Labels, and create the labels for your environment.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="79ccb-234">Erstellen automatisch angewendeter Richtlinien für Bezeichnungen</span><span class="sxs-lookup"><span data-stu-id="79ccb-234">Create auto-apply policies for labels.</span></span></p></td>
<td align="left"><span data-ttu-id="79ccb-p124">Wechseln Sie im Security & Compliance Center zu „Klassifizierung“, wählen Sie „Bezeichnungsrichtlinien“, und erstellen Sie Richtlinien für automatisch angewendete Bezeichnungen. Vergewissern Sie sich, dass Sie diese Richtlinien in der entsprechenden Reihenfolge erstellen.</span><span class="sxs-lookup"><span data-stu-id="79ccb-p124">Go to Classification in Security and Compliance Center, choose Label policies, and create the policies for auto-applying labels. Be sure to create these policies in the prioritized order.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="79ccb-237">Die folgende Abbildung zeigt, wie Sie eine automatisch angewendete Bezeichnung für die Bezeichnung „Kundendaten“ erstellen können.</span><span class="sxs-lookup"><span data-stu-id="79ccb-237">The following illustration shows how to create an auto-apply label for the Customer data label.</span></span>

![Erstellen und Anwenden einer Bezeichnung für Kundendaten](Media/Apply-labels-to-personal-data-in-Office-365-image3.png)

<span data-ttu-id="79ccb-239">In der Abbildung sehen Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="79ccb-239">In the illustration:</span></span>

-   <span data-ttu-id="79ccb-240">Die Bezeichnung „Kundendaten“ wird erstellt.</span><span class="sxs-lookup"><span data-stu-id="79ccb-240">The “Customer data” label is created.</span></span>

-   <span data-ttu-id="79ccb-241">Die gewünschten vertraulichen Informationstypen für die DSGVO werden aufgeführt: Nationale belgische Nummer, Kreditkartennummer, Kroatische ID-Kartennummer, nationale finnische ID-Nummer.</span><span class="sxs-lookup"><span data-stu-id="79ccb-241">The desired sensitive information types for GDPR are listed: Belgium National Number, Credit Card Number, Croatia Identity Card Number, Finland National ID.</span></span>

-   <span data-ttu-id="79ccb-242">Erstellen einer automatisch angewendeten Richtlinie, die die Bezeichnung „Kundendaten“ jeder Datei zuweist, die einen der vertraulichen Informationstypen enthält, die der Richtlinie hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="79ccb-242">Create an auto-apply policy assigns the label “Customer data” to any file that includes one of the sensitive information types that you add to the policy.</span></span>
