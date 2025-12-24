# CSS Pseudo-Classes Guide 📚

## Overview
This guide covers CSS pseudo-classes, which are keywords that allow you to style HTML elements based on their state or position without using JavaScript or additional classes.

## Table of Contents
- [What are Pseudo-Classes?](#what-are-pseudo-classes)
- [Syntax](#syntax)
- [Categories](#categories)
- [Common Pseudo-Classes](#common-pseudo-classes)
- [Practical Examples](#practical-examples)
- [Best Practices](#best-practices)
- [Common Mistakes](#common-mistakes)
- [Exercises](#exercises)
- [Resources](#resources)

## What are Pseudo-Classes?

Pseudo-classes are CSS selectors that target elements based on:
- User interaction (hover, click, focus)
- Position in the document tree (first-child, last-child)
- Element state (checked, disabled, valid)
- Content characteristics (empty, target)

## Syntax

```css
selector:pseudo-class {
  property: value;
}
```

### Basic Examples:
```css
/* Single pseudo-class */
a:hover { color: red; }

/* Multiple pseudo-classes */
input:required:valid { border-color: green; }

/* Pseudo-class with other selectors */
.nav-item:first-child { margin-left: 0; }
```

## Categories

### 1. User Action Pseudo-Classes
Handle user interactions with elements.

| Pseudo-class | Description | Common Use |
|-------------|-------------|------------|
| `:hover` | Mouse over element | Navigation menus, buttons |
| `:active` | Element being activated | Button press effect |
| `:focus` | Element has focus | Form input highlighting |
| `:focus-within` | Element or child has focus | Form container styling |

### 2. Location Pseudo-Classes
Style links based on navigation state.

| Pseudo-class | Description |
|-------------|-------------|
| `:link` | Unvisited links |
| `:visited` | Visited links |
| `:target` | Element matching URL fragment |

### 3. Tree-Structural Pseudo-Classes
Select elements based on document structure.

| Pseudo-class | Description | Example |
|-------------|-------------|---------|
| `:root` | Document root element | CSS variables |
| `:first-child` | First child of parent | `li:first-child` |
| `:last-child` | Last child of parent | `p:last-child` |
| `:nth-child(n)` | Nth child of parent | `tr:nth-child(2n)` |
| `:nth-last-child(n)` | Nth child from end | `div:nth-last-child(2)` |
| `:only-child` | Only child of parent | `span:only-child` |
| `:first-of-type` | First of element type | `h2:first-of-type` |
| `:last-of-type` | Last of element type | `p:last-of-type` |
| `:nth-of-type(n)` | Nth of element type | `img:nth-of-type(3)` |
| `:only-of-type` | Only one of type | `article:only-of-type` |

### 4. Input Pseudo-Classes
Style form elements based on state.

| Pseudo-class | Description | Use Case |
|-------------|-------------|----------|
| `:enabled` | Enabled form elements | Default state styling |
| `:disabled` | Disabled form elements | Grayed out inputs |
| `:checked` | Checked inputs | Custom checkboxes |
| `:indeterminate` | Indeterminate state | Partial selection |
| `:default` | Default form element | Pre-selected option |
| `:required` | Required fields | Mandatory indicators |
| `:optional` | Optional fields | Optional indicators |
| `:valid` | Valid input | Success feedback |
| `:invalid` | Invalid input | Error feedback |
| `:in-range` | Value in range | Number input validation |
| `:out-of-range` | Value out of range | Range warnings |
| `:read-only` | Read-only inputs | Non-editable fields |
| `:read-write` | Editable inputs | Editable fields |

### 5. Content Pseudo-Classes

| Pseudo-class | Description |
|-------------|-------------|
| `:empty` | Elements with no children |
| `:not(selector)` | Elements not matching selector |
| `:is(selector)` | Matches any of the selectors |
| `:where(selector)` | Like :is() but no specificity |
| `:has(selector)` | Parent has specific children |

## Common Pseudo-Classes

### Navigation Menu Example
```css
/* Navigation with pseudo-classes */
.nav-link {
  color: #333;
  text-decoration: none;
  padding: 10px 15px;
  transition: all 0.3s;
}

.nav-link:hover {
  color: #007bff;
  background-color: #f8f9fa;
}

.nav-link:active {
  transform: scale(0.98);
}

.nav-link:focus {
  outline: 2px solid #007bff;
  outline-offset: 2px;
}

/* Current page indicator */
.nav-link.current {
  font-weight: bold;
  color: #007bff;
}
```

### Form Validation Example
```css
/* Form input validation */
input[type="email"] {
  border: 2px solid #ddd;
  padding: 8px;
  transition: border-color 0.3s;
}

input[type="email"]:focus {
  border-color: #007bff;
  outline: none;
}

input[type="email"]:valid {
  border-color: #28a745;
}

input[type="email"]:invalid {
  border-color: #dc3545;
}

/* Required field indicator */
input:required {
  background-color: #fff9e6;
}

/* Disabled state */
input:disabled {
  background-color: #e9ecef;
  cursor: not-allowed;
  opacity: 0.6;
}
```

### Table Striping Example
```css
/* Zebra-striped table */
table {
  width: 100%;
  border-collapse: collapse;
}

tr:nth-child(even) {
  background-color: #f8f9fa;
}

tr:hover {
  background-color: #e9ecef;
}

/* Highlight first and last row */
tr:first-child {
  font-weight: bold;
  background-color: #007bff;
  color: white;
}

tr:last-child {
  border-bottom: 3px solid #007bff;
}
```

## Practical Examples

### 1. Interactive Button
```css
.btn {
  padding: 12px 24px;
  background: