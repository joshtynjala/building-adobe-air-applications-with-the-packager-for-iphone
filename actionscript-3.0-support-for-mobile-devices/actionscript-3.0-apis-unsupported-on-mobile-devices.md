# ActionScript 3.0 APIs unsupported on mobile devices

<div>

Some ActionScript 3.0 APIs that are not supported for applications running in
the mobile device profile (such as applications running on the iPhone).

When using the same ActionScript code to develop for multiple profiles (such as
desktop and mobile), use code to test if an API is supported. For example, the
NativeWindow class is not supported in iPhone applications. (iPhone applications
cannot use or create native windows.) To test if an application is running on a
profile that supports native windows (such as the desktop profile), check the
`NativeWindow.isSupported` property.

The following table lists APIs that are not supported in the mobile device
profile. It also lists properties you can check to determine when an application
is running on a platform that offers support for an API.

<div>

| API                                           | Test for support                             |
| --------------------------------------------- | -------------------------------------------- |
| Accessibility                                 | Capabilities.hasAccessibility                |
| Camera                                        | Camera.isSupported                           |
| DatagramSocket                                | DatagramSocket.isSupported                   |
| DNSResolver                                   | DNSResolver.isSupported                      |
| DockIcon                                      | NativeApplication.supportsDockIcon           |
| DRMManager                                    | DRMManager.isSupported                       |
| EncryptedLocalStore                           | EncryptedLocalStore.isSupported              |
| HTMLLoader                                    | HTMLLoader.isSupported                       |
| LocalConnection                               | LocalConnection.isSupported                  |
| Microphone                                    | Microphone.isSupported                       |
| NativeApplication.exit()                      | —                                            |
| NativeApplication.menu                        | NativeApplication.supportsMenu               |
| NativeApplication.isSetAsDefaultApplication() | NativeApplication.supportsDefaultApplication |
| NativeApplication.startAtLogin                | NativeApplication.supportsStartAtLogin       |
| NativeMenu                                    | NativeMenu.isSupported                       |
| NativeProcess                                 | NativeProcess.isSupported                    |
| NativeWindow                                  | NativeWindow.isSupported                     |
| NativeWindow.notifyUser()                     | NativeWindow.supportsNotification            |
| NetworkInfo                                   | NetworkInfo.isSupported                      |
| PDF support                                   | HTMLLoader.pdfCapability                     |
| PrintJob                                      | PrintJob.isSupported                         |
| SecureSocket                                  | SecureSocket.isSupported                     |
| ServerSocket                                  | ServerSocket.isSupported                     |
| Shader                                        | —                                            |
| ShaderFilter                                  | —                                            |
| StorageVolumeInfo                             | StorageVolumeInfo.isSupported                |
| XMLSignatureValidator                         | XMLSignatureValidator.isSupported            |

</div>

You cannot write HTML- and JavaScript-based AIR applications for the mobile
device profile.

Some ActionScript 3.0 classes are only partially supported:

<div>

#### File

iPhone applications only have access to the application directory and the
application storage directory. You can also call `File.createTempFile()` and
`File.createTempDirectory()`. Calling an operation to access another directory
(such as a FileStream read or write method) results in an IOError exception.

iPhone applications do not support native file browser dialog boxes, such as the
one provided by the `File.browseForOpen()` method.

</div>

<div>

#### Loader

In an iPhone application, you cannot use the `Loader.load()` method. However,
you cannot run any ActionScript code in SWF content loaded with the
`Loader.load()` method. However, you can use assets in the SWF file (such as
movie clips, images, fonts, and sounds in the library). You can also use the
`Loader.load()` method to load image files.

</div>

<div>

#### Video

Only Sorensen video and ON2 VP6 video are supported within an AIR application on
the iPhone.

You can use the `navigateToURL()` method to open an H.264 video outside the
application. As the `request` parameter, pass a URLRequest object with a URL
pointing to the video. The video launches in the video player of the iPhone.

</div>

<div>

#### Text fields

There are limitations for fonts and other settings of text fields on the iPhone.
See
[Fonts and text input](../iphone-application-design-considerations/fonts-and-text-input.md).

</div>

<div>

#### Unsupported APIs and debugging using ADL

Some AIR functionality that is not supported on the iPhone is still available
when testing an application using ADL (on the development computer). Be aware of
these differences when testing content using ADL.

This functionality includes the following video and audio codecs: Speex (audio),
H.264/AVC (video), and AAC (audio). These codecs are unavailable to AIR
applications running on the iPhone. However, they continue to function normally
on the desktop.

Accessibility and screen reader support works in ADL on Windows. However, these
APIs are not supported on the iPhone.

The RTMPE protocol works normally when used from ADL on the desktop. However a
NetConnection that attempts to connect using the RTMPE protocol do not succeed
on the iPhone.

The Loader class works without additional restrictions when content is executed
with ADL. However, when executing on the iPhone, attempts to load SWF content
that contains ActionScript byte code results in an error message.

Shader instances execute in ADL. However, on the iPhone pixel bender bytecode is
not interpreted and shaders have no graphical effect.

For more information, see
[Debugging an iPhone application](../compiling-and-debugging-iphone-applications/debugging-an-iphone-application.md).

</div>

</div>

<div>

<div>

</div>

</div>
