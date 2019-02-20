---
title: Vorbereiten von Verzeichnisattributen für die Synchronisierung mit Office 365 mithilfe des IdFix-Tools
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: 497593cf-24c6-491c-940b-7c86dcde9de0
description: Enthält Anweisungen zur Verwendung von IdFix zum Vorbereiten und Bereinigen des lokalen Verzeichnisses vor dem Synchronisieren mit Office 365.
ms.openlocfilehash: cdfee8178f731d20c799f550d1dacb0a04a72cae
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085094"
---
# <a name="prepare-directory-attributes-for-synchronization-with-office-365-by-using-the-idfix-tool"></a>Vorbereiten von Verzeichnisattributen für die Synchronisierung mit Office 365 mithilfe des IdFix-Tools
Dieses Thema enthält detaillierte Anweisungen zum Ausführen des IdFix-Tools, einige häufige Fehler, die auftreten können, Vorschläge zu Behebungen, Beispielen und bewährten Methoden für die Vorgehensweise bei einer hohen Anzahl von Fehlern.
  
## <a name="fixing-errors-in-your-directory-by-using-the-idfix-gui"></a>Beheben von Fehlern in Ihrem Verzeichnis mithilfe der IdFix-GUI
[Führen Sie das Office 365 IdFix-Tool](install-and-run-idfix.md) aus, um nach Problemen in Ihrem Verzeichnis zu suchen, und beheben Sie dann die Fehler in der GUI, wie in diesem Thema beschrieben. Wenn eine leere Tabelle vom Tool zurückgegeben wird, wurden keine Fehler ermittelt. Wenn in Ihrem Verzeichnis viele Probleme auftreten, kann es überwältigend sein, wenn das Tool die Fehler zurückgibt. Eine Möglichkeit, dies zu bewältigen, besteht darin, alle Fehler eines Typs zuerst zu beheben und dann zum nächsten Typ zu wechseln. 
  
1. Sehen Sie sich die Empfehlungen durch IdFix an, bevor Sie Änderungen vornehmen.
    
2. Sehen Sie die Liste der Fehler an, die IdFix zurückgegeben hat. Sie können die Fehler nach Fehlertyp sortieren, indem Sie oben in der Spalte auf **ERROR** klicken, in der die Fehlertypen aufgelistet werden. Wenn mehr als ein Fehler mit einem einzelnen Attribut verknüpft ist, werden die Fehler in einer Zeile kombiniert. Nach Möglichkeit stellt IdFix eine Empfehlung für eine Fehlerbehebung in der Spalte **UPDATE** dar Die Fehlerbehebung basiert auf einer Prüfung von anderen mit einem Objekt verknüpften Attributen. Obwohl diese in der Regel besser ist als das, was bereits im Verzeichnis vorhanden ist, können nur Sie entscheiden, was wirklich richtig ist. 
    
3. Wenn IdFix einen Vorschlag zur Behebung eines Duplizierungs Fehlers hat, wird das Update durch eines der drei Flags am Anfang des Werts in der **Update** -Spalte identifiziert, beispielsweise `[E]john.doe@contoso.com`. Wenn Sie den Vorschlag akzeptieren, wird das Flag nicht in das Verzeichnis eingefügt, wenn Sie die Änderung anwenden. Nur der Wert, der dem Vorschlags Kennzeichen folgt, wird angewendet, Beispiels `john.doe@contoso.com`Weise. Wenn Sie den Vorschlag annehmen möchten, wählen Sie die entsprechende Aktion in der Spalte **Aktion** aus. Die Flags zeigen Aktionen wie folgt an: 
    
 - **[C]** Empfohlene Aktion **COMPLETE**. Der Wert muss nicht bearbeitet werden.
    
 - **[E]** Empfohlene Aktion **EDIT**. Der Wert sollte geändert werden, um einen Konflikt mit einem anderen Wert im Verzeichnis zu vermeiden.
    
 - **[R]** Empfohlene Aktion **REMOVE**. Der Wert ist ein SMTP-Proxy in einem nicht meldungsfähigen Objekt und kann wahrscheinlich sicher entfernt werden.
    
