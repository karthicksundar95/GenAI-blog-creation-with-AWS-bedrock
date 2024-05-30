# GenAI-blog-creation-with-AWS-bedrock
(On AWS cloud) API creation to generate blogs using Llama model using AWS bedrock, API gateway , S3 and AWS lambda servies
This project demonstrates how to create an API service on AWS that triggers a Lambda function, which in turn uses AWS Bedrock's Llama 2 model to generate blog content. The generated content is then saved in AWS S3.

## Table of Contents
- [Overview](#overview)
- [Architecture](#architecture)
- [Components](#components)
  - [AWS Bedrock](#aws-bedrock)
  - [AWS Lambda](#aws-lambda)
  - [AWS API Gateway](#aws-api-gateway)
  - [AWS S3](#aws-s3)
- [Setup Instructions](#setup-instructions)
  - [Creating the Lambda Function](#creating-the-lambda-function)
  - [Setting Up API Gateway](#setting-up-api-gateway)
  - [Configuring AWS Bedrock](#configuring-aws-bedrock)
  - [Deploying and Testing](#deploying-and-testing)
- [Monitoring](#monitoring)
- [Pricing](#pricing)
- [License](#license)

## Overview

This project uses several AWS services to create a scalable and efficient blog content generation service. A user can send a blog topic via an API request, which triggers a Lambda function. This function queries AWS Bedrock's Llama 2 model to generate a 100-word blog post. The result is then saved to an AWS S3 bucket for storage and retrieval.

## Architecture

1. **API Request**: User sends a blog topic to the API Gateway.
2. **Lambda Trigger**: API Gateway triggers an AWS Lambda function.
3. **Content Generation**: Lambda function queries AWS Bedrock using the Llama 2 model.
4. **Storage**: Generated content is stored in an AWS S3 bucket.
5. **Response**: The API returns a confirmation and the location of the stored content.

## Components

### AWS Bedrock

- **Service**: Hosts Generative AI "Foundational Models".
- **Access**: Provides an API endpoint for invoking models and getting results.
- **Pricing**: Pay-as-you-go based on the number of requests.

### AWS Lambda

- **Function**: Write and paste your code in the function section.
- **Layer**: Upload all dependency packages as a zip file under the "Layers" section.
- **Trigger**: Add an API Gateway trigger.
- **Deploy**: Deploy the code (re-deploy after each code change).
- **Policy**: Attach necessary policies in the `Configuration -> Permissions -> {rolename}` section.
- **Monitor**: View logs in CloudWatch (logs may take 30-60 seconds to reflect).

### AWS API Gateway

- **API Creation**: Create an API with a unique name.
- **Routes**: Define routes (POST/GET) and name the API endpoints.
- **Integration**: Attach the Lambda function to the API.
- **Stages**: Create and deploy stages (dev/test/prod).
- **Deploy**: Deploy the API to the specified stage.

### AWS S3

- **Storage**: Used to store the generated blog content.
- **Access**: Secure access to stored content.

## Setup Instructions

### Creating the Lambda Function

1. Go to AWS Lambda and create a new function.
2. Paste your code in the function code section.
3. Create a layer with all necessary dependencies and attach it to your function.
4. Configure a trigger for the function from the API Gateway.

### Setting Up API Gateway

1. Create a new API in API Gateway.
2. Define the routes (e.g., POST /generateBlog).
3. Integrate the API with your Lambda function.
4. Create and deploy stages (e.g., dev, test, prod).

### Configuring AWS Bedrock

1. Access AWS Bedrock and configure the Llama 2 model.
2. Obtain the API endpoint and necessary credentials.
3. Use this endpoint in your Lambda function to generate content.

### Deploying and Testing

1. Deploy your Lambda function and API Gateway.
2. Test the API by sending a POST request with a blog topic.
3. Verify the generated content is stored in S3.

## Monitoring

- Use AWS CloudWatch to monitor logs and performance metrics.
- Logs can be accessed via the Lambda console under the Monitoring tab.

## Pricing

- **AWS Bedrock**: Charges based on the number of requests.
- **AWS Lambda**: Pay for compute time used.
- **AWS API Gateway**: Charges based on the number of API calls.
- **AWS S3**: Storage costs based on the amount of data stored and data transfer.

## License

This project is licensed under the MIT License.
