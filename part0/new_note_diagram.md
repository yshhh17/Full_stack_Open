sequenceDiagram
    participant browser
    participant server
    Note right of browser: user writes a note and Saves

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    server->>browser: HTTP 302 Redirects to /notes
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    Note right of server: server saves updates notes
    server-->>browser: Updated HTML document
    deactivate server

    browser->>server: GET main.css
    server-->>browser: CSS file

    browser->>server: GET main.js
    server-->>browser: Javascript file

    browser->>server: GET data.json
    activate server
    server-->>browser: Updated notes JSON
    deactivate server

    Note right of browser: Browserr renders updated notes
