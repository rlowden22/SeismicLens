# 🌋 Seismic Lens - Project Plan

## Project Overview

**Project Name:** Seismic Lens  
**Course:** Web Development - Project 2  
**Timeline:** 1 Week (7 days)  
**Estimated Hours:** 20-25 hours (3-4 hours/day)  
**Deployment Target:** Public server (Render/Railway/Heroku)

### What is Seismic Lens?

Seismic Lens is a full-stack geospatial web application that visualizes real-time earthquake activity and allows users to save interesting events and create custom map annotations. It demonstrates the integration of external APIs, database management, and interactive mapping in a practical geology/emergency management context.

---

## Technology Stack Explanation

### **Node.js**
- **Purpose:** JavaScript runtime environment that runs our server
- **Why:** Allows us to write backend code in JavaScript, handle HTTP requests, and manage server-side operations
- **Usage in this project:** 
  - Runs our Express server
  - Handles API requests from the frontend
  - Manages connections to MongoDB
  - Fetches data from external APIs (USGS)

### **Express.js**
- **Purpose:** Web application framework for Node.js
- **Why:** Simplifies creating API routes and handling HTTP requests
- **Usage in this project:**
  - Defines RESTful API endpoints (`/api/events`, `/api/annotations`)
  - Serves static HTML/CSS/JS files to the browser
  - Handles middleware (JSON parsing, CORS, error handling)
  - Routes requests to appropriate handler functions

### **MongoDB**
- **Purpose:** NoSQL document database
- **Why:** Flexible schema perfect for storing varied geological event data
- **Usage in this project:**
  - **Collection 1 (saved_events):** Stores earthquakes/volcanoes that users bookmark
  - **Collection 2 (annotations):** Stores custom user notes with geographic coordinates
  - Provides persistent storage for user-generated content
  - Native MongoDB driver used (NO Mongoose per assignment requirements)

### **JavaScript (Vanilla)**
- **Purpose:** Programming language for both frontend and backend
- **Why:** Required by assignment - no frameworks allowed on frontend
- **Usage in this project:**
  - **Backend (Node.js):** Server logic, database operations, API handling
  - **Frontend (Browser):** Client-side rendering, DOM manipulation, Leaflet map control
  - **ES6 Modules:** Modern `import/export` syntax (no `require()`)
  - Dynamic rendering of saved events and annotations without page reloads

### **Additional Technologies**
- **Leaflet.js:** Interactive map library for displaying earthquakes and annotations
- **USGS API:** Real-time earthquake data source
- **ESLint & Prettier:** Code quality and formatting tools

---

## Project Requirements Checklist

### Design Document (80 points)
- [ ] Project description (overview above)
- [ ] User personas (2-3 fictional users)
- [ ] User stories (5-10 stories)
- [ ] Design mockups (wireframes for main pages)

### Core Functionality (15 points each)
- [ ] App accomplishes all approved requirements
- [ ] Client-side rendering using vanilla JavaScript
- [ ] At least 1 working form
- [ ] At least 2 MongoDB Collections with CRUD operations
- [ ] JavaScript organized in modules

### Code Quality
- [ ] ESLint config file with no errors (5 pts)
- [ ] Code properly organized (files/folders) (5 pts)
- [ ] Formatted with Prettier (5 pts)
- [ ] CSS organized by modules (5 pts)
- [ ] Uses standard HTML tags appropriately (5 pts)
- [ ] No leftover/unused code (5 pts)
- [ ] Backend uses ES6 modules, NOT CJS/require (10 pts)

### Deployment & Documentation
- [ ] Deployed on public server and working (5 pts)
- [ ] Clear README with all required sections (10 pts)
- [ ] No exposed credentials (Mongo password hidden) (10 pts)
- [ ] package.json with dependencies (5 pts)
- [ ] MIT License file (5 pts)
- [ ] Short narrated video demonstration (10 pts)
- [ ] Google Form submission correct (5 pts)

