---
title: Planen von OneDrive for Business Multi-Geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: Informationen Sie zu OneDrive für Business Multi-Geo, Multi-Geo Funktionsweise und welche Geo-Speicherorte für die Speicherung von Daten zur Verfügung stehen.
ms.openlocfilehash: d7d6cfbbff4cf0ec2516f2506946c2832d96b3f2
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="plan-for-onedrive-for-business-multi-geo"></a>Planen von OneDrive for Business Multi-Geo

Diese Anleitung ist für Administratoren von multinationale Unternehmen (MNCs) entwickelt, die Vorbereiten ihrer SharePoint Online-Mandanten auf zusätzliche Regionen gemäß des Unternehmens Anwesenheit Daten vor-Ort-Anforderungen erfüllt erweitert werden.

In einer Konfiguration OneDrive Multi-Geo besteht aus Ihrem Office 365-Mandanten einen zentralen Speicherort (auch bekannt als dem Standardspeicherort) und einen oder mehrere Satelliten Geo-Speicherorte. Hierbei handelt es sich um einen einzelnen Mandanten, der sich über mehrere Geo-Standorte erstreckt. In OneDrive Multi-Geo ist Ihre Mandanten Informationen, einschließlich Geo-Standorten in Azure Active Directory (AAD) gesteuert. 

Es folgen einige wichtige Multi-Geo Begriffe, die Ihnen das Verständnis der grundlegenden Konzepte von der Konfiguration unterstützen:

