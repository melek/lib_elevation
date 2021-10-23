10/23/2021 - 1.0b6

* New Feature: New 'sightFilter' option allows you to constrain sight fading to some tokens. 
  * The default setting is '0' which fades sight for any token not on the current elevation.
  * Setting to '1' filters out tokens above the current elevation (e.g. flying tokens will always have sight).
  * Setting to '2' filters out tokens below the current elevation (e.g. ground-level tokens will always have sight).
* New Feature: New 'strictAppearance' options lets you choose whether to store complex information (rotation, size, and more) for elevation-linked tokens on the map. 
  * By default the setting is unchecked, and only the token's position will be explicitly stored. This default is a new option which greatly improves performance.
  * Checking this option will additionally store: layer, draw order, height, width, size, facing, opacity, visibility to players, shape, and layout. This setting will protect elevation-linked tokens from accidental changes when they are hidden off screen, such as by macros, and lets an elevation token appear differently when linked to different elevations.
* Improvement: Replaced all configuration getter functions and some others with JavaScript and laid groundwork under the hood to begin migrating Lib:Elevation towards a mainly JavaScript backend, which will greatly increase performance. You can now edit configuration values, such as which property represents "Elevation" in your campaign, in configuration.js.
* Improvement: Now deselects/reselects current selection when switching elevation, as selection and impersonation on the GM client for some reason greatly slows down elevation switching. Between this change, the new strictAppearance default, and new JavaScript functions, elevation switching times in have been cut in half. Impersonating a token on the GM client still slows down elevation, so GMs should avoid having a token impersonated when switching elevations.
* Bugfix: Check for external macro access before checking for updates and alert user if needed.
* Tweak: Removed bold text from Map Options input to work around Java's high DPI display issues.
* Tweak: Removed punctuation at end of Map Options dialog descriptions so they didn't double up with the inserted colon.

9/16/2021 - 1.0b5

* New Feature: Automatic Update Notifications have been added. On campaign load, the latest release from GitHub will be checked and if a new version has been added you will get an alert with a download link and the release notes you can read right in MapTool. Downloading and replacing the library is still a manual process.
* Bugfix: Properly respect 'useFogHack' option instead of always restoring fogs on elevation switch.
* Tweak: Re-implemented Fog Hack to be simpler and only reside on switchElevation.

9/12/2021 - 1.0b4

* Bugfix: 1.0b3 introduced some regressions and failed to actually fix switching key elevations when a linked token was deleted. Refactored elevation object getting throughout library to properly filter deleted tokens.
* Improvement: Switch to Token (Token ↑↓) overlay button no longer shows when no token is selected or no elevations are defined.
* Tweak: Correct some id HTML attributes in loadOverlay
* Tweak: Corrected non-breaking errors in switchElevation method

9/11/2021 - 1.0b3

* New Feature: New 'Only Follow Players' option allows you to prevent the map from switching to a new elevation when moving non-owned tokens up or down. This is good for moving NPCs without having to reload the map. Note that tokens owned by the GM or by All also count to automatically switch the elevation.
* Bugfix: Filter deleted tokens in getElevationTokens method to prevent error in calling functions. This fixes an error where deleting elevation tokens would prevent switching elevations on a map.
* Bugfix: Moving tokens to the current elevation now correctly refreshes the token states.
* Tweak: getElevationToken method now returns a JSON Array rather than a string list
* Tweak: Disabled elevation change buttons now show the current elevation instead of "At Top" or "At Bottom".

9/04/2021 - 1.0b2

* Bugfix: The elevation selector now works on MacOS (and hopefully Linux).
* Bugfix: Linking tokens to non-current elevations can no longer wipe out tokens on the destination key elevation.
* Improvement: Better organized the overlay buttons, added a disabled button state, and made sure all the elevation editing buttons were available even when no token was selected.
* Tweak: Ensured that both the 'step up' and 'step down' overlay buttons remain visible when a token is selected for consistent positioning. 
* Tweak: Fixed overlay 'step down' button tooltip text.
* Tweak: Relabeled 'Pck Tkn Elev' to 'Set Elevation'

8/27/2021 - 1.0b

* Initial beta release. Other changes are updates from 1.0a6
* Improvement: The library token itself now contains no campaign-specific data that needs to be preserved. 'getLibOption' and 'setLibOption' now grab the values from the map on which the library token resides. This means that there is no need to import any data at all when updating Lib:Elevation, you can simply delete the old token and drop in the updated one.
* Improvement: Map Option dialog is no longer tabbed, and specifies that you are editing default values when on the map containing the Lib:Elevation library token.
* Tweak: Clarify User Guide to specify that users never need to manually create a Map Elevation Data token ([#2](https://github.com/melek/lib_elevation/issues/2)).
* Tweak: Create new Map Elevation Data tokens on the Hidden layer instead of the Background layer ([Side effect of #2](https://github.com/melek/lib_elevation/issues/2)).
* Tweak: Removed some now obsolete functions: `setLibData`, `getLibData`, `setLibDataObj`, `getLibDataObj`, `deleteLibDataObj`
* Tweak: Refactored layer height logic to be more flexible.
* Tweak: The library version number is now additionally reflected in Lib:Elevation's GM Name field.
* Bugfix: Token fade (states/opacity for tokens on different elevations) no recalculates when adding an elevation. When map building, turning off Fog of War is advised to maintain clear vision of the map when adding elevations without having to first move a token to the elevation, then revealing vision ([#6](https://github.com/melek/lib_elevation/issues/6)).
