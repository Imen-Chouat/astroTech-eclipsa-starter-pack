# 🚀 AstroTech — Hackathon Eclipsa Official Resource Pack

Welcome, **Hackathon Eclipsa Flight Crews**!  
So zero teams get stuck setting up databases, fighting paywalls, or hunting for clean space datasets on Day 1, AstroTech has prepared this ready-to-clone resource repository containing **curated datasets, fail-safe JSON snapshots, and free API documentation** for all three tracks.

*(No pre-built code templates or demos are included—your crew has 100% creative freedom to design and architect your solution from scratch!)*

---

## 📁 Repository Structure

```text
astroTech-eclipsa-starter-pack/
├── README.md                                  # API endpoints, curl tests & dataset guide
├── .gitignore                                 # Standard Python / Node / IDE ignores
├── setup_git_repo.sh                          # Linux / macOS one-click Git init script
├── setup_git_repo.bat                         # Windows one-click Git init script
│
├── track1-astroGaze/                          # TRACK 1: Night-Sky Observation Companion
│   ├── astroGaze_messier_catalog.json         # 30 deep-sky objects (RA, Dec, magnitude, constellation)
│   └── bortle_scale_reference.json            # Bortle Dark-Sky Scale (Classes 1-9) & Star-Count Test data
│
├── track2-orbital-earth-watch/                # TRACK 2: Space-to-Ground Disaster Radar
│   ├── orbital_eonet_backup.json              # Offline snapshot of North Africa/Med & global hazards
│   └── regional_bboxes.json                   # Pre-built bounding boxes (Algeria, Med, Europe, Global) + cities
│
└── track3-bioAstra/                           # TRACK 3: Autonomous Deep-Space Crew Health
    ├── bioAstra_crew_vitals.csv               # 14 days (Sol 01-14) of synthetic telemetry for 3 astronauts
    ├── bioAstra_crew_vitals.json              # JSON version of the 14-day crew telemetry + baselines
    └── bioAstra_donki_backup.json             # Offline NASA DONKI X-class solar flare snapshot
```

---

## 🛰️ Free, Zero-Friction APIs & Quick `curl` Tests

### 1. NASA EONET API v3 — Live Orbital Disaster Events *(Track 2 — No API Key)*
Fetches real-time wildfires, severe storms, dust/haze, and volcanic events worldwide:
```bash
curl "https://eonet.gsfc.nasa.gov/api/v3/events?status=open&limit=10"
```
* **Filter by category (`wildfires`, `severeStorms`, `dustHaze`, `volcanoes`):**
  ```bash
  curl "https://eonet.gsfc.nasa.gov/api/v3/events?category=wildfires&status=open"
  ```
* **Filter by North Africa & Mediterranean bounding box (`minLon,maxLat,maxLon,minLat`):**
  ```bash
  curl "https://eonet.gsfc.nasa.gov/api/v3/events?bbox=-10,45,36,18&status=open"
  ```

### 2. NASA GIBS / Worldview WMTS Tiles — Daily Satellite Imagery *(Track 2 Bonus — No API Key)*
Daily true-color VIIRS satellite imagery tiles (Web Mercator `EPSG:3857`) ready for any map library:
```text
https://gibs.earthdata.nasa.gov/wmts/epsg3857/best/VIIRS_SNPP_CorrectedReflectance_TrueColor/default/YYYY-MM-DD/GoogleMapsCompatible_Level9/{z}/{y}/{x}.jpg
```

### 3. NASA DONKI API — Live Solar Flares & Radiation Alerts *(Track 3 Bonus — No API Key)*
Fetches live Solar Flare (`FLR`) or Solar Energetic Particle (`SEP`) telemetry from NASA CCMC:
```bash
curl "https://ccmc.gsfc.nasa.gov/DONKI-API/get/FLR?startDate=2026-11-01&endDate=2026-11-24"
```
* **Solar Energetic Particles (`SEP`):**
  ```bash
  curl "https://ccmc.gsfc.nasa.gov/DONKI-API/get/SEP?startDate=2026-11-01&endDate=2026-11-24"
  ```
*(Offline backup included in `track3-bioAstra/bioAstra_donki_backup.json`)*

### 4. OpenWeatherMap API — Hourly Cloud Cover, Humidity & Wind *(Track 1 — Free Tier)*
Sign up at [openweathermap.org](https://openweathermap.org/api) for a free API key to fetch hourly atmospheric conditions:
```bash
curl "https://api.openweathermap.org/data/2.5/forecast?lat=36.7538&lon=3.0588&units=metric&appid=YOUR_FREE_KEY"
```

### 5. OpenStreetMap + Leaflet.js — Keyless Interactive Maps *(Tracks 1 & 2)*
Completely free interactive mapping with zero API key or billing account required (`https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png`).

---

**Good luck, Crews — all systems are GO for liftoff!** 🚀
