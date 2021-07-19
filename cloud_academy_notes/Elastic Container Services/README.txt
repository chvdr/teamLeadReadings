ECS - Elastic Container Service -- this is directory name (wrongly set in the beginning)

COURSE: Compute Fundamentals For AWS

---------------
1. Introduction
---------------

----------------------------------------------------------------------------------
--                                                                              --
-- 	###                                                                      	--
-- 	 #  #    # ##### #####   ####  #####  #    #  ####  ##### #  ####  #    #	--
-- 	 #  ##   #   #   #    # #    # #    # #    # #    #   #   # #    # ##   #	--
-- 	 #  # #  #   #   #    # #    # #    # #    # #        #   # #    # # #  #	--
-- 	 #  #  # #   #   #####  #    # #    # #    # #        #   # #    # #  # #	--
-- 	 #  #   ##   #   #   #  #    # #    # #    # #    #   #   # #    # #   ##	--
-- 	### #    #   #   #    #  ####  #####   ####   ####    #   #  ####  #    #	--
--                                                                              --
----------------------------------------------------------------------------------

AWS Foundation Services 
* COMPUTE --> Only this is covered in this course, others below are only informationally present
* STORAGE 
* DATABASE 
* NETWORK

Stuart Scott - AWS Lead https://uk.linkedin.com/in/stuartanthonyscott/

Support contact: support@cloudacademy.com 

Throughout this course, I will discuss a number of different Compute services and features of AWS that fall under the category of Compute resources. 

* [What is Compute in AWS?]
As a result, I've broken the course into the following lectures, starting with [What is Compute in AWS?] Before we can discuss the different Compute resources available within AWS, it's important we understand what Compute is. 

* [EC2] -- Elastic Compute Cloud, known as [EC2]: the most common Compute service, VMs
{Elastic Compute Cloud}, known as [EC2]. This is one of the most common Compute services, and as a result this will likely be the longest lecture, as I want to cover a lot of the elements around EC2 to ensure you are aware of how it's put together and how it works. 

* [EC2 Container Service] -- ECS: EC2 Container Service related to Docker
Amazon ECS, the [EC2 Container Service]. Within this lecture, I will provide a high-level overview of what the EC2 Container Service is and how it relates to Docker. 

* [Elastic Container Registry] -- ECS to provide a secure location to store and manage Docker images
Amazon [Elastic Container Registry]. In this lecture I explain how this service links closely with ECS to provide a secure location to store and manage your Docker images. 

* [Elastic Container Service for Kubernetes] -- EKS provides a managed service allowing you run Kubernetes 
Amazon [Elastic Container Service for Kubernetes], EKS. Here I look at how EKS provides a managed service allowing you run Kubernetes across your AWS infrastructure without having to take care of running the Kubernetes Control Plane. 

* [AWS Elastic Beanstalk] -- automatically deploy applications using EC2 and a number of other AWS services
This lecture will provide an overview of the service, showing how it's used to automatically deploy applications using EC2 and a number of other AWS services. 

* [AWS Lambda] -- serverless service, run your own code in response to events
This lecture covers the Lambda serverless service, where I shall explain what serverless means and how this service is used to run your own code in response to events. 

* [AWS Batch] (batch computing) and [Amazon Lightsail] (virtual private service solution used for small-scale projects)
Here I will provide a high-level overview of this service that relates to batch computing. And Amazon Lightsail. Finally, we will look at Amazon Lightsail, the virtual private service solution used for small-scale projects and use cases. 

--------------------------
2. What is Compute in AWS?
--------------------------

---------------------------------------------------------------------------------------------
--  #####                                                             #    #     #  #####  --
-- #     #  ####  #    # #####  #    # ##### ######    # #    #      # #   #  #  # #     # --
-- #       #    # ##  ## #    # #    #   #   #         # ##   #     #   #  #  #  # #       --
-- #       #    # # ## # #    # #    #   #   #####     # # #  #    #     # #  #  #  #####  --
-- #       #    # #    # #####  #    #   #   #         # #  # #    ####### #  #  #       # --
-- #     # #    # #    # #      #    #   #   #         # #   ##    #     # #  #  # #     # --
--  #####   ####  #    # #       ####    #   ######    # #    #    #     #  ## ##   #####  --
---------------------------------------------------------------------------------------------
...

