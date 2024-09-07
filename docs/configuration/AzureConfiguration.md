# Azure Configuration

## Key Vault
The Key Vault secrets are created for you as part of the deployment process, however their values are not set.  This section will walk you thorough the keys and how they should be set.

1. Key Vault Access
   - Ensure that your user account is in the proper RAC Role to manage secrets in the Key Vault.  Add your user to the Key Vault Secrets Officer Role for the key Vault and wait for the permissions to propogate.  After you have been assigned this role, you can proceed with the following steps.

2. Key Vault Secrets
   - **SftpUserName:** Create a new version and set the value to be the user name that your institution has ssigned to you.
   - **SftpUrl:** Create a new version and set the value to be the URL of the PRODUCTION SFTP lockbox site.
   - **SftpTestUrl:** Create a new version and set the value to be the URL of the VALIDATION or TEST SFTP lockbox site.
   - **SftpKeyFile:** This one requires a little different procedure in order to get your key file into the secret. There are several way to accomplish this task and we encourage you to use the method that you are most comfortable with.  The steps that follow seem to be the most straight forward, but if you have a more preferred method, please use that instead.

     - Open a cloud shell in the Azure Portal
     - Upload your key file using the file upload feature.  This uploads the key file into the current cloud shell's storage (which may be temporary).

     ![File upload screenshot](/assests/FileUpload.png)

     - Run the following Azure command line command in the cloud shell: `az keyvault secret set –vault-name <name of key vault> –name SftpKeyFile –file <private ssh key > –encoding ascii`

