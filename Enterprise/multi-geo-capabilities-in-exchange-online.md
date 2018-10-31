---
title: Multi-Geo-Funktionen in Exchange Online
ms.author: chrisda
author: chrisda
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Normal
ms.assetid: ''
description: Erweitern Sie Ihre Office 365-Anwesenheit auf mehrere geografische Regionen mit Multi-Geo-Funktionen in Exchange Online.
ms.openlocfilehash: 5f34a2da47b9767aa9dfe22c6be7237951128960
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849921"
---
# <a name="multi-geo-capabilities-in-exchange-online"></a><span data-ttu-id="3bf67-103">Multi-Geo-Funktionen in Exchange Online</span><span class="sxs-lookup"><span data-stu-id="3bf67-103">Multi-Geo Capabilities in Exchange Online</span></span>

<span data-ttu-id="3bf67-p101">Multi-Geo-Funktionen in Office 365 aktivieren Sie einen einzelnen Mandanten auf mehrere geografische Standorte hinweg erstrecken. Wenn Multi-Geo aktiviert ist, können Kunden den Speicherort der Exchange Online Inhalt von Postfächern (Daten im Ruhezustand) für jeden Benutzer einzeln auswählen.</span><span class="sxs-lookup"><span data-stu-id="3bf67-p101">Multi-Geo Capabilities in Office 365 enable a single tenant to span multiple geographic locations. When multi-geo is enabled, customers can select the location of Exchange Online mailbox content (data at rest) on a per-user basis.</span></span>

<span data-ttu-id="3bf67-p102">Ihres Standorts für Ihre anfänglichen Mandanten (bezeichnet als zentralen Ort) wird basierend auf Ihrer Adresse bestimmt. Wenn Multi-Geo aktiviert ist, können Sie Postfächer in zusätzliche Satelliten Speicherorte durch setzen:</span><span class="sxs-lookup"><span data-stu-id="3bf67-p102">Your initial tenant location (referred to as the central location) is determined based on your billing address. When multi-geo is enabled, you can place mailboxes in additional satellite locations by:</span></span>

- <span data-ttu-id="3bf67-108">Erstellen eines neuen Postfachs Exchange Online direkt an einem Speicherort Satelliten.</span><span class="sxs-lookup"><span data-stu-id="3bf67-108">Creating a new Exchange Online mailbox directly in a satellite location.</span></span>

- <span data-ttu-id="3bf67-109">Verschieben Sie ein vorhandenes Exchange Online-Postfach an einem Speicherort Satelliten.</span><span class="sxs-lookup"><span data-stu-id="3bf67-109">Moving an existing Exchange Online mailbox into a satellite location.</span></span>

- <span data-ttu-id="3bf67-110">Onboarding ein Postfach aus einer lokalen Exchange-Organisation direkt in einen Speicherort Satelliten.</span><span class="sxs-lookup"><span data-stu-id="3bf67-110">Onboarding a mailbox from an on-premises Exchange organization directly into a satellite location.</span></span>

<span data-ttu-id="3bf67-111">Die folgenden Geo Speicherorte stehen für die Verwendung in einer Serverfarm mit mehreren Geo-Konfiguration:</span><span class="sxs-lookup"><span data-stu-id="3bf67-111">The following geo locations are available for use in a Multi-Geo configuration:</span></span>

- <span data-ttu-id="3bf67-112">Asien-Pazifik</span><span class="sxs-lookup"><span data-stu-id="3bf67-112">Asia Pacific</span></span>

- <span data-ttu-id="3bf67-113">Australien</span><span class="sxs-lookup"><span data-stu-id="3bf67-113">Australia</span></span>

- <span data-ttu-id="3bf67-114">Kanada</span><span class="sxs-lookup"><span data-stu-id="3bf67-114">Canada</span></span>

- <span data-ttu-id="3bf67-115">Europäische Union</span><span class="sxs-lookup"><span data-stu-id="3bf67-115">European Union</span></span>

- <span data-ttu-id="3bf67-116">Frankreich</span><span class="sxs-lookup"><span data-stu-id="3bf67-116">France</span></span>

- <span data-ttu-id="3bf67-117">Indien (derzeit nur verfügbar für Kunden mit Abrechnung Adressen in Indien)</span><span class="sxs-lookup"><span data-stu-id="3bf67-117">India (currently only available to customers with billing addresses in India)</span></span>

- <span data-ttu-id="3bf67-118">Japan</span><span class="sxs-lookup"><span data-stu-id="3bf67-118">Japan</span></span>

- <span data-ttu-id="3bf67-119">Korea</span><span class="sxs-lookup"><span data-stu-id="3bf67-119">Korea</span></span>

- <span data-ttu-id="3bf67-120">Vereinigtes Königreich</span><span class="sxs-lookup"><span data-stu-id="3bf67-120">United Kingdom</span></span>

- <span data-ttu-id="3bf67-121">Vereinigte Staaten</span><span class="sxs-lookup"><span data-stu-id="3bf67-121">United States</span></span>

## <a name="prerequisite-configuration"></a><span data-ttu-id="3bf67-122">Erforderliche Konfiguration</span><span class="sxs-lookup"><span data-stu-id="3bf67-122">Prerequisite configuration</span></span>
<span data-ttu-id="3bf67-p103">Bevor Sie mit der Verwendung von Multi-Geo-Funktionen in Exchange Online beginnen können, muss Microsoft Ihren Exchange Online-Mandanten für die Unterstützung von Multi-Geo konfigurieren. In diesem einmaligen Konfigurationsprozess wird ausgelöst, nachdem Sie anordnen, dass Office 365 Multi-Geo und die Lizenzen in Ihrem Mandanten angezeigt. Diese einmalige Konfigurationsprozess sollte in der Regel weniger als 30 Tage dauern. Office 365 Multi-Geo bestellen, wenden Sie sich an Ihrem Microsoft-Partner. Weitere Informationen finden Sie unter https://aka.ms/Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="3bf67-p103">Before you can start using Multi-Geo capabilities in Exchange Online, Microsoft needs to configure your Exchange Online tenant for multi-geo support. This one-time configuration process is triggered after you order Office 365 Multi-Geo and the licenses show up in your tenant. This one-time configuration process should typically take less than 30 days to complete. To order Office 365 Multi-Geo, contact your Microsoft representative. For more information, see https://aka.ms/Multi-Geo.</span></span>

