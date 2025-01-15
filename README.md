# 30 Days DevOps Challenge - Weather Dashboard

## Day 1: Building a Weather Data Collection System with AWS S3 and OpenWeather API

## Project Overview
This project is a Weather Data Collection System that demonstrates core DevOps principles by combining:
- External API Integration (OpenWeather API)
- Cloud Storage (AWS S3)
- Infrastructure as Code
- Version Control (Git)
- Python Development
- Error Handling
- Environment Management

## Features
- Fetches real-time weather data for multiple cities
- Displays temperature (°F), humidity, and weather conditions
- Automatically stores weather data in AWS S3
- Supports multiple cities tracking
- Timestamps all data for historical tracking

## Technical Architecture
- **Language:** Python 3.x
- **Cloud Provider:** AWS (S3)
- **External API:** OpenWeather API
- **Dependencies:** 
  - boto3 (AWS SDK)
  - python-dotenv
  - requests

## Project Structure

```markdown
weather-dashboard/
  src/
    __init__.py
    weather_dashboard.py
  tests/
  data/
  .env
  .gitignore
  requirements.txt
```
## Prerequisites
Ensure the following tools and credentials are set up on your local machine before proceeding:

 - **VS Code Editor** you can see documentation [here](https://code.visualstudio.com/download)

- **AWS CLI** you can see documentation [here](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)

- **AWS Account:** Access credentials with sufficient permissions to interact with S3.

- **OpenWeather API Key:** Generate an API key by signing up at OpenWeather API.
  
## Setup Instructions

1. Clone the repository:
  ```
  git clone https://github.com/ShaeInTheCloud/30days-weather-dashboard.git

  ```

2. Create a Virtual Environment

 Before proceeding with the installation, it’s highly recommended to create a virtual environment for Python. This ensures that your package dependencies are isolated from the global environment. The installation might fail if the package is managed externally (e.g., through `apt`). By isolating the environment, you can safely install and manage the required dependencies without interference.

Then you have to activate the virtual environment 
    ```
    source envname/bin/activate
    ```

  To do this:

  To create a virtual environment 

  ```
    python3 -m venv (your virtual environment name)
  ```

3. Install dependencies

   ```
   pip install -r requirements.txt
   ```

4. Configure environment variables (.env):
```
CopyOPENWEATHER_API_KEY=your_api_key
AWS_BUCKET_NAME=your_bucket_name
```

4.Configure AWS credentials:
```
aws configure

```
5.Run the Application
Execute the Python script to fetch and upload weather data:


   ``` 
   python src/weather_dashboard.py
   ```


## What I Learned
Working on this project helped me gain hands-on experience with:

- AWS S3: Creating and managing buckets.
- Environment Variable Management: Securing sensitive API keys.
- Python Best Practices: Writing clean, modular, and reusable code for API integration.
- Git Workflow: Using version control effectively for project development.
- Error Handling: Managing failures in distributed systems gracefully.
- Cloud Resource Management: Leveraging cloud services efficiently.

## Future Enhancements
- Add weather forecasting functionality.
- Implement data visualization for weather trends.
- Expand the city tracking feature.
- Create automated testing for better reliability.
- Set up a CI/CD pipeline for streamlined deployments.

## Connect and Collaborate
This project is a part of my **30 Days DevOps Challenge**. Feedback and suggestions are welcome!
Feel free to fork the repository, submit pull requests, or reach out for collaboration.
