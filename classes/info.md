# Classes Folder - The Brain of OceanBoard!

## What's This Folder About?
All the JavaScript logic lives here! This is where the magic happens behind the scenes. Think of it as the puppet master pulling all the strings!

## Subfolders

### `attributes/`
- Currently empty but ready for future file attribute systems
- Will handle things like tags, categories, metadata
- Think of it like giving your files superpowers!

### `canvas/`
- Currently empty but reserved for future canvas features
- Could be for drawings, diagrams, visual planning
- Your creative canvas awaits!

### `editors/`
Contains all the editor-related code:
- `markdowneditor.js` - The split-pane Markdown editor with toolbar
- `tabsystem.js` - Tab management (open, close, switch)
- `settingswindow.js` - Opens settings in a popup window
- `settingsapplier.js` - Applies settings in real-time (live updates!)

### `files/`
- `filetypes.js` - Determines what icon and color each file type gets
  - Episode (EP) = blue
  - Character (C) = green
  - Object (O) = orange
  - Scene (SC) = purple
  - Action (A) = red
  - Attribute (AT) = yellow

### `filesystem/`
The backbone of the entire system:
- `seriessystem.js` - Manages multiple series (workspaces)
- `storage.js` - Saves/loads everything to localStorage
- `dragdrop.js` - Makes things draggable
- `sidebaractions.js` - Handles sidebar button clicks
- `contextmenu.js` - Right-click menus
- `importexport.js` - ZIP export/import functionality

### `forStyles/`
- `particles.js` - The floating particle system (50 pink particles!)

## Main File

### `index.js`
This is the main entry point that:
1. Imports all other modules
2. Initializes everything on page load
3. Connects all the systems together
4. Makes sure everyone plays nice!

## How They Work Together

```
index.js
   ↓
   ├─→ editors/ (handles text editing)
   ├─→ files/ (knows about file types)
   ├─→ filesystem/ (saves, loads, organizes)
   ├─→ forStyles/ (makes it pretty)
   └─→ All connected via imports/exports!
```

## Code Style
- ES6 modules (`import`/`export`)
- Max 500 lines per file
- Clear function names
- Console logs with `[Module Name]` prefix
- No frameworks - pure vanilla JS!
