---
title: Multi-Geo-Funktionen in Exchange Online
ms.author: chrisda
author: chrisda
manager: serdars
ms.date: 4/11/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Normal
ms.assetid: ''
description: Erweitern Sie Ihre Office 365-Anwesenheit auf mehrere geografische Regionen mit Multi-Geo-Funktionen in Exchange Online.
ms.openlocfilehash: ea00ab52142e92e122273ab4ba718e98bd94b572
ms.sourcegitcommit: 12d3223cc2d6bf39a8960409a923254e1790fd2f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="multi-geo-capabilities-in-exchange-online"></a><span data-ttu-id="528fb-103">Multi-Geo-Funktionen in Exchange Online</span><span class="sxs-lookup"><span data-stu-id="528fb-103">Multi-Geo Capabilities in Exchange Online</span></span>

<span data-ttu-id="528fb-p101">Multi-Geo-Funktionen in Office 365 aktivieren Sie einen einzelnen Mandanten zu mehreren geografische Standorten (Geos) umfassen. Wenn Multi-Geo aktiviert ist, können Kunden den Speicherort der Exchange Online Inhalt von Postfächern (Daten im Ruhezustand) für jeden Benutzer einzeln auswählen.</span><span class="sxs-lookup"><span data-stu-id="528fb-p101">Multi-Geo Capabilities in Office 365 enable a single tenant to span multiple geographic locations (Geos). When Multi-Geo is enabled, customers can select the location of Exchange Online mailbox content (data at rest) on a per-user basis.</span></span>

<span data-ttu-id="528fb-p102">Ihres Standorts für Ihre anfänglichen Mandanten (bezeichnet als "Default" oder "Unternehmenszentrale") wird basierend auf Ihrer Adresse bestimmt. Wenn Multi-Geo aktiviert ist, können Sie Postfächer in Speicherorte durch zusätzliche "Satelliten" setzen:</span><span class="sxs-lookup"><span data-stu-id="528fb-p102">Your initial tenant location (referred to as your "default" or "central" location) is determined based on your billing address. When Multi-Geo is enabled, you can place mailboxes in additional "satellite" locations by:</span></span>

- <span data-ttu-id="528fb-108">Erstellen eines neuen Postfachs Exchange Online direkt in einer Satelliten.</span><span class="sxs-lookup"><span data-stu-id="528fb-108">Creating a new Exchange Online mailbox directly in a satellite.</span></span>

- <span data-ttu-id="528fb-109">Verschieben Sie ein vorhandenes Exchange Online-Postfach in eine Satelliten.</span><span class="sxs-lookup"><span data-stu-id="528fb-109">Moving an existing Exchange Online mailbox into a satellite.</span></span>

- <span data-ttu-id="528fb-110">Onboarding ein Postfach aus einer lokalen Exchange-Organisation direkt in eine Satelliten.</span><span class="sxs-lookup"><span data-stu-id="528fb-110">Onboarding a mailbox from an on-premises Exchange organization directly into a satellite.</span></span>

<span data-ttu-id="528fb-111">Die folgenden Geos stehen für die Verwendung in einer Serverfarm mit mehreren Geo-Konfiguration:</span><span class="sxs-lookup"><span data-stu-id="528fb-111">The following Geos are available for use in a Multi-Geo configuration:</span></span>

- <span data-ttu-id="528fb-112">Asien-Pazifik</span><span class="sxs-lookup"><span data-stu-id="528fb-112">Asia Pacific</span></span>

- <span data-ttu-id="528fb-113">Australien</span><span class="sxs-lookup"><span data-stu-id="528fb-113">Australia</span></span>

- <span data-ttu-id="528fb-114">Kanada</span><span class="sxs-lookup"><span data-stu-id="528fb-114">Canada</span></span>

- <span data-ttu-id="528fb-115">Europäische Union</span><span class="sxs-lookup"><span data-stu-id="528fb-115">European Union</span></span>

- <span data-ttu-id="528fb-116">Indien (derzeit nur verfügbar für Kunden mit Abrechnung Adressen in Indien)</span><span class="sxs-lookup"><span data-stu-id="528fb-116">India (currently only available to customers with billing addresses in India)</span></span>

- <span data-ttu-id="528fb-117">Japan</span><span class="sxs-lookup"><span data-stu-id="528fb-117">Japan</span></span>

- <span data-ttu-id="528fb-118">Korea</span><span class="sxs-lookup"><span data-stu-id="528fb-118">Korea</span></span>

- <span data-ttu-id="528fb-119">Vereinigtes Königreich</span><span class="sxs-lookup"><span data-stu-id="528fb-119">United Kingdom</span></span>

- <span data-ttu-id="528fb-120">USA</span><span class="sxs-lookup"><span data-stu-id="528fb-120">United States</span></span>

## <a name="prerequisite-configuration"></a><span data-ttu-id="528fb-121">Erforderliche Konfiguration</span><span class="sxs-lookup"><span data-stu-id="528fb-121">Prerequisite configuration</span></span>
<span data-ttu-id="528fb-p103">Bevor Sie mit der Verwendung von Multi-Geo-Funktionen in Exchange Online beginnen können, muss Microsoft Ihren Exchange Online-Mandanten für die Unterstützung von Multi-Geo konfigurieren. Diese einmalige Konfigurationsprozess wird ausgelöst, wenn Sie Multi-Geo Lizenzen bestellen und sollte in der Regel kleiner als 30 Tage dauern.</span><span class="sxs-lookup"><span data-stu-id="528fb-p103">Before you can start using Multi-Geo capabilities in Exchange Online, Microsoft needs to configure your Exchange Online tenant for Multi-Geo support. This one-time configuration process is triggered when you order Multi-Geo licenses and should typically take less than 30 days to complete.</span></span>

