# Changelog

## 0.10.3

- **Die Wärmepumpen-Leistung wurde ohne Einheit gelesen** — meldet der Sensor in kW (deiner tut das), kam 2,8 statt 2800 an: jede Sollwert-Anhebung zählte als zusätzlicher Verdichterstart und endete zu früh.
- **Im Modus „Automatisch" prüft SEA jetzt wirklich alle 15 Minuten** — bisher nur, solange jemand die Oberfläche offen hatte.
- **„Notstrom-Reserve" aus nimmt nicht mehr die harten Lade-Grenzen mit** — die Reserve-Untergrenze und die SoC-Obergrenze gelten immer, abschaltbar ist nur das aktive Nachladen.
- **„Batterie deckt Netzbezug" schaltet den Bezugs-Deckel nicht mehr still ab** — wer beides konfiguriert, bekommt jetzt auch beides.
- **Eine Maschine ohne eingetragene Nennleistung startet nicht mehr bei fast jedem Überschuss** — SEA nimmt, was sie im letzten Durchlauf wirklich gezogen hat.
- **Gestufte Geräte halten jetzt auch eine Frist aus einem Auftrag ein** und laufen ohne Auftrag nicht mehr los.
- **Deine eigenen Regeln erscheinen als Strategie** — bisher war ausgerechnet das Selbstgeschriebene auf der Strategien-Seite unsichtbar.
- **Eine Regel und die Regelung sind sich jetzt einig, ob eine Entität an ist** — bei Steckern wie „plugged_in" widersprachen sie sich.
- **Uhrzeiten mit Sekunden („22:00:00") brechen die Regelung nicht mehr ab.**

## 0.10.1

- **„Geplante Fenster" und das Diagramm darüber zeigen jetzt dieselbe Rechnung** — bisher stammten sie aus zwei getrennten Vorausberechnungen und konnten sich widersprechen.
- **„Plan für heute" folgt einem Eingriff sofort** — bisher zeigte die Karte nach einer Änderung bis zu 15 Minuten lang noch den alten Tag; auch ein geänderter Tarif rechnet die Vorschau jetzt neu.
- **Neu je Gerät: „Wert je kWh"** — damit entscheidet SEA nicht nur, wer zuerst drankommt, sondern auch, ob sich eine Stunde für dieses Gerät überhaupt lohnt; leer lassen ändert nichts.
- **Ein Gerät, dem eine kWh weniger wert ist als die Einspeisevergütung, nimmt den Sonnenstrom nicht mehr** — die Energie verdient im Netz mehr; ein laufendes Gerät wird davon nicht unterbrochen.
- **Haben alle beteiligten Geräte einen Wert, entscheidet er die Reihenfolge** statt der eingetragenen Rangzahl; gemischt bleibt es bei deiner Liste.
- **Beim Aufklappen auf dem Handy wird nicht mehr zu viel Platz frei gelassen** — es waren 38 Pixel je Zeile zu viel.
- **Eine günstige Stunde gilt nicht mehr für alle Geräte gleich** — dieselbe Stunde kann fürs Warmwasser lohnen und fürs Auto zu teuer sein.
- **Fahrzeuge haben jetzt eine eigene Entität für die Ladeleistung** — hängen zwei Autos an einer Wallbox, wurde die Leistung bisher dem erstbesten zugeschrieben; der Gast lud, angezeigt wurde es beim eigenen Auto.
- **Alle angesteckten Fahrzeuge werden im Flussdiagramm gezeigt**, jedes mit eigenem Ladestand und eigener Leistung.
- **Ein Verbraucher, der einen anderen als Elternteil hat, lässt sich jetzt auch dann aufklappen, wenn er das einzige Kind ist** — bisher brauchte ein Knoten mindestens zwei Kinder, um ein „+" zu bekommen.
- **Auf dem Handy wird beim Aufklappen wieder der passende Platz freigemacht** — die nächste Zeile rutschte dem Fahrzeug bisher auf den Kreis.
- **„Sonnenstrom und günstige Stunden nutzen" nutzt die günstigen Stunden jetzt wirklich** — die zweite Hälfte der Einstellung blieb bisher wirkungslos, im Winter also die ganze Saison.
- **In einer günstigen Stunde starten nicht mehr alle Geräte gleichzeitig** — SEA verteilt die Leistung des Hausanschlusses nach deiner Prioritätenliste; ein Gerät mit Frist geht vor.

## 0.10.0

- **SEA rechnet aus, wann das Auto spätestens laden muss** — aus der fehlenden Energie und der Ladeleistung statt aus einer eingetippten Uhrzeit; vorher wird nur freier Überschuss genutzt.
- **Reicht die Sonne für den Mindest-Ladestand nicht, sagt SEA es rechtzeitig** — mit der Menge, die offen bleibt, statt es am Ende festzustellen.
- **Widerspruch zwischen Ladeziel und Betriebsart wird sichtbar aufgelöst:** „Automatisch" setzt das Ziel durch, „Assistiert" bietet Netzstrom per Knopf an, sonst bleibt es beim Hinweis.
- **Die „PV-Schwelle" bei der Wallbox ist ohne Wirkung, sobald ein Mindest-Ladestand mit Uhrzeit hinterlegt ist** — das Feld sagt das jetzt, statt es stillschweigend zu sein.
- **SEA startet eine Maschine, die jemand befüllen muss, nur noch mit Auftrag.** Bisher schaltete die PV-Überschuss-Strategie die Waschmaschine ein, sobald Sonne da war — auch wenn keine Wäsche drin lag; jetzt ist ohne Auftrag Ruhe.
- **„Jetzt befüllt" plus Zeitrahmen je Maschine** stehen unter *Verhalten → Vorgaben & Grenzen* (früher „Anforderungen & Grenzen"; die Karte ist jetzt offen, statt zugeklappt): „ab" und „fertig bis" bleiben stehen, der Auftrag ist das Tägliche.
- **SEA erkennt den Start an der Maschine selbst** — über eine Ein/Aus-Entität (z. B. aus der Hersteller-Cloud) oder die Leistung der Messsteckdose ab einer Schwelle; einzustellen beim Gerät unter *Start erkennen*.
- **Wer am Gerät startet, gibt SEA einen Moment Zeit:** Direkt nach einem erkannten Start darf SEA die Maschine noch einmal abschalten und in ein günstiges Fenster legen — auch eine „nicht unterbrechbare". Läuft sie erst, wird sie nicht mehr angefasst.
- **„Fertig bis" wird nicht mehr eingetippt.** Der „späteste Start" ist beim Gerät entfallen — SEA rechnet ihn aus dem Zeitrahmen und der Laufdauer aus, die es aus dem Durchlauf gelernt hat.
- **„Max. Starts" zählt je Durchlauf statt je Tag** — drei Waschgänge sind drei Durchläufe, und der zweite erbt nicht mehr die Unterbrechungen des ersten. Zusammen mit „min. Auszeit" erscheint das Feld nur noch bei *unterbrechbar*, wo es überhaupt etwas bedeutet.
- **Sprachausgabe aufgeräumt:** Der Lautsprecher ist ein Strich-Symbol wie die übrigen Knöpfe (kein buntes Emoji) und steht jetzt immer direkt neben seiner Entität — der lange Entitätsname kürzt sich stattdessen ab. „Weitere Entität hinzufügen" hat ein +, keinen Stift, und der Erklärtext beginnt auf derselben Zeile wie die Überschrift.
- **Der Verlauf zeigt Ja/Nein-Größen wieder an** — „angesteckt", SG-Ready, Schalter. Sie fielen beim Einlesen der Historie stillschweigend heraus (ein Zustand „on" ist keine Zahl), deshalb stand im Verlauf „–", während dieselbe Entität auf der Status-Seite „an" zeigte. Sie erscheinen jetzt als Spur mit an/aus — und ein ausgefallener Sensor wird weiter als „keine Daten" gezeigt, nicht als „aus".
- **Das Auto hat jetzt zwei Werte statt einem:** einen **maximalen Ladezustand** beim Gerät (Batterieschutz — den überschreitet SEA nie, auch die Automatik nicht) und einen **Mindest-Ladezustand bis zu einer Zeit** unter *Vorgaben & Grenzen*. Mehr laden ist damit immer erlaubt und überschreibt keine Vorgabe mehr. Bestehende Einstellungen werden verhaltensneutral übernommen (der alte Ziel-Wert gilt zunächst als beides).
- **SEA ändert den Ladezustand des Autos nicht mehr selbst** — die Variante „Ziel-SoC auf 100 %" ist entfallen, weil Mehrladen ohnehin erlaubt ist.
- **Die Wärmepumpe darf sich beim Vorheizen von der Batterie helfen lassen** — das Häkchen „Batterie-Unterstützung" gibt es jetzt auch bei einer Wärmepumpe im Anhebungs-Modus. Es saß bisher nur bei schaltbaren Geräten, wodurch die Funktion für genau das Gerät unerreichbar war, für das sie gedacht ist.
- **Nichts ist mehr ausgeblendet.** Die Detail- und Regelungs-Einstellungen erscheinen für jeden, der die Einrichtung öffnet — wer eine Anlage verwaltet, muss auch sehen können, was daran eingestellt ist.
- **Auf dem Handy wird für ein ausgeklapptes Fahrzeug Platz geschaffen.** Die Höhe der Zeichenfläche zählte nur die Leistungs-Sensoren mit, nicht das Auto — sein Ladezustand wurde unten abgeschnitten.
- **Die Lade-Betriebsarten heißen jetzt nach ihren Quellen:** „Nur Sonnenstrom" · „Sonnenstrom und Batterie, kein Netzbezug" · „Sonnenstrom, Batterie und Netz". Die alten Namen verschwiegen genau das Unterscheidende — „immer laden" sagte nichts über die Batterie.
- **Netzladen endet, sobald der Mindest-Ladestand erreicht ist.** „Sonnenstrom, Batterie und Netz" verspricht, dass das Auto seinen Mindestwert rechtzeitig erreicht — nicht, dass SEA danach weiter Strom kauft. Darüber hinaus wird nur noch aus Überschuss und Batterie nachgeladen, bis zum maximalen Ladezustand. Ohne gesetzten Mindestwert bleibt es beim bisherigen „immer laden".
- **Und die dritte Betriebsart bezieht die Batterie jetzt wirklich ein.** Sie stand auf „ohne Batterie", während die Strategie „Batterie deckt Netzbezug" den Netzbezug des Autos ohnehin gedeckt hat — ein Versprechen, das SEA nicht halten konnte. Jetzt steht im Namen, was passiert.
- **Bei der Wärmepumpe entfällt der Umschalter „schalten / Sollwert".** Wärmepumpen nehmen Temperaturen, keine Watt — eine direkte Leistungssteuerung bieten sie praktisch nicht an. Stattdessen steht dort, was wirklich greift: die Anhebung an den Heizkreisen (und SG-Ready, falls verdrahtet).
- **Bei Wallbox, Heizstab, Wärmepumpe und Batterie heißt die Auswahl „Betriebsart"** statt „Gerätetyp" — dort sind es fertige Einstellungs-Pakete, kein Gerätetyp. „Gerätetyp" bleibt beim Verbraucher, wo es tatsächlich einer ist.
- **„Angepasst" ist überall wieder wählbar** und schaltet die Schalter frei, die die Voreinstellungen setzen (bei der Wallbox z. B. „Netzladen erlauben"). Bisher verschwand der Eintrag, sobald man eine Voreinstellung gewählt hatte — der Weg zurück war versperrt.
- **„Spätester Start" ist bei der Wallbox verschwunden** — die Frist kommt vom Fahrzeug („mindestens auf X % bis HH:MM" unter *Vorgaben & Grenzen*). An der Wallbox war das Feld ohnehin wirkungslos, sobald ein Fahrzeug verknüpft war.
- **Dabei zählt jetzt die Energie, nicht die Spitzenleistung:** SEA rechnet, was die Batterie über die *ganze* Laufzeit halten kann. Eine Batterie knapp über der Reserve liefert kurz 3 kW, aber keine 90 Minuten — vorher wurde genau das verwechselt.
- **Vorschläge dürfen die ganze Prioritätenliste umstellen** statt nur zweier fester Paare; alles, was ein Vorschlag nicht nennt, bleibt an seinem Platz.
- **Leistungen im kW-Bereich mit einer Nachkommastelle** („3,3 kW" statt „3,28 kW").
- **„Warmwasser über Wärmepumpe" lässt sich endlich übernehmen.** Die Variante stand mit ★ ganz oben und meldete trotzdem „nicht einstellbar" — SEA konnte sie rechnen, aber nicht umsetzen. Sie wird jetzt auf echte Einstellungen abgebildet: Der Heizstab nimmt nicht mehr am Überschuss teil, die Wärmepumpe rückt in der Prioritätenliste nach oben. Und der Weg zurück funktioniert auch (vorher wäre das Abschalten eine Einbahnstraße gewesen).
- **Die Meldung zur befüllten Maschine sagt jetzt, was wirklich passiert ist** — „läuft — am Gerät gestartet" oder „als beladen übernommen — Start verschoben". Bisher kam sie im Moment der Erkennung, also bevor SEA entschieden hatte, ob die Maschine laufen darf.
- **Jede befüllte Maschine hat genau eine Meldung.** „Als beladen übernommen" → „läuft" → „Durchlauf beendet" ersetzen einander, statt sich zu stapeln und sich zu widersprechen. Und wenn ein verschobener Auftrag später wirklich startet, sagt SEA das jetzt auch — vorher blieb „Start verschoben" stehen, während die Maschine schon lief.
- **Hinweise lassen sich wegklicken** (× oben rechts) — bei **allen** Meldungsarten (Plan-Hinweise, Money-Guard, Netz-Plausibilität, Konfigurations-Hinweise); vorher hatte nur eine davon das ×. Ein weggeklickter Hinweis bleibt weg, solange die Lage besteht — klärt sie sich und tritt später wieder auf, meldet er sich erneut.
- **Bei den Fahrzeugen steht der aktuelle Ladezustand** neben dem Ziel: „CLA 250+: Aktueller Ladezustand: 63 %" und rechts „Aufladen auf 80 % bis 07:00". Das Prozent-Feld ist breit genug für dreistellige Werte.
- **Im Automatik-Modus steht unter dem Plan „SEA hat angepasst"** — mit dem Zustand vorher und ohne „übernehmen"-Knopf (es gibt nichts mehr anzunehmen). In *regelbasiert* und *manuell* erscheint dort nichts mehr.
- **Das Fahrzeug ist im Flussdiagramm ein aufklappbares Kind seiner Wallbox** — über dasselbe „+" wie andere Unterebenen, mit seinem Ladezustand darunter.
- **„Plan für heute": Überschrift ohne Symbol** (keine andere Karte hat eines), drei Kacheln je Zeile statt Zeilenumbrüchen, und die Kennzahlen in derselben Größe wie bei *Aktuell*.
- **Die Lizenz-Karte unter Einrichtung ist immer sichtbar** und zeigt die Geräte-Seriennummer auch, wenn die Lizenzierung in dieser Version noch nicht aktiv ist — so lässt sich die Pi-Seriennummer schon jetzt ablesen (vorher erschien die Karte erst mit scharfer Lizenzprüfung).
- **Die Lizenz ist jetzt an den Raspberry Pi gebunden, nicht mehr an den Habitron-Router** — SEA läuft auf dem Pi, dessen Seriennummer (aus `/proc/cpuinfo`) ist sofort lesbar und übersteht ein Neu-Aufsetzen der SD-Karte. Die Lizenz-Karte zeigt sie als „Geräte-Seriennummer".
- **Ein Schlüssel ohne Seriennummer-Bindung (Wildcard) liest die Pi-Seriennummer gar nicht mehr ab** — so läuft eine Wildcard-Installation auch auf anderer Hardware (x86, VM), die keine solche Nummer hat.
- **Der Lizenz-Generator trägt eine 3-Buchstaben-Produktkennung** (Standard „SEA"): Ein Schlüssel gilt nur für das Produkt, dessen Kennung er trägt — dieselbe Signier-Datei kann so auch andere Produkte bedienen, ohne dass ein Schlüssel das falsche freischaltet. `tools/sign_license.py issue --product XYZ …`.
- **Zeitrahmen einer Maschine: ein Umschalter „fertig bis / nicht vor" und eine Zeit** statt zwei Feldern. „fertig bis" ist die Frist wie bisher; „nicht vor" ist jetzt eine **echte** Startsperre — vorher wurde „ab" nur für die Tag/Nacht-Unterscheidung herangezogen und hielt die Maschine gar nicht zurück.
- **Beide Zeiten meinen immer den nächsten Termin in der Zukunft.** „fertig bis 10:00" am Mittag eingestellt heißt: erst morgen um 10:00 fertig — die Maschine läuft dann morgen. Ein Tooltip sagt je nach Uhrzeit, was gerade gemeint ist.
- **Reicht die Zeit bis „fertig bis" voraussichtlich nicht, startet SEA trotzdem sofort** und sagt es — statt die Frist stillschweigend zu reißen.
- **SEA meldet Start und Ende eines Durchlaufs** — auf „Heute" und über die eingestellten Sprachausgabe-Entitäten („Waschmaschine: am Gerät gestartet. Fertig bis 18:00", „Durchlauf beendet. 1,2 kWh verbraucht").
- **Verlauf und „Plan für heute" fühlen sich jetzt gleich an.** Die „Operativen Strategien" im Verlauf werden von demselben Zeichner gemalt wie die Spuren im Plan — gleiche Höhe, gleiche Farben, gleiches Verhalten. Ein Klick auf einen Block erklärt, was die Strategie in dem Zeitraum gemacht hat (30 Sekunden sichtbar), genau wie im Plan.
- **Der PV-Ertrag liegt im Verlauf jetzt gelb hinter allem** — dieselbe amberfarbene Fläche wie im Plan.
- **Reicht der gewählte Zeitbereich in die Zukunft, ergänzt der Verlauf die Prognose** für PV und Hausverbrauch gestrichelt — und zwar lückenlos an die Messung anschließend (keine Lücke mehr zwischen „gemessen" und „prognostiziert"). Bisher gab es die Vorschau nur in „Heute".
- **Die senkrechte Achse im Plan sitzt weiter links** — die Spur-Beschriftung ist schmaler, dadurch bleibt mehr Platz fürs Diagramm.
- **Die Maschinen standen gar nicht in *Vorgaben & Grenzen*.** Die Karte suchte sie in der alten, entitäts-basierten Verbraucher-Liste, während der Haken „wird befüllt" beim eingerichteten Gerät landet — zwei Listen, die sich nie treffen. Damit war die Zeile immer leer und „jetzt befüllt" hätte auch nichts angelegt. Jetzt kommen beide aus derselben Quelle.
- **„Selbstbeendend" gibt es beim Verbraucher nicht mehr** — der Schalter ist für Hersteller-Programme da (Wärmepumpen-Boost, Quick Veto), wo SEAs „Aus" das Programm abwürgen würde. Eine Steckdose kennt so etwas nicht; „unterbrechbar: nein" sagt dort schon alles. Bei Wärmepumpe und Warmwasser bleibt er.
- **Und damit auch „Angepasst": Es erscheint nur noch, wo es wirklich etwas freischaltet** (oder wo die Einstellungen zu keinem Typ passen — dann ist es die ehrliche Anzeige). Beim Verbraucher sind Typ und die sichtbaren Schalter jetzt alles, was es gibt.
- **Die Schalter am Gerät erklären sich selbst.** Unter „unterbrechbar" und „selbstbeendend" steht jetzt in der Karte, was SEA im aktuellen Zustand tut („SEA darf den Durchlauf abschalten, sobald der Überschuss wegfällt — höchstens 2× je Durchlauf") statt eines Kürzels, das man erst deuten muss.
- **Das Ende eines Durchlaufs erkennt SEA an derselben Schwelle wie den Start** — nur andersherum: „Leistung länger als 3 Minuten unter 50 % der Start-Schwelle". Eine Einstellung, beide Richtungen; die Lücke dazwischen ist Absicht, denn eine Waschmaschine pendelt zwischen den Programmphasen um ihre Schwelle.
- **„Stopp bei" ist bei einer befüllten Maschine mit Leistungs-Sensor verschwunden** — dort war es unbrauchbar (man konnte kein „kleiner als" wählen, und kurze Pausen hätten den Durchlauf beendet). Stattdessen steht dort die Regel, die wirklich gilt. Mit einer Ein/Aus-Entität bleibt es: Ein Boolean kann „gestartet" heißen statt „läuft", dann weiß nur ein eigenes Fertig-Signal Bescheid — und das schließt den Auftrag jetzt auch wirklich.
- **„Leistung (an)" heißt jetzt „Nennleistung"** und der Hilfetext sagt, wozu der Wert dient: Er regelt nichts, er beantwortet nur „reicht der Überschuss zum Einschalten?" und „wie viel ist reserviert, bevor die nächste Priorität dran ist?".
- **Beim Verbraucher steht jetzt der Gerätetyp statt einer „Absicht": „Läuft ohne Benutzerstart" oder „Läuft mit Benutzerstart"** — die Geräte (Pool-Pumpe … / Waschmaschine …) stehen als Beispiele im Erklärtext. Das ist die einzige Frage, die SEA nicht selbst beantworten kann: dieselbe Steckdose trägt eine Pool-Pumpe oder eine Waschmaschine.
- **„Angepasst" lässt sich endlich wählen.** Es stand nur dann in der Liste, wenn es schon aktiv war — man kam also nie hin. Es schaltet jetzt die Experten-Schalter frei und speichert selbst nichts (der Typ ergibt sich aus den Schaltern, nicht umgekehrt).
- **„Unterbrechbar" gehört wieder dir** und ist immer sichtbar — auch bei der Waschmaschine. Es hängt an keinem Typ mehr, du kannst es also setzen, ohne den Gerätetyp zu verlieren; beim Benutzerstart-Typ ist „läuft durch" nur die Voreinstellung.
- **„Selbstbeendend" und „unterbrechbar" widersprechen sich nicht mehr:** Bei selbstbeendend schaltet SEA überhaupt nie ab, „unterbrechbar" hatte dort nie eine Wirkung — die Auswahl ist jetzt weg statt wirkungslos.
- **Die Absichten sagen, für welche Geräte sie gedacht sind** („Läuft ohne Zutun — Pool-Pumpe, Entfeuchter, Heizstab" gegenüber „Wird befüllt — Waschmaschine, Spülmaschine"), damit niemand eine Waschmaschine auf „läuft, wenn die Sonne reicht" stellt.
- **Negative Zahlen werden abgefangen.** „max. Starts = −1" hieß nicht „unbegrenzt", sondern: Die Last durfte nie starten. Die Felder lassen es nicht mehr zu, und SEA klemmt es auch serverseitig ab.
- **Bezeichnungen stehen bei mehrzeiligen Eingaben oben** (Start erkennen, Stopp bei) statt in der Mitte.
- **„Wird beladen" steht nur noch an einer Stelle** — in der Geräte-Frage „Was soll SEA damit tun?". Das rohe Häkchen unter *Erweitert – Zeiten & Grenzen* war dasselbe zweimal.
- **Die Auswahl der Geräte-Absicht ist nicht mehr eingequetscht** und zeigt den ganzen Text.
- **„Stopp bei" lässt sich wieder entfernen** — eine einmal gewählte Entität klebte für immer, es gab überhaupt keinen Löschen-Knopf. Sie steht jetzt bei den anderen Einrichtungs-Angaben unter *Erweitert – Zeiten & Grenzen*, und das Entfernen nimmt die Schwelle gleich mit.
- **Knopf „sofort starten"** neben „jetzt befüllt": SEA wartet dann nicht auf ein günstiges Fenster, sondern fährt die Maschine jetzt.
- **Auch die Tarif-Strategie startet keine leere Maschine mehr** — sie hatte dieselbe Lücke wie die PV-Strategie: ein günstiges Fenster war ihr Grund genug.
- **Eine Maschine, die wegen ihrer Frist laufen muss, wird nicht mehr abgeworfen.** Fristzwang und Netzbezugs-Abschaltung haben sich um sie gestritten — im Zweifel gewinnt die Frist.
- **Ohne Laufdaten wird der Auftrag nicht mehr abgelehnt:** SEA fährt die Maschine und lernt die Laufdauer in diesem Durchlauf; nur das Fenster im Plan fehlt beim ersten Mal.
- **Diagramme lassen sich auf dem Handy zeitlich schieben.** Statt einen ganzen Tag in die Handy-Breite zu quetschen, behält die Zeichnung ihre Breite und der Rahmen wird seitlich verschiebbar — im Plan wie im Verlauf, wo alle Diagramme (Leistung, Operative Strategien, Strompreis, Detail-Plots) gemeinsam schieben, damit sie dieselbe Zeit zeigen. Zwei Finger zoomen weiterhin die Zeitachse.
- **Der Ladestand von Batterie und Auto steht jetzt auch im Plan für heute** — gestrichelt, damit er sich von den gemessenen Leistungen unterscheidet; das Auto in eigener Farbe (blau), sonst wäre es mit der Strategie-Farbe verwechselbar gewesen.
- **Die Balken in den Spuren sind schlanker, „jetzt" kollidiert nicht mehr mit der kW-Beschriftung**, und die Spur-Beschriftung wird nicht mehr am linken Rand abgeschnitten.
- **Die Klick-Erklärung am Balken bleibt 30 Sekunden stehen.** Bisher hatte sie keine eigene Lebensdauer und wurde vom 5-Sekunden-Takt weggewischt.
- **Das Tagesplan-Diagramm ist deutlich größer und besser lesbar.** Es ist rund doppelt so hoch, die Spuren sind breiter (die Beschriftung darin passt jetzt hinein statt zu schrumpfen), und es hat Abstand zur Karte darüber.
- **Gleiche Größe, gleiche Farbe — im Plan wie im Verlauf.** PV ist überall bernsteinfarben, Verbrauch cyan, Ladestand petrol, der eigene Tarif blau. Nebenbei behoben: Im Verlauf hing die PV-Farbe an der Geräte-Reihenfolge — ein neues Gerät färbte sie um.
- **Neuer Modus „Automatisch — SEA adaptiert".** SEA prüft alle 15 Minuten, ob eine andere Einstellung dein Ziel besser erreicht — und stellt sie selbst um. Mit Bremsen: nur wenn es sich lohnt (ab 10 Cent am Tag), frühestens eine Stunde nach der letzten Umstellung, und nur was SEA wirklich einstellen kann. **Änderst du eine Vorgabe** (Auto-Frist, Ziel-Ladestand, Notreserve, Ziel), plant SEA sofort neu und darf auch sofort umstellen — die Sperrfrist schützt vor Zappeln, nicht vor dir. Jede Anpassung erscheint mit Uhrzeit und Begründung unter *Heute → Hinweise* und wird angesagt; rückgängig über „Alternativen prüfen".
- **Experten-Einstellungen waren für Administratoren unsichtbar.** SEA fragte Home Assistant nach einem `is_admin`-Feld, das die Benutzerliste gar nicht liefert — damit galt jeder als Nicht-Admin. Jetzt wird der Admin so bestimmt, wie HA es selbst tut (Besitzer oder aktives Mitglied der Administrator-Gruppe).
- **Der Plan sagt, warum eine Last darin fehlt.** Nimmt ein Gerät am PV-Überschuss teil, bekommt aber keine Spur, steht der Grund unter Hinweise: zu kurze Laufzeit für einen Balken (unter 10 Minuten werden weggelassen), kein Überschuss in der Prognose, Stopp-Bedingung erreicht, oder höher priorisierte Verbraucher nehmen alles. Bisher fehlte die Spur wortlos — und ein fehlender Balken lässt sich nicht anklicken.
- **Ziel und Autonomie stehen in der Kartenüberschrift** („Kosten · Automatisch") und auf *Heute* neben dem Plan — man sieht ohne Aufklappen, wonach SEA fährt. *Ziel & Kontrolle* und *Strategien & Regeln* starten zugeklappt, *Vorgaben & Grenzen* offen.
- **Testansage je Sprachausgabe-Entität:** Der Lautsprecher-Knopf neben der Entität sagt „Testansage" auf genau dieser an — damit sich „funktioniert der Lautsprecher?" klären lässt, bevor SEA etwas Wichtiges zu sagen hat.
- **Fußnote zur Bewertungszahl** in der Alternativen-Tabelle: was sie ist, warum der Batterie-Bestand mitzählt und warum sie kein Geldbetrag ist, den du zahlst.
- **„Plan für heute" klarer gegliedert:** Das Briefing beginnt mit der Überschrift **Jetzt** und listet jede Aussage als eigenen Punkt statt als Textblock. Die Kacheln sehen aus wie bei „Aktuell"; unter den Stromkosten stehen Bezug und Einspeisung je mit kWh **und** Euro. Die Bewertungszahl der Ziel-Prüfung wird nicht mehr angezeigt — sie ist ein Sortier-Kriterium, keine Aussage über deinen Tag, und hat mehr verwirrt als erklärt.
- **SEA sagt und schreibt jetzt dieselbe Zahl:** Auch im Briefing standen bisher die „erwarteten Kosten" der Bewertung; jetzt steht dort die Rechnung, die man mit kWh × Preis nachrechnen kann.
- **Die Karten unter „Verhalten" lassen sich einklappen** (Ziel & Kontrolle, Vorgaben & Grenzen, Strategien & Regeln) — der Zustand bleibt beim Ändern erhalten. Der Knopf heißt jetzt „Alternativen prüfen".
- **Hinweise verschwinden sofort, wenn das Problem behoben ist.** Sie wurden nur alle fünf Minuten geholt — eine korrigierte Entität blieb bis zu fünf Minuten lang angemahnt. Jetzt lädt SEA sie neu, sobald sich etwas ändert, das einen Hinweis auslösen oder beenden kann.
- **Jede Strategie hat eine Farbe — überall dieselbe.** Sie steht als farbiges Quadrat hinter dem Namen der Strategie und taucht damit erkennbar in den Spuren unter „Plan für heute" und im Streifen „Operative Strategien" wieder auf. (Bisher pflegten drei getrennte Farbtabellen dieselbe Sache — und widersprachen sich.)
- **Die Temperaturabsenkung sitzt jetzt in ihrer eigenen Strategie-Karte**, mit Farbe und den Gruppen direkt darin. Der Knopf dorthin zeigte seit der Menü-Neugliederung ins Leere.
- **Der Plan rechnet sich neu, wenn du ein Gerät ein- oder ausschaltest.** Bisher musste man „Neu planen" drücken — und sah nicht, wenn die Plan-Simulation scheiterte: Ein Fehler wurde als „wird gerade berechnet" ausgegeben, für immer. Jetzt sagt SEA, was schiefging.
- **Energiebilanz mit Preisen:** Hinter jeder Kilowattstunde steht, was sie gekostet hat. Bei HT/NT erscheinen zwei Zeilen (eine je Preis), bei dynamischem Tarif der mengengewichtete Durchschnitt.

- **Die Experten-Einstellungen folgen jetzt deinen Home-Assistant-Rechten.** Wer in HA Administrator ist, sieht sie — alle anderen nicht. Die Checkbox entfällt; SEA erkennt den angemeldeten Benutzer selbst. (Lässt sich der Benutzer ausnahmsweise nicht ermitteln, gilt weiter die Add-on-Option „expert", damit niemand plötzlich ohne seine Einstellungen dasteht.)

## 0.9.3

- **„Kosten heute" zeigte nicht die Stromkosten.** Die Kachel zeigte die Bewertungszahl, nach der die Ziel-Prüfung sortiert — die enthält zusätzlich den Batterie-Verschleiß und rechnet den abends noch gespeicherten Strom gegen (sonst wäre „Batterie leerfahren" immer die günstigste Variante). Jetzt steht dort die **Rechnung** (Bezug × Preis − Einspeisung × Vergütung, mit Ø-Preis), und die Bewertungszahl steht darunter offen aufgeschlüsselt.
- **„Leistung & Zuordnung" wieder einzeilig.** Radio, „Sensor" und die gewählte Entität stehen in einer Zeile, Stift und × rechtsbündig, das + darunter unter dem ×. (Das Popup hatte sich das Spalten-Layout der Komponenten-Seite geliehen, das dort gar nicht gilt — deshalb brach jede Zelle um.)
- **Bei der Einsparung sind die verwaisten Eingabefelder weg** (Speichergröße, PV-Leistung, Senkentyp, Fallback-Preise). Sie gehörten zu den entfernten Vergleichen; was sie konnten, macht die Investitions-Analyse mit der echten Regelung besser.
- **Dynamischer Tarif ohne Preis-Entität: SEA nimmt die Börse.** Ist „Dynamisch" gewählt, aber keine Entität hinterlegt, holt SEA stündlich die Day-Ahead-Preise und rechnet mit (Börsenpreis + dein Aufschlag) × MwSt — ein dynamischer Tarif funktioniert damit ohne Anbieter-Integration. Die Aufschlag-Felder stehen dann sichtbar dort, statt im Experten-Modus.
- **Die Analyse rechnet in jedem Tarifmodell.** Neue Karte: *Analyseart* (Rückblick/Vorschau/Investition), *Zeitraum* und *Stromtarif* (Fest / HT-NT / Dynamisch, deiner ist als „mein Tarif" markiert) — so lässt sich prüfen, ob sich ein anderes Tarifmodell rechnen würde. Erklärtext und Zeitraum-Auswahl folgen der Analyseart. Fehlen für ein Modell die Preise, sagt SEA das, statt zu raten.
- **Sprachausgabe auf mehreren Geräten gleichzeitig.** Die Entitäten werden wie überall über den Entitäten-Picker gewählt (mehrere = Ansage auf allen); ein stummes Gerät bringt die anderen nicht zum Schweigen.
- **PV-Prognose ohne Sonderfall.** Die gewählte Entität gilt — Forecast.Solar, Solcast oder andere, SEA erkennt das Format selbst. Nur wenn nichts gewählt ist, nimmt SEA die Solar-Prognose des HA-Energie-Dashboards.
- **Einrichtung aufgeräumt:** Komponenten sind wie die anderen Karten einklappbar; PV-Prognose und Sprachausgabe stehen untereinander im selben Zeilen-Layout wie die Komponenten; Tarife übernehmen Eingaben automatisch (kein Speichern-Knopf mehr).
- **Die Preis-Schwellen fürs Netzladen/Entladen stehen jetzt bei der Tarif-Strategie** (Verhalten) statt in der Tarif-Einrichtung — ein Tarif ist, was du zahlst, nicht was SEA damit tut.
- **Die Sparanalyse erklärt nur noch die beiden Vergleiche, die es gibt.**
- **Die Sprachausgabe meldet jetzt Entscheidungen, statt auf Knopfdruck vorzulesen.** Findet SEA im Modus „Assistiert" eine bessere Einstellung für heute, sagt es das über deine Voice-Entität — einmal je Vorschlag, nicht bei jeder Prüfung. Die Entität wird unter *Einrichtung → Allgemein* gewählt; die Vorlese-Knöpfe entfallen.
- **Seitenreihenfolge: Heute · Verlauf · Verhalten · Analyse · Status · Einrichtung.** „Geräte" heißt jetzt „Status" — es ist die Momentaufnahme aller Messwerte — und erscheint nur im Experten-Modus. Der Seitenwechsel per Scrollen folgt automatisch dem sichtbaren Menü.
- **„Ziel & Kontrolle" sachlicher und in sinnvoller Reihenfolge:** erst *Ziel* (Kosten minimieren / Autarkie maximieren / Eigenverbrauch maximieren), dann *Autonomie* (Assistiert/Regelbasiert/Manuell). Die Erklärung steht darunter, nicht im Auswahlfeld.
- **Anforderungen & Grenzen enthält nur noch echte Bedingungen.** Die Stopp-Temperatur des Heizstabs ist eine Gerätegrenze und steht bei der Komponente; die Notstrom-Reserve nennt jetzt die Batterie beim Namen.
- **Einsparung: nur noch die beiden aussagekräftigen Vergleiche** (PV-Volleinspeisung, Direkter Eigenverbrauch). Der Text der Analyse stimmt wieder: Sie fährt die echte Regelung über die ganze Anlage, nicht mehr nur Batterie und stärkste Last.
- **Kleinigkeit:** Das Zustands-Abzeichen bei „Netzanschluss-Grenzen" steht wieder bündig unter den anderen.

## 0.9.2

- **Größere Schrift im ganzen Fließtext.** Erklärungen, Beschriftungen, Knöpfe und Menü sind jetzt mindestens 14 px; auf dem Handy 12 px. Nur Diagramm-Beschriftungen und Abzeichen bleiben klein.
- **Weniger Kästen im Kasten.** Der Energiefluss trägt seine Überschrift jetzt selbst, ohne zweiten Rahmen darin — und heißt schlicht „Energiefluss". Die Energiebilanz heißt nur noch „Energiebilanz", denn die Seite heißt „Heute".
- **Alle Hinweise in einer Karte.** Money-Guard, Netz-Plausibilität, Konfigurations-Hinweise und neu auch die Meldungen der Tagesplanung („heute kein Fenster für die Anhebung") stehen zusammen unter „Hinweise" — jeder als eigene Karte. Die geplanten Fenster selbst bleiben beim Plan.
- **„Globale Strategie" und „Was-wäre-wenn" entfallen.** Beide sind überholt: Das Ziel („Worauf es dir heute ankommt") und die Ziel-Prüfung leisten dasselbe, nur genauer und mit deinen Anforderungen als harter Grenze.
- **Die Ziel-Prüfung sagt es, wenn nichts zu holen ist.** Kosten alle Varianten gleich viel, erscheint das als ein Satz statt als lange Liste mit sinnlosen „übernehmen"-Knöpfen.
- **Einrichtung aufgeräumt.** „Allgemein" steht oben (mit der Version), die Fahrzeuge sitzen bei den Komponenten, „Sicherung & Diagnose" ganz unten und übernimmt die Diagnose-Werte; die Karte „Status" entfällt.
- **Kontroll-Stufen kurz benannt:** Assistiert — SEA optimiert · Regelbasiert — SEA steuert · Manuell — SEA überwacht.
- **Seitenwechsel per Scrollen folgt wieder dem Menü.** Die Reihenfolge zeigte noch auf Seiten, die es nicht mehr gibt.

## 0.9.1

- **Sechs Menüpunkte statt neun, klar getrennt.** *Heute* (was läuft + der Plan), *Verhalten* (Ziel, Kontroll-Stufe, Anforderungen, Strategien, Temperaturabsenkung), *Geräte*, *Analyse* (Einsparung + Investition), *Verlauf* und *Einrichtung* (Komponenten, Fahrzeuge, Tarife, Grundeinstellungen). Was zusammengehört, steht jetzt beieinander — und jede Einstellung hat genau einen Ort, damit nichts mehr auseinanderlaufen kann.
- **Einheitliches Karten-Design auf allen Seiten.** Jeder Block sitzt in einer Karte mit roter Überschrift und schwarzem Inhalt; der Energiefluss hat endlich eine eigene Überschrift bekommen. Hinweise stehen ohne Rahmen darum, dafür jeder einzeln als Karte — Money-Guard und Netz-Plausibilität inbegriffen, sie gehören dazu.

## 0.9.0

- **Du bestimmst, wie viel SEA selbst macht.** Neu auf „Heute": *Assistiert* (SEA prüft von sich aus, ob eine andere Einstellung dein Ziel besser erreicht, und schlägt sie vor), *Regelbasiert* (wie bisher: SEA regelt nach deinen Einstellungen) oder *Manuell* (SEA schaut nur zu und zeichnet auf). Die Umschaltung fasst deine Einstellungen nicht an — zurückschalten stellt alles wieder her. Pflichten laufen in jeder Stufe weiter: Notreserve, Einspeise-Deckel, Zellpflege, das Zurückstellen angehobener Sollwerte und die Netzdeckung deiner Batterie.

## 0.8.9

- **Ein ausgefallener Leistungssensor bremst die Regelung nicht mehr aus.** SEA hat einen Sensor, der „nicht verfügbar" meldet, bisher als „0 Watt" gelesen und das Gerät deshalb dauerhaft mit nur rund einem Fünftel des Überschusses angesteuert, während der Rest ins Netz ging. Jetzt unterscheidet SEA „das Gerät ist aus" von „ich sehe das Gerät nicht", regelt in dem Fall auf dem quittierten Sollwert weiter und sagt es in der Warum-Zeile und als Hinweis auf „Heute".
- **Ein Gerät, das die zugeteilte Leistung nicht abnimmt, blockiert sie nicht mehr für die anderen.** Nimmt ein Teilnehmer über drei Minuten deutlich weniger, als SEA ihm befiehlt — etwa die Batterie, die kurz vor voll abregelt —, wird sein Anspruch auf das gekappt, was er wirklich schafft; der Rest fließt an das nächste Gerät in der Prioritätenliste, statt eingespeist zu werden. Kann er später wieder mehr, wächst er von selbst zurück.

## 0.8.8

- **Ein Ziel für den Tag — und es bewirkt wirklich etwas.** Auf „Heute" wählst du, worauf es dir ankommt (wenig Geld ausgeben, wenig Netzstrom, wenig einspeisen); SEA spielt den Prognosetag mit jeder Einstellungs-Variante durch, sortiert sie nach diesem Ziel und wirft alles raus, was deine Anforderungen verletzt (Reserve, Auto-Frist) — egal wie günstig es wäre. Die Siegervariante lässt sich per Knopf wirklich übernehmen; Varianten, die SEA noch nicht einstellen kann, sagen das offen, statt es zu versprechen. Von allein ändert sich nichts.
- **Jedes Gerät hat jetzt eine Absicht statt eines Schalter-Baukastens.** Bei Wallbox, Heizstab, Wärmepumpe, Batterie und Verbrauchern steht oben eine Auswahl („Nur mit Sonnenstrom laden", „Immer laden — PV zuerst, Rest aus dem Netz", …); SEA setzt die passenden Einstellungen selbst, der Rest liegt unter „Erweitert". Wer dort etwas von Hand ändert, sieht ehrlich „Angepasst" — die Absicht behauptet nie mehr, als die Einstellungen wirklich tun. Prioritäten-Reihenfolge und Wechselrichter-Modus bleiben unangetastet.
- **Dashboard und Tagesplan sind zu einer Seite „Heute" verschmolzen.** Beide zeigten dieselbe Vorausschau — jetzt stehen die aktuelle Lage und der Plan für heute untereinander auf einer Seite, sodass „Jetzt aktiv" und „Aktuell" gar nicht mehr auseinanderlaufen können; die geplanten Fenster (Warmwasser, verschiebbare Geräte) hängen als Unterkarte am Plan.
- **Investitions-Analyse: was bringt mehr PV oder mehr Speicher?** Neu unter Einsparung: SEA spielt die aufgezeichneten Tage mit größerer Batterie bzw. mehr PV noch einmal durch (echte Regelung, je Tag einzeln) und rechnet daneben, was derselbe Zeitraum an der Börse gekostet hätte — jeweils als Ersparnis für den Zeitraum und hochgerechnet aufs Jahr.
- **Einsparung: Rückblick jetzt in Tages-Scheiben.** Ein Mehrtages-Vergleich simuliert jeden Tag einzeln — mit dem SoC, der an diesem Tag tatsächlich aufgezeichnet wurde — und summiert die Kosten; ein früher falscher Ladestand verfälscht damit nicht mehr alle Folgetage. Die Baseline läuft dabei unter den Einstellungen, die damals wirklich aktiv waren, sodass Baseline und Variante direkt vergleichbar sind.
- **Einsparung rechnet jetzt auf dem reinen Hausverbrauch.** Die Rückblick-Vergleiche fahren die aufgezeichnete Basis-Last (SEAs steuerbare Lasten sind schon beim Aufzeichnen abgezogen), statt sie nachträglich zu rekonstruieren — die Szenarien entscheiden diese Lasten damit sauber neu, statt die alten Einstellungen mitzuschleppen. Ältere Aufzeichnungen nutzen weiter die bisherige Rekonstruktion.
- **Ein Debug-Download über den eingestellten Zeitbereich.** Der Verlauf-CSV enthält jetzt alles zum Eingrenzen einzelner Regelartefakte: Messdaten (inkl. reinem Hausverbrauch + Preis), SEAs Eingriffe (Sollwerte UND Schalten) und angehängt die zeitgestempelten Einstellungs-/Eingriffs-Änderungen (auch manuelle Kuratierung) — in einem Download. Der separate „Einstellungen-CSV"-Knopf entfällt.
- **Datensicherung enthält die manuelle Kuratierung.** Backups (und die Backup-Historie) sichern jetzt auch die Include/Exclude-/Rollen-Overrides mit — das komplette aktuelle Set, sauber wiederherstellbar.
- **Alle Steuer-Eingriffe protokolliert (auch Schalten).** Bisher wurden nur Sollwert-Eingriffe mit Zeitstempel gespeichert; jetzt auch Ein/Aus-Schaltungen — der Verlauf/CSV zeigt jede Aktion, die SEA ausgeführt hat.
- **CSV-Export erweitert + Einstellungs-Historie herunterladbar.** Der Verlauf-CSV enthält jetzt zusätzlich den reinen Hausverbrauch und den Preis; ein neuer Knopf „Einstellungen-CSV" lädt die zeitgestempelten Einstellungs-/Konfig-Änderungen (fürs Debugging: was war wann aktiv).
- **Fundament für faire Szenario-Vergleiche: reiner Hausverbrauch wird aufgezeichnet.** Zusätzlich zum Gesamt-Hausverbrauch speichert SEA jetzt den Grundverbrauch OHNE die von SEA gesteuerten Lasten (Heizstab, Wallbox, schaltbare Verbraucher) — damit ein Rückblick-Vergleich diese Lasten unter anderen Einstellungen sauber neu durchrechnen kann, statt die alten Entscheidungen mitzuschleppen.
- **Vollständige Einstellungs-Historie.** SEA hält jetzt einen zeitgestempelten Verlauf der plan-relevanten Einstellungen (bei jeder Änderung) vor — Grundlage, um später Szenarien exakt gegen die real aktiven Einstellungen zu vergleichen.
- **Tagesplan: „Was-wäre-wenn" mit Kosten-Delta.** Unter dem Plan stehen durchgerechnete Alternativen (z. B. Batterie als Backup halten, Auto zuerst laden) mit den Mehrkosten (+) oder der Ersparnis (−) für heute gegenüber dem aktuellen Plan — je Zeile ein echter Simulationslauf.
- **Tagesplan: Heizstab in der Wärme-Spur.** Der Heizstab lädt denselben Warmwasser-Speicher wie die Wärmepumpe (thermisch) — er erscheint jetzt in der Spur „Wärme" statt „Geräte".
- **Tagesplan an HA-Sprachausgabe.** Wähle eine HA-Voice-Entität (Assist-Satellit oder Notify-Ziel) per Auswahl; ein Knopf lässt SEA das Tagesplan-Briefing dort ansagen.
- **Tagesplan mit Morgen-Briefing zum Vorlesen.** Eine sprechbare Zusammenfassung des Tages (aktuelle Strategie, wann die Batterie deckt bzw. das Netz zieht, Batterie-Tiefststand, erwartete Kosten und Autarkie) steht jetzt oben am Tagesplan — mit „🔊 Vorlesen"-Knopf (Browser-Sprachausgabe).
- **Tagesplan mit Anforderungs-Leiste.** Auto-Frist (fertig um + Ziel-SoC), Warmwasser-Komfort und Mindest-Reserve stehen jetzt direkt am Tagesplan — Änderungen werden gespeichert und der Plan sofort neu gerechnet.
- **Neuer Menüpunkt „Tagesplan".** Ein eigener Bildschirm nach dem Dashboard zeigt den Plan für heute als Spuren-Ansicht: Preis-Band (Bezug + Einspeisung), PV und Verbrauch, Batterie-Ladestand als Kurve und je Speicher/Last eine Spur (Strategie, Batterie, Wärme, Auto, Geräte) — Klick auf einen Block zeigt das Warum.
- **Tagesplan mit Kosten-Kopf.** Oben stehen jetzt die erwarteten Kosten des Tages, Netzbezug/Einspeisung, Autarkiegrad und PV-Eigenverbrauch — direkt aus dem simulierten Tagesverlauf und deinen Preisen.

## 0.8.7

- **Ausblick spricht dieselbe Sprache wie „Aktuell“.** Die Phasen verwenden jetzt die Strategie-Bezeichnungen aus dem Feld „Aktuell“ (z. B. „PV-Überschuss: Eigenverbrauch und Speicherung“, „Batterie deckt Netzbezug“) statt eigener Fluss-Begriffe („Batterie lädt“) — „Jetzt aktiv“ liest sich damit identisch zur aktuell laufenden Strategie.
- **Ausblick unterstellt kein nicht-angestecktes Auto mehr (Standard).** Bisher nahm der Ausblick standardmäßig an, ein konfiguriertes Fahrzeug hänge „ab jetzt“ an der Wallbox, und lud es — das erzeugte Netzbezug und eine leer werdende Batterie, die live gar nicht existieren. Jetzt spiegelt der Ausblick die Realität (Auto nicht angesteckt); die „Was, wenn ab jetzt angesteckt“-Vorschau bleibt als Opt-in.
- **Ausblick: invertiertes Vorzeichen von Netz/Batterie berücksichtigt (Fehler behoben).** Hattest du in der Konfiguration die Vorzeichen-Umkehr für Netz- oder Batterieleistung aktiviert, drehte die Simulation die Flussrichtung um — eine **ladende** Batterie wurde als **entladend** gerechnet (und Einspeisung als Netzbezug). Der Ausblick berücksichtigt die Invert-Einstellungen jetzt korrekt und zeigt dieselbe Stromrichtung wie „Aktuell".
- **Ausblick „Jetzt aktiv" spiegelt zuverlässig den Ist-Zustand.** Deckt die Batterie gerade nur kurz (z. B. fast leer bei niedrigem SoC, in Minuten entladen), wurde diese kurze Startphase bisher als „Splitter" verworfen und der Ausblick sprang zur nächsten Phase (Laden/Netzbezug) — passte damit nicht zu „Aktuell". Die gerade laufende Phase bleibt jetzt immer erhalten, sodass „Jetzt aktiv" mit „Aktuell" übereinstimmt.
- **Ausblick startet exakt beim Ist-Zustand (Fehler behoben).** Der erste Balken übernimmt jetzt die momentane PV- und Verbrauchsleistung aus der Live-Bilanz (dieselbe Quelle wie „Aktuell") statt eines 10-Minuten-Mittels der Historie — das hinkte beim morgendlichen PV-Anstieg hinterher und zeigte „Netzbezug", während live gerade eingespeist und die Batterie geladen wurde. Jetzt stimmt „Jetzt aktiv" mit „Aktuell" überein.
- **Ausblick erklärt „Jetzt aktiv" („Warum?").** Unter „Jetzt aktiv" steht jetzt die Begründung der Regelung zum gezeigten Zeitpunkt (wie im Feld „Aktuell") — z. B. „Netzbezug decken [geregelt]", „Notstromreserve laden" oder „… → Reserve 30 %" —, sodass sofort erkennbar ist, warum die Batterie deckt, lädt oder das Netz das Haus deckt.
- **Reglerprotokoll nennt die begrenzende Grenze.** Wird ein Sollwert durch eine Grenze gekappt (z. B. Reserve, SoC-Max, Netzanschluss), steht diese jetzt in der Begründung, statt einen Wert auszuweisen, der gar nicht geschrieben wurde.
- **PV-Überschuss-Anhebung weicht der Batterie (Fehler behoben).** Die Warmwasser-/WP-Anhebung griff im Ausblick über Stunden und zog sich dabei den Überschuss, den eigentlich die höherpriore Batterie laden sollte — jetzt hält sie sich zurück, solange die Batterie noch Ladebedarf hat, und startet erst mit echtem Rest-Überschuss.
- **Ausblick startet mit dem aktuellen Batterie-Fluss.** Deckt die Batterie gerade den Netzbezug, beginnt der Ausblick jetzt genau damit, statt die Deckung im ersten Schritt „von 0" hochzuregeln und so einen Phantom-Netzbezug am Anfang zu zeigen.
- **Ausblick-Kurve zeigt den simulierten Batterie-Ladestand.** Im Kurvenplot unter dem Zeitstrahl liegt jetzt zusätzlich die simulierte SoC-Linie (0–100 %, rechte Achse) — der Lade-/Deck-Verlauf ist direkt neben PV und Verbrauch ablesbar.
- **Ausblick zeigt die angesetzte PV- und Verbrauchskurve.** Unter dem Zeitstrahl liegt jetzt ein kleiner Kurvenplot (kW über den Tag) mit den PV- und Grundlast-Werten, die der Ausblick tatsächlich simuliert — so ist sofort ablesbar, ob z. B. die PV nachts korrekt 0 ist und welche Last angenommen wird.
- **Ausblick zeigt den Batterie-Tiefststand.** Der Ausblick nennt jetzt, wann und wie tief die Batterie voraussichtlich am stärksten entladen ist (z. B. nachdem sie den Netzbezug über Nacht gedeckt hat) — den SoC-Tiefpunkt, den die Phasen-Balken bisher nur andeuteten.
- **Fluss-Plausibilitätswächter: warnt bei unmöglichem Energiefluss.** Zieht ein einzelner Verbraucher mehr Leistung als das ganze Haus misst (oder ergeben die gemessenen Verbraucher zusammen mehr als der Netzzähler), ist das physikalisch unmöglich — ein sicheres Zeichen für eine falsche Netz-Messung (z. B. ein falsch aufgelegter Stromwandler oder eine fehlende Phase, sodass ~1/3 jeder Drehstrom-Last wie Wallbox/Wärmepumpe im Netzwert fehlt). SEA zeigt das jetzt als Warnung auf dem Dashboard mit konkretem Hinweis (Stromwandler/Phasen prüfen), statt ein unmögliches Flussbild zu zeichnen.
- **Zeitzone von Home Assistant übernommen (Fehler behoben).** Das Add-on lief bislang in UTC — dadurch waren alle uhrzeitabhängigen Entscheidungen (Hoch-/Niedertarif-Fenster, das stunden­genaue Lastprofil, der Ausblick-Zeitstrahl) und die angezeigten Zeiten gegenüber der lokalen Uhr verschoben. SEA übernimmt jetzt die in Home Assistant eingestellte Zeitzone (beim Verbinden aus der HA-Konfiguration, zusätzlich früh beim Start), sodass Uhrzeiten und Prognose wieder zur echten Ortszeit passen.
- **Zielgetriebene Planung (Grundlage).** Neu ist eine Ebene über der Vorausschau, die ein übergeordnetes Ziel verfolgt statt nur Knöpfe zu vergleichen: Du gibst ein Ziel vor (geringste Kosten, größte Eigenversorgung oder maximaler Eigenverbrauch) plus harte Randbedingungen (Batterie-Reserve nicht unterschreiten, Auto bis zur Abfahrt geladen, Warmwasser über einer Komforttemperatur). SEA spielt alle Szenarien über den Prognosetag durch, sortiert sie so, dass zuerst die zulässigen (keine Randbedingung verletzt) und darunter das beste Ziel-Ergebnis steht — und erklärt, warum. Es ändert dabei nichts selbst, sondern empfiehlt.
- **Verschiebbare Verbraucher terminieren.** Für eine startbare Last (Waschmaschine, Spülmaschine …) findet SEA in der Prognose das günstigste bzw. „grünste" Zeitfenster — unter Beachtung von frühestem Start und Frist — und nennt Startzeitpunkt, den nötigen Netzbezug und den dabei genutzten PV-Überschuss.

## 0.8.6

- **Speichergrößen werden aus der Historie geschätzt.** Für Warmwasser-Speicher (und WP-Warmwasser) mit Temperatur- und Leistungssensor schätzt SEA aus vergangenen Aufheiz-Phasen die Wärmekapazität (≈ Volumen), den Wirkungsgrad und den Standby-Verlust — und speist diese Werte automatisch in Ausblick und Einsparung, sodass der Heizstab dort einen echten Speicher füllt und am Zielwert stoppt, statt als einfache Last zu gelten. Werte müssen nicht mehr von Hand gesetzt werden.
- **Robust ohne verknüpfte Geräte.** Fehlt ein Gerät oder ist es nicht mit Entitäten verknüpft (keine PV-Anlage, keine Wallbox, kein WP-Temperaturfühler …), rechnen Ausblick und Einsparung trotzdem sauber weiter: ohne PV-Gerät wird die PV-Prognose über eine Ersatz-Größe eingespeist, und Geräte ohne Sensor-Historie werden bei der Größen-Schätzung einfach übersprungen.
- **Mehrere geregelte Geräte korrekt berücksichtigt.** Hast du mehr als eine geregelte Last (z. B. Heizstab und künftig Wallbox), zieht die Analyse jetzt alle davon aus der Basislast ab, statt nur die stärkste — so wird nichts doppelt gezählt.
- **Ausblick und Einsparung rechnen jetzt mit der ganzen Anlage.** Beide fuhren bisher ein vereinfachtes Ersatzmodell (Batterie + stärkste regelbare Last + eine Wallbox + eine WP-Anhebung). Jetzt spielen sie einen Klon der kompletten Konfiguration mit der echten Regel-Logik durch — alle Verbraucher, Warmwasser-Speicher, Fahrzeug und Wärmepumpe so, wie sie wirklich geregelt werden. Voraussetzung ist ein konfiguriertes PV-Gerät (dorthin wird die PV-Prognose eingespeist). Die Szenarien der Einsparung (z. B. „Auto zuerst/zuletzt laden", „Warmwasser über Wärmepumpe/Heizstab") werden weiterhin verglichen und preislich gereiht.
- **Fundament: die Simulation kann jetzt die ECHTE Konfiguration klonen und fahren.** Statt eines handgebauten Teilmodells lässt sich die komplette Anlagen-Konfiguration losgelöst kopieren (ohne die echten Einstellungen zu berühren) und mit der echten Regel-Logik gegen ein virtuelles Anlagenmodell durchrechnen — Batterie, schaltbare/regelbare Verbraucher, Warmwasser-Speicher (thermisch, mit Abschalten am Zieltemperatur-Wert), Fahrzeug/Wallbox (Ladung bis Ziel-SoC) und Wärmepumpen-Boost inklusive, mit je Szenario überstellbaren Parametern. Damit teilen Vorausschau und echte Ausführung dieselbe Logik; darauf setzt später der zielgetriebene Szenarienvergleich auf. (Noch ohne sichtbare Änderung.)
- **Genauerer Ausblick: die Vorausberechnung nutzt jetzt durchgängig die simulierte Zeit.** Die Zeit-abhängigen Teile (Hochtarif/Niedertarif-Preis, „ist der Tarif gerade günstig?") lasen bisher die echte Uhr statt der Zeit des simulierten Tages — dadurch konnten Tarif-Fenster und Fristen im Ausblick zur falschen Tageszeit greifen. Jetzt folgt alles der vorgegebenen Zeit. (Fundament dafür, dass Simulation und echte Ausführung dieselbe Regel-Logik teilen.)
- **Money-Guard: Warnung, wenn die Regelung gerade Geld verliert.** Ein Wächter prüft laufend die Live-Bilanz gegen den Tarif und meldet auf dem Dashboard vier Fälle mit Symptom und wahrscheinlicher Ursache: Batterie lädt aus dem Netz ohne günstiges Tarif-Fenster, Netzbezug trotz PV-Überschuss, Batterie speist gespeicherte Energie unter Einkaufspreis ins Netz, und Batterie-Roundtrip ohne Tarifvorteil. Er **greift nicht in die Regelung ein** — nur erkennen und melden (mit Entprellung gegen Fehlalarme). Wo die Ursache eindeutig auf eine Einstellung zeigt, bietet das Banner einen **„Beheben"-Knopf** (mit Rückfrage) an, der die betreffende Einstellung anpasst (z. B. Tarif-Netzladen abschalten, Zyklenkosten anheben) — **du** löst es aus, nie automatisch.
- **Hierarchie: doppelt erfasste Lasten werden nicht mehr doppelt gezählt.** War ein Verbraucher sowohl als Komponente als auch als kuratierte Entität erfasst, zählte die Hierarchie ihn zweimal — dadurch konnte ein „Rest der Leistung"-Knoten fälschlich auf 0 fallen. Solche Doppel werden jetzt erkannt und übersprungen.
- **Ausblick beginnt jetzt beim Ist-Zustand.** Der erste Balken der Prognose passte manchmal nicht zu „Aktuell" (z. B. „Aktuell" lud die Batterie, der Ausblick sagte gleich „Batterie deckt Bezug"), weil die stündliche PV-Prognose für die laufende Stunde oft unter der aktuellen PV liegt. Jetzt werden PV und Last der letzten 10 Minuten (gemittelt, gegen Ausreißer) in die erste Stunde eingeblendet und laufen über eine Stunde in die Prognose über — der erste Balken stimmt mit dem aktuellen Zustand überein.
- **Sankey mit Zwischenebenen.** Gruppierte Verbraucher (z. B. „Heizung" mit Wärmepumpe + Heizstab) erscheinen im Sankey jetzt als eigener Balken in einer mittleren Spalte, der sich zu seinen Kindern verzweigt (Haus → Gruppe → Geräte); einzelne Lasten laufen wie bisher direkt von Haus zum Endpunkt. Ohne Hierarchie bleibt es ein flaches Diagramm. (Handy-Ansicht zeigt Gruppen vorerst als einzelne Balken.)
- **Verbraucherkarte aufgeräumt + Energiefluss klickbar.** Die Zeile „Leistung" steht jetzt direkt unter dem Namen (wichtigste Größe zuerst) und wird über den Stift bearbeitet (statt „Bearbeiten"-Knopf); sie zeigt kompakt den Sensor + die Zuordnung („Teil von …", „Rest von …", „Summe aus …"). Die Energie-Entität braucht keinen eigenen Namen mehr. Im Energiefluss öffnet ein Klick auf einen Verbraucher-Knoten (nicht Haus) direkt dessen Einstellungskarte. Der „Rest"-Knoten wird im Fluss zuverlässig aus der Hauslast berechnet.
- **„Rest der Leistung"-Knoten zeigt im Energiefluss jetzt den echten Rest.** Ein Knoten wie „Wohnung Ne" (Rest des Hauses) hat keinen eigenen Sensor — im Fluss-Diagramm blieb er darum bei 0 W ohne Linie. Jetzt übernimmt der Fluss für Rest-/Summen-Knoten die berechnete Leistung (Hauslast − gemessene Verbraucher) und zeichnet die Flusslinie. Solche Knoten werden außerdem nicht mehr in „Weitere Verbraucher" zusammengefasst, sondern als eigener benannter Bereich gezeigt.
- **Fehler behoben: Hierarchie-Zuordnung ging verloren, wenn ein Verbraucher auf „Rest der Leistung" stand.** Ein „Rest"-Knoten direkt unter „Haus" (ohne übergeordneten Zähler) ließ die interne Berechnung abstürzen — dadurch zeigte das Zuordnungs-Popup nur noch „Haus" und keine übergeordneten Verbraucher mehr. Solche Fälle werden jetzt sauber abgefangen (der Knoten fällt auf „eigener Sensor" zurück, mit Hinweis), die Auswahl funktioniert wieder.

- **Hierarchie-Zuordnung je Verbraucher (Editor).** In den **Komponenten** hat jetzt jedes Gerät im Leistungs-Block eine Zeile „Leistung & Zuordnung" mit **Bearbeiten**-Popup: dort wählt man die **Leistungsquelle** (eigener Sensor mit Entität · Summe der Kinder · Rest der Leistung) und den **übergeordneten Knoten** (Wurzel = „Haus", derselbe Name wie in den Diagrammen). So lassen sich z. B. Heizstab, Wärmepumpe und Wallbox unter einen gemeinsamen Knoten „Heizung"/„Zähler" hängen — auch reine Zähler-/Gruppenknoten **ohne** Stellglied sind auswählbar. Eine oder **mehrere** Leistungs-Entitäten werden jetzt **im selben Popup** gewählt (mehrere werden summiert — z. B. zwei als ein Gerät geregelte Wärmepumpen; das frühere separate Leistungs-Feld entfällt für diese Geräte); die aktuelle Zuordnung steht einzeilig an der Karte, falsch verdrahtete Zähler werden als Warnung angezeigt. (Gilt für alle Gerätearten inkl. Wärmepumpe.)
- **Verschachtelte Verbraucher im Energiefluss.** Sind Verbraucher einem übergeordneten Knoten zugeordnet, erscheinen sie im Fluss-Diagramm gebündelt unter diesem Knoten (z. B. „Heizung" mit Heizstab + Wärmepumpe) — aufklappbar wie schon „Weitere Verbraucher". Ohne konfigurierte Hierarchie bleibt die Darstellung unverändert.
- **Verbraucher-Einstellungen jetzt im Backup enthalten.** Die Konfiguration der „weiteren Verbraucher" (bisher in einer separaten `consumers.json`) wird beim ersten Start automatisch in den zentralen Einstellungs-Speicher überführt — damit wird sie ab jetzt auch mitgesichert und mit-wiederhergestellt. Die alte Datei bleibt unangetastet liegen; nichts geht verloren.
- **Verbraucher-Hierarchie (Grundlage).** Verbraucher können jetzt einem übergeordneten Knoten zugeordnet werden (z. B. Heizstab und Wallbox hinter einer gemeinsamen Messung, Geräte unter einem Unterzähler, Auto an Wallbox). SEA rechnet die Leistung je Knoten korrekt auf — gemessen, als Summe der Kinder oder als Rest unter einem Zähler — und zählt nichts doppelt; falsch verdrahtete Unterzähler werden erkannt und gemeldet. In dieser Version steckt die Grundlage im Hintergrund (Datenmodell + Auflösung); der Baum-Editor und die verschachtelte Anzeige folgen als nächstes.

## 0.8.5

- **Ausblick/Einsparung modellieren das Netzladen jetzt mit der PV-Schwelle.** Die Vorausberechnung fuhr die Wallbox bisher immer als „nur PV-Überschuss", auch wenn real „Laden aus dem Netz erlaubt" eingestellt ist — sie zeigte dadurch das Netzladen gar nicht und die PV-Schwelle blieb in der Prognose folgenlos. Jetzt übernimmt die Simulation die echte Lade-Betriebsart samt PV-Schwelle: nachts kein Netzladen, tagsüber ab der Schwelle — konsistent mit der Live-Regelung.
- **Wallbox-„PV-Schwelle" wirkt jetzt als Netzlade-Untergrenze.** Im Modus „Laden aus dem Netz erlaubt" lädt die Wallbox nur noch, wenn der verfügbare PV-Überschuss (über der Grundlast) die eingestellte PV-Schwelle erreicht. Damit bleibt der Netzanteil begrenzt (Netz ≈ Ladeleistung − Überschuss − Batterie): Bei z. B. 4 kW Schwelle, 11 kW Ladeleistung und 3,3 kW Batterie bleibt der Netzbezug ≈ 3,7 kW; unterhalb der Schwelle wird gar nicht aus dem Netz geladen. Eine nachrangige Last (Heizstab) hungert die höherpriore Wallbox nicht mehr unter die Schwelle. Bisher war die PV-Schwelle in diesem Modus wirkungslos (die Wallbox lud unabhängig vom PV-Überschuss).
- **Sicherheit: kein Netzladen der Wallbox bei unbekanntem Fahrzeug-SoC.** Ist für die Wallbox „Laden aus dem Netz erlaubt" aktiv und ein Ziel-SoC gesetzt, aber der Fahrzeug-SoC gerade **nicht lesbar** (z. B. direkt nach einem Add-on-Neustart, bevor Home Assistant die Fahrzeug-Zustände synchronisiert hat, oder wenn die SoC-Entität kurz „unavailable" ist), lädt SEA jetzt **nicht** aus dem Netz. Bisher konnte in diesem Fenster ein unbekannter SoC unkontrolliertes (Nacht-)Netzladen auslösen, das sich über den Ziel-SoC nicht stoppen ließ (Feldvorfall 13.07.: ein Neustart um 00:48 schaltete die Wallbox ein). Sobald der SoC wieder lesbar ist, greifen Ziel-SoC-Stopp und PV-Schwelle wie gewohnt.

- **Spar-Analyse: Wärmepumpen-COP jetzt korrekt bewertet.** Die WP-Anhebung (Warmwasser über die Wärmepumpe) wurde bisher wie resistive Wärme mit import÷COP bewertet — obwohl 1 kWh Strom in der WP **COP kWh Wärme** macht. Damit war die WP-Anhebung um den Faktor COP unterbewertet, und die Analyse riet fälschlich „lieber in die Batterie speichern". Jetzt zählt die WP-Anhebung mit dem vollen Bezugspreis (die WP erzeugt die Wärme so günstig, wie sie sonst aus dem Netz käme), der Heizstab weiter mit import÷COP — die effiziente WP schlägt den Heizstab, wie erwartet. Zusätzlich: Variante „Auto-Ziel-SoC auf 100 %", das Geräte-Tausch-Szenario **„Warmwasser über Wärmepumpe" vs. „über Heizstab"** (wenn beide WW machen — das eine Gerät an, das andere aus) und eine Kosten-Aufschlüsselung pro Variante (Tooltip: Bezug/Einspeisung/Wärme/WP-Anhebung/Auto + Batterie).

- **Einsparungs-Analyse (Vorschau) auf dem Detailgrad des Ausblicks — mit mehr Stellgrößen.** Die 24-h-Vorschau der Spar-Analyse simuliert jetzt dasselbe volle Modell wie der Ausblick: **Fahrzeug, WP-Anhebung und Batterie-Deckung** kommen mit, und alle simulierten Senken (v. a. die Wallbox) werden aus der Grundlast herausgerechnet — damit fällt der bisherige Phantom-Nachmittags-Verbrauch auch hier weg. Die €-Bewertung berücksichtigt zusätzlich die WP-Boost-Wärme und die ins Auto geladene Energie. Zusätzlich vergleicht die Analyse jetzt weitere **Prioritäts-Varianten**: „Auto zuerst/zuletzt laden" (Auto vor oder nach der Hausbatterie) und „WP-Anhebung bevorzugt/nachrangig" — so sieht man in €, ob eine andere Reihenfolge günstiger wäre. Der Rückblick spielt die tatsächlich aufgezeichneten Tage weiter nach (mit Batterie-Deckung).

- **Ausblick: Batterie deckt jetzt auch in der Simulation den Bezug.** Bisher hatte die Sim-Batterie die „Netzbezug-Deckung" nicht — jedes Defizit erschien sofort als „Netzbezug", obwohl die echte Batterie es (bis zur Reserve) abdeckt. Die Sim-Batterie übernimmt jetzt die Deckungs-Einstellung und die Reserve der echten Batterie, sodass Defizite korrekt als „Batterie deckt Bezug" (bis zur Reserve) und erst danach als „Netzbezug" erscheinen.

- **Ausblick: Wärmepumpen-Anhebung als eigene Phase.** Die Zeitraffer-Simulation umfasst jetzt auch die **Sollwert-Anhebung der Wärmepumpe** (thermisches Speicherladen): der echte Boost-Regler hebt im Ausblick den Heizkreis-Sollwert, wenn der Überschuss über der Schwelle hält, und die WP zieht dann Mehrleistung — als eigener Balken „…-Anhebung" im Strahl. Damit sind alle regelbaren Senken (Batterie, regelbare Last, Fahrzeug, WP-Anhebung) abgebildet.

- **Ausblick erscheint jetzt auch ohne separate regelbare Last.** Bisher brauchte die Zeitraffer-Simulation eine regelbare Batterie **und** eine zusätzliche modulierende Last — wer nur Batterie + Wallbox/Fahrzeug (und eine Wärmepumpe im Boost-Modus) hat, sah dauerhaft „Noch kein Tagesplan". Jetzt simuliert der Ausblick auch die reine Kombination Batterie + Fahrzeug. Ein ladbares Fahrzeug wird zudem korrekt als **Fahrzeug** erkannt (eigene Ladephase, Ziel-SoC-Stopp) statt als generische Last. Die Leer-Meldung nennt jetzt den echten Grund (fehlende PV-Prognose / keine regelbare Batterie / wird gerade berechnet).

- **„Aktuell"-Karte + Ausblick aufgeräumt.** Die Kachel **„Verbrauch"** (Hausverbrauch) erscheint jetzt genau dann, wenn sie zählt — bei Deckung aus der Batterie oder im Neutralbereich (PV deckt das Haus) — nicht beim Laden/Einspeisen. Ein Gerät, das eine Strategie nur noch **abgeschaltet hält** (z. B. „Wallbox: Ziel-SoC erreicht"), wird als Grund fürs Auslaufen kurz gezeigt, aber nicht mehr dauerhaft; ist eine Strategie danach ohne aktives Gerät, verschwindet sie aus der Leiste. Der Button **„Neu planen"** sitzt jetzt oben rechts in der Ausblick-Karte. Der irreführende Planer-Hinweis „Batterie nur teilweise aus PV planbar" entfällt — die Batterie (und das Fahrzeug) werden im Ausblick von der echten Engine simuliert, nicht mehr zusätzlich vom Planer als Aufgabe geführt.

- **Ausblick simuliert jetzt auch die Wallbox/das Fahrzeug.** Die Zeitraffer-Simulation der echten Regelung umfasst nun die Wallbox — sowohl **modulierend** (Ladeleistung folgt dem Überschuss) als auch **geschaltet** (an/aus, bei Bedarf mit **Batterie-Entladung als Ladeunterstützung**, sobald genug PV da ist). Weil es die echte Logik ist, stimmen „Auto lädt erst ab Überschuss-Schwellwert" und der Stopp bei erreichtem Ziel-SoC von selbst; im Zeitstrahl erscheint eine eigene **Fahrzeug-Phase**. Ist das Auto gerade **nicht angeschlossen**, nimmt der Ausblick an, es hängt ab jetzt an der Wallbox (mit Hinweis „bitte rechtzeitig anschließen") — per Klick lässt sich diese Annahme verwerfen, dann wird der Ist-Zustand ohne Fahrzeug simuliert.

- **Ausblick-Zeitstrahl: kompaktere Rand-Labels, 5-Minuten-Zeiten.** Der erste Balken zeigt nur „bis HH:MM", der letzte nur „ab HH:MM" (statt des ganzen Intervalls, das an den Rändern ohnehin offen ist). Alle Uhrzeiten auf volle 5 Minuten gerundet.

- **Ausblick: aktueller Zustand + lückenloser Zeitstrahl.** Ganz oben steht jetzt „Jetzt aktiv: … (voraussichtlich bis ~HH:MM)", und die laufende Phase ist im Strahl hervorgehoben. Ruhige Zeitfenster, in denen die PV gerade den Verbrauch deckt (weder Laden noch Bezug), erscheinen als eigene Phase „Eigenverbrauch" — der Strahl hat dadurch keine Löcher mehr.

- **Ausblick-Zeitstrahl als Wasserfall.** Jede Strategie-Phase steht jetzt in einer eigenen Zeile, zeitlich versetzt, mit Klartext-Label und Uhrzeit daneben (oder im Balken). Die gerade laufende Strategie beginnt bei „jetzt", ist hervorgehoben und mit „jetzt aktiv" markiert — so sieht man auf einen Blick, wie lange sie voraussichtlich aktiv bleibt und was danach kommt.

- **Karte „Ausblick" mit Strategie-Zeitstrahl (aus der echten Regelung).** Statt einer nachgebauten Näherung fährt SEA die **echte Regel-Engine im Zeitraffer** über den Prognosetag (PV-Prognose + gelerntes Verbrauchsprofil des Hauses, vom aktuellen SoC aus) und zeichnet die dabei getroffenen Entscheidungen als **Balken-Zeitstrahl**: wann die Batterie lädt, wann eine regelbare Last (z. B. Heizstab) den Überschuss bekommt, ab wann die Batterie den Bezug deckt und ab wann Netzbezug erwartet wird — plus die Planer-Fenster für Auto/Verbraucher/WW-Anhebung. Weil es dieselbe Logik wie die Live-Regelung ist, stimmen alle Randbedingungen (z. B. „Auto erst ab Überschuss-Schwellwert") von selbst. Kurze Textzeilen fassen zusammen, ab wann Batterie-Deckung bzw. Netzbezug beginnt. Reine Vorschau — die 10-s-Regelung bleibt die letzte Instanz.

- **Einheitliche Karten-Gliederung auf allen Seiten.** Jeder Abschnitt sitzt jetzt in einer gerahmten Karte mit größerer Überschrift (ohne Trennstrich) — auch Verlauf („Leistung & Prognose", „Weitere Messgrößen"), Einsparung („Ergebnis", „Energiebilanz im Zeitraum", „Analysen") und Strategien. Die **Info-Kacheln** sind neu gesetzt: Überschrift oben linksbündig, Wert mit Einheit darunter rechtsbündig, beide gleich groß (statt winziger Beschriftung unter einem riesigen Zahlenwert).

- **Drei abgesetzte Karten.** „Aktuell", „Ausblick" und „Energiebilanz" sind je eine große, gerahmte Karte mit Titel und Inhalten (Strategien + Info-Kacheln bzw. Plan bzw. Balken) darin — visuell klar getrennte Blöcke.

- **Dashboard aufgeräumt.** Direkt unter dem Diagramm eine Karte **„Aktuell"** mit den aktiven Strategien und dazu passenden Mini-Karten der *beteiligten* Größen: alle Leistungen > 200 W, Batterie- und (falls beteiligt) Fahrzeug-SoC, und die Temperaturen von Heizkreisen mit aktiver Anhebung. Die generischen KPI-Kacheln und die Rubrik „Aktive Steuerung" entfallen (waren redundant zur Strategie-Anzeige). Die **Energiebilanz (heute)** zeigt Autarkie- und Eigenverbrauchsquote als Balken über den kWh-Flüssen. Auf dem Handy ist das **Sankey** weniger stark gespreizt (Äste fächern über eine zentrierte Breite statt bis an die Ränder).

- **Aktive Strategien unter der Grafik.** Direkt unter dem Fluss-/Sankey-Diagramm zeigt eine farbig hinterlegte Leiste, welche Strategien gerade **operativ** sind und welches Gerät sie deswegen wie ansteuern — z. B. „PV-Überschuss → Batterie: regelbar 1560 W", „Batterie deckt Netzbezug → Entladung 580 W", „WP-Anhebung → Warmwasser +10 K → 60 °C". Farbe je Strategie wie im Verlaufs-Band.

- **Tagesplaner (Anzeige).** Neue „Heute geplant"-Übersicht: aus PV- und Preis-Prognose plant SEA die besten Zeitfenster für **Batterie**, **Auto** (mit Abfahrts-Deadline aus der Fahrzeug-Konfig — reicht die PV nicht, wird bis dahin das günstigste Netz eingeplant) und **einplanbare Verbraucher** (Waschmaschine/Spüler/Trockner). Priorität je Senke kommt aus der bestehenden Prioritäts-Liste. Verbraucher aktivierst du per Checkbox „In Tagesplanung einbeziehen"; auf dem Dashboard erscheint dann je Gerät ein Schalter „einplanen" — Energie und Dauer werden aus der **Leistungshistorie** des Geräts abgeleitet (keine Laufdaten → wird übersprungen, kein geratenes Profil). Button „Neu planen" für sofortige Neuberechnung. **Reine Anzeigestufe** — die 10-s-Regelung bleibt unverändert die letzte Instanz.

- **Kein Fehl-Start der WP-Anhebung durch Sensor-Transienten.** Die PV-Überschuss-Anhebung (thermisches Speicherladen der Wärmepumpe) startet erst, wenn der verfügbare Überschuss ~1 min anhält. Ein kurzer Ausreißer der WP-Leistung — z. B. wenn ein Heizstab die aus dem Zähler abgeleitete WP-Leistung beim Schalten transient springen lässt — löst die langsame thermische Anhebung nicht mehr aus. Halten und Beenden einer laufenden Anhebung bleiben unverändert reaktiv.

- **Strompreis-Chart spannt über den ganzen Zeitraum.** Beide Preislinien (eigener Tarif + Börse) reichen jetzt bis an beide Fenster-Ränder, statt am ersten/letzten Datenpunkt zu stoppen. Der Randwert ist der zuletzt *aktive* Preis (Stufenpreis korrekt gehalten, HT/NT-fähig über einen Carry-in-Punkt am Fensterstart). Damit wird auch bei starkem Hineinzoomen (Fenster < ~15 min zwischen zwei Preisänderungen) weiterhin eine gültige Linie gezeichnet statt nichts.

- **Kein Phantom-„PV-Überschuss" nachts.** Fällt nachts eine Last schlagartig ab, las SEA durch Sensor-Zeitversatz kurz einen Netz-Export, der größer war als die Batterie-Entladung — und wertete das als PV-Überschuss (kurzer Wechsel der Strategie auf „PV-Überschuss" samt kleinem Lade-Impuls in die Batterie). PV-Überschuss ist jetzt physikalisch auf die PV-Produktion begrenzt: bei PV ≈ 0 kann die Modulation nur zurückfahren, nie hochfahren — kein Phantom-Flip und keine Phantom-Ladung mehr. Grid-Laden (Tarif/Optimierer) bleibt unberührt.

- **Vollständigere Entscheidungs-Logs.** Jede Start/Stopp- und Richtungsentscheidung (Wechsel von/zu 0) steht jetzt im Log — auch wenn der Schreibvorgang gerade gedrosselt ist oder im Fehler-Backoff steckt (das war bisher unsichtbar und verbarg z. B. ein Zurücknehmen der Batterie-Deckung). Jede Batterie-Entlade-Entscheidung nennt zusätzlich den Grund und die Eingänge (warum 0 W bzw. warum geregelt). Log-Aufbewahrung erhöht.

- **Schnelleres Ausregeln bei plötzlichem PV-Einbruch.** Bricht die PV-Leistung während des Batterie-Ladens plötzlich ein (Wolke), wird die Ladung jetzt schneller zurückgenommen (asymmetrisch: runter schnell, rauf unverändert). Deutlich kleinere Bezugs-Spitzen — ohne die Schreibrate zur Batterie zu erhöhen. Im Replay der Aufzeichnung: Import −77 %, Spitze 4,4 → 1,8 kW.
- **Strategie-Status: Leerlauf zählt nicht mehr als operativ.** Eine Strategie, die nur einen Ruhewert neu setzt (z. B. „PV-Überschuss" mit Ladeleistung 0 nachts), erscheint jetzt korrekt als „aktiv" statt „operativ" — der operative Balken zeigt nur noch echte Eingriffe.
- **Strategie-Aktivierung entkoppelt & vereinheitlicht.** Jede Grid-/Batterie-Strategie (Batterie deckt Netzbezug, Bezugs-/Einspeise-Deckel, Notstrom-Reserve, Batteriepflege, Regeln) läuft jetzt unabhängig über ihren EIGENEN Schalter statt versehentlich am PV-Überschuss-Hauptschalter zu hängen — der Abschalten von PV-Überschuss legt sie nicht mehr still. Die Aktivierung liegt in einer einzigen deklarativen Tabelle (weniger Fehlerquellen).
- **Batterie-Konflikte prioritätsbewusst aufgelöst.** Bei gleichzeitigem Lade- und Entlade-Wunsch gewinnt die höherpriore Pflicht (z. B. Einspeise-Begrenzung vor Arbitrage-Entladung); eine harte Netzanschluss-Grenze wird als Untergrenze erzwungen, statt kurzzeitig überschritten zu werden.

- **Sankey mobil wieder lesbar.** Auf dem Handy ist der Haus-Kern jetzt kompakt und zentriert, die Quellen- und Verbraucher-Äste spreizen sich über die volle Breite und schwingen wieder zur Seite (statt senkrecht gerade zu laufen).

- **Einheitliche Linien-Icons statt Emojis.** Fluss-Ansicht, Sankey und das Tagesplan-Panel nutzen jetzt ein durchgängiges Linien-Icon-Set (Netz-Mast, Auto, Heizstab, Wärmepumpe, PV, Batterie, Haus, Verbraucher, Kalender) — plattformunabhängig statt Emoji. Der Netz-Kreis wird wieder gefüllt gezeichnet, und in aufgeklappten Unterkreisen ist die Leistung vertikal zentriert.

## 0.8.4

- **„Batterie deckt Netzbezug" läuft unabhängig vom PV-Überschuss-Schalter.** Die Batterie-Entladung zur Netzbezug-Deckung (und die Netzanschluss-Grenze) war fälschlich an den Hauptschalter „PV-Überschuss: Eigenverbrauch und Speicherung" gekoppelt. Wer PV-Überschuss abschaltete, legte damit unbeabsichtigt auch die Batterie-Deckung still — der Speicher stand still und das Haus bezog alles aus dem Netz, obwohl „Batterie deckt Netzbezug" aktiv war. Beide Strategien folgen jetzt ihrem eigenen Schalter; nur die batterie­gestützten Schaltlasten bleiben an den PV-Überschuss gebunden.

- **Netzbezug-Deckung gedämpft (kein Pendeln nachts).** Die Entladeleistung folgt dem Netzbezug jetzt über eine gedämpfte Regelung statt in einem Sprung auf den vollen Bezug. Ein zu großer Sprung konnte unter zeitversetzten Messwerten kurz überschießen, scheinbar einspeisen und die Überschuss-Regelung dagegen laden lassen — ein Lade-/Entlade-Pendeln. Die Dämpfung konvergiert ohne Überschwingen.

- **Version im Log beim Start.** Beim Add-on-Start wird die laufende Version einmal ins Log geschrieben — so ist im Log direkt ersichtlich, welche Version gerade läuft.

- **„Batterie deckt Netzbezug" nur operativ bei echter Entladung.** Das Halten der Batterie in
  Ruhe (0-Kommandos, während die PV das Haus deckt) gilt nicht mehr als operativ — der Balken
  zeigt jetzt nur die Zeiten echter Entladung.
- **Preis-Chart durchgängig.** „Mein Tarif" wird bis zum Fensterrand gezeichnet (der Zukunftspreis
  ist bekannt: statisch/HT-NT aus dem Modell, dynamisch aus der Preisprognose); die Börsenlinie
  hält den letzten veröffentlichten Wert bis zum Rand.

- **Weniger Log-Rauschen.** Die Tagesplan-Diagnosezeilen (kein Plan / Prognose-Slots) stehen jetzt nur noch auf Debug-Ebene; ein tatsächlich geplantes Anhebungs-Fenster wird wie bisher als Entscheidung geloggt.

- **Strategien starten zugeklappt.** Beim ersten Öffnen sind alle Strategie-Karten eingeklappt.

- **Hotfix: UI startete nicht.** Die neue gemeinsame Haus-Farbkonstante wurde nach der Serie
  deklariert, die sie nutzt — das brach beim Laden das gesamte UI-Skript (weiße/hängende Seite).
  Behoben; ein neuer automatischer Test fängt „Konstante vor Deklaration verwendet" künftig ab.

- **Haus überall cyan.** Die cyane Haus-Farbe des Sankey gilt jetzt auch im Fluss-Diagramm (Kreis)
  und im Verlauf (Serie „Haus") — eine gemeinsame Farbkonstante, konsistent über alle Ansichten.
- **Batterie-Plan bei voller Batterie.** Ist die Batterie bereits am Ziel-SoC, zeigt das Dashboard
  „Batterie bereits voll" statt einer sinnlosen Uhrzeit-Prognose.

- **Sankey wieder mit geschwungenen Bändern.** Die Kurven sind zurück (waren beim
  Erhaltungs-Fix verloren gegangen) — Quell-/Senken-Knoten stehen mit Abstand, die Bänder setzen
  am kompakten Haus-Balken lückenlos an; Breiten summieren sich weiterhin exakt, Farben kräftig.
- **Tagesplan auf dem Dashboard.** Die Prognose-Vorschau (Anhebungs-Fenster, Batterie-Vollzeit)
  steht jetzt als eigenes Panel „Heute geplant" über der aktiven Steuerung, nicht mehr in der
  Anhebungs-Strategiekarte (dort bleibt nur der WP-Starts-Zähler).
- **Kürzerer Eigenverbrauchs-Text.** Die Beschreibung der PV-Überschuss-Strategie ist auf zwei
  Zeilen gekürzt; die Details stehen im ℹ.

- **Sankey-Diagramm korrigiert und aufgefrischt.** Die Beitragsbreiten summieren sich jetzt exakt
  zur Gesamtbreite (links wie rechts) — die frühere Mindestbreite pro Fluss hatte die Erhaltung
  gebrochen. Bänder liegen lückenlos aneinander, Farben sind kräftiger (weniger grau), das Haus
  ist cyan; überlappende Beschriftungen kleiner Flüsse werden entzerrt.

- **Batterie ruht bei aktivem PV-Überschuss.** Die Netzbezugs-Deckung entlädt nicht mehr, während
  die PV das Haus deckt: Ein Totband (200 W) plus eine „PV deckt Haus"-Sperre verhindern, dass eine
  volle Batterie kleine Netz-Schwankungen um Null mit sinnlosem Mikro-Zyklen (und Über-Entladung in
  die Einspeisung) beantwortet. Echte Defizite (abends, Lastspitzen) werden weiterhin gedeckt.

- **Entity-Picker für die PV-Prognose.** Die PV-Prognose-Entität (Solcast o. Ä.) wird jetzt über
  denselben Auswahl-Dialog gewählt wie die Preis-Entität, statt sie als Text eintippen zu müssen.
- **„Sollwert unbekannt"-Hinweis nur noch im Log.** Der rein kosmetische Hinweis (Sollwert-Entität
  ohne lesbaren Zustand) steht nicht mehr im Hinweise-Panel — Regelung und Verlauf laufen ohnehin;
  er wird jetzt einmalig ins Log geschrieben.

- **Bilanz-Kontur durchgehend am Nulldurchgang.** Grün (Einspeisung) und Rot (Bezug) treffen sich
  jetzt am exakten, interpolierten Nulldurchgang — die Randlinie läuft sauber durch die Nulllinie,
  statt in der jeweils anderen Phase flach auf der Achse weiterzulaufen.
- **Fix: Bilanz-Flächen widersprachen sich.** Überschuss und Bezug konnten gleichzeitig
  erscheinen (Grün kam vom Regler-Signal, das eine ladende Batterie als verfügbaren Überschuss
  zählt; Rot vom echten Netzbezug). Beide Flächen leiten sich jetzt aus einer Größe ab — der
  Netzbilanz: Grün = echte Einspeisung, Rot = echter Bezug, nie gleichzeitig.
- **Tagesplaner (Anzeige).** SEA plant alle 15 Minuten das beste Prognosefenster für die
  Warmwasser-Anhebung (Länge = typische Ladedauer) und schätzt, wann die Batterie voll ist.
  Sichtbar auf der Anhebungs-Karte („heute geplant 12:30–14:00") und als gestricheltes Band
  auf der Strategie-Timeline — die Steuerung bleibt in dieser Stufe bewusst unverändert
  (erst nach ein paar Tagen Beobachtung greift der Plan in die Starts ein).

## 0.8.3

- **Prognose-Gate mit einstellbarer Ladedauer & für bindende Schaltlasten.** Die Wärmepumpe hat
  jetzt das Feld „Anhebung: typische Ladedauer" (Standard 90 min) — es bestimmt das Prognosefenster
  für den Start. Dasselbe Gate gilt für geschaltete Lasten, die sich beim Start binden (nicht
  unterbrechbar oder min. Laufzeit ≥ 30 min): gestartet wird nur, wenn die Prognose ihre Laufzeit
  trägt. Frei regelbare und unterbrechbare Lasten bleiben rein reaktiv; Deadlines gehen immer vor.
- **Anhebung startet prognosebasiert.** Der Start braucht zusätzlich zum aktuellen Überschuss
  eine tragfähige Prognose über die nächsten ~90 Minuten — kein Anfahren mehr am kurzen PV-Peak,
  wenn die eigentliche Heizphase ins Prognose-Tal fiele. Ohne Prognose gilt das bisherige
  Verhalten; laufende Anhebungen beendet weiterhin nur die gemessene Realität.
- **Bilanz als Flächen im Hintergrund.** Überschuss (grün) und Bezug (rot) füllen jetzt dezent
  gesättigt die Fläche zur Nulllinie, mit hauchdünner Kontur — alle anderen Kurven zeichnen
  darüber. Die separate „Netz"-Kurve entfällt (Bezug = rote Fläche, Einspeisung steckt im
  Überschuss); im CSV-Export bleibt der Netzwert enthalten.
- **Bezug-Kurve rückwirkend & ruhende Sensoren sichtbar.** Die rote Bezug-Kurve der Bilanz wird
  aus dem (schon immer vorzeichenbehaftet aufgezeichneten) Netzwert abgeleitet und funktioniert
  damit für die gesamte Historie. Sensoren ohne Änderung im Zeitfenster (z. B. Tanktemperatur in
  kurzen Fenstern) zeichnen jetzt eine gehaltene Linie statt eines unsichtbaren Einzelpunkts.
- **Regler berücksichtigt die Abtastzeit.** Aktoren, die nur alle N Takte geschrieben werden
  (Batterie-Schreibintervall), integrierten bisher N-mal langsamer pro Zeit — die Regeldynamik
  hing am Schreibintervall. Der Integral-Schritt wird jetzt auf Zeit normiert (und bleibt hart
  am realen Rest-Export gekappt): gleiche Rampe, egal ob alle 10 oder alle 30 s geschrieben wird.
- **Verlauf zeigt jetzt die Bilanz zweifarbig.** Aus „Überschuss" wird die vorzeichenbehaftete
  Bilanz: Überschuss grün, Netzbezug rot — zwei Legenden-Einträge, einzeln schaltbar.
- **SEA zeichnet die eigenen Sollwert-Kommandos auf.** Sollwert-Entitäten ohne lesbaren Zustand
  (z. B. Template-Zahlen, die „unknown" liefern) zeigten leere Verläufe — jetzt zeichnen Verlauf
  und Export die von SEA tatsächlich geschriebenen Werte (erfolgreiche Writes, mit Aufbewahrung).
- **Charts aufgeräumt.** Detail-Charts ohne Daten im Zeitfenster werden ausgeblendet (die
  Wertezeile bleibt); der Preis-Chart zeigt „Mein Tarif" auch in kurzen Zeitfenstern (feinere
  Auflösung + Stufen-Verlängerung bis zum Fensterrand).
- **Fix: Netzbezugs-Deckung kämpft nicht mehr gegen das Überschuss-Laden.** Bei PV-Überschuss
  (oder ladender Batterie) hält sich die Deckung jetzt strikt zurück — vorher konnte sie
  selbstverursachten Netzbezug „decken" und die Batterie in ein Voll-Lade/Entlade-Pendeln
  treiben (jeder Schreibzugriff hebt auf manchen Wechselrichtern die Gegenrichtung auf).
  Simulations-Szenario verankert: bei Überschuss nie eine Entladung, die Batterie lädt.
- **Langsame Geräte-Antworten sind keine Fehler.** Manche Geräte bestätigen Sollwert-Schreibungen
  erst nach vielen Sekunden; SEA wartet jetzt bis 35 s je Schreibvorgang, statt einen langsamen,
  aber erfolgreichen Write als Fehler zu werten. Ein wirklich totes Gerät bremst höchstens kurz
  und wird danach gedrosselt erneut versucht — schnelle Geräte merken von alledem nichts.
- **Sollwert-Wächter für Speicher.** Viele Batterien halten ihren letzten Sollwert, bis ein neuer
  ankommt — geht die Rückstellung verloren, läuft das Gerät gegen den aktuellen Befehl weiter
  (schlimmstenfalls entlädt es sich ins Netz). SEA vergleicht deshalb laufend den gemessenen
  Batteriefluss mit dem kommandierten Wert; weicht er länger als 2 Minuten deutlich ab, wird der
  Befehl mit Vorrang neu geschrieben und eine Warnung geloggt.
- **UI-Updates greifen sofort.** Die Oberfläche wird mit No-Cache-Header ausgeliefert — nach einem
  Add-on-Update kann der Browser nicht mehr ein altes UI-Skript mit der neuen API mischen
  (Geisterkarten/tote Buttons; bisher half nur Strg+F5).
- **Strategien orthogonal aufgeräumt.** Neue Ziel-Strategie „Batterie deckt Netzbezug": SEA
  entlädt die Batterie zur Deckung des Hausverbrauchs — nötig für Wechselrichter im manuellen
  Modus (z. B. sonnen unter SEA-Steuerung), je Batterie zuschaltbar. Peak-Shaving und
  Einspeise-Limit sind zu EINER Karte „Netzanschluss-Grenzen (Pflichten)" zusammengefasst;
  Notstrom-Reserve und Pflege-Vollladung wohnen jetzt als Parameter an der Batterie-Karte.
- **Ein gemeinsames Entlade-Budget.** Die Batterie-Unterstützung je Verbraucher ist nur noch ein
  Häkchen (statt lokaler Watt-Werte): das Budget wird zentral in der Reihenfolge der
  Prioritätenliste verteilt — eine höher priorisierte Wallbox darf das volle Budget beanspruchen,
  um zu starten; doppelt gezählt wird nie. Haus-Grundlast wird physisch immer zuerst gedeckt.
- **Zahnrad-Buttons springen zum aufgeklappten Gerät.** Alle ⚙-Buttons öffnen jetzt auf der
  Komponenten-Seite auch die Kategorie-Karte, klappen das Gerät auf und scrollen dorthin.
- **Anhebungs-Häkchen synchron.** Das Enable der Anhebungs-Strategie und das Häkchen der
  Wärmepumpe in der Prioritätenliste spiegeln sich jetzt gegenseitig — zwei Häkchen, eine
  Bedeutung, kein Widerspruchszustand mehr.
- **Wärmepumpen-Anhebung jetzt mit echter Priorität.** Die WP steht in der Prioritätenliste
  (auch ohne Steuer-Entität): Für den Start zählt der verfügbare Überschuss = Rest-Export plus
  die Leistung tiefer priorisierter Verbraucher (z. B. Heizstab) — die weichen automatisch,
  sobald der Verdichter anläuft. Teilnehmer oberhalb (z. B. Batterie) behalten ihre Leistung.
- **Strategien-Seite aufgeräumt.** Karten auf max. 2 Zeilen gekürzt (Details im ⓘ), WP-Strategie
  direkt nach dem Eigenverbrauch einsortiert, Zähler kompakt, Zahnrad-Button auch bei der
  Absenkung; Baselines kurz benannt (u. a. „PV-Volleinspeisung") für schmale Displays.
- **Anhebungs-Strategie: Anzeige & Bedienung.** Die Karte zeigt „operativ", solange eine
  Anhebung/Absenkung tatsächlich aktiv ist (nicht nur im Schreibmoment), listet die Wärmepumpen
  mit dem üblichen ⚙-Button zu den Geräte-Einstellungen (statt Text-Button) und erklärt die
  Schwellen-Logik: Sie misst den Rest-Überschuss nach den anderen Verbrauchern; läuft die WP,
  weicht der Heizstab automatisch zurück.
- **Spar-Analyse flutet das Log nicht mehr.** Die interne Simulation (echte Regel-Engine gegen
  ein Modell) schrieb ihre simulierten Entscheidungen ins echte Entscheidungs-Log — sie sah aus
  wie reales Schalten einer Entität „number.hz". Simulations-Läufe loggen jetzt nur noch auf
  Debug-Ebene; an Home Assistant geschrieben hat die Simulation nie.
- **Hotfix: UI startete in beta.22 nicht** („verbinde…" blieb stehen). Ein Zeilenumbruch war in
  einen Bestätigungstext des neuen Backup-Dialogs geraten und brach das UI-Skript. Ein neuer
  automatischer Test prüft das Inline-Skript jetzt auf genau diese Fehlerklasse.
- **Regelung bleibt bei hängenden Geräten flüssig.** Ein Gerät, dessen Integration nicht antwortet,
  bremste den 10-Sekunden-Regeltakt auf
  ~1 Zyklus/Minute aus. Jetzt: hartes Zeitlimit je Websocket-Befehl (30 s) und je Schreibvorgang
  im Zyklus (15 s), und nach 3 Fehlversuchen in Folge wird der Aktor 2 Minuten pausiert statt
  dauerhaft gehämmert — die übrige Regelung (ELWA, Verbraucher) läuft im Takt weiter.
- **Backup & Wiederherstellung der Einstellungen.** Grundeinstellungen → „Sicherung & Diagnose":
  alle Einstellungen + Komponenten-Konfiguration als lesbare/editierbare JSON-Datei herunterladen
  und wieder einspielen (vorher wird automatisch gesichert). Zusätzlich täglich ein automatisches
  Backup nach `backups/` (die letzten 14 bleiben). Backups sind versionstolerant: unbekannte Felder
  werden ignoriert, fehlende mit Standardwerten ergänzt.
- **Dauerhaftes, herunterladbares Log.** SEA schreibt zusätzlich ein rotierendes Logfile
  (`logs/sea.log`, überlebt Neustarts und Updates — das Supervisor-Log tat das nicht) und bietet es
  in „Sicherung & Diagnose" zum Download an. Für Support: Log + Backup + CSV-Export beilegen.
- **Heizkreis-Absenkung bei Abwesenheit.** Zweiter Arm der Absenkungs-Strategie: je Heizkreis
  eine Absenkung in K (gleiche Wert+aktiv-Logik wie die Anhebung), gesenkt wird erst nach
  einstellbarer Abwesenheitsdauer aller Personen (Standard 8 h), Rückkehr stellt sofort zurück.
  Bei langer Abwesenheit dominiert die Absenkung die Anhebung; Warmwasser ohne Absenkung lädt
  weiter aus der Sonne.
- **Zähler für zusätzliche WP-Starts.** Die Anhebungs-Karte zeigt, wie oft SEA die Wärmepumpe
  aus dem Stillstand gestartet hat (heute/gesamt) — Anhebungen bei laufender Pumpe verlängern
  nur den Lauf und zählen nicht. So ist der Verschleiß-Effekt belegbar.
- **Strategien zeigen echte Voraussetzungen.** Peak-Shaving, Einspeise-Limit, Notstrom-Reserve,
  Batteriepflege und Optimierer sind nur noch „verfügbar", wenn die nötigen Aktoren existieren
  (steuerbare Batterie, Netzleistung) — vorher erschienen sie auch auf Instanzen ohne PV/Batterie.
- **Anhebung je Heizkreis pausierbar.** Neben dem Anhebungs-Feld gibt es ein „aktiv"-Häkchen
  (klickbar erst bei Anhebung > 0): die Einstellung bleibt erhalten, wird aber nicht ausgeführt —
  z. B. Heizkreise im Sommer. Wird ein Kreis mitten in einer Anhebung pausiert oder der Hub
  gelöscht, stellt SEA den Sollwert trotzdem zuverlässig zurück (kommandierter Boost-Wert wird
  jetzt mit-persistiert).
- **Wärmepumpen-Karte entrümpelt.** Die Steuerung-Radios (schalten/Sollwert) erscheinen nur noch
  im Expertenmodus, solange keine Steuerung konfiguriert ist — für Anhebung und SG-Ready sind sie
  nicht nötig. Das Anhebungs-Feld gibt es nur bei Heizkreisen mit Sollwert-Entität (leer/0 = aus,
  das Feld ist der Enable); die Anhebungs-Parameter der Wärmepumpe erscheinen erst, wenn
  mindestens ein Heizkreis eine Sollwert-Entität hat.
- **Solltemperatur-Anhebung bei PV-Überschuss (Wärmepumpe).** Das Software-Gegenstück zu SG-Ready,
  für jede Wärmepumpe mit stellbaren Heizkreis-Zieltemperaturen (climate/water_heater/number):
  je Heizkreis eine Anhebung in K (Warmwasser z. B. +10 K, Heizkreis +2 K), je Wärmepumpe
  Überschuss-Schwelle, Mindesthaltezeit und max. Anhebungen/Tag — konfiguriert an der
  Komponenten-Karte, funktioniert auch ohne Steuer-Entität. Rückstellung garantiert (Zustand
  wird persistiert, auch über Neustarts), manuelle Sollwert-Änderungen gewinnen, geschrieben
  wird nur bei Übergängen (schonend für Cloud-APIs wie myVAILLANT).
- **Schalt-Verbraucher können „selbstbeendend" sein.** Für Hersteller-Boosts (z. B. Vaillant
  Warmwasser-Boost, Quick Veto): SEA schaltet nur ein, das Gerät beendet den Lauf selbst —
  SEA sendet nie Aus.
- **Heizkreis-Solltemperaturen in Verlauf & Export.** Die Zieltemperatur von climate-/water_heater-
  Entitäten steckt in den Attributen (der Zustand ist nur ein Modus) — Verlaufs-Plots und CSV-Export
  lesen sie jetzt aus und zeigen die Soll-Kurven der Heizkreise statt leerer Spalten.
- **Heizkreis-Sollwert akzeptiert water_heater-Entitäten.** Home Assistant bildet
  Warmwasserkreise (z. B. Vaillant) als eigene Domain `water_heater` ab — die Sollwert-Auswahl der
  Heizkreise bot bisher nur `climate`/`number` an.
- **COP-Eingabe an der Wärmepumpen-Komponente.** Das Feld „COP / JAZ (Warmwasser)" steht jetzt auf
  der Komponenten-Karte der Wärmepumpe (Einrichtung) — damit funktioniert es auch für eine rein
  gemessene, nicht steuerbare Wärmepumpe, die in der Strategien-Geräteliste gar nicht auftaucht.
- **Überschuss-Senke: Bewertung folgt dem Senkentyp.** Die Baseline bewertet aufgenommene Energie
  jetzt konsistent mit dem Kostenmodell der Spar-Analyse: Auto = ersetzt Netzbezug 1:1
  (Bezugspreis − Einspeisung), Heizstab = ersetzt Wärmepumpen-Wärme (Bezugspreis ÷ COP −
  Einspeisung, kann negativ sein). Der Senkentyp-Schalter setzt Leistung und Bewertung; die
  Info-Tabelle zeigt die angewandte Bewertung.
- **Einsparung: Baseline „Dynamischer Tarif" rechnet mit echten Börsenpreisen.** Statt des
  synthetischen Drei-Block-Tarifs verwendet die Baseline jetzt die echten EPEX-Stundenpreise des
  Zeitraums (effektiv, wie im Börsen-Vergleichstarif konfiguriert); „günstig" fürs Netzladen ist das
  untere Preis-Quartil des Fensters. Die drei Preisregler bleiben als Fallback, wenn die Börse nicht
  erreichbar ist — die Info-Tabelle zeigt, welche Preisbasis tatsächlich galt.
- **Börsen-Vergleichstarif: Aufschlag jetzt NETTO.** Klarere Standard-Darstellung:
  Effektivpreis = (Börsenpreis + **Aufschlag netto**) × (1 + MwSt) — die MwSt wird auf die Summe
  gerechnet, wie bei realen dynamischen Tarifen (Default: 14,5 ct netto, 19 %).
- **Börsen-Vergleichstarif.** Die Spar-Analyse kann jetzt mit einem realistischen dynamischen Tarif
  rechnen, auch ohne eigenen dynamischen Vertrag: **EPEX-Börsenpreis** (öffentliche
  aWATTar-Marktdaten, auch historisch) **× MwSt + Aufschlag** (Netzentgelte/Abgaben/Anbieter —
  konfigurierbar unter Tarife im Experten-Modus, Default 19 % / 17 ct). Preisbasis-Auswahl im
  Analyse-Panel („Meine Tarife" / „Börsenpreis + Aufschlag"); Wärme- und Restwert folgen dem
  Börsen-Mittel des Zeitraums. Ohne erreichbare Börsendaten verweigert die Rechnung, statt zu raten.
- **Preis-Chart im Verlauf.** Neues Diagramm „Strompreis (ct/kWh)" unter den Strategien: der eigene
  (aufgezeichnete) Tarifpreis und der Börsen-Vergleichstarif im selben Zeitfenster — inklusive der
  bereits veröffentlichten Day-Ahead-Stunden von morgen. Zoombar wie die anderen Charts.
- **Fix II: Anfahr-Sprung holt auch belegte Leistung zurück.** Hielt ein niedriger priorisierter
  Verbraucher (Heizstab) den Überschuss bereits, blieb der freie Export unter der
  Batterie-Mindestleistung und der Sprung zündete nie — obwohl die Leistung der Batterie zusteht.
  Der Sprung zählt jetzt die zurückholbare Leistung niedrigerer Prioritäten mit; die Übergabe
  passiert im selben Takt ohne Netzbezug. (Replay des Vorfalls: Batterie Ø 845 W statt 0.)
- **Fix: Batterie fährt jetzt auch bei kleinem Überschuss an (Anfahr-Sprung).** Wechselrichter wie die
  sonnen ignorieren Ladesollwerte unter ihrer Mindestleistung (~650 W). Der gedämpfte Regler-Schritt
  (20 % des Überschusses) blieb darunter — die Batterie kam nie ins Laden, der Heizstab bekam alles.
  Ist an der Batterie die **min. Leistung** gesetzt und der echte Rest-Überschuss deckt sie, startet
  SEA jetzt direkt mit der Mindestleistung (ohne Netzbezug) und regelt dann normal weiter. Neuer
  Dashboard-Hinweis, wenn eine regelbare Batterie ohne Mindestleistung konfiguriert ist.
- **Strategie-Einstellungen bei den Strategien.** „Lade-Vorrang bis SoC" steht jetzt in der
  PV-Überschuss-Karte, die Peak-Shaving-**Zeitfenster** direkt in der Peak-Shaving-Karte (Strategien-
  Seite) — die Grundeinstellungen enthalten keine Strategie-Parameter mehr. Die frühere Karte
  „PV-Überschuss & Speicher" heißt jetzt „Regelung" und ist komplett Experten-Modus (Regler-Parameter,
  Sensor-Angleichung, Schreibintervall).
- **Feinschliff II:** Beim Ausklappen auf dem Handy wird nur noch der tatsächlich benötigte Platz
  eingefügt (vorher großer Leerraum unter jeder ausgeklappten Gruppe); Kugel-Farbverlauf jetzt mit
  hellerer Mitte und deutlich satterem Rand.
- **Feinschliff nach Feedback:** kräftigere Kugel-Farben im Flussdiagramm; das Sankey zeigt die
  Einzelverbraucher ausklappbarer Gruppen in derselben Farbe wie die Fluss-Ansicht; Diagramm nach
  links gerückt und rechte Beschriftungen nicht mehr abgeschnitten.
- **Sankey-Ansicht auf dem Dashboard.** Umschalter oben rechts im Energiefluss: „Fluss" (Netz-Ansicht)
  oder „Sankey" — ein Fluss-Diagramm im Stil der HA-Energieansicht, aber mit den **aktuellen
  Leistungen** (Quellen → Haus → Verbraucher/Batterie/Einspeisung, Bandbreite ∝ Watt). Auf dem
  Handy gedreht (von oben nach unten) mit Legende.
- **Energiefluss aufgehübscht.** Kugeln mit radialem Farbverlauf, ohne Umrandung, leicht schwebend
  mit Schatten; größere Schrift und mehr Abstand (keine Überlappungen mehr). Beim Ausklappen wächst
  die Box jetzt nach unten — das Diagramm bleibt auf dem Handy lesbar statt zu schrumpfen.
- **Pinch-Zoom im Verlauf.** Auf dem Handy zoomt eine Zwei-Finger-Geste die Zeitachse aller
  Verlaufs-Diagramme (horizontal aufziehen = hineinzoomen), mit Live-Vorschau während der Geste.

## 0.8.2

- **Habitron-Bindung.** Der Smart Energy Agent ist Teil des Habitron-Systems: Ohne erkannte
  Habitron-Integration in Home Assistant zeigt die App eine Sperrseite und die Steuerung bleibt
  deaktiviert (harte Verriegelung; in der Entwicklungsumgebung und während des Starts offen).
  Proprietäre LICENSE-Datei ergänzt (alle Rechte vorbehalten, Nutzung nur für Habitron-Kunden).
- **Geräte-Einstellungen neu sortiert: „Zeiten & Grenzen" vs. „Experten-Einstellungen".** Startzeiten,
  Laufzeiten, Auszeiten, spätester Start, Unterbrechbarkeit, Mindestleistung und Mindestmenge/Tag sind
  KEINE Experten-Einstellungen mehr — sie stehen im für alle sichtbaren Panel „Zeiten & Grenzen".
  Experten-Einstellungen (nur im Experten-Modus) sind jetzt ausschließlich Dinge, die ein
  Normalverbraucher nicht verstellen sollte: W/Einheit, Stufen-Verdrahtung, SG-Ready-Relais,
  Batterie-Zyklenkosten — plus Regler-Parameter, Schreibintervall, Sensor-Angleichung und Regeln.
- **Experten-Modus admin-verriegelt.** Die Experten-Checkbox erscheint nur noch, wenn die neue
  App-Option „expert" gesetzt ist — App-Optionen kann in Home Assistant nur ein Administrator ändern.
  Ohne Freischaltung wird der Modus auch serverseitig abgewiesen.
- **Fix: Volle Batterie gibt den Überschuss frei.** Stand die (volle) Batterie oben in der Priorität,
  bekam sie weiter Überschuss zugeteilt, den sie nicht aufnehmen kann — niedriger priorisierte
  Verbraucher (Heizstab) gingen leer aus und die Energie ging als Export verloren. Eine Batterie am
  SoC-Limit gilt jetzt als gesättigt; der Überschuss fließt an die nächste Last. (Gefunden durch die
  24-h-Vorschau des Advisors, abgesichert als Simulations-Szenario.)
- **Spar-Analyse erklärt sich.** Über der Tabelle stehen jetzt die Eckdaten des Zeitraums (PV,
  Grundlast, Überschuss in kWh, Start-SoC) — und wenn alle Varianten praktisch gleich abschneiden,
  sagt ein Fazit **warum** (z. B. „Batterie zu Beginn schon voll — es gibt nichts zu verteilen"),
  statt sechs identische Zahlen unkommentiert zu zeigen.
- **Advisor Stufe 4: 24-h-Vorschau (Prognose-Modus).** Die Spar-Analyse kann jetzt neben dem Rückblick
  auch die **nächsten 24 Stunden** durchspielen: PV-Ertragsprognose (Forecast.Solar oder konfigurierte
  Entität) + **gelerntes Lastprofil** aus der eigenen Aufzeichnung (recency-gewichtetes
  Stunden-Profil, die regelbare Last herausgerechnet), Start beim aktuellen Batterie-SoC. Gleiche
  Varianten, gleiche €-Bewertung — ohne PV-Prognose verweigert die Vorschau, statt zu raten.
- **Experten-Modus.** Neue Checkbox in den Grundeinstellungen (Allgemein): Erst wenn aktiv, erscheinen
  die erweiterten Einstellungen (Regler-Parameter, Schreibintervall, Sensor-Angleichung), die
  „Erweitert"-Bereiche der Geräte (inkl. **Batterie-Zyklenkosten**, dorthin verschoben) und die
  eigenen Regeln. Für alle anderen bleibt die Oberfläche schlank.
- **Spar-Analyse umgezogen auf die Einsparung-Seite** (statt Strategien) und die Varianten verwenden
  jetzt den **konfigurierten Batterie-Namen** (z. B. „Sonnen-Batterie vor ELWA 2").
- **Advisor Stufe 3: Spar-Analyse auf der Strategien-Seite.** Neues Panel „Spar-Analyse": spielt die
  letzten 1/3/7 Tage aus der eigenen Aufzeichnung mit alternativen Einstellungen durch (beide
  Prio-Reihenfolgen Batterie/Last × Lade-Vorrang 0/30 %) und zeigt die Kosten je Variante in € mit
  Differenz zur aktuellen Einstellung — gerechnet mit den eigenen Tarifen, den Batterie-Zyklenkosten
  und dem Wärmepumpen-COP. Die Analyse läuft im Hintergrund (1–2 min); die tatsächlich gezogene
  Leistung der regelbaren Last wird aus der HA-History herausgerechnet, damit die Simulation sie neu
  planen kann.
- **Zyklenkosten jetzt je Batterie** (Geräte-Strategien, neben Kapazität) statt in den
  Grundeinstellungen — wie der COP eine Geräteeigenschaft.
- **Advisor Stufe 2: Sofort-Hinweise auf dem Dashboard.** SEA prüft die Konfiguration laufend auf
  bekannte Stolperfallen und zeigt sie als Hinweis-Karte: Sollwert-Entität liefert „unknown"
  (Template-Rücklesung defekt), „regelbar bis" über dem Geräte-Maximum (Phantom-Spielraum),
  fehlender Entladesollwert bei aktiven Entlade-Strategien, wiederholt fehlschlagende Schreibbefehle
  (Timeout/401). Keine Hinweise = keine Karte.
- **Kostenmodell nutzt die eigenen Einstellungen.** Bezugspreis aus dem konfigurierten Tarif
  (statisch/HT-NT/dynamisch), Einspeisevergütung aus den Tarif-Einstellungen. Neu in den
  Grundeinstellungen: **Batterie-Zyklenkosten (ct/kWh)** — der Planer zyklisiert nie für
  Cent-Bruchteile. Der **COP/JAZ ist je Wärmepumpe** einstellbar (Geräte-Strategien) und bewertet,
  ob Überschuss besser in Heizstab-Wärme oder Batterie/WP fließt — im Winter entscheidend.
- **Advisor-Grundlage (Stufe 1): Kostenfunktion + Einstellungs-Vergleich auf echten Tagen.** Neues
  Modul bewertet Simulationsläufe in **Euro** (Import/Einspeisung, **Zyklenkosten** der Batterie
  gegen unnötiges Zyklisieren, Restwert gespeicherter Energie, Wärme-Gutschrift für den Heizstab,
  dynamische Preise) und vergleicht Einstellungs-Varianten (Prioritäten, Lade-Vorrang, …) per Replay
  aufgezeichneter Tage — inkl. Batterien-Wirkungsgrad (88 % Round-Trip) im Anlagenmodell. Noch ohne
  UI; Basis für das kommende Empfehlungs-Panel und den späteren opt-in Auto-Modus.
- **Qualitätssicherung: Closed-Loop-Simulations-Harness.** Der komplette Regelkreis (echte Engine gegen
  ein Anlagenmodell mit den realen sonnen-Eigenheiten: hält Sollwerte, Lade-Write löscht Entladung,
  ignoriert Mini-Sollwerte, Write-Timeouts) läuft jetzt in 9 Szenario-Tests über hunderte Zyklen und
  prüft Invarianten (kein anhaltender Netzbezug, Rest-Export konvergiert, Prio-Reihenfolge im
  Dauerzustand, festgeklemmte Entladung wird geheilt — auch nachts). Verifiziert: die zwei teuersten
  Fehler der letzten Tage (leergesaugte Batterie, nicht-konvergierendes Laden) wären damit vor dem
  Release aufgefallen; künftige Regler-Änderungen müssen diese Szenarien bestehen.
- **Fix: Prioritäts-Umverteilung wirkt jetzt in beide Richtungen (Batterie bekommt gehaltene
  Verbraucher-Leistung zurück).** Hatte sich ein niedriger priorisierter Verbraucher (ELWA) in einer
  Export-Spitze Leistung gegriffen, behielt er sie dauerhaft — ein positives Überschuss-Signal wirft
  nie ab, und der Rück-Transfer zur höher priorisierten Batterie fehlte (die bekam nur den kleinen
  Rest-Export; beobachtet: ELWA hält 1–3 kW, Batterie bei 46 % SoC leer aus). Jetzt stellt jeder
  Teilnehmer, über dem jemand in der Prio-Liste steht, pro Takt den Ki-Anteil seiner Leistung zur
  Umverteilung: Höher priorisierte nehmen ihn (sanfte Wanderung ohne Netzbezug), sonst behält er ihn
  unverändert.
- **Verlaufsplots zeigen echte Stufen statt falscher Rampen.** HA zeichnet nur Wert-Änderungen auf —
  startete z. B. der Heizstab nach einer langen 0-Phase, malte der Plot eine stundenlange „Rampe" von 0
  zum neuen Wert. Jetzt wird der gehaltene Wert unmittelbar vor jeder Änderung eingefügt (bei Lücken
  > 60 s), sodass der Verlauf die tatsächliche Sprungform zeigt.
- **Fix: Batterie-Laden konvergiert wieder (kein Rest-Export, kein Kampf mit dem Heizstab).** Die
  Prioritäts-Umverteilung aus beta.13 hatte der Batterie den Regel-Integrator genommen: sie bekam pro
  Takt nur den PI-Bruchteil des Überschusses, ihr Ladewert summierte sich nie auf — Rest-Export ging
  dauerhaft ins Netz (beobachtet: ~600 W Export bei 13 % SoC), und Batterie und Heizstab „kämpften" in
  Schüben. Jetzt: Basis der Zuteilung ist wieder die **gemessene** Ladeleistung (Integrator), und der
  Vorrang eines höher priorisierten Verbrauchers wirkt als **ratenbegrenzter Transfer** (Ki-Anteil pro
  Takt) — die Leistung wandert sanft vom Speicher zum Verbraucher, ohne Netzbezug; ein gesättigter
  Verbraucher lässt den Rest der Batterie. Zudem regelt die Batterie jetzt auf ihre gemessene Leistung
  statt auf den (ggf. „unknown"-) Sollwert-Zustand — kein Aufziehen der Regelung, wenn ein Schreibbefehl
  verloren geht.
- **Einstellung „PV-Überschuss-Vorrang" entfällt — die Prioritäten-Liste entscheidet.** Steht die
  (regelbare) Batterie oben, lädt sie zuerst; Verbraucher mit höherer Priorität bekommen den Überschuss
  vor ihr und können ihr bereits laufende Ladeleistung innerhalb eines Takts wieder abnehmen (das ging
  vorher gar nicht). „Lade-Vorrang bis SoC" bleibt: darunter lädt die Batterie immer zuerst, unabhängig
  von der Liste. Eine Batterie **ohne** Ladesollwert wird konservativ behandelt (Batterie zuerst — ihre
  eigene Regelung verwaltet sie; Verbraucher bekommen nur echten Export-Überschuss).
- **Fix: Batterie lädt wieder aus PV-Überschuss (auch bei laufender Wallbox-Session).** Die
  Ladeunterstützung hält die Batterie während einer EV-Session mit einem Entladebefehl von **0 W** in
  Ruhe — dieser 0-Befehl schloss die Batterie fälschlich komplett aus der Überschuss-Verteilung aus,
  sodass sie **nie** einen Ladebefehl bekam, solange „Wallbox laden" aktiv war. Jetzt blockiert nur
  noch eine **aktive** Entladung (> 0 W) das Überschuss-Laden.
- **Batterie-Ansteuerung grundüberholt: eine Richtung pro Zyklus.** Neue zentrale Regel: Lade- und
  Entladesollwert einer Batterie schließen sich aus. Ist eine Seite aktiv (> 0), wird die Gegenseite in
  diesem Zyklus **gar nicht** geschrieben (auch keine 0) — auf der sonnen hebt jeder Schreibzugriff auf
  den Gegen-Sollwert das aktive Kommando auf. Sind beide Seiten 0, bleiben beide 0-Halte-Writes aktiv
  (Batterie wird bewusst in Ruhe gehalten).
- **Schreibintervall jetzt auf ALLEN Batterie-Befehlen.** Einspeiselimit, Notstromreserve,
  Batteriepflege und Optimierer schrieben bisher am Batterie-Schreibintervall vorbei (bei sich
  änderndem Wert jeden Takt). Alle Batterie-Sollwerte respektieren jetzt einheitlich das Intervall.
- **Entitäts-Auswahl liest frisch ein.** Beim Öffnen des Entitäts-Pickers (Stift-Button) zieht SEA
  jetzt die HA-Entitätsliste live neu — ein frisch angelegter Helfer (z. B. `input_number` /
  Template-Number) ist damit **sofort auswählbar**, ohne SEA erst neu verbinden/neustarten zu müssen.

- **Sicherheits-Fix: 0-Sollwert wird wieder aktiv gehalten (Batterie kann nicht ins Netz „durchlaufen").**
  Die Batterie hält ihren letzten erzwungenen Sollwert. Ein zuvor eingeführtes „Leerlauf-0 geht still"
  hatte SEA die 0 nur **einmal** schreiben lassen — griff dieser eine Write nicht, entlud die Batterie
  endlos ins Netz, ohne dass SEA je nachfasste. SEA behauptet den kommandierten Wert (auch **0**) jetzt
  wieder in **jedem Schreibintervall**, behält so die Kontrolle über den Aktor und fährt die Batterie
  zuverlässig auf 0 zurück. (Für saubere Logs den Sollwert über einen zuverlässigen lokalen Helfer/
  Template statt der direkten, timeout-anfälligen sonnen-`number`-Entität führen.)
- **Fix: sonnen-Batterie wird nicht mehr als Überschuss-Last „dauergeschrieben".** Die Modulation
  behandelte den Batterie-Ladesollwert wie den ELWA-Heizstab und schrieb ihn mit `force` **jeden
  Zyklus** (auch `0 W`, endlos) → dauernde `number_charge`-Timeouts im Log. Batterien werden jetzt
  aufs Schreibintervall gedrosselt und nicht mehr force-refresht; ein Leerlauf-Wert (0) wird nicht
  mehr wiederholt gesendet.
- **Fix: Batterie wird nicht geladen, während sie entladen soll.** Lädt ein höher priorisierter Regler
  (Peak-Shaving / Ladeunterstützung) die Batterie-Entladung, unterlässt die Überschuss-Modulation jetzt
  den Lade-Sollwert derselben Batterie — vorher hob der Lade-Write bei der sonnen die Entladung wieder
  auf, sodass die Entlade-Unterstützung nie stehen blieb.
- **Fix: Schreib-Intervall greift jetzt auch bei sich änderndem Sollwert.** Der Batterie-Entladewert
  folgt dem Live-Netzwert (Peak-Shaving `Netz − Limit`, Ladeunterstützung `min(Budget, Netz)`) und
  ändert sich dadurch fast jeden Takt. Bisher drosselte das Intervall nur bei **unverändertem** Wert,
  weshalb der Write (und der sonnen-Timeout) trotz „20 s" weiter alle 10 s kam. Jetzt ist das
  Batterie-Schreibintervall ein echter **Ratenbegrenzer**: innerhalb des Intervalls wird auch ein
  geänderter Sollwert zurückgehalten und am Intervallende der frischeste Wert geschrieben.
- **Fix: Schreib-Intervall greift auch bei fehlschlagenden Writes.** Ein Schreibvorgang, der scheitert
  (z. B. der sonnen-Timeout), merkte sich bisher nicht den Zeitpunkt — dadurch versuchte SEA es
  trotzdem jeden Takt (10 s). Jetzt wird der **Versuch** gemerkt, sodass das eingestellte
  Batterie-Schreibintervall auch bei Timeouts eingehalten wird (weniger Last aufs Gerät).
- **Robusterer Heartbeat (aktivitätsbasiert).** Die Verbindung gilt jetzt als lebendig, solange
  **irgendeine** Nachricht von HA ankommt (SEA abonniert Zustandsänderungen — eine gesunde Verbindung
  ist nie still). Der Ping ist nur noch ein Fallback für eine **wirklich stille** Verbindung. Damit
  löst ein einzelner, durch einen langsamen Geräte-Write blockierter Ping **keinen** Reconnect samt
  Discovery mehr aus, während Events weiterlaufen.

- **Batterie-Schreibintervall einstellbar.** Neu in den Grundeinstellungen: **„Batterie-Schreibintervall
  (s)"**. Manche Wechselrichter (sonnen) setzen die Entladung zurück, wenn kein frischer Sollwert kommt
  — aber jeder 10-s-Takt überlastet sie (der Schreibvorgang läuft in einen **Timeout** und stört sogar
  die HA-Verbindung). Damit lässt sich die stabile Kadenz ausprobieren (Standard 10 s). Der Entlade-
  Sollwert wird jetzt in diesem Intervall neu geschrieben statt zwangsweise jeden Takt.
- **Log entschlackt.** Kürzeres Format (nur Uhrzeit, kurzer Modulname ohne „smart_energy_agent."), und
  die HTTP-Zugriffszeilen (`GET /api/…`) laufen nur noch im Debug-Log — Info und „decision" bleiben
  knapp und lesbar.

- **Fix: Batterie-Entladung (sonnen) — kein „Laden = 0" mehr mitsenden.** Beim Entladen für
  Peak-Shaving/Ladeunterstützung schrieb SEA zusätzlich den Ladesollwert auf 0. Auf der sonnen setzt
  dieser gepaarte Schreibvorgang die Entladung wieder zurück (ein manueller, reiner Entlade-Sollwert
  hält dagegen). SEA schreibt jetzt **nur noch den Entladesollwert** (weiterhin alle 10 s neu).

- **Weniger Einstellungen sichtbar — „Betriebsart" + „Erweitert".** In den Geräte-Einstellungen
  (Komponenten) sind die selten geänderten Details jetzt unter **„Erweitert"** eingeklappt (PV-Schwelle,
  min. Laufzeit/Auszeit, Starts/Tag, spätester Start, Stufen, SG-Ready …). Für die **Wallbox** gibt es
  oben eine **Betriebsart**-Auswahl — *„Nur PV-Überschuss (+ Batterie)"* oder *„Immer laden — PV/
  Batterie zuerst, Rest Netz"* —, die die passende Einstellung automatisch setzt (statt der einzelnen
  „Laden aus Netz"-Option). Erster Schritt Richtung „sag *was*, nicht *wie*".

- **Entscheidungs-Log (neuer Log-Level „decision").** SEA protokolliert jetzt auf einem eigenen
  Level **zwischen INFO und WARNING**, **warum** eine Last zu einem Zeitpunkt **gestartet oder
  gestoppt** wurde (mit Sollwert und Begründung). Im Add-on unter *Konfiguration → log_level* auf
  **`decision`** stellen, dann zeigt das Protokoll nur noch diese Entscheidungen (plus Warnungen/
  Fehler) — ideal, um das Regelverhalten nachzuvollziehen. Bei `info` erscheinen sie zusätzlich; das
  laufende Nachregeln, der ±1-W-Impuls und Keepalive-Wiederholungen bleiben auf Debug.

## 0.8.1

- **Grundeinstellungen speichern automatisch.** Der „Speichern"-Knopf entfällt — Änderungen werden
  wie überall sofort übernommen. Ein dezenter **„gespeichert"-Hinweis unten** bestätigt es (dasselbe
  Muster jetzt konsistent auf allen Seiten).

- **Batterie-Entladung wird jetzt fortlaufend durchgesetzt.** Manche Batterie-Wechselrichter (sonnen)
  fallen mit dem Entladen nach kurzer Zeit wieder auf 0 zurück, wenn kein frischer Sollwert
  nachkommt — ein einmalig gesetzter Wert „verpufft". Peak-Shaving und Ladeunterstützung schreiben
  den Entlade-/Ladesollwert jetzt in **jedem Regeltakt (10 s) neu**, mit einer ±1-W-Variation, damit
  das Gerät die Entladung hält.

- **Batterie-Unterstützung: Laden beim Entladen stoppen.** Wenn die Ladeunterstützung die Batterie
  entlädt, setzt SEA jetzt zusätzlich den **Ladesollwert auf 0** (wie beim Peak-Shaving). Manche
  Wechselrichter ignorieren den Entlade-Sollwert, solange noch ein Ladesollwert ansteht — dann floss
  trotz kommandierter Entladung nichts.

- **Verlauf: Leistungs-Diagramm mit 1-kW-Raster.** Zusätzlich zu den beschrifteten Marken gibt es
  jetzt bei **jedem 1 kW** eine leichte Hilfslinie zum besseren Ablesen.
- **Fahrzeug ist eine eigene Komponente in den Plots.** Das Auto erscheint im Verlauf mit **SoC** und
  Lade-/Entlade-Sollwert als eigene Komponente (bisher nur in der Geräteansicht).
- **Wallbox führt keinen SoC mehr.** Der Ladezustand gehört zum Fahrzeug — die Wallbox zeigt in Plots
  und Geräteansicht keinen (Rest-)SoC mehr an.
- **Header und Menü bleiben beim Scrollen stehen.** Der horizontale Scroll liegt jetzt auf `<html>`
  statt `<body>`, damit `position:sticky` wieder greift: Kopfzeile oben und Menü seitlich bleiben
  fest, nur der Inhalt scrollt; ein zu langes Menü scrollt für sich.

- **Scrollen wieder wie früher (Umbau zurückgenommen).** Der Versuch, nur den inneren Bereich
  scrollen zu lassen (App-Shell), funktionierte geräteübergreifend nicht (Gesten blätterten um statt
  zu scrollen). Zurück auf das bewährte Verhalten: die **Seite** scrollt normal, Kopfzeile und Menü
  bleiben per `sticky` oben/seitlich stehen, und am Seitenende blättert Weiterscrollen zur nächsten
  Seite.

- **Regelbare Lasten: Sollwert bekommt einen ±1-W-Takt-Impuls.** Manche Geräte (z. B. der my-PV
  ELWA) setzen ihren eigenen Ansteuerungs-Timeout nur bei einem *geänderten* Sollwert zurück. Damit
  ein am Maximum gesättigter (sonst konstanter) Sollwert nicht als „unverändert" gilt und das Gerät
  in seinen Timeout-Cut läuft, variiert SEA den Modulations-Sollwert jetzt pro Takt minimal um 1 W
  (für die Last irrelevant; bei grob aufgelösten Stellgrößen wie A-Vorgaben ohne Wirkung).
- **Staleness-Schwelle auf 300 s angehoben.** Ein gültiger, aber ruhender Bilanzsensor (z. B. eine
  Batterie bei hohem SoC, die keine Leistungsänderungen mehr meldet) friert die regelbaren Lasten
  erst nach 300 s statt 180 s ein — mehr Reserve gegen versehentliches Einfrieren.

- **Verlauf: bessere Zeitachse.** Die X-Achse nutzt jetzt **runde Zeitschritte** (z. B. glatte
  2-Minuten-/Stunden-Marken) statt gleichmäßig geteilter, krummer Werte – dadurch keine
  ungleichmäßigen 2-/3-Minuten-Sprünge mehr. Beschriftung nur noch mit **Uhrzeit**; das **Datum**
  erscheint nur ganz links und bei Tageswechsel (Mitternacht). Die **Hilfslinien sind dunkler**
  (besser sichtbar), und beim Hineinzoomen kommen **feine Zwischenlinien** dazu.

- **Fix: periodisches Ausschalten des Heizstabs (Grenzzyklus) behoben.** Modulierende Lasten
  (Heizstab/ELWA etc.) bekommen ihren Sollwert jetzt in **jedem Regeltakt (10 s)** neu geschrieben,
  statt einen unveränderten Wert bis zu 55 s zu unterdrücken. Damit wird der **geräteeigene
  Sollwert-Watchdog** (z. B. der my-PV-ELWA, der ohne frischen Sollwert auf 0 zurückfällt) laufend
  gefüttert, und ein geräteseitiger Abschalt-Impuls wird **binnen 10 s** wieder überstimmt, statt bis
  zum nächsten Keepalive (~55 s) offen zu bleiben. Das beseitigt das beobachtete Rampe-hoch →
  Absturz → ~60 s-bei-0 → wieder-hoch-Muster trotz vorhandenem PV-Überschuss.

- **Verlauf: Zeitstreifen „Operative Strategien".** Unter dem Leistungs-Diagramm zeigt jetzt je
  Strategie ein farbiger Zeitstreifen (wie in HA), wann sie im gewählten Zeitraum tatsächlich Einfluss
  genommen hat – auf **derselben Zeitachse** wie das Diagramm. Der Zustand wird **synchron zum
  Regeltakt** (bei jeder Wertänderung, nicht mehr alle 30 s) aufgezeichnet, sodass die Grenzen exakt
  auf den gestellten Werten liegen. Für zurückliegende Zeiträume vor dieser Version liegen noch keine
  Daten vor.


- **Verschobene Einstellungen erscheinen nicht mehr doppelt unter „Grundeinstellungen".** Die in die
  Strategiekarten verschobenen Werte (Netzbezug-/Einspeise-Limit, Notstrom-Reserve, Batteriepflege,
  PV-Abregel-Entität) stehen nur noch dort; unter „Grundeinstellungen" bleiben lediglich die
  Peak-Zeitfenster und die Regler-Anteile.

- **Fahrzeug-SoC nicht mehr an der Wallbox.** Das Ladeziel wird ausschließlich je Fahrzeug
  (SoC-Entität + Ziel-SoC) unter „Fahrzeuge" eingestellt; die Wallbox-Karte führt keinen eigenen
  Fahrzeug-SoC mehr.

- **Regler-Einstellungen umbenannt.** „Modulation P-/I-Anteil" heißt jetzt schlicht
  **„Regler P-Anteil" / „Regler I-Anteil"** (ohne Zusatztexte).

- **Verlauf: Zeitbereich und Anzeige bleiben erhalten.** Der gewählte Zeitbereich (auch ein selbst
  eingegebener) **und** die Serien-Sichtbarkeit (Kurven an/aus) überleben jetzt den Neuaufruf von SEA
  — praktisch, wenn die HA-App nach dem Bildschirmschoner neu startet. Ohne gespeicherten Bereich
  öffnet der Verlauf auf „Tag bis jetzt"; die Live-Ansicht „Heute" wird beim Öffnen auf den aktuellen
  Tag nachgeführt.

- **Fix: Einsparungs-Zahlen sind wieder stimmig.** Baseline − Aktuell = Einsparung geht jetzt genau
  auf (vorher konnten die angezeigten Werte um einen Cent auseinanderlaufen).

- **Fix: „hängende" Bilanz/Überschuss abends behoben.** Das Zeit-Angleichungs-Fenster war nicht
  begrenzt — ein fast statischer Bilanzsensor (PV ~0 W oder ruhende Batterie am Abend) blähte es auf
  Minuten auf, sodass das Netzsignal über Minuten gemittelt wurde und **veraltete Tag-Werte
  (Einspeisung) mit aktuellen Abend-Werten (Bezug) vermischt** wurden. Ergebnis: ein falscher,
  „festhängender" Überschuss, der die ELWA fälschlich weiter hochhielt. Das Fenster ist jetzt auf
  **30 s gedeckelt** → Dashboard und Regelung reagieren wieder zeitnah.

- **Fix: Geräte-Leistungen werden nicht mehr geglättet angezeigt.** Die Zeitangleichung
  (signal_sync) hat bisher **auch die einzelnen Geräte-Leistungen** über ihr Fenster gemittelt —
  dadurch zeigte z. B. der Heizstab noch ~1,8 kW, obwohl er längst 0 zog (Fenster-Mittelwert), und
  ein langsamer Geräte-Sensor blähte das Fenster zusätzlich auf. Jetzt werden **nur die
  Bilanz-Eingänge PV/Netz/Batterie** angeglichen; **Geräte-Leistungen zeigen ihren Momentanwert**
  (eine gerade abgeschaltete Last steht sofort auf 0). Die Regelung nutzt weiterhin den geglätteten,
  netzbasierten Überschuss.

- **Strategie-Einstellungen direkt in der Karte + separates Aktiv-Enable.** Die schwellenbasierten
  Dienste (Peak-Shaving, Einspeise-Limit, Notstrom-Reserve, Batteriepflege) werden jetzt **in ihrer
  eigenen Strategiekarte** eingestellt (Schwellwert-Feld statt „→ Grundeinstellungen"). Zusätzlich
  hat **jede Strategie eine Aktiv-Checkbox**, die als **separates Enable** wirkt und die Einstellwerte
  **nicht** verändert — so kann man z. B. das Peak-Limit gesetzt lassen und den Dienst trotzdem
  vorübergehend abschalten. Bestehende Konfigurationen bleiben unverändert (Dienst mit gesetztem
  Schwellwert ist automatisch aktiv).

- **Geräte-Priorität eindeutig & per Pfeilen sortierbar.** Jedes steuerbare Gerät hat jetzt eine
  eindeutige Priorität; die Prio-Zahl entfällt, stattdessen **▲/▼-Pfeile** pro Zeile zum Verschieben.
  Neue Geräte kommen **unten** dazu. Überschrift jetzt **„Geräte (höchste Priorität oben)"** (schwarz).
- **Strategie-Kopfzeile neu:** rechtsbündig **Status-Label · Aktiv-Schalter · Info**. Neues Label
  **„operativ" (cyan)**, wenn die Strategie gerade tatsächlich eingreift (sonst aktiv / verfügbar /
  nicht verfügbar). Der Aktiv-Schalter sitzt jetzt in der Titelzeile (bei den schwellenbasierten
  Diensten Peak/Einspeise-Limit/Reserve/Pflege weiterhin über die Grundeinstellungen).
- **Icon-Buttons vereinheitlicht:** ⚙/ⓘ/▲/▼ nur noch als Icon, etwas größer und alle gleich breit.

- **Echter PI-Regler für regelbare Lasten (statt 1:1).** Der Heizstab wurde bisher pro Takt **1:1**
  auf den ganzen Überschuss gestellt (Deadbeat) — das schwingt bei Sensor-Totzeit und kippt in
  Netzbezug, was die geräteeigene Abschaltung des my-PV auslöst (Abstürze auf 0). Jetzt regelt ein
  **PI in Geschwindigkeitsform** (Δsoll = Kp·(e−e_prev) + Ki·e; die Lastleistung ist der Integrator):
  monotone Annäherung an Überschuss = 0, **ohne Überschwingen in Netzbezug**, eingeschwungen in ~80 s
  (statt Dauerschwingen). Zwei neue Einstellungen **„Modulation P-Anteil (Kp)"** (Default 0,1) und
  **„I-Anteil (Ki)"** (Default 0,2); Kp=0/Ki=1 = altes 1:1-Verhalten.

- **Fix: Sollwert nie über das Geräte-Limit senden.** Die Stellgröße wird jetzt auf das **Minimum
  aus konfigurierter max. Leistung und dem echten HA-Maximum der Entität** begrenzt. Bisher konnte
  ein zu hoher Wert (z. B. 3600 W an eine ELWA mit 3500 W) gesendet werden — das Gerät weist ihn ab,
  bekommt keinen gültigen Wert und läuft nach seinem Steuer-Timeout auf 0 (Netzeinspeisung statt
  Heizen).
- **Fix: „Daten unsicher, halten" friert regelbare Lasten nicht mehr grundlos ein.** Die
  Staleness-Erkennung hat jetzt einen absoluten Boden (180 s): ein gültiger, aber **ruhender**
  Sensor (z. B. die Batterie bei SoC 100 %, die kaum noch Updates schickt) wird nicht mehr für
  eine tote Quelle gehalten. Nur echte, lange Ausfälle halten die Modulation an.

- **Verlauf: CSV-Export** — Button „CSV-Export" exportiert alle Reihen des aktuell gewählten
  Zeitfensters (Bilanz inkl. **ungeklemmtem** Überschuss + alle Geräte-/Zusatzreihen) als
  Datei-Download (`sea_export_JJJJ_MM_TT:HH:MM.csv`).
- **Verlauf**: der kommandierte **Sollwert** regelbarer Lasten (z. B. ELWA `number.hz`) ist jetzt
  eine eigene plott-/exportierbare Reihe.

- **Fix: Heizstab/regelbare Lasten arbeiten jetzt kontinuierlich und ohne Rampe.** Der Überschuss
  wurde für modulierende Lasten geglättet — dadurch schaltete der Heizstab bei kurzen Haus-Spitzen
  ganz ab und kroch danach nur langsam wieder hoch (teils gar nicht mehr an), obwohl Überschuss da
  war. Jetzt folgt jede regelbare Last dem tatsächlichen Überschuss **direkt** (ein Regeltakt): sie
  regelt bei Bedarf **stufenlos herunter** statt abzuschalten, ist nur dann 0, wenn wirklich kein
  Überschuss da ist, und geht **sofort** wieder auf Volllast — kein langsames Hochrampen mehr. Die
  Einstellung „Modulation glätten (s)" entfällt.

- **Geräte-Seite** zeigt jetzt auch die **regelungsrelevanten Entitäten aus der Strategie**
  (Stopp-/Limit-Sensor wie die ELWA-Temperatur, „angesteckt", SG-Ready-Relais) — nicht nur
  Leistung/Energie.

- **Fix Einschaltschwelle geschalteter Lasten/Wallbox**: die Schwelle nutzte fälschlich die
  *aktuelle* Leistung (im Aus-Zustand 0 W) → die Wallbox sprang schon bei minimalem Überschuss an.
  Jetzt zählt die **Ladeleistung**: neues Feld **„max. Ladeleistung"** bei **Wallbox und Fahrzeug**,
  maßgeblich ist das **Minimum aus beiden**. So geht die Wallbox erst an, wenn PV (+ Batterie-
  Unterstützung) die Ladeleistung wirklich deckt.
- **„Laden aus Netz"**-Text angepasst: die **Batterie-Unterstützung zählt mit** (bei „aus" lädt sie
  aus PV + Batterie; bei „an" hat die Batterie Vorrang, das Netz füllt den Rest).

- **Batterie-Unterstützung beim Laden** (Wallbox u. a. Schaltlasten): pro Last einstellbar, bis zu
  wie viel Leistung sie aus der **Batterie** decken darf, um den **Netzbezug zu minimieren**. Eine
  geschaltete Wallbox geht so schon an, wenn **PV + Batterie-Budget** die Ladeleistung decken —
  die Batterie wird nie unter die **Reserve-SoC** entladen. Die Option erscheint nur, wenn die
  Batterie einen **Entlade-Sollwert** hat. Ist zusätzlich **„Laden aus Netz"** aktiv, lädt die
  Wallbox trotzdem durch — die **Batterie hat aber Vorrang** (deckt bis zum Budget), das Netz füllt
  nur den Rest.

- **Dashboard neu (Hero)**: der Live-**Energiefluss** steht groß oben, darunter kompakte
  **Kennzahl-Kacheln** (Hausverbrauch, PV, Netz, Batterie, Autarkie, Eigenverbrauch). Die
  **Energiebilanz** (heute) ist ans Dashboard-Ende gewandert (von der Verlaufsseite entfernt).
- **Modulation stabiler**: der Regeltakt ist auf **10 s** verkürzt (unveränderte Befehle nur als
  Keepalive ~55 s an HA). Regelbare Lasten (Heizstab, Batterie …) folgen dem Überschuss direkt und
  regeln bei hohem Hausverbrauch sofort herunter — behebt, dass Heizstab/Wallbox/Batterie
  fälschlich weiterliefen und **aus dem Netz** gezogen wurde.
- **Regeln**: der Zähler zeigt jetzt **grün „N aktiv"** und **blau „M verfügbar"** (jeweils nur,
  wenn vorhanden).
- **Scroll-Seitenwechsel**: etwas mehr Widerstand (höhere Schwelle).
- **Aktive Steuerung**: mehrere Stellgrößen desselben Geräts (z. B. Laden/Entladen der Batterie)
  werden zu **einer Zeile** zusammengefasst (keine Doppelanzeige mehr).
- **Aktive Steuerung** überarbeitet: alles in **einer Karte**, **Gerätenamen** statt
  Entitäts-IDs, Strategie-Bezeichnungen **1:1** wie bei den Geräte-Strategien, und die
  angezeigte Leistung ist die **Live-Ist-Leistung** (synchron mit dem Energiefluss; Sollwert als Nebeninfo).
- **Geräte**-Seite listet jetzt auch die **Fahrzeuge** (mit ihren Entitäten).
- **Verlauf**: größerer Hauptchart, ruhigere Legende.
- **Regeln (Strategien)**: eigene Klappkarte; jede Regel als Unterkarte mit **Name**,
  **Aktiv-Schalter**, **Entfernen** und JSON-Feld — statt eines einzigen JSON-Blocks.
- **Scroll-Navigation**: am Seitenende weiter nach unten scrollen öffnet die **nächste Seite**
  (nach oben am Anfang die vorherige), mit sanfter Einblend-/Snap-Animation; das Menü wird
  mitgesetzt. Höhere Schwelle gegen versehentliches Umschalten und **weiches „Vorschau"-Ziehen**:
  die Seite kommt beim Ziehen schon ein Stück und **flippt zurück**, wenn man nicht weiterzieht;
  auch per **Wischen** am Handy.
- **Temperaturabsenkung**: jede Gruppe als ein-/ausklappbare Karte (Gruppenname als Titel,
  „Gruppe entfernen" in der Titelzeile).
- **Grundeinstellungen** sind jetzt in **ein-/ausklappbare Karten** gegliedert (Allgemein,
  PV-Überschuss & Speicher, Tarife, Status) — wie die Strategien; beim Öffnen zugeklappt.
- **Komponenten**: jede Kategorie (Netz, Verbraucher, Fahrzeuge, …) ist eine **klappbare Karte**,
  die ihre Geräte **und** den „Hinzufügen"-Button enthält; beim Öffnen alle zugeklappt.
- Die **Seitenleiste bleibt beim Scrollen stehen** (fixiert unter dem Kopfbereich).
- Die **Strategie-Auswahl** wirkt jetzt als **Voreinstellung**: sie setzt die Master-Schalter
  (PV-Überschuss immer an; Tarif + Optimierer an bei Hybrid/Kosten, aus bei Eigenverbrauch/
  Autarkie) — danach frei feinjustierbar.
- **Reserve-SoC der Batterie** ist jetzt immer einstellbar (nicht mehr hinter „Tarif-Netzladen"
  versteckt); „Batterie-Mindest-SoC" heißt zur Klarheit **„Lade-Vorrang bis SoC"** (das ist die
  Lade-Vorrang-Schwelle, nicht die Entlade-Reserve).
- **Batterie-Tarif vereinheitlicht**: das einfache Schwellen-Netzladen läuft nur bei aktivem
  Tarif und nur, wenn der Prognose-Optimierer aus ist (sonst hat der Optimierer Vorrang).
- **Hilfe-Button (ⓘ)** mit Beschreibung für **jede** Strategie.
- **Einsparungsseite** überarbeitet: Ersparnis wird **grün**, Mehrkosten **rot** dargestellt
  (Betrag ohne Vorzeichen, Beschriftung „Ersparnis vs. Baseline" bzw. „Mehrkosten vs. Baseline").
  Die Erklärung der Vergleichs-Baselines liegt jetzt im **ⓘ-Popup** neben dem Auswahlfeld.
- **Einsparungsseite** sauber ausgerichtet: Zeitraum-Auswahl, Baseline-Selektor und die Felder
  darunter stehen in einem Raster gleicher Breite untereinander.
- Neue Baseline **„Dynamischer Tarif (Potenzial mit Speicher)"** mit realistischer
  Batterie-Simulation: drei Preisstufen (Hoch 17–21 Uhr / Niedrig 0–6 Uhr / Normal), eine Batterie
  der **einstellbaren Größe** wird über die echte Zeitreihe gerechnet (lädt PV-Überschuss, deckt
  den Verbrauch, lädt nachts günstig nach, entlädt in der Abendspitze). **Speichergröße** und
  **PV-Spitzenleistung** sind mit der aktuellen Anlage vorbelegt — durch Anpassen sieht man das
  Potenzial einer größeren Batterie bzw. eines PV-Ausbaus (Ertrag per Dreisatz skaliert).
- **PV-Überschuss-Senke**: zusätzlich zur Leistungsgrenze jetzt eine **Tages-Energiegrenze** (kWh)
  einstellbar (eigener Speicher der Senke, z.B. Warmwassertank/Auto-Akku); Auswahl per Selektor
  (Heizstab/Auto/Eigene).
- **Einsparungsseite** neu gegliedert: Zeitraum und Baseline-Selektor (in einer Karte mit dem
  ⓘ-Button) nutzen die volle Breite; die Prämissen (Tarif, Speicher, PV bzw. Senke) stehen jeweils
  in einer eigenen Zeile.
- **Modulierende Lasten ruhiger geregelt**: der Überschuss für die Modulation wird jetzt geglättet
  (neue Einstellung „Modulation glätten (s)", Standard 120 s, 0 = aus). Kurze Haus-/Batterie-Spitzen
  takten einen Heizstab nicht mehr auf 0 und wieder hoch.
- **Robust gegen nicht-synchrone Messwerte**: eine modulierende Last wird erst abgesenkt, wenn ein
  Defizit über mehrere Zyklen bestätigt ist (Entprellen); solange Überschuss/Einspeisung anliegt,
  bleibt sie an (Export-Schutz). Ein einzelner „verrutschter" Messpunkt wirft sie nicht mehr ab.
- **Sensor-Update-Rate**: auf der Seite „Geräte" steht jetzt hinter jeder Entität, wie oft sie
  aktualisiert (z. B. „(alle ~2 s)"), und veraltete Werte werden markiert.
- **Zeitliche Angleichung (neu, Grundeinstellungen „Sensoren zeitlich angleichen")**: nicht-synchrone
  Leistungssensoren werden vor der Bilanz zeitlich ausgerichtet — die schnellen über die Kadenz des
  langsamsten gemittelt, der langsamste hält seinen Wert. Basis für **Energiefluss-Anzeige und
  Regelung** → ruhigeres, konsistenteres Bild.
- **Staleness-Gate**: ist ein Bilanz-Sensor (Netz/Batterie) deutlich veraltet, werden modulierende
  Lasten eingefroren, statt auf veraltete Daten zu reagieren.
- **Heizstab/modulierende Lasten**: Stopp-Bedingung (z. B. „Stopp bei ≥ 65 °C") kann jetzt mit
  **Hysterese (Δ)** versehen werden — Wiederanlauf erst unter (Schwelle − Δ). Verhindert das
  schnelle Takten am Limit (ruhige, lange Zyklen statt Sägezahn).
- **Verlauf**: der **Begrenzungs-Sensor** einer Last (z. B. die ELWA-Temperatur „Stopp bei") wird
  jetzt im Detail-Plot mit dargestellt.
- **PV-Überschuss-Modulation**: regelt nun auf die **gemessene Ist-Leistung** der Last (statt des
  kommandierten Sollwerts) — sauberes Einschwingen ohne Überschwingen während der Rampe.
- **Einsparung (dynamische Baseline)**: Netz-Nachladen im Niedrig-Fenster nur noch, wenn es sich
  nach Wirkungsgrad-Verlusten lohnt (kein Verlustkauf bei flachem Tarif → größerer Speicher
  verschlechtert das Ergebnis nicht mehr).
- **Verlauf**: feste Zeiträume sind jetzt **kalender-ausgerichtet** (Tag 0–24 Uhr, Woche ab Montag,
  Monat ab dem 1., Jahr ab 1. Januar) statt rollierend ab „jetzt". ◀ ▶ blättert exakt einen
  Zeitraum weiter (z.B. einen Monat zurück). Neuer Button **„jetzt"** lässt den frei eingegebenen
  Zeitraum am aktuellen Zeitpunkt enden (z.B. letzte 24 h / 30 / 365 Tage).

## 0.7.0

- Neu: Dashboard-Panel **„Aktive Steuerung"** — zeigt live, welcher Regler gerade was
  und warum schaltet. Peak-Shaving, Einspeise-Limit, Notstrom-Reserve und Batteriepflege
  erscheinen jetzt mit Status auf der **Strategieseite**.
- Neu: **Regel-Editor** (JSON-logic) auf der Strategieseite; **Batterie-Kapazität** und
  optionale **PV-Abregel-Entität** konfigurierbar. Tageswerte (Mindestmenge, Pflege)
  überstehen jetzt Neustarts; der Optimierer nutzt die **Preis-Prognose** dynamischer Tarife.

- Neu: **Einspeise-Limit** — übersteigt die Einspeisung eine Grenze (W), wird die
  Batterie zwangsgeladen, um darunter zu bleiben.
- Neu: **Notstrom-Reserve (%)** — die Batterie wird auf diesen Ladezustand gehalten/
  geladen und von keiner Strategie darunter entladen (Backup für Stromausfall).
- Neu: **Zeitfenster-Peak-Shaving** — pro Tageszeit eigene Netzbezugs-Grenzen.
- Neu: **Batteriepflege** — periodische Vollladung (alle N Tage) zur SoC-Kalibrierung.

- UI: Der Menüpunkt „Erzeuger/Verbraucher" heißt jetzt **„Komponenten"** und enthält
  zusätzlich die **Fahrzeug-Verwaltung** (die separate Seite „Fahrzeuge" entfällt) —
  alle Anlagen-Komponenten an einem Ort.

- Neu: **Wärmepumpe SG-Ready** — zwei Relais (4 Zustände: normal / Anhebung / Zwang /
  Sperre) werden aus dem PV-Überschuss (und teurem Tarif) angesteuert.

- Neu: **Mindest-Energie/Tag** für mehrstufige Heizstäbe — wird notfalls rechtzeitig
  aus dem Netz garantiert (Energie-Pendant zum „spätesten Start").

- Neu: **Prognose-Optimierer (Batterie)** — lädt/entlädt die Batterie vorausschauend
  nach PV-Prognose und Strompreis (günstig laden, teuer entladen) und netzoptimiert
  (kein Netzladen, wenn die PV den Speicher noch füllt). Auf der Strategieseite
  aktivierbar; Reserve/Peak-Shaving bleiben übergeordnet. Standardmäßig aus.

- Neu: **Fähigkeits-Modell** intern — Geräte werden über Fähigkeiten (Speicher,
  ladbar, schaltbar, Stufen …) angesprochen; ein späteres V2G-Fahrzeug nimmt damit
  automatisch an Reserve/Peak/Eigenverbrauch teil.

## 0.6.0

- Neu: **Mehrstufiger Heizstab** — bei Warmwasser/Wärmepumpe lassen sich mehrere
  Schalt-Stufen (Relais) zuordnen; sie werden je nach PV-Überschuss zu-/abgeschaltet
  (max. Leistung gleichmäßig verteilt), notfalls bis zum „spätesten Start" erzwungen.

- Neu: **Fahrzeuge** als eigene Objekte (Seite „Fahrzeuge", mehrere möglich), getrennt
  von der Wallbox. Je nach Fähigkeit: nur SoC (Stopp-Signal), ladbar (Wallbox lädt bis
  Ziel-SoC) oder bidirektional (V2H/V2G – nimmt wie ein Speicher an Eigenverbrauch,
  Peak-Shaving und Reserve teil). Wallbox-Ladestopp folgt dem verknüpften Fahrzeug.

- Neu: Auf der Seite „Verlauf" eine **Energiebilanz** (unter den Detail-Plots), die
  über den aktuell angezeigten Zeitraum gerechnet wird (inkl. Zoom/Pan): PV-Erzeugung,
  Hausverbrauch, Netzbezug/-einspeisung, Batterie geladen/entladen, Eigenverbrauch,
  Eigenverbrauchsquote und Autarkiegrad.

- UI: Auf der Geräte-Einstellungsseite („Erzeuger/Verbraucher") sind die Überschriften
  der ausklappbaren Geräte-Karten wieder schwarz.

- Fix: Die angezeigte Version entspricht jetzt der tatsächlich laufenden (vorher
  blieb „0.2.1" stehen) — sie wird zur Laufzeit aus dem Build übernommen.

- Neu: Eigener Schalter „Dynamischer Tarif: Lastverschiebung aktiv" auf der
  Strategieseite — die Tarif-Lastverschiebung lässt sich jetzt unabhängig von der
  PV-Überschusssteuerung ein-/ausschalten.

- Der Schalter „Temperaturabsenkung aktiv" (vorher „Absenkung aktiv") steht nur
  noch auf der Strategieseite, nicht mehr zusätzlich bei den Thermostat-Einstellungen.

- UI: Seitentitel „Verlauf" (vorher „Verlauf & Prognose").

- UI: jede Seite hat jetzt eine Überschrift mit dem passenden Menü-Icon (vorher nur
  das Dashboard) und eine klarere Gliederung mit Unterüberschriften. „Erzeuger/
  Verbraucher" erscheint nun als Seitentitel statt als schlichte Zeile.

- UI: normale Schreibweise statt durchgängiger Großschreibung. Kategorien (z. B.
  Batterie, Wallbox, Gerätenamen) jetzt rot, fett und etwas größer; Untergruppen
  (z. B. Leistung, Energie) schwarz und fett. Seitenüberschriften etwas größer.
  Versionsnummer nicht mehr im Kopf — sie steht in den Grundeinstellungen.

- **Neu: Peak-Shaving** — Einstellung „Netzbezug deckeln bei (W)" (Grundeinstellungen,
  0 = aus): übersteigt der Netzbezug diesen Wert, entlädt die Batterie gezielt, um
  darunter zu bleiben (höchste Priorität vor Eigenverbrauch/Tarif). Benötigt eine
  Batterie mit Entladeleistungs-Sollwert-Entität.

- Leistungsfluss-Diagramm: auf dem **Handy größere Kreise** mit mehr seitlichem
  Abstand; expandierte Verbraucher (über „+") **stapeln jetzt nach unten** und
  schieben die folgenden Kreise nach unten (Rahmen wächst mit). Im Browser Kreise
  und Schrift minimal größer.

- „Auto angesteckt" (Wallbox) lässt sich jetzt auch mit **Sensor-Entitäten**
  belegen (z. B. ein Coupler-/Plug-Status-Sensor mit Textzustand), nicht nur mit
  Boolean-/Binary-Sensoren — neue, breitere Auswahl-Filtergruppe „connected".
- **Leistungsfluss-Diagramm:** größere, besser lesbare Schrift; auf dem **Handy**
  ein eigenes **vertikales Layout** (Haus oben als Knoten, die übrigen Größen in
  zwei Spalten darunter) statt des breiten, herunterskalierten Stern-Layouts.

- Geregelte Sollwerte werden jetzt **jeden Zyklus (re)geschrieben**, auch
  unverändert — manche Aktoren (z. B. Heizstab-Leistungssollwert) fallen sonst
  auf 0 zurück (Keepalive).
- **Wallbox:** Stopp-Bedingung als **„Fahrzeug-SoC"** ausgewiesen (lädt bis zum
  Ziel-SoC); zusammen mit „Auto angesteckt" sind so beide Fahrzeug-Entitäten
  konfigurierbar.
- **Dashboard:** neue Karte **Batterie-SoC (%)**. Karten **Netz** und **Batterie**
  zeigen nur noch positive Werte mit Richtungstext (**Bezug/Einspeisung** bzw.
  **Ladung/Entladung**).
- **Verlauf:** das Netz erscheint nur noch als **eine** Netto-Linie (Bezug −
  Einspeisung), auch wenn getrennte Bezugs-/Einspeise-Entitäten konfiguriert sind;
  die Batterie ebenso als eine Größe.

- Erzeuger/Verbraucher komplett auf ein **einheitliches Spalten-Layout** umgestellt
  (ein gemeinsames Zeilen-Raster für alle Felder): ausgewählte Entitäten stehen
  jetzt **linksbündig untereinander** in einer Spalte, „Ändern" durchgehend
  **rechtsbündig**, Zahlen-/Eingabefelder sauber ausgerichtet. **Heizkreise**
  übersichtlich als *Name*-Zeile mit *Temperatur*/*Sollwert* darunter (statt
  „Temp … Soll" in einer Zeile). „Steuerung" steht oben im Block; die Entität der
  Steuerung bekommt eine eigene, ausgerichtete Zeile. Eigene, kompakte
  **Handy-Variante** (Label-Zeile, darunter Wert + Aktionen).

- Aufklappbare Boxen (Geräte, Strategien) zeigen jetzt ein **ausgefülltes Dreieck**
  als Aufklapp-Icon: ▶ zugeklappt, dreht zu ▼ beim Öffnen. Die „Steuerung"-Zeile
  unter Erzeuger/Verbraucher ist sauber ausgerichtet; die Entitäts-Auswahl
  (Chip · Ändern · ×) bleibt als Gruppe zusammen und bricht bei Platzmangel
  gemeinsam um.

- UI-Korrekturen: Menü-Schrift etwas kleiner, damit der längste Eintrag in den
  (bei Auswahl gefärbten) Kasten passt; bei Erzeuger/Verbraucher sitzen Checkboxen/
  Radios und ihr Text jetzt **exakt auf einer Höhe** (0 px Versatz).

- UI-Feinschliff: roter **Header bleibt fix** stehen, nur der Inhalt darunter
  scrollt vertikal; **Menü-Texte kleiner** (passen in die Box); Grundeinstellungen
  mit **einheitlich ausgerichteter Eingabespalte**. Im **Handy-Modus**: Hamburger
  und Titel auf gleicher Höhe (Titel etwas weiter rechts), Geräte-Einstellungen
  sauber gestapelt statt verrutscht, und insgesamt **kleinere Schriften/Formen**,
  damit mehr auf die Seite passt.

- **Neues UI-Design** für alle Seiten: einheitliches Layout (festes 1024-px-
  Desktop, schmaler ⇒ horizontaler Scroll; Mobil hochkant mit Hamburger-Menü
  unterhalb des Headers, nur inhaltshoch), saubere Ausrichtung, einheitliche
  Buttons, durchgängiges SVG-Icon-Set. Header wie SmartHub: weiße Logo-Zeile
  über dem roten Banner (neue, dezente Sonne-/Wellen-Grafik), Schrift „Lucida
  Sans". Verbindungs-/Aktualisierungsstatus jetzt klein neben dem Dashboard-
  Titel statt im Header. Einsparung mit Münzen-Icon.

- **Schaltlasten: „unterbrechbar"** – neue Checkbox je geschalteter Entität (in
  der Geräte-Steuerung). An (Default): eine laufende Last darf bei Wegfall von
  Überschuss bzw. günstigem Tarif wieder abgeschaltet werden (z. B. Heizstab).
  Aus: die Last läuft nach dem Start bis zum Ziel durch und wird nur abgeschaltet,
  wenn das Ziel erreicht ist (z. B. Waschmaschine) – gilt für PV-Überschuss- und
  Tarif-Steuerung. Die Strategie-Beschreibungen erwähnen den Status im Beispiel.

- **Strategie-Beschreibungen**: jede Strategie hat jetzt einen **ⓘ-Info-Button**
  (nur Icon) neben ihrem Titel im Strategien-Bereich. Er öffnet eine kompakte
  Beschreibung (Funktionsweise · Voraussetzungen · Beispiel) in einem Overlay
  **innerhalb des SEA-Frames** (kein neues Fenster). Die **Voraussetzungen
  spiegeln die aktuelle Konfiguration** (✓/✗/⚠: PV+Netz, aktivierte Geräte mit
  Priorität, Master-Schalter, Vorrang/Mindest-SoC, Preisquelle + Schwellen,
  Thermostat-Gruppen), und das **Beispiel wird aus den real konfigurierten
  Geräten** und ihren Einstellungen gebaut (Name, Prio, max. Leistung, Stopp-
  Grenze, Deadline „spätester Start“, Lade-/Entlade-Schwellen, Absenk-Delta &
  Vorheiz-Vorlauf). Für PV-Überschuss, dynamischen Tarif und Temperaturabsenkung.

- **Bugfix – PV-surplus no longer runs loads from the battery**: the surplus
  controller regulated the grid to zero (`−grid_w`). With a battery present a
  *discharging* battery holds the grid at ~0 by itself, so a controllable load
  (e.g. an immersion heater) was never throttled back and kept draining the
  battery at night with no PV. The signal now folds in the battery power
  (`surplus_signal()`), so a discharging battery is never counted as surplus.
  New setting **„PV-Überschuss-Vorrang"** (Grundeinstellungen,
  `surplus_loads_first`): *Batterie zuerst* (default) gives loads only the
  export overflow, *Verbraucher zuerst* lets loads take PV directly (battery
  charges with the rest). Either way loads never run from the battery.
  Additional **„Batterie-Mindest-SoC (%)"** (`surplus_battery_min_soc`, 0 = off):
  in *Verbraucher zuerst* the battery keeps its charging power until the SoC
  reaches this reserve, so the storage is filled first before loads may divert
  the charge power.

- Verlauf: **drag a time range with the mouse** on any plot to zoom into it
  (a selection rectangle follows the drag); the range buttons (24 h/7 d/30 d)
  reset. All plots share the same window.
- Menu reordered: Dashboard, Verlauf, Strategien, Einsparung, Geräte,
  Einstellungen. Device gear buttons now open just that device's settings block
  (all others collapsed).
- Verlauf reworked: the **top plot now also shows every device's power**
  (consumers, wallbox, battery …) as toggleable series next to the balance
  (Haus/Netz/Überschuss). For the devices selected (enabled) in the top legend, a
  **set of detail plots** appears below — **one plot per sensor class** (all
  temperatures together, all SoC together, …) from HA's recorder, each auto-scaled
  to its own range. All plots share the **same time window** as the top plot.
  **Cumulative energies (kWh) and the measured device power are not repeated**
  below (the power is already in the top plot) — only additional quantities like
  the forced charge/discharge setpoint appear in the detail plots. New HA history
  fetch (`get_history`) + `/api/history-devices` and `/api/entity-history`.
- **Battery arbitrage – forced discharge at expensive prices**: a new battery
  actuator "Entladeleistungs-Sollwert (erzwungen)" lets the battery discharge on
  the dynamic tariff. New ceiling "Speicher entladen bei ≥ (ct/kWh)" (0 = off):
  when the price is at/above it and the SoC is above the reserve floor, the
  battery is driven to full discharge; charge/discharge/surplus are mutually
  exclusive (one controller). The battery's tariff toggle now governs both
  grid-charge and forced discharge, sharing the reserve-/target-SoC band.
- **Battery grid-charging on the dynamic tariff**: the battery can now charge
  from the grid in cheap/negative price windows. A global price ceiling
  "Speicher netzladen bei ≤ (ct/kWh)" (default **0** = only free/negative) plus a
  per-battery **target SoC band** (min reserve … max). Below the reserve floor it
  tops up at any price; otherwise it charges to the max target only when the
  price is at/under the ceiling (positive-price grid charging loses money to
  round-trip losses, hence the conservative default). The ControlEngine owns the
  battery in both surplus and grid-charge modes (no conflict with the tariff
  engine). Thermal storage already shifts via tariff load-shifting.
- Strategy list tidy-up: the separate "Wallbox PV-Überschussladen" and
  "Batterie-Optimierung" strategies are **removed** — both are already covered by
  the unified surplus list. Renamed: **"PV-Überschuss: Eigenverbrauch und
  Speicherung"** and **"Dynamischer Tarif: Lastverschiebung"**. The per-device
  settings button is now a small **gear icon (⚙)**.
- Tariff load-shifting follow-ups:
  - the **"spätester Start" deadline now also applies to tariff shifting** — a
    deferrable load (e.g. washing machine) is force-started by its deadline even
    if the tariff never got cheap. The deadline shows in the list (⏱ spätestens …).
  - the tariff list gained the **"Einstellungen →"** buttons (right-aligned, as in
    the surplus list).
  - **battery stop is the SoC** (already known) — the device block now asks only
    for the threshold ("Stopp bei SoC ≥ … %"), no entity picker. A threshold of 0
    disables the stop. For other devices the set-stop button is small/icon-only.
- Strategy UI reworked per feedback:
  - **One unified PV-surplus list**: all controllable devices (incl. wallbox AND
    battery) now live in the "PV-Überschuss-Eigenverbrauch" box, **sorted by
    priority** (high → low). The separate Wallbox/Batterie boxes no longer carry
    their own device lists. On the strategy page you only pick devices and set
    priority.
  - **Device-specific settings moved to the device block** under
    "Erzeuger/Verbraucher" (a new "PV-Überschuss-Steuerung" panel per device):
    PV threshold, min runtime/off, max starts, max/min power, W-per-unit, the
    wallbox "vehicle connected" entity and the stop condition.
  - **New "spätester Start" deadline** for deferrable loads (e.g. washing
    machine): if no surplus came by then, the device is **force-started** (from
    the grid if needed) within a 2 h window after the deadline.
- Fix "Aktueller Bezugspreis – (Entität liefert noch keinen Wert)" for dynamic
  tariffs: the current price now reads the entity's live/snapshot value
  immediately (no longer waits for the next hourly state change), the price
  entity is added to the watched set so its value stays fresh, and the value is
  **normalised to ct/kWh** from its unit (EUR/kWh, EUR/MWh, … are converted).
- **Critical persistence fix**: storage was briefly pointed at `/addon_config`,
  which is NOT a mount point — writes went to the container's ephemeral overlay
  and were lost on every restart/update (battery charge setpoint, tariff and
  other settings appeared "not saved"). The `addon_config:rw` share is mounted at
  **`/config`**; storage now uses `/config`. Migration copies any files left in
  `/data` or `/addon_config` over once.
- Fix persistence/refresh of the tariff & strategy settings:
  - the **tariff mode** dropdown now saves immediately (previously the choice was
    lost unless "Speichern" was clicked), and saving the tariff refreshes the
    strategy availability (a dynamic price source enables `tariff_shift` live).
  - the **price-entity picker** is now universal — it matches common dynamic
    tariff sensors (monetary device class, ct/kWh·EUR/kWh·öre/kWh·EUR/MWh… units,
    and number/input_number helpers), so the price entity is actually selectable.
  - added a round-trip persistence test (settings, strategy-loads, wizard config).
- **New strategy – Wallbox PV-Überschussladen (`ev_surplus`)**: the wallbox now
  follows the PV surplus via the unified modulation, with a **minimum charge
  power** (below it the wallbox switches off instead of pulling from the grid)
  and an optional **"vehicle connected"** guard entity. Excluded from the
  generic PV-surplus box (own box), kept selectable for tariff shifting.
- **New strategy – Dynamischer Tarif / Lastverschiebung (`tariff_shift`)**: a new
  `TariffEngine` runs deferrable loads during cheap periods. **Universal price
  model** (`tariff.py`) that adapts to whatever is registered: a dynamic price
  entity's upcoming-price attribute (greedy cheapest fraction), else an absolute
  threshold, else the static HT/NT window. The Strategien page shows the live
  "cheap/expensive" status. Both engines are gated by the master control switch.
- Entity picker: once an entity is selected, suggestions are narrowed to others
  with the **same name prefix** (same leading object-id tokens), so changing a
  pick stays within the same device/integration. Typing a search query lifts the
  restriction to find other families.
- Fix: the battery **charge-power setpoint** picker showed no candidates — its
  field used an undefined `number` unit group, so nothing ever matched. Added
  the `number` unit group (domains `number`/`input_number`); writable number
  entities can now be selected.
- Banner simplified: now shows only the sun (moved slightly right) — the PV
  modules, car and lightning bolt are gone. Gradient unchanged.
- **Persistent settings**: config + history now default to `/config` (the
  host-mapped `addon_config` share) instead of the add-on's private `/data`
  volume, so settings survive an uninstall/reinstall (HA wipes `/data` on
  uninstall). On update, existing legacy files are copied over once
  (non-destructive).
- Strategy device rows: the stop condition is now a small black ■ button on the
  device row; once set it appears on an indented second line. The line no longer
  has a checkbox — to remove it, click "ändern" and pick "— nicht zugeordnet —".
  Tooltips added across the pages (incl. "W/Einheit").
- Savings: the explanation text now adapts to the selected baseline.
- Dashboard: the power-flow frame height fits the diagram and grows for expanded
  sub-power circles (no more cut-off when expanding consumers).

- **Battery control**: the battery can take a charge-power setpoint (new wizard
  field) and then participates in PV-surplus as a **modulating load** (priority
  vs other loads configurable) — the Batterie-Optimierung strategy becomes
  available/active accordingly.
- **Consumer stop conditions**: per device an optional limit (e.g. vehicle SoC or
  temperature ≥ value). When reached the device is "satisfied" — switchable loads
  are switched off, modulating loads driven to 0 — so the **remaining surplus is
  redistributed to the other consumers**.

- Strategies now reference the **configured devices** (from Erzeuger/Verbraucher),
  not raw entities: pick which devices take part in PV-surplus self-consumption
  (and tariff shifting) per device, with priority/threshold/runtime. Multiple
  devices supported.
- **Modulating (regelbare) loads** (e.g. heating rod, wallbox) now absorb the
  **remaining surplus**: the control engine sets their power setpoint (number)
  to drive the grid toward zero, allocated by priority across all modulating
  loads, clamped to a max power, with a W-per-unit factor (e.g. wallbox amps).
  Switchable loads keep on/off control. The engine now uses the signed grid
  signal (fixes shedding after the surplus≥0 clamp).

- Strategien page: each strategy is now an **expandable box** with its settings
  inside (PV-surplus self-consumption holds the master switch + consumer control;
  setback holds its enable + link). Toggling an activation updates the box status
  (verfügbar ↔ aktiv) live.
- Tariff: the dynamic price entity now uses the same **entity picker popup**
  (new 'price' unit group).

- Strategies are now **auto-detected from the configured entities** and listed on
  the Strategien page with status (aktiv / verfügbar / verfügbar (folgt) / nicht
  verfügbar) and what's still missing — PV-surplus self-consumption, wallbox
  surplus charging, dynamic-tariff load shifting, battery optimisation, absence
  setback. `GET /api/strategies`, `strategies.overview()`.
- Removed the obsolete Phase-1 footer.

- Temperaturabsenkung reworked into **groups** (persons + their rooms): a group
  is set back only when **all** its persons are away; comfort returns when anyone
  is home. Multiple groups supported. Optional **predictive pre-heating** to a
  per-group comfort time using a **learned reheat rate** (min/K, EWMA). Frost
  guard + opt-in unchanged. Full-object `POST /api/thermostats` with server-side
  sanitising; live presence shown per group.

- Mobile: the sidebar collapses into a slide-in drawer; a white hamburger icon
  (from SmartHub) appears on the red header to toggle it, with a backdrop and
  auto-close on navigation. Desktop layout unchanged.

- New **Thermostate** settings page (Einstellungen → Thermostate): absence
  temperature setback for room/radiator thermostats (concept 6.6). Add named
  thermostats (climate entity + comfort/eco °C), a global presence entity, frost
  guard and a master switch. A new engine sets eco on away and comfort on home
  (opt-in, respects frost, no-op while presence is unknown). HA `call_service`
  now supports service data (climate.set_temperature).
- Power-flow: wider spacing for expanded sub-power circles (readable labels).

- Merged the forecast into the **Verlauf** view (removed the separate "Prognose"
  menu item): the forecast is drawn as **dashed lines in the same colours** as
  the history; chart colours now match the dashboard. Added **pan ◀/▶** buttons
  and a **free from/to** datetime selection (alternative to 24 h / 7 d / 30 d).
  The history API accepts an explicit `from`/`to` window; a time-based x-axis
  with a "now" marker aligns history and forecast.
- PV surplus is now clamped to **≥ 0** (no negative "surplus" when importing) —
  in the live balance, the recorded history and the forecast.
- History and forecast charts: shared renderer with **nice y-axis ticks, subtle
  horizontal/vertical grid lines and multiple x-axis time labels**.

- Power-flow diagram keeps a **configured device visible even when its entities
  are temporarily unavailable** (shows "–" instead of dropping the node);
  `balance` marks loads `configured` and reports unavailable parts as None.
- Tooltips on the setup buttons (Wählen/Ändern, clear ×, remove −, add, Entfernen,
  expand +/−, close).
- Setup page made compact: each device is now a **collapsible panel** (summary
  shows name + entity count), rows are tight and single-line where possible, and
  named powers/energies/circuits render as inline chips.
- UI cleanup: removed the "Auswahl der Entitäten" view; **Einrichtung** moved
  under **Einstellungen** (Einstellungen → Grundeinstellungen / Einrichtung).
  Tariffs merged into Grundeinstellungen and **pre-filled from the Energy
  dashboard** (price / feed-in / dynamic price entity) when not yet entered.
  Removed the global sign-invert checkboxes (per-instance invert is in the wizard).
- Wizard redesigned to a uniform **instance pattern**: setup starts empty with
  "… hinzufügen" buttons; every genus (PV, battery, heat pump, heating rod,
  wallbox, consumer) is an addable, renameable, removable instance — only the
  grid stays a fixed section. Entity pickers collapse to a summary after
  selection. Heat pump (and any genus) supports **multiple named powers/energies**
  (two pumps + auxiliary heater) and **heating circuits** (temperature + setpoint).
  Controllable instances get a **control radio** (switch via strategy / setpoint)
  that then asks for the actuator entity. Driven by a declarative
  `setup_catalog.INSTANCE_KINDS`; the whole config is posted and **sanitised**
  server-side; the old flat beta config is migrated automatically.
- Power-flow diagram: one **summary circle per device** with a **"+"** that
  expands its individual sub-powers as circles to the right (`balance` now emits
  `loads` with `parts`).
- Energy-dashboard pre-fill now **derives the power (and battery SoC) entity from
  the same HA device** as the configured energy entity — for PV, grid and battery
  — so power slots get pre-selected even when only energy entities are set up.
- Entity selection moved into a **popup dialog** (search + ranked list) opened by
  an "Ändern/Wählen" button, keeping the setup page clean.
- Suggestions now include **diagnostic/config entities** (heat-pump powers are
  often diagnostic) — previously hidden, so search couldn't find them; they rank
  slightly below primary entities. Same for device-based power derivation.
- Wizard: **free, user-named consumers** ("Weitere Verbraucher", e.g. "Allgemein",
  "Wohnungen") — each with its own power/energy entity (multi). They appear as
  extra nodes in the power-flow diagram and as groups in the device view.
- Dashboard: native animated **power-flow diagram** (SVG) — house in the centre
  with PV, grid (import/export direction), battery (charge/discharge + SoC) and
  the configured loads (heat pump, wallbox) as nodes; flow lines animate in the
  direction of energy flow with width scaled by power. Fed by `/api/flow`
  (balance now also reports wallbox power `ev_w`).
- Wizard fixes: multi-select (PV) no longer accumulates silently — already
  selected entities that the current search hides are now pinned (and can be
  unchecked), and the list re-renders after each change. The invert flag
  (grid / battery) is now also visible in the device view, which shows the
  sign-adjusted live power.
- Wizard: added the **wallbox / EV charger** category (charging power + energy +
  control actuators: charge-current setpoint and on/off), prefilled from the
  Energy dashboard's named device consumption.
- Heat pump now supports **multiple entities per quantity**: several power and
  energy meters (e.g. two pumps, summed), plus multi temperature sensors
  (heating circuits, DHW/buffer tanks — shown in the device view) and multiple
  control actuators (climate entities / setpoints per circuit). Energy-dashboard
  prefill accumulates several matching device-consumption entries into a list.

- Guided setup wizard ("Einrichtung"): instead of unreliable auto-classification,
  the user assigns the entities the agent really needs per logical category
  (v1: PV, heat pump, grid), choosing from HA-ranked suggestions — independent of
  which HA device an entity belongs to (solves scattered heat-pump entities and
  power measured by a separate Shelly PM3). New `setup_catalog.py` (slot catalog)
  and `suggest.py` (ranking + energy-prefs prefill); endpoints under `/api/setup/*`.
- Pre-fill from the HA Energy dashboard (`energy/get_prefs`): solar/grid power
  (`stat_rate`), energy meters, price entity and named device consumption
  (heat pump) are proposed top-of-list; one-click "Aus Energy-Dashboard übernehmen".
- The live energy balance now uses this explicit configuration once PV or grid
  power is set (`aggregator.balance_from_config`), falling back to the legacy
  role-based aggregation otherwise.
- Wizard now also covers the **battery** (charge/discharge power + SoC, sign
  flag; included in the balance: house = pv + grid − battery) and **control
  actuators** — for the heat pump a climate/thermostat entity or a number
  setpoint for the temperature setback/raise (marked "Stellgröße").
- Device view reworked: entities grouped by logical category (PV / battery /
  heat pump / grid) with live values, regardless of their HA device
  (`GET /api/categories`).
- App version shown in the header.
- Tests for the suggestion ranking, energy-prefs prefill (incl. battery) and
  config-based balance (incl. battery).

- Phase 2 (forecast): history-based household consumption forecast
  (recency-weighted hour-of-day load profile, weekday/weekend split) with a
  backtest of forecast accuracy (MAE/MAPE).
- Phase 2 (forecast): PV forecast from Home Assistant. Primary source is the
  Energy-dashboard `energy/solar_forecast` (Forecast.Solar; HA-cached, no
  upstream API hit, no entity config needed); a configurable PV-forecast entity
  (Solcast `detailedForecast`, generic list) is the fallback. The solar forecast
  is pulled on connect and refreshed every 15 min. Plus the resulting PV-surplus
  forecast (surplus = PV − load) — all via `GET /api/forecast`.
- New "Prognose" dashboard view: 24 h consumption/PV/surplus chart, kWh summary
  and forecast-error figure.
- Add unit-test setup (`pytest`, `requirements-dev.txt`) covering the forecast.

## 0.1.0

- First version: detection and curation of energy-related entities, live energy
  flow, history, consumer configuration, tariffs (purchase price/feed-in
  compensation), savings calculation with selectable baseline, and
  (off-by-default) PV-surplus control.
