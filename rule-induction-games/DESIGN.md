# Rule Induction Game Design Specification

## Purpose
Create 100 abstract games specifically designed to test LLM rule induction capabilities. Models observe natural language game transcripts and must infer the underlying rules without being told them explicitly.

## Core Principles

### 1. Novel Mechanics
- **No direct analogs** to known games (chess, checkers, go, etc.)
- **Unfamiliar combinations** of familiar concepts
- **Invented terminology** to prevent keyword matching
- **Novel interactions** between game elements

### 2. Rule Complexity Dimensions
Instead of "easy/medium/hard", we measure:
- **Rule count**: 3-15 distinct rules
- **Interaction depth**: How many rules jointly determine an outcome
- **Conditional complexity**: if/then/unless/except structures
- **State dependencies**: rules that change based on game state
- **Negative constraints**: what you CANNOT do (harder to infer)

### 3. Compositional Design
Rules should interact non-obviously:
- Rule A enables Rule B
- Rule C modifies the effect of Rule A
- Rule D creates exceptions to Rule B
- Multiple rules jointly determine legality

### 4. Edge Case Rich
- Boundary conditions (board edges, first/last turn)
- Tie-breaking rules
- Multiple simultaneous triggers
- Cascading effects
- Special states that change rule application

## Game Definition Schema

Each game will have BOTH structured and natural language representations:

### Structured Format (YAML)

```yaml
game_id: "string"
name: "string"

# State space definition
state:
  board:
    type: "grid | graph | linear | custom"
    dimensions: "5x5 | 7-node-graph | etc"
    topology: "orthogonal | diagonal | hexagonal | custom"

  pieces:
    - name: "string"
      colors: ["color1", "color2"]
      properties:
        - name: "property_name"
          type: "integer | boolean | enum"
          range: "min-max | values"

  players:
    count: 2-4
    turn_order: "alternating | simultaneous | custom"

# Formal rule definitions
rules:
  movement:
    - id: "R_MOVE_1"
      priority: 1
      condition: "formal condition"
      action: "formal action"
      effect: "state change"
      exceptions: ["exception conditions"]

  placement:
    - id: "R_PLACE_1"
      ...

  capture:
    - id: "R_CAPTURE_1"
      ...

  transformation:
    - id: "R_TRANSFORM_1"
      ...

  win_conditions:
    - id: "WIN_1"
      condition: "formal win condition"
      priority: 1

# Rule interactions (explicit)
interactions:
  - rules: ["R_MOVE_1", "R_CAPTURE_1"]
    type: "enabling | modifying | blocking"
    description: "how they interact"

# Natural language description
description: |
  Natural language overview of the game in 2-3 paragraphs.
  Written as if explaining to a human who will play.

rule_explanations:
  - rule_id: "R_MOVE_1"
    natural_language: "Plain English explanation"
    examples:
      - scenario: "description"
        legal: true/false
        reason: "why"

# Edge cases and corner cases
edge_cases:
  - scenario: "description"
    question: "what happens?"
    answer: "explanation"
    involved_rules: ["R_X", "R_Y"]

# Example initial states
example_states:
  - state_id: "initial"
    description: "starting position"
    representation: "visual/text"

  - state_id: "mid_game"
    description: "interesting mid-game position"
    representation: "visual/text"

# Difficulty indicators (for rule induction, not play)
induction_difficulty:
  observable_patterns: "low | medium | high"
  hidden_constraints: "low | medium | high"
  rule_interdependence: "low | medium | high"
  edge_case_frequency: "low | medium | high"
```

### Natural Language Format

Each game also gets a companion natural language document that reads like a game manual, but is designed for rule induction:

