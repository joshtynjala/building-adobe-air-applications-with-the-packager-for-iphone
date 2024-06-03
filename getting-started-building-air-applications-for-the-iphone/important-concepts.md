# Important concepts

It is important to understand the concepts and workflow involved before
developing an iPhone application using ActionScript 3.0.

## Glossary

The following terms are important to understand when building an iPhone
application.

iPhone Dev Center site  
The Apple Computer website (<https://developer.apple.com/ios/>) where you can do
the following:

- Apply to become an iPhone developer.

- Manage and create iPhone development certificates, provisioning profiles and
  app IDs (which are defined below).

- Submit applications for the App Store.

iPhone development certificate  
Used to identify a developer for the purpose of developing applications.

You obtain this file from Apple. You convert this certificate to a P12
certificate file to sign the iPhone application you create using ActionScript
3.0. See _P12 certificate file_.

You do not need an iPhone development certificate to simply debug and test Flash
Professional CS5 applications on the development computer. However, you need a
development certificate to install and test the application on an iPhone.

The development certificate is different from a distribution certificate, which
you use to build a final version of your application. You obtain a distribution
certificate from Apple when you build a final version of your application.

Certificate signing request  
A file that contains personal information used to generate a development
certificate. Also known as a CSR file.

Provisioning profile  
A file that lets you test or distribute an iPhone application. You obtain
provisioning profile files from Apple. A provisioning profile is assigned to a
specific development certificate, an application ID, and one or more device IDs.
There are different types of provisioning profiles:

- **Development provisioning profile** —Used to install a test version of an
  application to the developer's iPhone.

- **Test provisioning profile** —Also known as an ad-hoc provisioning profile.
  Used to distribute a test version of the application to multiple users (and
  iPhone units). With this provisioning profile and the test application, users
  can test your application without it being submitted to the App Store.

  > **Note:** you can also use a development provisioning profile to distribute
  > test applications to multiple devices.

- **Distribution provisioning profile** —Used to build an iPhone application to
  submit your application to the App Store.

App ID  
A unique string that identifies an iPhone application (or multiple applications)
from a specific developer. You create app IDs at the iPhone Dev Center site.
Each provisioning profile has an associated app ID or app ID pattern. You use
this app ID (or pattern) when developing an application. You use the app ID in
the Flash Professional CS5 iPhone Settings dialog box (or in the application
descriptor file).

App IDs at the iPhone Dev Center contain a bundle seed ID followed by a bundle
identifier. The bundle seed ID is a string of characters, such as 5RM86Z4DJM,
that Apple assigns to the App ID. The bundle identifier contains a reverse
domain name string that you pick. The bundle identifier may end in an asterisk
(\*), indicating a wildcard app ID. Examples are:

- 5RM86Z4DJM.com.example.helloWorld

- 96LPVWEASL.com.example.\* (a wildcard app ID)

There are two types of app ID at the iPhone Dev Center:

- Wildcard app IDs—At the iPhone Dev Center, these app IDs end in an asterisk
  (\*), such as 96LPVWEASL.com.myDomain.\* or 96LPVWEASL.\*. With a provisioning
  profile that uses this kind of app ID, you can generate test applications that
  use an app ID that matches the pattern. For the application's app ID, you can
  replace the asterisk with any string of valid characters. For example, if the
  iPhone Dev Center site specifies 96LPVWEASL.com.example.\* as the app ID, you
  can use com.example.foo or com.example.bar as the application's app ID.

- Specific app IDs—These define a unique app ID to use in an application. At the
  iPhone Dev Center, these app IDs do not end in an asterisk. An example is
  96LPVWEASL.com.myDomain.myApp. With a provisioning profile that uses this kind
  of app ID, applications much match the app ID exactly. For example, if the
  iPhone Dev Center site specifies 96LPVWEASL.com.example.helloWorld as the app
  ID, you must use com.example.foo as the application's app ID.

When developing your application, you specify the app ID in the iPhone settings
dialog box in Flash Professional CS5 or in the application descriptor file. For
more details on app IDs, see the "Deployment tab" section of
[Setting iPhone application properties in Flash Professional CS5](../compiling-and-debugging-iphone-applications/iphone-application-settings/setting-iphone-application-properties-in-flash-professional-cs5.md)
or see
[Setting iPhone application properties in the application descriptor file](../compiling-and-debugging-iphone-applications/iphone-application-settings/setting-iphone-application-properties-in-the-application-descriptor-file.md).

**Important:** When specifying the app ID, disregard the bundle seed ID portion
of the app ID. For example, if Apple lists your app ID as
96LPVWEASL.com.example.bob.myApp, disregard 96LPVWEASL—use com.example.bob.myApp
as the app ID. If Apple lists your app ID as 5RM86Z4DJM.\*, disregard
5RM86Z4DJM—this is a wildcard app ID.

You can find the app ID (or wildcard app ID pattern) associated with a
provisioning profile at the iPhone Dev Center
(<https://developer.apple.com/ios/>). Go to the iPhone Developer Program Portal
and then go to the Provisioning section.

P12 certificate file  
A P12 file (a file with a .p12 extension) is a type of certificate file (a
Personal Information Exchange file). The Packager for iPhone uses this type of
certificate to build an iPhone application. You convert the developer
certificate you receive from Apple into this form of certificate.

Unique Device ID  
A unique code identifying a specific iPhone. Also known as a UDID or a device
ID.

## Overview of the development workflow

When developing an application for the iPhone, you follow these steps:

1.  Install Flash Professional CS5 from Adobe.

2.  Install iTunes.

3.  Obtain developer files from Apple. These files include the developer
    certificate and provisioning profiles. See
    [Obtaining developer files from Apple](./obtaining-developer-files-from-apple/index.md).

4.  Convert the development certificate to a P12 certificate file. Flash CS5
    requires the certificate to be a P12 certificate. See
    [Obtaining developer files from Apple](./obtaining-developer-files-from-apple/index.md).

5.  Use iTunes to associate your provisioning profile with your iPhone.

6.  Write the application in Flash Professional CS5.

    It is important to understand the best practices for designing and
    optimizing code for an iPhone application. See
    [iPhone application design considerations](../iphone-application-design-considerations/index.md).

    Also, some ActionScript 3.0 APIs are limited or unsupported on the iPhone.
    See
    [ActionScript 3.0 API support for mobile devices](../actionscript-3.0-support-for-mobile-devices/index.md).

    You can also use Flash Builder 4.0 to edit the ActionScript 3.0 code for the
    application.

    You can use Flash Professional CS5 to test your application on the
    development computer.

7.  Create icon art and initial screen art for the application. Every iPhone
    application includes a set of icons that identify it to users. The iPhone
    displays the initial screen image as the program is loading. See
    [iPhone icon and initial screen images](../compiling-and-debugging-iphone-applications/iphone-icon-and-initial-screen-images.md).

8.  Edit the iPhone settings. These settings include the following:

    - The identity of the application (including the filename, the application
      name, the version number, and the app ID)

    - The location of the source icon art for the application

    - The P12 certificate and the provisioning profile assigned to the
      application

    - The initial aspect ratio of the application

    In Flash Professional CS5, you can edit these settings in the iPhone
    Settings dialog box. For details, see
    [Setting iPhone application properties in Flash Professional CS5](../compiling-and-debugging-iphone-applications/iphone-application-settings/setting-iphone-application-properties-in-flash-professional-cs5.md).

    You can also edit these settings directly in the application descriptor
    file. For more information, see
    [Setting iPhone application properties in the application descriptor file](../compiling-and-debugging-iphone-applications/iphone-application-settings/setting-iphone-application-properties-in-the-application-descriptor-file.md).

9.  Compile the IPA file using the Packager for iPhone. See
    [Compiling an iPhone application installer (IPA) file](../compiling-and-debugging-iphone-applications/compiling-an-iphone-application-installer-ipa-file/index.md).

10. Install and test the application on your iPhone. Use iTunes to install the
    IPA file.

For ad hoc distribution, repeat this general process, but use a test
provisioning profile instead of a development provisioning profile. For the
final distribution of the application, repeat this process using the
distribution provisioning profile. (See the [Glossary](#glossary) for
information on the different types of provisioning profiles.)

When you have built a distribution version of your application, see the
instructions in
[Submitting your iPhone application to the App Store](../compiling-and-debugging-iphone-applications/submitting-your-iphone-application-to-the-app-store.md).

For a quick tutorial on building a basic iPhone application, see
[Creating a Hello World iPhone application with Flash Professional CS5](./creating-a-hello-world-iphone-application-with-flash-professional-cs5/index.md).
