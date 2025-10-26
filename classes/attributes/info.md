# 🔗 Attributes System

> **The advanced linking and reference system for OceanBoard!**

---

## **What is the Attributes System?**

The Attributes System is OceanBoard's way of creating **smart links** between files! Think of it as:
- **Tagging system** - Mark important text references
- **Internal wiki links** - Jump between related content
- **Living dictionary** - Define once, reference everywhere
- **Knowledge graph** - Connect your story universe

---

## **Folder Contents**

```
attributes/
├── validation.js       # File-ID and key uniqueness validation
├── parser.js          # Parse attribute files and mentions (future)
├── linker.js          # Handle mention clicking and navigation (future)
├── bubble.js          # Confirmation bubble UI (future)
└── info.md            # This file
```

---

## **How It Works**

### **1. File IDs (Special Files)**

Every special file (Character, Object, Scene, etc.) can have a unique ID:

```markdown
$ file-id = "maya"

**Name:** Maya Rodriguez
**Age:** 25
```

- First line is ALWAYS `$ file-id = "value"`
- Hidden in preview (metadata only)
- Max 24 characters
- Alphanumeric only (letters and numbers)
- Must be unique across all files

**Example valid IDs:**
- ✅ `maya`
- ✅ `villain01`
- ✅ `SomeFuckingBulldog`
- ✅ `MomIAmOnTheInternet`

**Example invalid IDs:**
- ❌ `mr.robot` (contains dot)
- ❌ `my character` (contains space)
- ❌ `super-stupid` (contains hyphen)
- ❌ `verylongnameexceeding24chars` (too long)

---

### **2. Attribute Files (Dictionaries)**

Attribute files map **keys** to **file locations**:

```markdown
$ file-id = "maindict"

# Main Characters
hero = character.maya:4
villain = character.volkov:8
sidekick = character.alex:12

# Important Objects
mousepad = object.slideness:5
flower = object.protection:10
```

Format: `key = component.file-id:line`

- **key**: Short reference name (unique within file)
- **component**: File type (character, object, scene, etc.)
- **file-id**: The target file's ID
- **line**: Line number in target file (optional)

---

### **3. Mentioning in Regular Files**

**Method A: Natural Typing (with confirmation)**

```markdown
When character.maya entered the room...
     ^^^^^^^^^^^^^^
     Shows bubble: "Link to character.maya?" [Yes] [No]
```

- Type naturally: `component.file-id`
- Bubble appears asking for confirmation
- Click "Yes" → Converts to `@component.file-id` internally
- Click "No" → Remains as plain text

**Method B: Direct Link (no confirmation)**

```markdown
When @character.maya entered the room...
```

- Prefix with `@` to skip confirmation
- Instantly creates link
- Highlighted in editor
- In preview, shows only the file-id part

**Method C: Attach Selected Text**

1. Select text in editor
2. Right-click → "Attach to dictionary"
3. Enter key name (e.g., "bulldogWithLice")
4. Select attribute file from list
5. Auto-adds: `bulldogWithLice = component.file-id:currentLine`

---

## 🔍 **Display Behavior**

### **In Editor:**
```markdown
When @character.maya entered, she saw @object.flower on the table.
     ^^^^^^^^^^^^^^^                  ^^^^^^^^^^^^^^
     (highlighted)                    (highlighted)
```

### **In Preview:**
```
When maya entered, she saw flower on the table.
     ^^^^                  ^^^^^
     (clickable)           (clickable)
```

Only the file-id part is shown (component prefix stripped)!

---

## **Click Behavior**

When you click a mention:
1. Resolves `character.maya` to find file with `file-id = "maya"`
2. Opens that file in new tab (if not already open)
3. Scrolls to referenced line (if line number provided)
4. Highlights the referenced text

---

## **Validation Rules**

### **File-ID Validation:**
- ✅ Must be unique across all files
- ✅ Max 24 characters
- ✅ Alphanumeric only (a-z, A-Z, 0-9)
- ❌ No spaces, dots, hyphens, or symbols
- ❌ Cannot be empty

