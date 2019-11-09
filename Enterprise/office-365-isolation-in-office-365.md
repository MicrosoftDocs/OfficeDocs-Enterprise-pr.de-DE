---
title: Office 365 Isolierung und Zugriffssteuerung in Office 365
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
- SPO_Content
description: 'Zusammenfassung: eine Erläuterung der Isolierung und Zugriffssteuerung in den verschiedenen Anwendungen von Office 365.'
ms.openlocfilehash: 5855828faafaf12e609e93a1a4f0ec7419e0a9d6
ms.sourcegitcommit: 89ecf793443963b4c87cf1033bf0284cbfb83d9a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2019
ms.locfileid: "38078164"
---
# <a name="isolation-and-access-control-in-office-365"></a>Isolierung und Zugriffskontrolle in Office 365

Azure Active Directory und Office 365 verwenden ein hoch komplexes Datenmodell, das Dutzende von Diensten, Hunderte von Entitäten, Tausende von Beziehungen und Zehntausende von Attributen umfasst. Auf hoher Ebene sind Azure Active Directory und die Dienst Verzeichnisse die Container von Mandanten und Empfängern, die mithilfe von statusbasierten Replikationsprotokollen synchron gehalten werden. Zusätzlich zu den Verzeichnisinformationen, die in Azure Active Directory aufbewahrt werden, verfügen alle Dienst Arbeitslasten über eine eigene Verzeichnisdienst-Infrastruktur.
 
![Office 365 Mandantendaten Synchronisierung](media/office-365-isolation-tenant-data-sync.png)

In diesem Modell gibt es keine einzelne Quelle für Verzeichnisdaten. Bestimmte Systeme besitzen einzelne Daten, aber kein einzelnes System besitzt alle Daten. Office 365 Dienste kooperieren mit Azure Active Directory in diesem Datenmodell. Azure Active Directory ist das "System der Wahrheit" für freigegebene Daten, bei dem es sich typischerweise um kleine und statische Daten handelt, die von jedem Dienst verwendet werden. Das in Office 365 und Azure Active Directory verwendete Verbundmodell stellt die freigegebene Ansicht der Daten bereit.

Office 365 verwendet sowohl physischen Speicher als auch Azure-Cloud-Speicher. Exchange Online (einschließlich Exchange Online Schutz) und Skype for Business ihren eigenen Speicher für Kundendaten verwenden. SharePoint Online verwendet sowohl SQL Server Speicher als auch Azure-Speicher, daher ist die zusätzliche Isolierung von Kundendaten auf Speicherebene erforderlich.

## <a name="exchange-online"></a>Exchange Online

Exchange Online speichert Kundendaten in Postfächern. Postfächer werden in ESE-Datenbanken (Extensible Storage Engine) als Postfachdatenbanken gehostet. Dies umfasst Benutzerpostfächer, verknüpfte Postfächer, freigegebene Postfächer und Postfächer für Öffentliche Ordner. Zu den Benutzerpostfächern gehören gespeicherte Skype for Business Inhalte wie Unterhaltungs Verläufe.

Der Inhalt des Benutzerpostfachs umfasst Folgendes:

- E-Mails und e-Mail-Anhänge
- Kalender-und Frei/Gebucht-Informationen
- Kontakte
- Aufgaben
- Anmerkungen
- Gruppen
- Rückschluss Daten

Jede Postfachdatenbank in Exchange Online enthält Postfächer von mehreren Mandanten. Ein Autorisierungscode sichert jedes Postfach, auch innerhalb eines Mandanten. Standardmäßig hat nur der zugewiesene Benutzer Zugriff auf ein Postfach. Die Zugriffssteuerungsliste (Access Control List, ACL), die ein Postfach sichert, enthält eine von Azure Active Directory auf Mandantenebene authentifizierte Identität. Die Postfächer für jeden Mandanten sind auf Identitäten beschränkt, die für den Authentifizierungsanbieter des Mandanten authentifiziert wurden, der nur Benutzer von diesem Mandanten enthält. Inhalte in Mandant a können von Benutzern in Mandant B nicht in irgendeiner Weise abgerufen werden, es sei denn, Sie werden von Mandanten a ausdrücklich genehmigt.

## <a name="skype-for-business"></a>Skype for Business

Skype for Business speichert Daten an verschiedenen Stellen:

