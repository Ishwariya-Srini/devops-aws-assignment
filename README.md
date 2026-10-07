# devops-aws-assignment
# DevOps AWS Infrastructure & CI/CD Assignment

## 1. Project Overview

This project demonstrates a DevOps workflow for deploying a web application using Docker, Terraform, and GitHub Actions.

The project includes:

* Application containerization using Docker
* Infrastructure definition using Terraform
* CI/CD automation using GitHub Actions
* Terraform formatting and validation
* Docker image build and application testing
* HTTPS application hosting using GitHub Pages

## 2. Live Application

The application is available over HTTPS:

https://ishwariya-srini.github.io/devops-aws-assignment/

The application displays:

**Hello from DevOps Application!**

## 3. Project Architecture

```text
Developer
    |
    | Git Push
    v
GitHub Repository
    |
    v
GitHub Actions
    |
    +----------------------+
    | |
    v v
Docker Build Terraform
    | Init / Format
    v / Validate
Docker Test |
    | |
    +----------+----------+
               |
               v
        Successful CI Pipeline
               |
               v
       HTTPS Application
        GitHub Pages
```

## 4. Technologies Used

* GitHub
* Git
* GitHub Actions
* Docker
* Terraform
* AWS Terraform Provider
* Nginx
* GitHub Pages

## 5. Project Structure

```text
devops-aws-assignment/
│
├── app/
│ ├── Dockerfile
│ └── index.html
│
├── terraform/
│ ├── main.tf
│ ├── variables.tf
│ ├── output.tf
│ └── .terraform.lock.hcl
│
├── .github/
│ └── workflows/
│ └── ci-cd.yml
│
├── docs/
│
├── index.html
├── README.md
└── .gitignore
```

## 6. Application

The application is a simple HTML web application served using Nginx.

### Dockerfile

The Dockerfile uses the lightweight Nginx Alpine image and copies the application HTML file into the Nginx web root.

The container exposes port 80.

### Build Docker Image

```bash
docker build -t devops-app ./app
```

### Run Application Locally

```bash
docker run -d -p 8080:80 --name devops-app devops-app
```

The application can then be accessed at:

```text
http://localhost:8080
```

## 7. Terraform Infrastructure

Terraform is used to define the AWS infrastructure as code.

The Terraform configuration defines an EC2 instance with:

* AWS region
* AMI ID
* Instance type
* EC2 resource
* Instance ID output
* Public IP output

Example instance type:

```text
t2.micro
```

### Terraform Commands

Initialize Terraform:

```bash
cd terraform
terraform init
```

Format Terraform files:

```bash
terraform fmt
```

Validate Terraform configuration:

```bash
terraform validate
```

Terraform validation was successfully completed.

## 8. GitHub Actions CI/CD

The GitHub Actions workflow automatically runs when code is pushed to the `main` branch or when a pull request is created.

### Build Application

The pipeline:

1. Checks out the repository
2. Builds the Docker image
3. Starts the Docker container
4. Tests the application using curl
5. Stops and removes the test container

### Terraform Validation

The pipeline:

1. Checks out the repository
2. Installs Terraform
3. Runs Terraform initialization
4. Checks Terraform formatting
5. Validates the Terraform configuration

## 9. CI/CD Pipeline

```text
Git Push
   |
   v
Checkout Code
   |
   +-------------------+
   | |
   v v
Docker Build Terraform Init
   | |
   v v
Docker Test Terraform Format
                       |
                       v
                  Terraform Validate
                       |
                       v
                  Pipeline Success
```

## 10. AWS Infrastructure

The Terraform configuration is designed to provision an AWS EC2 instance.

Because an AWS account was not available for this assignment, the infrastructure was not provisioned in a live AWS environment.

Instead:

* Terraform configuration was created
* Terraform provider was initialized
* Terraform formatting was checked
* Terraform validation was successfully completed
* No AWS resources were actually created

This demonstrates the Infrastructure-as-Code configuration without creating AWS resources.

## 11. HTTPS Deployment

The static application is published using GitHub Pages.

GitHub Pages provides HTTPS access to the application.

Live URL:

https://ishwariya-srini.github.io/devops-aws-assignment/

## 12. Security Considerations

* Terraform state files are excluded using `.gitignore`
* Terraform provider files are excluded from Git
* No AWS credentials are stored in the repository
* Sensitive environment files are excluded
* GitHub Actions is used for automated validation

## 13. Conclusion

This project demonstrates a basic end-to-end DevOps workflow using GitHub, Docker, Terraform, and GitHub Actions.

The application is containerized, tested through CI, Terraform infrastructure is validated, and the application is available through an HTTPS URL.
