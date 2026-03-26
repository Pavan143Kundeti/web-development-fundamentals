# Day 8: HTML5 Multimedia - Audio, Video, Details & Iframe

## Overview

This lesson covers:
1. **Audio Tag** - Embedding audio files
2. **Video Tag** - Embedding video files
3. **Details/Summary Tags** - Collapsible content sections
4. **Iframe Tag** - Embedding external content

---

# Part 1: Audio Tag

## What is the Audio Tag?

The `<audio>` tag embeds audio files (music, podcasts, sound effects) into web pages.

### Basic Syntax

```html
<audio src="audio-file.mp3" controls>
    Your browser does not support audio.
</audio>
```

---

## Audio Attributes

### 1. Controls Attribute

Shows play, pause, volume, and download buttons.

```html
<audio src="song.mp3" controls>
    Your browser does not support audio.
</audio>
```

**Without controls:** Audio won't be visible or playable

---

### 2. Autoplay Attribute

Starts playing automatically when page loads.

```html
<audio src="song.mp3" controls autoplay>
    Your browser does not support audio.
</audio>
```

**Note:** Most browsers block autoplay with sound for better user experience

---

### 3. Loop Attribute

Repeats audio continuously.

```html
<audio src="background-music.mp3" controls loop>
    Your browser does not support audio.
</audio>
```

**Use case:** Background music, ambient sounds

---

### 4. Muted Attribute

Starts with sound muted.

```html
<audio src="song.mp3" controls muted>
    Your browser does not support audio.
</audio>
```

**User can unmute** by clicking volume button

---

## Supported Audio Formats

| Format | Extension | Browser Support |
|--------|-----------|-----------------|
| MP3 | .mp3 | All modern browsers |
| WAV | .wav | All modern browsers |
| OGG | .ogg | Firefox, Chrome, Opera |

---

## Multiple Source Files

Provide multiple formats for better browser compatibility.

```html
<audio controls>
    <source src="song.mp3" type="audio/mpeg">
    <source src="song.ogg" type="audio/ogg">
    <source src="song.wav" type="audio/wav">
    Your browser does not support audio.
</audio>
```

**Browser picks** the first format it supports

---

## Complete Audio Examples

### Example 1: Simple Audio Player

```html
<!DOCTYPE html>
<html>
<head>
    <title>Audio Player</title>
</head>
<body>
    <h2>Listen to Our Podcast</h2>
    <audio src="podcast.mp3" controls>
        Your browser does not support the audio element.
    </audio>
</body>
</html>
```

### Example 2: Background Music

```html
<audio src="background.mp3" autoplay loop muted>
    Your browser does not support audio.
</audio>
```

### Example 3: Multiple Audio Files

```html
<h3>Song 1</h3>
<audio src="song1.mp3" controls></audio>

<h3>Song 2</h3>
<audio src="song2.mp3" controls></audio>

<h3>Song 3</h3>
<audio src="song3.mp3" controls></audio>
```

---

# Part 2: Video Tag

## What is the Video Tag?

The `<video>` tag embeds video files into web pages.

### Basic Syntax

```html
<video src="video-file.mp4" controls width="640" height="360">
    Your browser does not support video.
</video>
```

---

## Video Attributes

### 1. Controls Attribute (Required)

Shows play, pause, volume, fullscreen, and download buttons.

```html
<video src="movie.mp4" controls>
    Your browser does not support video.
</video>
```

**Without controls:** Video won't be playable

---

### 2. Width and Height

Sets video player dimensions.

```html
<!-- Using pixels -->
<video src="movie.mp4" controls width="640" height="360">
</video>

<!-- Using percentages -->
<video src="movie.mp4" controls width="100%">
</video>
```

---

### 3. Autoplay Attribute

Starts playing automatically.

```html
<video src="intro.mp4" controls autoplay>
    Your browser does not support video.
</video>
```

**Note:** Most browsers require `muted` with autoplay

---

### 4. Loop Attribute

Repeats video continuously.

```html
<video src="animation.mp4" controls loop>
    Your browser does not support video.
</video>
```

---

### 5. Muted Attribute

Starts with sound off.

```html
<video src="movie.mp4" controls muted>
    Your browser does not support video.
</video>
```

