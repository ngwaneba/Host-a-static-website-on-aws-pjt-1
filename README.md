
# Hosting a Static Website on AWS

This DevOps project involves hosting a static HTML web app on AWS, leveraging various resources and best practices for scalability, reliability, and security. Below is an overview of the project, along with the key steps and configurations.

## Project Overview

The project utilizes the following AWS resources:

1. **Virtual Private Cloud (VPC):** Configured with public and private subnets across two availability zones for enhanced reliability.

2. **Internet Gateway:** Deployed to facilitate connectivity between VPC instances and the wider Internet.

3. **Security Groups:** Implemented as a network firewall mechanism to control inbound and outbound traffic.

4. **Availability Zones:** Leveraged two availability zones to enhance system reliability and fault tolerance.

5. **Public Subnets:** Used for infrastructure components like the NAT Gateway and Application Load Balancer.

6. **EC2 Instance Connect Endpoint:** Implemented for secure connections to assets within both public and private subnets.

7. **Private Subnets:** Positioned web servers (EC2 instances) for enhanced security.

8. **NAT Gateway:** Enabled instances in private subnets to access the Internet.

9. **Web Hosting:** The website is hosted on EC2 instances.

10. **Application Load Balancer (ALB):** Utilized for evenly distributing web traffic to an Auto Scaling Group of EC2 instances across multiple availability zones.

11. **Auto Scaling Group:** Manages EC2 instances automatically, ensuring website availability, scalability, fault tolerance, and elasticity.

12. **GitHub Repository:** Web files stored on GitHub for version control and collaboration.

13. **Certificate Manager:** Ensured secure communication using SSL/TLS certificates.

14. **Simple Notification Service (SNS):** Configured to alert about activities within the Auto Scaling Group.

15. **Route 53:** Registered the domain name and set up DNS records.

## Deployment Script

The following script automates the deployment of the web app on an EC2 instance:

```bash
#!/bin/bash
# Switch to the root user to gain full administrative privileges
sudo su
# Update all installed packages to their latest versions
yum update -y
# Install Apache HTTP Server
yum install -y httpd
# Change the current working directory to the Apache web root
cd /var/www/html
# Install Git
yum install git -y
# Clone the project GitHub repository to the current directory
git clone https://github.com/aosnotes77/host-a-static-website-on-aws.git
# Copy all files, including hidden ones, from the cloned repository to the Apache web root
cp -R host-a-static-website-on-aws/. /var/www/html/
# Remove the cloned repository directory to clean up unnecessary files
rm -rf host-a-static-website-on-aws
# Enable the Apache HTTP Server to start automatically at system boot
systemctl enable httpd
# Start the Apache HTTP Server to serve web content
systemctl start httpd
```

## Getting Started

Follow these steps to deploy the static website on AWS:

1. Clone this GitHub repository to your local machine.

2. Review the project's reference diagram for an overview of the AWS infrastructure.

3. Set up the required AWS resources as outlined in the deployment notes.

4. Customize the configuration files or environment variables to match your AWS setup and application requirements.

5. Execute the provided deployment script on your EC2 instance.

6. Access the deployed web app by navigating to the public IP address or DNS name of the EC2 instance in your web browser.

## Additional Notes

- **Security Considerations:** Ensure to follow AWS security best practices for a secure infrastructure.

- **Scaling:** Leverage Auto Scaling and Load Balancing for improved performance and reliability.