4. Nachdem Sie die Fehler gelesen und verstanden haben, aktualisieren Sie den Eintrag in der Spalte **Aktualisieren** mit Ihren Änderungen, und wählen Sie dann in der Spalte **Aktion** aus, was IdFix für die Implementierung der Änderung tun soll. Zwei Benutzer haben beispielsweise eine `proxyAddress` als Duplikat identifiziert. Nur ein Benutzer kann die für `proxyAddress` die e-Mail-Übermittlung verwenden. Um dies zu beheben, markieren Sie die Spalte **Aktion** für den Benutzer mit dem richtigen Wert **abgeschlossen** , und markieren **Sie** die Spalte **Aktion** für den anderen Benutzer. Dadurch wird das `proxyAddress` Attribut des Benutzers entfernt, zu dem `proxyAddress` dieser nicht gehört, und es wird keine Änderung an dem Benutzer vorgenommen `proxyAddress` , für den dies richtig ist.
    
## <a name="common-errors-and-fixes-detected-by-idfix"></a>Durch IdFix erkannte häufige Fehler und Fehlerbehebungen
In der folgenden Tabelle werden die durch IdFix erkannten Fehler beschrieben, und es werden die am häufigsten empfohlenen Fehlerbehebungen des Tools bereitgestellt. Zudem erfolgen in manchen Fällen Lösungsbeispiele.

