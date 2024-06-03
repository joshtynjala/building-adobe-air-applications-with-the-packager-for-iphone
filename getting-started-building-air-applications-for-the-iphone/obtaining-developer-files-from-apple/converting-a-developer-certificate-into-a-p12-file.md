# Converting a developer certificate into a P12 file

<div>

To develop iPhone applications using Flash Professional CS5, you must use a P12
certificate file. You generate this certificate based on the Apple iPhone
developer certificate file you receive from Apple.

<div>

#### Convert the iPhone developer certificate to a P12 file on Mac OS

Once you have downloaded the Apple iPhone certificate from Apple, export it to
the P12 certificate format. To do this on Mac® OS:

1.  Open the Keychain Access application (in the Applications/Utilities folder).

2.  If you have not already added the certificate to Keychain, select File \>
    Import. Then navigate to the certificate file (the .cer file) you obtained
    from Apple.

3.  Select the Keys category in Keychain Access.

4.  Select the private key associated with your iPhone Development Certificate.

    The private key is identified by the iPhone Developer: \<First Name\> \<Last
    Name\> public certificate that is paired with it.

5.  Select File \> Export Items.

6.  Save your key in the Personal Information Exchange (.p12) file format.

7.  You will be prompted to create a password that is used when you attempt to
    import this key on another computer.

</div>

<div>

#### Convert an Apple developer certificate to a P12 file on Windows

To develop iPhone applications using Flash CS5, you must use a P12 certificate
file. You generate this certificate based on the Apple iPhone developer
certificate file you receive from Apple.

1.  Convert the developer certificate file you receive from Apple into a PEM
    certificate file. Run the following command-line statement from the OpenSSL
    bin directory:

        openssl x509 -in developer_identity.cer -inform DER -out developer_identity.pem -outform PEM

2.  If you are using the private key from the keychain on a Mac computer,
    convert it into a PEM key:

    <div>

        openssl pkcs12 -nocerts -in mykey.p12 -out mykey.pem

    </div>

3.  You can now generate a valid P12 file, based on the key and the PEM version
    of the iPhone developer certificate:

        openssl pkcs12 -export -inkey mykey.key -in developer_identity.pem -out iphone_dev.p12

    If you are using a key from the Mac OS keychain, use the PEM version you
    generated in the previous step. Otherwise, use the OpenSSL key you generated
    earlier (on Windows).

</div>

</div>

<div>

<div>

</div>

</div>
