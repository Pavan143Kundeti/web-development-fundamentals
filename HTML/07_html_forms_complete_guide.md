# Day 7: HTML Forms - Complete Guide

## What are HTML Forms?

Forms are essential tools for collecting user data on websites. They allow users to input information and submit it to a server for processing.

### Common Uses of Forms
- User registration and login
- Contact forms
- Survey and feedback forms
- Search boxes
- Online shopping checkout
- Bank account applications
- File uploads

---

## Basic Form Structure

### Form Tag Syntax

```html
<form action="destination" method="post" target="_blank">
    <!-- Form fields go here -->
</form>
```

### Essential Form Attributes

| Attribute | Purpose | Values |
|-----------|---------|--------|
| `action` | Where to send form data | URL or file path |
| `method` | How to send data | `get` or `post` |
| `target` | Where to display response | `_self`, `_blank` |

---

## Form Attributes Explained

### 1. Action Attribute

Specifies where form data should be sent when submitted.

```html
<!-- Send to PHP file -->
<form action="response.php">
    <!-- form fields -->
</form>

<!-- Send to same folder file -->
<form action="process.html">
    <!-- form fields -->
</form>

<!-- Send to subfolder -->
<form action="pages/response.html">
    <!-- form fields -->
</form>
```

### 2. Method Attribute

Defines how data is sent to the server.

#### GET Method (Default)
```html
<form action="response.html" method="get">
    <!-- Data appears in URL -->
</form>
```
- Data visible in URL
- Less secure
- Limited data size
- Good for search forms

#### POST Method (Recommended)
```html
<form action="response.html" method="post">
    <!-- Data hidden from URL -->
</form>
```
- Data hidden from URL
- More secure
- No size limit
- Good for sensitive data (passwords, personal info)

### 3. Target Attribute

Controls where the response opens.

```html
<!-- Open in same tab (default) -->
<form action="response.html" target="_self">
</form>

<!-- Open in new tab -->
<form action="response.html" target="_blank">
</form>
```

---

# Input Types

The `<input>` tag is the most versatile form element with 15+ different types.

## 1. Text Input

For single-line text entry.

```html
<form>
    <label>Name:</label>
    <input type="text" name="username">
</form>
```

**Use for:** Names, usernames, single-line text

---

## 2. Password Input

Masks entered characters for security.

```html
<form>
    <label>Password:</label>
    <input type="password" name="password">
</form>
```

**Features:**
- Characters appear as dots (•••) or circles
- Hides sensitive information
- Use for passwords, PINs, OTPs

---

## 3. Email Input

Validates email format automatically.

```html
<form>
    <label>Email:</label>
    <input type="email" name="email">
</form>
```

**Browser Validation:**
- Checks for @ symbol
- Checks for domain (.com, .in, etc.)
- Shows error if format is wrong

---

## 4. Tel (Telephone) Input

For phone numbers.

```html
<form>
    <label>Mobile:</label>
    <input type="tel" name="mobile">
</form>
```

**Use for:** Mobile numbers, landline numbers

---

## 5. Number Input

For numeric values with increment/decrement controls.

```html
<form>
    <label>Age:</label>
    <input type="number" name="age">
</form>
```

**Features:**
- Up/down arrow buttons
- Mobile keyboard shows numbers
- Can set min, max, step values

---

## 6. Submit Button

Submits the form data.

```html
<form action="response.html">
    <input type="text" name="username">
    <input type="submit" value="Register">
</form>
```

**Default text:** "Submit"
**Custom text:** Use `value` attribute

---

## 7. Button

