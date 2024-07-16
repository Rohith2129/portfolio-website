**Project: Hosting A Resume Static Website And CI CD Pipeline**

**Route 53:** Route 53 is a highly scalable and reliable Domain Name System (DNS) web. It offers domain registration, DNS routing, and health checking services to manage the domain names and route internet traffic to the appropriate resources It is widely used by businesses and organizations to ensure reliable and efficient routing of internet traffic to their resources and to manage their domain names in the AWS ecosystem.

**CloudFront: **CloudFront is a content delivery network (CDN) service.It is designed to accelerate the delivery of static and dynamic web content, including websites, images, videos, APIs, and applications, to users worldwide. It used by organizations to improve the speed, scalability, and availability of their web content and applications. Whether it's delivering static files or dynamic API responses, CloudFront helps reduce latency, increase throughput, and enhance the overall user experience for customers accessing content from various locations worldwide.

**AWS Certificate Manager (ACM):** ACM simplifies the management and deployment of SSL/TLS certificates, allowing you to secure your applications and resources easily. By automating certificate provisioning and renewal processes and integrating with various AWS services, ACM helps ensure secure and encrypted communication between users and your applications.

**AWS S3:** Stands for Amazon Simple Storage Service. It allows individuals and organizations to store and retrieve large amounts of data, such as files, images, videos, and documents, in a highly scalable, secure, and cost-effective manner. AWS S3 is widely used for a variety of use cases, such as backup and restore, data archiving, content distribution, data lakes, and web hosting. Its flexibility, scalability, and robust feature set make it a popular choice for storing and managing data in the cloud.

**AWS CodePipeline:** It is a fully managed continuous integration and continuous delivery (CI/CD). It helps you automate and streamline the process of building, testing, and deploying applications. By integrating with various AWS services and third-party tools, it provides a comprehensive CI/CD solution for managing and delivering your applications with speed, efficiency, and reliability.

**GitHub:** GitHub is a web-based platform and version control repository hosting service that allows developers to collaborate on projects, track changes to code, and manage software development workflows. It is used by individual developers, open-source projects, and organizations of all sizes. 
 
