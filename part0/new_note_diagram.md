sequenceDiagram 
    participant browser
    participant server

    browser ->> server: POST new_note to /exampleapp/new_note
    activate server 
    server -->> browser: sends redirection url exampleapp/notes
    deactivate server

    browser ->> server: GET exampleapp/notes
    activate server
    server -->> browser: the html document
    deactivate server

    browser ->> server: GET main.css
    activate server
    server -->> browser: the main .css file
    deactivate server

    browser ->> server: GET main.js
    activate server
    server --> browser: the main.js file
    note right of browser: The browser executes the js code and does a GET request of data.json
    deactivate server

    browser ->> server: GET data.json
    activate server
    server --> browser: the data.json file
    deactivate server

    note right of browser: browser executes the callback function that parses and renders the notes
    
