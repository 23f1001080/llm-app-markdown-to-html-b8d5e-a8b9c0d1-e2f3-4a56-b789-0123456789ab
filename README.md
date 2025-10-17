## Markdown to HTML Converter with Tabbed Views and Code Highlighting

### 1. Project Title and Description:

This web application loads Markdown content from `input.md`, converts it into HTML using the `marked.js` library, and renders it dynamically. A key new feature is the introduction of **tabbed views**, allowing users to seamlessly switch between the **rendered HTML output** and the **original Markdown source**. It continues to integrate `highlight.js` to automatically detect and style code blocks within the rendered HTML content, ensuring a visually appealing and readable presentation of code.

### 2. Setup Instructions:

To run this application locally, you simply need a web browser.

1.  Save all the provided files (`index.html`, `input.md`, `README.md`, `LICENSE`) into a single directory on your computer.
2.  Open the `index.html` file directly in your web browser. Most browsers allow opening local HTML files (e.g., `file:///path/to/your/project/index.html`).

Alternatively, for a more robust local development environment, you can serve the files using a simple HTTP server:

*   **Python:**
    ```bash
    python -m http.server 8000
    ```
    Then, navigate to `http://localhost:8000/` in your browser.
*   **Node.js (requires `http-server` package):**
    ```bash
    npm install -g http-server
    http-server . -p 8000
    ```
    Then, navigate to `http://localhost:8000/` in your browser.

### 3. Usage Guide:

1.  **View Content:** Upon opening `index.html`, the content of `input.md` will be automatically loaded, converted to HTML, and displayed in the main content area under the 'HTML' tab.
2.  **Switch Views:** Two tabs, 'HTML' and 'Source', are located at the top of the content area:
    *   Clicking the **'HTML' tab** displays the fully rendered HTML output, complete with syntax highlighting for code blocks.
    *   Clicking the **'Source' tab** reveals the raw, original Markdown text loaded from `input.md`.
3.  **Modify Markdown:** To change the content displayed, simply edit the `input.md` file. Save your changes, then refresh `index.html` in your browser to see the updated rendering in both tab views.
4.  **Code Highlighting:** Any code blocks defined in `input.md` using the standard Markdown syntax (e.g., triple backticks `` ```javascript ``) will be automatically highlighted by `highlight.js` when viewing the 'HTML' tab.

### 4. Code Explanation:

*   **`index.html`**: 
    *   This is the main HTML file, structuring the entire application.
    *   It includes `<meta>` tags for character set and viewport, and a `<title>`.
    *   **CSS:** Contains an embedded `<style>` block for basic page and content area styling. New styles have been added for the tab container, tab buttons, and to manage the visibility of content sections. It also links to the `highlight.js` default CSS theme from a CDN.
    *   **Content Structure:**
        *   A main `div` with `id="container"` wraps the tab interface and content areas.
        *   A `div` with `id="markdown-tabs"` contains two `button` elements: `html-tab` and `source-tab`, which control the view.
        *   A `div` with `id="markdown-output"` displays the converted HTML content. This element is initially visible.
        *   A `pre` element with `id="markdown-source"` displays the raw Markdown content. This element is initially hidden.
    *   **Libraries:**
        *   `<script src="https://cdn.jsdelivr.net/npm/marked/marked.min.js"></script>`: Loads `marked.js` for Markdown to HTML conversion.
        *   `<script src="https://cdnjs.cloudflare.com/ajax/libs/highlight.js/11.9.0/highlight.min.js"></script>`: Loads `highlight.js` for syntax highlighting.
    *   **JavaScript Logic:** An embedded `<script>` block handles the core functionality:
        *   It waits for the `DOMContentLoaded` event.
        *   A `rawMarkdownContent` variable stores the Markdown fetched from `input.md`.
        *   The `fetch` API retrieves `input.md`.
        *   Upon retrieval, the Markdown is parsed to HTML using `marked.parse()` and inserted into `#markdown-output`.
        *   The raw Markdown content is also inserted into `#markdown-source`.
        *   `hljs.highlightAll()` is called to apply syntax highlighting to any code blocks in `#markdown-output`.
        *   **Tab Switching:** Event listeners are attached to the 'HTML' and 'Source' buttons. A `showTab` function is implemented to:
            *   Toggle the `active` class on the buttons and the `hidden` class on the content `div`s (`#markdown-output` and `#markdown-source`).
            *   Ensure only one tab's content is visible at a time.
        *   Error handling is included for fetch/render failures.

*   **`input.md`**: 
    *   This file contains the Markdown content that the `index.html` page will load and render. It's used to demonstrate headings, lists, paragraphs, and code blocks.

### 5. License Information:

This project is licensed under the MIT License.

```
MIT License

Copyright (c) 2025 Sakshi Agarwal

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS
FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS
OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
WHETHER IN AN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR
IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
```
