### 🚕 TaxiFare Prediction with TensorFlow & Vertex AI

This project uses Google Cloud's Vertex AI to build, train, and deploy a DNN model for NYC taxi fare prediction. It leverages features from trip coordinates, distance, and passenger count, with an end-to-end pipeline from BigQuery to Vertex AI for real-time inference.

## ⚙️ Architecture

The project architecture involves:

1.  BigQuery for data storage.
2.  Exporting data to GCS for training.
3.  Containerizing training code with Docker.
4.  Using Vertex AI for training and model deployment.

<p align="center">
  <img src="Architecture.png" alt="Architecture Diagram" width="500">
</p>

## 📊 Dataset

The NYC Taxi Fare dataset in GCS includes: pickup/drop-off coordinates, datetime, passenger count, and fare amount.

## 🧪 Feature Engineering

Key techniques include:

* Scaling latitude/longitude.
* Calculating Euclidean distance.
* Bucketization of coordinates.
* Feature crossing with `HashedCrossing`.
* Embedding high-cardinality crossed features.

## 🧠 Model Architecture

TensorFlow model: `Input → Feature Transform → Concatenate → Dense Layers → Output (Fare)`

## 🚀 Deployment

The trained `SavedModel` is deployed on **Google Vertex AI** via a Vertex AI Endpoint for scalable real-time predictions accessible through REST API or the SDK.