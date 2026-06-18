# fraud-detection
## KAIM Cohort 9 Week 5-6
Fraud Detection System for E-commerce & Banking
## Business Context
Fraudulent activities result in billions of dollars in losses annually and damage customer trust. This project aims to build a robust, machine-learning-driven detection system that identifies fraudulent transactions in real-time. By leveraging Geolocation Analysis and Transaction Pattern Recognition, we enable the company to:Prevent Financial Loss: Identify and block high-risk transactions before they are processed.Enhance Security: Detect botnets and account takeovers using device and IP velocity.Build Trust: Minimize "False Positives" to ensure a seamless experience for legitimate users.
## Project Setup
Prerequisites
* Python 3.8+
* pip or condaInstallation
1. Clone the repository:git clone https://github.com/Helina-Yilma/fraud-detection.git cd fraud-detection
2. Install dependencies:pip install -r requirements.txt
3. Environment Setup:
Ensure your data files are placed in the data/raw/ directory.
## Data Description
The system utilizes three primary datasets:
| Dataset | Description | Key Features |
| :--- | :--- | :--- |
| **`Fraud_Data.csv`** | Core transaction logs for e-commerce activity. | `user_id`, `signup_time`, `purchase_time`, `device_id`, `ip_address` |
| **`IpAddress_to_Country.csv`** | Metadata used to map numerical IP ranges to physical locations. | `lower_bound_ip`, `upper_bound_ip`, `country` |
| **`creditcard.csv`** | Anonymized bank transactions (PCA-transformed). | `V1`-`V28`, `Amount`, `Class` |
## Methodology (Current Progress)
### Task 1: Data Engineering
* Geolocation Integration: Merged IP addresses with country data using a merge_asof logic to provide spatial context to transactions.
* Feature Engineering: Created high-impact features:time_since_signup: Captures the "speed to fraud" metric.transaction_velocity: Tracks frequency per device_id.
* Class Imbalance: Applied SMOTE (Synthetic Minority Over-sampling Technique) to the training set to ensure the model learns fraud patterns effectively.
### Task 2: Modeling
Baseline: Logistic Regression.
Ensemble: Random Forest (current best performer with F1: 0.9084).
Evaluation: Focus on AUC-PR and Confusion Matrices rather than simple accuracy.
## Task 3: Model Explainablity
* Explainability: Implement SHAP values to interpret model decisions for transparency.
* Refactor: Move notebook logic into the src/ directory for production readiness.
* Dashboarding: Visualize geographical fraud hotspots in a summary report.
