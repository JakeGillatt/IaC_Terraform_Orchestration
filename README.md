
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
# Setting up the AWS keys/Variables for Terraform

1. In windows, go into 'Edit the system environment variables'
2. Select 'Environment variables'
3. In the 'User variables for' section, select 'New...'
4. Add the variable: Name: 'AWS_ACCESS_KEY_ID', Value: enter the access key
5. Add another variable: 'AWS_SECRET_ACCESS_KEY', Value: enter the secret access key
6. Add another variable: 'AWS_DEFAULT_REGION', Value: eu-west-1
7. Once they are added, select Ok to close the window
