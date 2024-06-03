# Setting iPhone application properties in Flash Professional CS5

<div>

The Flash Professional CS5 iPhone Settings dialog box lets you define many basic
properties of the iPhone application.

To open the iPhone Settings dialog box:

![](../../img/dingbat.png) Choose File \> iPhone Settings.

<div>

#### General tab

The General tab includes the following iPhone-related settings:

- Output file—The name of the application displayed under the application icon
  in the iPhone. Do not include a plus sign (+) character in the output
  filename.

- App name—The name of the application displayed under the application icon in
  the iPhone. Do not include a plus sign (+) character in the app name.

- Version—Helps users determine which version of your application they are
  installing. The version is used as the CFBundleVersion of the iPhone
  application. It must be in a format similar to nnnnn\[.nn\[.nn\]\] where n is
  a digit 0-9 and brackets indicate optional components, such as 1, 1.0, or
  1.0.1. iPhone versions must contain only digits and decimal points. iPhone
  versions can contain up to two decimal points.

- Aspect ratio—The initial aspect ratio of the application (portrait or
  landscape).

- Full screen—Whether the application uses the full screen, or if it displays
  the iPhone status bar.

- Auto orientation—Select this application to have the application's display
  contents reorient when the iPhone is reoriented.

  When using auto-orientation, for best results add ActionScript code to set the
  `align` property of the Stage to the following:

      stage.align = StageAlign.TOP_LEFT;
      stage.scaleMode = StageScaleMode.NO_SCALE;

- Rendering—How display objects are rendered on the iPhone:

  - CPU—The application uses the CPU to render all display objects. No hardware
    acceleration is used.

  - GPU—The application uses the iPhone GPU to composite bitmaps.

  - Auto—This feature has not been implemented.

  For more information, see
  [Hardware acceleration](../../iphone-application-design-considerations/hardware-acceleration.md).

- Included files—Add all files and directories to package in the iPhone
  application. The main SWF file and the application descriptor file are
  included by default. Add any other required assets to the Included Files list.
  Be sure to add the initial screen art file (Default.png) to the Included Files
  list.

</div>

<div>

#### Deployment tab

The Deployment tab includes signing and compilation settings for the
application:

- iPhone digital signature—Specify a P12 certificate file and the password for
  the certificate. You must convert the Apple iPhone certificate to the .p12
  format. For more information, see
  [Obtaining developer files from Apple](../../getting-started-building-air-applications-for-the-iphone/obtaining-developer-files-from-apple/index.md).

- Provisioning file—Point to the provisioning file for this application, which
  you obtained from Apple. For more information, see
  [Obtaining developer files from Apple](../../getting-started-building-air-applications-for-the-iphone/obtaining-developer-files-from-apple/index.md).

- App ID—The app ID uniquely identifies your application. If the provisioning
  file is tied to a specific application ID, Flash Professional CS5 sets this
  field, and you cannot edit it. Otherwise, the provisioning profile allows
  multiple (wildcard) app IDs. Provide an application ID that matches the
  application ID wildcard pattern you provided to Apple:

  - If your Apple app ID is com.myDomain.\*, the app ID in the iPhone Settings
    dialog box must start with com.myDomain. (such as com.myDomain.myApp or
    com.myDomain.app22).

  - If your Apple app ID is \*, the App ID in the iPhone Settings dialog box can
    be any string of valid characters.

  You can find the Apple app ID (or wildcard app ID pattern) associated with
  your provisioning profile at the iPhone Dev Center
  (<https://developer.apple.com/ios/>). Go to the iPhone Developer Program
  Portal and then go to the Provisioning section.

  **Important:** Disregard the characters at the front of the Apple app ID.
  Apple calls this string the Bundle Seed ID. For example, if Apple lists your
  app ID as 96LPVWEASL.com.example.bob.myApp, disregard 96LPVWEASL—use
  com.example.bob.myApp as the app ID. If Apple lists your app ID as
  5RM86Z4DJM.\*, disregard 5RM86Z4DJM—this is a wildcard app ID.

- iPhone deployment type:

  - Quick publishing for device testing—Choose this option to quickly compile a
    version of the application for testing on your developer iPhone.

  - Quick publishing for device debugging—Choose this option to quickly compile
    a debug version of the application for testing on your developer iPhone.
    With this option, the Flash Professional CS5 debugger can receive `trace()`
    output from the iPhone application. (See
    [Debugging an iPhone application](../debugging-an-iphone-application.md).)

  - Deployment - Ad Hoc—Choose this option to create an application for ad hoc
    deployment. See the Apple iPhone developer center

  - Deployment - Apple App Store—Choose this option to create a final version of
    the IPA file for deployment to the Apple App Store.

</div>

<div>

#### Icons tab

On the Icons tab, specify the location of the 29 x 29-pixel icon image, the 48 x
48-pixel icon image, the 57 x 57-pixel icon image, the 72 x 72-pixel icon image,
and the 512 x 512-pixel icon image. See
[iPhone icon and initial screen images](../iphone-icon-and-initial-screen-images.md).

<div>

<div>

Note: Options for the 48 x 48-pixel and 72 x 72-pixel are not included in the
version of the Packager for iPhone Preview included with Flash Professional CS5.
In Flash Professional CS5 select Help \> Updates to add these options.

</div>

</div>

</div>

</div>

<div>

<div>

</div>

</div>
