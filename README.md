# AI-Powered Mind Map and Concept Visualization Generator

> **Master of Computer Applications (MCA) Practical Project**  
> **Tech Stack:** MERN Stack (MongoDB, Express.js, React.js, Node.js) + Mermaid.js + OpenAI API

---

## 📌 Executive Summary

The **AI-Powered Mind Map and Concept Visualization Generator** is a full-stack web application designed for academic research, conceptual decomposition, and hierarchical knowledge visualization. 

The application accepts any academic topic, interfaces securely with the OpenAI API through an Express.js backend, and dynamically generates:
- **1 Main Overarching Concept**
- **4 to 6 Structured Subtopics** with active relational edge labels
- **2 to 4 Detailed Supporting Points** per subtopic
- **Interactive Mermaid.js Hierarchical Graph** with styled nodes and labeled branches
- **Concept Hierarchy View** with collapsible accordion nodes and one-click Markdown outline export
- **Full MongoDB Persistence** (Save, Retrieve, Search, and Delete)
- **Built-in Zero-Config Demo Mode** featuring pre-built academic models for **Machine Learning** and **Photosynthesis**, plus an algorithmic academic generator for offline execution.

---

## 🏗️ System Architecture

The application adopts a decoupled 3-tier client-server architecture:

```
[ React 19 Frontend (Vite) ]  <--(HTTP/REST Proxy)-->  [ Node.js + Express.js API ]
        |                                                        |
  • Responsive Dashboard                                   • Input Validation & Sanitize
  • Mermaid.js 11 SVG Canvas                               • OpenAI API Key Protection
  • Pan & Zoom Controls                                    • Mermaid Syntax Generator
  • Concept Hierarchy View                                 • Demo Mode Engine
  • Dark / Light Theme Engine                                    |
                                                      +----------+----------+
                                                      |                     |
                                               [ MongoDB Server ]     [ OpenAI API ]
                                                (Port 27017)           (gpt-4o-mini)
                                                Mongoose ODM
```

---

## 🚀 Key Features

| Feature | Description |
| :--- | :--- |
| **Interactive Mermaid.js Visualizer** | Renders hierarchical graphs (`graph LR`) with styled class nodes (`rootNode`, `subNode`, `leafNode`) and labeled branch relationships. |
| **Canvas Pan & Zoom Engine** | Smooth mouse drag panning, mouse wheel zooming, reset view button, and fullscreen modal mode. |
| **Vector SVG Download** | One-click lossless `.svg` export with sanitized filenames for reports and presentations. |
| **Concept Hierarchy Tree** | Accordion-based tree inspector with active relational pills, deep detail explanations, search filtering, and Markdown outline clipboard copy. |
| **Zero-Config Demo Mode** | Comprehensive pre-built datasets for **Machine Learning** and **Photosynthesis**, ensuring 100% functionality during offline viva demonstrations. |
| **MongoDB Persistence** | Full Mongoose CRUD operations allowing users to save, view, search, and delete mind maps from `mindmap_db`. |
| **Modern Dashboard** | Collapsible sidebar, breadcrumb navigation, live system health badges (MongoDB & OpenAI status), and animated loading progress indicators. |
| **Light & Dark Mode** | Instant theme toggle with CSS variable adaptation and persistent `localStorage` synchronization. |
| **Enterprise Security** | OpenAI API keys remain strictly in backend environment variables (`server/.env`). |

---

## 📂 Project Structure

```
d:\GenAI\
├── client/                     # Frontend Application (React 19 + Vite)
│   ├── public/                 # Static assets & favicon
│   ├── src/
│   │   ├── assets/             # Images & visual assets
│   │   ├── components/         # Modular React UI components
│   │   │   ├── Sidebar.jsx     # Navigation, logo, system status & theme toggle
│   │   │   ├── Header.jsx      # Top bar with status pills & mobile toggle
│   │   │   ├── TopicInput.jsx  # Search bar, Demo/AI switch & sample pills
│   │   │   ├── MermaidCanvas.jsx# Mermaid SVG renderer, pan/zoom & SVG download
│   │   │   ├── ConceptHierarchy.jsx # Collapsible tree hierarchy & outline copy
│   │   │   ├── SavedMindMaps.jsx    # MongoDB saved maps grid, search & delete
│   │   │   ├── VivaDocs.jsx    # MCA practical documentation & Viva Voce Q&A
│   │   │   ├── Toast.jsx       # Floating notification alert system
│   │   │   └── LoadingSkeleton.jsx  # Animated 4-step generation progress
│   │   ├── services/
│   │   │   └── api.js          # REST API client communication layer
│   │   ├── App.jsx             # Core application controller & state store
│   │   ├── index.css           # Custom CSS design system (Light/Dark themes)
│   │   └── main.jsx            # Application entrypoint
│   ├── index.html              # HTML5 root template
│   ├── package.json            # Client dependencies & scripts
│   └── vite.config.js          # Vite config with /api reverse proxy to :5000
│
├── server/                     # Backend Application (Node.js + Express)
│   ├── config/
│   │   └── db.js               # Mongoose MongoDB connection & event handlers
│   ├── controllers/
│   │   └── mindmapController.js# Generate, save, get, delete, & status controllers
│   ├── data/
│   │   └── demoData.js         # Pre-built Machine Learning & Photosynthesis datasets
│   ├── models/
│   │   └── MindMap.js          # Mongoose schema with subtopics & supporting points
│   ├── routes/
│   │   └── mindmapRoutes.js    # Express route mappings
│   ├── services/
│   │   ├── aiService.js        # OpenAI API client, JSON parser & Demo resolver
│   │   └── mermaidGenerator.js # Mermaid DSL compiler with labeled branches
│   ├── .env                    # Active backend environment variables (git-ignored)
│   ├── .env.example            # Environment variables configuration template
│   ├── package.json            # Server dependencies (Express, Mongoose, OpenAI)
│   └── server.js               # Main Express entrypoint & middleware
│
├── .gitignore                  # Git exclusion rules
├── package.json                # Root convenience scripts
└── README.md                   # Comprehensive MCA documentation
```

