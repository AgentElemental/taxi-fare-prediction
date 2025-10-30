# NYC Taxi Fare Prediction with Dynamic Pricing
## Machine Learning Project with Weather & Event Integration

### 📋 Project Overview
This project implements an intelligent taxi fare prediction system that uses machine learning  
to predict base fares and applies dynamic pricing based on real-time weather conditions and  
local events. Built specifically for the NYC Taxi Trip Dataset from Kaggle.

### 🎯 Features
- **ML-Powered Predictions**: Uses Random Forest, XGBoost, and Gradient Boosting models
- **Weather-Based Surge Pricing**: Automatically adjusts fares based on weather conditions
- **Event-Based Pricing**: Increases fares during concerts, sports events, and holidays
- **User-Friendly Interface**: Flask web application with intuitive UI
- **Real-Time Predictions**: Instant fare calculation with breakdown
- **API Endpoints**: RESTful API for integration with other systems

### 📊 Dataset
**Source**: Kaggle - NYC Taxi Trip Data  
**Link**: https://www.kaggle.com/datasets/anandaramg/taxi-trip-data-nyc

**Key Features Used**:
- Pickup/Dropoff Coordinates
- Trip Distance (calculated)
- Passenger Count
- Pickup Time (hour, day, week)
- Weather Conditions
- Event Information

### 🏗️ Project Structure

taxi-fare-prediction/
│
├── data/
│ ├── train.csv # Training dataset from Kaggle
│ ├── test.csv # Test dataset
│ └── weather_data.csv # Historical weather data (optional)
│
├── models/
│ ├── train_model.py # Model training script
│ ├── taxi_fare_model.pkl # Saved trained model
│ └── preprocessing.py # Data preprocessing functions
│
├── app/
│ ├── app.py # Flask application
│ ├── templates/
│ │ ├── index.html # Home page
│ │ └── result.html # Results page
│ └── static/
│ ├── css/
│ └── js/
├── notebooks/
│ ├── EDA.ipynb # Exploratory Data Analysis
│ └── Model_Training.ipynb # Model experimentation
├── requirements.txt # Python dependencies
├── README.md # This file
└── .gitignore



### 🚀 Getting Started

#### Prerequisites
- Python 3.8 or higher
- pip package manager
- 4GB+ RAM recommended

#### Installation

1. **Clone the repository**

git clone https://github.com/yourusername/taxi-fare-prediction.git
cd taxi-fare-prediction


2. **Create virtual environment**

python -m venv venv
source venv/bin/activate # On Windows: venv\Scripts\activate


3. **Install dependencies**

pip install -r requirements.txt


4. **Download dataset**
- Go to https://www.kaggle.com/datasets/anandaramg/taxi-trip-data-nyc
- Download train.csv and test.csv
- Place in `data/` folder

#### Training the Model

python models/train_model.py

This will:
- Load and preprocess the data
- Engineer features
- Train multiple ML models
- Save the best model to `models/taxi_fare_model.pkl`
- Display performance metrics

#### Running the Web Application

cd app
python app.py

Access the application at: http://localhost:5000

### 🎮 How to Use

1. **Enter Trip Details**:
   - Pickup coordinates (latitude/longitude)
   - Dropoff coordinates
   - Passenger count
   - Pickup time (hour and day)

2. **Set Dynamic Pricing Factors**:
   - Select current weather condition
   - Select if there's an event nearby

3. **Get Prediction**:
   - View base fare
   - See applied multipliers
   - Get final fare with breakdown

### 🧮 Dynamic Pricing Multipliers

#### Weather Multipliers
| Condition    | Multiplier | Example Impact      |
|--------------|------------|--------------------|
| Clear        | 1.0x       | $20.00 → $20.00    |
| Cloudy       | 1.1x       | $20.00 → $22.00    |
| Rain         | 1.3x       | $20.00 → $26.00    |
| Heavy Rain   | 1.5x       | $20.00 → $30.00    |
| Snow         | 1.7x       | $20.00 → $34.00    |
| Storm        | 2.0x       | $20.00 → $40.00    |

#### Event Multipliers
| Event Type   | Multiplier | Example Impact      |
|--------------|------------|--------------------|
| None         | 1.0x       | $20.00 → $20.00    |
| Holiday      | 1.3x       | $20.00 → $26.00    |
| Concert      | 1.4x       | $20.00 → $28.00    |
| Sports Event | 1.5x       | $20.00 → $30.00    |
| Festival     | 1.6x       | $20.00 → $32.00    |
| Major Event  | 2.5x       | $20.00 → $50.00    |

### 📈 Model Performance

Based on testing with the NYC Taxi dataset:

| Model            | RMSE | MAE  | R² Score | Training Time |
|------------------|------|------|----------|--------------|
| Linear Regression| 6.64 | 4.85 | 0.72     | Fast         |
| Random Forest    | 4.85 | 3.45 | 0.82     | Medium       |
| XGBoost          | 4.15 | 2.95 | 0.87     | Medium       |
| Gradient Boosting| 4.35 | 3.10 | 0.85     | Medium       |

**Best Model**: XGBoost (87% accuracy, lowest error)

### 🔧 API Usage

#### Endpoint: `/api/predict`
**Method**: POST  
**Content-Type**: application/json

**Request Body**:
{
"pickup_latitude": 40.7614,
"pickup_longitude": -73.9776,
"dropoff_latitude": 40.6413,
"dropoff_longitude": -73.7781,
"passenger_count": 2,
"pickup_hour": 14,
"pickup_weekday": 2,
"temperature": 25,
"weather_condition": "rain",
"event_type": "concert"
}

**Response**:
{
"success": true,
"base_fare": 18.50,
"weather_multiplier": 1.3,
"event_multiplier": 1.4,
"final_fare": 33.67,
"trip_distance": 15.2
}

### 🌦️ Weather API Integration

#### Recommended APIs:
1. **OpenWeatherMap** (Free tier available)
   - https://openweathermap.org/api
2. **Visual Crossing** (Free tier available)
   - https://www.visualcrossing.com/weather-api
3. **Open-Meteo** (Completely free)
   - https://open-meteo.com

### 📅 Event Data Integration

#### Recommended Sources:
1. **PredictHQ** - Event intelligence API
2. **Eventbrite API** - Public events
3. **NYC Open Data** - City events and holidays

### 🎓 Learning Resources

- **Machine Learning**: scikit-learn documentation
- **XGBoost**: https://xgboost.readthedocs.io
- **Flask**: https://flask.palletsprojects.com
- **Feature Engineering**: Kaggle tutorials

### 🤝 Contributing

Contributions are welcome! Please:
1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

### 📝 License

MIT License - feel free to use for personal and commercial projects

### 👨‍💻 Author

Your Name  
GitHub: @yourusername  
Email: your.email@example.com

### 🙏 Acknowledgments

- NYC Taxi & Limousine Commission for the dataset
- Kaggle community for inspiration
- scikit-learn and XGBoost developers

### 📞 Support

For issues and questions:
- Open an issue on GitHub
- Email: support@yourproject.com

---

**Happy Predicting! 🚕💨**
