# Resonance - Game Transcripts

## Transcript 1: Resonance Values

**Turn 1**
- Red: "I'll place at D4."
- *Board*: Red at D4
- Referee: "Red D4 resonance: 0.0 (no friendly markers)"

**Turn 2**
- Blue: "A1 for me."
- *Board*: Blue at A1
- Referee: "Blue A1 resonance: 0.0"

**Turn 3**
- Red: "D5, next to my D4."
- *Board*: Red at D5
- Referee: "Red D4 resonance: 1.0 (distance 1 to D5). Red D5 resonance: 1.0"

**Turn 4**
- Blue: "What are these resonance numbers?"
- Referee: "Continue playing."
- Blue: "I'll place B1."
- Referee: "Blue A1 resonance: 1.0. Blue B1 resonance: 1.0"

**Turn 5**
- Red: "E4 for me."
- Referee: "Red D4 resonance: 1.5 (1.0 from D5 + 0.5 from E4 at distance 2)"
- Red: "Oh! It's based on distance to friendly markers."

---

## Transcript 2: Instability

**Turn 8**
- Red: "I'll place at A7, far from my cluster."
- *Board*: Red at A7
- Referee: "Red A7 resonance: 0.27 (sum of 1/distance to other red markers)"
- Referee: "Resonance below 1.0. Marker unstable - removed!"
- *Board*: Red at A7 removed
- Red: "It disappeared!"

**Turn 9**
- Blue: "So we need to stay close to our other markers?"
- Red: "Looks like markers need at least 1.0 resonance to survive."

---

## Transcript 3: Destabilization Capture

**Setup**: Blue has isolated marker at C3 with resonance 1.3

**Turn 15**
- Red: "Blue's C3 marker looks weak. Let me place at B2."
- *Board*: Red at B2
- Referee: "Red B2 placed within distance 2 of Blue C3 (distance: 1.4). Blue C3 resonance: 1.3"
- Referee: "Destabilization capture! Blue C3 removed."
- Blue: "What? I had resonance above 1.0!"
- Red: "Maybe there's a different threshold for captures?"

**Turn 16**
- Blue: "So I need resonance above 1.5 to be safe from nearby enemy placements?"
- Red: "Within distance 2, it seems."

---

## Transcript 4: Manhattan Distance

**Setup**: Red at D4, E5 (distance calculation test)

**Turn 20**
- Blue: "How is distance calculated? D4 to E5 looks diagonal."
- Red: "The referee said 'manhattan distance' earlier."
- Blue: "So D4 to E5 is |4-5| + |4-5| = 2, not diagonal 1?"
- Referee: "Correct. Manhattan distance counts horizontal + vertical steps."

**Turn 21**
- Red: "That means D4 to E5 contributes 0.5 to resonance (1/2)."
- Blue: "And D4 to F4 would be distance 2, also 0.5."

---

## Transcript 5: Cluster Strategy

**Setup**: Mid-game tactical positioning

**Turn 28**
- Red: "I'll build a tight cluster at E4, E5, F4, F5."
- *Board*: Red 4-marker cluster
- Referee: "Resonances: E4=3.0, E5=3.0, F4=3.0, F5=3.0"
- Red: "High resonance from close proximity."

**Turn 29**
- Blue: "But my markers at B2, C3, D4 are more spread out."
- Referee: "Blue B2 resonance: 1.8, C3: 2.0, D4: 1.8"
- Blue: "Lower but still stable."

**Turn 30**
- Red: "I'll place at D5, within distance 2 of your D4."
- Referee: "Blue D4 resonance 1.8 > 1.5 but Red D5 is distance 1 away."
- Referee: "Blue D4 captured!"
- Blue: "The distance matters for the 1.5 threshold?"
- Red: "Seems like it. Within distance 2 and under 1.5 resonance."
