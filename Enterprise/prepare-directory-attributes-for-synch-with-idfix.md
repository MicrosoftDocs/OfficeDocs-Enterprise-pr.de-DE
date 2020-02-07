---
title: Vorbereiten von Verzeichnisattributen für die Synchronisierung mit Office 365 mithilfe des IdFix-Tools
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: 497593cf-24c6-491c-940b-7c86dcde9de0
description: Enthält Anweisungen zur Verwendung von IdFix zum Vorbereiten und Bereinigen des lokalen Verzeichnisses vor dem Synchronisieren mit Office 365.
ms.openlocfilehash: 97c13a2fd49cea0af63439d6fe6106e8d8996d97
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844086"
---
# <a name="prepare-directory-attributes-for-synchronization-with-office-365-by-using-the-idfix-tool"></a>Vorbereiten von Verzeichnisattributen für die Synchronisierung mit Office 365 mithilfe des IdFix-Tools

*Dieser Artikel gilt sowohl für Office 365 Enterprise als auch Microsoft 365 Enterprise*.

Dieses Thema enthält detaillierte Anweisungen zum Ausführen des IdFix-Tools, einige häufige Fehler, die auftreten können, vorgeschlagene Korrekturen, Beispiele und bewährte Methoden für Vorgehensweisen bei einer großen Anzahl von Fehlern.
  
## <a name="fixing-errors-in-your-directory-by-using-the-idfix-gui"></a>Beheben von Fehlern in Ihrem Verzeichnis mithilfe der IdFix-GUI

[Führen Sie das Office 365 IdFix-Tool](install-and-run-idfix.md) aus, um nach Problemen in Ihrem Verzeichnis zu suchen und dann die Fehler in der GUI zu beheben, wie in diesem Thema beschrieben. Wenn das Tool eine leere Tabelle zurückgibt, wurden keine Fehler ermittelt. Wenn es viele Probleme in Ihrem Verzeichnis gibt, kann es überwältigend sein, wenn das Tool die Fehler zurückgibt. Eine Möglichkeit, dies zu bewältigen, ist, alle Fehler eines Typs zuerst zu beheben und dann zum nächsten Typ zu übergehen. 
  
1. Bevor Sie mit der Durchführung von Änderungen beginnen, sehen Sie sich die von IdFix vorgestellten Empfehlungen an.
    
2. Überblicken Sie die Liste der Fehler, die von IdFix zurückgegeben wurden. Sie können die Fehler nach Fehlertyp sortieren, indem Sie oben in der Spalte, in der die Fehlertypen aufgelistet werden, auf **ERROR** klicken. Wenn mehreren Fehlern ein einzelnes Attribut zugeordnet ist, werden die Fehler zu einer Zeile zusammengefasst. Wenn möglich, stellt IdFix eine Empfehlung für eine Korrektur in der Spalte **Aktualisieren** dar. Das Update basiert auf einer Überprüfung anderer Attribute, die einem Objekt zugeordnet sind. Diese sind zwar normalerweise besser als die, die sich bereits im Verzeichnis befinden, aber nur Sie können entscheiden, was wirklich richtig ist. 
    
3. Wenn IdFix einen Vorschlag für eine Korrektur für einen Duplizierungs Fehler enthält, wird der Fix durch eine von drei Flags am Anfang des Werts in der Spalte **Update** identifiziert, beispielsweise `[E]john.doe@contoso.com`. Wenn Sie den Vorschlag akzeptieren, wird das Flag beim Anwenden der Änderung nicht in das Verzeichnis eingefügt. Nur der Wert, der dem Suggestion-Flag folgt, wird angewendet, `john.doe@contoso.com`beispielsweise. Wenn Sie den Vorschlag akzeptieren möchten, wählen Sie die entsprechende Aktion in der Spalte **Aktion** aus. Die Flags zeigen Aktionen wie folgt an: 
    
 - **[C]** vorgeschlagene Aktion **abgeschlossen**. Der Wert muss nicht bearbeitet werden.
    
 - **[E]** vorgeschlagene Aktion **Bearbeiten**. Der Wert sollte geändert werden, um einen Konflikt mit einem anderen Wert im Verzeichnis zu vermeiden.
    
 - **[R]** vorgeschlagene Aktion **Entfernen**. Der Wert ist ein SMTP-Proxy für ein Objekt, das nicht für e-Mail-aktiviert ist und möglicherweise problemlos entfernt werden kann.
    
