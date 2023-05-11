
#
# Installing Terraform onto your local machine

1. Open a Powershell window with admin and enter the following command: `Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))`
2. Once that command has completed, enter `choco install terraform`
- Terraform will now be installed
3. Once the installation is complete, enter `refreshenv` to refresh the variable
4. Close the powershell window and open a new git bash terminal
5. Use `terraform --version` to check the version
- You can use the command `terraform` to get a list of commands available

#
# Terraform Diagram:
![diagram](https://github.com/JakeGillatt/IaC_Terraform_Orchestration/assets/129315605/5b051225-6480-4c2d-bc0f-e684f3a11efd)

#
# Setting up the AWS keys/Variables for Terraform

1. In windows, go into 'Edit the system environment variables'
2. Select 'Environment variables'
3. In the 'User variables for' section, select 'New...'
4. Add the variable: Name: 'AWS_ACCESS_KEY_ID', Value: enter the access key
5. Add another variable: 'AWS_SECRET_ACCESS_KEY', Value: enter the secret access key
6. Once they are added, select Ok to close the window
7. In Powershell run `refreshenv` to reload the variables

#
# Setting up a main.tf file to launch an instance from an AMI

1. Open a new git bash terminal as admin
2. Create a main.tf file in your terraform directory (..documents/IaC/terraform), with `sudo nano main.tf`
3. Enter the following code into the file:
```
# who is the provider - AWS
# how to codify with terraform - syntax - name of resource {key = value} {sdfsdg}
# most commonly used commands - terraform init - terraform plan - terraform apply

provider "aws" {
        region = "eu-west-1"

}
# create a service on AWS
# which service? - EC2
resource "aws_instance" "app_instance" {
        # which ami to use? - ami i.d
        ami = "ami-YOUR-ID"
        # type of instance?
        instance_type = "t2.micro"
        # do you need the public ip?
        associate_public_ip_address = true
        # what would you like to name it?
        tags = {
            Name = "tech221_jake_terraform_app"
        }
}
```
4. Run the `terraform init` and check that it is successful
5. Run `terraform plan` to check which actions will be peformed
6. Run `terraform apply` to run the actions - this will launch an EC2 instance on AWS using the AMI we provided
- You can run `terraform destroy` to destroy the instance
