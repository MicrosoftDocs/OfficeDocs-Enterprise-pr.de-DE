---
title: "Verbundidentität für Ihre Office 365-Entwicklungs-/Testumgebung"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Strat_O365_Enterprise
- TLG
- Ent_TLGs
ms.assetid: 65a6d687-a16a-4415-9fd5-011ba9c5fd80
description: "Zusammenfassung: Konfigurieren Sie Verbundauthentifizierung für Ihre Office 365 Dev/Test-Umgebung."
ms.openlocfilehash: e37b57d5497f3151885682f7c4d8abca7120b99e
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="federated-identity-for-your-office-365-devtest-environment"></a>Verbundidentität für Ihre Office 365-Entwicklungs-/Testumgebung

 **Zusammenfassung:** Konfigurieren Sie Verbundauthentifizierung für Ihre Office 365 Dev/Test-Umgebung.
  
Office 365 unterstützt Identitätsverbund. Dies bedeutet, dass nicht durch die Überprüfung von Anmeldeinformationen selbst, Office 365 verbindenden Benutzers auf einem Server Verbundauthentifizierung verweist, die Office 365 vertraut. Wenn die Anmeldeinformationen des Benutzers korrekt sind, sendet der Verbundauthentifizierung-Server ein Sicherheitstoken, die der Client dann an Office 365 als Authentifizierungsbeweis sendet. Identitätsverbund ermöglicht die Verschiebung und Skalieren der Authentifizierung für ein Office 365-Abonnement und erweiterte Szenarien für Authentifizierung und Sicherheit.
  
In diesem Artikel wird beschrieben, wie Sie die Verbundauthentifizierung für die Office 365-Entwicklungs-/Testumgebung konfigurieren können, die zu Folgendem führt:
  
**Abbildung 1: Die Verbundauthentifizierung für Office 365 Dev/Test-Umgebung**

![Der Webanwendungs-Proxyserver, der der DirSync für die Office 365-Entwicklungs-/Testumgebung hinzugefügt wurde](images/f50039e4-796a-42c0-bfdc-87c2026b1579.png)
  
Die in Abbildung 1 gezeigte Konfiguration besteht aus:  
  
- Einem Office 365 E5-Testabonnement, das 30 Tage nach Erstellung abläuft.
    
- Einem vereinfachten Unternehmensintranet, das mit dem Internet verbunden ist, bestehend aus fünf virtuellen Computern in einem Subnetz eines virtuellen Azure-Netzwerks (DC1, APP1, CLIENT1, ADFS1 und PROXY1). Azure AD Connect wird auf APP1 ausgeführt, um die Liste von Konten in der Windows Server AD-Domäne mit Office 365 zu synchronisieren. PROXY1 erhält die eingehenden Authentifizierungsanfragen. ADFS1 überprüft Anmeldeinformationen mit DC1 und gibt Sicherheitstoken aus.
    
Das Einrichten dieser Entwicklungs-/Testumgebung besteht aus fünf Phasen:
  
1. Erstellen der simulierten Office 365-Entwicklungs-/Testumgebung mit DirSync.
    
2. Erstellen des AD FS-Servers (ADFS1).
    
3. Erstellen des Webproxyservers (PROXY1).
    
4. Erstellen eines selbstsignierten Zertifikats und Konfigurieren von ADFS1 und PROXY1.
    
5. Konfigurieren von Office 365 für Verbundidentität.
    
Um eine Bereitstellung in der Produktion über die Verbundauthentifizierung für Office 365 in Azure schrittweise, finden Sie unter [Deploy hohe Verfügbarkeit Verbundauthentifizierung für Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md).
  
> [!NOTE]
> Sie können diese Entwicklungs-/Testumgebung nicht mit einem Azure-Testabonnement konfigurieren. 
  
