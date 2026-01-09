**FunSaver – IM5 Projekt: Leistungsnachweis Interaktive Medien V**  
von Cyrill Felder und Nick Steinmann

(Partnerprojekt mit Simon Huber, Webdesign)

---
<img width="1681" height="881" alt="Bildschirmfoto 2026-01-10 um 00 07 38" src="https://github.com/user-attachments/assets/9632cb97-d078-451a-aa0c-ea9249fe31e0" />

## Projektidee

Der FunSaver ist ein interaktives Tool für Pingpong-Spieler:innen, mit dem sich besondere Spielmomente unkompliziert festhalten lassen. Per Knopfdruck werden die letzten 30 Sekunden einer laufenden Videoaufnahme gespeichert – genau jene Ballwechsel, die sonst in der Dynamik eines Matches verloren gehen würden.

Die Projektidee entstand aus dem Bedürfnis heraus, spontane Highlights sichtbar zu machen, ohne ein Spiel permanent aufzeichnen oder aktiv bedienen zu müssen. Der FunSaver verbindet Interaction Design, audiovisuelle Live-Software und Hardware-Input zu einem intuitiven, spielnahen System.

---

## Konzept & Zielsetzung

Ziel des Projekts war es, eine schnelle, robuste und leicht verständliche Lösung zu entwickeln, die direkt während des Spiels bedient werden kann. Der Fokus lag auf:

- minimaler Interaktion während des Matches  
- klarer und verlässlicher Trigger-Logik  
- einer durchgängigen Verarbeitungskette vom Spielmoment bis zur Veröffentlichung  

Der FunSaver ist als End-to-End-System konzipiert: vom spontanen Knopfdruck bis zur automatischen Online-Verfügbarkeit des Clips.

---

## Funktionsweise (End-to-End)

1. Eine Webcam zeichnet das Spielgeschehen kontinuierlich als Video auf  
2. Die letzten 30 Sekunden Video werden laufend in einem Buffer gespeichert  
3. Ein physischer (oder digitaler) Button löst den Speicherprozess aus  
4. Der zuvor gepufferte Moment wird als Videoclip gesichert  
5. Gleichzeitig wird ein Audio-Feedback abgespielt, das den gespeicherten Moment akustisch feiert  
6. Der Clip wird automatisch auf die Website **funsaver.ch** hochgeladen  
7. Das Highlight ist online abrufbar und teilbar  

---

## Technische Umsetzung (TouchDesigner)

Der gesamte FunSaver-Flow wurde in TouchDesigner umgesetzt. Sowohl Software-Logik als auch Hardware-Anbindung sind in einem zusammenhängenden Netzwerk realisiert.

### Video & Buffering

- Video-Input über `videodevin`  
- Permanentes Zwischenspeichern des Videostreams mittels `cache TOP`  
- wenn Trigger kommt Speicherung der letzten 30 Sekunden `moviefileout TOP`  
- Die Aufnahme greift bewusst auf bereits vergangene Frames zu (Pre-Record-Prinzip)  

---

## Trigger & Interaktion

- Button-Input externe Hardware (Serial Input) oder digital Button
- Verarbeitung über:
  - `keyboardin`
  - `button`
  - `logic`
  - `select`, `math` und `delay CHOPs`  
- Entprellung und Sicherstellung, dass pro Knopfdruck nur ein einzelner Aufnahme-Trigger ausgelöst wird  

---

## Timing & Kontrolle

- Zeitlogik über `timer CHOP`  
- Kontrolliertes Starten und Stoppen der Aufnahme  
- Schutz vor Mehrfachauslösungen während laufender Prozesse, das Signal kommt erst nacht Ablauf der 30 Sec durch 

---

## Audio-Feedback

- Separater Audio-Flow für Feedback und Musik  
- Beim Knopfdruck wird eine passende Musik bzw. ein Sound abgespielt  
- Der Sound dient als emotionales Feedback und markiert den besonderen Spielmoment  
- Audio-Ausgabe erfolgt live über `audiodevout`  
- Das Audio ist nicht Bestandteil der Videoaufnahme  

---

## Video-Feedback
- optional kann über Video-Output via `syphonout` für externe Anwendungen ein Video ausgegeben werden

