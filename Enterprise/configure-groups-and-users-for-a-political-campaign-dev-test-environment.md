---
title: "Konfigurieren von Gruppen und Benutzern für eine politische Kampagne in einer Entwicklungs-/Testumgebung"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: None
ms.custom: Strat_O365_Enterprise
ms.assetid: 0e22bcf3-bad3-42a4-b44f-276e0cf4790f
description: "Zusammenfassung: Erstellen Sie Office 365 und Enterprise-Mobilität + Testabonnements Sicherheit (zur Abstimmung) mit Benutzern und Gruppen für eine politischen Kampagne Test-/-Umgebung."
ms.openlocfilehash: 25d03e0aa521c8fdbf20c2dc3ff2fc46e1aabe2f
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2018
---
# <a name="configure-groups-and-users-for-a-political-campaign-devtest-environment"></a>Konfigurieren von Gruppen und Benutzern für eine politische Kampagne in einer Entwicklungs-/Testumgebung

 **Zusammenfassung:** Erstellen von Office 365 und Enterprise-Mobilität + Testabonnements Sicherheit (zur Abstimmung) mit Benutzern und Gruppen für eine politischen Kampagne Test-/-Umgebung.
  
Verwenden Sie die Anweisungen in diesem Artikel, um einer Test-/Umgebung erstellen, die vereinfachte Benutzerkonten und Gruppen für die [Microsoft Security Guidance for politischen Kampagnen, gemeinnützige Organisationen, und andere Agile Organisationen](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) -Lösung enthält.
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a>Phase 1: Erstellen Ihrer Office 365-Entwicklungs-/Testumgebung

In dieser Phase erhalten Sie Testabonnements für Office 365 E5 und Enterprise-Mobilität + Sicherheit (zur Abstimmung) E5 für fiktive Organisation, die eine politische Kampagne darstellt.
  
Folgen Sie zunächst den Anweisungen in **Phase 2** des Artikels [Office 365-Entwicklungs-/Testumgebung](office-365-dev-test-environment.md).
  
Im nächsten Schritt für den Test zur Abstimmung E5-Abonnement registrieren und die derselben Organisation wie Test Office 365-Abonnement hinzugefügt.
  