> [!TIP]
> Klicken Sie [hier](http://aka.ms/catlgstack), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in der Microsoft Cloud zu erhalten.
  
## <a name="phase-1-create-the-simulated-enterprise-office-365-devtest-environment-with-dirsync"></a>Phase 1: Erstellen der simulierten Office 365-Entwicklungs-/Testumgebung mit DirSync

Befolgen Sie die Anweisungen in [DirSync für Ihre Office 365 Dev/Test-Umgebung](dirsync-for-your-office-365-dev-test-environment.md) zum Erstellen der simulierten Enterprise Office 365-Test-/-Umgebung mit APP1 als Dirsync-Server und synchronisierte Identität zwischen Office 365 und Windows Azure AD Konten auf DC1.
  
Im nächsten Schritt erstellen Sie einen neuen öffentlichen DNS-Domänennamen basierend auf Ihren aktuellen Domänennamen und Ihrem Office 365-Abonnement hinzugefügt. Es wird empfohlen, mit dem Namen **Testlabor.** \<Ihrer öffentlichen Domäne >. Wenn der öffentlichen Domäne "contoso.com" lautet, fügen Sie beispielsweise der öffentlichen Domäne Name testlab.contoso.com.
  
Anweisungen zum Erstellen der richtigen DNS-Einträge im DNS-Anbieter und die Domäne hinzufügen, um Ihre Testversion Office 365-Abonnements finden Sie unter [Hinzufügen von Benutzern und Domäne zu Office 365](https://support.office.com/article/Add-users-and-domain-to-Office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611). 
  
Nachfolgend sehen Sie die daraus resultierende Konfiguration.
  
**Abbildung 2: DirSync für Office 365 Dev/Test-Umgebung**

![Die Office 365-Entwicklungs-/Testumgebung mit DirSync](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
In Abbildung 2 ist die DirSync für die Office 365-Entwicklungs-/Testumgebung dargestellt, die Office 365 sowie die virtuellen Computer CLIENT1, APP1 und DC1 in einem virtuellen Azure-Netzwerk umfasst.
  
## <a name="phase-2-create-the-ad-fs-server"></a>Phase 2: Erstellen des AD FS-Servers

Ein AD FS-Server bietet Verbundauthentifizierung zwischen Office 365 und den Konten in der Domäne „corp.contoso.com“, die auf DC1 gehostet wird.
  
Klicken Sie zum Erstellen eines Azure-virtueller Computers für ADFS1 Geben Sie den Namen Ihres Abonnements und die Ressourcengruppe und Azure Speicherort für Ihre Konfiguration Base, und führen Sie diese Befehle an der Befehlszeile Azure PowerShell auf dem lokalen Computer.
  
```
$subscr="<your Azure subscription name>"
$rgName="<the resource group name of your Base Configuration>"
Login-AzureRMAccount
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
$staticIP="10.0.0.100"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip = New-AzureRMPublicIpAddress -Name ADFS1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic = New-AzureRMNetworkInterface -Name ADFS1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName ADFS1 -VMSize Standard_D2_v2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for ADFS1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName ADFS1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "ADFS-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!TIP]
> Klicken Sie auf [hier](https://gallery.technet.microsoft.com/PowerShell-commands-for-f79bc2c2?redir=0) eine Textdatei ab, die PowerShell-Befehle in diesem Artikel enthält.
  
Im nächsten Schritt mit der [Azure-Portal](http://portal.azure.com) ADFS1 virtuellen Computer mit dem ADFS1 lokaler Administrator Kontoname und Kennwort hergestellt werden soll, und öffnen Sie eine Windows PowerShell-Eingabeaufforderung.
  
Zum Überprüfen der Namen Auflösung und Netzwerk-Kommunikation zwischen ADFS1 und DC1 führen Sie den Befehl **Ping dc1.corp.contoso.com** , und stellen Sie sicher, dass es vier Antworten gibt.
  
Verknüpfen Sie als Nächstes unter Verwendung der folgenden Befehle an der Windows PowerShell-Eingabeaufforderung auf ADFS1 den virtuellen Computer ADFS1 mit der Domäne CORP.
  
```
$cred=Get-Credential -UserName "CORP\\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

Nachfolgend sehen Sie die daraus resultierende Konfiguration.
  
**Abbildung 3: Hinzufügen von AD FS-server**

![Der AD FS-Server, der der DirSync für die Office 365-Entwicklungs-/Testumgebung hinzugefügt wurde](images/da82f39e-426d-41e2-842a-c13b382d63d5.png)
  
Abbildung 3 zeigt das Hinzufügen des ADFS1-Servers zu DirSync für die Office 365-Entwicklungs-/Testumgebung.
  
## <a name="phase-3-create-the-web-proxy-server"></a>Phase 3: Erstellen des Webproxyservers

PROXY1 stellt die Proxyfunktion für Authentifizierungsnachrichten zwischen Benutzern, die versuchen, sich zu authentifizieren, und ADFS1 bereit.
  
Um einen virtuellen Azure-Computer für PROXY1 zu erstellen, geben Sie den Namen Ihrer Ressourcengruppe und den Azure-Speicherort ein und führen diese Befehle in der Azure PowerShell-Befehlszeile auf Ihrem lokalen Computer aus.
  
```
$rgName="<the resource group name of your Base Configuration>"
$staticIP="10.0.0.101"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip = New-AzureRMPublicIpAddress -Name PROXY1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Static
$nic = New-AzureRMNetworkInterface -Name PROXY1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName PROXY1 -VMSize Standard_D2_v2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for PROXY1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName PROXY1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "PROXY1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> PROXY1 wird einer statischen öffentlichen IP-Adresse zugewiesen, da Sie einen öffentlichen DNS-Eintrag erstellen, der darauf verweist, und der nicht geändert werden muss, wenn Sie den virtuellen PROXY1-Computer neu starten. 
  
Fügen Sie eine Regel zur Netzwerksicherheitsgruppe des Subnetzes CorpNet um unaufgeforderten eingehenden Verkehr PROXY1s privaten IP-Adresse und TCP-Port 443 über das Internet zu ermöglichen. Führen Sie diese Befehle an der Azure PowerShell-Eingabeaufforderung auf dem lokalen Computer.
  
```
$rgName="<the resource group name of your Base Configuration>"
Get-AzureRmNetworkSecurityGroup -Name CorpNet -ResourceGroupName $rgName | Add-AzureRmNetworkSecurityRuleConfig -Name "HTTPS-to-PROXY1" -Description "Allow TCP 443 to PROXY1" -Access "Allow" -Protocol "Tcp" -Direction "Inbound" -Priority 101 -SourceAddressPrefix "Internet" -SourcePortRange "*" -DestinationAddressPrefix "10.0.0.101" -DestinationPortRange "443" | Set-AzureRmNetworkSecurityGroup
```

Im nächsten Schritt mit der [Azure-Portal](http://portal.azure.com) PROXY1 virtuellen Computer mit dem PROXY1 lokaler Administrator Kontoname und Kennwort hergestellt werden soll, und öffnen Sie eine Windows PowerShell-Eingabeaufforderung auf PROXY1.
  
Zum Überprüfen der Namen Auflösung und Netzwerk-Kommunikation zwischen PROXY1 und DC1 führen Sie den Befehl **Ping dc1.corp.contoso.com** , und stellen Sie sicher, dass es vier Antworten gibt.
  
Verknüpfen Sie als Nächstes unter Verwendung der folgenden Befehle an der Windows PowerShell-Eingabeaufforderung auf PROXY1 den virtuellen Computer PROXY1 mit der Domäne CORP.
  
```
$cred=Get-Credential -UserName "CORP\\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

Zeigen Sie die öffentliche IP-Adresse von PROXY1 mit den folgenden Azure PowerShell-Befehlen auf dem lokalen Computer an:
  
```
Write-Host (Get-AzureRMPublicIpaddress -Name "PROXY1-PIP" -ResourceGroup $rgName).IPAddress
```

Im nächsten Schritt arbeiten mit Ihrem öffentlichen DNS-Anbieter und erstellen einen neuen öffentlichen DNS-A-Datensatz für **fs.testlab.** \<des DNS-Domänennamens >, aufgelöst wird, um die IP-Adresse mit dem Befehl **Write-Host** angezeigt. Die **fs.testlab.** \<des DNS-Domänennamens > ist nachstehend der *Verbunddienst FQDN* .
  
Im nächsten Schritt der [Azure-Portal](http://portal.azure.com) verwenden, um am virtuellen Computer DC1 mithilfe der CORP verbinden\\User1 Anmeldeinformationen, und führen Sie dann die folgenden Befehle an einer Administratorebene Windows PowerShell-Eingabeaufforderung:
  
```
$testZone="<the FQDN of your testlab domain from phase 1, example: testlab.contoso.com>"
$testZoneFile= $testZone + ".dns"
Add-DnsServerPrimaryZone -Name $testZone -ZoneFile $testZoneFile
Add-DnsServerResourceRecordA -Name "fs" -ZoneName $testZone -AllowUpdateAny -IPv4Address "10.0.0.100" -TimeToLive 01:00:00
```

Diese Befehle erstellen einen DNS-A-Eintrag für den FQDN des Verbunddiensts, den virtuelle Computer im virtuellen Azure-Netzwerk in die private IP-Adresse von ADFS1 auflösen können.
  
Nachfolgend sehen Sie die daraus resultierende Konfiguration.
  
**Abbildung 4: Hinzufügen der Web Application Proxy-server**

![Der Webanwendungs-Proxyserver, der der DirSync für die Office 365-Entwicklungs-/Testumgebung hinzugefügt wurde](images/f50039e4-796a-42c0-bfdc-87c2026b1579.png)
  
Abbildung 4 zeigt das Hinzufügen des PROXY1-Servers.
  
## <a name="phase-4-create-a-self-signed-certificate-and-configure-adfs1-and-proxy1"></a>Phase 4: Erstellen eines selbstsignierten Zertifikats und Konfigurieren von ADFS1 und PROXY1

In dieser Phase erstellen Sie ein selbstsigniertes digitales Zertifikat für den FQDN des Verbunddiensts und konfigurieren ADFS1 und PROXY1 als AD FS-Farm.
  
Zunächst, mit dem das [Azure Portal](http://portal.azure.com) -Verbindung mit dem virtuellen Computer DC1 mithilfe der CORP\\User1 Anmeldeinformationen, und öffnen Sie dann eine Administratorebene Windows PowerShell command Prompt.
  
Im nächsten Schritt erstellen Sie das AD FS-Dienstkonto mit dem folgenden Befehl an der Windows PowerShell-Eingabeaufforderung auf DC1:
  
```
New-ADUser -SamAccountName ADFS-Service -AccountPassword (read-host "Set user password" -assecurestring) -name "ADFS-Service" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

Beachten Sie, dass Sie von dem Befehl aufgefordert werden, das Kontokennwort anzugeben. Verwenden Sie ein sicheres Kennwort, und notieren Sie es an einem sicheren Ort. Sie benötigen es für diese Phase und für Phase 5.
  
Verwendung des [Azure Portal](http://portal.azure.com) Verbindung mit dem ADFS1 virtuellen Computer mithilfe der CORP\\User1 Anmeldeinformationen. Öffnen Sie eine Administratorebene Windows PowerShell-Eingabeaufforderung auf ADFS1, füllen Sie Ihre Verbunddienst FQDN, und führen Sie dann die folgenden Befehle aus, um ein selbstsigniertes Zertifikat erstellen aus:
  
```
$fedServiceFQDN="<federation service FQDN>"
New-SelfSignedCertificate -DnsName $fedServiceFQDN -CertStoreLocation "cert:\\LocalMachine\\My"
New-Item -path c:\\Certs -type directory
New-SmbShare -name Certs -path c:\\Certs -changeaccess CORP\\User1
```

Gehen Sie dann folgendermaßen vor, um das neue selbstsignierte Zertifikat als Datei zu speichern.
  
1. Klicken Sie auf **Start**, geben Sie **mmc.exe**, und drücken Sie die **EINGABETASTE**.
    
2. Klicken Sie auf **Datei > Snap-In hinzufügen/entfernen**.
    
3. **Hinzufügen oder Entfernen von-Snap-ins**Doppelklicken Sie in der Liste der verfügbaren Snap-Ins auf **Zertifikate** , klicken Sie auf **Computerkonto**, und klicken Sie dann auf **Weiter**.
    
4. Klicken Sie im **Dialogfeld Computer auswählen**auf **Fertig stellen**, und klicken Sie dann auf **OK**.
    
5. Öffnen Sie im Strukturbereich **Zertifikate (lokaler Computer) > persönlich > Zertifikate**.
    
6. Mit der rechten Maustaste in des Zertifikats mit Ihrem Verbunddienst FQDN, klicken Sie auf **Alle Tasks**, und klicken Sie dann auf **Exportieren**.
    
7. Klicken Sie auf der Seite **Willkommen** auf **Weiter**.
    
8. Klicken Sie auf der Seite **Privatschlüssel exportieren** klicken Sie auf **Ja**, und klicken Sie dann auf **Weiter**.
    
9. Klicken Sie auf der Seite **Exportdateiformat** klicken Sie auf **alle erweiterten Eigenschaften exportieren**, und klicken Sie dann auf **Weiter**.
    
10. Klicken Sie auf der Seite **Sicherheit** , klicken Sie auf **Kennwort** , und geben Sie im Feld **Kennwort** ein Kennwort ein und **Kennwort bestätigen.**
    
11. Klicken Sie auf der Seite **zu exportierende Datei** auf **Durchsuchen**.
    
12. Navigieren Sie zu der **C:\\Zertifikate** Ordner, geben Sie **SSL** im Feld **Dateiname**ein, und klicken Sie dann auf **zu speichern.**
    
13. Klicken Sie auf der Seite **zu exportierende Datei** auf **Weiter**.
    
14. Klicken Sie auf der Seite **Fertigstellen des Zertifikatexport-Assistenten** auf **Fertig stellen**. Wenn Sie aufgefordert werden, klicken Sie auf **OK**.
    
Im nächsten Schritt erstellen Sie den AD FS-Dienst mit dem folgenden Befehl an der Windows PowerShell-Eingabeaufforderung auf ADFS1:
  
```
Install-WindowsFeature ADFS-Federation -IncludeManagementTools
```

Warten Sie, bis die Installation abgeschlossen ist.
  
Konfigurieren Sie als Nächstes den AD FS-Dienst mit den folgenden Schritten:
  
1. Klicken Sie auf **Start**, und klicken Sie dann auf das Symbol für **Server-Manager** .
    
2. Klicken Sie im Strukturbereich von Server-Manager auf **AD FS**.
    
3. Klicken Sie in der Symbolleiste oben auf das Symbol orange Vorsicht, und klicken Sie auf **der Verbunddienst auf diesem Server konfigurieren**.
    
4. Klicken Sie auf der Seite **Willkommen** des Active Directory Federation Services Konfigurations-Assistenten auf **Weiter**.
    
5. Klicken Sie auf der Seite **Verbindung mit AD DS** auf **Weiter**.
    
6. Auf der Seite **Diensteigenschaften angeben** :
    
  - Klicken Sie für **SSL-Zertifikat**auf den Pfeil nach unten, und klicken Sie dann auf das Zertifikat mit dem Namen von Ihrem Verbunddienst FQDN.
    
  - Geben Sie im Feld **Anzeigename für den Verbund Dienst**den Namen des fiktiven Unternehmens.
    
  - Klicken Sie auf **Weiter**.
    
7. Klicken Sie auf der Seite **Dienstkonto angeben** für **Kontonamen**auf **auswählen** .
    
8. **Wählen Sie Benutzer oder -Dienstkonto**Geben Sie ein **AD FS-Dienst**, klicken Sie auf **Namen überprüfen**und klicken Sie dann auf **OK**.
    
9. Geben Sie im Feld **Kennwort**das Kennwort für das AD FS-Dienstkonto ein, und klicken Sie dann auf **Weiter**.
    
10. Klicken Sie auf der Seite **Konfigurationsdatenbank angeben** auf **Weiter**.
    
11. Klicken Sie auf der Seite **Optionen überprüfen** auf **Weiter**.
    
12. Klicken Sie auf der Seite **Voraussetzung überprüft** auf **Konfigurieren**.
    
13. Klicken Sie auf der Seite **Ergebnisse** auf **Schließen**.
    
14. Klicken Sie auf **Start**, klicken Sie auf das Symbol Power, klicken Sie auf **neu**, und klicken Sie dann auf **Weiter**.
    
Über das [Portal Azure](http://portal.azure.com)Herstellen einer Verbindung mit der CORP PROXY1 mit\\User1 Kontoanmeldeinformationen.
  
Gehen Sie dann folgendermaßen vor, um das selbstsignierte Zertifikat zu installieren und PROXY1 zu konfigurieren.
  
1. Klicken Sie auf **Start**, geben Sie **mmc.exe**, und drücken Sie die **EINGABETASTE**.
    
2. Klicken Sie auf **Datei > Snap-In hinzufügen/entfernen**.
    
3. **Hinzufügen oder Entfernen von-Snap-ins**Doppelklicken Sie in der Liste der verfügbaren Snap-Ins auf **Zertifikate** , klicken Sie auf **Computerkonto**, und klicken Sie dann auf **Weiter**.
    
4. Klicken Sie im **Dialogfeld Computer auswählen**auf **Fertig stellen**, und klicken Sie dann auf **OK**.
    
5. Öffnen Sie im Strukturbereich **Zertifikate (lokaler Computer) > persönlich > Zertifikate**.
    
6. Mit der rechten Maustaste **Persönliche**, klicken Sie auf **Alle Tasks**, und klicken Sie dann auf **Importieren**.
    
7. Klicken Sie auf der Seite **Willkommen** auf **Weiter**.
    
8. Geben Sie auf der Seite **zu importierende Datei** ** \\ \\adfs1\\Zertifikate\\ssl.pfx**, und klicken Sie dann auf **Weiter**.
    
9. Geben Sie auf der Seite **Schutz des privaten Schlüssels** das Kennwort des Zertifikats im Feld **Kennwort**, und klicken Sie dann auf **nächsten.**
    
10. Klicken Sie auf der Seite **Zertifikatspeicher** auf **nächsten.**
    
11. Klicken Sie auf der Seite **Fertigstellen des Assistenten** auf **Fertig stellen**.
    
12. Klicken Sie auf der Seite **Zertifikatspeicher** auf **Weiter**.
    
13. Wenn Sie aufgefordert werden, klicken Sie auf **OK**.
    
14. Klicken Sie im Strukturbereich auf **Zertifikate** .
    
15. Mit der rechten Maustaste in des Zertifikats, und klicken Sie dann auf **Kopieren**.
    
16. Öffnen Sie im Strukturbereich **Vertrauenswürdige Stammzertifizierungsstellen > Zertifikate**.
    
17. Verschieben Sie den Mauszeiger unterhalb der Liste der installierten Zertifikate, mit der rechten Maustaste, und klicken Sie dann auf **Einfügen**.
    
Öffnen Sie eine PowerShell-Eingabeaufforderung auf Administratorebene, und führen Sie den folgenden Befehl aus:
  
```
Install-WindowsFeature Web-Application-Proxy -IncludeManagementTools
```

Warten Sie, bis die Installation abgeschlossen ist.
  
Verwenden Sie die folgenden Schritte, um den Webanwendungs-Proxydienst so zu konfigurieren, dass ADFS1 als Verbundserver verwendet wird:
  
1. Klicken Sie auf **Start**, und klicken Sie dann auf **Server-Manager**.
    
2. Klicken Sie im Strukturbereich **Remotezugriff**auf.
    
3. Klicken Sie in der Symbolleiste oben auf das Symbol orange Vorsicht, und klicken Sie dann auf **den Web Application Proxy-Assistenten zu öffnen**.
    
4. Klicken Sie auf der Seite **Willkommen** des Web Application Proxy Konfigurations-Assistenten auf **Weiter**.
    
5. Auf der Seite **Verbundserver** :
    
  - Geben Sie Ihre Verbunddienst FQDN im **Verbund Dienstname**.
    
  - Typ **CORP\\User1** im **Feld Benutzername**.
    
  - Geben Sie im Feld **Kennwort**das Kennwort für das Konto User1 an.
    
  - Klicken Sie auf **Weiter**.
    
6. Klicken Sie auf der Seite **AD FS-Proxy-Zertifikat** klicken Sie auf den Pfeil nach unten, klicken Sie auf das Zertifikat mit Ihrem Verbunddienst FQDN, und klicken Sie dann auf **Weiter**.
    
7. Klicken Sie auf **der Bestätigungsseite** auf **Konfigurieren**.
    
8. Klicken Sie auf der Seite **Ergebnisse** auf **Schließen**.
    
## <a name="phase-5-configure-office-365-for-federated-identity"></a>Phase 5: Konfigurieren von Office 365 für Verbundidentität

Verwendung des [Azure Portal](http://portal.azure.com) zum Herstellen einer Verbindung mit der CORP am virtuellen Computer APP1\\User1 Kontoanmeldeinformationen.
  
Verwenden Sie diese Schritte, um Azure AD Connect und Ihr Office 365-Abonnement für die Verbundauthentifizierung zu konfigurieren:
  
1. Doppelklicken Sie vom Desktop auf **Azure Active Directory verbinden**.
    
2. Klicken Sie auf der Seite **Willkommen auf Azure AD-verbinden** auf **Konfigurieren**.
    
3. Auf der Seite **zusätzliche Aufgaben** **ändern Benutzer - Anmeldung**auf, und klicken Sie dann auf **Weiter**.
    
4. Geben Sie auf der Seite **Verbindung mit Azure Active Directory herstellen** Ihre Office 365 globaler Administrator-Kontonamen und das Kennwort ein, und klicken Sie dann auf **Weiter**.
    
5. Klicken Sie auf der Seite **Benutzeranmeldung** auf **Verbund mit AD FS**, und klicken Sie dann auf **Weiter**.
    
6. Klicken Sie auf der Seite **AD FS-Farm** auf **einer vorhandenen AD FS-Farm verwenden**, geben Sie im Feld **Servername** **ADFS1** ein, und klicken Sie dann auf **Weiter**.
    
7. Wenn Sie für Server-Anmeldeinformationen aufgefordert werden, geben Sie die Anmeldeinformationen der corp\\User1 berücksichtigt werden, und klicken Sie dann auf **OK**.
    
8. Geben Sie auf der Seite Anmeldeinformationen für **Domänenadministrator** **CORP\\User1** **Benutzernamen** und das Kontokennwort im Feld **Kennwort ein**, und klicken Sie dann auf **Weiter**.
    
9. Geben Sie auf der Seite **AD FS-Dienstkonto** **CORP\\AD FS-Dienst** in **Benutzername** und das Kontokennwort in **Domänenkennwort für Benutzer**, und klicken Sie dann auf **Weiter**.
    
10. Klicken Sie auf der Seite **Azure AD-Domäne** in der **Domäne**wählen Sie den Namen der Domäne, die Sie zuvor erstellt und Ihr Office 365-Abonnement in Phase 1 hinzugefügt, und klicken Sie dann auf **Weiter**.
    
11. Klicken Sie auf der Seite **bereit zum Konfigurieren** klicken Sie auf **Konfigurieren**.
    
12. Klicken Sie auf der Seite **Installation abgeschlossen** auf **Überprüfen**.
    
    Nun sollten Meldungen angezeigt werden, aus denen hervorgeht, dass sowohl die Intranet- als auch die Internetkonfiguration überprüft wurde.
    
13. Klicken Sie auf der Seite **Installation ist abgeschlossen** auf **Beenden**.
    
Gehen Sie folgendermaßen vor, um zu zeigen, dass die Verbundauthentifizierung funktioniert:
  
1. Öffnen Sie eine neue private Instanz des Browsers auf Ihrem lokalen Computer, und wechseln Sie zur [https://portal.office.com](https://portal.office.com).
    
2. Geben Sie für die Anmeldeinformationen, **user1 @**\<die in Phase 1 erstellte Domäne >. 
    
    Wenn der Testdomäne **testlab.contoso.com**ist, würden Sie beispielsweise **user1@testlab.contoso.com**eingeben. Drücken Sie TAB oder zulassen Sie Office 365 automatisch Sie umleiten.
    
    Nun sollte eine Seite **die Verbindung ist nicht privat** angezeigt werden. Sie sehen dies, da Sie ein selbstsigniertes Zertifikat auf ADFS1 installiert, die dem Desktopcomputer nicht überprüfen kann. In einer Bereitstellung in der Produktion über die Verbundauthentifizierung verwenden Sie ein Zertifikat von einer vertrauenswürdigen Zertifizierungsstelle, und Ihre Benutzer nicht auf dieser Seite angezeigt.
    
3. Klicken Sie auf der Seite **Ihre Verbindung ist nicht privat** , klicken Sie auf **Erweitert**, und klicken Sie dann auf **fahren Sie mit \<Ihrer Verbunddienst FQDN >**. 
    
4. Melden Sie sich auf der Seite mit dem Namen Ihrer fiktiven Organisation mit den folgenden Informationen an:
    
  - **CORP\\User1** für den Namen
    
  - Das Kennwort für das Konto „User1“
    
    **Microsoft Office** -Startseite sollte angezeigt werden.
    
In diesem Verfahren wird veranschaulicht, dass der Test Office 365-Abonnement mit der Windows Azure AD "corp.contoso.com" Domäne gehostet auf DC1 im Verbund befindet. Hier werden die Grundlagen der Authentifizierungsprozess:
  
1. Wenn Sie die Verbunddomäne verwenden, die Sie in Phase 1 mit dem Anmeldekontonamen erstellt haben, wird Ihr Browser von Office 365 an den FQDN des Verbunddiensts und PROXY1 umgeleitet.
    
2. PROXY1 sendet dem lokalen Computer die Anmeldeseite des fiktiven Unternehmens.
    
3. Wenn Sie CORP senden\\User1 und das Kennwort zum PROXY1, es an weiterleitet ADFS1.
    
4. ADFS1 überprüft CORP\\User1 und das Kennwort mit DC1 und dem lokalen Computer ein Sicherheitstoken sendet.
    
5. Der lokale Computer sendet das Sicherheitstoken an Office 365.
    
6. Office 365 überprüft, dass das Sicherheitstoken von ADFS1 erstellt wurde und erlaubt den Zugriff.
    
Ihr Office 365-Testabonnement ist nun für die Verbundauthentifizierung konfiguriert. Sie können diese Entwicklungs-/Testumgebung für erweiterte Authentifizierungsszenarien verwenden.
  
## <a name="next-step"></a>Nächster Schritt

Wenn Sie sofort in der Produktion bereitstellen möchten, Verbundauthentifizierung hohe Verfügbarkeit für Office 365 in Azure, finden Sie unter [Deploy hohe Verfügbarkeit Verbundauthentifizierung für Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md).
  
## <a name="see-also"></a>Weitere Artikel

[Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz](cloud-adoption-test-lab-guides-tlgs.md)
  
[Basiskonfiguration der Entwicklungs-/Testumgebung](base-configuration-dev-test-environment.md)
  
[Office 365-Entwicklungs-/Testumgebung](office-365-dev-test-environment.md)
  
[Cloudakzeptanz und Hybridlösungen](cloud-adoption-and-hybrid-solutions.md)
  
[Bereitstellen der Verbundauthentifizierung mit Hochverfügbarkeit für Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)


