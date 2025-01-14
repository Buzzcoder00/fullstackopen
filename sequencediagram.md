sequenceDiagram
    participant browser
    participant server

    Note over browser: The user writes content into the text field.

    browser->>browser: User clicks the "Save" button
    Note over browser: The browser collects the input content and prepares a POST request.

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    Note over server: The server processes the request to create a new note.

    activate server
    server-->>browser: Confirmation response (e.g., success or updated note data)
    deactivate server

    Note over browser: The browser updates the page with the new note or a success message.

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    Note over browser: The browser fetches the updated list of notes (including the new note) to re-render the list.

    activate server
    server-->>browser: Updated JSON data with the new note
    deactivate server

    Note over browser: The browser executes the callback function to render the updated list of notes.

