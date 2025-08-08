# Phase 1: Basic Structure (MVP)

## Overview
Create the foundational structure for the Solitaire game with minimal viable functionality.

## Goals
- Establish Go backend with static file serving
- Create basic HTML layout and CSS structure
- Implement simple card representation
- Set up initial game state with proper card dealing
- Enable basic click-to-move functionality

## Tasks

### Backend Setup
- [ ] Initialize Go module (`go mod init solitaire`)
  *Establishes the Go project structure and dependency management system, creating the foundation for package imports and version control that enables the backend to function as a proper Go application.*
- [ ] Create `main.go` with HTTP server
  *Implements the core server functionality that will handle incoming web requests and serve the game interface, providing the essential backend infrastructure that bridges the Go application with web browsers.*
- [ ] Set up static file serving from `/static` directory
  *Configures the server to deliver HTML, CSS, and JavaScript files to browsers, enabling the frontend game interface to load and function properly without requiring a complex web framework.*
- [ ] Test server startup and file serving
  *Validates that the backend infrastructure works correctly before building frontend components, ensuring a solid foundation and preventing integration issues later in development.*

### Frontend Structure
- [ ] Create `static/index.html` with game layout
  *Establishes the visual structure and semantic markup for the Solitaire game interface, providing the HTML foundation that will host all game elements and interactions.*
- [ ] Set up basic CSS grid for game areas:
  - Stock pile (top-left)
  - Waste pile (next to stock)
  - Four foundation piles (top-right)
  - Seven tableau columns (bottom)
  *Creates a responsive and organized layout system that positions game components in their traditional Solitaire locations, ensuring intuitive gameplay and visual clarity.*
- [ ] Create `static/css/main.css` for layout and positioning
  *Defines the overall visual structure and positioning rules for the game interface, establishing consistent spacing, alignment, and responsive behavior across different screen sizes.*
- [ ] Create `static/css/cards.css` for card styling
  *Implements the visual appearance and styling for playing cards, creating recognizable card representations that enhance user experience and game readability.*

### Core JavaScript Files
- [ ] `static/js/cards.js` - Card object and deck management
  *Encapsulates all card-related functionality including card creation, deck initialization, and shuffling logic, providing the fundamental data structures that represent the game's playing pieces.*
- [ ] `static/js/game.js` - Game state and initialization
  *Manages the overall game state, tracking card positions and game progress while providing initialization routines that set up a new game with proper card distribution.*
- [ ] `static/js/board.js` - Game board management
  *Handles the visual representation and manipulation of the game board, coordinating between the logical game state and the DOM elements that players interact with.*
- [ ] `static/js/ui.js` - Basic UI interactions
  *Implements user interface event handling and feedback, translating player clicks and gestures into game actions while providing visual responses to user interactions.*

### Card System
- [ ] Define card object structure (suit, rank, faceUp)
  *Establishes the fundamental data model for playing cards, creating a standardized representation that supports game logic, validation, and visual rendering throughout the application.*
- [ ] Implement deck creation and shuffling
  *Generates a complete 52-card deck with proper randomization, ensuring fair gameplay and replicating the authentic Solitaire experience with unpredictable card arrangements.*
- [ ] Create initial deal function (7 columns with proper face-up/down)
  *Implements the standard Solitaire dealing pattern that distributes cards across tableau columns with the correct face-up/face-down configuration, establishing the starting game state.*
- [ ] Simple text-based card representation initially
  *Provides a minimal viable card display system using text labels, enabling rapid development and testing of game logic before implementing more sophisticated visual card designs.*

### Basic Interactions
- [ ] Click event handling for cards
  *Establishes the primary user interaction mechanism that detects and processes player clicks on cards, forming the foundation for all player-initiated game actions.*
- [ ] Basic move validation (can move to foundation/tableau)
  *Implements Solitaire rules validation that ensures only legal moves are allowed, maintaining game integrity and providing immediate feedback on valid player actions.*
- [ ] Simple card movement between piles
  *Creates the core gameplay mechanic that visually and logically transfers cards between different game areas, enabling the fundamental card manipulation that drives Solitaire gameplay.*
- [ ] Stock pile click to reveal cards
  *Implements the stock pile interaction that allows players to cycle through unused cards, providing access to additional playing options when tableau moves are unavailable.*

## File Structure Created
```
solitaire/
├── main.go
├── go.mod
└── static/
    ├── index.html
    ├── css/
    │   ├── main.css
    │   └── cards.css
    └── js/
        ├── cards.js
        ├── game.js
        ├── board.js
        └── ui.js
```

## Success Criteria
- [ ] Server runs on `http://localhost:8080`
  *Validates that the backend infrastructure is properly configured and accessible, ensuring the development environment is ready for testing and frontend integration.*
- [ ] Game board displays with 7 tableau columns
  *Confirms that the visual layout correctly renders the traditional Solitaire playing field, providing the expected game interface that players can recognize and navigate.*
- [ ] Cards are dealt correctly (face-up/down pattern)
  *Verifies that the initial game setup follows standard Solitaire rules, ensuring authentic gameplay experience and proper game state initialization.*
- [ ] Stock, waste, and foundation areas are visible
  *Validates that all essential game areas are properly rendered and positioned, providing complete access to all game functionality required for successful play.*
- [ ] Basic card clicks register and log to console
  *Confirms that user interaction detection is working correctly, enabling debugging and validation of player input before implementing full game responses.*
- [ ] Can move cards between valid positions
  *Demonstrates that the core gameplay loop is functional, validating that players can successfully execute the primary game actions required for Solitaire.*

## Technical Notes
- Use CSS Grid for layout flexibility
- Cards represented as divs with text content initially
- Event delegation for card interactions
- Simple game state object to track all card positions
- No animations in Phase 1 - focus on functionality

## Testing
- [ ] Verify correct initial deal (28 cards in tableau)
  *Validates the mathematical accuracy of card distribution, ensuring that the dealing algorithm correctly places the expected number of cards in the tableau according to Solitaire rules.*
- [ ] Test server serves all static files correctly
  *Confirms that the backend properly delivers all frontend assets, preventing broken resources and ensuring a complete user experience when accessing the game.*
- [ ] Confirm click events work on all card areas
  *Validates comprehensive user interaction coverage across all game zones, ensuring that players can interact with cards regardless of their position on the game board.*
- [ ] Basic move validation works
  *Tests the game rule enforcement system to ensure that illegal moves are properly rejected and legal moves are accepted, maintaining game integrity and providing appropriate player feedback.*
- [ ] Game state updates correctly after moves
  *Verifies that the internal game logic accurately tracks changes when cards are moved, ensuring data consistency and enabling features like move validation and game completion detection.*