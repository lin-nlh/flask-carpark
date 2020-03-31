# Flask Carpark

Carpark monitoring system

## Requirements
```
Flask
Flask-Migrate
Flask-SocketIO
Flask-SQLAlchemy
eventlet
psycopg2
gunicorn
python-dotenv
paho-mqtt
SQLAlchemy
```

## Installation

```
# This step is optional if you're not prefered virtualenv
$ python3 -m pip install virtualenv # in case you don't have
$ python3 -m virtualenv --python=python3 venv
$ sourve venv

# Start here
(venv) $ git clone https://github.com/phondanai/flask-carpark
(venv) $ cd flask-carpark
(venv) $ pip install -r requirements.txt
(venv) $ flask db upgrade
```

## Configuration
Create `.env` file and create your own configuration
```
SECRET_KEY="youneverknow"
SQLALCHEMY_DATABASE_URI=""
MQTT_BROKER_URL="mqtt.netpie.io"
MQTT_BROKER_PORT=1883
MQTT_CLIENT_ID="your mqtt client id"
MQTT_TOKEN="your mqtt token"
```

## Run
```
(venv) $ gunicorn --worker-class eventlet -w 1 application:app
```

## Running test
```
$ python tests.py
```

## Deploy
You need [Heroku Postgres](https://elements.heroku.com/addons/heroku-postgresql).
And config your environment variable according to your `.env` file.
```
$ heroku config:set SECRET_KEY="youneverknow"
$ heroku config:set MQTT_BROKER_URL="mqtt.netpie.io"
$ # ... and so on
```

Then deploy
```
$ git push heroku master
```

## Data Analytic Testcase

Test case: Check_Generated_Data-001
Description: Check whether the generated data is exist or can be download and readable from data source. 

Prerequisites: 
      1. User Authorization
      2. Web-page Avaliable 

Test Procedure:
      1. Enter website 
      2. Show report data

Test data: Generated Data from database 

Expected results:The report of data should be appeared in web page 

Actual result: -

**************************************************************************************************************

Test case: Test_Format-001

Description:Validation of the data type,data length and schema format associated with this format

---------------------------------------------------------
           |               |                 |             
Floor_Slot |	Status       |	YYYY-MM-DD     |	  Time
-----------|---------------|-----------------|-----------
F3_22	     |   Occupied	   |  1/12/2020      |	 9:58:00
F2_10	     |   Available   |	1/13/2020      |	10:58:00
  
Prerequisites:
        1. User Authorization
        2. Web-page Avaliable

Test Procedure:
        1.Enter website
        2.Query data from website
        3.Validate format and data type whether they are correctly mapped or compatible with the specified format.

Test data: Generated Data from database 

Expected results the data type and format of table should compatible with the format 

Actual result: -

*************************************************************************************************************


# Cloud and Server Test Case

## Test Case: 
      Server Test

## Description: 
      To have the data from the device for observing pattern on cloud server and export that data as csv file

## Procedure: 
      (1) To subscribe the MQTT Broker (netpie.io) to know the information of parking slot availability 
      (2) Export data as csv file for data analysis part.
 
 ## Test Data: 
      Raw data 3x25 = 75 slots
      Storage require/1 year 700MB (Raw) & 50 MB (compressed)
 
 ## Expected Results:
      .csv file of observing pattern (daily/weekly/yearly) for data analytic part
      