Transcript

Hello, and welcome to this very short lecture where we are going to answer the question, what is Compute in AWS? Before we begin to explore Compute services, resources and features, we must first understand what is meant by the term Compute. So what is it? 

Put simply, Compute resources can be considered the brains and processing power required by applications and systems to carry out computational tasks via a series of instructions. So essentially Compute is closely related to common server components, which many of you will already be familiar with, such as CPUs and RAM. With that in mind, a physical server within a data center would be considered a Compute resource, as it may have multiple CPUs and many gigs of RAM to process instructions given by the operating system and applications. 

Within AWS, there are a number of different services and features that offer Compute power to provide different functions. Some of these services provide Compute, which can comprise of utilizing hundreds of EC2 instances, or virtual servers, which may be used continuously for months or even years, processing millions upon millions of instructions. On the other end of this scale, you may only utilize a hew hundred milliseconds of Compute resource to execute just a few lines of code within AWS Lambda before relinquishing that Compute power. AWS Lambda is a serverless Compute resource in AWS, and I'll cover more on this service later in this course. Compute resources can be consumed in different quantities, for different lengths of time across a range of categories, offering a wide scope of performance and benefit options. So it will really depend on your requirements as to which Compute resource you use within AWS. 

In this course, we'll discuss them all, allowing you to decide which is best for your implementation. As a quick high level reference, AWS offers a Cloud Compute Index, which can be found using the link onscreen. And this shows different examples and scenarios of where you might use different Compute deployment units. That brings me to the end of this very short lecture. Now we are aware of what Compute is, let's start by looking at some of the services offered by AWS that provide this Compute resource, starting with Elastic Cloud Compute, EC2.

------------------------------
3. EC2 - Elastic Compute Cloud 
------------------------------

		***************************
		* #######  #####   #####  *
		* #       #     # #     # *
		* #       #             # *
		* #####   #        #####  *
		* #       #       #       *
		* #       #     # #       *
		* #######  #####  ####### *
		***************************
                         
... 

Hello and welcome to this lecture where I will explain what the EC2 service is and does, and how to configure an EC2 instance, so let's get started. As EC2 is one of the most common compute services used within AWS. I will discuss this service in greater detail over the other services that we'll cover in this course. 

EC2 is arguably the first compute service that you will encounter when working with AWS. It allows you to deploy virtual servers within your AWS environment and most people will require an EC2 instance within their environment as a part of at least one of their solutions. There are a number of elements in creating your EC2 instance, which I want to break down and explain. This will hopefully help to define how the service works and answer a number of questions that you may have. The EC2 service can be broken down into the following components: 
* Amazon machine images, AMIs 
* instant types
* instance purchasing options
* tenancy
* user data
* storage options
* security

Let's look at each of these individually. 

3.1 Amazon Machine Images

The first point I want to cover are AMIs, Amazon Machine Images. 

These are essentially templates of pre-configured EC2 instances which allow you to quickly launch a new EC2 instance based on the configuration within the AMI. This prevents you from having to install an operating system or any other common applications that you might need to install on a number of other EC2 instances. From a high level perspective an AMI is an image baseline that will include an operating system and applications along with any custom configuration. AWS provides a large number of AMIs covering different operating systems from Linux to Red Hat to Microsoft Windows among others. when configuring your EC2 instance, selecting your AMI is the first configuration choice you'll need to make. You can also create your own AMI images to help you speed up your own deployment. For example you would start with selecting an AWS AMI, let's say a Linux server. And then once it is up and running you may then need to install a number of your own custom applications and make specific configuration changes. Now if you needed another server to perform the same functionality, you could go through the same process of selecting a Linux AWS AMI, and again manually installing the applications and making your configurations. Or once you have made those changes on the first instance you can then simply create a brand new AMI or template of that instance with all the applications installed and configurations already made. Then if you need another instance of the same configuration all you would need to do is to select your custom AMI as the base image for your instance and it will launch with Linux server, your custom applications already installed and any configurations already made. As you can see this has many benefits and certainly comes in useful when implementing auto scaling. 

