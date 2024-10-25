
Please read the complete document

Step 1: Created Two S3 Buckets
    What I did: I created two S3 buckets:
    First bucket: Named it media-app-initial-image-1, where the original images will be uploaded.
    Second bucket: Named it media-app-resized-image-1, where the resized versions of the images will be stored.
    Folder structure: I created folders such as cover/, post/, and profile/ in both buckets to keep images organized.

Step 2: Created an SQS Queue
    What I did: I set up an SQS queue called media-app-queue-1. This queue will handle notifications triggered when images are uploaded to the media-app-initial-image-1 bucket.

Step 3: Edited the SQS Queue Access Policy
    What I did: I updated the access policy for the media-app-queue-1 SQS queue.
    Purpose: This allows the S3 bucket to send event notifications to the queue when new images are uploaded. Without this, the queue wouldn't be able to receive these notifications.

Step 4: Configured S3 Event Notifications
    What I did: I went to the media-app-initial-image-1 bucket settings and set up an event notification.
    Action: I configured it to send a message to the media-app-queue-1 SQS queue every time a new image is uploaded to the bucket.

Step 5: Created IAM Policies
    What I did: I created three separate IAM policies to ensure my Lambda function has the necessary permissions:
    CloudWatch Logs permission: So the Lambda function can log errors and other events for monitoring.

S3 bucket access permission: 
    So the Lambda function can read from the media-app-initial-image-1 bucket and     write                  resized images to the media-app-resized-image-1 bucket.
    SQS queue read permission: So the Lambda function can read messages from the SQS queue when an image upload event occurs.

Step 6: Created a Lambda Execution Role
    What I did: I created an IAM role specifically for the Lambda function and attached the three IAM policies created in Step 5. This role gives the Lambda function the necessary access to S3, SQS, and CloudWatch.

Step 7: Set Up the Lambda Function
    What I did: I created a Lambda function to handle image resizing.
    Code: I deployed the provided code, which contains logic to resize images.
    Execution role: I assigned the Lambda function the execution role I created in Step 6, so it has the required permissions to access the resources it needs.

Step 8: Tested the Setup
    What I did: I tested the entire pipeline by uploading images to the media-app-initial-image-1 bucket.
    What happened: The Lambda function resized the images and saved the resized versions to the media-app-resized-image-1 bucket as expected.
    Monitoring: I checked CloudWatch logs to ensure everything was working properly and to troubleshoot any issues that arose during testing. Everything worked smoothly.

--------------------------------------------------------------------------------------------------------------------
You will find all the images of services in the below folder
    - Images of services   
In S3 folder you will find 
    - Event notification file
In SQS you will find 
    - SQS Access Policy
In Lambda folder there are
    - Lambda function code
    - Lambdalayer img
    - Lambdatrigger img
In IAM Role folder you will find
    - IAM Role img     

--------------------------------------------------------------------------------------------------------------------
I would like to humbly explain my situation regarding the project. My work hours are from 10 AM to 7 PM, and I have a batch at FC Road from 11 AM to 1 PM, so I can only get home around 8 PM. Additionally, I have a session with my cousin from 7:30 PM to 9 PM, as he has an important exam next week. Even on Sundays, I have three batches to manage. 

Due to this tight schedule, I studied and implemented most of the pipeline between 12 AM and 6 AM, but I couldn't complete the DynamoDB and scaling parts. I kindly ask you to consider my efforts under these circumstances and overlook the remaining parts. Thank you for your understanding.

--------------------------------------------------------------------------------------------------------------------