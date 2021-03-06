Changelog
====
## 0.0.7
### Improvements
* Upgrade to lit-element 0.6.5.
### Fixes
* Switch back from unpkg-gcp.firebaseapp.com to unpkg.com again because of CORS error.

## 0.0.6
### New features
* Unit is displayed in the center of the wheel.
* **BREAKING.** To switch views click the unit. The button has been removed.
* Arrow coloring now also in *energy view*. *)
* Power, energy and money values displayed next to all arrows. *)
* A third view: *money view* for displaying energy costs and savings. *)
  When you supply card parameter `energy_price` (in addition to the parameters needed for the *energy view*) the *money view* becomes available.

*) To make this feature possible the breaking changes as described below were needed.

### Improvements
* Rewrite: separating calculating values in the code.
* Value for home will be calculated always and not taken from evt. home sensors anymore.
* **BREAKING.** Card parameter `grid_power_entity` has been split into `grid_power_consumption_entity` and `grid_power_production_entity`.
  Both card parameters are required and should have positive values.
  The combined parameter `grid_power_entity` can still be used to supply the grid icon in the *power view*, but the power value isn't used anymore. 
* **BREAKING.** Card parameter `grid_energy_entity` has been split into `grid_energy_consumption_entity` and `grid_energy_production_entity`.
  Both card parameters are required if you want to use the *energy view* and should have positive values.
  The combined parameter `grid_energy_entity` can still be used to supply the grid icon in the *energy view*, but the energy value isn't used anymore. 

## 0.0.5
### Fixes
* Switch from unpkg.com to unpkg-gcp.firebaseapp.com for broken lit-html dependency.

## 0.0.4
### New features
* New optional card parameters `solor_energy_entity`, `grid_energy_entity` and `home_energy_entity` to feed the new *energy view* of the wheel.
If you want to use the *energy view* the first two are required.
The third one for *home energy* will be calculated if omitted.
* A button to toggle between *power view* and the new *energy view*. The button is visible only when the *energy view* is available.
* A card parameter `initial_view` to set the initial view to *power view* or *energy view*. Valid values are `"power"` (default) and `"energy"`. 
* A card parameter `energy_decimals` to set the number of decimals used in the *energy view*.
### Improvements
* Rewrite of the code.
* Preparations in the code for showing values near arrows in a future release.
* A slightly better positioning of the icons.
* **BREAKING.** Renamed card parameter `decimals` to `power_decimals`.
* **BREAKING.** Renamed card parameter `solar_power_icon` to `solar_icon`.
* **BREAKING.** Renamed card parameter `grid_power_icon` to `grid_icon`.
* **BREAKING.** Renamed card parameter `home_power_icon` to `home_icon`.
* **BREAKING.** Renamed card parameter `color_power_icons` to `color_icons`.

## 0.0.3
### New features
* Added `color_power_icons` as optional boolean card parameter to color the power icons or not (=default). Yellow for consuming, green for producing.
With the new optional card parameters `consuming_color` and `producing_color` you can choose your own colors.
* Click on the power icons to open the more-info modals of your sensors.
* Support for [custom_updater](https://github.com/custom-components/custom_updater) custom component.
### Improvements
* Performance. Moved some code to run it only after config changes.
* Better syntax for 'Example requirements configuration' in readme.
* Icon for home power can also be set via `customize:` sensor settings now.

## 0.0.2
### New features
* Added `solar_power_icon` and `grid_power_icon` as optional card parameters.
* Added `decimals` as optional card parameter to display the power values in this number of decimals.
* Added `home_power_entity` as optional card parameter in case you already have a sensor for it and want to use it,
instead of letting the card calculate the value of it. 

## 0.0.1
### New features
* Calculates the current power that your home is consuming: home power.
  Input for the calculation is the (produced) solar power and the (consumed or produced) grid power.
* Displays the three power values (solar, grid and home) in 'a wheel'.
* Displays the transition between these powers as arrows.
  E.g. if your solar power panels produce power, the arrow from solar to home turns active.
  And if your solar power panels produce enough power to deliver some back to the grid, the arrow from solar to grid turns active.
* Works for default theme and custom themes that use [standard CSS vars](https://github.com/home-assistant/home-assistant-polymer/blob/master/src/resources/ha-style.js).
