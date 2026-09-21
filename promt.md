# MASTER-PROMPT: GODOT 4 – MASSIVE PHYSICS-BASED MOVING & INTERIOR DESIGN SIMULATION

## ROLLE DER KI

Du bist ab jetzt mein **Lead Game Developer, Principal Software Architect, Technical Director und Senior Gameplay Engineer** mit tiefgehender Expertise in:

* Godot 4.x
* GDScript
* Godot Physics / alternativ Godot Jolt
* CharacterBody3D und RigidBody3D
* PhysicalBone3D / Skeleton3D / prozeduralen Ragdolls
* Godot High-Level Multiplayer API
* MultiplayerSpawner
* MultiplayerSynchronizer
* Rendering und Shadern
* SubViewport / Render Targets
* Decals
* AnimationTree
* Blend Shapes / Morph Targets
* UI/UX-Architektur
* Savegames und persistenter Progression
* Data-driven Game Architecture
* Object Pooling
* Streaming großer Open-World-Bereiche
* Performance-Optimierung
* Third-Person-Kamerasystemen
* physikbasierten Interaktionen
* modularen Systemarchitekturen
* AAA-ähnlichen Grafik- und Optionssystemen
* Debugging und automatisierten Tests.

Du sollst das Projekt nicht wie ein kleines Demo-Projekt behandeln, sondern wie die technische Basis eines **vollwertigen kommerziellen PC-Spiels**, das später sehr stark erweitert werden kann.

Das Projekt soll primär für **Singleplayer und Co-op-Multiplayer** ausgelegt werden.

Das Spiel soll eine Mischung aus:

* wackeliger, humorvoller Physik,
* physikbasiertem Chaos,
* einer lebendigen Open-World-Stadt,
* Unternehmensmanagement,
* Fahrzeugen,
* Möbeltransport,
* Innenraumgestaltung,
* Character-Customization,
* Zerstörung,
* Fortschritt,
* Aufträgen,
* Sandbox-Elementen
* und überraschenden Spezialmissionen

sein.

Die Welt soll sich **lustig und chaotisch anfühlen**, aber technisch sauber aufgebaut sein.

---

# WICHTIG: DIE VORHANDENE REPOSITORY

In der dir gegebenen Repository befinden sich die Dateien des vorhandenen Godot-Projekts bzw. des Godot-Game-Folders.

### KRITISCHE REGEL

Bevor du neue Architektur oder Code erzeugst:

1. Untersuche zuerst die vorhandene Repository.
2. Analysiere bestehende Ordner.
3. Analysiere bestehende `.gd`-Dateien.
4. Analysiere vorhandene `.tscn`-Dateien.
5. Analysiere vorhandene `.godot`-Strukturen, sofern relevant.
6. Analysiere vorhandene Assets.
7. Analysiere bestehende Autoloads.
8. Analysiere Project Settings.
9. Analysiere bestehende Szenen und Node-Strukturen.
10. Prüfe, welche Systeme bereits existieren.
11. Vermeide unnötige Doppelimplementierungen.
12. Wenn bestehender Code weiterverwendbar ist, erweitere ihn statt ihn ohne Grund zu ersetzen.
13. Wenn bestehende Architektur schlecht oder instabil ist, begründe die notwendige Änderung.
14. Halte die neue Architektur möglichst kompatibel mit bereits vorhandenen Assets.
15. Erzeuge keine Platzhalter-Systeme, die nur so aussehen, als würden sie funktionieren.

### ZIEL

Alle von dir vorgeschlagenen Dateien, Skripte, Szenen und Systeme sollen später wieder in das vorhandene Projekt eingefügt werden können.

Die Antworten müssen deshalb so geschrieben sein, dass ein Entwickler bzw. eine andere KI die Ergebnisse direkt in eine Godot-4-Repository übernehmen kann.

Verwende keine Fantasie-APIs.

Verwende keine Godot-3-Syntax.

Verwende ausschließlich Godot-4-kompatible Architektur und GDScript-Syntax.

---

# 1. VISION DES SPIELS

Der Spieler besitzt ein kleines, zunächst heruntergekommenes Umzugsunternehmen.

Das Unternehmen übernimmt Aufträge in einer großen, dauerhaft existierenden Stadt.

Der Kern-Gameplay-Loop besteht aus:

**Zentrale → Auftrag erhalten → zum Einsatzort fahren → Gebäude betreten → Möbel physikalisch bewegen → Möbel beschädigen oder unbeschädigt transportieren → Truck beladen → zum Ziel fahren → Truck entladen → Möbel platzieren → Auftrag abschließen → Geld und Reputation erhalten → Unternehmen verbessern → Zentrale ausbauen → bessere Fahrzeuge/Werkzeuge kaufen → schwierigere Aufträge annehmen.**

Dabei soll das Spiel niemals zu einem simplen „Klicke Objekt an und es verschwindet im Inventar“-System werden.

Die Möbel sind **physische Objekte in der Welt**.

Der Spieler muss sie tatsächlich:

* greifen,
* drehen,
* ziehen,
* schieben,
* tragen,
* fallen lassen,
* aufladen,
* sichern,
* transportieren,
* herunterlassen,
* durch Türen bewegen,
* um Ecken manövrieren,
* Treppen hinunterbringen,
* aus Fenstern bewegen,
* mit Werkzeugen transportieren
* und am Ziel wieder abstellen.

Das bedeutet:

## KEIN traditionelles Inventar für große Möbel.

Ein Sofa wird nicht in einem UI-Slot gespeichert.

Ein Klavier verschwindet nicht einfach.

Ein Schrank bleibt ein physikalisches Objekt.

---

# 2. SPIELGEFÜHL

Das Spiel soll einen starken Fokus auf:

### Chaos

Physik kann unerwartete Situationen erzeugen.

### Humor

Animationen, NPCs, Kleidung, Objekte und Fahrzeuge dürfen absichtlich absurd sein.

### Immersion

Der Spieler soll das Gefühl haben, wirklich in einer kleinen Umzugsfirma zu arbeiten.

### Progression

Am Anfang ist fast alles improvisiert.

Später besitzt das Unternehmen:

* bessere Trucks,
* besseres Werkzeug,
* bessere Mitarbeiter,
* ein größeres HQ,
* bessere Werbung,
* bessere Reputation,
* bessere Kunden,
* bessere Aufträge,
* luxuriöse Möbel,
* Spezialfahrzeuge,
* zusätzliche Gebäude,
* besondere Ausrüstung
* und komplexere Missionen.

---

# 3. SINGLEPLAYER UND CO-OP

Das komplette Gameplay soll von Beginn an so aufgebaut werden, dass es sowohl:

## Singleplayer

als auch

## Co-op

unterstützt.

Der Singleplayer darf nicht einfach ein nachträglich hinzugefügter Modus sein.

Gameplay-Systeme sollen grundsätzlich netzwerkfähig gedacht werden.

---

# 4. MULTIPLAYER-ARCHITEKTUR

Verwende die Godot-4-High-Level-Multiplayer-Architektur.

Wichtige Systeme:

* MultiplayerSpawner
* MultiplayerSynchronizer
* Authority-basierte Logik
* RPCs
* Synchronisation wichtiger Gameplay-Zustände
* server-authoritative Architektur, sofern passend
* clientseitige Interpolation
* Ownership/Authority-Management.

### Wichtig

Das Projekt benötigt zunächst möglicherweise **keinen echten dedizierten Online-Service**.

Online-Multiplayer darf zunächst simuliert bzw. architektonisch vorbereitet werden.

Die Architektur soll aber später problemlos auf echtes Online-Multiplayer erweitert werden können.

### Lokal

Lokales Co-op soll möglich sein, beispielsweise über:

* Split-Screen oder
* lokale Controller-Unterstützung.

Die Architektur soll mehrere Player gleichzeitig in derselben Szene unterstützen.

### Online

Plane die Architektur so, dass später:

* Lobby-System
* Host
* Join
* Player Synchronisation
* Objekt-Synchronisation
* Fahrzeug-Synchronisation
* Physik-Synchronisation

hinzugefügt werden können.

---

# 5. HAUPTMENÜ

Beim Start erscheint ein hochwertiges Hauptmenü.

Das Menü soll nicht nach einem kleinen Hobbyprojekt aussehen.

Es soll wie ein kommerzielles Spiel strukturiert sein.

Menüpunkte:

* Spielen
* Charakter
* Unternehmen
* Einstellungen
* Extras
* Credits
* Spiel beenden.

---

# 6. CHARAKTERERSTELLUNG

Der Spieler besitzt einen vollständig anpassbaren, humorvollen, wackeligen Charakter.

Der Stil soll cartoonartig sein.

Die Charaktere sollen ähnliche Eigenschaften besitzen wie lustige, wackelige Figuren:

* große Bewegungen
* physikalisches Schwanken
* übertriebene Animationen
* weiche Reaktionen
* ragdollartige Momente
* komische Stürze
* physische Kleidung
* physische Accessoires.

Aber:

Die Architektur muss technisch sauber sein und darf nicht einfach nur aus einem einzigen RigidBody bestehen.

---

# 7. CHARAKTER-KUSTOMISIERUNG

Die Charakteranpassung soll sehr umfangreich sein.

Der Spieler soll unter anderem einstellen können:

## Körper

* Körpergröße
* Körperbreite
* Gewichtsklasse
* Bauchumfang
* Schulterbreite
* Kopfgröße
* Armgröße
* Beinlänge
* Handgröße
* Fußgröße
* Kopfbreite
* Halslänge.

Die Werte sollen möglichst stufenlos bzw. mit einem ausreichend feinen Slider verändert werden.

Nutze hierfür geeignete Morph-/Blend-Shape-/Shape-Key-Systeme.

---

# 8. MAL- UND PAINT-SYSTEM

