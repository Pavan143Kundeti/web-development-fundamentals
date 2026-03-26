# HTML Tables - Complete Guide

## What are HTML Tables?

Tables are used to display data in a structured format with rows and columns. They help organize information like student records, movie lists, salary details, or any data that needs to be presented in a grid format.

## Why Use Tables?

- Display data in organized rows and columns
- Compare information easily
- Create structured layouts
- Present financial data, schedules, or reports
- Show relationships between different data points

---

## Basic Table Structure

### Essential Table Tags

| Tag | Purpose | Description |
|-----|---------|-------------|
| `<table>` | Table container | Wraps the entire table |
| `<tr>` | Table Row | Creates a horizontal row |
| `<th>` | Table Heading | Column headers (bold & centered) |
| `<td>` | Table Data | Actual data cells |

### Basic Syntax

```html
<table>
    <tr>
        <th>Heading 1</th>
        <th>Heading 2</th>
        <th>Heading 3</th>
    </tr>
    <tr>
        <td>Data 1</td>
        <td>Data 2</td>
        <td>Data 3</td>
    </tr>
</table>
```

### Simple Example: Student Details

```html
<!DOCTYPE html>
<html>
<head>
    <title>Student Details</title>
</head>
<body>
    <table border="1">
        <tr>
            <th>Roll Number</th>
            <th>Name</th>
            <th>Location</th>
        </tr>
        <tr>
            <td>101</td>
            <td>Rajesh</td>
            <td>Hyderabad</td>
        </tr>
        <tr>
            <td>102</td>
            <td>Priya</td>
            <td>Mumbai</td>
        </tr>
        <tr>
            <td>103</td>
            <td>Amit</td>
            <td>Delhi</td>
        </tr>
    </table>
</body>
</html>
```

---

## Table Attributes

### 1. Border Attribute

Adds visible boundaries around table and cells.

```html
<!-- No border -->
<table>
    <tr><td>Data</td></tr>
</table>

<!-- Border with thickness 1 -->
<table border="1">
    <tr><td>Data</td></tr>
</table>

<!-- Border with thickness 5 -->
<table border="5">
    <tr><td>Data</td></tr>
</table>
```

**Note:** Standard HTML borders appear as double lines. To make them single lines, use CSS:

```html
<table border="1" style="border-collapse: collapse;">
    <tr><td>Data</td></tr>
</table>
```

### 2. Cellpadding Attribute

Controls space between cell content and cell border (inner spacing).

```html
<!-- No padding -->
<table border="1">
    <tr><td>Tight content</td></tr>
</table>

<!-- 10 pixels padding -->
<table border="1" cellpadding="10">
    <tr><td>Comfortable spacing</td></tr>
</table>

<!-- 20 pixels padding -->
<table border="1" cellpadding="20">
    <tr><td>Lots of space</td></tr>
</table>
```

### 3. Cellspacing Attribute

Controls space between individual cells (outer spacing).

```html
<!-- No spacing between cells -->
<table border="1" cellspacing="0">
    <tr>
        <td>Cell 1</td>
        <td>Cell 2</td>
    </tr>
</table>

<!-- 10 pixels spacing -->
<table border="1" cellspacing="10">
    <tr>
        <td>Cell 1</td>
        <td>Cell 2</td>
    </tr>
</table>
```

### Visual Comparison

| Attribute | Effect | Example |
|-----------|--------|---------|
| cellpadding="0" | No inner space | Content touches border |
| cellpadding="10" | 10px inner space | Content has breathing room |
| cellspacing="0" | Cells touch each other | No gap between cells |
| cellspacing="10" | 10px gap between cells | Visible separation |

### 4. Align Attribute

#### Table Alignment (on webpage)
```html
<!-- Align table to left -->
<table border="1" align="left">
    <tr><td>Left aligned table</td></tr>
</table>

<!-- Align table to center -->
<table border="1" align="center">
    <tr><td>Centered table</td></tr>
</table>

<!-- Align table to right -->
<table border="1" align="right">
    <tr><td>Right aligned table</td></tr>
</table>
```

