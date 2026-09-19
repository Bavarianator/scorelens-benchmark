# ScoreLens Benchmark v3

**→ [Zur interaktiven Rangliste](https://bavarianator.github.io/scorelens-benchmark/)**

Ein absichtlich schwerer Test für Modelle, die Dartwürfe per Handykamera werten: 8.373 Bilder in 47 Kategorien.
Jede Kategorie macht echte, nie trainierte Dartfotos auf genau eine Weise schwer – Blickwinkel, Licht, Bildqualität –, dazu kommen
Kombinationen, unveränderte schwere Würfe und Fotos völlig fremder Boards.

| Platz | Modell | Exakt gewertet | Spitzen gefunden | Exakt auf fremden Boards | Training |
|---:|---|---:|---:|---:|---|
| 1 | **dd8** | 39,8 % | 63,9 % | 12,1 % | data6 komplett + 4.800 extra-harte Bilder, Start von dd6 |
| 2 | **dd7** | 39,4 % | 62,3 % | 17,0 % | halbes data6 + 10.000 Roboflow-Bilder, Start von dd6 |
| 3 | **dd6** | 37,2 % | 62,5 % | 12,4 % | 71.132 Bilder, Schrägsicht und Bildstörung kombiniert |
| 4 | **dd3** | 29,2 % | 57,1 % | 9,2 % | dd2-Daten + 8.155 synthetische Schrägsichten |
| 5 | **dd5** | 28,3 % | 57,1 % | 2,8 % | gleiche Daten wie dd4, 50 Epochen |
| 6 | **dd4** | 27,5 % | 55,6 % | 4,9 % | 22.700 Bilder mit harten Fällen – in der App seit Beta 7 |
| 7 | **base** | 21,9 % | 54,2 % | 13,6 % | dart-sense-Original (YOLOv8n), unser Ausgangsmodell |
| 8 | **dd2** | 19,1 % | 50,8 % | 4,2 % | D1 + D2, 5.536 Bilder |
| 9 | **dd1** | 18,7 % | 51,9 % | 5,6 % | DeepDarts D1, 1.000 Bilder, Backbone eingefroren |

**Exakt gewertet** heißt: Das Modell findet alle vier Kalibrierpunkte des Boards, und jeder Dart im Bild bekommt die richtige Wertung
(etwa T20, S5, D16). Ein fehlender, ein zusätzlicher oder ein falsch gewerteter Dart macht das ganze Bild falsch. Alle Werte sind das
Mittel über die Kategorien – jede zählt gleich viel.

Die Störungen hängen nur am Bildnamen, nicht am Zufall des Laufs: Jedes Modell sieht exakt dieselben Bilder, neue Modelle lassen sich
jederzeit fair ergänzen.

## Bildquellen

- Validierungsteil von [DeepDarts](https://github.com/wmcnally/deep-darts) (McNally et al., CVPRW 2021) – in keinem Training enthalten
- Testsatz von [AnyDarts](https://github.com/rg3rber/AnyDarts) – echte Fotos anderer Boards, Darts und Handys

Das Basismodell stammt aus [dart-sense](https://github.com/bnww/dart-sense).
