# Seismic Lens - Design Document

**Project Name:** Seismic Lens  
**Author:** Rowan Lowden  
**Course:** 5610 
**Date:** October 2025

---

## 1. Project Description

**Seismic Lens** is a full-stack geospatial web application that visualizes real-time earthquake activity and allows users to save significant events and create custom map annotations.

### Problem
Current earthquake monitoring tools don't allow users to save events or add personal notes. Researchers, educators, and emergency managers need a way to bookmark significant earthquakes and annotate maps with their observations.

### Solution
Seismic Lens provides:
- Real-time earthquake visualization from USGS data
- Ability to save events with custom notes
- Geographic annotation system for marking observations
- Persistent storage in MongoDB
- Simple, intuitive interface

### Target Users
- Geology professors tracking events for research
- Emergency managers monitoring local seismic activity
- Teachers creating educational examples
- Geology enthusiasts building personal archives

### Tech Stack
- **Frontend:** HTML5, CSS3, Vanilla JavaScript, Leaflet.js
- **Backend:** Node.js, Express.js
- **Database:** MongoDB (native driver, no Mongoose)
- **API:** USGS Earthquake API

---

## 2. User Personas

### Persona 1: Dr. Sarah Chen - Geology Professor
**Age:** 42 | **Tech Level:** High

**Goals:**
- Track significant seismic events for research papers
- Save events with detailed notes for lectures
- Build personal archive of notable earthquakes

**Pain Points:**
- USGS doesn't allow saving or bookmarking
- No way to add context notes to events
- Needs quick access during lectures

**Quote:** *"I need a tool powerful enough for research but simple enough to use during a live lecture."*

---

### Persona 2: Mike Torres - Emergency Manager
**Age:** 38 | **Tech Level:** Medium

**Goals:**
- Monitor local seismic activity daily
- Mark areas of concern for team briefings
- Maintain historical record of county events

**Pain Points:**
- Needs simple, reliable tools for stressful situations
- Can't easily annotate maps for team coordination
- Must work on mobile during emergencies

**Quote:** *"In emergency management, I need information fast and I need to share it clearly with my team."*

---

### Persona 3: Emma Rodriguez - High School Teacher
**Age:** 29 | **Tech Level:** Medium

**Goals:**
- Show students real-time earthquake data
- Save example earthquakes of different magnitudes
- Create educational annotations for lessons

**Pain Points:**
- Scientific tools too complex for classroom
- Can't easily save teaching examples
- Students need intuitive interface

**Quote:** *"If I can show my students this is happening RIGHT NOW, they're 10x more engaged."*

---

## 3. User Stories

### Viewing Earthquakes
1. **As Dr. Sarah Chen**, I want to see real-time earthquake data on an interactive map, so that I can identify current seismic patterns
2. **As Emma Rodriguez**, I want to click earthquake markers to see details, so that I can explain events to students

### Saving Events
3. **As Dr. Sarah Chen**, I want to save significant events with notes, so that I can reference them in research papers
4. **As Mike Torres**, I want to save local seismic events, so that I can maintain a historical record
5. **As all users**, I want to view my saved events in a list, so that I can quickly access bookmarked items
6. **As Dr. Sarah Chen**, I want to edit my notes on saved events, so that I can update my analysis
7. **As Mike Torres**, I want to delete outdated events, so that my list stays relevant

### Creating Annotations
8. **As Mike Torres**, I want to create map annotations, so that I can mark areas of concern for team briefings
9. **As Emma Rodriguez**, I want to add educational annotations, so that students can see my explanations
10. **As Dr. Sarah Chen**, I want to edit annotations, so that I can refine my analysis over time
11. **As all users**, I want to delete annotations, so that my map stays uncluttered

---

## 4. Design Mockups

### Main Application View (Desktop)

```
┌────────────────────────────────────────────────────────────────┐
│  🌋 SEISMIC LENS                               [Help] [About]  │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│  ┌──────────────┐  ┌─────────────────────────────────────┐   │
│  │ SAVED EVENTS │  │                                     │   │
│  │ ──────────── │  │                                     │   │
│  │              │  │                                     │   │
│  │ 🔴 M7.2      │  │          LEAFLET MAP                │   │
│  │ Japan        │  │      (Interactive World)            │   │
│  │ Oct 1, 2025  │  │                                     │   │
│  │ "Major..."   │  │   • Red circles = Earthquakes       │   │
│  │ [Edit][Del]  │  │   • Blue pins = Annotations         │   │
│  │ ──────────── │  │   • Click to interact               │   │
│  │              │  │                                     │   │
│  │ 🔴 M5.8      │  │                                     │   │
│  │ California   │  │                                     │   │
│  │ Sep 30       │  │                                     │   │
│  │ [Edit][Del]  │  │                                     │   │
│  │              │  │                                     │   │
│  │ ANNOTATIONS  │  │                                     │   │
│  │ ──────────── │  │                                     │   │
│  │ 📍 San       │  │                                     │   │
│  │ Andreas...   │  │                                     │   │
│  │ [Edit][Del]  │  │                                     │   │
│  │              │  └─────────────────────────────────────┘   │
│  │ [+ New]      │                                            │
│  └──────────────┘                                            │
└────────────────────────────────────────────────────────────────┘
```