<span data-ttu-id="528fb-p104">Sie erhalten Benachrichtigungen im [Office 365 Nachrichtencenter](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093) bei der Konfiguration gestartet und abgeschlossen wurde. Konfiguration wird automatisch ausgelöst, wenn Sie Multi-Geo Lizenzen kaufen.</span><span class="sxs-lookup"><span data-stu-id="528fb-p104">You'll receive notifications in the [Office 365 message center](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093) when your configuration has started and completed. Configuration is automatically triggered when you buy Multi-Geo licenses.</span></span>

## <a name="mailbox-placement-and-moves"></a><span data-ttu-id="528fb-126">Platzierung von Postfach- und Verschiebungen</span><span class="sxs-lookup"><span data-stu-id="528fb-126">Mailbox placement and moves</span></span>
<span data-ttu-id="528fb-127">Nach Abschluss der erforderlichen Konfigurationsschritte Multi-Geo der Microsoft berücksichtigt Exchange Online Attributs **PreferredDataLocation** für Benutzerobjekte in Azure AD.</span><span class="sxs-lookup"><span data-stu-id="528fb-127">After Microsoft completes the prerequisite Multi-Geo configuration steps, Exchange Online will honor the **PreferredDataLocation** attribute on user objects in Azure AD.</span></span>

<span data-ttu-id="528fb-p105">Exchange Online synchronisiert die **PreferredDataLocation** -Eigenschaft aus dem Azure Active Directory in die **MailboxRegion** -Eigenschaft in der Exchange Online-Verzeichnisdienst. Der Wert der **MailboxRegion** bestimmt die Platzierung von Benutzerpostfächern und alle zugehörigen archivpostfächer Geo. Es ist nicht möglich, eines Benutzers primären Postfach und Archiv von Postfächern in verschiedenen Geos befinden, um zu konfigurieren. Pro Benutzerobjekt kann nur eine Geo konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="528fb-p105">Exchange Online synchronizes the **PreferredDataLocation** property from Azure AD into the **MailboxRegion** property in the Exchange Online directory service. The value of **MailboxRegion** determines the Geo where user mailboxes and any associated archive mailboxes will be placed. It isn't possible to configure a user's primary mailbox and archive mailboxes to reside in different Geos. Only one Geo may be configured per user object.</span></span>

- <span data-ttu-id="528fb-132">Wenn ein Benutzer mit einem vorhandenen Postfach **PreferredDataLocation** konfiguriert ist, wird das Postfach automatisch in der angegebenen Geo verschoben werden.</span><span class="sxs-lookup"><span data-stu-id="528fb-132">When **PreferredDataLocation** is configured on a user with an existing mailbox, the mailbox will be automatically moved to the specified Geo.</span></span> 

- <span data-ttu-id="528fb-133">Wenn ein Benutzer ohne ein vorhandenes Postfach **PreferredDataLocation** konfiguriert ist, wird das Postfach in der angegebenen Geo bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="528fb-133">When **PreferredDataLocation** is configured on a user without an existing mailbox, the mailbox will be provisioned into the specified Geo.</span></span> 

- <span data-ttu-id="528fb-134">Wenn keine Geo angegeben ist, wird das Postfach in der standardmäßigen Geo platziert werden.</span><span class="sxs-lookup"><span data-stu-id="528fb-134">If no Geo is specified, the mailbox will be placed in the default Geo.</span></span>

<span data-ttu-id="528fb-p106">**Hinweis**: Multi-Geo-Funktionen und Skype für Business Online gehostet Regional Besprechungen, verwenden Sie die **PreferredDataLocation** -Eigenschaft auf User-Objekte, um Dienste zu suchen. Wenn Sie **PreferredDataLocation** Werte für Benutzerobjekte Regional gehosteten Besprechungen konfigurieren, wird das Postfach für diesen Benutzer automatisch nach der angegebenen Geo verschoben, nachdem Multi-Geo auf dem Office 365-Mandanten aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="528fb-p106">**Note**: Multi-Geo capabilities and Skype for Business Online regionally hosted meetings both use the **PreferredDataLocation** property on user objects to locate services. If you configure **PreferredDataLocation** values on user objects for regionally hosted meetings, the mailbox for those users will be automatically moved to the specified Geo after Multi-Geo is enabled on the Office 365 tenant.</span></span>

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a><span data-ttu-id="528fb-137">Einschränkungen für Multi-Geo in Exchange Online</span><span class="sxs-lookup"><span data-stu-id="528fb-137">Feature limitations for Multi-Geo in Exchange Online</span></span>
1. <span data-ttu-id="528fb-p107">Nur Benutzerpostfächer, Ressourcenpostfächer (Raum- und Equipment Mailboxes) und freigegebene Postfächer Multi-Geo-Features nicht unterstützt. Sie können nur Postfächer für Öffentliche Ordner und Office 365-Gruppen in der Kunde home Geo platzieren.</span><span class="sxs-lookup"><span data-stu-id="528fb-p107">Only user mailboxes, resource mailboxes (room and equipment mailboxes), and shared mailboxes support Multi-Geo features. You can only place public folder mailboxes and Office 365 Groups in the customer's home Geo.</span></span>
 
2. <span data-ttu-id="528fb-p108">Sicherheit und Richtlinientreue (beispielsweise Überwachung und eDiscovery) in der Exchange-Verwaltungskonsole (EAC) verfügbaren Features sind nicht in Organisationen mit mehreren geografisch verfügbar. Stattdessen müssen Sie [Office 365-Sicherheit und Compliance Center](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) verwenden, um Features für Sicherheit und Einhaltung von Bestimmungen zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="528fb-p108">Security and compliance features (for example, auditing and eDiscovery) that are available in the Exchange admin center (EAC) aren't available in Multi-Geo organizations. Instead, you need to use the [Office 365 Security & Compliance Center](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) to configure security and compliance features.</span></span>

