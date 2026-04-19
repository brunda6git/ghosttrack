# 🚌 GhostTrack
### Resilient Real-Time Public Transport Tracking System

> 🏆 Built for **Track B — ThinkRoot x Vortex Hackathon 2026**

[![Live Demo](https://img.shields.io/badge/🚀_Live_Demo-ghosttrack.onrender.com-00ffcc?style=for-the-badge)](https://ghosttrack.onrender.com)
[![GitHub](https://img.shields.io/badge/GitHub-Repository-181717?style=for-the-badge&logo=github)](https://github.com/brunda6git/ghosttrack)

---

## 👻 What is GhostTrack?

GhostTrack is a real-time public transport tracking system built for **low bandwidth and high latency environments**. When GPS packets drop and the network fails, most trackers freeze or crash. GhostTrack doesn't.

It switches to **Ghost Mode** — predicting the bus position using last known velocity — keeping the tracking experience completely smooth and uninterrupted. When connectivity returns, all lost data is automatically recovered and merged back.

GhostTrack tracks **3 buses simultaneously** on real Bengaluru city routes, predicts ETAs using live-trained Machine Learning, detects anomalies in real time, and never breaks — no matter how bad the network gets.

---

## 🎯 The Problem

Current tracking systems **completely fail** in poor network conditions:

- 📡 GPS packets drop in dense, crowded environments
- ⏱️ ETAs become inaccurate or disappear entirely  
- 🔌 Systems freeze instead of gracefully degrading
- 😤 Commuters miss buses with zero information

---

## ✅ The Solution

A **multi-layered resilience architecture** that never breaks:

| Network Condition | What GhostTrack Does |
|---|---|
| ✅ Normal | Live GPS tracking, 1s updates |
| 🟡 Slow | Adaptive 2s updates, confidence tracking |
| 🔴 Very Bad | Ghost Mode activated, buffer storing lost packets |
| 🔁 Recovery | Buffer replayed, real path restored automatically |

---

## ✨ Features

| Feature | Description |
|---|---|
| 👻 **Ghost Mode** | Predicts bus position when GPS drops — no freeze, no crash |
| 📦 **Store & Forward Buffer** | Lost packets stored and auto-replayed on recovery |
| 🧠 **ML-Based ETA** | Per-bus Linear Regression trained live every session |
| 🔍 **Anomaly Detection** | Isolation Forest flags abnormal speed or route deviation |
| 🚦 **Delay Detection** | Toast alerts + banner when bus slows below threshold |
| 🗺️ **Custom Route Setting** | Real road routes via OSRM + Nominatim geocoding |
| 📈 **Adaptive Updates** | 1s → 2s → 3s frequency based on network strength |
| 🚏 **Stop ETA Predictions** | Live arrival time to each upcoming named bus stop |
| 📊 **Live Charts** | Real-time speed, confidence, and packet loss graphs |
| 🌙 **Dark / Light Map** | Full UI adapts automatically on theme switch |
| ⏰ **Peak Hour Detection** | Live clock with automatic Peak/Off-Peak badge |
| 📍 **Route Progress Bar** | Visual progress with bus emoji tracking completion % |

---

## 🏗️ System Architecture

```
GPS Simulator → ML Engine → FastAPI WebSocket → Leaflet.js Frontend
```
gps_simulator.py     →    server.py (BusML)    →    app.js

3 Bengaluru routes      • Linear Regression        • Live map markers
Packet drop sim         • Isolation Forest         • Chart.js graphs
Waypoint interpolation  • Route health score       • Ghost mode UI
Realistic GPS jitter    • Stop ETA predictor       • Delay alerts

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Backend | Python, FastAPI, WebSocket, Uvicorn |
| Machine Learning | Scikit-learn, NumPy |
| Frontend | Leaflet.js, Chart.js, HTML/CSS/JS |
| Routing | OSRM, Nominatim |
| Hosting | Render |

---

## 🚀 Run Locally

```bash
# Clone the repo
git clone https://github.com/brunda6git/ghosttrack.git
cd ghosttrack

# Install dependencies
pip install -r requirements.txt

# Start the server
uvicorn server:app --host 127.0.0.1 --port 8000 --reload
```

Open `http://localhost:8000` in your browser.

---

## 📁 File Structure
```bash
ghosttrack/
├── server.py              # FastAPI backend + WebSocket + per-bus ML
├── gps_simulator.py       # GPS simulation with packet drop
├── anomaly_detector.py    # Isolation Forest anomaly detection
├── crowd_predictor.py     # Weighted position prediction
├── route_scorer.py        # Rolling route health score
├── ml_predictor.py        # Linear Regression ETA module
├── index.html             # Main tracking UI
├── app.js                 # Frontend logic + WebSocket + charts
├── style.css              # All styling + dark/light mode
├── docs.html              # Project documentation page
└── requirements.txt       # Python dependencies
```

---

## 📊 Judging Criteria

| Criterion | Weight | How We Address It |
|---|---|---|
| 🛡️ System Resilience | 30% | Ghost mode, store-and-forward buffer, adaptive updates |
| 🎯 ETA Accuracy | 25% | Per-bus Linear Regression trained live |
| 🏗️ Technical Architecture | 20% | FastAPI WebSocket, 5 ML modules, 3 simultaneous buses |
| 🎨 User Experience | 10% | Live map, charts, alerts, dark/light mode, stop ETAs |
| 📄 Documentation | 15% | This README + full docs page at `/docs.html` |

---

## 👩‍💻 Team

| Name | Role |
|---|---|
| **Lasya K** | Frontend Engineer & ML |
| **Brunda Gunaga** | Backend Engineer & ML |

---

<div align="center">
  Built for <strong>Track B — Resilient Public Transport Tracking</strong>
  <br/>
  <a href="https://ghosttrack.onrender.com">🚀 ghosttrack.onrender.com</a>
</div>
