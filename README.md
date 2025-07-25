# Bricks CSS Autoeditor

A comprehensive tool for importing, converting, and managing CSS classes in Bricks Builder through JSON file processing.

🌐 **Live Tool:** [https://nerveband.github.io/bricks-css-autoeditor/](https://nerveband.github.io/bricks-css-autoeditor/)

## Overview

This project provides a complete toolkit to understand, document, and manipulate CSS formats used by Bricks Builder. It converts regular CSS files into Bricks JSON format, validates existing JSON files, and provides an interactive guide to the Bricks CSS structure.

## Features

### 🎨 CSS Import & Conversion
- **CSS File Upload** - Import regular CSS files and convert to Bricks JSON format
- **Paste CSS Code** - Convert CSS snippets with customizable options
- **Smart Property Mapping** - Automatically maps CSS properties to Bricks settings structure
- **Sample CSS Library** - 25+ pre-built components (buttons, cards, grids, typography)

### 📥 JSON Import & Validation
- **Bricks JSON Import** - Upload existing Bricks JSON files with format validation
- **Schema Validation** - Comprehensive validation against Bricks structure requirements
- **Structure Analysis** - Detects duplicate IDs, validates required fields, checks settings format
- **Real-time Statistics** - Shows class counts, modification status, and structure health

### 🛠️ Advanced Tools
- **Interactive Class Builder** - Visual form to create new CSS classes
- **Live CSS Preview** - See sample components rendered in real-time
- **Merge Functionality** - Combine converted CSS with existing Bricks JSON files
- **Export Options** - Filtered exports (modified only, with settings only)

### 📚 Comprehensive Documentation
- **Structure Guide** - Complete breakdown of Bricks JSON format
- **Real Examples** - Step-by-step walkthroughs with 4 detailed examples
- **Best Practices** - Guidelines for safe modification and common gotchas
- **Interactive Explorer** - Search and browse existing CSS classes

## Quick Start

1. **Visit the Tool:** [https://nerveband.github.io/bricks-css-autoeditor/](https://nerveband.github.io/bricks-css-autoeditor/)

2. **Import CSS:**
   - Upload a CSS file or use the sample CSS
   - Convert to Bricks JSON format
   - Review generated structure

3. **Merge & Export:**
   - Import existing Bricks JSON (optional)
   - Merge converted classes
   - Download combined file

4. **Import to Bricks:**
   - Use the downloaded JSON file in your Bricks Builder setup

## Workflow Examples

### Converting Custom CSS
```css
.my-button {
  padding: 12px 24px;
  background-color: var(--primary);
  border-radius: 8px;
  color: white;
}
```

Becomes:
```json
{
  "id": "btn001",
  "name": "my-button",
  "settings": {
    "_padding": {
      "top": "12px",
      "right": "24px", 
      "bottom": "12px",
      "left": "24px"
    },
    "_background": {
      "color": { "raw": "var(--primary)" }
    },
    "_border": {
      "radius": {
        "top": "8px",
        "right": "8px",
        "bottom": "8px", 
        "left": "8px"
      }
    },
    "_typography": {
      "color": { "raw": "white" }
    }
  },
  "_exists": false
}
```

## Sample CSS Components

The included `sample-styles.css` contains:

- **Buttons:** Primary, secondary, large variants
- **Cards:** Basic, hover effects, feature cards  
- **Grids:** Auto-fit, responsive columns
- **Typography:** Hero headings, section titles, lead text
- **Utilities:** Flexbox, spacing, animations
- **Advanced:** Glassmorphism, gradients, keyframe animations

## JSON Structure

Each Bricks CSS class follows this structure:

### Required Fields
- `id` - Unique 6-character identifier
- `name` - CSS class name  
- `settings` - Configuration object or empty array
- `_exists` - Always `false`

### Optional Fields
- `modified` - Unix timestamp
- `user_id` - User identifier
- `_mappedId` - Import mapping reference

### Settings Properties (53+ available)
- **Layout:** `_display`, `_gridTemplateColumns`, `_flexDirection`
- **Spacing:** `_padding`, `_margin`, `_rowGap`, `_columnGap`
- **Visual:** `_typography`, `_background`, `_border`, `_gradient`
- **Responsive:** Properties with breakpoint suffixes (`:mobile_landscape`)

## Validation & Safety

### ✅ Safe to Modify
- All properties within `settings` objects
- `modified` timestamp values
- `user_id` values

### ❌ Never Change
- `id` values (unique identifiers)
- `name` values (CSS class names)
- `_exists` values (always false)
- `_mappedId` values (when present)

## Browser Support

- Modern browsers with ES6+ support
- File upload/download capabilities
- CSS Grid and Flexbox support for previews

## Files in Repository

- `bricks-structure-guide.html` - Main interactive tool
- `sample-styles.css` - Example CSS components
- `bricks-css-classes.json` - Original Bricks JSON data
- `index.html` - Landing page

## Contributing

Contributions are welcome! Please feel free to submit issues or pull requests.

## License

This project is open source and available under the MIT License.