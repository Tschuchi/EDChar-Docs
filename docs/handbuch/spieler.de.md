# Spieler

## Deine Charaktere

Im Spieler-Modus zeigt die Seitenleiste **Charaktergenerator Earthdawn 1st Edition** und **Deine Charaktere:**. Klicke auf einen Charakter, um ihn zu öffnen. Solange ein Charakter offen ist, sind die anderen ausgegraut. Zum Schließen klickst du oben links im Hauptbereich auf das **X**.

Unter der Liste stehen diese Buttons:

| Button | Was er tut | Verfügbar |
|---|---|---|
| **Neu** | Legt einen neuen Charakter an, siehe unten | wenn kein Charakter offen ist |
| **Entf** | Öffnet **Charakter löschen**. Charakter auswählen und *Das lässt sich nicht rückgängig machen! '…' löschen?* bestätigen | wenn kein Charakter offen ist |
| **Export** | Lädt den offenen Charakter als `.edchar`-Datei herunter | wenn ein Charakter offen ist |
| **Import** | Lädt einen Charakter aus einer `.edchar`-Datei. Gibt es schon einen Charakter mit diesem Namen, wird nach Rückfrage eine Kopie angelegt. | immer |
| **PDF-Export** | Lädt den offenen Charakter als PDF-Charakterbogen herunter | wenn ein Charakter offen ist |

!!! example "Screenshot: `player-character-list.png`"
    Seitenleiste mit **Deine Charaktere:** und den Buttons **Neu**, **Entf**, **Export**, **Import**, **PDF-Export**.

## Einen Charakter anlegen

Das Anlegen hat drei Schritte.

**Schritt 1: Name, Disziplin und Volk**

1. Klicke auf **Neu**. Der Dialog **Neuen Charakter erstellen** öffnet sich.
2. Gib im Feld **Name** einen Namen ein (mindestens 3 Zeichen). Im Namensfeld erscheint der Button **Weiter**. Klicke darauf.
3. Wähle unter **Disziplin auswählen** deine Disziplin. Darunter erscheint eine Beschreibung der Disziplin.
4. Wähle unter **Volk auswählen** dein Volk. Darunter erscheint eine Beschreibung des Volks.
5. Klicke auf **Nächster Schritt**.

!!! example "Screenshot: `player-create-step1.png`"
    Dialog **Neuen Charakter erstellen** mit Name, Disziplin und Volk.

**Schritt 2: Attribute**

Der Dialog **Verteilung der Attributwerte** zeigt die sechs Attribute mit **Basis**, **Kosten**, **Volk**, **Wert** und **Stufe**. Erhöhe und senke die Basiswerte. Die Summe der Kosten steht als *… von max. 72* darunter. **Nächster Schritt** ist erst verfügbar, wenn alle Punkte verteilt sind.

!!! example "Screenshot: `player-create-step2.png`"
    Dialog **Verteilung der Attributwerte** mit allen Punkten verteilt.

**Schritt 3: Talente, Zauber und Fertigkeiten**

Der Dialog *Erhöhe nun die Ränge deiner Talente, lerne Zauber und wähle deine Fertigkeiten* erklärt die nächsten Schritte. Klicke auf **Fertigstellen**. Talentränge, Zauber und Fertigkeiten legst du danach im Charakterbogen im Reiter **Talente / Zauber / Fertigkeiten** fest.

Klickst du in Schritt 2 oder 3 auf **Abbrechen**, wird der in Schritt 1 angelegte Charakter wieder gelöscht.

## Der Charakterbogen

Ist ein Charakter offen, zeigt der Hauptbereich **Charakteransichten** und eine Reihe von Reitern. Auf schmalen Bildschirmen lässt sich die Reihe seitlich scrollen.

| Reiter | Inhalt |
|---|---|
| **Basiswerte** | Disziplin, Volk und Kreis, Attribute, Abwehrwerte, Todes- und Bewusstlosigkeitswert, Karma, Beschreibung |
| **Talente / Zauber / Fertigkeiten** | Talente je Kreis, Kniffe, Zauber und Matrizen, Fertigkeiten, Vielseitigkeit |
| **Kampf** | Makros, Initiative und Karma, Angriffe, Zauberwirken, Schaden |
| **Ausrüstung** | Waffen, Rüstung, Beute und alle anderen Gegenstände, Charakterbild |
| **Legende** | Verdiente und ausgegebene Legendenpunkte |
| **Notizen** | Eigene Dokumente zu diesem Charakter |
| **Kampagne** | Nur sichtbar, wenn der Charakter zu einer Kampagne gehört |

