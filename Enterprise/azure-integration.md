---
title: Azure-Integration in Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
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
description: Ihr Office 365-Abonnement enthält ein Abonnement für Azure AD. Integrieren Sie Office 365 mit Azure AD, wenn Sie eine Kennwortsynchronisierung oder einmaliges Anmelden mit Ihrer lokalen Umgebung wünschen.
ms.openlocfilehash: 0ad1c064d2ffe29f0f06e1368cd728d8b3bd630b
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085474"
---
# <a name="azure-integration-with-office-365"></a><span data-ttu-id="10b1c-104">Azure-Integration in Office 365</span><span class="sxs-lookup"><span data-stu-id="10b1c-104">Azure integration with Office 365</span></span>

<span data-ttu-id="10b1c-p102">Office 365 verwendet Azure Active Directory (Azure AD), um Benutzeridentitäten hinter den Kulissen zu verwalten. Ihr Office 365-Abonnement enthält ein kostenloses Abonnement für Azure AD, damit Sie Office 365 mit Azure AD integrieren können, wenn Sie Kennwörter synchronisieren oder die einmalige Anmeldung mit Ihrer lokalen Umgebung einrichten möchten. Sie können auch erweiterte Funktionen erwerben, um Ihre Konten besser zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="10b1c-p102">Office 365 uses Azure Active Directory (Azure AD) to manage user identities behind the scenes. Your Office 365 subscription includes a free subscription to Azure AD so that you can integrate Office 365 with Azure AD if you want to sync passwords or set up single sign-on with your on-premises environment. You can also buy advanced features to better manage your accounts.</span></span>
  
<span data-ttu-id="10b1c-108">Azure bietet auch andere Funktionen, wie das Verwalten integrierter apps, die Sie zum Erweitern und Anpassen Ihrer Office 365-Abonnements verwenden können.</span><span class="sxs-lookup"><span data-stu-id="10b1c-108">Azure also offers other functionality, like managing integrated apps, that you can use to extend and customize your Office 365 subscriptions.</span></span>
  
