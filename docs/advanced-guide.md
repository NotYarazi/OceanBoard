# OceanBoard - Complete Feature Documentation

> A comprehensive guide to every feature in OceanBoard v0.0.3 (old)

---

## **What is OceanBoard?**

OceanBoard is a **creative workspace for storytellers, writers, and dreamers**! Think of it as your personal story planning studio where you can organize series, seasons, episodes, characters, and everything else that makes your creative world come alive!

**Philosophy:** Simple, beautiful, and powerful - no ads, no accounts, no nonsense!

---

## **Core Features**

### 1. Series System

**What it does:** Manage multiple independent creative projects (like workspaces in VS Code!)

**How it works:**
- Click the **+ button** in the left pink strip
- Name your series (e.g., "My Epic Novel")
- Each series gets its own **color** and **cover image**
- Switch between series with one click
- Each series maintains completely separate files

**Cool features:**
- **Custom colors** - Right-click series → Change Color
- **Cover images** - Right-click series → Change Cover (supports GIF!)
- **Initials display** - Shows first 2 letters of series name
- **Active indicator** - Arrow points to current series
- **Independent workspaces** - Each series is a separate world

**Technical magic:**
- Stored in localStorage with unique IDs
- Covers stored as base64 (up to 2MB)
- Automatic metadata management
- Click any tile to switch instantly

---

### 2. File Explorer (Sidebar)

**What it does:** Organize your creative content into seasons and special files

#### **Seasons** (The Main Structure)
- Create folders for story arcs, volumes, or sections
- **Drag to reorder** - Grab the title, move it up/down
- **Collapsible** - Click arrow to hide/show episodes
- Each season contains episodes

#### **Episodes** (Your Story Files)
- The actual content files
- **Drag to reorder** within seasons
- **Drag between seasons** - Move files around!
- Color-coded by file type
- Click to open in editor

#### **Special Files** (Components Section)
Six unique file types:
- **Episode (EP)** - Blue - Main story content
- **Character (C)** - Green - Character profiles
- **Object (O)** - Orange - Important objects/items
- **Scene (SC)** - Purple - Scene descriptions
- **Action (A)** - Red - Action sequences
- **Attribute (AT)** - Yellow - Character/world attributes

**Why special files?**
- Always accessible (not hidden in seasons)
- Reference material
- Quick access to important info

---

### 3. Tab System

**What it does:** Manage multiple open files like a web browser

**Features:**
- **File type icons** - Visual identification
- **Color-coded** - Matches file type
- **Active indicator** - Pink underline on current tab
- **Close button** - X on each tab
- **Horizontal scroll** - When too many tabs open
- **Hover effects** - Tabs lift up on hover

**Smart behavior:**
- Opening same file? Switches to existing tab
- Closing tab? Switches to previous tab
- Last tab closed? Shows welcome screen with particles!

**Animations:**
- Smooth transitions
- Bounce-in when opening
- Scale on hover
- Active tab highlighted

---

### 4. Markdown Editor

**What it does:** Write in Markdown with live preview!

#### **Layout:**
- **Left pane:** Markdown input (your raw text)
- **Right pane:** Live preview (see the result!)
- **Bottom toolbar:** 13 formatting buttons

#### **Toolbar Buttons:**
1. **Bold** - `**text**`
2. **Italic** - `*text*`
3. **Strikethrough** - `~~text~~`
4. **Heading 1** - `# Title`
5. **Heading 2** - `## Title`
6. **Heading 3** - `### Title`
7. **Link** - `[text](url)`
8. **Quote** - `> quote`
9. **Code** - `` `code` ``
10. **Code Block** - ` ``` ```  `
11. **Bullet List** - `- item`
12. **Numbered List** - `1. item`
13. **Horizontal Rule** - `---`

#### **Smart Features:**
- **Auto-wrap selection** - Select text, click button!
- **Multi-line support** - Works with paragraphs
- **Live preview** - Updates as you type
- **Syntax highlighting** - Color-coded preview
- **Custom styling** - Pink headings, clean layout

---

### 5. Storage & Auto-Save

**What it does:** Never lose your work!

#### **Auto-Save**
- Saves every **15 seconds** by default
- Only saves **changed files**
- Runs in background silently
- Configurable in settings (5-60 seconds)

#### **What Gets Saved:**
- ✅ All file content
- ✅ File order within seasons
- ✅ Season order
- ✅ Series metadata (name, color, cover)
- ✅ Active series
- ✅ User settings

