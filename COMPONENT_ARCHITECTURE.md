# Component Architecture

This document outlines the modular structure of the Flood Safety Trainer application.

## Directory Structure

```
src/
├── components/           # React components
│   ├── index.js         # Component exports
│   ├── WelcomePage.jsx  # Landing/welcome screen
│   ├── GameScenario.jsx # Main game container
│   ├── GameStats.jsx    # Points and steps display
│   ├── ProgressTracker.jsx # Visual progress indicator
│   ├── LocationDisplay.jsx # Current location info
│   ├── RouteChoices.jsx # Route selection interface
│   └── GameCompletion.jsx # Success/completion screen
├── data/                # Game data and configuration
│   ├── index.js         # Data exports
│   └── gameScenario.js  # Game scenario definition
├── hooks/               # Custom React hooks
│   ├── index.js         # Hook exports
│   └── useGameState.js  # Game state management
├── assets/              # Static assets
├── App.jsx              # Main application component
├── main.jsx             # Application entry point
└── index.css            # Global styles
```

## Component Hierarchy

```
App
├── WelcomePage
└── GameScenario
    ├── GameStats
    ├── ProgressTracker
    ├── LocationDisplay
    ├── RouteChoices
    └── GameCompletion (conditional)
```

## Component Responsibilities

### Core Components

#### `App.jsx`
- **Purpose**: Main application router and state coordinator
- **Responsibilities**:
  - Manages top-level navigation between welcome and game screens
  - Handles page transitions
  - Provides clean separation between game states

#### `WelcomePage.jsx`
- **Purpose**: Application landing page and introduction
- **Responsibilities**:
  - Explains app purpose and functionality
  - Provides entry point to game scenarios
  - Sets user expectations with clear instructions

#### `GameScenario.jsx`
- **Purpose**: Main game container and coordinator
- **Responsibilities**:
  - Manages game flow and component orchestration
  - Handles conditional rendering of completion screen
  - Provides navigation controls
  - Uses custom game state hook for logic separation

### Game Interface Components

#### `GameStats.jsx`
- **Purpose**: Display current game metrics
- **Responsibilities**:
  - Shows points earned and steps taken
  - Provides consistent header with emergency branding
  - Updates in real-time as game progresses

#### `ProgressTracker.jsx`
- **Purpose**: Visual representation of evacuation progress
- **Responsibilities**:
  - Shows visited locations and current position
  - Provides visual feedback for completed steps
  - Animates current location indicator
  - Responsive design for different screen sizes

#### `LocationDisplay.jsx`
- **Purpose**: Current location information and feedback
- **Responsibilities**:
  - Displays current location name and description
  - Shows feedback messages for user actions
  - Color-codes feedback based on action safety
  - Provides context for next decisions

#### `RouteChoices.jsx`
- **Purpose**: Route selection interface
- **Responsibilities**:
  - Presents available evacuation routes
  - Provides visual indicators for route safety
  - Handles user interactions and choice submission
  - Animates dangerous route warnings

#### `GameCompletion.jsx`
- **Purpose**: Success screen and game conclusion
- **Responsibilities**:
  - Celebrates successful evacuation completion
  - Displays final scores and performance metrics
  - Provides options for replay and navigation
  - Shows placeholder for future scenario expansion

## Data Management

### `gameScenario.js`
- **Purpose**: Game configuration and scenario data
- **Contents**:
  - Location definitions with descriptions
  - Route mappings between locations
  - Safety indicators for each route
  - Extensible structure for additional scenarios

## State Management

### `useGameState.js`
- **Purpose**: Custom hook for game logic and state
- **Manages**:
  - Current player location
  - Points and step tracking
  - Feedback message state
  - Game completion status
  - Route history and path tracking
- **Provides**:
  - State getters for all game data
  - `makeMove()` function for processing route choices
  - `resetGame()` function for game restart
  - Clean separation of logic from UI components

## Key Design Principles

### 1. **Separation of Concerns**
- UI components handle presentation only
- Business logic isolated in custom hooks
- Data configuration separated from components
- Clear boundaries between different responsibilities

### 2. **Modularity**
- Each component has a single, well-defined purpose
- Components are reusable and testable in isolation
- Easy to modify individual features without affecting others
- Clear import/export structure with index files

### 3. **Maintainability**
- Consistent naming conventions across all files
- Well-documented component responsibilities
- Logical file organization and grouping
- Easy to locate and modify specific functionality

### 4. **Scalability**
- Easy to add new components or features
- Game data structure supports multiple scenarios
- Hook pattern allows for complex state management
- Component architecture supports feature expansion

## Benefits of This Structure

1. **Developer Experience**: Easy to find and modify specific functionality
2. **Code Reusability**: Components can be reused in different contexts
3. **Testing**: Each component can be tested in isolation
4. **Maintenance**: Changes to one component don't affect others
5. **Collaboration**: Multiple developers can work on different components
6. **Performance**: Components can be optimized individually
7. **Extensibility**: New features can be added without major refactoring

## Future Enhancements

This architecture supports easy addition of:
- New game scenarios and difficulty levels
- Additional UI components and features
- Complex state management with context or reducers
- API integration for dynamic content
- User authentication and progress tracking
- Multiplayer functionality
- Performance optimizations and code splitting