# LOA (Length of Stay) Prediction System

A machine learning-based healthcare application that predicts patient length of stay (LOS) in hospital settings. This project uses XGBoost and Random Forest regression models to estimate patient stay duration based on various clinical and demographic features.

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Project Structure](#project-structure)
- [Dataset Information](#dataset-information)
- [Installation](#installation)
- [Usage](#usage)
- [Model Performance](#model-performance)
- [Technologies Used](#technologies-used)
- [Contributing](#contributing)

## 🎯 Overview

This project analyzes patient healthcare data to predict the length of stay (LOS) in hours. The system combines multiple data sources including patient demographics, medical conditions, medications, encounters, and observations to build predictive models. The final implementation includes an interactive Gradio-based web interface for real-time predictions.

## ✨ Features

- **Multi-source Data Integration**: Combines data from patients, encounters, medications, conditions, and observations
- **Feature Engineering**: Creates predictive features from raw healthcare data
- **Dual Model Approach**: Implements both Random Forest and XGBoost regression models
- **Interactive Web Interface**: User-friendly Gradio dashboard for making predictions
- **Visual Analytics**: Includes data visualizations and model performance metrics

## 📁 Project Structure

```
LOA_Prediction/
│
├── Our_FINAL_UI.ipynb          # Main Jupyter notebook with all code
├── patients.csv                 # Patient demographic data
├── encounters.csv               # Hospital encounter records
├── medications.csv              # Medication prescriptions
├── conditions.csv               # Patient medical conditions
├── observations.csv             # Clinical observations (reduced size)
├── requirements.txt             # Python package dependencies
└── README.md                    # This file
```

## 📊 Dataset Information

The project uses five main CSV datasets:

1. **patients.csv**: Contains patient demographic information (age, gender, location, etc.)
2. **encounters.csv**: Records of patient hospital visits and encounters
3. **medications.csv**: Medication prescriptions and history
4. **conditions.csv**: Medical conditions and diagnoses
5. **observations.csv**: Clinical observations and vital signs

### ⚠️ Important Note About observations.csv

Due to GitHub file size limitations, the `observations.csv` file has been reduced in size by removing some rows. The uploaded version contains a representative sample of the original dataset. For production use or full analysis, you would need the complete dataset.

**Original Dataset Characteristics:**
- The observations dataset is typically very large due to the granular nature of clinical observations
- Only a subset of rows has been included in the GitHub repository
- The code will work with the reduced dataset, but results may vary compared to using the full dataset

## 🚀 Installation

### Prerequisites

- Python 3.7 or higher
- pip (Python package installer)
- Jupyter Notebook or JupyterLab (for running the notebook)

### Step-by-Step Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd LOA_Prediction
   ```

2. **Create a virtual environment (recommended)**
   ```bash
   python -m venv venv
   
   # On Windows:
   venv\Scripts\activate
   
   # On macOS/Linux:
   source venv/bin/activate
   ```

3. **Install required packages**
   ```bash
   pip install -r requirements.txt
   ```

   If you don't have a `requirements.txt` file, install packages manually:
   ```bash
   pip install pandas numpy scikit-learn xgboost gradio matplotlib seaborn jupyter
   ```

4. **Launch Jupyter Notebook**
   ```bash
   jupyter notebook
   ```

## 💻 Usage

### Running the Complete Project

1. Open `Our_FINAL_UI.ipynb` in Jupyter Notebook
2. Ensure all CSV files are in the same directory as the notebook
3. Run all cells sequentially (Cell → Run All)
4. The final cell will launch the Gradio interface

### Using the Prediction Interface

Once the Gradio interface is launched, you can:

1. Adjust the input sliders for:
   - **Age**: Patient age (0-100)
   - **Total Encounters**: Number of previous encounters (0-50)
   - **Emergency Visits**: Number of emergency room visits (0-20)
   - **Total Medications**: Current medications count (0-30)
   - **Total Conditions**: Medical conditions count (0-30)
   - **Chronic Conditions**: Chronic condition count (0-10)
   - **Total Observations**: Clinical observations count (0-50)

2. Click **"Predict LOS"** to get predictions

3. View the results:
   - Predicted LOS in days
   - Predicted LOS in hours
   - Risk recommendation
   - Feature importance visualization
   - Model accuracy plots

### Running Specific Sections

You can also run individual cells to:
- Load and explore data
- Perform feature engineering
- Train models independently
- Generate visualizations

## 📈 Model Performance

### XGBoost Model (Final Implementation)
- **Mean Absolute Error (MAE)**: 0.83 hours
- **Root Mean Squared Error (RMSE)**: 1.60 hours
- **R² Score**: 0.9631 (96.31% accuracy)

### Random Forest Model
- **Mean Absolute Error (MAE)**: 6.41 hours
- **Root Mean Squared Error (RMSE)**: 35.11 hours
- **R² Score**: 0.0096 (0.96% accuracy)

**Note**: XGBoost was selected as the primary model due to its superior performance, especially with the skewed LOS distribution.

## 🛠️ Technologies Used

- **Python 3.x**: Programming language
- **Pandas**: Data manipulation and analysis
- **NumPy**: Numerical computing
- **Scikit-learn**: Machine learning utilities and Random Forest
- **XGBoost**: Gradient boosting framework for regression
- **Gradio**: Web interface for machine learning models
- **Matplotlib**: Data visualization
- **Seaborn**: Statistical data visualization
- **Jupyter Notebook**: Interactive development environment

## 🔬 Methodology

1. **Data Loading**: Import all CSV files and perform initial data validation
2. **Data Cleaning**: Handle missing values with appropriate defaults
3. **Feature Engineering**: 
   - Calculate patient age from birthdate
   - Aggregate encounter statistics (total visits, emergency visits, LOS)
   - Count medications, conditions, and observations per patient
   - Identify high-risk conditions
   - Calculate chronic condition flags
4. **Model Training**: 
   - Split data into training and testing sets (80/20)
   - Train XGBoost and Random Forest models
   - Evaluate model performance
5. **Deployment**: Create interactive web interface with Gradio

## 📝 Key Features Used for Prediction

- Age
- Total Encounters
- Total Emergency Visits
- Total Medications
- Total Conditions
- Total Chronic Conditions
- Total Observations

## ⚠️ Important Notes

- This is a demonstration/educational project using synthetic or anonymized healthcare data
- The predictions should not be used for actual clinical decision-making
- Model performance may vary with different datasets
- The observations.csv file in this repository is a reduced version due to GitHub size limitations

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📄 License

This project is provided as-is for educational and demonstration purposes.

## 👤 Author

**Sasikumarreddy Vennapusa**

Created as part of a healthcare analytics project.

## 🙏 Acknowledgments

- Healthcare data structure based on standard FHIR/HL7 formats
- Model architecture inspired by healthcare analytics best practices

---

## 📤 Adding This Project to GitHub

### For README.md and requirements.txt:

**Option 1: Using Git (Recommended)**
1. Create a new repository on GitHub (if you haven't already)
2. In your local project folder, use Git commands:
   ```bash
   git add README.md
   git add requirements.txt
   git commit -m "Add README and requirements.txt"
   git push origin main
   ```

**Option 2: Direct Upload on GitHub Website**
1. Go to your GitHub repository page
2. Click "Add file" → "Upload files"
3. Drag and drop both `README.md` and `requirements.txt` files
4. Click "Commit changes"

**Note**: GitHub automatically displays README.md files in a nicely formatted way on your repository homepage, so you should **upload/commit the file directly** (not copy-paste). The markdown formatting will be rendered automatically by GitHub.

### About requirements.txt:

The `requirements.txt` file should be **committed/uploaded** to your GitHub repository along with your other files. This allows anyone who clones your repository to easily install all dependencies by running:
```bash
pip install -r requirements.txt
```

This is a standard practice in Python projects and makes it much easier for others (including recruiters) to set up and run your project on their own systems.

---

**Note for Recruiters/Reviewers**: This project demonstrates skills in data science, machine learning, healthcare analytics, and interactive web application development. The code is well-commented and structured for easy understanding and reproduction.

