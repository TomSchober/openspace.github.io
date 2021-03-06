---
title: Releases
layout: default

parent: Home
nav_order: 1
---

# Releases {: .no_toc}
OpenSpace versions labeled by a version number of the form `MM.mm.rr`,  where `MM` is the major version number, `mm` is the minor version nuber, and `rr` is the release number (see [Semantic Versioning](https://semver.org)).  In some cases there may be an additional number at the end, `MM.mm.rr.bb`, where bb is the build number, but that will only be for development and testing, not for public release.

1. TOC
{:toc}

# Overview
As development procedes, some versions get tagged with names.  This table indicates which version numbers go with which tags, and some notes about each:

| Version | _Name_ | _Date_ | _Description_ |
| ------- | ------ | ------ | - |
| 0.15.1 | Beta-6 | 2020-02-17 | This is the sixth beta release for OpenSpace in conjunction with the 4th annual developer's meeting |
| 0.15.0 | Beta-5 | 2019-09-17 | This is the fifth beta release for OpenSpace released on September, 17th, 2019 for the ASTC conference |
| 0.14.1 | Beta-4 | 2019-06-04 | This is the first patch release for the fourth beta |
| 0.14.0 | Beta-4 | 2019-05-20 | This is the fourth beta release for OpenSpace released on the 20th of May, 2019 |
| 0.13.0 | Beta-3 | 2018-11-05 | This is the third beta release for OpenSpace released on the 5th of November, 2018 |
| 0.12.0 | Beta-2 | 2018-07-11 | This is the second beta release for OpenSpace released on the 11th July 2018 in the aftermath of IPS in Toulouse, France. |
| 0.11.1 | Beta-1 | 2018-02-13 | This is a patch release for the beta-1 version released on January 1st, 2018. It mainly fixes bugs and issues that have come up for users with the beta-1 release of OpenSpace. |
| 0.11.0 | Beta-1 | 2018-01-01 | This is the first beta release for OpenSpace released on January 1st, 2018. It contains all of the previously released features + new content and feature updates. |
| 0.10.0 | Prerelease-15 | 2017-10-24 | This prerelease is a collection of features that have been developed since the last public prerelease version for release at the Association of Science – Technology Centers (ASTC) conference. |
| 0.9.0 | Prerelease-14 | 2017-07-20 | This prerelease is a collection of features that have been developed since the last public prerelease version. |
| 0.4.0 | Prerelease-9 | 2016-07-11 | This pre-release version was prepared for a meeting at the AMNH of the ISI User Network. |
| 0.2.0 | Prerelease-7 | 2015-07-08 | This prerelease was published for a global, networked event in celebration of New Horizon’s closest approach to Pluto. |
| 0.1.0 | Prerelease-5 | 2015-05-14 | This prerelease was published for the Pluto-Palooza event held at the AMNH in New York. |

***

# Beta-6
 - Version: 0.15.1
 - Date: 2020-01-27
 - Finished: [9c34a55e50d7039c4408d2d0f8f9b0e73fc93bdc](https://github.com/OpenSpace/OpenSpace/commit/9c34a55e50d7039c4408d2d0f8f9b0e73fc93bdc)

## Changelog
### Features
 - Added a new rendering feature that uses the rings of saturn to create shadows onto Saturn and vice versa
 - Added a new rendering method for anti-aliased trails that improve their visual look at feel
 - Improve the handling of touch input on Windows systems that no longer requires started a separate TUIO server.  This also improves the handling of the touch input.
 - Improved the automatic generation of unique names for screen space renderables
 - Added a bookmarks file that will automatically create scene graph nodes to be able to focus on interesting locations
 - Added a new property that makes it possible to disable all mouse input
 
### API
 - Fixed retrieval of navigation state from the `openspace.navigation.getNavigationState` function and make this function usable again
 - Added a script that enables to directly add a layder from GIBS `openspace.globebrowsing.addGibsLayer`
 - Updated GLM version to 0.9.9.6
 - Replaced Google Test framework with Catch2
 - Added basic functionality for Tracy profiler
 - Added CMake options to build targeting an AVX, AVX2, or AVX512 processor architecture

### Content
 - Added ISS asset to the default scene
 - Added asset for C2019 Q4 "Borisov" interstellar object
 - Added a WMS server for the Venus Magellan dataset
 - Added alpha channel to Kaguya layer
 - Added an atmosphere to Venus
 - Added the ability to display procedurally generated text labels and added labels for planetary bodies in the solar system.  The default binding to toggle their visibility is `L`
 - Added the ability to fade satellite trails
 - Added a feature to render stars with a fixed color to make interoperability with Glue easier 
 - Fixes spelling of layer name for Sea Ice concentration
 - Fixed the milky way by using a static translation to offset it, rather than doing it in the shader code
 - Added missingSun marker in the Osiris-REx scene

### Content Creation
 - Added a new scene graph node type that renders a line between two scene graph nodes
 - Added a new scene graph node type that shows the distance between two scene graph nodes

### Bugfixes
 - Fixed a rendering error in which the stars would be cut between viewports when rendering OpenSpace using a fisheye configuration
 - Fixed a bug where the application would crash when changing the segments property
 - Fixed a bug that prevents the removal of globebrowsing layers
 - Fixed a bug that made the atmosphere disappear when night or water layers weren't active
 - Fixed a bug that would cause temporal tile layers to be out of sync by a day
 - No longer assume that the GuiName for a DashboardItem is provided
 - Fixed a bug with the Dawn scene
 - Fixed duplicate keybinds in the rosetta scene
 - Fixed issue with the Mercury magnetosphere 
 - Added a fix where it was not possible to use a group name in the `getProperty` Lua function
 - Fixed bug in which OpenSpace would crash when an asset includes itself
 - Fixed error when loading some Linux-generated speck files on Windows
 - Fixed an issue to make OpenSpace work on CentOS with an older curl version
 - Fix a bug where the debug mode would not work because the website URL was empty

### Optimizations
 - Tweaked the message pumping of CEF to improve the UI responsiveness on Windows
 - Improved the loading time of the galaxy dataset by caching the star points using a binary file format
 - Drastically improved the rendering speed of the milky way volume by adaptively downscaling the rendering resolution
 - Improved the rendering performance of the billboard clouds used for galaxy points

# Beta-5
 - Version: 0.15.0
 - Date: 2019-09-17
 - Finished: [c3b481f1e9b340cda49147ce8c7eb2f99fc98f53](https://github.com/OpenSpace/OpenSpace/commit/c3b481f1e9b340cda49147ce8c7eb2f99fc98f53)

## Changelog
### Features
 - Added a partially linearized rendering pipeline that enables support for High Dynamic Range objects. This feature also adds support for changing the exposure of the virtual camera, enable tweaking of saturation, hue, and brightness of the overall image
 - Added a new, preliminary, profile creator to easily select which assets are included and save these as `.scene` files
 - Added a preliminary feature to perform offline rendering, which has to be enabled through the Lua interface as of now. When calling
`openspace.sessionRecording.enableTakeScreenShotDuringPlayback(framerate)`, the next playback of a session recording will create a PNG file for each frame while playing back the session recording at the selected framerate
 - Added a new feature that enables the control of the camera through a WebSocket API.
 - Added a new rendering method that enables a more efficient rendering of satellite trails
 - Added the ability for the user to specify the location of the temporary folder, which now defaults to the OpenSpace/temp folder, rather than a global operating system specific folder that is used between multiple applications

### UI Improvements
 - Added a new user interface to add online screen space images
 - Added support for multiple endpoints in the WebGUI
 - Allow the user to abort the loading screen through the ESC key

### API
 - Replaced old setCameraState with new function setNavigationState that works more consistently when in orbit around a planet
 - Added support for arrays in LuaScript topics
 - Exposed the GlobeTranslation properties correctly

### Content
 - Added a volumetric representation of the milky way
 - Added asset for the Apollo 11 descent
 - Added asset for the Swift-Tuttle comet
 - Added asset files for the Tesla roadster and Oumuamua interstellar objects
 - Fixed issue where the wrong identifier was used for requested the model data for Vesta
 - Add option to show information about the current frame and synchronization status in a HUD rendering
 - Added documentation and verification for the creation of globe browsing layers to detect missing or wrong keys
 - Added a new default configuration that contains a Fisheye rendering window and a GUI window
 - Removed the F4 performance measurement keys from the `base.asset`.  The performance window is still available through the old UI (F1)

### Content Creation
 - Added a new TimelineTranslation that interpolates between different Translations based on the in-game time
 - Added a new TimelineRotation that interpolates between different Rotations based on the in-game time

### Bugfixes
 - Fixed a bug where a joystick/gamepad would become unresponsive when changing the sensitivity
 - Fixed issue where the DashboardItem displaying the location on a globe would display negative altitudes correctly
 - Improved issues with the usability of the touchbar on MacBooks
 - Fix issue with uint32-limited tilecache size in bytes restricting larger caches
 - Fixed problem with zoom restrictions at min/max zoom levels when using the touch interface
 - Added fix to prevent starting a session recording/playback if another is already in progress.
 - Fixed problem where the atmosphere stereo separation was not correctly computed
 - Added a check to prevent sync buffer overflows when sending enormous Lua scripts >4KiB
 - Fixed a scaling issue with the screen space images
 - Fixed crash when requesting a local screen space image whose file did not exist
 - Fixed an issue where the download size of files >2GiB was not displayed correctly
 - Fixed an issue that prevented the WebGUI from starting on MacOS
 - Fixed an issue where the camera would jump a small bit when refocussing close to a planetary surface
 - Fixed a crash that would occur when trying to read two-line element files whose file on disk would not exist
 - Fixed an issue that would prevent runtime removal of more than one asset file
 - Fixed an issue where the wireframe sphere would not be rendered correctly when an uneven number of vertices was selected
 - Fixed an issue with the commandline parsing that would cause the application to hang indefinitely
 - Fixed an issue where the normal in camera space was not set for local globe browsing patches
 - Fixed a problem where the ephemeris information of Pluto expired on 2019-03-01
 - Fixed a problem in which the PerformanceManager would crash when enabled by the user

### Optimizations
 - Replaced Multisampling Antialiasing (MSAA) for a faster Fast Approximate Antialiasing (FXAA) which improves performance and reduced the graphics memory footprint of the application
 - Drastically improved the performance and timing consistency of the Globebrowsing image loading
 - Used the more optimal `setPropertyValueSingle` instead of `setPropertyValue` Lua function in the `propertyHelper.invert` functions, which no longer causes unnecessary RegExp to be compiled
 
# Beta-4 (Patch 1)
 - Version: 0.14.1
 - Date: 2019-06-04
 - Finished: [0a68b06823a0f4809150db5f649ac923560afc52](https://github.com/OpenSpace/OpenSpace/commit/0a68b06823a0f4809150db5f649ac923560afc52)

## Changelog
### Features
 - Turn fade-in value into a property and move away from dedicated fadeIn, fadeOut methods
 - Consolidated all documentation files into a single file

### Content
 - Add multiple CMB spheres to show multiverses
 - Added optional keybinds CTRL+I, CTRL+K, CTRL+O, and CTRL+L for situations where the keypad is not available
 - Added optional F12 keybind to create a screenshot if the PRINT_SCREEN button is not available
 - Added apollo 11 CSM orbits and mock LEM decent to the apollo_sites scene
 - Warn if keybinds are defined twice
 - Updated Apollo sites to new LEM model based on photogrammetry
 - Updated fixed Pioneer model
 - Updated the rosetta images to only download a single zip file that gets extracted

### Bugfixes
 - Add Shift+A keybind for New Horizons scene to set the Aim+Anchor method, restoring the A keybind to the previous usage
 - Read DefaultAccess parameter from the configuration file correctly
 - Fixed bug where the field-of-view settings on dome image generators would be broken
 - Fix a warning if interpolating a value using the setPropertyValueSingle Lua method
 - Various fixes in the New Horizons scene to make it operable
 - Various fixes for the Rosetta scene
 - Fixed keyboard shortcurts in OsirisRex scene
 - Rebound the Philae trail visibility from F to G so that it is not on the same key as the friction
 - Disable the Rosetta image plane on default
 - Automatically remove old delta time keybindings when new ones are set in order to prevent double-binding
 - Cleanup of Apollo scene shortcuts
 - Fixing Apollo 8 and flipbook shortcuts
 - Updated number of samples for configs to make gui work on MacOS
 - Fixed bug where the UI would not show up if the computer is not connected to the internet

# Beta-4
 - Version: 0.14.0
 - Date: 2019-05-20
 - Finished: [cdeaae5068444f09129c703c40c9733a7d47e7d1](https://github.com/OpenSpace/OpenSpace/commit/cdeaae5068444f09129c703c40c9733a7d47e7d1)

## Changelog
### Breaking changes
 - Renamed property owner identifier from renderable to Renderable.  For instance, the property `Scene.EarthTrail.renderable.Enabled` is now called `Scene.EarthTrail.Renderable.Enabled`, and likewise for all other items in the scene graph

### Features
 - Added session recording feature
> This feature enables the recording of camera movements and user interface interactions.  When playing a recording back later, all camera movements and state changes are occurring at the same times when they did during the initial recording.  The recording will start at the same in-game time and speed in which OpenSpace was when the recording was done.  Recordings can be shared between computers as long as they are played back on the same scene or otherwise strange behavior might occur.  There is a user interface to control the recording and there are Lua scripts available to start and stop the recording and playback `openspace.sessionRecording.startPlayback()`, `openspace.sessionRecording.stopPlayback()`, `openspace.sessionRecording.startRecording(<filename>)`, `openspace.sessionRecording.stopRecording()`, and others
 - Added support for the new web-based user interface based on Chromium Embedded Framework for MacOS
 - Added a new rendering methods for rendering star catalogues that improves the visual quality and provides future support for point-spread function based rendering methods.  Additionally, it adds the capability to inspect other data values that are available in SPECK files and map these to colors
 - Added an Anchor&Aim feature that enhances the previous Focus Node concept.  While it is still possible to focus the camera on a single object as before and have all camera movements occur relative to that object, it is not possible to aim at a second object which then stays fixed on the screen
 - Added the ability to change the field of view for the main rendering window at run-time.  Please be aware that this feature might have unintended consequences if multiple rendering windows with different field of views are shown on the same computer
 - Added an indicator showing the number of enabled layers for a globe and prevent the user from enabling too many layers simultaneously.  If too many layers are enabled, the last layer will be automatically disabled
 - Added the ability to rescale Web UI during run-time
 - Added the ability to position screen space objects in 3D space so that they are culled correctly.  Also added a more intuitive positioning method useful for flat screen displays as well as planetariums
 - Added a heuristic that sometimes filters out ESRI's "No data available yet" tiles and uses available lower resoltion tiles instead.  This does not seem to work in all cases, and when it does not work, the "No data available yet" tile will show up as before
 - Added the support for temporarily modifying mouse sensitivity when zooming.  The `Z` key will increase the mouse sensitivity while it is pressed down by a factor of 8, the `X` key will decrease the mouse sensitivity while it is pressed down by a factor of 2
 - Added shortcut to disable rendering on master node (Alt+R)
 - Introduced global and master rotation that modify the location of screen space items
 - Added a feature that will check for a new released version at program start and provide information to the user in the lower right part of the screen and it will also enter a line into the log file
 - Added more statistics for the dashboard framerate items showing the extremes, standard deviation, etc

### UI Improvements
  - Added a panel for controlling the new session recording feature
 > To record a playback feature, you enter a filename and hit the `Record` button.  If you want to edit the recording afterwards, enable the `Text file format`.  The recording is stored in the `recording` directory by default, which can be changed in the `openspace.cfg`.  To play back a recording either select it in the dropdown menu or enter the name of the recording file in the text file and press `Play`
- Easy access settings panel for Renderables.
> Each scene graph node in the `Scene` menu now has a wrench icon next to it which will cause a panel for that scene graph node to pop out and be separately available until it is closed by the user.  Additionally, the top of the `Scene` menu now always contains the settings for the current focus node.  If this element is popped out, it will dynamically update if the current focus node changes
- Quick Enable feature for Renderables and Globe layers.  All renderable objects and layers on globes now have a checkbox with which the object can be quickly enabled or disabled without needing to open the submenu
- Visual indicator for enabled globe layers.  If a globe layer is enabled, its text will be rendered in green;  if it is not enabled, the text is white
- Sorting of Elements.  All elements in the UI are now correctly sorted;  either by adhering to the GUI sorting as specified in an asset file, or sorting the planets by the their distance from the Sun
- Improved scene menu search to make it possible to better search for objects that contain multiple words
- Scene pane saves state between uses.  When closing the `Scene` menu, the state of the tree will now be saved and not be closed when the menu is brought up again
- Improved display of scene shortcuts.  The list of available shortcuts are not presented in a more cohesive way to make them easier to access
- Visual improvement of fonts rendering.

### API
 - Updated GDAL version to 2.4.1
 - Finding configuration file now starts from the `bin` folder and continues upwards, rather than the current working directory as before
 - Add `asset.filePath` to asset API which contains the full path to the currently evaluated asset, enabling more useful error messages
 - Added the ability to query the OpenSpace documentation via the networking API
 - Added the ability to pass arguments to Lua scripts via JSON through the networking API
 - Added the ability to transport return values from Lua scripts back to the networking API clients
 - Added the ability to remove scenegraph nodes based on regular expressions

### Content
 - Added a new WMS layer for Mars containing >500 local HiRISE patches, served by ESRI
 - Added a new scene showing the trajectory of Apollo 8, and adding many new features to the various Apollo landing sites
 - Added a new scene containing the Insight lander.  The scene contains a model of the lander, its trajectory during entry into the Marsian atmosphere and the eventual landing.  The model changes throughout the different phases of the landing by showing, for example, the separation of the heat shield and the deployment of the parachute
 - Added new feature to show planetary surface labels.  Every major object in the Solar System, except for Earth, now has planetary labels that can be shown interactively.  The labels are taken from the database of USGS
 - Added a scene showing the Gaia mission using a new and experimental multiscale renderer.  The dataset that is automatically synchronized at startup only contains a few million stars for which the radial velocity is available.
 - Added grids for showing light days, light months, light years, and more.  These grids can be used to show the increasing scale when leaving the solar system
 - Added the trails of the Pioneer 11 and 12 missions as they were leaving the solar system
 - Added new SPICE kernels to the Juno scene to complete its coverage
 - Added Apogee and Galah gaia subsets rendered with the new star rendering method, howing the metal abundances in a subset of stars close to the Sun
 - Small fixes to the Messenger scene
 - Added WMS layer for Enceladus, Titan, and Europa
 - Added a spherical grid representing the Oort cloud

### Content Creation
 - Introducing a new base asset/scene that should not be directly loaded, but that can serve as a base for all other scenes.  This scene sets up default keybindings, loads the common content of the solar system and the digital universe, loads the Web UI, and configures globe browsing customizations
 - Added the ability to create custom focus nodes on planetary surfaces from Lua that can serve as a focus node for specific surface positions, such as Mars HiRISE patches, landing locations on the Moon, and others
 - Added a new Translation lcass that uses longitude/latitude information to position an object on a globe
 - Added Lua function to query property identifiers
 - Added example assets for some components

### Bugfixes
 - Fixed issue in which scene graph transformations were applied in the wrong order leading to strange results
 - Fix for a bug where the resolution of the globe layers would decrease when enabling a layer on some graphic cards
 - Fixed an issue where the loading screen would not show percentages when downloading files
 - Fixed an issue where the time notifier in the UI is not updated if the scene is paused
 - Fix for a bug where temporal WMS datasets would not be cached correctly
 - Fix a bug where the `H` key would not correctly show the trails again after hiding them
 - Correctly sort scene items in the Web UI
 - Fixed issues preventing multiple properties from being set simultaneously from a Lua script
 - Fix for bug where the global black-out would not work correctly
 - Only show screenspace renderables on non-UI windows 
 
### Optimizations
 - Increased rendering speed of Web UI
 - Slightly improved the rendering speed of globerendering
 - Slightly improved the rendering speed of the stars


# Beta-3
 - Version: 0.13.0
 - Date: 2018-11-05
 - Finished: [8e93463c1aba03445804c10172c85be69cbc1cb3](https://github.com/OpenSpace/OpenSpace/commit/8e93463c1aba03445804c10172c85be69cbc1cb3)

## Changelog
### Features
  - New CEF-based user interface (currently only on Windows)
  - Added shortcuts menu to execute Lua scripts without needing to be bound to keyboard keys
  - Updated GDAL to 2.3.2
  - Show percentages and progress for sync downloads
  - Added abililty to interpolate time for smoother time jumping
  - Ability to filter scene graph objects based on time
  - Additional lighting options for model rendering
  - Render on-screen text informing the user of ongoing application shutdown
  - Added ability to disable the console key for kiosk mode
  - Improved the tracking of the touch interface and made it easier to open the menu in a touch environment
  - Enable Spout texture sharing on default on Windows
  - Added Lua functions to print cluster id
  - Added configuration file that supportes spherical mirror configuration

### Content
  - Add a default path (`OpenSpace/../OpenSpaceData`) to search for planetary patches
  - Add a proper radiosphere that grows in real time
  - Add Hyperion and Mimas to Saturn's major moons
  - Enable the ability to not load an asset on default and later load it at runtime
  - Added simple example for a slide deck state machine
  - Added new dashboard item that shows the camera's current velocity
  - Add a new scale that changes its value based on the current time, reference time, and speed
  - Add a rotation that provides a static rotation based on in-game time
  - Simplify specification of opacity for text labels
  - Converted all images from using pbm format to png format for better compatibility
  - Add non-SI units to the distance conversion

### Bugfixes
  - Fixed bug causing incorrect aspect ratio for manually specified window sizes
  - Fix bug preventing specification of easing functions for property setting
  - Fixed focus node creation for local surface patches
  - Workaround for MacOS Mojave 10.14 where the rendering would only show up after the window has been moved

### Optimizations
  - Major improvement of planetary rendering performance
  - Improvements of atmosphere rendering performance
  - Improved application startup time
  - Better reuse of shader objects to reduce memory footprint
  - Better reuse of textures to reduce memory footprint
  - Better reuse of vertex buffer objects for Digital Universe dataset to reduce memory footprint
  - Improved rendering times by reusing uniform locations

# Beta-2
  - Version: 0.12.0
  - Date: 2018-07-11
  - Finished: [c2b1a3fd42b107ed37a1d0006058ae9d2df4baaf](https://github.com/OpenSpace/OpenSpace/commit/c2b1a3fd42b107ed37a1d0006058ae9d2df4baaf)

## Changelog
### Features
  - A pre-build binary for MacOS is included in the download section of the webpage
  - Added support for using joysticks and gamepads as input devices. The `data/assets/util/default_joystick.asset` controls the handling of connected joysticks
  - Bittorrent-based file synchronization has been completely removed in favor of HTTP-based synchronization. This change will fix the majority of issues that users had while synchronizing data in a firewalled environment
  - The `default.scene` will now by default start at "yesterday"s date and show the as-of-yet incomplete VIIRS image for "today" if the user jumps to "today"
  - The startup and shutdown times of the application has been overall lowered
  - **Potentially breaking change:**  The layout of the central `openspace.cfg` has been changed and users must adapt their old, modified variants for this release.  Mitigation consists of removing the `return {` and single `}` at the top and bottom of the file respectively
  - Added a mechanism to pass commandline arguments to OpenSpace that modify the loaded `openspace.cfg` to enable the setting of start-up scenes, SGCT configuration files and others from the commandline for clustered environments
  - When `PRINT_SCREEN` is creating a screenshot, it is now placed in the `screenshots/{current date}/` folder, rather than the `bin` folder as it was before
  - The default horizontal field-of-view has been changed to 80 degrees, which can be overwritten in the `openspace.cfg` file by the user by modifying the `sgct.config.single` parameters as described in the `scripts/configuration_helper.lua` file
  - When running OpenSpace in a windowed setup, manually changing the size of the window will now automatically adapt the aspect ratio that is used for the rendering
  - Added an inituial ability to automatically create focus markers on planets based on available `.info` files by editing the `data/assets/customization/globebrowsing.asset` file and changing `CreateFocusNodes` to `true`
  - Added the ability to use a single-file HTTP-based synchronization from third party locations. Examples of this are in the `data/assets/examples/urlsynchronization.asset`
  - It is now possible to zoom by using the left mouse button and pressing the Alt key in addition to using the right mouse button to support MacOS touch pads
  - Made it possible to click on the friction markers in the image to toggle the individual friction modes in addition to using the `F`, `Shift+F`, and `Ctrl+F` keyboard shortcuts
    - The `Global Properties -> Dashboard` now has a single property that will toggle its visibililty on screen
  - **Potentially breaking change:** The names of properties in the scene tree is now simplified and users must adapt their custom scripts to add a `Scene.` prefix to properties that change attributes of objects in the scene graph.
  - Added support for stb_image-based texture reader on non-Windows platforms

### Content
  - Added asset for the Messenger mission
  - Added Pluto to the default scene
  - Added Scaling node to all planets

### Bugfixes
  - Make the minimum skirt length of globes depenent on its radius to support small globes, such as moons of Mars, Jupiter, and Saturn
  - Fix bug preventing Saturn's rings from rendering
  - Fix bug causing Kepler-based translation to use a wrong value for the semi-major axis

# Beta-1
  - Version: 0.11.1
  - Date: 2018-02-13
  - Finished: [a65eea61a1b8807ce3d69e9925e75f8e3dfb085d](https://github.com/OpenSpace/OpenSpace/commit/a65eea61a1b8807ce3d69e9925e75f8e3dfb085d)

## Changelog
 - Changed default timeout to WMS servers from 5 minutes to 3 seconds, fixing a timeout wait on startup
 - Fixed hanging torrent download issue
 - Bugfixes and performance improvement for atmosphere rendering
 - Stability fixes with regard to caching
 - Updated H2 regions to a new dataset
 - Added spherical grids to Digital Universe dataset
 - Improve the texture quality by using Linear Mipmapping on default
 - Automatically compute a reasonable aspect ratio for custom window sizes
 - Fix issue with commandline arguments not being parsed
 - Fixed rendering issue where the stars would not show up if they are the only Digital Universe object included in the scene
 

# Beta-1
  - Version: 0.11.0
  - Date: 2018-01-01
  - Finished: [6e969794638d7e4761180dc97ca01fb35f356e46](https://github.com/OpenSpace/OpenSpace/commit/6e969794638d7e4761180dc97ca01fb35f356e46) 

## Changelog
### Content
  - Enabled atmospheric scattering around planets
  - Added Digital universe datasets (https://www.amnh.org/our-research/hayden-planetarium/digital-universe)
  - Mars
    - Added WMS server for color map
    - Added WMS server for MOLA hillshade
    - Added Phobos and Deimos
  - Earth
    - Added new ERSI high resolution dataset
  - Added scene for Voyager 1 and Voyager 2
  - Added minor moons for Jupiter, Saturn, Neptune, Uranus

### Features
  - Rendering methods
    - Added ability to provide rendering to Spout clients (spout.zeal.co)
    - Added configuration file for Spout cube output for use in Worldviewer (https://www.elumenati.com/product/worldviewer/)
    - Added projection method for Spherical mirrors (paulbourke.net/dome)
  - User Interface
    - Added on-screen information about friction status
    - Added automatic fading of objects based on distance
    - Improved informational text telling the user that a shutdown is imminent
    - Added TUIO touch interface implementation (https://www.tuio.org)
    - Added MacBook touch bar items for opening GUI and focussing on objects
    - Improved tooltip handling
      - Only show tooltips after one second of hovering
      - Added ability to disable tooltips
    - Enabled the manual sorting of items in the user interface
    - Added simplified GUI mode and shifted GUI activation keys (F1 -> F3  and F2 is new simplified GUI)
  - Content
    - Improved the behavior of billboard sizes by limiting minimum/maximum size
    - Added Loadingscreen to appear while a scene is loading
    - Added implementation to allow scenes to load multithreaded
    - Added Rotation method that stays fixed to a specified body
    - Added transformation objects that evaluate Lua scripts for rapid prototyping
    - Enabled multiple directories for image sequences like New Horizons and Rosetta
  - Scenes
    - Changed data layout by splitting old data/scene folder into data/asset and sync folders, thus separating the scene specification and the downloaded data
    - Added ability to execute global initialization scripts
    - Moved VRT specification into separate customization asset
    - Cleanup of Earth, Moon, and Mars WMS configuration files
  - Other
    - Made OpenSpace an AppBundle on MacOS
    - Set default number of antialiasing samples to 4
    - Cleanup of logging behavior
    - Added GIT commit hash output in log

### Bugfixes
  - Changed the default length of Uranus to prevent SPICE errors that would case Uranus' trail to query positions before 1850
  - Fixed bug that prevented separate GUI window from working
  - Added support for multiple ImGUI contexts used for multiple windows
  - Prevent crash from happening when too many texture units are requested
  - Fix Rosetta scene and rendering on MacOS
  - First steps towards making OpenSpaceEngine resilient against missing SGCT configuration errors

### API
  - Added ability to query the current binding of keys
  - Added ability to change the range of the delta time slider
  - Added ability to specify exponents for all numeric sliders
  - Added function to unload Mission file
  - Renaming path tokens
    - `${BASE_PATH}` -> `${BASE}`
    - `${OPENSPACE_DATA}` -> `${DATA}`
    - New token `${WEB}`
  - Redesigned on-screen text information to be more flexible

# Prerelease 15 (ASTC) 
  - Version: 0.10.0
  - Date: 2017-10-24
  - Finished: [50fd93](https://github.com/OpenSpace/OpenSpace/commit/50fd9309ba9dc9e5d73bf4bde3b0d6014bb75287)