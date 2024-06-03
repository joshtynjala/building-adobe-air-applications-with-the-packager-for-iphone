# Edit application settings

<div>

**Important:** If you have not already done so, download the required developer
applications and files for iPhone development. See
[Obtaining developer files from Apple](../obtaining-developer-files-from-apple/index.md).

In the Flash Professional CS5 iPhone Settings dialog box, define many basic
properties of the iPhone application.

<div>

1.  Choose File \> iPhone OS Settings.

2.  In the General tab, make the following settings:

    - Output file: HelloWorld.ipa

      This is the filename of the iPhone installer file to be generated.

    - App name: Hello World

      This is the name of the application displayed under the application icon
      in the iPhone.

    - Version: 1.0

      The version of the application.

    - Aspect ratio: portrait

    - Full screen: selected.

    - Auto orientation: deselected.

    - Rendering: CPU

      The other options, GPU and Auto, use hardware acceleration for rendering.
      This feature can help improve performance for graphics-intensive
      applications (such as games) that have been designed to take advantage of
      hardware acceleration. For more information, see
      [Hardware acceleration](../../iphone-application-design-considerations/hardware-acceleration.md).

    - Included files: Add the initial screen art file (Default.png) to the
      Included Files list.

    <div>

    Note: For this Hello World example, do not modify the settings from those
    provided in these instructions. Some settings, such as the Version setting,
    have specific restrictions. These restrictions are described in
    [iPhone application settings](../../compiling-and-debugging-iphone-applications/iphone-application-settings/index.md).

    </div>

3.  In the Deployment tab, make the following settings:

    - Certificate: Browse and select the .p12 certificate based on the developer
      certificate you obtained from Apple.

      This certificate is used to sign the file. You must convert the Apple
      iPhone certificate to the .p12 format. For more information, see
      [Obtaining developer tools from Adobe](../obtaining-developer-tools-from-adobe.md).

    - Password: enter the password for the certificate.

    - Provisioning file: Browse and select the developer provisioning file that
      you obtained from Apple. See
      [Obtaining developer files from Apple](../obtaining-developer-files-from-apple/index.md).

    - App ID: If this field is selectable, you can enter an application ID that
      matches the application ID you provided to Apple (such as
      com.example.as3.HelloWorld).

      The application ID uniquely identifies your application.

      If the field is not selectable, then the provisioning profile is bound a
      specific application ID. The application ID is displayed in the field.

      For details on specifying an app ID, see the "Deployment tab" section of
      [Setting iPhone application properties in Flash Professional CS5](../../compiling-and-debugging-iphone-applications/iphone-application-settings/setting-iphone-application-properties-in-flash-professional-cs5.md).

4.  In the Icons tab, click the Icon 29 x 29 in the Icons list. Then specify the
    location of the 29 x 29-pixel PNG file you created earlier (see
    [Create icon art and initial screen art for the application](./create-icon-art-and-initial-screen-art-for-the-application.md)).
    Then specify PNG files for the 57 x 57-pixel icon and the 512 x 512-pixel
    icon.

5.  Click the OK button.

6.  Save the file.

</div>

For details on the application settings, see
[iPhone application settings](../../compiling-and-debugging-iphone-applications/iphone-application-settings/index.md).

</div>

<div>

<div>

</div>

</div>