3. <span data-ttu-id="528fb-p109">Outlook für Mac-Benutzer kann einen vorübergehenden Verlust des Zugriffs auf ihre Ordner Onlinearchiv auftreten, während Sie ihr Postfach in eine neue Geo verschieben. Diese Bedingung tritt auf, wenn die primäre Benutzerordner und archivpostfächer befinden sich in unterschiedlichen Geos, da das Verschieben von Postfächern Cross-Geo zu unterschiedlichen Zeiten abgeschlossen werden können.</span><span class="sxs-lookup"><span data-stu-id="528fb-p109">Outlook for Mac users may experience a temporary loss of access to their Online Archive folder while you move their mailbox to a new Geo. This condition occurs when the user's the primary and archive mailboxes are in different Geos, because cross-Geo mailbox moves may complete at different times.</span></span>

4. <span data-ttu-id="528fb-p110">Benutzer können nicht *Postfachordner* für Geos in Outlook im Web (früher als Outlook Web App oder OWA bezeichnet) freigeben. Beispielsweise kann kein Benutzer in der Europäischen Union Outlook im Web verwenden, um einen freigegebenen Ordner in einem Postfach zu öffnen, die sich in den USA befindet. Outlook auf dem Web-Benutzer kann jedoch *anderer Postfächer an* in anderen Geos öffnen, indem Sie mit einem separaten Browserfenster wie beschrieben in [eine andere Person Postfach in einem separaten Browserfenster in Outlook Web App zu öffnen](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).</span><span class="sxs-lookup"><span data-stu-id="528fb-p110">Users can't share *mailbox folders* across Geos in Outlook on the web (formerly known as Outlook Web App or OWA). For example, a user in the European Union can't use Outlook on the web to open a shared folder in a mailbox that's located in the United States. However, Outlook on the web users can open *other mailboxes* in different Geos by using a separate browser window as described in [Open another person’s mailbox in a separate browser window in Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).</span></span>

    <span data-ttu-id="528fb-147">**Hinweis**: Cross-Geo Postfach Ordnerfreigabe in Outlook auf Windows unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="528fb-147">**Note**: Cross-Geo mailbox folder sharing is supported in Outlook on Windows.</span></span>

5. <span data-ttu-id="528fb-p111">Derzeit wird Cross-Geo kalenderdelegierung in Outlook im Web nicht unterstützt. Cross-Geo kalenderdelegierung wird in Outlook auf Windows unterstützt.</span><span class="sxs-lookup"><span data-stu-id="528fb-p111">Currently, cross-Geo calendar delegation isn't supported in Outlook on the web. Cross-Geo calendar delegation is supported in Outlook on Windows.</span></span>

## <a name="administration"></a><span data-ttu-id="528fb-150">Administration</span><span class="sxs-lookup"><span data-stu-id="528fb-150">Administration</span></span> 
<span data-ttu-id="528fb-p112">Remote-PowerShell ist erforderlich, um anzeigen und Konfigurieren von Geo-bezogenen Eigenschaften in der Office 365-Umgebung. Informationen zu verschiedenen PowerShell-Module zum Verwalten von Office 365 finden Sie unter [Verwalten von Office 365 und Exchange Online mit Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6)verwendet.</span><span class="sxs-lookup"><span data-stu-id="528fb-p112">Remote PowerShell is required to view and configure Geo-related properties in your Office 365 environment. For information on various PowerShell modules used to administer Office 365, see [Managing Office 365 and Exchange Online with Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6).</span></span>