### Other Requirements
- [ ] App is usable with instructions (5 pts)
- [ ] App is actually useful (5 pts)
- [ ] Node + Express backend (5 pts)
- [ ] Everything submitted on time (5 pts)

### **CRITICAL: Cannot Use**
- ❌ Mongoose ODM (use native MongoDB driver)
- ❌ Template engines (Pug, EJS, Handlebars)
- ❌ Frontend frameworks (React, Vue, Angular)

---

## Week Timeline

### **Day 1-2: Setup & Backend (6-8 hours total)**

#### Day 1 (3-4 hours)
- [ ] Initialize project repository
- [ ] Set up Node.js project (`npm init`)
- [ ] Install dependencies (express, mongodb, dotenv, cors)
- [ ] Create basic folder structure
- [ ] Set up Express server with basic route
- [ ] Connect to MongoDB (local or Atlas)
- [ ] Test connection with simple console log

**Folder Structure:**
```
seismic-lens/
├── server/
│   ├── server.js           # Main Express server
│   ├── db.js              # MongoDB connection
│   └── routes/
│       ├── events.js      # Saved events CRUD routes
│       └── annotations.js # Annotations CRUD routes
├── public/
│   ├── index.html
│   ├── css/
│   │   ├── main.css
│   │   └── map.css
│   └── js/
│       ├── main.js        # Entry point
│       ├── map.js         # Leaflet map logic
│       ├── api.js         # API calls module
│       └── ui.js          # DOM manipulation
├── .env                   # MongoDB credentials (gitignored)
├── .gitignore
├── package.json
├── README.md
└── LICENSE
```

#### Day 2 (3-4 hours)
- [ ] Create MongoDB collections schema (plan structure)
- [ ] Implement CRUD routes for `saved_events`
  - POST /api/events (create)
  - GET /api/events (read all)
  - PUT /api/events/:id (update)
  - DELETE /api/events/:id (delete)
- [ ] Implement CRUD routes for `annotations`
  - POST /api/annotations (create)
  - GET /api/annotations (read all)
  - PUT /api/annotations/:id (update)
  - DELETE /api/annotations/:id (delete)
- [ ] Test all routes with Thunder Client/Postman
- [ ] Set up ESLint and Prettier configs

**Deliverable:** Working backend API that can create, read, update, and delete items in both collections

---

### **Day 3-5: Frontend Development (6-9 hours total)**

#### Day 3 (2-3 hours)
- [ ] Create basic HTML structure (index.html)
  - Header with title
  - Map container
  - Sidebar for saved events list
  - Forms container
- [ ] Add Leaflet.js via CDN
- [ ] Initialize map centered on world view
- [ ] Fetch earthquake data from USGS API
- [ ] Display earthquakes as markers on map

**USGS API endpoint:**
```
https://earthquake.usgs.gov/earthquakes/feed/v1.0/summary/all_day.geojson
```

#### Day 4 (2-3 hours)
- [ ] Create JavaScript modules structure
- [ ] Implement `api.js` - functions to call backend API
- [ ] Implement `ui.js` - functions to update DOM
- [ ] Display saved events list (fetch from backend, render to sidebar)
- [ ] Add "Save Event" form
  - Form appears when clicking earthquake marker
  - Submit saves to database via POST request
  - List updates dynamically (client-side rendering)

#### Day 5 (2-3 hours)
- [ ] Implement "Create Annotation" form
  - Click map → form appears with coordinates
  - Add text note
  - Submit saves to database
- [ ] Display annotations on map as custom markers
- [ ] Implement delete functionality (delete button for each saved item)
- [ ] Add basic CSS styling
  - Responsive layout
  - Clean form styling
  - Map sizing

**Deliverable:** Working frontend that displays map, saves events, creates annotations, and updates dynamically

---

### **Day 6-7: Polish & Deploy (6-8 hours total)**