Dies ist eines der wichtigsten Systeme des Spiels.

Der Spieler soll seinen Charakter **wirklich selbst bemalen können**.

Nicht:

„Klicke auf Arm → wähle Farbe.“

Sondern:

Der Spieler soll mit einem virtuellen Pinsel tatsächlich auf das Charaktermodell malen.

Beispielsweise:

* Pinsel
* Spray
* Airbrush
* Radierer
* verschiedene Pinselgrößen
* verschiedene Härten
* verschiedene Farben
* Transparenz
* Muster
* Streifen
* Punkte
* Graffiti
* Schablonen
* Farbverläufe
* Decals.

Der Spieler kann beispielsweise:

* eine Seite des Kopfes rot malen,
* eine Linie über den Arm zeichnen,
* einen Farbverlauf auf den Rücken malen,
* Muster auf den Bauch zeichnen,
* Graffiti auf Kleidung malen.

---

# 9. TECHNISCHE UMSETZUNG DES PAINT SYSTEMS

Untersuche und verwende geeignete Godot-Techniken wie:

* SubViewport
* Render-to-Texture
* ViewportTexture
* Texture Painting
* UV-Mapping
* Decals
* Shader-basierte Masken.

Die Architektur soll erlauben, dass die gemalten Daten:

* gespeichert,
* geladen,
* synchronisiert,
* auf Charaktere angewendet
* und später wieder verändert werden können.

Die Paint-Daten sollen möglichst kompakt speicherbar sein.

Baue das System modular.

---

# 10. SPRAYDOSEN UND GRAFFITI

Zusätzlich zum Charakter-Paint-System existieren Spraydosen.

Spraydosen können auf unterschiedliche Oberflächen angewendet werden:

* Charaktere
* Fahrzeuge
* Möbel
* Wände
* Türen
* Garagen
* HQ
* Schilder
* Container
* andere geeignete Oberflächen.

Das Spray-System muss erkennen können:

* Trefferpunkt
* Oberflächennormal
* Texturkoordinaten
* Sprayradius
* Farbe
* Opazität
* Rotation
* Decal-Größe.

Spraydosen sollen später unterschiedliche Eigenschaften besitzen:

* normale Spraydose
* große Spraydose
* feine Spraydose
* Neon
* Metallic
* Glow
* Glitzer
* Spezialfarben.

---

# 11. ACCESSOIRES

Charaktere können Accessoires tragen.

Beispiele:

* Helme
* Hüte
* Sombreros
* Sonnenbrillen
* riesige Kopfhörer
* Cowboyhüte
* Rucksäcke
* Schals
* Taschen
* Werkzeuggürtel
* Warnwesten
* Overalls
* lustige Schuhe
* riesige Stiefel
* Masken
* Weihnachtszubehör
* saisonale Items.

Accessoires sollen:

* freigeschaltet,
* gekauft,
* gespeichert,
* ausgerüstet
* und im Multiplayer synchronisiert werden können.

Einige Kleidungsstücke sollen bewusst physikalisch reagieren.

Beispiel:

Ein langer Schal kann sich:

* in Türen verfangen,
* an Möbeln hängen bleiben,
* im Wind flattern,
* an Fahrzeugen hängen.

---

# 12. FREISCHALTSYSTEM

Nicht alles darf direkt verfügbar sein.

Es soll ein langfristiges Freischaltsystem geben.

Freischaltungen können abhängig sein von:

* Geld
* Firmenlevel
* Reputation
* erfolgreichen Aufträgen
* Spezialaufträgen
* erreichten Meilensteinen
* geheimen Fundstücken
* besonderen Herausforderungen.

---

# 13. UNTERNEHMENSMANAGEMENT

Der Spieler besitzt kein normales Haus, sondern ein wachsendes Unternehmen.

Die Zentrale startet als:

* klein
* alt
* schmutzig
* heruntergekommen
* schlecht eingerichtet
* mit schlechtem Ruf.

In der Zentrale befinden sich beispielsweise:

* Rezeption
* kleines Büro
* Computer
* Lager
* Garage
* Mitarbeiterbereich.

---

# 14. HQ BUILD MODE

Das HQ besitzt einen eigenen Baumodus.

Der Spieler kann:

* Wände bauen
* Wände entfernen
* Türen setzen
* Fenster setzen
* Böden verlegen
* Decken bauen
* Räume erstellen
* Stockwerke hinzufügen
* Möbel platzieren
* Beleuchtung platzieren
* Dekoration anbringen
* Arbeitsplätze bauen
* Pausenräume bauen
* Lagerräume bauen
* Werkstätten bauen
* Empfangsbereiche bauen.

Das System soll grid-basiert arbeiten.

Aber einzelne Objekte sollen trotzdem fein verschoben werden können.

---

# 15. BAUSYSTEM

Entwickle ein modulares Building-System.

Baue Datenstrukturen für:

* WallPiece
* FloorPiece
* CeilingPiece
* DoorPiece
* WindowPiece
* StairPiece
* DecorationPiece.

Ein Bauobjekt soll Informationen besitzen wie:

* Kosten
* Kategorie
* Größe
* Material
* erforderliches Firmenlevel
* Stabilität
* visuelle Variante
* Rotationsoptionen.

---

# 16. HQ-REPUTATION

Das HQ soll nicht nur dekorativ sein.

Seine Qualität beeinflusst:

* Kunden
* Reputation
* Firmenwert
* Mitarbeiterzufriedenheit
* mögliche Aufträge.

Ein schäbiges HQ kann neue Kunden abschrecken.

Ein luxuriöses HQ kann höherwertige Kunden anziehen.

---

# 17. COMPUTER-SYSTEM

Im HQ befindet sich ein Computer.

Der Computer ist eine zentrale Management-Oberfläche.

Am Computer kann der Spieler:

* Aufträge ansehen
* Aufträge auswählen
* Firma verwalten
* Mitarbeiter verwalten
* Finanzen ansehen
* Fahrzeuge verwalten
* Marketing einstellen
* Statistiken ansehen
* Firmenwebsite verwalten
* Logo bearbeiten
* Slogan ändern
* Fortschritt ansehen.

---

# 18. UNTERNEHMENSWEBSITE

Beim Start des Spiels muss die Firma eine einfache Website erstellen.

Der Spieler entscheidet:

* Unternehmensname
* Logo
* Theme
* Website-Stil
* Hauptfarbe
* kurzen Text
* eventuell Slogan.

Die Website soll Auswirkungen auf:

* Kundenqualität
* Reputation
* Marketing
* Auftragsarten

haben.

---

# 19. MARKETING

Das Unternehmen besitzt ein Marketingbudget.

Der Spieler kann beispielsweise investieren in:

* lokale Werbung
* Social Media
* Plakate
* Radio
* Premium-Werbung
* aggressive Werbung
* günstige Werbung
* Luxussegment-Werbung.

Mehr Marketing bedeutet nicht automatisch nur Vorteile.

Hohe Nachfrage kann dazu führen, dass:

* mehrere Aufträge gleichzeitig verfügbar sind,
* mehr Mitarbeiter benötigt werden,
* mehr Fahrzeuge benötigt werden,
* mehr Stress entsteht.

---

# 20. NPC-MITARBEITER

Später können Mitarbeiter eingestellt werden.

Mitarbeiter sind ebenfalls wackelige Charaktere.

Sie besitzen Eigenschaften wie:

* Geschwindigkeit
* Kraft
* Genauigkeit
* Intelligenz
* Zuverlässigkeit
* Stressresistenz
* Fahrfähigkeit
* Möbelkenntnis
* Motivation.

Mitarbeiter können:

* fegen
* Möbel tragen
* sortieren
* Fahrzeuge beladen
* Fahrzeuge fahren
* Werkzeuge benutzen.

Aber:

Mitarbeiter sollen absichtlich nicht perfekt sein.

Ein NPC kann beispielsweise:

* Möbel fallen lassen
* gegen Türen laufen
* im falschen Raum stehen
* einen Schrank schief tragen
* mit einem Staubsauger über ein Kabel stolpern.

Das soll Teil des Humors sein.

---

# 21. MITARBEITER-MANAGEMENT

Mitarbeiter besitzen:

* Gehalt
* Arbeitszeit
* Energie
* Zufriedenheit
* Erfahrung
* Spezialisierung.

Der Spieler muss eventuell:

* Pausenräume bauen
* bessere Ausstattung kaufen
* Mitarbeiter bezahlen
* neue Fahrzeuge bereitstellen.

---

# 22. DIE STADT

Das Spiel besitzt eine große, dauerhaft existierende Stadt.

Die gesamte Stadt soll nicht wie einzelne kleine Level wirken.

Sie ist eine zusammenhängende Welt.

Beispielsweise mit:

* Wohngebieten
* Innenstadt
* Industriegebiet
* Vororten
* Villenviertel
* Hafengebiet
* Baustellen
* Einkaufsstraßen
* Tankstellen
* Werkstätten
* Lagerhäusern
* Wolkenkratzern
* Parks
* Friedhöfen
* versteckten Orten
* Hinterhöfen.

---

# 23. LEBENDIGE WELT

Die Stadt soll belebt sein.

Es gibt:

* Fußgänger
* Autos
* Busse
* Lieferwagen
* Baustellenfahrzeuge
* Fahrradfahrer
* Tiere
* Händler
* Kunden
* Stadtarbeiter.

NPCs besitzen einfache Tagesroutinen.

Autos fahren Routen.

Menschen bewegen sich zwischen interessanten Punkten.

---

# 24. PERFORMANZ

Die Stadt muss sehr groß sein und trotzdem performant laufen.

Nutze je nach Bedarf:

