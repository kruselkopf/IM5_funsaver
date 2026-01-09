# IM5_funsaver

**FunSaver – IM5 Projekt: Leistungsnachweis Interaktive Median V**  
von Cyrill Felder und Nick Steinmann

---

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
- Screens/Beamer für Video-Feedback Out


---

## Setup

1. TouchDesigner öffnen  
2. Projektdatei laden  
3. Webcam auswählen  
4. Speicherpfad und Upload-Ziel definieren  
5. Button oder Tastatur-Trigger aktivieren  

Nach dem Start läuft das System kontinuierlich im Hintergrund.

---

## Screenshots

- TouchDesigner Network (Video-, Trigger- und Audio-Feedback-Logik)  
- Buffer- und Recording-Flow  
- Upload- und Weiterverarbeitungssektion  

*(Screenshots sind im Repository abgelegt)*

---

## Projektfazit

Der FunSaver ist ein leichtgewichtiges, performantes und erweiterbares End-to-End-System, das zeigt, wie interaktives Design, Hardware-Input und audiovisuelle Live-Software sinnvoll zusammenspielen können.
Er macht Spielmomente sichtbar – und hörbar erlebbar – genau in dem Moment, in dem sie entstehen, und trägt sie ohne Umwege ins Web.
