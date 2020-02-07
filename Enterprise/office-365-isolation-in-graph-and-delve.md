---
title: Office 365 Mandanten Isolierung im Office Graph und vertiefen Sie sich
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
description: 'Zusammenfassung: eine Erläuterung der mandantenisolation im Office Graph und in "vertiefen".'
ms.openlocfilehash: c9e054494e6d71d84a19350bc38e0d3981fede45
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844436"
---
# <a name="tenant-isolation-in-the-office-graph-and-delve"></a>Mandantenisolation in Office Graph und Delve

## <a name="tenant-isolation-in-the-office-graph"></a>Mandanten Isolierung im Office Graph

Die [Office Graph](https://developer.microsoft.com) -Modell Aktivität in Office 365 Diensten, einschließlich Exchange Online, SharePoint Online, jammern, Skype for Business, Azure Active Directory und mehr sowie in externen Diensten wie anderen Microsoft-Diensten oder Drittanbieterdiensten. Office Graph-Komponenten werden in Office 365 verwendet. Das Office Graph stellt eine Sammlung von Inhalten und Aktivitäten sowie die Beziehungen zwischen diesen dar, die in der gesamten Office-Suite stattfinden. Es verwendet ausgefeilte maschinelle Lerntechniken, um Personen mit den relevanten Inhalten, Unterhaltungen und Personen um Sie zu verbinden. Beispielsweise verfügt der Mandanten Index in SharePoint Online über einen Office Graph-Index, der zur Bereitstellung von vertieften Abfragen verwendet wird, das Analyse Verarbeitungsmodul in SharePoint Online dient zum Speichern von Signalen und zum Berechnen von Einblicken, und Exchange Online berechnet die Benutzer Empfängercache als Eingabe in Mandanten Analyse.

Das Office Graph enthält Informationen zu Enterprise-Objekten wie Personen und Dokumenten sowie zu den Beziehungen und Interaktionen zwischen diesen Objekten. Die Beziehungen und Interaktionen werden als *Kanten*dargestellt. Das Office-Diagramm wird nach Mandanten segmentiert, sodass Kanten nur zwischen *Knoten* im gleichen Mandanten vorhanden sein können. Ein *Knoten* ist eine Entität mit einem Uniform Resource Identifier (URI), Knotentyp, Zugriffssteuerungsliste und einer Reihe von Facetten, die *Metadaten* und Ränder enthalten. Jedem Knoten sind Metadaten und Kanten zugeordnet, die in *Facets* wie im allgemeinen Wissens Modell angeordnet sind. *Metadaten* sind benannte Eigenschaften, die auf einem Knoten gespeichert sind, der zum Suchen, Filtern oder analysieren in der Office-Grafik verwendet werden kann. Ein *Facet* ist eine logische Auflistung von Metadaten und Rändern auf einem Knoten. Jedes facet beschreibt einen Aspekt eines Knotens. 

Das Office Graph bringt nicht alle Daten in ein einzelnes Repository; Vielmehr werden Metadaten und Beziehungen zu Daten gespeichert, die an anderer Stelle Leben. Das Office-Diagramm besteht aus mehreren Daten speichern und Verarbeitungskomponenten:

- Der Mandanten Graph-Speicher bietet einen optimierten Massenspeicher für effiziente Analysen.
- Der aktive Inhalts Cache bietet schnellen Zufallszugriff auf aktive Knoten und Kanten, um Benutzeroberflächen zu steuern.
- Der Eingabe Router benachrichtigt die internen und externen Komponenten von Änderungen am Mandanten Graph.

Analysen innerhalb jeder Arbeitsauslastung leiten Einblicke in die Mandanten weiten Berechnungen ab und drücken Sie auf das Mandanten Diagramm. Mandanten Analyse Gründe für alle Aktivitäten in einem Mandanten, um Einblicke in Verhaltensmuster zu erzeugen. Exchange Online berechnet beispielsweise den Empfängercache für jeden Benutzer mit Analysen, die das Postfach jedes Benutzers effizient begründen. Diese benutzerspezifische Analyse erzeugt eine Reihe von *RecipientCache-Rändern* für jede Person, die wiederum in das Mandanten Diagramm verschoben werden. Dadurch bleibt die Analyse Verarbeitung so weit wie möglich an den Quelldaten.

## <a name="tenant-isolation-in-delve"></a>Mandanten Isolierung in "vertiefen"

Wie bereits erwähnt, macht das Office Graph Erfahrungen, die Benutzern dabei helfen, aktuelle Aktivitäten in Ihrem Unternehmen zu entdecken und zusammenzuarbeiten, und stellt eine Entitäts zentrierte Plattform für Analysen zur Verfügung, um Inhalte und Aktivitäten über Arbeitslasten hinweg zu begründen und Jenseits Office 365. Vertiefen ist die erste solche Erfahrung, die von der Office-Grafik angetrieben wird.
Vertiefen ist eine Office 365 Weberfahrung, die Inhalte aus Office 365 und jammern von Unternehmen auf Office 365 Benutzer über die Office Graph-Oberfläche aufweist. Das Weberlebnis zeigt Daten als unterschiedliche Karten an, die jeweils ein bestimmtes Thema aufweisen, beispielsweise *um mich herum* oder *von mir modifiziert*. Jedes Board besteht aus mehreren Dokumentkarten, die einen Zusammenfassungstext und ein Bild aus dem Dokument anzeigen. Die Karte ermöglicht Benutzern das Öffnen des Dokuments oder eine Jammer Seite für das Dokument. Es gibt eine Seite für jede Person in einem Office 365 Mandanten, die die relevantesten Dokumente für diese Person anzeigt, sowie Symbole, die Exchange Online oder Skype for Business für die Interaktion mit dieser Person aufrufen können. Da Sie auf der Office Graph-API basieren, ist Sie von der Mandanten basierten Isolierung dieser API gebunden.