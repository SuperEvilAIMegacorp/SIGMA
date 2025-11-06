# Template Structure for Rule Induction Games

## Overview

I've created a complete template system for building 100 intentional rule-induction games. Here's what's included:

## Files Created

### 1. `DESIGN.md` - Design Philosophy & Specification
- **Purpose**: Documents the principles behind game design for rule induction
- **Key sections**:
  - Novel mechanics that avoid training data contamination
  - Rule complexity dimensions (not "easy/medium/hard" but compositional depth)
  - Game categories (grid, graph, state transformation, etc.)
  - Validation criteria for each game
  - Mechanics to explore (flux, contagion, anchoring, etc.)

### 2. `game_001_flux_zones.yaml` - Structured Game Definition
- **Purpose**: Formal, machine-readable game specification
- **Key sections**:
  - **State space**: Board geometry, piece properties, player structure
  - **Formal rules**: Each rule with ID, priority, conditions, actions, effects
  - **Rule interactions**: How rules combine (enabling, cascading, modifying)
  - **Natural language explanations**: Human-readable versions of each rule
  - **Edge cases**: Corner cases with questions and answers
  - **Example states**: Board positions at various game stages
  - **Induction difficulty metrics**: What makes this hard to infer

### 3. `game_001_flux_zones_transcript.md` - Natural Language Gameplay
- **Purpose**: What an LLM would see when doing rule induction
- **Key sections**:
  - **Transcript 1**: Tutorial game showing basic mechanics
  - **Transcript 2**: Illegal move examples (shows boundaries)
  - **Transcript 3**: Capture mechanics in detail
  - **Transcript 4**: Edge case - cascade discussions
  - **Transcript 5**: Multiple simultaneous captures
  - **Transcript 6**: Corner/edge constraints
  - **Transcript 7**: Win condition example
  - **Summary**: What can be inferred from observations

## Structure Highlights

### The YAML Format Provides:

**Formal Rule Representation**
```yaml
rules:
  placement:
    - id: "R_PLACE_1"
      priority: 1
      condition: "cell is empty AND (board is empty OR cell is orthogonally adjacent to own marker)"
      action: "place marker on cell"
      effect: "marker added to board, all flux charges recalculated"
      exceptions: []
```

**Rule Interactions (Compositional)**
```yaml
interactions:
  - rules: ["R_PLACE_1", "R_FLUX_1"]
    type: "enabling"
    description: "Placement triggers flux recalculation for all markers"

  - rules: ["R_CAPTURE_1", "R_FLUX_1"]
    type: "cascading"
    description: "Captures change flux charges which may trigger more captures"
```

**Edge Cases (Systematic)**
```yaml
edge_cases:
  - scenario: "Board edge flux"
    question: "Does a marker at the board edge have lower maximum flux?"
    answer: "Yes. An A1 corner marker has max flux of 3..."
    involved_rules: ["R_FLUX_1"]
```

### The Transcript Format Provides:

**Natural Language Game Play**
```
Turn 7:
- Red: "Placing at B3."
- *Board updates*: Red marker appears at B3
- *Capture*: Blue marker at C4 is removed
- Referee: "Red captures blue at C4."

- Blue: "Wait, why was my C4 captured?"
- Referee: "After Red placed at B3, the red marker at C3 had 3 adjacent
  red markers (B3, C2, D3). Blue at C4 had 0 adjacent blue markers.
  The difference was 3, which triggers capture."
```

**Illegal Move Examples**
```
- Red: "I'll place at E3."
- Referee: "Illegal move. You need to place adjacent to one of your existing markers."
- Red: "Oh, then I'll place at D3 instead."
```

**Rule Discovery Through Conversation**
```
- Blue: "Wait, why wasn't A3 captured too? Red at C3 also has 3 adjacent reds now."
- Referee: "A3 is diagonal from C3, not orthogonally adjacent. Captures only
  check markers that share an edge, not corners."
```

## Key Design Features of "Flux Zones" Example

### 1. Novel Mechanics
- **Flux charge**: Not in standard games (not chess, checkers, go, etc.)
- **Asymmetric adjacency**: Placement uses orthogonal, flux counts all 8, captures check orthogonal
- **Threshold capture**: Requires specific difference (≥2), not just any difference

### 2. Rule Interactions
- Placement → triggers flux recalculation → enables captures
- Captures → change flux values → affect future capture potential
- First move exception creates special case

### 3. Edge Cases Built In
- Board corners/edges limit maximum flux
- Diagonal vs orthogonal adjacency confusion
- Cascade effects don't chain
- Multiple simultaneous captures

### 4. Inference Challenges
An LLM would need to discover:
- **Three different adjacency rules** (placement, flux calc, capture checking)
- **The threshold of 2** for captures (hard to infer from few examples)
- **First move exemption** (only visible on turn 1)
- **Orthogonal vs diagonal** distinction in different contexts
- **No cascade chains** (negative rule - what doesn't happen)

### 5. Progressive Revelation
- Transcript 1: Basic placement and adjacency
- Transcript 2: Illegal moves show boundaries
- Transcript 3: Capture mechanics introduced
- Transcript 4: Cascade limitations shown
- Transcript 5: Multiple captures
- Transcript 6: Edge constraints
- Transcript 7: Win conditions

## What This Enables

### For Game Generation (100 games)
- **Systematic variation**: Change board size, piece properties, rule counts
- **Novel mechanics**: Flux, contagion, anchoring, phasing, resonance, etc.
- **Compositional complexity**: Rules that interact in non-obvious ways
- **Formal specification**: Can be simulated/verified programmatically

### For Scenario Generation
- YAML provides formal rules → can simulate games
- Generate legal/illegal move examples systematically
- Create edge cases methodically
- Build progressive difficulty transcripts

### For LLM Testing
- **Input**: Transcripts only (no rule descriptions)
- **Task**: Infer the rules from observations
- **Evaluation**:
  - Can it predict legal moves?
  - Can it explain why moves are illegal?
  - Can it identify edge cases?
  - Can it handle novel states (generalization)?

## Next Steps

Before generating all 100 games, I want to confirm:

1. **Is this structure what you envisioned?**
   - YAML for formal rules
   - Transcripts for natural language scenarios
   - Both together provide complete game definition

2. **Is the transcript style right?**
   - Player dialogue
   - Referee explanations
   - Illegal move discussions
   - Visual board states

3. **Is "Flux Zones" a good example?**
   - Novel enough (not in training data)?
   - Right level of complexity?
   - Good rule interactions?
   - Sufficient edge cases?

4. **Any changes to the schema?**
   - Additional fields needed?
   - Different organization?
   - More/fewer example scenarios?

Once validated, I'll systematically create 100 games following this template, with:
- 30 grid games (like Flux Zones, but varied mechanics)
- 15 graph games (node-edge structures)
- 15 state transformation games
- 10 simultaneous action games
- 10 accumulation games
- 10 constraint satisfaction games
- 10 hybrid mechanics games

Each will have:
- Unique novel mechanics
- Rich rule interactions
- Systematic edge cases
- Multiple transcripts showing progressive rule discovery
