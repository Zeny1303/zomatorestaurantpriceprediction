# Restaurant Price Range Prediction (Zomato Dataset)

Production-ready machine learning pipeline to predict a restaurant’s **price range/category** using structured attributes such as **location, cuisines, online ordering, table booking, ratings, and votes**.  
Designed with a clean, reproducible workflow and optional app layer for interactive inference.

---

## Why this project
Pricing is a core signal in food discovery platforms and internal analytics. New or incomplete listings often lack reliable cost information. This project estimates the **price range** from other available metadata to support:
- catalog enrichment for new restaurants
- consistent pricing buckets for search/filtering
- downstream analytics and reporting

---

## What’s included
- End-to-end ML workflow: **data ingestion → cleaning → EDA → feature engineering → training → evaluation → inference**
- Multiple baseline + advanced models for comparison
- Reproducible notebooks for experimentation
- Model serialization using `joblib`
- Optional **Streamlit** UI for interactive predictions

---

## Tech stack
- **Python 3.8+**
- **Pandas, NumPy**
- **Scikit-learn**
- **Matplotlib**
- **Joblib**
- **Streamlit** *(optional)*

---

## Repository structure
> Exact folders may vary slightly based on your local setup.

```text
zomatorestaurantpriceprediction/
├─ notebooks/                 # EDA + experiments
├─ data/                      # dataset files (optional / not tracked)
├─ models/                    # trained model artifacts (.joblib)
├─ app.py                     # Streamlit app (optional)
├─ requirements.txt
└─ README.md
```

---

## Quickstart

### 1) Clone
```bash
git clone https://github.com/Zeny1303/zomatorestaurantpriceprediction.git
cd zomatorestaurantpriceprediction
```

### 2) Create virtual environment *(recommended)*
```bash
python -m venv .venv
# Windows:
.venv\Scripts\activate
# macOS/Linux:
source .venv/bin/activate
```

### 3) Install dependencies
```bash
pip install -r requirements.txt
```

---

## Run experiments (Jupyter)
```bash
jupyter notebook
```

Open the notebooks under `notebooks/` to reproduce:
- data cleaning
- exploratory analysis
- feature engineering
- model training and evaluation

---

## Run the Streamlit app *(optional)*
If `app.py` exists:

```bash
streamlit run app.py
```

---

## Modeling approach

### Data preparation
Typical steps used in this workflow:
- Missing value handling
- Categorical encoding for features like `location`, `cuisine`, `restaurant type`
- Numeric feature scaling *(where applicable)*
- Feature selection to reduce noise

### Training and selection
Models are trained and compared using validation splits and consistent evaluation logic.  
The final model is persisted as:

```text
models/final_model.joblib
```

---

## Evaluation

Depending on how the target is treated:

### Regression setup *(predict numeric cost)*
- MAE
- RMSE
- R²

### Classification setup *(predict price bucket)*
- Accuracy
- Precision / Recall / F1
- Confusion matrix

> Replace this section with your best scores once finalized to make it recruiter-ready.

---

## Inference usage (example)

```python
import joblib

model = joblib.load("models/final_model.joblib")

# features must match training-time preprocessing
sample = [[...]]
pred = model.predict(sample)

print("Predicted price range:", pred[0])
```

---

## Engineering notes
- Keep training-time preprocessing consistent with inference-time preprocessing (prefer `sklearn.Pipeline`)
- Track feature schema changes carefully to avoid mismatch bugs
- Add automated tests for data validation and feature transformations

---

## Roadmap
- [ ] Convert preprocessing + model into a single `Pipeline`
- [ ] Add feature importance / explainability report
- [ ] Add Docker support for reproducible runs
- [ ] Deploy Streamlit app (Streamlit Cloud / container)

---

## License
MIT License. See `LICENSE`.

---

## Author
Sneha  
- GitHub: https://github.com/Zeny1303  
- LinkedIn: https://linkedin.com/in/sneha1309
