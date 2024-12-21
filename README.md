
# Jenkins-for-DevOps


# This Repository is for Jenkins & CICD Practice 

This Repository is made to practice Jenkins to implement daily life scenarios of a Devops Engineer.

## Folders

#### 

| Folder Name | Technologies     | Useages & Description                       |
| :-------- | :------- | :-------------------------------- |
| `Java_Sample_App` | `Java Application` | A simple application which shows current time |
| `Python_Flask_App` | `Python Application` | A simple application which show health of the server |


 ![Jenkins Cycle](https://github.com/AliFareed0009/Jenkins-for-DevOps/blob/6d123048eb11b7400fec0843f9b673432b0f9395/Images/jenkins%20cycle.png)


# The Following are topics covered in this Repository

# Introduction to Jenkins
- Jenkins is an open-source automation server that enables the automation of software development processes. It provides a platform for building, testing,
and deploying applications in an efficient and automated manner. Jenkins is widely used in the industry due to its flexibility, extensibility, and large
community support. It supports various programming languages and integrates with popular tools and frameworks.

## Continuous Integration and Delivery (CI/CD): 
- CI/CD is a software development practice that involves automating the process of integrating code changes,
building applications, running tests, and deploying them to production. The primary goals of CI/CD are to increase productivity, improve software quality,
and enable rapid and frequent releases. Continuous Integration (CI) focuses on integrating code changes frequently, while Continuous Delivery (CD) ensures
that applications can be released at any time.

## CI/CD Pipeline Overview: 
- A CI/CD pipeline is a series of automated steps that code goes through from version control to production deployment. It consists
of multiple stages, each representing a specific task or set of tasks. Common stages include code compilation, unit testing, code analysis, artifact creation,
and deployment. Jenkins allows you to define and manage these stages, ensuring that the entire process is automated, consistent, and reproducible.


# Jenkins Architecture : 

 ![Jenkins Architecture](https://github.com/AliFareed0009/Jenkins-for-DevOps/blob/6d123048eb11b7400fec0843f9b673432b0f9395/Images/what-is-jenkins.webp)

# Jenkins Setup on VM

### Install Java
  
    sudo apt update
    sudo apt install
    openjdk-17-jre
    java -version

### Install Jenkins

    curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \ /usr/share/keyrings/jenkins-keyring.asc > /dev/null
    echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \ https://pkg.jenkins.io/debian-stable binary/ | sudo tee \ /etc/apt/sources.list.d/jenkins.list > /dev/null
    sudo apt-get update
    sudo apt-get install jenkins

# Declarative Pipline
- Declarative pipelines provide a more structured and simplified approach to defining pipelines in Jenkins.
- They offer better readability, maintainability, and reusability compared to scripted pipelines.

## Structure of a Declarative Pipeline:
### Stages and steps: 
- Defining the different stages of the pipeline and the tasks performed in each stage.
- Stages represent logical divisions in the pipeline, such as build, test, and deploy.
- Steps define the individual tasks within each stage, such as code checkout, compilation, testing, and deployment.

### Agent: 
- Specifying the execution environment for the pipeline, such as a specific Jenkins node or a container.
  - Agents allow pipelines to run on designated resources, providing control over where each stage or step executes.


## Building Blocks of Declarative Pipelines:
### Steps: 
- Overview of commonly used built-in steps for actions like code checkout, building, testing, and deployment.
  - Discuss steps like git, sh, npm, docker, JUnit, archive, deploy, etc.
- Environment variables: Using environment variables to store and access information throughout the pipeline.
  - Explain how to define and use environment variables within the pipeline script.
  - Discuss the use of environment variables for storing credentials, build numbers, and other useful data.
- Parameters: Defining parameters to make pipelines more flexible and customizable.
  - Discuss different parameter types (e.g., string, boolean, choice) and their usage.
  - Explain how to prompt users for input and use parameter values within the pipeline script.
- Post actions: Configuring post-build actions, such as sending notifications or publishing reports.
  - Explain how to use the post block to define actions that execute after the pipeline completes.
  - Discuss actions like always, success, failure, unstable, email, junit, slack, etc.

# Shared Libraries
- Pipeline has support for creating "Shared Libraries" which can be defined in external source control repositories and loaded into existing Pipelines.

 ![Jenkins Shared library](https://github.com/AliFareed0009/Jenkins-for-DevOps/blob/81f57bc114d9e76d65674ce7f78e2f028d9cd78a/Images/jenkins%20shared%20library.png)

# User Management in Jenkins ( Role Based )
- By default, when you create a user in Jenkins, it can access almost everything. In this guide, we will cover how you can create fine-grained roles for proper access control to Jenkins Server. To manage users and roles, you need to have the necessary administrative privileges. Here are the steps to manage users and roles in Jenkins:

- Create new user: navigate to Jenkins Dashboard → Manage Jenkins → Users → Create User. Enter the user name, password, full name and email-address and then click Create User button.

  ![user role 1](https://github.com/AliFareed0009/Jenkins-for-DevOps/blob/81f57bc114d9e76d65674ce7f78e2f028d9cd78a/Images/User%20roles/1.%20create%20user.webp)

- Download and install Role-based Authorization Strategy plugin: goto Manage Jenkins → Plugins → Available plugins and search for Role in the search box and in the dropdown list, select Role-based Authentication Strategy plugin, proceed by clicking on Install without restart.

  ![user role 2](https://github.com/AliFareed0009/Jenkins-for-DevOps/blob/6d123048eb11b7400fec0843f9b673432b0f9395/Images/User%20roles/2.%20role%20user.webp)

- Change authorization to Role-based strategy: After successful installation of plugin, Go to Manage Jenkins → Security and select the Role-Based Strategy under the Authorization section, click on Apply and Save.

  ![user role 3](https://github.com/AliFareed0009/Jenkins-for-DevOps/blob/6d123048eb11b7400fec0843f9b673432b0f9395/Images/User%20roles/3.%20role%20user.webp)

- Creating roles and granting privileges to role: go to Manage Jenkins → Manage and Assign Roles
  There are three options:
  1. Manage Roles
  2. Assign Roles and
  3. Role Strategy Macros

- Click on the manage role, you can see that there is only one role admin, but three sessions:
  1. Global roles
  2. Item roles
  3. Agent roles

- Global roles → provide authorization and access to the global level. Let’s create employee role and assign access like read, view, etc.

  ![user role 4](https://github.com/AliFareed0009/Jenkins-for-DevOps/blob/6d123048eb11b7400fec0843f9b673432b0f9395/Images/User%20roles/4.%20user%20role.webp)

- Item roles → provides roles specific to a project. For a particular project, you can assign permissions like build, create, delete, configure. Let’s create developer role and add pattern like dev.* ie. project name starting from dev.

 ![user role 5](https://github.com/AliFareed0009/Jenkins-for-DevOps/blob/6d123048eb11b7400fec0843f9b673432b0f9395/Images/User%20roles/5.%20role%20user.webp)

- Assigning role to users: go to Manage Jenkins → Manage and Assign Roles → Assign Roles

Global roles → add aashish and naba user to the global roles and assign the employee role to both users.

  ![user role 6](https://github.com/AliFareed0009/Jenkins-for-DevOps/blob/6d123048eb11b7400fec0843f9b673432b0f9395/Images/User%20roles/6.%20role%20user.webp)

- Project roles → add aashish and naba user to the item roles and assign aashish as a developer and naba as a qa

  ![user role 7](https://github.com/AliFareed0009/Jenkins-for-DevOps/blob/6d123048eb11b7400fec0843f9b673432b0f9395/Images/User%20roles/7.%20role%20user.webp)

- Login as user with assigned role. For any new user created without being assigned a role, access denied message should be shown.

  ![user role 8](https://github.com/AliFareed0009/Jenkins-for-DevOps/blob/6d123048eb11b7400fec0843f9b673432b0f9395/Images/User%20roles/8.%20role%20user.webp)


# Email Notification on Pipeline Fail / Pass

   ![email failure and success](https://github.com/AliFareed0009/Jenkins-for-DevOps/blob/6d123048eb11b7400fec0843f9b673432b0f9395/Images/email%20faliure.png)

# Mega_Projects

- CI/CD Project with Kubernetes, ArgoCD, Prometheus.
- DevSecOps with OWSAP, Trivy, Sonarqube.












