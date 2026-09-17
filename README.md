# Blüte

Ein Glücksrad, das sich merkt, was es zieht.

Du gibst Optionen ein, drehst, und das Rad entscheidet. Der Unterschied zu
anderen Rädern: Jedes Segment wächst nach außen, je öfter es gezogen wurde.
Nach zwanzig Drehs ist aus dem Kreis eine unregelmäßige Blüte geworden.

**Live:** https://erdinc55.github.io/gluecksrad/

## Die Idee dahinter

Das Rad ist gleichzeitig seine eigene Statistik. Ein separates Balkendiagramm
daneben brauchte es deshalb nicht.

Wichtig dabei: Die **Winkel** aller Segmente bleiben immer gleich groß. Bei acht
Optionen bekommt jede genau 45 Grad, egal wie oft sie schon dran war. Getroffen
wird nur über den Winkel — der Radius ist reine Anzeige. Das Rad sieht also
schief aus, ist aber komplett fair.

Der gestrichelte Kreis markiert den Radius, den ein Segment bei perfekt
gleichmäßiger Verteilung hätte. Bei wenigen Drehs zackt die Form wild darum
herum, mit mehr Drehs legt sie sich näher an den Kreis an. Man sieht dem Rad
also beim Ausgleichen zu.

## Was ich beim Bauen gelernt habe

Mein erster Gedanke war, zu einem zufälligen Winkel zu drehen und danach
abzulesen, welches Segment unter dem Zeiger steht. Das klingt gleichwertig, ist
es aber nicht — durch Rundungen verschieben sich die Wahrscheinlichkeiten
leicht, ohne dass man es merkt.

Jetzt läuft es andersherum: Erst wird der Gewinner gezogen, danach der Winkel
berechnet, der ihn unter den Zeiger bringt. Ziehung und Darstellung sind damit
sauber getrennt.

Die zweite Sache waren die Farben. Bei zwanzig Segmenten sieht eine feste
Farbliste schnell nach Bonbons aus. Ich berechne die Farben jetzt: Jede Option
springt im Farbkreis um 137,5 Grad weiter, den goldenen Winkel. Pflanzen ordnen
ihre Blätter nach demselben Winkel an, damit sie sich möglichst wenig
überdecken. Bei Farben sorgt das dafür, dass Nachbarsegmente immer weit
auseinanderliegen — bei drei Optionen genauso wie bei dreißig.

## Bedienung

Optionen lassen sich einzeln eintippen oder als Liste auf einmal einfügen, eine
pro Zeile. Die Anzahl ist nicht begrenzt.

Wird ein Segment schmaler als zwölf Grad, passt kein Text mehr hinein. Dann
zeigt es nur noch seine Nummer, die zur Liste daneben gehört. Unlesbar kleine
Schrift fand ich schlechter als gar keine.

Optionen und Auswertung bleiben im Browser gespeichert. Der Zurücksetzen-Knopf
löscht nur die Zählung, die Optionen bleiben stehen.

## Was drin steckt

Reines HTML, CSS und JavaScript, keine Bibliotheken.

- `index.html` — Aufbau
- `style.css` — Gestaltung
- `script.js` — Rad zeichnen, drehen, Statistik

Das Rad ist SVG, kein Canvas. So ist jedes Segment ein eigenes Element, das ich
einzeln einfärben und aufleuchten lassen kann.

## Selbst ausprobieren

Repository herunterladen und `index.html` im Browser öffnen. Kein Server nötig.

```
git clone https://github.com/Erdinc55/gluecksrad.git
```

Oben in `script.js` steht ein Block `KONFIG`. Dort lassen sich Drehdauer,
Umdrehungen und die Größe des Erwartungskreises verstellen.

## Was noch offen ist

- Die Auswertung liegt nur im eigenen Browser
- Gewichtete Optionen, bei denen manche wahrscheinlicher sind, wären der
  nächste logische Schritt — dann müssten die Winkel allerdings doch
  unterschiedlich groß werden
