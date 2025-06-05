# Azure Configuration

## Key Vault
The Key Vault secrets are created for you as part of the deployment process, however their values are not set.  This section will walk you thorough the keys and how they should be set.

1. Key Vault Access
   - Ensure that your user account is in the proper RAC Role to manage secrets in the Key Vault.  Add your user to the `Key Vault Secrets Officer` Role for the key Vault and wait for the permissions to propogate.  After you have been assigned this role, you can proceed with the following steps.

2. Key Vault Secrets
   - **SftpUserName:** Create a new version and set the value to be the user name that your institution has assigned to you.
   - **SftpUrl:** Create a new version and set the value to be the URL of the PRODUCTION SFTP lockbox site.
   - **SftpTestUrl:** Create a new version and set the value to be the URL of the VALIDATION or TEST SFTP lockbox site.
   - **SftpKeyFile:** This one requires a little different procedure in order to get your key file into the secret. There are several ways to accomplish this task and we encourage you to use the method that you are most comfortable with.  The steps that follow seem to be the most straight forward, but if you have a more preferred method, please use that instead.

     - Open a cloud shell in the Azure Portal
     - Upload your key file using the file upload feature.  This uploads the key file into the current cloud shell's storage (which may be temporary).

     ![File upload screenshot](/assests/FileUpload.png)

     - Run the following Azure command line command in the cloud shell: `az keyvault secret set --name SftpKeyFile --vault-name {Key Vault Name} --file {Key File Name with extension} --encoding ascii`

## Function App
The Function App has several custom environment variables and settings that are configured as part of the deployment.  This section outlines those variable along with settings that can be useful for testing and / or troubleshooting.

- **CONNECTION_URL** This variable holds the ***name*** of the key vault secret to retrieve the SFTP service's url from.  During deployment this variable is set to use the **SftpTestUrl** secret.  Once you have tested the function against your provider's validation url, this variable should be changed to use the secret stored in the **SftpUrl** secret.

![Connection Url variable screenshot](/assests/Connection_url.png)

-  **KEY_VAULT_NAME** This variable holds the name of the key vault to retrieve secrets from.  During deployment this variable is set to be the name of the key vault which is deployed as part of this marketplace offer.

![Key vault name screenshot](/assests/Key_vault_name.png)

- **CORS** This function App setting normally needs to be updated if you are testing your app via the Azure portal.  If you are leveraging the Test/Run functionality within the Azure portal on the individual functions, you will normally receive an error unless the Azure portal has been allowed in the function app's CORS setting.  This can be done as shown in the following screenshot.  (The Azure portal also will list this in the rror that you receive when testing a function in this manner.)

![Cors setting screenshot](/assests/CORS_Setting.png)

