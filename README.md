# Log Ingestor and Query Interface

This project implements a robust log ingestor and query interface using Flask, PostgreSQL, and Flask-SQLAlchemy. It allows the ingestion of log data over HTTP and provides a comprehensive interface for querying logs.

## Table of Contents

- [How to Run the Project](#how-to-run-the-project)
- [System Design](#system-design)
- [Features Implemented](#features-implemented)
- [Identified Issues](#identified-issues)

## How to Run the Project

1. **Clone the repository:**

    ```bash
    git clone https://github.com/your-username/log-ingestor-query-interface.git
    cd log-ingestor-query-interface
    ```

2. **Install dependencies:**

    ```bash
    pip install Flask Flask-SQLAlchemy psycopg2
    ```

3. **Set up PostgreSQL:**

    - Create a PostgreSQL database and user.
    - Update the database URI in both `log_ingestor.py` and `query_interface.py` with your PostgreSQL credentials and database information.

4. **Run the log ingestor and query interface:**

    - Run the log ingestor:

        ```bash
        python log_ingestor.py
        ```

        The log ingestor will run on port 3000 by default.

    - Run the query interface:

        ```bash
        python query_interface.py
        ```

        The query interface will run on port 5000 by default.

5. **Send log data to the log ingestor:**

    ```bash
    curl -X POST -H "Content-Type: application/json" -d '{"level": "error", "message": "Failed to connect to DB", ...}' http://localhost:3000/ingest
    ```

6. **Query logs using the query interface:**

    ```bash
    curl -X GET "http://localhost:5000/search?level=error&message=Failed%20to%20connect"
    ```

## System Design

The system consists of two main components:

- **Log Ingestor:**
    - Receives log data over HTTP.
    - Stores logs in a PostgreSQL database using Flask-SQLAlchemy.
    - Runs on port 3000 by default.

- **Query Interface:**
    - Provides an HTTP endpoint for searching logs.
    - Retrieves logs based on query parameters.
    - Runs on port 5000 by default.

## Features Implemented

- **Log Ingestor:**
    - Accepts log data in a specified JSON format.
    - Stores logs in a PostgreSQL database.
    - Runs on a configurable HTTP port (default: 3000).

- **Query Interface:**
    - Offers a comprehensive HTTP endpoint for searching logs.
    - Supports basic filtering based on log attributes.
    - Runs on a configurable HTTP port (default: 5000).

## Identified Issues

- **Database Connection:** The project assumes a stable and accessible PostgreSQL database. Ensure that the PostgreSQL server is running and the database connection details in both files are accurate.
- **Security Considerations:** The project lacks advanced security measures. Consider implementing authentication, authorization, and input validation for production use.
- **Error Handling:** While error handling is present, additional improvements may be needed for more robust error reporting and logging.


