# Google Cloud Fundamentals: Getting Started with App Engine

## Overview

In this lab, you create and deploy a simple App Engine application using a virtual environment in the Google Cloud Shell.

## Objectives

In this lab, you learn how to perform the following tasks:

    -   Initialize App Engine.

    -   Preview an App Engine application running locally in Cloud Shell.

    -   Deploy an App Engine application, so that others can reach it.

    -   Disable an App Engine application, when you no longer want it to be visible.

### Step 1:

### Confirm active account name on google cloud

`gcloud auth list`

### List project IDs

`gcloud config list project`

## Step 2:

Initialize your App Engine app with your project and choose its region:

`gcloud app create --project=$DEVSHELL_PROJECT_ID`

> When prompted, select the region where you want your App Engine application located.

Clone the source code repository for a sample application in the hello_world directory:

`git clone https://github.com/GoogleCloudPlatform/python-docs-samples`

Navigate to the source directory:

`cd python-docs-samples/appengine/standard_python3/hello_world`

## Step 3:

### Run Hello World application locally

Execute the following command to download and update the packages list.

`sudo apt-get update`

Set up a virtual environment in which you will run your application. Python virtual environments are used to isolate package installations from the system.

`sudo apt-get install virtualenv`

> If prompted [Y/n], press Y and then Enter.

`virtualenv -p python3 venv`

Activate the virtual environment.

`source venv/bin/activate`

Navigate to your project directory and install dependencies.

`pip install -r requirements.txt`

Run the application:

`python main.py`

> Please ignore the warning if any.

Verify that the app is not deployed. In the Cloud Console

`Click on this link (http://127.0.0.1:8080/)`

`gcloud app instances list`

## Step 4:

### Deploy and run Hello World on App Engine

Navigate to the source directory:

`cd ~/python-docs-samples/appengine/standard_python3/hello_world`

Deploy your Hello World application.

`gcloud app deploy`

> If prompted "Do you want to continue (Y/n)?", press Y and then Enter.

    This app deploy command uses the app.yaml file to identify project configuration.

Launch your browser to view the app at http://YOUR_PROJECT_ID.appspot.com

`gcloud app browse`

-   Copy and paste the URL into a new browser window.

`https://qwiklabs-gcp-00-04639c8d350b.uc.r.appspot.com`

## Step 5:

### Disable the application

`gcloud app versions stop VERSION_ID`

OR

Goto into **App Engine** > **Instances**
Select all the **instances** you want to **delete**
Click on **delete**
