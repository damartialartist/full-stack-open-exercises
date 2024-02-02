sequenceDiagram 
    participant browser
    participant server

   browser ->> server: GET spa.html
   activate server
   server --> browser: the html file
   deactivate server

   browser ->> server: GET main.css
   activate server
   server --> browser: the main.css file
   deactivate server

   browser ->> server: GET spa.js
   activate server
   server --> browser: the spa.js file
   deactivate server
   note right of browser: The browser executs the js file an fetches the json file

   browser ->> server: GET data.json
   activate server
   server --> browser: The json file
   deactivate server
   note right of browser: the browser executes the callback function and renders the notes

   note right of browser: The browser enters a new note which is intercepted by the javascript code
   
   browser ->> browser: append the new note to existing notes and redraws it
   browser ->> server: POST new_note_spa.json
