---
title: Externe DNS-Einträge für Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/21/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: c0531a6f-9e25-4f2d-ad0e-a70bfef09ac0
description: 'Zusammenfassung: Referenzliste von DNS-Einträgen zur Verwendung bei der Planung einer komplexen Office 365-Bereitstellung.'
ms.openlocfilehash: d0804cec4ce2c15345a9c4ddc83525d1961f8db4
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "44996539"
---
# <a name="external-domain-name-system-records-for-office-365"></a>Externe DNS-Einträge für Office 365

|||
|:-----|:-----|
|![Domäne](media/e05b1c78-1df0-4200-ba40-6e26b7ead68f.png)|**Want to see a customized list of DNS records for your Office 365 organization?** You can [find the info you need to create Office 365 DNS records](https://support.office.microsoft.com/article/Gather-the-information-you-need-to-create-Office-365-DNS-records-77f90d4a-dc7f-4f09-8972-c1b03ea85a67) for your domain in Office 365.  <br/> **Need step-by-step help to add these records at your domain's DNS host, such as GoDaddy or eNom?** [Find links to step-by-step instructions for many popular DNS hosts](https://go.microsoft.com/fwlink/?LinkId=286745). <br/>  **Sticking around to use the reference list for your own custom deployment?** The below list should be used as a reference for your custom Office 365 deployment. You will need to select which records apply to your organization and fill in the appropriate values. <br/> **Zurück zu** [Netzwerkplanung und Leistungsoptimierung für Office 365](https://aka.ms/tune).  <br/> |

Often the SPF and MX records are the hardest to figure out. We've updated our SPF records guidance at the end of this article. The important thing to remember is that _you can only have a single SPF record for your domain_. You can have multiple MX records; however, that can cause problems for mail delivery. Having a single MX record that directs email to one mail system removes many potential problems.
  
The sections below are organized by service in Office 365. To see a customized list of the Office 365 DNS records for your domain, sign in to Office 365 and [Gather the information you need to create Office 365 DNS records](https://support.office.com/article/77f90d4a-dc7f-4f09-8972-c1b03ea85a67).
  
## <a name="external-dns-records-required-for-office-365-core-services"></a>Für Office 365 erforderliche externe DNS-Einträge (Hauptdienste):
<a name="BKMK_ReqdCore"> </a>

Every Office 365 customer needs to add two records to their external DNS. The first CNAME record ensures that Office 365 can direct workstations to authenticate with the appropriate identity platform. The second required record is to prove you own your domain name.
  
||||
|:-----|:-----|:-----|
|**DNS-Eintrag** <br/> |**Zweck** <br/> |**Zu verwendender Wert** <br/> |
|**CNAME** <br/> **(Suite)** <br/> |Used by Office 365 to direct authentication to the correct identity platform. [More information](https://go.microsoft.com/fwlink/p/?LinkId=322005) <br/> **Hinweis:** Dieser CNAME gilt nur für Office 365, betrieben von 21Vianet.   |**Alias:** msoID  <br/> **Ziel:** clientconfig.partner.microsoftonline-p.net.cn  <br/> |
|**TXT** <br/> **(Domänenüberprüfung)** <br/> |Used by Office 365 to verify only that you own your domain. It doesn't affect anything else.  <br/> |**Host:** @ (oder, bei einigen DNS-Hostinganbietern, Ihr Domänenname)  <br/> **TXT Value (TXT-Wert):** _Eine von_ Office 365 bereitgestellte Textzeichenfolge  <br/> Der Office 365-Assistent zur **Domäneneinrichtung** stellt die Werte zur Verfügung, die Sie zum Erstellen dieses Eintrags verwenden.  <br/> |


## <a name="external-dns-records-required-for-email-in-office-365-exchange-online"></a>Für E-Mail in Office 365 (Exchange Online) erforderliche externe DNS-Einträge
<a name="BKMK_ReqdCore"> </a>

Email in Office 365 requires several different records. The three primary records that all customers should use are the Autodiscover, MX, and SPF records.
  
- Der **AutoErmittlungseintrag** ermöglicht es Clientcomputern, Exchange automatisch zu finden und den Client ordnungsgemäß zu konfigurieren.

- **The MX record** tells other mail systems where to send email for your domain. **Note:** When you change your email to Office 365, by updating your domain's MX record, ALL email sent to that domain will start coming to Office 365.  
Möchten Sie nur einige wenige E-Mail-Adressen auf Office 365 umstellen? Sie können [Office 365 mit ein paar E-Mail-Adressen in der eigenen benutzerdefinierten Domäne einführen](https://support.office.com/article/39cee536-6a03-40cf-b9c1-f301bb6001d7).

- **Anhand des TXT-Eintrags für SPF** überprüfen E-Mail-Systeme der Empfänger, ob es sich bei dem Server, der Ihre E-Mail sendet, um einen von Ihnen genehmigten Server handelt. Dies hilft, Probleme wie E-Mail-Spoofing und -Phishing zu verhindern. Lesen Sie [Für SPF erforderliche externe DNS-Einträge](external-domain-name-system-records.md#BKMK_SPFrecords) im vorliegenden Artikel, um besser zu verstehen, was Sie zu ihrem Datensatz hinzufügen sollten.

E-Mail-Benutzer, die Exchange-Partnerverbund verwenden, benötigen außerdem einen zusätzlichen CNAME- und TXT-Eintrag, der am unteren Rand der Tabelle aufgeführt ist.
  
||||
|:-----|:-----|:-----|
|**DNS-Eintrag** <br/> |**Zweck** <br/> |**Zu verwendender Wert** <br/> |
|**CNAME** <br/> **(Exchange Online)** <br/> |Helps Outlook clients to easily connect to the Exchange Online service by using the Autodiscover service. Autodiscover automatically finds the correct Exchange Server host and configures Outlook for users.  <br/> |**Alias:** Autodiscover  <br/> **Target (Ziel):** autodiscover.outlook.com  <br/> |
|**MX** <br/> **(Exchange Online)** <br/> |Sendet eingehende Mails für Ihre Domäne an den Exchange Online-Dienst in Office 365.  <br/> [!NOTE] Sobald E-Mails an Exchange Online übertragen werden, sollten Sie die MX-Einträge entfernen, die auf Ihr altes System verweisen.   |**Domain (Domäne):** Beispielsweise contoso.com  <br/> **Ziel-e-Mail-Server:** \<MX token\> . mail.protection.outlook.com  <br/> **Preference/Priority (Präferenz/Priorität):** Niedriger als alle anderen MX-Einträge (dies stellt sicher, dass E-Mail an Exchange Online übermittelt wird) – z. B. 1 oder "low" (niedrig)  <br/>  Führen Sie die \<MX token\> folgenden Schritte aus, um das zu finden:  <br/>  Melden Sie sich bei Office 365 an, und wechseln Sie zu "Office 365-Administrator" \> "Domänen".  <br/>  Wählen Sie in der Spalte "Aktion" für Ihre Domäne "Probleme beheben" aus.  <br/>  Wählen Sie im Abschnitt für MX-Einträge die Option "Was korrigiere ich?" aus.  <br/>  Folgen Sie den Anweisungen auf dieser Seite, um den MX-Eintrag zu aktualisieren.  <br/> [Was ist MX-Priorität?](https://go.microsoft.com/fwlink/p/?LinkId=396471) <br/> |
|**SPF (TXT)** <br/> **(Exchange Online)**  <br/> |Helps to prevent other people from using your domain to send spam or other malicious email. Sender policy framework (SPF) records work by identifying the servers that are authorized to send email from your domain.  <br/> |[Für SPF erforderliche externe DNS-Einträge](external-domain-name-system-records.md#BKMK_SPFrecords) <br/> |
|**TXT** <br/> **(Exchange-Partnerverbund)** <br/> |Für Exchange-Partnerverbund für Hybridbereitstellungen verwendet.  <br/> |**TXT-Eintrag 1:** Beispiel: contoso.com und zugeordneter, benutzergenerierter Hash-Text zum Nachweis für die Domäne (Beispiel: Y96nu89138789315669824)  <br/> **TXT-Eintrag 2:** Beispiel: exchangedelegation.contoso.com und zugeordneter, kundengenerierter Hash-Text zum Nachweis für die Domäne (Beispiel: Y3259071352452626169)  <br/> |
|**CNAME** <br/> **(Exchange-Partnerverbund)** <br/> |Helps Outlook clients to easily connect to the Exchange Online service by using the Autodiscover service when your company is using Exchange federation. Autodiscover automatically finds the correct Exchange Server host and configures Outlook for your users.  <br/> |**Alias:** Beispiel: Autodiscover.service.contoso.com  <br/> **Target (Ziel):** autodiscover.outlook.com  <br/> |


## <a name="external-dns-records-required-for-skype-for-business-online"></a>Für Skype for Business Online erforderliche externe DNS-Einträge
<a name="BKMK_ReqdCore"> </a>

Wenn Sie [Office 365-URLs und IP-Adressbereiche](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO) verwenden, müssen bestimmte Schritte ausgeführt werden, um sicherzustellen, dass Ihr Netzwerk ordnungsgemäß konfiguriert ist.

> [!NOTE]
> Diese DNS-Einträge gelten auch für Teams – insbesondere in einem Hybridszenario mit Teams und Skype for Business Online, bei dem bestimmte Verbundprobleme auftreten könnten.
  
||||
|:-----|:-----|:-----|
|**DNS-Eintrag** <br/> |**Zweck** <br/> |**Zu verwendender Wert** <br/> |
|**SRV** <br/> **(Skype for Business Online)** <br/> |Allows your Office 365 domain to share instant messaging (IM) features with external clients by enabling SIP federation. Read more about [Office 365 URLs and IP address ranges](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO).  <br/> |**Service (Dienst):** sipfederationtls  <br/> **Protocol (Protokoll):** TCP  <br/> **Priority (Priorität):** 100  <br/> **Weight (Gewichtung):** 1  <br/> **Port:** 5061  <br/> **Target (Ziel):** sipfed.online.lync.com  <br/> **Hinweis:** Wenn die Firewall oder der Proxy-Server SRV-Lookups auf einem externen DNS blockiert, sollten Sie diesen Eintrag außerdem dem internen DNS-Eintrag hinzufügen.   |
|**SRV** <br/> **(Skype for Business Online)** <br/> |Von Skype for Business zur Koordinierung des Informationsflusses zwischen Lync-Clients verwendet.  <br/> |**Service (Dienst):** sip  <br/> **Protocol (Protokoll):** TLS  <br/> **Priority (Priorität):** 100  <br/> **Weight (Gewichtung):** 1  <br/> **Port:** 443  <br/> **Target (Ziel):** sipdir.online.lync.com  <br/> |
|**CNAME** <br/> **(Skype for Business Online)** <br/> |Vom Lync-Client zur Unterstützung der Suche nach dem Skype for Business Online-Dienst und der Anmeldung verwendet.  <br/> |**Alias:** sip  <br/> **Target (Ziel):** sipdir.online.lync.com  <br/> Weitere Informationen finden Sie unter [Office 365-URLs und -IP-Adressbereiche](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO).  <br/> |
|**CNAME** <br/> **(Skype for Business Online)** <br/> |Vom mobilen Lync-Client zur Unterstützung der Suche nach dem Skype for Business Online-Dienst und der Anmeldung verwendet.  <br/> |**Alias:** lyncdiscover  <br/> **Target (Ziel):** webdir.online.lync.com  <br/> |

## <a name="external-dns-records-required-for-office-365-single-sign-on"></a>Für das einmalige Anmelden bei Office 365 erforderliche externe DNS-Einträge
<a name="BKMK_ReqdCore"> </a>

||||
|:-----|:-----|:-----|
|**DNS-Eintrag** <br/> |**Zweck** <br/> |**Zu verwendender Wert** <br/> |
|**Host (A)** <br/> |Used for single sign-on (SSO). It provides the endpoint for your off-premises users (and on-premises users, if you like) to connect to your Active Directory Federation Services (AD FS) federation server proxies or load-balanced virtual IP (VIP).  <br/> |**Target (Zielwert):** Beispielsweise sts.contoso.com  <br/> |

## <a name="external-dns-records-required-for-spf"></a>Für SPF erforderliche externe DNS-Einträge
<a name="BKMK_SPFrecords"> </a>

> [!IMPORTANT]
> SPF is designed to help prevent spoofing, but there are spoofing techniques that SPF cannot protect against. In order to protect against these, once you have set up SPF, you should also configure DKIM and DMARC for Office 365. To get started, see [Use DKIM to validate outbound email sent from your domain in Office 365](https://technet.microsoft.com/library/mt695945%28v=exchg.150%29.aspx). Next, see [Use DMARC to validate email in Office 365](https://technet.microsoft.com/library/mt734386%28v=exchg.150%29.aspx).
  
SPF records are TXT records that help to prevent other people from using your domain to send spam or other malicious email. Sender policy framework (SPF) records work by identifying the servers that are authorized to send email from your domain.
  
You can only have one SPF record (that is, a TXT record that defines SPF) for your domain. That single record can have a few different inclusions but the total DNS lookups that result can't be more than 10 (this helps prevent denial of service attacks). See the table and other examples below to help you create or update the right SPF record values for your environment.
  
### <a name="structure-of-an-spf-record"></a>Struktur eines SPF-Eintrags

All SPF records contain three parts: the declaration that it is an SPF record, the domains, and IP addresses that should be sending email, and an enforcement rule. You need all three in a valid SPF record. Here's an example of a common SPF record for Office 365 when you use only Exchange Online email:
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com -all
```

Ein E-Mail-System, das eine E-Mail über Ihre Domäne empfängt, prüft den SPF-Eintrag, und wenn es sich bei dem E-Mail-Server, der die Nachricht gesendet hat, um einen Office 365-Server handelte, wird die Nachricht akzeptiert. Wenn es sich bei dem Server, der die Nachricht gesendet hat, beispielsweise um Ihr altes Mailsystem oder ein bösartiges System im Internet handelt, kann die SPF-Prüfung fehlschlagen, und die Nachricht wird nicht zugestellt. Überprüfungen wie diese helfen, Spoofing- und Phishingnachrichten zu verhindern.
  
### <a name="choose-the-spf-record-structure-you-need"></a>Auswählen der benötigten Struktur des SPF-Eintrags

In Szenarien, in denen Sie nicht nur Exchange Online-E-Mail für Office 365 verwenden (beispielsweise, wenn Sie außerdem mit E-Mails arbeiten, die von SharePoint Online stammen), verwenden Sie die folgende Tabelle, um zu bestimmen, was in den Wert des Eintrags aufgenommen werden soll.
  
> [!NOTE]
> If you have a complicated scenario that includes, for example, edge email servers for managing email traffic across your firewall, you'll have a more detailed SPF record to set up. Learn how: [Set up SPF records in Office 365 to help prevent spoofing](https://go.microsoft.com/fwlink/?LinkId=787656). You can also learn much more about how SPF works with Office 365 by reading [How Office 365 uses Sender Policy Framework (SPF) to help prevent spoofing](https://go.microsoft.com/fwlink/?LinkId=787065).
  
|||||
|:-----|:-----|:-----|:-----|
||Wenn Sie Folgendes verwenden...  <br/> |Zweck  <br/> |Diese Einschlüsse hinzufügen  <br/> |
|1   <br/> |Alle E-Mail-Systeme (erforderlich)  <br/> |Alle SPF-Einträge beginnen mit dem folgenden Wert  <br/> |v=spf1  <br/> |
|2   <br/> |Exchange Online (verbreitet)  <br/> |Bei ausschließlicher Nutzung von Exchange Online verwenden  <br/> |include:spf.protection.outlook.com  <br/> |
|3   <br/> |Drittanbieter-E-Mail-Systeme (weniger verbreitet)  <br/> ||enthalten:\<email system like mail.contoso.com\>  <br/> |
|4   <br/> |Lokales E-Mail-System (weniger verbreitet)  <br/> |Verwenden Sie dies, wenn Sie Exchange Online Protection oder Exchange Online zusammen mit einem anderen Mailsystem verwenden.  <br/> |ip4:\<0.0.0.0\>  <br/> ip6:\< : : \>  <br/> enthalten:\<mail.contoso.com\>  <br/> Die Werte in spitzen Klammern (\<\>) sollten andere E-Mail-Systeme sein, die E-Mails für Ihre Domäne senden.  <br/> |
|5   <br/> |Alle E-Mail-Systeme (erforderlich)  <br/> ||-all  <br/> |

### <a name="example-adding-to-an-existing-spf-record"></a>Beispiel: Hinzufügen zu einem vorhandenen SPF-Eintrag
<a name="bkmk_addtospf"> </a>

If you already have an SPF record, you'll need to add or update values for Office 365. For example, say your existing SPF record for contoso.com is this:
  
``` dns
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:smtp.adatum.com -all
```

Jetzt aktualisieren Sie den SPF-Eintrag für Office 365. Sie bearbeiten den aktuellen Datensatz so, dass Sie einen SPF-Eintrag haben, der die benötigten Werte enthält. Für Office 365, "SPF.Protection.Outlook.com".
  
Richtig:
  
``` dns
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:spf.protection.outlook.com include:smtp.adatum.com -all
```

Falsch:
  
``` dns
Record 1:
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:smtp.adatum.com -all
Record 2:
Values: v=spf1 include:spf.protection.outlook.com -all
```

### <a name="more-examples-of-common-spf-values"></a>Weitere Beispiele für häufig verwendete SPF-Werte
<a name="bkmk_addtospf"> </a>

Wenn Sie die vollständige Office 365 Suite verwenden und mailschimpanse verwenden, um Marketing-e-Mails in Ihrem Auftrag zu senden, könnte Ihr SPF-Eintrag bei Contoso.com wie folgt aussehen, wobei die Zeilen 1, 3 und 5 aus der obigen Tabelle verwendet werden. Beachten Sie, dass die Zeilen 1 und 5 erforderlich sind.
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com include:servers.mcsv.net -all
```

Alternativ kann bei einer Exchange-Hybridkonfiguration, in der E-Mails sowohl von Office 365 als auch von Ihrem lokalen E-Mail-System gesendet werden, der SPF-Eintrag bei contoso.com wie folgt aussehen:
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com include:mail.contoso.com -all
```

These are some common examples that can help you adapt your existing SPF record when you add your domain to Office 365 for email. If you have a complicated scenario that includes, for example, edge email servers for managing email traffic across your firewall, you'll have a more detailed SPF record to set up. Learn how: [Set up SPF records in Office 365 to help prevent spoofing](https://go.microsoft.com/fwlink/?LinkId=787656).
  
Mit diesem kurzen Link gelangen Sie wieder hierher zurück: [https://aka.ms/o365edns](https://aka.ms/o365edns)
