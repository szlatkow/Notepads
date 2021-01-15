# Notepads CI/CD documentation

* after merging the PR, the first run of the main workflow will not complete successfully, because it requires specific setup explained in this documentation

## 1. Set up Dependabot

Dependabot is a GitHub native security tool that goes through the dependencies in your project and creates alerts, and PRs with updates when a new and/or non-vulnerable version is found.

- for PRs with version updates, this pipeline comes pre-configured for all current dependency sources in your project, so at "Insights" tab -> "Dependency graph" -> "Dependabot", you should be able to see all tracked sources of dependencies, when they have been checked last and view a full log of the last check

![Dependabot_tab](/ScreenShots/CI-CD_DOCUMENTATION/Dependabot_tab.png)

![Dependabot_log_page](/ScreenShots/CI-CD_DOCUMENTATION/Dependabot_log_page.png)

### Set up security alerts and updates
##### - GitHub, through Dependabot, also natively offers a security check for vulnerable dependencies

1. Go to "Settings" tab of your repo

2. Go to "Security&Analysis" section

3. Click "Enable" for both "Dependabot alerts" and "Dependabot security updates"

- By enabling "Dependabot alerts", you would be notified for any vulnerable dependencies in your project. At "Security" tab -> "Dependabot alerts", you can manage all alerts. By clicking on an alert, you would be able to see a detailed explanation of the vulnerability and a viable solution.

![Dependabot_alerts_page](/ScreenShots/CI-CD_DOCUMENTATION/Dependabot_alerts_page.png)

![Dependabot_alert_page](/ScreenShots/CI-CD_DOCUMENTATION/Dependabot_alert_page.png)

- By enabling "Dependabot security updates", you authorize Dependabot to create PRs specifically for **security updates**

![Dependabot_PRs](/ScreenShots/CI-CD_DOCUMENTATION/Dependabot_PRs.png)

### Set up Dependency graph
##### - The "Dependency graph" option should be enabled by default for all public repos, but in case it isn't:

1. Go to "Settings" tab of your repo

2. Go to "Security&Analysis" section

3. Click "Enable" for the "Dependency graph" option

- this option enables the "Insights" tab -> "Dependency graph" section -> "Dependencies" tab, in which all the dependencies for the project are listed, under the different manifests they are included in

![Dependabot_dependency_graph](/ScreenShots/CI-CD_DOCUMENTATION/Dependabot_dependency_graph.png)

NOTE: **screenshots are only exemplary**

<br>

## 2. Set up SonarCloud 
  
SonarCloud is a cloud-based code quality and security service.

1. Go to https://sonarcloud.io/

2. Click the "Log in" button and create a new account or connect with GitHub account (recommended).

3. At the top right corner click the "+" sign.

4. From the dropdown select "Create new Organization".

5. Click the button "Choose an organization on Github".

6. Select an account for your organization setup.

7. On **Repository Access** select "Only select repositories" and select your project and click the "Save" button.

8. On the "Create organization page" don't change your **Key** and click "Continue".

9. Select the Free plan then click the "Create Organization" button to finalize the creation of your Organization.

10. From the dropdown select "Analyze new project".

11. Select the "Bogus" project and click "Set Up" button at the top right corner.

12. Under the "Choose another analysis method" sign click the "With Github Actions" sign. 

13. Copy the Name of the token and the Value and use them on step "16".

14. To Create a secret on GitHub click the fast forward button **Settings>Secrets** .
 
15. Then click "New Repository secret"

16. Enter the "Name" and the "Value" and click **Add Secret**.

17. No further steps are required for this setup.

18. Run manually your workflow one time to deliver the code to SonarCloud.

19. In order to set a "Quality gate" follow the next steps.

19. After the run go to the Project page.

20. Click on the button "Set new code definition" and select  "Previous version".

21. Manually run the workflow and there you have set a Quality gate.