* MultiMeshInstance3D
* GridMap
* Occlusion Culling
* LOD
* Visibility Ranges
* Chunk Streaming
* Objekt-Pooling
* instanzierte Szenen
* vereinfachte Collision Meshes
* Distance Culling.

Architektur soll bereits auf große Mengen von Objekten ausgelegt werden.

---

# 25. TAG-/NACHT-ZYKLUS

Die Stadt besitzt einen dynamischen Tagesablauf.

Beispielsweise:

Morgen → Tag → Abend → Nacht.

Dies beeinflusst:

* Licht
* Schatten
* NPC-Verhalten
* Verkehr
* Geschäfte
* Aufträge
* Wetter
* Atmosphäre.

---

# 26. WETTER

Dynamisches Wetter:

* Sonne
* bewölkt
* Regen
* starker Regen
* Sturm
* Nebel
* Gewitter.

Wetter soll Gameplay beeinflussen.

Beispielsweise:

Regen:

* Straßen werden rutschiger
* Möbeloberflächen können rutschiger werden
* Fahrzeuge haben weniger Grip
* Gegenstände können beim Transport leichter abrutschen.

Starker Wind:

* leichte Objekte können bewegt werden
* Planen flattern
* Kartons können wegfliegen
* Möbel auf Kränen werden schwerer kontrollierbar.

---

# 27. FAHRZEUGE

Der Spieler besitzt initial einen alten kleinen Umzugstruck.

Das Fahrzeug besitzt:

* 2 Sitze
* Ladefläche
* Türen
* Reifen
* Motor
* Fahrwerk
* Hupen-System
* Licht
* Ladegewicht.

Das Fahrzeug soll physikalisch funktionieren.

---

# 28. TRUCK-UPGRADES

Der Start-Truck kann in der Garage erweitert werden.

Beispiele:

### Motor

* stärkerer Motor
* bessere Beschleunigung
* höhere Nutzlastfähigkeit.

### Federung

* Standard
* verstärkt
* Heavy Duty
* Offroad.

### Reifen

* Standard
* Grip
* Regen
* Heavy Load.

### Ladefläche

* größer
* höher
* breiter.

### Sonstiges

* neue Hupe
* Sirene
* Lackierung
* Vinyls
* Decals
* Graffiti
* LED-Beleuchtung
* Seitenspiegel
* Dachaufbauten.

---

# 29. VERSCHIEDENE FAHRZEUGE

Später sollen neue Fahrzeuge gekauft werden können.

Beispiele:

* Gabelstapler
* großer Möbelwagen
* kleiner Van
* Heavy-Duty-Truck
* Hover-Truck
* Transportanhänger
* Kranfahrzeug
* Spezialfahrzeug.

Jedes Fahrzeug soll einen eigenen Gameplay-Vorteil besitzen.

---

# 30. SHOP-SYSTEM

In der Stadt existieren Shops.

Beispielsweise:

## Fahrzeughändler

Hier kauft man:

* Trucks
* Vans
* Gabelstapler
* Spezialfahrzeuge
* Hover-Fahrzeuge.

## Baumarkt

Hier kauft man:

* Werkzeuge
* Farben
* Pinsel
* Spraydosen
* Seile
* Sackkarren
* Werkzeugkisten
* Baumaterial
* Ersatzteile.

## Kleidungsgeschäft

Hier kauft man:

* Kleidung
* Hüte
* Accessoires
* Spezial-Outfits.

## Möbelhaus

Hier kauft man:

* Sofas
* Tische
* Schränke
* Betten
* Fernseher
* Luxusmöbel
* Pflanzen
* Lampen
* Dekoration.

---

# 31. PHYSIKALISCHE GREIF-MECHANIK

Das Greifen ist ein absoluter Kernmechanismus.

Der Spieler kann ein Objekt physisch greifen.

Steuerung soll sowohl:

* Maus/Tastatur
* Controller

unterstützen.

Der Spieler kann:

* Objekt anheben
* nach links ziehen
* nach rechts ziehen
* nach vorne ziehen
* nach hinten ziehen
* hochziehen
* herunterziehen
* drehen
* loslassen.

Das System soll sich wie eine vereinfachte 6DOF-Physikinteraktion anfühlen.

Mögliche technische Ansätze:

* Generic6DOFJoint3D
* PinJoint3D
* physikalische Impulse
* Spring Forces
* Target Position
* Damped Movement.

Teste, welche Variante für Godot 4 am stabilsten ist.

---

# 32. GRAB SYSTEM DESIGN

Ein Greif-System soll mindestens folgende Zustände besitzen:

* Idle
* Detecting
* CandidateFound
* Grabbing
* Holding
* Rotating
* Throwing
* Releasing.

Das System muss wissen:

* welches Objekt gegriffen wird,
* welcher Spieler es hält,
* wo es gehalten wird,
* wie schwer es ist,
* ob es gleichzeitig von mehreren Spielern gehalten werden darf.

---

# 33. CO-OP LIFTING

Große Objekte können einen bestimmten Kraftbedarf besitzen.

Beispiele:

### Karton

1 Spieler

### Sofa

1–2 Spieler

### Klavier

2 Spieler

### Tresor

2–4 Spieler

### Industriemaschine

mehrere Spieler / Spezialwerkzeug.

Wird ein schweres Objekt von zu wenigen Spielern angehoben, kann es:

* kaum bewegt werden
* kippen
* rutschen
* herunterfallen.

Der Schwerpunkt soll physikalisch berücksichtigt werden.

---

# 34. MULTI-GRAB SYSTEM

Mehrere Spieler können gleichzeitig dasselbe Objekt greifen.

Das Objekt besitzt dann mehrere Grab-Constraints.

Beispielsweise:

Player A links.

Player B rechts.

Das System errechnet daraus eine gemeinsame physikalische Bewegung.

Achte besonders auf:

* Stabilität
* Netzwerk-Synchronisation
* Ownership
* Jitter
* Explosions-/Velocity-Fehler
* Snap-Probleme.

---

# 35. WERKZEUGE

Werkzeuge erweitern die Physik.

Beispiele:

### Sackkarre

Möbel können:

* darauf gelegt
* gekippt
* geschoben
* gezogen

werden.

### Seil

Möbel können:

* befestigt
* gezogen
* herabgelassen
* hochgezogen

werden.

### Seilwinde

Kann mit:

* Truck
* Kran
* Bodenanker

verbunden werden.

### Besen

Kann kleine Objekte bewegen.

### Laubbläser

Kann leichte Objekte physikalisch wegblasen.

### Hammer

Kann bestimmte Gegenstände beschädigen.

---

# 36. MÖBEL-SYSTEM

Möbel sollen modular aufgebaut sein.

Ein Möbelobjekt kann Komponenten besitzen wie:

* PhysicsBody
* Collision
* Visual
* Interaction
* Damage
* Material
* Audio
* GrabPoints
* BreakableParts.

---

# 37. MÖBEL-DATEN

Jedes Möbelstück soll datengetrieben sein.

Beispielsweise:

* ID
* Name
* Kategorie
* Kaufpreis
* Gewicht
* Wert
* Stabilität
* Zerbrechlichkeit
* Schwerpunkt
* Material
* Größe
* benötigte Spieleranzahl
* Schadensgrenze
* Reparaturkosten
* Seltenheit.

Verwende möglichst Resources für statische Daten.

Beispielsweise:

`FurnitureData.tres`

---

# 38. DAMAGE-SYSTEM

Jedes empfindliche Möbelstück besitzt einen Schadenstatus.

Beispielsweise:

0 % – Neu

1–20 % – leichte Kratzer

20–40 % – sichtbar beschädigt

40–70 % – stark beschädigt

70–99 % – kritisch

100 % – zerstört.

Der Schaden kann durch verschiedene Ereignisse entstehen:

* hohe Aufprallgeschwindigkeit
* Fallenlassen
* Quetschen
* Kippen
* gegen Wand schlagen
* gegen Türrahmen schlagen
* von anderen Möbeln getroffen werden
* Explosionen bzw. Spezialeffekte.

---

# 39. MATERIAL-SPEZIFISCHE SCHÄDEN

Schaden soll materialabhängig sein.

### Glas

Kann:

* Risse bekommen
* splittern
* vollständig zerbrechen.

### Holz

Kann:

* Kratzer bekommen
* brechen
* Teile verlieren.

### Metall

Kann:

* Dellen bekommen
* verbiegen.

### Elektronik

Kann:

* Gehäuse beschädigt bekommen
* Display beschädigt bekommen
* ausfallen.

### Keramik

Kann:

* Risse bekommen
* zerbrechen.

---

# 40. BEISPIEL FERNSEHER

Ein Fernseher könnte beispielsweise:

0–30 Schaden = optisch intakt

30–60 = sichtbare Displayrisse

60–90 = stark beschädigt

90–100 = Display komplett defekt.

Das beeinflusst am Ende die Bezahlung.

---

# 41. BEZAHLUNG

Jeder Auftrag besitzt eine Grundzahlung.

Die endgültige Zahlung hängt ab von:

* Zeit
* Möbelzustand
* Vollständigkeit
* Beschädigungen
* Sonderzielen
* Kundenzufriedenheit
* Reputation.

Beispielsweise:

Grundlohn: 5.000 €

Schäden: -650 €

Zeitbonus: +300 €

Sonderziel: +500 €

Endzahlung: 5.150 €

Die Formel soll zentral konfigurierbar sein.

---

# 42. AUFTRAGSSYSTEM

Baue ein datengetriebenes Mission-System.

Ein Auftrag besitzt beispielsweise:

* Mission ID
* Auftraggeber
* Startpunkt
* Zielpunkt
* Möbel-Liste
* Zeitlimit
* Basiszahlung
* Bonus
* Strafzahlungen
* Spezialregeln
* Wetter
* Tageszeit
* Schwierigkeitsgrad.

