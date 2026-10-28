# PhishGuard — Phishing Website Detector System

**PhishGuard** is a lightweight, static URL-based analysis tool designed to detect phishing websites in real-time. Built using Python, machine learning heuristics, SQLite, and Tkinter, it provides instant classification with a risk score ($0–100$) without navigating to potentially dangerous sites.

---

## 📌 Project Information

- **Project Title:** Phishing Website Detector System (PhishGuard)
- **Author:** Monira Akter Mahin (ID: IT24017)
- **Institution:** Mawlana Bhashani Science and Technology University (MBSTU)
- **Department:** Department of Information and Communication Technology
- **Course:** ICT-3107 — Software Engineering and Project Management
- **Supervisor:** Professor Dr. Ziaur Rahman

---

## ✨ Features

- **Instant URL Scanning:** Static URL feature extraction (Length, IP Host, `@` symbol, Hyphens, HTTPS usage, URL Shorteners, Keyword analysis).
- **Risk Score Generation:** Assigns a risk score ($0–100$) and classifies URLs as **LEGITIMATE** (Green) or **PHISHING** (Red).
- **Scan History:** Automatically logs all scan attempts with timestamps into a local SQLite database.
- **User Feedback & Reporting:** Allows users to submit reports on false positives/negatives for continuous model refinement.
- **Data Export:** Export scan history to CSV format for external analysis.
- **Admin Utilities:** Retrain models and manage blacklist records.

---

## 🔄 System Workflow

The following flowchart illustrates the step-by-step execution path when a user submits a URL to the system:

```text
+-----------------------+
|   User Enters URL     |
+-----------+-----------+
            |
            v
   /-----------------\
  /   URL Valid?      \---[ No ]---> [ Show Error Message ]
  \-------------------/
            |
          [ Yes ]
            v
+-----------------------+
| Extract Features      |  (Length, IP, '@', Hyphens, HTTPS, Shortener, etc.)
+-----------+-----------+
            |
            v
+-----------------------+
| Compute Risk Score    |  (PhishingClassifier Engine)
+-----------+-----------+
            |
            v
   /-----------------\
  / Score >=         \---[ Yes ]---> [ Label: PHISHING (Red) ]
  \ Threshold?       /                      |
   \-----------------/                      |
            |                               |
          [ No ]                            |
            v                               |
 [ Label: LEGITIMATE (Green) ]              |
            |                               |
            +---------------+---------------+
                            |
                            v
             +------------------------------+
             |  Save Result to SQLite DB    |
             +------------------------------+
                            |
                            v
             +------------------------------+
             | Display Result on GUI / End  |
             +------------------------------+
```

---

## 🛠️ Technology Stack & Architecture

- **Language:** Python 3.x
- **GUI Framework:** Tkinter
- **ML / Data Processing:** `scikit-learn`, `numpy`, `pandas`
- **Database:** SQLite3
- **Testing:** `pytest` (Targeting $\ge 70\%$ coverage)
- **Process Model:** Agile Incremental (Scrum Sprints)

### Key UML & Architecture Components
- **`PhishGuardApp`**: GUI Layer handling user input and visual display.
- **`Analyst`**: Main controller handling scanning logic.
- **`URLFeatureExtractor`**: Extracts URL heuristic features.
- **`PhishingClassifier`**: Classifies features using weighted heuristics / ML model.
- **`ScanResult`**: Encapsulates scan output and metadata.
- **`ScanHistory`**: Manages SQLite persistent database operations.

---

## 🚀 Getting Started

### Prerequisites
Make sure you have Python 3.8+ installed on your system.

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/phishguard.git
   cd phishguard
   ```

2. Create and activate a virtual environment (optional but recommended):
   ```bash
   python -m venv venv
   # On Windows:
   venv\Scripts\activate
   # On Linux/macOS:
   source venv/bin/activate
   ```

3. Install required packages:
   ```bash
   pip install scikit-learn pytest
   ```

### Running the Application

Navigate to the source directory and launch `main.py`:

```bash
cd src/phishguard
python main.py
```

---

## 🧪 Testing

Run automated unit tests with `pytest`:

```bash
pytest tests/
```

---

## 🔮 Future Roadmap

- [ ] Integration of ML model with HTML content analysis & WHOIS lookup.
- [ ] Browser extension integration (Chrome / Firefox).
- [ ] E-mail content scanner module.
- [ ] REST API development for third-party integrations.

---

## 📜 License

This project is created for academic purposes under the Software Engineering and Project Management course (ICT-3107) at Mawlana Bhashani Science and Technology University.