#### Cell Content Alignment
```html
<table border="1">
    <tr>
        <td align="left">Left aligned text</td>
        <td align="center">Centered text</td>
        <td align="right">Right aligned text</td>
    </tr>
</table>
```

### 5. Width and Height Attributes

#### Using Percentages
```html
<!-- Table takes 50% of webpage width -->
<table border="1" width="50%">
    <tr><td>Half width table</td></tr>
</table>

<!-- Table takes 100% of webpage width -->
<table border="1" width="100%">
    <tr><td>Full width table</td></tr>
</table>
```

#### Using Pixels
```html
<!-- Fixed width of 300 pixels -->
<table border="1" width="300">
    <tr><td>300px wide table</td></tr>
</table>

<!-- Fixed width and height -->
<table border="1" width="400" height="200">
    <tr><td>400x200 table</td></tr>
</table>
```

#### Column-Specific Width
```html
<table border="1">
    <tr>
        <td width="100">100px wide</td>
        <td width="200">200px wide</td>
        <td width="150">150px wide</td>
    </tr>
</table>
```

### 6. Background Color (bgcolor)

#### Entire Table
```html
<table border="1" bgcolor="lightblue">
    <tr>
        <td>Cell 1</td>
        <td>Cell 2</td>
    </tr>
</table>
```

#### Specific Row
```html
<table border="1">
    <tr bgcolor="yellow">
        <td>Highlighted row</td>
        <td>Highlighted row</td>
    </tr>
    <tr>
        <td>Normal row</td>
        <td>Normal row</td>
    </tr>
</table>
```

#### Specific Cell
```html
<table border="1">
    <tr>
        <td>Normal cell</td>
        <td bgcolor="lightgreen">Highlighted cell</td>
        <td>Normal cell</td>
    </tr>
</table>
```

---

## Advanced Table Formatting

### Colspan - Merging Columns

Merges multiple columns into a single cell horizontally.

#### Example 1: Simple Colspan
```html
<table border="1">
    <tr>
        <th colspan="3">Student Information</th>
    </tr>
    <tr>
        <th>Roll No</th>
        <th>Name</th>
        <th>Grade</th>
    </tr>
    <tr>
        <td>101</td>
        <td>Rahul</td>
        <td>A</td>
    </tr>
</table>
```

**Result:** "Student Information" spans across 3 columns.

#### Example 2: Movie List with Colspan
```html
<table border="1" width="60%">
    <tr>
        <th colspan="4">Top Movies 2024</th>
    </tr>
    <tr>
        <th>Rank</th>
        <th>Movie Name</th>
        <th>Director</th>
        <th>Rating</th>
    </tr>
    <tr>
        <td>1</td>
        <td>Movie A</td>
        <td>Director X</td>
        <td>9.5</td>
    </tr>
    <tr>
        <td>2</td>
        <td>Movie B</td>
        <td>Director Y</td>
        <td>9.2</td>
    </tr>
</table>
```

### Rowspan - Merging Rows

Merges multiple rows into a single cell vertically.

#### Example 1: Simple Rowspan
```html
<table border="1">
    <tr>
        <td rowspan="3">Department</td>
        <td>Employee 1</td>
    </tr>
    <tr>
        <td>Employee 2</td>
    </tr>
    <tr>
        <td>Employee 3</td>
    </tr>
</table>
```

**Result:** "Department" cell spans 3 rows vertically.

#### Example 2: Salary Details with Rowspan
```html
<table border="1" cellpadding="10">
    <tr>
        <th>Employee</th>
        <th>Position</th>
        <th>Salary</th>
    </tr>
    <tr>
        <td rowspan="2">IT Department</td>
        <td>Developer</td>
        <td>₹50,000</td>
    </tr>
    <tr>
        <td>Tester</td>
        <td>₹40,000</td>
    </tr>
    <tr>
        <td rowspan="2">HR Department</td>
        <td>Manager</td>
        <td>₹60,000</td>
    </tr>
    <tr>
        <td>Assistant</td>
        <td>₹35,000</td>
    </tr>
</table>
```

