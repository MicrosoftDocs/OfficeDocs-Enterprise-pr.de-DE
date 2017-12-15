---
title: "Verwenden von Microsoft Azure Active Directory für die SharePoint 2013-Authentifizierung"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_Solutions
ms.assetid: bef810a4-53f6-4962-878e-e20b5019baeb
description: 'Zusammenfassung: Erfahren Sie, wie den Azure Access Control Service verwenden, um SharePoint Server 2013-Benutzer mit Azure Active Directory zu authentifizieren.'
ms.openlocfilehash: 85db8376aeb06ef6f291b563410c991ea24351d5
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2017
---
# <a name="using-microsoft-azure-active-directory-for-sharepoint-2013-authentication"></a><span data-ttu-id="77414-103">Verwenden von Microsoft Azure Active Directory für die SharePoint 2013-Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="77414-103">Using Microsoft Azure Active Directory for SharePoint 2013 authentication</span></span>

 <span data-ttu-id="77414-104">**Zusammenfassung:** Erfahren Sie, wie den Azure Access Control Service verwenden, um SharePoint Server 2013-Benutzer mit Azure Active Directory zu authentifizieren.</span><span class="sxs-lookup"><span data-stu-id="77414-104">**Summary:** Learn how to use the Azure Access Control Service to authenticate your SharePoint Server 2013 users with Azure Active Directory.</span></span>
  
<span data-ttu-id="77414-p101">Die Verwaltung der Benutzer kann einfacher sein, wenn Sie sie mithilfe unterschiedlicher Identitätsanbieter authentifizieren. Berücksichtigen Sie, wie bequem es sein kann, einen Identitätsanbieter zu nutzen, den Sie als vertrauenswürdig einstufen, den aber eine andere Person verwaltet. Sie können beispielsweise über einen Authentifizierungstyp für Benutzer verfügen, die auf SharePoint Server 2013 in der Cloud zugreifen, und über einen weiteren für SharePoint 2013-Benutzer in Ihrer lokalen Umgebung. Der Azure Access Control Service ermöglicht diese Optionen.</span><span class="sxs-lookup"><span data-stu-id="77414-p101">It can be easier to manage your users by authenticating them with different identity providers. Consider how convenient it can be to use an identity provider that you trust, but someone else manages. For example, you could have one type of authentication for users who access SharePoint Server 2013 in the cloud and another for SharePoint 2013 users in your on-premises environment. The Azure Access Control Service makes these choices possible.</span></span> 
  
