<!--
title: "Create Users"
description: "Creating Users in Contrast"
tags: "Admin onboarding user settings license defend protection create"
-->

System and Organization Administrators can create users individually, in groups, or through [Microsoft Active Directory](installation-setupauth.html#ad) (AD) or [LDAP](installation-setupauth.html#ldap) integrations. All users are required to have a default organization and a default role within that organization. 

>**Note:** Verify the [Roles](admin-manageorgsroleperm.html#roles) that you want to assign to users so that they have the appropriate level of functionality.

You may decide to designate an [Application Access Group](admin-onboardteam.html#group), which provides more administrative functionality to the users for specific applications or restricts which applications the users in the group can view or modify.

## System Settings

Enterprise-on-Premises (EOP) customers can delegate users to perform system administration functions across organizations such as managing users, groups, applications, licenses, API keys and security policies. This assumes that you created multiple organizations in Contrast as part of a multi-tenant deployment. See [Granting and Revoking SuperAdmin Permissions](admin-manageorgs.html#sa) to get started.

To create users as a System Administrator, go to the **User menu** and choose **SuperAdmin** in the **Use Contrast Security as** section. Select the **Users** page in the top navigation. 

### Individual users

To add a single user, click the button to **Add User** above the grid, and complete the following steps: 

* Enter the user's **First Name**, **Last Name** and **Email Address** in the provided fields. 
* Check the box if you want to **Require email activation** instead of requiring a password.
* Choose which of the **System Roles** should apply to the user in the dropdown menu. The default is **None**. 
* Choose the **Organization** to which the user belongs. 
* Once you decide on an organization, you can choose the default **Organization Role** in the dropdown menu as well as an **Application Access Group** in the multiselect field.
* Choose the **Date Format**, **Time Format** and **Time Zone** in the dropdown fields. 
* The box to **Use Organization Settings** is checked by default. Uncheck the box to create your own settings using the **Access** toggle, or check the box to **make user API only**. 
* Use the toggle to enable **Protect** access for the user. The toggle is **off** by default. 
* Click the **Add** button to save the information and create the user.  

<a href="assets/images/Add-user-system-settings.png" rel="lightbox" title="Add a user as a SuperAdmin"><img class="thumbnail" src="assets/images/Add-user-system-settings.png"/></a>


### Multiple users 

To bulk add users, click the upload icon above the grid in the **Users** page to import a spreadsheet with the users' information. The spreadsheet must be CSV format, and include the following fields for each user. **All field headings and values in the spreadsheet must be formatted as shown.** 

* **First Name** 
* **Last Name**
* **Email** or **Username** <br> See the **Authentication** section below for more requirements. 
* **Organization UUID** 
* **Organization Role** <br> Values can be "View", "Edit", "Rules_admin" or "Admin".

> **Note:** Find the Organization UUID in the Contrast interface by impersonating the appropriate organization, and then going to **Organization Settings > Organization tab > General Information section**. 

##### Authentication methods

For users who have [HTTP Header](installation-setupauth.html#http-proxy), [LDAP](installation-setupauth.html#ldap) or [AD](installation-setupauth.html#ad) authentication configured, you must use the field heading **Username** instead of **Email** in the spreadsheet. The username values entered in the spreadsheet and the authentication configuration must match exactly. 

##### Templates

Download **CSV templates** directly from the Contrast interface by hovering over the upload icon and clicking the link in the tooltip, or by clicking the links below. 

* [Database or SSO authentication](assets/attachments/user_upload/Contrast-user-upload-template-superadmin-email.csv)
* [HTTP Header, LDAP or AD authentication](assets/attachments/user_upload/Contrast-user-upload-template-superadmin-username.csv)

#### Optional information 

The following information is optional for each user. To include the fields in the spreadsheet, add a new column and value(s) for each as given below. 

* **Email Activation** <br> If the value is "None", the default is "Required Password".
* **System Administration** <br> The default value is "Off".
* **Groups** <br> Values can be "View", "Edit", "Rules Admin", "Admin" or custom group names. Format multiple group names as "GroupA&&GroupB&&GroupC".
* **Date Format** <br> The default value is the organization setting, such as "MM/dd/YYYY".
* **Time Format** <br> The default value is the organization setting, such as "hh:mm a".
* **Timezone** <br> The default value is the organization time zone.
* **Access** <br> The default value is "On".
* **API only** <br> The default value is "Off".
* **Protect** <br> The default value is "Off".

### Upload progress

Once the spreadsheet upload is in progress, you can leave the page and continue with other tasks in Contrast. If the upload is successful, Contrast shows you a confirmation message with the number of users uploaded. If the upload failed, Contrast shows you an error message with the source of the error on the spreadsheet.

## Organization Settings

To create users as an Organization Administrator, go to the **User menu > Organization Settings > Users tab**. 

### Individual users

To add a single user, click the button to **Add User** above the grid, and complete the following steps: 

* Enter the user's **First Name**, **Last Name** and **Email Address** in the provided fields. 
* Choose the user's **Organization Role** in the dropdown menu. 
* Select an **Application Access Group** to which to add the user in the dropdown menu, if desired. 
* Choose **Date Format**, **Time Format** and **Time Zone** settings in the dropdown menus. 
* If you want to disable the user's access to your organization in the Contrast interface, use the **Access** toggle. (The user has access by default.)
* Check the box if you want the user to have **API Only** access. <br> (The user will have access Contrast's REST API, but won't have access to the Contrast interface.)
* Use the toggle to enable **Protect** access for the user. The toggle is **off** by default. 
* Click the **Add** button to save the information and create the user.  

<a href="assets/images/Add-user-org-settings.png" rel="lightbox" title="Add a user as an OrgAdmin"><img class="thumbnail" src="assets/images/Add-user-org-settings.png"/></a>

### Multiple users

To bulk add users, click the upload icon above the grid in the **Users** page to import a spreadsheet with the users' information. The spreadsheet must be CSV format, and include the following fields for each user. **All field headings and values in the spreadsheet must be formatted as shown.** 

* **First Name**
* **Last Name** 
* **Email** or **Username** <br> See the **Authentication** section below for more requirements. 
* **Organization Role** <br> Values can be "View", "Edit", "Rules_admin" or "Admin".

##### Authentication methods

For users who have [HTTP Header](installation-setupauth.html#http-proxy), [LDAP](installation-setupauth.html#ldap) or [AD](installation-setupauth.html#ad) authentication configured, you must use the field heading **Username** instead of **Email** in the spreadsheet. The username values entered in the spreadsheet and the authentication configuration must match exactly.  

##### Templates

Download **CSV templates** directly from the Contrast interface by hovering over the upload icon and clicking the link in the tooltip, or by clicking the links below. 

* [Database or SSO authentication](assets/attachments/user_upload/Contrast-user-upload-template-organizationadmin-email.csv)
* [HTTP Header, LDAP or AD authentication](assets/attachments/user_upload/Contrast-user-upload-template-organizationadmin-username.csv)

#### Optional information 

The following information is optional for each user. To include the fields in the spreadsheet, add a new column and value(s) for each as given below. 

* **Groups** <br> Values can be "View", "Edit", "Rules Admin", "Admin" or custom group names. Format multiple group names as "GroupA&&GroupB&&GroupC".
* **Protect** <br> The default value is "Off".
* **Date Format** <br> The default value is the organization setting, such as "MM/dd/YYYY".
* **Time Format** <br> The default value is the organization setting, such as "hh:mm a".
* **Timezone** <br> The default value is the organization time zone.
* **API only** <br> The default value is "Off".
* **Access** <br> The default value is "On".
* **Protect** <br> The default value is "Off". 

### Upload progress

Once the spreadsheet upload is in progress, you can leave the page and continue with other tasks in Contrast. If the upload is successful, Contrast shows you a confirmation message with the number of users uploaded. If the upload failed, Contrast shows you an error message with the source of the error on the spreadsheet.

## User Status

Once added, each user's status is displayed on the main **Users** page so that you can see who's awaiting activation, active or inactive, or locked out of their account based on a security policy. For more information about user administration, read how to [Manage Users](admin-manageorgs.html#manage-user). 

<a href="assets/images/User-grid.png" rel="lightbox" title="Users grid for Organization Administrators"><img class="thumbnail" src="assets/images/User-grid.png"/></a>



