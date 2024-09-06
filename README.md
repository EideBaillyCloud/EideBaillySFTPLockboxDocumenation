![Eide Bailly SFTP Function App Logo](assests/SFTPLockbox350.png)

# Eide Bailly SFTP Lockbox Function Documentation

Thank you for your interest in the Eide Bailly SFTP Lockbox Function.  This Azure Fuction app will assist developers in your organization in connecting to a finanical insituation's lockbox SFTP site.  Currently, the solution only supports authentication via a user name and x509 certificate.  These credentials, along with the URL for the lockbox site, are securely stored in an Azure Key Vault which is deployed along with the function in the same resource group.

## Overview
The function app provides developers with three functions:
1. GetIpAddress
   - GET: 
   - Returns the static IP address of the function app which is configured during deployment.  This can be useful if you need to supply the function's IP address to your insitution for whitelisting on their firewall / server.

2. Get FileList
   - POST: { "Path": "path to your files from the root of the server" }

## Documentaiton

1. [Azure Deployment](docs/deployment/AzureDeployment.md)
2. [COnfiguration](docs/configuration/AzureConfiguration.md)
