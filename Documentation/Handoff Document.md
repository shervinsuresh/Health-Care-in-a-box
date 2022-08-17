# Engagement Handoff 

##  
**Confidentiality of Contents**

** ** 
The contents of this document are shared only under NDA and should not be reattributed.

##  
**Amazon Web Services Disclaimer**

 
This document is not legally-binding, and is not an offer to contract that can be accepted by either party. All responses, descriptions and observations in this document are informational and are provided solely for discussion purposes. Neither party will have any obligation or liability with respect to the matters described in this document. All obligations must be set forth in a separate definitive agreement executed by the parties addressing such matters, provided, however, that neither party will have any liability for any failure or refusal to enter into a definitive agreement for any reason. Amazon Web Services, Inc. (AWS) has provided responses based on its current knowledge, but these responses may change at any time due to a variety of factors, including without limitation, changes to your requirements, the capabilities of any third party you select to assist with implementation, and changes to AWS’s service offerings. AWS does not make any representations or warranties of any kind in this document. Any use of the AWS service offerings will be governed by the AWS Customer Agreement available at http://aws.amazon.com/agreement/ (or other definitive written agreement between the parties), not this document. AWS does not accept any terms or conditions included in this document that conflict with or are in addition to the terms and conditions set forth in the AWS Customer Agreement.   
 

## 
**Document Objective**


** ** 
This document provides a summary of the engagement conducted by the Solutions Architect Intern team and a list of next steps. This document assumes a familiarity with AWS terms and is written for a generally technical audience. 
 
 

## 
**Contributing Participants**

###  
**Key members of the Customer Team** 

|Name	|Title/Role	|Email	|
|---	|---	|---	|
|Keisuke Nakagawa	|Director of Innovation	|[drknakagawa@ucdavis.edu](mailto:drknakagawa@ucdavis.edu)	|
|Daniel Bradley 	|CIC Member	|[dsbradley@ucdavis.edu](mailto:dsbradley@ucdavis.edu)	|

### **Key Contributors from AWS**

|Name	|Title/Role	|Email	|
|---	|---	|---	|
|Lynn Kreun	|Manager CAT	|lkreun@amazon.com	
|Tim Jones	|Solutions Architect CAT	|awstijon@amazon.com	
|Jon Sou	|Solutions Architect CAT	|jonsou@amazon.com	
|Shervin Suresh	|Solutions Architect Intern	|scshervi@amazon.com	
|Ayush Misra	|Solutions Architect Intern	|aymisra@amazon.com	
|Joseph Baroody	|Solutions Architect Intern	|jbaroody@amazon.com	
|Keonna Parrish	|Solutions Architect Intern	|keonnpar@amazon.com	
|Andrew Crabbe	|Senior Solutions Architect AMC	|crabbea@amazon.com	
|Kas Parthasarathy	|Senior Solutions Architect AMC	|kasparth@amazon.com	
|Qing Liu	|Senior Solutions Architect AMC	|qnamzn@amazon.com	

## 
**Summary of Objectives**


The Sacramento Solutions Architect (SA) Interns worked with UC Davis Health to create a “healthcare in the box” system. This system was created in preparation for UC Davis Health’s Cloud Innovation Center; for future  deployment, testing, and implementations. The SA interns worked to understand the customer’s requirements and provided multiple sprint presentations which guided the customer through the system progression. 


* Deployment
    * Analytics
        * Amazon HealthLake
        * Amazon QuickSight
    * Cloud Deployment

        * Elastic Compute Cloud
        * Relational Database Service
        * Application Load Balancer
        * AWS CloudFormation
        *  Creation of networking components (VPC, Subnets, Routing) 
* Enablement
    * Healthcare Standards
        * FHIR

# 
**Current Architecture and Infrastructure**

### **Architecture Diagram**

![architecture diagram](/Diagrams/Project%20Architecture.png)
# 
**Accomplishments and Deliverables ** 


**Sprint 1**
We worked on understanding the AWS management console and using it to create our first system implementation. We began by creating a Virtual Private Cloud (VPC) with 2 public and 2 private subnets and placing a MYSQL RDS into one of the private subnets.
We validated the functionality of OpenEMR through a local deployment, then completed most of deploying the application on Elastic Compute Cloud (EC2). The application was then validated for functionality through the use of creating patients through the user interface. After successful application deployment an Elastic Load Balancer was added to help route traffic.  Furthermore, collectively we honed in on the problem at hand and familiarized ourselves with the nuances of OpenEMR, while beginning to delve into the standards of the FHIR format. 
  
