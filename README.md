# Secure Web Application Deployment with Ansible & AWS CLB

<h2>Project Overview</h2>
This project demonstrates a secure, automated cloud infrastructure deployment. As a Junior Cloud Engineer, I’ve architected a high-availability web environment using Ansible for configuration management and an AWS Classic Load Balancer (CLB) to distribute traffic across private EC2 instances.
<h2>Key Features</h2>
<li>Zero Public Exposure: Web servers reside in private subnets with no public IPs.</li>
<li>Secure Access: Infrastructure management via a Bastion Host using SSH ProxyJump.</li>
<li>Automated Provisioning: One-command deployment using Ansible playbooks.</li>
<li>High Availability: Traffic is managed through a Load Balancer, ensuring redundancy.</li>
<img width="1711" height="1800" alt="cloud drawio" src="https://github.com/user-attachments/assets/0b894c66-d199-461a-8262-983800265dc9" />

<h2> Architecture</h2>
The setup consists of:
<li> 1 Bastion Host: The only entry point for SSH management.</li>
<li>2 Private Web Servers: Running Nginx, accessible only via the Load Balancer or Bastion.</li>
<li>1 Classic Load Balancer (CLB): Handles incoming HTTP traffic and routes it to the healthy web instances.</li>

<h2>Note: While the initial requirement suggested an ALB, this implementation uses a CLB due to specific AWS account restrictions, achieving the same high-availability goal.</h2>

<h2>Business Scenario</h2>
I was tasked as a Junior Cloud Engineer to architect and deploy a secure web infrastructure for a growing company.

<h3>The Client's Requirements:</h3>
<li>Security: Implementation of a "Least Privilege" access model for all servers.</li>
<li>Automation: Eliminating manual configuration errors via Infrastructure as Code (IaC).</li>
<li>High Availability: Ensuring the application remains online even if a server fails.</li>
<li>Documentation: Providing a clear technical roadmap of the deployment.</li>

<h2> Quick Start</h2>
<h3>Prerequisites</h3>
<li>An AWS Account.</li>
<li>Ansible installed on your local machine.</li>
<li>SSH Key pair configured on AWS.</li>

<h3>1. Configuration</h3>
<li>Update your inventory.ini with your instance IPs and ensure your SSH config is set for ProxyJump</li>

<h3>2. Run the Playbook</h3>
<li>Execute the deployment to install Nginx and push the custom HTML templates:</li>
ansible-playbook -i inventory.ini deploy-nginx.yml

<h2>Project Structure</h2>
<li>ansible.sh: Shell script for environment bootstrapping.</li>
<li>deploy-nginx.yml: Main playbook for Nginx installation and service management.</li>
<li>inventory.ini: Lists the Bastion and Private Web Server details.</li>
<li>config: Custom SSH configuration for seamless connectivity.</li>
<h2> Learning Outcomes</h2>
<li>Automation: Eliminated manual server configuration, ensuring idempotency.</li>
<li>Security: Implemented the principle of least privilege by isolating web servers from the public internet.</li>
<li>Load Balancing: Observed real-time traffic distribution by refreshing the CLB DNS.</li>
<h2>Detailed Article</h2>
For a deep dive into the architecture diagrams, challenges faced, and a step-by-step walkthrough, check out my full write-up on:
 <a href = "https://medium.com/@RealKingHubs/how-i-deployed-a-secure-web-application-on-aws-a-practical-guide-for-junior-cloud-engineers-d84ac3553b8f">Medium</a> | <a href = "https://realkinghubs-blog.hashnode.dev/securing-web-apps-on-aws-essential-steps-for-junior-cloud-engineers">Hashnode</a>
