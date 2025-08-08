# Phase 2: Core Gameplay

## Overview
Implement complete game logic and rule validation for a fully playable Solitaire game.

## Goals
- Complete move validation system
- Implement all Solitaire rules correctly
- Add stock/waste pile functionality
- Enable face-down card flipping
- Implement win condition detection

## Tasks

### Move Validation System
- [ ] Tableau building rules (alternating colors, descending rank)
  *Implements the core Solitaire rule validation that ensures cards can only be placed on tableau columns in descending rank with alternating colors, maintaining authentic gameplay and preventing invalid moves that would break the game logic.*
- [ ] Foundation building rules (same suit, ascending rank A-K)
  *Enforces the foundation pile construction rules that require cards to be built in ascending order from Ace to King within the same suit, enabling the primary winning mechanism of Solitaire.*
- [ ] Empty column rules (only Kings can fill empty spaces)
  *Validates the special tableau rule that restricts empty column filling to Kings only, maintaining strategic gameplay balance and preventing abuse of empty spaces that would make the game too easy.*
- [ ] Multiple card movement (valid sequences)
  *Enables the advanced gameplay mechanic that allows moving multiple cards as a unit when they form a valid descending sequence, significantly improving game flow and strategic options.*
- [ ] Prevent invalid moves with user feedback
  *Provides immediate visual or textual feedback when players attempt illegal moves, enhancing user experience by teaching game rules and preventing confusion about why actions fail.*

### Stock and Waste Pile
- [ ] Stock pile click to deal cards to waste
  *Implements the fundamental stock pile interaction that allows players to cycle through unused cards, providing access to additional playing options when tableau moves are limited.*
- [ ] Turn-3 mode (deal 3 cards at once)
  *Provides the classic Solitaire variant that reveals three cards simultaneously from the stock pile, increasing game difficulty and creating the traditional challenging gameplay experience.*
- [ ] Turn-1 mode (deal 1 card at a time)
  *Offers an easier gameplay variant that reveals one card at a time from the stock pile, making the game more accessible to beginners while maintaining strategic depth.*
- [ ] Cycle through stock when empty
  *Enables the stock pile recycling mechanism that returns waste cards to the stock when depleted, providing continued access to cards and preventing premature game endings.*
- [ ] Waste pile top card availability
  *Ensures that only the topmost waste pile card can be moved or played, maintaining proper game flow and preventing exploitation of deeper waste pile cards.*

### Card Flipping Mechanism
- [ ] Auto-flip face-down cards when exposed
  *Automatically reveals face-down cards when they become the top card of a tableau column, maintaining smooth gameplay flow and ensuring players always have access to playable cards.*
- [ ] Update tableau display when cards are flipped
  *Synchronizes the visual representation with card state changes when cards are revealed, ensuring the interface accurately reflects the current game state and available moves.*
- [ ] Ensure only top face-down card in column can be flipped
  *Enforces the rule that prevents flipping buried face-down cards, maintaining game integrity and ensuring that card revelation follows proper Solitaire progression rules.*

### Foundation Management
- [ ] Auto-detect valid foundation moves
  *Identifies opportunities for moving cards to foundation piles automatically, helping players recognize optimal moves and reducing the cognitive burden of constantly checking foundation possibilities.*
- [ ] Allow moves from tableau and waste to foundations
  *Enables card transfers from both tableau columns and waste pile to foundation stacks, providing complete flexibility in building foundation piles from all available card sources.*
- [ ] Prevent invalid foundation moves
  *Validates foundation pile moves to ensure cards follow the ascending rank and same-suit requirements, maintaining game rule integrity and preventing invalid foundation construction.*
- [ ] Foundation to tableau moves (when beneficial)
  *Allows strategic movement of cards from foundation back to tableau when it enables better moves, providing advanced players with additional tactical options to optimize their game strategy.*

### Game State Management
- [ ] Track all card positions accurately
  *Maintains precise record of every card's location throughout the game, ensuring data integrity and enabling features like move validation, undo functionality, and win condition detection.*
