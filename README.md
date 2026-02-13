# ITSM Incident Management - Machine Learning Project

## Project Overview
This project implements Machine Learning solutions to improve IT Service Management (ITSM) operations for ABC Tech, a mid-size IT-enabled organization handling 22,000-25,000 IT service tickets per month.

**Project Reference:** PM-PR-0012  
**Client:** ABC Tech

## Business Problem
Recent customer surveys indicated poor incident management performance. Management aimed to leverage Machine Learning for prediction and automation to improve ITSM operations and customer satisfaction.

## Use Cases Implemented

### 1. High Priority Ticket Prediction
- **Objective:** Identify Priority 1 and Priority 2 incidents in advance
- **Models Used:** Logistic Regression, Random Forest, XGBoost
- **Benefit:** Enables proactive issue resolution and reduces downtime

### 2. Incident Volume Forecasting
- **Objective:** Forecast quarterly and annual incident trends
- **Technique:** Time series analysis
- **Benefit:** Better workforce and infrastructure planning

### 3. Auto Tagging of Tickets
- **Objective:** Automatically assign priorities and categories to incidents
- **Benefit:** Reduces manual effort and reassignment delays

### 4. RFC Failure Prediction
- **Objective:** Detect potential failures in change requests
- **Models Used:** Logistic Regression, Random Forest, XGBoost
- **Performance:**
  - Random Forest: 71% accuracy, F1-score 0.69-0.73
  - XGBoost: 69% accuracy, high recall (0.82) for failure detection
- **Benefit:** Prevents misconfigurations and service disruptions

## Dataset
- **Source:** MySQL database with historical ITSM incident data
- **Period:** 2012-2014
- **Size:** Approximately 46,000 incident records
- **Access:** Read-only access to production database

## Technologies Used
- **Programming Language:** Python 3.10
- **Libraries:**
  - Data Processing: pandas, numpy
  - Database: mysql-connector-python, SQLAlchemy
  - Machine Learning: scikit-learn, XGBoost
  - Visualization: matplotlib, seaborn (implied)

## Project Structure
```
├── Client_project.ipynb    # Main Jupyter notebook with all analyses
├── README.md              # Project documentation
└── requirements.txt       # Python dependencies (to be created)
```

## Installation

### Prerequisites
- Python 3.10+
- MySQL access credentials (if connecting to database)

### Setup
```bash
# Clone the repository
git clone https://github.com/yourusername/itsm-ml-project.git
cd itsm-ml-project

# Create virtual environment
python -m venv itsm_env
source itsm_env/bin/activate  # On Windows: itsm_env\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

### Required Packages
```
pandas
numpy
mysql-connector-python
sqlalchemy
scikit-learn
xgboost
jupyter
```

## Usage

1. **Launch Jupyter Notebook:**
   ```bash
   jupyter notebook Client_project.ipynb
   ```

2. **Database Connection:**
   - Update database credentials in the notebook
   - Ensure MySQL server is accessible

3. **Run Analysis:**
   - Execute cells sequentially
   - Models will be trained and evaluated automatically

## Model Performance

### RFC Failure Prediction Results
| Model | Accuracy | Precision (Class 1) | Recall (Class 1) | F1-Score (Class 1) |
|-------|----------|---------------------|------------------|--------------------|
| Logistic Regression | 0.71 | 0.62 | 0.79 | 0.69 |
| Random Forest | 0.71 | 0.63 | 0.76 | 0.69 |
| XGBoost | 0.69 | 0.60 | 0.82 | 0.69 |

**Key Insight:** XGBoost achieves the highest recall (0.82), making it ideal for failure detection scenarios where catching all failures is critical.

## Business Impact

### Operational Benefits
- ✅ Faster incident resolution time
- ✅ Reduced ticket reassignment and handling delays
- ✅ Improved IT staffing and infrastructure planning
- ✅ Early detection of system risks and misconfigurations
- ✅ Automation of ITSM ticket classification
- ✅ Improved customer satisfaction and service quality

### ITIL Alignment
The implemented solutions align with ITIL best practices for:
- Incident Management
- Change Management
- Service Level Management
- Capacity Planning

## Key Findings
1. **Class Imbalance:** Dataset shows more "No Failure" than "Failure" cases, handled using `class_weight='balanced'`
2. **Model Selection:** Random Forest provides balanced performance for production deployment
3. **Failure Detection:** XGBoost is recommended when detecting failures is more critical than overall accuracy

## Future Improvements
- Feature engineering from `Open_Time`, related incidents, and `Handle_Time_hrs`
- Hyperparameter tuning for Random Forest and XGBoost
- Ensemble models for improved stability
- Integration with production ticketing system
- Real-time prediction API

## Contributing
Contributions are welcome! Please feel free to submit a Pull Request.

## License
This project is licensed under the MIT License - see the LICENSE file for details.

## Contact
For questions or feedback, please open an issue in this repository.

## Acknowledgments
- ABC Tech for providing the ITSM dataset
- ITIL framework for best practice guidelines

---

**Note:** Database credentials in the notebook should be updated or removed before public deployment. Use environment variables for sensitive information.
