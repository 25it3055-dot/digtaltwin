# 🩺 ArogyaSanket
### AI-Assisted Health Trend Analysis | Digital Twin Challenge 2026

**Project Theme:** Healthcare Analytics, Artificial Intelligence and Digital Health  
**Problem Statement:** Option C — Predict Deterioration Risk from Sleep and Activity

---

## 📌 1. Project Overview

ArogyaSanket is a healthcare analytics prototype that explores how sleep quality, daily physical activity, heart rate and patient history can be combined to understand changes in health-related trends over time.

The project aims to demonstrate how data processing, transparent analytical indicators and machine-learning techniques can help identify patterns that may deserve further attention.

### Key Objectives

- Analyze sleep, steps and heart-rate data.
- Explore historical health trends.
- Identify unusual patterns and data-quality issues.
- Visualize changes in health indicators over time.
- Demonstrate an explainable AI/ML workflow.
- Provide a clear interface for exploring health-related data.

## 🎯 2. Problem Statement

**Digital Twin Challenge 2026 — Option C: Predict deterioration risk from sleep and activity.**

The challenge is to combine patient history, sleep quality, step counts and heart rate to identify patterns associated with a predefined risk outcome and show how the indicator changes over time.

ArogyaSanket explores this challenge through a healthcare analytics interface and a data-driven analysis workflow.

## 🏥 3. Healthcare Use Case

ArogyaSanket demonstrates how wearable-style data and historical records can be explored together.

### Example Inputs
- Sleep duration and sleep quality
- Daily step count
- Heart-rate readings
- Timestamped activity records
- Historical context, where available

### Expected Outputs
- Visual summaries of health-related trends
- Identification of missing or unusual readings
- Illustrative indicators based on available inputs
- Time-based comparisons
- Explanations of the factors contributing to a displayed indicator

**Clinical limitation:** This is an educational prototype, not a clinically validated medical device. Demonstration scores and synthetic-data models must not be interpreted as validated medical probabilities or used for diagnosis, treatment or emergency decisions.

## 👥 4. Team Details

- **Team Name:** [thundercode]
- **Team Leader:** [Soumya singh]
- **Team Members:** [gitanjali, soumya singh , manasvi rai and priyanshu gaurav]
- **College / Institution:** [rajiv gandhi insitiute of petroluem technology]
- **Department:** [CSE]
*Incubator:** [NA]

## 🛠️ 5. Technical Stack

The intended project stack includes:

- **Frontend:** React, Vite, JavaScript and CSS
- **Backend:** Python and FastAPI
- **Data Processing:** Pandas and NumPy
- **Machine Learning:** Scikit-learn
- **Testing:** Pytest
- **Version Control:** Git and GitHub

The final implementation and dependency files should be checked to confirm which technologies are actually used.

## 🤖 6. AI/ML Model and Framework Details

The project explores two analysis approaches:

### A. Rule-Based Analysis
A transparent demonstration approach can combine selected input signals to produce an illustrative indicator. Its rules and limitations should be documented.

### B. Machine-Learning Workflow
A synthetic-data model can demonstrate data preparation, model training, prediction and evaluation.

Synthetic labels are not real clinical outcomes. Performance on synthetic data does not establish clinical accuracy or the ability to predict real patient deterioration.

### Future Validation
A reliable deterioration-prediction model would require:
- An appropriate dataset with clearly defined outcomes
- Documented data provenance and permitted usage
- Patient-level separation of training and test data
- Appropriate evaluation metrics and calibration
- Bias, privacy and safety assessments
- Independent clinical validation before any clinical use

## 🏗️ 7. System Architecture

The intended system workflow is:

1. **User Interface:** Collects or displays health-related inputs.
2. **Backend API:** Receives requests and coordinates processing.
3. **Data Processing:** Checks input validity and prepares records.
4. **Analysis Layer:** Calculates documented indicators or runs the available model.
5. **Results Layer:** Returns analysis results to the interface.
6. **Dashboard:** Displays trends and explanatory information.

**Architecture Diagram:** <img width="1536" height="1024" alt="Arogya Sanket Digital Health Pipeline" src="https://github.com/user-attachments/assets/093786f1-3bbc-444d-9372-1191401bb79b" />

Add the actual architecture PDF to the repository before submission.

## 📊 8. Project Presentation

The presentation should cover:
- Problem statement and motivation
- Proposed solution
- Healthcare use case
- System architecture
- Technical stack
- AI/ML workflow
- Demonstration and outcomes
- Limitations and future scope


**Canva Presentation:** https://canva.link/thsmann67linn5l

Upload the exported PDF or PPT to the repository and verify that it opens correctly.

## 📂 10. Repository Structure

The repository should contain the actual project files, for example:

```text
digitaltwin/
├── README.md
├── LICENSE
├── .gitignore
├── requirements.txt
├── backend/
├── frontend/
├── scripts/
├── tests/
├── sample_data/
└── docs/
    ├── architecture.pdf
    ├── ArogyaSanket_Presentation.pdf
    ├── DATA_PROVENANCE.md
    └── TESTING_CHECKLIST.md
```

This is an illustrative structure. Keep only directories and files that exist in the submitted project, and upload the complete application code.

## 🚀 11. Setup and Execution

Follow the setup instructions documented for the actual project.

For a Python backend using FastAPI, a typical environment setup is:

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

Start the backend using the command configured in the project. For example, if its entry point is `backend.app.main`:

```bash
uvicorn backend.app.main:app --reload
```

For a React/Vite frontend, open a second terminal:

```bash
cd frontend
npm install
npm run dev
```

These commands depend on the actual project structure and configuration. Verify them by running the application before submission.

## 🧪 12. Testing

Document the tests that have actually been executed.

If the project uses Pytest:

```bash
pytest -q
```

If the frontend uses Vite:

```bash
cd frontend
npm run build
```

Record test results honestly. Do not report tests as passing unless they have been run successfully.

## 🔐 13. Data Privacy and Responsible AI

- Do not commit passwords, API keys or secret credentials.
- Do not publish identifiable patient records.
- Use synthetic or appropriately authorized and de-identified data.
- Document data sources and usage restrictions.
- Explain the limitations of synthetic data.
- Do not claim clinical accuracy without suitable validation.
- Do not use demonstration outputs for real medical decisions.

## 🔗 15. Submission Links

- **GitHub Repository:** https://github.com/25it3055-dot/digitaltwin
- **Canva Presentation:** https://canva.link/thsmann67linn5l
- **Architecture PDF:** <img width="1536" height="1024" alt="Arogya Sanket Digital Health Pipeline" src="https://github.com/user-attachments/assets/9964e4d3-5b50-4688-bcf9-2bc2a6585364" />


## ✅ 16. Submission Checklist

- [ ] Team details completed
- [ ] College/incubator information completed
- [ ] Project title and problem statement documented
- [ ] Healthcare use case explained
- [ ] Technical stack verified against the implementation
- [ ] AI/ML approach and limitations documented

- [ ] Architecture diagram PDF/PPT uploaded
- [ ] Project presentation PDF/PPT uploaded
- [ ] Complete source code uploaded
- [ ] Repository and required links publicly accessible

---

**ArogyaSanket — Making Health Trends Easier to Explore Through Data and AI.**
