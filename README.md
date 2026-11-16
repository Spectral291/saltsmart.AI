# 🌴 SaltSmart AI — Smart Farming for the Desert (A-001)

> **Hackathon Track:** A-001 Smart Farming for the Desert  
> **Target Region:** Al Ain, Abu Dhabi Emirate, UAE (`24.2075° N, 55.7447° E`)  
> **Target Farming System:** 10-Hectare Commercial Date Palm (*Phoenix dactylifera*) Grove (~1,000 Palms)  
> **Primary Water Source:** Brackish Groundwater Wells ($EC_w = 3.5\text{ dS/m} \approx 2,240\text{ ppm TDS}$)

---

## 🎯 The Hidden Problem Inside the Problem

In desert agriculture, groundwater is inherently brackish. When well-meaning growers or simplistic AI tools attempt to save water by arbitrarily cutting back irrigation (e.g., a naïve 30% reduction), salt builds up in the crop root zone without being leached out. 

This is the **"Water-Saving Trap"**:
- **Farmer's Habit (10 mm/day flat schedule):** Consumes 900,000 m³ of non-renewable groundwater over 90 days. Soil $EC_e$ is flushed to 1.8 dS/m, but water waste is catastrophic.
- **Naïve Cut (Cut 30% to "save water"):** Applies 630,000 m³. Without adequate leaching fraction, salts from the 3.5 dS/m well water accumulate in the root zone, driving soil $EC_e$ up to **5.2 dS/m** (well past the date palm limit of 4.0 dS/m). Yield collapse begins!
- **SaltSmart AI:** Calculates the exact dynamic **FAO-29 Leaching Requirement ($LR$)** and daily **Hargreaves $ET_0$**. Applies 462,000 m³, holds root-zone soil $EC_e$ safely at **3.9 dS/m**, and saves **438 Million Liters (48.6%)** with **0% crop loss**!

---

## 📊 Ground Truth & Research Parameters

All parameters are derived from UAE agricultural field studies and FAO guidelines:

| Parameter | Value & Source | Context for Hackathon Judges |
| :--- | :--- | :--- |
| **Location** | Al Ain, Abu Dhabi Emirate (`24.2075° N, 55.7447° E`) | Oasis farming region dependent on deep saline aquifers |
| **Target Farm** | 10 Hectares (~1,000 Date Palms) | Typical medium-sized family date palm grove in Al Ain |
| **Water Source** | Brackish Groundwater ($EC_w = 3.5\text{ dS/m}$) | Representative inland aquifer salinity (~2,240 ppm TDS) |
| **Soil Type** | Hyperthermic Typic Torripsamments (Coarse Sand) | Fast-draining (>50 mm/hr), minimal natural water retention |
| **Crop Tolerance** | Date Palm threshold ($EC_e = 4.0\text{ dS/m}$) | FAO Irrigation & Drainage Paper 29 (100% potential yield) |
| **Weather Dataset** | 91-Day Real ERA5 Satellite Reanalysis (Jan 1 – Mar 31) | Historical daily maximum/minimum temperatures for Al Ain |

---

## 🚀 The Desert Rules Fit

1. **Desert Rule #1 (Water Optimization):**
   Saves **48.6% water** (**438 Million Liters** over 90 days on a 100 ha oasis cluster; **43.5 Million Liters** on a single 10 ha family farm) compared to calendar habits.
2. **Desert Rule #2 (Low-Bandwidth Delivery):**
   Requires no apps for field workers. Automatically formats a plain-text **WhatsApp alert** sent at 05:00 AM with pump runtime and target millimeters.
3. **Desert Rule #3 (Offline Resiliency & Zero Hardware Cost):**
   Requires zero in-field sensors beyond a standard $15 handheld salinity pen. Computes extraterrestrial solar radiation ($R_a$) and $ET_0$ using an offline mathematical implementation of the FAO-56 Hargreaves-Samani algorithm.

---

## 🛠️ Tech Stack & Architecture

- **Backend:** Python 3, Flask
- **Agronomic Engines:** 
  - FAO-56 Hargreaves-Samani Reference Evapotranspiration Algorithm
  - FAO-29 Ayers & Westcot Leaching Requirement Model
  - Dynamic Soil-Salinity ($EC_e$) Root-Zone Mass Balance
- **Climate Data:** Open-Meteo ERA5 Reanalysis Weather Archive (Al Ain: Latitude 24.2075° N, Longitude 55.7447° E) with local offline cache fallback
- **Frontend UI:** Tailwind CSS, Chart.js, HTML5 Responsive Canvas, LocalStorage Caching

---

## ⚡ Quickstart

### 1. Clone & Enter Directory
```bash
git clone https://github.com/your-username/saltsmart-ai-desert-farming.git
cd saltsmart-ai-desert-farming
```

### 2. Install Dependencies
```bash
pip install -r requirements.txt
```

### 3. Run the Web Application
```bash
python app.py
```

Open your browser at **`http://localhost:5000`** (or `http://127.0.0.1:5000`).

---

## 📁 Repository Structure

```
saltsmart-ai-desert-farming/
│── templates/
│   └── index.html          # Interactive dashboard with Chart.js & WhatsApp preview
│── app.py                  # Flask backend, Hargreaves engine & simulation API
│── weather_cache.json      # 91-day real ERA5 satellite climate dataset for Al Ain
│── requirements.txt        # Minimal Python dependencies
└── README.md               # Complete project documentation & pitch guide
```

---

## 📹 60-Second Video Demo Script & Storyboard

### [0:00 - 0:12] THE HOOK & ANGLE
- **Visual:** Open SaltSmart dashboard on the "The Water-Saving Trap" banner.
- **Voiceover:** *"Farming in the desert comes with a hidden trap. When farmers cut water to save resources, salt from brackish groundwater builds up in the soil, poisoning crops. Most teams will tell farmers to water less. We tell them how to water smart."*

### [0:12 - 0:32] THE SOLUTION & LIVE DEMO
- **Visual:** Drag Salinity Slider to 3.5 dS/m. Hover over the Leaching Fraction bar and point to the WhatsApp Alert box.
- **Voiceover:** *"Meet SaltSmart AI. Designed for small-scale growers in Al Ain, UAE. By combining local well salinity readings with real satellite weather data, our engine calculates the FAO-29 leaching fraction. It delivers a plain WhatsApp message every morning telling the farmer the exact millimeters needed to feed the plant and flush the salt."*

### [0:32 - 0:48] THE PROOF & DATA
- **Visual:** Point to Chart.js graph showing Red Line (Cut 30%) climbing to 5.2 dS/m and Green Line (SaltSmart) staying safe at 3.9 dS/m.
- **Voiceover:** *"Look at the 90-day real weather simulation. A naive 30% water cut poisons the soil above the date palm limit of 4 dS/m. SaltSmart holds soil salinity safely at 3.9 dS/m while using 48% less water than traditional habits."*

### [0:48 - 1:00] THE DESERT RULES FIT
- **Visual:** Toggle between Salem's Farm and Oasis Cluster view. Show GitHub repository structure.
- **Voiceover:** *"It works offline, requires zero expensive hardware beyond a $15 salinity pen, and saves 438 million liters of water per season. That’s SaltSmart AI."*
