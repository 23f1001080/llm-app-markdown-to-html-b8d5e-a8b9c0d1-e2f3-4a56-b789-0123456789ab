## Markdown to HTML Converter with Code Highlighting

### 1. Project Title and Description:

This web application provides a static page that takes Markdown content from `input.md`, converts it into HTML using the `marked.js` library, and renders it dynamically into a designated area on the page. It also integrates `highlight.js` to automatically detect and style code blocks within the Markdown content, providing a visually appealing and readable presentation of code.

### 2. Setup Instructions:

To run this application locally, you simply need a web browser.

1.  Save all the provided files (`index.html`, `input.md`, `README.md`) into a single directory on your computer.
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

1.  **View the Markdown:** Upon opening `index.html`, the content of `input.md` will be automatically loaded, converted to HTML, and displayed in the main content area.
2.  **Modify Markdown:** To change the content displayed, simply edit the `input.md` file. Save your changes, then refresh `index.html` in your browser to see the updated rendering.
3.  **Code Highlighting:** Any code blocks defined in `input.md` using the standard Markdown syntax (e.g., triple backticks ` ```javascript `) will be automatically highlighted by `highlight.js`.

### 4. Code Explanation:

*   **`index.html`**: 
    *   This is the main HTML file.
    *   It includes `<meta>` tags for character set and viewport, and a `<title>`.
    *   **CSS:** Contains a `<style>` block for basic page and content area styling, along with a `<link>` to load the `highlight.js` default CSS theme from a CDN.
    *   **Content Area:** A `div` with `id="markdown-output"` acts as the container where the converted HTML will be rendered.
    *   **Libraries:**
        *   `<script src="https://cdn.jsdelivr.net/npm/marked/marked.min.js"></script>`: Loads the `marked.js` library from a CDN, which is responsible for parsing Markdown into HTML.
        *   `<script src="https://cdnjs.cloudflare.com/ajax/libs/highlight.js/11.9.0/highlight.min.js"></script>`: Loads the `highlight.js` library from a CDN, which provides syntax highlighting for code blocks.
    *   **JavaScript Logic:** An embedded `<script>` block handles the core functionality:
        *   It waits for the `DOMContentLoaded` event to ensure the HTML structure is fully loaded.
        *   It uses the `fetch` API to asynchronously retrieve the content of `input.md`.
        *   Upon successful retrieval, `marked.parse(markdownContent)` is called to convert the Markdown string into an HTML string.
        *   The resulting HTML is then inserted into the `innerHTML` of the `#markdown-output` element.
        *   Crucially, `hljs.highlightAll()` is called *after* the HTML is rendered to scan the newly added content for code blocks and apply syntax highlighting.
        *   Error handling is included to catch issues during fetching or rendering.

*   **`input.md`**: 
    *   This file contains the Markdown content that the `index.html` page will load and render. It includes headings, lists, paragraphs, and code blocks to demonstrate the functionality.

### 5. License Information:

This project is licensed under the MIT License.

```
MIT License

Copyright (c) 2023 The Project Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```