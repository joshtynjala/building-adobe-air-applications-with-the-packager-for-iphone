# Optimizing video performance

To optimize mobile video playback, ensure that there is little else going on in
your application while video is playing. This allows the video decoding and
rendering processes to use as much CPU as possible.

Have little or no ActionScript code running while the video plays. Try to avoid
running code that runs on a frequent interval timer or on the timeline.

Minimize the redrawing of non-video display objects. Especially avoid redrawing
display objects that intersect with the video area. This is true even if they
are hidden underneath the video. They will still be redrawn and use up
processing resources. For example, use simple shapes for the position indicator
and update the position indicator just a couple of times a second rather than on
every frame. Don't have the video controls overlapping the video area; put them
directly below. If you have a video buffering animation, don't hide it behind
the video when it is not in use; set it to invisible.
