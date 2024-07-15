# House Price Prediction

This project is a web application for predicting house prices based on various features such as the number of bedrooms, bathrooms, house size, and zip code. The application is built using Flask and a pre-trained Ridge regression model.

## Table of Contents
- [Installation](#installation)
- [Usage](#usage)
- [Model Training](#model-training)
- [Web Application](#web-application)
- [File Structure](#file-structure)
- [Contributing](#contributing)
- [License](#license)

## Supervised by
[Prof. Agughasi Victor Ikechukwu](https://github.com/Victor-Ikechukwu), (Assistant Professor) Department of CSE, MIT Mysore

## Collaborators
- 4MH21CS097 [Siri G](https://github.com/Siribug)
- 4MH21CS103 [Suhas K M](https://github.com/suhaskm28)
- 4MH21CS107 [Syed Furkhan Ahmed](https://github.com/)
- 4MH21CS112 [Thejas R](https://github.com/Thejuraj2003)

## Installation

### Prerequisites
- Python 3.x
- Flask
- Pandas
- Scikit-learn
- Pickle

### Steps
1. Clone the repository:
    ```bash
    https://github.com/jumaan1st/housepricepredict.git
    ```
2. Navigate to the project directory:
    ```bash
    cd house-price-prediction
    ```
3. Install the required packages:
    ```bash
    pip install -r requirements.txt
    ```

## Usage

1. Make sure your dataset (`final_dataset.csv`) and pre-trained model (`RidgeModel.pkl`) are in the project directory.

2. Run the Flask application:
    ```bash
    python app.py
    ```

3. Open your browser and go to `http://127.0.0.1:5000/` to access the web application.

4. Fill in the form with the required details (number of bedrooms, bathrooms, size, and zip code) and click the "Predict Price" button to get the predicted house price.

## Model Training

### Steps
1. Load your dataset:
    ```python
    import pandas as pd
    data = pd.read_csv('final_dataset.csv')
    ```

2. Split the data into features and target variable:
    ```python
    X = data[['beds', 'baths', 'size', 'zip_code']]
    y = data['price']
    ```

3. Split the data into training and testing sets:
    ```python
    from sklearn.model_selection import train_test_split
    X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=0)
    ```

4. Train the Ridge regression model:
    ```python
    from sklearn.linear_model import Ridge
    pipe = Ridge()
    pipe.fit(X_train, y_train)
    ```

5. Save the trained model:
    ```python
    import pickle
    pickle.dump(pipe, open('RidgeModel.pkl', 'wb'))
    ```

## Web Application

The web application is built using Flask. The main files are:

- `app.py`: The main Flask application file that handles routes and predictions.
- `templates/index.html`: The HTML template for the web application interface.
- `final_dataset.csv`: The dataset used for predictions.
- `RidgeModel.pkl`: The pre-trained Ridge regression model.

### Routes

- `/`: The home route that renders the main page with the form.
- `/predict`: The route that handles the prediction logic.

## File Structure

```
house-price-prediction/
│
├── app.py
├── final_dataset.csv
├── RidgeModel.pkl
├── requirements.txt
└── templates/
    └── index.html
```

## Contributing

Contributions are welcome! Please fork the repository and create a pull request with your changes.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