!!! example "Screenshot: `player-sheet-tabs.png`"
    Charakterbogen mit **Charakteransichten** und der Reihe der Reiter.

### Basiswerte

Der Reiter zeigt diese Boxen:

- **1. Disziplin & Kreis:** Name, **Disziplin:**, **Volk:** und **Kreis:**. Mit **+** und **−** neben dem Kreis änderst du ihn. Bringt ein neuer Kreis einen Attributpunkt, öffnet sich der Dialog **Verteile 1 Attributpunkt**. Der Stift (Tooltip **Charakternamen bearbeiten**) ändert den Namen.
- **Attribute:** die sechs Attribute mit Volks-Modifikator und Stufe. Der Stift (Tooltip **Attribute bearbeiten**) öffnet die Attributwerte.
- **Charakterbeschreibung:** Geschlecht, Größe, Alter, Haare, Augen, Erscheinungsbild. Bearbeiten mit dem Stift (Tooltip **Charakterbeschreibung bearbeiten**).
- **2. Disziplin und Kreis:** eine zweite Disziplin beginnst du mit **2. Disziplin beginnen?**.
- **Basis-Abwehrwerte & Rüstung**, **Todes- & Bewusstlosigkeitswert**, **Wundschwelle & Erholung**, **Initiative**, **Bewegung & Trage-/Hebekraft**.
- **Dauerhafte Wunden & Belastung:** bearbeiten mit dem Stift (Tooltip **Dauerhafte Wunden und Belastung bearbeiten**).
- **Karmapunkte:** aktuelles und maximales Karma, **Karma-Ritual**.
- **Besondere Fähigkeiten:** **Volksfähigkeiten:** und **Disziplinfähigkeiten:**.
- **Beschreibung, persönliche Zitate oder sonstige Besonderheiten:** freier Text.

Unter **Weitere Einflüsse oder Verbesserungen auf deine Basiswerte?** trägst du Boni aus Zaubern, Gegenständen oder anderen Quellen ein, zum Beispiel einen Todeswert-Bonus von Holzhaut. **Tierbegleiter hinzufügen?** und **Tierbegleiter anzeigen** verwalten Tierbegleiter.

In **Wundschwelle & Erholung** nutzt du Erholungstests mit **Erh.test nutzen: Stufe … 🎲 …** und füllst sie mit **8h Schlaf** wieder auf.

!!! example "Screenshot: `player-base-values.png`"
    Reiter **Basiswerte** mit den Boxen **1. Disziplin & Kreis** und **Attribute**.

### Talente / Zauber / Fertigkeiten

- **Talente:** die Talente deiner Disziplin, nach Kreisen gruppiert. Den Rang erhöhst oder senkst du mit den Pfeil-Buttons (Tooltips **Rank erhöhen** und **Rank verringern**). Der Tooltip zeigt die Kosten in Legendenpunkten, zum Beispiel *Erhöhen kostet … LP*. Auf Touch-Geräten hältst du den Button gedrückt, um die Kosten zu sehen. **Nur verfügbare Kreise anzeigen** und **Alle Kreise anzeigen** wechseln die Ansicht.
- **Talent-Kniffe:** Kniffe fügst du mit **Kniffe hinzufügen** hinzu. Es gibt **Standard-Kniffe** und **Eigene Kniffe**.
- **Zauber:** Zauber fügst du mit **Zauber hinzufügen** hinzu, eigene legst du mit **Eigenen Zauber anlegen** an. Sortieren mit **A-Z sortieren** oder **Nach Kreis sortieren**.
- **Matrizen:** Zauber legst du mit **Matrix bearbeiten** in deine Zaubermatrizen.
- **Fertigkeiten:** Fertigkeiten fügst du mit **Fertigkeiten hinzufügen** hinzu. Es gibt **Standard-Fertigkeiten** und **Eigene Fertigkeiten**. Sortieren mit **A..Z sortieren** oder **Nach Kategorie sortieren**.
- **Vielseitigkeit:** nur für Menschen. Erhöhe den Rang von Vielseitigkeit, um mit **Vielseitigkeits-Talente hinzufügen** Talente anderer Disziplinen hinzuzufügen.

!!! example "Screenshot: `player-talents.png`"
    Reiter **Talente / Zauber / Fertigkeiten** mit den Talenten eines Kreises und dem Kosten-Tooltip.