---

### 6. Poster Attribute

Shows thumbnail image before video plays.

```html
<video src="movie.mp4" controls poster="thumbnail.jpg" width="640" height="360">
    Your browser does not support video.
</video>
```

**Poster image** displays until user clicks play

---

## Supported Video Formats

| Format | Extension | Browser Support |
|--------|-----------|-----------------|
| MP4 | .mp4 | All modern browsers (Recommended) |
| WebM | .webm | Chrome, Firefox, Opera |
| OGG | .ogg | Firefox, Chrome, Opera |

---

## Multiple Source Files

```html
<video controls width="640" height="360">
    <source src="movie.mp4" type="video/mp4">
    <source src="movie.webm" type="video/webm">
    <source src="movie.ogg" type="video/ogg">
    Your browser does not support the video tag.
</video>
```

---

## Complete Video Examples

### Example 1: Basic Video Player

```html
<!DOCTYPE html>
<html>
<head>
    <title>Video Player</title>
</head>
<body>
    <h2>Watch Our Tutorial</h2>
    <video src="tutorial.mp4" controls width="800" height="450">
        Your browser does not support the video tag.
    </video>
</body>
</html>
```

### Example 2: Video with Poster

```html
<video src="movie.mp4" controls poster="movie-poster.jpg" width="640" height="360">
    Your browser does not support video.
</video>
```

### Example 3: Autoplay Muted Video

```html
<video src="intro.mp4" autoplay muted loop width="100%">
    Your browser does not support video.
</video>
```

### Example 4: Multiple Videos

```html
<h3>Video 1: Introduction</h3>
<video src="intro.mp4" controls width="640" height="360"></video>

<h3>Video 2: Tutorial</h3>
<video src="tutorial.mp4" controls width="640" height="360"></video>

<h3>Video 3: Conclusion</h3>
<video src="conclusion.mp4" controls width="640" height="360"></video>
```

---

# Part 3: Details and Summary Tags

## What are Details/Summary Tags?

Create collapsible content sections that users can expand/collapse by clicking.

### Basic Syntax

```html
<details>
    <summary>Click to expand</summary>
    <p>Hidden content goes here</p>
</details>
```

---

## How It Works

- **Summary:** The visible heading (always shown)
- **Details:** Container for collapsible content
- **Click summary:** Content expands/collapses

---

## Details/Summary Examples

### Example 1: Simple Collapsible Section

```html
<details>
    <summary>What is HTML?</summary>
    <p>HTML stands for HyperText Markup Language. It is used to create web pages.</p>
</details>
```

**Output:**
- Closed: ▶ What is HTML?
- Open: ▼ What is HTML?
        HTML stands for HyperText Markup Language...

---

### Example 2: FAQ Section

```html
<!DOCTYPE html>
<html>
<head>
    <title>FAQ</title>
</head>
<body>
    <h2>Frequently Asked Questions</h2>
    
    <details>
        <summary>What is web development?</summary>
        <p>Web development is the process of creating websites and web applications using HTML, CSS, and JavaScript.</p>
    </details>
    
    <details>
        <summary>How long does it take to learn HTML?</summary>
        <p>Basic HTML can be learned in 1-2 weeks with consistent practice. Mastery takes several months.</p>
    </details>
    
    <details>
        <summary>Do I need to know programming?</summary>
        <p>No, HTML is a markup language, not a programming language. It's beginner-friendly and easy to learn.</p>
    </details>
    
    <details>
        <summary>What tools do I need?</summary>
        <p>You only need a text editor (like VS Code) and a web browser to start learning HTML.</p>
    </details>
</body>
</html>
```

---

### Example 3: Course Modules

```html
<h2>Course Content</h2>

<details>
    <summary>Module 1: HTML Basics</summary>
    <ul>
        <li>Introduction to HTML</li>
        <li>HTML Tags and Elements</li>
        <li>Document Structure</li>
        <li>Text Formatting</li>
    </ul>
</details>

<details>
    <summary>Module 2: HTML Forms</summary>
    <ul>
        <li>Form Elements</li>
        <li>Input Types</li>
        <li>Form Validation</li>
        <li>Submit and Reset</li>
    </ul>
</details>

<details>
    <summary>Module 3: Multimedia</summary>
    <ul>
        <li>Images</li>
        <li>Audio</li>
        <li>Video</li>
        <li>Embedding Content</li>
    </ul>
</details>
```

