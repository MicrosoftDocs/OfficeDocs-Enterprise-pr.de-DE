---
title: Herunterladen und Ausführen des Office 365 IdFix-Tools
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
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
description: Hier erfahren Sie, wie Sie das Office 365 IdFix-Tool herunterladen und ausführen, um die Active Directory-Domänendienste (AD DS) vor dem Synchronisieren mit Office 365 zu bereinigen.
ms.openlocfilehash: 4a402cf245ebd20fbc5846908d521469ebfb90c1
ms.sourcegitcommit: 10ae1163f8443c53f19dfad6b7c2b2bb952bf759
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2019
ms.locfileid: "34490752"
---
# <a name="download-and-run-the-office-365-idfix-tool"></a>Herunterladen und Ausführen des Office 365 IdFix-Tools


IdFix identifiziert Fehler wie Duplikate und Formatierungsprobleme in Ihrer Active Directory-Domänendienste Domäne (AD DS), bevor Sie mit Office 365 synchronisieren. 
  
Um diese Aufgabe erfolgreich abzuschließen, sollten Sie mit Benutzer-, Gruppen-und Kontaktobjekten in AD DS komfortabel arbeiten.
  
Wenn Sie diese Aufgabe nicht ausführen können, gibt es einige andere Möglichkeiten. Diese Methoden sind möglicherweise einfacher, aber Sie können auch länger dauern oder andere Nachteile haben. Dies sind:
  
- **Ausführen der Verzeichnissynchronisierung ohne Ausführen von IdFix** 

  Sie können Ihr Verzeichnis ohne Verwendung des IdFix-Tools synchronisieren, dies wird jedoch nicht empfohlen. Das Beheben von Fehlern vor der Synchronisierung dauert kürzer und bietet häufig einen reibungslosen Übergang zur Cloud. 

- **Einen Berater einstellen** 

  Wenn Sie Expertenhilfe erhalten, können Sie Ihre Benutzer schnell in Betrieb nehmen und Ihr Verzeichnis synchronisieren. 
    
## <a name="what-you-need-to-run-idfix"></a>Was Sie zum Ausführen von IdFix benötigen

Am einfachsten können Sie IdFix auf einen Computer herunterladen, der mit Ihrer AD DS Domäne verbunden ist. Sie können es auf dem Domänencontroller ausführen, wenn Sie möchten, es ist jedoch nicht erforderlich.
  
### <a name="idfix-hardware-requirements"></a>IdFix-Hardwareanforderungen

Der Computer, auf dem Sie IdFix herunterladen, muss diese minimalen Hardwareanforderungen erfüllen:
  
- 4 GB RAM 
- 2 GB Speicherplatz auf der Festplatte
   
### <a name="idfix-software-requirements"></a>IdFix-Softwareanforderungen

Der Computer, auf dem Sie IdFix herunterladen, muss derselben AD DS Domäne hinzugefügt werden, aus der Sie Benutzer mit Office 365 synchronisieren möchten. 