## Mic zum Anfeuern
- Ein kleines Handmikrofon kann während dem Spiel zum anfeuern der Spielenden genutz werden.
- Dabei wird die Stimme mit einem Effekt verzerrt. 

## Output & Weiterverarbeitung
- Automatisierte Weiterverarbeitung nach der Speicherung  
- Upload-Trigger direkt aus TouchDesigner  

---

## Upload & Web-Integration

Nach der lokalen Speicherung werden die Videoclips automatisch auf die Website **funsaver.ch** hochgeladen.  
Der Upload ist Teil des konzipierten Workflows und erfordert keine zusätzliche Benutzerinteraktion.

Die Website dient als zentrale Plattform zur Ansicht der gespeicherten Spielmomente und wurde von Simon Huber umgesetzt.

---

## Hardware & Software

### Software

- TouchDesigner  


### Hardware

- Laptop (inkl. Tastatur als alternativer Trigger)
- Webcam
- kleines Microfon
- Physischer Button (über Serial Input)
- Screen/Beamer für Video-Feedback Out


---

## Setup

1. Alle Inhalte von Github herunterladen
2. TouchDesigner öffnen  
3. Projektdatei laden  
4. Webcam auswählen
5. optional Screen/Beamer hinzufügen
6. Datei Motivation4.wav neu verknüpfen bei Audio-Feedback (Audio File out)
7. Speicherpfad und Upload-Ziel definieren  
8. Button oder Tastatur-Trigger aktivieren  

Nach dem Start läuft das System kontinuierlich im Hintergrund.

---

## Screenshots & Bilder

Im Rahmen dieses Projektes wurde ein Prototyp entwickelt. Ein entgültiges herzustellen Produkt liegt nicht im Rahmen dieses Leistungsnachweises. 
Dennoch konnten wir alle Funktionen mit Hilfe einer Kartonschaschtel und Plastikstande aufbauen und Testvideos aufnehmen.

