```mermaid
sequenceDiagram
    participant browser
    participant server

    Note over browser: The user writes content into the text field in the SPA.

    browser->>browser: User clicks the "Save" button
    Note over browser: The browser prepares a POST request with the new note data.

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    Note over server: The server processes the request and stores the new note.

    activate server
    server-->>browser: Confirmation response (e.g., success message or updated note data)
    deactivate server

    Note over browser: The SPA updates the user interface to reflect the new note.

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    Note over browser: The browser fetches the updated list of notes to render the new list.

    activate server
    server-->>browser: Updated JSON data with the new note
    deactivate server

    Note over browser: The SPA dynamically renders the updated list of notes.