Missionen sollen prozedural bzw. parametrisch erstellt werden können.

---

# 43. NORMALE AUFTRÄGE

Beispiele:

* kleine Wohnung
* normales Einfamilienhaus
* großes Familienhaus
* Büro
* Restaurant
* Laden
* Arztpraxis
* Lager
* Werkstatt.

Jeder Auftrag besitzt andere Herausforderungen.

---

# 44. SPEZIALAUFTRÄGE / BOSS-MISSIONEN

Das Spiel soll besondere Aufträge besitzen.

Diese Missionen sollen deutlich anders funktionieren als normale Umzüge.

## MISSION 1: DAS SPUKHAUS

Ort:

Altes Haus nahe Friedhof.

Besonderheiten:

* Nacht
* Nebel
* Gewitter
* Möbel bewegen sich teilweise selbst
* Türen schlagen zu
* Gegenstände schweben
* Möbel können den Spieler verfolgen
* einige Objekte reagieren auf Licht
* versteckte Räume
* paranormale Ereignisse.

Es soll trotzdem primär ein humorvolles Chaos-Spiel bleiben und kein reines Horror-Spiel werden.

---

# 45. MISSION 2: BANK-RÄUMUNG

Auftrag:

Eine Bank muss geräumt werden.

Problem:

Goldtresore sind extrem schwer.

Das Fahrzeug reagiert auf das Gewicht.

Wird ein Tresor falsch positioniert, kann:

* das Heck absinken,
* der Truck schlecht lenken,
* das Fahrzeug kippen,
* die Traktion sinken.

Der Spieler muss die Ladung physikalisch sinnvoll verteilen.

---

# 46. MISSION 3: WOLKENKRATZER

Ein Auftrag im 30. Stock eines Hochhauses.

Problem:

* kein nutzbarer Aufzug
* großer Möbeltransport
* Wind
* Baukran
* offene Fenster
* sehr hohe Fallhöhe.

Der Spieler muss Möbel mithilfe eines Krans durch Fenster bewegen.

Der Wind beeinflusst die Last.

Ein schlecht befestigtes Sofa kann:

* gegen das Gebäude schlagen,
* rotieren,
* Fenster zerstören,
* abstürzen.

---

# 47. MISSION 4: DIE MESSI-WOHNUNG

Extrem viele Kleinstobjekte:

* Papier
* Dosen
* Kartons
* Bücher
* Plastik
* Kleidung
* Müll.

Die meisten Objekte sind keine normalen Möbel.

Hier muss der Spieler Werkzeuge verwenden:

* Besen
* Staubsauger
* Laubbläser
* Container.

Das Ziel ist eher:

„Entrümpeln“

als klassisches „Möbel tragen“.

---

# 48. MISSION 5: RIVALISIERENDE UMZUGSFIRMA

Eine KI-Gegenfirma taucht auf.

Sie versucht:

* Kundenaufträge zu stehlen
* Möbel vor dem Spieler wegzutransportieren
* Fahrzeuge zu blockieren
* Chaos zu verursachen.

Wichtig:

Diese Rivalen sollen nicht einfach nur Standardgegner sein.

Sie sollen selbst Umzugsfahrzeuge verwenden und physikalisch mit der Stadt interagieren.

---

# 49. WEITERE SPEZIALMISSIONEN

Entwickle zusätzliche einzigartige Aufträge.

Beispielsweise:

### Aquarium-Transport

Ein riesiges Aquarium darf nicht umkippen.

### Hochzeit

Extrem zerbrechliche Dekoration.

### Museum

Unbezahlbare Exponate müssen transportiert werden.

### Baustelle

Möbel müssen durch unfertige Gebäude bewegt werden.

### Luxusvilla

Alles ist extrem teuer und empfindlich.

### Tierheim

Während des Umzugs laufen Tiere durch die Wohnung.

### Büro-Serverraum

Schwere Server-Racks.

Spezialanforderung:

Stromversorgung darf nicht beschädigt werden.

### Hafen

Container müssen mit Kränen verladen werden.

### Sturmmission

Extreme Windbedingungen.

### Krankenhaus

Empfindliche Geräte.

### Promi-Haus

Zeitdruck durch Medien und Kameras.

---

# 50. PROGRESSION

Das Spiel soll ungefähr einen deutlichen 5+ Stunden langen Progressionsbogen besitzen, aber **kein starres Spielende** haben.

Das Ziel ist:

Der Spieler kann nach dem eigentlichen Progressionsbogen endlos weiter optimieren.

Der Begriff „5 Stunden“ soll als grober Kern-Progressionsrahmen verstanden werden, nicht als harte maximale Spieldauer.

Danach:

* bessere Fahrzeuge
* seltenere Möbel
* härtere Aufträge
* bessere HQs
* höhere Reputation
* seltene Cosmetics
* verrücktere Missionen
* zusätzliche Herausforderungen.

---

# 51. ECONOMY

Die Spielwirtschaft soll modular aufgebaut sein.

Währungen können sein:

* Geld
* Reputation
* eventuell Prestige.

Geld wird verwendet für:

* Fahrzeuge
* Reparaturen
* Werkzeug
* Möbel
* Farben
* Gebäude
* Mitarbeiter
* Marketing.

---

# 52. SPIELSTAND

Singleplayer unterstützt:

* Neues Spiel
* Spiel laden
* mehrere Spielstände.

Beim Start eines neuen Spiels kann der Spieler den Firmennamen festlegen.

Ein Savegame soll unter anderem speichern:

* Firma
* Geld
* Reputation
* HQ
* Fahrzeuge
* Charakter
* Paint
* Accessoires
* freigeschaltete Inhalte
* Möbel
* Fortschritt
* Missionen
* Mitarbeiter
* Einstellungen.

Verwende eine versionierbare Savegame-Struktur.

Plane Migrationen für spätere Savegame-Versionen ein.

---

# 53. HAUPTMENÜ FLOW

Der Ablauf soll ungefähr so aussehen:

START

↓

MAIN MENU

↓

SPIELEN

↓

SINGLEPLAYER
ODER
MULTIPLAYER

---

## SINGLEPLAYER

↓

Neues Spiel
oder
Spielstand laden

↓

Bei neuem Spiel:

Firmenname

↓

Charakter erstellen

↓

HQ

↓

Computer

↓

Unternehmenswebsite erstellen

↓

Erster Kunde erscheint

↓

Auftrag annehmen

↓

Routenkarte

↓

Truck

↓

Einsatzort

↓

Möbel ausräumen

↓

Truck beladen

↓

Zielort

↓

Möbel abladen

↓

Auftrag abschließen

↓

Geld / Reputation

↓

HQ verbessern

↓

Neue Möglichkeiten

---

## MULTIPLAYER

↓

Lokal
oder
Online

Lokal:

* Host
* Join
* Savegame auswählen.

Online:

* Host Session
* Join Session
* Session-Code / Lobby-System als spätere Erweiterung.

---

# 54. ROUTEN-/KARTENSYSTEM

Nach Annahme eines Auftrags soll eine Kartenansicht erscheinen.

Die Karte zeigt:

* aktuelles HQ
* Zieladresse
* Route
* Distanz
* eventuell erwartete Fahrzeit
* Verkehr
* Wetter
* Markierungen.

Die Navigation soll sowohl:

* auf der Weltkarte
* als auch als In-World-Wegführung

funktionieren können.

---

# 55. UI/UX

Das Interface soll modern und klar sein.

Es soll mindestens besitzen:

* Interaktionshinweise
* Objektinformationen
* Schadensanzeige
* Gewicht
* Mission Objective
* Geld
* Reputation
* Minimap
* Karte
* Fahrzeugstatus
* Werkzeug-Slots
* Quest-Anzeige.

Die UI muss für:

* Maus/Tastatur
* Controller

geeignet sein.

---

# 56. AAA-OPTIONSMENÜ

Das Optionsmenü soll realistisch und technisch sinnvoll sein.

Nicht einfach irgendwelche Fake-Optionen.

### Grafik

* Grafik-Preset
* Low
* Medium
* High
* Ultra.

Zusätzlich:

* Auflösung
* Window Mode
* Borderless
* VSync
* FPS-Limit
* MSAA
* Shadow Quality
* Shadow Distance
* Ambient Occlusion
* Volumetric Effects
* Fog Quality
* Reflection Quality
* Texture Quality
* Effects Quality
* Particle Quality
* View Distance
* LOD Quality
* Anti-Aliasing.

---

# 57. RAYTRACING / HIGH-END RENDERING

Plane hochwertige Rendering-Optionen ein.

Wo Godot dies technisch ermöglicht, soll die Architektur moderne Features unterstützen.

Berücksichtige:

* SDFGI
* VoxelGI
* Reflection Probes
* Screen-Space Effects
* hochwertige Schatten
* dynamische Beleuchtung.

WICHTIG:

Keine Option darf lediglich im Menü existieren, ohne technische Wirkung.

Jede Option muss:

* tatsächlich auf Project Settings / Rendering / Nodes / Shader wirken
* sauber ein- und ausschaltbar sein
* möglichst ohne Neustart aktualisierbar sein.

Wenn eine Funktion in der verwendeten Godot-Version anders heißt oder technisch nicht existiert, verwende die tatsächlich verfügbare Godot-4-Funktion und dokumentiere die Abweichung.

---

# 58. OUTLINE / VISUAL STYLE

Alle relevanten Objekte sollen einen schwarzen Outline-Look besitzen.

Der Grafikstil soll:

* Low- bis Mid-Poly
* cartoonartig
* modern
* sauber
* leicht überzeichnet

sein.

Der Outline-Effekt soll zentral verwaltet werden.

Mögliche Techniken:

* Inverted Hull
* Normal-based Outline
* Depth-based Outline
* Post-Processing.

