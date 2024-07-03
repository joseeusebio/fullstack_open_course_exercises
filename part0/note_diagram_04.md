```mermaid

sequenceDiagramNote
  participant browser
  participant server

  browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
  activate server
  server-->>browser: Response status HTTP 302, request HTTP GET https://studies.cs.helsinki.fi/exampleapp/notes
  browser-->>Reloading page Notes
  deactivate server

  Note right of browser: O navegador envia a entrada (input) do usuario para o servidor, onde gera 5 novas requisições HTTP

  browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
  activate server
  server-->>browser: Response status HTTP 200, main.css file
  deactivate server

  browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
  activate server
  server-->>browser: Response status HTTP 200, main.js file
  deactivate server

  browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
  activate server
  server-->>browser: Response status HTTP 200, notes data.json file
  deactivate server

  Note right of browser: O navegador executa o codigo JavaScript, os dados enviados pelo body da requisição POST são acessados pelo servidor e então criado um novo objeto no array notes, na qual é carregado pelo arquivo data.json e visualizado na página.

```