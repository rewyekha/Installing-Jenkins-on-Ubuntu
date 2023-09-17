# 1. Installing Jenkins

First, update the default packages lists for upgrades with the following command:

```bash
sudo yum update –y
```

Then, Add the Jenkins repo using the following command:

```bash
sudo wget -O /etc/yum.repos.d/jenkins.repo \
    https://pkg.jenkins.io/redhat-stable/jenkins.repo
```

Now, Import a key file from Jenkins-CI to enable installation from the package:

```bash
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
```

```bash
sudo yum upgrade
```

Install Java (Amazon Linux 2):

```bash
sudo amazon-linux-extras install java-openjdk11 -y
```
Install Java (Amazon Linux 2023):

```bash
sudo dnf install java-11-amazon-corretto -y
```

finally!!!!, Install Jenkins:

```bash
sudo yum install jenkins -y
```

Enable the Jenkins service to start at boot:

```bash
sudo systemctl enable jenkins
```

Start Jenkins as a service:

```bash
sudo systemctl start jenkins
```

check the status of the Jenkins service using the command:

```bash
sudo systemctl status jenkins
```

All Set! You can now start automating...

# 2. How to Configure and Run Jenkins

i. Connect to http://<your_server_public_DNS>:8080 from your browser. You will be able to access Jenkins through its management interface:

ii. To check the initial password, use the cat command as indicated below:

```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

iii. The Jenkins installation script directs you to the # Customize Jenkins page. Click # Install suggested plugins.

iv. Once the installation is complete, the Create First Admin User will open. Enter your details, and then select Save and Continue.

v. On the left-hand side, select Manage Jenkins, and then select Plugins.

vi. Select the Available tab, and then enter Amazon EC2 plugin at the top right.

vii. Select the checkbox next to Amazon EC2 plugin, and then select Install without restart.

viii. Once the installation is done, select Back to Dashboard.

ix. Select Configure a cloud if there are no existing nodes or clouds.

x. If you already have other nodes or clouds set up, select Manage Jenkins.

xi. After navigating to Manage Jenkins, select Configure Nodes and Clouds from the left hand side of the page.

xii. Select Configure Clouds

xiii. Select Add a new cloud, and select Amazon EC2. A collection of new fields appears.

# 3. Click Add under Amazon EC2 Credentials

a. From the Jenkins Credentials Provider, select AWS Credentials as the Kind.

b. Scroll down and enter in the IAM User programmatic access keys with permissions to launch EC2 instances and select Add.

c. Scroll down to select your region using the drop-down, and select Add for the EC2 Key Pair’s Private Key.

d. Scroll down and select Enter Directly under Private Key, then select Add.

e. Open the private key pair you created in the creating a key pair step and paste in the contents from "-----BEGIN RSA PRIVATE KEY-----" to "-----END RSA PRIVATE KEY-----". Select Add when completed.

f. Scroll down to "Test Connection" and ensure it states "Success". Select Save when done

You are now ready to use EC2 instances as Jenkins agents!!!!!!!!!!!!
