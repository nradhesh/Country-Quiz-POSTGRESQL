# Country Capitals Quiz Game

This project is a quiz game that tests users' knowledge of country capitals. The backend is built with Node.js using the Express framework and PostgreSQL as the database. The list of countries and capitals is imported from a CSV file named `capitals.csv`.

## Table of Contents

- [Features](#features)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Database Setup](#database-setup)
- [Running the Application](#running-the-application)
- [API Endpoints](#api-endpoints)
- [Contributing](#contributing)
- [License](#license)

## Features

- Import countries and capitals from a CSV file.
- Store the data in a PostgreSQL database.
- Serve a quiz game to users via an Express.js API.
- Track scores and provide feedback.

## Prerequisites

- Node.js
- npm
- PostgreSQL
- pgAdmin (optional, for database management)

## Installation

1. Clone the repository:

    ```sh
    git clone https://github.com/yourusername/country-capitals-quiz-game.git
    cd country-capitals-quiz-game
    ```

2. Install dependencies:

    ```sh
    npm install
    ```

3. Set up environment variables by creating a `.env` file in the root directory with the following content:

    ```env
    DATABASE_URL=postgres://username:password@localhost:5432/quiz_game
    ```

## Database Setup

1. Create a PostgreSQL database:

    ```sh
    createdb quiz_game
    ```

2. Create the `capitals` table:

    ```sql
    CREATE TABLE capitals (
        id serial PRIMARY KEY,
        country VARCHAR(45),
        capital VARCHAR(45)
    );
    ```

3. Import the `capitals.csv` data into the `capitals` table. You can use the following script:

    ```sh
    psql -d quiz_game -c "\copy capitals(country, capital) FROM 'path/to/capitals.csv' DELIMITER ',' CSV HEADER;"
    ```

## Running the Application

1. Start the Express server:

    ```sh
    npm start
    ```

2. The server will run on `http://localhost:3000`.

## API Endpoints

- `GET /api/quiz`: Fetch a random quiz question.
- `POST /api/quiz`: Submit an answer and get the result.

Example request for fetching a quiz question:

```sh
GET /api/quiz
Response:
{
  "id": 1,
  "country": "France",
  "capital": "Paris"
}