**Sprint 2**

We worked on further deploying the containerized OpenEMR, though the application only ran with a database running on the EC2 instance, and worked on resolving issues to deploy multiple instances of OpenEMR.
We started working within Postman as a generic FHIR client to connect to OpenEMR.  We then began to troubleshoot issues with SSL certificates and connecting to the site address. We utilized CloudFront to connect to OpenEMR locally. 
We began to distinguish the different versions of HL7 and FHIR understanding the advantages that FHIR brought to us in the scope of this project. 
We began to generate data with Synthea locally and learned many of the features of the data including the format and the level of ease at which we were able to alter certain properties including the names of patients. Next, through Postman, an API client, we were able to load the data into OpenEMR and use various features built into the platform such as searching for patients and inspecting their vitals. We accomplished the ability of integrating synthetic data into OpenEMR while interacting with patient records through Postman as well.
We also worked with the Picture Archive and Communication System (PACS) integrated with OpenEMR, thus providing demoes proving the integrated PACS functioned correctly while in deployed in the cloud.
 
**Sprint 3**

In addition to working with openEMR, we advanced our data pipeline to include HealthLake and Amazon QuickSight functionality.  
Within our pipeline, we defined clear use-cases in which we would provide any user with the ability to upload external data sets into an S3 bucket. Another option that we worked on implementing was the ability to create synthetic data directly in OpenEMR. By establishing this pipeline, we needed to understand the capabilities and roles of CCDA (used for importing) and FHIR (used for exporting data into S3 bucket leading into Amazon HealthLake). After generating the data, as a team, we collectively decided using a CloudFormation template would be most efficient in going about the ability to making this an end customer triggered capability. We began implementing certain parameters and worked towards understanding ways in which we could incorporate the generation of data through the UserData script.
Did a deep dive into documentation on FHIR, authorization vs authentication, scopes, and nuances within OpenEMR. Within postman, we used parameters in order to filter and retrieve single/multiple records. 
We were able to deploy a properly containerized version of OpenEMR that connects with an external database on RDS, as well as working on CloudFormation Templates to deploy the current architecture in a more user friendly way. There was also an Amazon Machine Image (AMI) created for an OpenEMR EC2 instance that connects to an external Database.

#  
**Next Steps**

### **Possible Future Enhancements** 

**PACS/ VNA integration** 
Amazon HealthLake supports both structured and unstructured data. Using HealthLake APIs, we look to incorporate medical imaging report data into Amazon HealthLake. In addition, Orthanc DICOM Server AMI supports DICOM images for PACS/VNA integration. This open source platform can be connected to s3 storage for additional resiliency and cost.    

**Improve the agnostic ability of the EMR platform**- Through the use of AWS services it allows for a simpler coupling of different applications for the Electronic Medical Record (EMR) systems. In particular since OpenEMR was used in the current iteration of implementation, the ability to swap out OpenEMR for an application such as WorldVistA is a logical step. Thus in order to provide the first steps for implementing an agnostic EMR system, an Amazon Machine Image (AMI) was created using the WorldVistaA docker image, though the AMI requires further refinement, due to unseen complexity of the WorldVistA system. 
The Next Steps would include:

1. adding a Graphic User Interface to the AMI, and finishing up the EC2 deployment of WorldVistA
2. Updating the CloudFormation Template (provided in the GitHub) with the updated AMI for World VistA
3. The application natively doesn’t seem to support external databases, so research into the code of the WorldVistA application would be required (see Resources for links to the code)

**Develop auto scalable platforms -** With the Healthcare Platform needing to cater to many sizes of entities, the ability for the platform to scale automatically is a very important next step. With auto scaling especially with Elastic Container Service (ECS) it would allow for the resources needed at that moment to be added (such as compute, memory, and storage). Thus to implement the auto-scalability of the platform, the next steps needed are:

1. Deploying OpenEMR Application built on the Container (as given in the GitHub) through ECS
    1. The issue stems from the connection of the ECS cluster to the RDS database not being resolved


