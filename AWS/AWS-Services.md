## AWS CloudFormation 2019/03/01
- a shell script like template managing AWS resources, provisioning, and setting.
- formatted in yaml, json
- save the template to the s3 bucket -> point to the template and built stack.

<img title='スクリーンショット 2019-03-01 9.19.37.png' src='/attachments/b25f2b73-d081-4cb0-a9ba-40816a525bf1' width="579" data-meta='{"width":579,"height":275}'>

cloud formation syntax
```yaml
AWSTemplateFormatVersion: '2010-09-09'
Resources:
  FirstVPC:
    Type: AWS::EC2::VPC
    Properties:
      CidrBlock: 10.0.0.0/16
      Tags:
      - Key: Name
        Value: FirstVPC
  InternetGateway:
    Type: AWS::EC2::InternetGateway
    Properties:
      Tags:
      - Key: Name
        Value: FirstVPC-IGW
  AttachGateway:
    Type: AWS::EC2::VPCGatewayAttachment
    Properties:
      VpcId: !Ref FirstVPC
      InternetGatewayId: !Ref InternetGateway
```
!Ref (built in function)
- points to the reasorce value
ex. the last line `!Ref InternetGateway` points to the value of InternetGateway in the middle block of the code

## AWS Lambda 2019/03/04
- offers serverless code execution system.

benefit
- Lambda does not need any setup; therefore, programmers can ignore the management of servers and just focus on coding.
In the past, programmers had to prepare  OS, web server, the web application server to run the code. 

- cost only while the code is running. 
By running code with a server,  it constantly cost money. Thus, running code with lambda is beneficial to users

## AWS Step Functions 2019/03/05
The visual workflows are representing a state machine and manages the execution and orchestration of microservices.
- state machine is written by json and yaml, and in the future accepts python as language

## AWS SSM (Simple System Manager) 2019/03/06
console interface managing AWS reasources such as EC2 instances, sagemaker, and etc.

The sample process

<img title='スクリーンショット 2019-03-06 16.33.16.png' src='/attachments/8fa9cf44-dd17-4423-8c2b-2a4bfef9cbd0' width="650" data-meta='{"width":650,"height":712}'>

1. access SSM console

2. operate EC2, linux machine, etc

3. Save the log to S3

benefit
- Secure
To access ec2 server, No need for ssh login. Therefore, cracker is not capable of penetrating the server through the ssh access.
