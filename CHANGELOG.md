9/12/2021 - 1.0b4

* Bugfix: 1.0b3 introduced some regressions and failed to actually fix switching key elevations when a linked token was deleted. Refactored elevation object getting throughout library to properly filter deleted tokens.
* Improvement: Switch to Token (Token ↑↓) overlay button no longer shows when no token is selected or no elevations are defined.
* Tweak: Correct some id HTML attribtues in loadOverlay
* Tweak: Corrected non-breaking errors in switchElevation method

9/11/2021 - 1.0b3

* New Feature: New 'Only Follow Players" option allows you to prevent the map from switching to a new elevation when moving non-owned tokens up or down. This is good for moving NPCs without having to reload the map. Note that tokens owned by the GM or by All also count to automatically switch the elevation.
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
