# ActionScript APIs specific to mobile AIR applications

<div>

<div>

The following APIs are available only in AIR applications on mobile devices.
They are not currently functional in Flash Player or desktop versions of AIR.

</div>

<div>

#### Screen orientation API

The screen orientation API lets you work with the orientation of the stage and
the iPhone:

- `Stage.autoOrients` — Whether the application is set to have the stage
  automatically reorient when the device is rotated. This property is set to
  `true` when the Auto Orientation option is selected in the Flash Professional
  CS5 iPhone Settings dialog box. (You can also set the `autoOrients` element to
  `true` in the application descriptor file.) See
  [iPhone application settings](../compiling-and-debugging-iphone-applications/iphone-application-settings/index.md).
  You can cancel the automatic reorientation by adding an `orientationChanging`
  event listener for the Stage object. Calling the `preventDefault()` method of
  this event object cancels the automatic reorientation.

  When using auto-orientation, for best results set the `align` property of the
  Stage to the following:

      stage.align = StageAlign.TOP_LEFT;
      stage.scaleMode = StageScaleMode.NO_SCALE;

- `Stage.deviceOrientation` —The physical orientation of the device. The
  StageOrientation class defines values for this property.

- `Stage.orientation` —The current orientation of the stage. The
  StageOrientation class defines values for this property.

- `Stage.supportsOrientationChange` —Set to `true` on the iPhone, and `false` in
  an AIR application.

- `Stage.setOrientation()` —Sets the orientation of the stage. This method has
  one parameter, which is a string defining the new stage orientation. The
  constants in the StageOrientation class define possible values for the
  parameter.

- StageOrientation—Defines stage orientation values. For example,
  `StageOrientation.ROTATED_RIGHT` indicates a stage that is rotated right
  relative to the default orientation of the device.

- StageOrientationEvent—Defines events that the Stage dispatches when the
  orientation of the screen changes. This event occurs when the user rotates the
  iPhone. There are two types of events. The Stage dispatches the
  `orientationChanging` event as the device is being rotated. To prevent the
  stage from reorienting, call the `preventDefault()` method of the
  `orientationChanging` event object. The Stage dispatches the
  `orientationChange` event once the stage reorientation is complete.

Currently, the screen orientation API is only useful in AIR applications on
mobile devices. If a mobile AIR application and a desktop AIR application share
source code, use the `Stage.supportsOrientationChange` property to check if the
API is supported.

The following example shows how to respond to the user rotating the device:

    stage.addEventListener(StageOrientationEvent.ORIENTATION_CHANGE,
            onOrientationChange);

    function onOrientationChange(event:StageOrientationEvent):void
    {
        switch (event.afterOrientation) {
            case StageOrientation.DEFAULT:
                // re-orient display objects based on
                // the default (right-side up) orientation.
                break;
            case StageOrientation.ROTATED_RIGHT:
                // Re-orient display objects based on
                // right-hand orientation.
                break;
            case StageOrientation.ROTATED_LEFT:
                // Re-orient display objects based on
                // left-hand orientation.
                break;
            case StageOrientation.UPSIDE_DOWN:
                // Re-orient display objects based on
                // upside-down orientation.
                break;
        }
    }

In this example, in the case of different stage orientations, there are comments
instead of functional code.

You can change the orientation of the stage by calling the `setOrientation()`
method of the Stage object. Setting the orientation is an asynchronous
operation. You can check when the orientation is complete by listening for the
`orientationChange` event. The following code shows how to set the stage to the
right-hand orientation:

    stage.addEventListener(StageOrientationEvent.ORIENTATION_CHANGE,
            onOrientationChange);
    stage.setOrientation(StageOrientation.ROTATED_RIGHT);

    function onOrientationChange(event:StageOrientationEvent):void
    {
        // Code to handle the new Stage orientation
    }

As the Stage rotates it resizes, and the Stage object dispatches a `resize`
event. You can resize and reposition display objects on the Stage in response to
the `resize` event.

</div>

<div>

#### NativeApplication.systemIdleMode and SystemIdleMode

The `NativeApplication.systemIdleMode` property lets you prevent the iPhone from
going into idle mode. By default, an iPhone goes into idle mode if there is no
touch screen interaction for some period. Idle mode can cause the screen to dim.
It can also cause the iPhone to go into lock mode. This property can be set to
one of two values:

<div>

- `SystemIdleMode.NORMAL` —The iPhone follows the normal idle mode behavior.

- `SystemIdleMode.KEEP_AWAKE` —The application attempts to prevent the iPhone
  from going into idle mode.

</div>

This functionality is only supported on mobile devices. It is not supported in
AIR applications running on desktop operating systems. In an application running
on the desktop, setting the `NativeApplication.systemIdleMode` property has no
effect.

The following code shows how to disable the iPhone idle mode:

<div>

    NativeApplication.nativeApplication.systemIdleMode = SystemIdleMode.KEEP_AWAKE;

</div>

</div>

<div>

#### CameraRoll

The CameraRoll class lets you add an image to the iPhone camera roll. The
`addBitmapData()` method adds an image to the iPhone camera roll. The method has
one parameter, `bitmapData`. This parameter is the BitmapData object containing
the image to add to the camera roll.

CameraRoll functionality is only supported on mobile devices. It is not
supported in AIR applications running on desktop operating systems. To check at
runtime whether your application supports the CamerRoll functionality, check the
static `CameraRoll.supportsAddBitmapData` property.

After you call the `addBitmapData()` method, the CameraRoll object dispatches
one of two events:

<div>

- `complete` —The operation completed successfully.

- `error` —There was an error. For example, perhaps there is not enough free
  space on the iPhone to store the image.

</div>

