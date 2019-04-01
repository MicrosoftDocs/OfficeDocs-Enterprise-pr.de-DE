---
title: Multi-Geo-Funktionen in OneDrive und SharePoint Online
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: Erweitern Sie Ihre Office 365-Präsenz auf mehrere geografische Regionen mit Multi-Geo-Funktionen in OneDrive Online.
ms.openlocfilehash: 15dcb44943fa1bf331ef6260946f7c3a632d3c4a
ms.sourcegitcommit: dffbcfb1cbc9776a29229a787c1eab4192e55cff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2019
ms.locfileid: "30948586"
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online"></a><span data-ttu-id="9d544-103">Multi-Geo-Funktionen in OneDrive und SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="9d544-103">Multi-Geo Capabilities in OneDrive and SharePoint Online in Office 365</span></span>

<span data-ttu-id="9d544-104">Multi-Geo-Funktionen in OneDrive und SharePoint Online bieten Kontrolle über das Land oder die Region, in dem/der freigegebene Ressourcen wie SharePoint-Teamsites und Office 365-Gruppenpostfächer gespeichert sind.</span><span class="sxs-lookup"><span data-stu-id="9d544-104">Multi-Geo capabilities in OneDrive and SharePoint Online enables control of the country or region where shared resources like SharePoint team sites and Office 365 Group mailboxes are stored at rest.</span></span>

<span data-ttu-id="9d544-105">Benutzer, Gruppenpostfächer und SharePoint-Sites haben Preferred Data Locations (PDLs), die den geografischen Ort für die verknüpften Daten angeben.</span><span class="sxs-lookup"><span data-stu-id="9d544-105">Each user, Group mailbox, and SharePoint site has a Preferred Data Location (PDL) which denotes the geo location where related data is to be stored.</span></span> <span data-ttu-id="9d544-106">Die personenbezogenen Daten von Benutzern (Exchange-Posteingang und OneDrive) können zusammen mit beliebigen Office 365-Gruppen oder SharePoint-Sites, die sie erstellen, am angegebenen geografischen Ort gespeichert werden, um Datenaufbewahrungsanforderungen zu erfüllen.</span><span class="sxs-lookup"><span data-stu-id="9d544-106">Users' personal data (Exchange mailbox and OneDrive) along with any Office 365 Groups or SharePoint sites that they create can be stored in the specified geo location to meet data residency requirements.</span></span> <span data-ttu-id="9d544-107">Sie können [verschiedene Administratoren für jeden geografischen Ort angeben](add-a-sharepoint-geo-admin.md).</span><span class="sxs-lookup"><span data-stu-id="9d544-107">You can [specify different administrators for each geo location](add-a-sharepoint-geo-admin.md).</span></span>

<span data-ttu-id="9d544-108">Benutzer erhalten die vertraute Oberfläche bei Verwendung von Office 365-Diensten, einschließlich Office-Anwendungen, OneDrive und Suche.</span><span class="sxs-lookup"><span data-stu-id="9d544-108">Users get a seamless experience when using Office 365 services, including Office applications, OneDrive, and Search.</span></span> <span data-ttu-id="9d544-109">Details finden Sie unter [Benutzererfahrung in einer Multi-Geo-Umgebung](multi-geo-user-experience.md).</span><span class="sxs-lookup"><span data-stu-id="9d544-109">See [User experience in a multi-geo environment](multi-geo-user-experience.md) for details.</span></span>

## <a name="onedrive"></a><span data-ttu-id="9d544-110">OneDrive</span><span class="sxs-lookup"><span data-stu-id="9d544-110">OneDrive</span></span>

<span data-ttu-id="9d544-111">Das OneDrive jedes Benutzers kann in Einklang mit der PDL an einem Satellitenort bereitgestellt oder [von einem Administrator dorthin verschoben werden](move-onedrive-between-geo-locations.md).</span><span class="sxs-lookup"><span data-stu-id="9d544-111">Each user's OneDrive can be provisioned in or [moved by an administrator](move-onedrive-between-geo-locations.md) to a satellite location in accordance with the user's PDL.</span></span> <span data-ttu-id="9d544-112">Persönliche Dateien verbleiben an diesem geografischen Ort, obwohl sie mit Benutzern an anderen geografischen Orten geteilt werden können.</span><span class="sxs-lookup"><span data-stu-id="9d544-112">Personal files are then kept in that geo location, though they can be shared with users in other geo locations.</span></span>

