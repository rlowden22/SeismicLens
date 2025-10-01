# 🌋 Seismic Lens

**Seismic Lens** is a full-stack geospatial web application that visualizes real-time earthquake and volcanic activity worldwide. Built with modern web technologies, it provides an interactive platform for exploring Earth's dynamic geological processes.

![Seismic Lens Demo](link-to-screenshot.png) <!-- Add  screenshot here -->

## 🌍 Overview

Seismic Lens combines real-time earthquake monitoring with comprehensive volcanic event data, offering users an analytical view into tectonic activity across the globe. Through an interactive map interface, users can filter events, explore patterns, and understand the spatial relationships between seismic and volcanic phenomena.

## ✨ Features

- **Real-Time Earthquake Data**: Live earthquake feed from USGS with magnitude, depth, and location details
- **Volcanic Activity Tracking**: Historical eruption data from the Smithsonian Global Volcanism Program
- **Interactive Map Interface**: Powered by Leaflet.js with custom markers and pop-ups
- **Advanced Filtering**: Filter events by magnitude, date range, event type, and geographic region
- **Data Persistence**: MongoDB backend for storing user preferences and cached event data
- **Responsive Design**: Mobile-friendly interface for viewing on any device
- **RESTful API**: Clean API architecture for fetching and serving geological data

## 🛠️ Tech Stack

**Frontend:**
- HTML5, CSS3, JavaScript
- Leaflet.js for interactive mapping
- Responsive design with modern CSS

**Backend:**
- Node.js
- Express.js
- MongoDB with Mongoose ODM

**APIs:**
- USGS Earthquake API
- Smithsonian Global Volcanism Program

**Deployment:**
- Github Pages (or your deployment platform)

## 📋 Prerequisites

Before running this project, make sure you have:

- Node.js (v14 or higher)
- MongoDB (local installation or MongoDB Atlas account)
- npm or yarn package manager

## 🚀 Getting Started

### Installation

1. **Clone the repository**
```bash
   git clone https://github.com/yourusername/seismic-lens.git
   cd seismic-lens
