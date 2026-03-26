# JavaScript Day 24: AJAX and XMLHttpRequest

## Introduction

AJAX (Asynchronous JavaScript And XML) allows you to update parts of a web page without reloading the entire page. It's the technology behind modern interactive websites.

**Think of AJAX like checking your mailbox: you can check for new mail without leaving your house and rebuilding it.**

---

## Part 1: What is AJAX?

### AJAX Definition

AJAX = Asynchronous JavaScript And XML

AJAX is not a programming language. It's a technique that combines:
- XMLHttpRequest object (to request data)
- JavaScript and HTML DOM (to display data)

### What AJAX Can Do

| Action | Description |
|--------|-------------|
| Read data | Get data from server after page loads |
| Update page | Change content without reloading |
| Send data | Send data to server in background |
| Async operations | Don't freeze the page |

### Visual: Traditional vs AJAX

```
Traditional Web:
User clicks → Page reloads → Server responds → New page loads
(Page freezes during reload)

AJAX:
User clicks → Request sent → Page stays active → Update part of page
(Page stays responsive)
```

---

## Part 2: How AJAX Works

### AJAX Flow

```
1. Event occurs (button click, page load)
    ↓
2. JavaScript creates XMLHttpRequest
    ↓
3. XMLHttpRequest sends request to server
    ↓
4. Server processes request
    ↓
5. Server sends response back
    ↓
6. JavaScript reads response
    ↓
7. JavaScript updates page
```

### Visual: AJAX Communication

```
Browser                    Server
   │                          │
   │──── Request ────────────>│
   │                          │
   │  (Page stays active)     │
   │                          │
   │<──── Response ───────────│
   │                          │
   │  Update part of page     │
```

---

## Part 3: The XMLHttpRequest Object

### Creating XMLHttpRequest

```javascript
const xhttp = new XMLHttpRequest();
```

All modern browsers support XMLHttpRequest.

### Basic AJAX Example

```javascript
// Create XMLHttpRequest object
const xhttp = new XMLHttpRequest();

// Define callback function
xhttp.onload = function() {
    document.getElementById("demo").innerHTML = this.responseText;
};

// Send request
xhttp.open("GET", "ajax_info.txt");
xhttp.send();
```

---

## Part 4: XMLHttpRequest Methods

### Essential Methods

| Method | Description |
|--------|-------------|
| `new XMLHttpRequest()` | Create new object |
| `open(method, url, async)` | Specify request details |
| `send()` | Send GET request |
| `send(string)` | Send POST request |
| `abort()` | Cancel request |
| `setRequestHeader()` | Add HTTP header |
| `getAllResponseHeaders()` | Get all headers |
| `getResponseHeader()` | Get specific header |

### The open() Method

```javascript
xhttp.open(method, url, async);
```

**Parameters:**
- `method`: "GET" or "POST"
- `url`: File location
- `async`: true (asynchronous) or false (synchronous)

### The send() Method

```javascript
// For GET requests
xhttp.send();

// For POST requests
xhttp.send("fname=John&lname=Doe");
```

---

## Part 5: XMLHttpRequest Properties

### Important Properties

| Property | Description |
|----------|-------------|
| `onload` | Function to call when loaded |
| `onreadystatechange` | Function to call when state changes |
| `readyState` | Request status (0-4) |
| `responseText` | Response as string |
| `responseXML` | Response as XML |
| `status` | HTTP status code (200, 404, etc.) |
| `statusText` | Status text ("OK", "Not Found") |

### readyState Values

| Value | State | Description |
|-------|-------|-------------|
| 0 | UNSENT | Request not initialized |
| 1 | OPENED | Server connection established |
| 2 | HEADERS_RECEIVED | Request received |
| 3 | LOADING | Processing request |
| 4 | DONE | Request finished, response ready |

---

## Part 6: Using onload

### The onload Property

```javascript
const xhttp = new XMLHttpRequest();

xhttp.onload = function() {
    // This runs when response is ready
    document.getElementById("demo").innerHTML = this.responseText;
};

xhttp.open("GET", "ajax_info.txt");
xhttp.send();
```

### Complete Example

