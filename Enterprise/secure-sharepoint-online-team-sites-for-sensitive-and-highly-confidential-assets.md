---
title: "Sichere SharePoint Online-Teamwebsites für sensible und streng vertrauliche Daten"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 8c088e88-a9ba-4044-bced-722196f4496d
description: "Zusammenfassung: Wie Contoso den Schutz sensibler Daten und streng vertrauliche SharePoint Online-Teamwebsites für die einfachere, aber dennoch sichere Zusammenarbeit von Führungskräften und Forschungszentren implementierte hat."
ms.openlocfilehash: 1574babb54bfcb3fd74fb8ce4f31c364bb96b14a
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2017
---
# <a name="secure-sharepoint-online-team-sites-for-sensitive-and-highly-confidential-assets"></a><span data-ttu-id="2d05f-103">Sichere SharePoint Online-Teamwebsites für sensible und streng vertrauliche Daten</span><span class="sxs-lookup"><span data-stu-id="2d05f-103">Secure SharePoint Online team sites for sensitive and highly confidential assets</span></span>

 <span data-ttu-id="2d05f-104">**Zusammenfassung:** Wie Contoso den Schutz sensibler Daten und streng vertrauliche SharePoint Online-Teamwebsites für die einfachere, aber dennoch sichere Zusammenarbeit von Führungskräften und Forschungszentren implementierte hat.</span><span class="sxs-lookup"><span data-stu-id="2d05f-104">**Summary:** How Contoso implemented sensitive protection and highly confidential SharePoint Online team sites for easier, yet secure, collaboration for executives and its research centers..</span></span>
  
<span data-ttu-id="2d05f-p101">Die Führungsebene von Contoso möchte Office 365 nutzen und ihre Dateien an einem zentralen Ort speichern, sodass Zusammenarbeit unabhängig vom Aufenthaltsort einer Führungskraft möglich ist. Entsprechend möchten die Forschungsabteilungen von Contoso - mit Vertretungen in Paris, Moskau, New York, Peking und Bangalore - ihre lokalen digitalen Bestände in die Cloud überführen, um leichter darauf zugreifen zu können und eine offenere Zusammenarbeit zwischen Teams zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="2d05f-p101">The executive leadership of Contoso want to use Office 365 and store their files in a single location for collaboration, regardless of where an executive might be. Similarly, Contoso's research departments—with divisions in Paris, Moscow, New York, Beijing, and Bangalore—would like to transition their on-premises digital assets to the cloud for easier access and more open collaboration across teams.</span></span>
  
<span data-ttu-id="2d05f-p102">Allerdings muss in beiden Fällen der Zugriff auf diese Ressourcen auf die Teilmenge der Personen beschränkt werden, die zum Anzeigen oder Ändern der Ressourcen berechtigt sind, wobei die laufenden Berechtigungen für die Website von den IT-Mitarbeitern verwaltet werden. Darüber hinaus müssen Ressourcen, die absichtlich oder versehentlich verteilt werden, verschlüsselt und mit Berechtigungen versehen sein, um den Zugriff durch Personen zu verhindern, die nicht zum Anzeigen oder Ändern berechtigt sind.</span><span class="sxs-lookup"><span data-stu-id="2d05f-p102">However, in both of these cases, access to these resources must be restricted to the subset of people who are allowed to view or change them, with ongoing permissions for the site administered by IT staff. Additionally, even if some resources are intentionally or unintentionally distributed, they must be encrypted and have permissions to prevent those who do not have access to view or change their contents.</span></span>
  
<span data-ttu-id="2d05f-109">Sicherheits- und SharePoint-Administratoren in der IT-Abteilung von Contoso haben sich für den Einsatz des Schutzes sensibler Daten und streng vertraulicher SharePoint Online-Teamwebsites entschieden, wie in Abbildung 1 dargestellt.</span><span class="sxs-lookup"><span data-stu-id="2d05f-109">Security and SharePoint administrators in Contoso's IT department decided to use sensitive protection and highly-confidential SharePoint Online team sites, as shown in Figure 1.</span></span>
  
<span data-ttu-id="2d05f-110">**Abbildung 1: Schutz sensibler Daten und streng vertrauliche SharePoint Online-Teamwebsites im Vergleich**</span><span class="sxs-lookup"><span data-stu-id="2d05f-110">**Figure 1: Comparison of sensitive protection and highly confidential SharePoint Online team sites**</span></span>

![Schutz sensibler Daten und streng vertrauliche SharePoint Online-Teamwebsites](images/Contoso_Poster/SP_Solution.png)
  
<span data-ttu-id="2d05f-112">Contoso hat die folgenden Schritte ausgeführt, um sichere SharePoint Online-Teamwebsites für die Führungskräfte und Forschungsteams zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="2d05f-112">Contoso used these steps to create secure SharePoint Online team sites for their executives and research teams:</span></span>
  
1. <span data-ttu-id="2d05f-113">Erstellen einer vertraulichen SharePoint Online-Teamwebsite für **Führungskräfte**</span><span class="sxs-lookup"><span data-stu-id="2d05f-113">Create an **Executives** sensitive SharePoint Online team site</span></span>
    
    <span data-ttu-id="2d05f-114">Die neue Teamwebsite verwendet vorhandene Azure Active Directory (AD)-Gruppen für Führungskräfte als Mitglieder mit der SharePoint-Berechtigungsstufe „Bearbeiten“ und eine kleine Gruppe von SharePoint-Administratorkonten als Besitzer mit der Berechtigungsstufe „Vollzugriff“.</span><span class="sxs-lookup"><span data-stu-id="2d05f-114">The new team site uses existing Azure Active Directory (AD) groups for executives as members with the Edit SharePoint permission level and a small set of SharePoint administrator accounts as owners with the Full Control permission level.</span></span>
    
