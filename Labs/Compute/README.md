AWS EC2 Web Server Deployment Lab

In this lab, I deployed an EC2 instance to host a simple web server and enabled termination protection to prevent accidental deletion. I monitored system performance using AWS CloudWatch and configured security group rules to allow HTTP traffic for public access.

To simulate scaling in a real-world environment, I resized the EC2 instance to handle increased workloads and verified termination protection before safely terminating the instance at the end of the lab.

Task 1: Launching your EC2 instance



Choosing an Amazon Machine Image (AMI)

I navigated to the EC2 launch page and selected the default Amazon Linux 2023 Amazon Machine Image (AMI). This AMI provides the operating system and requires configuration to create the EC2 instance. I kept the default Quick Start AMI since it is optimized for AWS services and commonly used for secure and reliable deployments



Choosing an instance type

I selected the t3.micro EC2 instance type, which offers 2 vCPUs and 1 GB of memory, suitable for this lab setup.


Configuring the network settings

I opened the Network settings pane and edited the configuration to select the Lab VPC as the network where the EC2 instance would be launched. I then created a new security group named Web Server security group and added a description to identify it as the firewall for my web server.

To improve security, I removed the default inbound SSH rule since remote login was not required for this lab. This ensured that only necessary traffic would be allowed to reach the instance.


Configuring advanced details

I expanded the Advanced details section and enabled Termination protection to prevent the EC2 instance from being accidentally deleted. I then added a User Data script to automatically configure the instance when it launched.

The script installed the Apache web server, set it to start automatically on boot, started the service, and created a simple web page displaying a welcome message. This allowed the web server to be ready for use as soon as the instance was running.


Launching an EC2 instance

After completing all the EC2 configuration settings, I launched the instance by selecting Launch instance and then viewed it in the instances list. The instance initially appeared in a Pending state while it was being created and then changed to Running once it finished booting.

I selected the Web Server instance to view its details and reviewed the information in the Details, Security, and Networking tabs. I waited until the instance showed a Running state with 2/2 status checks passed, confirming that the server was fully operational and ready for use.



Monitor Your Instance

I selected the EC2 instance and navigated to the Status checks tab to monitor its health. Both the System reachability and Instance reachability checks had passed, confirming that the underlying AWS infrastructure and the instance itself were functioning properly.

I then opened the Monitoring tab to view the Amazon CloudWatch metrics associated with the instance. Since the instance was recently launched, only a few metrics were available. I expanded one of the graphs to see a detailed view of the performance data.

Lastly, I used the Monitor and troubleshoot option to retrieve the Instance Screenshot, which displays the instance’s console output as if a physical screen were attached, helping to verify that the system was running correctly.



Update Your Security Group and Access the Web Server

After launching the EC2 instance, I attempted to access the web server by copying the Public IPv4 address from the instance details and opening it in a web browser. At first, the web page did not load because the security group was not allowing inbound traffic on port 80, which is required for HTTP web access.


Resize Your Instance: Instance Type and EBS Volume

As part of managing resource usage, I reviewed the EC2 instance to understand how instance types can be adjusted when workloads change. Before making any size modifications, I stopped the Web Server instance by selecting Instance state and choosing Stop instance from the EC2 Management Console.
