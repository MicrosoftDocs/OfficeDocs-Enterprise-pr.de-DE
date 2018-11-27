---
title: Azure-Integration in Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: a5efce5d-9c9c-4190-b61b-fd273c1d425f
description: Ihr Office 365-Abonnement umfasst ein Abonnement für Azure Active Directory. Integrieren Sie Office 365 mit Azure AD, wenn Sie mit Ihrer lokalen Umgebung kennwortsynchronisierung oder einmaliges Anmelden möchten.
ms.openlocfilehash: 8b7af5ba8d5106900384369a3e6548af40f9e201
ms.sourcegitcommit: 9c493c4e18e83491d106c5e9bab55d1a89298879
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2018
ms.locfileid: "26674419"
---
# <a name="azure-integration-with-office-365"></a><span data-ttu-id="081ef-104">Azure-Integration in Office 365</span><span class="sxs-lookup"><span data-stu-id="081ef-104">Azure integration with Office 365</span></span>

<span data-ttu-id="081ef-p102">Office 365 verwendet Azure Active Directory (AD Azure) zur Verwaltung von Benutzeridentitäten im Hintergrund. Ihr Office 365-Abonnement umfasst ein kostenloses Abonnement von Azure AD, damit Sie Office 365 mit Azure AD integrieren können, wenn Sie Synchronisieren von Kennwörtern oder einmaliges Anmelden mit Ihrer lokalen Umgebung einrichten möchten. Sie können auch erweiterte Funktionen, um Ihre Konten besser zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="081ef-p102">Office 365 uses Azure Active Directory (Azure AD) to manage user identities behind the scenes. Your Office 365 subscription includes a free subscription to Azure AD so that you can integrate Office 365 with Azure AD if you want to sync passwords or set up single sign-on with your on-premises environment. You can also buy advanced features to better manage your accounts.</span></span>
  
<span data-ttu-id="081ef-108">Azure bietet auch andere Funktionen, wie das Verwalten von integrierten-apps, die Sie erweitern und Anpassen Ihrer Office 365-Abonnements verwenden können.</span><span class="sxs-lookup"><span data-stu-id="081ef-108">Azure also offers other functionality, like managing integrated apps, that you can use to extend and customize your Office 365 subscriptions.</span></span>
  
