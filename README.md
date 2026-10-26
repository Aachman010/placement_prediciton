# 🎓 Student Placement Predictor

A Machine Learning web application that predicts whether a student is likely to get placed based on academic performance, study habits, attendance, and other student-related factors.

The application uses a **Decision Tree Classifier**, a FastAPI backend, and an HTML frontend to provide placement predictions through a web interface.

## 🚀 Features

- **Placement Prediction:** Predicts whether a student is likely to be placed or not placed.
- **Academic Factors:** Uses study hours, attendance, previous scores, and exam scores.
- **Lifestyle Factors:** Considers sleep hours and internet usage.
- **Assignment Tracking:** Includes the number of completed assignments.
- **Student Information:** Uses gender, extracurricular participation, and academic branch.
- **REST API:** Provides a prediction endpoint using FastAPI.
- **Interactive Frontend:** Serves an HTML interface for entering student information and viewing predictions.
- **One-Hot Encoding:** Handles branch categories using the feature columns saved during model training.

## 🛠️ Tech Stack

- **Programming Language:** Python
- **Machine Learning Algorithm:** Decision Tree Classifier
- **Backend:** FastAPI
- **Data Processing:** Pandas
- **Model Serialization:** Joblib
- **Data Validation:** Pydantic
- **Frontend:** HTML

## 📂 Project Structure

```text
placement_prediction/
│
├── app.py
├── placement_model.joblib
├── columns.joblib
├── student_placement_predictor.html
├── student_performance_dataset.csv
├── Decision_Tree.ipynb
├── requirements.txt
├── README.md
└── .gitignore
```

## 📋 Input Features

The application accepts the following student information:

| Feature | Description | Data Type |
|---|---|---|
| `gender` | Student's gender | String |
| `study_hours` | Hours spent studying | Float |
| `attendance` | Student attendance | Float |
| `sleep_hours` | Average sleep hours | Float |
| `internet_usage` | Internet usage | Float |
| `assignments_completed` | Number of completed assignments | Float |
| `previous_score` | Previous academic score | Float |
| `extracurricular` | Participation in extracurricular activities | String |
| `exam_score` | Examination score | Float |
| `branch` | Student's academic branch | String |

**Note:** The expected units, ranges, and accepted category values depend on the dataset used to train the model.

## ⚙️ How It Works

1. The user enters student information through the HTML frontend.
2. The frontend sends the data to the FastAPI `/predict` endpoint.
3. The backend converts gender and extracurricular participation into numerical values.
4. The student's branch is converted into one-hot encoded features using the saved training columns.
5. Pandas creates a DataFrame with the same feature columns used during model training.
6. The trained Decision Tree Classifier predicts the student's placement outcome.
7. The API returns the result as either `Placed` or `Not Placed`.

## 🔌 API Endpoints

### 1. Home

**Endpoint:** `GET /`

Returns the HTML frontend.

### 2. Predict Student Placement

**Endpoint:** `POST /predict`

Accepts student information as JSON and returns the predicted placement status.

**Example request:**

```json
{
  "gender": "Male",
  "study_hours": 5.5,
  "attendance": 90,
  "sleep_hours": 7,
  "internet_usage": 3,
  "assignments_completed": 8,
  "previous_score": 75,
  "extracurricular": "Yes",
  "exam_score": 82,
  "branch": "CSE"
}
```

**Example response:**

```json
{
  "prediction": "Placed"
}
```

*The response is illustrative. Actual predictions depend on the trained model and input data.*

## 💻 Installation and Setup

### Prerequisites

- Python 3.10 or a compatible version
- pip
- Git

### 1. Clone the Repository

```bash
git clone https://github.com/Aachman010/placement_prediction.git
cd placement_prediction
```

### 2. Create a Virtual Environment

**Windows:**

```bash
python -m venv venv
venv\Scripts\activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

Ensure your `requirements.txt` includes the packages required by your application:

```text
fastapi
uvicorn
pandas
scikit-learn
joblib
```

### 4. Run the Application

```bash
uvicorn app:app --reload
```

### 5. Open the Application

Once the server starts, visit:

- **Web Application:** http://127.0.0.1:8000
- **Interactive API Documentation:** http://127.0.0.1:8000/docs

## 🌳 Machine Learning Model

This project uses a **Decision Tree Classifier** to predict student placement outcomes based on academic performance, study habits, attendance, and other student-related factors.

### How the Decision Tree Works

A Decision Tree is a supervised machine learning algorithm that makes predictions by learning decision rules from training data.

It repeatedly splits the dataset based on feature values, creating branches that lead to a final prediction.

For example, the model might learn that students with certain combinations of exam scores, attendance, and study hours are more likely to be placed.

The actual decision rules depend on the patterns learned during training.

### Model Workflow

1. **Input Features:** Collects student information, including study hours, attendance, previous scores, and exam scores.
2. **Feature Preprocessing:** Converts categorical features into numerical values and applies one-hot encoding to the student's branch.
3. **Decision Tree Classification:** Evaluates the input features using learned decision rules.
4. **Prediction:** Classifies the student into one of two categories:
   - `Placed`
   - `Not Placed`

### Model Storage

- `placement_model.joblib` — Stores the trained Decision Tree model.
- `columns.joblib` — Stores the feature-column information required to prepare input data consistently with the training data.

### Model Evaluation

The model can be evaluated using the following classification metrics:

- **Accuracy:** Measures the proportion of correct predictions.
- **Precision:** Measures how many predicted positive cases are actually positive.
- **Recall:** Measures how many actual positive cases the model correctly identifies.
- **F1-score:** Combines precision and recall into a single metric.
- **Confusion Matrix:** Shows correct and incorrect predictions for each class.

Actual performance metrics should be added after verifying the model evaluation results.

## ⚠️ Limitations

- Predictions depend on the quality and representativeness of the training dataset.
- The model's performance depends on the features and patterns present in the training data.
- Predictions are estimates and do not guarantee actual placement outcomes.
- The application should not be used as the sole basis for real recruitment or educational decisions.

## 🔮 Future Improvements

- Add model evaluation metrics and visualizations.
- Improve input validation and error handling.
- Display prediction probabilities where appropriate.
- Deploy the application to a cloud hosting platform.
- Improve the frontend's usability and responsiveness.
- Add automated testing for the API and prediction pipeline.

## 👨‍💻 Author

**Aachman Bhardwaj**

GitHub: [@Aachman010](https://github.com/Aachman010)

## 📄 License

This project is intended for educational and learning purposes. Add a specific open-source license if you want to define the terms under which others may use, modify, and distribute the code.

---

*Built using Python, FastAPI, and a Decision Tree Classifier to explore student placement prediction.*
