# CityMate - Smart Tourist Guide for Indian Cities

CityMate is a functional, responsive tourist guide for discovering Indian cities like a local. It supports city selection, category browsing, search, sorting, place details, Google Maps navigation, registration, login, recently viewed places, and per-user favorites.

## Why this project

Tourists often know the name of a city but not the places that make it memorable. CityMate organizes attractions, food, history, nature, cafes, shopping and religious places into one simple experience.

## Features

- Eight seeded cities: Indore, Bhopal, Ujjain, Jaipur, Delhi, Mumbai, Agra and Varanasi.
- Indore demo data including Rajwada Palace, Lal Bagh Palace, Sarafa Bazaar, Chappan Dukan, Patalpani, Regional Park, Central Museum and Annapurna Temple.
- Registration with validation and SHA-256 password hashing through Web Crypto.
- Login, persistent browser session and logout.
- IndexedDB persistence for users, cities, places, favorites and viewed places.
- Search by place name, category or description.
- Category filters and sorting by popularity, rating and name.
- Detailed place pages with hours, fee, address, rating and contact notes.
- Google Maps search and directions links without an embedded secret API key.
- Responsive navigation and mobile layouts.
- Empty states, validation errors and user-friendly notifications.

## Technology stack

- HTML5, CSS3 and modern browser JavaScript.
- IndexedDB for a proper local relational-style data store during demonstration.
- Web Crypto API for password hashing.
- Google Maps URL integration; no API key is required for destination links.
- No build step or dependency folder is needed for the included demo.

## Run locally

1. Open this folder in VS Code.
2. Open `index.html` in Chrome or Edge, or serve the folder with VS Code Live Server.
3. Visit `#cities`, choose a city, search or filter places, and open a place detail page.
4. Create an account from **Log in**. The browser will create the IndexedDB database automatically.

A local server is recommended because browser security policies vary when files are opened directly. The app does not require npm for the included browser version.

## Data and database setup

On the first launch, `app.js` seeds the `cities` and `places` IndexedDB object stores. User accounts and favorites are created as the user works. Browser DevTools > Application > IndexedDB can be used to inspect the database.

`database/schema.sql` contains the equivalent relational schema for a future Node/Express + MySQL implementation. It is included for the college project architecture and viva discussion.

## Environment variables and Google Maps

The current implementation uses public Google Maps destination URLs and therefore does not expose credentials. `.env.example` documents the optional values for a production backend or an embedded Maps JavaScript API:

```env
GOOGLE_MAPS_API_KEY=your_api_key_here
DATABASE_URL=mysql://user:password@localhost:3306/citymate
SESSION_SECRET=replace_with_a_long_random_value
```

Never commit a real API key or password. If an embedded map is added later, load the key from a server-side environment configuration.

## Project structure

```text
CityMate/
├── index.html                 # application shell and authentication modal
├── styles.css                 # responsive visual system
├── app.js                    # data, IndexedDB, routes, UI and interactions
├── database/schema.sql       # production-oriented relational schema
├── database/seed.json        # starter data reference
├── .env.example              # safe configuration template
├── PROJECT_DOCUMENTATION.md  # viva-friendly report
└── CityMate_Tourist_Guide_Minor_Project.zip
```

## Demonstration checklist

1. Choose Indore from the home page.
2. Search for `Rajwada` and open the result.
3. Use **Get directions** and confirm the Google Maps URL opens.
4. Register a new account, save the place, and open **Favorites**.
5. Log out and confirm favorites are isolated to the account.
6. Try a category chip such as **Food & Restaurants** and sort by rating.
7. Resize the browser to verify the mobile navigation and responsive cards.

## Production extension

For deployment, replace the IndexedDB service with an Express API, move password hashing to the server with bcrypt or Argon2, use secure HTTP-only sessions, validate all request bodies, and connect the tables in `database/schema.sql` to MySQL or PostgreSQL. Add server-side admin middleware before exposing city/place CRUD operations.

## Limitations of the classroom demo

Venue hours, fees and contacts are explicitly marked as demo information where appropriate. The app uses curated remote Unsplash images and local browser persistence, so it is ready for a viva and functional demonstration but is not a multi-device production service yet.
