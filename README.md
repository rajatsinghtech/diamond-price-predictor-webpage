> Written manually, without AI assistance.

# diamond-price-predictor-webpage

## What this does

Predicts diamond prices from carat, cut, colour, clarity, and dimensions
with a trained ML model, served through a Flask API plus a Bootstrap web
page where users enter values and get a price.

## Business process

A buyer/seller enters a diamond's specs; the page calls
`/diamonds_api/`; the model returns a price. The model (`joblib`, XGBoost /
scikit-learn era) was trained in `Diamond_predictor.ipynb` on the Kaggle
diamonds dataset â€” see the
[portfolio post](https://rajatsingh.tech/portfolio/2025/07/19/building-a-machine-learning-based-diamond-price-predictor-how-i-created-a-flask-web-app-hosted-on-azure/)
for the full story. Note: `diamond_predictor.joblib` is over 100 MB so it
is NOT in the repo â€” download it from
https://drive.google.com/file/d/1e0yl1v3ehgLBkc7Mw2MpiPVR9CjA7VnX/view?usp=sharing
and place it inside the `flask-app` folder.

## Technical flow

`Jupyter_Notebook/Diamond_predictor.ipynb` (data cleaning + training on
`diamonds.csv`) â†’ `flask-app/api.py` loads the joblib model and serves
predictions with Flask-CORS â†’ `index.html` + `diamond.svg` front end.

## Repository structure

- [`flask-app/api.py`](flask-app/api.py) â€” the prediction API
- [`Jupyter_Notebook/`](Jupyter_Notebook/) â€” training notebook and dataset
- [`index.html`](index.html), [`diamond.svg`](diamond.svg) â€” the web page

## How to run

1. Switch to the `flask-app` directory (with the downloaded joblib in it)
2. Run `export FLASK_APP=api` and `export FLASK_ENV=development`
3. `flask run` â€” Flask 1.1.1, Flask-Cors 3.0.10; analysis stack pinned in
   the original notes (scikit-learn 0.24.2, xgboost 1.4.2, pandas 1.3.2)