#### Day 6 (3-4 hours)
- [ ] Code cleanup
  - Remove console.logs
  - Remove unused code/comments
  - Run ESLint and fix all errors
  - Run Prettier on all files
- [ ] Organize CSS into modules
- [ ] Add update functionality (edit notes on saved events)
- [ ] Test all CRUD operations thoroughly
- [ ] Add error handling (try/catch, user-friendly messages)
- [ ] Create `.env.example` file (template without real credentials)
- [ ] Update `.gitignore` to exclude `.env`

#### Day 7 (3-4 hours)
- [ ] Deploy to Render/Railway/Heroku
- [ ] Configure environment variables on server
- [ ] Test deployed app thoroughly
- [ ] Write comprehensive README
  - Author, class link, objective
  - Screenshot of app
  - Installation instructions
  - How to use
  - Technologies used
  - API endpoints
- [ ] Add MIT License
- [ ] Record narrated video demo (5-10 minutes)
  - Show earthquake visualization
  - Demonstrate saving events
  - Create annotation
  - Show CRUD operations
  - Explain technical implementation briefly
- [ ] Submit Google Form with correct thumbnail/links
- [ ] Final git commit and freeze code

**Deliverable:** Fully deployed, documented, and demonstrated application

---

## Database Schema

### Collection 1: `saved_events`
```javascript
{
  _id: ObjectId,
  event_id: String,           // USGS event ID
  type: String,               // "earthquake" or "volcano"
  title: String,              // Event title from USGS
  magnitude: Number,          // Magnitude value
  coordinates: {
    lat: Number,
    lng: Number
  },
  depth: Number,              // Depth in km
  timestamp: Date,            // When event occurred
  user_notes: String,         // User's custom notes
  saved_at: Date              // When user saved it
}
```

### Collection 2: `annotations`
```javascript
{
  _id: ObjectId,
  coordinates: {
    lat: Number,
    lng: Number
  },
  annotation_text: String,    // User's note
  category: String,           // "observation", "analysis", "prediction"
  created_at: Date,
  updated_at: Date,
  related_event_id: String    // Optional: link to saved event
}
```

---

## API Endpoints

### Saved Events
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/events` | Get all saved events |
| POST | `/api/events` | Save a new event |
| PUT | `/api/events/:id` | Update event notes |
| DELETE | `/api/events/:id` | Delete saved event |

### Annotations
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/annotations` | Get all annotations |
| POST | `/api/annotations` | Create new annotation |
| PUT | `/api/annotations/:id` | Update annotation |
| DELETE | `/api/annotations/:id` | Delete annotation |

---

## User Personas

### Persona 1: Dr. Sarah Chen
**Role:** Geology Professor at UC Berkeley  
**Age:** 42  
**Tech Savvy:** High  
**Goals:**
- Track significant seismic events for research papers
- Annotate patterns in volcanic activity
- Share interesting events with students

**Pain Points:**
- Existing tools are too complex or too simple
- Needs quick way to bookmark events during lectures
- Wants to add context notes to events

### Persona 2: Mike Torres
**Role:** Emergency Management Coordinator, San Luis Obispo County  
**Age:** 38  
**Tech Savvy:** Medium  
**Goals:**
- Monitor local seismic activity
- Mark areas of concern for team briefings
- Keep historical record of significant events

**Pain Points:**
- Needs simple, reliable tool that works on mobile
- Must quickly identify high-magnitude events
- Wants to annotate map for team coordination

### Persona 3: Emma Rodriguez
**Role:** High School Earth Science Teacher  
**Age:** 29  
**Tech Savvy:** Medium  
**Goals:**
- Show students real-time earthquake data
- Create educational annotations for lessons
- Save examples of different magnitude events

**Pain Points:**
- Needs intuitive interface for classroom use
- Students should understand it quickly
- Wants to save examples for future lessons

---

## User Stories