1. Falls erforderlich, melden Sie sich mit den Anmeldeinformationen des globalen Administratorkontos für Ihr Testabonnement beim Office 365-Portal an. Hilfe finden Sie unter [Wo kann ich mich bei Office 365 Business anmelden?](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Klicken Sie auf die Kachel **Admin**.
    
3. Klicken Sie auf der Registerkarte **Office Admin Center** in Ihrem Browser im linken Navigationsbereich auf **Abrechnung > Dienste kaufen**.
    
4. Suchen Sie auf der Seite **Dienste kaufen** den Artikel **Enterprise Mobility + Security E5**. Platzieren Sie den Mauszeiger auf dem Artikelnamen, und klicken Sie auf **Start free trial**.
    
5. Klicken Sie auf der Seite für die **Bestätigung Ihrer Bestellung** auf **Jetzt versuchen**.
    
6. Klicken Sie auf der Seite **Bestellbestätigung** auf **Weiter**.
    
Aktivieren Sie im nächsten Schritt die zur Abstimmung E5 Lizenz für das globale Administratorkonto ein.
  
1. Klicken Sie auf der Registerkarte **Office 365 Admin Center** in Ihrem Browser im linken Navigationsbereich auf **Benutzer > Aktive Benutzer**.
    
2. Klicken Sie auf Ihr globales Administratorkonto und dann auf **Bearbeiten**, um die **Produktlizenzen** anzuzeigen.
    
3. Setzen Sie im Bereich **Product licenses** die Produktlizenz für **Enterprise Mobility + Security E5** auf **On**. Klicken Sie auf **Speichern** und dann auf **Schließen**.
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups"></a>Phase 2: Erstellen und Konfigurieren der Azure Active Directory(AD)-Gruppen

In dieser Phase werden die Azure AD-Gruppen für Ihre Kampagne erstellt und konfiguriert.
  
Erstellen Sie zunächst eine Reihe von Gruppen für eine typische politischen Kampagne mit dem Azure-Portal.
  
1. Fahren Sie auf einer separaten Registerkarte in Ihrem Browser mit der Azure-Portal unter [https://portal.azure.com](https://portal.azure.com). Bei Bedarf, melden Sie sich mit den Anmeldeinformationen des das globale Administratorkonto ein Test E5 für Office 365-Abonnement.
    
2. Klicken Sie im Azure-Portal auf **Azure Active Directory > Benutzer und Gruppen > Alle Gruppen**.
    
3. Führen Sie die folgenden Schritte für jede Gruppenname in dieser Liste aus:
    
  - Senior-Mitarbeiter und strategische Mitarbeiter
    
  - IT-Mitarbeiter
    
  - Analytiker
    
  - Stammpersonal
    
  - Betriebspersonal
    
  - Außendienstmitarbeiter
    
1. Klicken Sie auf dem Blatt **Alle Gruppen** auf **+ Neue Gruppe**.
    
2. Geben Sie im **Feld Name**den Namen der Gruppe aus der Liste.
    
3. Wählen Sie **dynamische Benutzer** , **Mitgliedschaft**in.
    
4. Klicken Sie auf **Ja** für **Office-Features aktivieren**.
    
5. Klicken Sie auf die **Dynamische Abfrage hinzufügen**.
    
6. In **Hinzufügen von Benutzern, in dem**, wählen Sie **Abteilung**.
    
7. Wählen Sie im nächsten Feld **entspricht**.
    
8. Geben Sie im nächsten Feld den Namen der Gruppe aus der Liste aus.
    
9. Klicken Sie auf **Abfrage hinzufügen**, und klicken Sie dann auf **Erstellen**.
    
10. Klicken Sie auf **Benutzer und Gruppen - alle Gruppen**.
    
Im nächsten Schritt konfigurieren Sie die Gruppen, sodass Elemente automatisch Office 365 E5 und zur Abstimmung E5 Lizenzen zugewiesen sind.
  
1. Klicken Sie im Azure-Portal auf **Azure Active Directory > Lizenzen > Alle Produkte**.
    
2. Wählen Sie in der Liste **Enterprise-Mobilität + Sicherheit E5** und **Office 365 Enterprise E5**, und klicken Sie dann auf **+ zuweisen**.
    
3. Klicken Sie auf dem Blatt **Lizenz zuweisen** auf **Benutzer und Gruppen**.
    
4. Wählen Sie in der Liste der Gruppen Folgendes aus:
    
  - Analytiker
    
  - Außendienstmitarbeiter
    
  - IT-Mitarbeiter
    
  - Betriebspersonal
    
  - Stammpersonal
    
  - Senior-Mitarbeiter und strategische Mitarbeiter
    
5. Klicken Sie auf **Auswählen** und dann auf **Zuweisen**.
    
6. Schließen Sie die Registerkarte für das Azure Portal in Ihrem Browser.
    
## <a name="phase-3-add-your-user-accounts"></a>Phase 3: Hinzufügen von Benutzerkonten

In dieser Phase werden beispielhafte Benutzerkonten für Ihre politische Kampagne hinzugefügt.
  
Erstens Sie [Verbinden mit dem Azure Active Directory V2 PowerShell-Modul](https://go.microsoft.com/fwlink/?linkid=842218).
  
Geben Sie anschließend den Namen Ihrer Organisation, Ihren Standort und ein gemeinsames Kennwort ein, und führen Sie dann die folgenden Befehle an der PowerShell-Eingabeaufforderung oder in der ISE-Umgebung ein (Integrated Script Environment) aus:
  
```
$orgName="<organization name, such as contoso for the contoso.onmicrosoft.com trial subscription domain name>"
$location="<the ISO ALPHA2 country code, such as US for the United States>"
$commonPassword="<common password for all the new accounts>"

$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPassword

$deptName="Senior and strategic staff"
$userNames=@("Candidate","ChiefOfStaff","Strategic1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="IT staff"
$userNames=@("ITAdmin1","ITAdmin2") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Analytics staff"
$userNames=@("DataScientist1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Regular core staff"
$userNames=@("Regular1","Regular2") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Operations staff"
$userNames=@("Operations1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Field staff"
$userNames=@("FieldConsultant1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }

```

> [!IMPORTANT]
> Hier eine allgemeine Kennwort werden für die Automatisierung und Erleichterung der Konfiguration für eine Test-/-Umgebung. Dies ist nicht für Produktion Abonnements empfohlen. Wie Sie sich jedes dieser Benutzerkonten für neue anmelden, werden Sie aufgefordert, das Kennwort zu ändern. 
  
Gehen Sie folgendermaßen vor, um sicherzustellen, dass die dynamische Gruppenmitgliedschaft und gruppenbasierte Lizenzierung ordnungsgemäß funktionieren.
  
1. Klicken Sie auf der Registerkarte **Microsoft Office Home** in Ihrem Browser auf die Kachel **Admin**.
    
2. Klicken Sie auf der neuen Registerkarte **Office Admin Center** des Browsers auf **Benutzer**.
    
3. Klicken Sie in der Liste der Benutzer auf **Candidate**.
    
4. Überprüfen Sie im Bereich, in der die Eigenschaften des Benutzerkontos **Candidate** aufgelistet, die aus:
    
  - Es ist ein Mitglied der Gruppe **Senior und strategische Mitarbeiter** (im **Gruppenmitgliedschaften**).
    
  - Es wurde die **Mobilität in Unternehmen + Sicherheit E5** und **Office 365 Enterprise E5** Lizenzen (in **Lizenzen**) zugewiesen.
    
5. Schließen Sie den Bereich **Candidate** Benutzer Konto.
    
## <a name="record-values-for-future-reference"></a>Notieren von Werten für zukünftige Verwendung

Notieren Sie diese Werte für die Arbeit mit Office 365- und EMS-Testabonnements für diese Entwicklung-/Testumgebung:
  
- Organisationsname für das Testabonnement: _______________________________________________  
    
    Für den Domänennamen contoso.onmicrosoft.com des Testabonnements lautet der Name der Organisation zum Beispiel „contoso“.
    
- Der Name der Office 365 globaler Administrator: ___.onmicrosoft.com
    
    Notieren Sie das Kennwort für dieses Konto und das allgemeine anfängliche Kennwort für die anderen Benutzerkonten an einem sicheren Ort.
    
## <a name="next-step"></a>Nächster Schritt

Erstellen Sie die vier verschiedenen Typen von SharePoint Online Teamwebsites in dieser Umgebung Test-/und [Teamwebsites in einer politischen Kampagne Test-/Umgebung erstellen](create-team-sites-in-a-political-campaign-dev-test-environment.md).
  
## <a name="see-also"></a>Weitere Artikel

[Microsoft-Sicherheitsleitfaden für politische Kampagnen, gemeinnützigen Organisationen und andere agile Organisationen](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[Erstellen von Teamwebsites in einer politischen Kampagne Test-/-Umgebung](create-team-sites-in-a-political-campaign-dev-test-environment.md)
  
[Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz](cloud-adoption-test-lab-guides-tlgs.md)
  
[Cloudakzeptanz und Hybridlösungen](cloud-adoption-and-hybrid-solutions.md)




