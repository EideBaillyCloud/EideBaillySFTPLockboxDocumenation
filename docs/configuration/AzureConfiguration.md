# Azure Configuration

## Key Vault
The Key Vault secrets are created for you as part of the deployment process, however their values are not set.  This section will walk you thorough the keys and how they should be set.

1. Key Vault Access
   - Ensure that your user account is in the proper RAC Role to manage secrets in the Key Vault.  Add your user to the Key Vault Secrets Officer Role for the key Vault and wait for the permissions to propogate.  After you have been assigned this role, you can proceed with the following steps.

2. Key Vault Secrets
   - SftpUserName: Create a new version and set the value to be the user name that your institution has ssigned to you.
   - SftpUrl: Create a new version and set the value to be the URL of the PRODUCTION SFTP lockbox site.
   - SftpTestUrl: Create a new version and set the value to be the URL of the VALIDATION or TEST SFTP lockbox site.
   - SftpKeyFile: This one requires a little different procedure in order to get your key file into the secret. That prcess is outlined next.

