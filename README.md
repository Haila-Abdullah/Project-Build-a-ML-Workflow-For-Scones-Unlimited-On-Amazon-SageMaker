# Build a Machine Learning Workflow for Scones Unlimited on Amazon SageMaker

## Project Overview

This project demonstrates how to build a complete machine learning pipeline for **Scones Unlimited**, a scone delivery company, using AWS SageMaker and other AWS services. The goal is to create an image classification model that can distinguish between delivery vehicle types (bicycles vs. motorcycles) to improve logistics and routing.

The workflow includes:

- Data preparation and staging  
- Model training and deployment using SageMaker  
- Supporting Lambda functions for preprocessing, inference, and filtering  
- A Step Function to orchestrate the entire flow  
- Basic model monitoring and visualization

---

## Background

Image classification is a common computer vision task used in industries like autonomous vehicles, ecommerce, and healthcare. For Scones Unlimited, the model helps identify delivery vehicles from images to better route drivers and optimize operations.

---

## Project Steps

### Step 1: Data Staging  
- Prepared a dataset of bicycle and motorcycle images.  
- Uploaded data to Amazon S3 for training.

### Step 2: Model Training & Deployment  
- Trained an image classification model using SageMaker.  
- Deployed the model as a real-time inference endpoint.

### Step 3: Lambdas and Step Function  
- Created three AWS Lambda functions:  
  1. **serialize_image_data** – retrieves the image from S3 and encodes it.  
  2. **image_classification** – calls the SageMaker endpoint for predictions.  
  3. **filter_low_confidence** – checks if the inference confidence meets a threshold.  
- Linked the Lambdas using AWS Step Functions to build an automated inference pipeline.

### Step 4: Testing & Evaluation  
- Tested the Step Function with sample input images.  
- Verified correct prediction and Step Function flow.

### Step 6: Resource Cleanup  
- Deleted unused AWS resources to avoid unnecessary charges.

---

## Architecture Diagram

![Step Functions Workflow](step%20functions%20graph%201.png)

---

## How to Use

1. **Set up AWS Environment**  
   - Launch SageMaker Studio and create a user with full SageMaker and Lambda permissions.  
   - Upload image data to S3.

2. **Train & Deploy the Model**  
   - Run the provided Jupyter notebook to preprocess data, train the model, and deploy the endpoint.

3. **Deploy Lambda Functions**  
   - Create and deploy three Lambda functions (`serialize_image_data`, `image_classification`, `filter_low_confidence`) with appropriate IAM roles.

4. **Create the Step Function**  
   - Use the `MyStateMachine.asl.json` file to define the Step Function visually.  
   - Assign an IAM role that allows calling Lambda functions.

5. **Run the Workflow**  
   - Trigger the Step Function using test input (S3 bucket/key).  
   - Monitor execution via AWS Step Functions Console.

---

## Project Files

- `MyStateMachine.asl.json` — Step Function definition  
- `Project_Build_a_ML_Workflow_For_Scones_Unlimited_On_Amazon_SageMaker.ipynb` — Jupyter notebook for training and deployment  
- `lambda.py` — Contains all three Lambda functions  
- `step functions graph 1.png` — Screenshot of the working Step Function  
- `step functions graph 2.png` — Screenshot of the working Step Function
- `README.md` — This file

---

## Lessons Learned

- How to train and deploy machine learning models using AWS SageMaker  
- Serverless workflow design using AWS Lambda and Step Functions  
- Error handling and state management in asynchronous ML workflows  
- Setting inference confidence thresholds for safety  
- Leveraging AWS services to build scalable and production-ready ML solutions
