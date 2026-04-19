# Networking Assignment

## 1. Buy a domain
- My domain U-hamza.co.uk was bought from cloudfare as this was a cheaper option. A typical domain costs around $5.

## 2. Launching and EC2 instance
- Set up an AWS account if you don't already have one. Standard packages are free unless upgraded.
- Click on AWS management control and navigate to Amazon EC2.
- Select launch an instance.

  

<img width="1220" height="715" alt="Screenshot 2026-04-18 at 17 49 03" src="https://github.com/user-attachments/assets/139e26e0-006e-442e-8083-0626f7899a0f" />


<br/>



- There is a walkthrough option availabe which recommends default settings for running an instance.
- The settings I used were:
    - AMI: Amazon Linux 2
    - Instance type: t3.micro (free)
    - Key pair: create/download one (you’ll need it to SSH)

- Then:
Under Security Group, allow:
SSH (port 22)
HTTP (port 80)
HTTPS (port 443) (optional but recommended)

## 3. Install and run NGINX:
- Open your terminal and run this command: ssh -i your-key.pem ec2-user@YOUR_PUBLIC_IP   (USE YOUR KEY PAIR FROM THE PREVIOUS STEP AND YOUR PUBLIC ID)
- Install these commands:
    - sudo yum update -y
    - sudo amazon-linux-extras install nginx1 -y
    - sudo systemctl start nginx
    - sudo systemctl enable nginx

- Test it:
    Go to your browser and type: <br/>
     http://YOUR_PUBLIC_IP  ----> You should then see the NGINX welcome page


<img width="1420" height="631" alt="Screenshot 2026-04-17 at 23 28 17" src="https://github.com/user-attachments/assets/93521f9a-8ffd-4438-85ad-b5932f54cb98" />






## 4. Configure DNS (Create A record)

- Go to your DNS provider (In my case cloudfare)
- Go to DNS and then add record.
- A record settings:
    - Type: A
    - Name: @ ( @ is used for root)
    - Ipv4 address: copy your value in from your EC2 instance.
    - Proxy status: DNS only
    - TTL: Auto
- Save and add record



<img width="1104" height="465" alt="Screenshot 2026-04-19 at 12 23 52" src="https://github.com/user-attachments/assets/7413134e-35bf-45e5-b2e6-ec9a82253fa3" />


<br/>

- You can also do another A record and set name: WWW (This will allow you to run your domain with www. as well)

<img width="1090" height="269" alt="Screenshot 2026-04-19 at 12 24 16" src="https://github.com/user-attachments/assets/b5f221de-5050-477b-b124-a2e02dbb0514" />

<br/>



