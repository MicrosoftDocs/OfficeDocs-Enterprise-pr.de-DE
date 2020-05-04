---
title: Zuweisen von Office 365 Lizenzen zu Benutzerkonten
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/03/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Beschreibt, wie Benutzerkonten Office 365 Lizenzen entweder einzeln oder basierend auf der Gruppenmitgliedschaft zuweisen.
ms.openlocfilehash: 77e6f6c20e9eeff11487a31cb2d616abbed42601
ms.sourcegitcommit: 11751463c952f57f397b886eebfbd37790d461af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2020
ms.locfileid: "44009380"
---
# <a name="assign-office-365-licenses-to-user-accounts"></a><span data-ttu-id="66108-103">Zuweisen von Office 365 Lizenzen zu Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="66108-103">Assign Office 365 licenses to user accounts</span></span>

<span data-ttu-id="66108-104">*Dieser Artikel gilt sowohl für Office 365 Enterprise als auch für Microsoft 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="66108-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="66108-105">Für das nur-Cloud-Identitätsmodell können Sie den Benutzerkonten Office 365 Lizenzen zuweisen, je nachdem, wie Sie erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="66108-105">For the cloud-only identity model, you can assign Office 365 licenses to user accounts as they are created, depending on how you create them.</span></span>

<span data-ttu-id="66108-106">Wenn Active Directory-Domänendienste (AD DS) Benutzerkonten zum ersten Mal synchronisiert werden, wird für das hybride Identitätsmodell nicht automatisch eine Office 365 Lizenz zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="66108-106">For the hybrid identity model, when Active Directory Domain Services (AD DS) user accounts are synchronized for the first time, they are not automatically assigned an Office 365 license.</span></span>

<span data-ttu-id="66108-107">In beiden Fällen müssen Sie Benutzerkonten eine Lizenz zuweisen, damit Ihre Benutzer auf Office 365 Dienste wie e-Mail und Microsoft Teams zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="66108-107">In either case, you must assign a license to user accounts so your users can access Office 365 services, such as email and Microsoft Teams.</span></span>

<span data-ttu-id="66108-108">Sie können Benutzerkonten entweder einzeln oder automatisch über die Gruppenmitgliedschaft Lizenzen zuweisen.</span><span class="sxs-lookup"><span data-stu-id="66108-108">You can assign licenses to user accounts either individually or automatically through group membership.</span></span>

<span data-ttu-id="66108-109">Um einzelnen Benutzerkonten Office 365 Lizenzen zuzuweisen, können Sie Folgendes verwenden:</span><span class="sxs-lookup"><span data-stu-id="66108-109">To assign Office 365 licenses to individual user accounts, you can use:</span></span>

- [<span data-ttu-id="66108-110">Das Microsoft 365 Admin Center</span><span class="sxs-lookup"><span data-stu-id="66108-110">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/subscriptions-and-billing/assign-licenses-to-users)
- [<span data-ttu-id="66108-111">Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="66108-111">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/assign-licenses-to-user-accounts-with-office-365-powershell)

<span data-ttu-id="66108-112">Informationen zur automatischen Zuweisung von Lizenzen finden Sie unter [Group-based licensing in Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).</span><span class="sxs-lookup"><span data-stu-id="66108-112">For automatic license assignment, see [group-based licensing in Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).</span></span>

## <a name="next-steps"></a><span data-ttu-id="66108-113">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="66108-113">Next steps</span></span>

<span data-ttu-id="66108-114">Mit dem vollständigen Benutzer kontensatz, dem Lizenzen zugewiesen wurden, können Sie nun folgende Aufgaben durchsetzen:</span><span class="sxs-lookup"><span data-stu-id="66108-114">With the full set of user accounts that have been assigned licenses, you are now ready to:</span></span>

- [<span data-ttu-id="66108-115">Implementieren der Sicherheit</span><span class="sxs-lookup"><span data-stu-id="66108-115">Implement security</span></span>](https://docs.microsoft.com/microsoft-365/security/office-365-security/security-roadmap)
- [<span data-ttu-id="66108-116">Bereitstellen von Client Software wie Microsoft 365-apps</span><span class="sxs-lookup"><span data-stu-id="66108-116">Deploy client software, such as Microsoft 365 Apps</span></span>](https://docs.microsoft.com/DeployOffice/deployment-guide-microsoft-365-apps)
- [<span data-ttu-id="66108-117">Einrichten der Verwaltung mobiler Geräte in Office 365</span><span class="sxs-lookup"><span data-stu-id="66108-117">Set up Mobile Device Management in Office 365</span></span>](https://support.office.com/article/set-up-mobile-device-management-mdm-in-office-365-dd892318-bc44-4eb1-af00-9db5430be3cd)
- [<span data-ttu-id="66108-118">Konfigurieren von Diensten und Anwendungen</span><span class="sxs-lookup"><span data-stu-id="66108-118">Configure services and applications</span></span>](configure-services-and-applications.md)
