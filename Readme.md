# Simple example of containerizing ML models wrapped in Flask 
# Deployment of ML models using Python's Scikit-Learn + Flask + Docker by CWallaceh

1. git clone https://github.com/cwallaceh/sklearn_flask_docker.git
     and cd into sklearn_flask_docker directory

# Install required python packages
2. pip3 install -r requirements.txt

# Train the Model locally: python code/train.py or specify your python version
3.  pytho3 code/train.py

# Launch Flask Server to Run App: Add the endpoints specified in app.py to check the it works in a browser
4. flask run -p 5000

# Stop Flask API Server
5. Ctrl+C


# But before that make sure that the Docker Daemon is running on your MAC first:
   open -a Docker
# Link your docker registry aka DockerHub to the Docker desktop using usrname & passwd
   docker ps

# Build a docker image of the flask api app using the instructions in the Dockerfile
6. docker build . -t from_ds_to_mlops

# Run the docker image 
7. docker run -p 8000:8000 from_ds_to_mlops

# Interact with API over http on the endpoint /health by sending GET request using curl command
8. `curl -X GET http://localhost:8000/health`

# Interact with API over http on the endpoint /info by sending GET request using curl command
9. `curl -X GET http://localhost:8000/info`

# Interact with API over http on the endpoint /predict by sending statistics about a cell in the form of json file, and the model will output a prediction of whether it's cancer or not.
10. `curl -d '[{"radius_mean": 17.99, "texture_mean": 10.38, "perimeter_mean": 122.8, "area_mean": 1001.0, "smoothness_mean": 0.1184, "compactness_mean": 0.2776, "concavity_mean": 0.3001, "concave points_mean": 0.1471, "symmetry_mean": 0.2419, "fractal_dimension_mean": 0.07871, "radius_se": 1.095, "texture_se": 0.9053, "perimeter_se": 8.589, "area_se": 153.4, "smoothness_se": 0.006399, "compactness_se": 0.04904, "concavity_se": 0.05373, "concave points_se": 0.01587, "symmetry_se": 0.03003, "fractal_dimension_se": 0.006193, "radius_worst": 25.38, "texture_worst": 17.33, "perimeter_worst": 184.6, "area_worst": 2019.0, "smoothness_worst": 0.1622, "compactness_worst": 0.6656, "concavity_worst": 0.7119, "concave points_worst": 0.2654, "symmetry_worst": 0.4601, "fractal_dimension_worst": 0.1189}]' \
     -H "Content-Type: application/json" \
     -X POST http://0.0.0.0:8000/predict`



Detailed instructions:
https://github.com/cwallaceh/sklearn_flask_docker