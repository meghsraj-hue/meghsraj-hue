# Project 2-Jenkins Backup and Restore on AWS S3

**Source:** Original supplied project document. Technical steps and screenshots are reproduced for portfolio review.

**Before publishing:** Review every screenshot for credentials, IP addresses, customer information and private account details.

Course-End Project 2: Jenkins Backup and Restore on AWS S3

Project Title

Jenkins Backup and Restore on AWS S3 for Business Continuity

Objective

To implement a reliable backup and restore solution for Jenkins using AWS S3, ensuring protection of Jenkins job configurations, plugins, build history, and application data. This project automates backups and enables quick recovery in case of Jenkins server failure.

1. Project Description

TechNova Inc. uses Jenkins for Continuous Integration and Continuous Deployment (CI/CD). A recent Jenkins server crash caused the loss of critical job configurations and build data.

To prevent such incidents, a backup and restore mechanism is implemented using:

Jenkins Server

```text
AWS EC2
```

```text
AWS S3 Bucket
```

IAM Role/User

```text
AWS CLI
```

Shell Scripts

Cron Jobs

The solution automatically backs up the Jenkins Home Directory (/var/lib/jenkins) to AWS S3 and restores it whenever required.

2. Architecture Diagram

+-------------------+

|   Jenkins Server  |

|   (AWS EC2)       |

+---------+---------+

|

|

Backup Script

|

v

+-------------------+

| AWS CLI           |

+---------+---------+

|

|

v

+-------------------+

| Amazon S3 Bucket  |

| Jenkins Backups   |

+-------------------+

Restore Process

S3 Bucket

|

|

v

Jenkins Server

3. Prerequisites

```text
AWS Services
```

```text
AWS Account
```

EC2 Instance (Ubuntu 22.04)

S3 Bucket

IAM User or IAM Role

Software

Java 17

Jenkins

```text
Git
```

```text
AWS CLI
```

4. Task 1 – Create AWS EC2 Server and Install Jenkins

Step 1: Launch EC2 Instance

Navigate:

![Original project screenshot 1](screenshots/figure-001.png)

![Original project screenshot 2](screenshots/figure-002.png)

![Original project screenshot 3](screenshots/figure-003.png)

![Original project screenshot 4](screenshots/figure-004.png)

![Original project screenshot 5](screenshots/figure-005.png)

![Original project screenshot 6](screenshots/figure-006.png)

![Original project screenshot 7](screenshots/figure-007.png)

Step 2: Connect to EC2

```text
sudo apt update
```

```text
sudo apt upgrade -y
```

Then install Java:

```text
sudo apt install openjdk-17-jdk -y
```

check

java -version

![Original project screenshot 8](screenshots/figure-008.png)

![Original project screenshot 9](screenshots/figure-009.png)

![Original project screenshot 10](screenshots/figure-010.png)

Add Jenkins Repository Key

```text
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee /usr/share/keyrings/jenkins-keyring.asc > /dev/null
```

![Original project screenshot 11](screenshots/figure-011.png)

Add Jenkins Repository

```text
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian-stable binary/ | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null
```

![Original project screenshot 12](screenshots/figure-012.png)

Update Package List

![Original project screenshot 13](screenshots/figure-013.png)

Check Jenkins Installation

![Original project screenshot 14](screenshots/figure-014.png)

Start Jenkins:

![Original project screenshot 15](screenshots/figure-015.png)

Verify Jenkins Service

![Original project screenshot 16](screenshots/figure-016.png)

Jenkins Home is

![Original project screenshot 17](screenshots/figure-017.png)

Create the S3 Bucket

![Original project screenshot 18](screenshots/figure-018.png)

![Original project screenshot 19](screenshots/figure-019.png)

![Original project screenshot 20](screenshots/figure-020.png)

Create IAM User

IAM

→ Users

→ Create User

![Original project screenshot 21](screenshots/figure-021.png)

![Original project screenshot 22](screenshots/figure-022.png)

![Original project screenshot 23](screenshots/figure-023.png)

Attach IAM Role to EC2

This is the correct AWS way.

Steps:

Go to AWS Console → EC2

Select your instance: ip-172-31-29-216

```text
Click:
Actions → Security → Modify IAM Role
```

Attach or create a role with permissions like:

AmazonS3FullAccess (if needed)