**Have a Fully Complete and Deployable CloudFormation Template with Synthetic Data -** Specifically regarding the pipeline, currently we envision an end-user with the ability of either uploading external files of synthetic data that they may have locally or the option of generating the data directly in OpenEMR. Currently, we are working on data that we have created locally, and the next step, through a CloudFormation Template, would be having these records in the cloud so that anybody could access them. By integrating CloudFormation, you are using a template that describes all the AWS resources necessary and then CLoudFormation takes care of configuring and provisioning those resources. Using a certain AMI, and the instance that we are running on, this process is fairly straightforward with a few intricacies in regards to the way CloudFormation works. The next steps would be:

1. Figure out which parameters are essential and necessary to the application (currently we are using an OpenEMR Standard version with a few additional parameters
2. Incorporate the ‘Import-Patients’ function correctly into the User-Data script (currently we have the right function, but the command isn’t being executed correctly)
3. Use the AWS-CLI to run certain commands in order for the function to be called
4. Use the SSM Parameter Store and inside CloudFormation, use a certain parameter store value and provide two options (s3 uri or synthetic data)
5. Warning: New Properties may not be created, so you can only use the built-in properties of an EC2 instance (https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-ec2-instance.html)

**End Goal:** We are trying to create a design in which there can be an end customer (self service) triggered capability of generating the data. Once this data is auto-generated in the template, there will be a sync through Postman into an S3 bucket leading into Amazon HealthLake and going down the pipeline.

**Fully Connected Data Pipeline-** In order to make API calls in OpenEMR we will connect Postman to the cloud (Hosted Zone) in order to receive an SSL certificate and override the Site Address ID issue. 
We then can Introduce FHIR Works on AWS through postman in order to:

1. Fix the dependency on the sessions implemented in the OpenEMR Application (shown in the screenshot on the GitHub showing the file structure and files needed to update)
    1. This subtask requires the user to be well versed in PHP coding language

     2.  CRUD operations for all R4 base FHIR resources
     3.  Basic search per resource type
     4. Ability to get and post binary resources (Unstructured Data into s3 bucket using pre-signed URL)
     5. Ability to post a transaction bundle of 25 entries or less (FHIR Bulk Data)

#  **Resources ** 

* **WorldVistA Website: https://worldvista.org/AboutVistA**
* **WorldVistA Docker: https://hub.docker.com/r/worldvista/worldvista-ehr/**
* **WorldVistA Server Code Link (needed to see for changing Database): https://sourceforge.net/projects/worldvista-ehr/files/WorldVistA_EHR_3.0/WVEHR_3.0_Ver2-16-YottaDB-GTM.zip/download**
* **WorldVistA Client Code Link: https://sourceforge.net/projects/worldvista-ehr/files/WorldVistA_EHR_3.0/CPRS-WVEHR3.0Ver2-16_BasedOn1.0.30.16SourceCode.zip/download**
* **OpenEMR GitHub:** https://github.com/openemr/openemr/find/master
* **Connecting to an external Database: https://aws.amazon.com/premiumsupport/knowledge-center/ecs-fargate-task-database-connection/**
* **ECS Instances: https://docs.aws.amazon.com/AmazonECS/latest/developerguide/ECS_instances.html**
* **AWSNetworkingLab:**https://networking.workshop.aws/  
* **HealthLake Workshop Link** https://catalog.us-east-1.prod.workshops.aws/workshops/498fdbc5-46e1-4cb0-97a0-f4ec3a30f26a/en-US/step-1-setup-import-and-export
* **EC2 Properties on CF Template**  https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-ec2-instance.html
* **Developer Setup for Synthea** https://github.com/synthetichealth/synthea/wiki/Basic-Setup-and-Running
* **Synthetic Data Sets to Download** https://synthea.mitre.org/downloads
* **OpenEMR Standard CFN Template** https://github.com/openemr/openemr-devops/blob/master/packages/standard/cfn/OpenEMR-Standard.json
* **Synthetic Function for UserData Script** https://github.com/openemr/openemr-devops/blob/master/docker/openemr/flex-3.14/utilities/devtoolsLibrary.source
* **Connection to OpenEMR** https://github.com/openemr/openemr/blob/master/CONTRIBUTING.md#xdebug
* **Orthanc DICOM Server with AWS-S3 support https://aws.amazon.com/marketplace/pp/prodview-7rdskbiq3tb34#pdp-support**

