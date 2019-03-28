---
layout: tutorial
title: Troubleshooting
weight: 6
show_children: true
---
<!-- NLS_CHARSET=UTF-8 -->
# Troubleshooting
{: #troubleshooting }

* In case of any error, refer to the `log.log` file for the respective platform folder path below:

    * On mac OS: `~/Library/Logs/IBM Digital App Builder/log.log`.
    * On Windows: `%USERPROFILE%\AppData\Roaming\IBM Digital App Builder\log.log`.


* Failure to create a Data set for a Microservice using a swagger file.

    For the first time users of the Builder, the microservice creation may fail due to network letency.
    To get rid of this, follow these steps:
    1. Open command prompt and go to the installed location of the app.
    2. `cd ibm\adapterGenerator`
    3. Run the following command
        `windows> execute.bat .`
        `mac>./execute.sh .`
    4. On successful complication of the above command, you can start using microservice (swagger file) from the Digital App Builder.

* Failure to preview the app on Windows.

    In the Digital App Builder, go to **Settings > Repair project** and click **Rebuild Dependencies** and **Rebuild Platforms** buttons.

* Android App does not work after adding the List component to the app.

    This is due to Android WebView version is less than 68.X.XXXX.XX. To resolve this, upgrade the Android WebView version to 68.X.XXXX.XX or above.

* In MacOS, preview of the app on an Android simulator fails with app crashes. With the following error:

    `java.lang.RuntimeException: Unable to create application com.ibm.MFPApplication: java.lang.RuntimeException: Client configuration file mfpclient.properties not found in application assets. Use the MFP CLI command 'mfpdev app register' to create the file.`

    To resolve this, from the terminal navigate to the app ionic directory and run the following commands:

    `ionic cordova plugin remove cordova-plugin-mfp
    ionic cordova plugin add cordova-plugin-mfp`

    and preview from the Digital App Builder again.

* Unable to generate the adapter when importing swagger json/yaml file.

    Error when importing swagger json/yaml file and the error is due to Maven dependency.

    Ideally all the Maven dependencies if does not exists are downloaded and installed behind the scene. But there are somecases where Maven fails because of multiple Maven versions in the system. To solve this issue follow these steps:

    a. Go to the Aa\pp location and open execute.sh / execute.bat file depending on the OS. (`<APP_LOCATION>\ibm\adapterGenerator`)
    b. Edit all the `call %MAVEN_HOME% clean install` to `call %MAVEN_HOME% -U clean install`.

        Adding `-U` will force maven to check any external dependencies that need to be updated based on the POM file.