In addition to both AWS managed and your custom managed AMIs, you could also select an AMI from the AWS marketplace. The AWS marketplace is essentially an online store that allows you to purchase AMIs from trusted vendors like Cisco, Citrix, Alert Logic et cetera. These vendor AMIs may have specific applications and configurations already made, such as instances that are optimized with built-in security and monitoring tools or contained database migration systems. Lastly community AMIs also exists which are a repository of AMIs that have been created and shared by other AWS members. 

Let's now take a look at instance types, once you have selected your AMI from any of the different sources already discussed, you must then select an instance type. An instance type simply defines the size of the instance based on a number of different parameters, these being ECUs. This defines a number of EC2 compute units for instance, vCPUs this is the number of virtual CPUs on the instance. Physical processor, this is the process speed used on the instance. Clock speed, it's clock speed in gigahertz. Memory, the amount of memory associated. Incident storage this is the capacity of the local instance store volumes available. EBS optimized available, this defines if the instance supports EBS optimized storage or not. Network performance, this shows the performance level of rate of data transfer. IPV6 support, this simply indicates if the instance type supports IPV6. Process architecture this shows the architected type of the processor. AES-NI, this stands for advanced encryption standard new instructions and it shows if the instance supports it for enhanced data protection. AVX this indicates if the instance supports AVX which is advanced vector extensions, which are primary used for applications focused on audio and video, scientific calculations and 3D modeling analysis. And finally Turbo which shows if the instance supports intel turbo boost and AMD turbo core technologies. The key parameters here to primarily be aware of for general usage of an EC2 instance, could be summarized as vCPUs and memory, instant storage and network performance. But obviously this really depends on your actual usage and application. Having this flexibility of variant instances allows you to select the most appropriate size or power of an instance that you need for optimal performance within your applications. These different instance types are categorized into different family types that offer distinct performance benefits, which again helps you to select the most appropriate instance for your needs. Within each of these instance families you will have a range of instant types with varied CPU, memory, storage and network performance et cetera. 

3.2 Instant ypes 

These INSTANCE FAMILIES can be summarized as follows: 

▌MICRO INSTANCES, these instances have a low cost against them due to the minimal amount of CPU and memory power that they offer. These are ideal for very low throughput use cases such as low traffic websites. 

▌GENERAL-PURPOSE, instance types within this family have a balanced mix of CPU memory and storage making them ideal for small to medium databases, tests and development servers and back-end servers. 

▌COMPUTE OPTIMIZED, as the name implies instance types within this family have a greater focus on compute. They have the highest performing processes installed allowing them to be used for high-performance front end servers, web servers, high-performance science and engineering applications and video encoding and batch processing. 

▌GPU, GPU stands for graphics processing unit. And so the instances within this family are optimized for graphic intensive applications. 

▌FPGA, this family of instances allows you to customize field programmable gate arrays. To create application specific hardware accelerations when used with applications that use massively parallel processing power such as genomics and financial computing. 

▌MEMORY OPTIMIZED, this family include instance types that are primarily used for large-scale enterprise class in-memory applications, such as performing real time processing of unstructured data. They are also ideal for enterprise applications such as Microsoft SharePoint. These instances of the lowest cost per gigabyte of RAM against all other instance families. 

▌STORAGE OPTIMIZED, as expected these are optimized for enhanced storage. Instances in this family use SSD backed instant storage for low latency and very high I/O, input/output performance, including very high IOPS which is input/output operations per second. And these are great for analytic workloads and no SQL databases. Data file systems and log processing applications. 