<span data-ttu-id="3bf67-p104">Sie erhalten Benachrichtigungen im [Office 365 Nachrichtencenter](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093) nach Abschluss die Konfiguration. Konfiguration wird automatisch ausgelöst, wenn Ihre Multi-Geo-Lizenzen in Ihrem Mandanten angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3bf67-p104">You'll receive notifications in the [Office 365 message center](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093) when your configuration has completed. Configuration is automatically triggered once your multi-geo licenses show up in your tenant.</span></span>

## <a name="mailbox-placement-and-moves"></a><span data-ttu-id="3bf67-130">Platzierung von Postfach- und Verschiebungen</span><span class="sxs-lookup"><span data-stu-id="3bf67-130">Mailbox placement and moves</span></span>
<span data-ttu-id="3bf67-131">Nach Abschluss der Konfigurationsschritte erforderliche Multi-Geo Microsoft berücksichtigt Exchange Online Attributs **PreferredDataLocation** für Benutzerobjekte in Azure AD.</span><span class="sxs-lookup"><span data-stu-id="3bf67-131">After Microsoft completes the prerequisite multi-geo configuration steps, Exchange Online will honor the **PreferredDataLocation** attribute on user objects in Azure AD.</span></span>

<span data-ttu-id="3bf67-p105">Exchange Online synchronisiert die **PreferredDataLocation** -Eigenschaft aus dem Azure Active Directory in die **MailboxRegion** -Eigenschaft in der Exchange Online-Verzeichnisdienst. Der Wert der **MailboxRegion** bestimmt die Platzierung von Benutzerpostfächern und alle zugehörigen archivpostfächer Geo. Es ist nicht möglich, eines Benutzers primären Postfach und Archiv von Postfächern in geografisch verschiedenen Standorten befinden, um zu konfigurieren. Pro User-Objekt kann nur über einen Geo Speicherort konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="3bf67-p105">Exchange Online synchronizes the **PreferredDataLocation** property from Azure AD into the **MailboxRegion** property in the Exchange Online directory service. The value of **MailboxRegion** determines the Geo where user mailboxes and any associated archive mailboxes will be placed. It is not possible to configure a user's primary mailbox and archive mailboxes to reside in different geo locations. Only one geo location may be configured per user object.</span></span>

- <span data-ttu-id="3bf67-136">Wenn ein Benutzer mit einem vorhandenen Postfach **PreferredDataLocation** konfiguriert ist, wird das Postfach in eine Warteschlange Umsetzung aufgenommen werden und automatisch an den angegebenen Geo-Speicherort verschoben.</span><span class="sxs-lookup"><span data-stu-id="3bf67-136">When **PreferredDataLocation** is configured on a user with an existing mailbox, the mailbox will be put into a relocation queue and automatically moved to the specified geo location.</span></span> 

- <span data-ttu-id="3bf67-137">Wenn ein Benutzer ohne ein vorhandenes Postfach **PreferredDataLocation** konfiguriert ist, wird das Postfach in der angegebenen Geo Speicherort bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="3bf67-137">When **PreferredDataLocation** is configured on a user without an existing mailbox, the mailbox will be provisioned into the specified geo location.</span></span> 

- <span data-ttu-id="3bf67-138">Wenn **PreferredDataLocation** auf einem bestimmten Benutzer nicht angegeben wird, wird das Postfach in der zentralen Speicherort platziert werden.</span><span class="sxs-lookup"><span data-stu-id="3bf67-138">When **PreferredDataLocation** is not specified on a user, the mailbox will be placed in the central location.</span></span>

- <span data-ttu-id="3bf67-139">Wenn der Code **PreferredDataLocation** falsch ist (z. B. ein Typ von NAN anstelle von Name), wird das Postfach in der zentralen Speicherort platziert werden.</span><span class="sxs-lookup"><span data-stu-id="3bf67-139">If the **PreferredDataLocation** code is incorrect (e.g. a type of NAN instead of NAM), the mailbox will be placed in the central location.</span></span>

<span data-ttu-id="3bf67-p106">**Hinweis**: Multi-Geo-Funktionen und Skype für Business Online gehostet Regional Besprechungen, verwenden Sie die **PreferredDataLocation** -Eigenschaft auf User-Objekte, um Dienste zu suchen. Wenn Sie **PreferredDataLocation** Werte für Benutzerobjekte Regional gehosteten Besprechungen konfigurieren, wird das Postfach für diesen Benutzer automatisch an den angegebenen Geo Speicherort verschoben, nachdem Multi-Geo auf dem Office 365-Mandanten aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="3bf67-p106">**Note**: multi-geo capabilities and Skype for Business Online regionally hosted meetings both use the **PreferredDataLocation** property on user objects to locate services. If you configure **PreferredDataLocation** values on user objects for regionally hosted meetings, the mailbox for those users will be automatically moved to the specified geo location after multi-geo is enabled on the Office 365 tenant.</span></span>

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a><span data-ttu-id="3bf67-142">Einschränkungen für Multi-Geo in Exchange Online</span><span class="sxs-lookup"><span data-stu-id="3bf67-142">Feature limitations for Multi-Geo in Exchange Online</span></span>
1. <span data-ttu-id="3bf67-p107">Nur Benutzerpostfächer, Ressourcenpostfächer (Raum- und Equipment Mailboxes) und freigegebene Postfächer Multi-Geo-Features nicht unterstützt. Öffentliche Ordner-Postfächer und Office 365 Gruppen bleiben am zentralen Standort.</span><span class="sxs-lookup"><span data-stu-id="3bf67-p107">Only user mailboxes, resource mailboxes (room and equipment mailboxes), and shared mailboxes support multi-geo features. Public Folder Mailboxes and Office 365 Groups remain in the central location.</span></span>
 
2. <span data-ttu-id="3bf67-p108">Sicherheit und Richtlinientreue (beispielsweise Überwachung und eDiscovery) in der Exchange-Verwaltungskonsole (EAC) verfügbaren Features sind nicht in Organisationen mit mehreren geografisch verfügbar. Stattdessen müssen Sie [Office 365-Sicherheit und Compliance Center](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) verwenden, um Features für Sicherheit und Einhaltung von Bestimmungen zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="3bf67-p108">Security and compliance features (for example, auditing and eDiscovery) that are available in the Exchange admin center (EAC) aren't available in multi-geo organizations. Instead, you need to use the [Office 365 Security & Compliance Center](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) to configure security and compliance features.</span></span>