Wähle die technisch geeignetste Variante für Performance und Multiplayer.

---

# 59. PHYSIK-CHARAKTER

Der Spielercharakter soll sich wackelig anfühlen.

Aber die Steuerung darf nicht unpräzise oder frustrierend werden.

Deshalb soll die Architektur zwischen:

* Gameplay Movement
* Physical Body
* Visual Skeleton
* Ragdoll
* Animation

unterscheiden.

Der Spieler soll normal laufen können, aber bei:

* Kollision
* Sturz
* Explosion
* Fahrzeugunfall
* schwerem Objektkontakt

physikalisch reagieren.

---

# 60. RAGDOLL-SYSTEM

Nutze:

* Skeleton3D
* PhysicalBoneSimulator3D bzw. geeignete Godot-4-Physic-Bone-Strukturen
* AnimationTree
* Blend-Übergänge.

Ragdoll darf dynamisch aktiviert/deaktiviert werden.

Beispielsweise:

NORMAL

↓

IMPACT

↓

STAGGER

↓

RAGDOLL

↓

RECOVERY

↓

NORMAL

---

# 61. PLAYER NODE TREE

Erzeuge einen detaillierten Node Tree für den Spieler.

Berücksichtige mindestens:

* Player Root
* Movement
* Visual
* Skeleton
* Physical Bones
* Camera
* Camera Pivot
* Interaction Origin
* Interaction Ray
* Grab Point
* Hands
* Audio
* UI Anchor
* Network Synchronizer.

Die genaue Struktur soll begründet werden.

---

# 62. TRUCK NODE TREE

Erzeuge einen modularen Truck.

Berücksichtige:

* Vehicle Root
* Body
* Collision
* Wheel System
* Engine
* Suspension
* Seat
* Passenger Seat
* Driver Seat
* Cargo Area
* Cargo Anchors
* Lights
* Horn
* Interaction
* Damage
* Paint/Decals
* Network Synchronizer.

---

# 63. MODULARES MÖBEL NODE TREE

Erzeuge einen wiederverwendbaren Möbelstandard.

Beispielsweise:

FurnitureRoot

├── Visual
├── Collision
├── RigidBody3D
├── Interaction
├── GrabPoints
├── DamageComponent
├── BreakableParts
├── Audio
├── DecalReceiver
├── NetworkSync.

Die Architektur soll sowohl einfache Objekte als auch komplexe Möbel unterstützen.

---

# 64. COMPONENT-BASED DESIGN

Verwende möglichst eine modulare Component-Architektur.

Beispiele:

* HealthComponent
* DamageComponent
* InteractionComponent
* GrabComponent
* PaintComponent
* VehicleComponent
* SaveableComponent
* NetworkComponent
* InventoryComponent
* WeatherReactionComponent
* BreakableComponent.

Vermeide riesige Monolith-Skripte.

---

# 65. AUTOLOADS / GLOBAL SYSTEMS

Plane geeignete globale Manager.

Beispielsweise:

* GameManager
* SaveManager
* SceneManager
* InputManager
* AudioManager
* UIManager
* InteractionManager
* MissionManager
* EconomyManager
* VehicleManager
* CharacterManager
* MultiplayerManager
* WeatherManager
* WorldManager.

Verwende aber nicht automatisch für alles einen Autoload.

Erkläre, was wirklich global sein muss und was als normale Scene/Service-Struktur umgesetzt werden sollte.

---

# 66. INTERACTION MANAGER

Eines der wichtigsten Core-Skripte soll sein:

`InteractionManager.gd`

Dieser Manager soll die zentrale Logik für Interaktionen bereitstellen.

Mindestens:

* Objekt-Erkennung
* Raycasts
* Interaktionsziel
* Grab-Erkennung
* Grab Start
* Grab Update
* Grab Release
* Objektrotation
* Werkzeuginteraktionen
* Paint Interactions
* Spray
* Damage Detection.

---

# 67. PHYSIKALISCHES GREIFEN IM INTERACTION MANAGER

Implementiere eine robuste Architektur für:

1. Erkennen eines interagierbaren Objektes.
2. Prüfen, ob es greifbar ist.
3. Prüfen, ob Masse/Kraft innerhalb des Spielerlimits liegt.
4. Erstellen eines stabilen Grab-Constraints.
5. Übertragen der Zielposition.
6. optionaler Rotation.
7. Begrenzung extremer Geschwindigkeiten.
8. korrektem Loslassen.
9. Multiplayer-Synchronisation.

Vermeide direkte Teleportation physischer Objekte.

Die Lösung soll physikalisch glaubwürdig sein.

---

# 68. GRAB FEEL

Das Greifen soll sich gut anfühlen.

Berücksichtige:

* Spring Strength
* Damping
* Mass Ratio
* Distance
* Maximum Force
* Rotation Torque
* Maximum Velocity.

Diese Parameter sollen später im Inspector konfigurierbar sein.

---

# 69. DAMAGE-BERECHNUNG

Der InteractionManager bzw. ein dedizierter Damage-Service soll Aufpralle auswerten.

Berücksichtige:

* Relative Velocity
* Collision Impulse
* Mass
* Material
* Surface Type
* empfindliche Komponenten.

Erzeuge keine willkürlichen Schadenswerte.

Die Schadensermittlung soll nachvollziehbar und deterministisch genug sein.

---

# 70. PAINT LOGIC

Der InteractionManager soll erkennen können:

Spieler hält Pinsel/Spraydose

↓

Hit-Test

↓

Surface Receiver gefunden

↓

Hit Position

↓

Surface Normal

↓

UV / Decal Position

↓

Paint Operation

↓

Visual Update

↓

Save State

↓

Multiplayer Sync.

---

# 71. INPUT ARCHITECTURE

Nutze Godot Input Actions.

Keine harte Abhängigkeit von:

`Input.is_key_pressed(KEY_...)`

wo ein Input Mapping sinnvoller ist.

Definiere beispielsweise:

* move_forward
* move_backward
* move_left
* move_right
* interact
* grab
* release
* rotate_object
* jump
* sprint
* tool_next
* tool_previous
* open_map
* open_inventory
* open_menu
* vehicle_accelerate
* vehicle_brake
* vehicle_horn.

Unterstütze Keyboard, Mouse und Controller.

---

# 72. SAVE ARCHITECTURE

Savegames müssen:

* robust
* versioniert
* erweiterbar
* möglichst fehlertolerant

sein.

Speichere keine unnötigen Laufzeitobjekte.

Verwende Datenmodelle / Dictionaries / Resources oder ein anderes sauberes serialisierbares Format.

Beispielsweise:

`save_version = 1`

Spätere Versionen:

`save_version = 2`

mit Migration.

---

# 73. DEBUG-TOOLS

Entwickle ein Entwickler-Debug-System.

Es soll möglich sein:

* Geld zu setzen
* Mission abzuschließen
* Objekt zu spawnen
* Objekt zu löschen
* Physik-Infos zu sehen
* FPS zu sehen
* Netzwerkstatus zu sehen
* Collision Shapes anzuzeigen
* Grab-Constraints zu visualisieren
* Schaden anzuzeigen.

Das Debug-System darf in Release Builds deaktiviert werden.

---

# 74. PERFORMANCE

Achte insbesondere auf:

* Physik-Tick
* Netzwerk-Tick
* zu viele RigidBodies
* zu viele Collision Shapes
* zu viele Decals
* GPU-Overdraw
* Partikel
* NPC-Anzahl
* Fahrzeugsimulation
* große Open World.

Verwende keine unnötigen `_process()`-Loops.

Nutze:

* Timer
* Signals
* Physics Tick
* Caching
* Object Pooling

wo sinnvoll.

---

# 75. PHYSIK-OPTIMIERUNG

Die Stadt kann Millionen dekorativer Objekte besitzen, aber nicht Millionen aktive Physics Bodies.

Unterscheide:

### Static World

Gebäude, Straßen, Wände.

### Dynamic Physics

Möbel, Fahrzeuge, Spieler.

### Lightweight Physics

Kleine lose Objekte.

### Cosmetic

Nicht physikalisch relevante Dekoration.

Diese Kategorien sollen technisch voneinander getrennt werden.

---

# 76. WORLD STREAMING

Erstelle eine Architektur für die Aufteilung der Stadt in Zellen.

Beispielsweise:

CityChunk

* loaded
* active
* visible
* simulated.

Nahe dem Spieler:

volle Simulation.

Weiter entfernt:

reduzierte Simulation.

Sehr weit entfernt:

keine aktive Simulation.

---

# 77. NPC SYSTEM

NPCs sollen nicht jeden Frame mit voller Logik laufen.

Verwende unterschiedliche Simulationsstufen.

Beispielsweise:

FULL

REDUCED

ANIMATED

STATIC.

---

# 78. AUDIO

Plane ein modulares Audiosystem.

Physik soll Geräusche erzeugen:

* Möbel fallen
* Glas zerbricht
* Holz knackt
* Metall schlägt auf
* Truck hupt
* Motor läuft
* Reifen rutschen
* Regen
* Wind
* Schritte.

Sounds können abhängig sein von:

* Material
* Masse
* Geschwindigkeit
* Surface.

---

# 79. MATERIAL SYSTEM

Erzeuge Materialtypen.

Beispielsweise:

* Wood
* Metal
* Glass
* Plastic
* Fabric
* Ceramic
* Rubber
* Concrete
* Grass
* Asphalt.

Diese Daten sollen von mehreren Systemen verwendet werden:

* Damage
* Audio
* Friction
* Paint
* Weather
* Visual Effects.

---

# 80. RUTSCH- UND FRIKTIONS-SYSTEM

Materialien besitzen unterschiedliche Reibungswerte.

Regen kann diese Werte verändern.

Beispielsweise:

