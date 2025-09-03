- [DOM (Document Object Model) — Syntax \& Semantics Classification](#dom-document-object-model--syntax--semantics-classification)
  - [1. DOM Structure (Tree Grammar)](#1-dom-structure-tree-grammar)
  - [2. Node Types (Constructs)](#2-node-types-constructs)
  - [3. DOM Selection Syntax (Access Grammar)](#3-dom-selection-syntax-access-grammar)
  - [4. DOM Mutation (Constructs)](#4-dom-mutation-constructs)
  - [5. DOM Event Handling (Full Classification)](#5-dom-event-handling-full-classification)
    - [5.1 Event Target \& Registration](#51-event-target--registration)
    - [5.2 Event Phases (Semantics)](#52-event-phases-semantics)
    - [5.4 Event Object (Data Grammar)](#54-event-object-data-grammar)
    - [Visualization of DOM \& Events](#visualization-of-dom--events)
    - [Key concepts for beginners](#key-concepts-for-beginners)
- [localStorage](#localstorage)
- [HTTP Request](#http-request)
  - [fetch](#fetch)
  - [axios (third-party library, not an API)](#axios-third-party-library-not-an-api)
  - [XMLHttpRequest (XHR)](#xmlhttprequest-xhr)
  - [Differences (purpose \& practical choice)](#differences-purpose--practical-choice)
    - [Which to pick?](#which-to-pick)
- [Node.js — Host Model](#nodejs--host-model)
  - [1 Grammar — the kinds of runtime constructs Node offers](#1-grammar--the-kinds-of-runtime-constructs-node-offers)
  - [2 Constructs — how you write these things](#2-constructs--how-you-write-these-things)
  - [3 Semantics — what happens at runtime](#3-semantics--what-happens-at-runtime)
    - [Common gotchas \& advice — tell it like it is](#common-gotchas--advice--tell-it-like-it-is)
- [React — A pre-built rules + helpers that keeps your UI in sync with your data being updated automatically](#react--a-pre-built-rules--helpers-that-keeps-your-ui-in-sync-with-your-data-being-updated-automatically)
  - [1. Grammar — the building blocks (what kinds of constructs exist)](#1-grammar--the-building-blocks-what-kinds-of-constructs-exist)
  - [2. Constructs — how you write the grammar in code (with examples)](#2-constructs--how-you-write-the-grammar-in-code-with-examples)
  - [3. Semantics — how these constructs behave at runtime](#3-semantics--how-these-constructs-behave-at-runtime)
  - [4. Classification cheat-sheets (quick reference)](#4-classification-cheat-sheets-quick-reference)
  - [Ten Commandments Rules](#ten-commandments-rules)
- [CanvasRenderingContext2D API](#canvasrenderingcontext2d-api)
  - [Other big families](#other-big-families)
  - [How to Think of It:](#how-to-think-of-it)

## DOM (Document Object Model) — Syntax & Semantics Classification

DOM (Document Object Model) manipulation is how you interact with HTML elements using JavaScript. A programming interface for web documents.

- It represents the HTML or XML document as a structured tree of objects, where each node corresponds to a part of the document, such as an element, attribute, or text.
- It allows scripts (like JavaScript) to read, modify, and manipulate the content, structure, and style of a webpage dynamically.

Conceptually, it’s the “live object grammar” of a web page: where ECMAScript describes the language of computation, DOM describes the language of documents and interaction.

### 1. DOM Structure (Tree Grammar)

- Root: document → entry point.
- Element nodes: hierarchical tags (`<html>`, `<body>`, `<p>`).
- Attribute nodes: metadata on elements (`id`, `class`, `src`).
- Text nodes: leaf content.
- Comment nodes: ignored in rendering, present in tree.

Corresponding DOM tree (simplified):

```css
Document
 └─ Element (html)
     ├─ Element (head)
     │    └─ Element (title)
     └─ Element (body)
          ├─ Element (h1)
          │    └─ Text("Hello World!")
          └─ Element (p)
               └─ Text("This is a paragraph.")
```

Semantics:

- Any change to this tree (e.g. element.textContent = ...) updates the rendered page immediately.
- Nodes have parent/child/sibling relations; traversal APIs rely on this structure.

### 2. Node Types (Constructs)

| Node Type | Example Representation | Semantics                                                |
| --------- | ---------------------- | -------------------------------------------------------- |
| Element   | `<div>`, `<p>`         | Structural building block; can have attributes/children. |
| Attribute | `id="header"`          | Metadata of element; accessible via `.getAttribute()`.   |
| Text      | `"Hello World!"`       | Raw text inside elements.                                |
| Comment   | `<!-- note -->`        | Ignored in rendering; preserved in tree.                 |
| Document  | `document`             | Global root; represents whole page.                      |

### 3. DOM Selection Syntax (Access Grammar)

| Construct                       | Grammar Form                           | Returns             | Semantics                     |
| ------------------------------- | -------------------------------------- | ------------------- | ----------------------------- |
| `getElementById(id)`            | `document.getElementById("foo")`       | Element or null     | Fast unique selector by `id`. |
| `getElementsByClassName(class)` | `document.getElementsByClassName("c")` | Live HTMLCollection | Updates as DOM changes.       |
| `getElementsByTagName(tag)`     | `document.getElementsByTagName("div")` | Live HTMLCollection | Traverses by element type.    |
| `querySelector(sel)`            | `document.querySelector(".foo > p")`   | First match         | Full CSS selector grammar.    |
| `querySelectorAll(sel)`         | `document.querySelectorAll("ul li")`   | Static NodeList     | Snapshot of all matches.      |

Summary Cheat Sheet

```js
// By ID (fastest)
document.getElementById("id");

// By Class (returns HTMLCollection)
document.getElementsByClassName("class");

// By Tag (e.g., div, p)
document.getElementsByTagName("div");

// CSS Selectors (modern)
document.querySelector(".class"); // First match
document.querySelectorAll("div.highlight"); // All matches
```

### 4. DOM Mutation (Constructs)

| Construct                         | Grammar Form        | Semantics                                             |
| --------------------------------- | ------------------- | ----------------------------------------------------- |
| `element.textContent = "..."`     | property assignment | Replaces all text children with new text.             |
| `element.innerHTML = "<b>Hi</b>"` | property assignment | Parses string into DOM nodes; unsafe with user input. |
| `parent.appendChild(node)`        | method call         | Inserts node at end of children.                      |
| `parent.insertBefore(node, ref)`  | method call         | Inserts node before `ref`.                            |
| `node.remove()`                   | method call         | Detaches node from parent.                            |
| `cloneNode(deep)`                 | method call         | Creates copy of node (shallow/deep).                  |

Semantics:

- Mutations alter the live tree; repaint/reflow may occur.
- Reparenting moves nodes; they cannot exist in two places.

### 5. DOM Event Handling (Full Classification)

Events can be attached in three syntactic forms:

- Inline HTML attributes
  ```html
  <button onclick="alert('clicked')">Click</button>
  ```
  - Uses the on<event> form (like onclick, onkeyup).
  - Oldest style, still supported, but mixes HTML with JS.
- DOM element properties
  ```js
  button.onclick = function () {
    alert("clicked");
  };
  ```
  - Direct assignment to a property (element.on<event>).
  - Replaces any existing handler.
- addEventListener (modern standard)
  ```js
  button.addEventListener("click", () => alert("clicked"));
  ```
  - Supports multiple listeners, event options (once, capture, passive).
  - Preferred method in modern JavaScript.

#### 5.1 Event Target & Registration

```js
target.addEventListener(type, listener, options?)
```

Semantics:

- Listeners are stored in target’s event-list table.
- Multiple listeners allowed.
- Options alter dispatch behavior (see phases below).

Parameters:

1. type (string) – The name of the event to listen for (e.g., "click", "keydown").
2. listener (function) – The callback function to execute when the event fires. It receives an Event object.
3. options (optional) – An object or boolean controlling event behavior:
   - capture (boolean) – indicates if the event should be captured during the capture phase instead of bubbling.
   - once (boolean) – the listener will be invoked at most once.
   - passive (boolean) – signals the listener won’t call preventDefault(), improving performance for scrolling events.

```js
<button id="myButton">Click Me</button>
<script>
  const button = document.getElementById("myButton");

  // Add a click event listener
  button.addEventListener("click", (event) => {
    alert("Button clicked!");
    console.log(event); // The Event object
  });

  // Add a keydown listener to window
  window.addEventListener("keydown", (event) => {
    if (event.key === "ArrowUp") {
      console.log("Up arrow pressed");
    }
  });
</script>
```

#### 5.2 Event Phases (Semantics)

Events travel through three phases:

```js
Capture phase: window → document → ... → target
Target phase:  event at target element
Bubble phase:  target → ... → document → window
```

- Default: listeners fire in bubble phase.
- {capture:true} → fire during capture.
- stopPropagation() halts further listeners.
- Legacy on... attributes = shorthand for event assignment.
- Event objects unify across categories (MouseEvent, KeyboardEvent, etc.).
- Event bubbling/capturing still applies no matter which syntax you use.

1. Event Target:

   - The object that can receive events. Most commonly:
   - DOM elements (div, canvas, button)
   - document
   - window

2. Event Types:

   - Mouse events: "click", "mousedown", "mouseup", "mousemove", "mouseover", "mouseout"
     - onclick – single click
     - ondblclick – double click
     - onmousedown – button pressed
     - onmouseup – button released
     - onmouseover – pointer enters element
     - onmouseout – pointer leaves element
     - onmousemove – pointer moves
       ```js
       element.onmouseover = () => console.log("Mouse entered");
       ```
   - Keyboard events: "keydown", "keyup", "keypress"
     - onkeydown – key pressed down
     - onkeypress – key pressed and held (deprecated, use keydown)
     - onkeyup – key released
       ```js
       window.onkeydown = (e) => console.log(e.key);
       ```
   - Window/document events: "resize", "scroll", "focus", "blur"
     - onload – resource/page fully loaded
     - onunload – leaving page (deprecated, use beforeunload)
     - onresize – window resized
     - onscroll – scrolling occurred
   - Touch events (mobile): "touchstart", "touchmove", "touchend"
     - ontouchstart – finger touches screen
     - ontouchmove – finger moves
     - ontouchend – finger lifted
     - ontouchcancel – gesture aborted
   - Form/input events: "input", "change", "submit"
     - onfocus – element gains focus
     - onblur – element loses focus
     - oninput – input value changes live
     - onchange – input value committed (e.g., after blur or Enter)
     - onselect – text selected inside input/textarea
     - onsubmit – form submitted
     - onreset – form reset
   - Drag and Drop Events
     - ondragstart – drag begins
     - ondrag – dragging in progress
     - ondragover – dragged element moves over drop target
     - ondrop – element dropped
     - ondragend – drag finished
   - Media Events
     - onplay – playback started
     - onpause – playback paused
     - onended – playback finished
     - (also onvolumechange, ontimeupdate, etc.)
   - Other / Misc
     - onerror – error in resource/script
     - oncontextmenu – right-click menu
     - onanimationstart, ontransitionend – CSS animations/transitions
   - Custom events: Developers can create their own events using new CustomEvent().

3. Event phases (capturing and bubbling):

   - Events travel in three phases:
   - Capture phase: from window down to the target element
   - Target phase: the event reaches the target element
   - Bubble phase: from target element back up to window
   - addEventListener can listen during capture by setting capture: true.

4. Event object:

   - Passed to the listener as a parameter.
   - Contains details about the event:
   - event.type → event type
   - event.target → the element that triggered the event
   - event.key → key pressed (for keyboard events)
   - event.clientX, event.clientY → mouse coordinates

5. Advantages over older methods:

   - Older on<event> properties (e.g., element.onclick = ...) overwrite previous handlers.
   - addEventListener allows multiple listeners on the same element/event type.

| Category       | Core Events                                                                                      | Example Semantics                                      |
| -------------- | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------ |
| **Mouse**      | `click`, `dblclick`, `mousedown`, `mouseup`, `mousemove`, `mouseover`, `mouseout`, `contextmenu` | Coordinates in `event.clientX/Y`; bubbling enabled.    |
| **Keyboard**   | `keydown`, `keyup`, `keypress` (legacy)                                                          | Keys in `event.key`; repeat if held.                   |
| **Form/Input** | `focus`, `blur`, `input`, `change`, `submit`, `reset`, `select`                                  | Focus/blur do not bubble; input fires on value change. |
| **Window/Doc** | `load`, `unload`, `resize`, `scroll`                                                             | Triggered on window/document lifecycle.                |
| **Drag/Drop**  | `dragstart`, `dragover`, `drop`, `dragend`                                                       | `dataTransfer` object carries payload.                 |
| **Touch**      | `touchstart`, `touchmove`, `touchend`, `touchcancel`                                             | Multi-touch points in `event.touches`.                 |
| **Media**      | `play`, `pause`, `ended`, `timeupdate`                                                           | Media element state transitions.                       |
| **Clipboard**  | `copy`, `cut`, `paste`                                                                           | Access clipboard data via `event.clipboardData`.       |
| **Custom**     | `new CustomEvent("myEvent", {detail:...})`                                                       | Application-defined payloads.                          |

- Key Takeaways

  - addEventListener is built-in, part of the browser API.
  - Allows you to monitor user interactions and system events in real-time.
  - Provides flexibility with capture, once, and passive options.
  - Works for all standard events (mouse, keyboard, touch, etc.) and custom events.
  - Safer and more versatile than older on<event> assignments.

- DOM vs HTML
  | HTML (Static) | DOM (Dynamic) |
  | ------------------------ | --------------------------------- |
  | Written in `.html` file. | Constructed in memory by browser. |
  | Declarative markup. | Mutable object graph. |
  | No runtime behavior. | Live interaction via JS. |

#### 5.4 Event Object (Data Grammar)

Every event callback receives an Event object (or subclass):
| Property | Meaning |
| -------------------- | ------------------------------------------ |
| `type` | Event name (`"click"`). |
| `target` | Element that originated event. |
| `currentTarget` | Element whose listener is executing. |
| `bubbles` | Boolean, whether event bubbles. |
| `cancelable` | Boolean, whether `preventDefault()` works. |
| `defaultPrevented` | True if default action suppressed. |
| `clientX`, `clientY` | Mouse/touch coordinates. |
| `key`, `code` | Key pressed for keyboard events. |
| `dataTransfer` | Data object for drag/drop. |
| `detail` | Payload for `CustomEvent`. |

Semantics:

- Event objects are reused by browser; don’t store long-term.
- Default actions (e.g. form submit, link navigation) can be blocked with `preventDefault()`.

#### Visualization of DOM & Events

```
DOM Tree
 document
 └─ html
     └─ body
         ├─ button#myBtn
         │
Event Dispatch (click)
 window → document → html → body → button (target)
                     ↑                  ↓
               capture phase         bubble phase
```

#### Key concepts for beginners

- DOM is a live tree of nodes mirroring the page.
- You query nodes, mutate them, and listen to events.
- Events move in phases (capture → target → bubble).
- Old on<event> attributes exist, but addEventListener is the standard grammar.
- DOM is not ECMAScript itself, but sits beside it as the browser’s native runtime language.

## localStorage

`localStorage` is the Web Storage API’s persistent key-value store: simple, synchronous string storage scoped per origin. Data persists across page loads and browser restarts until explicitly removed.

```js
// Store a string
localStorage.setItem("theme", "dark");

// Read it back
const theme = localStorage.getItem("theme"); // "dark"

// Store a JS object (serialize)
localStorage.setItem("todos", JSON.stringify([{ id: 1, text: "learn JS" }]));
const todos = JSON.parse(localStorage.getItem("todos") || "[]");

// Remove
localStorage.removeItem("theme");

// Clear all keys for this origin
localStorage.clear();
```

Explanation & important caveats (beginners must know)

- localStorage only stores strings. Use JSON.stringify / JSON.parse for objects/arrays.
- It's synchronous: reading/writing can block the main thread. Don’t store large data or do heavy localStorage operations in tight loops. For larger or structured storage, prefer IndexedDB.
- Storage size limits vary by browser (commonly ~5MB); don’t assume unlimited space.
- localStorage is accessible to any JavaScript running on the same origin — meaning it’s vulnerable to XSS (if an attacker can run JS on your page, they can read localStorage). Never store secrets or tokens you don’t want client scripts to see.
- localStorage changes trigger a storage event in other tabs/windows of the same origin (but not in the same window that performed the change), which is useful to sync state across tabs.

Simple visualization (where to store what)

```
Cookie
sent to server on every request (small, used for auth/cookie-based sessions)

localStorage
client-only, persistent, strings, synchronous (good for small app prefs)

sessionStorage
like localStorage but cleared when tab closes

IndexedDB
client-only, async, large structured data for bigger offline-capable data
```

Quick cheat sheet / TL;DR (practical rules)
localStorage is great for small, non-sensitive, persistent data (UI prefs, small caches). For big data or secure tokens, use IndexedDB or server storage.

## HTTP Request

### fetch

`fetch()` is the modern, built-in browser API for making network requests. It returns a Promise that resolves to a `Response` object; note that the Promise only rejects for network failures or a badly formed URL — it does not reject for HTTP error status like `404` or `500`. You must check `response.ok` or `response.status`.
[MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch?utm_source=chatgpt.com)

Promise-based:

```js
fetch("/api/user")
  .then((res) => {
    if (!res.ok) throw new Error(`HTTP ${res.status}`);
    return res.json();
  })
  .then((data) => console.log(data))
  .catch((err) => console.error("Fetch error:", err));
```

async/await:

```js
async function getUser() {
  const res = await fetch("/api/user");
  if (!res.ok) throw new Error(`HTTP ${res.status}`);
  const data = await res.json();
  return data;
}
```

Abort / timeout (fetch + `AbortController`):

```js
const controller = new AbortController();
setTimeout(() => controller.abort(), 5000);

try {
  const res = await fetch("/api/long", { signal: controller.signal });
  // ...check res.ok and process
} catch (err) {
  if (err.name === "AbortError") console.log("Request aborted");
}
```

How it works (plain English)

- `fetch(url, options)` returns a Promise for a `Response`.
- The `Response` exposes body readers (`.json()`, `.text()`, `.blob()`, streaming via `body`), headers, `status`, and `ok`.
- Because `fetch` resolves on HTTP errors, you must explicitly check `response.ok` (or `status`). Failure to do so is the #1 beginner bug.
  [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch?utm_source=chatgpt.com)

Visualization (simple flow)

```
Your code -> fetch()  --> network --> server
          <- Promise resolves to Response (even if 404)
          -> call res.json() to read body
```

Pros

- Native (no library).
- Promise-based and ergonomic with `async/await`.
- Modern features: streaming bodies, `AbortController`, readable streams.

Cons / gotchas

- Doesn’t reject on HTTP errors (you must check `response.ok`).
  MDN Web Docs
- Credentials/cookies: default credentials policy is `same-origin`; to send cookies cross-site you must set `credentials: 'include'`.
  MDN Web Docs
- No built-in interceptors or automatic JSON error parsing — you roll those yourself.

### axios (third-party library, not an API)

`axios` is a widely used, promise-based HTTP client library that works both in the browser (wraps XHR) and in Node.js (wraps the native `http` module). It offers features that make real-world API work easier: auto JSON transforms, request/response interceptors, timeouts, cancellation, and convenient config defaults.
[Axios](https://axios-http.com/docs/intro?utm_source=chatgpt.com)
Promise-based:

```js
axios
  .get("/api/user")
  .then((res) => console.log(res.data))
  .catch((err) => console.error(err));
```

async/await:

```js
try {
  const res = await axios.get("/api/user");
  console.log(res.data);
} catch (err) {
  // err.response, err.request, err.message help diagnose
}
```

Interceptors (attach headers, handle auth):

```js
axios.interceptors.request.use((config) => {
  config.headers.Authorization = `Bearer ${token}`;
  return config;
});

axios.interceptors.response.use(
  (res) => res,
  (err) => {
    if (err.response && err.response.status === 401) {
      // refresh token or redirect
    }
    return Promise.reject(err);
  }
);
```

Timeout and cookies:

```js
axios.get("/private", { timeout: 5000, withCredentials: true });
```

How it works (plain English)

- In the browser axios issues requests via `XMLHttpRequest`; in Node it uses Node’s `http` module — same API across environments. It returns a Promise which resolves with a response object that has `.data` (parsed body), `.status`, `.headers`, `.config`.
  [Axios](https://axios-http.com/docs/intro?utm_source=chatgpt.com)
- By default, axios rejects the Promise when the HTTP status is outside the range `200 <= status < 300` (you can change this behavior with `validateStatus`). That difference vs `fetch` is a common reason folks pick axios.
  [Axios](https://axios-http.com/docs/handling_errors?utm_source=chatgpt.com)

Pros

- Nice defaults (auto parse JSON to `res.data`), easy interceptors (for auth/metrics), built-in timeouts, cancelation helpers, widely used in tutorials and enterprise apps.
  [Axios](https://axios-http.com/docs/intro?utm_source=chatgpt.com)

Cons / gotchas

- Adds a dependency and bundle size (tiny but not zero).
- Behavior differences vs `fetch` (errors, defaults) — you should learn what axios returns on error (`err.response`, `err.request`).

### XMLHttpRequest (XHR)

`XMLHttpRequest` is the original browser API for AJAX-style requests. It uses an event/callback model (`onreadystatechange`, `onload`, `onerror`, `onprogress`) and exposes `readyState` values you can observe to track progress and completion. Modern `fetch` wraps the same underlying browser network primitives but with a Promise and friendlier API.
[MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest?utm_source=chatgpt.com)

Minimal example (classic)

```js
const xhr = new XMLHttpRequest();
xhr.open("GET", "/api/user", true); // true = asynchronous
xhr.onload = function () {
  if (xhr.status >= 200 && xhr.status < 300) {
    const data = JSON.parse(xhr.responseText);
    console.log(data);
  } else {
    console.error("HTTP", xhr.status);
  }
};
xhr.onerror = function () {
  console.error("Network error");
};
xhr.send();
```

`readyState` values (brief):

- `0` UNSENT — not opened
- `1` OPENED — `open()` called
- `2` HEADERS_RECEIVED — `send()` called and headers available
- `3` LOADING — response body is being received (partial)
- `4` DONE — complete [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest?utm_source=chatgpt.com)

How it works (plain English)

- Event-driven: you register handlers for state changes, load, error, and progress. It gives finer-grained progress callbacks (useful for file uploads/downloads).
- Synchronous mode exists but should be avoided—the UI will freeze.
- Pros
- Fine-grained control (progress events).
- Very widely supported (legacy browsers).

Cons

- Verbose, callback-style; Promise-based APIs (fetch/axios) are typically easier to read and compose.
- More boilerplate to parse responses and handle common patterns.

### Differences (purpose & practical choice)

| Feature / concern              |                                                              `fetch` |                                                                             `axios` |                            `XHR` |
| ------------------------------ | -------------------------------------------------------------------: | ----------------------------------------------------------------------------------: | -------------------------------: |
| API style                      |                                               Promise-based (native) |                                                             Promise-based (library) |             Callback/event based |
| Rejects on 4xx/5xx by default? |               **No** — resolves; check `res.ok`. ([MDN Web Docs][1]) | **Yes** — rejects by default outside 2xx (`validateStatus` overrides). ([Axios][2]) | No (you check `status` manually) |
| Auto JSON parsing              |                                           No (you call `res.json()`) |                                              Yes — `res.data` auto-parsed when JSON |                               No |
| Interceptors / middleware      |                                              No (you build wrappers) |                                                            ✅ built-in interceptors |                               No |
| Cancellation                   |                                                    `AbortController` |                                         Cancel tokens / AbortController (supported) |                    `xhr.abort()` |
| Credentials / cookies          | `credentials` option; defaults to `same-origin`. ([MDN Web Docs][3]) |                          `withCredentials: true/false` (configurable). ([Axios][4]) |     `xhr.withCredentials = true` |
| Browser + Node?                |            Browser (Node has `fetch` in newer versions or polyfills) |                 Works in browser **and** Node (isomorphic) — same API. ([Axios][4]) |                     Browser only |
| Streaming support              |                                          Yes (ReadableStream bodies) |                                               Some support (depends on environment) |                          Limited |

[1]: https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch?utm_source=chatgpt.com "Using the Fetch API - MDN"
[2]: https://axios-http.com/docs/handling_errors?utm_source=chatgpt.com "Handling Errors | Axios Docs"
[3]: https://developer.mozilla.org/en-US/docs/Web/API/Request/credentials?utm_source=chatgpt.com "Request: credentials property - MDN - Mozilla"
[4]: https://axios-http.com/docs/intro?utm_source=chatgpt.com "Getting Started | Axios Docs"

#### Which to pick?

- Use `fetch` when you want a zero-dependency, standards-based approach for simple requests and you’re comfortable doing a couple things manually (checking response.ok, parsing JSON, wiring timeouts).
  [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch?utm_source=chatgpt.com)
  +1
- Use `axios` for production apps where you want convenience (automatic JSON handling), interceptors for auth and retries, easy timeouts, cross-platform (browser + Node), and a friendlier error object. [Axios](https://axios-http.com/docs/intro?utm_source=chatgpt.com)
- Learn XHR so you understand legacy code, progress events, and the lower-level mechanics — but prefer fetch/axios for new code.
  [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest?utm_source=chatgpt.com)

Beginner-friendly pitfall checklist (tell-it-like-it-is)

- If you used `fetch` and can’t figure out why 404s don’t trigger .`catch()` — that’s by design: check `response.ok`.
  [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch?utm_source=chatgpt.com)
- If cookies aren’t being sent with requests across domains, you probably need `credentials: 'include'` (fetch) or `{ withCredentials: true }` (axios), and the server must set proper CORS headers.
  [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/API/Request/credentials?utm_source=chatgpt.com)
  [Axios](https://axios-http.com/docs/intro?utm_source=chatgpt.com)
- If you need request/response logging, auth injection, retries, or consistent error shapes — axios interceptors save you from reinventing wheels.
  [Axios](https://axios-http.com/docs/interceptors?utm_source=chatgpt.com)

So at the programming style level:

- XHR = HTTP request API, callback/event style.
- fetch = HTTP request API, Promise-native.
- axios = HTTP request library, Promise-wrapped (built on XHR/Node http).

Visualization (Venn diagram idea)

```
               ┌────────────────────────────┐
               │   HTTP request mechanisms  │
               │                            │
   ┌───────────┼─────────────┐              │
   │           │             │              │
   │       XMLHttpRequest    │              │
   │                         │              │
   │   ┌─────────────────────┼───────┐      │
   │   │   Promise-based APIs │       │      │
   │   │                      │       │      │
   │   │    fetch, axios ◀────┘       │      │
   │   └──────────────────────────────┘      │
   │                                         │
   └─────────────────────────────────────────┘
```

- XHR = inside “HTTP request” only.
- fetch = overlap between “HTTP request” and “Promises” (native).
- axios = overlap too, but it’s a library rather than a native API.

## Node.js — Host Model

Node.js is a JavaScript runtime (server-side environment) built on the V8 JavaScript engine that exposes module loading, an event-driven asynchronous system, and host-level bindings (CLI, process, buffers, I/O) alongside the language.
[Node.js](https://nodejs.org/api/documentation.html?utm_source=chatgpt.com)

Mental model (how to think about Node)

- JavaScript language (ECMAScript) = the grammar & semantics of JavaScript.
- Node.js = the host environment that provides runtime features and execution policy on top of that language: module resolution, the event loop and scheduling, global objects, CLI lifecycle, and safe bridges to OS-level resources.
- Treat Node as “ECMAScript + host model.” The host model is what we’ll classify.

### 1 Grammar — the kinds of runtime constructs Node offers

Think of these as the core language categories for Node:

- Module system — two module grammars: ECMAScript Modules (ESM) and CommonJS (CJS).
  [Node.js](https://nodejs.org/api/esm.html)
  +1
- Asynchrony & scheduling model — the event loop, timers, microtasks, `process.nextTick`, and `setImmediate`.
  [Node.js](https://nodejs.org/en/learn/asynchronous-work/event-loop-timers-and-nexttick?utm_source=chatgpt.com)
- Top-level execution rules — how Node starts a program, top-level `await` behavior in ESM, process exit rules.
  [Node.js](https://nodejs.org/api/esm.html)
  +1
- Global host objects & environment — `globalThis`, `process`, `Buffer`, `console`, and web-like globals (e.g., `fetch` in modern Node).
  [Node.js](https://nodejs.org/api/globals.html?utm_source=chatgpt.com)
- Concurrency primitives & isolation — Worker threads and child processes (separate runtimes).
- Streams & resource model — streaming/iterable IO as first-class runtime patterns.
- Native bindings / ABI — Node-API (N-API) for native addons (bridge to compiled code).

These are the “non-API” categories that define the behavioral language of Node.

### 2 Constructs — how you write these things

1. Modules (ESM vs CommonJS)

   Essence: Two module grammars with different syntax and resolution semantics. Node supports both and provides interoperability rules.
   [Node.js](https://nodejs.org/api/esm.html)

   - ECMAScript Modules (ESM) (modern, browser-like)

     - Use `import` / `export`.
     - Enabled by file extension `.mjs`, or by `"type": "module"` in the nearest `package.json` for `.js`, or via explicit ESM loaders.
     - Supports top-level `await`.
       [Node.js](https://nodejs.org/api/packages.html?utm_source=chatgpt.com)

   ```js
   // package.json: { "type": "module" }  OR use .mjs extension
   // math.js (ESM)
   export function add(a, b) {
     return a + b;
   }

   // main.js (ESM)
   import { add } from "./math.js";
   console.log(add(2, 3)); // 5
   ```

   - CommonJS (CJS) (legacy Node default for many years)

     - Use `require()` / `module.exports`.
     - Default for `.cjs` and for `.js` when `"type": "commonjs"` or no `type` field.
       [Node.js](https://nodejs.org/api/packages.html?utm_source=chatgpt.com)

   ```js
   // circle.cjs (CJS)
   module.exports.area = (r) => Math.PI * r * r;

   // main.cjs
   const circle = require("./circle.cjs");
   console.log(circle.area(2));
   ```

   Key rules (practical):

   - .mjs / "type":"module" → treated as ESM; .cjs or absence of "type":"module" often yields CommonJS for .js. Node inspects markers and has a deterministic resolution algorithm. [Node.js](https://nodejs.org/api/esm.html)

   Interop gotchas (syntax outcomes).

   - Requiring an ESM with top-level `await` will throw `ERR_REQUIRE_ASYNC_MODULE`; use dynamic `import()` instead.
     [Node.js](https://nodejs.org/api/modules.html?utm_source=chatgpt.com)

   Visualization.

   ```js
   package.json
   ├─ "type": "module"   → .js treated as ESM → import/export, top-level await
   └─ "type": "commonjs" → .js treated as CJS → require/module.exports
   File extensions
   ├─ .mjs → ESM
   └─ .cjs → CJS
   ```

2. Top-Level `await` (ESM-only syntax)

   - In ESM files you may write `await` at the top level; execution of dependents waits for it to settle.
   - If a top-level await never settles, Node exits with code 13 (“Unsettled TLA”).
     [Node.js](https://nodejs.org/api/esm.html?utm_source=chatgpt.com)

   ```js
   // data.mjs (ESM)
   const resp = await fetch("https://example.com/data.json");
   const data = await resp.json();
   export default data;
   ```

   Semantics: allowed in ESM modules; when using top-level await (TLA), module evaluation may wait for promises to resolve — if a TLA promise never settles Node may report a warning/error (Node documents unsettled TLA and related exit behavior). [Node.js](https://nodejs.org/api/esm.html)

3. Asynchrony Model & Scheduling

   Common constructs:

   - `setTimeout(fn, ms)` — schedule callback in timers phase
   - `setImmediate(fn)` — schedule callback to check phase
   - `process.nextTick(fn)` — schedule microtask-like callback executed before Promises’ microtask queue on same tick
   - `Promise.resolve().then(fn)` — microtask queue (job queue)

   ```js
   console.log("start");

   process.nextTick(() => console.log("nextTick"));
   Promise.resolve().then(() => console.log("promise"));
   setTimeout(() => console.log("timeout"), 0);
   setImmediate(() => console.log("setImmediate"));

   console.log("end");
   ```

   ```
    start
    end
    nextTick
    promise
    timeout    // timers phase
    setImmediate // check phase
   ```

   Semantics note: Node’s event loop has named phases; `process.nextTick()` runs before microtasks or at a special queue processed earlier — that ordering is important when reasoning about starvation and scheduling.
   [Node.js](https://nodejs.org/en/learn/asynchronous-work/event-loop-timers-and-nexttick?utm_source=chatgpt.com)

4. Globals & Host environment

   Examples of host constructs you’ll use often:

   - globalThis — host global object
   - process — CLI/process lifecycle, env vars (process.env), argv, exit codes
   - Buffer — binary data container in Node (not part of vanilla JS)
   - fetch, Request, Response, FormData — available as web-like globals in modern Node releases (introduced around Node 18+; see globals docs).
     Node.js

   Example:

   ```js
   console.log(globalThis === global); // true-ish in Node
   console.log(process.argv.slice(2)); // CLI args
   ```

5. Streams & Iteration
   Constructs: Node exposes stream and iterable patterns for incremental I/O — you’ll use readable/writable streams and async iteration for memory-efficient I/O (e.g., `for await` `(const chunk of stream)`).

6. Workers & Child processes (isolation)
   Constructs: `worker_threads` provide threads with separate event loops; `child_process` spawns separate OS processes (complete runtime). Use worker for CPU-bound tasks or isolation.

7. Native Addons (Node-API / N-API)
   Construct: when you need C/C++/Rust speed or system access, write an addon using N-API so compiled modules can be loaded as Node modules. This is the boundary between JS language and native ABI.
   [Node.js](https://nodejs.org/api/n-api.html?utm_source=chatgpt.com)

### 3 Semantics — what happens at runtime

This is the operational meaning — the rules you must rely on.

Module semantics

- ESM is asynchronous: ESM parsing/resolution can be async (import(), import.meta.resolve), and ESM supports top-level await. CommonJS `require()` is synchronous and has different lifecycle semantics. Interop exists but has gotchas (named exports vs `module.exports`, require of ESM with TLA may be unsupported).
  [Node.js](https://nodejs.org/api/esm.html)

Event loop semantics

- Single JS thread: Node runs your JS on one thread (unless you create workers). Non-blocking I/O is achieved by offloading to the OS or the threadpool; callbacks re-enter the event loop phases. The event loop has phases (timers → pending callbacks → idle/prepare → poll → check → close) and microtask/nextTick queues that affect precise ordering. Long sync work blocks the loop.
  [Node.js](https://nodejs.org/en/learn/asynchronous-work/event-loop-timers-and-nexttick?utm_source=chatgpt.com)

Scheduling & starvation

- `process.nextTick()` can starve I/O if abused — it runs before other event loop tasks. Promise microtasks run after `nextTick` but before returning control to the loop phases. Use judiciously.

Program lifecycle

- Node starts by loading the script/module, runs its top-level code, then enters the event loop. The process exits when there is no more work to do (no pending timers, handles, or scheduled callbacks), or when you call `process.exit(code)`. Unsettled top-level awaits can cause warnings/errors; Node documents a specific exit code for unsettled top-level await.
  [Node.js](https://nodejs.org/api/process.html?utm_source=chatgpt.com)

Host semantics differences vs browser

- Node has server/OS-level responsibilities (file descriptors, process signals, CLI flags), different global objects (Buffer, process), and historically different module semantics than browsers — though ESM alignment improved that. Modern Node also brings browser-like globals (fetch, Headers) to make portable code easier.
  [Node.js](https://nodejs.org/api/globals.html?utm_source=chatgpt.com)

Visualizations (mental maps)

Node core map (simplified)

```
[Your JS file]  --(loader)--> [Module graph: ESM or CJS nodes]
       |
       v
 Event loop & scheduling ←→ Host APIs (libuv, threadpool, kernel)
       |
       v
 Global objects: process, Buffer, console, fetch
```

Event loop flow (simplified)

```
sync code runs
→ process.nextTick queue
→ microtask queue (Promises jobs)
→ timers phase (setTimeout)
→ poll phase (I/O callbacks)
→ check phase (setImmediate)
→ close callbacks
→ repeat until no work -> process exits
```

(Use this map to reason about ordering.)

Quick beginner cheat-sheet
| Concept | How to write it | Runtime meaning |
| --------------- | ---------------------------------------------------: | ---------------------------------------------------------------------------------- |
| ESM module | `import x from './x.js'` (`"type":"module"` or .mjs) | Async module format; supports top-level await. ([Node.js][1]) |
| CommonJS module | `const x = require('./x.cjs')` | Synchronous loader, `module.exports`. ([Node.js][2]) |
| Top-level await | `const r = await fetch(...)` in ESM | Module evaluation may pause; unsettled TLA has documented behavior. ([Node.js][1]) |
| Next tick | `process.nextTick(fn)` | Runs before microtasks; can starve loop if abused. ([Node.js][3]) |
| Microtasks | `Promise.resolve().then(fn)` | Runs after nextTick, before returning to event loop phases. ([Node.js][3]) |
| Global fetch | `await fetch(url)` (Node 18+) | Web-style fetch available globally in modern Node. ([Node.js][4]) |

[1]: https://nodejs.org/api/esm.html "Modules: ECMAScript modules | Node.js v24.7.0 Documentation"
[2]: https://nodejs.org/api/modules.html?utm_source=chatgpt.com "CommonJS modules | Node.js v24.7.0 Documentation"
[3]: https://nodejs.org/en/learn/asynchronous-work/event-loop-timers-and-nexttick?utm_source=chatgpt.com "Node.js event loop documentation"
[4]: https://nodejs.org/api/globals.html?utm_source=chatgpt.com "Global objects | Node.js v24.7.0 Documentation"

#### Common gotchas & advice — tell it like it is

Node: ESM with top-level await and dynamic import

Mixing CJS & ESM: interop works but has sharp edges (default exports, TLA incompatibilities). Prefer one module system per package unless you know the resolution rules.
[Node.js](https://nodejs.org/api/esm.html)

Blocking the event loop: heavy synchronous CPU work blocks everything. Move CPU-bound tasks to worker threads or child processes.
[Node.js](https://nodejs.org/en/learn/asynchronous-work/event-loop-timers-and-nexttick?utm_source=chatgpt.com)

process.nextTick abuse: small helpful tool — large misuse causes starvation. Use microtasks or setImmediate depending on needs.
[Node.js](https://nodejs.org/en/learn/asynchronous-work/event-loop-timers-and-nexttick?utm_source=chatgpt.com)

Assume web parity carefully: Node now includes many web globals (e.g., fetch), but file paths, module resolution, and process lifecycle are Node-specific. Check docs for version differences.
[Node.js](https://nodejs.org/api/globals.html?utm_source=chatgpt.com)

## React — A pre-built rules + helpers that keeps your UI in sync with your data being updated automatically

React is a JavaScript UI library for building user interfaces as a tree of reusable components. It provides a small “language layer” on top of JavaScript (JSX, component conventions, hooks, a rendering model) that describes how to declare UI, manage local state, respond to events, and coordinate rendering.

Mental model (how to think about React)

- Components are pure-ish functions that describe what the UI should look like for a given state & props.
- React’s job: call those components, build a virtual representation of UI, update only what changed in the real DOM, and manage side effects (subscriptions, timers) cleanly.
- Think: React is a UI translator — it translates data (props + state) → UI.

### 1. Grammar — the building blocks (what kinds of constructs exist)

- JSX expressions — embedded XML-like syntax inside JavaScript that expresses UI values.
- Components — units of UI: function components (modern) or classes (legacy).
- Props — read-only inputs to components (like function parameters).
- State — local, mutable memory inside components that triggers re-renders.
- Hooks — special `use\*` functions that let function components use state, effects, refs, memoization, etc.
- Events — JSX event props (e.g., `onClick`) mapped to a normalized event system.
- Rendering model — how and when React schedules renders (including batching / concurrent features).
- Server / Client boundaries — directives and patterns for server-rendered components (server components) vs interactive client components.

### 2. Constructs — how you write the grammar in code (with examples)

1. JSX syntax

   JSX is a syntax for producing element values inside JS. It compiles to `React.createElement(...)` calls (or the modern JSX transform) and is just an expression—so it fits anywhere an expression fits. Key JSX rules:

   - Tags must close; attributes are JS expressions inside `{}`; children are nested; boolean props can be shorthand.
   - `className` not `class`; event props are `onClick`, `onChange`, etc.
   - Expressions render their value; `false`, `null`, and `undefined` render nothing. [React](https://react.dev/?utm_source=chatgpt.com)

   ```jsx
   const title = <h1 id="hero">Hello</h1>; // JSX produces a value
   const card = <Card padding={8}>{title}</Card>; // children & props
   const el = <div className="card">{user.name}</div>;
   ```

   Note: Newer JSX transforms import helper functions automatically instead of compiling to React.createElement.
   [React](https://legacy.reactjs.org/blog/2020/09/22/introducing-the-new-jsx-transform.html?utm_source=chatgpt.com)

2. Components

   Function component (preferred):

   ```jsx
   function Greeting({ name }) {
     return <h1>Hello, {name}</h1>;
   }
   ```

   Class component (legacy):

   ```jsx
   class Greeting extends React.Component {
     render() {
       return <h1>Hello, {this.props.name}</h1>;
     }
   }
   ```

3. Props (Component Input)

   React components are just functions (or classes, legacy) that return JSX. Name with `PascalCase`. Props are the function parameters; props are read-only. Returning `null` renders nothing.
   [React](https://react.dev/reference/react?utm_source=chatgpt.com)

   Example (function component).

   ```jsx
   function Greeting({ name }) {
     // props
     return <h2>Hello, {name}</h2>; // JSX return
   }
   ```

   Class components still work but new code should prefer functions + Hooks. [React](https://react.dev/reference/react?utm_source=chatgpt.com)

4. State (component-local memory)

   State is the local, mutable memory of a React component. When state changes, React schedules that component to re-render so the UI reflects the new values.

   Grammar / Constructs (how you write it).

   - const [value, setValue] = useState(initialValue); — the canonical syntax in function components.
   - In class components (legacy) you’d use this.state and this.setState(...) (not covered deeply here).

   Hook form (function components):

   ```jsx
   import { useState } from "react";

   function Counter() {
     const [n, setN] = useState(0);
     return <button onClick={() => setN(n + 1)}>{n}</button>;
   }

   // or other way

   function Counter() {
     const [count, setCount] = React.useState(0);
     return <button onClick={() => setCount(count + 1)}>{count}</button>;
   }
   ```

   Key semantics: calling `setCount` schedules a re-render; use the functional updater `setCount(prev => ...)` when the update depends on previous state.

5. Hooks (rules & examples)

   Hooks are special functions (names start with use) that let function components tap into React features: state, effects, refs, memoization, etc.

   Grammar / Constructs.

   - Built-ins: `useState`, `useEffect`, `useRef`, `useMemo`, `useCallback`, `useContext`, `useReducer`, `useImperativeHandle`, `useLayoutEffect`, `useDebugValue`.
   - Custom hooks: any function whose name starts with use and that calls other hooks internally (e.g., `useAuth()`).

   Rules (critical):

   - Only call Hooks at the top level of React function components or other hooks (never inside loops, conditions, or nested functions).
   - Only call Hooks from React function components or custom hooks. These rules let React reliably track hook call order/state.
     React

   Semantics (what they provide):

   - useState → local state + setter.
   - useEffect → side effects after render and optional cleanup (maps to lifecycle behavior).
   - useRef → persistent mutable container not triggering re-renders.
   - useMemo/useCallback → memoize values/functions between renders (optimization tools).

   ```jsx
   function Timer({ ms }) {
     const [t, setT] = useState(0); // state
     const ref = useRef(); // ref
     useEffect(() => {
       // effect
       const id = setInterval(() => setT((x) => x + 1), ms);
       return () => clearInterval(id); // cleanup
     }, [ms]); // dependencies
     return <div>{t}</div>;
   }
   ```

   Primary state hooks.

   - useState(initial) — simplest state variable.
   - useReducer(reducer, initial) — centralize update logic.
   - Treat objects/arrays in state as immutable—create copies on update.
     [React](https://react.dev/reference/react/useState?utm_source=chatgpt.com)

6. Events (React’s model of user interaction)

   React handles DOM events (like `click`, `keydown`, `submit`) using camelCase event props instead of native HTML `on...` attributes.

   Grammar / Constructs (how you attach handlers):

   - Written in `camelCase` (`onClick` not `onclick`).
   - Passed as functions, not strings.
   - Event objects are wrapped in React’s synthetic event system.
   - JSX prop (preferred): `<button onClick={handle}>` — camelCase event name and a function value (not a string).
   - You can still add native listeners on real DOM nodes (via ref + addEventListener) if needed, but JSX handlers are the idiomatic way.
     [React](https://legacy.reactjs.org/docs/handling-events.html?utm_source=chatgpt.com)
     [React](https://react.dev/learn/responding-to-events?utm_source=chatgpt.com)

   ```jsx
   function Row({ item }) {
     function onClick(e) {
       e.preventDefault();
       console.log("clicked", item.id);
     }
     return <div onClick={onClick}>{item.text}</div>;
   }
   ```

   When to use native `addEventListener`:

   - If you must listen on window or document directly (outside component tree), or need non-React lifetime semantics, use a ref + useEffect to register/cleanup native listeners.

   Example (native listener via ref):

   ```jsx
   useEffect(() => {
     function onScroll() {
       /* ... */
     }
     window.addEventListener("scroll", onScroll);
     return () => window.removeEventListener("scroll", onScroll);
   }, []);
   ```

   Visual (dispatch):

   ```
   Browser -> native event -> React root listener -> React dispatch -> your handler (SyntheticEvent)
   ```

   (You write `<div onMouseOver={...}>`, React gives you a normalized event object and calls your handler.)

7. Rendering model — scheduling & batching

   - React batches state updates to avoid unnecessary renders. Starting React 18, automatic batching is broader (covers more async contexts), reducing excessive re-renders and improving performance. React also introduced the foundations for concurrent rendering (cooperative rendering that can interrupt low-priority updates). Use startTransition (when available) to mark low-priority updates.
     [React](https://legacy.reactjs.org/blog/2022/03/29/react-v18.html?utm_source=chatgpt.com)

8. Server & Client components (boundaries)
   - In some modern React architectures (Server Components), modules default to server execution; you opt into client-side behavior using a "use client" directive at the top of a module. There’s also "use server" for server-only functions in the server components model. These directives create a clear server/client boundary in the module tree.
     [React](https://react.dev/reference/rsc/use-client?utm_source=chatgpt.com)

### 3. Semantics — how these constructs behave at runtime

Component execution & re-rendering

- React invokes the component function to compute UI from props + state. When state/props change React re-invokes the function to compute the new UI snapshot and apply minimal DOM updates.

Hook slots & ordering

- Hooks are tracked by call order per component instance (first useState → slot0, next useState → slot1, etc.). Changing that order across renders (e.g., by calling a hook conditionally) breaks the mapping and causes bugs — hence Rules of Hooks.
  [React](https://react.dev/reference/rules/rules-of-hooks?utm_source=chatgpt.com)

Effects & cleanup lifecycle

- useEffect(fn, deps) runs fn after render. If fn returns a function, React calls that as cleanup before the next effect run and before unmount.

Events & delegation

- React listens for native events and dispatches them into your handler functions. The library normalizes differences across browsers; older optimizations like event pooling were changed in React 17 to improve developer ergonomics.
  [React](https://legacy.reactjs.org/docs/legacy-event-pooling.html?utm_source=chatgpt.com)

Rendering / concurrency

- React 18’s changes (automatic batching and concurrent rendering primitives) change how updates are scheduled — for you this mostly means better performance and new tools to mark low-priority state (transitions). React still preserves the functional mental model: state → render → DOM.
  [React](https://legacy.reactjs.org/blog/2022/03/29/react-v18.html?utm_source=chatgpt.com)

Server/client split

- Files marked "use client" can use state, effects, browser APIs — they run on the client. Server components run on the server and can fetch data without shipping JS to the client; use "use client" only where you need interactivity.
  [React](https://react.dev/reference/rsc/use-client?utm_source=chatgpt.com)

### 4. Classification cheat-sheets (quick reference)

By purpose

- Structure / declaration: JSX, components, props
- State & lifecycle: useState, useReducer, useEffect
- Behavior & events: onClick, onChange, SyntheticEvent
- Performance / scheduling: automatic batching, useMemo, startTransition
- Environment: Server Components ('use client' / 'use server')
  Quick “Cheat-Sheet” Tables

| Concept       |                Small example | When to use                |
| ------------- | ---------------------------: | -------------------------- |
| JSX           |          `<div>{name}</div>` | describe UI value          |
| Component     |  `function C(){return <p/>}` | reusable UI unit           |
| Props         |                 `<C x={1}/>` | parametrize components     |
| State         | `const [s,setS]=useState(0)` | keep local UI state        |
| Effect        |  `useEffect(()=>fetch(),[])` | subscribe / fetch / timers |
| Event         |       `<button onClick={h}>` | user interactions          |
| Context       |    `const T=createContext()` | global-ish values          |
| Server/Client |   `'use client'` top-of-file | mark interactive component |

5. Visual maps (simple diagrams)

```
props + state
     ↓
component function runs
     ↓
returns JSX (tree)
     ↓
React diffs with previous tree
     ↓
apply minimal DOM updates
```

Hooks slot idea (why ordering matters)

```
render #1: useState(A) -> slot0
          useState(B) -> slot1

render #2: same order -> values map correctly
if order changes -> React reads wrong slot -> bug
```

Server/Client boundary

```
App (server component)
 ├─ Header (server)
 └─ Widget (client)  <-- 'use client' (contains state, events)
```

### Ten Commandments Rules

1. Treat state and props as immutable — never mutate them in place; always replace by creating a new object/array.

   What: Never mutate arrays/objects stored in state or props.

   Why: React detects changes via references (shallow checks). Mutating in place keeps the same object reference → React may not notice and won’t re-render.

   ```js
   // BAD: mutates array in place
   goals.push("x");
   setGoals(goals); // may not re-render

   // GOOD: create a new array
   setGoals((prev) => [...prev, "x"]);
   ```

2. Use the state setter or reducer to update state — don’t assign to state variables directly.

   What: Always call the updater returned by useState (setX) or dispatch from useReducer.

   Why: React only tracks updates made through its APIs. Direct assignment won’t trigger reconciliation.

   ```js
   // WRONG
   count = count + 1; // does nothing useful

   // RIGHT
   setCount((c) => c + 1);
   ```

3. If new state depends on the old state, use the functional updater `setState(prev => new)` to avoid stale reads.

   What: setX(prev => compute(prev))

   Why: State updates are batched and may be asynchronous; using the functional form ensures you get the freshest previous state.

   ```js
   // avoid stale reads:
   setCount(c + 1); // might use an old `c` if multiple updates queued

   // safe form:
   setCount((prev) => prev + 1);
   ```

4. Call Hooks only at the top level of React function components or custom hooks (don’t call inside loops/conditions/nested functions).

   What: Call Hooks only at the top level of function components or other hooks (not inside if/for/while/nested functions).

   Why: React relies on the call order of hooks to map hook calls to internal “slots.” Changing order breaks that mapping and produces bugs/warnings.

   Wrong:

   ```js
   if (isShown) {
     useEffect(() => {
       /*...*/
     }, []);
   }
   ```

   Right:

   ```js
   useEffect(() => {
     if (!isShown) return;
     // ...
   }, [isShown]);
   ```

   See React’s Rules of Hooks. [React](https://react.dev/reference/rules/rules-of-hooks?utm_source=chatgpt.com)

5. Don’t cause side effects during render — use `useEffect` / `useLayoutEffect` for side effects; render must be pure.

   What: Rendering should be pure (no I/O, no subscriptions, no DOM mutations). Use useEffect or useLayoutEffect for side effects.

   Why: Pure rendering ensures determinism and lets React optimize. Side-effects during render can cause surprising behavior or break SSR.

   ```js
   useEffect(() => {
     const id = setInterval(tick, 1000);
     return () => clearInterval(id);
   }, []);
   ```

6. Clean up effects — return a cleanup function from useEffect when you subscribe or start timers to avoid leaks.

   What: When an effect creates a subscription or timer, return a cleanup function to unsubscribe/clear on deps change or unmount.

   Why: Prevents memory leaks and duplicate subscriptions.

   ```js
   useEffect(() => {
     const sub = subscribe((x) => setX(x));
     return () => sub.unsubscribe();
   }, [someDep]);
   ```

7. Avoid setting state during render (this creates infinite renders); schedule updates in effects or event handlers.

   What: Avoid calling setState while React is computing the render (synchronously inside the component body).

   Why: It triggers an immediate re-render → possible infinite loop. Use useEffect or event handlers instead.

   Wrong:

   ```js
   // BAD — causes re-renders while rendering
   if (!loaded) setLoaded(true);
   ```

   Right:

   ```js
   useEffect(() => {
     if (!loaded) setLoaded(true);
   }, [loaded]);
   ```

8. Use stable keys for lists; avoid using array index as key when list order or identity can change.

   What: Use unique identifiers as React keys for lists to preserve element identity.

   Why: Keys let React match old vs new items; wrong keys lead to incorrect DOM reuse (weird UI, lost inputs).

   ```js
   {
     items.map((item) => <Row key={item.id} data={item} />);
   }
   ```

   Avoid key={index} when list order/identity can change.

9. Use useRef for mutable values you don’t want to trigger renders (timers, DOM nodes, mutable caches).

   What: useRef stores mutable .current that survives renders but doesn’t trigger re-renders when changed.

   Why: Good for timers, DOM nodes, last-known value for event handlers, debouncing.

   ```js
   const timer = useRef();
   timer.current = setTimeout(...);
   ```

   Docs and community posts explain when to pick useRef vs useState.
   [DEV Community](https://dev.to/trinityyi/when-to-use-useref-instead-of-usestate-3h4o?utm_source=chatgpt.com)
   [Stack Overflow](https://stackoverflow.com/questions/56455887/react-usestate-or-useref?utm_source=chatgpt.com)

10. Don’t duplicate derived data in state — compute it from existing state/props instead of storing it redundantly.

    What: Don’t keep the same information in multiple state variables; compute derived data at render time or with useMemo if expensive.

    Why: Duplicated state can go out of sync and creates extra update logic.

    ```js
    // BAD
    const [count, setCount] = useState(0);
    const [double, setDouble] = useState(count * 2);

    // GOOD
    const double = count * 2;
    ```

Quick “Wrong vs Correct” cheatsheet (practical)
| Scenario | Wrong | Correct |
| ------------------------ | ------------------------------------------- | ------------------------------------------------ |
| Add item to array | `arr.push(x); setArr(arr);` | `setArr(prev => [...prev, x])` |
| Update object prop | `obj.name = 'A'; setObj(obj);` | `setObj(prev => ({...prev, name:'A'}))` |
| Prev-dependent update | `setC(c + 1); setC(c + 1);` | `setC(prev => prev + 1); setC(prev => prev + 1)` |
| Hook placement | `if (cond) useEffect(...);` | `useEffect(()=>{ if(cond) {...} }, [cond])` |
| List keys | `items.map((i, idx) => <Item key={idx} />)` | `items.map(i => <Item key={i.id} />)` |
| Mutable non-render value | `countRef = 0` (global var) | `const ref = useRef(0); ref.current = ...` |

Visual hierarchy :

```
Hard Rules (React enforced)
 ├─ Rules of Hooks (placement, where allowed)
 ├─ State immutability (no mutation, no direct assign)
 └─ Pure render (no side effects in render)

Strong Conventions (React works, but breaks easily)
 ├─ No duplicate derived state
 ├─ Cleanup effects
 ├─ Stable list keys
 └─ Avoid non-serializables in state

Best Practices (community wisdom)
 ├─ Group state sensibly
 ├─ Use reducer for complex state
 ├─ Use memo/callback sparingly
 ├─ Split components logically
 └─ Lift state when shared

Meta Rules (ecosystem/JS habits)
 ├─ No import mutation
 ├─ Avoid main-thread blocks
 └─ ESLint for safety
```

## CanvasRenderingContext2D API

When you’re inside `<canvas>`, everything comes from the CanvasRenderingContext2D API.

```js
const ctx = canvas.getContext("2d");
```

1. Path Methods (building geometric paths)

   These define shapes by constructing a sequence of connected lines/curves.

   - beginPath() - Resets the list of sub-paths, starting a new empty path.

     Use case: Prevents new shapes from being connected to old ones.

   Syntax:

   ```js
   ctx.beginPath();
   ```

   Example:

   ```js
   ctx.beginPath();
   ctx.moveTo(50, 50);
   ctx.lineTo(200, 50);
   ctx.stroke();
   ```

   - moveTo(x, y) - Moves the “pen” to (x, y) without drawing.

   Use case: Starting a new line at a specific coordinate.

   - lineTo(x, y) - Creates a straight line from current point → (x, y).

   Use case: Building polygons or free-hand drawings.

   - arc(x, y, radius, startAngle, endAngle [, anticlockwise]) - Adds an arc or circle to the path. Angles in radians (not degrees).

   Use case: Circles, arcs, pie charts.

   ```js
   ctx.beginPath();
   ctx.arc(100, 75, 50, 0, Math.PI * 2);
   ctx.stroke();
   ```

   - closePath() - Connects the last point to the start point automatically.

   Use case: Completing polygons.

   Example:

   ```js
   ctx.beginPath();
   ctx.moveTo(50, 50);
   ctx.lineTo(150, 50);
   ctx.lineTo(100, 150);
   ctx.closePath();
   ctx.stroke(); // outline triangle
   ```

2. Fill and Stroke (rendering paths)

   - fill() - Fills the interior of the current path with the current fillStyle.

   Use case: Filled shapes (buttons, circles, areas).

   - stroke() - Outlines the current path with strokeStyle and lineWidth.

   Use case: Drawing outlines.

   Example:

   ```js
   ctx.fillStyle = "red";
   ctx.strokeStyle = "black";

   ctx.beginPath();
   ctx.rect(80, 80, 120, 100);
   ctx.fill(); // red interior
   ctx.stroke(); // black border
   ```

   - fillRect(x, y, width, height) - Shortcut to fill a rectangle (no beginPath() needed).

   Use case: Quick background blocks, UI panels.

   - strokeRect(x, y, width, height) - Shortcut to fill a rectangle (no beginPath() needed).

   Use case: Quick background blocks, UI panels.

   ```js
   ctx.fillStyle = "red";
   ctx.fillRect(20, 20, 100, 80);

   ctx.strokeStyle = "black";
   ctx.strokeRect(20, 20, 100, 80);
   ```

   - clearRect(x, y, width, height) - Clears part of the canvas, making it fully transparent.

   Use case: Game loops (redraw screen each frame).

   ```js
   ctx.clearRect(0, 0, canvas.width, canvas.height);
   ```

3. Image methods

   - drawImage(image, dx, dy [, dWidth, dHeight]) - Draws an image or video onto the canvas.

   ```
   - drawImage(img, x, y)
   - drawImage(img, dx, dy, dw, dh)
   - drawImage(img, sx, sy, sw, sh, dx, dy, dw, dh)
   ```

   Example:

   ```js
   const img = new Image();
   img.src = "sprite.png";
   img.onload = () => ctx.drawImage(img, 50, 50, 100, 100);
   ```

   4. State & Styles

   - fillStyle / strokeStyle - Sets the color/gradient/pattern used for filling/stroking.

   ```js
   ctx.fillStyle = "#00FF00";
   ctx.strokeStyle = "rgba(0,0,255,0.5)";
   ```

   - lineWidth, lineJoin, lineCap

   ```
   lineWidth: thickness of strokes.
   lineJoin: corner style (miter, bevel, round).
   lineCap: end of lines (butt, round, square).
   ```

   ```js
   ctx.lineWidth = 8;
   ctx.lineJoin = "round";
   ctx.lineCap = "square";
   ```

   - save() / restore() - Save/restore the drawing state (colors, transforms, clipping).

   ```js
   ctx.save();
   ctx.fillStyle = "red";
   ctx.fillRect(10, 10, 50, 50);
   ctx.restore(); // back to old style
   ```

   ###⚡ Big Picture Classification

   - Path Construction → beginPath, moveTo, lineTo, arc, closePath.
   - Rendering → fill, stroke, fillRect, strokeRect, clearRect.
   - Images → drawImage.
   - State & Styles → fillStyle, strokeStyle, lineWidth, save/restore.

### Other big families

- Text methods: fillText(), strokeText(), measureText().
- Transformations: translate(), rotate(), scale().
- Compositing: globalCompositeOperation (blending modes like Photoshop).
- Pixel manipulation: getImageData(), putImageData() (low-level bitmap access).

### How to Think of It:

- Path methods → “construct geometry.”
- Stroke/fill → “apply paint to geometry.”
- Direct shapes → “shortcuts for rectangles.”
- Images → “place photos/sprites on canvas.”
- Styling → “set brush/pen look.”
- Text, transform, pixels → “extra tools for text, effects, advanced drawing.”