## <a name="sites-and-groups"></a><span data-ttu-id="9d544-113">Sites und Gruppen</span><span class="sxs-lookup"><span data-stu-id="9d544-113">Active Directory Sites and Routing Groups tab</span></span>

<span data-ttu-id="9d544-114">Wenn ein Benutzer eine mit einer SharePoint-Gruppe verbundene Site erstellt, wird ihre PDL verwendet, um den geografischen Ort zu bestimmen, an dem die Site und ihr zugehöriges Gruppenpostfach erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="9d544-114">When a user creates a SharePoint group-connected site, their PDL is used to determine the geo location where the site and its associated Group mailbox is created.</span></span> <span data-ttu-id="9d544-115">(Wenn der PDL-Wert des Benutzers nicht festgelegt oder auf den geografischen Ort festgelegt wurde, der nicht als Satellitenort konfiguriert wurde, werden Site und Postfach am zentralen Ort erstellt.)</span><span class="sxs-lookup"><span data-stu-id="9d544-115">(If the user's PDL value hasn't been set, or has been set to geo location that hasn't been configured as a satellite location, then the site and mailbox are created in the central location.)</span></span>

<span data-ttu-id="9d544-116">Andere Office 365-Dienste als Exchange, OneDrive und SharePoint sind nicht Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="9d544-116">Office 365 services other than Exchange, OneDrive, and SharePoint are not Multi-Geo.</span></span> <span data-ttu-id="9d544-117">Office 365-Gruppen, die jedoch von diesen Diensten erstellt werden, erhalten die PDL des Erstellers. Exchange-Gruppenpostfach und SharePoint O365-Gruppensite werden am entsprechenden geografischen Ort bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="9d544-117">However, Office 365 Groups that are created by these services will be stamped with the PDL of the creator and their Exchange Group mailbox and SharePoint O365 Group Site provisioned in the corresponding geo.</span></span> 

## <a name="managing-the-multi-geo-environment"></a><span data-ttu-id="9d544-118">Verwalten der Multi-Geo-Umgebung</span><span class="sxs-lookup"><span data-stu-id="9d544-118">Managing the multi-geo environment</span></span>

<span data-ttu-id="9d544-119">Das Einrichten und Verwalten Ihrer Multi-Geo-Umgebung erfolgt über das SharePoint-Admin Center.</span><span class="sxs-lookup"><span data-stu-id="9d544-119">Setting up and managing your multi-geo environment is done through the SharePoint admin center.</span></span> 

![Screenshot der Seite mit geografischen Orten im SharePoint-Admin Center](media/sharepoint-multi-geo-admin-center.png)

<span data-ttu-id="9d544-121">(Für einige Aktionen wie das Verschieben einer SharePoint- oder OneDrive-Site ist Microsoft PowerShell erforderlich.)</span><span class="sxs-lookup"><span data-stu-id="9d544-121">(Some actions, such as moving a SharePoint site or a OneDrive site require Microsoft PowerShell.)</span></span>

## <a name="see-also"></a><span data-ttu-id="9d544-122">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="9d544-122">See also</span></span>

[<span data-ttu-id="9d544-123">Aka.ms/GetMultiGeo </span><span class="sxs-lookup"><span data-stu-id="9d544-123">Aka.ms/GetMultiGeo </span></span>](https://Aka.ms/GetMultiGeo)

[<span data-ttu-id="9d544-124">Verwalten einer Multi-Geo-Umgebung</span><span class="sxs-lookup"><span data-stu-id="9d544-124">Administering a multi-geo environment</span></span>](administering-a-multi-geo-environment.md)

[<span data-ttu-id="9d544-125">SharePoint-Speicherkontingente in Multi-Geo-Umgebungen</span><span class="sxs-lookup"><span data-stu-id="9d544-125">SharePoint storage quotas in multi-geo environments</span></span>](sharepoint-multi-geo-storage-quota.md)

[<span data-ttu-id="9d544-126">Verwalten von Exchange Online-Postfächern in einer Multi-Geo-Umgebung</span><span class="sxs-lookup"><span data-stu-id="9d544-126">Administering Exchange Online mailboxes in a multi-geo environment</span></span>](administering-exchange-online-multi-geo.md)