3. <span data-ttu-id="3bf67-p109">Outlook für Mac-Benutzer kann einen vorübergehenden Verlust des Zugriffs auf ihre Ordner Onlinearchiv auftreten, während Sie ihr Postfach an einen neuen Speicherort Geo bewegen. Diese Bedingung tritt auf, wenn die primäre Benutzerordner und archivpostfächer befinden sich in unterschiedlichen Geo-Speicherorte, da das Verschieben von Postfächern Cross-Geo zu unterschiedlichen Zeiten abgeschlossen werden können.</span><span class="sxs-lookup"><span data-stu-id="3bf67-p109">Outlook for Mac users may experience a temporary loss of access to their Online Archive folder while you move their mailbox to a new geo location. This condition occurs when the user's the primary and archive mailboxes are in different geo locations, because cross-Geo mailbox moves may complete at different times.</span></span>

4. <span data-ttu-id="3bf67-p110">Benutzer können nicht *Postfachordner* für Geo Speicherorten in Outlook im Web (früher als Outlook Web App oder OWA bezeichnet) freigeben. Beispielsweise kann kein Benutzer in der Europäischen Union Outlook im Web verwenden, um einen freigegebenen Ordner in einem Postfach zu öffnen, die sich in den USA befindet. Outlook auf dem Web-Benutzer kann jedoch *anderer Postfächer an* in anderen Geos öffnen, indem Sie mit einem separaten Browserfenster wie beschrieben in [eine andere Person Postfach in einem separaten Browserfenster in Outlook Web App zu öffnen](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).</span><span class="sxs-lookup"><span data-stu-id="3bf67-p110">Users can't share *mailbox folders* across geo locations in Outlook on the web (formerly known as Outlook Web App or OWA). For example, a user in the European Union can't use Outlook on the web to open a shared folder in a mailbox that's located in the United States. However, Outlook on the Web users can open *other mailboxes* in different Geos by using a separate browser window as described in [Open another person’s mailbox in a separate browser window in Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).</span></span>

    <span data-ttu-id="3bf67-152">**Hinweis**: Cross-Geo Postfach Ordnerfreigabe in Outlook auf Windows unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="3bf67-152">**Note**: Cross-geo mailbox folder sharing is supported in Outlook on Windows.</span></span>

## <a name="administration"></a><span data-ttu-id="3bf67-153">Administration</span><span class="sxs-lookup"><span data-stu-id="3bf67-153">Administration</span></span> 
<span data-ttu-id="3bf67-p111">Remote-PowerShell ist erforderlich, anzeigen und mit mehreren geografisch Eigenschaften in der Office 365-Umgebung konfigurieren. Informationen zu verschiedenen PowerShell-Module zum Verwalten von Office 365 finden Sie unter [Verwalten von Office 365 und Exchange Online mit Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6)verwendet.</span><span class="sxs-lookup"><span data-stu-id="3bf67-p111">Remote PowerShell is required to view and configure multi geo properties in your Office 365 environment. For information on various PowerShell modules used to administer Office 365, see [Managing Office 365 and Exchange Online with Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6).</span></span>