---

### Example 4: Product Details

```html
<h2>Product Information</h2>

<details>
    <summary>Product Specifications</summary>
    <table border="1" cellpadding="10">
        <tr>
            <td>Brand</td>
            <td>Samsung</td>
        </tr>
        <tr>
            <td>Model</td>
            <td>Galaxy S24</td>
        </tr>
        <tr>
            <td>Storage</td>
            <td>256GB</td>
        </tr>
        <tr>
            <td>RAM</td>
            <td>8GB</td>
        </tr>
    </table>
</details>

<details>
    <summary>Shipping Information</summary>
    <p>Free shipping on orders above ₹500</p>
    <p>Delivery in 3-5 business days</p>
    <p>Cash on Delivery available</p>
</details>

<details>
    <summary>Return Policy</summary>
    <p>30-day return policy</p>
    <p>Product must be in original condition</p>
    <p>Refund processed within 7 days</p>
</details>
```

---

### Example 5: Open by Default

Use `open` attribute to show content by default.

```html
<details open>
    <summary>Important Notice</summary>
    <p>This section is expanded by default. Users can still collapse it.</p>
</details>
```

---

## Benefits of Details/Summary

1. **Saves Space** - Hides content until needed
2. **Better Organization** - Groups related information
3. **User Control** - Users decide what to view
4. **No JavaScript** - Works with pure HTML
5. **Accessibility** - Screen reader friendly

---

# Part 4: Iframe Tag

## What is an Iframe?

Iframe (Inline Frame) embeds another HTML document or external content within the current page.

### Basic Syntax

```html
<iframe src="url-or-file-path" width="600" height="400">
    Your browser does not support iframes.
</iframe>
```

---

## Iframe Attributes

### 1. Src (Source)

URL or file path to embed.

```html
<iframe src="page.html"></iframe>
<iframe src="https://www.example.com"></iframe>
```

---

### 2. Width and Height

Sets iframe dimensions.

```html
<!-- Pixels -->
<iframe src="page.html" width="800" height="600"></iframe>

<!-- Percentage -->
<iframe src="page.html" width="100%" height="500"></iframe>
```

---

### 3. Frameborder

Shows or hides border (deprecated, use CSS instead).

```html
<!-- No border -->
<iframe src="page.html" frameborder="0"></iframe>

<!-- With border -->
<iframe src="page.html" frameborder="1"></iframe>
```

**Modern approach:** Use CSS `border: none;`

---

### 4. Scrolling

Controls scrollbar visibility.

```html
<!-- Auto (default) -->
<iframe src="page.html" scrolling="auto"></iframe>

<!-- Always show -->
<iframe src="page.html" scrolling="yes"></iframe>

<!-- Never show -->
<iframe src="page.html" scrolling="no"></iframe>
```

---

## Common Iframe Uses

### 1. Embedding Another HTML Page

```html
<iframe src="contact.html" width="100%" height="400">
    Your browser does not support iframes.
</iframe>
```

---

### 2. Embedding YouTube Videos

```html
<!-- Get embed code from YouTube -->
<iframe 
    width="560" 
    height="315" 
    src="https://www.youtube.com/embed/VIDEO_ID" 
    frameborder="0" 
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
    allowfullscreen>
</iframe>
```

**Steps to embed YouTube video:**
1. Go to YouTube video
2. Click "Share"
3. Click "Embed"
4. Copy the iframe code
5. Paste in your HTML

---

### 3. Embedding Google Maps

```html
<iframe 
    src="https://www.google.com/maps/embed?pb=..." 
    width="600" 
    height="450" 
    style="border:0;" 
    allowfullscreen="" 
    loading="lazy">
</iframe>
```

**Steps to embed Google Maps:**
1. Go to Google Maps
2. Search for location
3. Click "Share"
4. Click "Embed a map"
5. Copy the iframe code

---

### 4. Embedding PDF Documents

```html
<iframe 
    src="document.pdf" 
    width="100%" 
    height="600" 
    style="border: none;">
    Your browser does not support PDFs.
    <a href="document.pdf">Download PDF</a>
</iframe>
```

