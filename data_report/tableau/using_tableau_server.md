# Using Tableau Server service
You can use the interface provided by the Tableau Server service to embed Tableau worksheets into business applications.

## Before you start

Ensure that the following requirements are met:

- You have contacted EnOS™ sales representative or your Envision project manager to purchase the Tableau Server service.
- An application has been registed in the EnOS™ Console.
- Download and install [JDK 1.8](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)
- Download and install [Maven 3](https://maven.apache.org/install.html)

## Procedure

1. From the left navigation panel, click **Third party plugins > Tableau**. The **Information** page shows the number of Tableau Server licenses purchased, the date of purchase, and the expiration date.

   .. image:: media/tableau_basicinfo_en.png

   - You can click **Enter** to enter the login page of Tableau Server, and manage the site of your Tableau Server instance on EnOS™. About Tableau Server site management, please refer to  [site management.](https://onlinehelp.tableau.com/current/server/en-us/manage_site.htm).
   - Or you can click **More about Tableau** and enter to Tableau website to learn more about Tableau products and services.

2. Click **User Management**.

   .. image:: media/tableau_usermgnt_en.png

   - User list view displays the basic information of account in Tableau Server, such as display name, user name, and site role.
   - You can choose **Operation** to register your application account or modify the link between application account and Tableau Server account.

3. Register the application account and associate the purchased Tableau account.

   .. image:: media/tableau_link_user_en.png

    There are two sources of application accounts you have registered.
    - EnOS™ account: the account of the current EnOS™ customer.
    - External account: you can register any accounts (excluding spaces), usually using the application account that will embed Tableau worksheet.

    **Note**: there is a one-to-one mapping between the Tableau Server account and the application account.That is, a Tableau Server account can only be linked to one application account, and the linked application account cannot be linked to any other Tableau Server account.

4. Inplement Single Sign on (SSO), embed Tableau worksheet into application

   1. Configure the dependency of EnOS™ API service in Maven project. Through this dependency, you can use the EEOP package in the EnOS™ API service to complete the application authentication.

      ```
      <dependency>
	  	<groupId>com.envisioniot</groupId>
	  	<artifactId>eeop</artifactId>
	  	<version>0.1.47</version>
      </dependency>
      ```
      **Note**: You need to download the latest EnOS™ API service SDK from the SDK center in EnOS™ Portal and load it into your project.

   2. Configure the necessary information. Before using the Tableau Server service, you need to be authenticated by EnOS™ authentication service. Thus, you need to configure the necessary information about EnOS™ into the program.
      ```
      //appKey and appSecret get when creating application.
      appKey: XXXXXxXXXXXXXXXXXXXXXXXXXX
      appSecret: XXXXXxXXXXXXXXXXXXXXXXXXXX
      //EnOS™APIUrl fixed
      EnOS™APIUrl: https://eos.envisioncn.com/eeop
      //EnOS™User and EnOS™Password is the account and password for your EnOS™ Portal
      EnOS™User: XXXXXXXX
      EnOS™Password: XXXXXXXX
      ```
   3. At the same time, you also need to configure the address of the Tableau Server service, your organization ID, the application account registered in the Tableau Server service and the target Tableau worksheet url.
      ```
      //Tableau Server service interface address is fixed，
        final String tableauPluginUrl = "https://ag-cn2.envisioniot.com/tableau-plugin/external/url";
      //appUser is the site name of Tableau
        final String appUser = "XXXX";
      //EnOS™OrganizationID is the organization ID of EnOS™ Portal，can preview at data preview
        final String EnOS™OrganizationId = "XXXXXXXXXX";
      //tableauContent is the Tableau worksheet link that you want to access at the end     
        final String tableauContent = "/views/Payroll/AveragePayrollAnalysis";
      ```

    4. Obtain the Tableau worksheet URL through the Tableau Server service interface.

      ```
        public TableauUrlResponse getTableauUrl() {
            Map<String, String> params = new HashMap<>();
            params.put("appUser", appUser);
            params.put("orgId", EnOS™OrganizationId);
            params.put("content", tableauContent);
            try {
                return EnOS™PluginRequestUtil.doQuery(tableauPluginUrl, appConfig.getAppKey(), appConfig.getAppSecret(), params, TableauUrlResponse.class);
            } catch (Exception ex) {
                logger.error("get tableau url error ", ex);
                return new TableauUrlResponse(TableauUrlResponse.ERROR, "error");
            }
        }
      ```
The successful operation of the program will return to the target Tableau worksheet URL.

See [Sample Code](sample_code) for the detailed application design.
