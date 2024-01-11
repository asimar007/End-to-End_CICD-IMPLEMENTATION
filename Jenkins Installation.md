
# Jenkins

Here, The Jenkins Installation steps:-

## Installation on EC2 Instance

## AWS EC2 Instance

- Go to AWS Console

- Instances(running)

- Launch instances

![ec2.png](https://github.com/asimar007/Cross-Region-Migration-of-AWS-EBS-Volumes/blob/main/Screenshot/ec2.png?raw=true)

### Install Jenkins.

Pre-Requisites:

- Java (JDK)

### Run the below commands to install Java and Jenkins

Install Java

```

sudo apt update

sudo apt install openjdk-11-jre

```

Verify Java is Installed

```

java -version

```

Now, you can proceed with installing Jenkins

```

curl -fsSL https://pkg.jenkins.io/debian/jenkins.io-2023.key | sudo tee \

/usr/share/keyrings/jenkins-keyring.asc > /dev/null

echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \

https://pkg.jenkins.io/debian binary/ | sudo tee \

/etc/apt/sources.list.d/jenkins.list > /dev/null

sudo apt-get update

sudo apt-get install jenkins

```

**Note: ** By default, Jenkins will not be accessible to the external world due to the inbound traffic restriction by AWS. Open port 8080 in the inbound traffic rules as show below.

- EC2 > Instances > Click on <Instance-ID>

- In the bottom tabs -> Click on Security

- Security groups

- Add inbound traffic rules as shown in the image (you can just allow TCP 8080 as well, in my case, I allowed `All traffic`).

(![SG.png](https://github.com/asimar007/Cross-Region-Migration-of-AWS-EBS-Volumes/blob/main/Screenshot/SG.png?raw=true)

### Login to Jenkins using the below URL:

http://<ec2-instance-public-ip-address>:8080 [You can get the ec2-instance-public-ip-address from your AWS EC2 console page]

Note: If you are not interested in allowing `All Traffic` to your EC2 instance

1. Delete the inbound traffic rule for your instance

2. Edit the inbound traffic rule to only allow custom TCP port `8080`

After you login to Jenkins,

- Run the command to copy the Jenkins Admin Password -

```
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

- Enter the Administrator password

<img  width="1291"  alt="Screenshot 2023-02-01 at 10 56 25 AM"  src="https://user-images.githubusercontent.com/43399466/215959008-3ebca431-1f14-4d81-9f12-6bb232bfbee3.png">

### Click on Install suggested plugins

<img  width="1291"  alt="Screenshot 2023-02-01 at 10 58 40 AM"  src="https://user-images.githubusercontent.com/43399466/215959294-047eadef-7e64-4795-bd3b-b1efb0375988.png">

Wait for the Jenkins to Install suggested plugins

<img  width="1291"  alt="Screenshot 2023-02-01 at 10 59 31 AM"  src="https://user-images.githubusercontent.com/43399466/215959398-344b5721-28ec-47a5-8908-b698e435608d.png">

Create First Admin User or Skip the step [If you want to use this Jenkins instance for future use-cases as well, better to create admin user]

<img  width="990"  alt="Screenshot 2023-02-01 at 11 02 09 AM"  src="https://user-images.githubusercontent.com/43399466/215959757-403246c8-e739-4103-9265-6bdab418013e.png">

Jenkins Installation is Successful. You can now starting using the Jenkins

<img  width="990"  alt="Screenshot 2023-02-01 at 11 14 13 AM"  src="https://user-images.githubusercontent.com/43399466/215961440-3f13f82b-61a2-4117-88bc-0da265a67fa7.png">


