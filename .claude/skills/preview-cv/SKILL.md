---
description: Preview the CV locally in a browser
disable-model-invocation: true
allowed-tools: Bash(python3 *), Bash(open *)
---

Start a local HTTP server and open the CV in the default browser:

1. Run `python3 -m http.server 8000 --directory /Users/chaimasaad/Downloads/cv-chaima` in the background
2. Run `open http://localhost:8000` to open it in the browser
3. Inform the user the server is running at http://localhost:8000 and they can stop it with Ctrl+C
