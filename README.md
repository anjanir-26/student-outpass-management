Student Outpass Management System

An Outpass Management  System using serverless web application, which helps students to apply outpass or to request a leave.

This serverless web application helps  hostel students to make a request for outing , whenever outing requested a mail is sent to corresponding hostel incharge , he/she will accept or reject your request and student also receives the status of your request .

AWS services to implement this serverless web application
-	Lambda
-	S3
-	API Gateway
-	SES (Simple Email Service)
-	Dynamo DB
-	IAM
Mechanism:

Here is a brief explanation of how this mechanism works:

1.	An HTML form is hosted on a web page and served to the user through a web server. The user fills out the form with their details and submits it.
2.	The form data is sent to API Gateway, which is a fully managed service that allows developers to create, deploy, and manage APIs at any scale. API Gateway acts as a front door for the backend services and APIs that power the application, and it is responsible for securely routing the request to the appropriate backend service or function.

 
3.	The request is then forwarded to a Lambda function, which is a serverless compute service that runs code in response to events and automatically manages the underlying compute resources. The Lambda function receives the form data and performs the necessary processing, such as storing the data in DynamoDB and sending an email notification to respective hostel incharge  using SES.

4.	Now, the hostel Incharge receives mail which includes student details like id, name, reason for outing , start date and end date additionally mail also includes accept or reject request. If incharge clicks on accept link it is a API gateway endpoint that triggers lambda and perform update operation for status as accepted in DynamoDB for that requested Student details and vice versa .



5.	Whenever status is accepted for respective student details , lambda is triggered and sends an email to that student who requested for outing stating that your outpass request has been accepted , and vice versa. 

6.	Like wise it provides an easy mechanism for hostel students to request outpass .

Overall, this mechanism leverages the power of multiple AWS services to provide a scalable, reliable, and cost-effective solution for processing HTML form submissions and storing them in DynamoDB while also sending email notifications to the user using SES.



 <img width="957" alt="1" src="https://github.com/anjanir-26/student-outpass-management/assets/110450315/fe89a57f-4da8-4fa9-b7e6-bfa8605aa07e">

IAM : Add required permissions like API Gateway, S3, SES, Dynamo DB and create a role to lambda.

 <img width="960" alt="2" src="https://github.com/anjanir-26/student-outpass-management/assets/110450315/65e622c6-282d-498b-b8ae-3a1c480da694">

SES : Before you apply outpass make sure that your mail should be verified so that you can send or receive mail.

 <img width="959" alt="3" src="https://github.com/anjanir-26/student-outpass-management/assets/110450315/8403ee81-0195-48e6-b840-068c1eb3cd1d">

Dynamo DB : create a table in Dynamo DB

 <img width="956" alt="4" src="https://github.com/anjanir-26/student-outpass-management/assets/110450315/6b7ffbae-2e39-41f5-ac28-912f66cf80b1">

Lambda : create a lambda function and assign the iam role with the given permissions , which stores the details of student in dynamo db and sends an email to hostel incharge to accept/reject the request whenever student apply outing request.

 <img width="960" alt="5" src="https://github.com/anjanir-26/student-outpass-management/assets/110450315/6ff754d9-109e-488a-b10c-4694cd3c9edf">

Another lambda function which will update the status of student in dynamo db as accepted whenever hostel incharge clicks on link corresponds to accept in mail.

 
<img width="955" alt="6" src="https://github.com/anjanir-26/student-outpass-management/assets/110450315/0a5670a5-acec-43b1-b59b-494b8174d3a4">

Another lambda function which will update the status of student in dynamo db as rejected whenever hostel incharge clicks on link corresponds to accept in mail.

 <img width="960" alt="7" src="https://github.com/anjanir-26/student-outpass-management/assets/110450315/1c29a88d-6512-49f2-a9c2-834297359e82">

API Gateway : configure api gateway for addApplicants , accept and reject.

 <img width="949" alt="8" src="https://github.com/anjanir-26/student-outpass-management/assets/110450315/448e6cc5-9283-47de-9a6d-acccf979631f">

S3 : configure S3 bucket and upload HTML files , make them as public and enable static web hosting.

 <img width="959" alt="9" src="https://github.com/anjanir-26/student-outpass-management/assets/110450315/cc780b1c-573b-482e-8c13-d37a83181b47">

Click on the link , it will open a static website as shown below
<img width="960" alt="10" src="https://github.com/anjanir-26/student-outpass-management/assets/110450315/349bc74a-f1c6-42da-8a15-1a5bfd06e1c8">

<img width="483" alt="11" src="https://github.com/anjanir-26/student-outpass-management/assets/110450315/9f174542-2edb-4c9b-9b38-1683b7eb5b30">
<img width="960" alt="12" src="https://github.com/anjanir-26/student-outpass-management/assets/110450315/b9a84ec2-2625-4db1-85d4-08f3d3edb132">
<img width="462" alt="13" src="https://github.com/anjanir-26/student-outpass-management/assets/110450315/85626746-1dac-4938-ac93-4b8e44a7999f">





  
 
 

 

 


 

 










