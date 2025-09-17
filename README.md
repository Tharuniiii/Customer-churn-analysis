# Customer-churn-analysis

# Project Overview

This app allows users to input customer attributes (demographic, services, contract, billing) and instantly get a prediction whether the customer will churn. Predictions are produced by a saved classifier loaded with joblib in app.py

# Features

Interactive Streamlit UI for collecting customer attributes.

Preprocessing of categorical variables (mapping string categories to integers).

Loads a pre-trained model and makes single-instance predictions.

Clear output: "likely to churn" or "likely to stay".

# Files
app.py — Streamlit application and input preprocessing. 

final_gb_classifier.pkl — pre-trained Gradient Boosting model (expected by app.py)

Prerequisites

Python 3.9+ recommended.

pip for package management.

A local copy of the trained model file final_gb_classifier.pkl.

# Installation & Setup

Clone or copy the project folder to your machine.

Create and activate a virtual environment (recommended)

# How to Run Locally

Important: By default app.py loads the model from an absolute path:

model = joblib.load(r"C:\Users\Tharuni\Desktop\projects\customer churn analysis Gradientboost\final_gb_classifier.pkl")

# Run the app
streamlit run app.py

# Usage

Use the radio/select inputs to provide customer features (gender, services, contract, payment method, charges, tenure group, etc.).

Click Predict.

The app displays whether the customer is likely to churn or stay.

The app expects categorical inputs as strings for some fields (e.g., Internet Service, Contract, Payment Method) and maps them internally to numeric codes — this mapping is defined in preprocess_input() inside app.py.

# Model & Preprocessing Details

Model

The Streamlit app loads a joblib-serialized model final_gb_classifier.pkl. The model was trained externally and saved to disk; app.py loads it to make predictions. 

Preprocessing (as implemented in app.py)

InternetService mapping: 'DSL' -> 0, 'Fiber optic' -> 1, 'No' -> 2. 

Contract mapping: 'Month-to-month' -> 0, 'One year' -> 1, 'Two year' -> 2. 

PaymentMethod mapping:
'Electronic check' -> 0, 'Mailed check' -> 1, 'Bank transfer (automatic)' -> 2, 'Credit card (automatic)' -> 3.

# How to Retrain / Replace Model

Train your classifier in a separate script / notebook using the same features and preprocessing mappings.

Save the model with joblib.dump(model, "final_gb_classifier.pkl").

Replace the existing final_gb_classifier.pkl file in your project folder (or edit the path in app.py to point to the new file).

Run streamlit run app.py to verify predictions.
