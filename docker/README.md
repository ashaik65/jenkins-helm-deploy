### How to Create/Add a User in Jenkins ####

Step 1) Login to Jenkins Dashboard

Login to your Jenkins dashboard by visiting http://localhost:8080/

If you haven’t installed Jenkins in your local server, go to the appropriate URL and access your dashboard by using your login credentials.

![jenkins-users](https://github.com/ashaik65/jenkins-helm-deploy/assets/34375439/5113eb8c-d374-4d9e-9478-c32d47d2472e)


Step 2) Choose the option

You will now see options to create and add user in Jenkins and manage current users.

Step 3) Create a new User

Under Manage Jenkins, Click Create User
Enter Jenkins add user details like password, name, email etc.
Click Create User

![091318_0444_HowtoCreate2](https://github.com/ashaik65/jenkins-helm-deploy/assets/34375439/57b838ef-1fff-4f76-a433-638e1238ca00)

Step 4) User is created

You will see on the dashboard that a new Jenkins create user as per the details entered.

![091318_0444_HowtoCreate3](https://github.com/ashaik65/jenkins-helm-deploy/assets/34375439/518d194f-ff04-4f1f-b6ca-bdb48478232b)

### How to Install Role Strategy Plugin in Jenkins ###
There are two methods for installing plugins in Jenkins:

1. Installing it through your Jenkins dashboard
2. Downloading the plugin from Jenkins website and installing it manually.

Step 1)

1. Go to Manage Jenkins

2. Click on the Manage Plugins option

![091318_0444_HowtoCreate4](https://github.com/ashaik65/jenkins-helm-deploy/assets/34375439/b616ee6a-836c-4c4e-8ee7-f8ef91eedfbc)

Step 2)

1. In available section, screen Search for “role”.
2. Select Role-based Authorization Strategy plugin
3. Click on “Install without restart” (make sure you have an active internet connection)

![091318_0444_HowtoCreate5](https://github.com/ashaik65/jenkins-helm-deploy/assets/34375439/966124ae-7de5-44e2-8e5f-c24473cc48a1)


Step 3)

Once the plugin is installed, a “success” status will be displayed.

![091318_0444_HowtoCreate6](https://github.com/ashaik65/jenkins-helm-deploy/assets/34375439/f4097dee-0989-4005-906a-55e1478c60f7)


Click on Go back to the top page.

Step 4) Go to Manage Jenkins -> Configure Global Security -> Under Authorization, select Role Based Strategy. Click on Save.

![091318_0444_HowtoCreate7](https://github.com/ashaik65/jenkins-helm-deploy/assets/34375439/642f313c-08ee-4311-a713-057453140ba7)


### How to Manage Users and Roles in Jenkins ###
Following are the steps on how to manage and assign roles in Jenkins:

Step 1)

1. Go to Manage Jenkins

2. Select Manage and Assign Roles

![091318_0444_HowtoCreate8](https://github.com/ashaik65/jenkins-helm-deploy/assets/34375439/511ba4be-e33c-4791-9fa8-8f490e19768a)


Note: that the Manage and Assign Roles option will only be visible if you’ve installed the role strategy plugin.

Step 2) Click on Manage Roles to add new roles based on your organization.


![091318_0444_HowtoCreate9](https://github.com/ashaik65/jenkins-helm-deploy/assets/34375439/33d6f9b7-375d-4bf6-84f6-3a1e0abbcc42)


Step 3) To create a new role called “developer”,>

1. Type “developer” under “role”.
2. Click on “Add” to create a new role.
3. Now, select the Jenkins user permissions you want to assign to the “Developer” role.
4. Click Save

![091318_0444_HowtoCreate10](https://github.com/ashaik65/jenkins-helm-deploy/assets/34375439/4259e906-3111-4e7f-950a-84dce4aeefee)


How to Assign Roles in Jenkins
Step 1) Now that you have created roles, let us assign them to specific users.

1. Go to Manage Jenkins
2. Select Manage and Assign Roles

![091318_0444_HowtoCreate11](https://github.com/ashaik65/jenkins-helm-deploy/assets/34375439/34c0a5d9-3201-44a3-9ee0-15a8125bf29e)

Step 2) We shall add the new role “developer” to user “guru99“

1. Selector developer role checkbox
2. Click Save

![091318_0444_HowtoCreate12](https://github.com/ashaik65/jenkins-helm-deploy/assets/34375439/6b004aa2-09e8-47f4-b92d-56198d3af372)

You can assign any role to any user, as per your need.


