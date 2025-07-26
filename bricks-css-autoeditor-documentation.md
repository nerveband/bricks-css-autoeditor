# Bricks CSS Autoeditor - Comprehensive Documentation

## Table of Contents

1. [Overview](#overview)
2. [Project Description](#project-description)
3. [Features](#features)
4. [Architecture](#architecture)
5. [User Interface](#user-interface)
6. [Technical Implementation](#technical-implementation)
7. [Usage Guide](#usage-guide)
8. [JSON Structure Reference](#json-structure-reference)
9. [CSS Conversion Examples](#css-conversion-examples)
10. [Best Practices](#best-practices)
11. [Sample Components](#sample-components)
12. [Deployment](#deployment)

## Overview

**Bricks CSS Autoeditor** is a comprehensive web-based tool designed to bridge the gap between traditional CSS development and the Bricks Builder ecosystem. It provides developers with the ability to import, convert, validate, and manage CSS classes in Bricks Builder's JSON format.

**Live Tool:** [https://nerveband.github.io/bricks-css-autoeditor/](https://nerveband.github.io/bricks-css-autoeditor/)

## Project Description

The Bricks CSS Autoeditor solves a critical workflow challenge for Bricks Builder users who want to:
- Import existing CSS libraries into Bricks Builder
- Convert custom CSS code to Bricks JSON format
- Validate and debug existing Bricks JSON files
- Understand the complex Bricks CSS structure
- Create new CSS classes with a visual interface

### Key Problems Solved

1. **Format Conversion**: Automates the tedious process of converting CSS to Bricks JSON
2. **Validation**: Ensures JSON files meet Bricks structure requirements
3. **Documentation**: Provides comprehensive guide to Bricks JSON format
4. **Visual Editing**: Offers interactive tools for creating and previewing CSS classes

## Features

### 🎨 CSS Import & Conversion

- **Multiple Input Methods**:
  - File upload for CSS files
  - Direct CSS code pasting
  - Sample CSS library included
  
- **Smart Conversion Engine**:
  - Parses standard CSS properties
  - Maps to Bricks settings structure
  - Handles pseudo-classes (:hover, :focus)
  - Processes media queries
  - Auto-generates unique IDs

### 📥 JSON Import & Validation

- **Comprehensive Validation**:
  - Schema validation against Bricks requirements
  - Duplicate ID detection
  - Required field verification
  - Settings format checking
  
- **Real-time Analysis**:
  - Total class count
  - Classes with/without settings
  - Modified class tracking
  - File size calculation

### 🛠️ Advanced Tools

- **Interactive Class Builder**:
  - Visual form interface
  - Property grouping (Layout, Spacing, Visual)
  - Live preview generation
  
- **Merge Functionality**:
  - Combine converted CSS with existing JSON
  - Intelligent conflict resolution
  - Preserve existing modifications

- **Export Options**:
  - Filter by modification status
  - Export only classes with settings
  - Minified or formatted output

### 📚 Documentation System

- **Structure Guide**:
  - Complete property reference (53+ properties)
  - Nested object documentation
  - Responsive variant explanations
  
- **Interactive Examples**:
  - Step-by-step conversion demos
  - Real-world use cases
  - Best practice guidelines

## Architecture

### Technology Stack

- **Frontend**: Pure HTML5, CSS3, JavaScript (ES6+)
- **Styling**: Custom CSS with CSS variables for theming
- **No Dependencies**: Runs entirely in the browser
- **Storage**: LocalStorage for temporary data

### File Structure

```
bricks-css-autoeditor/
├── index.html                    # Landing page
├── bricks-structure-guide.html   # Main application
├── sample-styles.css            # Example CSS components
├── bricks-css-classes.json      # Original Bricks data
└── README.md                    # Project documentation
```

## User Interface

### Design System

The application uses a modern, clean design system with:

- **Color Palette**:
  - Primary: Blue scale (#3b82f6 to #1e3a8a)
  - Neutral: Gray scale (#fafafa to #171717)
  - Success: Green (#22c55e)
  - Warning: Orange (#f59e0b)
  - Danger: Red (#ef4444)

- **Typography**:
  - System font stack for optimal readability
  - Modular scale (1.333 ratio)
  - Responsive font sizes

- **Layout**:
  - Maximum width: 88rem (1408px)
  - Responsive grid system
  - Card-based component organization

### Key UI Components

1. **Header Section**:
   - Application title with gradient text
   - Description and statistics display
   - Quick navigation options

2. **Tabbed Interface**:
   - CSS Upload tab
   - Paste CSS tab
   - JSON Import tab
   - Sample & Preview tab

3. **Interactive Sections**:
   - Collapsible panels for organization
   - Smooth animations and transitions
   - Hover effects for interactivity

## Technical Implementation

### CSS Parser

The CSS parser handles various CSS patterns:

```javascript
// Example parsing logic
function parseCSS(cssText) {
  // Extract CSS rules
  const rules = cssText.match(/[^{]+\{[^}]+\}/g);
  
  // Process each rule
  rules.forEach(rule => {
    const selector = extractSelector(rule);
    const properties = extractProperties(rule);
    const bricksObject = convertToBricks(selector, properties);
  });
}
```

### Property Mapping

CSS properties are mapped to Bricks settings:

```javascript
const propertyMap = {
  'padding': '_padding',
  'margin': '_margin',
  'display': '_display',
  'grid-template-columns': '_gridTemplateColumns',
  'background-color': '_background.color',
  'border-radius': '_border.radius'
};
```

### ID Generation

Unique 6-character IDs are generated:

```javascript
function generateBricksId() {
  const chars = 'abcdefghijklmnopqrstuvwxyz0123456789';
  return Array.from({length: 6}, () => 
    chars[Math.floor(Math.random() * chars.length)]
  ).join('');
}
```

## Usage Guide

### Quick Start Workflow

1. **Access the Tool**:
   - Navigate to the live tool URL
   - Click "Launch Application" on the landing page

2. **Import CSS**:
   - Choose input method (upload or paste)
   - Review the parsed CSS in the preview
   - Adjust conversion options if needed

3. **Convert to JSON**:
   - Click "Convert to JSON"
   - Review the generated Bricks objects
   - Validate the structure

4. **Export or Merge**:
   - Download as new JSON file, or
   - Merge with existing Bricks JSON
   - Apply export filters as needed

### Advanced Workflows

#### Workflow 1: Converting Design System

1. Upload your design system CSS file
2. Review and organize generated classes
3. Add custom prefixes for namespacing
4. Export organized JSON structure

#### Workflow 2: Debugging Existing JSON

1. Import your Bricks JSON file
2. Review validation results
3. Fix any structural issues
4. Re-export cleaned file

#### Workflow 3: Creating New Classes

1. Use the Interactive Builder
2. Set properties visually
3. Preview in real-time
4. Add to existing collection

## JSON Structure Reference

### Core Object Structure

```json
{
  "id": "abc123",           // Required: 6-char unique ID
  "name": "my-class",       // Required: CSS class name
  "settings": {},           // Required: Settings object or []
  "_exists": false,         // Required: Always false
  "modified": 1234567890,   // Optional: Unix timestamp
  "user_id": 1,            // Optional: User identifier
  "_mappedId": "import_01"  // Optional: Import reference
}
```

### Settings Properties

#### Layout Properties
- `_display`: CSS display property
- `_position`: CSS position property
- `_gridTemplateColumns`: Grid columns definition
- `_gridTemplateRows`: Grid rows definition
- `_flexDirection`: Flex container direction
- `_alignItems`: Flex/grid alignment
- `_justifyContent`: Flex/grid justification

#### Spacing Properties
- `_padding`: Object with top/right/bottom/left
- `_margin`: Object with top/right/bottom/left
- `_rowGap`: Vertical spacing in grid/flex
- `_columnGap`: Horizontal spacing in grid/flex

#### Visual Properties
- `_typography`: Text styling object
- `_background`: Background properties
- `_border`: Border and radius properties
- `_boxShadow`: Shadow effects
- `_transform`: CSS transforms
- `_filter`: CSS filters
- `_cssCustom`: Raw CSS strings

#### Responsive Variants
Properties can have breakpoint suffixes:
- `:mobile_portrait`
- `:mobile_landscape`
- `:tablet_portrait`

Example: `_padding:mobile_landscape`

### Complex Object Examples

#### Typography Object
```json
"_typography": {
  "font-size": "1.5rem",
  "font-weight": "600",
  "line-height": "1.2",
  "letter-spacing": "0.02em",
  "text-transform": "uppercase",
  "color": {
    "raw": "var(--primary-color)"
  }
}
```

#### Padding/Margin Object
```json
"_padding": {
  "top": "2rem",
  "right": "1.5rem",
  "bottom": "2rem",
  "left": "1.5rem"
}
```

#### Background Object
```json
"_background": {
  "color": {
    "raw": "#ffffff"
  },
  "image": {
    "url": "path/to/image.jpg",
    "size": "cover",
    "position": "center"
  }
}
```

## CSS Conversion Examples

### Example 1: Button Component

**Input CSS:**
```css
.btn-primary {
  display: inline-block;
  padding: 12px 24px;
  background-color: #3b82f6;
  color: white;
  border-radius: 8px;
  font-weight: 600;
  transition: all 0.3s ease;
}
```

**Output JSON:**
```json
{
  "id": "btn001",
  "name": "btn-primary",
  "settings": {
    "_display": "inline-block",
    "_padding": {
      "top": "12px",
      "right": "24px",
      "bottom": "12px",
      "left": "24px"
    },
    "_background": {
      "color": {
        "raw": "#3b82f6"
      }
    },
    "_typography": {
      "color": {
        "raw": "white"
      },
      "font-weight": "600"
    },
    "_border": {
      "radius": {
        "top": "8px",
        "right": "8px",
        "bottom": "8px",
        "left": "8px"
      }
    },
    "_cssCustom": "transition: all 0.3s ease;"
  },
  "_exists": false
}
```

### Example 2: Grid Layout

**Input CSS:**
```css
.grid-auto {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 24px;
  padding: 40px;
}
```

**Output JSON:**
```json
{
  "id": "grd001",
  "name": "grid-auto",
  "settings": {
    "_display": "grid",
    "_gridTemplateColumns": "repeat(auto-fit, minmax(300px, 1fr))",
    "_gridGap": "24px",
    "_padding": {
      "top": "40px",
      "right": "40px",
      "bottom": "40px",
      "left": "40px"
    }
  },
  "_exists": false
}
```

## Best Practices

### Do's ✅

1. **Validate Before Import**:
   - Always validate JSON structure
   - Check for duplicate IDs
   - Verify required fields

2. **Use Semantic Names**:
   - Choose descriptive class names
   - Follow naming conventions
   - Use prefixes for organization

3. **Optimize Settings**:
   - Remove empty settings objects
   - Use CSS variables for maintainability
   - Group related classes

4. **Test Responsiveness**:
   - Add responsive variants as needed
   - Test across breakpoints
   - Use relative units

### Don'ts ❌

1. **Never Modify System Fields**:
   - Don't change `id` values
   - Don't alter `_exists` property
   - Preserve `_mappedId` references

2. **Avoid Conflicts**:
   - Don't duplicate class names
   - Don't mix incompatible properties
   - Don't override system classes

3. **Performance Considerations**:
   - Avoid excessive custom CSS
   - Limit deep nesting
   - Minimize file size

## Sample Components

The included `sample-styles.css` provides ready-to-use components:

### Button Components
- `.btn-primary` - Primary action button
- `.btn-secondary` - Secondary action button
- `.btn-large` - Large button variant

### Card Components
- `.card` - Basic card container
- `.card-hover` - Card with hover effects
- `.card-feature` - Feature card design

### Layout Components
- `.grid-auto` - Auto-fit responsive grid
- `.grid-2-col` - Two column grid
- `.grid-3-col` - Three column grid

### Typography
- `.heading-hero` - Hero section heading
- `.heading-section` - Section heading
- `.text-lead` - Lead paragraph text
- `.text-accent` - Accent text style

### Utilities
- `.flex-center` - Center content
- `.flex-between` - Space between items
- `.spacing-section` - Section padding
- `.spacing-container` - Container padding

### Advanced Effects
- `.glassmorphism` - Glass effect
- `.gradient-text` - Gradient text
- `.animate-fade` - Fade animation
- `.hover-scale` - Scale on hover

## Deployment

The application is deployed using GitHub Pages:

1. **Repository Setup**:
   - Push all files to GitHub repository
   - Enable GitHub Pages in settings
   - Select main branch as source

2. **Custom Domain (Optional)**:
   - Add CNAME file with domain
   - Configure DNS settings
   - Enable HTTPS

3. **Updates**:
   - Push changes to main branch
   - GitHub Pages auto-deploys
   - Changes live in ~10 minutes

### Local Development

To run locally:

1. Clone the repository
2. Open `index.html` in a web browser
3. No build process required
4. All features work offline

---

## Support & Contributing

- **Issues**: Report bugs via GitHub Issues
- **Features**: Request features via pull requests
- **Documentation**: Improve docs with PRs
- **Community**: Join discussions in Issues

## License

MIT License - Free for personal and commercial use

---

*Built with ❤️ for the Bricks Builder community*