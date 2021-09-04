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