<span data-ttu-id="77414-p102">In diesem Artikel wird erläutert, wie Sie den Azure Access Control Service zum Authentifizieren der SharePoint 2013-Benutzer mit Azure AD anstatt mit Ihrem lokalen Active Directory verwenden können. Bei dieser Konfiguration wird Azure AD zu einem vertrauenswürdigen Identitätsanbieter für SharePoint 2013. Diese Konfiguration fügt eine Authentifizierungsmethode für Benutzer hinzu, die getrennt von der Active Directory-Authentifizierung ist, die von der SharePoint 2013-Installation selbst verwendet wird. Um von diesem Artikel zu profitieren, sollten Sie mit WS-Federation vertraut sein. Weitere Informationen finden Sie unter [Grundlegendes zu WS-Federation](https://go.microsoft.com/fwlink/p/?linkid=188052).</span><span class="sxs-lookup"><span data-stu-id="77414-p102">This article explains how you can use the Azure Access Control Service to authenticate your SharePoint 2013 users with Azure AD, instead of your on-premises Active Directory. In this configuration, Azure AD becomes a trusted identity provider for SharePoint 2013. This configuration adds a user authentication method that is separate from Active Directory authentication used by the SharePoint 2013 installation itself. To benefit from this article, you should be familiar with WS-Federation. For more information, see [Understanding WS-Federation](https://go.microsoft.com/fwlink/p/?linkid=188052).</span></span>
  
<span data-ttu-id="77414-114">Die folgende Abbildung veranschaulicht die Funktionsweise der Authentifizierung für SharePoint 2013-Benutzer bei dieser Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="77414-114">The following figure shows how authentication works for SharePoint 2013 users in this configuration.</span></span>
  
![Mit Azure Active Directory authentifizierte Benutzer](images/SP_AzureAD.png)
  
<span data-ttu-id="77414-116">Das in diesem Artikel verwendete Beispiel stammt von Kirk Evans, Microsoft Architect für das Azure Center of Excellence.</span><span class="sxs-lookup"><span data-stu-id="77414-116">The example used in this article is provided by Kirk Evans, Microsoft Architect for the Azure Center of Excellence.</span></span> 
  
<span data-ttu-id="77414-117">Informationen zur SharePoint 2013-Barrierefreiheit finden Sie unter [Barrierefreiheit für SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=393123).</span><span class="sxs-lookup"><span data-stu-id="77414-117">For information about SharePoint 2013 accessibility, see [Accessibility for SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=393123).</span></span>
  
## <a name="configuration-overview"></a><span data-ttu-id="77414-118">Übersicht über die Konfiguration</span><span class="sxs-lookup"><span data-stu-id="77414-118">Configuration overview</span></span>

<span data-ttu-id="77414-119">Führen Sie die folgenden allgemeinen Schritte zum Einrichten der Umgebung für das Verwenden von Azure AD als SharePoint 2013-Identitätsanbieter aus.</span><span class="sxs-lookup"><span data-stu-id="77414-119">Follow these general steps to set up your environment to use Azure AD as a SharePoint 2013 identity provider.</span></span>
  
1. <span data-ttu-id="77414-120">Erstellen Sie einen neuen Azure AD-Mandanten und -Namespace.</span><span class="sxs-lookup"><span data-stu-id="77414-120">Create a new Azure AD tenant and namespace.</span></span>
    
2. <span data-ttu-id="77414-121">Fügen Sie einen WS-Federation-Identitätsanbieter hinzu.</span><span class="sxs-lookup"><span data-stu-id="77414-121">Add a WS-Federation identity provider.</span></span>
    
3. <span data-ttu-id="77414-122">Fügen SharePoint als eine Anwendung der vertrauenden Seite hinzu.</span><span class="sxs-lookup"><span data-stu-id="77414-122">Add SharePoint as a relying party application.</span></span>
    
4. <span data-ttu-id="77414-123">Erstellen Sie ein selbstsigniertes für SSL zu verwendendes Zertifikat.</span><span class="sxs-lookup"><span data-stu-id="77414-123">Create a self-signed certificate to use for SSL.</span></span>
    
5. <span data-ttu-id="77414-124">Erstellen Sie eine Regelgruppe für die anspruchsbasierte Authentifizierung.</span><span class="sxs-lookup"><span data-stu-id="77414-124">Create a rule group for claims-based authentication.</span></span>
    
6. <span data-ttu-id="77414-125">Konfigurieren Sie das X.509-Zertifikat.</span><span class="sxs-lookup"><span data-stu-id="77414-125">Configure the X.509 certificate.</span></span>
    
7. <span data-ttu-id="77414-126">Erstellen Sie eine Anspruchszuordnung.</span><span class="sxs-lookup"><span data-stu-id="77414-126">Create a claim mapping.</span></span>
    
8. <span data-ttu-id="77414-127">Konfigurieren Sie SharePoint für den neuen Identitätsanbieter.</span><span class="sxs-lookup"><span data-stu-id="77414-127">Configure SharePoint for the new identity provider.</span></span>
    
9. <span data-ttu-id="77414-128">Legen Sie die Berechtigungen fest.</span><span class="sxs-lookup"><span data-stu-id="77414-128">Set the permissions.</span></span>
    
10. <span data-ttu-id="77414-129">Überprüfen Sie den neuen Anbieter.</span><span class="sxs-lookup"><span data-stu-id="77414-129">Verify the new provider.</span></span>
    
## <a name="create-azure-ad-tenant-and-namespace"></a><span data-ttu-id="77414-130">Erstellen eines neuen Azure AD-Mandanten und -Namespace</span><span class="sxs-lookup"><span data-stu-id="77414-130">Create Azure AD tenant and namespace</span></span>

<span data-ttu-id="77414-p103">Führen Sie die folgenden Schritte zum Erstellen eines neuen Azure AD-Mandanten und eines zugehörigen Namespace aus. In diesem Beispiel verwenden wir den Namespace "Blueskyabove".</span><span class="sxs-lookup"><span data-stu-id="77414-p103">Use the following steps to create a new Azure AD tenant and an associated namespace. In this example, we use the namespace "blueskyabove."</span></span> 
  
1. <span data-ttu-id="77414-133">Klicken Sie im Azure-Verwaltungsportal auf **Active Directory**, und erstellen Sie einen neuen Azure AD-Mandanten.</span><span class="sxs-lookup"><span data-stu-id="77414-133">In the Azure Management Portal, click **Active Directory**, and then create a new Azure AD tenant.</span></span>
    
2. <span data-ttu-id="77414-134">Klicken Sie auf **Access Control-Namespaces**, und erstellen Sie einen neuen Namespace.</span><span class="sxs-lookup"><span data-stu-id="77414-134">Click **Access Control Namespaces**, and create a new namespace.</span></span> 
    
3. <span data-ttu-id="77414-p104">Klicken Sie auf der unteren Leiste auf **Verwalten**. Dadurch wird dieser Speicherort geöffnet: https://blueskyabove.accesscontrol.windows.net/v2/mgmt/web.</span><span class="sxs-lookup"><span data-stu-id="77414-p104">Click **Manage** on the bottom bar. This should open this location, https://blueskyabove.accesscontrol.windows.net/v2/mgmt/web.</span></span>
    
4. <span data-ttu-id="77414-p105">Öffnen Sie Windows PowerShell. Verwenden Sie das Microsoft Online Services-Modul für Windows PowerShell, das eine Voraussetzung für die Installation von Azure für Windows PowerShell-Cmdlets ist.</span><span class="sxs-lookup"><span data-stu-id="77414-p105">Open Windows PowerShell. Use the Microsoft Online Services Module for Windows PowerShell, which is a prerequisite for installing the Azure for Windows PowerShell cmdlets.</span></span>
    
5. <span data-ttu-id="77414-139">Geben Sie an der Windows PowerShell-Eingabeaufforderung den Befehl  `Connect-Msolservice` und dann Ihre Anmeldeinformationen ein.</span><span class="sxs-lookup"><span data-stu-id="77414-139">From the Windows PowerShell command prompt, type the command:  `Connect-Msolservice`, and then type your credentials.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="77414-140">Weitere Informationen zur Verwendung von Azure für Windows PowerShell-Cmdlets finden Sie unter [Verwalten von Azure AD mit Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=393124).</span><span class="sxs-lookup"><span data-stu-id="77414-140">For additional information about how to use Azure for Windows PowerShell cmdlets, see [Manage Azure AD using Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=393124).</span></span> 
  
6. <span data-ttu-id="77414-141">Geben Sie über eine Windows PowerShell-Eingabeaufforderung die folgenden Befehle ein:</span><span class="sxs-lookup"><span data-stu-id="77414-141">From a Windows PowerShell command prompt, type the following commands:</span></span>
    
  ```
  Import-Module MSOnlineExtended -Force
  ```

  ```
  $replyUrl = New-MsolServicePrincipalAddresses -Address "https://blueskyabove.accesscontrol.windows.net/"
  ```

  ```
  New-MsolServicePrincipal -ServicePrincipalNames @("https://blueskyabove.accesscontrol.windows.net/") -DisplayName "BlueSkyAbove ACS Namespace" -Addresses $replyUrl
  ```

    <span data-ttu-id="77414-142">Die folgende Abbildung veranschaulicht das Ergebnis der Ausgabe.</span><span class="sxs-lookup"><span data-stu-id="77414-142">The following figure illustrates the output result.</span></span>
    
     ![Erstellen von Dienstprinzipalnamen](images/ServicePrincipalNames.jpg)
  
## <a name="add-a-ws-federation-identity-provider-to-the-namespace"></a><span data-ttu-id="77414-144">Hinzufügen eines WS-Federation-Identitätsanbieters zum Namespace</span><span class="sxs-lookup"><span data-stu-id="77414-144">Add a WS-Federation identity provider to the namespace</span></span>

<span data-ttu-id="77414-145">Führen Sie die folgenden Schritte aus, um einen neuen WS-Federation-Identitätsanbieter zum Namespace "Blueskyabove" hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="77414-145">Use the following steps to add a new WS-Federation identity provider to the blueskyabove namespace.</span></span>
  
1. <span data-ttu-id="77414-146">Wechseln Sie im Azure-Verwaltungsportal zu **Active Directory** > **Access Control-Namespaces**, klicken Sie auf **Neue Instanz erstellen** und dann auf **Verwalten**.</span><span class="sxs-lookup"><span data-stu-id="77414-146">From the Azure management portal, go to **Active Directory** > **Access Control Namespaces**, click **Create a new instance**, and then click **Manage**.</span></span>
    
2. <span data-ttu-id="77414-147">Klicken Sie im Azure Access Control-Portal auf **Identitätsanbieter** > **Hinzufügen**, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="77414-147">From the Azure Access Control portal, click **Identity Providers** > **Add**, as illustrated in the following figure.</span></span>
    
     ![Dialogfeld "Identitätsanbieter" in Azure](images/Identity.jpg)
  
3. <span data-ttu-id="77414-149">Klicken Sie auf **WS-Federation-Identitätsanbieter**, wie in der folgenden Abbildung dargestellt, und dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="77414-149">Click **WS-Federation identity provider**, as illustrated in the following figure, and then click **Next**.</span></span>
    
     ![Einstellungen zum Hinzufügen von Identitätsanbietern](images/AddIdentity.jpg)
  
4. <span data-ttu-id="77414-p106">Füllen Sie den Anzeigenamen und Anmeldelinktext aus, und klicken Sie auf **Speichern**. Geben Sie für die WS-Federation-Metadaten-URL https://accounts.accesscontrol.windows.net/blueskyabove.onmicrosoft.com/FederationMetadata/2007-06/FederationMetadata.xml ein. Die folgende Abbildung zeigt die Einstellung.</span><span class="sxs-lookup"><span data-stu-id="77414-p106">Fill out the display name and logon link text, and then click **Save**. For the WS-Federation metadata URL, type https://accounts.accesscontrol.windows.net/blueskyabove.onmicrosoft.com/FederationMetadata/2007-06/FederationMetadata.xml. The following figure illustrates the setting.</span></span>
    
     ![Verbundidentitätsanbieter](images/FederationIdentity.jpg)
  
## <a name="add-sharepoint-as-a-relying-party-application"></a><span data-ttu-id="77414-155">Hinzufügen von SharePoint als eine Anwendung der vertrauenden Seite</span><span class="sxs-lookup"><span data-stu-id="77414-155">Add SharePoint as a relying party application</span></span>

<span data-ttu-id="77414-156">Führen Sie die folgenden Schritte aus, um SharePoint als Anwendung der vertrauenden Seite hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="77414-156">Use the following steps to add SharePoint as a relying party application.</span></span>
  
<span data-ttu-id="77414-157">Weitere Informationen zu den Einstellungen der Anwendung der vertrauenden Seite finden Sie unter [Anwendungen der vertrauenden Seite](https://go.microsoft.com/fwlink/p/?LinkId=393125).</span><span class="sxs-lookup"><span data-stu-id="77414-157">For additional information about relying party application settings, see [Relying Party Applications](https://go.microsoft.com/fwlink/p/?LinkId=393125).</span></span>
  
1. <span data-ttu-id="77414-158">Klicken Sie über das Portal Azure Access Control auf **Anwendungen vertrauenden Seite**, und klicken Sie dann auf **Hinzufügen**, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="77414-158">From the Azure Access Control portal, click **Relying party applications**, and then click **Add**, as illustrated in the following figure.</span></span>
    
     ![Relying Party-Anwendungseinstellungen](images/RelyingPartyApplications.jpg)
  
## <a name="create-a-self-signed-certificate-to-use-for-ssl"></a><span data-ttu-id="77414-160">Erstellen eines selbstsignierten für SSL zu verwendenden Zertifikats.</span><span class="sxs-lookup"><span data-stu-id="77414-160">Create a self-signed certificate to use for SSL</span></span>

<span data-ttu-id="77414-161">Führen Sie die folgenden Schritte zum Erstellen einer neuen, selbstsignierten Zertifikats aus, das für die sichere Kommunikation über SSL verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="77414-161">Use the following steps to create a new, self-signed certificate to use for secure communications over SSL.</span></span>
  
1. <span data-ttu-id="77414-162">Erweitern Sie die Webanwendung für die Verwendung derselben URL wie "PublishingSite", wählen Sie aber SSL mit Port 443, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="77414-162">Extend the web application to use the same URL as PublishingSite, but use SSL with port 443, as illustrated in the following figure.</span></span>
    
     ![Einstellungen zur Anwendungserweiterung](images/ExtendWebApp.jpg)
  
2. <span data-ttu-id="77414-164">Doppelklicken Sie in IIS-Manager auf **Serverzertifikate**.</span><span class="sxs-lookup"><span data-stu-id="77414-164">In IIS Manager, double-click **Server Certificates**.</span></span>
    
3. <span data-ttu-id="77414-p107">Klicken Sie im Bereich **Aktionen** auf **Selbstsigniertes Zertifikat erstellen**. Geben Sie in das Feld **Anzeigename für das Zertifikat** einen Anzeigenamen ein, und klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="77414-p107">In the **Actions** pane, click **Create Self-Signed Certificate**. Type a friendly name for the certificate in the **Specify a friendly name for the certificate** box, and then click **OK**.</span></span>
    
4. <span data-ttu-id="77414-167">Vergewissern Sie sich im Dialogfeld **Sitebindung bearbeiten**, dass der Hostname dem Anzeigenamen entspricht, wie in den folgenden Abbildungen dargestellt.</span><span class="sxs-lookup"><span data-stu-id="77414-167">From the **Edit Site Binding** dialog box, ensure the host name is the same as the friendly name, as illustrated in the following figures.</span></span>
    
     ![Assistent "Selbstsigniertes Zertifikat erstellen"](images/SelfSignedCert.jpg)
  
     ![Hostname im Dialogfeld "Bindungen bearbeiten"](images/SelfSignedCert1.jpg)
  
5. <span data-ttu-id="77414-170">Klicken Sie im Azure-Verwaltungsportal auf den virtuellen Computer, den Sie konfigurieren möchten, und klicken Sie dann auf **Endpunkte**.</span><span class="sxs-lookup"><span data-stu-id="77414-170">From the Azure management portal, click the virtual machine that you want to configure, and then click **Endpoints**.</span></span>
    
6. <span data-ttu-id="77414-171">Klicken Sie auf **Hinzufügen** und dann auf **-->** (für "Weiter").</span><span class="sxs-lookup"><span data-stu-id="77414-171">Click **Add**, and then click **-->** (for Next).</span></span>
    
7. <span data-ttu-id="77414-172">Geben Sie in das Feld **Name** einen Namen für den Endpunkt ein.</span><span class="sxs-lookup"><span data-stu-id="77414-172">In **Name**, type a name for the endpoint.</span></span>
    
8. <span data-ttu-id="77414-p108">Geben Sie in **Öffentlicher Port** und **Privater Port** die Portnummern ein, die Sie verwenden möchten, und klicken Sie dann zum Fertigstellen auf das Häkchen. Diese Nummern können unterschiedlich sein. In diesem Artikel verwenden wir 443, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="77414-p108">In **Public Port** and **Private Port**, type the port numbers that you want to use, and then click the check mark to complete. These numbers can be different. For the purposes of this article, we are using 443, as illustrated in the following figure.</span></span>
    
     ![Endpunkteinstellungen in Azure](images/AddEndpoint.jpg)
  
    > [!NOTE]
    > <span data-ttu-id="77414-177">Weitere Informationen dazu, wie Sie einem virtuellen Computer einen Endpunkt in Azure hinzufügen, finden Sie unter [Einrichten von Endpunkten für einen virtuellen Computer](https://go.microsoft.com/fwlink/p/?LinkId=393126).</span><span class="sxs-lookup"><span data-stu-id="77414-177">For additional information about how to add an endpoint to a virtual machine in Azure, see [How to Set Up Endpoints to a Virtual Machine](https://go.microsoft.com/fwlink/p/?LinkId=393126).</span></span> 
  
9. <span data-ttu-id="77414-178">Fügen Sie im Access Control Services-Portal eine vertrauende Seite hinzu, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="77414-178">From the Access Control services portal, add a relying party, as illustrated in the following figure.</span></span>
    
     ![Einstellungen zum Hinzufügen der vertrauenden Seite](images/AddRelyingParty.jpg)
  
## <a name="create-a-rule-group-for-claims-based-authentication"></a><span data-ttu-id="77414-180">Erstellen einer Regelgruppe für die anspruchsbasierte Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="77414-180">Create a rule group for claims-based authentication</span></span>

<span data-ttu-id="77414-181">Führen Sie die folgenden Schritte aus, um eine neue Regelgruppe zur Steuerung der anspruchsbasierten Authentifizierung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="77414-181">Use the following steps to create a new rule group to control claims-based authentication.</span></span>
  
1. <span data-ttu-id="77414-182">Klicken Sie im linken Bereich auf **Regelgruppen** und dann auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="77414-182">In the left pane, click **Rule groups**, and then click **Add**.</span></span>
    
2. <span data-ttu-id="77414-p109">Geben Sie einen Namen für die Regelgruppe ein, klicken Sie auf **Speichern** und dann auf **Generieren**. In diesem Artikel verwenden wir **Default Rule Group for. spvms.cloudapp.net**, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="77414-p109">Type a name for the rule group, click **Save**, and then click **Generate**. For the purposes of this article, we are using **Default Rule Group for. spvms.cloudapp.net**, as illustrated in the following figure.</span></span>
    
     ![Regelgruppeneinstellungen in Azure](images/RuleGroup.jpg)
  
     ![Regeln nach Auswahl von "Generieen"](images/GenerateRules.jpg)
  
    > [!NOTE]
    > <span data-ttu-id="77414-187">Weitere Informationen zum Erstellen von Regelgruppen finden Sie unter [Regelgruppen und Regeln](https://go.microsoft.com/fwlink/p/?LinkId=393128).</span><span class="sxs-lookup"><span data-stu-id="77414-187">For additional information about how to create rule groups, see [Rule Groups and Rules](https://go.microsoft.com/fwlink/p/?LinkId=393128).</span></span> 
  
3. <span data-ttu-id="77414-p110">Klicken Sie auf die Regelgruppe, die Sie ändern möchten, und dann auf die Anspruchsregel, die Sie ändern möchten. In diesem Artikel fügen wir der Gruppe eine Anspruchsregel zum Übergeben von **name** als **upn** hinzu, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="77414-p110">Click the rule group that you want to change, and then click the claim rule that you want to change. For the purposes of this article, we add a claim rule to the group to pass **name** as **upn**, as illustrated by the following figure.</span></span>
    
     ![Anspruchsregeleinstellungen in der Azure-Zugriffssteuerung](images/ClaimRules.jpg)
  
4. <span data-ttu-id="77414-191">Löschen Sie die vorhandene Anspruchsregel **upn**, und belassen Sie die Regel **Name Claim to UPN** unverändert, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="77414-191">Delete the existing claim rule named **upn**, and leave the **Name Claim to UPN** rule, as illustrated by the following figure.</span></span>
    
     ![Regeleinstellungen in der Azure-Zugriffssteuerung](images/ClaimToUPN.jpg)
  
## <a name="configure-the-x509-certificate"></a><span data-ttu-id="77414-193">Konfigurieren des X.509-Zertifikats</span><span class="sxs-lookup"><span data-stu-id="77414-193">Configure the X.509 certificate</span></span>

<span data-ttu-id="77414-194">Führen Sie die folgenden Schritte zum Konfigurieren des X.509-Zertifikats aus, das zum Signieren von Token verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="77414-194">Use the following steps to configure the X.509 certificate to use for token signing.</span></span>
  
1. <span data-ttu-id="77414-195">Klicken Sie im Bereich Access Control Service unter **Entwicklung** auf **Anwendungsintegration**.</span><span class="sxs-lookup"><span data-stu-id="77414-195">In the Access Control Service pane, under **Development**, click **Application integration**.</span></span>
    
2. <span data-ttu-id="77414-196">Wechseln Sie in **Endpunktverweis** zur Datei **Federation.xml**, die Ihrem Azure-Mandanten zugeordnet ist, und kopieren Sie den Speicherort in die Adressleiste des Browsers.</span><span class="sxs-lookup"><span data-stu-id="77414-196">In **Endpoint Reference**, locate the **Federation.xml** that is associated with your Azure tenant, and then copy the location in the address bar of a browser.</span></span>
    
3. <span data-ttu-id="77414-197">Wechseln Sie in der Datei **Federation.xml** zum Abschnitt **RoleDescriptor**, und kopieren Sie die Informationen aus dem Element  _<X509Certificate>_, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="77414-197">In the **Federation.xml** file, locate the **RoleDescriptor** section, and copy the information from the _<X509Certificate>_ element, as illustrated in the following figure.</span></span>
    
     ![X509-Zertifikatelement in der Datei "Federation.xml"](images/X509Cert.jpg)
  
4. <span data-ttu-id="77414-199">Erstellen Sie im Stammverzeichnis von Laufwerk C:\\ einen Ordner namens **Certificates**.</span><span class="sxs-lookup"><span data-stu-id="77414-199">From the root of drive C:\\, create a folder named **Certificates**.</span></span>
    
5. <span data-ttu-id="77414-200">Speichern Sie die X.509-Zertifikatinformationen im Ordner C:\\Zertifikate mit dem Dateinamen **AcsTokenSigning.cer**.</span><span class="sxs-lookup"><span data-stu-id="77414-200">Save the X509Certificate information to the folder C:\\Certificates with the file name, **AcsTokenSigning.cer**.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="77414-201">Der Dateiname muss mit der Erweiterung .cer gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="77414-201">The file name must be saved with a .cer extension.</span></span> 
  
     ![Speichern von X509-Zertifikatelementinformation als Datei](images/X509Cert_Save.jpg)
  
## <a name="create-a-claim-mapping-by-using-windows-powershell"></a><span data-ttu-id="77414-203">Erstellen einer Anspruchszuordnung mithilfe von Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="77414-203">Create a claim mapping by using Windows PowerShell</span></span>

<span data-ttu-id="77414-204">Gehen Sie folgendermaßen vor, um eine Anspruchszuordnung mithilfe von Windows PowerShell zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="77414-204">Use the following steps to create a claim mapping by using Windows PowerShell.</span></span>
  
<span data-ttu-id="77414-205">Stellen Sie sicher, dass Sie über die folgenden Mitgliedschaften verfügen:</span><span class="sxs-lookup"><span data-stu-id="77414-205">Verify that you have the following memberships:</span></span>
  
1. <span data-ttu-id="77414-206">Feste Serverrolle **securityadmin** auf der SQL Server-Instanz.</span><span class="sxs-lookup"><span data-stu-id="77414-206">**securityadmin** fixed server role on the SQL Server instance.</span></span>
    
2. <span data-ttu-id="77414-207">Feste Datenbankrolle **db_owner** für alle Datenbanken, die aktualisiert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="77414-207">**db_owner** fixed database role on all databases that will be updated.</span></span>
    
3. <span data-ttu-id="77414-208">Gruppe Administratoren auf dem Server, auf dem die Windows PowerShell-Cmdlets ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="77414-208">Administrators group on the server on which you are running the Windows PowerShell cmdlets.</span></span>
    
<span data-ttu-id="77414-209">Ein Administrator kann mithilfe des **Add-SPShellAdmin** -Cmdlets Berechtigungen zur Verwendung des SharePoint 2013-Cmdlets gewähren.</span><span class="sxs-lookup"><span data-stu-id="77414-209">An administrator can use the **Add-SPShellAdmin** cmdlet to grant permissions to use SharePoint 2013 cmdlets.</span></span>
  
> [!NOTE]
> <span data-ttu-id="77414-p111">Wenn Sie über keine Berechtigungen verfügen, kontaktieren Sie Ihren Setup-Administrator oder SQL Server-Administrator, um die Berechtigungen anzufordern. Weitere Informationen zu Windows PowerShell-Berechtigungen finden Sie unter [Add-SPShellAdmin](http://technet.microsoft.com/library/2ddfad84-7ca8-409e-878b-d09cb35ed4aa.aspx).</span><span class="sxs-lookup"><span data-stu-id="77414-p111">If you do not have permissions, contact your Setup administrator or SQL Server administrator to request permissions. For additional information about Windows PowerShell permissions, see [Add-SPShellAdmin](http://technet.microsoft.com/library/2ddfad84-7ca8-409e-878b-d09cb35ed4aa.aspx).</span></span> 
  
1. <span data-ttu-id="77414-212">Klicken Sie im **Startmenü** auf **Alle Programme**.</span><span class="sxs-lookup"><span data-stu-id="77414-212">From the **Start** menu, click **All Programs**.</span></span>
    
2. <span data-ttu-id="77414-213">Klicken Sie auf **Microsoft SharePoint 2013-Produkte**.</span><span class="sxs-lookup"><span data-stu-id="77414-213">Click **Microsoft SharePoint 2013 Products**.</span></span>
    
3. <span data-ttu-id="77414-214">Klicken Sie auf **SharePoint 2013-Verwaltungsshell**.</span><span class="sxs-lookup"><span data-stu-id="77414-214">Click **SharePoint 2013 Management Shell**.</span></span>
    
4. <span data-ttu-id="77414-215">Geben Sie an der Windows PowerShell-Eingabeaufforderung den folgenden Befehl ein, um eine neue Anspruchszuordnung zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="77414-215">At the Windows PowerShell command prompt, type the following commands to create a claim mapping:</span></span>
    
  ```
  $cert = New-Object System.Security.Cryptography.X509Certificates.X509Certificate2("c:\\certificates\\AcsTokenSigning.cer")
  ```

  ```
  New-SPTrustedRootAuthority -Name "ACS BlueSkyAbove Token Signing" -Certificate $cert
  ```

  ```
  $map = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn" -IncomingClaimTypeDisplayName "UPN" -SameAsIncoming
  ```

  ```
  $map2 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname" -IncomingClaimTypeDisplayName "GivenName" -SameAsIncoming
  ```

  ```
  $map3 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname" -IncomingClaimTypeDisplayName "SurName" -SameAsIncoming
  ```

  ```
  $realm = "urn:sharepoint:spvms"
  ```

  ```
  $ap = New-SPTrustedIdentityTokenIssuer -Name "ACS Provider" -Description "SharePoint secured by SAML in ACS" -realm $realm -ImportTrustCertificate $cert -ClaimsMappings $map,$map2,$map3 -SignInUrl "https://blueskyabove.accesscontrol.windows.net/v2/wsfederation" -IdentifierClaim "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn"
  ```

## <a name="configure-sharepoint-for-the-new-identity-provider"></a><span data-ttu-id="77414-216">Konfigurieren von SharePoint für den neuen Identitätsanbieter</span><span class="sxs-lookup"><span data-stu-id="77414-216">Configure SharePoint for the new identity provider</span></span>

<span data-ttu-id="77414-217">Gehen Sie zum Konfigurieren der SharePoint-Installation für den neuen Identitätsanbieter für Azure AD wie folgt vor.</span><span class="sxs-lookup"><span data-stu-id="77414-217">Use the following steps to configure your SharePoint installation to the new identity provider for Azure AD.</span></span>
  
1. <span data-ttu-id="77414-218">Vergewissern Sie sich, dass das Benutzerkonto, mit dem dieses Verfahren ausgeführt wird, Mitglied der SharePoint-Gruppe "Farmadministratoren" ist.</span><span class="sxs-lookup"><span data-stu-id="77414-218">Verify that the user account that is performing this procedure is a member of the Farm Administrators SharePoint group.</span></span>
    
2. <span data-ttu-id="77414-219">Klicken Sie in Zentraladministration auf der Startseite auf **Anwendungsverwaltung**.</span><span class="sxs-lookup"><span data-stu-id="77414-219">In Central Administration, on the home page, click **Application Management**.</span></span>
    
3. <span data-ttu-id="77414-220">Klicken Sie auf der Seite **Anwendungsverwaltung** im Abschnitt **Webanwendungen** auf **Webanwendungen verwalten**.</span><span class="sxs-lookup"><span data-stu-id="77414-220">On the **Application Management** page, in the **Web Applications** section, click **Manage web applications**.</span></span>
    
4. <span data-ttu-id="77414-221">Klicken Sie auf die entsprechende Webanwendung.</span><span class="sxs-lookup"><span data-stu-id="77414-221">Click the appropriate web application.</span></span>
    
5. <span data-ttu-id="77414-222">Klicken Sie auf dem Menüband auf **Authentifizierungsanbieter**.</span><span class="sxs-lookup"><span data-stu-id="77414-222">From the ribbon, click **Authentication Providers**.</span></span>
    
6. <span data-ttu-id="77414-p112">Klicken Sie unter **Zone** auf den Namen der Zone (z. B. **Standard**).</span><span class="sxs-lookup"><span data-stu-id="77414-p112">Under **Zone**, click the name of the zone. For example, **Default**.</span></span>
    
7. <span data-ttu-id="77414-p113">Wählen Sie auf der Seite **Authentifizierung bearbeiten** im Abschnitt **Forderungsauthentifizierungstypen** die Option **Vertrauenswürdiger Identitätsanbieter**, und klicken Sie dann auf den Namen Ihres Anbieters, der in diesem Artikel **ACS Provider** hießt. Klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="77414-p113">On the **Edit Authentication** page, in the **Claims Authentication Types** section, select **Trusted Identity provider**, and then click the name of your provider, which for purposes of this article is **ACS Provider**. Click **OK**.</span></span>
    
8. <span data-ttu-id="77414-227">Die folgende Abbildung veranschaulicht die Einstellung **Trusted Provider**.</span><span class="sxs-lookup"><span data-stu-id="77414-227">The following figure illustrates the **Trusted Provider** setting.</span></span>
    
![Einstellung "Vertrauenswürdiger Anbieter" in einer Webanwendung](images/AddProvider_Azure.jpg)
  
## <a name="set-the-permissions"></a><span data-ttu-id="77414-229">Festlegen der Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="77414-229">Set the permissions</span></span>

<span data-ttu-id="77414-230">Gehen Sie folgendermaßen vor, um die Zugriffsberechtigungen für die Webanwendung festzulegen.</span><span class="sxs-lookup"><span data-stu-id="77414-230">Use the following steps to set the permissions to access the web application.</span></span>
  
1. <span data-ttu-id="77414-231">Klicken Sie in Zentraladministration auf der Startseite auf **Anwendungsverwaltung**.</span><span class="sxs-lookup"><span data-stu-id="77414-231">In Central Administration, on the home page, click **Application Management**.</span></span>
    
2. <span data-ttu-id="77414-232">Klicken Sie auf der Seite **Anwendungsverwaltung** im Abschnitt **Webanwendungen** auf **Webanwendungen verwalten**.</span><span class="sxs-lookup"><span data-stu-id="77414-232">On the **Application Management** page, in the **Web Applications** section, click **Manage web applications**.</span></span>
    
3. <span data-ttu-id="77414-233">Klicken Sie auf die entsprechende Webanwendung und anschließend auf **Benutzerrichtlinie**.</span><span class="sxs-lookup"><span data-stu-id="77414-233">Click the appropriate web application, and then click **User Policy**.</span></span>
    
4. <span data-ttu-id="77414-234">Klicken Sie unter **Richtlinie für Webanwendung** auf **Benutzer hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="77414-234">In **Policy for Web Application**, click **Add Users**.</span></span>
    
5. <span data-ttu-id="77414-235">Klicken Sie im Dialogfeld **Benutzer hinzufügen** in **Zonen** auf die entsprechende Zone, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="77414-235">In the **Add Users** dialog box, click the appropriate zone in **Zones**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="77414-236">Geben Sie in das Dialogfeld **Benutzer hinzufügen** Folgendes ein:user2@blueskyabove.onmicrosoft.com (ACS-Anbieter).</span><span class="sxs-lookup"><span data-stu-id="77414-236">In the **Add Users** dialog box, typeuser2@blueskyabove.onmicrosoft.com (ACS Provider).</span></span>
    
7. <span data-ttu-id="77414-237">Klicken Sie in **Berechtigungen** auf **Vollzugriff**.</span><span class="sxs-lookup"><span data-stu-id="77414-237">In **Permissions**, click **Full Control**.</span></span>
    
8. <span data-ttu-id="77414-238">Klicken Sie auf **Fertig stellen**, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="77414-238">Click **Finish**, and then click **OK**.</span></span>
    
<span data-ttu-id="77414-239">Die folgende Abbildung zeigt den Abschnitt **Benutzer hinzufügen** einer vorhandenen Webanwendung.</span><span class="sxs-lookup"><span data-stu-id="77414-239">The following figure illustrates the **Add Users** section of an existing web application.</span></span>
  
![Hinzufügen von Benutzern zu einer vorhandenen Webanwendung](images/AddUsers_Azure.jpg)
  
## <a name="verify-the-new-provider"></a><span data-ttu-id="77414-241">Überprüfen des neuen Anbieters</span><span class="sxs-lookup"><span data-stu-id="77414-241">Verify the new provider</span></span>

<span data-ttu-id="77414-242">Führen Sie die folgenden Schritte aus, um zu prüfen, ob der neuen Identitätsanbieter funktioniert, indem Sie sicherstellen, dass der neue Authentifizierungsanbieter bei der Anmeldeaufforderung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="77414-242">Use the following steps to verify that the new identity provider is working by ensuring that the new authentication provider appears on the sign-in prompt.</span></span>
  
1. <span data-ttu-id="77414-243">Melden Sie sich mithilfe des neuen Anbieters **Blue Sky Above** an, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="77414-243">Sign in by using the new provider named **Blue Sky Above**, as illustrated in the following figure.</span></span>
    
     ![Anmeldedialogfeld mit neuem vertrauenswürdigen Anbieter](images/BlueSkyAbove.jpg)
  
## <a name="additional-resources"></a><span data-ttu-id="77414-245">Zusätzliche Ressourcen</span><span class="sxs-lookup"><span data-stu-id="77414-245">Additional resources</span></span>

[<span data-ttu-id="77414-246">Grundlegendes zu WS-Federation</span><span class="sxs-lookup"><span data-stu-id="77414-246">Understanding WS-Federation</span></span>](https://go.microsoft.com/fwlink/p/?linkid=188052)
  
[<span data-ttu-id="77414-247">Cloudakzeptanz und Hybridlösungen</span><span class="sxs-lookup"><span data-stu-id="77414-247">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
## <a name="join-the-discussion"></a><span data-ttu-id="77414-248">An der Diskussion teilnehmen</span><span class="sxs-lookup"><span data-stu-id="77414-248">Join the discussion</span></span>

|<span data-ttu-id="77414-249">**Kontakt**</span><span class="sxs-lookup"><span data-stu-id="77414-249">**Contact us**</span></span>|<span data-ttu-id="77414-250">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="77414-250">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="77414-251">**Welche Lösungen benötigen Sie?**</span><span class="sxs-lookup"><span data-stu-id="77414-251">**What cloud adoption content do you need?**</span></span> <br/> |<span data-ttu-id="77414-p114">Wir entwickeln Inhalte für Lösungen auf Grundlage mehrerer Microsoft-Produkte und -Dienste. Lassen Sie uns wissen, was Sie von unseren serverübergreifenden Lösungen halten, oder fordern Sie spezifische Lösungen an, indem Sie eine E-Mail an [MODAcontent@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20) senden.</span><span class="sxs-lookup"><span data-stu-id="77414-p114">We are creating content for cloud adoption that spans multiple Microsoft cloud platforms and services. Let us know what you think about our cloud adoption content, or ask for specific content by sending email to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).  </span></span><br/> |
|<span data-ttu-id="77414-254">**An der Diskussion über Lösungen teilnehmen**</span><span class="sxs-lookup"><span data-stu-id="77414-254">**Join the cloud adoption discussion**</span></span> <br/> |<span data-ttu-id="77414-p115">Wenn Sie über Cloud-basierte Lösungen engagierten sind, sollten Sie die Teilnahme an der Cloud Annahme Advisory Board (CAAB) für die Verbindung mit einer größeren, kräftige Community von Microsoft Entwickler von Inhalten, aus dem Gesundheitswesen Experten und Kunden aus der ganzen Welt. Um teilzunehmen, fügen Sie sich als Mitglied der [CAAB (Cloud Annahme Advisory Board) Speicherplatz](https://aka.ms/caab) der Community Tech Center für Microsoft hinzu, und senden Sie uns eine kurze e-Mail unter [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Alle Benutzer können Community-bezogenen Inhalte im [CAAB Blog](https://blogs.technet.com/b/solutions_advisory_board/)lesen. CAAB Mitglieder erhalten jedoch Einladungen an private Webinare, in denen neue Cloud-Migrationsressourcen und Lösungen beschrieben.</span><span class="sxs-lookup"><span data-stu-id="77414-p115">If you are passionate about cloud-based solutions, consider joining the Cloud Adoption Advisory Board (CAAB) to connect with a larger, vibrant community of Microsoft content developers, industry professionals, and customers from around the globe. To join, add yourself as a member of the [CAAB (Cloud Adoption Advisory Board) space](https://aka.ms/caab) of the Microsoft Tech Community and send us a quick email at [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Anyone can read community-related content on the [CAAB blog](https://blogs.technet.com/b/solutions_advisory_board/). However, CAAB members get invitations to private webinars that describe new cloud adoption resources and solutions.  </span></span><br/> |
|<span data-ttu-id="77414-258">**Die hier gezeigte Grafik abrufen**</span><span class="sxs-lookup"><span data-stu-id="77414-258">**Get the art you see here**</span></span> <br/> |<span data-ttu-id="77414-p116">Wenn Sie eine bearbeitbare Kopie der Grafik, die Sie in diesem Artikel sehen möchten, werden wir freuen an Sie gesendet werden. Ihre Anfrage, einschließlich der URL und der Titel der Art [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20)per e-Mail.</span><span class="sxs-lookup"><span data-stu-id="77414-p116">If you want an editable copy of the art you see in this article, we'll be glad to send it to you. Email your request, including the URL and title of the art, to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).  </span></span><br/> |
   