```html
<!DOCTYPE html>
<html>
<body>

<div id="demo">
    <h2>Let AJAX change this text</h2>
    <button onclick="loadDoc()">Change Content</button>
</div>

<script>
function loadDoc() {
    const xhttp = new XMLHttpRequest();
    
    xhttp.onload = function() {
        document.getElementById("demo").innerHTML = this.responseText;
    };
    
    xhttp.open("GET", "ajax_info.txt");
    xhttp.send();
}
</script>

</body>
</html>
```

---

## Part 7: Using onreadystatechange

### The onreadystatechange Property

```javascript
const xhttp = new XMLHttpRequest();

xhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
        document.getElementById("demo").innerHTML = this.responseText;
    }
};

xhttp.open("GET", "ajax_info.txt");
xhttp.send();
```

### Why Check readyState and status?

```javascript
if (this.readyState == 4 && this.status == 200) {
    // readyState 4 = request finished
    // status 200 = OK
    // Safe to use response
}
```

### Visual: onreadystatechange Events

```
Request starts
    ↓
readyState = 1 → onreadystatechange fires
    ↓
readyState = 2 → onreadystatechange fires
    ↓
readyState = 3 → onreadystatechange fires
    ↓
readyState = 4 → onreadystatechange fires
(Check status here!)
```

---

## Part 8: GET Requests

### Simple GET Request

```javascript
xhttp.open("GET", "demo_get.asp");
xhttp.send();
```

### Avoid Cached Results

Add unique ID to URL:

```javascript
xhttp.open("GET", "demo_get.asp?t=" + Math.random());
xhttp.send();
```

### Send Information with GET

```javascript
xhttp.open("GET", "demo_get2.asp?fname=Henry&lname=Ford");
xhttp.send();
```

### Example: GET with Parameters

```javascript
function loadUser(userId) {
    const xhttp = new XMLHttpRequest();
    
    xhttp.onload = function() {
        document.getElementById("demo").innerHTML = this.responseText;
    };
    
    xhttp.open("GET", "getuser.php?id=" + userId);
    xhttp.send();
}
```

---

## Part 9: POST Requests

### Simple POST Request

```javascript
xhttp.open("POST", "demo_post.asp");
xhttp.send();
```

### POST with Data

```javascript
xhttp.open("POST", "ajax_test.asp");
xhttp.setRequestHeader("Content-type", "application/x-www-form-urlencoded");
xhttp.send("fname=Henry&lname=Ford");
```

### Example: POST Form Data

```javascript
function submitForm() {
    const xhttp = new XMLHttpRequest();
    
    xhttp.onload = function() {
        document.getElementById("result").innerHTML = this.responseText;
    };
    
    xhttp.open("POST", "submit.php");
    xhttp.setRequestHeader("Content-type", "application/x-www-form-urlencoded");
    xhttp.send("name=John&email=john@example.com");
}
```

---

## Part 10: GET vs POST

### When to Use GET

