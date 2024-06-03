# Saving application state

Your application may quit at any time (for example when the phone rings).
Consider saving the state of your application anytime it changes. For example,
you can save settings to a file or a database in the application storage
directory. Or you can save data to a local shared object. You can then restore
the state of your application when it relaunches. If a phone call interrupts an
application, it will restart when the call ends.

Do not rely on the NativeApplication object dispatching an `exiting` event when
the application quits; it may not.
