# CityMate Project Documentation

## 1. Introduction

CityMate is a smart tourist guide for Indian cities. It helps a traveller choose a city, discover places by category, read useful details, save favourites and open directions.

## 2. Problem Statement

Visitors often miss important attractions, food places and local experiences because information is spread across many sources. CityMate brings structured city information into one simple interface.

## 3. Objectives

- Provide a clear city and place discovery workflow.
- Make search, filtering and sorting fast for a traveller.
- Allow users to create an account and save places.
- Connect place discovery with practical map navigation.
- Create a clean, responsive application suitable for a college demonstration.

## 4. Proposed Solution

The application uses a responsive single-page interface. Seed data describes cities and places. IndexedDB stores the application records in the browser for the included demonstration. The relational schema in `database/schema.sql` shows how the same model can be deployed with a server database.

## 5. Features

Registration, login, logout, city selection, category filters, text search, popularity/rating/name sorting, place details, favorites, recently viewed records, responsive navigation and Google Maps links.

## 6. Functional Requirements

1. A visitor can view cities and select one.
2. A visitor can search and filter the selected city's places.
3. A visitor can open a place detail page.
4. A registered user can log in and log out.
5. A registered user can add and remove favorites.
6. A user can open Google Maps directions for a place.
7. Invalid forms show readable validation errors.

## 7. Non-functional Requirements

The interface is responsive, keyboard-friendly, lightweight, maintainable, and uses semantic HTML. Passwords are hashed before browser persistence in the demo. No API secret is included in client code.

## 8. Technology Used

HTML5, CSS3, JavaScript, IndexedDB, Web Crypto API and Google Maps URL integration. A future deployment can use Node.js, Express and MySQL using the supplied relational schema.

## 9. System Architecture

```text
Browser UI
  -> hash router and page renderers
  -> application services in app.js
  -> IndexedDB stores: users, cities, places, favorites, views
  -> external Google Maps destination URLs
```

The architecture is intentionally dependency-light so the project can be demonstrated from a local folder. The data access functions (`all`, `put`) form a small boundary that can later be replaced with HTTP API calls.

## 10. Database Design

- `users`: account identity and password hash.
- `cities`: name, state, description and image.
- `places`: city relationship, category, location, rating, popularity and practical visit information.
- `favorites`: many-to-many user/place relationship.
- `recently_viewed`: user place history.

Primary and foreign keys, unique email addresses and cascading relationships are documented in `database/schema.sql`.

## 11. Modules

- Home and city discovery module.
- Authentication module.
- City dashboard and search module.
- Place details module.
- Favorites module.
- Maps integration module.
- Persistence and seed data module.

## 12. User Flow

Home -> Cities -> City dashboard -> Search/category -> Place details -> Save favorite or Get directions. Registration can happen when the user chooses to save a place. Favorites are available from the navigation bar.

## 13. API Overview

The browser version does not require a server API. The production API can expose:

- `POST /api/auth/register`
- `POST /api/auth/login`
- `POST /api/auth/logout`
- `GET /api/cities`
- `GET /api/cities/:cityId/places?search=&category=&sort=`
- `GET /api/places/:placeId`
- `GET /api/favorites`
- `POST /api/favorites/:placeId`
- `DELETE /api/favorites/:placeId`

Every protected endpoint should validate a secure session on the server.

## 14. Google Maps Integration

Each place stores an address and coordinates. The demo creates encoded Google Maps search and directions URLs from the place name and address. This works without a Google API key. An embedded map can be added later by reading `GOOGLE_MAPS_API_KEY` from environment configuration rather than hard-coding it.

## 15. Future Scope

Add an Express backend, secure HTTP-only sessions, admin city/place CRUD, image uploads, live map markers, reviews, multilingual content, recommendation scoring, public transport information and email notifications.

## 16. Conclusion

CityMate demonstrates a complete tourism discovery workflow rather than a static collection of pages. Its separation of data, rendering and persistence gives the project a clear path from classroom demo to deployable application.
