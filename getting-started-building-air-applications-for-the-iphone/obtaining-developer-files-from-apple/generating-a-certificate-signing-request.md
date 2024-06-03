# Generating a certificate signing request

<div>

To obtain a developer certificate, you generate a certificate signing request
file, which you submit at the Apple iPhone Dev Center site.

<div>

#### Generate a certificate signing request on Mac OS

On Mac OS, you can use the Keychain Access application to generate a code
signing request. The Keychain Access application is in the Utilities
subdirectory of the Applications directory. On the Keychain Access menu, select
Certificate Assistant \> Request a Certificate from a Certificate Authority.

1.  Open Keychain Access.

2.  On the Keychain Access menu, select Preferences.

3.  In the Preferences dialog box, click Certificates. Then set Online
    Certificate Status Protocol and Certificate Revocation List to Off. Close
    the dialog box.

4.  On the Keychain Access menu, select Certificate Assistant \> Request a
    Certificate from a Certificate Authority.

5.  Enter the e-mail address and name that matches your iPhone developer account
    ID. Do not enter a CA e-mail address. Select Request is Saved to Disk and
    then click the Continue button.

6.  Save the file (CertificateSigningRequest.certSigningRequest).

7.  Upload the CSR file to Apple at the
    [iPhone developer site](https://developer.apple.com/ios/). (See "Apply for
    an iPhone developer certificate and create a provisioning profile".)

</div>

<div>

#### Generate a certificate signing request on Windows

For Windows developers, it may be easiest to obtain the iPhone developer
certificate on a Mac computer. However, it is possible to obtain a certificate
on a Windows computer. First, you create a certificate signing request (a CSR
file) using OpenSSL:

<div>

1.  Install OpenSSL on your Windows computer. (Go to
    <https://wiki.openssl.org/index.php/Binaries>.)

    You may also need to install the Visual C++ 2008 Redistributable files,
    listed on the Open SSL download page. (You do _not_ need Visual C++
    installed on your computer.)

2.  Open a Windows command session, and CD to the OpenSSL bin directory (such as
    c:\OpenSSL\bin\\.

3.  Create the private key by entering the following in the command line:

        openssl genrsa -out mykey.key 2048

    Save this private key file. You will use it later.

    When using OpenSSL, do not ignore error messages. If OpenSSL generates an
    error message, it may still output files. However, those files may not be
    usable. If you see errors, check your syntax and run the command again.

4.  Create the CSR file by entering the following in the command line:

        openssl req -new -key mykey.key -out CertificateSigningRequest.certSigningRequest  -subj "/emailAddress=yourAddress@example.com, CN=John Doe, C=US"

    Replace the e-mail address, CN (certificate name), and C (country) values
    with your own.

5.  Upload the CSR file to Apple at the
    [iPhone developer site](https://developer.apple.com/ios/). (See "Apply for
    an iPhone developer certificate and create a provisioning profile".)

</div>

</div>

</div>

<div>

<div>

</div>

</div>
