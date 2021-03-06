# Adding a User Signup Workflow

#### Engaging the Approval Workflow Executor in the API Manager

1.  Log in to API-M management console ( `https://<Server-Host>:9443/carbon` ) and select **Browse** under **Resources**.

    ![Browse resources]({{base_path}}/assets/img/learn/wf-extensions-browse.png)

2.  Go to `/_system/governance/apimgt/applicationdata/workflow-extensions.xml` resource, disable the **UserSignUpSimpleWorkflowExecutor** and enable **UserSignUpApprovalWorkflowExecutor** for user self sign up.

    ```
    <WorkFlowExtensions>
        ...
            <!--UserSignUp executor="org.wso2.carbon.apimgt.impl.workflow.UserSignUpSimpleWorkflowExecutor"/-->
            <UserSignUp executor="org.wso2.carbon.apimgt.impl.workflow.UserSignUpApprovalWorkflowExecutor"/>
        ...
    </WorkFlowExtensions>
    ```

3.  Go to the Developer Portal Web interface of API Manager and sign up / register as a new user. (Go to **Sign in** --> **Create Account**  and add the details of the new user).
   
    ![Create new  Account]({{base_path}}/assets/img/learn/devportal-create-account.png)

4.  Note that a message "User registration completed successfully " appears if the Approval Workflow Executor is invoked correctly

    ![Browse resources]({{base_path}}/assets/img/learn/user-registration-success.png)

5.  Log in to the [Admin Portal](`https://localhost:9443/admin`) (`https://<Server-Host>:9443/admin`) of API Manager giving the admin username and password.

6.  Navigate to **Tasks** --> **User Creation** and approve or reject the user signup task listed by clicking on approve or reject.

    ![Browse resources]({{base_path}}/assets/img/learn/user-creation-pending-list.png)

7.  Go back to the Developer Portal and see that the user is now registered. If the user is successfully registered then user can login to devportal successfully with that account.

