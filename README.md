# ML Model Dashboard

A modern web dashboard for visualizing machine learning model performance and metrics. This application consists of a Flask backend API that serves ML model artifacts and a responsive frontend dashboard for data visualization.

## Features

- **Model Overview**: Display key model information (algorithm, accuracy, dataset size, features)
- **Performance Metrics**: Show precision, recall, and F1-score for classification models
- **Confusion Matrix**: Visual representation of prediction accuracy
- **Interactive Charts**: Performance comparisons and prediction distributions
- **Predictions Table**: Sample predictions with actual vs predicted values
- **Real-time Data**: Refresh functionality to update dashboard data

## Project Structure

```
pert6/
├── backend/
│   └── app.py              # Flask API server
├── dashboard/
│   ├── index.html          # Main dashboard HTML
│   ├── styles.css          # Modern CSS styling
│   └── script.js           # Frontend JavaScript
├── artifacts/
│   └── model_results.json  # ML model artifacts data
├── requirements.txt        # Python dependencies
└── README.md              # This file
```

## Setup and Installation

### 1. Install Dependencies

Make sure you have Python 3.7+ installed, then install the required packages:

```bash
pip install -r requirements.txt
```

The requirements include:
- Flask (web framework)
- Flask-CORS (cross-origin requests)
- pandas, numpy, scikit-learn (ML dependencies)

### 2. Start the Backend API

Navigate to the project directory and run:

```bash
python backend/app.py
```

The API server will start at `http://localhost:5000` with the following endpoints:

- `GET /api/health` - Health check
- `GET /api/model/info` - Basic model information
- `GET /api/model/predictions` - Prediction data
- `GET /api/model/evaluation` - Evaluation metrics
- `GET /api/model/metrics/summary` - Summarized metrics for dashboard
- `GET /api/model/all` - All model data

### 3. Open the Frontend Dashboard

Open the `dashboard/index.html` file in your web browser, or serve it using a local web server:

```bash
# Using Python's built-in server
cd dashboard
python -m http.server 8000
```

Then visit `http://localhost:8000` in your browser.

## API Endpoints

### Model Information
```
GET /api/model/info
```
Returns basic model information including algorithm, accuracy, data shape, and feature count.

### Predictions Data
```
GET /api/model/predictions
```
Returns formatted prediction data with predicted vs actual values and correctness indicators.

### Evaluation Metrics
```
GET /api/model/evaluation
```
Returns detailed evaluation metrics including classification report and confusion matrix.

### Metrics Summary
```
GET /api/model/metrics/summary
```
Returns a comprehensive summary optimized for dashboard visualization.

## Dashboard Features

### Model Overview Cards
- **Accuracy**: Overall model performance percentage
- **Algorithm**: Type of ML algorithm used
- **Dataset Size**: Number of training samples
- **Features**: Number of input variables

### Performance Metrics
- Precision, Recall, and F1-Score for each class
- Weighted averages for overall performance
- Visual confusion matrix

### Data Visualizations
- **Performance Chart**: Bar chart comparing metrics across classes
- **Prediction Results**: Doughnut chart showing correct vs incorrect predictions

### Predictions Table
- Sample of first 10 predictions
- Shows predicted vs actual values
- Color-coded correctness indicators

## Model Data Format

The application expects model artifacts in JSON format (`artifacts/model_results.json`) with the following structure:

```json
{
  "model_info": {
    "algorithm": "Random Forest",
    "accuracy": 0.929,
    "data_shape": [45000, 14],
    "features_count": 13
  },
  "predictions": {
    "predicted_values": [0.0, 1.0, ...],
    "actual_values": [0.0, 1.0, ...],
    "total_predictions": 9000
  },
  "evaluation": {
    "accuracy_score": 0.929,
    "classification_report": { ... },
    "confusion_matrix": [[6796, 194], [444, 1566]]
  }
}
```

## Technology Stack

### Backend
- **Flask**: Python web framework
- **Flask-CORS**: Cross-origin resource sharing
- **JSON**: Data serialization

### Frontend
- **HTML5**: Semantic markup
- **CSS3**: Modern styling with Grid and Flexbox
- **JavaScript (ES6+)**: Interactive functionality
- **Chart.js**: Data visualization library
- **Font Awesome**: Icons
- **Google Fonts (Inter)**: Typography

## Browser Support

The dashboard is compatible with modern browsers:
- Chrome 70+
- Firefox 63+
- Safari 12+
- Edge 79+

## Customization

### Adding New Metrics
1. Update the backend API to include new metrics in the summary endpoint
2. Add corresponding UI elements in `dashboard/index.html`
3. Update the JavaScript in `dashboard/script.js` to handle new data

### Styling Changes
Modify `dashboard/styles.css` to customize:
- Color scheme (CSS custom properties at the top)
- Layout and spacing
- Typography and fonts
- Responsive breakpoints

### Chart Modifications
Update chart configurations in `dashboard/script.js`:
- Change chart types (bar, line, pie, etc.)
- Modify colors and styling
- Add new chart types for additional visualizations

## Troubleshooting

### Backend Issues
- Ensure all dependencies are installed: `pip install -r requirements.txt`
- Check that the artifacts file exists: `artifacts/model_results.json`
- Verify the Flask server is running on port 5000

### Frontend Issues
- Check browser console for JavaScript errors
- Ensure the backend API is accessible at `http://localhost:5000`
- Verify CORS is properly configured

### Data Issues
- Validate JSON format in `model_results.json`
- Check that all required fields are present
- Ensure numeric values are properly formatted

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## License

This project is open source and available under the MIT License.
