---
title: Azure-Integration in Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/09/2019
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: a5efce5d-9c9c-4190-b61b-fd273c1d425f
description: Ihr Office 365-Abonnement enthält ein Abonnement für Azure AD. Integrieren Sie Office 365 mit Azure AD, wenn Sie die Kennwortsynchronisierung oder das einmalige Anmelden mit Ihrer lokalen Umgebung wünschen.
ms.openlocfilehash: 44231420ee92c37f14874d6fb0f9e926d8d4369d
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2019
ms.locfileid: "38745788"
---
# <a name="azure-integration-with-office-365"></a><span data-ttu-id="b82f9-104">Azure-Integration in Office 365</span><span class="sxs-lookup"><span data-stu-id="b82f9-104">Azure integration with Office 365</span></span>

<span data-ttu-id="b82f9-105">*Dieser Artikel bezieht sich sowohl auf Office 365 Enterprise als auch auf Microsoft 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="b82f9-105">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="b82f9-106">Office 365 verwendet Azure Active Directory (Azure AD), um Benutzeridentitäten hinter den Kulissen zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="b82f9-106">Office 365 uses Azure Active Directory (Azure AD) to manage user identities behind the scenes.</span></span> <span data-ttu-id="b82f9-107">Ihr Office 365-Abonnement enthält ein kostenloses Abonnement für Azure AD, damit Sie Office 365 mit Azure AD integrieren können, wenn Sie Kennwörter synchronisieren oder einmaliges Anmelden mit Ihrer lokalen Umgebung einrichten möchten.</span><span class="sxs-lookup"><span data-stu-id="b82f9-107">Your Office 365 subscription includes a free subscription to Azure AD so that you can integrate Office 365 with Azure AD if you want to sync passwords or set up single sign-on with your on-premises environment.</span></span> <span data-ttu-id="b82f9-108">Sie können auch erweiterte Funktionen erwerben, um Ihre Konten besser zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="b82f9-108">You can also buy advanced features to better manage your accounts.</span></span>
  
<span data-ttu-id="b82f9-109">Azure bietet auch andere Funktionen wie das Verwalten integrierter apps, mit denen Sie Ihre Office 365 Abonnements erweitern und anpassen können.</span><span class="sxs-lookup"><span data-stu-id="b82f9-109">Azure also offers other functionality, like managing integrated apps, that you can use to extend and customize your Office 365 subscriptions.</span></span>
  
