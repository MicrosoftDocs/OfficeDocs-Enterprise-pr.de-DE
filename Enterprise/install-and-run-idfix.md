---
title: Installieren und Ausführen des Office 365 IdFix-Tools
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: get-started-article
f1_keywords:
- O365E_HRCSetupAADConnectIDFixLM617036
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: Installieren und Ausführen des Office 365-IdFix-Tools zum Bereinigen Ihres Active Directory, bevor Sie es mit Office 365 synchronisieren.
ms.openlocfilehash: a35b2a476f2b30eccc955b980eda6315b146af27
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2019
ms.locfileid: "33488001"
---
# <a name="install-and-run-the-office-365-idfix-tool"></a>Installieren und Ausführen des Office 365 IdFix-Tools

IdFix identifiziert Fehler wie Duplikate und Formatierungsprobleme in Ihrem Verzeichnis, bevor Sie mit Office 365 synchronisieren. 
  
Damit Sie diese Aufgabe erfolgreich abschließen können, sollten Sie sich mit Benutzer-, Gruppen-und Kontaktobjekten in Active Directory vertraut machen.
  
Wenn Sie diese Aufgabe nicht abschließen können, gibt es einige andere Möglichkeiten. Diese Methoden sind möglicherweise einfacher, aber Sie können auch länger dauern oder andere Nachteile haben. Dies sind:
  
- **Führen Sie die Verzeichnissynchronisierung ohne Ausführen von IdFix aus.** Sie können Ihr Verzeichnis synchronisieren, ohne das IdFix-Tool auszuführen, es wird jedoch nicht empfohlen. Das Beheben von Fehlern vor der Synchronisierung dauert schneller und bietet häufig einen reibungsloseren Übergang zur Cloud. 
- **Mieten Sie einen Berater.** Wenn Sie Experten helfen, können Sie Ihre Benutzer schnell einrichten, und Ihr Verzeichnis wird synchronisiert. 
    
## <a name="what-you-need-to-run-idfix"></a>Was Sie zum Ausführen von IdFix benötigen

Am einfachsten können Sie IdFix auf einem Computer installieren, der mit Ihrer Domäne verbunden ist. Sie können es auf dem Domänencontroller ausführen, aber es ist nicht erforderlich.
  
### <a name="idfix-hardware-requirements"></a>IdFix-Hardwareanforderungen

Der Computer, auf dem Sie IdFix installieren, muss diese minimalen Hardwareanforderungen erfüllen:
  
- 4 GB RAM 
- 2 GB Festplattenspeicherplatz
    
### <a name="idfix-software-requirements"></a>IdFix-Softwareanforderungen

Der Computer, auf dem Sie IdFix installieren, muss derselben Active Directory-Domäne hinzugefügt werden, von der Sie Benutzer mit Office 365 synchronisieren möchten. Auf dem Computer muss .NET Framework 4,0 installiert sein. 
  