Auf dem Computer muss auch .NET Framework 4,0 installiert sein. Wenn Sie Windows Server 2008 oder höher durchführen, ist die .NET Framework wahrscheinlich bereits installiert. Wenn dies nicht der Fall ist, können Sie [.NET 4,0 aus dem Download Center](https://go.microsoft.com/fwlink/p/?LinkId=400475) oder mit Windows Update herunterladen. 
  
### <a name="idfix-permissions-requirements"></a>IdFix-Berechtigungsanforderungen

Das Benutzerkonto, das Sie zum Ausführen von IdFix verwenden, muss über Lese-und Schreibzugriff auf die AD DS Domäne verfügen.
  
Wenn Sie nicht sicher sind, ob Ihr Benutzerkonto diese Anforderungen erfüllt, und Sie nicht sicher sind, wie Sie überprüfen möchten, können Sie IdFix trotzdem herunterladen und ausführen. Wenn Ihr Benutzerkonto nicht über die richtigen Berechtigungen verfügt, wird IdFix einfach einen Fehler angezeigt, wenn Sie versuchen, es auszuführen.
  
## <a name="download-and-extract-idfix"></a>Herunterladen und Extrahieren von IdFix

Befolgen Sie diese Anweisungen. 
  
1. Melden Sie sich bei dem Computer an, auf dem Sie das IdFix-Tool ausführen möchten.
    
2. Wechseln Sie zur Microsoft-Download Website für das [IdFix Dirsync-Tool zur Fehlerbehebung](https://go.microsoft.com/fwlink/?linkid=867219).
    
3. Laden Sie die ZIP-Datei herunter, und öffnen Sie Sie.
    
3. Wählen Sie im Fenster **IdFix** **extrahieren**aus, und extrahieren Sie dann **alle**. Standardmäßig wird IdFix in `C:\Users\<your user name>\Documents\IdFix`extrahiert. 
    
6. Wählen Sie **extrahieren**aus.

Diese Anweisungen wurden mit Internet Explorer auf einem Server mit Windows Server 2016 ausgeführt. Wenn Sie eine andere Version von Windows oder einen anderen Browser verwenden, sind Ihre Schritte möglicherweise unterschiedlich.
    
## <a name="run-the-idfix-tool"></a>Ausführen des IdFix-Tools

Nachdem Sie IdFix heruntergeladen und extrahiert haben, führen Sie ihn aus, um nach Problemen in Ihrer AD DS Domäne zu suchen.
  
1. Melden Sie sich bei dem Computer, auf dem Sie IdFix heruntergeladen haben, mit einem Konto an, das über Lese-/Schreibzugriff auf Ihre AD DS Domäne verfügt.
    
2. Wechseln Sie im Datei-Explorer zu dem Speicherort, an dem Sie IdFix extrahiert haben. Wenn Sie während der Extraktion den Standardordner ausgewählt haben, wechseln `C:\Users\<your user name>\Documents\IdFix`Sie zu. 
    
3. Doppelklicken Sie auf **IdFix. exe**. 
  
4. Standardmäßig verwendet IdFix den mehrmandantenfähigen Regelsatz, um die Einträge in Ihrem Verzeichnis zu testen. Dies ist der richtige Regelsatz für die meisten Office 365 Kunden. Wenn Sie jedoch ein Office 365 dedizierter oder internationaler Traffic in Arms Regulations (ITAR))-Kunde sind, können Sie IdFix so konfigurieren, dass stattdessen der dedizierte Regelsatz verwendet wird. Wenn Sie nicht sicher sind, welche Art von Kunde Sie haben, können Sie diesen Schritt gefahrlos überspringen. Klicken Sie auf das Zahnradsymbol in der Menüleiste, und wählen Sie dann **dediziert**aus, um den Regelsatz auf "dediziert" festzulegen.
    
5. Wählen Sie **Abfrage**aus.
    
    ![Wählen Sie Abfrage in IdFix aus.](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. Standardmäßig durchsucht IdFix das gesamte Verzeichnis nach Fehlern.
    
    Je nach der Größe Ihres Verzeichnisses kann das Ausführen der Abfrage eine Weile dauern. Sie können den Fortschritt am unteren Rand des Hauptfensters des Tools überwachen. Wenn Sie auf **Abbrechen**klicken, müssen Sie von Anfang an neu starten.
  
7. Nachdem IdFix die Abfrage abgeschlossen hat, können Sie Ihr Verzeichnis synchronisieren, wenn keine Fehler vorliegen. Wenn in Ihrem Verzeichnis Fehler vorliegen, wird empfohlen, dass Sie diese vor der Synchronisierung korrigieren. Weitere Informationen finden Sie unter [Prepare Directory attributes for Synchronization with Office 365](prepare-directory-attributes-for-synch-with-idfix.md) .
    
    Es ist zwar nicht zwingend erforderlich, die Fehler vor der Synchronisierung zu beheben, es wird jedoch dringend empfohlen, dass Sie mindestens alle von IdFix zurückgegebenen Fehler überprüfen.
    
    Jeder Fehler wird in einer separaten Zeile im Hauptfenster des Tools angezeigt. 
    
8. Wenn Sie mit der vorgeschlagenen Änderung in der Spalte **Aktualisieren** einverstanden sind, wählen Sie in der Spalte **Aktion** aus, was Sie von IdFix ausführen möchten, um die Änderung zu implementieren, und klicken Sie dann auf über **nehmen**. Wenn Sie auf über **nehmen**klicken, nimmt das Tool die Änderungen im Verzeichnis vor.
    
    Sie müssen nach jeder Aktualisierung nicht auf **anwenden** klicken. Stattdessen können Sie mehrere Fehler beheben, bevor Sie auf über **nehmen** klicken, und IdFix ändert alle gleichzeitig. Sie können die Fehler nach Fehlertyp sortieren, indem Sie oben in der Spalte, in der die Fehlertypen aufgeführt werden, auf **Fehler** klicken. 
    
    Eine Strategie besteht darin, alle Fehler desselben Typs zu beheben. beheben Sie beispielsweise zuerst alle Duplikate, und wenden Sie Sie an. Korrigieren Sie als nächstes die Zeichenformat Fehler usw. Jedes Mal, wenn Sie die Änderungen anwenden, erstellt das IdFix-Tool eine separate Protokolldatei, mit der Sie Ihre Änderungen rückgängig machen können, falls Sie einen Fehler machen. Das [Transaktionsprotokoll](idfix-transaction-log.md) wird in dem Ordner gespeichert, in dem Sie IdFix extrahiert haben, was _C:\Users\<Ihrem Benutzernamen> \documents\idfix_ Standardmäßig entspricht. 
    
    ![Beheben von Fehlern in IdFix.](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. Nachdem Sie alle Änderungen am Verzeichnis vorgenommen haben, führen Sie IdFix erneut aus, um sicherzustellen, dass die von Ihnen vorgenommenen Korrekturen keine neuen Fehler verursachen. Sie können diese Schritte so oft wie nötig wiederholen. Es empfiehlt sich, den Prozess einige Male vor dem Synchronisieren durchzugehen.
    
## <a name="additional-resources-on-idfix"></a>Zusätzliche Ressourcen auf IdFix 

- [Ausgeschlossene und unterstützte Objekte und Attribute für IdFix](idfix-excluded-and-supported-objects-and-attributes.md)  
- [Office 365 IdFix-Transaktionsprotokoll](idfix-transaction-log.md)
    
## <a name="video-training"></a>Videoschulung

Weitere Informationen finden Sie in der Lektion [Installieren und Verwenden des IdFix-Tools](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), das Ihnen von LinkedIn Learning zur Verfügung gestellt wird.
  

