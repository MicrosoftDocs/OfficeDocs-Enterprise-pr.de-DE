---
title: Planen von Multi-Geo in OneDrive for Business
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Informationen zu Multi-Geo in OneDrive for Business, zur Funktionsweise von Multi-Geo und zu für Datenspeicher verfügbaren geografischen Standorten.
ms.openlocfilehash: 54efc6092338e505ef44344f9c3d3a7efe9ae498
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2018
---
# <a name="plan-for-onedrive-for-business-multi-geo"></a>Planen von Multi-Geo in OneDrive for Business

Dieser Leitfaden wurde für Administratoren von multinationalen Unternehmen (MNCs) entwickelt, die den SharePoint Online-Mandanten für die Erweiterung auf weitere geografische Standorte entsprechend den Unternehmensanforderungen in Bezug auf die Datenaufbewahrung vorbereiten.

In einer Multi-Geo-Konfiguration von OneDrive besteht der Office 365-Mandant aus einem zentralen Standort (auch Standardstandort genannt) und einem oder mehreren Satellitenstandorten. Dies ist ein einzelner Mandanten, der mehrere geografische Standorte umfasst. In Multi-Geo in OneDrive werden Ihre Mandanteninformationen, darunter die geografischen Standorte, in Azure Active Directory (AAD) verwaltet. 

Im Folgenden werden einige wichtige Begriffe in Bezug auf Multi-Geo erläutert, die beim Verständnis der grundlegenden Konzepte der Konfiguration hilfreich sind:

