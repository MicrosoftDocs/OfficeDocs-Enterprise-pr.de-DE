---
title: Office 365 Isolierung und Zugriffssteuerung in Azure Active Directory
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
description: 'Zusammenfassung: wie Isolierung und Zugriffssteuerung in Azure Active Directory funktionieren.'
ms.openlocfilehash: ac8ea9cf0550517f4d4d8c6eac10812700bb668b
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844466"
---
# <a name="isolation-and-access-control-in-azure-active-directory"></a>Isolierung und Zugriffssteuerung in Azure Active Directory

Azure Active Directory wurde entwickelt, um mehrere Mandanten auf hochsichere Weise durch die logische Datenisolierung zu hosten. Der Zugriff auf Azure Active Directory ist von einer Autorisierungsebene abgegrenzt. Azure-Active Directory isolieren Kunden, die Mandanten Container als Sicherheitsgrenzen verwenden, um den Inhalt eines Kunden zu schützen, damit der Zugriff auf Inhalte nicht möglich ist oder von Kollegen beeinträchtigt wird. Von der Autorisierungs Schicht von Azure Active Directory werden drei Prüfungen durchgeführt:

- Ist der Prinzipal für den Zugriff auf Azure Active Directory Mandanten aktiviert?
- Ist der Prinzipal für den Zugriff auf Daten in diesem Mandanten aktiviert?
- Ist die Rolle des Prinzipals in diesem Mandanten für den Typ des angeforderten Datenzugriffs autorisiert?

Keine Anwendung, kein Benutzer, kein Server oder kein Dienst kann auf Azure-Active Directory ohne entsprechende Authentifizierung und Token oder Zertifikat zugreifen. Anforderungen werden zurückgewiesen, wenn Sie nicht von ordnungsgemäßen Anmeldeinformationen begleitet werden.

Azure Active Directory hostet jeden Mandanten in seinem eigenen geschützten Container, mit Richtlinien und Berechtigungen für und innerhalb des Containers, der ausschließlich vom Mandanten besessen und verwaltet wird.
 
![Azure-Container](media/office-365-isolation-azure-container.png)

Das Konzept von Mandanten Containern ist tief im Verzeichnisdienst auf allen Ebenen verankert, von Portalen bis hin zu persistentem Speicher. Selbst wenn mehrere Azure Active Directory-Mandanten Metadaten auf demselben physikalischen Datenträger gespeichert werden, gibt es keine Beziehung zwischen den Containern, die nicht durch den Verzeichnisdienst definiert sind, was wiederum vom mandantenadministrator diktiert wird. Es kann keine direkte Verbindung zu Azure Active Directory Speicher von einer anfordernden Anwendung oder einem Dienst ohne vorheriges durchlaufen der Autorisierungs Schicht geben.

Im Beispiel unten verfügen Contoso und Fabrikam über separate, dedizierte Container, und obwohl diese Container möglicherweise einige derselben zugrunde liegenden Infrastruktur wie Server und Speicher freigeben, bleiben Sie getrennt und voneinander isoliert und werden von Autorisierungsebenen und Zugriffssteuerung.
 
![Dedizierte Azure-Container](media/office-365-isolation-azure-dedicated-containers.png)

Darüber hinaus gibt es keine Anwendungskomponenten, die in Azure Active Directory ausgeführt werden können, und es ist für einen Mandanten nicht möglich, die Integrität eines anderen Mandanten gewaltsam zu verletzen, auf die Verschlüsselungsschlüssel eines anderen Mandanten zuzugreifen oder unformatierte Daten vom Server zu lesen.

Standardmäßig werden von Azure Active Directory alle Vorgänge, die von Identitäten in anderen Mandanten ausgestellt werden, nicht zugelassen. Jeder Mandant ist in Azure Active Directory durch anspruchsbasierte Zugriffssteuerungen logisch isoliert. Lese-und Schreibvorgänge von Verzeichnisdaten werden auf Mandanten Container beschränkt und von einer internen Abstraktionsschicht und einer rollenbasierten Zugriffs Steuerungsschicht (Role-Based Access Control, RBAC) gesteuert, die den Mandanten zusammen als Sicherheitsgrenze erzwingen. Jede Verzeichnisdaten Zugriffsanforderung wird von diesen Schichten verarbeitet, und jede Zugriffsanforderung in Office 365 wird durch die obige Logik überwacht.

Azure Active Directory verfügt über die Partitionen Nordamerika, US-Regierung, Europäische Union, Deutschland und World Wide. Ein Mandant ist in einer einzelnen Partition vorhanden, und Partitionen können mehrere Mandanten enthalten. Partitionsinformationen werden von Benutzern abstrahiert. Eine bestimmte Partition (einschließlich aller Mandanten in Ihr) wird in mehrere Rechenzentren repliziert. Die Partition für einen Mandanten wird basierend auf den Eigenschaften des Mandanten ausgewählt (beispielsweise der Ländercode). Geheimnisse und andere vertrauliche Informationen in jeder Partition werden mit einem dedizierten Schlüssel verschlüsselt. Die Schlüssel werden automatisch generiert, wenn eine neue Partition erstellt wird.

Azure Active Directory Systemfunktionen sind eine eindeutige Instanz für jede Benutzersitzung. Darüber hinaus verwendet Azure Active Directory Verschlüsselungstechnologien, um freigegebene Systemressourcen auf Netzwerkebene zu isolieren, um eine unbefugte und unbeabsichtigte Weitergabe von Informationen zu verhindern.