<span data-ttu-id="10b1c-109">Sie können die Azure AD-Bereitstellungs Ratgeber für eine geführte Einrichtung und Konfiguration verwenden:</span><span class="sxs-lookup"><span data-stu-id="10b1c-109">You can use the Azure AD deployment advisors for a guided setup and configuration experience:</span></span>
 - [<span data-ttu-id="10b1c-110">Azure AD Connect Advisor</span><span class="sxs-lookup"><span data-stu-id="10b1c-110">Azure AD Connect advisor</span></span>](https://aka.ms/aadconnectpwsync)
 - [<span data-ttu-id="10b1c-111">AD FS-Bereitstellungs Ratgeber</span><span class="sxs-lookup"><span data-stu-id="10b1c-111">AD FS deployment advisor</span></span>](https://aka.ms/adfsguidance)
 - [<span data-ttu-id="10b1c-112">Azure RMS-Bereitstellungs-Assistent</span><span class="sxs-lookup"><span data-stu-id="10b1c-112">Azure RMS Deployment Wizard</span></span>](https://aka.ms/azuremsguidance)
 - [<span data-ttu-id="10b1c-113">Azure AD Premium-Setup Handbuch</span><span class="sxs-lookup"><span data-stu-id="10b1c-113">Azure AD Premium setup guide</span></span>](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-office-365-identity-management"></a><span data-ttu-id="10b1c-114">Azure AD Editions und Office 365 Identity Management</span><span class="sxs-lookup"><span data-stu-id="10b1c-114">Azure AD editions and Office 365 identity management</span></span>

<span data-ttu-id="10b1c-p103">Wenn Sie ein kostenpflichtiges Abonnement für Office 365 haben, haben Sie auch ein Gratis Abonnement für Azure AD. Sie können Azure AD zum Erstellen und Verwalten von Benutzer-und Gruppenkonten verwenden. Um dieses Abonnement zu aktivieren, müssen Sie eine einmalige Registrierung ausführen. Anschließend können Sie über Ihr Office 365-Verwaltungsportal auf Azure AD zugreifen. Weitere Informationen finden Sie unter [Registrieren Ihres kostenlosen Azure AD-Abonnements](https://go.microsoft.com/fwlink/p/?LinkId=617127).</span><span class="sxs-lookup"><span data-stu-id="10b1c-p103">If you have a paid subscription to Office 365, you also have a free subscription to Azure AD. You can use Azure AD to create and manage user and group accounts. To activate this subscription you have to complete a one-time registration. Afterward, you can access Azure AD from your Office 365 admin portal. For instructions, see [register your free Azure AD subscription](https://go.microsoft.com/fwlink/p/?LinkId=617127).</span></span> 
  
> [!TIP]
> <span data-ttu-id="10b1c-p104">BeFolgen Sie die obigen Anweisungen, um das ﻿kostenlose Azure AD-Abonnement zu registrieren, das mit Ihrem Abonnement für Office 365 geliefert wird. Gehen Sie nicht direkt zu azure.microsoft.com, um sich anzumelden, oder Sie erhalten ein Test-oder kostenpflichtiges Abonnement für Microsoft Azure, das von Ihrem kostenlosen für Office 365 getrennt ist.</span><span class="sxs-lookup"><span data-stu-id="10b1c-p104">Follow the instructions above to register the free Azure AD subscription that comes with your subscription to Office 365. Don't go directly to azure.microsoft.com to sign up or you'll end up with a trial or paid subscription to Microsoft Azure that is separate from your free one for Office 365.</span></span> 
  
<span data-ttu-id="10b1c-122">Mit dem kostenlosen Abonnement können Sie mit lokalen Verzeichnissen synchronisieren, einmaliges Anmelden einrichten und mit vielen Software als Dienstanwendungen wie Salesforce, DropBox und vielem mehr synchronisieren.</span><span class="sxs-lookup"><span data-stu-id="10b1c-122">With the free subscription you can synchronize with on-premises directories, set up single sign-on, and synchronize with many software as service applications, such as Salesforce, DropBox and many more.</span></span>
  
<span data-ttu-id="10b1c-p105">Wenn Sie eine erweiterte AD DS-Funktionalität, eine bidirektionale Synchronisierung und andere Verwaltungsfunktionen wünschen, können Sie Ihr kostenloses Abonnement auf ein bezahltes Premium-Abonnement upgraden. Weitere Informationen finden Sie unter [Azure Active Directory Editions](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis).</span><span class="sxs-lookup"><span data-stu-id="10b1c-p105">If you want enhanced AD DS functionality, bi-directional synchronization, and other management capabilities, you can upgrade your free subscription to a paid premium subscription. For details see [Azure Active Directory editions](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis).</span></span>
  
<span data-ttu-id="10b1c-125">Weitere Informationen zu Office 365 und Azure AD finden Sie unter [Grundlegendes zu office 365 Identity und Azure Active Directory](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9).</span><span class="sxs-lookup"><span data-stu-id="10b1c-125">For more information about Office 365 and Azure AD, see [Understanding Office 365 Identity and Azure Active Directory](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9).</span></span>
  
## <a name="extend-the-capabilities-of-your-office-365-tenant"></a><span data-ttu-id="10b1c-126">Erweitern der Funktionen Ihres Office 365-Mandanten</span><span class="sxs-lookup"><span data-stu-id="10b1c-126">Extend the capabilities of your Office 365 tenant</span></span>

|<span data-ttu-id="10b1c-127">**Funktion**</span><span class="sxs-lookup"><span data-stu-id="10b1c-127">**Feature**</span></span>|<span data-ttu-id="10b1c-128">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="10b1c-128">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="10b1c-129">Integrierte apps</span><span class="sxs-lookup"><span data-stu-id="10b1c-129">Integrated apps</span></span>  <br/> |<span data-ttu-id="10b1c-p106">Sie können einzelnen apps Zugriff auf Ihre Office 365-Daten gewähren, wie e-Mail, Kalender, Kontakte, Benutzer, Gruppen, Dateien und Ordner. Sie können diese apps auch auf globaler Administratorebene autorisieren und für Ihr gesamtes Unternehmen zugänglich machen, indem Sie die apps in Azure AD registrieren. Weitere Informationen finden Sie unter [integrierte apps und Azure AD für Office 365-Administratoren](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).</span><span class="sxs-lookup"><span data-stu-id="10b1c-p106">You can grant individual apps access to your Office 365 data, like mail, calendars, contacts, users, groups, files, and folders. You can also authorize these apps at global admin level and make them available to your entire company by registering the apps in Azure AD. For details see [Integrated Apps and Azure AD for Office 365 administrators](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).  </span></span><br/> <span data-ttu-id="10b1c-133">Siehe auch [Azure AD-Anwendungskatalog und einmaliges Anmelden](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span><span class="sxs-lookup"><span data-stu-id="10b1c-133">See also [Azure AD application gallery and single-sign-on](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span></span>  <br/> |
|<span data-ttu-id="10b1c-134">PowerApps</span><span class="sxs-lookup"><span data-stu-id="10b1c-134">PowerApps</span></span>  <br/> | <span data-ttu-id="10b1c-p107">Power apps sind fokussierte Apps für mobile Geräte, die eine Verbindung zu Ihren vorhandenen Datenquellen wie SharePoint-Listen und anderen Daten-apps herstellen können. Weitere Informationen finden Sie unter [Erstellen einer PowerApp für eine Liste in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) und [PowerApps Seite](https://powerapps.microsoft.com/) .</span><span class="sxs-lookup"><span data-stu-id="10b1c-p107">Power apps are focused apps for mobile devices that can connect to your existing data sources like SharePoint lists, and other data apps. See [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) for details.  </span></span><br/> |
   
<span data-ttu-id="10b1c-137">Weitere Ressourcen zur Microsoft-Cloud und Office 365 finden Sie in den folgenden Ressourcen:</span><span class="sxs-lookup"><span data-stu-id="10b1c-137">For other resources about the Microsoft Cloud and Office 365, see these resources:</span></span>
  
- [<span data-ttu-id="10b1c-138">Microsoft-Cloud-Identität für Enterprise-Architekten</span><span class="sxs-lookup"><span data-stu-id="10b1c-138">Microsoft Cloud Identity for Enterprise Architects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524586)
    
- [<span data-ttu-id="10b1c-139">Bereitstellen der Office 365-Verzeichnissynchronisierung (DirSync) in Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="10b1c-139">Deploy Office 365 Directory Synchronization (DirSync) in Microsoft Azure</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=517887)
    

<span data-ttu-id="10b1c-140">Weitere Informationen finden Sie unter [integrierte apps und Azure AD für Office 365 Administratoren](integrated-apps-and-azure-ads.md) und [Azure AD-Anwendungskatalog und Single Sign-on](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).</span><span class="sxs-lookup"><span data-stu-id="10b1c-140">Learn more at [Integrated Apps and Azure AD for Office 365 administrators](integrated-apps-and-azure-ads.md) and [Azure AD application gallery and single-sign-on](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).</span></span>

### <a name="power-apps"></a><span data-ttu-id="10b1c-141">Power apps</span><span class="sxs-lookup"><span data-stu-id="10b1c-141">Power Apps</span></span>
<span data-ttu-id="10b1c-p108">Power apps sind fokussierte Apps für mobile Geräte, die eine Verbindung zu Ihren vorhandenen Datenquellen wie SharePoint-Listen und anderen Daten-apps herstellen können. Weitere Informationen finden Sie unter [Erstellen einer PowerApp für eine Liste in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) und [PowerApps Seite](https://powerapps.microsoft.com/) .</span><span class="sxs-lookup"><span data-stu-id="10b1c-p108">Power apps are focused apps for mobile devices that can connect to your existing data sources like SharePoint lists, and other data apps. See [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) for details.</span></span>