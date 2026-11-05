# User guide to the Supervision App for Android

## Background

The Supervision App is designed for field users to manage and monitor supervision activities. It lets you synchronize with DHIS2, and it supports offline use.

The main features are:

* A dashboard showing the current status of indicators.
* An overview of previous supervision action plans.
* Access to supervision tracker forms.  
* Synchronization for sending collected data to DHIS2. 
* Offline functioning.

## Technical specification and installation

### Android requirements

* Works on Android 13 and later
* Compatible with phones and tablets

### Installation instructions

Until the app is published on the Play Store, you can install it manually.

1. Download the APK from your DHIS2 administrator, or get the download link from your DHIS2 administrator: [Android Supervision App](https://github.com/HISPWCA/Supervision-Apks/releases/tag/v.1.2.5).
2. Locate the file in your Downloads folder.
3. Tap the file and follow the on‑screen instructions to install or update the app.

![The GitHub release page for Supervision version 1.2.5, with the APK file under Assets.](resources/images/dq_android_supervision/Image14_framed.png)

![The Android dialog that asks you to confirm the download of the APK file.](resources/images/dq_android_supervision/Image15_framed.png)

![The Android dialog that asks you to confirm the update of the Supervision app.](resources/images/dq_android_supervision/Image16_framed.png)

## Login page

1. Open the app.
2. Enter the **Server url**, **Username**, and **Password**.
3. Tap **Log in** to open the home interface.

![The login screen with the server URL, username, and password fields.](resources/images/dq_android_supervision/Image17_framed.png)

![The app synchronizes the configuration after login.](resources/images/dq_android_supervision/Imageconfig_framed.png)

## Home interface

After you log in, the app shows the available supervision forms, for example DQR-RSC.

First-time setup:

1. Tap the menu icon (three horizontal lines).
2. Tap **Settings**.
3. Tap **Sync configuration**.

![The home screen with the list of available supervision programs.](resources/images/dq_android_supervision/Image3_framed.png)

![The side menu with the Settings item.](resources/images/dq_android_supervision/Image1_framed.png)

![The Settings screen with the Sync configuration option.](resources/images/dq_android_supervision/Image2_framed.png)

## Selecting a supervision event

1. Choose the tracker program, for example DQR-RSC.

![The list of supervision programs, where you choose the tracker program.](resources/images/dq_android_supervision/Image3_framed.png)

2. Choose the organisation unit to supervise.

![The list of organisation units for the chosen program, with the Synchronize button at the top.](resources/images/dq_android_supervision/Image4_framed.png)

3. View the planned supervisions (events). The most recent appear at the top.

![An organisation unit with its planned supervision events, most recent first.](resources/images/dq_android_supervision/Image22_framed.png)

1. Tap an event to show the charts of the indicators whose quality you want to check. The single values at the top are the values for the period shown at the top.
2. To show the values for another period, tap the period and choose the new period in the calendar.

![The event dashboard with the period selector, single values, and a 12-month chart.](resources/images/dq_android_supervision/Image10_framed.png)

![The event dashboard with the legend, a 12-month indicator chart, and the Open form button.](resources/images/dq_android_supervision/Image8_framed.png)

## Open the form

1. Tap **Open form** (top right).
2. Sections are collapsed by default. Tap **Show Fields** to expand.
3. Fill in the required fields section by section.
4. When you have finished, tap **Save** (disk icon, bottom right).

![The event dashboard with the Open form button at the top right.](resources/images/dq_android_supervision/Image8_framed.png)

![The supervision form with the event details and facility information sections.](resources/images/dq_android_supervision/Image20_framed.png)

## Supervision dashboard: results visualization

You can view supervision results directly on the Android device, even if the data is not synchronized.

1. Tap the chart icon at the bottom center.
2. To show other indicators, tap the other tabs of the dashboard.


   > **Note**
   >
   > The app generates the dashboard automatically from the data entered, even if there is no Internet connection.

3. You can share the dashboard as a PDF file, online or offline. When online, you can share the PDF file with any communication app on the Android device, for example WhatsApp, Snapchat, Gmail, or Slack. When no Internet connection is available, you can share the file using Bluetooth.
4. To share using Bluetooth, make sure that Bluetooth is enabled on both devices and that they are paired. You can also download the file to your device: tap **Share** > **Printer** > **pdf**.

![The supervision dashboard with indicator tabs and charts.](resources/images/dq_android_supervision/Imageanalytics_framed.png)

![The Android share panel for the dashboard PDF file.](resources/images/dq_android_supervision/Image13_framed.png)

## Data synchronization

After you save supervision data:

1. When back online, go to the supervision selection page and tap **Synchronize**.
2. Alternatively, go to **Settings** > **Synchronize Data** to upload locally saved supervision data to the DHIS2 server.
