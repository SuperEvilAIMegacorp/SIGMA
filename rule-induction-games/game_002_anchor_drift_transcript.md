# Anchor Drift - Game Transcripts

## Transcript 1: Introduction to Drift

**Turn 1**
- Red: "Placing at C3."
- *Board updates*

```
5 [ ][ ][ ][ ][ ]
4 [ ][ ][ ][ ][ ]
3 [ ][ ][R][ ][ ]
2 [ ][ ][ ][ ][ ]
1 [ ][ ][ ][ ][ ]
   A  B  C  D  E
```

**Turn 2**
- Blue: "Placing at C5."
- *Board updates*
- *Drift*: Red marker at C3 moves to C2
- Referee: "Red marker at C3 drifts south to C2, away from the blue marker."

```
5 [ ][ ][B][ ][ ]
4 [ ][ ][ ][ ][ ]
3 [ ][ ][ ][ ][ ]
2 [ ][ ][R][ ][ ]
1 [ ][ ][ ][ ][ ]
   A  B  C  D  E
```

- Red: "Wait, why did my marker move?"
- Referee: "After placement, enemy markers that aren't anchored drift away from the nearest enemy."

**Turn 3**
- Red: "Placing at B2."
- *Board updates*
- *Drift*: Blue marker at C5 moves to C6... wait, there is no C6.
- Referee: "Blue marker at C5 would drift north, but that's off the board. It stays at C5."

```
5 [ ][ ][B][ ][ ]
4 [ ][ ][ ][ ][ ]
3 [ ][ ][ ][ ][ ]
2 [ ][R][R][ ][ ]
1 [ ][ ][ ][ ][ ]
   A  B  C  D  E
```

**Turn 4**
- Blue: "Placing at D5."
- *Board updates*
- *Drift*: Red at C2 stays (anchored), Red at B2 drifts to A2

```
5 [ ][ ][B][B][ ]
4 [ ][ ][ ][ ][ ]
3 [ ][ ][ ][ ][ ]
2 [R][ ][R][ ][ ]
1 [ ][ ][ ][ ][ ]
   A  B  C  D  E
```

- Blue: "Why did B2 drift but not C2?"
- Referee: "C2 has a friendly neighbor at B2 (well, before B2 drifted). Let me recalculate... Actually, after B2 drifts to A2, C2 is no longer anchored. But drift happens simultaneously for all markers, so we check anchor status before any drifts occur."

---

## Transcript 2: Anchoring Mechanics

**Current State**:
```
5 [ ][ ][ ][ ][ ]
4 [ ][ ][ ][ ][ ]
3 [R][R][R][ ][ ]
2 [ ][R][ ][ ][ ]
1 [ ][ ][ ][ ][ ]
   A  B  C  D  E
```

**Turn**
- Blue: "Placing at B5."
- *Board updates*
- *Drift check*:
  - R@A3: Has neighbors at B3. Only 1 neighbor, not anchored. Drifts from A3 to A2.
  - R@B3: Has neighbors at A3, C3, B2. That's 3 neighbors - anchored. No drift.
  - R@C3: Has neighbor at B3. Only 1 neighbor, not anchored. Drifts from C3 to D3.
  - R@B2: Has neighbor at B3. Only 1 neighbor, not anchored. Drifts from B2 to B1.

```
5 [ ][B][ ][ ][ ]
4 [ ][ ][ ][ ][ ]
3 [ ][R][D][ ][ ]
2 [R][ ][ ][ ][ ]
1 [ ][R][ ][ ][ ]
   A  B  C  D  E
```

- Red: "So B3 didn't drift because it had 3 neighbors?"
- Referee: "Exactly. A marker needs 2 or more orthogonal neighbors to be anchored."

---

## Transcript 3: Capture Mechanics

**Current State**:
```
5 [ ][B][ ][ ][ ]
4 [ ][ ][ ][ ][ ]
3 [R][R][R][ ][ ]
2 [ ][R][ ][ ][ ]
1 [ ][ ][ ][ ][ ]
   A  B  C  D  E
```

**Turn**
- Red: "Placing at B4."
- *Board updates*
- *Drift*: Blue at B5 would drift to B6 (off board) or A5 or C5. Nearest enemy is at B4, so it drifts away... options are A5, C5, or stays.
- Referee: "Blue at B5 is adjacent to red at B4. It tries to drift away. Options: A5, C5. Let's say it drifts to C5."
- *New position*: Blue at C5
- *Check capture*: Blue at C5 is adjacent to... only B4. Not captured.

Actually, let me reconsider this scenario for a better capture example.

**Current State**:
```
5 [ ][ ][ ][ ][ ]
4 [ ][ ][ ][ ][ ]
3 [R][R][R][R][ ]
2 [ ][R][ ][ ][ ]
1 [ ][ ][ ][ ][ ]
   A  B  C  D  E
```

**Turn**
- Blue: "Placing at C5."
- *Board updates*
- *Drift*: Red markers check drift
  - R@B3 has neighbors A3, C3, B2 (3 neighbors) - anchored, no drift
  - Others may drift...

Let me create a clearer capture scenario:

**Current State**:
```
5 [ ][ ][B][ ][ ]
4 [ ][ ][ ][ ][ ]
3 [R][R][ ][R][ ]
2 [ ][R][ ][ ][ ]
1 [ ][ ][ ][ ][ ]
   A  B  C  D  E
```

