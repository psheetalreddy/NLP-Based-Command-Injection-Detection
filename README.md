# Real-Time NLP Input Sanitizer for Command Injection Detection

## Overview
This project implements an advanced security system designed to protect web applications from **Command Injection** attacks. By leveraging Natural Language Processing (NLP) and Machine Learning, the system identifies malicious patterns in user inputs that traditional signature-based filters might miss.

## Key Features
- **NLP-Powered Detection:** Uses `TfidfVectorizer` with character-level n-grams (2-4) to capture structural nuances of command injection payloads.
- **Automated ML Pipeline:** Integrates preprocessing and classification into a robust `sklearn.pipeline`.
- **Hyperparameter Optimization:** Utilizes `GridSearchCV` to optimize Logistic Regression and Random Forest models.
- **Middleware Simulation:** Includes logic to categorize inputs into `BLOCK`, `LOG_AND_ALLOW`, or `ALLOW` based on confidence thresholds.

## Tech Stack
- **Language:** Python
- **Libraries:** Scikit-learn, Pandas, NumPy, Seaborn, Matplotlib
- **Techniques:** TF-IDF (Char n-grams), Logistic Regression, Random Forest

## Getting Started

### 1. Data Preparation
Before training the model, you must generate the training data:
- Run the **Dataset Creation Notebook** (`Command Line Injection-Dataset_Creation.ipynb`). This script will synthesize a balanced dataset of benign and malicious strings and save it as `advanced_command_injection_dataset.jsonl` in the project directory.

### 2. Installation
Install the required Python dependencies:
```bash
pip install pandas scikit-learn seaborn matplotlib
```

### 3. Training and Evaluation
- Run the main project notebook to load the generated `.jsonl` file.
- The script will perform a stratified split, tune hyperparameters, and save the best-performing pipeline to `adv_model/Logistic_Regression_pipeline.pkl`.

### 4. Deployment Simulation
Use the `inspect_input()` function within the notebook to test the real-time middleware logic against custom strings.

## Results
- **Best Model:** Logistic Regression (C=10)
- **Accuracy:** ~99.98%
- **F1-Score:** 1.00

## License
This project is licensed under the MIT License.
