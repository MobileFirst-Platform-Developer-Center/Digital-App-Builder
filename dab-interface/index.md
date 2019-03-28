---
layout: tutorial
title: Digital App Builder workbench interface
weight: 4
show_children: true
---
<!-- NLS_CHARSET=UTF-8 -->
# Digital App Builder interface
{: #digital-app-builder-interface }

![DAB interface](dab-workbench-elements.png)

Digital App Builder interface consists of the following in the Left navigation panel:

* **Workbench** - displays or hides the page details
* **Data** - helps you to add a dataset by connecting to an existing data source or create a data source for a microservice using OpenAPI doc. 
* **Watson** - consists of Image Recognition and Chatbot (Watson Assistant) components for configuring an existing instance or create a new instance. 
* **Engagement** - You can increase your user engagement with the app by adding Push notifications services
* **Console**: displays the console to see the activities and code for each component. 
* **Settings**: displays the App details, Server info, Plugins, and Repair Project (like Rebuilding dependencies, Rebuilding platforms, Resetting IBM Cloud credentials).

## Workbench
{: #workbench }

Workbench helps you to design the pages. Workbench consists of three work areas:

![Workbench](dab-workbench.png)

1. **Pages/Controls**: This area displays the name of the pages created by default. Use **+** sign to create a new page. On clicking **Controls** icon, displays controls that helps in adding functionality to a page in an app. You can drag and drop the controls from the respective Controls pallette to a page's canvas. Each control has a set of properties and actions.

    Following is the list of controls provided available:
    * **Basic**: You can drag-and-drop these basic controls (Button, Heading, Image, and Label) to the canvas and configure the properties and actions.

        ![Pages / Congrols](dab-workbench-basic-controls.png)

        * **Button** - Buttons has a property to label. In the Action tab you can specify the page to navigate to on click of the Button.
        * **Heading Text** - Helps you to add a heading text for the application such as Page Title.
        * **Image** - Helps you upload a local image or provide a url of an image.
        * **Label** - Helps you to add static text to your page body. 
    * **Databound** - helps you to connect with a data set and operate on the entities in the data set. Databound consists of two components: **List** and **Connected Labels**

        ![Databound controls](dab-workbench-databound-controls.png)

        * **List** - Create a new page and drag and drop the List component. Add the **List Title**, Choose the list type to work on, Add content to work on, and select the dataset to use.
        * **Connected Labels** - You can add the connected labels and add value to it.
    * **Login** - Login consists of the **Login Form** control. Drag and drop the login form to the page.
 
        The Login Form control helps you to create a login page for your application to connect the user to the Mobile Foundation server. Mobile Foundation server provides a security framework to authenticate users and provide that security context to access the data sets. For more information read [here](https://mobilefirstplatform.ibmcloud.com/tutorials/en/foundation/8.0/authentication-and-security/creating-a-security-check/).

        ![Login Form](dab-workbench-login-control.png)

        To enable Login Form, perform the following steps:

        1. Make the following changes on Mobile Foundation Server
            * Deploy a security check adapter which would take username and password as input. You can use the sample adapter from [here](https://github.com/MobileFirst-Platform-Developer-Center/SecurityCheckAdapters/tree/release80).
            * In the mfpconsole, go to app's security tab and under Mandatory Application Scope, add the above created security definition as scope element.
        2. Make the following configuration in your Application using the Builder.
            * Add **Login Form** control to a page in the canvas.
            * In **Properties** tab, provide the **Security check name** and the page to navigate **On Login Success**.
            * Run the app.
    * **AI** - AI controls allows you to add Watson AI capabilities to your app.

        * **Watson Chat** - This control provides a complete chat interface that can be powered with Watson Assistant service on IBM Cloud. 

            ![Watson Assistant](dab-workbench-ai-watson-chat.png)

            * In the properties section select the configured Watson Assistant service and select the Workspace you want to connect to. To define and train a Chat conversation see [Chatbot](#chatbot) under Watson.

        * **Watson Visual Recognition** - This control provides an ability to take a picture and have Watson Visual recognition service identify it for you.
         
            ![Watson Visual Recognition](dab-workbench-ai-watson-vr.png)
 
            *  In the properties section select the configured Visual Recognition service and the classification model. To define and train using your own images see [Image recognition](#image-recognition) under Watson.

2. **Canvas** section - This area consists of the Current Channel selected, Current Page name, Design/Code Toggle, and Canvas.

    * **Channel** icon - This displays the current channel selected. You can add additional channels by selecting the required channels in the Platforms section under **Settings > App > App details**.
    * Current Page Name - Displays the canvas page name. When switched between pages, the current page name gets updated to the selected page.
    * **Design / Code** - This option brings the Code editor view to edit the code and enable to view the design back and debug any errors. In the canvas, switch from Design to Code, to view the code of the specific file in the project editor. Switching the Design to Code will display the following popup screen:

        ![Design - Code Toggle alert](dab-design-code-editor.png)

        **WARNING** - When you click **Create**, an editable version of your application is created locally. Any changes made in the editable version will not be reflected in the original app and vice versa. This will display the project explorer with all the project files for the application.

    * **Canvas** - At the centre of this section is the canvas which displays either the design or the code. You can drag-and-drop the controls and create the app.

3. **Properties/Actions** tab - At the right-hand side is the properties and action tab. When a control is placed in the canvas, you can edit and modify the properties of the control and connect a control with a related action to perform.

## Data
{: #dataset-integration}

Creating a Data set for a micro service involves the following steps. After creating the data set, you can connect the data bound controls in your app.

### Creating a new data set

1. From the landing page of the Digital App Builder, open any existing App or create one.
2. Click **Data** on the left hand panel.

    ![Data](dab-list-menu.png)

3. Click **Add new data set**. This displays the Add a data set window.

    ![Add new data set](dab-list-add-data-set.png)

4. Create a data set. You can either create from an existing source (default) or create a data source for a microservice using an OpenAPI doc.
    * **Create from existing data source** (default) - This will populate the dropdown with all the Data sources (adapters) from the configured Mobile Foundation server instance. 
    * **Create Data source for a microservice using OpenAPI doc** - This option lets you create a Data Source from an Open API specification document (Swagger json/yml) file, and a Data Set from it.

### Create a Data set from an existing Data Source

1. Select the Datasource for which you want to create the Dataset.
2. This will populate the available entities in the Data Source. Select the entity to be created.
3. Give a name to the dataset and click the **Add** button. This will add the dataset and you will be able to see the Attributes and Actions associated with that dataset.

    ![New dataset with attributes](dab-list-dataset-attributes.png)

4. You can Hide some of the attributes and Actions based on what you want to do with the data set.
5. You can also edit the **Display Labels** for the attributes
6. You can also Test any of the GET Actions by providing the required attributes and clicking on the **Run this action** which is part of the Action. Remember for this to work you should have specified the Confidential client name and password in the **Settings** tab.

### Create a Data source for a Microservice using a swagger file

1. Select the **json/yml** file for which you want to create a datasource for and click **Generate**.
2. This will generate an Adapter, which is a configuration artifact on the MF server that you can re-use and deploy it to the Mobile Foundation server instance.
3. Select the entity for which you want to define the data source for.
4. Give a name to the dataset and click on **Add** button.
5. This will add the Dataset and you will be able to see the Attributes and Actions associated with that dataset.

You can now bind this data set to any of the data bound controls.

## Watson
{: #integrating-with-watson-services}

The Digital App Builder provides an ability to configure the app to connect to the various Watson services provisioned on IBM Cloud.

### Chatbot
{: #chatbot }

Chatbots are powered by Watson Assistant service on IBM Cloud. Create a Watson Assistant instance on IBM Cloud. For more information, see [here](https://cloud.ibm.com/catalog/services/watson-assistant-formerly-conversation).

Once configured you can create a new **Workspace**. The workspace is a set of conversations that make up a chatbot. After creating a Workspace, start creating the dialogs. Provide a set of questions for a intent and a set of answers for that intent. Watson Assistant uses Natural Language Understand to interpret the intent based on the sample questions you provided. It can then try to interpret the question that a user asks in various styles and map it to the intent.

To enable a chatbot in your app, perform the following steps:

1. Click **Watson** and then click **Chatbot**. This displays the **Work with Watson Assistant** screen.

    ![Watson Chatbot](dab-watson-chat.png)

2. Click **Connect** to your Watson Assistance instance.

    ![Watson Chat instance](dab-watson-chat-instance.png)

3. Enter the **API key** details and specify the **URL** of your Watson Assistance instance. 
4. Provide a **Name** to your chatbot and click **Connect**. This displays your chat service dashboard of the **Name** given.

    ![Watson Chatbot workspace](dab-watson-chat-workspace.png)

5. Add a workspace by clicking **Add a workspace** which displays the **Create a new model** popup.

    ![Watson Chatbot workspace new model](dab-watson-chat-new-model.png)

6. Enter the **Workspace name** and **Workspace description** and click **Create**. This creates three **Conversation** workspace (Welcome, No match found, and New conversation).

    ![Watson Chatbot default conversation](dab-watson-chat-conversations.png)

7. Click **New conversation** to educate the new chatbot model. 

    ![Watson Chatbot Q&A](dab-watson-chat-questions.png)

8. Add questions and the response either as a csv file or as an individual questions and the response. For example, **Add a user statement** for If the user intends to ask, and then **Add a bot response** for the **Then, the bot should respond with**. or you can upload questions and the responses for the bot to respond.
9. Click **Save**.
10. Click the Chatbot icon at the botton right-hand side to test the chatbot.

    ![Chatbot testing](dab-watson-chat-testing.png)

### Image Recognition 
{: #image-recognition }

Image recognition capability is powered by Watson Visual recognition service on IBM Cloud. Create a Watson Visual Recognition instance on IBM Cloud. For more information, see [here](https://cloud.ibm.com/catalog/services/visual-recognition).

Once configured, you can now create a new Mobel and add classes to it. You can drag and drop images in to the Builder and then train your Model on those images. Once the training is complete, you can either download the CoreML model or use the Model in a AI control in your app.

To enable a Visual Recognition in your app, perform the following steps:

1. Click **Watson** and then click **Image Recognition**. This displays the **Work with Watson Visual Recognition** screen.

    ![Watson Visual Recognition](dab-watson-vr.png)

2. Click **Connect** to your Watson Visual Recognition instance.

    ![Watson Visual Recognition Instance](dab-watson-vr-instance.png)

3. Enter the **API key** details and specify the **URL** of your Watson Visual Recognition instance. 
4. Provide a **Name** to your Image Recognition instance in the app and click **Connect**. This displays the dashboard for your model.

    ![Watson VR new model](dab-watson-vr-new-model.png)

5. Click **Add new model** to create a new model. This will display **Create a new Model** popup.

    ![Watson VR model name](dab-watson-vr-model-name.png)

6. Enter the **Model name** and click **Create**. This will display the classes for that model and a **Negative** class.

    ![Watson VR Model Class](dab-watson-vr-model-class.png)

7. Click **Add new class**. This will display a popup to specify a name for the new class.

    ![Watson VR Model Class Name](dab-watson-vr-model-class-name.png)

8. Enter the **Class name** for the new class and click **Create**. This will display the workspace to add your images for training the model.

    ![Watson VR Model Class training](dab-watson-vr-model-class-train.png)

9. Add the images to the model either by drag and drop them into the workspace or use Browse to access the images.

10. You can go back to your workspace after adding the images and test by clicking **Test Model**.

    ![Watson VR Model Class testing](dab-watson-vr-model-class-train-test.png)

11. In the **Try your model** section, add an image and then result is displayed.


## Engagement
{: #engagement}

You can add Push notifications to your app and increase user engagement.

To add Push notifications to your app:

1. Select **Engagement**. This will display the list of available services. Currently only Push Notifications services is available.

    ![Engagement Push](dab-engagement-push.png)

2. In the **Push Notifications** click **Connect**. This displays the **Connect to Push Notification instance** dialog.

    ![Engagement Push Notifications instance](dab-engagement-push-instance.png)

2. Enter **Name**, **API Key**, **App GUID**, **Client Secret Key**, select the **Region** and click **Connect**.
3. The Name entered above get added to the page under Engagement.
4. Configure push notification for Android by providing **API Secret Key** and **Sender ID** and click **Save configuration**.

    ![Engagement Push Notification Android configuration](dab-engagement-push-android-configure.png)

5. Navigate to the iOS tab and provide push configuration details: select the **Environment**, provide the .p12 file with path, and enter the **Password** and click **Save configuration**.

    ![Engagement Push Notification iOS configuration](dab-engagement-push-ios-configure.png)

## Console
{: #console }

Helps you to view the code for each of the components. Also displays the information about various activities and errors.

## Settings
{: #settings}

Settings helps you to manage the app settings and rectify any errors during the build process. Settings consists of **App details**, **Server**, **Plugins**, and **Repair Project** tabs.

### App details
{: #app-details}

App details displays information about your app: **App Icon**, **Name**, **Location** where the files are stored, **Project/Bundle Id** provided at the time of creating the app, **Platforms** (channels) selected, **Service** enabled.

![Setting App details](dab-settings-app-details.png)

You can change the **App icon** by clicking the icon and uploading a new icon.

You can add/remove additional Platforms by checking/unchecking the checkbox near them.

Click **Save** to update the changes.

### Server
{: #server }

The Server info displays the **Server details** you are currently working on. You can edit the information by clicking the **Edit** link. You can add or modify the confidential client authorization.

![Settings server details](dab-settings-server.png)

The Server tab also displays **Recent servers**.

You can also add new server by clicking **Connect new +** button and provide the details in the **Connect to a new server** popup and click **Connect**.

![Settings new server](dab-settings-server-new-server.png)

### Plugins
{: #plugins}

Plugins displays list of plugins available in the Digital App Builder. Following actions can be performed:

![Settings Plugins available](dab-settings-plugins.png)

* **Install new** - You can install new plugins by clicking this button. This displays the **New plugin** dialog. Enter the **Plugin name**, **Version** (optional), and if it is a **Local plugin**, enable the switch for the same and point to the location and click **Install**.
* From the list of Plugins already installed, you can edit the version and reinstall the plugin or uninstall a plugin by selecting the link for the respective plugin.

### Repair project
{: #repair-project}

Repair project tab helps you to fix issues by clicking the respective options.

![Settings Repair](dab-settings-repair.png)

* **Rebuild dependencies** - If the project is unstable, you can try re-building dependencies.
* **Rebuild platforms** - If you see any platform related errors in console, try rebuilding the platforms. if you have made any changes to the channels or added additional channels, use this option.
* **Reset IBM Cloud credentials for Playground server** - You can reset the IBM Cloud Credentials used to login to the Playground Server. Resetting the Credentials cache will also clear out all your apps on the Playground server. **THIS OPERATION CANNOT BE REVERSED.**

 