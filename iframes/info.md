# IFrames Folder - The Window Within Windows! 🪟

## What's This Folder About?
This is where standalone HTML pages live that open in **new browser windows** or iframes!

## Files Inside

### `settings.html`
**The Control Panel!**

A **complete standalone page** that opens in a popup window!

#### What It Does
Manages all user preferences:
- **Font Size** - How big is your text? (10-24px)
- **Line Height** - Spacing between lines (1.2-2.5)
- **Line Numbers** - Show/hide editor line numbers
- **Word Wrap** - Wrap long lines or scroll?
- **Smooth Scroll** - Buttery smooth scrolling
- **Autosave Interval** - How often to save (5-60 seconds)

#### Special Features
1. **Live Updates**
   - Changes apply INSTANTLY
   - Uses `window.postMessage()` to talk to parent
   - No page reload needed!
   - See changes as you adjust sliders

2. **Two Reset Options**
   - **Clear All Data**: Nuclear option (everything goes!)
   - **Reset to Empty State**: Keeps settings, removes series
   - Double confirmation for safety!

3. **Standalone Design**
   - Full HTML page with own styles
   - Matches main app design
   - Pink accents everywhere
   - Smooth range sliders

#### How It Opens
```javascript
// From settingswindow.js
const settingsWindow = window.open(
    './iframes/settings.html',
    'OceanBoard Settings',
    'width=500,height=700'
);
```

#### Communication Flow
```
Settings Window                Main Window
     ↓                              ↑
  Change slider               Apply change
     ↓                              ↑
  postMessage() ──────────→  addEventListener('message')
     ↓                              ↑
  Save to localStorage        Update CSS variables
```

#### Storage Keys Used
```javascript
'ob-setting-fontsize'        // Editor font size
'ob-setting-lineheight'      // Line spacing
'ob-setting-linenumbers'     // Show line numbers?
'ob-setting-wordwrap'        // Wrap text?
'ob-setting-smoothscroll'    // Smooth scrolling?
'ob-setting-autosave'        // Autosave interval
```

## Why IFrames/Popups?

### Advantages
1. **Isolation** - Separate context, won't break main app
2. **Focus** - Settings get full attention
3. **Persistence** - Can stay open while you work
4. **Modern** - Popup windows are cool!
5. **Independence** - Own CSS, own JavaScript

### Disadvantages
1. **Popup blockers** - Some browsers might block it
2. **Communication overhead** - Need postMessage
3. **Separate state** - Must sync with parent

## File Structure

```html
settings.html
├── <head>
│   ├── Inline CSS (matches main theme)
│   └── Google Fonts
├── <body>
│   ├── Header (Settings title)
│   ├── Settings groups
│   │   ├── Editor settings (font, line height, etc.)
│   │   └── System settings (autosave)
│   ├── Reset buttons
│   └── Inline JavaScript
└── Communication logic
```

## Future Files

### Possibilities
- `about.html` - About OceanBoard page
- `help.html` - Help documentation
- `export-preview.html` - Preview before export
- `welcome-tutorial.html` - First-time user guide
- `theme-editor.html` - Custom theme creator
- `keyboard-shortcuts.html` - Shortcut reference

## Technical Details

### postMessage API
Used for cross-window communication:
```javascript
// Sending from settings
window.opener.postMessage({
    type: 'setting-update',
    setting: 'fontSize',
    value: '16'
}, '*');

// Receiving in main
window.addEventListener('message', (event) => {
    const { type, setting, value } = event.data;
    // Apply the setting!
});
```

### Window Features
```javascript
window.open(url, name, features);
// features: 'width=500,height=700,resizable=yes'
```

### Accessing Parent
```javascript
window.opener            // Reference to parent window
window.opener.location   // Can reload parent
window.close()          // Close self
```

## Best Practices

### Do's
- Keep files standalone (include all needed CSS)
- Use postMessage for communication
- Handle window.opener being null (if blocked)
- Provide fallbacks for blocked popups
- Close window when done

### Don'ts
- Don't rely on parent DOM (may not exist!)
- Don't use `window.parent` (for iframes only)
- Don't create circular references
- Don't forget to handle popup blockers

## Fun Facts
- Settings window is 500x700px (perfect size!)
- Uses same fonts as main app
- Fully functional even if detached
- Can be moved/resized by user
- Lives independently!

## Debugging Tips
```javascript
console.log('[Settings Window] Opened');
console.log('Parent exists?', window.opener !== null);
console.log('Sending message:', data);
```

## Future Enhancements
- Draggable window (custom title bar)
- Remember window position
- Multiple tabs in settings
- Keyboard shortcuts display
- Theme preview
- Advanced mode toggle
