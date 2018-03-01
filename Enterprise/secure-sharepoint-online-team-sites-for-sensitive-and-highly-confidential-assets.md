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
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 8c088e88-a9ba-4044-bced-722196f4496d
description: "Zusammenfassung: Wie Contoso den Schutz sensibler Daten und streng vertrauliche SharePoint Online-Teamwebsites für die einfachere, aber dennoch sichere Zusammenarbeit von Führungskräften und Forschungszentren implementierte hat."
ms.openlocfilehash: c615280d39117f68515fb13d4ba83428d73e4fd3
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="secure-sharepoint-online-team-sites-for-sensitive-and-highly-confidential-assets"></a>Sichere SharePoint Online-Teamwebsites für sensible und streng vertrauliche Daten

 **Zusammenfassung:** Wie Contoso den Schutz sensibler Daten und streng vertrauliche SharePoint Online-Teamwebsites für die einfachere, aber dennoch sichere Zusammenarbeit von Führungskräften und Forschungszentren implementierte hat.
  
Die Führungsebene von Contoso möchte Office 365 nutzen und ihre Dateien an einem zentralen Ort speichern, sodass Zusammenarbeit unabhängig vom Aufenthaltsort einer Führungskraft möglich ist. Entsprechend möchten die Forschungsabteilungen von Contoso - mit Vertretungen in Paris, Moskau, New York, Peking und Bangalore - ihre lokalen digitalen Bestände in die Cloud überführen, um leichter darauf zugreifen zu können und eine offenere Zusammenarbeit zwischen Teams zu ermöglichen.
  
Allerdings muss in beiden Fällen der Zugriff auf diese Ressourcen auf die Teilmenge der Personen beschränkt werden, die zum Anzeigen oder Ändern der Ressourcen berechtigt sind, wobei die laufenden Berechtigungen für die Website von den IT-Mitarbeitern verwaltet werden. Darüber hinaus müssen Ressourcen, die absichtlich oder versehentlich verteilt werden, verschlüsselt und mit Berechtigungen versehen sein, um den Zugriff durch Personen zu verhindern, die nicht zum Anzeigen oder Ändern berechtigt sind.
  
Sicherheits- und SharePoint-Administratoren in der IT-Abteilung von Contoso haben sich für den Einsatz des Schutzes sensibler Daten und streng vertraulicher SharePoint Online-Teamwebsites entschieden, wie in Abbildung 1 dargestellt.
  
**Abbildung 1: Schutz sensibler Daten und streng vertrauliche SharePoint Online-Teamwebsites im Vergleich**

![Schutz sensibler Daten und streng vertrauliche SharePoint Online-Teamwebsites](images/Contoso_Poster/SP_Solution.png)
  
Contoso hat die folgenden Schritte ausgeführt, um sichere SharePoint Online-Teamwebsites für die Führungskräfte und Forschungsteams zu erstellen:
  
1. Erstellen einer vertraulichen SharePoint Online-Teamwebsite für **Führungskräfte**
    
    Die neue Teamwebsite verwendet vorhandene Azure Active Directory (AD)-Gruppen für Führungskräfte als Mitglieder mit der SharePoint-Berechtigungsstufe „Bearbeiten“ und eine kleine Gruppe von SharePoint-Administratorkonten als Besitzer mit der Berechtigungsstufe „Vollzugriff“.
    
2. Migrieren der Dateien der Führungskräfte
    
    Vorhandene lokale Dateien und Ordner von Führungskräften werden in die neue SharePoint Online-Teamwebsite für Führungskräfte verschoben.
    
3. Erstellen einer streng vertraulichen SharePoint Online-Teamwebsite für die **Forschung**
    
    Die neue Teamwebsite verwendet vorhandene Azure Active Directory (AD)-Gruppen des Forschungsteams als Mitglieder mit der SharePoint-Berechtigungsstufe „Bearbeiten" und eine kleine Gruppe von SharePoint-Administratorkonten als Besitzer mit der Berechtigungsstufe „Vollzugriff". Durch eine den Forschungsdateien zugewiesene AIP-Bezeichnung wird sichergestellt, dass diese verschlüsselt sind und nur von den Mitgliedern einer Forschungsgruppe geöffnet werden können.
    
4. Migrieren der Forschungsdateien
    
    Vorhandene lokale Dateien und Ordner des Forschungsteams werden in die neue SharePoint Online-Teamwebsite für die Forschung verschoben.
    
Das Ergebnis sind zwei Zusammenarbeitswebsites, deren Zugriff von Sicherheits- und SharePoint-Administratoren streng kontrolliert wird. Dateien mit dem AIP-Bezeichnung „Streng vertraulich" werden auch dann verschlüsselt, wenn sie außerhalb der Forschungs-Teamwebsite verteilt werden, und können nur von einem Mitglied eines Forschungsteams geöffnet werden.
  
Weitere Informationen finden Sie unter [Sichern von SharePoint Online-Websites und -Dateien](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-and-files).
  
 Informationen zum Einrichten dieses Szenarios für eine Demonstration, Machbarkeitsstudie oder zu Entwicklungs-/Testzwecken finden Sie unter[SharePoint Online-Websites in einer Dev/Test-Umgebung](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-dev-test).
  
## <a name="see-also"></a>Siehe auch

[Enterprise-Szenarien für die Contoso Corporation](enterprise-scenarios-for-the-contoso-corporation.md)
  
[Contoso in der Microsoft-Cloud](contoso-in-the-microsoft-cloud.md)
  
[Ressourcen zur Cloud-IT-Architektur von Microsoft](microsoft-cloud-it-architecture-resources.md)

[Stretch-Datenbank](https://msdn.microsoft.com/library/dn935011.aspx)
  
[Microsoft-Roadmap Enterprise Cloud: Ressourcen für IT-Entscheidungsträger](https://sway.com/FJ2xsyWtkJc2taRD)




