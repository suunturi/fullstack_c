```mermaid

sequenceDiagram
    participant browser
    participant server

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    server-->>browser: 302 Found https://studies.cs.helsinki.fi/exampleapp/notes
    deactivate server

    Note right of browser: Browser posts form data to /new_note, server responds with 302 redirect to instruct browser to reload /notes again

    browser->>server GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: html page
    deactivate server

    browser->>server GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: css file
    deactivate server

    Note right of browser: linked css file in the html page instructs browser to load the resource css file

    browser->>server GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: javascript file
    deactivate server

    Note right of browser: linked javascript file in the html page instructs browser to load the resource

    browser->>server GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: json file
    deactivate server

    Note right of browser: browser executes javascript file which instruct browser to get a json resource file
```