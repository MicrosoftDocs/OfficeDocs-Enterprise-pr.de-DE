---
title: Microsoft 365-Isolations Steuerelemente
ms.author: josephd
author: JoeDavies-MSFT
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
description: 'Zusammenfassung: eine Erläuterung der Isolierungs Steuerelemente in Microsoft 365.'
ms.openlocfilehash: da26bb6a41c97a16865bfdd5bdf6aada2069f7fe
ms.sourcegitcommit: 4c519f054216c05c42acba5ac460fb9a821d6436
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "44774910"
---
# <a name="microsoft-365-isolation-controls"></a>Microsoft 365-Isolations Steuerelemente 

Microsoft arbeitet kontinuierlich daran, sicherzustellen, dass die mehrmandantenfähige Architektur von Microsoft 365 auf Unternehmensebene Sicherheit, Vertraulichkeit, Datenschutz, Integrität, lokale, internationale und Verfügbarkeits [Standards](https://www.microsoft.com/TrustCenter/Compliance?service=Office#Icons)unterstützt. Die Skalierung und der Umfang der von Microsoft bereitgestellten Dienste machen es schwierig und nicht wirtschaftlich, Microsoft 365 mit erheblicher menschlicher Interaktion zu verwalten. Microsoft 365-Dienste werden über mehrere global verteilte Rechenzentren bereitgestellt, die jeweils hoch automatisiert sind und nur wenige Vorgänge erfordern, die einen menschlichen Touch oder Zugriff auf Kunden Inhalte benötigen. Unsere Mitarbeiter unterstützen diese Dienste und Rechenzentren mithilfe von automatisierten Tools und hochgradig sicherem Remotezugriff. 

Microsoft 365 besteht aus mehreren Diensten, die wichtige Geschäftsfunktionen bereitstellen und zur gesamten Microsoft 365-Erfahrung beitragen. Jeder dieser Dienste ist in sich geschlossen und für die Integration in einen anderen Dienst konzipiert.

Microsoft 365 ist mit den folgenden Grundsätzen konzipiert:

 - ** [Dienstorientierte Architektur](https://docs.microsoft.com/previous-versions/aa480021(v=msdn.10)):** entwerfen und entwickeln von Software in Form von interoperablen Diensten, die eine klar definierte Geschäftsfunktionalität bieten.
 - **[Operational Security Assurance](https://www.microsoft.com/download/details.aspx?id=40872):** ein Framework, in dem das Wissen über die verschiedenen Funktionen von Microsoft integriert wird, einschließlich des Microsoft- [Sicherheits Entwicklungslebenszyklus](https://www.microsoft.com/sdl/default.aspx), des [Microsoft Security Response Centers](https://technet.microsoft.com/library/dn440717.aspx)und des tiefen Bewusstseins für die Cyber-Bedrohungslandschaft.

Microsoft 365-Dienste arbeiten miteinander zusammen, werden jedoch so konzipiert und implementiert, dass Sie unabhängig voneinander als autonome Dienste bereitgestellt und betrieben werden können. Microsoft trennt Aufgaben und Bereiche der Verantwortung für Microsoft 365, um Möglichkeiten für unbefugte oder unbeabsichtigte Änderungen oder den Missbrauch von Ressourcen der Organisation zu verringern. Microsoft 365 Teams haben Rollen als Teil eines umfassenden rollenbasierten Zugriffssteuerungsmechanismus definiert.

## <a name="customer-content-isolation"></a>Isolierung von Kundeninhalten

Alle Kunden Inhalte in einem Mandanten sind von anderen Mandanten und von Betriebs-und Systemdaten isoliert, die in der Verwaltung von Microsoft 365 verwendet werden. In Microsoft 365 werden mehrere Arten von Schutz implementiert, um das Risiko einer Gefährdung durch einen Microsoft 365-Dienst oder eine Anwendung zu minimieren. Mehrere Schutzformen verhindern auch den unbefugten Zugriff auf die Informationen von Mandanten oder das Microsoft 365-System selbst.

Informationen dazu, wie Microsoft die logische Isolierung von Mandantendaten in Microsoft 365 implementiert, finden Sie unter [Mandanten Isolierung in Microsoft 365](office-365-tenant-isolation-overview.md).
