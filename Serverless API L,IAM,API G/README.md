## Serverless API With Lambda, IAM, API Gateway Project

This project details the creation of a serverless backend on AWS, transitioning from initial infrastructure setup to final data verification. The project involves building an API Gateway, a lambda function, and dynamoDB for data persistence.

**Architectural Diagram**
<img width="704" height="384" alt="IMG_7958" src="https://github.com/user-attachments/assets/b0620b74-ffff-44c9-b907-9c31b4931e0d" />


# Amazon DynamoDB setup

Created the students NoSQL database table with "id" as the partition key to store student submissions.
On-demand Capacity mode

**DynamoDB Table**
<img width="1243" height="621" alt="ASM4-DynamoDB" src="https://github.com/user-attachments/assets/40c1eae3-5abf-42c1-bdf5-a0fd317ce02d" />


# IAM Policy & Role

Created an IAM execution role with an inline policy with the principle of least privilege.
allowed dynamodb:PutIten specifically on the students table ARN

**IAM Policy JSON**
<img width="1257" height="601" alt="ASM4-IAM-Policy-JSON" src="https://github.com/user-attachments/assets/6781d8f2-11b9-4096-86e0-333f733bbc86" />

# Lambda Function 
<img width="792" height="555" alt="ASM4-lambda function" src="https://github.com/user-attachments/assets/bcbfb062-455a-40dc-be57-3c9e8eb8eb11" />


# API Gateway
Public entrypoint 
- POST method: configured as a Lambda proxy integration to pass data directly to the function,
- OPTIONS method: configured as a Mock integration to handle CORS preflight requests independantly

**API with Lambda integrated**
<img width="973" height="323" alt="ASM4-API x Lambda" src="https://github.com/user-attachments/assets/7fbf95e8-0e75-4776-8fb5-caf1c6d4b4f5" />


# Testing

Validated system functionality by testing with terminal commands and verified record in the DynamoDB table.


**Terminal Test**
img width="569" height="357" alt="ASM4-Terminal-Upload" src="https://github.com/user-attachments/assets/b9f883f6-8356-4716-b77e-271fdb357cb4" />

**DynamoDB Verification**<
<img width="651" height="386" alt="ASM4- Validation" src="https://github.com/user-attachments/assets/c7fcc012-6eaa-4992-baa9-728634af08b3" />


# key Learnings

- IAM security: The importance of limiting resource access to only what is required.
- CORS (Cross-Origin Resource Sharing): Understanding that browsers block cross-domain requests unless the API explicitly responds to OPTIONS requests with correct headers
- Procy Integration: Learned how API Gateway act as a passthrough for data to Lambda


