<span data-ttu-id="b82f9-110">Sie können die Azure AD-Bereitstellungs Ratgeber für eine gesteuerte Setup-und Konfigurationsumgebung verwenden (Sie müssen bei Office 365 angemeldet sein):</span><span class="sxs-lookup"><span data-stu-id="b82f9-110">You can use the Azure AD deployment advisors for a guided setup and configuration experience (you must be signed in to Office 365):</span></span>

 - [<span data-ttu-id="b82f9-111">Azure AD Connect-Ratgeber</span><span class="sxs-lookup"><span data-stu-id="b82f9-111">Azure AD Connect advisor</span></span>](https://aka.ms/aadconnectpwsync)
 - [<span data-ttu-id="b82f9-112">Bereitstellungsratgeber für AD FS</span><span class="sxs-lookup"><span data-stu-id="b82f9-112">AD FS deployment advisor</span></span>](https://aka.ms/adfsguidance)
 - [<span data-ttu-id="b82f9-113">Leitfaden für Azure AD Premium-Setup</span><span class="sxs-lookup"><span data-stu-id="b82f9-113">Azure AD Premium setup guide</span></span>](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-office-365-identity-management"></a><span data-ttu-id="b82f9-114">Azure AD Editionen und Office 365 Identitätsverwaltung</span><span class="sxs-lookup"><span data-stu-id="b82f9-114">Azure AD editions and Office 365 identity management</span></span>

<span data-ttu-id="b82f9-115">Wenn Sie über ein kostenpflichtiges Abonnement für Office 365 verfügen, haben Sie auch ein kostenloses Abonnement für Azure AD.</span><span class="sxs-lookup"><span data-stu-id="b82f9-115">If you have a paid subscription to Office 365, you also have a free subscription to Azure AD.</span></span> <span data-ttu-id="b82f9-116">Sie können Azure AD verwenden, um Benutzer-und Gruppenkonten zu erstellen und zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="b82f9-116">You can use Azure AD to create and manage user and group accounts.</span></span> <span data-ttu-id="b82f9-117">Um dieses Abonnement zu aktivieren, müssen Sie eine einmalige Registrierung durchführen.</span><span class="sxs-lookup"><span data-stu-id="b82f9-117">To activate this subscription you have to complete a one-time registration.</span></span> <span data-ttu-id="b82f9-118">Anschließend können Sie über Ihr Office 365-Verwaltungsportal auf Azure AD zugreifen.</span><span class="sxs-lookup"><span data-stu-id="b82f9-118">Afterward, you can access Azure AD from your Office 365 admin portal.</span></span> 

<span data-ttu-id="b82f9-119">Anweisungen finden Sie unter [Verwenden Ihres kostenlosen Azure AD-Abonnements](https://go.microsoft.com/fwlink/p/?LinkId=617127).</span><span class="sxs-lookup"><span data-stu-id="b82f9-119">For instructions, see [use your free Azure AD subscription](https://go.microsoft.com/fwlink/p/?LinkId=617127).</span></span> <span data-ttu-id="b82f9-120">Befolgen Sie die Anweisungen zum Registrieren des kostenlosen Azure AD Abonnements, das mit Ihrem Abonnement für Office 365 geliefert wird.</span><span class="sxs-lookup"><span data-stu-id="b82f9-120">Follow the instructions to register the free Azure AD subscription that comes with your subscription to Office 365.</span></span> <span data-ttu-id="b82f9-121">Gehen Sie nicht direkt zu Azure.Microsoft.com, um sich anzumelden, oder Sie erhalten ein Test-oder kostenpflichtiges Abonnement für Microsoft Azure, das von Ihrem kostenlosen für Office 365 getrennt ist.</span><span class="sxs-lookup"><span data-stu-id="b82f9-121">Don't go directly to azure.microsoft.com to sign up or you'll end up with a trial or paid subscription to Microsoft Azure that is separate from your free one for Office 365.</span></span> 
  
<span data-ttu-id="b82f9-122">Mit dem kostenlosen Abonnement können Sie mit lokalen Verzeichnissen synchronisieren, einmaliges Anmelden einrichten und mit vielen Software als Dienstanwendungen wie Salesforce, Dropbox und vieles mehr synchronisieren.</span><span class="sxs-lookup"><span data-stu-id="b82f9-122">With the free subscription you can synchronize with on-premises directories, set up single sign-on, and synchronize with many software as service applications, such as Salesforce, DropBox and many more.</span></span>
  
<span data-ttu-id="b82f9-123">Wenn Sie erweiterte Active Directory-Domänendienste (AD DS) Funktionalität, bidirektionale Synchronisierung und andere Verwaltungsfunktionen wünschen, können Sie Ihr kostenloses Abonnement auf ein kostenpflichtiges Premium-Abonnement upgraden.</span><span class="sxs-lookup"><span data-stu-id="b82f9-123">If you want enhanced Active Directory Domain Services (AD DS) functionality, bi-directional synchronization, and other management capabilities, you can upgrade your free subscription to a paid premium subscription.</span></span> <span data-ttu-id="b82f9-124">Ausführliche Informationen finden Sie unter [Azure Active Directory Editions](https://azure.microsoft.com/pricing/details/active-directory/).</span><span class="sxs-lookup"><span data-stu-id="b82f9-124">For details see [Azure Active Directory editions](https://azure.microsoft.com/pricing/details/active-directory/).</span></span>
  
<span data-ttu-id="b82f9-125">Weitere Informationen zu Office 365 und Azure AD finden Sie unter [Understanding Office 365 Identity and Azure Active Directory](https://docs.microsoft.com/office365/enterprise/about-office-365-identity).</span><span class="sxs-lookup"><span data-stu-id="b82f9-125">For more information about Office 365 and Azure AD, see [Understanding Office 365 Identity and Azure Active Directory](https://docs.microsoft.com/office365/enterprise/about-office-365-identity).</span></span>
  
## <a name="extend-the-capabilities-of-your-office-365-tenant"></a><span data-ttu-id="b82f9-126">Erweitern der Funktionen des Office 365 Mandanten</span><span class="sxs-lookup"><span data-stu-id="b82f9-126">Extend the capabilities of your Office 365 tenant</span></span>

|<span data-ttu-id="b82f9-127">**Feature**</span><span class="sxs-lookup"><span data-stu-id="b82f9-127">**Feature**</span></span>|<span data-ttu-id="b82f9-128">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="b82f9-128">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="b82f9-129">Integrierte apps</span><span class="sxs-lookup"><span data-stu-id="b82f9-129">Integrated apps</span></span>  <br/> |<span data-ttu-id="b82f9-130">Sie können einzelnen apps Zugriff auf Ihre Office 365 Daten gewähren, wie e-Mail, Kalender, Kontakte, Benutzer, Gruppen, Dateien und Ordner.</span><span class="sxs-lookup"><span data-stu-id="b82f9-130">You can grant individual apps access to your Office 365 data, like mail, calendars, contacts, users, groups, files, and folders.</span></span> <span data-ttu-id="b82f9-131">Sie können diese apps auch auf globaler Administratorebene autorisieren und Sie für Ihr gesamtes Unternehmen zur Verfügung stellen, indem Sie die apps in Azure AD registrieren.</span><span class="sxs-lookup"><span data-stu-id="b82f9-131">You can also authorize these apps at global admin level and make them available to your entire company by registering the apps in Azure AD.</span></span> <span data-ttu-id="b82f9-132">Ausführliche Informationen finden Sie unter [integrierte apps und Azure AD für Office 365 Administratoren](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).</span><span class="sxs-lookup"><span data-stu-id="b82f9-132">For details see [Integrated Apps and Azure AD for Office 365 administrators](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).</span></span>  <br/> <span data-ttu-id="b82f9-133">Siehe auch [einmaliges Anmelden bei Anwendungen](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span><span class="sxs-lookup"><span data-stu-id="b82f9-133">Also see [single sign-on to applications](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span></span>  <br/> |
|<span data-ttu-id="b82f9-134">PowerApps</span><span class="sxs-lookup"><span data-stu-id="b82f9-134">PowerApps</span></span>  <br/> | <span data-ttu-id="b82f9-135">Power apps sind fokussierte Apps für mobile Geräte, die mit Ihren vorhandenen Datenquellen wie SharePoint-Listen und anderen Daten-apps verbunden werden können.</span><span class="sxs-lookup"><span data-stu-id="b82f9-135">Power apps are focused apps for mobile devices that can connect to your existing data sources like SharePoint lists, and other data apps.</span></span> <span data-ttu-id="b82f9-136">Weitere Informationen finden Sie unter [Erstellen eines PowerApp für eine Liste auf SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) -und [PowerApps-Seite](https://powerapps.microsoft.com/) .</span><span class="sxs-lookup"><span data-stu-id="b82f9-136">See [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) for details.</span></span>  <br/> |
   
<span data-ttu-id="b82f9-137">Weitere Informationen finden Sie unter [integrierte apps und Azure AD für Office 365 Administratoren](integrated-apps-and-azure-ads.md) und [Azure AD Anwendungskatalog und einmaliges Anmelden](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).</span><span class="sxs-lookup"><span data-stu-id="b82f9-137">Learn more at [Integrated Apps and Azure AD for Office 365 administrators](integrated-apps-and-azure-ads.md) and [Azure AD application gallery and single-sign-on](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).</span></span>

## <a name="see-also"></a><span data-ttu-id="b82f9-138">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="b82f9-138">See also</span></span>

[<span data-ttu-id="b82f9-139">Übersicht zu Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="b82f9-139">Microsoft 365 Enterprise overview</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
