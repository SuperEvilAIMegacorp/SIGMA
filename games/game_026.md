# Quantum Chess

## Game Information
- **Genre**: Abstract Strategy
- **Players**: 2
- **Duration**: 20-30 minutes
- **Complexity**: 7/10 (Complex)

## Objective
Capture opponent's king, but pieces exist in quantum superposition.

## Components
- Chess-like board (8x8)
- 16 pieces per player (king, 3 nobles, 12 pawns)
- Quantum state trackers
- Probability dice (6-sided)

## Setup
1. Standard starting formation
2. Each player sets up on their side

## Rules
1. On your turn, declare a piece to move
2. Choose up to 3 possible destination squares
3. Roll probability die to determine actual destination:
   - 1-2: first choice
   - 3-4: second choice (if declared)
   - 5-6: third choice (if declared)
4. If fewer than 3 destinations declared, re-roll on higher numbers
5. Captures occur if you land on opponent's piece
6. King moves are always deterministic (no probability)

## Winning Condition
Capture opponent's king.

## Special Rules
- Pawns promote to nobles at far rank (not queens)
- Nobles move like queens
- You cannot declare impossible moves
- Some pieces have special abilities affecting probability
