### 🚕 TaxiFare Prediction with TensorFlow & Vertex AI 

This project builds and **deploys** a Deep Neural Network (DNN) model to predict New York City taxi fares using pickup/drop-off coordinates, distance, and passenger count. It includes end-to-end preprocessing, training, and **deployment on Google Cloud Vertex AI** for real-time inference.

## 📊 Dataset

NYC Taxi Fare dataset available on Google Cloud Storage (GCS), containing fields like:
- Pickup and drop-off latitude/longitude  
- Datetime of trip  
- Passenger count  
- Fare amount (target)

## 🧪 Feature Engineering

### ✅ Scaling  
- Longitude scaled from `[-78, -70]` to `[0, 1]`  
- Latitude scaled from `[37, 45]` to `[0, 1]`  

### 📏 Distance Calculation  
- Euclidean distance computed from pickup to drop-off coordinates.  

### 🗺️ Bucketization  
- Discretization of scaled latitude and longitude into spatial bins.  

### ✖️ Feature Crossing  
- Pickup and drop-off location crosses using `HashedCrossing`  
- `pickup_cross dropoff → embedding → flatten`  

### 🔎 Embedding  
- High-cardinality hashed crosses are converted into low-dimensional dense representations (10D vectors).  

## 🧠 Model Architecture

```text
Input → Feature Transform (Lambda, Discretization, HashedCrossing, Embedding) → Concatenate → Dense Layers → Output (Fare)
```

## 🚀 Deployment

The model is exported in `SavedModel` format and deployed on **Google Vertex AI**:
- Model uploaded to Google Cloud Storage (GCS)
- Served using Vertex AI endpoint for scalable, real-time predictions
- Easily accessible via REST API or SDK

