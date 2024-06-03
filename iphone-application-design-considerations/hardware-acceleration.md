# Hardware acceleration

You can use OpenGL ES 1.1 hardware acceleration to enhance graphics performance
in some applications. Games and other applications in which display objects are
animated can benefit from hardware acceleration. Applications that use hardware
acceleration can off-load some graphics processes to from the CPU to the iPhone
GPU, which can greatly improve performance.

When designing an application to use the GPU it is important to follow rules
that ensure the content is GPU-accelerated effectively.

To use the hardware acceleration, set the Rendering to GPU in the General tab of
the iPhone Settings dialog box in Flash Professional CS5. You can also set the
`renderMode` property to `gpu` in the application descriptor file:

    <initialWindow>
    <renderMode>gpu</renderMode>
    ...

See
[Setting iPhone application properties in Flash Professional CS5](../compiling-and-debugging-iphone-applications/iphone-application-settings/setting-iphone-application-properties-in-flash-professional-cs5.md)
and
[Setting iPhone application properties in the application descriptor file](../compiling-and-debugging-iphone-applications/iphone-application-settings/setting-iphone-application-properties-in-the-application-descriptor-file.md).

There are four classes of display objects that can render quickly in hardware
acceleration if their content changes infrequently:

- Bitmap objects

- 2D Display objects for which the `cacheAsBitmap` property is set to `true`,
  and optionally have their `cacheAsBitmapMatrix` property set (see below)

- 3D Display objects (i.e. have their `z` property set)

- Display objects that have a single solid-color rectangular fill and that have
  edges that align with the pixels on the screen.

Vector-based objects rerender whenever another sprite animates over or under
them. So, any object serving as a backdrop or foreground to an animation should
also belong to one of these categories.

For display objects that have `cacheAsBitmap` set to `true`, setting
`cacheAsBitmapMatrix` causes the GPU to use the bitmap that results from the
matrix transformation. The GPU uses the bitmap representation even if the object
is rotated or scaled. The GPU can composite and animate this bitmap much more
quickly than the CPU can redraw a vector-rendered object.

Setting `cacheAsBitmap` to `true` alone causes a display object (and any
children) to be cached. The display object is not redrawn when new regions are
exposed, or the whole combined graphic is translated.

When a display object's `cacheAsBitmapMatrix` property is set, the application
can build a representation of the display object even when it is not visible.
The application builds a cached representation of the display object at the
start of the next frame. Then when you add the display object to the stage, the
application renders it quickly. Also, the application can quickly animate rotate
or scale the object. For objects that rotate or scale, do not set the
`cacheAsBitmap` property without also setting the `cacheAsBitmapMatrix`
property.

The application can also quickly perform alpha transformations an object that is
cached as a bitmap. However only `alpha` values between 0 and 1.0 are supported
for hardware-accelerated alpha transformations. That corresponds to a
`colorTransform.alphaMultiplier` setting between 0 to 256.

Do not set the `cacheAsBitmap` property to `true` for frequently updated
objects, such as text fields.

Display objects that have frequently changing graphical content are generally
poor candidates for GPU rendering. This is especially true on earlier devices
with less powerful GPUs. The overhead of uploading the graphics to the GPU can
make CPU rendering a better choice.

Restructure display objects that contain child display objects that move
relative to the parent. Change them so that the child display objects become
siblings of the parent. This ensures they will each have their own bitmap
representation. Also, each display object will be able to move relative to the
others without any need for new graphics to be uploaded to the GPU.

Set the `cacheAsBitmap` property to `true` at the highest level of the display
list where child display objects do not animate. In other words, set it for
display object containers that contain no moving parts. Do not set it on the
child display objects. Do _not_ set it for sprites containing other display
objects that animate.

When you set the `z` property of a display object, the application always uses a
cached bitmap representation. Also, after you set the `z` property of a display
object, the application uses the cached bitmap representation, even if you
rotate or scale the object. The application does not use the
`cacheAsBitmapMatrix` property for display objects that have a set `z` property.
The same rules apply when you set any three-dimensional display object
properties, including the `rotationX`, `rotationY`, `rotationZ`, and
`transform.matrix3D` properties.

Do not set the `scrollRect` or `mask` property of a display object container
containing content for which you want to use hardware acceleration. Setting
these properties disables hardware acceleration for the display object container
and its child objects. As an alternative to setting the `mask` property, layer a
mask display object over the display object being masked.

There are limits to the size of display objects available for hardware
acceleration. On older devices, the limit is 1024 pixels or less in both width
and height. On newer devices, the limit is 2048 pixels or less. You can use the
GPU rendering diagnostic tool to test performance on a device.

The GPU also uses iPhone RAM to store bitmap images. It uses as least as much
memory as is needed for the bitmap images.

The GPU uses memory allocations that are powers of 2 for each dimension of the
bitmap image. For example, the GPU can reserve memory in 512 x 1024 or 8 x 32
sizes. So a 9 x 15-pixel image takes up the same amount of memory as a 16 x
16-pixel image. For cached display objects, you may want to use dimensions that
are close to powers of 2 (but not more) in each direction. For example, it is
more efficient to use a 32 x 16-pixel display object than a 33 x 17-pixel
display object.

Do not rely on a resized Stage to scale down assets that were sized for other
platforms (such as the desktop). Rather, use the `cacheAsBitmapMatrix` property,
or resize the assets before publishing for the iPhone. 3D objects ignore the
`cacheAsBitmapMatrix` property when caching a surface image. For this reason, it
is better to resize display objects before publishing if they will be rendered
on a 3D surface.

There is a trade-off between the benefits of hardware acceleration and RAM
usage. As memory fills up, iPhone OS notifies other running, native iPhone
applications to free up memory. As these applications process this notification
and work to free memory, they may compete with your application for CPU cycles.
This can momentarily degrade the performance of your application. Be sure to
test your application on older devices, as they may have substantially less
memory available for your running process.

When debugging the application on the iPhone, you can enable the GPU rendering
diagnostics feature. This feature aids you in seeing how your application uses
GPU rendering. For more information, see "Debugging with GPU rendering
diagnostics" in
[Debugging an iPhone application](../compiling-and-debugging-iphone-applications/debugging-an-iphone-application.md).

For information on using the `cacheAsBitmapMatrix` property, see the
"DisplayObject.cacheAsBitmapMatrix" section in
[ActionScript APIs specific to mobile AIR applications](../actionscript-3.0-support-for-mobile-devices/actionscript-apis-specific-to-mobile-air-applications.md).
