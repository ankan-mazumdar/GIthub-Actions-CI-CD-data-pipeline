### Automating Data Pipelines with Python & GitHub Actions

![image](https://github.com/user-attachments/assets/5fdbe965-55bc-49db-812e-bb6741f4189e)

![image](https://github.com/user-attachments/assets/6264087c-f6b8-4254-ba4d-4b5a0ea09b03)


## The project covers:

Creating and managing workflows with GitHub Actions which provides
• Free compute envt and resources for actions on public repos.
• Simple config et up using 
.yml file.
Automating tasks such as data extraction, processing, and transformation.
Scheduling jobs with cron expressions in GitHub Actions.
Implementing Python scripts to automate data-related tasks.

![image](https://github.com/user-attachments/assets/4ce14483-ab55-4093-9f75-f132a3972583)

![image](https://github.com/user-attachments/assets/10fe3cd6-57a2-4267-b048-5b8f9fa93077)


### Project Setup
## 1. Repository Initialization
Create a new repository in GitHub for your data pipeline project.
Clone the repository to your local machine.
## 2. Directory Structure
Set up your project directory with the following structure:

```
/<repository-root>
│
├── .github/
│   └── workflows/
│       └── data-pipeline.yml
│
├── scripts/
│   └── data_pipeline.py
│
└── .gitignore
```

## 3. Python Environment Setup
Initialize a Python environment:

```
python -m venv venv
source venv/bin/activate  # For Linux/MacOS
.\venv\Scripts\activate  # For Windows
```
Install the necessary libraries:

```
pip install -r requirements.txt
Define environment variables required for the scripts.
```

## GitHub Actions Setup
1. Creating a Workflow
create the .github/workflows/data-pipeline.yml file.
![image](https://github.com/user-attachments/assets/7e257038-b3ef-4822-b0fa-5204481dfd21)

Define the workflow with the following key elements:

```
name: Data Pipeline Automation

on:
  schedule:
    - cron: '35 0 * * *'  # Runs at 00:35 daily

jobs:
  pipeline:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v2

      - name: Set up Python
        uses: actions/setup-python@v2
        with:
          python-version: 3.x

      - name: Install dependencies
        run: |
          python -m pip install --upgrade pip
          pip install -r requirements.txt

      - name: Run data pipeline
        run: |
          python scripts/data_pipeline.py
```

## 2. Repository Secrets
Configure secrets in the repository settings if pipeline requires sensitive information like API keys.
![image](https://github.com/user-attachments/assets/ccc2f61e-1572-412e-9a0a-c7aa342d89c7)
![image](https://github.com/user-attachments/assets/d5a100b5-dcc4-4d8e-9a38-01b90af79f3d)

![image](https://github.com/user-attachments/assets/f4baee6a-9cf1-4c05-9d6b-8ef62062d274)


## 4. Workflow Triggers
We will use a cron job to schedule the pipeline to run daily at 00:35.

Python Script Implementation
1. Creating the Data Pipeline Script
In the scripts directory, create the data_pipeline.py file.

Implement the pipeline logic.
This script can be expanded to include various data pipeline steps, such as extracting video IDs from YouTube, processing video transcripts, cleaning data, and creating text embeddings.

## Running the Pipeline
1. Commit and Push Changes
Stage, commit, and push the changes to GitHub:

```
git add .
git commit -m "Initial pipeline setup"
git push origin main
```

## 2. Monitor Workflow Execution
   
![image](https://github.com/user-attachments/assets/33135022-b785-43a0-8237-c03a1d51cb90)

After pushing, the workflow should trigger automatically based on the defined schedule or on a manual trigger.
Check the Actions tab in your GitHub repository to monitor the workflow's progress.
Monitoring and Debugging
Workflow Logs: Monitor the execution logs in the GitHub Actions interface.
Error Handling: If errors occur, the logs will provide details to help you debug.