The following code adds an image of the stage (a screen capture) to the camera
roll:

<div>

    if (CameraRoll.supportsAddBitmapData)
    {
        var cameraRoll:CameraRoll = new CameraRoll();
        cameraRoll.addEventListener(ErrorEvent.ERROR, onCrError);
        cameraRoll.addEventListener(Event.COMPLETE, onCrComplete);
        var bitmapData:BitmapData = new BitmapData(stage.stageWidth, stage.stageHeight);
        bitmapData.draw(stage);
        cameraRoll.addBitmapData(bitmapData);
    }
    else
    {
        trace("not supported.");
    }

    function onCrError(event:ErrorEvent):void
    {
        // Notify user.
    }

    function onCrComplete(event:Event):void
    {
        // Notify user.
    }

</div>

</div>

<div>

#### DisplayObject.cacheAsBitmapMatrix

The `cacheAsBitmapMatrix` property is a Matrix object that defines how a display
object is rendered when `cacheAsBitmap` is set to `true`. The application uses
this matrix as a transformation matrix when rendering the bitmap version of the
display object.

With `cacheAsBitmapMatrix` set, the application retains a cached bitmap image
rendered using that matrix, instead of the display matrix. (The display matrix
is the value of the `transform.concatenatedMatrix` of the display object.) If
this matrix does not match the display matrix, the bitmap is scaled and rotated
as necessary.

A display object with `cacheAsBitmapMatrix` set is only rerendered when the
value of `cacheAsBitmapMatrix` changes. The bitmap is scaled or rotated as
appropriate to conform to the display matrix.

Both CPU- and GPU-based rendering benefit from the use of the
`cacheAsBitmapMatrix` property, although GPU rendering typically benefits more.

<div>

Note: To use the hardware acceleration, set the Rendering to GPU in the General
tab of the iPhone Settings dialog box in Flash Professional CS5. (Or set the
`renderMode` property to `gpu` in the application descriptor file.)

</div>

For example, the following code uses an untransformed bitmap representation of
the display object:

<div>

    matrix:Matrix = new Matrix(); // creates an identity matrix
    mySprite.cacheAsBitmapMatrix = matrix;
    mySprite.cacheAsBitmap = true;

</div>

The following code uses a bitmap representation that matches the current
rendering:

<div>

    mySprite.cacheAsBitmapMatrix = mySprite.transform.concatenatedMatrix;
    mySprite.cacheAsBitmap = true;

</div>

Usually, the identity matrix ( `new Matrix()`) or `transform.concatenatedMatrix`
suffices. However, you can use another matrix, such as a scaled-down matrix, to
upload a different bitmap to the GPU. For example, the following example applies
a `cacheAsBitmapMatrix` matrix that is scaled by 0.5 on the x- and y-axes. The
bitmap object that the GPU uses is smaller, however the GPU adjusts its size to
match the `transform.matrix` property of the display object.:

<div>

    matrix:Matrix = new Matrix(); // creates an identity matrix
    matrix.scale(0.5, 0.5); // scales the matrix
    mySprite.cacheAsBitmapMatrix = matrix;
    mySprite.cacheAsBitmap = true;

</div>

Generally, choose a matrix that transforms the display object to the size that
it will appear in the application. For example, if your application displays the
bitmap version of the sprite scaled down by a half, use a matrix that scales
down by a half. If your application will display the sprite larger than its
current dimensions, use a matrix that scales up by that factor.

There is a practical limit to the size of display objects for which the
`cacheAsBitmapMatrix` property is set. The limit is 1020 by 1020 pixels. There
is a practical limit for the total number of pixels for all display objects for
which the `cacheAsBitmapMatrix` property is set. That limit is about four
million pixels.

There are many considerations when using `cacheAsBitmapMatrix` and hardware
acceleration. It is important to know which display objects should have that
property set, and which ones should not. For important information on using this
property, see
[Hardware acceleration](../iphone-application-design-considerations/hardware-acceleration.md).

You can use the GPU rendering diagnostics feature to diagnose GPU usage in debug
builds of your application. For more information, see
[Debugging an iPhone application](../compiling-and-debugging-iphone-applications/debugging-an-iphone-application.md).

</div>

<div>

#### Networking notes

Using the following URL schemes with the `nativigateToURL()` function causes a
document to open in an external application:

<div>

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>URL scheme</p></th>
<th><p>Result of call to nativeToURL()</p></th>
<th><p>Example</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>mailto:</p></td>
<td><p>Opens a new message in the mail application.</p></td>
<td><div>
<pre><code>str = &quot;mailto:test@example.com&quot;; 
var urlReq:URLReq = new URLRequest(str); 
navigateToURL(urlReq);</code></pre>
</div></td>
</tr>
<tr class="even">
<td><p>sms:</p></td>
<td><p>Opens a message in the text message application.</p></td>
<td><div>
<pre><code>str = &quot;sms:1-415-555-1212&quot;; 
var urlReq:URLReq = new URLRequest(str); 
navigateToURL(urlReq);</code></pre>
</div></td>
</tr>
<tr class="odd">
<td><p>tel:</p></td>
<td><p>Dials a phone number on the phone (with user approval).</p></td>
<td><div>
<pre><code>str = &quot;tel:1-415-555-1212&quot;; 
var urlReq:URLReq = new URLRequest(str); 
navigateToURL(urlReq);</code></pre>
</div></td>
</tr>
</tbody>
</table>

</div>

An iPhone application may rely on installed self-signed root certificates for
server authentication during a secure transaction, such as an https request. A
server should send not just the leaf certificate but also all intermediate
certificates chaining to the root certificate.

</div>

</div>

<div>

<div>

</div>

</div>
