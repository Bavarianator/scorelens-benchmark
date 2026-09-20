# ScoreLens Benchmark v3.1

**→ [Zur interaktiven Rangliste](https://bavarianator.github.io/scorelens-benchmark/)**

Ein absichtlich schwerer Test für Modelle, die Dartwürfe per Handykamera werten: 8.373 Bilder in 47 Kategorien.
Jede Kategorie macht echte, nie trainierte Dartfotos auf genau eine Weise schwer – Blickwinkel, Licht, Bildqualität –, dazu kommen
Kombinationen, unveränderte schwere Würfe und Fotos völlig fremder Boards.

| Platz | Modell | App-Wertung | … ohne AnyDarts | … nur AnyDarts-Fotos | Exakt im Rohbild | Training |
|---:|---|---:|---:|---:|---:|---|
| 1 | **dd9** | 55,2 % | 54,9 % | 55,8 % | 52,5 % | 112.834 Bilder: Copy-Paste enger Spitzen, fremde Boards |
| 2 | **dd8** | 43,7 % | 55,6 % | 9,0 % | 39,8 % | data6 komplett + 4.800 extra-harte Bilder, Start von dd6 |
| 3 | **dd7** | 43,5 % | 53,6 % | 14,0 % | 39,4 % | halbes data6 + 10.000 Roboflow-Bilder, Start von dd6 |
| 4 | **dd6** | 42,1 % | 52,5 % | 11,9 % | 37,2 % | 71.132 Bilder, Schrägsicht und Bildstörung kombiniert |
| 5 | **dd3** | 36,8 % | 41,4 % | 23,5 % | 29,2 % | dd2-Daten + 8.155 synthetische Schrägsichten |
| 6 | **dd5** | 33,6 % | 42,4 % | 7,8 % | 28,3 % | gleiche Daten wie dd4, 50 Epochen |
| 7 | **base** | 33,1 % | 29,7 % | 43,0 % | 21,9 % | dart-sense-Original (YOLOv8n), unser Ausgangsmodell |
| 8 | **dd1** | 31,6 % | 29,5 % | 37,5 % | 18,7 % | DeepDarts D1, 1.000 Bilder, Backbone eingefroren |
| 9 | **dd4** | 31,2 % | 40,4 % | 4,3 % | 27,5 % | 22.700 Bilder mit harten Fällen – in der App seit Beta 7 |
| 10 | **dd2** | 24,8 % | 27,3 % | 17,3 % | 19,1 % | D1 + D2, 5.536 Bilder |

**App-Wertung** bildet die zweistufige Erkennung der App nach: Erst muss das Modell das Board finden (vier der sechs Kalibrierpunkte,
Entzerrung auf 3 mm genau), dann im frontal entzerrten Ausschnitt jeden Dart richtig werten (etwa T20, S5, D16). Ein fehlender, ein
zusätzlicher oder ein falsch gewerteter Dart macht das ganze Bild falsch. **Exakt im Rohbild** ist die strengere Fassung ohne Entzerrung.
Alle Werte sind das Mittel über die Kategorien – jede zählt gleich viel.

**Zur Spalte „nur AnyDarts-Fotos":** Das sind echte Fotos eines anderen Boards mit anderen Darts. Bis dd8 kennt kein Modell diesen Aufbau –
dort zeigt die Spalte, wie gut ein Modell auf Fremdes überträgt (das Basismodell schlägt hier alle Feintunings). Ab dd9 stammt Trainingsmaterial
vom selben Aufbau; der Sprung dort ist deshalb kein Beleg für Fremdtauglichkeit. Den fairen Vergleich zeigt die Spalte „ohne AnyDarts".

Die Störungen hängen nur am Bildnamen, nicht am Zufall des Laufs: Jedes Modell sieht exakt dieselben Bilder, neue Modelle lassen sich
jederzeit fair ergänzen.

## Bildquellen

- Validierungsteil von [DeepDarts](https://github.com/wmcnally/deep-darts) (McNally et al., CVPRW 2021) – in keinem Training enthalten
- Testsatz von [AnyDarts](https://github.com/rg3rber/AnyDarts) – echte Fotos anderer Boards, Darts und Handys

Das Basismodell stammt aus [dart-sense](https://github.com/bnww/dart-sense).