**Turn**
- Red: "Placing at C4."
- *Board updates*
- *Drift*: Blue at C5 drifts away from C4. Can go to B5, D5, or stay at C5 if blocked.
- Referee: "Blue at C5 drifts to... let's say D5."

```
5 [ ][ ][ ][B][ ]
4 [ ][ ][R][ ][ ]
3 [R][R][ ][R][ ]
2 [ ][R][ ][ ][ ]
1 [ ][ ][ ][ ][ ]
   A  B  C  D  E
```

**Next Turn**
- Blue: "Placing at D4."
- *Board updates*
- *Drift*: R@D3 drifts away from D4. Can go to D2, E3, or C3.
- Referee: "Red at D3 drifts to... D2."

```
5 [ ][ ][ ][B][ ]
4 [ ][ ][R][B][ ]
3 [R][R][ ][ ][ ]
2 [ ][R][D][ ][ ]
1 [ ][ ][ ][ ][ ]
   A  B  C  D  E
```

**Next Turn**
- Red: "Placing at C3."
- *Board updates*
- *Drift*: Blue markers drift
  - B@D5 drifts from C3, nearest is C3, drifts to E5 or stays
  - B@D4 drifts from C3, drifts to E4 or stays

Let me simplify this and create a clearer capture scenario:

**Current State**:
```
5 [ ][ ][ ][ ][ ]
4 [ ][R][R][R][ ]
3 [ ][R][B][R][ ]
2 [ ][R][R][R][ ]
1 [ ][ ][ ][ ][ ]
   A  B  C  D  E
```

**Turn**
- Blue: "Placing at A3."
- *Board updates*
- *Drift*: Blue at C3 has red neighbors at B3, C4, D3, C2 (4 neighbors). Wait, blue isn't drifting, red is.
- Referee: "Actually, red markers would drift from blue placement. But most reds here are anchored with 2+ neighbors."

This is getting complex. Let me create a simpler, clearer capture:

**Current State**:
```
5 [ ][ ][B][ ][ ]
4 [ ][R][R][R][ ]
3 [ ][ ][R][ ][ ]
2 [ ][ ][ ][ ][ ]
1 [ ][ ][ ][ ][ ]
   A  B  C  D  E
```

**Turn**
- Red: "Placing at C2."
- *Board updates*
- *Drift*: Blue at C5 drifts toward... wait, away from nearest enemy.
- Nearest reds: C4 is distance 1, others farther.
- Blue drifts from C5 away from C4: options are B5, D5.
- Referee: "Blue drifts to D5."

```
5 [ ][ ][ ][B][ ]
4 [ ][R][R][R][ ]
3 [ ][ ][R][ ][ ]
2 [ ][ ][R][ ][ ]
1 [ ][ ][ ][ ][ ]
   A  B  C  D  E
```

**Turn**
- Red: "Placing at D3."
- *Board updates*
- *Drift*: Blue at D5 drifts away. Nearest red is D4 (distance 1).
- Drifts to E5 or D6(no) or C5.
- Referee: "Blue drifts to E5."

```
5 [ ][ ][ ][ ][B]
4 [ ][R][R][R][ ]
3 [ ][ ][R][R][ ]
2 [ ][ ][R][ ][ ]
1 [ ][ ][ ][ ][ ]
   A  B  C  D  E
```

**Turn**
- Red: "Placing at E4."
- *Board updates*
- *Drift*: Blue at E5 drifts away from E4.
- Can only go to D5 or E6(no).
- Drifts to D5.
- *Check capture*: Blue at D5 is now adjacent to D4, E4. Only 2 reds. Not captured (needs 3+).

```
5 [ ][ ][ ][B][ ]
4 [ ][R][R][R][R]
3 [ ][ ][R][R][ ]
2 [ ][ ][R][ ][ ]
1 [ ][ ][ ][ ][ ]
   A  B  C  D  E
```

**Turn**
- Red: "Placing at D2."
- *Board updates*
- *Drift*: Blue at D5 drifts. Nearest reds: D4 distance 1, E4 distance 1, D3 distance 2.
- Drifts away from D4/E4 cluster. Best direction: C5 or back to E5?
- Referee: "Blue drifts to C5."

```
5 [ ][ ][B][ ][ ]
4 [ ][R][R][R][R]
3 [ ][ ][R][R][ ]
2 [ ][ ][R][D][ ]
1 [ ][ ][ ][ ][ ]
   A  B  C  D  E
```

**Turn**
- Red: "Placing at B5."
- *Board updates*
- *Drift*: Blue at C5 drifts away from B5 (distance 1).
- Can go to D5, C6(no), B5(occupied).
- Drifts to D5.
- *Check capture*: Blue at D5 adjacent to D4, E4, D3. That's 3 red markers!
- Referee: "Blue marker captured!"

```
5 [ ][R][ ][ ][ ]
4 [ ][R][R][R][R]
3 [ ][ ][R][R][ ]
2 [ ][ ][R][D][ ]
1 [ ][ ][ ][ ][ ]
   A  B  C  D  E
```

---

## Summary

From these transcripts, we can infer:

1. **Drift rule**: After placement, enemy markers drift away from nearest enemy
2. **Anchor rule**: Markers with 2+ orthogonal neighbors don't drift
3. **Capture rule**: If marker drifts adjacent to 3+ enemies, it's captured
4. **Board edges**: Can't drift off board
5. **Distance calculation**: Drift is away from nearest enemy marker