2. <span data-ttu-id="2d05f-115">Migrieren der Dateien der Führungskräfte</span><span class="sxs-lookup"><span data-stu-id="2d05f-115">Migrate executives files</span></span>
    
    <span data-ttu-id="2d05f-116">Vorhandene lokale Dateien und Ordner von Führungskräften werden in die neue SharePoint Online-Teamwebsite für Führungskräfte verschoben.</span><span class="sxs-lookup"><span data-stu-id="2d05f-116">Move existing on-premises executive files and folders to the new Executives SharePoint Online team site.</span></span>
    
3. <span data-ttu-id="2d05f-117">Erstellen einer streng vertraulichen SharePoint Online-Teamwebsite für die **Forschung**</span><span class="sxs-lookup"><span data-stu-id="2d05f-117">Create a **Research** highly confidential SharePoint Online team site</span></span>
    
    <span data-ttu-id="2d05f-p103">Die neue Teamwebsite verwendet vorhandene Azure Active Directory (AD)-Gruppen des Forschungsteams als Mitglieder mit der SharePoint-Berechtigungsstufe „Bearbeiten" und eine kleine Gruppe von SharePoint-Administratorkonten als Besitzer mit der Berechtigungsstufe „Vollzugriff". Durch eine den Forschungsdateien zugewiesene AIP-Bezeichnung wird sichergestellt, dass diese verschlüsselt sind und nur von den Mitgliedern einer Forschungsgruppe geöffnet werden können.</span><span class="sxs-lookup"><span data-stu-id="2d05f-p103">The new team site uses existing Azure AD research team groups as members with the Edit permission level and a small set of SharePoint administrator accounts as owners with the Full Control permission level. An AIP label assigned to research files ensures that they are encrypted and only members of a research group can open them.</span></span>
    
4. <span data-ttu-id="2d05f-120">Migrieren der Forschungsdateien</span><span class="sxs-lookup"><span data-stu-id="2d05f-120">Migrate research files</span></span>
    
    <span data-ttu-id="2d05f-121">Vorhandene lokale Dateien und Ordner des Forschungsteams werden in die neue SharePoint Online-Teamwebsite für die Forschung verschoben.</span><span class="sxs-lookup"><span data-stu-id="2d05f-121">Move existing research team on-premises files and folders to the new Research SharePoint Online team site.</span></span>
    
<span data-ttu-id="2d05f-p104">Das Ergebnis sind zwei Zusammenarbeitswebsites, deren Zugriff von Sicherheits- und SharePoint-Administratoren streng kontrolliert wird. Dateien mit dem AIP-Bezeichnung „Streng vertraulich" werden auch dann verschlüsselt, wenn sie außerhalb der Forschungs-Teamwebsite verteilt werden, und können nur von einem Mitglied eines Forschungsteams geöffnet werden.</span><span class="sxs-lookup"><span data-stu-id="2d05f-p104">The result is two collaboration sites whose access is tightly controlled by security and SharePoint administrators. For files with the Highly Confidential AIP label, even if they are distributed outside the Research team site, they are encrypted and can only be opened by a member of a research team.</span></span>
  
<span data-ttu-id="2d05f-124">Weitere Informationen finden Sie unter [Sichern von SharePoint Online-Websites und -Dateien]((https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-and-files)).</span><span class="sxs-lookup"><span data-stu-id="2d05f-124">For more information, see [Secure SharePoint Online sites and files]((https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-and-files)).</span></span>
  
 <span data-ttu-id="2d05f-125">Informationen zum Einrichten dieses Szenarios für eine Demonstration, Machbarkeitsstudie oder zu Entwicklungs-/Testzwecken finden Sie unter[SharePoint Online-Websites in einer Dev/Test-Umgebung]((https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-dev-test)).</span><span class="sxs-lookup"><span data-stu-id="2d05f-125">To set this up for demonstration, proof-of-concept, or dev/test, see[Secure SharePoint Online sites in a dev/test environment]((https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-dev-test)).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2d05f-126">Weitere Artikel</span><span class="sxs-lookup"><span data-stu-id="2d05f-126">See Also</span></span>

[<span data-ttu-id="2d05f-127">Enterprise-Szenarien für die Contoso Corporation</span><span class="sxs-lookup"><span data-stu-id="2d05f-127">Enterprise scenarios for the Contoso Corporation</span></span>](enterprise-scenarios-for-the-contoso-corporation.md)
  
[<span data-ttu-id="2d05f-128">Contoso in der Microsoft-Cloud</span><span class="sxs-lookup"><span data-stu-id="2d05f-128">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="2d05f-129">Ressourcen zur Cloud-IT-Architektur von Microsoft</span><span class="sxs-lookup"><span data-stu-id="2d05f-129">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

<span data-ttu-id="2d05f-130">[Stretch-Datenbank]((https://msdn.microsoft.com/library/dn935011.aspx))</span><span class="sxs-lookup"><span data-stu-id="2d05f-130">[Stretch Database]((https://msdn.microsoft.com/library/dn935011.aspx))</span></span>
  
<span data-ttu-id="2d05f-131">[Microsoft-Roadmap Enterprise Cloud: Ressourcen für IT-Entscheidungsträger]((https://sway.com/FJ2xsyWtkJc2taRD))</span><span class="sxs-lookup"><span data-stu-id="2d05f-131">[Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers]((https://sway.com/FJ2xsyWtkJc2taRD))</span></span>