### Viewing & Exploring
1. **As Dr. Sarah Chen**, I want to see real-time earthquake data on an interactive map, so that I can identify current seismic activity patterns
2. **As Emma Rodriguez**, I want to click on earthquake markers to see detailed information, so that I can explain event characteristics to my students
3. **As Mike Torres**, I want to quickly identify high-magnitude events, so that I can assess potential local threats

### Saving Events
4. **As Dr. Sarah Chen**, I want to save significant volcanic events with my own notes, so that I can reference them in my research papers
5. **As Emma Rodriguez**, I want to bookmark example earthquakes of different magnitudes, so that I can use them in future lessons
6. **As Mike Torres**, I want to save local seismic events, so that I can maintain a historical record for my county

### Creating Annotations
7. **As Mike Torres**, I want to annotate areas of concern on the map, so that I can brief my emergency response team on potential hazards
8. **As Dr. Sarah Chen**, I want to add analysis notes to specific locations, so that I can track my observations over time
9. **As Emma Rodriguez**, I want to create educational annotations on the map, so that students can see my explanations alongside the data

### Managing Data
10. **As all users**, I want to view my saved events in a list, so that I can quickly access previously bookmarked items
11. **As Dr. Sarah Chen**, I want to edit my notes on saved events, so that I can update my analysis as I learn more
12. **As Mike Torres**, I want to delete outdated annotations, so that my map stays relevant and uncluttered

---

## Design Mockups

### Main Page Layout
```
+----------------------------------------------------------+
|  🌋 SEISMIC LENS                                    [?]  |
+----------------------------------------------------------+
|                           |                              |
|  SAVED EVENTS            |                              |
|  ----------------        |                              |
|  🔴 M7.2 Japan           |                              |
|  📝 Major event...       |        LEAFLET MAP           |
|  [Edit] [Delete]         |      (Interactive World      |
|                          |         Map View)            |
|  🔴 M5.8 California      |                              |
|  📝 Local concern        |      • Earthquake markers    |
|  [Edit] [Delete]         |      • Annotation markers    |
|                          |      • Click to interact     |
|  [+ New Annotation]      |                              |
|                          |                              |
+----------------------------------------------------------+
```

### Save Event Form (Modal)
```
+--------------------------------+
|  Save Earthquake Event         |
+--------------------------------+
|  Title: M7.2 - Japan          |
|  Magnitude: 7.2               |
|  Depth: 35 km                 |
|  Date: 2025-10-02             |
|                               |
|  Your Notes:                  |
|  +-------------------------+  |
|  |                         |  |
|  |                         |  |
|  +-------------------------+  |
|                               |
|  [Cancel]  [Save Event]       |
+--------------------------------+
```

### Create Annotation Form
```
+--------------------------------+
|  Create Annotation             |
+--------------------------------+
|  Location: 35.5°N, 120.7°W    |
|                               |
|  Category:                    |
|  ( ) Observation              |
|  (•) Analysis                 |
|  ( ) Prediction               |
|                               |
|  Annotation:                  |
|  +-------------------------+  |
|  |                         |  |
|  |                         |  |
|  +-------------------------+  |
|                               |
|  [Cancel]  [Create]           |
+--------------------------------+
```

---

## MVP Features (Must Have)

✅ **Core Features:**
- Display real-time earthquakes on Leaflet map
- Save events to database with user notes
- Create custom annotations with coordinates
- View all saved events in sidebar list
- Delete saved events and annotations
- Client-side rendering (no page reloads)
- Full CRUD on both collections
- At least 2 working forms

✅ **Technical Requirements:**
- Node + Express backend
- MongoDB with native driver (no Mongoose)
- Vanilla JavaScript client-side rendering
- ES6 modules (import/export)
- ESLint + Prettier
- Deployed and working

---

## Nice-to-Have Features (If Time Permits)

⭐ **Enhancement Ideas:**
- Filter earthquakes by magnitude/date
- Update saved event notes (PUT operation)
- Search functionality for saved events
- Different marker colors by magnitude
- Click annotation marker to view/edit
- Export saved events as JSON
- Volcanic eruption data integration
- User authentication

