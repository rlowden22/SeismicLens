# 🌋 Seismic Lens

**Seismic Lens** is a full-stack geospatial web application that visualizes real-time earthquake activity worldwide and allows users to save events and create custom map annotations. Built with modern web technologies, it provides an interactive platform for exploring Earth's dynamic geological processes.

![Seismic Lens Demo](link-to-screenshot.png) <!-- Add screenshot here -->

**Author:** [Your Name]  
**Course:** [Course Name and Link]  
**Project Objective:** Build a full-stack web application using Node.js, Express, MongoDB (native driver), and vanilla JavaScript to visualize real-time seismic data with user annotation capabilities.

---

## 🌍 Overview

Seismic Lens combines real-time earthquake monitoring from USGS with user-driven data management, offering an analytical view into global tectonic activity. Through an interactive Leaflet.js map interface, users can explore earthquake patterns, save significant events, and create custom geographic annotations for research, education, or emergency management purposes.

This application demonstrates practical integration of external APIs, NoSQL database management, client-side rendering without frameworks, and RESTful API design.

---

## ✨ Features

### Core Functionality
- **Real-Time Earthquake Visualization**: Live earthquake feed from USGS displaying magnitude, depth, location, and timestamp
- **Interactive Leaflet Map**: Click-to-interact map with custom markers and detailed pop-ups
- **Save Earthquake Events**: Bookmark significant events with custom notes for future reference
- **Custom Map Annotations**: Create geographic annotations with coordinates and categorized observations
- **Client-Side Rendering**: Dynamic content updates without page reloads using vanilla JavaScript
- **Full CRUD Operations**: Create, Read, Update, and Delete functionality on saved events and annotations
- **Responsive Design**: Mobile-friendly interface that works across devices

### Technical Features
- **RESTful API Architecture**: Clean, organized backend API endpoints
- **MongoDB Persistence**: Two collections storing user-generated content
- **ES6 Module System**: Modern JavaScript with import/export syntax
- **No Template Engines**: Pure client-side rendering for maximum flexibility
- **Native MongoDB Driver**: Direct database integration without ODM abstractions

---

## 🛠️ Tech Stack

### Frontend
- **HTML5** - Semantic markup structure
- **CSS3** - Modular styling with responsive design
- **Vanilla JavaScript** - ES6 modules for client-side logic
- **Leaflet.js** - Interactive mapping library

### Backend
- **Node.js** - JavaScript runtime environment
- **Express.js** - Web application framework
- **MongoDB Native Driver** - Database connectivity (no Mongoose)

### External APIs
- **USGS Earthquake API** - Real-time seismic data feed

### Development Tools
- **ESLint** - Code linting and quality assurance
- **Prettier** - Code formatting
- **Git** - Version control

### Deployment
- **[Render/Railway/Heroku]** - Cloud hosting platform
- **MongoDB Atlas** - Cloud database hosting

---

## 📊 Database Schema

### Collection 1: `saved_events`
Stores earthquake events that users have bookmarked for future reference.

```javascript
{
  _id: ObjectId,
  event_id: String,           // USGS event ID
  type: String,               // "earthquake"
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
Stores user-created geographic annotations and observations.

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

## 🔌 API Endpoints

### Saved Events
| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/events` | Retrieve all saved events |
| `POST` | `/api/events` | Save a new earthquake event |
| `PUT` | `/api/events/:id` | Update notes on saved event |
| `DELETE` | `/api/events/:id` | Delete a saved event |

