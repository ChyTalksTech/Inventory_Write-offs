# Inventory Health & Write-off Prediction: North America Pilot

## Executive Summary
This project implements an automated predictive pipeline to identify high-value inventory obsolescence within the **North America System ($15.4M Group Cost)**. By bridging classical statistics (Prophet) with advanced Ensemble Learning (XGBoost) and Anomaly Detection (Isolation Forest), the system identifies **$737,114.22** in underlying Obsolescence with **100% precision (PR-AUC 1.0)**.


## Architectural Workflow
The pipeline follows a **CRISP-DM** framework integrated with **GitFlow** for regulated environment auditability.

1.  **Ingestion Layer:** snowflake "Push-down" filtering of SAP MSEG/MARA tables.
2.  **Veracity Layer:** Temporal Forward-Fill and Log-Transformation stabilize Lumpy Demand.
3.  **Predictive Layer:** XGBoost regressor optimized for financial **WMAE**, outperforming Prophet (MASE 0.63) and LSTM (MASE 4.21).
4.  **Anomaly Layer:** Isolation Forest trained on residuals to capture 'Black Swan' operational failures.
5.  **XAI Layer:** SHAP-driven explainability to mitigate **Automation Bias** and support Human-in-the-Loop decision making.



## Key Performance Metrics
| Model | MASE | WMAE (Financial) | R² / PR-AUC |
| :--- | :--- | :--- | :--- |
| **Prophet (Baseline)** | 0.6337 | $138,326 | -0.31 |
| **XGBoost (Champion)** | -- | **$73,553** | **0.5433** |
| **LSTM (Deep Learning)** | 4.2146 | $884,214 | -398.6 |
| **Isolation Forest** | -- | -- | **1.0 (PR-AUC)** |


## Installation & Reproducibility
To ensure GxP-compliant environment parity:

```bash
# Clone the repository
git clone https://github.com/your-repo/inventory-health.git

# Create virtual environment
python -m venv venv
source venv/bin/activate  # venv\Scripts\activate on Windows

# Install locked dependencies
pip install -r requirements.txt
```



## Governance & Ethics
* **Data Lineage:** Full traceability from Snowflake source to USD-homogenized prediction.
* **Anonymization:** All site-specific identifiers and vendor names are hashed.
* **Human-in-the-Loop:** The dashboard is designed as a "rebuttable presumption" framework, requiring qualitative override codes for AI-discrepancies to avoid Automation Bias.

**Status:** Pilot Complete / Ready for Global Scaling ($262.4M VaR).