Holz auf trockenem Boden ≠ Holz auf nassem Boden.

Das beeinflusst:

* Möbel
* Fahrzeuge
* Spieler
* Werkzeuge.

---

# 81. FAHRZEUG-PHYSIK

Der Truck soll sich nicht wie ein Arcade-Sprite bewegen.

Er soll Gewicht spürbar machen.

Wenn die Ladefläche leer ist:

→ leichter.

Wenn sie voll ist:

→ schwerer.

Wenn das Gewicht links liegt:

→ Fahrzeug kann sich zur Seite neigen.

Wenn ein Tresor hinten steht:

→ anderes Fahrverhalten.

Das soll spielerisch vereinfacht, aber physikalisch nachvollziehbar umgesetzt werden.

---

# 82. LADUNGSSICHERUNG

Implementiere optional ein System zur Ladungssicherung.

Beispielsweise:

* Gurte
* Befestigungspunkte
* Seile
* Netze.

Schlecht gesicherte Möbel können während der Fahrt:

* rutschen
* umkippen
* gegeneinander schlagen.

Damit entsteht ein kompletter Sub-Gameplay-Loop.

---

# 83. GARAGE

In der Garage kann der Spieler Fahrzeuge:

* reparieren
* lackieren
* tunen
* dekorieren
* aufrüsten.

Paint und Decals sollen auch hier funktionieren.

---

# 84. CUSTOM TRUCK PAINT

Der Truck soll vollständig individualisierbar sein:

* Primärfarbe
* Sekundärfarbe
* Felgenfarbe
* Reifen
* Decals
* Graffiti
* Logos
* Firmenfarben.

---

# 85. MÖBEL-CUSTOMIZATION

Möbel sollen teilweise ebenfalls personalisierbar sein.

Beispielsweise:

* Stofffarbe
* Holzfarbe
* Metallfarbe
* Muster
* Decals.

Das kann für Sandbox/HQ und Shops relevant sein.

---

# 86. VERSTECKTE SYSTEME / EASTER EGGS

Baue Raum für:

* versteckte Gegenstände
* geheime Missionen
* seltene Fahrzeuge
* besondere Hüte
* absurde Möbel
* Easter Eggs.

Beispiele:

* goldene Toilette
* riesiger Gartenzwerg
* Mini-Truck
* extrem schwerer Kühlschrank
* mysteriöse Kiste.

---

# 87. RANDOM EVENTS

Die Stadt soll gelegentlich dynamische Ereignisse erzeugen.

Beispiele:

* Verkehrsunfall
* Baustelle
* Straßensperrung
* Demonstration
* Stromausfall
* heftiger Sturm
* Feuerwehreinsatz
* verlorener Gegenstand
* spontaner NPC-Auftrag.

Der Spieler kann diese Ereignisse optional erleben.

---

# 88. KOMISCHE PHYSIK-EREIGNISSE

Das Spiel soll Momente fördern, die Spieler später Freunden erzählen.

Beispiele:

Ein Sofa bleibt in einer Tür stecken.

Ein Spieler zieht am Sofa.

Ein zweiter Spieler zieht von der anderen Seite.

Die Tür löst sich aus den Angeln.

Das Sofa fliegt die Treppe runter.

Ein Mitarbeiter erschrickt.

Der Truck fährt rückwärts dagegen.

Der Auftrag endet trotzdem erfolgreich, aber mit massivem Schaden.

Solche Situationen sollen möglich sein, ohne dass das System geskriptet ist.

---

# 89. MISSION GENERATION

Missionen sollen aus Daten bestehen.

Beispielsweise:

`MissionDefinition`

enthält:

* SourceLocation
* DestinationLocation
* RequiredObjects
* OptionalObjects
* TimeLimit
* WeatherOverride
* SpecialRules
* Reward
* DamageMultiplier
* Difficulty.

Dadurch soll später Content ohne Änderung des Core-Codes ergänzt werden können.

---

# 90. GAMEPLAY STATES

Erstelle zentrale States für:

* MainMenu
* CharacterCreator
* HQ
* BuildMode
* MissionPreparation
* Driving
* JobSite
* Loading
* Transport
* Unloading
* MissionComplete
* Pause.

Die State Machine soll modular sein.

---

# 91. SCENE MANAGEMENT

Die Architektur muss berücksichtigen, dass:

* Main Menu
* Character Creator
* HQ
* City
* Mission Interiors
* Shops
* Garage

nicht alle permanent gleichzeitig voll simuliert werden müssen.

Nutze Szenenwechsel und/oder Streaming.

---

# 92. SHOP-INNENRÄUME

Shops sollen echte Gebäude in der Welt sein.

Der Spieler geht hinein.

Dort kann man:

* NPC ansprechen
* Produkte ansehen
* kaufen
* testen.

Die Shops sollen nicht ausschließlich als UI-Menüs existieren.

---

# 93. INVENTAR

Es darf ein Inventar geben für:

* Spraydosen
* Werkzeuge
* Kleidung
* kleinere Gegenstände
* Zubehör.

Aber keine klassische „Möbel im Inventar“-Logik für große Möbel.

---

# 94. QUEST- UND OBJECTIVE SYSTEM

Aufträge können mehrere Objectives haben.

Beispiel:

1. Küche vollständig ausräumen.
2. Fernseher unbeschädigt transportieren.
3. Sofa nicht fallen lassen.
4. Truck richtig beladen.
5. Zielort innerhalb Zeit erreichen.

Optionalziele geben Bonus.

---

# 95. FAIL STATES

Missionen sollen nicht ausschließlich „Game Over“ kennen.

Mögliche Zustände:

* Auftrag erfolgreich
* Auftrag teilweise erfolgreich
* Auftrag schlecht abgeschlossen
* Auftrag abgebrochen
* Auftrag gescheitert.

Das Spiel soll humorvoll mit Fehlern umgehen.

---

# 96. REPUTATIONSSYSTEM

Die Firma besitzt Reputation.

Diese beeinflusst:

* Kundenzahl
* Auftragstyp
* Kundenbudget
* mögliche Aufträge
* Shops
* Freischaltungen.

Reputation kann sinken durch:

* extreme Schäden
* Abbruch
* schlechte Zeit
* verlorene Gegenstände.

---

# 97. KUNDEN

Kunden sollen verschiedene Profile besitzen.

Beispielsweise:

* Student
* Familie
* Unternehmer
* Rentner
* Millionär
* Gamer
* Musiker
* Wissenschaftler
* Künstler
* Exzentriker.

Die Möbel und Missionen passen dazu.

---

# 98. KUNDENWÜNSCHE

Kunden können spezielle Anforderungen haben:

* „Bitte den Fernseher nicht beschädigen.“
* „Das Klavier darf keinen Kratzer bekommen.“
* „Die Vase meiner Großmutter ist unbezahlbar.“
* „Alles muss bis 18 Uhr fertig sein.“

Das erhöht die Spannung.

---

# 99. PHYSIKALISCHE UMWELT-INTERAKTION

Die Welt soll möglichst viele Interaktionen erlauben.

Beispiele:

* Türen öffnen
* Fenster öffnen
* Schubladen öffnen
* Schränke verschieben
* Lampen umwerfen
* Kartons stapeln
* Müll verschieben
* Vorhänge bewegen.

Aber unterscheide bewusst zwischen:

Gameplay-Relevanz und

reiner Dekoration,

damit die Performance erhalten bleibt.

---

# 100. ARCHITEKTURPRINZIPIEN

Die gesamte Codebasis soll folgende Prinzipien befolgen:

### SOLID

Wo sinnvoll.

### Separation of Concerns

Gameplay != UI != Daten != Speicherung != Netzwerk.

### Data Driven

Missionen, Möbel, Fahrzeuge und Items sollen nicht hart in Code kodiert werden.

### Composition over Inheritance

Komponenten bevorzugen, wenn passend.

### Signals

Für lose Kopplung.

### Dependency Injection / Services

Wo hilfreich.

### Configurable

Balancing-Werte nicht überall hart codieren.

---

# 101. CODING STYLE

Verwende sauberes GDScript.

Beispielsweise:

* Typannotationen
* klare Variablennamen
* keine unnötigen Ein-Buchstaben-Namen
* keine riesigen Methoden
* Kommentare nur dort, wo sie tatsächlich helfen
* keine unnötigen globalen Zustände.

Vermeide:

* `get_node("../../../../whatever")`
* harte Szenenpfade überall
* versteckte Singletons
* unkontrollierte RPCs
* ungetypte Datenstrukturen, wo Typen sinnvoll sind.

Nutze bevorzugt:

* `@export`
* `class_name`
* `signal`
* `enum`
* typed arrays/dictionaries
* Resources.

---

# 102. FEHLERBEHANDLUNG

Das System soll robuste Fehlerbehandlung besitzen.

Beispielsweise:

Wenn ein Möbelobjekt keine DamageComponent besitzt:

→ nicht crashen.

Wenn ein Netzwerkspieler verschwindet:

→ Grab-Constraint sauber lösen.

Wenn ein Savegame beschädigt ist:

→ Fehler melden und auf sicheren Zustand zurückfallen.

Wenn ein Asset fehlt:

→ Fallback nutzen.

---

# 103. MULTIPLAYER-SICHERHEIT

Auch wenn Online zunächst simuliert ist:

RPCs dürfen nicht blind alles akzeptieren.

Überprüfe:

* Authority
* erlaubte Aktionen
* Objektzugriff
* Ownership.

---

# 104. NETZWERK-PHYSIK

Überlege sorgfältig, welche Objekte:

* vollständig synchronisiert
* nur bei Interaktionen synchronisiert
* interpoliert
* server-authoritativ

simuliert werden.

Nicht jedes kleine Objekt muss permanent vollständige Netzwerkdaten senden.

---