### Annotations
| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/annotations` | Retrieve all annotations |
| `POST` | `/api/annotations` | Create a new annotation |
| `PUT` | `/api/annotations/:id` | Update an annotation |
| `DELETE` | `/api/annotations/:id` | Delete an annotation |

---

## 📋 Prerequisites

Before running this project, ensure you have:

- **Node.js** (v14 or higher)
- **MongoDB** (local installation or MongoDB Atlas account)
- **npm** or **yarn** package manager
- **Git** for version control

---

## 🚀 Getting Started

### Installation

1. **Clone the repository**
```bash
git clone https://github.com/yourusername/seismic-lens.git
cd seismic-lens
```

2. **Install dependencies**
```bash
npm install
```

3. **Set up environment variables**

Create a `.env` file in the root directory:

```env
MONGODB_URI=your_mongodb_connection_string
PORT=3000
```

**Note:** Never commit your `.env` file. Use `.env.example` as a template.

4. **Start MongoDB**

If using local MongoDB:
```bash
mongod
```

If using MongoDB Atlas, ensure your connection string is correct in `.env`

5. **Run the application**
```bash
npm start
```

6. **Open in browser**
```
http://localhost:3000
```

---

## 📖 How to Use

### Viewing Earthquakes
1. Open the application - the map will automatically load recent earthquake data from USGS
2. Earthquake markers appear as circles on the map
3. Click any marker to view event details (magnitude, depth, location, time)

### Saving Events
1. Click on an earthquake marker
2. Click the "Save Event" button in the popup
3. Add optional notes about why this event is significant
4. Click "Save" - the event appears in your saved events sidebar
5. View, edit, or delete saved events from the sidebar

### Creating Annotations
1. Click the "Add Annotation" button or click anywhere on the map
2. Enter your observation text
3. Select a category (observation, analysis, or prediction)
4. Click "Create" - your annotation appears as a custom marker
5. Click annotation markers to view, edit, or delete them

### Managing Data
- **Edit**: Click the edit icon on saved items to update notes
- **Delete**: Click the delete icon to remove items
- All changes sync with the MongoDB database automatically

---

## 📁 Project Structure

```
seismic-lens/
├── server/
│   ├── server.js              # Express server setup
│   ├── db.js                  # MongoDB connection
│   └── routes/
│       ├── events.js          # Saved events CRUD routes
│       └── annotations.js     # Annotations CRUD routes
├── public/
│   ├── index.html             # Main HTML file
│   ├── css/
│   │   ├── main.css          # General styles
│   │   └── map.css           # Map-specific styles
│   └── js/
│       ├── main.js           # Application entry point
│       ├── map.js            # Leaflet map logic
│       ├── api.js            # API communication module
│       └── ui.js             # DOM manipulation module
├── .env                       # Environment variables (gitignored)
├── .env.example               # Environment template
├── .eslintrc.json            # ESLint configuration
├── .prettierrc               # Prettier configuration
├── .gitignore                # Git ignore rules
├── package.json              # Project dependencies
├── LICENSE                   # MIT License
└── README.md                 # This file
```

---

## 🧪 Development

### Code Quality

The project uses ESLint and Prettier for code quality:

```bash
# Run ESLint
npm run lint

# Format code with Prettier
npm run format
```

### Testing API Endpoints

Use tools like Thunder Client, Postman, or curl:

```bash
# Get all saved events
curl http://localhost:3000/api/events

# Create new annotation
curl -X POST http://localhost:3000/api/annotations \
  -H "Content-Type: application/json" \
  -d '{"coordinates":{"lat":35.5,"lng":-120.7},"annotation_text":"Test","category":"observation"}'
```

---

## 🚀 Deployment

### Deploy to Render/Railway/Heroku

1. **Prepare for deployment**
   - Ensure `.env` is in `.gitignore`
   - Verify all dependencies are in `package.json`
   - Test locally one final time

2. **Set environment variables on hosting platform**
   - Add `MONGODB_URI` with your Atlas connection string
   - Add `PORT` (usually auto-assigned by platform)

3. **Deploy**
   - Connect your GitHub repository
   - Platform will automatically detect Node.js and deploy
   - Verify deployment by visiting the live URL

4. **Verify**
   - Test all CRUD operations on live site
   - Check that earthquake data loads
   - Ensure database operations work correctly

---

## 📺 Video Demonstration

Watch the full demonstration: [Link to Video]

The video covers:
- Real-time earthquake visualization
- Saving events with custom notes
- Creating geographic annotations
- CRUD operations demonstration
- Technical architecture overview

---

## 🎓 Learning Outcomes

This project demonstrates:
- Full-stack web development with Node.js and Express
- MongoDB database design and native driver usage
- RESTful API architecture and implementation
- Client-side rendering without frontend frameworks
- ES6 module system and modern JavaScript
- Integration with external APIs (USGS)
- Interactive mapping with Leaflet.js
- Responsive web design principles
- Git version control and deployment workflows

---

## 🔒 Security Notes

- MongoDB credentials are stored in `.env` and never committed to Git
- Environment variables are used for all sensitive configuration
- Input validation on all API endpoints
- CORS properly configured for security

---

## 🤝 Contributing

This is an educational project, but suggestions are welcome:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/improvement`)
3. Commit changes (`git commit -m 'Add improvement'`)
4. Push to branch (`git push origin feature/improvement`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgments

- **USGS** for providing real-time earthquake data API
- **Leaflet.js** for the excellent mapping library
- **MongoDB** for flexible NoSQL database solution
- **Cal Poly** Web Development course for project requirements
- **Esri** for inspiration in geospatial visualization

---

## 📞 Contact

**[Your Name]**  
- GitHub: [@yourusername](https://github.com/yourusername)
- Email: your.email@example.com
- LinkedIn: [Your LinkedIn](https://linkedin.com/in/yourprofile)

---

## 🐛 Known Issues / Future Enhancements

### Known Issues
- None currently

### Future Enhancements
- Add volcanic eruption data from Smithsonian Global Volcanism Program
- Implement user authentication for personalized saved events
- Add advanced filtering by magnitude, date range, and region
- Export saved events and annotations as GeoJSON
- Add heatmap visualization for earthquake density
- Implement real-time updates using WebSockets
- Add data analytics dashboard showing trends over time

---

**Built with ❤️ for understanding Earth's dynamic geology**