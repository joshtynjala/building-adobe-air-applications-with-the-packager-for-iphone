# Other ways to improve display object performance

Hardware acceleration can speed up graphics performance in some classes of
display objects Here are a few tips on how to maximize graphics performance:

- Try to limit the numbers of items visible on stage. Each item takes some time
  to render and composite with the other items around it.

  When you no longer need to display a display object, set its `visible`
  property to `false` or remove it from the stage ( `removeChild()`). Do not
  simply set its `alpha` property to 0.

- Avoid blend modes in general, and the layer blend mode in particular. Use the
  normal blend mode whenever possible.

- Display object filters are expensive computationally. Use them sparingly. For
  example, using a few filters on an introduction screen may be acceptable.
  However, avoid using filters on many objects or on objects that are being
  animated or when you must use a high frame rate.

- Avoid morph shapes.

- Avoid using clipping.

- If possible, set the `repeat` parameter to `false` when calling the
  `Graphic.beginBitmapFill()` method.

- Don't overdraw. Use the background color as a background. Don't layer large
  shapes on top of each other. There is a cost for every pixel that must be
  drawn. This is particularly true for display objects that are not hardware
  accelerated.

- Avoid shapes with long thin spikes, self intersecting edges, or lots of fine
  detail along the edges. These shapes take longer to render than display
  objects with smooth edges. This is particularly true for display objects that
  are not hardware accelerated.

- Make bitmaps in sizes that are close to, but less than, 2 <sup>n</sup> by 2
  <sup>m</sup> bits. The dimensions do not have to be power of 2, but they
  should be close to a power of 2, without being larger. For example, a
  31-by-15–pixel image renders faster than a 33-by-17–pixel image. (31 and 15
  are just less than powers of 2: 32 and 16.) Such images also use memory more
  efficiently.

- Limit the size of display objects to 1024 x 1024 pixels (or 2048 x 2048 on
  newer devices).
