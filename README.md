# SIGIZI BALITA (Toddler Nutrition Information & Analysis System)

**Live Application:** [https://sigizi-balita-unand.vercel.app/](https://sigizi-balita-unand.vercel.app/)
SIGIZI BALITA is a comprehensive digital platform designed to help Posyandu Cadres and Puskesmas Midwives monitor, record, and analyze the growth and nutritional status of toddlers in real-time. This platform integrates Artificial Intelligence (Machine Learning) using a Random Forest Classification model to predict nutritional status and provide accurate early intervention recommendations.

---

## Key Features

### 1. Posyandu Cadre Work Portal
*   **Registration & Examination**: Recording of toddlers' physical data including Weight, Height, Head Circumference, Mid-Upper Arm Circumference, and Height Measurement Method.
*   **Instant Analysis Results**: Automatic calculation of Z-Scores (Weight/Age, Height/Age, Weight/Height) based on the anthropometry standards of the Indonesian Ministry of Health.
*   **AI Recommendations**: Prediction of nutritional status classification based on Machine Learning along with direct actionable recommendations.
*   **Examination History**: Structured storage of all monthly toddler examination logs.

### 2. Puskesmas Midwife Dashboard Portal
*   **Regional Monitoring**: Aggregate monitoring of the distribution of toddlers' nutritional status across all Posyandu in the Puskesmas working area.
*   **Smart Data Filtering**: Searching, filtering, and reviewing specific nutritional history per toddler or per working area.
*   **Cadre Data**: Management and coordination of active cadre data assigned to each respective Posyandu.
*   **PDF Reports**: Exporting toddler nutritional history periodically into print-ready PDF documents.

---

## Architecture & Technology

*   **Frontend**: 
    *   React 18 with TypeScript
    *   Vite (Build Tooling & Bundler)
    *   Tailwind CSS (Clean, minimalist, responsive interface design)
    *   Lucide React (SVG icon library)
    *   Recharts (Statistical charts visualization for toddler growth)
*   **Backend**: 
    *   Python with Flask Framework (Nutrition Analysis API)
    *   Scikit-Learn (Random Forest Classification Model)
    *   Pandas & NumPy (Data preprocessing)
*   **Database & Authentication**: 
    *   Firebase Authentication (Secure access separation for Cadres and Midwives)
    *   Firebase Firestore (Structured document storage and real-time synchronization)

---

## Project Folder Structure

```
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
```

---

## Local Installation & Operation Guide

### 1. Backend Setup (Flask API)
*   Ensure Python 3.11+ is installed on your computer.
*   Open a terminal in the project root directory and run the following commands:
    ```bash
    # Create a virtual environment
    python -m venv venv
    
    # Activate the virtual environment
    # On Windows:
    venv\Scripts\activate
    # On macOS/Linux:
    source venv/bin/activate
    
    # Install dependencies
    pip install -r requirements.txt
    
    # Run the backend server
    python app.py
    ```
    The backend API will run on port `5000` (or the environment port `PORT` if declared).

### 2. Frontend Setup (React + Vite)
*   Ensure NodeJS 18+ is installed.
*   Open a new terminal in the project root directory and run the following commands:
    ```bash
    # Install frontend dependencies
    npm install
    
    # Run the local development server
    npm run dev
    ```
    The local frontend will be hosted by default on port `3000` (or `5173`).

---

## Environment Variables Configuration (`.env`)

To fully connect the services in production, create a `.env` file in the frontend root level with the following key configurations:

```env
VITE_API_URL=https://<your-backend-domain>.onrender.com

VITE_FIREBASE_API_KEY=your_firebase_api_key
VITE_FIREBASE_AUTH_DOMAIN=your_project.firebaseapp.com
VITE_FIREBASE_PROJECT_ID=your_project_id
VITE_FIREBASE_STORAGE_BUCKET=your_project.appspot.com
VITE_FIREBASE_MESSAGING_SENDER_ID=your_sender_id
VITE_FIREBASE_APP_ID=your_app_id
```

---

## Deployment Guide

### 1. Deploy Backend API on Render.com
*   Create an account on [Render.com](https://render.com).
*   Select **New Web Service** and follow the guide to link your Git repository.
*   Render will automatically track the `render.yaml` file in the project root to process build and start configurations:
    *   **Build Command**: `pip install -r requirements.txt`
    *   **Start Command**: `gunicorn app:app`
    *   **Runtime**: Python 3.11.0

### 2. Deploy Frontend on Vercel.com
*   Log in to [Vercel.com](https://vercel.com) and import the same repository.
*   Vercel will automatically detect the Vite framework.
*   Enter all environment variables (`VITE_API_URL` and Firebase configuration) in the **Environment Variables** menu before deploying.
*   SPA routing will run perfectly automatically thanks to the provided `vercel.json` configuration.
