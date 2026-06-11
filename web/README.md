# AgriTech Digital Twin - Web Platform

This directory contains the web-based agriculture decision support platform, which consists of an **Angular 17+ frontend** and a **FastAPI Python backend**.

## Prerequisites & Required Accounts

Before setting up the project, ensure you have the following installed and configured:
- **Node.js**: v18 or higher (for the frontend application)
- **npm**: v9 or higher
- **Python**: 3.9 or higher (for the backend application)
- **PostgreSQL**: A running instance of PostgreSQL for the backend database
- **OpenRouter Account**: You need an API key from [OpenRouter](https://openrouter.ai/) for the AI agronomy assistant features (Grower GPT).

---

## 1. Backend Setup (`/backend`)

The backend is a cache-first, satellite-driven API integrated with AI-driven agronomic advice.

### Installation & Virtual Environment

1. Open a terminal and navigate to the backend directory:
   ```bash
   cd backend
   ```
2. Create a Python virtual environment:
   ```bash
   python -m venv venv
   ```
3. Activate the virtual environment:
   - **Windows:**
     ```bash
     venv\Scripts\activate
     ```
   - **macOS/Linux:**
     ```bash
     source venv/bin/activate
     ```
4. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```

### Configuration

1. Create a `.env` file in the `backend/` directory with the following variables:
   ```env
   DATABASE_URL=postgresql://user:password@localhost:5432/agritech
   OPENROUTER_API_KEY=your_openrouter_api_key_here
   ```
   *(Update the credentials in `DATABASE_URL` to match your local PostgreSQL setup).*

### Database Setup

1. Make sure your PostgreSQL server is running.
2. Create the `agritech` database if it doesn't exist.
3. Run the migrations/population scripts to set up the database schema and mock data (like the `satellite_cache` table):
   ```bash
   python apply_migration.py
   python populate_db.py
   ```

### Running the Server

1. Start the FastAPI development server:
   ```bash
   uvicorn app.main:app --reload
   ```
   *(Alternatively, run `python run.py` if configured).*
2. The backend API will be available at `http://localhost:8000`.

---

## 2. Frontend Setup (`/agritechplatform`)

The frontend is an Angular 17+ application serving as a Digital Twin dashboard using Open-Meteo for weather data and Leaflet for interactive maps.

### Installation

1. Open a new terminal and navigate to the frontend directory:
   ```bash
   cd agritechplatform
   ```
2. Install npm dependencies:
   ```bash
   npm install
   ```

### Configuration

1. Create a `.env` file in the `agritechplatform/` directory. You can use the provided `.env.example` as a template:
   ```env
   API_BASE_URL=http://localhost:8000
   OPENROUTER_API_KEY=your_openrouter_api_key_here
   AUCTION_PREVIEW_IMAGE_URL=https://res.cloudinary.com/your-cloud-name/image/upload/your-preview-image.png
   ```

### Running the Application

1. Ensure the backend is running before starting the frontend to enable full functionality.
2. Start the Angular development server:
   ```bash
   npm start
   ```
3. Open your browser and navigate to `http://localhost:4200`.

---

## System Overview & Data Flow

- **Frontend Dashboard**: Visualizes IoT sensor data, integrates with Leaflet maps, tracks water/irrigation metrics, and provides an AI agronomy chat interface.
- **Backend Services**: Provides a cache-first API for satellite data (fetching values like NDWI for water stress) and proxies requests to OpenRouter for the Grower GPT chat service.
- **Data Source**: Currently uses a local PostgreSQL database combined with external weather APIs (Open-Meteo) and OpenRouter (for LLM generation).