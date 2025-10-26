# Media Folder - The Asset Vault!

## What's This Folder About?
This is where all your visual goodies live! Images, icons, fonts, videos - if it's not code, it's probably here! Think of it as OceanBoard's closet!

## Subfolders

### `files/`
**User Uploaded Treasures!**
- Currently empty
- Reserved for user-uploaded files
- Attachments, images, documents
- Your personal file cabinet!

### `fonts/`
**The Typography Treasury!**
- Currently empty (we use Google Fonts!)
- Reserved for custom fonts
- Could hold special handwriting fonts
- Future home of unique typefaces!

### `icons/`
**The Icon Gallery!**

Contains the OceanBoard logo in multiple formats:
- `Icon-B&W.png` - Black & white PNG version
- `Icon-B&W.svg` - Black & white SVG (scalable!)
- `Icon-Pink.png` - Pink PNG version (our main color!)
- `Icon-Pink.svg` - Pink SVG (the scalable hero!)

**Used in:**
- Favicon (browser tab icon)
- Sidebar logo
- Empty state branding
- Documentation

### `images/`
**The Picture Paradise!**
- Currently empty
- Reserved for UI images
- Screenshots, backgrounds, promotional images
- Your visual showcase!

### `videos/`
**The Motion Picture Studio!**
- Currently empty
- Reserved for tutorial videos
- Demo recordings
- Animated guides

## File Organization

```
media/
├── files/      (user content)
├── fonts/      (typography)
├── icons/      (logos & symbols)
├── images/     (pictures)
└── videos/     (moving pictures)
```

## Icon Details

### The OceanBoard Logo
- **Design**: Simple, recognizable
- **Colors**: Pink (#E43967) and B&W variants
- **Formats**: PNG for compatibility, SVG for scaling
- **Size**: 44x44px in sidebar
- **Style**: Rounded, friendly, modern

### Why Both PNG and SVG?
- **PNG**: Works everywhere, fixed size
- **SVG**: Scales infinitely, smaller file size
- Best of both worlds!

## Current Usage

### Sidebar Logo
```css
.ob-logo {
    background-image: url('../../media/icons/Icon-Pink.svg');
}
```

### Favicon
```html
<link rel="shortcut icon" href="./media/icons/Icon-Pink.png">
```

## Future Plans
- User avatar system
- Custom emoji pack
- Series cover image library
- Animation frames
- Sound effect files (if we add audio!)
- Sticker pack (because why not?)

## Fun Facts
- All icons are under 10KB
- SVG files are just XML (text!)
- Pink is #E43967 (our signature color!)
- Logo is visible in browser tabs worldwide!

## Guidelines
- Keep images optimized (no 10MB files!)
- Use SVG when possible (scalable!)
- PNG for photos, SVG for icons
- Maintain consistent style
- Name files clearly
