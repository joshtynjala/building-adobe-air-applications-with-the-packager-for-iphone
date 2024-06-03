# Obtaining and working with iPhone developer files

<div>

You need to obtain an iPhone developer certificate and provisioning profiles
from Apple. You also need to convert the certificate into a P12 certificate.

<div>

#### Install iTunes

You need iTunes to install your application on your iPhone. Also, you use iTunes
to determine the device ID of your iPhone. You will need to know the device ID
when applying for an iPhone developer certificate.

</div>

<div>

#### Apply for an iPhone developer certificate and create a provisioning profile

If you have not already done so, sign up to be a registered iPhone developer at
the Apple iPhone Dev Center site (<https://developer.apple.com/ios/>).

<div>

<div>

Note: You do _not_ need the iPhone SDK or XCode to develop AIR applications for
the iPhone. You do need to be a registered iPhone developer. And you need to
obtain a developer certificate and a provisioning profile.

</div>

</div>

1.  Log in to the iPhone Dev Center using your iPhone developer account ID.

2.  At the iPhone Dev Center, apply for (and purchase) an iPhone developer
    certificate.

    You will receive an e-mail message from Apple containing your iPhone
    Developer Program activation code.

3.  Return to the iPhone Dev Center. Follow the instructions on activating your
    developer program (and enter your activation code when prompted).

4.  When your activation code is accepted, go to the iPhone developer Program
    Portal section of the iPhone Dev Center.

5.  Create a certificate signing request file. You will use this file to obtain
    a iPhone Development Certificate. For instructions, see
    [Generating a certificate signing request](./generating-a-certificate-signing-request.md).

6.  In the next step, you will be asked to provide the Device ID (or Unique
    Device ID) for your iPhone. You can obtain the UDID from iTunes:

    1.  Connect your iPhone with a USB cable. Then, in iTunes, select the
        summary tab for the iPhone.

    2.  Once you have downloaded the provisioning profile from the iPhone
        developer center site, add it to iTunes.

    3.  Then click the Serial Number displayed. The UDID is now displayed. Click
        Command-C on Mac or Control-C on Windows to copy the UDID to the
        clipboard.

7.  Create and install a provisioning profile and an iPhone development
    certificate.

    Follow the instructions at the iPhone Dev Center. Look for instructions at
    the iPhone Developer Program Portal section. You may want to use the
    Development Provisioning Assistant to obtain your development certificate
    and create your provisioning profile.

    Ignore steps involving XCode. You do not need to use XCode to develop iPhone
    applications using Flash Professional CS5.

8.  In iTunes, select File \> Add To Library. Then select the provisioning
    profile file (which has mobileprovision as the filename extension). Then
    sync your iPhone with iTunes.

    This lets you test the application associated with this provisioning profile
    on your iPhone.

    To verify that a specific provisioning profile is added to iTunes, you can
    try to add it to the library. If iTunes asks for you to replace an existing
    provisioning profile, you can press the Cancel button. (The profile is
    already installed.) Also, you can check the provisioning profiles installed
    on your iPhone:

    1.  Open the Settings application on your iPhone.

    2.  Open the General category.

    3.  Tap Profiles. The Profiles page lists your installed provisioning
        profiles.

9.  If you have not done so, download the iPhone development certificate file (a
    .cer file).

    The Development Provisioning Assistant may have provided you with a link to
    download this file. You can also find the file at the Certificates section
    of the Provisioning Portal at the Apple iPhone Dev Center site
    (<https://developer.apple.com/ios/>).

10. Next, you will convert the iPhone developer certificate to a P12 file. For
    instructions, see
    [Converting a developer certificate into a P12 file](./converting-a-developer-certificate-into-a-p12-file.md).

You can now create a simple Hello World application. See
[Creating a Hello World iPhone application with Flash Professional CS5](../creating-a-hello-world-iphone-application-with-flash-professional-cs5/index.md).

</div>

</div>

<div>

<div>

</div>

</div>
