# Dynamic Honeypot Orchestrator with Web Dashboard 🍯

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) <!-- Choose your license -->
[![Python Version](https://img.shields.io/badge/python-3.x-blue.svg)]() <!-- Specify Python version -->
[![Node.js Version](https://img.shields.io/badge/node-18.x%2B-green.svg)]() <!-- Specify Node.js version -->
<!-- Add other badges as needed: build status, code coverage, etc. -->

A comprehensive web application designed to streamline the deployment, management, monitoring, and analysis of network honeypots using Docker, featuring a real-time dashboard, attack simulation, and AI-powered threat insights.

**Authors:**
*   Devrajsinh Shripalsinh Jhala
*   Suryadevsinh Harishchandrasinh Zala
*   Udit Chaudhary
*   Gladwin Kurian
  
*(Birla Institute of Technology and Sciences, Pilani)*

---

## Overview

Managing network honeypots often involves complex setups, manual log aggregation, and fragmented tools. This project, the **Dynamic Honeypot Orchestrator**, tackles these challenges by providing a unified, intuitive web-based platform.

It simplifies the entire honeypot lifecycle:
*   **Easy Deployment:** Deploy common honeypot types (SSH, Web) as Docker containers via a simple UI.
*   **Centralized Monitoring:** Automatically aggregate attack logs from all honeypots.
*   **Real-time Visibility:** Monitor attacks as they happen through an interactive dashboard.
*   **Data Visualization:** Understand attack patterns with charts and summaries.
*   **Attack Simulation:** Test your honeypot setups and security posture with built-in attack generators.
*   **AI-Powered Insights:** Leverage Google's Gemini AI for automated threat analysis and security recommendations.

This platform aims to lower the barrier to entry for effective honeypot utilization, empowering cybersecurity professionals, researchers, and enthusiasts.

---

## ✨ Key Features

*   **Web-Based Management:** Intuitive interface to Create, View, and Delete honeypot instances.
*   **Simplified Docker Deployment:** Abstract away Docker complexities for deploying standard honeypots (e.g., `cowrie/cowrie`, `vulnerables/web-dvwa`). Handles state recovery on restart.
*   **Automated Log Aggregation:** Collects, parses, and deduplicates attack data from deployed honeypots into a central store.
*   **Real-Time Dashboard:** Visualize live attack data, timelines, source IPs, targeted ports, and attack types with IST timestamps.
*   **Comprehensive Visualization:** Includes timeline charts, daily activity bar graphs, attack type distribution graphs, and statistical summaries (using Chart.js).
*   **Sophisticated Attack Simulation:**
    *   Test single, complex attacks (SQLi, XSS, Port Scan, DoS, etc.) with adjustable complexity levels.
    *   Run sustained SSH brute-force campaigns with configurable parameters.
*   **AI-Driven Analysis:** Integrated Google Gemini AI provides:
    *   Automated analysis of attack patterns.
    *   Actionable security recommendations based on observed activity.
*   **Responsive UI:** Modern frontend built with Next.js, React, TypeScript, and Tailwind CSS.

---

## 🛠️ Technology Stack

*   **Backend:**
    *   Framework: Python / FastAPI
    *   Container Orchestration: Docker / `docker-py` library
    *   Data Persistence: JSON Files
    *   AI Integration: Google Gemini API
    *   Core: Asynchronous programming (asyncio)
*   **Frontend:**
    *   Framework: TypeScript / Next.js / React
    *   Styling: Tailwind CSS
    *   Charting: Chart.js
    *   Icons: Lucide React
*   **Core Concepts:** RESTful API Design, Containerization (Docker)

---

## 🏛️ Architecture

The system uses a decoupled Client-Server architecture:

*   **Backend (FastAPI):** Acts as the control plane.
    *   Handles API requests from the frontend.
    *   Manages honeypot configurations and lifecycle (via Docker API).
    *   Persists state (honeypots, attacks) to JSON files.
    *   Runs background tasks for log polling from honeypot containers.
    *   Interacts with the Google Gemini API for analysis.
    *   Pushes real-time updates to the frontend (details needed - likely WebSockets or SSE).
*   **Frontend (Next.js):** Provides the user interface.
    *   Communicates with the backend via REST API.
    *   Displays dashboards, lists, forms, and visualizations.
    *   Receives and displays real-time attack data.

---

## 🚀 Getting Started

### Prerequisites

*   Docker Engine installed and running.
*   Python 3.x installed.
*   Node.js (v18.x or later) and npm/yarn installed.
*   Google Gemini API Key (for AI features).

### Installation

1.  **Clone the repository:**
    ```
    git clone https://github.com/your-username/your-repo-name.git
    cd your-repo-name
    ```

2.  **Backend Setup:**
    ```
    cd backend # Or your backend directory name
    # [TODO: Add command for creating a virtual environment, e.g., python -m venv venv]
    # [TODO: Add command to activate virtual environment]
    pip install -r requirements.txt
    # [TODO: Add instructions for setting up environment variables, e.g., .env file for GEMINI_API_KEY]
    ```

3.  **Frontend Setup:**
    ```
    cd ../frontend # Or your frontend directory name
    npm install
    # or
    # yarn install
    # [TODO: Add instructions for any frontend environment variables if needed]
    ```

### Running the Application

1.  **Start the Backend:**
    ```
    cd backend # Or your backend directory name
    # [TODO: Add command to start FastAPI server, e.g., uvicorn main:app --reload]
    # Ensure Docker daemon is running!
    ```
    The backend API will typically be available at `http://localhost:8000`.

2.  **Start the Frontend:**
    ```
    cd ../frontend # Or your frontend directory name
    npm run dev
    # or
    # yarn dev
    ```
    The frontend development server will typically be available at `http://localhost:3000`.

3.  **Access the Dashboard:**
    Open your web browser and navigate to `http://localhost:3000`.

---

## 📋 Usage

1.  **Navigate** to the web dashboard in your browser.
2.  **Deploy Honeypots:** Use the UI to define and deploy new honeypot instances (e.g., select SSH or Web type, provide a name). The backend will orchestrate the Docker container creation.
3.  **Monitor Attacks:** View the dashboard for real-time attack logs, statistics, and visualizations. Data is collected automatically from active honeypots.
4.  **Simulate Attacks:** Go to the simulation section to test your honeypots:
    *   Generate single complex attacks (SQLi, XSS, etc.) with varying complexity.
    *   Initiate longer SSH brute-force campaigns.
5.  **Get AI Insights:** Use the AI analysis panel to send aggregated attack data to Google Gemini and receive summaries and security recommendations.
6.  **Manage Honeypots:** View the status of deployed honeypots and delete them when no longer needed via the UI.

---

## ✅ Operational Benefits

*   **Reduced Operational Overhead:** Centralized management saves time and effort.
*   **Increased Efficiency:** Automates log collection and parsing.
*   **Improved Threat Visibility:** Unified, real-time view across honeypots.
*   **Enhanced Situational Awareness:** Quick insights into trends and attack vectors.
*   **Accelerated Analysis:** AI provides rapid initial assessments.
*   **Simplified Testing:** Integrated simulator for easy validation.
*   **Lowered Barrier to Entry:** User-friendly interface for broader accessibility.
*   **Cost-Effective:** Leverages open-source components.

---

## 🔮 Future Work

*   **Database Integration:** Replace file-based JSON persistence with a robust database (e.g., PostgreSQL, MongoDB) for better scalability and transactional integrity.
*   **Expanded Honeypot Support:** Add easy deployment for more honeypot types (e.g., RDP, FTP, Telnet, ICS/SCADA).
*   **Role-Based Access Control (RBAC):** Implement user roles and permissions.
*   **SIEM Integration:** Add options to forward aggregated logs to Security Information and Event Management (SIEM) systems.
*   **Enhanced Simulation:** More complex and configurable attack scenarios and campaigns.
*   **Improved Alerting:** Configurable alerts based on specific attack patterns or thresholds.

---

## 🙌 Contributing

Contributions are welcome! Please feel free to open an issue or submit a pull request.

[TODO: Add contribution guidelines - e.g., coding style, testing requirements, PR process]

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

<!-- Make sure you actually add a LICENSE file to your repo -->

---

*This project was developed as part of academic work at the Birla Institute of Technology and Sciences, Pilani.*