-   **Mandanten** – eines Unternehmens Darstellung in der Office 365-Cloud, die in der Regel eine oder mehrere Domänen mit ihm verbundenes hat (beispielsweise http://contoso.sharepoint.com). 

-   **Geo-Speicherorte** – die geografische Standorte hinweg, in Ihrem Mandanten Daten gehostet wird. Multi-Geo Mandanten Zeitspanne mehr als einem Geo-Standort, beispielsweise Nordamerika und Europa.

-   **Zulässige Daten Speicherorte (ADL)** – die Geo Speicherorte für den Host von OneDrive und SharePoint-Daten Ihres Mandanten konfiguriert wurde.

-   **Bevorzugte Daten Speicherort (Verteilerliste)** – die Geo Speicherort eines einzelnen Benutzers OneDrive Daten. Dies kann vom Administrator in eines der zulässigen Datenspeicherorte festgelegt werden, die für den Mandanten konfiguriert wurden. Beachten Sie, wenn Sie der persönlichen Verteilerliste für einen Benutzer, die bereits über eine OneDrive-Website verfügt ändern, ihre OneDrive Daten nicht am neuen Speicherort Geo automatisch bewegt werden. Weitere Informationen finden Sie unter [einer OneDrive-Bibliothek mit einem anderen Geo-Speicherort zu verschieben](move-onedrive-between-geo-locations.md) .

Multi-Geo aktivieren sind vier wichtige Schritte erforderlich:

1.  Arbeiten Sie mit Ihr Kundenteam, die Dienstplan _Multi-Geo-Funktionen in Office 365_ hinzufügen möchten.

2.  Wählen Sie die gewünschten Satellitenassemblys Geo Speicherorte und Ihres Mandanten hinzugefügt werden.

3.  Bevorzugte Datenspeicherort Ihrer Benutzer auf den gewünschten Satelliten Geo Speicherort festgelegt. Wenn eine neue Website OneDrive für einen Benutzer bereitgestellt wird, ist es zu ihrer Verteilerliste bereitgestellt.

4.  Migrieren von vorhandenen OneDrive-Websites der Benutzer aus dem Hauptstandort zu ihren bevorzugten Datenspeicherort nach Bedarf.

Details für jeden dieser Schritte finden Sie unter [Konfigurieren von OneDrive für Unternehmen Multi-Geo](multi-geo-tenant-configuration.md) .

> [!IMPORTANT]
> Beachten Sie, dass die Multi-Geo-Features von Office 365 sind nicht für die Optimierung Fälle Leistung ausgelegt, dafür entwickelt, Daten vor-Ort-Anforderungen erfüllen. Informationen zur leistungsoptimierung für Office 365 finden Sie unter [netzwerkplanung und leistungsoptimierung für Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) , oder wenden Sie sich an Ihrem Supportpersonal.

Sie können konfigurieren einen der folgenden Speicherorte Satelliten Geo Speicherorte sein, auf dem Sie Dateien OneDrive hosten können. Wie Sie Multi-Geo planen möchten, stellen Sie eine Liste der Speicherorte, die Sie Ihrem Office 365-Mandanten hinzufügen möchten. Es wird empfohlen beginnend mit einem oder zwei Satellitenstandorten und schrittweise auf Weitere Geo-Speicherorte erweitert bei Bedarf.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Speicherort</strong></th>
<th align="left"><strong>Code</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Asien-Pazifik</td>
<td align="left">APC</td>
</tr>
<tr class="even">
<td align="left">Europa / Mittlerer Osten / Afrika</td>
<td align="left">EUR</td>
</tr>
<tr class="odd">
<td align="left">Nordamerika</td>
<td align="left">NAME</td>
</tr>
<tr class="even">
<td align="left">Australien</td>
<td align="left">AUS</td>
</tr>
<tr class="odd">
<td align="left">Kanada</td>
<td align="left">KÖNNEN</td>
</tr>
<tr class="odd">
<td align="left">Japan</td>
<td align="left">JAPANISCHE</td>
</tr>
<tr class="even">
<td align="left">Korea</td>
<td align="left">KOREANISCHE</td>
</tr>
<tr class="odd">
<td align="left">Vereinigtes Königreich</td>
<td align="left">GBR</td>
</tr>
</tbody>
</table>

Zukünftige geografische Speicherorte:
  
- Frankreich
- Indien

Wenn Sie mehrere Geo konfigurieren, nehmen Sie die Möglichkeit, Ihre lokale Infrastruktur konsolidieren während der Migration zu Office 365. Beispielsweise wenn Sie lokale-Farmen in Singapur und Malaysia verfügen, können klicken Sie dann Sie diese an die APC Satelliten Position konsolidieren bereitgestellten Daten vor-Ort-Anforderungen Sie dies tun, können.

## <a name="best-practices"></a>Bewährte Methoden

Es wird empfohlen, dass die Erstellung eines Testbenutzers in Office 365 ersten Tests durchführen. Wir werde durchgehen einige Schritte Tests und Überprüfungen mit diesen Benutzer bevor Sie mit integrierten produktionsbenutzern in das Feature OneDrive Multi-Geo fortfahren.

Wenn Sie mit dem Testbenutzer Tests abgeschlossen haben, wählen Sie eine Pilotgruppe – vielleicht aus Ihre IT-Abteilung – zuerst OneDrive in einen neuen Geo-Speicherort verwendet werden. Wählen Sie für diese Gruppe ersten Benutzer, die noch nicht über eine OneDrive verfügen. Es wird empfohlen nicht mehr als fünf Personen in dieser ersten Gruppe und schrittweise erweitern einen Ansatz im Batchmodus Einführung folgen.

Jeder Benutzer muss eine *bevorzugte Datenspeicherort* (Verteilerliste) so festgelegt, dass Office 365, welche Geo-Speicherort zum Bereitstellen ihrer OneDrive ermitteln können verfügen. Bevorzugte Datenspeicherort des Benutzers muss eine der gewählten Satellitenstandorten oder den zentralen Standort übereinstimmen. Während das Verteilerliste Feld nicht obligatorisch ist, wird empfohlen, eine Verteilerliste für alle Benutzer festgelegt werden. Arbeitslasten eines Benutzers ohne eine Verteilerliste werden am zentralen Standort auf der Grundlage der Logik Multi-Geo bereitgestellt werden.   

Erstellen Sie eine Liste der Benutzer, und umfassen Sie ihren Benutzerprinzipalnamen (UPN) und den Speicherort Code für den Speicherort der entsprechenden bevorzugten Daten. Test-Benutzer und der anfänglichen Pilotgruppe zu enthalten. Für die Konfigurationsverfahren benötigen Sie dieser Liste.

Wenn Ihre Benutzer von einem lokalen Active Directory (AD) System Azure Active Directory (AAD) synchronisiert sind, müssen Sie den Speicherort der bevorzugten Daten synchronisierten Benutzer mithilfe von Azure Active Directory verbinden festlegen. Speicherort der bevorzugten Daten von Azure AD-PowerShell synchronisierten Benutzer können nicht direkt konfiguriert werden. Die Schritte zum Einrichten der Verteilerliste in Active Directory und synchronisieren fallen [Azure Active Directory verbinden Sync: Konfigurieren des bevorzugten Datenspeicherort für Office 365-Ressourcen](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).

Die Verwaltung von einem Mandanten Multi-Geo kann unterscheiden sich von einem Multi-Geo-Mandanten, so viele der Einstellungen für SharePoint und OneDrive und Dienste sind Multi-Geo berücksichtigen. Es wird empfohlen, dass Sie [Verwalten einer Umgebung mit mehreren geografisch](administering-a-multi-geo-environment.md) , ehe Sie mit der Konfiguration fortzufahren.

Lesen Sie ausführliche Informationen über Ihre Endbenutzer Erfahrung in einer Umgebung mit mehreren geografisch [Benutzerinteraktion in einer Multgeo Umgebung](multi-geo-user-experience.md) .

Um die ersten Schritte beim Konfigurieren von OneDrive für Unternehmen Multi-Geo, finden Sie unter [Konfigurieren von OneDrive für Unternehmen Multi-Geo](multi-geo-tenant-configuration.md).

Wenn Sie die Konfiguration abgeschlossen haben, denken Sie daran, [Migrieren Ihrer Benutzer OneDrive Bibliotheken](move-onedrive-between-geo-locations.md) Bedarf Ihrer Benutzer arbeiten von zu ihren bevorzugten Datenspeicherorte erhalten.