4. Nachdem Sie die Fehler gelesen und verstanden haben, aktualisieren Sie den Eintrag in der Spalte **Update** mit Ihren Änderungen, und wählen Sie dann in der Spalte **Aktion** aus, was Sie von IdFix ausführen möchten, um die Änderung zu implementieren. Beispielsweise kann es sein, dass zwei `proxyAddress` Benutzer als Duplikate identifiziert wurden. Nur ein Benutzer kann die `proxyAddress` for-e-Mail-Zustellung verwenden. Um dies zu beheben, markieren Sie die **Aktions** Spalte für den Benutzer mit dem korrekten Wert und markieren Sie **die Spalte** **Aktion** **Entfernen** für den anderen Benutzer. Dadurch wird das `proxyAddress` Attribut des Benutzers entfernt, dem dieser `proxyAddress` nicht angehört, und es nimmt keine Änderung an dem Benutzer vor `proxyAddress` , für den dies richtig ist.
    
## <a name="common-errors-and-fixes-detected-by-idfix"></a>Häufige Fehler und Korrekturen, die von IdFix erkannt wurden
In der folgenden Tabelle werden die von IdFix erkannten Fehler beschrieben, die am häufigsten empfohlenen Korrekturen des Tools bereitgestellt und in einigen Fällen Beispiele für die Problembehebung bereitgestellt.

