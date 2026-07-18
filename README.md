# 🗺️ Smart Travel & Real-Time "Vibe" Itinerary Planner

[![Python Version](https://img.shields.io/badge/python-3.10%2B-blue.svg)](https://www.python.org)
[![Framework](https://img.shields.io/badge/framework-Flask-lightgrey.svg)](https://flask.palletsprojects.com/)
[![Database](https://img.shields.io/badge/database-SQLite%20%2F%20SQLAlchemy-green.svg)](https://www.sqlalchemy.org/)
[![NLP Engine](https://img.shields.io/badge/NLP-TextBlob-orange.svg)](https://textblob.readthedocs.io/)


---
A dynamic, data-driven travel itinerary generator built using Flask, SQLAlchemy, and TextBlob NLP. This application creates multi-day travel routes optimized by the Haversine formula, continuously checking live external telemetry APIs (Air Quality and Traffic congestion patterns) via a concurrent asynchronous worker pool to ensure high-quality, "Healthy" travel planning.

🚀 Key Engineering Features (For Viva/Project Presentation)
Concurrent Asynchronous Telemetry: Built with concurrent.futures.ThreadPoolExecutor to execute third-party API tracking (OpenWeather & TomTom) in parallel, reducing network latency bottlenecks by up to 80%.

Geospatial Precision Architecture: Replaced inaccurate flat Euclidean mapping with the Haversine Formula to ensure mathematically sound great-circle distances across the geoid surface of the Earth.

Sentiment-Driven Feedback Loop: Integrated natural language processing (NLP) using TextBlob to calculate an automated Vibe Score based on the lexical polarity of user feedback.

🛠️ Tech Stack & Architecture
Backend Framework: Flask (Python 3.10+)

Database / ORM: SQLite / Flask-SQLAlchemy 3.x

Security & Authentication: Flask-Login & Flask-Bcrypt (Blowfish password hashing architecture)

External APIs Utilized:

Geoapify API: Geospatial forward/reverse geocoding and Categorized POI (Point of Interest) extraction.

OpenWeatherMap API: Atmospheric telemetry and real-time Air Quality Index (AQI) data.

TomTom Traffic API: Live geometric bounding-box traffic collision and congestion mapping.

🏗️ Project Structure

```text

├── app.py                  # Core Routing System & Telemetry Controller
├── models.py               # Relational Database Models & Schema Architectures
├── smart_travel_final.db   # SQLite Relational Database
├── requirements.txt        # Third-party dependencies management manifest
├── static/                 
│   └── css/
│       └── style.css       # Custom UI Styles & Visual Layout Theme
└── templates/              # Jinja2 HTML5 Interface Framework
    ├── index.html          # Core parameter workspace
    ├── results.html        # Dynamic itinerary & algorithmic metrics rendering
    ├── login.html          # Secure user identification gate
    ├── register.html       # User identity provisioning dashboard
    └── profile.html        # Historical sentiment logs and user portfolios


```
⚡ Quick Start & Installation
1. Clone the Workspace Environment
https://github.com/Nishan1546/Travel-and-Tourism-Recommended-System-Using-Machine-Learning/tree/main
cd smart-travel-planner
2. Configure Virtual Environment & Packages
python -m venv venv
source venv/bin/activate  # On Windows use: venv\Scripts\activate
pip install -r requirements.txt
3. Establish Local API Secret Configurations
Open app.py and replace the placeholder credential tags with your valid keys:
GEO_API_KEY = "your_geoapify_key"
OWM_API_KEY = "your_openweathermap_key"
TOMTOM_KEY = "your_tomtom_key"
4. Initialize Database Models & Boot Engine
python app.py
Open your browser and navigate to [http://127.0.0.1:5002](http://127.0.0.1:5002).

📊 Performance Core Metrics MeasuredThe application profiles and computes three fundamental telemetry matrices displayed natively inside the execution UI panel:
1. System Compute Latency ($t_{exe}$): Measures end-to-end execution runtime for geo-queries and batch matrix allocations.
2. Category Structural Accuracy ($\%$): Reflects the algorithmic performance of the POI routing engine in providing diverse category allocations (Religious, Nature, and Historic spots) balanced across multi-day parameters.
3. Route Distribution Optimization Efficiency ($\%$): Measures path optimizing capability by comparing the Haversine distance tracking of the generated itinerary against a randomized path configuration.

### 3. Route Distribution Optimization Efficiency (%)
Measures the path-optimizing capability of our engine by comparing the total Haversine distance of our smart mixed itinerary against a completely randomized shuffle of the same destinations.

$$Efficiency = \left( \frac{\text{Distance}_{\text{Random}} - \text{Distance}_{\text{Smart}}}{\text{Distance}_{\text{Random}}} \right) \times 100\%$$

* **$\text{Distance}_{\text{Smart}}$**: The total kilometers calculated sequentially using our Haversine algorithm.
* **$\text{Distance}_{\text{Random}}$**: The baseline distance if a traveler visited the exact same spots in a randomized, un-optimized order.