### Würfeln und Info-Suche

Die Reiter **Basiswerte**, **Talente / Zauber / Fertigkeiten** und **Kampf** enthalten zwei Werkzeuge:

- **Würfeln:** wähle unter *Wähle die Stufe, für die du würfeln willst:* eine Stufe. Die App zeigt die passenden Würfel, zum Beispiel *Stufe 8 = 🎲: …*. Mit dem Würfel-Button würfelst du, das Ergebnis erscheint in einem Fenster.
- **Infos zu Disziplinen, Passionen, Talenten oder Zaubern suchen:** wähle unter *Wonach suchst du?* **Disziplin**, **Talent**, **Passion**, **Tal.-Beschr.**, **Zauber** oder **Zauberbeschr.** und gib einen Namen oder Suchbegriff ein.

Bei Würfen, für die Karma erlaubt ist, fragt die App *Möchtest du Karma für diesen Wurf verwenden?*. Bei zwei Disziplinen fragt sie zusätzlich *Karma aus welcher Disziplin?*.

!!! example "Screenshot: `player-dice.png`"
    Box **Würfeln** und ein Würfelergebnis.

### Kampf

- **Makros für Stufe-Würfel:** häufige Würfe speicherst du mit **Makro hinzufügen** als Makro (Name, Stufe, Karma verwenden, zusätzliche Info). Du kannst zwischen alphabetischer und manueller Reihenfolge wechseln und Makros mit **Nach vorne verschieben** und **Nach hinten verschieben** umsortieren.
- **Initiative & Karma-Nutzung:** **Ini würfeln** würfelt die Initiative, **Ini setzen** setzt sie von Hand. Karma setzt du mit **Karma … verw.** ein.
- **Wähle deinen Angriff und füge Schaden zu!:** wähle ein Angriffstalent mit **Wähle dein Angriffstalent!** oder greife mit **Nur Geschicklichkeit!** an. Trage einen situativen **Bonus/Malus** ein, würfle den **Angriffswurf**, markiere **Treffer** oder **Verfehlt** und würfle dann mit deiner Waffe den **Schadenswurf**.
- **Zauber wirken:** wähle einen Zauber aus deinen Matrizen oder aus dem **Zauberspeicher**, webe die Fäden (*Wie viele Fäden auf einmal weben?*) und würfle den Zauberwirken-Test.
- **Schaden erleiden, Wunden & Heilung:** trage unter **Erlittener Schaden** den Schaden ein, wähle den Schutz (**Phys. Rüstung** oder **Myst. Rüstung**) und klicke auf **Schaden anwenden**. **Heilung anwenden**, **Erholungstest** und **Wunden heilen** verringern Schaden und Wunden.
- **Kampf-Abwehrwerte, Rüstung & Wundschwelle** und **Todes-/Bewusstlosigkeitswert & Schaden** zeigen die aktuellen Werte.
- **Verwendete Ausrüstung:** wähle die Waffe (**Wähle deine Waffe:**) und die Rüstung (**Wähle deine Rüstung:**), die du im Kampf benutzt.

!!! example "Screenshot: `player-combat.png`"
    Reiter **Kampf** mit einem Angriffswurf.

### Ausrüstung

Der Reiter hat eine Box je Kategorie: **Deine Waffen**, **Deine Rüstung**, **Deine Beute**, **Deine Blutamulette**, **Deine magischen Gegenstände**, **Deine Thread-Objekte**, **Deine sonstigen Gegenstände**, **Deine Heilmittel**, **Deine Vorräte**, **Deine Abenteuerausrüstung**, **Deine Kleidung** und **Dein Bild**.

- Gegenstände fügst du mit dem Plus-Button der Box hinzu, zum Beispiel **Waffen hinzufügen**, und wählst sie aus der Liste. *Kannst du den gesuchten Gegenstand nicht finden? Füge einen beliebigen Gegenstand aus der Liste hinzu und bearbeite ihn danach passend.*
- Ein Klick auf einen Gegenstand zeigt seine Details, dort kannst du ihn bearbeiten. Gelöscht wird er mit dem Mülleimer-Symbol.
- **Deine Beute:** Geld fügst du mit **+ Beute** hinzu und gibst es mit **- Beute** aus.
- **Dein Bild:** ein Charakterbild hochladen. Es erscheint auch auf dem PDF-Charakterbogen.

!!! example "Screenshot: `player-equipment.png`"
    Reiter **Ausrüstung** mit Waffen und Rüstung.

### Legende