**NOTE:** Focus on MVP first. Only add enhancements if you finish early!

---

## Daily Progress Tracker

### Day 1: ___/___/___ (Hours: ____)
**Completed:**
- [ ] 
- [ ] 
- [ ] 

**Issues/Notes:**
- 

**Tomorrow's Goal:**
- 

---

### Day 2: ___/___/___ (Hours: ____)
**Completed:**
- [ ] 
- [ ] 
- [ ] 

**Issues/Notes:**
- 

**Tomorrow's Goal:**
- 

---

### Day 3: ___/___/___ (Hours: ____)
**Completed:**
- [ ] 
- [ ] 
- [ ] 

**Issues/Notes:**
- 

**Tomorrow's Goal:**
- 

---

### Day 4: ___/___/___ (Hours: ____)
**Completed:**
- [ ] 
- [ ] 
- [ ] 

**Issues/Notes:**
- 

**Tomorrow's Goal:**
- 

---

### Day 5: ___/___/___ (Hours: ____)
**Completed:**
- [ ] 
- [ ] 
- [ ] 

**Issues/Notes:**
- 

**Tomorrow's Goal:**
- 

---

### Day 6: ___/___/___ (Hours: ____)
**Completed:**
- [ ] 
- [ ] 
- [ ] 

**Issues/Notes:**
- 

**Tomorrow's Goal:**
- 

---

### Day 7: ___/___/___ (Hours: ____)
**Completed:**
- [ ] 
- [ ] 
- [ ] 

**Issues/Notes:**
- 

**Final Submission:**
- [ ] Code frozen on GitHub
- [ ] Video uploaded
- [ ] Deployed and tested
- [ ] Google Form submitted

---

## Resources & References

### Documentation
- [Express.js Docs](https://expressjs.com/)
- [MongoDB Node Driver](https://www.mongodb.com/docs/drivers/node/current/)
- [Leaflet.js](https://leafletjs.com/)
- [USGS Earthquake API](https://earthquake.usgs.gov/earthquakes/feed/v1.0/geojson.php)

### Tutorials
- [MongoDB Native Driver Tutorial](https://www.mongodb.com/docs/drivers/node/current/quick-start/)
- [Leaflet Quick Start](https://leafletjs.com/examples/quick-start/)
- [Express Routing Guide](https://expressjs.com/en/guide/routing.html)

### Deployment
- [Render Deployment Guide](https://render.com/docs)
- [Railway Deployment](https://docs.railway.app/)
- [MongoDB Atlas Setup](https://www.mongodb.com/docs/atlas/getting-started/)

---

## Troubleshooting Common Issues

### MongoDB Connection Issues
- Check if MongoDB is running locally
- Verify connection string in `.env`
- Ensure IP whitelist on MongoDB Atlas

### CORS Errors
- Add CORS middleware to Express
- Check frontend is making requests to correct URL

### Leaflet Map Not Displaying
- Verify Leaflet CSS is included in HTML
- Check map container has explicit height in CSS
- Console.log to verify data is being fetched

### Client-Side Rendering Not Working
- Check browser console for errors
- Verify API endpoints are returning data
- Use `console.log` to debug data flow

---

## Notes & Ideas

*Use this section for any additional thoughts, questions, or ideas that come up during development*

- 
- 
- 

---

## Success Criteria

This project will be considered successful when:

1. ✅ All rubric requirements are met (see checklist above)
2. ✅ A user can visit the deployed site and immediately see earthquake data
3. ✅ A user can save an event and see it appear in their saved list
4. ✅ A user can create an annotation and see it on the map
5. ✅ A user can delete items they've created
6. ✅ The code is clean, organized, and follows best practices
7. ✅ The video demonstration clearly shows all functionality
8. ✅ The app impresses as a professional portfolio piece for Esri

**Remember:** Done is better than perfect. Focus on functionality first, polish second.

Good luck! 🚀