Collecting workspace information# Real-Time Tracker Application Documentation

## Overview

The Real-Time Tracker is a Node.js web application that enables real-time location tracking of users on a map. It uses [Express](https://expressjs.com/), [Socket.IO](https://socket.io/), [EJS](https://ejs.co/), and [Leaflet](https://leafletjs.com/) for the backend and frontend, providing seamless, live updates of user locations.

---

## Features

- Real-time geolocation tracking using browser APIs
- Live map updates with [Leaflet](https://leafletjs.com/)
- Multiple users tracked simultaneously
- Automatic marker removal when users disconnect

---

## Project Structure

```
app.js
package.json
steps.yaml
public/
  css/
    style.css
  js/
    script.js
views/
  index.ejs
```

---

## Installation

1. **Clone the repository**

   ```sh
   git clone <repo-url>
   cd RealtimeTracker
   ```

2. **Install dependencies**

   ```sh
   npm install
   ```

3. **Start the server**
   ```sh
   node app.js
   ```
   The app runs on [http://localhost:3000](http://localhost:3000).

---

## Usage

1. Open [http://localhost:3000](http://localhost:3000) in your browser.
2. Allow location access when prompted.
3. Your location will appear on the map. Other users opening the app will also appear in real time.

---

## File Descriptions

### app.js

- Main server file.
- Sets up Express, Socket.IO, and EJS.
- Handles socket events for sending and receiving location data.
- Serves static files and the main view.

### script.js

- Handles geolocation tracking in the browser.
- Emits location updates to the server via Socket.IO.
- Updates the map and markers in real time.

### style.css

- Styles for the map and page layout.

### index.ejs

- Main HTML template rendered by Express.
- Loads Leaflet and Socket.IO scripts.
- Contains the map container.

### steps.yaml

- Step-by-step outline of the application's logic.

---

## Socket Events

- **send-location**: Emitted by the client with `{ latitude, longitude }`.
- **receive-location**: Broadcast by the server with `{ id, latitude, longitude }`.
- **user-disconnected**: Broadcast by the server with the user's socket id.

---

## How It Works

1. **Client connects**:  
   The browser requests geolocation and starts sending updates via `send-location`.

2. **Server receives location**:  
   On each update, the server emits `receive-location` to all clients, including the sender.

3. **Map updates**:  
   Each client updates or creates a marker for the user on the map.

4. **User disconnects**:  
   The server emits `user-disconnected`, and clients remove the corresponding marker.

---

## Dependencies

- express
- socket.io
- ejs
- leaflet (via CDN)

---

## License

ISC © Prathamesh Magar

---

## Author

Prathamesh Magar

---

For more details, see the source files:

- app.js
- script.js
- index.ejs
- style.css
- steps.yaml
