# Infra Guard

Infra Guard is a static web demo for a Smart City monitoring app. It uses webcam-based image classification with Teachable Machine models to detect road cleanliness and waste categories, then sends reclamation alerts to Firebase Realtime Database. An admin dashboard displays incoming alerts on a Leaflet map.

## Project structure

- `index.html` - User scanner interface
- `admin.html` - Admin dashboard for reviewing and resolving alerts
- `models/road/` - Teachable Machine model assets for road cleanliness
- `models/waste/` - Teachable Machine model assets for waste classification

## Features

- Switch between `road` and `waste` scanning modes
- Live webcam capture and model prediction
- Display prediction label and confidence
- Send alert to Firebase with GPS coordinates and timestamp
- Admin view with realtime Firebase updates
- Leaflet map with markers for each reclamation
- Delete resolved alerts from Firebase

## Dependencies

The project loads dependencies from CDN inside the HTML files:

- Firebase Realtime Database Compat SDK
- TensorFlow.js
- Teachable Machine image library
- Leaflet map library

## How to use

1. Open `index.html` in a browser that supports webcam access.
2. Select a mode: `Route (Propre/Sale)` or `Déchets (Plastique...)`.
3. Allow webcam and geolocation access.
4. The app classifies the camera view and shows the top result with confidence.
5. Press `🚨 ENVOYER RÉCLAMATION` to send the alert to Firebase.
6. Open `admin.html` to monitor incoming reclamations on the map.

## Firebase configuration

Both pages are configured to use the same Firebase Realtime Database URL:

- `https://smartcity-b4b77-default-rtdb.firebaseio.com/`

Alerts are stored under the `reclamations` node.

## Model details

### Road model

- Labels: `dirty road`, `clean road`
- Folder: `models/road/`

### Waste model

- Labels: `plastic`, `metal`, `cardboard`
- Folder: `models/waste/`

## Notes

- This project is intended as a local static demo and does not include server-side code.
- For production usage, host the files on a web server and secure the Firebase database rules.