✅ Use GET when:
- Retrieving data
- Request is idempotent (doesn't change server state)
- Data is not sensitive
- Small amount of data

### When to Use POST

✅ Use POST when:
- Sending large amounts of data
- Updating server data
- Sending sensitive information
- Sending user input
- File uploads

### Comparison Table

| Feature | GET | POST |
|---------|-----|------|
| Data in URL | Yes | No |
| Cached | Yes | No |
| Bookmarkable | Yes | No |
| Size limit | Yes (~2000 chars) | No limit |
| Security | Less secure | More secure |

---

## Part 11: Handling Responses

### responseText Property

Get response as string:

```javascript
xhttp.onload = function() {
    document.getElementById("demo").innerHTML = this.responseText;
};
```

### responseXML Property

Get response as XML:

```javascript
xhttp.onload = function() {
    const xmlDoc = this.responseXML;
    const x = xmlDoc.getElementsByTagName("ARTIST");
    
    let txt = "";
    for (let i = 0; i < x.length; i++) {
        txt += x[i].childNodes[0].nodeValue + "<br>";
    }
    
    document.getElementById("demo").innerHTML = txt;
};
```

---

## Part 12: Response Headers

### getAllResponseHeaders()

Get all headers:

```javascript
const xhttp = new XMLHttpRequest();

xhttp.onload = function() {
    document.getElementById("demo").innerHTML = 
        this.getAllResponseHeaders();
};

xhttp.open("GET", "ajax_info.txt");
xhttp.send();
```

### getResponseHeader()

Get specific header:

```javascript
const xhttp = new XMLHttpRequest();

xhttp.onload = function() {
    document.getElementById("demo").innerHTML = 
        this.getResponseHeader("Last-Modified");
};

xhttp.open("GET", "ajax_info.txt");
xhttp.send();
```

---

## Part 13: Multiple Callback Functions

### Reusable AJAX Function

```javascript
function loadDoc(url, callback) {
    const xhttp = new XMLHttpRequest();
    
    xhttp.onload = function() {
        callback(this);
    };
    
    xhttp.open("GET", url);
    xhttp.send();
}

// Use it
loadDoc("url-1", myFunction1);
loadDoc("url-2", myFunction2);

function myFunction1(xhttp) {
    document.getElementById("demo1").innerHTML = xhttp.responseText;
}

function myFunction2(xhttp) {
    document.getElementById("demo2").innerHTML = xhttp.responseText;
}
```

---

## Part 14: Practical Examples

### Example 1: Load Text File

```html
<button onclick="loadDoc()">Load Text</button>
<div id="demo"></div>

<script>
function loadDoc() {
    const xhttp = new XMLHttpRequest();
    
    xhttp.onload = function() {
        document.getElementById("demo").innerHTML = this.responseText;
    };
    
    xhttp.open("GET", "ajax_info.txt");
    xhttp.send();
}
</script>
```

### Example 2: Search Suggestions

```html
<input type="text" onkeyup="showHint(this.value)" placeholder="Type a name">
<p>Suggestions: <span id="txtHint"></span></p>

<script>
function showHint(str) {
    if (str.length == 0) {
        document.getElementById("txtHint").innerHTML = "";
        return;
    }
    
    const xhttp = new XMLHttpRequest();
    
    xhttp.onload = function() {
        document.getElementById("txtHint").innerHTML = this.responseText;
    };
    
    xhttp.open("GET", "gethint.php?q=" + str);
    xhttp.send();
}
</script>
```

### Example 3: Load Database Data

```html
<select onchange="showCustomer(this.value)">
    <option value="">Select a customer:</option>
    <option value="1">Customer 1</option>
    <option value="2">Customer 2</option>
</select>

<div id="txtHint">Customer info will be listed here...</div>

<script>
function showCustomer(str) {
    if (str == "") {
        document.getElementById("txtHint").innerHTML = "";
        return;
    }
    
    const xhttp = new XMLHttpRequest();
    
    xhttp.onload = function() {
        document.getElementById("txtHint").innerHTML = this.responseText;
    };
    
    xhttp.open("GET", "getcustomer.php?q=" + str);
    xhttp.send();
}
</script>
```

---

## Part 15: Asynchronous vs Synchronous

### Asynchronous (Recommended)

```javascript
xhttp.open("GET", "ajax_info.txt", true);  // true = async
xhttp.send();
```

Page stays responsive while waiting.

### Synchronous (Not Recommended)

```javascript
xhttp.open("GET", "ajax_info.txt", false);  // false = sync
xhttp.send();
document.getElementById("demo").innerHTML = xhttp.responseText;
```

Page freezes while waiting!

### Visual: Async vs Sync

```
Asynchronous:
Request sent → Page active → Response arrives → Update page

Synchronous:
Request sent → Page frozen → Response arrives → Update page
```

---

## Part 16: Error Handling

### Check Status Code

```javascript
const xhttp = new XMLHttpRequest();

xhttp.onload = function() {
    if (this.status == 200) {
        document.getElementById("demo").innerHTML = this.responseText;
    } else {
        document.getElementById("demo").innerHTML = "Error: " + this.status;
    }
};

xhttp.open("GET", "ajax_info.txt");
xhttp.send();
```

### Common Status Codes

| Code | Meaning |
|------|---------|
| 200 | OK |
| 201 | Created |
| 400 | Bad Request |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |
| 500 | Internal Server Error |

---

## Part 17: AJAX vs Fetch API

### XMLHttpRequest (Old Way)

```javascript
const xhttp = new XMLHttpRequest();

xhttp.onload = function() {
    console.log(this.responseText);
};

xhttp.open("GET", "data.json");
xhttp.send();
```

### Fetch API (Modern Way)

```javascript
fetch("data.json")
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.log(error));
```

### Comparison Table

| Feature | XMLHttpRequest | Fetch API |
|---------|----------------|-----------|
| Syntax | Verbose | Clean |
| Promises | No | Yes |
| Modern | No | Yes |
| Browser support | All browsers | Modern browsers |
| Recommended | No | Yes |

---

## Part 18: Working with XML

### Load and Parse XML

```javascript
const xhttp = new XMLHttpRequest();

xhttp.onload = function() {
    const xmlDoc = this.responseXML;
    const cd = xmlDoc.getElementsByTagName("CD");
    
    let table = "<tr><th>Artist</th><th>Title</th></tr>";
    
    for (let i = 0; i < cd.length; i++) {
        table += "<tr><td>" +
            cd[i].getElementsByTagName("ARTIST")[0].childNodes[0].nodeValue +
            "</td><td>" +
            cd[i].getElementsByTagName("TITLE")[0].childNodes[0].nodeValue +
            "</td></tr>";
    }
    
    document.getElementById("demo").innerHTML = table;
};

xhttp.open("GET", "cd_catalog.xml");
xhttp.send();
```

---

## Part 19: Common Mistakes

### Mistake 1: Not Checking readyState

```javascript
// Wrong ❌
xhttp.onreadystatechange = function() {
    document.getElementById("demo").innerHTML = this.responseText;
};

// Correct ✅
xhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
        document.getElementById("demo").innerHTML = this.responseText;
    }
};
```

### Mistake 2: Using Synchronous Requests

```javascript
// Wrong ❌ - Freezes page
xhttp.open("GET", "ajax_info.txt", false);

// Correct ✅ - Page stays responsive
xhttp.open("GET", "ajax_info.txt", true);
```

### Mistake 3: Forgetting to Send

```javascript
// Wrong ❌
xhttp.open("GET", "ajax_info.txt");
// Missing xhttp.send()!

// Correct ✅
xhttp.open("GET", "ajax_info.txt");
xhttp.send();
```

### Mistake 4: Not Handling Errors

```javascript
// Wrong ❌
xhttp.onload = function() {
    document.getElementById("demo").innerHTML = this.responseText;
};

// Correct ✅
xhttp.onload = function() {
    if (this.status == 200) {
        document.getElementById("demo").innerHTML = this.responseText;
    } else {
        console.log("Error:", this.status);
    }
};
```

---

## Part 20: Key Takeaways

### ✅ Remember These Points

1. **AJAX** updates page without reloading
2. **XMLHttpRequest** is the core object
3. **onload** handles response when ready
4. **open()** specifies request details
5. **send()** sends the request
6. **GET** for retrieving data
7. **POST** for sending data
8. **Always use async** (true)
9. **Check status code** (200 = OK)
10. **Fetch API** is the modern alternative

### AJAX Quick Reference

```javascript
// Create XMLHttpRequest
const xhttp = new XMLHttpRequest();

// Define callback
xhttp.onload = function() {
    if (this.status == 200) {
        document.getElementById("demo").innerHTML = this.responseText;
    }
};

// GET request
xhttp.open("GET", "data.txt", true);
xhttp.send();

// POST request
xhttp.open("POST", "submit.php", true);
xhttp.setRequestHeader("Content-type", "application/x-www-form-urlencoded");
xhttp.send("name=John&age=30");

// With parameters
xhttp.open("GET", "getuser.php?id=123", true);
xhttp.send();
```

### Modern Alternative (Fetch)

```javascript
// Fetch is cleaner and uses promises
fetch("data.json")
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.log(error));
```

---

## What's Next?

In the next lesson, we'll learn about:

### Coming Up: JavaScript Day 25

- JSON (JavaScript Object Notation)
- Parsing JSON data
- Stringifying objects
- Working with JSON APIs
- Practical JSON examples

---

*Congratulations! You've completed JavaScript Day 24. You now understand AJAX and XMLHttpRequest!*

---

**Practice with AJAX and see you in the next class!** 🚀