3.3 Instance purchasing options. 

You can purchase EC2 instances through a variety of different payment plans. These have been designed to help you save cost by selecting the most appropriate option for your deployment. The different EC2 payment options are as follows: * ON-DEMAND instances, * RESERVED instances, * SCHEDULED instances, * SPOT instances and * ON-DEMAND CAPACITY RESERVATIONS. It's good to be aware of these different options as well having an understanding of these can help you save a considerable amount of money depending on your use case. Let me run through each option to help explain. 

Starting with 

ON-DEMAND INSTANCE

These are EC2 instances that you can launch at any time and have it provisioned and available to you within minutes. You can use this instance for a shorter time or for as long as you need before terminating the instance. These instances have a flat rate and is determined on the instance type selected and is paid by the second. On-demand instances are typically used for short term uses where workloads can be irregular and where workload can be interrupted. Many users of AWS use on-demand instances within their testing and development environments. And when you stop or terminate your on-demand instance you'll stop paying for the compute resource. 

RESERVED INSTANCES 

allow you to purchase a discount for an incidents type with set criteria for a set period of time in return for a reduced cost compared to on-demand instances. This reduction can be as much as 75%. These reservations against instances must be purchased in either one or three year time frames. Further reductions can be achieved with reserved instances depending on which payment methods you select. There are three options available to you, firstly all upfront. The complete payment for the one or three year reservation is paid. And this offers the largest discount and no further payment is required regardless of the number of hours the instance is used. Partial upfront, here a smaller upfront payment is made and then a discount is applied to any hours used by the instance during the term. And finally no upfront, no upfront or partial payments are made and the smallest discount of the three models is applied to any hours used by the instance. Reserved instances are used for long-term predictable workloads allowing you to make full use of the cost savings to be had when using compute resources offered by EC2. 

SCHEDULED INSTANCES

these are similar to reserved instances and the fact that you pay for the reservations of an instance on a recurring schedule, either daily, weekly or monthly. For example you might have a weekly task that is scheduled that performs some kind of bulk processing for a number of hours at the same time every week. With scheduled instances you could set up a scheduled instance to run during that set timeframe once a week. And this prevents you for having to use the on-demand instances which would incur a higher price. You should note that when using scheduled instances but even if you didn't use the instance you would still be charged. This allows you to provision instances for scheduled workloads that are not continuously running. Which is where a reserved instance would be the preferred choice. 

SPOT INSTANCES 

allows you to bid for unused EC2 compute resources, however your resource is not guaranteed for a fixed period of time. To you to spot instance you must bid higher than the current spot price which is set by AWS. And this spot price fluctuates depending on supply and demand of the unused resource. If your bid price for an instance type is higher than the spot price, then you'll purchase that instance. But as soon as your bid price becomes lower than the fluctuating spot price, you will be issued a two-minute warning before the instance automatically terminates and is removed from your AWS environment. The bonus for spot instances is that you can bid for large EC2 instances at a very low cost point saving a huge amount on cost. Due to the nature of how the instances can be suddenly removed from your environment, spot instances are only useful for processing data and applications that can be suddenly interrupted. Such as batch jobs and background processing of data. 

CAPACITY RESERVATIONS 

allows you to reserve capacity for your EC2 instances based on different attributes. Such as instance type, platform and tenancy et cetera. Within a particular availability zone for any period of time. This ensures that you always have the available number of instances you require within a specific availability zone immediately. This capacity reservation could also be used in conjunction with your reserved instances discount providing you additional savings. 

3.4 Tenancy

Let me now talk to you about EC2 tenancy and this relates to what underlying host your EC2 instance will reside on. So essentially the physical server within an AWS data center. Again there are different options available to you with pros and cons to each. 

>> SHARED TENANCY: this option will launch your EC2 instance on any available host with the specified resources required for your selected instance type. Regardless of which other customers and users also have EC2 instances running on the same host, hence the share tenancy name. AWS implement advanced security mechanisms to prevent one EC2 instance from accessing another on the same host. How the security is applied and operated is out of scope of this course and it is maintained by AWS themselves. 

