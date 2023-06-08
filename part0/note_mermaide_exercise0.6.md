sequenceDiagram
    participant browser
    participant server
    
    Note: website gets loaded 
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server


    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "HTML is easy", "date": "2023-1-1" }, ... ]
    deactivate server

    Note: adding new note the web does not retrieve all the files again, it only GETs the new_note_spa.

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa.json
    activate server
    server-->>browser: added the file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/new_note_spa.json
    activate server
    server-->>browser: [{ "content": "HTML is easy", "date": "2023-1-1" }, ... ]
    deactivate server