#### **Storage Technology:**
- Uses **localStorage** (5-10MB typically)
- Persists between sessions
- Works offline
- No server needed
- No accounts required

---

### 6. Import/Export System

**What it does:** Backup and share your work!

#### **Two Export Types:**

#### 1️⃣ **Full Workspace Export**
**Includes:**
- ✅ All series
- ✅ All files and content
- ✅ Settings (font size, line height, etc.)
- ✅ Series covers and colors
- ✅ Active series state

**File:** `OceanBoard-Workspace-YYYY-MM-DD-HHmmss.zip`

#### 2️⃣ **Files Only Export**
**Includes:**
- ✅ All series and files
- ✅ Series covers and colors
- ❌ No settings

**File:** `OceanBoard-Files-YYYY-MM-DD-HHmmss.zip`

#### **How to Use:**
1. Click **Export** button (download icon)
2. Choose export type:
   - **OK** = Full Workspace
   - **Cancel** = Files Only
3. ZIP file downloads automatically!

#### **Import:**
1. Click **Import** button (upload icon)
2. Select your `.zip` file
3. System auto-detects type
4. Page reloads with imported data

#### **ZIP Structure:**
```
OceanBoard-Workspace-2025-10-21.zip
├── oceanboard.json        # Metadata
├── settings.json          # Settings (workspace only)
├── active-series.txt      # Current series
├── series/
│   └── series-*.json      # Each series
└── files/
    └── *.txt              # All file contents
```

---

### 7. Settings System

**What it does:** Customize OceanBoard to your liking!

**Opens in:** Separate popup window

#### **Editor Settings:**
- **Font Size** (10-24px) - How big is your text?
- **Line Height** (1.2-2.5) - Space between lines
- **Line Numbers** (On/Off) - Show line numbers in editor
- **Word Wrap** (On/Off) - Wrap long lines or scroll?
- **Smooth Scroll** (On/Off) - Smooth scrolling behavior

#### **System Settings:**
- **Autosave Interval** (5-60 seconds) - How often to save

#### **Reset Options:**
1. **Clear All Data** - Remove EVERYTHING (nuclear option!)
2. **Reset to Empty State** - Remove series, keep settings

**Live Updates:**
- Changes apply **instantly**
- No page reload needed
- See effects immediately
- Smooth transitions

---

### 8. Particles & Animations

**What it does:** Make everything beautiful and alive!

#### **Particle System:**
- **50 floating particles** with pink hues
- **Connected lines** between nearby particles
- **Smooth movement** with edge wrapping
- **Opacity pulsing** for breathing effect

**Where you see it:**
- Empty state (no series)
- All tabs closed (welcome screen)

#### **Animations Everywhere:**
- **Series tiles** - Bounce in, lift on hover
- **Tabs** - Smooth transitions, scale on hover
- **Buttons** - Lift, scale, glow effects
- **Welcome screen** - Staggered entrance
- **Context menus** - Scale in/out
- **File explorer** - Smooth reordering

**Animation Types:**
- Float, Pulse, Fade, Slide, Bounce
- Shimmer, Glow, Rotate, Wave, Sparkle
- All GPU-accelerated (super smooth!)

---

### 9. Context Menus

**What it does:** Right-click operations!

#### **File/Season Context Menu:**
Right-click any file or season:
- **Rename** - Change name (50 char limit)
- **Duplicate** - Make a copy
- **Add Episode** - Create new file in season
- **Delete** - Remove permanently

#### **Series Context Menu:**
Right-click any series tile:
- **Rename Series**
- **Change Color** - Pick a custom color
- **Change Cover** - Upload image/GIF
- **Remove Cover** - Back to color only
- **Delete Series** - Remove with confirmation

**Features:**
- Material icons
- Pink hover state
- Smooth animations
- Smart positioning (stays on screen)

---

### 10. Empty State

**What it does:** Beautiful welcome experience!

**When you see it:**
- First launch (no series yet)
- All series deleted
- Clicking "Reset to Empty State"

**What's included:**
- **Floating particles** background
- **Welcome message** with OceanBoard logo
- **Quick action buttons:**
  - Website
  - Changelog
  - Documentation
- **Helpful hint** about the + button

**Animations:**
- Particles float and connect
- Text bounces in
- Buttons slide in with delays
- Smooth hover effects (fill animation!)

---
## **That's OceanBoard!**

A complete creative workspace built with love, vanilla JavaScript, and lots of pink! No ads, no accounts, no BS - just pure creative freedom!

**Made with by umaera**
