# Installing an iPhone application

To install your development application on an iPhone, you add the provisioning
profile to the iPhone, and then you install the application on the iPhone.

#### Add the provisioning profile to the iPhone

To add the provisioning profile to the iPhone:

1.  In iTunes, select File \> Add To Library. The select the provisioning
    profile file (which has mobileprovision as the filename extension).

    Make sure that your iPhone is added to the provisioning profile. You can
    manage provisioning profiles at the Apple iPhone Dev Center site
    (<https://developer.apple.com/ios/>). Go to the iPhone Developer Program
    Portal section of the site. Click the Devices link to manage the list of
    devices your development application can be installed on. Click the
    Provisioning link to manage your provisioning profiles.

2.  Connect your iPhone to your computer and sync.

For information on obtaining a provisioning profile, see
[Obtaining developer files from Apple](../getting-started-building-air-applications-for-the-iphone/obtaining-developer-files-from-apple/index.md).

#### Install the application

You install your development application in the same way that you install any
other IPA file:

1.  If you have previously installed a version of the application, delete the
    application from your device and from the list of applications in iTunes.

2.  Add the application in iTunes, in any of the following ways:

    - On the File menu (in iTunes), choose the Add to Library command. Then
      select the IPA file and click the Open button.

    - Double-click the IPA file.

    - Drag the IPA file into the iTunes library.

3.  Connect your iPhone to the USB port on your computer.

4.  In iTunes, check the Application tab for the device, and ensure that the
    application is selected in the list of applications to be installed.

5.  Sync your iPhone.

#### Troubleshooting application installation problems

If iTunes displays an error when you try to install the application, check the
following:

- Make sure the device ID is added to the provisioning profile.

- To make sure that the provisioning profile is installed, you can drag it to
  iTunes or use the File \> Add to Library command.

Also, check that your application's app ID matches the Apple app ID:

- If your Apple app ID is com.myDomain.\*, the app ID in the app descriptor file
  or the App ID in the iPhone Settings dialog box must start with com.myDomain
  (such as com.myDomain.anythinghere).

- If your Apple app ID is com.myDomain.myApp, the app ID in the app descriptor
  file or the Flash Profession CS5 user interface must be com.myDomain.myApp.

- If your Apple app ID is \*, the App ID in the app descriptor file or the Flash
  Profession CS5 user interface can be anything.

You set the application's app ID in the iPhone Settings dialog box in Flash
Professional CS5 or in the application descriptor file.
