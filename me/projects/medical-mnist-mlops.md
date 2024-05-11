---
description: >-
  This project embodies a resilient pipeline harmonizing continuous training and
  deployment principles, guided by MLOps methodologies. Leveraging a Streamlit
  frontend, users seamlessly upload medical MN
layout:
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: false
---

# 🩺 Medical MNIST MLOPs

### Streamlit  Frontend

{% embed url="https://medical-mnist.streamlit.app/" %}

### Pipeline Architecture

<figure><img src="../../.gitbook/assets/Medical MNIST CT CD - Imgur.png" alt=""><figcaption><p>Architecture</p></figcaption></figure>

1. **User Interaction:**
   * The pipeline begins with a Streamlit frontend, providing users with an intuitive interface to upload medical MNIST images for classification.
2. **Model Inference:**
   * Upon image upload, the pipeline fetches the latest trained model from the MLFlow model registry. This model is then used to make predictions on the uploaded images.
3. **Error Correction Mechanism:**
   * In case the prediction is incorrect, users have the option to provide the correct class label. If provided, the image along with the corrected label is stored in AWS S3 for future reference.
4. **Airflow DAG:**
   * Scheduled to run weekly, an Airflow Directed Acyclic Graph (DAG) automates the process of fetching new data from AWS S3 and retrieving the latest model from the MLFlow model registry.
5. **Model Retraining:**
   * Once the new data and model are fetched, the pipeline initiates the process of retraining the model on the updated dataset. This ensures that the model remains up-to-date and capable of making accurate predictions.
6. **Model Registry Update:**
   * Upon successful retraining, the newly trained model is uploaded to the MLFlow model registry, replacing the previous version. This ensures that the latest model is readily available for inference in subsequent interactions with the Streamlit frontend.
7. **Continuous Improvement:**
   * The iterative nature of the pipeline ensures continuous improvement in model performance over time as it adapts to new data and updates.

### Features

1. **Streamlit Frontend:** Users can upload medical MNIST images for classification.
2. **MLFlow Integration:** Models are fetched from the MLFlow model registry to make predictions.
3. **Correction Mechanism:** If the prediction is incorrect, users can provide the correct class label, and the image with the corrected class label will be uploaded to AWS S3.
4. **Airflow DAG:** Scheduled to run weekly, Airflow DAG fetches new data from AWS and the latest model from the MLFlow model registry, retrains the model on new data, and uploads the new model to the MLFlow registry.
5. **AWS S3 Integration:** Images with corrected labels are stored in AWS S3 for future reference and analysis.

### Airflow UI

<figure><img src="../../.gitbook/assets/Medical MNIST CT CD - Imgur (1).png" alt=""><figcaption><p>Airflow UI</p></figcaption></figure>

### Experiment Tracking

<figure><img src="../../.gitbook/assets/Medical MNIST CT CD - Imgur (2).png" alt=""><figcaption><p>MLflow</p></figcaption></figure>

### Streamlit Frontend

<figure><img src="../../.gitbook/assets/Medical MNIST CT CD - Imgur (3).png" alt=""><figcaption></figcaption></figure>