- [ ] Maintain face-up/face-down states
  *Preserves the visibility state of each card throughout the game, ensuring that face-down cards remain hidden until properly revealed and supporting the strategic elements of hidden information.*
- [ ] Update game state after each move
  *Synchronizes the internal game model with player actions in real-time, ensuring that all game logic operates on current data and enabling immediate validation of subsequent moves.*
- [ ] Validate game state consistency
  *Implements integrity checks that verify the game state remains logically consistent after each operation, preventing data corruption and ensuring reliable game behavior throughout play.*

### Win/Lose Detection
- [ ] Check for win condition (all cards in foundations)
  *Continuously monitors game progress to detect when all 52 cards have been successfully moved to foundation piles, triggering victory celebration and game completion procedures.*
- [ ] Detect when no more moves are possible
  *Analyzes the current game state to identify unwinnable positions where no legal moves remain, allowing the game to notify players and offer new game options when stuck.*
- [ ] Game over states and messaging
  *Provides clear feedback when games end through either victory or deadlock conditions, offering appropriate celebratory or consolatory messages and game completion statistics.*
- [ ] New game functionality
  *Implements complete game reset capability that clears the current state and initializes a fresh game with newly shuffled cards, enabling continuous play sessions.*

## Enhanced Features

### Smart Move Detection
- [ ] Highlight valid move destinations when card is selected
  *Provides visual guidance by highlighting all legal move destinations when a card is clicked, reducing player frustration and helping newcomers learn valid move patterns.*
- [ ] Show which cards can be moved to clicked position
  *Displays available cards that can legally move to a clicked destination, enabling reverse move discovery where players select targets first and see movement options.*
- [ ] Prevent obviously bad moves (e.g., burying useful cards)
  *Implements intelligent move analysis that warns players about potentially harmful moves like burying lower-rank cards under higher ones, helping prevent strategic mistakes.*

### Auto-Move Features
- [ ] Double-click to auto-move to foundation (if valid)
  *Provides convenient shortcut for moving cards to foundation piles through double-clicking, streamlining gameplay by automating obvious beneficial moves.*
- [ ] Auto-complete when only foundation moves remain
  *Automatically finishes the game when all remaining cards can only move to foundations, eliminating tedious manual completion and providing satisfying game conclusion.*
- [ ] Option to disable auto-moves for manual control
  *Provides player preference settings that allow disabling automated features, enabling full manual control for players who prefer complete agency over every move.*

### Game Rules Variants
- [ ] Vegas scoring (Turn-3 with limited passes)
  *Implements the challenging Vegas Solitaire variant with restricted stock cycling and monetary scoring system, providing competitive gameplay for experienced players.*
- [ ] Standard scoring (Turn-1 unlimited passes)
  *Offers the traditional Solitaire scoring system with unlimited stock cycling, providing accessible gameplay suitable for casual players and learning.*
- [ ] Configuration options for rule variants
  *Creates a flexible settings system that allows players to customize game rules and difficulty, accommodating different skill levels and playing preferences.*

## Technical Implementation

### Enhanced Game State
```javascript
gameState = {
  tableau: [[], [], [], [], [], [], []], // 7 columns
  foundations: [[], [], [], []], // 4 suit foundations
  stock: [], // remaining deck
  waste: [], // dealt cards
  settings: { turnCount: 3, passes: unlimited }
}
```

### Move Validation Functions
- [ ] `isValidTableauMove(card, targetColumn)`
  *Encapsulates tableau move validation logic in a reusable function that checks color alternation and rank sequence rules, providing consistent rule enforcement across the application.*
- [ ] `isValidFoundationMove(card, targetFoundation)`
  *Implements foundation-specific validation that verifies suit matching and ascending rank requirements, ensuring foundation piles are built correctly according to Solitaire rules.*
- [ ] `canMoveSequence(cards, targetColumn)`
  *Validates multi-card sequence movements by checking that the entire sequence follows tableau building rules, enabling efficient batch card operations.*
- [ ] `getValidMoves(card)` - returns array of valid destinations
  *Provides comprehensive move analysis that returns all legal destinations for a given card, supporting features like move highlighting and AI assistance.*

