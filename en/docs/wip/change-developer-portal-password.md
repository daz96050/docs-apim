
# Change the Developer Portal Password  
  
  You can change your own password for the WSO2 API Manager Developer Portal using the Developer Portal UI.    
  
Follow the instructions below to change your password:   
  
1. Sign in to the Developer Portal.      
  
     `https://<hostname>:9443/devportal`   
  Example: `https://localhost:9443/devportal`   
  Use your username and password to sign in.      
  
2. Click  on your username at the top right corner and select  **Change Password**.    
  
     [![Change Developer Portal password User Menu]({{base_path}}/assets/img/learn/change-devportal-password-user-menu-click.png)]({{base_path}}/assets/img/learn/change-devportal-password-user-menu-click.png)      
  
3. Enter your old password, a new password, re-enter the new password, and thereafter click **SAVE** to submit changes. The new password should adhere to the custom password policies as described below.
  
     [![Developer portal password change submit]({{base_path}}/assets/img/learn/change-devportal-password-submiting.png)]({{base_path}}/assets/img/learn/change-devportal-password-submiting.png)  
  
## Use custom password policy
You can define your custom password policy by defining one or both of the followings. 
    
1. [User store password regex](https://apim.docs.wso2.com/en/latest/administer/managing-users-and-roles/managing-user-stores/configure-primary-user-store/configuring-a-jdbc-user-store/#configuring-a-jdbc-user-store)  
Example:
```toml
[user_store]
type = "database_unique_id"

[user_store.properties]
PasswordJavaRegEx = "^[\\S]{6,30}$"
```
2. [Identity management  password policies](https://apim.docs.wso2.com/en/latest/install-and-setup/setup/security/identity-management-for-the-api-dev-portal/#password-policies)

<html>    
    <div class="admonition note">    
        <p class="admonition-title">Note</p>    
        <p>
            The password policy set by identity management password policies can be overridden by Management console for each tenant.
        </p>    
    </div>
</html>
<html>    
    <div class="admonition note">    
        <p class="admonition-title">Note</p>    
        <p>
            When changing the password, new password will be validated against user store password regex and conditions enforced by identity management password policy. If these conditions/regex patterns are set to be in conflict with each other, you may not be able to change your password.
        </p>    
    </div>
</html>

## Display password policy guidelines
  
Alternatively, you can display a list of policy guidelines on the password changing UI.  
  
[![DevPortal password policy guideline displaying]({{base_path}}/assets/img/learn/change-devportal-password-policy-guideline-display.png)]({{base_path}}/assets/img/learn/change-devportal-password-policy-guideline-display.png)  
  
1. Enable Password changing guidelines in the `settings.js` file.  

    a. Open the `<API-M_HOME>/repository/deployment/server/jaggeryapps/devportal/site/public/theme/settings.js` file.  
     
    b. Edit the configuration as follows:  
   
 ```javascript
 const Settings = { 
    ...
    passwordChange: { 
        guidelinesEnabled: true, 
        ... 
    },
 };
 ```
2. List your custom guidelines under `Settings.passwordChange.policyList`.  
 
  ```javascript
  const Settings = { 
     ...
     passwordChange: { 
         guidelinesEnabled: true, 
         policyList: [
             'Policy 1',
             'Policy 2',
             'Policy 3',
         ],
     },
  };
  ```
 
  <html>    
   <div class="admonition note">    
   <p class="admonition-title">Note</p>    
   <p>If the guideline list is empty, the change password UI will not show the Password Policy guidelines section.</p>    
   </div>    
   </html>