- <span data-ttu-id="528fb-p113">Sie benötigen die [Microsoft Azure Active Directory-PowerShell-Modul](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 oder später in v1.x an die **PreferredDataLocation** -Eigenschaft auf User-Objekte angezeigt werden. Zum Verbinden mit Azure AD-PowerShell finden Sie unter [Connect to Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span><span class="sxs-lookup"><span data-stu-id="528fb-p113">You need the [Microsoft Azure Active Directory PowerShell Module](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 or later in v1.x to see the **PreferredDataLocation** property on user objects. To connect to Azure AD PowerShell, see [Connect to Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span></span> 

- <span data-ttu-id="528fb-155">Zum Verbinden mit Exchange Online PowerShell finden Sie unter [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span><span class="sxs-lookup"><span data-stu-id="528fb-155">To connect to Exchange Online PowerShell, see [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span></span> 

### <a name="connect-directly-to-a-specific-geo-using-exchange-online-powershell"></a><span data-ttu-id="528fb-156">Verbinden Sie mit einer bestimmten Geo von Exchange Online PowerShell direkt</span><span class="sxs-lookup"><span data-stu-id="528fb-156">Connect directly to a specific Geo using Exchange Online PowerShell</span></span>
<span data-ttu-id="528fb-p114">Exchange Online PowerShell wird in der Regel mit der standardmäßigen Geo verbunden. Aber Sie können auch direkt mit nicht standardmäßigen Geos anschließen. Es wird empfohlen, aufgrund von Leistungssteigerungen direkt an den nicht standardmäßigen Geo verbinden, wenn Sie nur Benutzer in dieser Geo verwalten.</span><span class="sxs-lookup"><span data-stu-id="528fb-p114">Typically, Exchange Online PowerShell will connect to the default Geo. But, you can also connect directly to non-default Geos. Because of performance improvements, we recommend connecting directly to the non-default Geo when you only manage users in that Geo.</span></span>

<span data-ttu-id="528fb-p115">Zum Verbinden mit einer bestimmten Geo ist der Parameter *ConnectionUri* anders als die regulären Verbindung Anweisungen. Die restlichen Befehle und Werte sind identisch. Die Schritte sind:</span><span class="sxs-lookup"><span data-stu-id="528fb-p115">To connect to a specific Geo, the *ConnectionUri* parameter is different than the regular connection instructions. The rest of the commands and values are the same. The steps are:</span></span>

1. <span data-ttu-id="528fb-163">Öffnen Sie auf dem lokalen Computer Windows PowerShell, und führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="528fb-163">On your local computer, open Windows PowerShell and run the following command:</span></span>
    
    ```
    $UserCredential = Get-Credential
    ```
   <span data-ttu-id="528fb-164">Klicken Sie im Dialogfeld **Windows PowerShell anmelden** Geben Sie die geschäftliche Rufnummer oder Schule Konto und Kennwort ein, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="528fb-164">In the **Windows PowerShell Credential Request** dialog box, type your work or school account and password, and then click **OK**.</span></span>
    
2. <span data-ttu-id="528fb-p116">Ersetzen Sie `<emailaddress>` mit der e-Mail-Adresse von **jedem** Postfach im Ziel Geo und den folgenden Befehl ausführen. Die Berechtigungen für das Postfach und in Bezug auf Ihre Anmeldeinformationen in Schritt 1 sind keinen Faktor. die e-Mail-Adresse weist einfach Exchange Online, wo Sie eine Verbindung herstellen.</span><span class="sxs-lookup"><span data-stu-id="528fb-p116">Replace `<emailaddress>` with the email address of **any** mailbox in the target Geo and run the following command. Your permissions on the mailbox and the relationship to your credentials in Step 1 are not a factor; the email address simply tells Exchange Online where to connect.</span></span>
  
   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   <span data-ttu-id="528fb-167">Wenn olga@contoso.onmicrosoft.com die e-Mail-Adresse eines Postfachs in die Geo gültig, den Sie eine Verbindung herstellen möchten ist, führen Sie beispielsweise den folgenden Befehl ein:</span><span class="sxs-lookup"><span data-stu-id="528fb-167">For example, if olga@contoso.onmicrosoft.com is the email address of a valid mailbox in the Geo you want to connect, run the following command:</span></span>

   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```
3. <span data-ttu-id="528fb-168">Führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="528fb-168">Run the following command:</span></span>
    
    ```
    Import-PSSession $Session
    ```

### <a name="azure-ad-connect-version-requirements"></a><span data-ttu-id="528fb-169">Anforderungen an Softwareversionen von Azure Active Directory verbinden</span><span class="sxs-lookup"><span data-stu-id="528fb-169">Azure AD Connect version requirements</span></span>
<span data-ttu-id="528fb-p117">Verbinden von AAD Version 1.1.524.0 oder höher ist die einzige unterstützte Methode zum Festlegen der **PreferredDataLocation** -Eigenschaft auf User-Objekte, die synchronisiert werden aus dem lokalen Active Directory. Ausführliche Anweisungen finden Sie unter [Azure Active Directory verbinden Sync: Konfigurieren des bevorzugten Datenspeicherort für Office 365-Ressourcen](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span><span class="sxs-lookup"><span data-stu-id="528fb-p117">AAD Connect version 1.1.524.0 or later is the only supported method for setting the **PreferredDataLocation** property on user objects that are synchronized from on-premises Active Directory. For detailed instructions, see [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

### <a name="geo-codes"></a><span data-ttu-id="528fb-172">Geo-Codes</span><span class="sxs-lookup"><span data-stu-id="528fb-172">Geo Codes</span></span>
<span data-ttu-id="528fb-p118">Drei Buchstaben Codes können Sie die geografisch in der **PreferredDataLocation** -Eigenschaft festlegen. Die folgende Tabelle enthält die Codes für die Geos verfügbar:</span><span class="sxs-lookup"><span data-stu-id="528fb-p118">You use three-letter codes to specify the Geo in the **PreferredDataLocation** property. The following table lists the codes for the available Geos:</span></span>

|<span data-ttu-id="528fb-175">Geo</span><span class="sxs-lookup"><span data-stu-id="528fb-175">Geo</span></span> |<span data-ttu-id="528fb-176">Code</span><span class="sxs-lookup"><span data-stu-id="528fb-176">Code</span></span> |
|---------|---------|
|<span data-ttu-id="528fb-177">Asien-Pazifik</span><span class="sxs-lookup"><span data-stu-id="528fb-177">Asia/Pacific</span></span> |<span data-ttu-id="528fb-178">APC</span><span class="sxs-lookup"><span data-stu-id="528fb-178">APC</span></span> |
|<span data-ttu-id="528fb-179">Australien</span><span class="sxs-lookup"><span data-stu-id="528fb-179">Australia</span></span> |<span data-ttu-id="528fb-180">AUS</span><span class="sxs-lookup"><span data-stu-id="528fb-180">AUS</span></span> |
|<span data-ttu-id="528fb-181">Kanada</span><span class="sxs-lookup"><span data-stu-id="528fb-181">Canada</span></span> |<span data-ttu-id="528fb-182">KÖNNEN</span><span class="sxs-lookup"><span data-stu-id="528fb-182">CAN</span></span> |
|<span data-ttu-id="528fb-183">Europäische Union</span><span class="sxs-lookup"><span data-stu-id="528fb-183">European Union</span></span> |<span data-ttu-id="528fb-184">EUR</span><span class="sxs-lookup"><span data-stu-id="528fb-184">EUR</span></span> |
|<span data-ttu-id="528fb-185">Indien</span><span class="sxs-lookup"><span data-stu-id="528fb-185">India</span></span> |<span data-ttu-id="528fb-186">IND</span><span class="sxs-lookup"><span data-stu-id="528fb-186">IND</span></span> |
|<span data-ttu-id="528fb-187">Japan</span><span class="sxs-lookup"><span data-stu-id="528fb-187">Japan</span></span> |<span data-ttu-id="528fb-188">JAPANISCHE</span><span class="sxs-lookup"><span data-stu-id="528fb-188">JPN</span></span> |
|<span data-ttu-id="528fb-189">Korea</span><span class="sxs-lookup"><span data-stu-id="528fb-189">Korea</span></span> |<span data-ttu-id="528fb-190">KOREANISCHE</span><span class="sxs-lookup"><span data-stu-id="528fb-190">KOR</span></span> |
|<span data-ttu-id="528fb-191">Vereinigtes Königreich</span><span class="sxs-lookup"><span data-stu-id="528fb-191">United Kingdom</span></span> |<span data-ttu-id="528fb-192">GBR</span><span class="sxs-lookup"><span data-stu-id="528fb-192">GBR</span></span> |
|<span data-ttu-id="528fb-193">USA</span><span class="sxs-lookup"><span data-stu-id="528fb-193">United States</span></span> |<span data-ttu-id="528fb-194">NAME</span><span class="sxs-lookup"><span data-stu-id="528fb-194">NAM</span></span> |

<span data-ttu-id="528fb-p119">**Hinweis**: die Eigenschaften **PreferredDataLocation** und **MailboxRegion** sind Zeichenfolgen mit keine Fehler überprüfen. Wenn Sie einen ungültigen Wert (beispielsweise NAN) eingeben wird das Postfach in der standardmäßigen Geo platziert werden.</span><span class="sxs-lookup"><span data-stu-id="528fb-p119">**Note**: The **PreferredDataLocation** and **MailboxRegion** properties are strings with no error checking. If you enter an invalid value (for example, NAN) the mailbox will be placed in the default Geo.</span></span>

### <a name="view-the-available-geos-that-are-configured-in-your-exchange-online-organization"></a><span data-ttu-id="528fb-197">Anzeigen der verfügbaren Geos, die in Ihrer Exchange Online-Organisation konfiguriert sind</span><span class="sxs-lookup"><span data-stu-id="528fb-197">View the available Geos that are configured in your Exchange Online organization</span></span>
<span data-ttu-id="528fb-198">Um die Liste der konfigurierten Geos in Ihrer Exchange Online-Organisation anzuzeigen, führen Sie den folgenden Befehl im Exchange Online PowerShell:</span><span class="sxs-lookup"><span data-stu-id="528fb-198">To see the list of configured Geos in your Exchange Online organization, run the following command in Exchange Online PowerShell:</span></span>

```
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table Region
```

<span data-ttu-id="528fb-199">Die Ausgabe des Befehls sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="528fb-199">The output of the command looks like this:</span></span>

```
Region
------
APC
AUS
CAN
EUR
GBR
JPN
KOR
NAM
```

### <a name="find-the-geo-location-of-a-mailbox"></a><span data-ttu-id="528fb-200">Suchen Sie den Speicherort Geo eines Postfachs</span><span class="sxs-lookup"><span data-stu-id="528fb-200">Find the Geo location of a mailbox</span></span>
<span data-ttu-id="528fb-201">Das Cmdlet **Get-Mailbox** in Exchange Online PowerShell die folgenden Geo-bezogene Eigenschaften auf Postfächer angezeigt:</span><span class="sxs-lookup"><span data-stu-id="528fb-201">The **Get-Mailbox** cmdlet in Exchange Online PowerShell displays the following Geo-related properties on mailboxes:</span></span>

- <span data-ttu-id="528fb-202">**Datenbank**: die ersten 3 Buchstaben des Datenbanknamens entsprechen Geo-Code, dem Sie darüber informiert, in dem das Postfach aktuell gespeichert ist.</span><span class="sxs-lookup"><span data-stu-id="528fb-202">**Database**: The first 3 letters of the database name correspond to the Geo code, which tells you where the mailbox is currently located.</span></span>

- <span data-ttu-id="528fb-203">**MailboxRegion**: Gibt den Geo-Code, die von der Administrator (aus **PreferredDataLocation** in Azure Active Directory synchronisiert) festgelegt wurde.</span><span class="sxs-lookup"><span data-stu-id="528fb-203">**MailboxRegion**: Specifies the Geo code that was set by the admin (synchronized from **PreferredDataLocation** in Azure AD).</span></span>

- <span data-ttu-id="528fb-204">**MailboxRegionLastUpdateTime**: Gibt an, wann MailboxRegion (automatisch oder manuell) zuletzt aktualisiert wurde.</span><span class="sxs-lookup"><span data-stu-id="528fb-204">**MailboxRegionLastUpdateTime**: Indicates when MailboxRegion was last updated (either automatically or manually).</span></span>

<span data-ttu-id="528fb-205">Um diese Eigenschaften für ein Postfach anzuzeigen, verwenden Sie die folgende Syntax:</span><span class="sxs-lookup"><span data-stu-id="528fb-205">To see these properties for a mailbox, use the following syntax:</span></span>

```
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

<span data-ttu-id="528fb-206">Um die Geo-Informationen für das Postfach chris@contoso.onmicrosoft.com angezeigt wird, führen Sie beispielsweise den folgenden Befehl:</span><span class="sxs-lookup"><span data-stu-id="528fb-206">For example, to see the Geo information for the mailbox chris@contoso.onmicrosoft.com, run the following command:</span></span>

```
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

<span data-ttu-id="528fb-207">Die Ausgabe des Befehls sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="528fb-207">The output of the command looks like this:</span></span>

```
Database                    : EURPR03DG077-db007 
MailboxRegion               : EUR 
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM 
```

> [!NOTE]
> <span data-ttu-id="528fb-208">Wenn der Geo-Code in den Datenbanknamen **MailboxRegion** Wert entspricht, wird das Postfach automatisch in die Geo angegeben durch den Wert **MailboxRegion** (Exchange Online sucht nach einer Abweichung zwischen diese Eigenschaftswerte) verschoben werden.</span><span class="sxs-lookup"><span data-stu-id="528fb-208">If the Geo code in the database name doesn't match **MailboxRegion** value, the mailbox will be automatically moved to the Geo specified by the **MailboxRegion** value (Exchange Online looks for a mismatch between these property values).</span></span>

### <a name="move-an-existing-cloud-mailbox-to-a-specific-geo"></a><span data-ttu-id="528fb-209">Verschieben eines vorhandenen Cloud-Postfachs in einer bestimmten Geo</span><span class="sxs-lookup"><span data-stu-id="528fb-209">Move an existing cloud mailbox to a specific Geo</span></span>
<span data-ttu-id="528fb-210">Verwenden Sie die Cmdlets **Get-MsolUser** und **Set-MsolUser** in Azure AD-Moduls für Windows PowerShell anzeigen oder Angeben der Geo, unter dem Postfach eines Benutzers gespeichert wird.</span><span class="sxs-lookup"><span data-stu-id="528fb-210">Use the **Get-MsolUser** and **Set-MsolUser** cmdlets in the Azure AD Module for Windows PowerShell to view or specify the Geo where a user's mailbox will be stored.</span></span>

<span data-ttu-id="528fb-211">Um den Wert **PreferredDataLocation** für einen Benutzer anzuzeigen, verwenden Sie diese Syntax in Azure AD-PowerShell:</span><span class="sxs-lookup"><span data-stu-id="528fb-211">To view the **PreferredDataLocation** value for a user, use this syntax in Azure AD PowerShell:</span></span>

```
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

<span data-ttu-id="528fb-212">Um den **PreferredDataLocation** -Wert für den Benutzer michelle@contoso.onmicrosoft.com angezeigt wird, führen Sie beispielsweise den folgenden Befehl:</span><span class="sxs-lookup"><span data-stu-id="528fb-212">For example, to see the **PreferredDataLocation** value for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

```
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

<span data-ttu-id="528fb-213">Die Ausgabe des Befehls sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="528fb-213">The output of the command looks like this:</span></span>

```
UserPrincipalName     : michelle@contoso.onmicrosoft.com
PreferredDataLocation : EUR
```

<span data-ttu-id="528fb-214">Verwenden Sie die folgende Syntax zum Ändern des **PreferredDataLocation** -Werts für ein nur-Cloud-Benutzerobjekt in Azure AD-PowerShell:</span><span class="sxs-lookup"><span data-stu-id="528fb-214">To modify the **PreferredDataLocation** value for a cloud-only user object, use the following syntax in Azure AD PowerShell:</span></span>

``` 
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoCode>
```

<span data-ttu-id="528fb-215">Um den **PreferredDataLocation** -Wert, der Europäischen Union (EUR) für den Benutzer michelle@contoso.onmicrosoft.com festzulegen, führen Sie beispielsweise den folgenden Befehl:</span><span class="sxs-lookup"><span data-stu-id="528fb-215">For example, to set the **PreferredDataLocation** value to the European Union (EUR) for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

``` 
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

<span data-ttu-id="528fb-216">**Notes**:</span><span class="sxs-lookup"><span data-stu-id="528fb-216">**Notes**:</span></span>

- <span data-ttu-id="528fb-p120">Wie bereits erwähnt für synchronisierte User-Objekte aus dem lokalen Active Directory können nicht Sie dieses Verfahren verwenden. Sie müssen den **PreferredDataLocation** -Wert mit AAD verbinden zu ändern. Weitere Informationen finden Sie unter [Azure Active Directory verbinden Sync: Konfigurieren des bevorzugten Datenspeicherort für Office 365-Ressourcen](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span><span class="sxs-lookup"><span data-stu-id="528fb-p120">As mentioned previously for synchronized user objects from on-premises Active Directory, you can't use this procedure. You need to change the **PreferredDataLocation** value using AAD Connect. For more information, see [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span> 

- <span data-ttu-id="528fb-220">Wie lange es dauert, ein Postfach verschieben von mehreren Faktoren abhängig:</span><span class="sxs-lookup"><span data-stu-id="528fb-220">How long it takes to move a mailbox depends on several factors:</span></span>
 
  - <span data-ttu-id="528fb-221">Die Größe und Typ des Postfachs.</span><span class="sxs-lookup"><span data-stu-id="528fb-221">The size and type of mailbox.</span></span>
 
  - <span data-ttu-id="528fb-222">Die Anzahl der Postfächer, die verschoben werden.</span><span class="sxs-lookup"><span data-stu-id="528fb-222">The number of mailboxes being moved.</span></span>
 
  - <span data-ttu-id="528fb-223">Die Verfügbarkeit von Ressourcen verschieben.</span><span class="sxs-lookup"><span data-stu-id="528fb-223">The availability of move resources.</span></span>

#### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a><span data-ttu-id="528fb-224">Move Postfächer, die auf die Aufbewahrung für eventuelle Rechtsstreitigkeiten sind deaktiviert</span><span class="sxs-lookup"><span data-stu-id="528fb-224">Move disabled mailboxes that are on Litigation Hold</span></span>
<span data-ttu-id="528fb-p121">Postfächer auf Aufbewahrung für eventuelle Rechtsstreitigkeiten, die für eDiscovery beibehalten werden, die Zwecke verschoben werden können, indem Sie ihre **PreferredDataLocation** Wert im deaktivierten Zustand deaktiviert. Verschieben eines deaktiviert Postfachs beweissicherungsverfahren:</span><span class="sxs-lookup"><span data-stu-id="528fb-p121">Disabled mailboxes on Litigation Hold that are preserved for eDiscovery purposes can't be moved by changing their **PreferredDataLocation** value in their disabled state. To move a disabled mailbox on litigation hold:</span></span>

1. <span data-ttu-id="528fb-227">Das Postfach vorübergehend eine Lizenz zuweisen.</span><span class="sxs-lookup"><span data-stu-id="528fb-227">Temporarily assign a license to the mailbox.</span></span>

2. <span data-ttu-id="528fb-228">Ändern der **PreferredDataLocation**.</span><span class="sxs-lookup"><span data-stu-id="528fb-228">Change the **PreferredDataLocation**.</span></span>

3. <span data-ttu-id="528fb-229">Entfernen Sie die Lizenz aus dem Postfach, nachdem er auf den ausgewählten Geo verschoben wurde, um wieder in den aktiven Zustand zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="528fb-229">Remove the license from the mailbox after it has been moved to the selected Geo to put it back into the disabled state.</span></span>

### <a name="create-new-cloud-mailboxes-in-a-specific-geo"></a><span data-ttu-id="528fb-230">Erstellen Sie neue Cloud-Postfächer in einer bestimmten Geo</span><span class="sxs-lookup"><span data-stu-id="528fb-230">Create new cloud mailboxes in a specific Geo</span></span> 
<span data-ttu-id="528fb-231">Zum Erstellen eines neuen Postfachs in einem bestimmten Geo müssen Sie führen Sie einen der folgenden Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="528fb-231">To create a new mailbox in a specific Geo, you need to do either of these steps:</span></span>

- <span data-ttu-id="528fb-232">Konfigurieren Sie den Wert **PreferredDataLocation** , wie beschrieben im vorherigen Abschnitt *vor dem* das Postfach in Exchange Online (beispielsweise durch Konfigurieren des **PreferredDataLocation** -Werts für einen Benutzer vor dem Zuweisen einer Lizenz) erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="528fb-232">Configure the **PreferredDataLocation** value as described in the previous section *before* the mailbox is created in Exchange Online (for example, by configuring the **PreferredDataLocation** value on a user before assigning a license).</span></span> 

- <span data-ttu-id="528fb-233">Weisen Sie eine Lizenz zur selben Zeit, den, die Sie den Wert **PreferredDataLocation** festlegen.</span><span class="sxs-lookup"><span data-stu-id="528fb-233">Assign a license at the same time you set the **PreferredDataLocation** value.</span></span>

<span data-ttu-id="528fb-234">Verwenden Sie die folgende Syntax, um einen neuen Cloud-only lizenzierten Benutzer (nicht AAD verbinden synchronisiert) in einer bestimmten Geo erstellen, in Azure AD-PowerShell:</span><span class="sxs-lookup"><span data-stu-id="528fb-234">To create a new cloud-only licensed user (not AAD Connect synchronized) in a specific Geo, use the following syntax in Azure AD PowerShell:</span></span>

```
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoCode> 
```
<span data-ttu-id="528fb-235">In diesem Beispiel erstellen Sie ein neues Benutzerkonto für Elizabeth Brunner mit den folgenden Werten:</span><span class="sxs-lookup"><span data-stu-id="528fb-235">This example create a new user account for Elizabeth Brunner with the following values:</span></span>

- <span data-ttu-id="528fb-236">Benutzerprinzipalname: ebrunner@contoso.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="528fb-236">User principal name: ebrunner@contoso.onmicrosoft.com</span></span>

- <span data-ttu-id="528fb-237">Vorname: Elizabeth</span><span class="sxs-lookup"><span data-stu-id="528fb-237">First name: Elizabeth</span></span>

- <span data-ttu-id="528fb-238">Nachname: Brunner</span><span class="sxs-lookup"><span data-stu-id="528fb-238">Last name: Brunner</span></span>

- <span data-ttu-id="528fb-239">Anzeigename Elizabeth Brunner</span><span class="sxs-lookup"><span data-stu-id="528fb-239">Display name Elizabeth Brunner</span></span>

- <span data-ttu-id="528fb-240">Kennwort: zufällig generiert und in die Ergebnisse des Befehls (da wir den Parameter *Password* nicht verwenden)</span><span class="sxs-lookup"><span data-stu-id="528fb-240">Password: randomly-generated and shown in the results of the command (because we're not using the *Password* parameter)</span></span>

- <span data-ttu-id="528fb-241">Lizenz: Contoso:ENTERPRISEPREMIUM (E5)</span><span class="sxs-lookup"><span data-stu-id="528fb-241">License: contoso:ENTERPRISEPREMIUM (E5)</span></span>

<span data-ttu-id="528fb-242">3-Speicherort: Australien (AUS)</span><span class="sxs-lookup"><span data-stu-id="528fb-242">3- Location: Australia (AUS)</span></span>

```
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

<span data-ttu-id="528fb-243">Weitere Informationen zum Erstellen neuer Benutzerkonten und Suchen von LicenseAssignment Werte in Azure AD-PowerShell finden Sie unter [Erstellen von Benutzerkonten mit Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) und [Lizenzen anzeigen und-Dienste mit Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).</span><span class="sxs-lookup"><span data-stu-id="528fb-243">For more information about creating new user accounts and finding LicenseAssignment values in Azure AD PowerShell, see [Create user accounts with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) and [View licenses and services with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).</span></span>

> [!NOTE]
> <span data-ttu-id="528fb-p122">Wenn Sie zum Aktivieren eines Postfachs und benötigen das Postfach direkt in die Geo erstellt werden, die in **PreferredDataLocation**angegeben ist Exchange PowerShell verwenden, müssen Sie ein Exchange Online-Cmdlet wie **Enable-Mailbox** oder **New-Mailbox** verwenden direkt in der Clouddienst. Wenn Sie das Cmdlet **Enable-RemoteMailbox** lokale Exchange verwenden, wird das Postfach in der standardmäßigen Geo erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="528fb-p122">If you are using Exchange PowerShell to enable a mailbox and need the mailbox to be created directly in the Geo that's specified in **PreferredDataLocation**, you need to use an Exchange Online cmdlet such as **Enable-Mailbox** or **New-Mailbox** directly against the cloud service. If you use the **Enable-RemoteMailbox** on-premises Exchange cmdlet, the mailbox will be created in the default Geo.</span></span>

### <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo"></a><span data-ttu-id="528fb-246">Integrierte einer vorhandenen lokalen Postfächer in einer bestimmten Geo</span><span class="sxs-lookup"><span data-stu-id="528fb-246">Onboard existing on-premises mailboxes in a specific Geo</span></span>
<span data-ttu-id="528fb-247">Die standard-Onboarding-Tools und Prozesse können Sie ein Postfach aus einer lokalen Exchange-Organisation zu Exchange Online, einschließlich der [migrationsdashboard in der Exchange-Verwaltungskonsole](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331)und das Cmdlet [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) im Exchange Online migrieren PowerShell.</span><span class="sxs-lookup"><span data-stu-id="528fb-247">You can use the standard onboarding tools and processes to migrate a mailbox from an on-premises Exchange organization to Exchange Online, including the [Migration dashboard in the EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331), and the [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) cmdlet in Exchange Online PowerShell.</span></span>

<span data-ttu-id="528fb-p123">Der erste Schritt besteht, stellen Sie sicher, dass ein User-Objekt vorhanden ist, für jedes Postfach Onboarded, und stellen Sie sicher, dass der richtige Wert **PreferredDataLocation** in Azure Active Directory konfiguriert ist. Onboarding-Tools werden den Wert **PreferredDataLocation** berücksichtigt und migrieren Sie die Postfächer werden direkt an die angegebenen Geo.</span><span class="sxs-lookup"><span data-stu-id="528fb-p123">The first step is to verify a user object exists for each mailbox to be onboarded, and verify the correct **PreferredDataLocation** value is configured in Azure AD. The onboarding tools will respect the **PreferredDataLocation** value and will migrate the mailboxes directly to the specified Geo.</span></span>

<span data-ttu-id="528fb-250">Alternativ können Sie auf integrierte Postfächer direkt in einem bestimmten Geo mithilfe des Cmdlets [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) in Exchange Online PowerShell die folgenden Schritte aus.</span><span class="sxs-lookup"><span data-stu-id="528fb-250">Or, you can use the following steps to onboard mailboxes directly in a specific Geo using the [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) cmdlet in Exchange Online PowerShell.</span></span>

1. <span data-ttu-id="528fb-p124">Stellen Sie sicher, dass das Benutzerobjekt vorhanden ist, für jedes Postfach Onboarded und **PreferredDataLocation** in Azure Active Directory auf den gewünschten Wert festgelegt ist. Der Wert der **PreferredDataLocation** werden dem **MailboxRegion** -Attribut des entsprechenden e-Mail-Benutzerobjekts im Exchange Online synchronisiert.</span><span class="sxs-lookup"><span data-stu-id="528fb-p124">Verify the user object exists for each mailbox to be onboarded and that **PreferredDataLocation** is set to the desired value in Azure AD. The value of **PreferredDataLocation** will be synchronized to the **MailboxRegion** attribute of the corresponding mail user object in Exchange Online.</span></span>

2. <span data-ttu-id="528fb-253">Verbinden Sie direkt mit der bestimmte Satelliten Geo mithilfe der Connection-Anweisungen aus weiter oben in diesem Thema.</span><span class="sxs-lookup"><span data-stu-id="528fb-253">Connect directly to the specific satellite Geo using the connection instructions from earlier in this topic.</span></span>

3. <span data-ttu-id="528fb-254">In Exchange Online PowerShell speichern Sie die lokalen Administrator-Anmeldeinformationen, die zum Ausführen einer Migrations von Postfächern in einer Variablen, mithilfe des folgenden Befehls verwendet wird:</span><span class="sxs-lookup"><span data-stu-id="528fb-254">In Exchange Online PowerShell, store the on-premises administrator credentials that's used to perform a mailbox migration in a variable by running the following command:</span></span>

    ```
    $RC = Get-Credential
    ```

4. <span data-ttu-id="528fb-255">Erstellen Sie in Exchange Online PowerShell eine neue **New-MoveRequest** ähnlich dem folgenden Beispiel:</span><span class="sxs-lookup"><span data-stu-id="528fb-255">In Exchange Online PowerShell, create a new **New-MoveRequest** similar to the following example:</span></span> 

    ```
    New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
    ```

5. <span data-ttu-id="528fb-256">Wiederholen Sie Schritt #4 für jedes Postfach, die Sie benötigen zum Migrieren von lokalem Exchange zu der Satelliten Geo, den Sie derzeit verbunden sind.</span><span class="sxs-lookup"><span data-stu-id="528fb-256">Repeat step #4 for every mailbox you need to migrate from on-premises Exchange to the satellite Geo you are currently connected to.</span></span>

6. <span data-ttu-id="528fb-257">Wenn Sie zusätzliche Postfächer in einer anderen Satelliten Geo migrieren möchten, wiederholen Sie die Schritte 2 bis 4 für jede bestimmte Satelliten Geo.</span><span class="sxs-lookup"><span data-stu-id="528fb-257">If you need to migrate additional mailboxes to a different satellite Geo, repeat steps 2 through 4 for each specific satellite Geo.</span></span>

### <a name="multi-geo-reporting"></a><span data-ttu-id="528fb-258">Multi-Geo Reporting</span><span class="sxs-lookup"><span data-stu-id="528fb-258">Multi-Geo Reporting</span></span>
<span data-ttu-id="528fb-p125">**Multi-Geo Usage Reports** in Office 365 Administrationscenter zeigt die Anzahl der Benutzer von Geo. Der Bericht zeigt die Verteilung der Benutzer für den aktuellen Monat und bietet Verlaufsdaten für die letzten 6 Monate.</span><span class="sxs-lookup"><span data-stu-id="528fb-p125">**Multi-Geo Usage Reports** in the Office 365 admin center displays the user count by Geo. The report displays user distribution for the current month and provides historical data for the past 6 months.</span></span>
 