# 105. UI DEBUGGING

Baue Debug-Informationen ein für:

* aktuelles Interaction Target
* Grab Strength
* Grab Distance
* Object Mass
* Damage %
* Network Authority
* Physics State
* Mission State.

---

# 106. DATEI- UND ORDNERSTRUKTUR

Erstelle eine professionelle Godot-Ordnerstruktur.

Zum Beispiel logisch getrennt nach:

`core/`

`gameplay/`

`player/`

`vehicles/`

`furniture/`

`missions/`

`world/`

`ui/`

`systems/`

`components/`

`data/`

`resources/`

`scenes/`

`shaders/`

`audio/`

`materials/`

`tools/`

`debug/`

`save/`

`multiplayer/`

Die endgültige Struktur soll an die tatsächlich vorhandene Repo angepasst werden.

---

# 107. REQUIRED DELIVERABLE 1 – KOMPLETTE ORDNERSTRUKTUR

Generiere eine vollständige Godot-Ordnerstruktur.

Für jeden wichtigen Ordner erklären:

* Zweck
* Verantwortlichkeit
* Beispiele enthaltene Dateien
* Abhängigkeiten
* warum diese Trennung sinnvoll ist.

Zeige anschließend den kompletten Tree als Codeblock.

---

# 108. REQUIRED DELIVERABLE 2 – PLAYER NODE TREE

Generiere einen vollständigen Player Node Tree.

Berücksichtige insbesondere:

* CharacterBody3D
* Visual
* Skeleton3D
* PhysicalBones
* Collision
* Camera
* Camera Pivot
* Interaction Ray
* Grab Origin
* Audio
* MultiplayerSynchronizer
* AnimationTree
* Ragdoll Controller
* Paint Receiver
* Equipment.

Erkläre die Verantwortung jedes Nodes.

---

# 109. REQUIRED DELIVERABLE 3 – TRUCK NODE TREE

Generiere einen vollständigen modularen Truck Node Tree.

Berücksichtige:

* Fahrzeugphysik
* Sitze
* Räder
* Federung
* Motor
* Ladefläche
* Gewicht
* Schaden
* Lack
* Decals
* Licht
* Hupe
* Netzwerk.

---

# 110. REQUIRED DELIVERABLE 4 – MODULARES MÖBEL

Generiere einen vollständigen Node Tree für ein Möbelstück.

Das Modell muss:

* greifbar
* beschädigbar
* bemalbar
* zerstörbar
* speicherbar
* synchronisierbar

sein können.

---

# 111. REQUIRED DELIVERABLE 5 – INTERACTION MANAGER

Generiere das Core-GDScript für:

`InteractionManager.gd`

Das Skript soll mindestens Architektur für:

* Raycast
* Interactable Detection
* Grab
* Grab Release
* Physics Manipulation
* Rotation
* Multi Grab
* Paint
* Spray
* Damage.

enthalten.

Wichtig:

Schreibe keinen pseudo-code-artigen Müll wie:

`doPhysicsThing()`

sondern echten, möglichst direkt verwendbaren Godot-4-Code.

Wo bestimmte Bestandteile aufgrund fehlender Assets oder Szenen noch nicht final implementierbar sind, kapsel sie sauber hinter Schnittstellen.

---

# 112. REQUIRED DELIVERABLE 6 – CORE DATA CLASSES

Erstelle passende Datenstrukturen für:

* FurnitureData
* VehicleData
* MissionData
* CharacterData
* CosmeticData
* SaveData.

Nutze Godot Resources, wo das sinnvoll ist.

---

# 113. REQUIRED DELIVERABLE 7 – SAVE SYSTEM ARCHITECTURE

Zeige:

* SaveManager
* SaveData
* Serialization
* Deserialization
* Versionierung
* Migration.

---

# 114. REQUIRED DELIVERABLE 8 – MULTIPLAYER ARCHITECTURE

Zeige:

* NetworkManager
* Host/Client
* Player Spawn
* MultiplayerSpawner
* MultiplayerSynchronizer
* Object Ownership
* Grab Sync
* Vehicle Sync
* Mission State Sync.

---

# 115. REQUIRED DELIVERABLE 9 – MISSION ARCHITECTURE

Zeige:

* MissionManager
* MissionDefinition
* MissionState
* Objective
* Reward
* Damage Penalty
* Completion.

---

# 116. REQUIRED DELIVERABLE 10 – IMPLEMENTIERUNGSREIHENFOLGE

Erstelle eine sinnvolle Entwicklungsreihenfolge.

Nicht alles gleichzeitig.

Priorität:

### PHASE 1

Project Foundation

### PHASE 2

Player

### PHASE 3

Interaction

### PHASE 4

Furniture

### PHASE 5

Truck

### PHASE 6

Mission

### PHASE 7

HQ

### PHASE 8

Customization

### PHASE 9

Economy

### PHASE 10

Multiplayer

### PHASE 11

City

### PHASE 12

Advanced Content

### PHASE 13

Optimization

---

# 117. VERTICAL SLICE

Bevor das gesamte Spiel geplant wird, entwirf einen vollständigen Vertical Slice.

Der Vertical Slice soll bereits enthalten:

* Main Menu
* Character
* kleines HQ
* einen Truck
* eine Stadtsektion
* einen Auftrag
* ein Haus
* Möbel
* Greifmechanik
* Truck beladen
* Truck fahren
* Zielort
* Möbel abladen
* Schaden
* Bezahlung
* Savegame.

Erst wenn dieser Core Loop stabil ist, soll auf weitere Systeme aufgebaut werden.

---

# 118. TESTSTRATEGIE

Definiere Tests für:

* Grab
* Release
* Damage
* Save
* Load
* Mission Completion
* Truck Load
* Multiplayer Join
* Multiplayer Leave.

Erstelle gegebenenfalls einfache Test-Scenes.

---

# 119. PHYSIK-TESTSCENES

Erstelle kleine Testarenen:

### Grab Test

Objekte mit unterschiedlicher Masse.

### Damage Test

Objekte fallen aus verschiedenen Höhen.

### Furniture Test

Sofa, Tisch, Schrank.

### Multiplayer Test

Zwei Spieler greifen dasselbe Sofa.

### Vehicle Load Test

Truck mit verschiedenen Gewichten.

Diese Testscenes sind sehr wichtig, weil die Kernidee des Spiels auf Physik basiert.

---

# 120. DESIGN DER ABHÄNGIGKEITEN

Zeige deutlich:

Wer darf wen referenzieren?

Beispielsweise:

UI
↓
Gameplay Services
↓
Components
↓
World Objects.

Vermeide:

Furniture → MainMenu

oder

Player → ShopUI

wenn eine lose Kopplung sinnvoller wäre.

---

# 121. SIGNAL ARCHITECTURE

Definiere zentrale Signals.

Beispiele:

`interaction_started`

`interaction_ended`

`object_grabbed`

`object_released`

`damage_changed`

`mission_started`

`mission_completed`

`mission_failed`

`money_changed`

`reputation_changed`

`save_completed`

`player_joined`

`player_left`.

---

# 122. EXTENSIBILITY

Die Architektur muss offen genug sein, später hinzuzufügen:

* Steam Multiplayer
* Dedicated Server
* weitere Städte
* neue Fahrzeuge
* neue Möbel
* neue Missionen
* NPC-Mitarbeiter
* größere Gebäude
* neue Wettertypen
* Jahreszeiten
* neue Shops
* neue Paint Tools.

---

# 123. MODULARITY

Ein neues Möbelstück sollte idealerweise nur benötigen:

1. Model
2. Collision
3. FurnitureData
4. optional BreakableParts
5. optional Sounds
6. optional Decal Receiver.

Der Core-Code soll dafür nicht geändert werden müssen.

---

# 124. BALANCING

Werte sollen zentral konfigurierbar sein.

Nicht:

`damage = velocity * 17.372`

an zehn verschiedenen Stellen.

Stattdessen:

`DamageSettings`

oder entsprechende Resources.

---

# 125. IMMERSIVE DETAIL SYSTEMS

Füge sinnvolle zusätzliche Systeme hinzu, die das Spiel interessanter machen.

Beispiele:

### Möbelkatalog

Spieler können bekannte Möbelstücke sammeln.

### Kundentypen

Unterschiedliche Kunden verhalten sich unterschiedlich.

### Firmenstatistik

* Anzahl Aufträge
* Schaden
* Verdientes Geld
* Durchschnittszeit
* beschädigte Gegenstände.

### Trophäen

Beispielsweise:

„100 Sofas transportiert“

„Nie eine Vase beschädigt“

„Truck 50-mal umgekippt“.

---

# 126. CHAOS EVENTS

Baue seltene zufällige Ereignisse.

Zum Beispiel:

* ein Möbelstück verhakt sich
* NPC fällt hin
* Regen beginnt genau beim Einladen
* Tür blockiert Sofa
* Strom fällt aus
* Kran schwankt
* Waschmaschine läuft plötzlich
* Tier rennt durch die Wohnung.

Diese Systeme sollen emergentes Gameplay fördern.

---

# 127. EXTREME LATE-GAME CONTENT

Später darf das Spiel immer absurder werden.

Beispielsweise:

* Umzug auf einem fahrenden Zug
* Schiff-Umzug
* Baustellenkran
* unterirdischer Bunker
* gigantisches Luxus-Hotel
* Freizeitpark
* UFO-artige Spezialmission
* Schwerelosigkeits-Testlabor
* extrem kleine Möbel in riesigen Hallen
* extrem große Möbel in viel zu kleinen Häusern.

Diese Missionen sollen jedoch auf denselben Core-Systemen basieren.

---

# 128. KEINE CONTENT-SPAGHETTI-ARCHITEKTUR

Sehr wichtig:

Erstelle nicht für jede Mission ein komplett neues System.

