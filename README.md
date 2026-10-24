# ArogyaSanket — Complete Prototype

A full-stack educational prototype containing a React/Vite dashboard, FastAPI backend, API tests, wearable-data quality auditing, a non-destructive preprocessing pipeline, integration checklist, model-readiness gate, and deployment/demo documentation.

> **Clinical safety notice:** This is not a medical device. The current score is an illustrative rule-based demo indicator, not a trained model, probability, or clinically validated deterioration prediction. Never use it for diagnosis, triage, treatment, or real patient-care decisions. Use synthetic data only.


## Advanced intelligence workspace (added)

The **AI Intelligence** navigation item adds a research/demo workspace for:
- historical EHR context + timestamped wearable signals on a common time axis;
- a backend `POST /api/v1/intelligence/fusion` endpoint that parses and sorts timestamps, flags missing/invalid timestamps and sensor fields, counts duplicate timestamps, summarizes a supplied-sample median baseline, and reports deviations;
- a timeline point selector and transparent, hand-written rule summaries (not SHAP attributions);
- a what-if control panel that demonstrates how the existing demo rules respond to hypothetical sleep, step and heart-rate values;
- explicit safety/uncertainty limitations and a validation panel that marks AUROC, sensitivity, specificity, precision, calibration, false-alarm rate and lead time as unavailable until labelled outcomes and patient-level held-out evaluation exist.

The fusion endpoint is data engineering and descriptive analysis. A separate educational logistic-regression model is now trained on a reproducible synthetic cohort and can be called with `POST /api/v1/intelligence/predict`. Its labels are generated from an invented formula; it is **not** a clinically trained or validated deterioration model, and its score is not a medical probability. The API flags missing inputs and values outside the synthetic training range, but these are only simple demo guardrails—not calibrated uncertainty or a validated out-of-distribution detector. Its median is only a descriptive baseline of the supplied rows; production baselines need appropriate historical windows and validation. The example EHR fields and records are fictional. The UI includes a **Run synthetic model** action showing a synthetic-only score, coefficient-based explanations, and patient-level holdout metrics. The metrics are explicitly labelled synthetic-only and must not be represented as clinical performance.

### Run the fusion demo
Start the FastAPI backend and frontend using the steps above. Open **AI Intelligence** and click **Run fusion analysis**. The UI sends synthetic EHR context and the currently displayed timeline to the backend, then shows record-quality counts and the full JSON response.

The AI Intelligence page loads editorial images from Unsplash over the internet. If images do not load, the rest of the page still works.

## 1. Requirements

- macOS/Linux terminal
- Python 3.10+ (Python 3.11/3.12 recommended)
- Node.js 18+ and npm
- Git (for version control)

## 2. Start the backend

From this project root:

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
pip install -r requirements.txt
uvicorn backend.app.main:app --reload
```

Open `http://127.0.0.1:8000/health` and API docs at `http://127.0.0.1:8000/docs`.

Expected health response has `"status": "ok"` and service `arogyasanket-backend`.

## 3. Start the frontend

Open a **second terminal**, go to this project root, then:

```bash
cd frontend
npm install
cp .env.example .env
npm run dev
```

Open the local URL Vite prints (usually `http://localhost:5173`). Keep both terminals running. The frontend defaults to `http://127.0.0.1:8000`; change `VITE_API_BASE_URL` in `frontend/.env` only if your backend is elsewhere. Restart Vite after changing it.

## 4. Run automated tests

From the project root, with the virtual environment active:

```bash
pytest -q
```

Build-check the frontend from another terminal:

```bash
cd frontend
npm run build
```

## 5. Test API integration manually

1. Open `http://127.0.0.1:8000/docs`.
2. Try `POST /api/v1/risk/estimate` with:

```json
{
  "patient_id": "demo-patient-001",
  "sleep_hours": 4.5,
  "steps_today": 1800,
  "baseline_steps": 6500,
  "resting_heart_rate": 104,
  "baseline_resting_heart_rate": 76
}
```

3. Try `POST /api/v1/timeline` with the same body.
4. Try `GET /api/v1/timeline/demo-patient-001` and confirm the entry is returned.
5. In the frontend, submit the demo form and check the response panel. The timeline storage is **in-memory only** and is cleared when the backend restarts; it is not production persistence.
6. Test theme toggle, chart rendering, loading/error state, and browser console.

## 6. Wearable dataset audit and preprocessing

Place the source CSV at `data/raw/dataset_activity_skunk.csv`, then run:

```bash
python scripts/audit_activity_skunk.py data/raw/dataset_activity_skunk.csv
python scripts/prepare_activity_skunk.py data/raw/dataset_activity_skunk.csv
```

The audit writes `data/processed/activity_skunk_quality_report.json`. The preparation script writes a separate flagged copy at `data/processed/activity_skunk_flagged.csv`; it does **not** delete rows or automatically replace heart-rate values. Inspect flags and source documentation before making any cleaning decisions.

Known limitation: this activity dataset has no patient identifier, calendar date, or clinical deterioration outcome labels. It cannot by itself support patient-level timeline linkage or train a deterioration prediction model. Hour/minute fields alone do not establish which observations belong to a particular patient or day.

## 7. Synthetic model demo and data provenance

The project includes a generated dataset at `data/processed/synthetic_deterioration_cohort.csv`, a trained artifact at `backend/app/artifacts/synthetic_baseline.joblib`, and metrics at `data/processed/synthetic_validation_metrics.json`. Rebuild them with:

```bash
python scripts/train_synthetic_model.py
```

The generated cohort has 240 simulated patients and 1,920 snapshots. The binary `event_within_2h` label is created by a hand-written formula; it is not a real clinical outcome. A patient-level grouped split prevents patients from appearing in both training and test groups. Metrics (AUROC, sensitivity, specificity, precision, Brier score, balanced accuracy and false-alarm rate) measure only recovery of the simulated rule. Lead time is unavailable because the synthetic cohort has no event-onset timestamps. See `docs/DATA_PROVENANCE.md` and `docs/RISK_MODEL_READINESS.md`.

## 8. Risk-model readiness

See `docs/RISK_MODEL_READINESS.md`. Do not train/evaluate a model until an authorized dataset has a defined outcome, time horizon, patient identifier, appropriate features, and enough positive/negative examples. Use patient-level splits to avoid leakage. The optional scaffold `scripts/train_baseline.py` intentionally requires explicit target and patient-ID columns and will stop if they are missing. It is not a clinical model certification.

## 9. Before deployment

- Do not use real patient identifiers or health records in this demo.
- Set `AROGYASANKET_CORS_ORIGINS` to a comma-separated list of exact allowed frontend origins (local origins are the default).
- Replace in-memory timeline storage with a secure database and authentication/authorization.
- Add audit logging, privacy/security review, backups, rate limits, and environment-specific secrets.
- Deploy frontend and backend separately if needed; set `VITE_API_BASE_URL` to the deployed backend URL and configure CORS for the exact frontend origin.
- Do not claim clinical prediction or validation unless supported by appropriate evidence and review.

See `docs/WORK_PLAN.md` and `docs/TESTING_CHECKLIST.md` for the Phase 1–5 task breakdown.

## Frontend navigation update

The frontend now includes working navigation views for Overview, Patients, Wearable data, Risk timeline, Settings, and Help center. Preferences are stored locally in the browser. The patient directory and signal values are fictional demo content. For frontend setup, see `frontend/README.md`.
# digtaltwin