### **Attribute Key Validation:**
- ✅ Must be unique within the same attribute file
- ✅ Can contain letters, numbers, underscores, hyphens
- ❌ Cannot have duplicate keys in same file

### **Reference Validation:**
- ✅ Referenced file-id must exist
- ✅ Component type should match (optional warning)
- ⚠️ Handling if target file deleted

---

## 📊 **Data Storage**

### **In-Memory Registries:**

```javascript
// File ID Registry
fileIdRegistry = Map {
  "maya" => "[C] - Maya Rodriguez",
  "drWowlo" => "[C] - The Villain",
  "sharpVodca" => "[O] - Sharp Vodca"
}

// Attribute Keys Registry
attributeKeysRegistry = Map {
  "[AT] - Main Dictionary" => Set ["Hero", "villain", "AFuckingOctopi"],
  "[AT] - Locations" => Set ["house", "forest", "nowhere"]
}
```

### **Rebuild on Load:**
- Scans all files in localStorage
- Extracts file-ids from special files
- Extracts keys from attribute files
- Builds lookup maps for fast access

---

## **Use Cases**

### **World-Building**
```markdown
The @location.castle was guarded by @character.knight.
He wielded @object.amulet passed down for generations.
```

### **Character Tracking**
```markdown
Attribute file:
protagonist = character.emma:1
antagonist = character.bruno:1
raccoon = character.willy:1

Story:
@protagonist met @raccoon at the tavern.
Later, @antagonist appeared...
```

### **Scene References**
```markdown
Back at @scene.sewer, @character.kingofsewer made his decision.
```

---

## 💡 **Future Enhancements**

### **Phase 1 (Current)**
- ✅ File-ID system
- ✅ Validation (uniqueness, format)
- ⏳ Parser for attribute files
- ⏳ Mention detection
- ⏳ Click navigation

### **Phase 2**
- [ ] Auto-complete suggestions
- [ ] Hover preview tooltip
- [ ] Backlinks (show all mentions)
- [ ] Broken link detection
- [ ] Bulk rename support

### **Phase 3**
- [ ] Graph view (visual connections)
- [ ] Relationship mapping
- [ ] Timeline integration
- [ ] Smart suggestions
- [ ] Export with resolved links

---

## **Technical Details**

### **File-ID Regex:**
```javascript
/^\$\s*file-id\s*=\s*"([^"]+)"\s*$/
```

### **Attribute Line Regex:**
```javascript
/^([a-zA-Z0-9_-]+)\s*=\s*([a-z]+)\.([a-zA-Z0-9]+)(?::(\d+))?$/
```

### **Mention Pattern:**
```javascript
// With @: Instant link
/@([a-z]+)\.([a-zA-Z0-9]+)/g

// Without @: Needs confirmation
/([a-z]+)\.([a-zA-Z0-9]+)/g
```

---

## **Why This is Awesome**

1. **No Manual ID Management** - File-IDs are declared in the file itself
2. **Type Safe** - Validation prevents duplicates and errors
3. **Natural Writing** - Write "character.maya" naturally
4. **Flexible** - Use @ for instant links or get confirmation
5. **Smart Preview** - Shows clean text, links work behind scenes
6. **Scalable** - Works for small stories or massive worlds
7. **Interconnected** - Creates a web of related content

---

## **Example Workflow**

### **Step 1: Create Character**
```markdown
$ file-id = "emma"

**Name:** Emma Stone
**Role:** Detective
**Age:** 32
```

### **Step 2: Create Attribute Dictionary**
```markdown
$ file-id = "maincast"

detective = character.emma:1
partner = character.jake:1
```

### **Step 3: Write Story**
```markdown
@character.emma arrived at the crime scene.
She called her @character.jake for backup.
```

### **Step 4: Preview Reads:**
```
Emma arrived at the crime scene.
She called her Jake for backup.
```

### **Step 5: Click "Emma" → Opens Character File**

---

<div align="center">

**Made with 💖 by umaera**

</div>
