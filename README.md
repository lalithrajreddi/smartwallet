# Human Development Index (HDI) Predictor

An interactive, end-to-end Machine Learning web application designed to predict the **Human Development Index (HDI)** of countries. The project leverages **Python**, **Flask**, **Scikit-Learn**, and **Seaborn** to build a predictive engine and data analysis dashboard, presenting results through a responsive, modern dark-themed web interface.

---

## 🚀 Key Features

*   **Predictive ML Engine**: Enter Life Expectancy, Expected/Mean Years of Schooling, and GNI Per Capita. The application uses a trained **Linear Regression** model to predict the country's HDI score, classify it into one of the four official UNDP categories (**Very High, High, Medium, or Low**), calculate dimension-specific sub-indices, and dynamically recommend comparable countries from the dataset.
*   **Insights & EDA Gallery**: Interactive visualization hub showcasing 6 detailed exploratory charts (heatmaps, distributions, strip plots, and logarithmic scatter plots) with a clean lightbox viewer.
*   **Country Explorer Database**: Searchable, filterable interactive table displaying indicators and official HDI scores for 188 nations. Clicking any country's row dynamically autofills the predictor form for quick evaluations.
*   **Methodology & Statistics**: Displays official UNDP mathematical calculation formulas and outputs the actual trained model coefficients and intercept parameters directly from the serialized model.

---

## 🛠️ Technology Stack

*   **Backend Web Framework**: `Flask` (Python web server & API endpoints)
*   **Machine Learning**: `Scikit-Learn` (Linear Regression model fitting & metrics evaluation)
*   **Data Manipulation**: `Pandas` & `NumPy` (Feature engineering, cleaning, and indexing)
*   **Data Visualization**: `Seaborn` & `Matplotlib` (Exploratory Data Analysis plots generation)
*   **Serialization**: `Pickle` (Model saving and dynamic reloading)
*   **Frontend Interface**: `HTML5`, `Vanilla CSS3` (Glassmorphism design system, sliding transitions, glowing accents, and responsive layout), and `ES6 Javascript` (Async Fetch requests, DOM manipulation, input synchronization, and filtering).

---

## 📂 Codebase File Structure

```
SmartWallet/ (Project Directory)
├── app.py                  # Flask web backend application hosting routes
├── download_data.py        # Data pipeline: downloads, cleans, and calculates target HDI
├── eda.py                  # Generates high-quality statistical plots
├── train_model.py          # Splits dataset, trains model, and serializes it
├── hdi_model.pkl           # Serialized Linear Regression model
├── hdi_processed.csv       # Clean preprocessed country dataset
├── model_summary.txt       # Saved coefficients and testing performance logs
├── requirements.txt        # Required Python libraries list
├── .gitignore              # Ignores pycache, IDE configs, and environments
├── templates/
│   └── index.html          # Dynamic HTML dashboard interface
└── static/
    ├── css/
    │   └── style.css       # Premium space-dark stylesheet
    ├── js/
    │   └── main.js         # Frontend controller scripts (Fetch calls, UI tab transitions)
    └── plots/              # Pre-rendered Exploratory Data Analysis charts
        ├── correlation_matrix.png
        ├── education_vs_hdi.png
        ├── gni_vs_hdi.png
        ├── hdi_distribution.png
        ├── life_expectancy_vs_hdi.png
        └── strip_plot.png
```

---

## ⚙️ Installation & Setup Instructions

Follow these step-by-step instructions to get the application running on your local machine:

### 1. Prerequisites
Make sure you have **Python 3.10 or higher** installed on your system. You can check your version by running:
```bash
python --version
```

### 2. Clone/Open the Project Directory
Navigate into the project root directory in your terminal:
```bash
cd d:/Projects/SmartWallet
```

### 3. Create a Virtual Environment (Recommended)
Isolate the project dependencies by creating a python virtual environment:
*   **Windows (PowerShell)**:
    ```powershell
    python -m venv venv
    .\venv\Scripts\Activate.ps1
    ```
*   **macOS / Linux**:
    ```bash
    python3 -m venv venv
    source venv/bin/activate
    ```

### 4. Install Dependencies
Install all the required data science and web libraries listed in `requirements.txt`:
```bash
pip install -r requirements.txt
```

### 5. Run the Data Pipeline (Optional)
The dataset, plots, and serialized model are checked into Git. However, you can run the files sequentially if you want to rebuild the model and charts from scratch:
*   **Download & Preprocess Data**:
    ```bash
    python download_data.py
    ```
*   **Generate EDA Visualizations**:
    ```bash
    python eda.py
    ```
*   **Train and Serialize Model**:
    ```bash
    python train_model.py
    ```

### 6. Start the Web Server
Launch the Flask development server:
```bash
python app.py
```

Once running, open your web browser and navigate to:
👉 **[http://127.0.0.1:5000/](http://127.0.0.1:5000/)**

---

## 🧪 Scenario Verification Parameters

You can verify the model predictions in the **Predictive Engine** tab using these scenario inputs:

### Scenario 1: Very High Human Development (Emerging Developed Tier)
*   **Inputs**: Life Expectancy = `82.0` yrs, Expected Schooling = `16.0` yrs, Mean Schooling = `12.0` yrs, GNI = `50,000` PPP$
*   **Expected Outcome**: **Very High** classification. Predicted HDI Score $\approx$ **`0.913`**. (Similar countries: Sweden, Liechtenstein, New Zealand).

### Scenario 2: Emerging Economy Development Gaps (Developing Tier)
*   **Inputs**: Life Expectancy = `70.0` yrs, Expected Schooling = `12.0` yrs, Mean Schooling = `8.0` yrs, GNI = `10,000` PPP$
*   **Expected Outcome**: **Medium** classification. Predicted HDI Score $\approx$ **`0.660`**. (Similar countries: Kyrgyzstan, South Africa, Iraq).

### Scenario 3: Development Intervention Priority (Low Tier)
*   **Inputs**: Life Expectancy = `55.0` yrs, Expected Schooling = `8.0` yrs, Mean Schooling = `4.0` yrs, GNI = `1,500` PPP$
*   **Expected Outcome**: **Low** classification. Predicted HDI Score $\approx$ **`0.432`**. (Similar countries: Democratic Republic of Congo, Liberia, Guinea-Bissau).
