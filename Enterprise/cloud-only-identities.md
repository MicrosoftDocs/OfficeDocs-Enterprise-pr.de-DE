---
title: Office 365 nur-Cloud-Identitäten
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Beschreibt, wie Benutzer und Gruppen erstellt werden, wenn Ihr Office 365-Abonnement nur Cloud-Identitäten verwendet.
ms.openlocfilehash: 7a2aaf7705378da3cbd91b415f07d10b6e039293
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2019
ms.locfileid: "34164610"
---
# <a name="office-365-cloud-only-identities"></a><span data-ttu-id="4f8ab-103">Office 365 nur-Cloud-Identitäten</span><span class="sxs-lookup"><span data-stu-id="4f8ab-103">Office 365 cloud-only identities</span></span>

<span data-ttu-id="4f8ab-104">Bei der reinen cloudbasierten Identität werden alle Ihre Benutzer, Gruppen und Kontakte im Azure Active Directory (Azure AD)-Mandanten Ihres Office 365 Abonnements gespeichert.</span><span class="sxs-lookup"><span data-stu-id="4f8ab-104">With cloud-only identity, all your users, groups, and contacts are stored in the Azure Active Directory (Azure AD) tenant of your Office 365 subscription.</span></span> <span data-ttu-id="4f8ab-105">Hier sind die grundlegenden Komponenten der reinen cloudbasierten Identität.</span><span class="sxs-lookup"><span data-stu-id="4f8ab-105">Here are the basic components of cloud-only identity.</span></span>
 
![](./media/about-office-365-identity/cloud-only-identity.png)

<span data-ttu-id="4f8ab-106">Benutzer und ihre Benutzerkonten in Organisationen können auf verschiedene Arten kategorisiert werden.</span><span class="sxs-lookup"><span data-stu-id="4f8ab-106">Users and their user accounts in organizations can be categorized in a number of ways.</span></span> <span data-ttu-id="4f8ab-107">Einige sind beispielsweise Mitarbeiter und haben einen permanenten Status.</span><span class="sxs-lookup"><span data-stu-id="4f8ab-107">For example, some are employees and have a permanent status.</span></span> <span data-ttu-id="4f8ab-108">Bei einigen handelt es sich um Kreditoren, Auftragnehmer oder Partner mit einem temporären Status.</span><span class="sxs-lookup"><span data-stu-id="4f8ab-108">Some are vendors, contractors, or partners that have a temporary status.</span></span> <span data-ttu-id="4f8ab-109">Einige sind externe Benutzer, die über keine Benutzerkonten verfügen, aber weiterhin Zugriff auf bestimmte Dienste und Ressourcen für die Unterstützung von Interaktion und Zusammenarbeit erhalten müssen.</span><span class="sxs-lookup"><span data-stu-id="4f8ab-109">Some are external users that have no user accounts but must still be granted access to specific services and resources to support interaction and collaboration.</span></span> <span data-ttu-id="4f8ab-110">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="4f8ab-110">For example:</span></span>

- <span data-ttu-id="4f8ab-111">Mandantenkonten stellen Benutzer in Ihrem Unternehmen dar, die Sie für Clouddienste lizenzieren.</span><span class="sxs-lookup"><span data-stu-id="4f8ab-111">Tenant accounts represent users within your organization that you license for cloud services</span></span>

- <span data-ttu-id="4f8ab-112">B2B-Konten (Business-to-Business) stellen Benutzer außerhalb Ihrer Organisation dar, die Sie zur Teilnahme an der Zusammenarbeit einladen, eine Bestandsaufnahme der Benutzertypen für Ihre Organisation durchführen.</span><span class="sxs-lookup"><span data-stu-id="4f8ab-112">Business to Business (B2B) accounts represent users outside your organization that you invite to participate in collaboration Take stock of the types of users to your organization.</span></span> <span data-ttu-id="4f8ab-113">Was sind die Gruppierungen?</span><span class="sxs-lookup"><span data-stu-id="4f8ab-113">What are the groupings?</span></span> <span data-ttu-id="4f8ab-114">Beispielsweise können Sie Benutzer nach allgemeinen Funktionen oder Zweck in Ihrer Organisation gruppieren.</span><span class="sxs-lookup"><span data-stu-id="4f8ab-114">For example, you can group users by high-level function or purpose to your organization.</span></span>

