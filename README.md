# Purpose of Version: Decoupling data collection fron visualization

1. Separate Data Collection from Visualization
Data Collection Service (Python) → Database → Web Application (Frontend)

2. Time-Series Database Implementation
Postgres and SQlite → Optimized for sensor data storage

3. Data Processing Pipeline
Data Collection → Pre-processing → Aggregation → Storage → API Layer → Client Applications

    Each stage can be independently scaled:

   - Data Collection: Python script communicating with the interrogator
   - Pre-processing: Filtering, validation, unit conversion
   - Aggregation: Downsampling for different time resolutions
   - Storage: Time-series database for persistent storage
   - API Layer: REST or WebSocket interface for clients
   - Client Applications: Web dashboard, mobile app, etc.

4. Lightweight Solution (Python-based)
Python Data Service → Postgres + SQlite DBs → FastAPI → Plotly Dash/React Frontend



# BraggMETER Monitoring System File Structure

```mermaid
graph TD
    root[remote_monitor] --> backend
    root --> frontend
    root --> data

    backend --> data_collector.py
    backend --> requirements.txt
    backend --> sensor_data.db

    frontend --> public
    frontend --> src
    frontend --> package.json
    frontend --> postcss.config.js
    frontend --> tailwind.config.js
    frontend --> node_modules

    public --> index.html

    src --> components
    src --> App.jsx
    src --> index.js
    src --> index.css

    components --> Dashboard.jsx
    components --> SensorCards.jsx

    data --> sensor_data.db
    
    classDef backend fill:#d1e7dd,stroke:#198754,stroke-width:2px;
    classDef frontend fill:#f8d7da,stroke:#dc3545,stroke-width:2px;
    classDef data fill:#cff4fc,stroke:#0dcaf0,stroke-width:2px;
    classDef config fill:#fff3cd,stroke:#ffc107,stroke-width:2px;
    
    class backend,data_collector.py,requirements.txt,sensor_data.db backend;
    class frontend,public,src,package.json,postcss.config.js,tailwind.config.js,node_modules frontend;
    class data data;
    class components,Dashboard.jsx,SensorCards.jsx frontend;
    class index.html,App.jsx,index.js,index.css frontend;
```