|**Fehler**|**Beschreibung des Fehlertyps**|**Vorgeschlagene Korrektur**|**Beispiel**|
|:-----|:-----|:-----|:-----|
|**Zeichen** | Ungültige Zeichen. Der Wert enthält ein ungültiges Zeichen. | Der vorgeschlagene Fix für den Fehler, der in der Spalte **Update** angezeigt wird, zeigt den Wert mit dem ungültigen Zeichen entfernt.  <br/> | Ein nach folgender Leerzeichen am Ende einer gültigen e-Mail-Adresse ist ein ungültiges Zeichen, beispielsweise:  <br/> " `user@contoso.com` "  <br/> Ein führender Leerraum am Anfang einer gültigen e-Mail-Adresse ist ein ungültiges Zeichen, beispielsweise:  <br/> " ` user@contoso.com `"  <br/>  Das `ú` Zeichen ist ein ungültiges Zeichen. |
|**doppelte** | Doppelter Eintrag. Der Wert weist ein Duplikat innerhalb des Abfragebereichs auf. Alle doppelten Werte werden als Fehler angezeigt. | Bearbeiten oder Entfernen von Werten, um Duplikate zu vermeiden. Das Tool stellt keine vorgeschlagene Korrektur für Duplikate bereit. Stattdessen müssen Sie auswählen, welches der zwei oder mehr Duplikate der richtige ist, und die doppelten Einträge oder Einträge löschen. ||
|**format** | Formatierungsfehler. Der Wert verstößt gegen die Formatanforderungen für die Attributverwendung. | Das vorgeschlagene Update zeigt den Wert an, bei dem ungültige Zeichen entfernt werden. Wenn keine ungültigen Zeichen vorhanden sind, werden das Update und der Wert gleich angezeigt. Sie müssen bestimmen, was Sie im Update wirklich wünschen. Das Tool stellt keine vorgeschlagene Korrektur für alle Formatierungsfehler bereit. | SMTP-Adressen müssen beispielsweise RFC 2822 entsprechen, und mailNickname kann nicht mit einem Punkt beginnen oder enden. Weitere Informationen zu den Formatanforderungen für Verzeichnisattribute finden Sie unter "Verzeichnisobjekt-und Attribut Vorbereitung" in [Vorbereiten der Bereitstellung von Benutzern über die Verzeichnissynchronisierung zu Office 365](prepare-for-directory-synchronization.md). |
|topleveldomain  <br/> |Domäne der obersten Ebene. Dies gilt für Werte, die der [RFC 2822](https://go.microsoft.com/fwlink/p/?LinkId=401464) -Formatierung unterliegen. Wenn es sich bei der Domäne der obersten Ebene nicht um Internet Routing handelt, wird dies als Fehler erkannt. Beispielsweise ist eine SMTP-Adresse, die mit. local endet, nicht Internet routingfähig und würde diesen Fehler verursachen. |Ändern Sie den Wert in eine Internet Routingfähige Domäne `.com` wie `.net`oder. | Wechseln `myaddress@fourthcoffee.local` Sie `fourthcoffee.com` zu oder eine andere routingfähige Internetdomäne.  <br/> Anweisungen finden Sie unter [Vorgehensweise Vorbereiten einer nicht routingfähigen Domäne (wie. Local Domain) für die Verzeichnissynchronisierung](prepare-a-non-routable-domain-for-directory-synchronization.md). |
|**domainpart** | Domänen Teilefehler. Dies gilt für Werte, die der RFC 2822-Formatierung unterliegen. Wenn der Domänenteil des Werts ungültig ist und nicht mit RFC 2822 übereinstimmt, wird dieser generiert. | Ändern Sie den Wert in einen, der RFC 2822 entspricht. Stellen Sie beispielsweise sicher, dass keine Leerzeichen oder unzulässige Zeichen enthalten sind. | Wechseln `myaddress@fourth coffee.com` Sie `myaddress@fourthcoffee.com`zu. |
|**domainpart_localpart** | Fehler in der lokalen Komponente. Dies gilt für Werte, die der RFC 2822-Formatierung unterliegen. Wenn der lokale Teil des Werts ungültig ist und nicht mit RFC 2822 übereinstimmt, wird dieser generiert. |Ändern Sie den Wert in einen, der RFC 2822 entspricht. Stellen Sie beispielsweise sicher, dass keine Leerzeichen oder unzulässige Zeichen enthalten sind. |Wechseln `my"work"address@fourthcoffee.com` Sie `myworkaddress@fourthcoffee.com`zu. |
|**length** | Length-Fehler. Der Wert verstößt gegen den Längen Grenzwert für das Attribut. Dies wird am häufigsten auftreten, wenn das Verzeichnisschema geändert wurde.  | Durch das von IdFix vorgeschlagene Update wird der Wert auf die zulässige Länge gekürzt.  <br/> Beachten Sie, dass dies möglicherweise unerwünschte Ergebnisse hervorrufen kann. Sie sollten das vorgeschlagene Update überprüfen und bei Bedarf ändern, bevor Sie auf über **nehmen**klicken. ||
|**leer**  | Leer oder Null-Fehler. Der Wert verletzt die NULL-Einschränkung für Attribute, die synchronisiert werden sollen. Nur wenige Attribute müssen einen Wert enthalten. | Wenn möglich, wird das vorgeschlagene Update andere Attributwerte nutzen, um einen wahrscheinlichen Ersatz zu generieren. ||
|**mailmatch** | Dies gilt nur für Office 365 dediziert. Der Wert stimmt nicht mit dem e-Mail-Attribut überein. | Das vorgeschlagene Update ist der e-Mail-Attributwert, der mit "SMTP:" vorangestellt wurde. ||
    
## <a name="operations-you-can-perform-by-using-idfix"></a>Vorgänge, die Sie mit IdFix ausführen können
Um einen Fehler zu beheben, wählen Sie eine Option aus der Dropdownliste **Aktion** aus. In der folgenden Tabelle werden die **Aktions** Vorgänge beschrieben, die Sie mit dem IdFix-Tool für Attribute ausführen können. Wenn Sie die Spalte **Action** leer lassen, führt das IdFix-Tool keine Aktionen für diesen spezifischen Fehler im Verzeichnis aus. 

|**Aktion**|**Aktionsbeschreibung**|**Beispiel**|
|:-----|:-----|:-----|
|**Abgeschlossen** | Der ursprüngliche Wert ist akzeptabel und sollte nicht geändert werden, obwohl er als Fehler erkannt wurde. | Zwei Benutzer haben ein proxyAddress identifiziert als Duplikat. Nur einer kann den Wert für die e-Mail-Zustellung verwenden. Markieren Sie den Benutzer mit dem korrekten Wert als **abgeschlossen**. |
|**Entfernen** | Der Attributwert wird aus dem Quellobjekt gelöscht. Im Fall eines mehrwertigen Attributs wird beispielsweise `proxyAddresses`nur der einzelne angezeigte Wert gelöscht. | Zwei Benutzer haben ein proxyAddress identifiziert als Duplikat. Nur einer kann den Wert für die e-Mail-Zustellung verwenden. Markieren Sie den Benutzer mit dem doppelten Wert als **Entfernen**. |
|**Bearbeiten** | Die Informationen in der Spalte **Aktualisieren** werden verwendet, um den Attributwert zu ändern. Wenn ein gültiger **Aktualisierungs** Wert von IdFix vorgeschlagen wurde, wählen Sie in der Spalte **Aktion** die Option **Bearbeiten** aus, und fahren Sie mit dem nächsten Fehler fort. Wenn Ihnen der Vorschlag nicht gefällt, geben Sie in der Spalte **Aktualisieren** einen neuen ein, und wählen Sie dann in der Spalte **Aktion** die Option **Bearbeiten**aus. ||
|**Rückgängig** | Diese Option ist nur verfügbar, wenn Sie aus einem Transaktionsprotokoll wiederhergestellt haben. Wenn Sie **Rückgängig**auswählen, wird der Attributwert auf den ursprünglichen Wert wiederhergestellt. ||
|**FAIL** | Dieser Wert wird nur zurückgegeben, wenn ein **Aktualisierungs** Wert einen unbekannten Konflikt mit AD DS Regeln aufweist. In diesem Fall können Sie den Wert in der Spalte **Update** erneut bearbeiten, wenn Sie wissen, was der Fehler ist. Es kann erforderlich sein, die Werte im Objekt mithilfe der ADSI-Bearbeitung zu analysieren. Weitere Informationen finden Sie unter [ADSI-Editor (AdsiEdit. msc)](https://go.microsoft.com/fwlink/p/?LinkId=401170). ||

Nachdem Sie eine **Aktion** für einen Fehler oder einen Batch von Fehlern ausgewählt haben, klicken Sie auf über **nehmen**. Wenn Sie auf **Apply** klicken, nimmt das Tool die Änderungen im Verzeichnis vor. Sie können Korrekturen für mehrere Fehler bereitstellen, bevor Sie auf über **nehmen** klicken, und IdFix wird Sie alle gleichzeitig ändern.

Führen Sie IdFix erneut aus, um sicherzustellen, dass die von Ihnen vorgenommenen Korrekturen keine neuen Fehler verursachen. Sie können diese Schritte beliebig oft wiederholen. Es ist eine gute Idee, den Vorgang ein paar Mal durchzugehen, bevor Sie die Synchronisierung vornehmen.
    
## <a name="changing-the-rule-set-used-by-idfix"></a>Ändern des von IdFix verwendeten Regelsatzes
IdFix verwendet standardmäßig den mehrinstanzenfähigen Regelsatz zum Testen der Einträge in Ihrem Verzeichnis. Dies ist der richtige Regelsatz für die meisten Office 365 = Customers. Wenn Sie jedoch ein Office 365 dedizierter oder ITAR (International Traffic in Arms Regulations)-Kunde sind, können Sie IdFix so konfigurieren, dass stattdessen der dedizierte Regelsatz verwendet wird. Wenn Sie nicht sicher sind, was für ein Kundentyp Sie sind, können Sie diesen Schritt einfach überspringen. Klicken Sie auf das Zahnradsymbol in der Menüleiste, und klicken Sie dann auf **dediziert**, um den Regelsatz auf dediziert festzulegen.
  
## <a name="changing-the-scope-of-the-search-used-by-idfix"></a>Ändern des Bereichs der Suche, die von IdFix verwendet wird
Standardmäßig durchsucht IdFix das gesamte Verzeichnis. Wenn Sie möchten, können Sie das Tool so konfigurieren, dass stattdessen eine bestimmte Unterstruktur durchsucht wird. Klicken Sie dazu in der Menüleiste auf das Filter Symbol, und geben Sie eine gültige Unterstruktur ein.
  
## <a name="rolling-back-your-changes-by-using-the-idfix-gui"></a>Rollback der Änderungen mithilfe der IdFix-GUI
Jedes Mal, wenn Sie auf **Apply** klicken, um Änderungen zu übernehmen, erstellt das IdFix-Tool eine separate Datei namens Transaktionsprotokoll, in der die soeben vorgenommenen Änderungen aufgelistet werden. Sie können das Transaktionsprotokoll verwenden, um nur die Änderungen zurückzusetzen, die sich im letzten Protokoll befinden, falls Sie einen Fehler machen. Wenn Sie während der Aktualisierung einen Fehler machen, können Sie die zuletzt angewendeten Änderungen rückgängig machen, indem Sie auf **Rückgängig**klicken. Wenn Sie auf **Rückgängig**klicken, verwendet IdFix das Transaktionsprotokoll, um nur die Änderungen im letzten Transaktionsprotokoll zurückzusetzen. Weitere Informationen zur Verwendung des Transaktionsprotokolls finden Sie unter [Reference: Office 365 IdFix-Transaktionsprotokoll](idfix-transaction-log.md).

## <a name="next-step"></a>Nächster Schritt

[Einrichten der Verzeichnissynchronisierung](set-up-directory-synchronization.md)