---

### Earthquake Popup

```
┌─────────────────────────────┐
│ Earthquake Details      [×] │
├─────────────────────────────┤
│ Location: Tokyo, Japan      │
│ Magnitude: 7.2              │
│ Depth: 35 km                │
│ Time: Oct 1, 2025 14:23 UTC │
│                             │
│ [💾 Save Event] [USGS Link] │
└─────────────────────────────┘
```

---

### Save Event Form

```
┌─────────────────────────────────┐
│ 💾 Save Earthquake Event        │
├─────────────────────────────────┤
│ Location: Tokyo, Japan          │
│ Magnitude: 7.2                  │
│ Depth: 35 km                    │
│ Date: Oct 1, 2025               │
│                                 │
│ Your Notes:                     │
│ ┌───────────────────────────┐   │
│ │ Add notes here...         │   │
│ │                           │   │
│ └───────────────────────────┘   │
│ (Max 500 characters)            │
│                                 │
│    [Cancel]  [💾 Save Event]    │
└─────────────────────────────────┘
```

---

### Create Annotation Form

```
┌─────────────────────────────────┐
│ 📍 Create Annotation            │
├─────────────────────────────────┤
│ Location: 35.5°N, 120.7°W       │
│                                 │
│ Category:                       │
│ ○ Observation                   │
│ ● Analysis                      │
│ ○ Prediction                    │
│                                 │
│ Annotation:                     │
│ ┌───────────────────────────┐   │
│ │ Your observation...       │   │
│ │                           │   │
│ └───────────────────────────┘   │
│ (Max 500 characters)            │
│                                 │
│   [Cancel]  [📍 Create]         │
└─────────────────────────────────┘
```

---

### Mobile View

```
┌──────────────┐
│ 🌋 LENS  ☰  │
├──────────────┤
│              │
│   LEAFLET    │
│     MAP      │
│  (Fullscreen)│
│              │
│  Touch to    │
│  interact    │
│              │
├──────────────┤
│ [📋][+Add]   │
└──────────────┘
```

**Mobile Features:**
- Hamburger menu for saved items
- Full-screen map
- Touch-friendly buttons
- Bottom action bar

---

## 5. Database Schema

### Collection 1: saved_events

```javascript
{
  _id: ObjectId,
  event_id: String,        // USGS ID
  type: String,            // "earthquake"
  title: String,           // Event title
  magnitude: Number,
  coordinates: {
    lat: Number,
    lng: Number
  },
  depth: Number,
  timestamp: Date,         // Event time
  user_notes: String,      // User's notes
  saved_at: Date          // When saved
}
```

### Collection 2: annotations

```javascript
{
  _id: ObjectId,
  coordinates: {
    lat: Number,
    lng: Number
  },
  annotation_text: String,
  category: String,        // "observation", "analysis", "prediction"
  created_at: Date,
  updated_at: Date,
  related_event_id: String // Optional
}
```

---

## 6. API Endpoints

### Saved Events
- `GET /api/events` - Get all saved events
- `POST /api/events` - Save new event
- `PUT /api/events/:id` - Update event notes
- `DELETE /api/events/:id` - Delete event

### Annotations
- `GET /api/annotations` - Get all annotations
- `POST /api/annotations` - Create annotation
- `PUT /api/annotations/:id` - Update annotation
- `DELETE /api/annotations/:id` - Delete annotation

---

## 7. Technical Architecture

```
Frontend (Browser)
├── HTML/CSS/JavaScript
├── Leaflet.js for maps
└── Fetch API calls

    ↕ HTTP

Express Backend
├── Routes (events, annotations)
├── MongoDB native driver
└── CORS middleware

    ↕

MongoDB Database
├── saved_events collection
└── annotations collection

External:
└── USGS Earthquake API (fetched by frontend)
```

---

## 8. Key Features (MVP)

**Must Have:**
- ✅ Display real-time earthquakes on map
- ✅ Save events with notes (CRUD)
- ✅ Create annotations (CRUD)
- ✅ View saved items in sidebar
- ✅ Edit and delete functionality
- ✅ Client-side rendering (vanilla JS)
- ✅ Mobile responsive

**Nice to Have (if time):**
- Filter by magnitude/date
- Search saved events
- Export data
- Different marker colors by magnitude

---

## Success Criteria

✅ User can view earthquakes immediately  
✅ User can save event in under 30 seconds  
✅ User can create annotation in under 45 seconds  
✅ All CRUD operations work reliably  
✅ Interface is intuitive without instructions  
✅ Works on both desktop and mobile  
✅ Code is clean and well-organized