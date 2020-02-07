---
title: Office 365 Umgang mit Datenbeschädigung
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
description: Eine Erläuterung der Datenbeschädigung in Office 365 und der Bemühungen von Microsoft um Verhinderung und Wiederherstellung.
ms.openlocfilehash: 1477ab4dca0f9126eb04b76b9f8f65ff0b5eefc8
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844486"
---
# <a name="dealing-with-data-corruption-in-office-365"></a><span data-ttu-id="daef8-103">Umgang mit Datenbeschädigung in Office 365</span><span class="sxs-lookup"><span data-stu-id="daef8-103">Dealing with Data Corruption in Office 365</span></span>

<span data-ttu-id="daef8-104">Einer der Herausforderungen bei der Ausführung eines umfangreichen Cloud-Diensts besteht darin, dass angesichts der großen Datenmengen und unabhängigen Systeme Datenbeschädigungen umgangen werden.</span><span class="sxs-lookup"><span data-stu-id="daef8-104">One of the challenging aspects of running a large-scale cloud service is how to handle data corruption, given the large volume of data and independent systems.</span></span> <span data-ttu-id="daef8-105">Die Beschädigung von Daten kann durch folgende Ursachen verursacht werden:</span><span class="sxs-lookup"><span data-stu-id="daef8-105">Data corruption can be caused by:</span></span>

- <span data-ttu-id="daef8-106">Anwendungs-oder Infrastrukturfehler, die einen oder alle Anwendungszustände beschädigen</span><span class="sxs-lookup"><span data-stu-id="daef8-106">Application or infrastructure bugs, corrupting some or all of the application state</span></span>
- <span data-ttu-id="daef8-107">Hardware Probleme, die zu Datenverlusten oder zum Lesen von Daten führen können</span><span class="sxs-lookup"><span data-stu-id="daef8-107">Hardware issues that result in lost data or an inability to read data</span></span>
- <span data-ttu-id="daef8-108">Menschliche Betriebsfehler</span><span class="sxs-lookup"><span data-stu-id="daef8-108">Human operational errors</span></span>
- <span data-ttu-id="daef8-109">Böswillige Hacker und verärgerte Mitarbeiter</span><span class="sxs-lookup"><span data-stu-id="daef8-109">Malicious hackers and disgruntled employees</span></span>
- <span data-ttu-id="daef8-110">Vorfälle in externen Diensten, die zu einem Datenverlust führen</span><span class="sxs-lookup"><span data-stu-id="daef8-110">Incidents in external services that result in some loss of data</span></span>

<span data-ttu-id="daef8-111">Da höhere Ausfallsicherheit in der Datenintegrität weniger Daten Beschädigungs Vorfälle bedeutet, hat Microsoft in Office 365 Schutzmechanismen integriert, um zu verhindern, dass eine Beschädigung stattfindet, sowie von Systemen und Prozessen, mit denen Daten wiederhergestellt werden können, wenn dies der Fall ist.</span><span class="sxs-lookup"><span data-stu-id="daef8-111">Because greater resiliency in data integrity means fewer data corruption incidents, Microsoft has built into Office 365 protection mechanisms to prevent corruption from happening, as well as systems and processes that enable us to recover data if it does.</span></span> <span data-ttu-id="daef8-112">Checks and Processes sind in den verschiedenen Phasen des Engineering-Release-Prozesses vorhanden, um die Ausfallsicherheit bei Datenbeschädigung zu verbessern, einschließlich:</span><span class="sxs-lookup"><span data-stu-id="daef8-112">Checks and processes exist within the various stages of the engineering release process to increase resiliency against data corruption, including:</span></span>

- <span data-ttu-id="daef8-113">System Design</span><span class="sxs-lookup"><span data-stu-id="daef8-113">System Design</span></span>
- <span data-ttu-id="daef8-114">Code Organisation und-Struktur</span><span class="sxs-lookup"><span data-stu-id="daef8-114">Code organization and structure</span></span>
- <span data-ttu-id="daef8-115">Code Überprüfung</span><span class="sxs-lookup"><span data-stu-id="daef8-115">Code review</span></span>
- <span data-ttu-id="daef8-116">Komponententests, Integrationstests und Systemtests</span><span class="sxs-lookup"><span data-stu-id="daef8-116">Unit tests, integration tests, and system tests</span></span>
- <span data-ttu-id="daef8-117">Trip Wires-Tests/Tore</span><span class="sxs-lookup"><span data-stu-id="daef8-117">Trip wires tests/gates</span></span>

<span data-ttu-id="daef8-118">In Office 365 Produktionsumgebungen stellt die Peer Replikation zwischen Rechenzentren sicher, dass es immer mehrere Live Kopien aller Daten gibt.</span><span class="sxs-lookup"><span data-stu-id="daef8-118">Within Office 365 production environments, peer replication between datacenters ensures that there are always multiple live copies of any data.</span></span> <span data-ttu-id="daef8-119">Standard Bilder und-Skripts werden verwendet, um verloren gegangene Server wiederherzustellen, und replizierte Daten werden verwendet, um Kundendaten wiederherzustellen.</span><span class="sxs-lookup"><span data-stu-id="daef8-119">Standard images and scripts are used to recover lost servers, and replicated data is used to restore customer data.</span></span> <span data-ttu-id="daef8-120">Aufgrund der integrierten Tests und Prozesse für die Ausfallsicherheit von Daten hält Microsoft Sicherungen nur von Office 365 Dokumentation zum Informationssystem (einschließlich sicherheitsbezogener Dokumentation) mit integrierter Replikation in SharePoint Online und unserem internen Code. Repository-Tool, Quell Depot.</span><span class="sxs-lookup"><span data-stu-id="daef8-120">Because of the built-in data resiliency checks and processes, Microsoft maintains backups only of Office 365 information system documentation (including security-related documentation), using built-in replication in SharePoint Online and our internal code repository tool, Source Depot.</span></span> <span data-ttu-id="daef8-121">Die Systemdokumentation wird in SharePoint Online gespeichert, und das Quell Depot enthält System-und Anwendungsbilder.</span><span class="sxs-lookup"><span data-stu-id="daef8-121">System documentation is stored in SharePoint Online, and Source Depot contains system and application images.</span></span> <span data-ttu-id="daef8-122">Sowohl SharePoint Online als auch das Quell Depot verwenden die Versionsverwaltung und werden nahezu in Echtzeit repliziert.</span><span class="sxs-lookup"><span data-stu-id="daef8-122">Both SharePoint Online and Source Depot use versioning and are replicated in near real time.</span></span>
