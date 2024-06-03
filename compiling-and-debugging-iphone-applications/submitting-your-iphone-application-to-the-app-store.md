# Submitting your iPhone application to the App Store

To submit your application to the App Store:

1.  Obtain a distribution certificate and provisioning profile from the iPhone
    Dev Center website (<https://developer.apple.com/ios/>).

    A distribution certificate is named "iPhone Developer: XXX.cer," where XXX
    is your name.

    For more information, see
    [Obtaining developer files from Apple](../getting-started-building-air-applications-for-the-iphone/obtaining-developer-files-from-apple/index.md).

2.  Convert the distribution certificate into a P12 file.

    For more information, see
    [Converting a developer certificate into a P12 file](../getting-started-building-air-applications-for-the-iphone/obtaining-developer-files-from-apple/converting-a-developer-certificate-into-a-p12-file.md).

3.  Compile your application using the P12 file and provisioning profile.

    Use the P12 file you made based on the distribution certificate. Use the app
    ID associated with the distribution provisioning profile.

    For more information, see
    [Compiling an iPhone application installer (IPA) file](./compiling-an-iphone-application-installer-ipa-file/index.md).

4.  Submit the application at the iPhone Dev Center website
    (<https://developer.apple.com/ios/>).

    > **Important:** Apple requires that you use the Apple _Application Loader_
    > program in order to upload applications to the App Store. Apple only
    > publishes _Application Loader_ for Mac OS X. While you can develop an AIR
    > application for the iPhone using a Windows computer, you must have access
    > to a computer running OS X (version 10.5.3, or later) to submit the
    > application to the App Store. You can get the Application Loader program
    > from the Apple iOS Dev Center.
