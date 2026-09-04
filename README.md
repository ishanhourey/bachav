# Bachav

**Report. Connect. Rescue.**

Bachav is a beginner-friendly, functional front-end prototype for an animal rescue and emergency reporting platform. It demonstrates the complete college-project flow in the browser:

`Citizen report -> Case ID -> Rescuer accepts -> Status updates -> Citizen tracks`

## Run it

1. Install VS Code and a modern browser such as Chrome or Edge.
2. Open this folder in VS Code.
3. Open `index.html` in a browser. The VS Code Live Server extension is optional, but recommended for a smoother local experience.
4. Use the **Log in** button to try one of the demo roles below.

No npm, database server, API key, or build step is required for this demonstration. Cases and the signed-in user are stored in the browser's `localStorage`, so refreshing the page keeps your demo data. Use the browser developer tools to clear site data and reset the demo.

## Demo accounts

These credentials are fictional and for demonstration only.

| Role | Email | Password |
| --- | --- | --- |
| Citizen | `user@bachav.demo` | `DemoUser123` |
| Rescuer | `rescuer@bachav.demo` | `DemoRescue123` |
| Administrator | `admin@bachav.demo` | `DemoAdmin123` |

## Main files

- `index.html` - application shell, accessible navigation, login modal, and footer
- `styles.css` - responsive visual system and page layouts
- `app.js` - seeded data, routing, authentication demo, report form, upload preview, geolocation request, case workflow, and notifications
- `demo.py` - original empty workspace file, retained unchanged

## Demonstration checklist

1. Open `#report` and submit a Dog or Cat report with a location and description.
2. Confirm the generated case ID and `Reported` status.
3. Sign out, log in as the rescuer, and open the new case from **Available cases**.
4. Use **Accept rescue** / **Update status** repeatedly to show the timeline moving toward `Case Resolved`.
5. Sign in as the citizen again and open **My dashboard** to show the same case status.
6. Sign in as the administrator and open **Admin console** to show network statistics and reports.

## Technical extension path

For a production version, replace the demo objects and `localStorage` calls in `app.js` with a backend API and database. Suggested tables are `users`, `rescuers`, `animal_reports`, `rescue_updates`, and `notifications`. Store password hashes on the server, protect role-based routes there, and use a maps provider such as OpenStreetMap/Leaflet or Google Maps through environment configuration. The current map is a visual fallback and the AI section is explicitly a prototype upload acknowledgement, not a medical diagnosis or a real classification model.

## Minor-project presentation notes

**Problem:** People find injured animals but cannot quickly reach a suitable local responder, while rescuers lack structured, timely case information.

**Solution:** Bachav creates a shared reporting and coordination channel for citizens, verified rescuers, and administrators.

**Objectives:** Capture reliable case details, connect reports with nearby responders, provide transparent status tracking, and improve accountability.

**Modules:** Authentication and roles, emergency report intake, photo preview, location request, citizen dashboard, rescuer queue, case status workflow, admin monitoring, notifications, and future AI integration.

**Technology:** HTML5, CSS3, vanilla JavaScript, browser Geolocation API, FileReader API, and localStorage for the classroom prototype.

**Future scope:** Secure backend authentication, PostgreSQL or MongoDB persistence, verified rescuer onboarding, real map markers, SMS/email notifications, analytics, and a trained image classification service.

**Limitations:** This prototype has no server-side authentication, real-time notifications, cloud image storage, or medical diagnosis. It is suitable for demonstration and UI/workflow evaluation, not real emergency operations.
