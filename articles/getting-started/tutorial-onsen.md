<properties pageTitle="Getting started with Onsen apps in Visual Studio"
  description="This is an article on onsen tutorial"
  services=""
  documentationCenter=""
  authors="mikejo5000" />
  <tags ms.technology="cordova" ms.prod="visual-studio-dev14"
     ms.service="na"
     ms.devlang="javascript"
     ms.topic="article"
     ms.tgt_pltfrm="mobile-multiple"
     ms.workload="na"
     ms.date="12/01/2015"
     ms.author="mikejo"/>

# Get started with Onsen UI apps in Visual Studio

[Onsen UI](https://onsen.io) is a front-end UI framework for developing beautiful cross-platform mobile apps using Cordova. You can use Visual Studio 2015 to easily create and debug cross-platform Onsen UI apps.

## Get the Onsen UI templates!
You can install the Onsen UI starter templates in Visual Studio and use them to start building an app.

1. If you haven't already, [install Visual Studio 2015](http://go.microsoft.com/fwlink/?LinkID=533794).

    When you install Visual Studio, make sure you include the optional components, **HTML/JavaScript (Apache Cordova)** under **Cross-Platform Mobile Development**.

    >**Note**: Quickly verify that you can load and build the default Blank App template. In Visual Studio, choose **File**, **New**, **Project**, **JavaScript**, **Apache Cordova Apps**, **Blank App** and name the new project "blank", and build it with F5. If you have any trouble, see these [troubleshooting steps](../tips-and-workarounds/general/tips-and-workarounds-general-readme.md).

2. Install the Onsen UI templates.

    Visit [VS Extension for Onsen UI](https://visualstudiogallery.msdn.microsoft.com/8968a18d-cc94-4ebf-8183-ed0e1f6247f3) in Visual Studio Gallery, and add it directly to Visual Studio by downloading and double-clicking on the downloaded file.

    ![Onsen UI Extenstions and Updates](media/tutorial-onsen/image06.png)

    Or, do it in Visual Studio, by selecting **Tools**, **Extensions** and **Updates**. In the **Extensions and Updates** dialog box, select **Online**. In the search box, type **Onsen UI**.

3. Choose **Download** to download and install them. When you are asked for permission to install the templates, give your permission.

4. Choose **Restart** to restart Visual Studio. Now, choose **File**, **New**, then **Project**. When you choose **Installed**, then **Templates**, the new starter templates will show up under both **JavaScript**, **Apache Cordova Apps** and **TypeScript**, **Apache Cordova Apps**.

   ![Onsen UI New Project](media/tutorial-onsen/image01.png)

5. Choose one of the following starter templates for your new project:

   * Onsen UI Blank
   * Onsen UI Master-Details
   * Onsen UI Sliding Menu
   * Onsen UI Split View
   * Onsen UI Tab Bar

6. Choose **OK**.

    Visual Studio creates the Onsen UI project.

## Get your app running on Android
1. Add the Android platform by Android as a debug target (Solution Platforms list), and then choose Build, then Build Solution.

2. Choose Android as a debug target (Solution Platforms list), and to get the app running choose a target such as the **Ripple - Nexus S** (running in a simulator environment), the **VS Emulator 5" KitKat (4.4)** (Hyper-V required) or the **Google Android Emulator** (slow to load initially).

    ![Onsen UI Android Debug Target](media/tutorial-onsen/image05.png)

    You can configure a Google Android emulator in [AVD Manager](http://taco.visualstudio.com/en-us/docs/run-app-apache/).

3. Press F5, and the app should load correctly.

    ![Onsen UI Android App](media/tutorial-onsen/image00.png)

## Get your app running on iOS
You can run initially on the Ripple Emulator after selecting iOS as a debug target, but for detailed info on setting up the remotebuild agent for iOS, see [this topic](http://taco.visualstudio.com/en-us/docs/ios-guide/).

The Onsen UI starter templates should run correctly on iOS when the remotebuild agent is running on a Mac (or using an extension like [Monaca for Visual Studio 2015](https://visualstudiogallery.msdn.microsoft.com/21a7a495-5a24-4eab-a519-2f6e6d176049)), and when Visual Studio is configured to connect to it). Please note that the complete steps are outside the scope here.

## Get your app running on Windows
1. If it's not already installed, use the Visual Studio install program to install the **Universal Windows App Development Tools** (it should already be installed).

2. Open config.xml in Visual Studio, choose Windows, and in the Windows Target Version, choose Windows 10.0, and save changes.

3. Choose **Windows-x64** from the Solution Platforms list.

4. Choose a Windows deployment target, such as **Local Machine**.

5. Press F5 to run your app.

    ![Onsen UI on Windows](media/tutorial-onsen/image04.png)

## Use TypeScript in an Onsen UI app
You can use TypeScript in an Onsen UI app.

1. Choose **File**, **New**, then **Project**. On **New Project** dialog, choose **Installed**, **Templates**, **TypeScript**, **Apache Cordova Apps**.

2. Choose one of the following starter templates for your new project:
   * Onsen UI Blank TS
   * Onsen UI Master-Details TS
   * Onsen UI Sliding Menu TS
   * Onsen UI Split View TS
   * Onsen UI Tab Bar TS

3. Choose **OK**.

4. Visual Studio creates the Onsen UI project.

    TypeScript source codes are located in **scripts** folder, with the extension of **.ts**. TypeScript codes will be compiled and saved as **appBundle.js** under **www/scripts** folder. You can modify the compiler options by changing **tsconfig.json** file.

    ![Onsen UI TypeScript](media/tutorial-onsen/image02.png)

## What's Next?
You can use Visual Studio's build and [debug tools](http://taco.visualstudio.com/en-us/docs/debug-using-visual-studio/), use the configuration manager to easily [add device plugins](http://taco.visualstudio.com/en-us/docs/manage-plugins/) to your app to get up and running quick. To learn more about Onsen UI, see the [Onsen UI framework docs](https://onsen.io/docs.html).

![Onsen UI Plugins](media/tutorial-onsen/image03.png)

## Troubleshooting: Let's fix it

A few errors are fairly common in the starter templates when debugging in Visual Studio.

### Error running on Windows 8.1?
Onsen UI templates are intended to run on Windows 10 machines. Please upgrade your development environment to Windows 10 with the latest update of Visual Studio 2015.

### Unhandled exception running on Windows?

Windows apps are more strict about the security when running as a HTML5 apps. Onsen UI includes the sim to support compatibility, but you cannot use **document.write()** or access to **innerHTML**. Please read [an article that describes HTML, CSS, and JavaScript features and differences](https://msdn.microsoft.com/en-us/library/windows/apps/hh465380.aspx) for more details.

### appxrecipe file missing

If you see this error when targeting Windows 10, make sure you set Windows 10.0 as the target in the Windows tab of the configuration designer (config.xml). Then rebuild the project.

### Error saying that the Content Security Policy is missing?

Visual Studio will use the Cordova Whitelist plugin by default, so you need to update index.html in the Cordova app with the following `<meta> element:

```html
<meta http-equiv="Content-Security-Policy" content="default-src 'self' data: gap: https://ssl.gstatic.com 'unsafe-eval'; style-src 'self' 'unsafe-inline'; media-src" *>
```

### Certificate error on Windows?
Make sure your credentials are up to date. Check for any notifications or warning icons in the upper right of Visual Studio.

![Onsen UI Certificate Error](media/tutorial-onsen/image07.png)

You may need to re-enter your credentials. If the notifications indicate that you need to update Cordova tooling, please click on the notifications and follow instructions.

### Visual Studio Emulator for Android won't run?

The VS Emulator for Android requires Hyper-V and is not supported when running on a VM. For more info, see [this information](https://msdn.microsoft.com/en-us/library/mt228282.aspx#NoStart2).

If you have previously run the VS Emulator for Android successfully but now the emulator won't run, try deleting the emulator VM instance in Hyper-V Manager. For more info, see [Troubleshooting](https://msdn.microsoft.com/en-us/library/mt228282).

### Other issues?

If you have errors running the Blank App template (rather than just the Onsen UI starter apps), see these [troubleshooting steps](../tips-and-workarounds/general/tips-and-workarounds-general-readme.md).

If that doesn't resolve issues, post questions on [Onsen UI Community](https://community.onsen.io/).