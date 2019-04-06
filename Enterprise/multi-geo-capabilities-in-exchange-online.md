---
title: Exchange Multi-Geo
ms.author: chrisda
author: chrisda
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: Informationen zu Multi-Geo-Funktionen in Exchange Online.
ms.openlocfilehash: 60d25cab08ada195d1b189b30bdce8ea505f1d19
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "30931774"
---
# <a name="multi-geo-capabilities-in-exchange-online"></a>Multi-Geo-Funktionen in Exchange Online

In einer Multi-Geo-Umgebung können Sie den Speicherort von Exchange Online-Postfachinhalten (Daten im Ruhezustand) auf Benutzerebene auswählen.

Sie können Postfächer an Satellitenstandorten platzieren, indem Sie:

- Erstellen eines neuen Exchange Online-Postfachs direkt an einem Satellitenstandort

- Umstellen eines vorhandenen Exchange Online-Postfachs an einen Satellitenstandort durch Ändern des bevorzugten Datenspeicherorts des Benutzers

- Direktes Onboarding eines Postfachs von einer lokalen Exchange-Organisation an einem Satellitenstandort

## <a name="mailbox-placement-and-moves"></a>Platzierung und Verschiebung von Postfächern
Nachdem Microsoft die erforderlichen Multi-Geo-Konfigurationsschritte abgeschlossen hat, ehrt Exchange Online das **PreferredDataLocation** -Attribut für Benutzerobjekte in Azure AD.

Exchange Online synchronisiert die **PreferredDataLocation** -Eigenschaft von Azure AD mit der **MailboxRegion** -Eigenschaft im Exchange Online-Verzeichnisdienst. Der Wert von **MailboxRegion** bestimmt den Geo-Speicherort für Benutzerpostfächer und zugehörige Archivpostfächer. Es ist nicht möglich, das primäre Postfach eines Benutzers zu konfigurieren und die Postfächer für die Archivierung in unterschiedlichen geografischen Speicherorten zu archivieren. Pro Benutzerobjekt kann nur ein geografischer Speicherort konfiguriert werden.

- Wenn **PreferredDataLocation** für einen Benutzer mit einem vorhandenen Postfach konfiguriert ist, wird das Postfach in eine Relocation-Warteschlange gestellt und automatisch an den angegebenen geografischen Speicherort verschoben. 

- Wenn **PreferredDataLocation** für einen Benutzer ohne ein vorhandenes Postfach konfiguriert ist, wird es beim Einrichten des Postfachs an den angegebenen geografischen Standort übermittelt. 

- Wenn **PreferredDataLocation** nicht für einen Benutzer angegeben ist, wird es beim Einrichten des Postfachs an der zentralen Stelle eingerichtet.

- Wenn der **PreferredDataLocation** -Code falsch ist (z. b. ein NaN-Typ anstelle von Nam), wird das Postfach an der zentralen Stelle übermittelt.

**Hinweis**: Multi-Geo-Funktionen und Skype for Business Online-Konferenzen, die in der Region gehostet werden, verwenden die **PreferredDataLocation** -Eigenschaft für Benutzerobjekte, um nach Diensten zu suchen. Wenn Sie **PreferredDataLocation** -Werte für Benutzerobjekte für Regional gehostete Besprechungen konfigurieren, wird das Postfach für diese Benutzer automatisch an den angegebenen geografischen Standort verschoben, nachdem Multi-Geo für den Office 365-Mandanten aktiviert wurde.

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a>Funktionseinschränkungen für Multi-Geo in Exchange Online

1. Sicherheits-und Compliance-Funktionen (beispielsweise Überwachung und eDiscovery), die im Exchange Admin Center (EAC) verfügbar sind, sind in Multi-Geo-Organisationen nicht verfügbar. Stattdessen müssen Sie das [Office 365 Security _AMP_ Compliance Center](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) verwenden, um Sicherheits-und Kompatibilitätsfeatures zu konfigurieren.

2. Outlook für Mac-Benutzer haben möglicherweise einen temporären Verlust des Zugriffs auf Ihren Online Archivordner, während Sie Ihr Postfach an einen neuen geografischen Standort verschieben. Diese Bedingung tritt auf, wenn sich die primären und Archivpostfächer des Benutzers an unterschiedlichen geografischen Standorten befinden, da die Verschiebung von geografischen Postfächern zu unterschiedlichen Zeiten erfolgen kann.

3. Benutzer können *Postfachordner* nicht über Geo-Speicherorte in Outlook im Web freigeben (früher als Outlook Web App oder OWA bezeichnet). Beispielsweise kann ein Benutzer in der Europäischen Union Outlook im Web nicht verwenden, um einen freigegebenen Ordner in einem Postfach zu öffnen, das sich in den USA befindet. Outlook im Web-Benutzer können jedoch *andere Postfächer* in verschiedenen GEOSS in einem separaten Browserfenster öffnen, wie unter [Öffnen einer anderen Person in einem separaten Browserfenster in Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362)beschrieben.

    **Hinweis**: die übergreifende Ordnerfreigabe von Postfächern wird in Outlook auf Windows unterstützt.

