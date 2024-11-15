# Edit the initial screen graphic

Before you compiled your application, you created a Default.png file (see
[Create icon art and initial screen art for the application](./create-icon-art-and-initial-screen-art-for-the-application.md)).
This PNG file serves as the startup image while the application loads. When you
tested the application on your iPhone, you may have noticed this blank screen at
startup.

You should change this image to match the startup screen of your application
("Hello World!"):

1.  Open your application on your device. When the first "Hello World" text
    appears, press and hold the Home button (below the screen). While holding
    the Home button, press the Power/Sleep button (at the top of the iPhone).
    This takes a screenshot and sends it to the Camera Roll.

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

3.  Replace the Default.png file (in your development directory) with a PNG
    version of the screen capture image.

4.  Recompile the application (see
    [Compiling the IPA file](../../compiling-and-debugging-iphone-applications/compiling-an-iphone-application-installer-ipa-file/index.md))
    and reinstall it on your iPhone.

The application now uses the new startup screen as it loads.

> **Note:** You can create any art you'd like for the Default.png file, as long
> as it is the correct dimensions (320 by 480 pixels). However, it is often best
> to have the Default.png image match the initial state of your application.
