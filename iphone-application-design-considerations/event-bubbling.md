# Event bubbling

<div>

For a deeply nested display object container, bubbling of events can be
expensive. Reduce this expense by handling the event completely in the target
object, then calling the `stopPropagation()` method of the event object. Calling
this method prevents the event from bubbling up. Calling this method also means
that parent objects do not receive the event.

Related gains can be realized by flattening the display object nesting, to avoid
long event chains.

Register for MouseEvent events instead of TouchEvent events when possible.
MouseEvent events use less processor overhead than TouchEvent events.

Set the `mouseEnabled` and `mouseChildren` properties to `false`, when possible.

</div>

<div>

<div>

</div>

</div>