```markdown
# [Game Name]

## Overview
[2-3 paragraph description of what the game looks like when played]

## How to Play
[Natural language rules, written conversationally]

## Example Turn Sequence
[Narrative of several turns being played, showing legal and illegal moves]

Player A: "I'll place my red marker on B3."
Player B: "That's not allowed - you need to be adjacent to one of your existing markers."
Player A: "Oh right, then I'll place on C2 instead."
[Game state updates shown]

## Why This Game Tests Rule Induction
[Internal notes on what makes this challenging]
- Rules X and Y interact non-obviously
- Edge case Z is rare but important
- Negative constraint W is hard to infer
```

## Game Design Categories

### Category 1: Grid Games (30 games)
- 5x5 or 7x7 grids
- Piece placement, movement, capture
- Spatial relationships, adjacency rules
- Control/territory mechanics
- Novel: charge mechanics, contagion, field effects

### Category 2: Graph Games (15 games)
- Node-and-edge structures
- Path formation, network building
- Connection rules, flow mechanics
- Novel: directional edges, colored paths, weighted nodes

### Category 3: State Transformation Games (15 games)
- Pieces change properties over time
- Metamorphosis rules
- Stack/layer mechanics
- Novel: conditional transformations, cascading effects

### Category 4: Simultaneous Action Games (10 games)
- Both players choose actions secretly
- Resolution rules for conflicts
- Rock-paper-scissors style interactions
- Novel: priority systems, partial information reveals

### Category 5: Accumulation Games (10 games)
- Score/resource collection
- Set building with complex scoring
- Combo multipliers
- Novel: negative scoring, score caps, theft mechanics

### Category 6: Constraint Satisfaction Games (10 games)
- Puzzle-like placement with constraints
- Each move must satisfy multiple conditions
- Novel: propagating constraints, constraint relaxation

### Category 7: Hybrid Mechanics (10 games)
- Combining multiple novel mechanics
- Cross-category rule interactions
- Maximum compositional complexity

## Key Distinctions from Traditional Games

1. **No Theme**: Abstract only (no "you're a wizard" narratives)
2. **No Flavor**: Pure mechanics (no "crystal," "potion," "spell" unless mechanically distinct)
3. **Small State Space**: Max 7x7 boards, limited piece counts
4. **Deterministic**: No dice, no shuffling (pure logic)
5. **Complete Information**: Both players see everything (no hidden hands)
6. **Novel Terminology**: Invent terms like "flux," "anchor," "phase" for new mechanics

## Mechanics to Explore

### Novel Concepts Not in Common Games
- **Charge/Energy**: Pieces accumulate properties based on neighbors
- **Contagion**: States spread according to rules
- **Anchoring**: Some pieces lock others in place
- **Phasing**: Pieces exist in multiple states
- **Resonance**: Pieces interact at a distance based on properties
- **Cascade**: One action triggers chain reactions
- **Threshold**: Effects activate only when conditions met
- **Polarity**: Pieces attract/repel based on properties
- **Echo**: Previous moves influence current possibilities
- **Debt**: Negative resources that must be cleared

## What Makes a Good Rule Induction Game

### Good Properties
✓ Rules interact in non-obvious ways
✓ Edge cases reveal deeper rules
✓ Illegal moves illuminate boundaries
✓ Multiple valid strategies exist
✓ Pattern matching fails (must understand rules)
✓ Compositional reasoning required

### Bad Properties
✗ Too simple (trivial pattern matching works)
✗ Too similar to known games
✗ Rules are independent (no interactions)
✗ Edge cases are rare
✗ Only one obvious strategy
✗ Ambiguous rules (unclear what's legal)

## Validation Criteria

For each game, verify:
1. Can you generate 20+ interesting scenarios?
2. Do scenarios reveal rules progressively?
3. Are there interesting illegal moves to show?
4. Do rules interact in at least 3 ways?
5. Would an LLM need deep understanding (not pattern matching)?
6. Are edge cases systematic and important?

## Next Steps

1. Create first 10 games in Category 1 (Grid Games)
2. Test scenario generation from these games
3. Validate that rules are inferable but challenging
4. Iterate on schema based on learnings
5. Expand to all 100 games systematically