-   **Mandant** – Darstellung einer Organisation in der Office 365-Cloud, mit der in der Regel eine oder mehrere Domänen verknüpft sind (zum Beispiel http://contoso.sharepoint.com). 

-   **Geografische Standorte** – Die geografischen Standorte, an denen die Daten Ihres Mandanten gehostet werden. Multi-Geo-Mandanten umfassen mehr als einen geografischen Standort, zum Beispiel Nordamerika und Europa.

-   **Zugelassene Datenspeicherorte (Allowed Data Locations, ADL)** – Die geografischen Standorte, für die Ihr Mandant zum Hosten von OneDrive- und SharePoint-Daten konfiguriert wurde.

-   **Bevorzugter Datenspeicherort (Preferred Data Location, PDL)** – Der geografische Standort, an dem OneDrive-Daten eines einzelnen Benutzers gespeichert sind. Dieser kann vom Administrator auf jeden zugelassenen Datenspeicherort festgelegt werden, der für den Mandanten konfiguriert wurde. Wenn Sie den bevorzugten Datenspeicherort für einen Benutzer ändern, der bereits über eine OneDrive-Website verfügt, werden seine OneDrive-Daten nicht automatisch an den neuen geografischen Standort verschoben. Weitere Informationen finden Sie unter [Verschieben einer OneDrive-Bibliothek an einen anderen geografischen Standort](move-onedrive-between-geo-locations.md).

Für die Aktivierung von Multi-Geo müssen Sie die folgenden Schritte durchführen:

1.  Arbeiten Sie mit Ihrem Kontoteam, um den Serviceplan für _Multi-Geo-Funktionen in Office 365_ hinzuzufügen.

2.  Wählen Sie die gewünschten Satellitenstandorte, und fügen Sie sie Ihrem Mandanten hinzu.

3.  Legen Sie den bevorzugten Datenspeicherort und den gewünschten Satellitenstandort für Ihre Benutzer fest. Wenn eine neue OneDrive-Website für einen Benutzer bereitgestellt wird, wird sie an dem bevorzugten Datenspeicherort bereitgestellt.

4.  Migrieren Sie bei Bedarf vorhandene OneDrive-Websites der Benutzer von dem Standardort zu dem bevorzugten Datenspeicherort.

Weitere Informationen zu den einzelnen Schritten finden Sie unter [Konfigurieren von Multi-Geo in OneDrive for Business](multi-geo-tenant-configuration.md).

> [!IMPORTANT]
> Beachten Sie, dass Multi-Geo-Funktionen von Office 365 nicht auf Leistungsoptimierung ausgelegt sind, sie dienen lediglich dazu, die jeweiligen Datenaufbewahrungsanforderungen zu erfüllen. Informationen zur Leistungsoptimierung für Office 365 finden Sie unter [Netzwerkplanung und Leistungsoptimierung für Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848), oder wenden Sie sich hierzu an Ihre Supportgruppe.

Sie können einen der folgenden Standorte als Satellitenstandorte festlegen, an denen OneDrive-Dateien gehostet werden können. Erstellen Sie bei der Planung von Multi-Geo eine Liste der Orte, die Sie Ihrem Office 365-Mandanten hinzufügen möchten. Es wird empfohlen, mit einem oder zwei Satellitenstandorten zu beginnen und dann bei Bedarf schrittweise weitere geografische Standorte hinzuzufügen.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Standort</strong></th>
<th align="left"><strong>Code</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Asien-Pazifik</td>
<td align="left">APC</td>
</tr>
<tr class="even">
<td align="left">Europa/Naher Osten/Afrika</td>
<td align="left">EUR</td>
</tr>
<tr class="odd">
<td align="left">Nordamerika</td>
<td align="left">NAM</td>
</tr>
<tr class="even">
<td align="left">Australien</td>
<td align="left">AUS</td>
</tr>
<tr class="odd">
<td align="left">Kanada</td>
<td align="left">CAN</td>
</tr>
<tr class="odd">
<td align="left">Japan</td>
<td align="left">JPN</td>
</tr>
<tr class="even">
<td align="left">Korea</td>
<td align="left">KOR</td>
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

Beim Konfigurieren von Multi-Geo sollten Sie auch eine Konsolidierung der lokalen Infrastruktur während der Migration zu Office 365 berücksichtigen. Wenn Sie zum Beispiel über lokale Farmen in Singapur und Malaysia verfügen, können Sie sie an dem Satellitenstandort APC zusammenführen, wenn dies entsprechend den Datenaufbewahrungsanforderungen möglich ist.

## <a name="best-practices"></a>Bewährte Methoden

Es wird empfohlen, einen Testbenutzer in Office 365 zu anfänglichen Testzwecken zu erstellen. Es werden einige Test- und Überprüfungsschritte für diesen Benutzer durchgeführt, bevor mit der Multi-Geo-Funktion in OneDrive für Produktionsbenutzer fortzufahren.

Nach Abschluss der Tests mit dem Testbenutzer, wählen Sie eine Pilotgruppe, vielleicht von Ihrer IT-Abteilung, die zunächst OneDrive an dem neuen geografischen Standort verwenden soll. Wählen Sie für diese erste Gruppe Benutzer, die noch nicht über OneDrive verfügen. Es wird empfohlen, nicht mehr als fünf Personen zu dieser ersten Gruppe hinzuzufügen und sie schrittweise zu erweitern und schließlich einen Rollout im Batch durchzuführen.

Für jeden Benutzer muss ein *bevorzugter Datenspeicherort* festgelegt werden, damit Office 365 den geografischen Standort für die Bereitstellung von OneDrive ermitteln kann. Der bevorzugte Datenspeicherort des Benutzers muss mit einem der ausgewählten Satellitenstandorte oder dem zentralen Standort übereinstimmen. Obwohl das Feld für den bevorzugten Datenspeicherort kein Pflichtfeld ist, wird empfohlen, einen bevorzugten Datenspeicherort für alle Benutzer festzulegen. Workloads eines Benutzers ohne bevorzugten Datenspeicherort werden basierend auf der Multi-Geo-Logik an dem zentralen Standort bereitgestellt.   

Erstellen Sie eine Liste Ihrer Benutzer mit den entsprechenden Benutzerprinzipalnamen und den Codes für die entsprechenden bevorzugten Datenspeicherorte. Fügen Sie Ihren Testbenutzer und die erste Pilotgruppe hinzu. Sie benötigen diese Liste für die Konfigurationsverfahren.

Wenn für Ihre Benutzer eine Synchronisierung zwischen dem lokalen Active Directory (AD)-System und Azure Active Directory (AAD) erfolgt, müssen Sie den bevorzugten Datenspeicherort für die synchronisierten Benutzer mithilfe von Azure Active Directory Connect festlegen. Sie können den bevorzugten Datenspeicherort für synchronisierte Benutzer nicht direkt mithilfe von Azure AD PowerShell konfigurieren. Die Schritte zum Einrichten der bevorzugten Datenspeicherorte in AD und zum Synchronisieren dieser Liste finden Sie unter [Azure Active Directory Connect-Synchronisierung: Konfigurieren des bevorzugten Datenspeicherorts für Office 365-Ressourcen](https://docs.microsoft.com/de-DE/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).

Die Verwaltung eines Multi-Geo-Mandanten kann von der eines Nicht-Multi-Geo-Mandanten abweichen, da viele SharePoint- und OneDrive-Einstellungen und -Dienste über Multi-Geo-Funktionen verfügen. Es wird empfohlen, den Artikel [Verwalten einer Multi-Geo-Umgebung](administering-a-multi-geo-environment.md) zu lesen, bevor Sie mit der Konfiguration fortfahren.

Informationen zur Endbenutzererfahrung in einer Multi-Geo-Umgebung finden Sie unter [Benutzererfahrung in einer Multi-Geo-Umgebung](multi-geo-user-experience.md).

Informationen zu den ersten Schritten beim Konfigurieren von Multi-Geo in OneDrive for Business finden Sie unter [Konfigurieren von Multi-Geo in OneDrive for Business](multi-geo-tenant-configuration.md).

Denken Sie nach Abschluss der Konfiguration daran, [die OneDrive-Bibliotheken Ihrer Benutzer](move-onedrive-between-geo-locations.md) bei Bedarf zu migrieren, damit Benutzer an ihren bevorzugten Datenspeicherorten arbeiten können.