---

## ⚙️ Installation & Setup Guide

### Prerequisites
1. **Node.js** (v18.x or higher, v24.x verified)
2. **npm** (v9.x or higher)
3. **MongoDB Server** (Running locally on default port `27017` or via MongoDB Atlas URI)

---

### Step 1: Install Server Dependencies
```powershell
cd d:\GenAI\server
npm.cmd install
```

### Step 2: Configure Server Environment Variables
Verify or edit `server/.env`:
```env
PORT=5000
NODE_ENV=development
MONGODB_URI=mongodb://127.0.0.1:27017/mindmap_db

# Optional: Add your OpenAI API key for live generation.
# If omitted or left empty, the application automatically runs in Demo Mode!
OPENAI_API_KEY=
OPENAI_MODEL=gpt-4o-mini
```

### Step 3: Install Client Dependencies
```powershell
cd d:\GenAI\client
npm.cmd install
```

---

## 🏃 Running the Application

### Option A: Run Server and Client Simultaneously
Open two separate terminal windows:

**Terminal 1 (Backend Server):**
```powershell
cd d:\GenAI\server
npm.cmd run dev
# Server will run on: http://localhost:5000
```

**Terminal 2 (Frontend Client):**
```powershell
cd d:\GenAI\client
npm.cmd run dev
# Frontend will run on: http://localhost:5173
```

Open your browser and visit: **`http://localhost:5173`**

---

## ⚡ Zero-Config Demo Mode (Offline Demonstration)

This application is engineered specifically so that **no API key or internet connection to OpenAI is required** for viva evaluation:

1. **Pre-built Academic Topics**:
   - **Machine Learning**: Generates 5 academic subtopics (*Supervised Learning*, *Unsupervised Learning*, *Reinforcement Learning*, *Deep Learning & Neural Architectures*, *Model Evaluation & MLOps*) with 3 supporting points each and labeled relational branches.
   - **Photosynthesis**: Generates 5 biochemical subtopics (*Chloroplast Ultrastructure*, *Light-Dependent Reactions*, *Chemiosmotic Photophosphorylation*, *Calvin-Benson Cycle*, *Physiological Adaptations*) with 3 supporting points each.
2. **Arbitrary Topic Fallback**:
   - Entering any other topic in Demo Mode uses the algorithmic academic generator to produce a 5-tier concept decomposition (*Theoretical Foundations*, *Core Architecture*, *Methodologies*, *Trade-offs*, *Modern Applications*), ensuring examiners can test any subject without runtime failure.

---

## 📡 REST API Reference

Base URL: `http://localhost:5000/api/mindmaps`

| Method | Endpoint | Description | Request Body |
| :--- | :--- | :--- | :--- |
| `GET` | `/status` | Server health, MongoDB status, & OpenAI readiness | None |
| `POST` | `/generate` | Generate concept hierarchy & Mermaid diagram | `{ "topic": "Machine Learning", "forceDemo": true }` |
| `POST` | `/` | Save generated mind map to MongoDB | Mind map JSON payload |
| `GET` | `/` | Retrieve all saved mind maps (supports `?search=`) | None |
| `GET` | `/:id` | Fetch specific mind map by MongoDB ObjectID | None |
| `DELETE`| `/:id` | Remove mind map from MongoDB | None |

---

## 🎓 Practical Viva Voce Questions & Answers

### Q1: What is the primary role of Mongoose in this project?
**Answer:** Mongoose acts as the Object Data Modeling (ODM) library for MongoDB. It enforces strict schemas for the hierarchical mind map data, validates required fields (ensuring a minimum of 3 subtopics), handles timestamps, and enables fast indexing for keyword searches on topics and tags.

### Q2: How does the application prevent OpenAI API key leakage?
**Answer:** The React frontend never stores or references the OpenAI API key. All AI completions are delegated through the Express.js backend (`/api/mindmaps/generate`). The API key resides solely in the server's `.env` file, which is excluded from version control via `.gitignore`.

### Q3: How does the Mermaid rendering lifecycle prevent DOM conflicts in React?
**Answer:** In `MermaidCanvas.jsx`, Mermaid is invoked asynchronously inside a `useEffect` hook with `mermaid.initialize()` and `mermaid.render(uniqueSvgId, mermaidCode)`. The generated SVG markup is received as a sanitized string and injected into a zoomable/pannable container, avoiding race conditions and direct DOM mutations that could disrupt React’s virtual DOM reconciliation.

### Q4: How is vector SVG export implemented?
**Answer:** The SVG XML string rendered by Mermaid is converted into an in-memory `Blob` of type `image/svg+xml`. An ephemeral Object URL is generated via `URL.createObjectURL()`, and a programmatic anchor click initiates a direct download with a formatted filename (e.g., `machine-learning-mindmap.svg`).

### Q5: How is system resilience maintained when MongoDB is temporarily unavailable?
**Answer:** The MongoDB connection handler (`server/config/db.js`) traps initial connection errors without terminating the Node.js process. When the database is offline, mind map generation and SVG download still function uninterrupted. If the user attempts to save, the backend returns a clear `503 Service Unavailable` status with a descriptive notification rather than crashing.

---

## 📜 License
Developed for academic MCA practical demonstration. Released under the MIT License.
