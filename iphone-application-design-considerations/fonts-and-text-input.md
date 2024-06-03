# Fonts and text input

For best appearance, use device fonts. For example, the following fonts are
device fonts on the iPhone:

- Serif: Times New Roman, Georgia, and \_serif

- Sans-serif: Helvetica, Arial, Verdana, Trebuchet, Tahoma, and \_sans

- Fixed-width: Courier New, Courier, and \_typewriter

Use fonts that are 14 pixels or larger.

Use device fonts for editable text fields. Device fonts in text fields also
render more quickly than embedded fonts.

Do not use underlined text for input text fields. Also, do not set the alignment
of the text field. Input text fields on the iPhone only support left alignment
(the default).

If you use TLF Text setting for a text field in Flash Professional CS5, turn off
runtime shared library in the default linkage in ActionScript 3.0 Settings.
Otherwise the application will not work on the iPhone because it would try to
use the runtime shared library SWF file:

1.  Select File \> Publish Settings.

2.  In the Publish Settings dialog box, click the Flash tab.

3.  Click the Script button the right of the Script (ActionScript 3.0) drop-down
    list.

4.  Click the Library Path tab.

5.  In the Default Linkage drop-down list, select Merged Into Code.

Consider implementing alternatives to using input text fields. For example, to
have the user enter a numerical value, you do not need a text field. You can
provide two buttons to increase or decrease the value.

Be aware of the space used by the virtual keyboard. When the virtual keyboard is
activated (for example when a user taps within a text field), the application
adjusts the position of the stage. The automatic repositioning ensures that the
selected input text field is visible:

- A text field at the top of the stage moves to the top of the visible stage
  area. (The visible stage area is smaller to accommodate the virtual keyboard.)

- A text field at the bottom of the stage stays at the bottom of the new stage
  area.

- A text field in another part of the stage is moved to the vertical center of
  the stage.

When the user clicks a text field to edit it (and the virtual keyboard is
displayed), the TextField object dispatches a `focusIn` event. You can add an
event listener for this event to reposition the text field.

A single-line text field includes a clear button (to the right of the text) when
the user edits the text. However, this clear button is not displayed if the text
field is too narrow.

After editing text in a single-line text field, the user dismisses the virtual
keyboard by tapping the Done key on the keyboard.

After editing text in a multi-line text field, the user dismisses the virtual
keyboard by tapping outside the text field. This removes focus from the text
field. Make sure that your design includes area outside the text field when the
virtual keyboard is displayed. If the text field is too large, no other area may
be visible.

Using some Flash Professional CS5 components can prevent you from removing focus
from a text field. These components are designed for use on desktop machines,
where this focus behavior is desirable. One such component is the TextArea
component. When it is in focus (and being edited), you cannot remove focus by
clicking another display object. Placing some other Flash Professional CS5
components onstage can also prevent the focus from changing from the text field
being edited.

Do not rely on keyboard events. For example, some SWF content designed for the
web uses the keyboard to let the user control the application. However, on the
iPhone, the virtual keyboard is only present when the user edits a text field.
An iPhone application only dispatches keyboard events when the virtual keyboard
is present.