Der Reiter **Deine Legende** führt deine Legendenpunkte.

- **Legende hinzufügen** öffnet **Legendeneintrag hinzufügen**: wähle mit **Datum auswählen** ein Datum, gib die **Punkte** und den Anlass ein, wähle **Verdiente Punkte** oder **Ausgegebene Punkte** und klicke auf **Eintrag speichern**.
- Oben stehen **Verdiente Legendenpunkte** und **Ausgegebene Legendenpunkte** sowie *Du hast … LP zum Ausgeben.*
- **Ausgeg. LP berechnen** berechnet die Legendenpunkte, die für Attributerhöhungen, Talentränge, Fertigkeitsränge und den Beginn einer 2. Disziplin ausgegeben wurden. Legendenpunkte für Karma oder Fäden sind nicht enthalten.
- Ein Klick auf einen Eintrag zeigt ihn an, dort kannst du ihn bearbeiten.

Legendenpunkte, die deine Spielleitung vergibt, übernimmst du im Reiter **Kampagne**, siehe unten.

!!! example "Screenshot: `player-legend.png`"
    Reiter **Legende** mit verdienten und ausgegebenen Einträgen.

### Notizen

Im Reiter **Notizen** legst du beliebig viele Dokumente zu diesem Charakter an, zum Beispiel eine Hintergrundgeschichte oder Notizen zu Sitzungen.

- **Neu** legt ein Dokument an. Der **Dokumentname** darf Buchstaben, Ziffern, Leerzeichen und `. _ - ( ) , ! & ' +` enthalten.
- Umbenennen und Löschen geht über die Symbole daneben (Tooltips **Umbenennen** und **Löschen**).
- Der Editor speichert automatisch und zeigt **Gespeichert …**.
- Die Werkzeugleiste formatiert Text: Überschriften, **Fett**, **Kursiv**, **Aufzählung**, **Nummerierte Liste**. **Bild einfügen** fügt ein Bild an der Cursorposition ein. **Sprungmarke einfügen** fügt einen Link auf eine Überschrift im selben Dokument ein.
- Zwischen **Bearbeiten** und **Vorschau** wechselst du oben. In der Vorschau öffnen Links einen neuen Browser-Tab, Sprungmarken scrollen zur Überschrift.

!!! example "Screenshot: `player-notes.png`"
    Reiter **Notizen** mit einem Dokument im Editor und der Werkzeugleiste.

## Einer Kampagne beitreten

Deine Spielleitung lädt dich per E-Mail ein.

1. Öffne den Link in der Einladungs-E-Mail. Melde dich bei Bedarf an.
2. Die Seite **Kampagnen-Einladung** zeigt *Du wurdest eingeladen*, die **Kampagne** und **Gültig bis**.
3. Wähle unter **Charakter auswählen** den Charakter, der der Kampagne beitritt. Hast du noch keinen Charakter, lege zuerst einen an.
4. Klicke auf **Annehmen**. Die App bestätigt *Einladung angenommen – willkommen in der Kampagne!*. Mit **Ablehnen** lehnst du die Einladung ab.

!!! example "Screenshot: `player-invitation.png`"
    Seite **Kampagnen-Einladung** mit Charakterauswahl.

## Der Reiter Kampagne

Sobald dein Charakter zu einer Kampagne gehört, erscheint der Reiter **Kampagne**. Eine Zahl am Reiter zeigt neue Nachrichten und Dokumente, und die App spielt einen Ton, wenn etwas Neues ankommt.

- **Kampagne:** Name, **Reales Startdatum**, **Mein Status** (**Aktiv** oder **Inaktiv**) und unter **Mitreisende:** die anderen Charaktere.
- **Legendenpunkte:** von der Spielleitung vergebene Legendenpunkte. Mit **Übernehmen** übernimmst du sie. Übernommene Vergaben zeigen **Bereits übernommen**.
- **Ankündigungen:** Nachrichten der Spielleitung an alle Spieler.
- **Chat mit Spielleitung:** dein privater Chat mit der Spielleitung. Schreibe unter *Nachricht schreiben...* und klicke auf **Senden**.
- **Dokumente vom GM:** Handouts und Dokumente, die die Spielleitung mit dir teilt.
- **Kampagne verlassen:** nach der Bestätigung wirst du in der Kampagne als inaktiv markiert.

!!! example "Screenshot: `player-campaign.png`"
    Reiter **Kampagne** mit Legendenpunkten, Ankündigungen und Chat.