General purpose button (doesn't submit form by default).

```html
<input type="button" value="Click Me">
```

**Use for:** Custom actions with JavaScript

---

## 8. Reset Button

Clears all form data.

```html
<form>
    <input type="text" name="username">
    <input type="email" name="email">
    <input type="reset" value="Clear Form">
</form>
```

**Action:** Resets all fields to default values

---

## 9. Color Picker

Allows users to select colors.

```html
<form>
    <label>Favorite Color:</label>
    <input type="color" name="color">
</form>
```

**Features:**
- Opens color palette
- Returns hex color code
- Default: Black (#000000)

---

## 10. Hidden Input

Stores data invisibly (not shown to user).

```html
<form>
    <input type="hidden" name="user_id" value="12345">
</form>
```

**Use for:**
- User IDs
- Session tokens
- Tracking information
- Data set by JavaScript

---

## 11. Radio Buttons

Select ONE option from multiple choices.

```html
<form>
    <label>Gender:</label><br>
    <input type="radio" name="gender" value="male"> Male<br>
    <input type="radio" name="gender" value="female"> Female
</form>
```

**Important Rules:**
- Same `name` attribute for all options in a group
- Different `value` for each option
- Only one can be selected at a time

---

## 12. Checkboxes

Select MULTIPLE options.

```html
<form>
    <label>Languages Known:</label><br>
    <input type="checkbox" name="lang" value="english"> English<br>
    <input type="checkbox" name="lang" value="hindi"> Hindi<br>
    <input type="checkbox" name="lang" value="telugu"> Telugu
</form>
```

**Features:**
- Multiple selections allowed
- Each checkbox independent
- Use same `name` for related options

---

## 13. Range Slider

Select value from a range.

```html
<form>
    <label>Volume:</label>
    <input type="range" name="volume" min="0" max="100">
</form>
```

**Default:** 0 to 100
**Customizable:** Use min, max, step attributes

---

## 14. Date Picker

Select a date from calendar.

```html
<form>
    <label>Date of Birth:</label>
    <input type="date" name="dob">
</form>
```

**Format:** MM/DD/YYYY
**Features:** Calendar popup, year/month navigation

---

## 15. File Upload

Upload files from computer.

```html
<form>
    <label>Upload Document:</label>
    <input type="file" name="document">
</form>
```

**Use for:** Images, PDFs, documents, any file type

---

## 16. Search Input

Creates a search box.

```html
<form>
    <input type="search" name="query">
</form>
```

**Features:**
- Shows clear (X) button
- Pressing Enter submits form
- Optimized for search functionality

---

## 17. Time Picker

Select time (hours and minutes).

```html
<form>
    <label>Appointment Time:</label>
    <input type="time" name="appointment">
</form>
```

**Format:** HH:MM (24-hour or AM/PM)

---

## 18. Month Picker

Select month and year.

```html
<form>
    <label>Select Month:</label>
    <input type="month" name="month">
</form>
```

**Format:** YYYY-MM

---

## 19. Datetime-Local

Select date and time together.

```html
<form>
    <label>Event Date & Time:</label>
    <input type="datetime-local" name="event">
</form>
```

**Includes:** Date + Time selection

---

## 20. Week Picker

Select week number of the year.

```html
<form>
    <label>Select Week:</label>
    <input type="week" name="week">
</form>
```

**Format:** Week 40 of 2024

---

## 21. URL Input

For website addresses.

```html
<form>
    <label>Website:</label>
    <input type="url" name="website">
</form>
```

**Validation:** Checks for proper URL format (http://, https://)

---

# Input Attributes

## Essential Attributes

### 1. Name Attribute

**Most Important!** Identifies the field when sending data to server.

```html
<input type="text" name="username">
<input type="email" name="email">
<input type="password" name="password">
```

**Without name:** Data won't be sent to server

---

### 2. Value Attribute

Sets default or button text.

```html
<!-- Default text in field -->
<input type="text" name="city" value="Hyderabad">

<!-- Button text -->
<input type="submit" value="Register">
<input type="button" value="Click Me">
```

---

### 3. Placeholder Attribute

Shows hint text inside field.

```html
<input type="text" name="username" placeholder="Enter your name">
<input type="email" name="email" placeholder="example@email.com">
```

**Disappears** when user starts typing

---

### 4. Required Attribute

Makes field mandatory.

```html
<input type="text" name="username" required>
<input type="email" name="email" required>
```

**Browser shows error** if field is empty on submit

---

### 5. Maxlength Attribute

Limits maximum characters.

```html
<input type="text" name="username" maxlength="10">
```

**User cannot type** more than specified characters

---

### 6. Minlength Attribute

Sets minimum characters required.

```html
<input type="password" name="password" minlength="8">
```

**Browser validates** on submit

---

### 7. Min and Max Attributes

For number, date, and range inputs.

```html
<!-- Age between 18 and 60 -->
<input type="number" name="age" min="18" max="60">

<!-- Date range -->
<input type="date" name="dob" min="1960-01-01" max="2005-12-31">

<!-- Range slider -->
<input type="range" name="volume" min="0" max="100">
```

---

### 8. Step Attribute

Defines increment/decrement value.

```html
<!-- Increment by 5 -->
<input type="number" name="quantity" step="5">

<!-- Result: 0, 5, 10, 15, 20... -->
```

---

### 9. Disabled Attribute

Disables the field (cannot interact).

```html
<input type="text" name="username" disabled>
<input type="submit" value="Submit" disabled>
```

**Use case:** Disable submit until conditions met

---

### 10. Readonly Attribute

User can see but not edit.

```html
<input type="text" name="city" value="Hyderabad" readonly>
```

**Difference from disabled:**
- Readonly: Data is sent to server
- Disabled: Data is NOT sent to server

---

### 11. Checked Attribute

Pre-selects radio button or checkbox.

```html
<!-- Radio button -->
<input type="radio" name="gender" value="male" checked> Male
<input type="radio" name="gender" value="female"> Female

<!-- Checkbox -->
<input type="checkbox" name="terms" checked> I agree
```

---

### 12. Size Attribute

Sets visible width of input field.

```html
<input type="text" name="username" size="30">
```

**Note:** Width in characters, not pixels

---

# Textarea Tag

For multi-line text input.

## Syntax

```html
<textarea name="address" rows="5" cols="30">
Default text here
</textarea>
```

### Attributes

| Attribute | Purpose |
|-----------|---------|
| `rows` | Number of visible lines |
| `cols` | Number of visible characters per line |
| `name` | Field identifier (required) |

### Example

```html
<form>
    <label>Address:</label><br>
    <textarea name="address" rows="4" cols="40" placeholder="Enter your full address"></textarea>
</form>
```

**Features:**
- Resizable (drag bottom-right corner)
- Supports multiple lines
- Scrollbar appears if content exceeds rows

---

# Select Tag (Dropdown)

Creates dropdown menus.

## Basic Dropdown

```html
<form>
    <label>Select Language:</label>
    <select name="language">
        <option value="en">English</option>
        <option value="hi">Hindi</option>
        <option value="te">Telugu</option>
        <option value="ta">Tamil</option>
    </select>
</form>
```

### Select Attributes

#### 1. Multiple Selection

```html
<select name="languages" multiple>
    <option value="en">English</option>
    <option value="hi">Hindi</option>
    <option value="te">Telugu</option>
</select>
```

**Usage:** Hold Ctrl (Windows) or Cmd (Mac) and click

#### 2. Size Attribute

Shows multiple options without dropdown.

```html
<select name="language" size="3">
    <option value="en">English</option>
    <option value="hi">Hindi</option>
    <option value="te">Telugu</option>
    <option value="ta">Tamil</option>
</select>
```

**Shows 3 options** with scrollbar for rest

#### 3. Selected Attribute

Pre-selects an option.

```html
<select name="language">
    <option value="en">English</option>
    <option value="hi">Hindi</option>
    <option value="te" selected>Telugu</option>
</select>
```

### Option Tag Attributes

```html
<option value="en">English</option>
```

- **value:** Data sent to server
- **Text between tags:** What user sees

---

# Complete Form Examples

## Example 1: Registration Form

```html
<!DOCTYPE html>
<html>
<head>
    <title>Registration Form</title>
</head>
<body>
    <h2>User Registration</h2>
    <form action="response.html" method="post">
        <!-- Name -->
        <label>Full Name:</label><br>
        <input type="text" name="fullname" placeholder="Enter your name" required><br><br>
        
        <!-- Email -->
        <label>Email:</label><br>
        <input type="email" name="email" placeholder="example@email.com" required><br><br>
        
        <!-- Password -->
        <label>Password:</label><br>
        <input type="password" name="password" minlength="8" required><br><br>
        
        <!-- Mobile -->
        <label>Mobile Number:</label><br>
        <input type="tel" name="mobile" placeholder="+91 98765 43210" required><br><br>
        
        <!-- Date of Birth -->
        <label>Date of Birth:</label><br>
        <input type="date" name="dob" required><br><br>
        
        <!-- Gender -->
        <label>Gender:</label><br>
        <input type="radio" name="gender" value="male" required> Male
        <input type="radio" name="gender" value="female"> Female<br><br>
        
        <!-- Languages -->
        <label>Languages Known:</label><br>
        <input type="checkbox" name="lang" value="english"> English<br>
        <input type="checkbox" name="lang" value="hindi"> Hindi<br>
        <input type="checkbox" name="lang" value="telugu"> Telugu<br><br>
        
        <!-- City -->
        <label>City:</label><br>
        <select name="city" required>
            <option value="">Select City</option>
            <option value="hyderabad">Hyderabad</option>
            <option value="mumbai">Mumbai</option>
            <option value="delhi">Delhi</option>
            <option value="bangalore">Bangalore</option>
        </select><br><br>
        
        <!-- Address -->
        <label>Address:</label><br>
        <textarea name="address" rows="4" cols="40" placeholder="Enter full address"></textarea><br><br>
        
        <!-- Terms -->
        <input type="checkbox" name="terms" required> I agree to terms and conditions<br><br>
        
        <!-- Buttons -->
        <input type="submit" value="Register">
        <input type="reset" value="Clear Form">
    </form>
</body>
</html>
```

---

## Example 2: Contact Form

```html
<!DOCTYPE html>
<html>
<head>
    <title>Contact Us</title>
</head>
<body>
    <h2>Contact Form</h2>
    <form action="submit.php" method="post">
        <!-- Name -->
        <label>Your Name:</label><br>
        <input type="text" name="name" required><br><br>
        
        <!-- Email -->
        <label>Email Address:</label><br>
        <input type="email" name="email" required><br><br>
        
        <!-- Subject -->
        <label>Subject:</label><br>
        <input type="text" name="subject" required><br><br>
        
        <!-- Message -->
        <label>Message:</label><br>
        <textarea name="message" rows="6" cols="50" required></textarea><br><br>
        
        <!-- Submit -->
        <input type="submit" value="Send Message">
    </form>
</body>
</html>
```

---

## Example 3: Job Application Form

```html
<!DOCTYPE html>
<html>
<head>
    <title>Job Application</title>
</head>
<body>
    <h2>Job Application Form</h2>
    <form action="apply.php" method="post" enctype="multipart/form-data">
        <!-- Personal Information -->
        <h3>Personal Information</h3>
        
        <label>Full Name:</label><br>
        <input type="text" name="fullname" required><br><br>
        
        <label>Email:</label><br>
        <input type="email" name="email" required><br><br>
        
        <label>Phone:</label><br>
        <input type="tel" name="phone" required><br><br>
        
        <label>Date of Birth:</label><br>
        <input type="date" name="dob" required><br><br>
        
        <!-- Education -->
        <h3>Education</h3>
        
        <label>Highest Qualification:</label><br>
        <select name="qualification" required>
            <option value="">Select</option>
            <option value="10th">10th</option>
            <option value="12th">12th</option>
            <option value="graduate">Graduate</option>
            <option value="postgraduate">Post Graduate</option>
        </select><br><br>
        
        <!-- Experience -->
        <h3>Experience</h3>
        
        <label>Years of Experience:</label><br>
        <input type="number" name="experience" min="0" max="50"><br><br>
        
        <label>Current Company:</label><br>
        <input type="text" name="company"><br><br>
        
        <!-- Skills -->
        <h3>Skills</h3>
        
        <input type="checkbox" name="skills" value="html"> HTML<br>
        <input type="checkbox" name="skills" value="css"> CSS<br>
        <input type="checkbox" name="skills" value="javascript"> JavaScript<br>
        <input type="checkbox" name="skills" value="python"> Python<br><br>
        
        <!-- Resume Upload -->
        <label>Upload Resume:</label><br>
        <input type="file" name="resume" required><br><br>
        
        <!-- Availability -->
        <label>Available to Join:</label><br>
        <input type="date" name="joindate"><br><br>
        
        <!-- Expected Salary -->
        <label>Expected Salary (₹):</label><br>
        <input type="number" name="salary" min="0" step="1000"><br><br>
        
        <!-- Submit -->
        <input type="submit" value="Submit Application">
    </form>
</body>
</html>
```

---

## Example 4: Survey Form

```html
<!DOCTYPE html>
<html>
<head>
    <title>Customer Survey</title>
</head>
<body>
    <h2>Customer Satisfaction Survey</h2>
    <form action="survey.php" method="post">
        <!-- Name -->
        <label>Name:</label><br>
        <input type="text" name="name" required><br><br>
        
        <!-- Email -->
        <label>Email:</label><br>
        <input type="email" name="email" required><br><br>
        
        <!-- Rating -->
        <label>Rate our service (1-10):</label><br>
        <input type="range" name="rating" min="1" max="10" value="5"><br><br>
        
        <!-- Satisfaction -->
        <label>How satisfied are you?</label><br>
        <input type="radio" name="satisfaction" value="very_satisfied"> Very Satisfied<br>
        <input type="radio" name="satisfaction" value="satisfied"> Satisfied<br>
        <input type="radio" name="satisfaction" value="neutral"> Neutral<br>
        <input type="radio" name="satisfaction" value="dissatisfied"> Dissatisfied<br><br>
        
        <!-- Feedback -->
        <label>Additional Feedback:</label><br>
        <textarea name="feedback" rows="5" cols="50"></textarea><br><br>
        
        <!-- Submit -->
        <input type="submit" value="Submit Survey">
    </form>
</body>
</html>
```

---

# Form Validation

## Browser Built-in Validation

### Required Fields
```html
<input type="text" name="username" required>
```

### Email Validation
```html
<input type="email" name="email" required>
```

### URL Validation
```html
<input type="url" name="website" required>
```

### Number Range
```html
<input type="number" name="age" min="18" max="60" required>
```

### Text Length
```html
<input type="text" name="username" minlength="3" maxlength="20" required>
```

### Pattern Matching
```html
<!-- Only letters -->
<input type="text" name="name" pattern="[A-Za-z]+" required>

<!-- Phone number (10 digits) -->
<input type="tel" name="phone" pattern="[0-9]{10}" required>
```

---

# Best Practices

## 1. Always Use Labels
```html
<label for="username">Username:</label>
<input type="text" id="username" name="username">
```

## 2. Use Appropriate Input Types
- Email for emails
- Tel for phone numbers
- Number for numeric values
- Date for dates

## 3. Provide Clear Placeholders
```html
<input type="email" placeholder="example@email.com">
```

## 4. Use Required Attribute
```html
<input type="text" name="username" required>
```

## 5. Group Related Fields
```html
<fieldset>
    <legend>Personal Information</legend>
    <!-- fields here -->
</fieldset>
```

## 6. Use POST for Sensitive Data
```html
<form method="post">
    <input type="password" name="password">
</form>
```

---

# Common Mistakes to Avoid

### 1. Missing Name Attribute
```html
<!-- Wrong: No name -->
<input type="text">

<!-- Correct -->
<input type="text" name="username">
```

### 2. Wrong Radio Button Grouping
```html
<!-- Wrong: Different names -->
<input type="radio" name="gender1" value="male"> Male
<input type="radio" name="gender2" value="female"> Female

<!-- Correct: Same name -->
<input type="radio" name="gender" value="male"> Male
<input type="radio" name="gender" value="female"> Female
```

### 3. Forgetting Form Tag
```html
<!-- Wrong: No form tag -->
<input type="text" name="username">
<input type="submit">

<!-- Correct -->
<form action="submit.php" method="post">
    <input type="text" name="username">
    <input type="submit">
</form>
```

---

# Summary

## Form Elements

| Element | Purpose |
|---------|---------|
| `<form>` | Container for form |
| `<input>` | Various input types |
| `<textarea>` | Multi-line text |
| `<select>` | Dropdown menu |
| `<option>` | Dropdown options |
| `<button>` | Clickable button |
| `<label>` | Field label |

## Essential Attributes

| Attribute | Purpose |
|-----------|---------|
| `name` | Field identifier |
| `value` | Default/button text |
| `placeholder` | Hint text |
| `required` | Mandatory field |
| `minlength/maxlength` | Text length limits |
| `min/max` | Number/date limits |
| `readonly` | View only |
| `disabled` | Cannot interact |

## Input Types Summary

- **Text:** text, password, email, tel, url, search
- **Numbers:** number, range
- **Date/Time:** date, time, month, week, datetime-local
- **Selection:** radio, checkbox, color, file
- **Buttons:** submit, reset, button
- **Special:** hidden

Forms are the backbone of user interaction on websites. Master these concepts to create professional, user-friendly forms!

---

*Congratulations! You've completed Day 7. Next, we'll learn about CSS styling!*