>> DEDICATED TENANCY: this includes both dedicated instances and dedicated hosts. Dedicated instances are hosted on hardware that no other customer can access. It can only be accessed by your own AWS account. You may be required to launch your instances as a dedicated instance due to internal security policies or external compliance controls. Dedicated instances do incur additional charges due to the fact you are preventing other customers from running EC2 instances on the same hardware and so there will likely be unused capacity remaining. However the hardware might be shared by other resources you have running in your own account. 

>> DEDICATED HOST: a dedicated host is effectively the same as dedicated instances. However they offer additional visibility and control, how you can place your instances on the physical host. They also allow you to use your existing licenses, such as PA-VM license or Windows Server licenses et cetera. Using dedicated hosts give you the ability to use the same host for a number of instances that you want to launch and align with any compliance and regulatory requirements. If you don't need to address any compliance or security issues that require dedicated tenancy, then I recommend using shared tenancy to reduce your overall costs. 

3.5 User Data 

USER DATA: during the configuration of your EC2 instance there is a section called user data. Which allows you to enter commands that will run during the first boot cycle of the instance. This is a great way to automatically perform functions upon boot, such as to pull down any additional software you want installing from any software repositories you may have. You could also download and get the latest OS updates during boot. For example you could enter

yum -y update

(yum update dash y) for a Linux instance which will then update its own software automatically at the time of boot. 

3.6 Storage options

STORAGE OPTIONS: as a part the configuration when setting up an EC2 instance, you are asked to select and configure your storage requirements. 

Selecting storage for your EC2 instance will depend on the instance selected, what you intend to use the instance for and how critical the data is. Storage for EC2 can be classified between two distinct categories, PERSISTENT STORAGE and EPHEMERAL STORAGE (EPHEMERAL meaning TEMPORARY).

* PERSISTENT storage is available by attaching elastic block storage EBS (Elastic Block Storage) volumes. 

* And a EPHEMERAL storage is created by some EC2 instances themselves using a local storage on the underlying host known as INSTANCE BACK STORAGE. 

Let's look at each of these storage options in greater depth. 

>> PERSISTENT: EBS volumes are separate devices from the EC2 instance itself. And so it's not physically attached like ephemeral storage is. EBS volumes are considered network attached storage devices which are then logically attached to the EC2 instance via the AWS network. This principle IS NOT DISSIMILAR to attaching an external hard disk to your home laptop or PC. With the external hard disk represent your EBS volume and your PC represents your EC2 instance. The data on EBS volumes are automatically replicated to other EBS volumes within the same availability zone for resiliency which is managed by AWS. You can disconnect an EBS volume from your EC2 instance and the data will remain intact. Allowing you to reattach it to another EC2 instance if required. You can also implement encryption on these volumes if needed and take backup snapshots of all the data on the volume to S3. EBS volumes can be created in different sizes again with different performance capabilities depending on your requirements. 

>> EPHEMERAL: Ephemeral storage or instance backed storage is the storage that is physically attached to the underlying host on which the EC2 instance resides on. Looking back at our previous example, this would be similar to your own laptop or PC's hard disk. There is a difference here though, with AWS EC2 instances as soon as the instance is stopped or terminated all saved data on a ephemeral storage is lost. If you reboot your instance then the data will remain but not if you stop it. Therefore if you have data that you need to retain it is not recommended that you use instance backed storage for this data. Instead use EBS volumes for persistent data storage. Unlike EBS volumes you are unable to detach ephemeral instance store volumes from the instance. 

3.7 Security