### Combining Colspan and Rowspan

```html
<table border="1" cellpadding="10" width="80%">
    <tr>
        <th colspan="4" bgcolor="lightblue">Company Report 2024</th>
    </tr>
    <tr>
        <th rowspan="2">Quarter</th>
        <th colspan="3">Sales (in Lakhs)</th>
    </tr>
    <tr>
        <th>Product A</th>
        <th>Product B</th>
        <th>Product C</th>
    </tr>
    <tr>
        <td>Q1</td>
        <td>50</td>
        <td>60</td>
        <td>70</td>
    </tr>
    <tr>
        <td>Q2</td>
        <td>55</td>
        <td>65</td>
        <td>75</td>
    </tr>
</table>
```

---

## Practical Example: Webpage Layout

Creating a complete webpage structure using tables with colspan and rowspan.

```html
<!DOCTYPE html>
<html>
<head>
    <title>Webpage Layout with Tables</title>
</head>
<body>
    <table border="1" width="100%" cellpadding="10" cellspacing="0">
        <!-- Top Menu -->
        <tr>
            <td colspan="4" bgcolor="lightblue" align="center" height="60">
                <h2>Top Menu / Header</h2>
            </td>
        </tr>
        
        <!-- Main Content Area -->
        <tr>
            <!-- Side Menu -->
            <td rowspan="2" bgcolor="lightgreen" width="20%" valign="top">
                <h3>Side Menu</h3>
                <ul>
                    <li>Home</li>
                    <li>About</li>
                    <li>Services</li>
                    <li>Contact</li>
                </ul>
            </td>
            
            <!-- Technology Section -->
            <td colspan="2" bgcolor="lightyellow" height="200">
                <h3>Technology Section</h3>
                <p>Latest technology news and updates...</p>
            </td>
            
            <!-- Sports Section -->
            <td bgcolor="lightcoral">
                <h3>Sports</h3>
                <p>Sports updates...</p>
            </td>
        </tr>
        
        <!-- Additional Content Row -->
        <tr>
            <td colspan="3" bgcolor="lavender" height="150">
                <h3>Main Content Area</h3>
                <p>Your main content goes here...</p>
            </td>
        </tr>
        
        <!-- Footer -->
        <tr>
            <td colspan="4" bgcolor="lightgray" align="center" height="50">
                <p>&copy; 2024 Your Website. All rights reserved.</p>
            </td>
        </tr>
    </table>
</body>
</html>
```

---

## Complete Examples

### Example 1: Student Information Table

```html
<table border="1" cellpadding="8" cellspacing="0" width="70%" align="center">
    <tr bgcolor="navy" style="color: white;">
        <th>Roll Number</th>
        <th>Student Name</th>
        <th>Location</th>
        <th>Grade</th>
    </tr>
    <tr>
        <td align="center">101</td>
        <td>Rajesh Kumar</td>
        <td>Hyderabad</td>
        <td align="center">A</td>
    </tr>
    <tr bgcolor="lightgray">
        <td align="center">102</td>
        <td>Priya Sharma</td>
        <td>Mumbai</td>
        <td align="center">A+</td>
    </tr>
    <tr>
        <td align="center">103</td>
        <td>Amit Patel</td>
        <td>Delhi</td>
        <td align="center">B+</td>
    </tr>
    <tr bgcolor="lightgray">
        <td align="center">104</td>
        <td>Sneha Reddy</td>
        <td>Bangalore</td>
        <td align="center">A</td>
    </tr>
</table>
```

### Example 2: Product Comparison Table

