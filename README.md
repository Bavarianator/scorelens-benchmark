# ScoreLens Benchmark v3.1

**→ [Zur interaktiven Rangliste](https://bavarianator.github.io/scorelens-benchmark/)**

Ein absichtlich schwerer Test für Modelle, die Dartwürfe per Handykamera werten: 8.373 Bilder in 47 Kategorien.
Jede Kategorie macht echte, nie trainierte Dartfotos auf genau eine Weise schwer – Blickwinkel, Licht, Bildqualität –, dazu kommen
Kombinationen, unveränderte schwere Würfe und Fotos völlig fremder Boards.

| Platz | Modell | App-Wertung | Exakt im Rohbild | App-Wertung auf fremden Boards | Training |
|---:|---|---:|---:|---:|---|
| 1 | **dd8** | 43,7 % | 39,8 % | 9,0 % | data6 komplett + 4.800 extra-harte Bilder, Start von dd6 |
| 2 | **dd7** | 43,5 % | 39,4 % | 14,0 % | halbes data6 + 10.000 Roboflow-Bilder, Start von dd6 |
| 3 | **dd6** | 42,1 % | 37,2 % | 11,9 % | 71.132 Bilder, Schrägsicht und Bildstörung kombiniert |
| 4 | **dd3** | 36,8 % | 29,2 % | 23,5 % | dd2-Daten + 8.155 synthetische Schrägsichten |
| 5 | **dd5** | 33,6 % | 28,3 % | 7,8 % | gleiche Daten wie dd4, 50 Epochen |
| 6 | **base** | 33,1 % | 21,9 % | 43,0 % | dart-sense-Original (YOLOv8n), unser Ausgangsmodell |
| 7 | **dd1** | 31,6 % | 18,7 % | 37,5 % | DeepDarts D1, 1.000 Bilder, Backbone eingefroren |
| 8 | **dd4** | 31,2 % | 27,5 % | 4,3 % | 22.700 Bilder mit harten Fällen – in der App seit Beta 7 |
| 9 | **dd2** | 24,8 % | 19,1 % | 17,3 % | D1 + D2, 5.536 Bilder |

**App-Wertung** bildet die zweistufige Erkennung der App nach: Erst muss das Modell das Board finden (vier der sechs Kalibrierpunkte,
Entzerrung auf 3 mm genau), dann im frontal entzerrten Ausschnitt jeden Dart richtig werten (etwa T20, S5, D16). Ein fehlender, ein
zusätzlicher oder ein falsch gewerteter Dart macht das ganze Bild falsch. **Exakt im Rohbild** ist die strengere Fassung ohne Entzerrung.
Alle Werte sind das Mittel über die Kategorien – jede zählt gleich viel.

Die Störungen hängen nur am Bildnamen, nicht am Zufall des Laufs: Jedes Modell sieht exakt dieselben Bilder, neue Modelle lassen sich
jederzeit fair ergänzen.

## Bildquellen

- Validierungsteil von [DeepDarts](https://github.com/wmcnally/deep-darts) (McNally et al., CVPRW 2021) – in keinem Training enthalten
- Testsatz von [AnyDarts](https://github.com/rg3rber/AnyDarts) – echte Fotos anderer Boards, Darts und Handys

Das Basismodell stammt aus [dart-sense](https://github.com/bnww/dart-sense).