<span data-ttu-id="081ef-109">Die Berater Azure AD-Bereitstellung können eine geführte Einrichtung und Konfiguration wünschen:</span><span class="sxs-lookup"><span data-stu-id="081ef-109">You can use the Azure AD deployment advisors for a guided setup and configuration experience:</span></span>
 - [<span data-ttu-id="081ef-110">Azure Active Directory verbinden advisor</span><span class="sxs-lookup"><span data-stu-id="081ef-110">Azure AD Connect advisor</span></span>](https://aka.ms/aadconnectpwsync)
 - [<span data-ttu-id="081ef-111">AD FS-Bereitstellung advisor</span><span class="sxs-lookup"><span data-stu-id="081ef-111">AD FS deployment advisor</span></span>](https://aka.ms/adfsguidance)
 - [<span data-ttu-id="081ef-112">Azure RMS-Bereitstellungs-Assistenten</span><span class="sxs-lookup"><span data-stu-id="081ef-112">Azure RMS Deployment Wizard</span></span>](https://aka.ms/azuremsguidance)
 - [<span data-ttu-id="081ef-113">Handbuch für Azure AD-Premium</span><span class="sxs-lookup"><span data-stu-id="081ef-113">Azure AD Premium setup guide</span></span>](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-office-365-identity-management"></a><span data-ttu-id="081ef-114">Azure AD-Editionen und Office 365 Identitätsmanagement</span><span class="sxs-lookup"><span data-stu-id="081ef-114">Azure AD editions and Office 365 identity management</span></span>

<span data-ttu-id="081ef-p103">Wenn Sie über ein kostenpflichtiges Abonnement zu Office 365 verfügen, müssen Sie auch ein kostenloses Abonnement von Azure AD. Azure AD können zum Erstellen und Verwalten von Benutzer- und Gruppenkonten. Um dieses Abonnement zu aktivieren, müssen Sie eine einmalige Anmeldung abzuschließen. Anschließend können Sie von Ihrem Office 365-Verwaltungsportal Azure AD zugreifen. Anweisungen finden Sie unter [Registrieren Ihrer kostenlose Azure AD-Abonnement](https://go.microsoft.com/fwlink/p/?LinkId=617127).</span><span class="sxs-lookup"><span data-stu-id="081ef-p103">If you have a paid subscription to Office 365, you also have a free subscription to Azure AD. You can use Azure AD to create and manage user and group accounts. To activate this subscription you have to complete a one-time registration. Afterward, you can access Azure AD from your Office 365 admin portal. For instructions, see [register your free Azure AD subscription](https://go.microsoft.com/fwlink/p/?LinkId=617127).</span></span> 
  
> [!TIP]
> <span data-ttu-id="081ef-p104">Befolgen Sie die Anweisungen oben zum Lieferumfang Ihres Abonnements zu Office 365 registrieren Sie das kostenlose Azure AD-Abonnement. Nicht direkt azure.microsoft.com sich registrieren, oder Sie daran ein Test- oder kostenpflichtiges Abonnement für Microsoft Azure, die von Ihrer kostenlose einen für Office 365 getrennt ist.</span><span class="sxs-lookup"><span data-stu-id="081ef-p104">Follow the instructions above to register the free Azure AD subscription that comes with your subscription to Office 365. Don't go directly to azure.microsoft.com to sign up or you'll end up with a trial or paid subscription to Microsoft Azure that is separate from your free one for Office 365.</span></span> 
  
<span data-ttu-id="081ef-122">Mit dem kostenlosen Abonnement können Sie synchronisieren mit lokalen Verzeichnisse, richten Sie einmaliges Anmelden und Synchronisieren mit vielen Software als dienstanwendungen wie Vertriebs, Ablage und viele weitere.</span><span class="sxs-lookup"><span data-stu-id="081ef-122">With the free subscription you can synchronize with on-premises directories, set up single sign-on, and synchronize with many software as service applications, such as Salesforce, DropBox and many more.</span></span>
  
<span data-ttu-id="081ef-p105">Wenn Sie erweiterte Funktionalität von AD DS, bidirektionale Synchronisierung und andere Verwaltungsfunktionen möchten, können Sie Ihr kostenlose Abonnement in ein kostenpflichtiges Premium-Abonnement aktualisieren. Weitere Informationen finden Sie in [Azure Active Directory-Editionen](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis).</span><span class="sxs-lookup"><span data-stu-id="081ef-p105">If you want enhanced AD DS functionality, bi-directional synchronization, and other management capabilities, you can upgrade your free subscription to a paid premium subscription. For details see [Azure Active Directory editions](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis).</span></span>
  
<span data-ttu-id="081ef-125">Weitere Informationen zu Office 365 und Azure AD finden Sie unter [Grundlegendes zu Office 365-Identität und Azure Active Directory](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9).</span><span class="sxs-lookup"><span data-stu-id="081ef-125">For more information about Office 365 and Azure AD, see [Understanding Office 365 Identity and Azure Active Directory](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9).</span></span>
  
## <a name="extend-the-capabilities-of-your-office-365-tenant"></a><span data-ttu-id="081ef-126">Erweitern der Funktionen von Office 365-Mandanten</span><span class="sxs-lookup"><span data-stu-id="081ef-126">Extend the capabilities of your Office 365 tenant</span></span>

|<span data-ttu-id="081ef-127">**Funktion**</span><span class="sxs-lookup"><span data-stu-id="081ef-127">**Feature**</span></span>|<span data-ttu-id="081ef-128">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="081ef-128">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="081ef-129">Integrierte apps</span><span class="sxs-lookup"><span data-stu-id="081ef-129">Integrated apps</span></span>  <br/> |<span data-ttu-id="081ef-p106">Sie können einzelne apps Zugriff auf Ihre Office 365-Daten, wie e-Mail, Kalender, Kontakte, Benutzer, Gruppen, Dateien und Ordner erteilen. Sie können auch diese apps auf globaler Administrator Ebene autorisieren und zur Verfügung stellen der im gesamten Unternehmens durch die Registrierung von apps in Azure AD. Weitere Informationen finden Sie unter [integrierte Apps und Azure Active Directory für Office 365-Administratoren](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).</span><span class="sxs-lookup"><span data-stu-id="081ef-p106">You can grant individual apps access to your Office 365 data, like mail, calendars, contacts, users, groups, files, and folders. You can also authorize these apps at global admin level and make them available to your entire company by registering the apps in Azure AD. For details see [Integrated Apps and Azure AD for Office 365 administrators](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).  </span></span><br/> <span data-ttu-id="081ef-133">Siehe auch [Azure AD-Anwendung Gallery und Single-Sign-on](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span><span class="sxs-lookup"><span data-stu-id="081ef-133">See also [Azure AD application gallery and single-sign-on](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span></span>  <br/> |
|<span data-ttu-id="081ef-134">PowerApps</span><span class="sxs-lookup"><span data-stu-id="081ef-134">PowerApps</span></span>  <br/> | <span data-ttu-id="081ef-p107">Power-apps sind fokussierte apps für mobile Geräte, die mit den vorhandenen Daten Datenquellen wie SharePoint-Listen verbinden können und andere Daten apps. Weitere Informationen finden Sie unter [Erstellen einer PowerApp für eine Liste in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) und [PowerApps Seite](https://powerapps.microsoft.com/) .</span><span class="sxs-lookup"><span data-stu-id="081ef-p107">Power apps are focused apps for mobile devices that can connect to your existing data sources like SharePoint lists, and other data apps. See [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) for details.  </span></span><br/> |
   
<span data-ttu-id="081ef-137">Andere Ressourcen zu den Microsoft-Cloud und Office 365 finden Sie unter folgenden Ressourcen:</span><span class="sxs-lookup"><span data-stu-id="081ef-137">For other resources about the Microsoft Cloud and Office 365, see these resources:</span></span>
  
- [<span data-ttu-id="081ef-138">Microsoft-Cloud-Identität für Enterprise-Architekten</span><span class="sxs-lookup"><span data-stu-id="081ef-138">Microsoft Cloud Identity for Enterprise Architects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524586)
    
- [<span data-ttu-id="081ef-139">Bereitstellen der Office 365-Verzeichnissynchronisierung (DirSync) in Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="081ef-139">Deploy Office 365 Directory Synchronization (DirSync) in Microsoft Azure</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=517887)
    

<span data-ttu-id="081ef-140">Weitere Informationen finden Sie unter [integrierte Apps und Azure Active Directory für Office 365-Administratoren](integrated-apps-and-azure-ads.md) und [Azure AD-Anwendung Gallery und Single-Sign-on](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).</span><span class="sxs-lookup"><span data-stu-id="081ef-140">Learn more at [Integrated Apps and Azure AD for Office 365 administrators](integrated-apps-and-azure-ads.md) and [Azure AD application gallery and single-sign-on](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).</span></span>

### <a name="power-apps"></a><span data-ttu-id="081ef-141">Power-Apps</span><span class="sxs-lookup"><span data-stu-id="081ef-141">Power Apps</span></span>
<span data-ttu-id="081ef-p108">Power-apps sind fokussierte apps für mobile Geräte, die mit den vorhandenen Daten Datenquellen wie SharePoint-Listen verbinden können und andere Daten apps. Weitere Informationen finden Sie unter [Erstellen einer PowerApp für eine Liste in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) und [PowerApps Seite](https://powerapps.microsoft.com/) .</span><span class="sxs-lookup"><span data-stu-id="081ef-p108">Power apps are focused apps for mobile devices that can connect to your existing data sources like SharePoint lists, and other data apps. See [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) for details.</span></span>