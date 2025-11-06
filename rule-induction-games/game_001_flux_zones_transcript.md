# Flux Zones - Game Transcripts

## Transcript 1: Tutorial Game

**Setup**: Empty 5x5 grid, coordinates A-E (columns) and 1-5 (rows)

**Turn 1**
- Red: "I'll place my marker at C3."
- *Board updates*: Red marker appears at C3

```
5 [ ][ ][ ][ ][ ]
4 [ ][ ][ ][ ][ ]
3 [ ][ ][R][ ][ ]
2 [ ][ ][ ][ ][ ]
1 [ ][ ][ ][ ][ ]
   A  B  C  D  E
```

**Turn 2**
- Blue: "I'll place at C4."
- *Board updates*: Blue marker appears at C4

```
5 [ ][ ][ ][ ][ ]
4 [ ][ ][B][ ][ ]
3 [ ][ ][R][ ][ ]
2 [ ][ ][ ][ ][ ]
1 [ ][ ][ ][ ][ ]
   A  B  C  D  E
```

**Turn 3**
- Red: "I'll place at E3."
- Referee: "Illegal move. You need to place adjacent to one of your existing markers."
- Red: "Oh, then I'll place at D3 instead."
- *Board updates*: Red marker appears at D3

```
5 [ ][ ][ ][ ][ ]
4 [ ][ ][B][ ][ ]
3 [ ][ ][R][R][ ]
2 [ ][ ][ ][ ][ ]
1 [ ][ ][ ][ ][ ]
   A  B  C  D  E
```

**Turn 4**
- Blue: "I'll place at B2."
- Referee: "Illegal move. Must be adjacent to your markers."
- Blue: "Right. I'll place at B4 then."
- *Board updates*: Blue marker appears at B4

```
5 [ ][ ][ ][ ][ ]
4 [ ][B][B][ ][ ]
3 [ ][ ][R][R][ ]
2 [ ][ ][ ][ ][ ]
1 [ ][ ][ ][ ][ ]
   A  B  C  D  E
```

**Turn 5**
- Red: "Placing at C2."
- *Board updates*: Red marker appears at C2

```
5 [ ][ ][ ][ ][ ]
4 [ ][B][B][ ][ ]
3 [ ][ ][R][R][ ]
2 [ ][ ][R][ ][ ]
1 [ ][ ][ ][ ][ ]
   A  B  C  D  E
```

**Turn 6**
- Blue: "Placing at D4."
- *Board updates*: Blue marker appears at D4

```
5 [ ][ ][ ][ ][ ]
4 [ ][B][B][B][ ]
3 [ ][ ][R][R][ ]
2 [ ][ ][R][ ][ ]
1 [ ][ ][ ][ ][ ]
   A  B  C  D  E
```

**Turn 7**
- Red: "Placing at B3."
- *Board updates*: Red marker appears at B3
- *Capture*: Blue marker at C4 is removed
- Referee: "Red captures blue at C4."

```
5 [ ][ ][ ][ ][ ]
4 [ ][B][ ][B][ ]
3 [ ][R][R][R][ ]
2 [ ][ ][R][ ][ ]
1 [ ][ ][ ][ ][ ]
   A  B  C  D  E
```

- Blue: "Wait, why was my C4 captured?"
- Referee: "After Red placed at B3, the red marker at C3 had 3 adjacent red markers (B3, C2, D3). Blue at C4 had 0 adjacent blue markers. The difference was 3, which triggers capture."

**Turn 8**
- Blue: "Placing at D5."
- *Board updates*: Blue marker appears at D5

```
5 [ ][ ][ ][B][ ]
4 [ ][B][ ][B][ ]
3 [ ][R][R][R][ ]
2 [ ][ ][R][ ][ ]
1 [ ][ ][ ][ ][ ]
   A  B  C  D  E
```

**Turn 9**
- Red: "Placing at E3."
- *Board updates*: Red marker appears at E3

```
5 [ ][ ][ ][B][ ]
4 [ ][B][ ][B][ ]
3 [ ][R][R][R][R]
2 [ ][ ][R][ ][ ]
1 [ ][ ][ ][ ][ ]
   A  B  C  D  E
```

**Turn 10**
- Blue: "Placing at C5."
- *Board updates*: Blue marker appears at C5
- *Capture*: Blue marker at B4 is removed
- Blue: "Wait, I just captured my own marker?!"
- Referee: "No, that was Red's capture. When you placed at C5, it changed the counts. Let me explain: Blue at B4 had 1 adjacent blue (at C5). Red at C3 has 3 adjacent reds (B3, C2, D3). Since 3 >= 1+2, Red captures Blue at B4."

```
5 [ ][ ][B][B][ ]
4 [ ][ ][ ][B][ ]
3 [ ][R][R][R][R]
2 [ ][ ][R][ ][ ]
1 [ ][ ][ ][ ][ ]
   A  B  C  D  E
```

