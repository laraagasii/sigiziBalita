# SIGIZI BALITA (Toddler Nutrition Information & Analysis System) 

**Live Application:** [sigizi-balita-unand.vercel.app](https://sigizi-balita-unand.vercel.app/)

**SIGIZI BALITA** is a comprehensive digital platform designed to help Posyandu Cadres and Puskesmas Midwives monitor, record, and analyze the growth and nutritional status of toddlers in real-time. This platform integrates Artificial Intelligence (Machine Learning) using a Random Forest Classification model to predict nutritional status and provide accurate early intervention recommendations.

> **Team / Contributors:** This project was collaboratively built and developed by **Lara**, **Fayi**, and **Sherly**.

##  Key Features

**1. Posyandu Cadre Work Portal**
*   **Registration & Examination:** Recording of toddlers' physical data including Weight, Height, Head Circumference, Mid-Upper Arm Circumference, and Height Measurement Method.
*   **Instant Analysis Results:** Automatic calculation of Z-Scores (Weight/Age, Height/Age, Weight/Height) based on the anthropometry standards of the Indonesian Ministry of Health.
*   **AI Recommendations:** Prediction of nutritional status classification based on Machine Learning along with direct actionable recommendations.
*   **Examination History:** Structured storage of all monthly toddler examination logs.

**2. Puskesmas Midwife Dashboard Portal**
*   **Regional Monitoring:** Aggregate monitoring of the distribution of toddlers' nutritional status across all Posyandu in the Puskesmas working area.
*   **Smart Data Filtering:** Searching, filtering, and reviewing specific nutritional history per toddler or per working area.
*   **Cadre Data:** Management and coordination of active cadre data assigned to each respective Posyandu.
*   **PDF Reports:** Exporting toddler nutritional history periodically into print-ready PDF documents.

##  Architecture & Technology

**Frontend:**
*   React 18 with TypeScript
*   Vite (Build Tooling & Bundler)
*   Tailwind CSS (Clean, minimalist, responsive interface design)
*   Lucide React (SVG icon library)
*   Recharts (Statistical charts visualization for toddler growth)

**Backend:**
*   Python with Flask Framework (Nutrition Analysis API)
*   Scikit-Learn (Random Forest Classification Model)
*   Pandas & NumPy (Data preprocessing)

**Database & Authentication:**
*   Firebase Authentication (Secure access separation for Cadres and Midwives)
*   Firebase Firestore (Structured document storage and real-time synchronization)

##  Project Folder Structure

```text
SIGIZI BALITA/
├── app.py                      # Flask API Server (Machine Learning)
├── model_rf_gizi.pkl           # Trained Random Forest Model file
├── requirements.txt            # Python Backend Dependencies
├── render.yaml                 # Blueprint file for Render.com deployment
├── vercel.json                 # SPA routing configuration for Vercel
├── package.json                # NodeJS Frontend Dependencies
├── vite.config.ts              # Vite bundling & performance optimization configuration
├── src/
│   ├── config/
│   │   ├── firebase.ts         # Firebase SDK Initialization
│   │   └── AuthContext.tsx     # Session management / user roles (Cadre/Midwife)
│   ├── services/
│   │   ├── api.ts              # Frontend HTTP Connection to ML API
│   │   ├── db.ts               # Firestore DB interaction interface
│   │   └── gizi.ts             # Local anthropometry logic (fall-back)
│   ├── pages/                  # Application pages (Cadre & Midwife)
│   ├── components/             # Reusable UI components
│   └── layouts/                # Navigation layout wrapper
└── public/