|**Fehler**|**Fehlertypbeschreibung**|**Empfohlene Fehlerbehebung**|**Beispiel**|
|:-----|:-----|:-----|:-----|
|**character** | Unzulässige Zeichen. Der Wert enthält ein Zeichen, das ungültig ist. | Die in der Spalte **UPDATE** angezeigte empfohlene Fehlerbehebung für den Fehler zeigt den Wert mit dem ungültigen entfernten Zeichen.  <br/> | Ein abschließender Leerraum am Ende einer gültigen e-Mail-Adresse ist ein ungültiges Zeichen, beispielsweise:  <br/> " `user@contoso.com` "  <br/> Ein führender Leerraum am Anfang einer gültigen e-Mail-Adresse ist ein ungültiges Zeichen, beispielsweise:  <br/> " ` user@contoso.com `"  <br/>  Das `ú` Zeichen ist ein ungültiges Zeichen. |
|**duplicate** | Doppelter Eintrag. Der Wert verfügt über ein Duplikat im Bereich der Abfrage. Alle doppelten Werte werden als Fehler angezeigt. | Bearbeiten oder entfernen Sie Werte zum Beseitigen von Dopplungen. Das Tool stellt keine empfohlene Fehlerbehebung für Duplikate bereit. Vielmehr müssen Sie auswählen, welches der zwei oder mehr Duplikate richtig ist, und Sie müssen das Duplikat bzw. die Duplikate löschen. ||
|**format** | Formatierungsfehler. Der Wert verletzt die Formatierungsanforderungen für die Attributverwendung. | Das empfohlene "Update" zeigt den Wert mit den entfernten ungültigen Zeichen. Wenn keine ungültigen Zeichen vorhanden sind, sind "Update" und "Value" gleich. Es bleibt Ihnen überlassen zu bestimmen, was Sie wirklich im "Update" einbeziehen möchte. Das Tool stellt keine empfohlene Fehlerbehebung für alle Formatierungsfehler bereit. | Beispielsweise müssen SMTP-Adressen mit RFC 2822 und mailNickname nicht mit einem Punkt beginnen oder enden. Weitere Informationen zu den Formatanforderungen für Verzeichnisattribute finden Sie unter "Directory-Objekt und-Attribut Vorbereitung" in [Vorbereiten der Bereitstellung von Benutzern über die Verzeichnissynchronisierung in Office 365](prepare-for-directory-synchronization.md). |
|topleveldomain  <br/> |Domäne der obersten Ebene. Dies gilt für Werte, die der [RFC 2822](https://go.microsoft.com/fwlink/p/?LinkId=401464) -Formatierung unterliegen. Wenn die Domäne der obersten Ebene nicht im Internet routingfähig ist, wird diese als Fehler identifiziert. Beispiel: eine SMTP-Adresse, die in. local endet, ist nicht im Internet routingfähig und würde diesen Fehler verursachen. |Ändern Sie den Wert in eine im `.com` Internet Routingfähige Domäne `.net`wie oder. | Wechseln `myaddress@fourthcoffee.local` Sie `fourthcoffee.com` zu oder in eine andere, im Internet Routingfähige Domäne.  <br/> Anweisungen hierzu finden Sie unter [Vorbereiten einer nicht routingfähigen Domäne (beispielsweise. Local Domain) für die Verzeichnissynchronisierung](prepare-a-non-routable-domain-for-directory-synchronization.md). |
|**domainpart** | Domänenanteilfehler. Dies gilt für Werte gemäß der RFC 2822-Formatierung. Wenn die Domänenteilmenge des Werts ungültig ist und RFC 2822 nicht erfüllt, wird dies generiert. | Ändern Sie den Wert in einen, der RFC 2822 entspricht. Stellen Sie beispielsweise sicher, dass Sie keine Leerzeichen oder ungültigen Buchstaben enthält. | Wechseln `myaddress@fourth coffee.com` Sie `myaddress@fourthcoffee.com`zu. |
|**domainpart_localpart** | Fehler beim lokalen Teil. Dies gilt für Werte gemäß der RFC 2822-Formatierung. Wenn der lokale Teil des Werts ungültig ist und RFC 2822 nicht erfüllt, wird dies generiert. |Ändern Sie den Wert in einen, der RFC 2822 entspricht. Stellen Sie beispielsweise sicher, dass Sie keine Leerzeichen oder ungültigen Buchstaben enthält. |Wechseln `my"work"address@fourthcoffee.com` Sie `myworkaddress@fourthcoffee.com`zu. |
|**length** | Fehler bei der Länge. Der Wert überschreitet die Längenbegrenzung für das Attribut. Dies tritt am häufigsten auf, wenn das Verzeichnisschema geändert wurde.  | Das von IdFix empfohlene Update schneidet den Wert auf eine zulässige Länge zu.  <br/> Beachten Sie, dass dies zu unerwünschten Ergebnissen führen kann. Sie sollten die empfohlene Fehlerbehebung überprüfen und ggf. ändern, bevor Sie auf **Übernehmen** klicken. ||
|**blank**  | Leer oder null-Fehler. Der Wert verletzt die null-Beschränkung für zu synchronisierende Attribute. Nur wenige Attribute müssen einen Wert enthalten. | Das empfohlene Update verwendet nach Möglichkeit andere Attributwerte, um einen wahrscheinlichen Ersatz zu generieren. ||
|**mailmatch** | Dies gilt nur für Office 365 dediziert. Der Wert stimmt nicht mit dem Mail-Attribut überein. | Das vorgeschlagene Update ist der e-Mail-Attributwert, der mit "SMTP:" vorangestellt wird. ||
    
## <a name="operations-you-can-perform-by-using-idfix"></a>Mithilfe von IdFix ausführbare Vorgänge
Zum Beheben eines Fehlers wählen Sie in der Dropdownliste **Aktion** eine Option aus. In der folgenden Tabelle werden die **Aktions** Vorgänge beschrieben, die Sie mit dem IdFix-Tool für Attribute ausführen können. Wenn Sie die Spalte **Aktion** leer lassen, führt das IdFix-Tool keine Aktion für diesen bestimmten Fehler im Verzeichnis aus. 

|**Aktion**|**Aktionsbeschreibung**|**Beispiel**|
|:-----|:-----|:-----|
|**COMPLETE** | Der ursprüngliche Wert ist akzeptabel und sollte nicht geändert werden, obwohl er als ein Fehler identifiziert wurde. | Zwei Benutzer haben eine proxyAddress als Duplikat identifiziert. Nur ein Benutzer kann den Wert für die E-Mail-Übermittlung verwenden. Markieren Sie den Benutzer mit dem richtigen Wert als **COMPLETE**. |
|**Entfernen** | Der Attributwert wird aus dem Source-Objekt gelöscht. Bei einem mehrwertigen Attribut wird beispielsweise `proxyAddresses`nur der angezeigte Einzelwert gelöscht. | Zwei Benutzer haben eine proxyAddress als Duplikat identifiziert. Nur ein Benutzer kann den Wert für die E-Mail-Übermittlung verwenden. Markieren Sie den Benutzer mit dem doppelten Wert als **REMOVE**. |
|**Bearbeiten** | Die Informationen in der Spalte **Update** werden verwendet, um den Attributwert zu ändern. Wenn von IdFix ein gültiger **Aktualisierungs** Wert vorgeschlagen wurde, wählen Sie in der Spalte **Aktion** die Option **Bearbeiten** aus, und fahren Sie mit dem nächsten Fehler fort. Wenn Sie den Vorschlag nicht mögen, geben Sie in der Spalte **Update** einen neuen ein, und klicken Sie dann in der Spalte **Aktion** auf **Bearbeiten**. ||
|**UNDO** | Diese Option ist nur verfügbar, wenn Sie die Wiederherstellung mithilfe eines Transaktionsprotokolls vorgenommen haben. Bei Wahl von **UNDO** wird der Attributwert auf den Originalwert zurückgesetzt. ||
|**FAIL** | Dieser Wert wird nur zurückgegeben, wenn ein **Aktualisierungs** Wert einen unbekannten Konflikt mit AD DS-Regeln aufweist. In diesem Fall können Sie den Wert in der Spalte **Update** erneut bearbeiten, wenn Sie wissen, was der Fehlschlag ist. Möglicherweise müssen Sie die Werte im Objekt mithilfe von ADSI-Bearbeitung analysieren. Weitere Informationen finden Sie unter [ADSI-Bearbeitung (AdsiEdit. msc)](https://go.microsoft.com/fwlink/p/?LinkId=401170). ||

Klicken Sie nach der Auswahl einer **ACTION** für einen Fehler oder einen Fehlerstapel auf **Übernehmen**. Wenn Sie auf **Übernehmen** klicken, nimmt das Tool die Änderungen im Verzeichnis vor. Sie können Fehlerbehebungen für mehrere Fehler bereitstellen, bevor Sie auf **Übernehmen** klicken, und IdFix ändert sie alle gleichzeitig.

Führen Sie IdFix erneut aus, um sicherzustellen, dass die von Ihnen vorgenommenen Korrekturen keine neuen Fehler einFührten. Sie können diese Schritte beliebig oft wiederholen. Es empfiehlt sich, den Prozess einige Male zu durchlaufen, bevor Sie synchronisieren.
    
## <a name="changing-the-rule-set-used-by-idfix"></a>Ändern des durch IdFix verwendeten Regelsatzes
Standardmäßig verwendet IdFix den mandantenfähigen Regelsatz, um die Einträge in Ihrem Verzeichnis zu testen. Dies ist der richtige Regelsatz für die meisten Office 365 =-Kunden. Wenn Sie jedoch ein Office 365 Dedicated-oder ITAR (International Traffic in Arms Regulations)-Kunde sind, können Sie IdFix so konfigurieren, dass stattdessen der dedizierte Regelsatz verwendet wird. Wenn Sie nicht sicher sind, welche Art von Kunden Sie sind, können Sie diesen Schritt gefahrlos überspringen. Klicken Sie auf das Zahnradsymbol in der Menüleiste, und klicken Sie dann auf **dediziert**, um den Regelsatz auf Dedicated festzulegen.
  
## <a name="changing-the-scope-of-the-search-used-by-idfix"></a>Ändern des durch IdFix verwendeten Suchbereichs
IdFix überprüft standardmäßig das gesamte Verzeichnis. Bei Bedarf können Sie das Tool so konfigurieren, dass es stattdessen nach einer bestimmten Unterstruktur sucht. Klicken Sie dafür auf der Menüleiste auf das Symbol zum Filtern, und geben Sie eine gültige Unterstruktur ein.
  
## <a name="rolling-back-your-changes-by-using-the-idfix-gui"></a>Rollback der Änderungen mithilfe IdFix-GUI
Jedes Mal, wenn Sie auf **anwenden** klicken, um Änderungen zu übernehmen, erstellt das IdFix-Tool eine separate Datei mit dem Namen Transaktionslog, in der die soeben vorgenommenen Änderungen aufgelistet werden. Sie können das Transaktionsprotokoll verwenden, um nur die Änderungen zurückzusetzen, die sich im neuesten Protokoll befinden, falls Sie einen Fehler machen. Wenn Sie beim Aktualisieren einen Fehler machen, können Sie die zuletzt angewendeten Änderungen rückgängig machen, indem Sie auf **Rückgängig**klicken. Wenn Sie auf **Rückgängig**klicken, verwendet IdFix das Transaktionsprotokoll, um nur die Änderungen zurückzusetzen, die sich im letzten Transaktionsprotokoll befinden. Weitere Informationen zur Verwendung des Transaktionsprotokolls finden Sie unter [Reference: Office 365 IdFix Transaction Log](idfix-transaction-log.md).