### Game Rules Engine
- [ ] Move execution with rollback capability
  *Implements transactional move system that can reverse operations if validation fails or errors occur, ensuring game state integrity and enabling undo functionality.*
- [ ] Rule validation before moves
  *Establishes pre-move validation system that checks rule compliance before executing actions, preventing invalid operations and maintaining consistent game behavior.*
- [ ] Game state integrity checks
  *Implements comprehensive validation that ensures the game state remains mathematically and logically consistent, detecting and preventing data corruption or rule violations.*
- [ ] Move history for undo functionality
  *Maintains detailed record of all game actions to enable move reversal, providing players with safety net for experimental moves and mistake recovery.*

## Success Criteria
- [ ] All Solitaire rules correctly implemented
  *Validates that the game faithfully reproduces traditional Solitaire rules and behavior, ensuring authentic gameplay experience that matches player expectations.*
- [ ] No invalid moves possible
  *Confirms that the validation system successfully prevents all rule violations, ensuring game integrity and providing reliable rule enforcement throughout play.*
- [ ] Stock/waste cycling works correctly
  *Verifies that the stock pile recycling mechanism functions properly in both turn-1 and turn-3 modes, maintaining consistent card availability and game flow.*
- [ ] Face-down cards flip automatically
  *Ensures that card revelation happens seamlessly when tableau columns are uncovered, maintaining smooth gameplay without requiring manual intervention.*
- [ ] Win condition properly detected
  *Validates that game completion is accurately identified when all cards reach foundation piles, ensuring players receive proper victory recognition and game closure.*
- [ ] Game can be completed successfully
  *Confirms that winnable games can actually be finished through the interface, ensuring that no bugs prevent players from achieving victory in solvable deals.*
- [ ] New game resets everything correctly
  *Verifies that game initialization properly clears all previous state and establishes fresh starting conditions, preventing data leakage between game sessions.*

## Testing Scenarios
- [ ] Test all valid tableau moves (alternating colors)
  *Systematically validates that all legal tableau placements are correctly accepted, ensuring comprehensive rule coverage and preventing false rejections of valid moves.*
- [ ] Test foundation building (A-K same suit)
  *Verifies that foundation construction follows proper sequence and suit requirements, testing the core winning mechanism through comprehensive scenario coverage.*
- [ ] Test empty column filling (Kings only)
  *Validates the special rule enforcement for empty tableau spaces, ensuring that only Kings can initiate new column sequences while other ranks are properly rejected.*
- [ ] Test stock cycling and waste pile
  *Comprehensively validates stock pile functionality including card dealing, waste pile management, and recycling behavior in both turn modes.*
- [ ] Test face-down card exposure
  *Verifies that card revelation mechanisms work correctly when tableau columns are uncovered, ensuring proper game progression and card availability.*
- [ ] Test multiple card sequences
  *Validates the complex multi-card movement system through various sequence lengths and configurations, ensuring batch operations maintain rule compliance.*
- [ ] Test win scenario completion
  *Simulates complete game victories to ensure win detection and completion procedures function correctly, validating the entire game lifecycle.*
- [ ] Test dead-end game detection
  *Validates the system's ability to recognize unwinnable positions, ensuring players receive appropriate feedback when no legal moves remain available.*

## Performance Considerations
- [ ] Efficient move validation algorithms
  *Optimizes rule checking procedures to minimize computational overhead, ensuring responsive gameplay even with complex validation requirements and frequent rule checks.*
- [ ] Minimal DOM manipulation during moves
  *Reduces browser rendering overhead by batching DOM updates and using efficient update patterns, maintaining smooth animation and responsive user interface.*
- [ ] Fast game state updates
  *Optimizes internal data structure operations to minimize latency between player actions and game response, ensuring immediate feedback and fluid gameplay experience.*
- [ ] Responsive user interactions
  *Ensures that all player inputs receive immediate visual feedback and processing, creating engaging gameplay that responds instantly to user actions and maintains player engagement.*