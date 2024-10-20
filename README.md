# Application 1 : Rule Engine with AST

> Zeotap | Software Engineer Intern | Assignment | Application 1


### Installation

- Frontend
  ```bash
  cd frontend/
  npm install
  ```
- Backend

  If `poetry` isn't previously installed, install it first.

  ```bash
 .\venv\Scripts\activate

  $VENV_PATH/bin/pip install -U pip setuptools
  $VENV_PATH/bin/pip install poetry
  ```

  Then continue to create a venv, and install dependencies

  ```bash
  cd backend/
  poetry install
  ```

- Database

  After a `poetry install`, execute the following to setup raw data in your
  postgres instance. Make sure to populate the connection creds in the `.env`.

  ```bash
  docker run --name some-postgres -e POSTGRES_PASSWORD=mysecretpassword -p 5432:5432 -d postgres
  ```

### How to run

Expecting that above installation process, suceeded.

- Frontend
  ```bash
  npm run dev
  ```
- Backend
  ```bash
  poetry run python main.py --dev
  ```
- Database
  ```bash
  docker run --name some-postgres -e POSTGRES_PASSWORD=mysecretpassword -p 5432:5432 -d postgres
  ```

## About Solution

The solution, as expected and listed down in the doc, contains a UI, an API, and a database.
For UI, I opted for Next.js . API is writen with FastAPI, because
it is really fast both post deployment, and while writing code. System Performance is my
foremost priority, only to be followed by developer productivity.


### Code Structure

This section will talk about files, and what they do.

- Backend
  file_path | description
  ----------------|-----------------------
  main.py | Entrypoint of the server
  poetry.lock | Dependencies for the server, managed by poetry
  pyproject.toml | Py Project Metadata
  rule_engine/ast_utils.py | Contains Class definitions and Utility functions around the AST like Node, etc
  rule_engine/database.py | ORM and Functions to read/write through database
  rule_engine/main.py | Entrypoint to the API, contains API contracts
  rule_engine/models.py | DB Table Schema
  rule_engine/parser_utils.py | Parser and Tokenizer definitions and utilities

- Frontend
  file_path | description
  ----------------|-----------------------
  app/ | Source Code of the App
  app/components/ASTTree.tsx | Component to visualize AST
  app/services/api.ts | Middleware/Utility to connect to REST API
  app/page.tsx | Entrypoint to the UI, renders the main pageV