**Features:**
- View PDF in browser
- Download option
- Print option
- Zoom controls

---

### 5. Embedding External Websites

```html
<iframe 
    src="https://www.wikipedia.org" 
    width="100%" 
    height="600" 
    style="border: 1px solid #ccc;">
</iframe>
```

**Note:** Some websites block iframe embedding for security

---

## Complete Iframe Examples

### Example 1: Embedding Local Page

```html
<!DOCTYPE html>
<html>
<head>
    <title>Main Page</title>
</head>
<body>
    <h1>Welcome to Our Website</h1>
    
    <h2>Contact Form</h2>
    <iframe src="contact.html" width="100%" height="400" style="border: 1px solid #ddd;">
    </iframe>
    
    <h2>About Us</h2>
    <iframe src="about.html" width="100%" height="300" style="border: 1px solid #ddd;">
    </iframe>
</body>
</html>
```

---

### Example 2: YouTube Video Gallery

```html
<!DOCTYPE html>
<html>
<head>
    <title>Video Gallery</title>
</head>
<body>
    <h1>Our Video Tutorials</h1>
    
    <h2>Tutorial 1: HTML Basics</h2>
    <iframe 
        width="560" 
        height="315" 
        src="https://www.youtube.com/embed/VIDEO_ID_1" 
        frameborder="0" 
        allowfullscreen>
    </iframe>
    
    <h2>Tutorial 2: CSS Styling</h2>
    <iframe 
        width="560" 
        height="315" 
        src="https://www.youtube.com/embed/VIDEO_ID_2" 
        frameborder="0" 
        allowfullscreen>
    </iframe>
</body>
</html>
```

---

### Example 3: Google Maps Location

```html
<!DOCTYPE html>
<html>
<head>
    <title>Our Location</title>
</head>
<body>
    <h1>Visit Our Office</h1>
    <p>123 Main Street, Hyderabad, India</p>
    
    <iframe 
        src="https://www.google.com/maps/embed?pb=YOUR_MAP_CODE" 
        width="100%" 
        height="450" 
        style="border:0;" 
        allowfullscreen="" 
        loading="lazy">
    </iframe>
</body>
</html>
```

---

### Example 4: PDF Viewer

```html
<!DOCTYPE html>
<html>
<head>
    <title>Document Viewer</title>
</head>
<body>
    <h1>Company Report 2024</h1>
    
    <iframe 
        src="report.pdf" 
        width="100%" 
        height="800" 
        style="border: 1px solid #ccc;">
        <p>Your browser does not support PDFs.</p>
        <p><a href="report.pdf">Download the PDF</a></p>
    </iframe>
</body>
</html>
```

---

### Example 5: Multiple Iframes Layout

```html
<!DOCTYPE html>
<html>
<head>
    <title>Dashboard</title>
    <style>
        .iframe-container {
            display: flex;
            gap: 20px;
            margin: 20px 0;
        }
        iframe {
            border: 2px solid #ddd;
            border-radius: 5px;
        }
    </style>
</head>
<body>
    <h1>Company Dashboard</h1>
    
    <div class="iframe-container">
        <iframe src="sales.html" width="48%" height="400"></iframe>
        <iframe src="analytics.html" width="48%" height="400"></iframe>
    </div>
    
    <div class="iframe-container">
        <iframe src="reports.html" width="100%" height="400"></iframe>
    </div>
</body>
</html>
```

---

## Iframe Security Considerations

### 1. Sandbox Attribute

Restricts iframe capabilities for security.

```html
<iframe src="untrusted.html" sandbox></iframe>
```

**Sandbox restrictions:**
- No JavaScript execution
- No form submission
- No plugins
- No top navigation

### 2. Allow Specific Features

```html
<iframe 
    src="page.html" 
    sandbox="allow-scripts allow-forms">
</iframe>
```

---

## Complete Project Example

### Main Page with All Multimedia Elements