Detailiere Aufnahmen und Funktion ist auf unserer Website zu finden: (https://funsaver.ch/anleitung)

Prototyp
<img width="1697" height="875" alt="Bildschirmfoto 2026-01-10 um 00 10 20" src="https://github.com/user-attachments/assets/5ef8d5b6-fe0c-4d32-b85c-ab2098484842" />

<img width="1520" height="881" alt="Bildschirmfoto 2026-01-10 um 00 10 31" src="https://github.com/user-attachments/assets/ff631fd0-4126-44c9-9a93-556dc7aa7970" />

Mikrofon zum Anfeuern der Spielenden
<img width="1637" height="1099" alt="Bildschirmfoto 2026-01-10 um 00 10 41" src="https://github.com/user-attachments/assets/cdae6301-3040-48c0-b869-e73bbff0b95a" />




Mikrofon und Webcam für den Prototypen haben wir billig im Brokenhaus gefunden. 
![IMG_3656](https://github.com/user-attachments/assets/e2b81be3-d822-40cf-9d91-ff467efec6fa)

Unser Touchdesigner Projekt 
<img width="1575" height="926" alt="Bildschirmfoto 2026-01-10 um 00 06 42" src="https://github.com/user-attachments/assets/0727d3f0-ab8d-42c0-8db2-4848a10561ef" />



---
## Technische Herausforderung: Server-Anbindung (Infomaniak) & Automatisierung

Die Anbindung von TouchDesigner an die Website war der anspruchsvollsten Teile des Projekts. 
Da wir **Infomaniak** als Hosting-Anbieter nutzen, konnten wir keinen einfachen HTTP-Upload oder eine fertige Upload-API verwenden. Für unser Setup war der zuverlässigste Weg:

- **SSH** (Shell-Zugriff)  
- **SFTP** (File Transfer über SSH)  
- **MySQL** Zugriff über den Server  

Deshalb wurde eine eigene Upload-Pipeline in TouchDesigner (Python) umgesetzt: TouchDesigner verbindet sich direkt mit dem Server, lädt Clips hoch und schreibt anschließend einen Eintrag in die Datenbank.

---

## Upload- & Datenbank-Workflow (End-to-End)

Sobald TouchDesigner einen neuen Clip lokal gespeichert hat, startet automatisch folgende Kette:

### 1) Upload per SFTP (über SSH)
TouchDesigner baut eine SSH-Verbindung zum Server auf und lädt den Clip per **SFTP** in ein definiertes Web-Verzeichnis hoch (z. B. /pics_from_td/).

### 2) Öffentliche URL generieren
Aus dem Upload-Pfad und der Base-URL wird automatisch die öffentliche Clip-URL erzeugt, z. B.: /funsaver.ch/pics_from_td/clip_0123.mp4

### 3) Eintrag in die MySQL-Datenbank
Damit die Website den Clip kennt und anzeigen kann, wird diese URL in eine Datenbanktabelle geschrieben (z. B. `records`):

sql
INSERT INTO records (url) VALUES (//funsaver.ch/pics_from_td/clip_0123.mp4);

---

## Trigger-Punkt in TouchDesigner

Der Übergang vom lokalen Clip zum Server-Upload wird in TouchDesigner über einen **CHOP Execute DAT** ausgelöst:

```python
def onOffToOn(channel, sampleIndex, val, prev):
    local_filepath = "demopic.png"
    parent().Upload_and_insertDB(local_filepath)
    return
```

Dieser Code wird ausgeführt, wenn ein CHOP-Signal von **0 auf 1** wechselt (z. B. Button oder neuer Clip).  
Dabei wird der komplette Server-Workflow gestartet:
SSH-Verbindung → Upload → URL-Erzeugung → Datenbank-Insert.

---

## Wie die Website die Clips anzeigt

Die Website lädt keine Dateien hoch, sondern arbeitet vollständig datenbankbasiert:

1. Beim Laden der Seite fragt die Website die **Datenbank** ab (Liste aus URLs + Timestamp).
2. Für jeden Eintrag prüft die Website serverseitig, ob die Datei unter der URL existiert.
3. Die Clips werden **nach Timestamp sortiert** (neueste zuerst) und angezeigt.

So entsteht eine klare Trennung:

- **TouchDesigner** erzeugt Clips, triggert Upload und schreibt den DB-Eintrag  
- **Server** speichert Dateien und Datenbank  
- **Website** zeigt nur das an, was in der Datenbank steht und existiert  

---

## Pipeline

```
Knopfdruck → Clip speichern → SSH/SFTP Upload → DB INSERT → 
Website liest DB → Datei-Check → Sortierung nach Timestamp → Anzeige
```

---

## Projektfazit

Der FunSaver ist ein leichtgewichtiges, performantes und erweiterbares End-to-End-System, das zeigt, wie interaktives Design, Hardware-Input und audiovisuelle Live-Software sinnvoll zusammenspielen können.  
Er macht Spielmomente sichtbar – und hörbar erlebbar – genau in dem Moment, in dem sie entstehen, und trägt sie ohne Umwege ins Web.

Gleichzeitig war die Umsetzung technisch deutlich anspruchsvoller als ursprünglich erwartet. Durch das Hosting bei **Infomaniak** war eine einfache Upload-Lösung nicht möglich, was zu einer vergleichsweise komplexen SSH-/SFTP-/Datenbank-Pipeline führte. Diese zusätzliche technische Hürde verkopmplizierte einiges und machte die Entwicklung deutlich aufwendiger als geplant. Ohne die Unterstützung von **Jan** und seine Tutorials wäre dieser Teil kaum umsetzbar gewesen – allein das vollständige Verstehen und Nachvollziehen des Codes im TD hat mehrere Stunden in Anspruch genommen.

Umso grösser war der Moment, als am Ende alles funktionierte: Der Knopfdruck, der Clip, der Upload, der Datenbankeintrag und die Anzeige auf der Website griffen erstmals nahtlos ineinander. Dieser Erfolgsmoment machte die gesamte Komplexität plötzlich greifbar und lohnend.

Das Projekt bot uns die Möglichkeit, **alles bisher gelernte anzuwenden** – von Interaction Design über audiovisuelle Live-Software bis hin zu Server- und Webintegration. Es war ein Projekt, in dem wir nicht nur technische Fähigkeiten zeigen konnten, sondern auch unsere **kreative Vorstellungskraft** voll ausspielen durften. 

Wir bedanken uns herzlich bei Jan für die tolle Unterstützung und Motivation am Projekt/Idee festzuhalten. 

