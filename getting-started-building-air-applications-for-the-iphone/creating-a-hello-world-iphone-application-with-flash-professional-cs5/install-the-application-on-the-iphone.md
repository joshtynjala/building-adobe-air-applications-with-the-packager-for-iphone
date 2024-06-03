# Install the application on the iPhone

<div>

To install the iPhone application for testing on an iPhone:

1.  Open the iTunes application.

2.  If you have not already done so, add the provisioning profile for this
    application to iTunes. In iTunes, select File \> Add File To Library. The
    select the provisioning profile file (which has mobileprovision as the file
    type).

    For now, to test the application on your developer iPhone, use the
    development provisioning profile.

    Later, when distributing an application to the iTunes Store, use the
    distribution profile. To distribute the application ad-hoc (to multiple
    devices without going through the iTunes Store), use the ad-hoc provisioning
    profile.

    For more information on provisioning profiles, see
    [Obtaining developer files from Apple](../obtaining-developer-files-from-apple/index.md).

3.  Some versions of iTunes do not replace the application if the same version
    of the application is already installed. In this case, delete the
    application from your device and from the list of applications in iTunes.

4.  Double-click the IPA file for your application. It should appear in the list
    of applications.

5.  Connect your iPhone to the USB port on your computer.

6.  In iTunes, check the Application tab for the device, and ensure that the
    application is selected in the list of applications to be installed.

7.  Select the device in the left-hand list of the iTunes application. Then
    click the Sync button. When the sync completes, the Hello World application
    appears on your iPhone.

If the new version is not installed, delete it from your iPhone and from the
list of applications in iTunes, and then redo this procedure. This may be the
case if the currently installed version uses the same application ID and
version.

If iTunes displays an error when you try to install your application, see
"Troubleshooting application installation problems" in
[Installing an iPhone application](../../compiling-and-debugging-iphone-applications/installing-an-iphone-application.md).

</div>

<div>

<div>

</div>

</div>
