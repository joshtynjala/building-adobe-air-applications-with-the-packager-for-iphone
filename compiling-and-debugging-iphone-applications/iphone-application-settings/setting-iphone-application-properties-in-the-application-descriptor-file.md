# Setting iPhone application properties in the application descriptor file

The application descriptor file is an XML file containing properties for the
entire application, such as its name, version, copyright, and other settings.

Flash Professional CS5 generates an application descriptor file based on the
settings in the iPhone Settings dialog box. However, you can also edit the
application descriptor file in a text editor. Flash Professional names the
application descriptor file by adding "-app.xml" to your project name. For
example, the application descriptor file for a HelloWorld project is named
HelloWorld-app.xml. Edit the application descriptor file if you want to define
settings not supported in the Flash Professional CS5 iPhone Settings dialog box.
For example, you can define the `InfoAdditions` element to define info.Plist
settings for the application.

**Important:** Do not edit the application descriptor file while the Flash
Professional CS5 dialog box is open. Save changes to the application descriptor
file before you open the iPhone Settings dialog box.

Here's an example application descriptor file:

    <?xml version="1.0" encoding="UTF-8"?>
    <application xmlns="http://ns.adobe.com/air/application/2.0">
    <id>com.example.HelloWorld</id>
    <filename>HelloWorld</filename>
    <name>Hello World</name>
    <version>v1</version>
    <initialWindow>
        <renderMode>gpu</renderMode>
        <content>HelloWorld.swf</content>
        <fullScreen>true</fullScreen>
        <aspectRatio>portrait</aspectRatio>
        <autoOrients>true</autoOrients>
    </initialWindow>
    <supportedProfiles>mobileDevice desktop</supportedProfiles>
    <icon>
        <image29x29>icons/icon29.png</image29x29>
        <image57x57>icons/icon57.png</image57x57>
        <image512x512>icons/icon512.png</image512x512>
    </icon>
    <iPhone>
        <InfoAdditions>
            <![CDATA[
                <key>UIStatusBarStyle</key>
                <string>UIStatusBarStyleBlackOpaque</string>
                <key>UIRequiresPersistentWiFi</key>
                <string>NO</string>
            ]]>
        </InfoAdditions>
    </iPhone>
    </application>

Here are details on the settings in this application descriptor file:

- In the `<application>` element, the AIR 2.0 namespace is required for building
  iPhone applications:

  **\<application xmlns="http://ns.adobe.com/air/application/2.0"\>**

