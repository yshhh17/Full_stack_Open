sequenceDiagram
    participant browser
    participant server
    Note right of browser: user opens SPA page

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server->>browser: HTTP 302 Redirects to /notes
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET main.css
    server-->>browser: CSS file

    browser->>server: GET main.js
    server-->>browser: Javascript file

    Note right of browser: browser executes js and fetches data

    browser->>server: GET data.json
    activate server
    server-->>browser: Json [{"content": "blah", "date": "1"}]
    deactivate server

    Note right of browser: Javascript renders notes without reloading the page.