Wenn Sie Windows Server 2008 oder Windows Server 2012, ist .NET Framework wahrscheinlich bereits installiert. Ist dies nicht der Fall, können Sie [.net 4,0 aus dem Download Center](https://go.microsoft.com/fwlink/p/?LinkId=400475) oder über Windows Update herunterladen. 
  
### <a name="idfix-permissions-requirements"></a>IdFix-Berechtigungsanforderungen

Das Benutzerkonto, mit dem Sie IdFix ausführen, muss Lese-/Schreibzugriff auf das Verzeichnis haben.
  
Wenn Sie nicht sicher sind, ob Ihr Benutzerkonto diese Anforderungen erfüllt, und Sie nicht sicher sind, wie Sie überprüfen, können Sie IdFix installieren und ausführen. Wenn Ihr Benutzerkonto nicht über die richtigen Berechtigungen verfügt, wird bei der Ausführung von IdFix nur ein Fehler angezeigt.
  
## <a name="install-idfix"></a>Installieren von IdFix

Zum Installieren von IdFix können Sie **IdFix. exe**herunterladen und entpacken: 
  
1. Melden Sie sich an dem Computer an, auf dem Sie das IdFix-Tool installieren möchten.
    
2. Wechseln Sie zur Microsoft-Download Website für das [IdFix Dirsync Error Remediation Tool](https://go.microsoft.com/fwlink/?linkid=867219).
    
3. Klicken Sie auf **Herunterladen**.
    
4. Wenn Sie dazu aufgefordert werden, wählen Sie **Ausführen**aus.
    
5. Geben Sie im Dialogfeld **WinZip Self-Extractor** im Textfeld **unzip to Folder** den Speicherort ein, an dem Sie das IdFix-Tool installieren möchten, oder navigieren Sie zu diesem. Standardmäßig wird IdFix in `C:\Deployment Tools\`installiert. 
    
6. Wählen Sie **unzip**aus.
    
## <a name="run-the-idfix-tool"></a>Ausführen des IdFix-Tools

Führen Sie nach der Installation von IdFix das Tool aus, um nach Problemen in Ihrem Verzeichnis zu suchen:
  
1. Melden Sie sich mit einem Konto mit Lese-/Schreibzugriff auf das Verzeichnis an dem Computer an, auf dem Sie IdFix installiert haben.
    
2. Wechseln Sie im Datei-Explorer zu dem Speicherort, an dem Sie IdFix installiert haben. Wenn Sie während der Installation den Standardordner ausgewählt haben, `C:\Deployment Tools\IdFix`wechseln Sie zu.
    
3. Doppelklicken Sie auf **IdFix. exe**. 
    
    ![Wählen Sie die Datei IdFix. exe aus.](media/a9387bbc-991f-41c2-a500-45e3ce574285.JPG)
  
4. Standardmäßig verwendet IdFix den mandantenfähigen Regelsatz, um die Einträge in Ihrem Verzeichnis zu testen. Dies ist der richtige Regelsatz für die meisten Office 365-Kunden. Wenn Sie jedoch ein Office 365 Dedicated-oder ITAR (International Traffic in Arms Regulations)-Kunde sind, können Sie IdFix so konfigurieren, dass stattdessen der dedizierte Regelsatz verwendet wird. Wenn Sie nicht sicher sind, welche Art von Kunden Sie sind, können Sie diesen Schritt gefahrlos überspringen. Klicken Sie auf das Zahnradsymbol in der Menüleiste, und wählen Sie dann **dediziert**aus, um den Regelsatz auf Dedicated festzulegen.
    
5. Wählen Sie **Query**aus.
    
    ![Wählen Sie Query in IdFix aus.](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. Standardmäßig durchsucht IdFix das gesamte Verzeichnis auf Fehler.
    
    Abhängig von der Größe des Verzeichnisses kann das Ausführen der Abfrage eine Weile dauern. Sie können den Fortschritt am unteren Rand des Hauptfensters des Tools ansehen. Wenn Sie auf **Abbrechen**klicken, müssen Sie von vorn beginnen.
    
    ![IdFix-Abfrage und Fehleranzahl.](media/da0198a0-7d4d-4afe-a256-e82f1330ada5.JPG)
  
7. Nachdem IdFix die Abfrage abgeschlossen hat, können Sie mit der Synchronisierung des Verzeichnisses fortfahren, falls keine Fehler vorliegen. Wenn Ihr Verzeichnis fehlerhaft ist, sollten Sie diese vor der Synchronisierung korrigieren. Wenn Sie genauere Informationen zu Fehlertypen und Empfehlungen zur bestmöglichen Möglichkeit zum Beheben von Fehlern benötigen, lesen Sie die Links am Ende dieses Themas. 
    
    Es ist zwar nicht zwingend erforderlich, die Fehler vor der Synchronisierung zu beheben, es wird jedoch dringend empfohlen, dass Sie zumindest alle von IdFix zurückgegebenen Fehler überarbeiten.
    
    Jeder Fehler wird in einer separaten Zeile im Hauptfenster des Tools angezeigt. 
    
8. Wenn Sie der vorgeschlagenen Änderung in der Spalte **Update** zustimmen, wählen Sie in der Spalte **Aktion** aus, was IdFix tun soll, um die Änderung zu implementieren, und klicken Sie dann auf über **nehmen**. Wenn Sie auf über **nehmen**klicken, nimmt das Tool die Änderungen im Verzeichnis vor.
    
    Sie müssen nach jeder Aktualisierung nicht auf **anwenden** klicken. Stattdessen können Sie mehrere Fehler beheben, bevor Sie auf **anwenden** klicken, und IdFix wird Sie alle gleichzeitig ändern. Sie können die Fehler nach Fehlertyp sortieren, indem Sie oben in der Spalte, in der die Fehlertypen aufgelistet werden, auf **Fehler** klicken. 
    
    Eine Strategie besteht darin, alle Fehler des gleichen Typs zu beheben. beheben Sie beispielsweise zuerst alle Duplikate, und wenden Sie Sie an. Korrigieren Sie als nächstes die Zeichenformat Fehler usw. Jedes Mal, wenn Sie die Änderungen übernehmen, erstellt das IdFix-Tool eine separate Protokolldatei, mit der Sie die Änderungen rückgängig machen können, falls Sie einen Fehler machen. Das [Transaktionsprotokoll](idfix-transaction-log.md) wird in dem Ordner gespeichert, in dem Sie IdFix installiert haben.  _C:\Deployment Tools\IdFix_ standardmäßig. 
    
    ![Beheben von Fehlern in IdFix.](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. Nachdem alle Änderungen am Verzeichnis vorgenommen wurden, führen Sie IdFix erneut aus, um sicherzustellen, dass die von Ihnen vorgenommenen Korrekturen keine neuen Fehler einführten. Sie können diese Schritte beliebig oft wiederholen. Es empfiehlt sich, den Prozess einige Male zu durchlaufen, bevor Sie synchronisieren.
    
## <a name="i-want-to-refine-my-search-or-dig-deeper-into-the-errors-what-else-can-i-do-with-idfix"></a>Ich möchte meine Suche verfeinern oder tiefer in die Fehler eingraben, was kann ich sonst noch mit IdFix tun?

Weitere ausführliche Informationen finden Sie in den folgenden Themen:
  
- [Vorbereiten von Verzeichnisattributen für die Synchronisierung mit Office 365 mithilfe des IdFix-Tools](prepare-directory-attributes-for-synch-with-idfix.md) . Wenn Sie das Tool installiert haben, wechseln Sie zu diesem Thema, um detailliertere Anweisungen zum Ausführen des Tools, häufige Fehler, die auftreten werden, Empfohlene Korrekturen, Beispiele und bewährte Methoden für die Vorgehensweise bei einer hohen Anzahl von Fehlern. 
- [Referenz: Ausgeschlossene und unterstützte Objekte und Attribute für IdFix](idfix-excluded-and-supported-objects-and-attributes.md)  
- [Referenz: Office 365 IdFix-Transaktionsprotokoll](idfix-transaction-log.md)
    
## <a name="video-training"></a>Videoschulung

Weitere Informationen finden Sie in der Lektion [Installieren und Verwenden des IDFix-Tools](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), die Ihnen von LinkedIn Learning zur Verfügung gestellt wird.
  

