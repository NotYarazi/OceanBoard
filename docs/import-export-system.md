# Import/Export System

## Overview
OceanBoard includes a powerful import/export system that allows you to backup and share your work using ZIP files.

## Export Options

### Full Workspace Export
**What's included:**
- OceanBoard version
- All settings (font size, line height, word wrap, etc.)
- All series with metadata (names, colors, cover images)
- All seasons and episodes
- All file contents
- Active series information

**Use this when:**
- Creating a complete backup
- Moving to another computer
- Sharing your entire workspace with collaborators

**File naming:** `OceanBoard-Workspace-YYYY-MM-DD-HHmmss.zip`

### Files Only Export
**What's included:**
- OceanBoard version (basic)
- All series with metadata
- All seasons and episodes
- All file contents

**NOT included:**
- Settings (font size, line height, etc.)

**Use this when:**
- Sharing just your story/project files
- Want recipient to use their own settings
- Creating a lightweight backup

**File naming:** `OceanBoard-Files-YYYY-MM-DD-HHmmss.zip`

## How to Export

1. Click the **Export** button (download icon) in the header
2. Choose your export type:
   - Click **OK** for Full Workspace (with settings)
   - Click **Cancel** for Files Only (no settings)
3. The ZIP file will download automatically
4. Save it somewhere safe!

## How to Import

1. Click the **Import** button (upload icon) in the header
2. Select your OceanBoard `.zip` file
3. The system automatically detects if it's a Workspace or Files export
4. Click OK on the success message
5. The page will reload with your imported data

**Note:** Import will ADD to your existing data. If you want a clean import, use "Reset to Empty State" in Settings first.

## File Structure

Inside the ZIP file:

```
OceanBoard-Workspace-2025-10-21-143055.zip
├── oceanboard.json          # Metadata (version, type, date)
├── settings.json            # All settings (workspace export only)
├── active-series.txt        # Currently active series
├── series/                  # All series data
│   ├── series-1234567.json
│   └── series-7654321.json
└── files/                   # All file contents
    ├── episode-123.txt
    ├── character-456.txt
    └── scene-789.txt
```

## Technical Details

- **Library:** JSZip (loaded from CDN)
- **Storage:** localStorage keys are preserved
- **Version:** 0.0.3 (old)
- **Max Size:** Limited by localStorage (usually 5-10MB)
- **Format:** JSON for metadata, plain text for file contents

## Troubleshooting

**Import fails:**
- Make sure the file is a valid OceanBoard export
- Check that it's not corrupted
- Try exporting again from source

**Export too large:**
- Consider exporting individual series separately (coming soon)
- Remove unused files or series
- Compress large cover images

**Settings not importing:**
- Make sure you exported as "Full Workspace" not "Files Only"
- Check that settings.json exists in the ZIP

## Future Features
- Export individual series
- Import with merge/replace options
- Compression settings
- Cloud sync integration
