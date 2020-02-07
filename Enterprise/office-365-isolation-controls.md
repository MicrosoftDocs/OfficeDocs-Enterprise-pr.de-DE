---
title: Isolierungssteuerungen in Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: 'Zusammenfassung: eine Erläuterung der Isolierungs Steuerelemente in Office 365.'
ms.openlocfilehash: e5ce9f2b581c49f3c08803034bc526b2fdb91a9a
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844446"
---
# <a name="office-365-isolation-controls"></a>Isolierungssteuerungen in Office 365 

Microsoft arbeitet kontinuierlich daran, sicherzustellen, dass die mehrmandantenfähige Architektur von Office 365 auf Unternehmensebene Sicherheit, Vertraulichkeit, Datenschutz, Integrität, lokale, internationale und Verfügbarkeits [Standards](https://www.microsoft.com/TrustCenter/Compliance?service=Office#Icons)unterstützt. Die Größe und der Umfang der von Microsoft bereitgestellten Dienste machen es schwierig und nicht wirtschaftlich, Office 365 mit bedeutender menschlicher Interaktion zu verwalten. Office 365 Dienste werden über mehrere global verteilte Rechenzentren bereitgestellt, die jeweils hoch automatisiert sind und nur wenige Vorgänge erfordern, die einen menschlichen Touch oder Zugriff auf Kunden Inhalte benötigen. Unsere Mitarbeiter unterstützen diese Dienste und Rechenzentren mithilfe von automatisierten Tools und hochgradig sicherem Remotezugriff. Einige Details darüber, wie umfangreiche Dienste in Office 365 betrieben werden, finden Sie unter [a Behind the Scenes Blick auf Office 365 für IT-Experten](https://channel9.msdn.com/Events/SharePoint-Conference/2014/SPC202).

Office 365 besteht aus mehreren Diensten, die wichtige Geschäftsfunktionen bereitstellen und zur gesamten Office 365 Erfahrung beitragen. Jeder dieser Dienste ist in sich geschlossen und für die Integration in einen anderen Dienst konzipiert.

Office 365 ist mit den folgenden Prinzipien konzipiert:

 - ** [Dienstorientierte Architektur](https://msdn.microsoft.com/library/aa480021.aspx):** entwerfen und entwickeln von Software in Form von interoperablen Diensten, die eine klar definierte Geschäftsfunktionalität bieten.
 - **[Operational Security Assurance](https://www.microsoft.com/download/details.aspx?id=40872):** ein Framework, in dem das Wissen über die verschiedenen Funktionen von Microsoft integriert wird, einschließlich des Microsoft- [Sicherheits Entwicklungslebenszyklus](https://www.microsoft.com/sdl/default.aspx), des [Microsoft Security Response Centers](https://technet.microsoft.com/library/dn440717.aspx)und des tiefen Bewusstseins für die Cyber-Bedrohungslandschaft.

Office 365 Dienste arbeiten untereinander zusammen, werden jedoch so konzipiert und implementiert, dass Sie unabhängig voneinander als autonome Dienste bereitgestellt und betrieben werden können. Microsoft trennt Aufgaben und Zuständigkeitsbereiche für Office 365 aus, um die Möglichkeiten für die unbefugte oder unbeabsichtigte Änderung oder den Missbrauch von Ressourcen der Organisation zu verringern. Office 365 Teams haben Rollen als Teil eines umfassenden rollenbasierten Zugriffssteuerungsmechanismus definiert.

## <a name="customer-content-isolation"></a>Isolierung von Kundeninhalten

Alle Kunden Inhalte in einem Mandanten sind von anderen Mandanten und von Betriebs-und Systemdaten isoliert, die bei der Verwaltung von Office 365 verwendet werden. In Office 365 werden mehrere Arten von Schutz implementiert, um das Risiko einer Gefährdung eines Office 365 Diensts oder einer Anwendung zu minimieren. Mehrere Schutzformen verhindern auch den unbefugten Zugriff auf die Informationen von Mandanten oder das Office 365 System selbst.

Informationen dazu, wie Microsoft die logische Isolierung von Mandantendaten in Office 365 implementiert, finden Sie unter [Mandanten Isolierung in Office 365](office-365-tenant-isolation-overview.md).
