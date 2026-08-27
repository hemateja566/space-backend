# Space Backend

Backend API for the Space Explorer application. Built with Node.js and Express, using JSON Server for rapid prototyping.

## Overview

RESTful API providing space-related data (planets, missions, astronauts, etc.) for the Space Explorer frontend.

## Features

- RESTful endpoints for space data
- JSON-based database (db.json)
- CORS enabled for frontend integration
- Lightweight, zero-config setup

## Project Structure

```
space-backend/
â”œâ”€â”€ db.json              # Mock database
â”œâ”€â”€ package.json         # Dependencies & scripts
â”œâ”€â”€ package-lock.json    # Locked dependencies
â”œâ”€â”€ node_modules/        # Installed packages
â””â”€â”€ README.md
```

## Tech Stack

- **Runtime**: Node.js
- **API**: json-server (Express-based)
- **Database**: JSON file (db.json)
- **Deployment**: Can deploy to Heroku, Railway, Render

## Getting Started

### Prerequisites

- Node.js 16+
- npm

### Installation

```bash
cd space-backend
npm install
```

### Running the Server

```bash
# Start json-server on port 3001
npm start
# Or directly:
npx json-server --watch db.json --port 3001
```

Server runs at `http://localhost:3001`

## API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/planets` | List all planets |
| GET | `/planets/:id` | Get planet by ID |
| POST | `/planets` | Create new planet |
| PUT | `/planets/:id` | Update planet |
| DELETE | `/planets/:id` | Delete planet |
| GET | `/missions` | List all missions |
| GET | `/astronauts` | List all astronauts |
| GET | `/agencies` | List space agencies |

## Database Schema (db.json)

```json
{
  "planets": [
    { "id": 1, "name": "Earth", "type": "Terrestrial", "moons": 1, "distanceFromSun": 1 }
  ],
  "missions": [
    { "id": 1, "name": "Apollo 11", "year": 1969, "status": "Completed" }
  ],
  "astronauts": [
    { "id": 1, "name": "Neil Armstrong", "nationality": "American", "missions": 2 }
  ],
  "agencies": [
    { "id": 1, "name": "NASA", "country": "USA", "founded": 1958 }
  ]
}
```

## Available Queries

json-server supports:
- Filtering: `/planets?type=Terrestrial`
- Sorting: `/planets?_sort=distanceFromSun&_order=asc`
- Pagination: `/planets?_page=1&_limit=10`
- Search: `/planets?q=Mars`
- Relationships: `/planets/1/missions` (if defined)

## Development

```bash
# Watch for changes
npm run dev
```

## Deployment

### Heroku
```bash
heroku create space-backend-api
git push heroku main
```

### Railway/Render
- Connect GitHub repo
- Set start command: `npx json-server --watch db.json --port $PORT --host 0.0.0.0`

## License

MIT License