![image](https://github.com/Basanagoudapatil02/Project-Hosting-A-Static-Resume-Website-And-CI-CD-Pipeline/assets/63364609/000040a3-7d3f-4113-ab81-e47621f00565)


Pre-Requisites
1.	Html Code
2.	Github account
3.	AWS account
4.	Domain name: www.basanagoudapatil.co

Step 1: Create a S3 bucket 
•	Create a bucket and give name to it and open it to public access 

![image](https://github.com/Basanagoudapatil02/Project-Hosting-A-Static-Resume-Website-And-CI-CD-Pipeline/assets/63364609/c20802f5-ba87-4721-ac8f-3deb42977b7f)
 
•	Click on create bucket.

 ![image](https://github.com/Basanagoudapatil02/Project-Hosting-A-Static-Resume-Website-And-CI-CD-Pipeline/assets/63364609/813e458c-cfa7-4125-aaef-bfa2ab36088c)

•	Go to properties and edit static website hosting
•	Make it enable and set the default page of the website and give error path also if you have and save it.

  ![image](https://github.com/Basanagoudapatil02/Project-Hosting-A-Static-Resume-Website-And-CI-CD-Pipeline/assets/63364609/ca2ecb4d-b86c-47a8-ac8e-622cb17afc7a)

•	Now, upload your all files and folder related to code to this bucket.
 
![image](https://github.com/Basanagoudapatil02/Project-Hosting-A-Static-Resume-Website-And-CI-CD-Pipeline/assets/63364609/5d446ecd-3f2c-4ae1-8385-3739296d2482)

Step 2: Create a CloudFront distribution 
•	Click on create cloudfront distribution.
•	Choose your origin domain name in S3 section.
•	Select origin access as legacy access identities.

![image](https://github.com/Basanagoudapatil02/Project-Hosting-A-Static-Resume-Website-And-CI-CD-Pipeline/assets/63364609/33917d38-7284-47b0-867c-a7f132a598ed)
 
•	Create a new origin access identity (OAI) and select update the bucket policy too.

 ![image](https://github.com/Basanagoudapatil02/Project-Hosting-A-Static-Resume-Website-And-CI-CD-Pipeline/assets/63364609/92c02f01-df2d-4803-905a-b542c8d84519)

•	In default cache behaviour setting in viewer section ,I want http requests to redirect to https and in allowed HTTP method I have chosen 3rd option. And keep other setting as default only.

 ![image](https://github.com/Basanagoudapatil02/Project-Hosting-A-Static-Resume-Website-And-CI-CD-Pipeline/assets/63364609/d1dbceef-ef30-4bbd-866e-cb685cbab271)

•	Select your Web Application Firewall (WAF) ,I have enable it and it has some charges for it, estimated to cost $14 for 10 million requests/month as per AWS.

 ![image](https://github.com/Basanagoudapatil02/Project-Hosting-A-Static-Resume-Website-And-CI-CD-Pipeline/assets/63364609/e6084008-a2db-4288-88ee-c712c76cca41)

•	In setting section, I used all edge location and give alternate domain name.(www.basanagouda96@gmail.com)

 ![image](https://github.com/Basanagoudapatil02/Project-Hosting-A-Static-Resume-Website-And-CI-CD-Pipeline/assets/63364609/db541f96-94a8-41cd-bbf8-d740d8153c67)

•	Now request for custom SSL certificate and certificate must be in the US east-1 (N.Virginial) region, click on request certificate.
•	Go with the default setting that is request a public certificate and click on next.

 ![image](https://github.com/Basanagoudapatil02/Project-Hosting-A-Static-Resume-Website-And-CI-CD-Pipeline/assets/63364609/f480dc45-f708-4f1e-9466-2fc38738696c)

•	Entre your Fully qualified domain name, mine is *.basanagoudapatil.co
•	In Validation method , select DNS validation as recommended.
•	In key algorithm, select RSA 	2048

 ![image](https://github.com/Basanagoudapatil02/Project-Hosting-A-Static-Resume-Website-And-CI-CD-Pipeline/assets/63364609/9a83f9a8-991b-449c-8954-5eab2e652267)

•	Click of request.

 ![image](https://github.com/Basanagoudapatil02/Project-Hosting-A-Static-Resume-Website-And-CI-CD-Pipeline/assets/63364609/630ca03f-a8f6-482e-8198-b4c7a97e495e)

•	Click on certificate Id and go Domain’s section

 ![image](https://github.com/Basanagoudapatil02/Project-Hosting-A-Static-Resume-Website-And-CI-CD-Pipeline/assets/63364609/3ed27b73-3b51-48e7-932b-117e7fda787f)

•	It populate a CName name and CNAME value for you so this CNN value using this you can put that in your DNS whichever DNS you are using like Route 53, GoDaddy, etc. In that create a CName record using this value and it will validated for you.
•	After validating your CNN then certificate status will show issued. 

 ![image](https://github.com/Basanagoudapatil02/Project-Hosting-A-Static-Resume-Website-And-CI-CD-Pipeline/assets/63364609/8334092f-9bab-4de1-8b14-7945162a423a)

•	Go back to cloudfront and refresh custom SSL certificate and select your certificate which one you created in above.

 ![image](https://github.com/Basanagoudapatil02/Project-Hosting-A-Static-Resume-Website-And-CI-CD-Pipeline/assets/63364609/19647f7d-5e73-450b-9663-e15d6b71b880)

•	keep all default setting as it is and define a default root object path, in my case it is index.html. 
•	Click on create distribution 
•	After some minutes, the status of cloudfront distribution will be enable and you check your website using distribution domain name.

 ![image](https://github.com/Basanagoudapatil02/Project-Hosting-A-Static-Resume-Website-And-CI-CD-Pipeline/assets/63364609/f6236bdb-7ef7-456f-acc2-979df506dc94)

•	Yes, it will visible through cloudfront domain name.
•	Now, go to your DNS distribution and create CNN record for this cloudfront domain name.
www.basanagoudapatil  cloudfrornt domain name

![image](https://github.com/Basanagoudapatil02/Project-Hosting-A-Static-Resume-Website-And-CI-CD-Pipeline/assets/63364609/00573d35-b5aa-41e7-915a-0330aab95ac9)

•	Now check in web browse weather our website is accessible
 
•	Yes it is visible by domain name (www.basanagouda.co)
Step 3: Create a Codepipe for CI/CD
•	Click of create a pipeline
•	Give a name to pipeline , select new service role and in advance settings select default location & default AWS managed key , click on next

![image](https://github.com/Basanagoudapatil02/Project-Hosting-A-Static-Resume-Website-And-CI-CD-Pipeline/assets/63364609/8bc65185-1285-4e71-9786-e6520a7d5603)
 
•	In Add source stage, select source provider as GitHub (version1)
•	Click on connect and connect to you GitHub and select your git repo and branch name.
•	Select GitHub web for change detection option.
 
![image](https://github.com/Basanagoudapatil02/Project-Hosting-A-Static-Resume-Website-And-CI-CD-Pipeline/assets/63364609/51d5a352-f93d-4b38-954b-1618f23169eb)

•	In add deploy stage , select provider as Amazon S3 and region as us-east
•	Select your bucket and click on extract file 
•	Review it and click on create pipeline. 

![image](https://github.com/Basanagoudapatil02/Project-Hosting-A-Static-Resume-Website-And-CI-CD-Pipeline/assets/63364609/7539ee6f-8fb0-4db5-ae6d-9a93b2589930)

•	S3 pipeline is successfully create 
•	To check it, change something in your code and commit it and it will reflect it your website.

![image](https://github.com/Basanagoudapatil02/Project-Hosting-A-Static-Resume-Website-And-CI-CD-Pipeline/assets/63364609/3d981cce-552f-44dc-b553-07dc646c6e1e)

•	Its working Sucessfully. Here I created a  static website using S3, Route53, Cloudfront, and Code pipeline.  

![image](https://github.com/Basanagoudapatil02/Project-Hosting-A-Static-Resume-Website-And-CI-CD-Pipeline/assets/63364609/78995ff7-2c1e-4008-a055-26a2821568de)
 

 
































 