- Benutzer-und Kontoinformationen, einschließlich Verbindungs Endpunkten, Mandanten-IDs, Wähleinstellungen, Roamingeinstellungen, Anwesenheitsstatus, Kontaktlisten usw., werden auf den Skype for Business Active Directory Servern und in verschiedenen Skype for Business Datenbankservern gespeichert. Kontaktlisten werden im Exchange Online Postfach des Benutzers gespeichert, wenn der Benutzer für beide Produkte aktiviert ist, oder auf Skype for Business Servern, wenn der Benutzer dies nicht tut. Skype for Business Datenbankserver sind nicht partitioniert pro Mandanten, aber die mehrinstanzenfähige Isolierung von Daten wird über die rollenbasierte Zugriffssteuerung (Role-Based Access Control, RBAC) erzwungen.
- Besprechungsinhalte und hochgeladene Daten werden auf DFS-Freigaben (Distributed File System) gespeichert. Dieser Inhalt kann auch in Exchange Online archiviert werden, wenn dieser aktiviert ist. Die DFS-Freigaben werden nicht pro Mandant partitioniert. der Inhalt ist mit ACLs gesichert, und Mehrmandantenfähigkeit wird über RBAC erzwungen.
- Anruf Detaildatensätze, bei denen es sich um den Aktivitätsverlauf handelt, wie Anrufverlauf, Chatsitzungen, Anwendungsfreigabe, Chatverlauf usw., können auch in Exchange Online gespeichert werden, aber die meisten Anruf Detaildatensätze werden temporär auf KDS-Servern (Call Detail Record) gespeichert. Inhalt wird nicht pro Mandant partitioniert, aber Mehrmandantenfähigkeit wird über RBAC erzwungen.

## <a name="sharepoint-online"></a>SharePoint Online

SharePoint Online verfügt über mehrere unabhängige Mechanismen zur Datenisolierung. Sie speichert Objekte als abstrahierten Code in Anwendungsdatenbanken. Wenn ein Benutzer beispielsweise eine Datei in SharePoint Online hochlädt, wird die Datei zerlegt, in Anwendungscode übersetzt und in mehreren Tabellen über mehrere Datenbanken gespeichert.

Wenn ein Benutzer direkten Zugriff auf den Speicher erhält, der die Daten enthält, kann der Inhalt nicht für einen Menschen oder ein anderes System als SharePoint Online interpretiert werden. Diese Mechanismen umfassen Sicherheitszugriffssteuerung und Eigenschaften. Alle SharePoint Online Ressourcen werden durch den Autorisierungscode und die RBAC-Richtlinie gesichert, einschließlich innerhalb eines Mandanten. Die Zugriffssteuerungsliste (Access Control List, ACL), die eine Ressource sichert, enthält eine auf Mandantenebene authentifizierte Identität. SharePoint Online Daten für einen Mandanten sind auf vom Authentifizierungsanbieter für den Mandanten authentifizierte Identitäten limitiert.

Zusätzlich zu den ACLs wird eine Eigenschaft auf Mandantenebene, die den Authentifizierungsanbieter angibt (Dies ist die mandantenspezifische Azure-Active Directory), einmal geschrieben und kann nicht mehr geändert werden, nachdem Sie festgelegt wurde. Nachdem die Mandanten Eigenschaft des Authentifizierungsanbieters für einen Mandanten festgelegt wurde, kann Sie nicht mithilfe aller für einen Mandanten verfügbar gemachten APIs geändert werden.

Für jeden Mandanten wird eine eindeutige *Abonnement* -Nr verwendet. Alle Kunden Standorte befinden sich im Besitz eines Mandanten und weisen dem Mandanten eine eindeutige *Abonnement* -Nummer zu. Die *Subscription* -Eigenschaft für eine Website wird einmal geschrieben und ist dauerhaft. Nachdem eine Website einem Mandanten zugewiesen wurde, kann Sie nicht zu einem anderen Mandanten verschoben werden. Die *Abonnement* -Nr ist der Schlüssel, der zum Erstellen des Sicherheitsbereichs für den Authentifizierungsanbieter verwendet wird und an den Mandanten gebunden ist.

SharePoint Online verwendet SQL Server und Azure-Speicher für die Speicherung von Inhaltsmetadaten. Der Partitionsschlüssel für den Inhaltsspeicher lautet *Site* -Nr in SQL. Bei der Ausführung einer SQL-Abfrage verwendet SharePoint Online eine *Website* -Überprüfung, die als Teil einer *Abonnement* -Bestätigung auf Mandantenebene überprüft wurde.

SharePoint Online speichert verschlüsselte Dateiinhalte in Microsoft Azure BLOBs. Jede SharePoint Online Farm verfügt über ein eigenes Microsoft Azure Konto, und alle in Azure gespeicherten BLOBs werden einzeln mit einem Schlüssel verschlüsselt, der im SQL-Inhaltsspeicher gespeichert ist. Der Verschlüsselungsschlüssel, der in Code von der Autorisierungs Schicht geschützt wird und nicht direkt für den Endbenutzer verfügbar gemacht wird. SharePoint Online verfügt über eine Echtzeitüberwachung, um zu erkennen, wann eine HTTP-Anforderung Daten für mehr als einen Mandanten liest oder schreibt. Die Anforderungs-ID- *Abonnement* -ID wird anhand der *Abonnement* -ID der aufgerufenen Ressource nachverfolgt. Anforderungen für den Zugriff auf Ressourcen von mehr als einem Mandanten sollten niemals durch Endbenutzer geschehen. Dienstanforderungen in einer Umgebung mit mehreren Mandanten sind die einzige Ausnahme. Der Suchcrawler zieht beispielsweise Inhaltsänderungen für eine gesamte Datenbank gleichzeitig durch. Dies umfasst normalerweise das Abfragen von Websites von mehr als einem Mandanten in einer einzelnen Dienstanforderung, was aus Effizienzgründen geschieht.
