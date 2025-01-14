```mermaid
sequenceDiagram
    participant browser
    participant server
    
    browser->>browser: User types a new note in the text field
    browser->>browser: User presses the "Save" button
    
    Note right of browser: The browser sends the data (new note) to the server.
    
    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/notes with { "content": "New note content", "date": "2025-01-14" }
    activate server
    
    server-->>browser: Response with the new note saved (status 200 or similar)
    deactivate server
    
    Note right of browser: The browser updates the UI to reflect the new note.
    
    browser->>browser: Add new note to the list of displayed notes
    
    Note right of browser: Optionally, the browser may fetch the updated notes list (JSON) to refresh the view.
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: Return updated list of notes (including the new note)
    deactivate server
    
    browser->>browser: Render the updated list of notes with the new note included
