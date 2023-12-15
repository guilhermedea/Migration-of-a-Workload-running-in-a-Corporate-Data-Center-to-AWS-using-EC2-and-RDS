# Migration of a Workload running in a Corporate Data Center to AWS using EC2 and RDS

![post picture](https://miro.medium.com/v2/resize:fit:720/format:webp/0*jfNgfZp9gCOhrdZM.jpg)

In another project based on a real-world scenario, I acted as the Cloud Specialist responsible for migrating a workload running in a Corporate 
DataCenter to AWS. The application and database were migrated to AWS using the Lift & Shift (rehost) model, moving both application and database data.

I followed some migration steps: Planning (sizing, prerequisites, resource naming), Execution (resource provisioning, best practices), Go-live
(validation test — Dry-run, final migration — Cutover) and Post Go-live (ensure the operation of the application and user access).

![solution architecture](https://miro.medium.com/v2/resize:fit:720/format:webp/0*VAEK5r16I-tVQo9s.jpg)

I fundamentally believe in the importance of good planning for any type of project, and this one wasn’t different. Because it involved lots of resources, 
each step had to be carried out slowly, using a good documentation to guide the process and at the same time balance performance and cost.

Beginning from the starting point, I created a dedicated VPC for the project, with a public subnet and two private subnets, on two different Availability 
Zones. The provisioning process of the EC2 instance and RDS began with analysing the current on-premises infrastructure used by the client. 
From this analysis, it was possible to select the necessary instance shapes for the operation. During this process I created the Security 
Groups, allowing internal communication from the EC2 instance on the public subnet with the database on the private subnet, with the Internet 
Gateway allowing public access to the app.

![Created database on RDS. I’ve edited out the endpoint address.](https://miro.medium.com/v2/resize:fit:720/format:webp/0*X2st5qfQ6gCS0msT.png)

With the structure ready, it was time to prepare the EC2 instance to run the application. Again, using a good planning and analysing the existing structure,
I installed all the apps and libraries needed to run the application normally. After this, I connected the instance with the RDS database, where the data
migration from the on-premises database to the cloud one was successfully executed.

With the RDS database filled, it was needed to update the application’s code to use the RDS’s endpoint address. After updating the code, the application was deployed.

![Deploying the application on terminal](https://miro.medium.com/v2/resize:fit:720/format:webp/0*y4TgnM0kJ6lStLcM.png)

To validate the execution, I’ve accessed the EC2’s public address through the port used by the Internet Gateway and created an article with my name. 
With that, the execution is validated.

![Dashboard](https://miro.medium.com/v2/resize:fit:720/format:webp/0*-P_t5VVeZ_XDEGSt.png)

Every migration must be done with caution and patience. The biggest part of this project was to collect data and information to create the correct infraestructure.
A rushed migration, without documentation and data can be catastrophic and cause major financial lossess. Thanks to the available tools, along the collected 
and documented data, the migration was done in a very short time and in a very safe way.