Security, security is fundamental with any AWS deployment. As so I just want to highlight a couple of points relating specifically to EC2 security. Firstly and during creation of your EC2 instance you will be asked to select a security group for your instance. A security group is essentially an instance level firewall allowing you to restrict both ingress and egress traffic by specifying what traffic allowed to communicate with it. You can restrict this communication by source ports and protocols for both inbound and outbound communication. Your instances are then associated with this security group. More information on security groups can be found in my blog post, found here covering instance level security. At the very end of your EC2 instance creation, you will need to select an existing key pair or create and download a new one. But what is a key pair and what is it used for? A key pair, as the name implies, is made up of two components, a public key and a private key. The function of key pairs is to encrypt the login information for Linux and Windows EC2 instances. And then decrypt the same information allowing you to authenticate onto the instance. The public key encrypts data such as the username and password. For Windows instances, the private key is used to decrypt this data allowing you to gain access to the login credentials including the password. For Linux instances the private key is used to remotely connect onto the instance via SSH. The public key is held and kept by AWS, and the private key is your responsibility to keep and ensure that it is not lost or compromised. So going back to when you create your EC2 instance and a new key pair. You're given the opportunity to download the key pair, once you have done this you must keep that file safe until you're ready to log on to the associated EC2 instance. It's worth noting that you can use the same key pair on multiple instances to save you managing multiple private keys. Do bear in mind however should the private key become compromised access could be gained to all the instances where that key pair was used. Once you have authenticated to the EC2 instance the first time, you can set up additional less privileged access controls such as local windows accounts allowing other users to connect and authenticate to or even utilize Microsoft Active Directory. One final point regarding security on your EC2 instance it is your responsibility to maintain and install the latest OS and security patches released by the OS vendor as dictated within the AWS shared responsibility model. More information on this can be found in this blog post. 

4. DEMO: Creating your first EC2 instance

We have now covered the main elements of the EC2 service that should hopefully allow you to get started by creating your first EC2 instance and selecting the most appropriate configuration for your needs. But to reiterate what we have covered and make it all fit together, I will demonstrate how to create a new EC2 instance from within the console, quickly highlighting the elements we have discussed as I go through. 

Okay so I'm logged into my AWS management console, and to start with we need to go to EC2 which is under the compute category. Now this take us to the EC2 console and from here we can simply select launch instance. Now this is the first stage of the configuration where we have to select our Amazon Machine Image, AMI. And here are a number of AWS AMIs that they supply, covering Windows, Red Hat, Linux et cetera. On the left hand side there's just a few other options if you've created any AMIs yourself that would be stored here. I mentioned the AWS marketplace earlier and here you can see lots of different AMIs from other suppliers such as Trend Micro, Juniper Networks, Barracuda et cetera. And also the community AMI as well. So let's get started with the Quick Start and look at some of the AWS supplied AMIs and I'm just going to launch this Amazon Linux box. So I'll select that as my AMI, now we get to choose instance type. And we can filter up here with different types of instance types, general purpose, computer optimized et cetera. Just going to leave it as all, and then down here we can see the different families and the types, the vCPUs, memory et cetera that each of these has. So I'm going to leave it on the T2 micro general purpose instance. 

So I'm going to select next configure instance details. Now I have a number of options here, the number of instances that we want to launch. I'm just going to keep it as one. If we want to launch this as a spot instance then we can select this box here to do so. But I'm just going to create it as an on-demand instance. We can select VPC that we want to run it in and we'll have different VPCs there. You can then select the subnet if you'd like. And if you'd like to auto-assign a public IP address. We can assign a role to an EC2 instance if we need to and we can also control the shutdown behavior. So when we shut down all EC2 instance, do you want to terminate that instance or just stop. I'm going to leave that as a default or stop. There's a couple of other controls you can put in here, enable termination protection. And what that will do, that will prevent you from terminating your instance until you uncheck this box. And you can also enable detail cloud watch monitoring if you need to. With regards to tenancy we discussed this earlier rather we shared or one of the dedicated instance or on a dedicated host, I'm going to leave that as shared. I'll leave all the other options as default and then I'll click on next to go to storage. This shows the current storage that comes with the AMI. We consider there's 8 gig in size and it's a general-purpose SSD drive. It's a tick box here to delete the volume on termination and we can see that it's not encrypted. If we wanted to add a new volume, we can add an EBS volume here. Again we can specify the size, eight gig or if you want to add it to 30 for example. And then we can also again delete on termination and we have the option to encrypt the EBS volume if we wanted to it's by selecting the default AWS EBS encryption key. So now we have two drives, one of them is the root volume and an additional drive which is an EBS volume. 

