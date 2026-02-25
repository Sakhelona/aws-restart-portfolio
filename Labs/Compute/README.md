AWS EC2 Web Server Deployment Lab

In this lab, I deployed an EC2 instance to host a simple web server and enabled termination protection to prevent accidental deletion. I monitored system performance using AWS CloudWatch and configured security group rules to allow HTTP traffic for public access.

To simulate scaling in a real-world environment, I resized the EC2 instance to handle increased workloads and verified termination protection before safely terminating the instance at the end of the lab.

Task 1: Launching your EC2 instance
<img width="616" height="454" alt="image" src="https://github.com/user-attachments/assets/456c7e8d-756f-4197-9019-21790f4d06c4" />




Choosing an Amazon Machine Image (AMI)

I navigated to the EC2 launch page and selected the default Amazon Linux 2023 Amazon Machine Image (AMI). This AMI provides the operating system and requires configuration to create the EC2 instance. I kept the default Quick Start AMI since it is optimized for AWS services and commonly used for secure and reliable deployments

<img width="634" height="452" alt="image" src="https://github.com/user-attachments/assets/4978e979-eba6-4ba5-9a4a-44d157b6c4e1" />


Choosing an instance type

I selected the t3.micro EC2 instance type, which offers 2 vCPUs and 1 GB of memory, suitable for this lab setup.
<img width="629" height="421" alt="image" src="https://github.com/user-attachments/assets/8d2b3d50-8173-4550-a28b-966160d259c2" />



Configuring the network settings

I opened the Network settings pane and edited the configuration to select the Lab VPC as the network where the EC2 instance would be launched. I then created a new security group named Web Server security group and added a description to identify it as the firewall for my web server.

To improve security, I removed the default inbound SSH rule since remote login was not required for this lab. This ensured that only necessary traffic would be allowed to reach the instance.
<img width="940" height="182" alt="image" src="https://github.com/user-attachments/assets/c7e8db1f-0c2d-4865-a5ca-fbf9bc6318b5" />



Configuring advanced details

I expanded the Advanced details section and enabled Termination protection to prevent the EC2 instance from being accidentally deleted. I then added a User Data script to automatically configure the instance when it launched.

The script installed the Apache web server, set it to start automatically on boot, started the service, and created a simple web page displaying a welcome message. This allowed the web server to be ready for use as soon as the instance was running.
<img width="779" height="180" alt="image" src="https://github.com/user-attachments/assets/a8d298a2-39b8-4a82-874f-8e8559d6c540" />


Launching an EC2 instance

After completing all the EC2 configuration settings, I launched the instance by selecting Launch instance and then viewed it in the instances list. The instance initially appeared in a Pending state while it was being created and then changed to Running once it finished booting.

I selected the Web Server instance to view its details and reviewed the information in the Details, Security, and Networking tabs. I waited until the instance showed a Running state with 2/2 status checks passed, confirming that the server was fully operational and ready for use.

<img width="924" height="426" alt="image" src="https://github.com/user-attachments/assets/cb44a0e0-962d-4f56-aa84-7110f5ca5f6a" />


Monitor Your Instance

I selected the EC2 instance and navigated to the Status checks tab to monitor its health. Both the System reachability and Instance reachability checks had passed, confirming that the underlying AWS infrastructure and the instance itself were functioning properly.

I then opened the Monitoring tab to view the Amazon CloudWatch metrics associated with the instance. Since the instance was recently launched, only a few metrics were available. I expanded one of the graphs to see a detailed view of the performance data.

Lastly, I used the Monitor and troubleshoot option to retrieve the Instance Screenshot, which displays the instance’s console output as if a physical screen were attached, helping to verify that the system was running correctly.
<img width="909" height="470" alt="image" src="https://github.com/user-attachments/assets/407f4a0e-c569-4e03-bde0-6d539b53a5fd" />



Update Your Security Group and Access the Web Server

After launching the EC2 instance, I attempted to access the web server by copying the Public IPv4 address from the instance details and opening it in a web browser. At first, the web page did not load because the security group was not allowing inbound traffic on port 80, which is required for HTTP web access.
<img width="940" height="309" alt="image" src="https://github.com/user-attachments/assets/395dd273-275b-41c2-9bb5-dfdc95959b17" />



Resize Your Instance: Instance Type and EBS Volume

As part of managing resource usage, I reviewed the EC2 instance to understand how instance types can be adjusted when workloads change. Before making any size modifications, I stopped the Web Server instance by selecting Instance state and choosing Stop instance from the EC2 Management Console.
<img width="916" height="458" alt="image" src="https://github.com/user-attachments/assets/742e6389-263f-47c0-96a0-211b55c16364" />
