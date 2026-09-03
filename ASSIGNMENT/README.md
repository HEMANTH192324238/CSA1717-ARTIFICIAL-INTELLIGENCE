# Intelligent Traffic Congestion Prediction and Smart Route Recommendation

## 1. Project Overview
This project demonstrates an AI-based traffic management workflow that:
1. Uses historical traffic data to predict congestion.
2. Converts predicted congestion into dynamic road-network costs.
3. Uses graph-based shortest-path routing to recommend an efficient route.
4. Provides a web frontend for prediction and route recommendation.

## 2. Architecture

Frontend (HTML/CSS/JavaScript)
        |
        | REST API / JSON
        v
Backend (Python + Flask)
        |
        +--> Pandas / NumPy
        +--> Scikit-learn Random Forest
        +--> NetworkX road graph
        |
        v
Traffic prediction -> Dynamic edge weights -> Smart route

## 3. Technologies Used
### Frontend
- HTML5
- CSS3
- JavaScript (Fetch API)

### Backend
- Python 3.x
- Flask
- Flask-CORS
- Pandas
- NumPy
- Scikit-learn
- NetworkX
- Matplotlib

### Development
- VS Code / PyCharm
- Jupyter Notebook or Google Colab for experimentation
- Git and GitHub for version control

## 4. Dataset
`data/traffic_dataset.csv` contains:
- road_segment_id
- timestamp
- speed
- volume
- congestion_level

The included CSV is a synthetic, reproducible demonstration dataset. It is intended to make the project runnable without external downloads. For final academic reporting, replace it with the approved real traffic dataset and rerun the experiments.

## 5. Algorithms
### Congestion Prediction
Random Forest Classification is used to predict:
- Low
- Medium
- High congestion

Features:
- road segment
- hour
- day of week
- speed
- traffic volume

### Route Recommendation
NetworkX represents the road network as a weighted graph. A baseline route minimizes physical distance, while the smart route minimizes predicted travel cost after congestion-based dynamic weights are applied.

## 6. Installation

### Backend
Open a terminal in `backend/`:

```bash
python -m venv .venv
```

Windows:
```bash
.venv\Scripts\activate
```

Linux/macOS:
```bash
source .venv/bin/activate
```

Install dependencies:
```bash
pip install -r requirements.txt
```

Start the API:
```bash
python app.py
```

The API will run at:
`http://localhost:5000`

### Frontend
Open `frontend/index.html` in a browser after starting the backend.

For a local static server, from `frontend/` run:
```bash
python -m http.server 5500
```
Then open:
`http://localhost:5500`

## 7. API Endpoints

### Health
`GET /api/health`

### Dataset
`GET /api/dataset?limit=20`

### Congestion Prediction
`POST /api/predict`

Example JSON:
```json
{
  "road_segment_id": 1,
  "hour": 18,
  "day_of_week": 2,
  "speed": 30,
  "volume": 900
}
```

### Smart Route
`POST /api/route`

Example JSON:
```json
{
  "source": "A",
  "target": "F",
  "hour": 18,
  "day_of_week": 2
}
```

## 8. Demonstration Flow
1. Start the Flask backend.
2. Open the frontend.
3. Confirm "Backend connected".
4. Enter traffic conditions and click **Predict Congestion**.
5. Select source and destination and click **Recommend Smart Route**.
6. Load the dataset preview.
7. Run `backend/algorithm.py` separately when execution evidence/model metrics are required.

## 9. Academic Reporting
Do not copy demonstration metrics as final experimental results. Report the accuracy, F1 score, confusion matrix, route costs, and travel-time savings produced after running the approved final dataset.

## 10. Repository Structure
```text
Intelligent_Traffic_Congestion_Project_FullStack/
├── frontend/
│   ├── index.html
│   ├── style.css
│   ├── app.js
│   └── README.md
├── backend/
│   ├── app.py
│   ├── algorithm.py
│   └── requirements.txt
├── data/
│   └── traffic_dataset.csv
├── outputs/
│   └── .gitkeep
├── .gitignore
└── README.md
```