- The `<id>` element:

  **\<id\>com.example.as3.HelloWorld\</id\>** The application ID uniquely
  identifies your application. The recommended form is a dot-delimited,
  reverse-DNS-style string, such as `"com.company.AppName"`. The compiler uses
  this value as the bundle ID for the iPhone application.

  If the provisioning file is tied to a specific app ID, use that app ID in this
  element. Disregard the characters Apple assigns at the start of the Apple app
  ID (known as the bundle seed ID). For example, if the app ID for the
  provisioning profile is 96LPVWEASL.com.example.bob.myApp, use
  com.example.bob.myApp as the app ID in the application descriptor file.

  If the provisioning profile allows multiple (wildcard) app IDs, its app ID
  ends in an asterisk (such as 5RM86Z4DJM.\*). Provide an application ID that
  matches the app ID wildcard pattern you provided to Apple:

  - If your Apple app ID is com.myDomain.\*, the app ID in the application
    descriptor file must start with com.myDomain. You can specify an app ID such
    as com.myDomain.myApp or com.myDomain.app22.

  - If your Apple app ID is \*, the App ID in the app descriptor file can be any
    string of valid characters.

  You can find the Apple app ID (or wildcard app ID pattern) associated with
  your provisioning profile at the iPhone Dev Center (
  <https://developer.apple.com/ios/>). Go to the iPhone Developer Program Portal
  and then go to the Provisioning section.

  **Important:** Disregard the characters at the front of the Apple app ID.
  Apple calls this string the Bundle Seed ID. For example, if Apple lists your
  app ID as 5RM86Z4DJM.\*, disregard 5RM86Z4DJM—this is a wildcard app ID. If
  Apple lists your app ID as 96LPVWEASL.com.example.bob.myApp, disregard
  96LPVWEASL—use com.example.bob.myApp as the app ID.

- The `<filename>` element:

  **\<filename\>HelloWorld\</filename\>** The name used for the iPhone installer
  file. Do not include a plus sign (+) character in the filename.

- The `<name>` element:

  **\<name\>Hello World\</name\>** The name of the application displayed in the
  iTunes application and in the iPhone. Do not include a plus sign (+) character
  in the name.

- The `<version>` element:

  **\<version\>1.0\</version\>** Helps users to determine which version of your
  application they are installing. The version is used as the CFBundleVersion of
  the iPhone application. It must be in a format similar to nnnnn\[.nn\[.nn\]\]
  where n is a digit 0-9 and brackets indicate optional components, such as 1,
  1.0, or 1.0.1. iPhone versions must contain only digits and decimal points.
  iPhone versions can contain up to two decimal points.

- The `<initialWindow>` element contains the following child elements to specify
  the properties for of the initial appearance of the application:

  **\<content\>HelloWorld.swf\</content\>** Identifies the root SWF file to
  compile into the iPhone application.

  **\<visible\>true\</visible\>** This is a required setting.

  **\<fullScreen\>true\</fullScreen\>** Specifies that the application uses the
  entire screen of the iPhone.

  **\<aspectRatio\>portrait\</aspectRatio\>** Specifies that the initial aspect
  ratio of the application is in portrait mode (rather than landscape). Note the
  Default.png file used to define the initial window of the application should
  be 320 pixels wide and 480 pixels high, regardless of this setting. (See
  [iPhone icon and initial screen images](../iphone-icon-and-initial-screen-images.md).)

  **\<autoOrients\>true\</autoOrients\>** (Optional) Specifies whether the
  orientation of content in the application automatically reorients as the
  device itself changes physical orientation. The default value is `true`. You
  can cancel automatic orientation by calling the `preventDefault()` method of
  an `orientationChanging` event. dispatched by the Stage object. For more
  information, see
  [Setting and detecting screen orientation](https://web.archive.org/web/20220814030226/http://help.adobe.com/en_US/as3/dev/WS5b3ccc516d4fbf351e63e3d118676a47e0-8000.html#WS789ea67d3e73a8b220f0e28f123c3c58a85-8000).

  When using auto-orientation, for best results set the `align` property of the
  Stage to the following:

      stage.align = StageAlign.TOP_LEFT;
      stage.scaleMode = StageScaleMode.NO_SCALE;

  **\<renderMode\>gpu\</renderMode\>** (Optional) The rendering mode used by the
  application. There are three possible settings:

  - `cpu` —The application uses the CPU to render all display objects. No
    hardware acceleration is used.

  - `gpu` —The application uses the iPhone GPU to composite bitmaps.

  - `auto` —This feature has not been implemented.

  For more information, see
  [Hardware acceleration](../../iphone-application-design-considerations/hardware-acceleration.md).

- The `<profiles>` element:

  **\<profiles\>mobileDevice\</profiles\>** Limits the application to be
  compiled into the mobile device profile. This profile currently only supports
  iPhone applications. There are three supported profiles:

  - `desktop` —A desktop AIR application.

  - `extendedDesktop` —A desktop AIR application with support for the native
    process API.

  - `mobileDevice` —An AIR application for a mobile device. Currently, iPhone is
    the only supported mobile device.

  Limiting the application to a specific profile prevents it from being compiled
  into other profiles. If you specify no profile, then you can compile an
  application for any of these profiles. You can specify multiple profiles by
  listing them each, separated by spaces, in the `<profiles>` element.

  Be sure to include `mobileDevice` as a supported profile (or leave the
  `<profiles>` element empty).

- The `<icon>` element contains the following child elements to specify the
  icons used by the application:

  **\<image29x29\>icons/icon29.png\</image29x29\>** This is the image used in
  Spotlight search results.

  **\<image48x48\>icons/icon48.png\</image48x48\>** This is the image used in
  Spotlight search results on the iPad.

  **\<image57x57\>icons/icon57.png\</image57x57\>** This is the image used on
  the iPhone and iPod Touch home screen.

  **\<image72x72\>icons/icon72.png\</image72x72\>** This is the image used on
  the iPad home screen.

  **\<image512x512\>icons/icon512.png\</image512x512\>** This is the image used
  in the iTunes application.

  The Packager for iPhone tool uses the 29, 57, and 512 icons referenced in the
  application descriptor file. The tool copies them to files called
  Icon-Small.png, Icon.png, and iTunesArtwork respectively. To avoid having this
  copy made, you can package those files directly. Package them directly by
  placing them in the directory that contains the application descriptor file
  and list the correct names and paths.

  The 512 image is for internal testing only. When submitting an application to
  Apple you submit the 512 image separately. It is not included in the IPA.
  Specify it so you can make sure that your 512 image looks good in iTunes
  before submitting it.

- The `<iPhone>` element contains the following child elements to specify
  iPhone-specific settings:

  **\<InfoAdditions\>\</InfoAdditions\>** contains the child elements specifying
  key-value pairs to use as Info.plist settings for the application:

      <![CDATA[
      <key>UIStatusBarStyle</key>
      <string>UIStatusBarStyleBlackOpaque</string>
      <key>UIRequiresPersistentWiFi</key>
      <string>NO</string>
      ]]>

  In this example, the values set the status bar style of the application and
  state that the application does not require persistent Wi-Fi access.

  The InfoAdditions settings are enclosed in a `CDATA` tag.

  For iPad support, include key-value settings for `UIDeviceFamily`. The
  `UIDeviceFamily` setting is an array of strings. Each string defines supported
  devices. The `<string>1</string>` setting defines support for the iPhone and
  iPod Touch. The `<string>2</string>` setting defines support for the iPad. The
  `<string>3</string>` setting defines support for the tvOS. If you specify only
  one of these strings, only that device family is supported. For example, the
  following setting limits support to the iPad:

      <key>UIDeviceFamily</key>
      <array>
          <string>2</string>
      </array>>

  The following sets support for both device families (iPhone/iPod Touch and
  iPad):

      <key>UIDeviceFamily</key>
      <array>
      <string>1</string>
      <string>2</string>
      </array>

  For information on other Info.plist settings, see the Apple developer
  documentation.