```html
<table border="1" cellpadding="12" width="90%" align="center" style="border-collapse: collapse;">
    <tr bgcolor="darkblue" style="color: white;">
        <th colspan="4">Product Comparison 2024</th>
    </tr>
    <tr bgcolor="lightblue">
        <th>Feature</th>
        <th>Basic Plan</th>
        <th>Pro Plan</th>
        <th>Enterprise</th>
    </tr>
    <tr>
        <td>Storage</td>
        <td align="center">10 GB</td>
        <td align="center">100 GB</td>
        <td align="center">Unlimited</td>
    </tr>
    <tr bgcolor="lightyellow">
        <td>Users</td>
        <td align="center">1</td>
        <td align="center">10</td>
        <td align="center">Unlimited</td>
    </tr>
    <tr>
        <td>Support</td>
        <td align="center">Email</td>
        <td align="center">Email + Chat</td>
        <td align="center">24/7 Phone</td>
    </tr>
    <tr bgcolor="lightyellow">
        <td>Price</td>
        <td align="center">₹500/month</td>
        <td align="center">₹2000/month</td>
        <td align="center">₹5000/month</td>
    </tr>
</table>
```

---

## Best Practices

### 1. Structure and Semantics
- Always use `<th>` for headers, not `<td>`
- Use `<table>` only for tabular data, not for layout
- Keep table structure simple and logical

### 2. Accessibility
- Add meaningful headers
- Use proper row and column structure
- Consider screen reader users

### 3. Styling
- Use CSS for modern styling instead of HTML attributes
- Keep borders consistent
- Use appropriate colors for readability

### 4. Responsive Design
- Avoid fixed pixel widths when possible
- Use percentages for flexible layouts
- Consider mobile users

---

## Common Mistakes to Avoid

### 1. Mismatched Columns
```html
<!-- Wrong: Different number of cells per row -->
<table border="1">
    <tr>
        <td>Cell 1</td>
        <td>Cell 2</td>
    </tr>
    <tr>
        <td>Cell 1</td>
        <td>Cell 2</td>
        <td>Cell 3</td> <!-- Extra cell! -->
    </tr>
</table>
```

### 2. Forgetting Closing Tags
```html
<!-- Wrong -->
<table>
    <tr>
        <td>Data
    </tr>
</table>

<!-- Correct -->
<table>
    <tr>
        <td>Data</td>
    </tr>
</table>
```

### 3. Incorrect Colspan/Rowspan Values
```html
<!-- Wrong: colspan doesn't match actual columns -->
<table border="1">
    <tr>
        <td colspan="5">Header</td> <!-- Says 5 but only 3 columns exist -->
    </tr>
    <tr>
        <td>A</td>
        <td>B</td>
        <td>C</td>
    </tr>
</table>
```

---

## Practice Exercises

### Exercise 1: Basic Table
Create a table showing your weekly schedule with days and activities.

### Exercise 2: Colspan Practice
Create a table for a restaurant menu with categories spanning multiple columns.

### Exercise 3: Rowspan Practice
Create an employee table where department names span multiple employee rows.

### Exercise 4: Complex Layout
Design a webpage layout using tables with header, sidebar, main content, and footer.

---

## Summary

| Concept | Tag/Attribute | Purpose |
|---------|---------------|---------|
| Table container | `<table>` | Wraps entire table |
| Table row | `<tr>` | Creates horizontal row |
| Table heading | `<th>` | Column headers (bold) |
| Table data | `<td>` | Data cells |
| Border | `border="1"` | Adds cell borders |
| Cell padding | `cellpadding="10"` | Inner cell spacing |
| Cell spacing | `cellspacing="5"` | Space between cells |
| Alignment | `align="center"` | Position content |
| Width/Height | `width="50%"` | Table dimensions |
| Background | `bgcolor="blue"` | Cell/row/table color |
| Merge columns | `colspan="3"` | Span across columns |
| Merge rows | `rowspan="2"` | Span across rows |

Tables are powerful tools for organizing data. Master these concepts to create professional, well-structured data presentations!

---

*Next lesson: We'll learn about HTML forms and user input elements!*