# Q-SAT-GUARD: Proof-of-Concept Demo

This repository contains the source code for the Proof-of-Concept (PoC) demo of the **Q-SAT-GUARD** project, a research proposal submitted to the Samsung Technology Research Program. The demo aims to showcase the core functionalities of the proposed framework: a mobile-centric Post-Quantum Cryptography (PQC) benchmarking engine and a simplified AI-based anomaly detector.

## 🎯 Project Goal

To build a functional demo that tangibly illustrates the two pillars of the Q-SAT-GUARD proposal:
1.  **PQC Performance Benchmarking:** Visualize the performance trade-offs (latency, memory) of NIST-standardized PQC algorithms running on a real Samsung Android device.
2.  **Anomaly Detection:** Demonstrate the feasibility of monitoring cryptographic processes and flagging abnormal behavior, simulating the detection of potential implementation flaws or side-channel vulnerabilities.

## 🏛️ Demo Architecture

The demo consists of three main components:
1.  **Android "Probe" App (`/android-app`):** A headless Android application that runs PQC benchmarks and sends performance metrics to the backend.
2.  **Backend Server (`/backend`):** A Python/FastAPI server that receives, stores, and serves the benchmark data via a REST API.
3.  **Frontend Dashboard (`/frontend`):** A simple web-based dashboard that visualizes the collected data and highlights anomalies.

---

## 🚀 Development Roadmap & Task Board

This section outlines the development tasks, structured by phases.

### Phase 1: Android PQC Benchmarking App (`/android-app`)

**Status: Not Started ⏳**

- [ ] **Task 1.1: Project Setup:** Create a new Android Studio project with Kotlin.
- [ ] **Task 1.2: Dependency Integration:** Add Bouncy Castle PQC provider (`bcprov-jdk18on`, `bcpkix-jdk18on`) to `build.gradle.kts`.
- [ ] **Task 1.3: Implement KEM Benchmarks:**
    - [ ] Create a function `runKemBenchmark(algorithm: String, iterations: Int)` that measures KeyGen, Encapsulate, Decapsulate latency.
    - [ ] Test with `Kyber-512` and `Kyber-768`.
- [ ] **Task 1.4: Implement Signature Benchmarks:**
    - [ ] Create a function `runSignatureBenchmark(algorithm: String, iterations: Int)` that measures KeyGen, Sign, Verify latency.
    - [ ] Test with `Dilithium-2` and `Dilithium-3`.
- [ ] **Task 1.5: Implement Metric Collection:**
    - [ ] Integrate `System.nanoTime()` for precise latency measurement.
    - [ ] Integrate `Debug.getMemoryInfo()` to capture memory usage before and after tests.
- [ ] **Task 1.6: Simulate Anomaly:**
    - [ ] Create a "vulnerable" version of a benchmark function (e.g., `runSignatureBenchmark_WithAnomaly`) that includes a `Thread.sleep()` to simulate a timing leak.
- [ ] **Task 1.7: Network Layer:**
    - [ ] Integrate Retrofit for making HTTP requests.
    - [ ] Define data models (e.g., `BenchmarkResult.kt`) for JSON serialization.
    - [ ] Implement a function to POST results to the backend API.

### Phase 2: Backend & Frontend (`/backend`, `/frontend`)

**Status: Not Started ⏳**

- [ ] **Task 2.1 (Backend): Setup FastAPI Server:** Create a basic Python project with FastAPI and Uvicorn.
- [ ] **Task 2.2 (Backend): Database Model:** Define a SQLAlchemy model (or use simple file storage) for benchmark results.
- [ ] **Task 2.3 (Backend): API Endpoints:**
    - [ ] Implement `POST /api/benchmark` to receive and save data from the Android app.
    - [ ] Implement `GET /api/results` to query and return data for the frontend.
- [ ] **Task 2.4 (Frontend): Basic HTML Structure:** Create an `index.html` file for the dashboard.
- [ ] **Task 2.5 (Frontend): Integrate Chart.js:** Add the Chart.js library.
- [ ] **Task 2.6 (Frontend): Data Fetching:** Write JavaScript to fetch data from the backend's `/api/results` endpoint.
- [ ] **Task 2.7 (Frontend): Implement Visualizations:**
    - [ ] Create a bar chart for comparing average algorithm performance.
    - [ ] Create a line chart for visualizing sequential operations and flagging anomalies (e.g., data points with an `is_anomaly=true` flag).

### Phase 3: Integration & Finalization

**Status: Not Started ⏳**

- [ ] **Task 3.1: End-to-End Testing:** Deploy the backend and test the full data flow from the Android app to the dashboard.
- [ ] **Task 3.2: Code Cleanup & Documentation:** Add comments and clean up the codebase.
- [ ] **Task 3.3: Create Demo Script:** Write a step-by-step script for presenting the demo.
- [ ] **Task 3.4: Record Demo Video:** Record a high-quality video walkthrough of the PoC in action.

## 🛠️ How to Run

*(This section will be filled in once the project is runnable.)*

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/ailabteam/q-sat-guard-demo.git
    cd q-sat-guard-demo
    ```
2.  **Start the backend server:**
    ```bash
    cd backend
    # ... instructions to run the server
    ```
3.  **Run the Android app:**
    - Open the `/android-app` directory in Android Studio.
    - Build and run on a physical Samsung device.
4.  **View the dashboard:**
    - Open `/frontend/index.html` in a web browser.
    