```html
<!DOCTYPE html>
<html>
<head>
    <title>Multimedia Showcase</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        section {
            margin: 40px 0;
            padding: 20px;
            background-color: #f5f5f5;
            border-radius: 8px;
        }
        h2 {
            color: #333;
            border-bottom: 2px solid #4CAF50;
            padding-bottom: 10px;
        }
        details {
            margin: 10px 0;
            padding: 10px;
            background-color: white;
            border-radius: 5px;
        }
        summary {
            cursor: pointer;
            font-weight: bold;
            padding: 10px;
        }
        iframe {
            border: none;
            border-radius: 5px;
        }
    </style>
</head>
<body>
    <h1>Welcome to Our Multimedia Website</h1>
    
    <!-- Audio Section -->
    <section>
        <h2>🎵 Audio Player</h2>
        <p>Listen to our latest podcast episode:</p>
        <audio controls>
            <source src="podcast.mp3" type="audio/mpeg">
            <source src="podcast.ogg" type="audio/ogg">
            Your browser does not support audio.
        </audio>
    </section>
    
    <!-- Video Section -->
    <section>
        <h2>🎬 Video Tutorial</h2>
        <p>Watch our introduction video:</p>
        <video controls width="100%" poster="video-thumbnail.jpg">
            <source src="intro.mp4" type="video/mp4">
            <source src="intro.webm" type="video/webm">
            Your browser does not support video.
        </video>
    </section>
    
    <!-- Details/Summary Section -->
    <section>
        <h2>❓ Frequently Asked Questions</h2>
        
        <details>
            <summary>What services do you offer?</summary>
            <p>We offer web development, mobile app development, and digital marketing services.</p>
        </details>
        
        <details>
            <summary>What are your working hours?</summary>
            <p>We are available Monday to Friday, 9 AM to 6 PM IST.</p>
        </details>
        
        <details>
            <summary>How can I contact support?</summary>
            <p>Email: support@example.com<br>Phone: +91 98765 43210</p>
        </details>
        
        <details open>
            <summary>Special Offer!</summary>
            <p style="color: red; font-weight: bold;">Get 20% off on all services this month!</p>
        </details>
    </section>
    
    <!-- YouTube Iframe Section -->
    <section>
        <h2>📺 Featured Videos</h2>
        <iframe 
            width="100%" 
            height="400" 
            src="https://www.youtube.com/embed/VIDEO_ID" 
            allowfullscreen>
        </iframe>
    </section>
    
    <!-- Google Maps Section -->
    <section>
        <h2>📍 Our Location</h2>
        <p>Visit us at our office:</p>
        <iframe 
            src="https://www.google.com/maps/embed?pb=YOUR_MAP_CODE" 
            width="100%" 
            height="400" 
            allowfullscreen 
            loading="lazy">
        </iframe>
    </section>
    
    <!-- PDF Document Section -->
    <section>
        <h2>📄 Company Brochure</h2>
        <iframe 
            src="brochure.pdf" 
            width="100%" 
            height="600">
            <p>Your browser does not support PDFs.</p>
            <p><a href="brochure.pdf">Download Brochure</a></p>
        </iframe>
    </section>
</body>
</html>
```

---

## Summary

### Audio Tag
- Embeds audio files (MP3, WAV, OGG)
- Attributes: controls, autoplay, loop, muted
- Use `<source>` for multiple formats

### Video Tag
- Embeds video files (MP4, WebM, OGG)
- Attributes: controls, width, height, poster, autoplay, loop, muted
- MP4 recommended for best compatibility

### Details/Summary
- Creates collapsible sections
- No JavaScript needed
- Great for FAQs, course modules, product details
- Use `open` attribute to expand by default

### Iframe
- Embeds external content
- Use for: YouTube videos, Google Maps, PDFs, other websites
- Attributes: src, width, height, frameborder, scrolling
- Security: Use `sandbox` attribute for untrusted content

---

## Best Practices

1. **Always provide fallback content** for unsupported browsers
2. **Use controls attribute** for audio and video
3. **Optimize file sizes** for faster loading
4. **Use appropriate formats** (MP4 for video, MP3 for audio)
5. **Set dimensions** for iframes to prevent layout issues
6. **Test across browsers** for compatibility
7. **Consider mobile users** - use responsive dimensions
8. **Respect copyright** - only embed content you have rights to use

---

*Congratulations! You've completed Day 8. You now know how to add rich multimedia content to your websites!*