# iPhone icon and initial screen images

<div>

All iPhone applications have icons which appear in the user interface of the
iTunes application and on the iPhone.

<div>

#### iPhone application icons

You define the following icons for an iPhone application:

<div>

- A 29-by-29–pixel icon—Spotlight search results on the iPhone and iPod touch
  use this icon.

- A 48-by-48–pixel icon—Spotlight search results on the iPad use this icon.

- A 57-by-57–pixel icon—The iPhone and iPod touch home screens display this
  icon.

- A 72-by-72–pixel icon (optional)—The iPad home screen displays this icon.

- A 512-by-512–pixel icon—iTunes displays this icon. The 512-pixel PNG file is
  used only for testing development versions of your application When you submit
  the final application to the Apple App Store, you submit the 512 image
  separately, as a JPG file. It is not included in the IPA.

</div>

In Flash Professional CS5, add these icons in Icons tab of the the iPhone
Settings dialog box. See
[Setting iPhone application properties in Flash Professional CS5](./iphone-application-settings/setting-iphone-application-properties-in-flash-professional-cs5.md).

You can also add the locations of the icons to the application descriptor file:

    <icon>
        <image29x29>icons/icon29.png</image29x29>
        <image57x57>icons/icon57.png</image57x57>
        <image72x72>icons/icon72.png</image72x72>
        <image512x512>icons/icon512.png</image512x512>
    </icon>

The iPhone adds a glare effect to the icon. You do not need to include it in
your source image. To remove this default glare effect, add the following to the
`InfoAdditions` element in the application descriptor file:

    <InfoAdditions>
    <![CDATA[
        <key>UIPrerenderedIcon</key>
        <true/>
    ]]>
    </InfoAdditions>

See
[Setting iPhone application properties in the application descriptor file](./iphone-application-settings/setting-iphone-application-properties-in-the-application-descriptor-file.md).

</div>

<div>

#### The initial screen art (Default.png)

All iPhone applications display an initial image while the application loads on
the iPhone. You define the initial image in a PNG file named Default.png. In the
main development directory, create a PNG file named Default.png. (Do _not_ put
this file in a subdirectory. Be sure to name the file Default.png, with an
uppercase D.)

The Default.png file is 320 pixels wide by 480 pixels tall, regardless of the
initial orientation of the application or whether it is full-screen or not.

If the initial orientation of your application is landscape, use the same
dimensions that a portrait application uses: 320 pixels wide by 480 pixels high.
However, rotate the artwork 90° counter-clockwise in the PNG file. The left side
of the PNG art corresponds to the top of the iPhone screen in landscape mode.
(For information on setting the initial application orientation, see
[iPhone application settings](./iphone-application-settings/index.md).)

For an application that is not full-screen, the top 20 pixels of the default
image art are ignored. The iPhone displays its status bar over the 20 pixel-wide
rectangle at the top of the default image. In a landscape-orientation
application, this region corresponds to the left 20 pixel-wide rectangle of the
Default.png file (which displays on the top in landscape mode). In a
portait-orientation application, this region is the top 20 pixel-wide rectangle
of the Default.png file.

For most applications, the Default.png image should match the startup screen of
the application. To take a screenshot of the startup screen of your application:

1.  Open your application on the iPhone. When the first screen of the user
    interface appears, press and hold the Home button (below the screen). While
    holding the Home button, press the Power/Sleep button (at the top of the
    device). This takes a screenshot and sends it to the Camera Roll.

2.  Transfer the image to your development computer by transferring photos from
    iPhoto or another photo transfer application. (On Mac OS, you can also use
    the Image Capture application.)

    You can also e-mail the photo to your development computer:

    - Open the Photos application.

    - Open the Camera Roll.

    - Open the screenshot image you captured.

    - Tap the image and then tap the "forward" (arrow) button in the
      bottom-left-hand corner. Then click the Email Photo button and send the
      image to yourself.

<div>

<div>

Note: You can create any art you'd like for the Default.png file, as long as it
is the correct dimensions. However, it is often best to have the Default.png
image match the initial state of your application.

</div>

</div>

Do not include text in the Default.png image if your application is localized
into multiple languages. The Default.png is static, and the text would not match
other languages.

In Flash Professional CS5, be sure to add the Default.png file to the Included
Files list in the iPhone settings dialog box. See
[Setting iPhone application properties in Flash Professional CS5](./iphone-application-settings/setting-iphone-application-properties-in-flash-professional-cs5.md).

When compiling using the PFI application on the command line, be sure to
reference this file in the list of included assets. See
[Creating an iPhone application installer file from the command line](./compiling-an-iphone-application-installer-ipa-file/creating-an-iphone-application-installer-file-from-the-command-line.md).

</div>

</div>

<div>

<div>

</div>

</div>