- <span data-ttu-id="3bf67-p112">Sie benötigen die [Microsoft Azure Active Directory-PowerShell-Modul](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 oder später in v1.x an die **PreferredDataLocation** -Eigenschaft auf User-Objekte angezeigt werden. User-Objekte in AAD über AAD Connect synchronisiert können nicht ihre **PreferredDataLocation** Wert direkt über die PowerShell AAD geändert haben. Nur-Cloud-User-Objekte können über die PowerShell AAD geändert werden. Zum Verbinden mit Azure AD-PowerShell finden Sie unter [Connect to Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span><span class="sxs-lookup"><span data-stu-id="3bf67-p112">You need the [Microsoft Azure Active Directory PowerShell Module](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 or later in v1.x to see the **PreferredDataLocation** property on user objects. User objects synchronized via AAD Connect into AAD cannot have their **PreferredDataLocation** value directly modified via AAD PowerShell. Cloud-only user objects can be modified via AAD PowerShell. To connect to Azure AD PowerShell, see [Connect to Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span></span> 

- <span data-ttu-id="3bf67-160">Zum Verbinden mit Exchange Online PowerShell finden Sie unter [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span><span class="sxs-lookup"><span data-stu-id="3bf67-160">To connect to Exchange Online PowerShell, see [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span></span> 

### <a name="connect-directly-to-a-specific-geo-using-exchange-online-powershell"></a><span data-ttu-id="3bf67-161">Verbinden Sie mit einer bestimmten Geo von Exchange Online PowerShell direkt</span><span class="sxs-lookup"><span data-stu-id="3bf67-161">Connect directly to a specific Geo using Exchange Online PowerShell</span></span>
<span data-ttu-id="3bf67-p113">Exchange Online PowerShell wird in der Regel mit den Standardspeicherort Geo verbunden. Aber Sie können auch direkt mit nicht standardmäßigen Geo Speicherorte anschließen. Es wird empfohlen, aufgrund von Leistungssteigerungen direkt auf den Speicherort nicht standardmäßigen Geo verbinden, wenn Sie nur Benutzer an diesem Standort Geo verwalten.</span><span class="sxs-lookup"><span data-stu-id="3bf67-p113">Typically, Exchange Online PowerShell will connect to the default geo location. But, you can also connect directly to non-default geo locations. Because of performance improvements, we recommend connecting directly to the non-default geo location when you only manage users in that geo location.</span></span>

<span data-ttu-id="3bf67-p114">Zum Verbinden mit einer bestimmten Geo ist der Parameter *ConnectionUri* anders als die regulären Verbindung Anweisungen. Die restlichen Befehle und Werte sind identisch. Die Schritte sind:</span><span class="sxs-lookup"><span data-stu-id="3bf67-p114">To connect to a specific Geo, the *ConnectionUri* parameter is different than the regular connection instructions. The rest of the commands and values are the same. The steps are:</span></span>

1. <span data-ttu-id="3bf67-168">Öffnen Sie auf dem lokalen Computer Windows PowerShell, und führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="3bf67-168">On your local computer, open Windows PowerShell and run the following command:</span></span>
    
    ```
    $UserCredential = Get-Credential
    ```
   <span data-ttu-id="3bf67-169">Klicken Sie im Dialogfeld **Windows PowerShell anmelden** Geben Sie die geschäftliche Rufnummer oder Schule Konto und Kennwort ein, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="3bf67-169">In the **Windows PowerShell Credential Request** dialog box, type your work or school account and password, and then click **OK**.</span></span>
    
2. <span data-ttu-id="3bf67-p115">Ersetzen Sie `<emailaddress>` mit der e-Mail-Adresse von **jedem** Postfach im Zielspeicherort Geo und den folgenden Befehl ausführen. Die Berechtigungen für das Postfach und in Bezug auf Ihre Anmeldeinformationen in Schritt 1 sind keinen Faktor. die e-Mail-Adresse weist einfach Exchange Online, wo Sie eine Verbindung herstellen.</span><span class="sxs-lookup"><span data-stu-id="3bf67-p115">Replace `<emailaddress>` with the email address of **any** mailbox in the target geo location and run the following command. Your permissions on the mailbox and the relationship to your credentials in Step 1 are not a factor; the email address simply tells Exchange Online where to connect.</span></span>
  
   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   <span data-ttu-id="3bf67-172">Wenn olga@contoso.onmicrosoft.com die e-Mail-Adresse eines Postfachs in die Geo gültig, den Sie eine Verbindung herstellen möchten ist, führen Sie beispielsweise den folgenden Befehl ein:</span><span class="sxs-lookup"><span data-stu-id="3bf67-172">For example, if olga@contoso.onmicrosoft.com is the email address of a valid mailbox in the Geo you want to connect, run the following command:</span></span>

   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```
3. <span data-ttu-id="3bf67-173">Führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="3bf67-173">Run the following command:</span></span>
    
    ```
    Import-PSSession $Session
    ```

### <a name="azure-ad-connect-version-requirements"></a><span data-ttu-id="3bf67-174">Anforderungen an Softwareversionen von Azure Active Directory verbinden</span><span class="sxs-lookup"><span data-stu-id="3bf67-174">Azure AD Connect version requirements</span></span>
<span data-ttu-id="3bf67-p116">Verbinden von AAD Version 1.1.524.0 oder höher ist die einzige unterstützte Methode zum Festlegen der **PreferredDataLocation** -Eigenschaft auf User-Objekte, die synchronisiert werden aus dem lokalen Active Directory. User-Objekte in AAD über AAD Connect synchronisiert können nicht ihre **PreferredDataLocation** Wert direkt über die PowerShell AAD geändert haben. Nur-Cloud-User-Objekte können über die PowerShell AAD geändert werden. Ausführliche Anweisungen finden Sie unter [Azure Active Directory verbinden Sync: Konfigurieren des bevorzugten Datenspeicherort für Office 365-Ressourcen](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span><span class="sxs-lookup"><span data-stu-id="3bf67-p116">AAD Connect version 1.1.524.0 or later is the only supported method for setting the **PreferredDataLocation** property on user objects that are synchronized from on-premises Active Directory. User objects synchronized via AAD Connect into AAD cannot have their **PreferredDataLocation** value directly modified via AAD PowerShell. Cloud-only user objects can be modified via AAD PowerShell. For detailed instructions, see [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

### <a name="geo-codes"></a><span data-ttu-id="3bf67-179">Geo-Codes</span><span class="sxs-lookup"><span data-stu-id="3bf67-179">Geo Codes</span></span>
<span data-ttu-id="3bf67-p117">Drei Buchstaben Codes können Sie die geografisch in der **PreferredDataLocation** -Eigenschaft festlegen. Die folgende Tabelle enthält die Codes für die Geos verfügbar:</span><span class="sxs-lookup"><span data-stu-id="3bf67-p117">You use three-letter codes to specify the Geo in the **PreferredDataLocation** property. The following table lists the codes for the available Geos:</span></span>

|<span data-ttu-id="3bf67-182">Geo</span><span class="sxs-lookup"><span data-stu-id="3bf67-182">Geo</span></span> |<span data-ttu-id="3bf67-183">Code</span><span class="sxs-lookup"><span data-stu-id="3bf67-183">Code</span></span> |
|---------|---------|
|<span data-ttu-id="3bf67-184">Asien-Pazifik</span><span class="sxs-lookup"><span data-stu-id="3bf67-184">Asia/Pacific</span></span> |<span data-ttu-id="3bf67-185">APC</span><span class="sxs-lookup"><span data-stu-id="3bf67-185">APC</span></span> |
|<span data-ttu-id="3bf67-186">Australien</span><span class="sxs-lookup"><span data-stu-id="3bf67-186">Australia</span></span> |<span data-ttu-id="3bf67-187">AUS</span><span class="sxs-lookup"><span data-stu-id="3bf67-187">AUS</span></span> |
|<span data-ttu-id="3bf67-188">Kanada</span><span class="sxs-lookup"><span data-stu-id="3bf67-188">Canada</span></span> |<span data-ttu-id="3bf67-189">CAN</span><span class="sxs-lookup"><span data-stu-id="3bf67-189">CAN</span></span> |
|<span data-ttu-id="3bf67-190">Europäische Union</span><span class="sxs-lookup"><span data-stu-id="3bf67-190">European Union</span></span> |<span data-ttu-id="3bf67-191">EUR</span><span class="sxs-lookup"><span data-stu-id="3bf67-191">EUR</span></span> |
|<span data-ttu-id="3bf67-192">Frankreich</span><span class="sxs-lookup"><span data-stu-id="3bf67-192">France</span></span> |<span data-ttu-id="3bf67-193">FRA</span><span class="sxs-lookup"><span data-stu-id="3bf67-193">FRA</span></span>|
|<span data-ttu-id="3bf67-194">Indien</span><span class="sxs-lookup"><span data-stu-id="3bf67-194">India</span></span> |<span data-ttu-id="3bf67-195">IND</span><span class="sxs-lookup"><span data-stu-id="3bf67-195">IND</span></span> |
|<span data-ttu-id="3bf67-196">Japan</span><span class="sxs-lookup"><span data-stu-id="3bf67-196">Japan</span></span> |<span data-ttu-id="3bf67-197">JPN</span><span class="sxs-lookup"><span data-stu-id="3bf67-197">JPN</span></span> |
|<span data-ttu-id="3bf67-198">Korea</span><span class="sxs-lookup"><span data-stu-id="3bf67-198">Korea</span></span> |<span data-ttu-id="3bf67-199">KOR</span><span class="sxs-lookup"><span data-stu-id="3bf67-199">KOR</span></span> |
|<span data-ttu-id="3bf67-200">Vereinigtes Königreich</span><span class="sxs-lookup"><span data-stu-id="3bf67-200">United Kingdom</span></span> |<span data-ttu-id="3bf67-201">GBR</span><span class="sxs-lookup"><span data-stu-id="3bf67-201">GBR</span></span> |
|<span data-ttu-id="3bf67-202">Vereinigte Staaten</span><span class="sxs-lookup"><span data-stu-id="3bf67-202">United States</span></span> |<span data-ttu-id="3bf67-203">NAM</span><span class="sxs-lookup"><span data-stu-id="3bf67-203">NAM</span></span> |

<span data-ttu-id="3bf67-p118">**Hinweis**: die Eigenschaften **PreferredDataLocation** und **MailboxRegion** sind Zeichenfolgen mit keine Fehler überprüfen. Wenn Sie einen ungültigen Wert (beispielsweise NAN) eingeben wird das Postfach in der standardmäßigen Geo platziert werden.</span><span class="sxs-lookup"><span data-stu-id="3bf67-p118">**Note**: The **PreferredDataLocation** and **MailboxRegion** properties are strings with no error checking. If you enter an invalid value (for example, NAN) the mailbox will be placed in the default Geo.</span></span>

### <a name="view-the-available-geos-that-are-configured-in-your-exchange-online-organization"></a><span data-ttu-id="3bf67-206">Anzeigen der verfügbaren Geos, die in Ihrer Exchange Online-Organisation konfiguriert sind</span><span class="sxs-lookup"><span data-stu-id="3bf67-206">View the available Geos that are configured in your Exchange Online organization</span></span>
<span data-ttu-id="3bf67-207">Um die Liste der konfigurierten Geos in Ihrer Exchange Online-Organisation anzuzeigen, führen Sie den folgenden Befehl im Exchange Online PowerShell:</span><span class="sxs-lookup"><span data-stu-id="3bf67-207">To see the list of configured Geos in your Exchange Online organization, run the following command in Exchange Online PowerShell:</span></span>

```
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table
```

<span data-ttu-id="3bf67-208">Die Ausgabe des Befehls sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="3bf67-208">The output of the command looks like this:</span></span>

```
APC
AUS
CAN
EUR
FRA
GBR
JPN
KOR
NAM
```

### <a name="view-the-default-geo-for-your-exchange-online-organization"></a><span data-ttu-id="3bf67-209">Die Standardeinstellung Geo für Ihre Exchange Online-Organisation anzeigen</span><span class="sxs-lookup"><span data-stu-id="3bf67-209">View the default Geo for your Exchange Online organization</span></span>
<span data-ttu-id="3bf67-210">Um die standardmäßige Geo Ihrer Exchange Online-Organisation anzuzeigen, führen Sie den folgenden Befehl im Exchange Online PowerShell:</span><span class="sxs-lookup"><span data-stu-id="3bf67-210">To view the default geo of your Exchange Online organization, run the following command in Exchange Online PowerShell:</span></span>

```
Get-OrganizationConfig | Select DefaultMailboxRegion
```

<span data-ttu-id="3bf67-211">Die Ausgabe des Befehls sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="3bf67-211">The output of the command looks like this:</span></span>

```
DefaultMailboxRegion
--------------------
NAM
```


### <a name="find-the-geo-location-of-a-mailbox"></a><span data-ttu-id="3bf67-212">Suchen Sie den Speicherort Geo eines Postfachs</span><span class="sxs-lookup"><span data-stu-id="3bf67-212">Find the Geo location of a mailbox</span></span>
<span data-ttu-id="3bf67-213">Das Cmdlet **Get-Mailbox** in Exchange Online PowerShell zeigt die folgenden Multi-Geo bezogenen Eigenschaften für Postfächer:</span><span class="sxs-lookup"><span data-stu-id="3bf67-213">The **Get-Mailbox** cmdlet in Exchange Online PowerShell displays the following multi-geo related properties on mailboxes:</span></span>

- <span data-ttu-id="3bf67-p119">**Datenbank**: die ersten 3 Buchstaben des Datenbanknamens entsprechen Geo-Code, dem Sie darüber informiert, in dem das Postfach aktuell gespeichert ist. Für Online Archivpostfächer der **ArchiveDatabase** sollte-Eigenschaft verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="3bf67-p119">**Database**: The first 3 letters of the database name correspond to the Geo code, which tells you where the mailbox is currently located. For Online Archive Mailboxes the **ArchiveDatabase** property should be used.</span></span>

- <span data-ttu-id="3bf67-216">**MailboxRegion**: Gibt den Code der Geo-Speicherort, der durch den Administrator (aus **PreferredDataLocation** in Azure Active Directory synchronisiert) festgelegt wurde.</span><span class="sxs-lookup"><span data-stu-id="3bf67-216">**MailboxRegion**: Specifies the geo location code that was set by the admin (synchronized from **PreferredDataLocation** in Azure AD).</span></span>

- <span data-ttu-id="3bf67-217">**MailboxRegionLastUpdateTime**: Gibt an, wann MailboxRegion (automatisch oder manuell) zuletzt aktualisiert wurde.</span><span class="sxs-lookup"><span data-stu-id="3bf67-217">**MailboxRegionLastUpdateTime**: Indicates when MailboxRegion was last updated (either automatically or manually).</span></span>

<span data-ttu-id="3bf67-218">Um diese Eigenschaften für ein Postfach anzuzeigen, verwenden Sie die folgende Syntax:</span><span class="sxs-lookup"><span data-stu-id="3bf67-218">To see these properties for a mailbox, use the following syntax:</span></span>

```
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

<span data-ttu-id="3bf67-219">Um die Geo-Informationen für das Postfach chris@contoso.onmicrosoft.com angezeigt wird, führen Sie beispielsweise den folgenden Befehl:</span><span class="sxs-lookup"><span data-stu-id="3bf67-219">For example, to see the Geo information for the mailbox chris@contoso.onmicrosoft.com, run the following command:</span></span>

```
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

<span data-ttu-id="3bf67-220">Die Ausgabe des Befehls sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="3bf67-220">The output of the command looks like this:</span></span>

```
Database                    : EURPR03DG077-db007 
MailboxRegion               : EUR 
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM 
```

> <span data-ttu-id="3bf67-221">**Hinweis:** Wenn der Code Geo Speicherort in den Namen der Datenbank **MailboxRegion** Wert entspricht, wird das Postfach werden automatisch in eine Warteschlange Umsetzung aufgenommen werden und in den angegebenen durch den Wert **MailboxRegion** Geo Speicherort verschoben (Exchange Online sucht nach einer Konflikt zwischen diese Eigenschaftswerte).</span><span class="sxs-lookup"><span data-stu-id="3bf67-221">**Note:** If the geo location code in the database name doesn't match **MailboxRegion** value, the mailbox will be automatically be put into a relocation queue and moved to the geo location specified by the **MailboxRegion** value (Exchange Online looks for a mismatch between these property values).</span></span>

### <a name="move-an-existing-cloud-only-mailbox-to-a-specific-geo"></a><span data-ttu-id="3bf67-222">Verschieben eines vorhandenen nur-Cloud-Postfachs in einer bestimmten Geo</span><span class="sxs-lookup"><span data-stu-id="3bf67-222">Move an existing cloud-only mailbox to a specific Geo</span></span>
<span data-ttu-id="3bf67-p120">Ein nur-Cloud-Benutzer ist ein Benutzer nicht Syncrhonized über AAD Connect-Mandanten. Diesen Benutzer wurde direkt in Azure Active Directory erstellt. Verwenden Sie die Cmdlets **Get-MsolUser** und **Set-MsolUser** in Azure AD-Moduls für Windows PowerShell anzeigen oder Angeben der Geo, eine nur-Cloud-Postfach des Benutzers gespeichert wird.</span><span class="sxs-lookup"><span data-stu-id="3bf67-p120">A cloud-only user is a user not syncrhonized to the tenant via AAD Connect. This user was created directly in Azure AD. Use the **Get-MsolUser** and **Set-MsolUser** cmdlets in the Azure AD Module for Windows PowerShell to view or specify the Geo where a cloud-only user's mailbox will be stored.</span></span>

<span data-ttu-id="3bf67-226">Um den Wert **PreferredDataLocation** für einen Benutzer anzuzeigen, verwenden Sie diese Syntax in Azure AD-PowerShell:</span><span class="sxs-lookup"><span data-stu-id="3bf67-226">To view the **PreferredDataLocation** value for a user, use this syntax in Azure AD PowerShell:</span></span>

```
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

<span data-ttu-id="3bf67-227">Um den **PreferredDataLocation** -Wert für den Benutzer michelle@contoso.onmicrosoft.com angezeigt wird, führen Sie beispielsweise den folgenden Befehl:</span><span class="sxs-lookup"><span data-stu-id="3bf67-227">For example, to see the **PreferredDataLocation** value for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

```
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

<span data-ttu-id="3bf67-228">Die Ausgabe des Befehls sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="3bf67-228">The output of the command looks like this:</span></span>

```
UserPrincipalName     : michelle@contoso.onmicrosoft.com
PreferredDataLocation : EUR
```

<span data-ttu-id="3bf67-229">Verwenden Sie die folgende Syntax zum Ändern des **PreferredDataLocation** -Werts für ein nur-Cloud-Benutzerobjekt in Azure AD-PowerShell:</span><span class="sxs-lookup"><span data-stu-id="3bf67-229">To modify the **PreferredDataLocation** value for a cloud-only user object, use the following syntax in Azure AD PowerShell:</span></span>

``` 
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoCode>
```

<span data-ttu-id="3bf67-230">Um die **PreferredDataLocation** -Wert der Europäischen Union (EUR) Geo für den Benutzer michelle@contoso.onmicrosoft.com festzulegen, führen Sie beispielsweise den folgenden Befehl:</span><span class="sxs-lookup"><span data-stu-id="3bf67-230">For example, to set the **PreferredDataLocation** value to the European Union (EUR) geo for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

``` 
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

<span data-ttu-id="3bf67-231">**Hinweise**:</span><span class="sxs-lookup"><span data-stu-id="3bf67-231">**Notes**:</span></span>

- <span data-ttu-id="3bf67-p121">Wie weiter oben erwähnt können nicht zuvor nachfolgend für synchronisierte User-Objekte aus dem lokalen Active Directory verwendet werden. Sie müssen den **PreferredDataLocation** -Wert mit AAD verbinden zu ändern. Weitere Informationen finden Sie unter [Azure Active Directory verbinden Sync: Konfigurieren des bevorzugten Datenspeicherort für Office 365-Ressourcen](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span><span class="sxs-lookup"><span data-stu-id="3bf67-p121">As mentioned previously you cannot use this procedure for synchronized user objects from on-premises Active Directory. You need to change the **PreferredDataLocation** value using AAD Connect. For more information, see [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span> 

- <span data-ttu-id="3bf67-235">Wie lange dauert es, um eine Mailboxfrom zu verschieben, dessen aktuelle Geo am neuen Speicherort für die gewünschte Geo verschiedenen Faktoren abhängig:</span><span class="sxs-lookup"><span data-stu-id="3bf67-235">How long it takes to relocate a mailboxfrom its current geo to the new desired geo location depends on several factors:</span></span>
 
  - <span data-ttu-id="3bf67-236">Die Größe und Typ des Postfachs.</span><span class="sxs-lookup"><span data-stu-id="3bf67-236">The size and type of mailbox.</span></span>
 
  - <span data-ttu-id="3bf67-237">Die Anzahl der Postfächer, die verschoben werden.</span><span class="sxs-lookup"><span data-stu-id="3bf67-237">The number of mailboxes being moved.</span></span>
 
  - <span data-ttu-id="3bf67-238">Die Verfügbarkeit von Ressourcen verschieben.</span><span class="sxs-lookup"><span data-stu-id="3bf67-238">The availability of move resources.</span></span>

#### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a><span data-ttu-id="3bf67-239">Move Postfächer, die auf die Aufbewahrung für eventuelle Rechtsstreitigkeiten sind deaktiviert</span><span class="sxs-lookup"><span data-stu-id="3bf67-239">Move disabled mailboxes that are on Litigation Hold</span></span>
<span data-ttu-id="3bf67-p122">Postfächer auf Aufbewahrung für eventuelle Rechtsstreitigkeiten, die für eDiscovery beibehalten werden, die Zwecke verschoben werden können, indem Sie ihre **PreferredDataLocation** Wert im deaktivierten Zustand deaktiviert. Verschieben eines deaktiviert Postfachs beweissicherungsverfahren:</span><span class="sxs-lookup"><span data-stu-id="3bf67-p122">Disabled mailboxes on Litigation Hold that are preserved for eDiscovery purposes cannot be moved by changing their **PreferredDataLocation** value in their disabled state. To move a disabled mailbox on litigation hold:</span></span>

1. <span data-ttu-id="3bf67-242">Das Postfach vorübergehend eine Lizenz zuweisen.</span><span class="sxs-lookup"><span data-stu-id="3bf67-242">Temporarily assign a license to the mailbox.</span></span>

2. <span data-ttu-id="3bf67-243">Ändern der **PreferredDataLocation**.</span><span class="sxs-lookup"><span data-stu-id="3bf67-243">Change the **PreferredDataLocation**.</span></span>

3. <span data-ttu-id="3bf67-244">Entfernen Sie die Lizenz aus dem Postfach, nachdem er auf den ausgewählten Geo Speicherort verschoben wurde, um wieder in den aktiven Zustand zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="3bf67-244">Remove the license from the mailbox after it has been moved to the selected geo location to put it back into the disabled state.</span></span>

### <a name="create-new-cloud-mailboxes-in-a-specific-geo"></a><span data-ttu-id="3bf67-245">Erstellen Sie neue Cloud-Postfächer in einer bestimmten Geo</span><span class="sxs-lookup"><span data-stu-id="3bf67-245">Create new cloud mailboxes in a specific Geo</span></span> 
<span data-ttu-id="3bf67-246">Zum Erstellen eines neuen Postfachs in einem bestimmten Geo-Speicherort müssen Sie führen Sie einen der folgenden Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="3bf67-246">To create a new mailbox in a specific geo location, you need to do either of these steps:</span></span>

- <span data-ttu-id="3bf67-p123">Konfigurieren Sie den Wert **PreferredDataLocation** , wie beschrieben in den Abschnitt der vorherigen *vor* , wenn, die das Postfach im Exchange Online erstellt wird. Konfigurieren Sie beispielsweise den Wert **PreferredDataLocation** für einen Benutzer, bevor Sie eine Lizenz zuweisen.</span><span class="sxs-lookup"><span data-stu-id="3bf67-p123">Configure the **PreferredDataLocation** value as described in the previous section *before* the mailbox is created in Exchange Online. For example, configure the **PreferredDataLocation** value on a user before assigning a license.</span></span> 

- <span data-ttu-id="3bf67-249">Weisen Sie eine Lizenz zur selben Zeit, den, die Sie den Wert **PreferredDataLocation** festlegen.</span><span class="sxs-lookup"><span data-stu-id="3bf67-249">Assign a license at the same time you set the **PreferredDataLocation** value.</span></span>

<span data-ttu-id="3bf67-250">Verwenden Sie die folgende Syntax, um einen neuen Cloud-only lizenzierten Benutzer (nicht AAD verbinden synchronisiert) in einer bestimmten Geo erstellen, in Azure AD-PowerShell:</span><span class="sxs-lookup"><span data-stu-id="3bf67-250">To create a new cloud-only licensed user (not AAD Connect synchronized) in a specific Geo, use the following syntax in Azure AD PowerShell:</span></span>

```
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoCode> 
```
<span data-ttu-id="3bf67-251">In diesem Beispiel erstellen Sie ein neues Benutzerkonto für Elizabeth Brunner mit den folgenden Werten:</span><span class="sxs-lookup"><span data-stu-id="3bf67-251">This example create a new user account for Elizabeth Brunner with the following values:</span></span>

- <span data-ttu-id="3bf67-252">Benutzerprinzipalname: ebrunner@contoso.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="3bf67-252">User principal name: ebrunner@contoso.onmicrosoft.com</span></span>

- <span data-ttu-id="3bf67-253">Vorname: Elizabeth</span><span class="sxs-lookup"><span data-stu-id="3bf67-253">First name: Elizabeth</span></span>

- <span data-ttu-id="3bf67-254">Nachname: Brunner</span><span class="sxs-lookup"><span data-stu-id="3bf67-254">Last name: Brunner</span></span>

- <span data-ttu-id="3bf67-255">Anzeigename Elizabeth Brunner</span><span class="sxs-lookup"><span data-stu-id="3bf67-255">Display name Elizabeth Brunner</span></span>

- <span data-ttu-id="3bf67-256">Kennwort: zufällig generiert und in die Ergebnisse des Befehls (da wir den Parameter *Password* nicht verwenden)</span><span class="sxs-lookup"><span data-stu-id="3bf67-256">Password: randomly-generated and shown in the results of the command (because we're not using the *Password* parameter)</span></span>

- <span data-ttu-id="3bf67-257">Lizenz: Contoso:ENTERPRISEPREMIUM (E5)</span><span class="sxs-lookup"><span data-stu-id="3bf67-257">License: contoso:ENTERPRISEPREMIUM (E5)</span></span>

- <span data-ttu-id="3bf67-258">Standort: Australien (AUS)</span><span class="sxs-lookup"><span data-stu-id="3bf67-258">Location: Australia (AUS)</span></span>

```
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

<span data-ttu-id="3bf67-259">Weitere Informationen zum Erstellen neuer Benutzerkonten und Suchen von LicenseAssignment Werte in Azure AD-PowerShell finden Sie unter [Erstellen von Benutzerkonten mit Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) und [Lizenzen anzeigen und-Dienste mit Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).</span><span class="sxs-lookup"><span data-stu-id="3bf67-259">For more information about creating new user accounts and finding LicenseAssignment values in Azure AD PowerShell, see [Create user accounts with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) and [View licenses and services with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).</span></span>

> <span data-ttu-id="3bf67-p124">**Hinweis:** Wenn Sie zum Aktivieren eines Postfachs und benötigen das Postfach direkt in die Geo erstellt werden, die in **PreferredDataLocation**angegeben ist Exchange Online PowerShell verwenden, müssen Sie ein Exchange Online-Cmdlet wie **Enable-Mailbox** oder \*\*New-Mailbox verwenden \*\*direkt für die Cloud-Dienst. Wenn Sie das Cmdlet **Enable-RemoteMailbox** lokale Exchange verwenden, wird das Postfach in der standardmäßigen Geo erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="3bf67-p124">**Note:** If you are using Exchange Online PowerShell to enable a mailbox and need the mailbox to be created directly in the Geo that's specified in **PreferredDataLocation**, you need to use an Exchange Online cmdlet such as **Enable-Mailbox** or **New-Mailbox** directly against the cloud service. If you use the **Enable-RemoteMailbox** on-premises Exchange cmdlet, the mailbox will be created in the default Geo.</span></span>

### <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo"></a><span data-ttu-id="3bf67-262">Integrierte einer vorhandenen lokalen Postfächer in einer bestimmten Geo</span><span class="sxs-lookup"><span data-stu-id="3bf67-262">Onboard existing on-premises mailboxes in a specific Geo</span></span>
<span data-ttu-id="3bf67-263">Die standard-Onboarding-Tools und Prozesse können Sie ein Postfach aus einer lokalen Exchange-Organisation zu Exchange Online, einschließlich der [migrationsdashboard in der Exchange-Verwaltungskonsole](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331)und das Cmdlet [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) im Exchange Online migrieren PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3bf67-263">You can use the standard onboarding tools and processes to migrate a mailbox from an on-premises Exchange organization to Exchange Online, including the [Migration dashboard in the EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331), and the [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) cmdlet in Exchange Online PowerShell.</span></span>

<span data-ttu-id="3bf67-p125">Der erste Schritt besteht, stellen Sie sicher, dass ein User-Objekt vorhanden ist, für jedes Postfach Onboarded, und stellen Sie sicher, dass der richtige Wert **PreferredDataLocation** in Azure Active Directory konfiguriert ist. Onboarding-Tools werden den Wert **PreferredDataLocation** berücksichtigt und migrieren Sie die Postfächer werden direkt an die angegebenen Geo.</span><span class="sxs-lookup"><span data-stu-id="3bf67-p125">The first step is to verify a user object exists for each mailbox to be onboarded, and verify the correct **PreferredDataLocation** value is configured in Azure AD. The onboarding tools will respect the **PreferredDataLocation** value and will migrate the mailboxes directly to the specified Geo.</span></span>

<span data-ttu-id="3bf67-266">Alternativ können Sie auf integrierte Postfächer direkt in einem bestimmten Geo Speicherort mithilfe des Cmdlets [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) in Exchange Online PowerShell die folgenden Schritte aus.</span><span class="sxs-lookup"><span data-stu-id="3bf67-266">Or, you can use the following steps to onboard mailboxes directly in a specific geo location using the [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) cmdlet in Exchange Online PowerShell.</span></span>

1. <span data-ttu-id="3bf67-p126">Stellen Sie sicher, dass das Benutzerobjekt vorhanden ist, für jedes Postfach Onboarded und **PreferredDataLocation** in Azure Active Directory auf den gewünschten Wert festgelegt ist. Der Wert der **PreferredDataLocation** werden dem **MailboxRegion** -Attribut des entsprechenden e-Mail-Benutzerobjekts im Exchange Online synchronisiert.</span><span class="sxs-lookup"><span data-stu-id="3bf67-p126">Verify the user object exists for each mailbox to be onboarded and that **PreferredDataLocation** is set to the desired value in Azure AD. The value of **PreferredDataLocation** will be synchronized to the **MailboxRegion** attribute of the corresponding mail user object in Exchange Online.</span></span>

2. <span data-ttu-id="3bf67-269">Verbinden Sie direkt mit der bestimmte Satelliten Geo mithilfe der Connection-Anweisungen aus weiter oben in diesem Thema.</span><span class="sxs-lookup"><span data-stu-id="3bf67-269">Connect directly to the specific satellite Geo using the connection instructions from earlier in this topic.</span></span>

3. <span data-ttu-id="3bf67-270">In Exchange Online PowerShell speichern Sie die lokalen Administrator-Anmeldeinformationen, die zum Ausführen einer Migrations von Postfächern in einer Variablen, mithilfe des folgenden Befehls verwendet wird:</span><span class="sxs-lookup"><span data-stu-id="3bf67-270">In Exchange Online PowerShell, store the on-premises administrator credentials that's used to perform a mailbox migration in a variable by running the following command:</span></span>

    ```
    $RC = Get-Credential
    ```

4. <span data-ttu-id="3bf67-271">Erstellen Sie in Exchange Online PowerShell eine neue **New-MoveRequest** ähnlich dem folgenden Beispiel:</span><span class="sxs-lookup"><span data-stu-id="3bf67-271">In Exchange Online PowerShell, create a new **New-MoveRequest** similar to the following example:</span></span> 

    ```
    New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
    ```

5. <span data-ttu-id="3bf67-272">Wiederholen Sie Schritt #4 für jedes Postfach, die Sie benötigen zum Migrieren von lokalem Exchange zu den Satelliten Speicherort, den Sie derzeit verbunden sind.</span><span class="sxs-lookup"><span data-stu-id="3bf67-272">Repeat step #4 for every mailbox you need to migrate from on-premises Exchange to the satellite location you are currently connected to.</span></span>

6. <span data-ttu-id="3bf67-273">Wenn Sie zusätzliche Postfächer in einen anderen Satelliten Speicherort migrieren möchten, wiederholen Sie die Schritte 2 bis 4 für jeden Satellitenstandort bestimmte.</span><span class="sxs-lookup"><span data-stu-id="3bf67-273">If you need to migrate additional mailboxes to a different satellite location, repeat steps 2 through 4 for each specific satellite location.</span></span>

### <a name="multi-geo-reporting"></a><span data-ttu-id="3bf67-274">Multi-Geo Reporting</span><span class="sxs-lookup"><span data-stu-id="3bf67-274">Multi-Geo Reporting</span></span>
<span data-ttu-id="3bf67-p127">**Multi-Geo Usage Reports** in Office 365 Administrationscenter zeigt die Anzahl der Benutzer, hängt vom Speicherort Geo. Der Bericht zeigt die Verteilung der Benutzer für den aktuellen Monat und bietet Verlaufsdaten für die letzten 6 Monate.</span><span class="sxs-lookup"><span data-stu-id="3bf67-p127">**Multi-Geo Usage Reports** in the Office 365 admin center displays the user count by geo location. The report displays user distribution for the current month and provides historical data for the past 6 months.</span></span>
