# Sample Program - Embed Tableau Worksheet in Application
This sample project is used to demonstrate how to integrate worksheets developed by tableau desktop into business applications to achieve single sign-on.

The sample code is only for reference, you need to integrate it into the application according to actual needs.

## Before you start
To successfully use the sample project, you need the following:
-  EnOS™ API SDK Version 0.1.47
-  [JDK 1.8](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)
- [Maven 3](https://maven.apache.org/install.html)

## Scenario

This example simulates a Web application, sending a request to the back-end service by clicking a button on a web page. This allows the back-end service to send a request to the Tableau Server service to obtain the URL of the tableau worksheet. Finally, it displays the signed-in tableau worksheet page in an `iframe` at the front end.

2. Sample project framework
-  This sample project is developed using `JDK 1.8` and `Spring Boot 2.0`.
-  The back-end calls the API that obtains the tableau URL through the application key, application secret, application account registered in the tableau server service, and the worksheet url in Tableau.
-  The front-end uses `jQuery` to call the interface in the back-end to obtain the tableau worksheet URL and display it in `iframe`.

## Procedure

1. Download the sample application code.

2. Load the Maven project after extracting the sample code.

3. Run the `TableauPluginDemoApplication` class. Browse to `localhost: 8080` in the browser to enter the following page.

   .. image:: media/sample_01.png

4. Click  **Report**. The application will load the tableau worksheet page in the form of `iframe`.

   .. image:: media/sample_02.png

<!--end-->