---

## Transcript 2: Illegal Move Examples

**Turn 1**
- Red: "Placing at A1."
- *Board updates*

**Turn 2**
- Blue: "I'll place at B2."
- Referee: "Legal."
- *Board updates*

**Turn 3**
- Red: "Placing at A3."
- Referee: "Illegal - must be adjacent to your existing marker at A1."
- Red: "Can I place at B1?"
- Referee: "Let me check adjacency... B1 shares an edge with A1. Yes, legal."
- Red: "Okay, placing at B1."
- *Board updates*

**Turn 4**
- Blue: "Placing at C3."
- Referee: "Illegal - C3 is diagonal from B2, not edge-adjacent."
- Blue: "What about C2?"
- Referee: "C2 shares an edge with B2. Legal."
- Blue: "Placing at C2."
- *Board updates*

---

## Transcript 3: Capture Mechanics

**Current State**:
```
5 [ ][ ][ ][ ][ ]
4 [ ][ ][R][R][ ]
3 [B][B][R][ ][ ]
2 [ ][B][ ][ ][ ]
1 [ ][ ][ ][ ][ ]
   A  B  C  D  E
```

**Turn**
- Red: "Placing at C2."
- *Board updates*
- *Capture*: Blue at B2 removed
- Referee: "Red at C3 now has 3 adjacent reds (C2, C4, D4). Blue at B2 has 1 adjacent blue (B3). Difference is 2, so capture occurs. Blue at B2 is removed."

**Current State**:
```
5 [ ][ ][ ][ ][ ]
4 [ ][ ][R][R][ ]
3 [B][B][R][ ][ ]
2 [ ][ ][R][ ][ ]
1 [ ][ ][ ][ ][ ]
   A  B  C  D  E
```

- Blue: "Wait, why wasn't A3 captured too? Red at C3 also has 3 adjacent reds now."
- Referee: "A3 is diagonal from C3, not orthogonally adjacent. Captures only check markers that share an edge, not corners."

---

## Transcript 4: Edge Case - Cascade Discussion

**Current State**:
```
5 [ ][ ][ ][ ][ ]
4 [ ][R][B][R][ ]
3 [ ][R][R][R][ ]
2 [ ][ ][R][ ][ ]
1 [ ][ ][ ][ ][ ]
   A  B  C  D  E
```

**Turn**
- Red: "Placing at C5."
- *Board updates*
- *Capture*: Blue at C4 removed

**New State**:
```
5 [ ][ ][R][ ][ ]
4 [ ][R][ ][R][ ]
3 [ ][R][R][R][ ]
2 [ ][ ][R][ ][ ]
1 [ ][ ][ ][ ][ ]
   A  B  C  D  E
```

- Red: "Now that C4 is gone, does the red at C3 get recalculated?"
- Referee: "Yes, all markers recalculate their adjacent counts after captures."
- Red: "So C3 now has 4 adjacent reds (B3, C2, C5, D3). Do any new captures happen?"
- Referee: "No. Captures only happen immediately after placement, not from the cascading count changes."

---

## Transcript 5: Multiple Captures

**Current State**:
```
5 [ ][ ][ ][ ][ ]
4 [ ][B][ ][B][ ]
3 [ ][R][R][R][ ]
2 [ ][ ][R][ ][ ]
1 [ ][ ][ ][ ][ ]
   A  B  C  D  E
```

**Turn**
- Red: "Placing at C4."
- *Board updates*
- *Captures*: Blue at B4 removed, Blue at D4 removed
- Referee: "Red at C3 has 3 adjacent reds (B3, C2, C4, D3). Both B4 and D4 are orthogonally adjacent to C3, and both have 0 adjacent blues. 3 >= 0+2 for both, so both are captured."

**New State**:
```
5 [ ][ ][ ][ ][ ]
4 [ ][ ][R][ ][ ]
3 [ ][R][R][R][ ]
2 [ ][ ][R][ ][ ]
1 [ ][ ][ ][ ][ ]
   A  B  C  D  E
```

---

## Transcript 6: Corner Constraints

**Turn 1**
- Red: "Placing at A1."

**Turn 2**
- Blue: "Placing at E5."

**Turn 3**
- Red: "Placing at B1."

**Turn 4**
- Blue: "Placing at E4."

**Turn 5**
- Red: "Placing at A2."

**Current State**:
```
5 [ ][ ][ ][ ][B]
4 [ ][ ][ ][ ][B]
3 [ ][ ][ ][ ][ ]
2 [R][ ][ ][ ][ ]
1 [R][R][ ][ ][ ]
   A  B  C  D  E
```