Click on next add tags, here we can add a key value pair tag to this instance. So for example a key of name and a value of my instance. And we can add additional tags as well as you can see here we can add up to 50 tags if we wanted to. So we can add a project that it belongs to or the cost et cetera, any tags that make it more usable to you. Once you've finished adding your tags click on configure security group. And this is where we control what can and can't access your instance. You can create a new secure group or select an existing security group that you might already have. If we create a new security group and call it My Security Group, then you can add a description. And here are the rules for the security group. So at the moment we have SSH using TCP across port 22 and can you have the source as a custom IP address range or a single IP address. So you might just want a specific subnet in your VPC to talk to this instance or you can have anywhere, or you can have just your own IP address. Let's put in a custom IP address range of 10.0.1.0/24. And again you can add a description in there if you want to. You can add a new rule, for example HTTP traffic. And again you can add your source, cite anywhere then once you're happy with your security groups click on review and launch. And this just provides a summary of all the configuration options that you've made up to this point. If you need to edit any other details you can just click on the right hand side here, edit the instance type the security groups et cetera. Once you're happy with all of your information click on launch. And this is where you can select or create a new key pair to connect your instance. 

So let's go ahead and create a new key pair, call it My Instance, and now I need to download this key pair. Which will download the private part, once that key pair is downloaded I can then click on launch instance. Now if we go back to our dashboard by clicking on view instances. We can see here that it's trying to launch at the minute, the status is pending and it shouldn't take too long for that to become active. And here we go we can now see it's up and running. 

Before I finish this demonstration I just want to point out one last point relating to status checks that we can see from within our EC2 dashboard. These status checks are used to check the health and status of your EC2 instance and understanding what kind of faults could trigger these checks to fail. Kinda help you troubleshoot issues with your EC2 resources. There are two types of status checks. System status checks and instant status checks. If the system status check fails then it is likely to be an issue with the underlying host rather than a configuration issue with your EC2 instance. Common issues that trigger system status checks to fail are loss of power, loss of network connectivity and hardware and software issues on the underlying host. Basically a system status check failure is out of our control as the fault lies with components that AWS are responsible for. The best way to resolve this will be to stop the instance and restart. This is likely to cause the instance to launch on another physical host resolving the problem. Do not reboot the instance as this will cause the instance to continue running on the same physical server. Instance data checks, these differ from system status checks as if this fails then it would likely require your input to help them resolve the issue. This check looks at the EC2 instance itself, rather than focusing on the underlying hosts. Common issues that trigger this checks to fail are incorrect network configuration, corrupted file systems, exhausted memory or incompatible kernel. These faults will require you to troubleshoot and resolve the issue, for example changing the network configuration. If you'd like some hands-on experience with EC2, then we do offer two labs in which you can practice creating your own EC2 instances for both Linux and Windows. 

That now brings me to the end of this lecture on EC2, like I mentioned previously this is going to be the longest and most in-depth lecture, simply due to how much of a key compute service it is in a wide range of use cases.




>> Next steps 

 ####### #######    ######  ####### 
    #    #     #    #     # #     # 
    #    #     #    #     # #     # 
    #    #     #    #     # #     # 
    #    #     #    #     # #     # 
    #    #     #    #     # #     # 
    #    #######    ######  ####### 
                                    

--> the below is still not started

Table of Contents:
1. Introduction
2. What is Compute in AWS?
3. EC2 - Elastic Compute Cloud 
ECS - Elastic Container Service
ECR - Elastic Container Registry 
EKS - Elastic Container Service for Kubernetes
AWS Elastic Beanstalk
AWS Lambda
AWS Batch
Amazon Lightsail





