# JsDok

JsDok is a powerful yet lightweight JavaScript library designed for modern web development. It combines the elegance of a jQuery-like syntax with the performance and capabilities of modern JavaScript. Whether you're manipulating the DOM, handling smooth animations, managing local/session storage, or building sleek UI components, JsDok has you covered.

With a modular architecture, minimal footprint, and intuitive API, JsDok empowers developers to build fast, dynamic, and responsive web applications — all without the bloat of larger frameworks. It's the perfect tool for developers who want simplicity, speed, and flexibility in one elegant package.

![Version](https://img.shields.io/badge/version-0.1.0--beta.2-blue.svg)
![Size](https://img.shields.io/badge/size-48kb_minified-green.svg)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](./LICENSE)
[![Demo](https://img.shields.io/badge/demo-live-green.svg)](https://buntysoni.github.io/JsDok/)

## Table of Contents

- [Features](#features)
- [Installation](#installation)
- [Basic Usage](#basic-usage)
- [DOM Manipulation](#dom-manipulation)
- [Animations](#animations)
- [Event Handling](#event-handling)
- [Storage Management](#storage-management)
- [Form Handling](#form-handling)
- [UI Components](#ui-components)
- [Network Operations](#network-operations)
- [User Activity Tracking](#user-activity-tracking)
- [State Management](#state-management)
- [Browser Support](#browser-support)
- [License](#license)

## Features

- 🚀 **Lightweight Core**: Only 28KB minified
- 🎨 **Rich Animations**: Built-in fade, slide, shake, pulse effects
- 🔄 **DOM Manipulation**: jQuery-like syntax for easy DOM operations
- 📊 **Smart Components**: Advanced table, word cloud, progress bar
- 💾 **Storage Utilities**: Enhanced localStorage and IndexedDB support
- 🔐 **Secure Storage**: Encrypted local storage operations
- 📡 **Network Operations**: AJAX and WebSocket support
- 📝 **Form Management**: Validation, serialization, and reset capabilities
- 🎯 **Event System**: Simplified event handling
- 📊 **Activity Tracking**: Comprehensive user interaction monitoring
- 🔄 **State Management**: Built-in state management system

## Installation

### Direct Download

```html
<script src="jsdok.min.js"></script>
```

### CDN

```html
<script src="https://cdn.jsdelivr.net/gh/buntysoni/jsdok@v0.1.0-beta.2/dist/jsdok.min.js"></script>
```

## Basic Usage

```javascript
// DOM Ready
$(function () {
  // Select elements
  $(".myElement").text("Hello World");

  // Chaining
  $("#myButton")
    .addClass("active")
    .fadeIn()
    .on("click", function () {
      $(this).text("Clicked!");
    });
});
```

## DOM Manipulation

```javascript
// Creating elements
$("<div>").addClass("new-element").appendTo("body");

// Modifying elements
$(".element")
  .addClass("highlight")
  .css({
    backgroundColor: "#f0f0f0",
    padding: "10px",
  })
  .attr("data-id", "123");

// Traversing
$(".item").parent().find(".child").next().prev();
```

## Animations

### Basic Animations

```javascript
// Fade effects
$(".element").fadeIn(400);
$(".element").fadeOut(400);

// Slide effects
$(".panel").slideDown(400);
$(".panel").slideUp(400);
```

### Special Effects

```javascript
// Shake effect
$(".error").shake(5, 500, 5);

// Pulse effect
$(".notification").pulse(1.1, 600, 3);

// Typewriter effect
$(".title").typewriter("Welcome to JsDok", 50);

// Spring animation
$(".box").springAnimation(
  {
    left: 100,
    top: 50,
  },
  {
    stiffness: 0.1,
    damping: 0.8,
  }
);
```

## Storage Management

### Local Storage

```javascript
// Basic storage
$.setStorage("user", { id: 1, name: "John" });
const user = $.getStorage("user");

// Secure storage
$.setSecureStorage("apiKey", "secret-key-123");
const apiKey = $.getSecureStorage("apiKey");

// Storage with expiry
$.setStorageWithExpiry("token", "xyz", 3600); // expires in 1 hour
const token = $.getStorageWithExpiry("token");
```

### IndexedDB Operations

```javascript
// Save multiple records
await $.saveManyToDB("myDB", "users", [
  { name: "John", age: 30 },
  { name: "Jane", age: 25 },
]);

// Get all records
const users = await $.getAllFromDB("myDB", "users");

// Update record
await $.updateInDB("myDB", "users", {
  id: 1,
  name: "John Updated",
});
```

## Smart Table Component

```javascript
$("#tableContainer").smartTable({
  columns: [
    { field: "id", title: "ID" },
    { field: "name", title: "Name" },
    {
      field: "email",
      title: "Email",
      formatter: (value) => `<a href="mailto:${value}">${value}</a>`,
    },
  ],
  data: users,
  pageSize: 10,
  pageSizes: [5, 10, 25, 50],
  multiSelect: true,
  onRowClick: (row, index, event) => {
    console.log("Row clicked:", row);
  },
  onSort: (field, order) => {
    console.log("Sorted by:", field, order);
  },
});
```

## Form Handling

### Form Validation

```javascript
const errors = $("#registrationForm").validateForm({
  username: [
    { type: "required", message: "Username is required" },
    { type: "minLength", value: 3, message: "Min 3 characters" },
  ],
  email: [
    { type: "required" },
    { type: "email", message: "Invalid email format" },
  ],
  password: [
    { type: "required" },
    {
      type: "pattern",
      pattern: /^(?=.*[A-Za-z])(?=.*\d)[A-Za-z\d]{8,}$/,
      message: "Password must contain letters and numbers",
    },
  ],
});
```

### Form Serialization

```javascript
const formData = $("#myForm").serializeForm();
```

## User Activity Tracking

```javascript
const tracker = $("#app").trackUserActivity({
  summaryInterval: 30000, // 30 seconds
  trackScreenTime: true,
  trackMouse: true,
  trackKeyboard: true,
  trackScroll: true,
  onSummary: (stats) => {
    console.log("Session Duration:", stats.screenTimeFormatted);
    console.log("Mouse Clicks:", stats.mouseClicks);
    console.log("Key Presses:", stats.keystrokes);
    console.log("Scroll Events:", stats.scrollEvents);
    console.log("Idle Time:", stats.idleTimeFormatted);
  },
});
```

## State Management

```javascript
const state = $("#app").createState({
  count: 0,
  user: null,
});

const manager = $("#app").getStateManager();

manager.subscribe((newState) => {
  console.log("State updated:", newState);
});

manager.setState((state) => ({
  ...state,
  count: state.count + 1,
}));
```

## Network Operations

### AJAX Requests

```javascript
$.net({
  url: "https://api.example.com/data",
  method: "POST",
  data: { id: 123 },
  headers: {
    Authorization: "Bearer token",
  },
  success: (response) => {
    console.log("Success:", response);
  },
  error: (xhr, status, error) => {
    console.error("Error:", error);
  },
});
```

### WebSocket

```javascript
$("#socket").websocket("wss://example.com/socket", {
  reconnectAttempts: 5,
  reconnectDelay: 1000,
  onOpen: () => console.log("Connected"),
  onMessage: (event) => console.log("Received:", event.data),
});
```

## Browser Support

- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)
- Opera (latest)

## License

MIT License

Copyright (c) 2024-2025 Unlein® Private Limited

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## Support

For support, email contact@unlein.com or create an issue in the GitHub repository.