<span data-ttu-id="4f8ab-p104">Darüber hinaus können einige Clouddienste für Benutzer außerhalb Ihres Unternehmens ohne Benutzerkonten freigegeben werden. Sie müssen diese Benutzergruppen ebenfalls identifizieren.</span><span class="sxs-lookup"><span data-stu-id="4f8ab-p104">Additionally, some cloud services can be shared with users outside your organization without any user accounts. You'll need to identify these groups of users as well.</span></span>

<span data-ttu-id="4f8ab-117">Sie können Gruppen in Azure AD für verschiedene Zwecke verwenden, die die Verwaltung Ihrer Cloud-Umgebung vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="4f8ab-117">You can use groups in Azure AD for several purposes that simplify management of your cloud environment.</span></span> <span data-ttu-id="4f8ab-118">Beispielsweise können Sie mit Azure Ad Gruppen Folgendes tun:</span><span class="sxs-lookup"><span data-stu-id="4f8ab-118">For example, with Azure AD groups, you can:</span></span>

- <span data-ttu-id="4f8ab-119">Verwenden Sie die Gruppenbasierte Lizenzierung, um Ihren Benutzerkonten automatisch Lizenzen für Office 365 zuzuweisen, sobald diese hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="4f8ab-119">Use group-based licensing to assign licenses for Office 365 to your user accounts automatically as soon as they are added.</span></span>
- <span data-ttu-id="4f8ab-120">Sie können bestimmten Gruppen auf Grundlage von Benutzerkontoattributen wie Abteilung Benutzerkonten dynamisch hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="4f8ab-120">Add user accounts to specific groups dynamically based on user account attributes, such as department.</span></span>
- <span data-ttu-id="4f8ab-121">Sie können automatisch SaaS-Anwendungen für Benutzer bereitstellen und den Zugriff auf diese Anwendungen mit der mehrstufigen Authentifizierung und anderen Regeln für bedingten Zugriff schützen.</span><span class="sxs-lookup"><span data-stu-id="4f8ab-121">Automatically provision users for Software as a Service (SaaS) applications and to protect access to those applications with multi-factor authentication and other conditional access rules.</span></span>
- <span data-ttu-id="4f8ab-122">Bereitstellungsberechtigungen und Zugriffsebenen für SharePoint Online Teamwebsites.</span><span class="sxs-lookup"><span data-stu-id="4f8ab-122">Provision permissions and levels of access for SharePoint Online team sites.</span></span>

<span data-ttu-id="4f8ab-123">Sie können neue ***Benutzer*** mit folgendem erstellen:</span><span class="sxs-lookup"><span data-stu-id="4f8ab-123">You can create new ***users*** with:</span></span>

- [<span data-ttu-id="4f8ab-124">Das Microsoft 365 Admin Center</span><span class="sxs-lookup"><span data-stu-id="4f8ab-124">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/add-users/add-users)
- [<span data-ttu-id="4f8ab-125">Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="4f8ab-125">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell)

<span data-ttu-id="4f8ab-126">Sie können mit folgendem neue ***Gruppen*** erstellen:</span><span class="sxs-lookup"><span data-stu-id="4f8ab-126">You can create new ***groups*** with:</span></span>

- [<span data-ttu-id="4f8ab-127">Das Microsoft 365 Admin Center</span><span class="sxs-lookup"><span data-stu-id="4f8ab-127">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/create-groups/create-groups)
- [<span data-ttu-id="4f8ab-128">Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="4f8ab-128">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-groups-with-powershell)


## <a name="next-step-for-cloud-only-identities"></a><span data-ttu-id="4f8ab-129">Nächster Schritt für nur-Cloud-Identitäten</span><span class="sxs-lookup"><span data-stu-id="4f8ab-129">Next step for cloud-only identities</span></span>

[<span data-ttu-id="4f8ab-130">Zuweisen von Lizenzen für Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="4f8ab-130">Assign licenses to user accounts</span></span>](assign-licenses-to-user-accounts.md)