Eine Mission darf neue Parameter und Regeln besitzen, aber die Grundsysteme sollen wiederverwendet werden.

Beispiel:

Spukhaus nutzt:

Mission System
+
Furniture System
+
Physics System
+
Weather
+
Event System.

Nicht:

`HauntedHouseMegaManager.gd`

mit 5.000 Zeilen.

---

# 129. VISUELLE ARCHITEKTUR

Definiere:

* Materials
* Shaders
* Lighting
* Outline
* Weather VFX
* Damage VFX
* UI.

Nutze gemeinsame Shader und Materialien, wenn möglich.

---

# 130. FOKUS AUF PERFORMANCE UND STABILITÄT

Das Spiel kann extrem viele Physikobjekte enthalten.

Der wichtigste technische Grundsatz lautet:

**Physik-Komplexität darf nicht unkontrolliert wachsen.**

Implementiere daher:

* Physics Sleep
* Activation Radius
* Simplified Collision
* object categories
* pooling
* reduced simulation
* distance-based activation.

---

# 131. CODE-QUALITÄT

Generierter Code soll:

* vollständig
* syntaktisch korrekt
* lesbar
* modular
* Godot-4-kompatibel
* typisiert
* erweiterbar

sein.

Falls du eine API oder Funktion nicht sicher kennst:

Erfinde sie nicht.

Nutze stattdessen die tatsächlich verfügbare Godot-4-API oder markiere die Stelle eindeutig als versionsabhängig und erläutere die notwendige Anpassung.

---

# 132. OUTPUT-FORMAT

Deine Antwort soll nicht einfach nur eine riesige Menge Code ausgeben.

Strukturiere die Antwort exakt in:

## A. Repository Analyse

Was existiert bereits?

Was kann wiederverwendet werden?

Was fehlt?

## B. Gesamtarchitektur

Diagramm/Hierarchie der Systeme.

## C. Ordnerstruktur

Kompletter Tree.

## D. Node Trees

Player

Truck

Furniture

HQ

Mission

## E. Datenarchitektur

Resources / Data Classes.

## F. Core Systems

Liste mit Verantwortlichkeiten.

## G. InteractionManager.gd

Vollständiger Core-Code.

## H. Weitere Core-Skripte

Die wichtigsten Scripts.

## I. Multiplayer

Architektur + relevante Scripts.

## J. Save System

Architektur + Code.

## K. Mission System

Architektur + Code.

## L. Customization

Architektur + Paint-System.

## M. Build Mode

Architektur.

## N. Fahrzeug-System

Architektur.

## O. Stadt

Streaming / NPC / Verkehr / Wetter.

## P. UI

Screens und Zustände.

## Q. Entwicklungs-Roadmap

Reihenfolge.

## R. Testplan

Wie alles überprüft wird.

---

# 133. WICHTIG FÜR CODE

Wenn du Code schreibst:

* Jeder Codeblock muss den korrekten Dateinamen enthalten.
* Gib den vollständigen Pfad an.
* Gib die Rolle der Datei an.
* Gib an, welche Dateien davon abhängig sind.
* Vermeide unvollständige Codefragmente, außer wenn explizit nur ein Ausschnitt sinnvoll ist.
* Verwende keine erfundenen Imports.
* Verwende keine nicht vorhandenen Klassen.
* Verwende keine Godot-3-APIs.

Beispiel:

```text
res://gameplay/interaction/interaction_manager.gd
```

Dann:

```gdscript
extends Node
class_name InteractionManager
```

---

# 134. WICHTIG FÜR SZENEN

Wenn du Nodes vorschlägst:

Gib an:

* Node Name
* Node Type
* Parent
* Zweck
* relevante Properties
* relevante Scripts.

Beispielsweise:

```text
Player
└── Physics
    ├── CollisionShape3D
    ├── Visual
    └── InteractionOrigin
```

---

# 135. WICHTIG FÜR DIE REPO-INTEGRATION

Der gesamte Output muss so gestaltet sein, dass ich:

1. Dateien kopieren kann.
2. Ordner erstellen kann.
3. Szenen aufbauen kann.
4. Scripts einfügen kann.
5. das Projekt starten kann.

Der Output soll deshalb konkrete Integrationshinweise geben.

Beispielsweise:

„Diese Datei nach `res://...`“

„Dieses Script an Node X hängen.“

„Diese Resource im Inspector konfigurieren.“

---

# 136. KEIN OVERENGINEERING OHNE GRUND

Obwohl das Spiel sehr groß ist, soll die Architektur nicht unnötig kompliziert sein.

Jedes System soll eine klare Begründung besitzen.

Wenn es zwei mögliche Ansätze gibt:

* erkläre kurz beide
* entscheide dich für einen
* begründe die Entscheidung.

---

# 137. GODOT VERSION

Zielplattform ist Godot 4.x.

Berücksichtige die Unterschiede zwischen modernen Godot-4-Releases.

Wenn eine Funktion versionsabhängig ist, erwähne dies explizit.

---

# 138. PRIORITÄTEN

Priorität 1:

Spielbarkeit.

Priorität 2:

stabile Physik.

Priorität 3:

saubere Architektur.

Priorität 4:

Multiplayer-Kompatibilität.

Priorität 5:

Customization.

Priorität 6:

Welt und Content.

Priorität 7:

Grafik-Polishing.

---

# 139. CORE LOOP FIRST

Die allerwichtigste Regel:

Bevor du riesige Systeme entwirfst, stelle sicher, dass dieser Ablauf funktioniert:

**Spieler → Objekt erkennen → Objekt greifen → Objekt physisch bewegen → Objekt beschädigen können → Objekt in Truck laden → Truck fahren → Ziel erreichen → Objekt abladen → Auftrag abschließen → Geld erhalten.**

Dieser Loop muss das Fundament des gesamten Spiels bilden.

---

# 140. ENDZIEL

Das Endergebnis soll sich wie ein Mix aus:

* physikbasiertem Comedy-Spiel
* Umzugssimulation
* Management-Spiel
* Open-World-Sandbox
* Interior-Design-Spiel
* Character-Customization-Spiel
* Co-op-Chaos-Spiel

anfühlen.

Dabei soll das Spiel nicht bloß viele Features besitzen.

**Die Systeme müssen miteinander interagieren.**

Ein Beispiel:

Der Spieler kauft einen besseren Truck.

↓

Mehr Gewicht möglich.

↓

Dadurch schwerere Möbel transportierbar.

↓

Dadurch bessere Missionen verfügbar.

↓

Dadurch mehr Geld.

↓

Dadurch HQ-Ausbau.

↓

Dadurch bessere Mitarbeiter.

↓

Dadurch größere Aufträge.

↓

Dadurch noch größere Möbel.

↓

Dadurch Bedarf an Spezialwerkzeugen.

↓

Dadurch neue Shops relevant.

Das gesamte Spiel soll ein miteinander verbundenes System bilden.

---

# 141. DEINE AUFGABE AB JETZT

Arbeite wie ein echter Lead Developer an diesem Projekt.

### SCHRITT 1

Analysiere die vorhandene Repository vollständig.

### SCHRITT 2

Erstelle eine technische Bestandsaufnahme.

### SCHRITT 3

Identifiziere bestehende Systeme.

### SCHRITT 4

Erstelle eine Zielarchitektur.

### SCHRITT 5

Zeige exakt, welche bestehenden Dateien geändert werden sollen.

### SCHRITT 6

Zeige, welche neuen Dateien erstellt werden sollen.

### SCHRITT 7

Erstelle zuerst das Core-Fundament.

### SCHRITT 8

Implementiere den Vertical Slice.

### SCHRITT 9

Danach erweitere die Architektur schrittweise.

---

# 142. BESONDERS WICHTIG

Du sollst nicht nur beschreiben, „was man machen könnte“.

Du sollst **eine tatsächlich implementierbare technische Grundlage** erstellen.

Vermeide allgemeine Aussagen wie:

„Man könnte einen InteractionManager machen.“

Stattdessen:

„Erstelle `res://gameplay/interaction/interaction_manager.gd` und hänge ihn an Node X.“

---

# 143. ABSCHLUSSANFORDERUNG

Am Ende deiner Antwort möchte ich:

1. die komplette Ordnerstruktur,
2. die Architekturübersicht,
3. alle wichtigen Node Trees,
4. die wichtigsten Datenklassen,
5. das InteractionManager-Core-Script,
6. Save-System-Grundlagen,
7. Mission-System-Grundlagen,
8. Multiplayer-Architektur,
9. Customization-Architektur,
10. HQ-/Build-Architektur,
11. Fahrzeug-Architektur,
12. Möbel-/Damage-System,
13. Entwicklungsreihenfolge
14. konkrete Integrationsanweisungen.

Die Architektur muss so gestaltet sein, dass ich später zusätzliche Inhalte hinzufügen kann, ohne den Kern des Projekts neu schreiben zu müssen.

---

# 144. LETZTE REGEL

Denke nicht wie jemand, der eine kleine Godot-Demo baut.

Denke wie ein **Lead Developer eines großen, modularen Sandbox-Spiels**.

Die Systeme sollen sich gegenseitig ergänzen.

Physik soll Gameplay erzeugen.

Customization soll Progression erzeugen.

Progression soll neue Missionen ermöglichen.

Missionen sollen die Physik und Werkzeuge herausfordern.

Das HQ soll den Fortschritt sichtbar machen.

Die Stadt soll die Spielwelt lebendig machen.

Multiplayer soll nicht nachträglich „daraufgeklebt“ werden.

Und der Code soll langfristig wartbar bleiben.

**Beginne jetzt mit der Analyse der vorhandenen Repository und entwickle darauf basierend die konkrete Godot-4-Architektur und die Core-Implementierung.**
