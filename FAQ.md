# Tact FAQ

**Why does Tact not remember my window size, position, and sidebar size on macOS?**

This relies on macOS state restoration. This is controlled by the `Close windows when quitting an app` preference in Settings, General. Make sure that the checkbox is turned off: macOS window should then function as expected in terms of remembering size, position, and sidebar size.

**Why do I see an error “The application “iCloud” does not have permission to open “(null).” when trying to accept an invitation or request?**

This may happen on macOS when you have not moved Tact.app to /Applications. Please move Tact.app to /Applications and then it should work.

**My Tact installation is completely hosed. Something is very wrong with it and it doesn’t behave correctly. How do I get back into a good state?**

On iOS, just delete the app, and reinstall it from TestFlight.

On macOS:

* Make sure the app is not running.
* Open the folder `~/Library/Containers` and remove any folders with "Tact" in their name.
* Run this command in Terminal: `defaults delete com.justtact.Tact`
* Restart Tact.

After following these instructions on either platform, Tact downloads recent content again to this device, and is again usable. You can access earlier content in each chat with “Load more”.
