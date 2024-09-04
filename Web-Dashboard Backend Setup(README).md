# Inteliforz Web-Dashboard Backend Setup

## Clone the Repository

To clone the repository, use the following URL:
```bash
https://git-codecommit.us-east-1.amazonaws.com/v1/repos/ansell-api

```
Make sure to have the required AWS CodeCommit credentials for cloning.

## Install Dependencies

#### Step 1: Install dotenv
Install the dotenv package using npm:
```bash
npm install dotenv

```

#### Step 2: Create the Environment File
Create a file named .env.dev in the root directory of your project and add the following environment variables to it:

#### Environment variables
```
ACCESS_KEY_ID=AKIA33HVY2XR36WKN5WG
AWS_REGION=us-east-1
BULK_OPER=https://sqs.us-east-1.amazonaws.com/814411732451/dev-BulkOperations
CERT_BUCKET=ansell-dev-glove-device-certs
CLOUDFRONT_URL=https://de6g279kdomxq.cloudfront.net
COUCH_DB_CONSIDER_DATE=2024-06-15
COUCH_DB_DAILY_METRIC_NAME=dev-daily-metricbasics
COUCH_DB_METRIC_NAME=dev-metricbasics-v2
COUCH_DB_URL=http://webapp:Web987!@localhost:5000
CTSD_REPORTS_BUCKET=ansell-glove-ctsd-report-dev
DB_AUTHDB=admin
DB_CUPID=us-east-1_LaB3PJBcd
DB_HOST=mongodb://localhost:6000/
DB_NAME=user-management-dev
DB_PASSWORD=UP9bs5XxLnd3AsWU
DB_USER=dbAdmin
DEVICE_CERTS_DYNAMO_TABLE_NAME=dev-glove-device-create-history
DYNAMO_TABLE_NAME=modjoul-api-v2-endpoint-logs-dev
EMAIL_SNS=arn:aws:sns:us-east-1:814411732451:ap-dev-jit-notification
GLOVE_ARTIFACT_BUCKET_KEY=glove_bulk-user-creation-dev/
GLOVE_ARTIFACT_BUCKET_NAME=ansell-dev-temp-artifacts
GLOVE_CERT_CHANGE_STEP_MACHINE_ARN=arn:aws:states:us-east-1:814411732451:stateMachine:dev-glove-cert-change
GLOVE_DEVICE_BATTERY_LEVEL_ELIGIBLE_MARGIN=75
GLOVE_DEVICE_CREATION_S3_BUCKET=ansell-dev-temp-artifacts
GLOVE_DEVICE_HEALTH_REPORTED_TIME_FACTOR_MINUTES=10000
GLOVE_DEVICE_MEMORY_ELIGIBLE_MARGIN=10
GLOVE_KMS_ENCRYPT_KEY=08897976-bd7e-4b4a-b8bb-52a94fe3345d
IMG_LOGO_BUCKET_NAME=ansell-profile-img
IOT_DATA_ENDPOINT=a3p6iuua1kr60v-ats.iot.us-east-1.amazonaws.com
METRIC_ALL_DATA_CSV_BUCKET=ansell-dev-ansell-metric-all-data-csv
MONGO_DB_URI=mongodb://dbAdmin:UP9bs5XxLnd3AsWU@localhost:6000/user-management-dev?authSource=admin&readPreference=primary&appname=MongoDB%20Compass&ssl=false
NODE_ENV=development
PRODUCT_ENV=dev
PRODUCT_NAME=glove
REDIS_CLUSTER_HOST=workforce-test-redis-ro.rnpitr.ng.0001.use1.cache.amazonaws.com
REDIS_CLUSTER_PORT=6379
REGION=us-east-1
REPORT_BUCKET=ansell-dev-reports
SECRET_ACCESS_KEY=Hw4n1qsdLcC9hXlXlow9Jjtd3sdEeBpGW/c462zL
STRIPE_KEY=sk_test_51HNI1IBFJXzQUvJHMI6AOxeMUnl3yZd2X6spiE6tXYoM1x4HXM3kPnNxDWDtkUeHJLULdLTaVKchPynvuDvafTTl00n6h0yck1
THING_GROUP=Glove-Dev-Group
THING_GROUP_ARN=arn:aws:iot:us-east-1:814411732451:thinggroup/Glove-Dev-Group
TOPIC_DEVICE_NAME=dev-iot-2
USER_CREATION_SQS=https://sqs.us-east-1.amazonaws.com/814411732451/devUserBulkCreationGlove
VERSION=v2023.12.19

```

#### Step 3: Configure dotenv in index.js
In your index.js file, configure dotenv to load environment variables from the .env.dev file:

```bash
require('dotenv').config({ path: '.env.dev' });

```

#### Step 4: Download the PEM File 
Download the PEM file (ansell-dev-nix-jump.pem) and place it in your backend directory. Ensure the path to the PEM file is correct when running the MongoDB and CouchDB connection commands.

PEM File download Link: [PEM file](https://guvvala.sharepoint.com/:u:/s/AnsellInteliforzProject/EYR5u42nU6lHsq9Z46SsB0QBudaaCOCeg2hpldtNiOqUZg?e=MPeUmY)


#### Step 5: Run MongoDB & CouchDB Commands 
To connect to the DEV Jump server for MongoDB and CouchDB, run the following SSH commands in different command prompts. Replace path/to/ansell-dev-nix-jump.pem with the actual path to your PEM file.

#### MongoDB Connection Command:
```bash
ssh -N -i path/to/ansell-dev-nix-jump.pem -L 6000:ip-10-50-3-71.ec2.internal:27017 ec2-user@ec2-3-229-172-189.compute-1.amazonaws.com

```

#### CouchDB Connection Command:
```bash
ssh -N -i path/to/ansell-dev-nix-jump.pem -L 5000:ip-10-50-3-71.ec2.internal:5984 ec2-user@ec2-3-229-172-189.compute-1.amazonaws.com

```

#### Step 6: Run the Server
To start the server, use the following npm command:
```bash
npm run start

```

#### Run CouchDB in Local

Access CouchDB locally at : (http://localhost:5000/_utils/#/database/dev-metricbasics-v2/_design/metricCollection/_view/timeSeries)

- Username: webapp
- Password: Web987!

#### MongoDB DEV URL:

```
mongodb://dbAdmin:UP9bs5XxLnd3AsWU@localhost:6000/user-management-dev?authSource=admin&readPreference=primary&appname=MongoDB%20Compass&ssl=false 

```
