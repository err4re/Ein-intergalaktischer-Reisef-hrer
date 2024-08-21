# Ein-intergalaktischer-Reisef-hrer

# 1. Installation

Für die Installation empfehlen wir euch:
1.  [miniconda](https://docs.anaconda.com/miniconda/miniconda-install/) (*empfohlen*) oder [Anaconda](https://www.anaconda.com/download) (mit GUI "graphical user interface")
2.   [jupyter lab](https://jupyter.org/) (Editor)

Wer lieber seine Lieblings-IDE verwenden möchten kann das (auf eigene Gefahr hin ;)) gerne tun. Wir werden Python verwenden, weil dies in der Physik die mit Abstand am stärksten verbreitete und sehr mächtige Programmiersprache ist.

### Environment

Nachdem ihr miniconda oder Anaconda und damit :snake: installiert habt, ist es Zeit ein environment (virtuelle Umgebung) für unseren Kurs zu erstellen. Das könnt ihr in der GUI erledigen oder bequem im Terminal *(empfohlen)*, fragt uns gerne nach Hilfe.

Los geht's, öffnet das (miniconda oder Anaconda) Terminal und verwendet die folgenden Befehle. Ihr könnt das Terminal einfach in der Suchleiste suchen. Und dann:

`conda create -n akademie2024 python=3`

Hier erstellen wir eine Umgebung mit dem Namen `akademie2024` und verwenden in dieser Umgebung Python 3 (niemand will mehr Python 2 und so sind wir uns sicher, dass es nicht peinlich wird). Ihr könnte gerne auch einen anderen Namen als `akademie2024` verwenden, das liegt bei euch. Aber jetzt ist es wahrscheinlich zu spät :joy:

Kurzes Update:

`conda update conda`

Als nächstes aktivieren wir die neue Umgebung, das heißt wir wechseln in diese Umgebung:

`conda activate akademie2022`

Ihr solltet jetzt neben eurem Cursor so etwas wie `(akademie2022)` sehen. Dann kann es jetzt mit den interessanten packages (Erweiterung für Anaconda und/oder Python) los gehen.

Wir beginnen mit [Jupyter Lab](https://jupyter.org), einem Editor für :snake: (und viele andere Programmiersprachen), den ihr heute Vormittag schon gesehen habt. 

Jetzt Jupyter Lab installieren:

`conda install jupyterlab`

Stimmt jetzt bitte allen Abfragen zu zusätzlichen packages zu (und im weiteren Verlauf genauso :sweat_smile:). Ok das hat hoffentlich geklappt, ansonsten fragt bei uns nach.

Weiter geht es mit ein paar Python libraries (Bibliotheken mit nützlichen Funktionen, die wir nicht selber schreiben wollen und können :dizzy_face:). Für die Mathe:

`conda install numpy`

Für die Graphen:

`conda install matplotlib`

# 2. Erste Notebooks

Dann starten wir zum ersten Mal unser frisches Jupyter Lab:

`jupyter lab`

Hier könnt ihr jetzt ein neues Notebook erstellen, zum Beispiel unter **File>New>Notebook**. Schaut euch als erstes die Bibliothek `matplotlib` an, genaueres dazu [hier](https://matplotlib.org/).

Jetzt habt alles was ihr braucht um bei der Coding Demo mitzumachen oder sofort mit der Aufgabenliste zu starten :rocket:

### Aufgabenliste:

1. definiere eine lineare Funktion
2. plotte den Graphen dieser Funktion
3. gib dem Plot eine Überschrift und beschrifte die Achsen
4. definiere ein Potenzgesetz ($y = a \cdot x^b$) und erstelle einen analogen Plot
5. erstelle außerdem einen doppelt-logarithmischen Plot
6. erstelle einen interaktiven Plot für eine Potenzgesetz mit variablem Koeffizienten, das heißt der Koeffizient kann interaktiv verändert werden (z.B. mit Schiebereglern)

Zusätzliche Informationen und Beispiele zu `matplotlib` findet ihr [hier](https://matplotlib.org/stable/tutorials/index.html).

### Verständnisfragen:

1. Welche Steigung weist der Graph aus Aufgabe 5) auf? Warum?
2. Wie verändert sich der Graph aus Aufgabe 6) durch die Skalierung des Koeffizienten? (sehr cool, dass ihr den interaktiven Plot hinbekommen habt :raised_hands:)

# 3. Bestimmung der Erdbeschleunigung

Für die Auswertung unserer Daten brauchen wir (natürlich) noch eine weitere Bibliothek:

`conda install scipy`

Diese Bibliothek ist super nützlich und mega schnell! :fire: Differentialgleichungen lösen, integrieren und vieles mehr könnt ihr jetzt mit `scipy`. [Hier](https://scipy.org/) gibt es einen Überblick.

Wir wollen uns vor allem mit der Funktion [`curve_fit`](https://docs.scipy.org/doc/scipy/reference/generated/scipy.optimize.curve_fit.html) anfreunden, mehr dazu in der [Dokumentation](https://docs.scipy.org/doc/scipy/reference/generated/scipy.optimize.curve_fit.html). Eine Dokumentation ist eine Art Katalog aller Funktionen und Funktionalitäten, welche eine Bibliothek zur Verfügung stellt. Zum Glück ist `scipy` wirklich gut dokumentiert, sogar mit Beispielen (einfach ein bisschen scrollen).

Im wesentlichen sind die folgenden Schritte notwendig:
1. Bibliotheken importieren
2. Fit-Funktion definieren, also unser mathematisches Modell
3. Daten initialisieren, zum Beipsiel zwei Arrays
4. mit `curve_fit` die Parameter (z.B. Erdbeschleunigung und Widerstandsbeiwert) der Fit-Funktion an Daten anpassen
5. Ergebnis plotten
6. nachdenken, Modell oder Modelle überdenken, weiterdenken...

Zusammen kriegt ihr das hin :handshake:

Wer es bis hier geschafft hat, kann jetzt einen interaktiven Plot erstellen. Dieser enthält die Datenpunkte und einen Graphen mit interaktiven Parametern, welche z.B. über Schieberegler verändert werden können. Wie sensibel ist die Übereinstimmung zwischen Daten und Modell? Hättet ihr dieselben optimalen Parameter wie mit `scipy` gefunden?