or custom policy for your use case

Save

![Original project screenshot 24](screenshots/figure-024.png)

![Original project screenshot 25](screenshots/figure-025.png)

![Original project screenshot 26](screenshots/figure-026.png)

![Original project screenshot 27](screenshots/figure-027.png)

![Original project screenshot 28](screenshots/figure-028.png)

Restore command

```text
aws s3 cp jenkins-backup.tar.gz s3://jenkins-backup-project-2026/
```

![Original project screenshot 29](screenshots/figure-029.png)

![Original project screenshot 30](screenshots/figure-030.png)

![Original project screenshot 31](screenshots/figure-031.png)

Final Remaining Step (Restore Validation)

On your EC2 terminal run:

```text
mkdir restore-test
tar -xzvf jenkins-backup.tar.gz -C restore-test
```

Then verify:

```text
ls restore-test/var/lib/jenkins/jobs
```

Expected:

BackupJob

Take a screenshot.

That screenshot proves the restore process works.

![Original project screenshot 32](screenshots/figure-032.png)

![Original project screenshot 33](screenshots/figure-033.png)

![Original project screenshot 34](screenshots/figure-034.png)

Final Project Status

![Original project screenshot 35](screenshots/figure-035.png)

Backup Creation

tar -czvf jenkins-backup.tar.gz /var/lib/jenkins

✅ Backup archive created

![Original project screenshot 36](screenshots/figure-036.png)

After backup creation:

```text
ls -lh jenkins-backup.tar.gz
```

![Original project screenshot 37](screenshots/figure-037.png)

Conclusion

The Jenkins Backup and Restore on AWS S3 project was successfully implemented to ensure reliable protection and recovery of Jenkins application data. An AWS EC2 instance was provisioned, and Jenkins was installed and configured as the CI/CD server. Jenkins service availability was verified through system and network checks, and Jenkins configuration data was stored in the Jenkins home directory.

A backup strategy was implemented by creating a compressed archive of the Jenkins home directory, which contains job configurations, plugins, user settings, and system configuration files. Amazon S3 was configured as the backup repository, providing secure and durable storage for backup data. AWS IAM policies and roles were created to support secure access management, and AWS authentication was validated using AWS CloudShell.

The backup process was successfully demonstrated by creating and uploading backup files to the S3 bucket. The restore process was validated by extracting the backup archive and verifying recovery of Jenkins job data. Successful restoration of the Backup Job confirmed that Jenkins configuration and application data can be recovered in the event of server failure.

Jenkins UI was not shown because at last:

This project demonstrates an effective backup and disaster recovery solution using Jenkins, AWS EC2, Amazon S3, IAM, and AWS CLI. The implemented solution improves data protection, reduces recovery time, and supports business continuity requirements for modern DevOps environments.

During project execution, Jenkins service was successfully installed and verified at the operating system level using systemctl and network port validation commands. Although the Jenkins web console was not consistently accessible due to environment and network restrictions within the lab setup, all Jenkins configuration files, job definitions, and service data were successfully backed up and restored. The project objectives of backup creation, S3 storage integration, and restore validation were fully achieved and verified through command-line and system-level testing.

## Tables and recorded configurations

### Source table 1
Task | Status
EC2 Instance Created | ✅
Java Installed | ✅
Jenkins Installed | ✅
Jenkins Service Running | ✅
Port 8080 Listening | ✅
Jenkins Home Verified | ✅
BackupJob Created | ✅
AWS CLI Installed | ✅
Jenkins Backup Archive Created | ✅

### Source table 2
Requirement | Status
Launch EC2 Instance | ✅
Configure Security Group (22,8080) | ✅
Install Java | ✅
Install Jenkins | ✅
Verify Jenkins Running | ✅
Create Jenkins Job (BackupJob) | ✅
Create Backup Archive | ✅
Install AWS CLI | ✅
Create S3 Bucket | ✅
Create IAM Policy | ✅
Create IAM Role | ✅
Configure Trust Relationship | ✅
Verify AWS Authentication (CloudShell) | ✅
Upload File to S3 | ✅
Verify File in S3 | ✅
Restore Jenkins Backup | ✅
Verify Recovered Job | ✅
Jenkins Server; systemctl status jenkins; ss -tulnp | grep 8080; ✅ Jenkins installed and running | 
