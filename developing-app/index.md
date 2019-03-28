---
layout: tutorial
title: Developing an app
weight: 5
show_children: true
---
<!-- NLS_CHARSET=UTF-8 -->
# Developing an App
{: #developing-an-app }

Developing an app includes the following steps:

1. Create an app. Refer to [Creating an app](../getting-started/) section.
2. Design your app by adding the required controls. For more information, refer to [Digital App Builder interface](../dab-interface/).
3. Add the services (Watson Chat, Watson Visual Recognition, Push Notifications, Data Set) you need in your app.
4. Add or modify the Platforms, if required. Refer to the [Settings > App details](../settings/) section.
5. Preview your app. Refer to [Preview the app using the simulator](#preview-the-app-using-the-simulator).
6. After previewing your application and if it is ready for build, after rectifying any errors, perform the following steps for building the application:

    * **For Android app:**
        a. Navigate to the directory, which you have specified at the time of creating the app.
        b. Go to ionic folder.
        c. Go to **Platform > Android**.
        d. Open Android Studio and then go to **File > Open Project** > Choose the android folder mentioned in step c.
        e. Build the project. 
           >**Note**: For publishing and building follow the steps from tutorial [https://developer.android.com/studio/publish/](https://developer.android.com/studio/publish/).

    * **For iOS app**:
        a. Navigate to the directory, which you have specified at the time of creating the app.
        b. Go to ionic folder.
        c. Go to Platform > iOS.
        d. Open **Xcode** and then build the project. 
            >**Note**: For publishing and building follow the steps from tutorial [https://developer.apple.com/ios/submit/](https://developer.apple.com/ios/submit/).


## Preview the app using the simulator
{: #preview-the-app-using-the-simulator }

You can preview the app developed by connecting to the simulation to the channel selected.

* To preview the App on iOS, download and install **XCode** from Apple App Store.
* To preview the App on Android, 
    * Install Android Studio and follow the instruction. [https://developer.android.com/studio/](https://developer.android.com/studio/)
    * Configure an Android Virtual Machine. Follow the instructions [here](https://developer.android.com/studio/releases/emulator).

