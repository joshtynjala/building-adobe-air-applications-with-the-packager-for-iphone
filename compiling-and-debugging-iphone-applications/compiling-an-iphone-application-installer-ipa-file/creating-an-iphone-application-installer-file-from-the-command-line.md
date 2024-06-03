# Creating an iPhone application installer file from the command line

You can run the Packager for iPhone from the command line. The Packager for
iPhone converts the SWF file byte code and other source files into a native
iPhone application.

1.  Open a command shell or a terminal and navigate to the project folder of
    your iPhone application.

2.  Next, use the pfi tool to create the IPA file, using the following syntax:

        pfi -package -target [ipa-test ipa-debug ipa-app-store ipa-ad-hoc] -provisioning-profile PROFILE_PATH SIGNING_OPTIONS TARGET_IPA_FILE APP_DESCRIPTOR SOURCE_FILES

    Change the reference `pfi` to include the full path to the pfi application.
    The pfi application is installed in the pfi/bin subdirectory of the Flash
    Professional CS5 installation directory

    Select the `-target` option that corresponds to the type of iPhone
    application you want to create:

    - `-target ipa-test` —Choose this option to quickly compile a version of the
      application for testing on your developer iPhone.

    - `-target ipa-debug` —Choose this option to compile a debug version of the
      application for testing on your developer iPhone. With this option, you
      can use a debug session to receive `trace()` output from the iPhone
      application.

      You can include one of the following `-connect` options (
      `CONNECT_OPTIONS`) to specify the IP address of the development computer
      running the debugger:

      - `-connect` —The application will attempt to connect to a debug session
        on the development computer used to compile the application.

      - `-connect IP_ADDRESS` —The application will attempt to connect to a
        debug session on the computer with the specified IP address. For
        example:

            -target ipa-debug -connect 192.0.32.10

      - `-connect HOST_NAME` —The application will attempt to connect to a debug
        session on the computer with the specified host name. For example:

            -target ipa-debug -connect bobroberts-mac.example.com

        > **Note:** The `-connect` option is not included in the Packager for
        > iPhone Preview included Flash Professional CS5. Update the Packager
        > for iPhone by selecting Help \> Updates in Flash Professional CS5.

      The `-connect` option is optional. If not specified, the resulting debug
      application will not attempt to connect to a hosted debugger.

      If a debug connection attempts fail, the application presents a dialog
      asking the user to enter the IP address of the debugging host machine. A
      connection attempt can fail if the device is not connected to wifi. It can
      also occur if the device is connected but not behind the firewall of the
      debugging host machine.

      For more information, see
      [Debugging an iPhone application](../debugging-an-iphone-application.md).

      You can also include the `-renderingdiagnostics` option to enable the GPU
      rendering diagnostics feature. For more information, see "Debugging with
      GPU rendering diagnostics" in
      [Debugging an iPhone application](../debugging-an-iphone-application.md).

    - `-target ipa-ad-hoc` —Choose this option to create an application for ad
      hoc deployment. See the Apple iPhone developer center

    - `-target ipa-app-store` —Choose this option to create a final version of
      the IPA file for deployment to the Apple App Store.

      Replace the _`PROFILE_PATH`_ with the path to the provisioning profile
      file for your application. For more information on provisioning profiles,
      see
      [Obtaining developer files from Apple](../../getting-started-building-air-applications-for-the-iphone/obtaining-developer-files-from-apple/index.md).

      Replace the _`SIGNING_OPTIONS`_ to reference your iPhone developer
      certificate and password. Use the following syntax:

          -storetype pkcs12 -keystore P12_FILE_PATH -storepass PASSWORD

      Replace _P12_FILE_PATH_ with the path to your P12 certificate file.
      Replace _PASSWORD_ with the certificate password. (See the example below.)
      For more information on the P12 certificate file, see
      [Converting a developer certificate into a P12 file](../../getting-started-building-air-applications-for-the-iphone/obtaining-developer-files-from-apple/converting-a-developer-certificate-into-a-p12-file.md).

      Replace the _`APP_DESCRIPTOR`_ to reference the application descriptor
      file.

      Replace the _`SOURCE_FILES`_ to reference the main SWF file of your
      project followed by any other assets to include. Include the paths to all
      icon files you defined in the application settings dialog box in Flash CS5
      or in a custom application descriptor file. Also, add the initial screen
      art file, Default.png.

Consider the following example:

    pfi -package -target ipa-test -storetype pkcs12 -keystore "/Users/Jeff/iPhoneCerts/iPhoneDeveloper_Jeff.p12" -storepass dfb7VKL19 "HelloWorld.ipa" "HelloWorld-app.xml" "HelloWorld.swf" "Default.png" "icons/icon29.png" "icons/icon57.png" "icons/icon512.png"

It compiles a HelloWorld.ipa file using the following:

- A specific PKCS#12 certificate using the certificate password dfb7VKL19

- The HelloWorld-app.xml application descriptor file

- A source HelloWorld.swf file

- Specific Default.png and icon files

The pfi application compiles the application, based on the application
descriptor file, the SWF file, and the other assets, into an IPA file.

On Mac OS, you can use a certificate stored in the keychain by adding the
following options to the pfi command:

     -alias ALIAS_NAME -storetype KeychainStore -providerName Apple

Replace _ALIAS_NAME_ with the alias of the certificate you want to use. When you
point to a certificate stored in the Mac keychain, you do specify the alias
instead of pointing to a certificate file location.