**Turn 6**
- Blue: "Placing at D5."
- Referee: "Red at A1 has 2 adjacent reds (B1, A2). Blue at E5 has 1 adjacent blue (E4). But E5 is not orthogonally adjacent to A1, so no capture check even happens. If it were adjacent, the difference would be 1, which is less than 2, so no capture anyway."

**Turn 7**
- Red: "Placing at B2."
- *Board updates*

**Current State**:
```
5 [ ][ ][ ][B][B]
4 [ ][ ][ ][ ][B]
3 [ ][ ][ ][ ][ ]
2 [R][R][ ][ ][ ]
1 [R][R][ ][ ][ ]
   A  B  C  D  E
```

- Blue: "So red at A1 now has 3 neighbors (A2, B1, B2). That's the maximum it can have in the corner, right?"
- Referee: "Correct. Corner positions can only have at most 3 adjacent cells."

---

## Transcript 7: Win Condition

**Current State**:
```
5 [ ][ ][ ][ ][ ]
4 [ ][ ][ ][ ][ ]
3 [ ][R][R][R][ ]
2 [ ][ ][R][ ][ ]
1 [ ][ ][B][ ][ ]
   A  B  C  D  E
```

**Turn**
- Red: "Placing at C1."
- *Board updates*
- *Capture*: Blue at C1 removed (wait, Red just placed there...)
- Referee: "Actually, let me recalculate. Red places at C1. Red at C2 now has 3 adjacent reds (C1, C3, D2... wait, where's D2? Let me recount."

**Correct State**:
```
5 [ ][ ][ ][ ][ ]
4 [ ][ ][ ][ ][ ]
3 [ ][R][R][R][ ]
2 [ ][ ][R][ ][ ]
1 [ ][ ][B][ ][ ]
   A  B  C  D  E
```

**Turn**
- Red: "Placing at C1."
- Referee: "C1 is occupied by Blue. Illegal move."
- Red: "Oh! Placing at B2."
- *Board updates*

```
5 [ ][ ][ ][ ][ ]
4 [ ][ ][ ][ ][ ]
3 [ ][R][R][R][ ]
2 [ ][R][R][ ][ ]
1 [ ][ ][B][ ][ ]
   A  B  C  D  E
```

**Turn**
- Blue: "Placing at D1."
- *Board updates*

```
5 [ ][ ][ ][ ][ ]
4 [ ][ ][ ][ ][ ]
3 [ ][R][R][R][ ]
2 [ ][R][R][ ][ ]
1 [ ][ ][B][B][ ]
   A  B  C  D  E
```

**Turn**
- Red: "Placing at C1."
- *Board updates*
- *Capture*: Blue at C1 captured
- Referee: "Red at C2 has 4 adjacent reds. Blue at C1 has 1 adjacent blue. 4 >= 1+2, so Blue at C1 captured."

```
5 [ ][ ][ ][ ][ ]
4 [ ][ ][ ][ ][ ]
3 [ ][R][R][R][ ]
2 [ ][R][R][ ][ ]
1 [ ][ ][R][B][ ]
   A  B  C  D  E
```

**Turn**
- Blue: "I need to place adjacent to D1... Placing at D2."
- *Board updates*

```
5 [ ][ ][ ][ ][ ]
4 [ ][ ][ ][ ][ ]
3 [ ][R][R][R][ ]
2 [ ][R][R][B][ ]
1 [ ][ ][R][B][ ]
   A  B  C  D  E
```

**Turn**
- Red: "Placing at D3."
- *Board updates*
- *Capture*: Blue at D2 captured

```
5 [ ][ ][ ][ ][ ]
4 [ ][ ][ ][ ][ ]
3 [ ][R][R][R][ ]
2 [ ][R][R][ ][ ]
1 [ ][ ][R][B][ ]
   A  B  C  D  E
```

**Turn**
- Blue: "I have to place adjacent to D1... but C1, D2, and E1 are either occupied or captured. Can I place at E2?"
- Referee: "E2 is not adjacent to D1. You have no legal moves."
- Referee: "Red wins - Blue has no legal placement moves."

---

## Summary of Observations

From these transcripts, we can infer:

1. **Placement rules**: Must be adjacent (edge, not corner) to existing markers, except first move
2. **Adjacency types**:
   - Placement checks: orthogonal only (edge-sharing)
   - "Count" calculations: all 8 neighbors (orthogonal + diagonal)
   - Capture checks: orthogonal only
3. **Capture rule**: Requires difference of ≥2 in adjacent marker counts
4. **Capture direction**: Only orthogonally adjacent enemies are captured
5. **Multiple captures**: Can capture all qualifying adjacent enemies simultaneously
6. **Cascade**: Counts update after captures, but don't trigger new captures
7. **Win conditions**: No enemy markers left OR enemy has no legal moves
8. **Board limits**: Corner/edge positions limit maximum neighbor counts
