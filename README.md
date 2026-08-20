

# Set Up a Web App in the Cloud

**Project Link:** [View Project](http://nextwork.ai/projects/aws-devops-vscode)

**Author:** Adrian Nigel  
**Email:** adriannigel32@gmail.com

---

## Set Up a Web App Using AWS and VS Code

![Image](http://nextwork.ai/fulfilled_white_majestic_sea_otter/uploads/aws-devops-vscode_7a1de541)

---

## Introducing Today's Project!

In this project, I am going to launch an EC2 instance and connect to the instance via VS Code to generate a web app inside it. I'm working on this project to learn how to build a CI/CD pipeline from scratch that automates the build and deployment of a web app.

Side note: I chose VS Code due to its popularity, but I have also used the Linux Ubuntu terminal before, which I highly recommend if you are a DevOps engineer.

This project is part 1 of a series of DevOps projects where I'm building a CI/CD pipeline!

I did this project to enhance my DevOps skills.

### Key tools and concepts

Services I used were:
 -VS Code.
 -Amazon EC2
 Key concepts I learnt include:
 -SSH connections
 -Launching an Instance.

### Project reflection

This project took me approximately 3 hours, including troubleshooting. The most challenging part was connecting to the EC2 instance via VS Code since I was using WSL(Windows SubSystem For Linux), where you cannot connect to Linux and SSH to the server at the same time. It was most rewarding to see a successful connection to the EC2 instance.

One interesting thing I came across in this project was connecting to the EC2 instance host via VS Code.

---

## Launching an EC2 instance

### What I did in this step

In this step, I will:
- Launch a new EC2 instance.
- Set up a key pair for secure access.
- Set up network settings for the instance.

The network settings make sure we can find our EC2 instance, and the key-value pair permits us to access the EC2 instance.

I started this project by launching an EC2 instance because EC2 instances are like virtual computers that live in the cloud and we want our web app to live in the cloud.

![Image](http://nextwork.ai/fulfilled_white_majestic_sea_otter/uploads/aws-devops-vscode_7852fbf3)

### I also enabled SSH

SSH, i.e. Secure Shell, is a protocol used to make sure only authorized users can access a remote server.  I enabled SSH so that it can verify that I have the correct private key that matches the public key on the server.

SSH is also a type of network traffic. Once SSH has authorized me, it'll set up a secure connection between me and the EC2 instance. All data transferred (including your commands and the responses from the instance) gets encrypted. This encryption makes SSH an ideal method for working with virtual servers.

### Key pairs

A key pair is a way to connect to an EC2 instance that we launched on AWS. Key pairs work by having two halves, a public key that AWS keeps and a private key that we download to our computer. When we want to login to our EC2 instance, AWS matches the private key we give it to our public key.

### Downloaded key pair file

Once I set up my key pair, AWS automatically downloaded the private key file to my computer . I moved that private key file to a safe folder on my computer.

---

## Set up VS Code

### What I did in this step

In this step, I will:
-Set up a terminal in VS Code so I can communicate with the EC2 instance.
-Update my key pair's permission settings, so that I can use it to log into the EC2 instance later.


### What is VS Code?

VS Code is an IDE (Intergrated Development Environment). If not the most popular IDE🤖.

I installed VS Code to enable me to connect to the EC2 instance to write and edit code that will live inside the instance.

![Image](http://nextwork.ai/fulfilled_white_majestic_sea_otter/uploads/aws-devops-vscode_53d05e68)

---

## My first terminal commands

A terminal is a place where our computer receives our commands about what we want it to do. 
The first command I ran for this project is "cd Desktop/CODE_FOLDER/DevOps".

### Updating file permissions

I also updated my private key's permissions by running the commands:
-" icacls "nextwork-keypair.pem" /reset"
-"icacls "nextwork-keypair.pem" /grant:r "adrian nigel:R"
-"icacls "nextwork-keypair.pem" /inheritance:r"

This command gives me permission so that I can  use the file to connect to an EC2 instance.

![Image](http://nextwork.ai/fulfilled_white_majestic_sea_otter/uploads/aws-devops-vscode_9328ada1)

---

## SSH connection to EC2 instance

### What I did in this step

In this step, I will use the terminal in VS Code to connect to the EC2 instance that I created earlier. Then we can set up the web application.

### Connecting to EC2

To connect to my EC2 instance, I ran the command "ssh -i [path to private key] ec2-user@[IPv4 address to EC2 instance]".
This command sets up an SSH connection directly between my local computer and the instance.

### This command required an IPv4 address

A server's IPv4 DNS is the public address that identifies where the server lives in the cloud. It assists our computer in locating the EC2 instance that we launched.

![Image](http://nextwork.ai/fulfilled_white_majestic_sea_otter/uploads/aws-devops-vscode_e3069dca)

---

## Maven & Java

### What I did in this step

In this next step, I will;
-Install Apache Maven on your EC2 instance.
-Install Amazon Corretto 8, a version of Java.
-Verify the installations.

These tools are crucial in setting up a Java web app from scratch.

### Why I'm using Maven

Apache Maven is a tool that helps developers build and organize Java software projects. It is a package manager, which means it automatically downloads any external pieces of code your project depends on to work.

Maven is required in this project because we want to use its ability to spin up web apps using archetypes.

Archetypes are like templates to lay out the foundations for different types of projects e.g., web apps.

### Why I'm using Java

Java is a popular programming language used to build different types of applications, from mobile apps to large enterprise systems. We will be using it to develop our web app.

Java is required in this project because it lays the foundation for writing our web app code. Maven needs Java to run.

---

## Create the Application

### What I did in this step

In this step, I will generate my web app inside the EC2 instance using Maven and Java.

### Creating the Java web app

I generated a Java web app using the command [mvn archetype:generate -DgroupId=com.nextwork.app -DartifactId=nextwork-web-project -DarchetypeArtifactId=maven-archetype-webapp -DinteractiveMode=false
]

This command tells Maven to generate a web app using an existing template that it has and also tells Maven to call the generated web app.

### Installing Remote - SSH

I installed Remote - SSH, which is an extension in VS Code. I installed it to connect VS Code directly to the EC2 instance

### SSH configuration details

Configuration details required to set up a remote connection include:
-The host-EC2 instance address.
-The identity file-the location of our private key.
-The user we are logging in as for our instance

![Image](http://nextwork.ai/fulfilled_white_majestic_sea_otter/uploads/aws-devops-vscode_2939cf01)

---

## Create the Application

### Exploring the project structure

Using VS Code's file explorer, I could see a couple of folders and subfolder that define our webapp . These folders and subfolders have been organised into different parts of our app.

Two of the project folders created by Maven are src and webapp, which stores webapp files for the look of the webapp.Src is the parent folder that contains all the source code for the app.

![Image](http://nextwork.ai/fulfilled_white_majestic_sea_otter/uploads/aws-devops-vscode_45f91fd7)

---

## Using Remote - SSH

### What I did in this step

In this step, I will:
-Install an extension in VS Code.
-Use the extension to set up a connection between VS Code and your EC2 instance.
-Explore and edit your Java web app's files using VS Code.

 because...

### Updating the web app

The index.jsp is a file in our web app that defines both the HTML content and any code that goes into generating dynamic content(content that changes).

I edited index.jsp file by updating the code to also say "Hello World! I am Adrian" and also added a paragraph after.

![Image](http://nextwork.ai/fulfilled_white_majestic_sea_otter/uploads/aws-devops-vscode_7a1de541)

---

## Using nano

### Additional improvements

In this part, I will edit code without an IDE.

### Terminal vs IDE

This time I used the EC2 instance terminal to edit index.jsp, I ran the command "cd" to navigate to the index.jsp file then ran "nano index.jsp" to open the file in nano.

Compared to using an IDE, editing index.jsp in the terminal feels quicker and more remote-friendly. I like the terminal because it requires few resources. However, it has a steep learning curve for beginners.

### Verifying my work

To verify my editing work in the terminal, I opened the VS Code window that had my SSH connection to my EC2 instance. It was possible to see my changes in VS Code right away.

![Image](http://nextwork.ai/fulfilled_white_majestic_sea_otter/uploads/aws-devops-vscode_a3324ad41)

---

---
