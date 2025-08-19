# URL Shortening Web App

## Overview

A full-stack URL shortening web application that allows users to shorten long URLs into compact, shareable links. The project is built using Node.js, PostgreSQL, and Docker. It includes analytics such as click tracking and is containerized for easy deployment.

### Features

* Shorten long URLs into unique short codes
* Redirect short links to original URLs
* Track the number of visits per URL
* Store timestamp for each redirect
* Dockerized for easy setup and deployment

### Tech Stack

* **Backend:** Node.js (Express)
* **Database:** PostgreSQL
* **Containerization:** Docker, Docker Compose
* **Utilities:** nanoid (for generating short codes), dotenv (for environment variables)

## Project Structure

```
url-shortener/
├── Dockerfile
├── docker-compose.yml
├── index.js
├── package.json
├── .env
└── init.sql
```

## Setup Instructions

### Prerequisites

* Docker and Docker Compose installed
* Node.js installed (optional if running outside Docker)

### Steps

1. **Clone the repository**

```bash
git clone <repository-url>
cd url-shortener
```

2. **Create `.env` file**

```env
DATABASE_URL=postgres://postgres:password@db:5432/shortener
```

3. **Run the application with Docker Compose**

```bash
docker-compose up --build
```

* This will start both the Node.js app and PostgreSQL database.
* The database will be initialized using `init.sql`.

4. **Access the app**

* API endpoint to shorten URL: `POST http://localhost:3000/shorten`
* Redirect short URL: `GET http://localhost:3000/<short_code>`

### Example Request

```bash
curl -X POST http://localhost:3000/shorten \
-H "Content-Type: application/json" \
-d '{"original_url": "https://example.com"}'
```

### Stop the application

```bash
docker-compose down
```

