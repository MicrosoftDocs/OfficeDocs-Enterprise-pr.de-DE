---
title: Exchange Multi-Geo
ms.author: chrisda
author: chrisda
manager: serdars
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: Weitere Informationen zu Multi-Geo-Funktionen in Exchange Online.
ms.openlocfilehash: d518121c69ee29ee246c6947e361a74a3933310f
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069931"
---
# <a name="multi-geo-capabilities-in-exchange-online"></a>Multi-Geo-Funktionen in Exchange Online

In einer Multi-Geo-Umgebung können Sie den Speicherort des Exchange Online-Postfachinhalts (Daten im Ruhezustand) benutzerabhängig auswählen.

Sie können Postfächer an Satelliten-Geo-Speicherorten platzieren, indem Sie:

- Ein neues Exchange Online-Postfach direkt an einem Satelliten-Geo-Speicherort erstellen.

- Ein vorhandenes Exchange Online-Postfach auf einen Satelliten-Geo-Speicherort verschieben, indem Sie den bevorzugten Datenspeicherort des Benutzers ändern.

- Ein Postfach von einer lokalen Exchange-Organisation direkt in einen Satelliten-Geo-Speicherort einbinden.

## <a name="mailbox-placement-and-moves"></a>Platzieren und Verschieben von Postfächern

Nachdem Microsoft die erforderlichen Konfigurationsschritte für die Multi-Geo-Konfiguration abgeschlossen hat, wird Exchange Online das Attribut **PreferredDataLocation** für Benutzerobjekte in Azure AD berücksichtigen.

Exchange Online synchronisiert die Eigenschaft **PreferredDataLocation** von Azure AD mit der Eigenschaft **MailboxRegion** im Exchange Online-Verzeichnisdienst. Der Wert von **MailboxRegion** bestimmt den Geo-Speicherort, an dem Benutzerpostfächer und alle zugehörigen Archivpostfächer platziert werden. Es ist nicht möglich, den primären Postfach eines Benutzers zu konfigurieren und Postfächer so zu archivieren, dass sie sich an verschiedenen Geo-Speicherorten befinden. Pro Benutzerobjekt kann nur ein Geo-Speicherort konfiguriert werden.

- Wenn **PreferredDataLocation** auf einem Benutzer mit einem bestehenden Postfach konfiguriert ist, wird das Postfach in eine Verlagerungswarteschlange gestellt und automatisch an den angegebenen Geo-Speicherort verschoben.

- Wenn **PreferredDataLocation** für einen Benutzer ohne bestehendes Postfach konfiguriert ist, wird es bei der Bereitstellung des Postfachs an dem angegebenen Geo-Speicherort bereitgestellt.

- Wenn **PreferredDataLocation** nicht für einen Benutzer angegeben ist, wird es bei der Bereitstellung des Postfachs in dem zentralen Geo-Speicherort bereitgestellt.

- Wenn der **PreferredDataLocation**-Code falsch ist (z. B. ein Typ von NAN anstelle von NAM), wird das Postfach in den zentralen Geo-Speicherort bereitgestellt.

**Hinweis**: Multi-Geo-Funktionen und regional gehostete Besprechungen von Skype for Business Online verwenden beide die Eigenschaft **PreferredDataLocation** auf Benutzerobjekten, um Dienste zu finden. Wenn Sie die **PreferredDataLocation**-Werte für Benutzerobjekte für regional gehostete Besprechungen konfigurieren, wird das Postfach für diese Benutzer automatisch an den angegebenen Geo-Speicherort verschoben, nachdem Multi-Geo auf dem Office 365-Mandanten aktiviert wurde.

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a>Funktionseinschränkungen für Multi-Geo in Exchange Online

- Sicherheits- und Compliance-Funktionen (z. B. Auditing und eDiscovery), die im Exchange Admin Center (EAC) verfügbar sind, sind in Multi-Geo-Organisationen nicht verfügbar. Stattdessen müssen Sie das [Office 365 Security & Compliance Center](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) verwenden, um Sicherheits- und Compliance-Funktionen zu konfigurieren.

- Outlook für Mac-Benutzer können einen vorübergehenden Verlust des Zugriffs auf ihren Online-Archivordner erleiden, während Sie ihr Postfach an einen neuen Geo-Speicherort verschieben. Diese Situation tritt auf, wenn sich die Primär- und Archivpostfächer des Benutzers an verschiedenen Geo-Speicherorten befinden, da Geo-übergreifende Postfachverschiebungen zu unterschiedlichen Zeiten durchgeführt werden können.

- Benutzer können *Postfachordner* nicht über Geo-Speicherorte hinweg in Outlook im Web freigeben (früher bekannt als Outlook Web App oder OWA). Beispielsweise kann ein Benutzer in der Europäischen Union Outlook im Web nicht verwenden, um einen freigegebenen Ordner in einem Postfach zu öffnen, das sich in den Vereinigten Staaten befindet. Outlook im Web-Benutzer können jedoch *andere Postfächer* an verschiedenen Geo-Speicherorten öffnen, indem sie ein separates Browserfenster verwenden, wie unter [Postfach einer anderen Person in einem separaten Browserfenster in Outlook Web App öffnen](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362) beschrieben.

  **Hinweis**: Die Geo-übergreifende Freigabe von Postfachordnern wird in Outlook on Windows unterstützt.

- Öffentliche Ordner werden in Multi-Geo-Organisationen unterstützt. Die öffentlichen Ordner müssen jedoch in dem zentralen Geo-Speicherort verbleiben. Sie können öffentliche Ordner nicht an Satelliten-Geo-Speicherorten verschieben.
