MockingDroid
============

MockingDroid is a VERY SMALL template app for interactive mockups on Android, for performing usability tests and getting a feeling of how well your UI ideas work out.
It works by presenting HTML files which are present in the assets folder (or alternatively, online), which can
be structured like ordinary HTML, including hyperlinks, stylesheets, images,...
Additionally, some file-naming conventions are defined to enable screen transitions on menu and search button presses.

You can view MockingDroid as a highly restricted web browser on UI-mockup-steroids.

Features
--------

 * You stay in full control of your mockups - use plain HTML.
 * Screen-resolution independent - scaling happens automatically via the WebView's zoom factor (as long as all pages are same width, have a look at Requirements).
 * All conventional hardware buttons work; Menu and search buttons work if files with the corresponding names are present (look below). Back-button support can be globally disabled, or globally enabled and selectively switched off per HTML file (look below).
 * Resuming the app after passivation works as expected, returning to the last viewed screen.

Requirements
------------

 * "start.html" must be present in the project's /assets folder - this is the first screen a user sees upon starting the app. 
Alternatively, you can customize the start page path in /res/values/settings.xml (online pages allowed).
 * The setting mockups_width in /res/values/settings.xml (default at 400px) should equal the width of all mockup pages (have a look at the sample pages, where image width is set to 400px via style.css).

Usage Instructions
------------------

 0. Get the Android SDK and Tools, or just try out with the demo app in Downloads.
 1. Clone source into a directory
 2. Copy your mockup's HTML structure into /assets (have a look at the sample files there), if you want to use local files.
 3. Adjust settings /res/values/settings.xml - set the standard page width of your mockups (usually the width of images, can also be a scaled size set in CSS), and the path to the starting page (local or online). Back-button support can globally be switched off by setting a number of <= 0, or enabled by providing a number >= 1. The filename-conventions (suffixes) for HTML files for menu and search screens can also be adjusted here.
 4. Run (tested only at API Level 8 [Android 2.2])

### Menu & Search Button usage:
 * For a HTML file to support a transition to a menu or search file, extra files have to exist:
	  * filename.menu.html and/or filename.search.html, which contain the screen with menu/search additions
	  * these suffixes can be configured in /res/values/settings.xml
 * If a menu or search screen file is not found (or no HTTP-OK is received from remote server), the button-press is simply ignored.

### Back Button usage:
 * The back button can be enabled or disabled globally (/res/values/settings.xml).
 * Pressing the back button on the first page (defined in /res/values/settings.xml) results currently in the termination of the app (as expected).
 * If globally enabled, back button support can be switched off per HTML file, by putting "nobackbutton" ANYWHERE in the file. E.g. using a hidden span with a class "nobackbutton" will be fine.
 * You can set the target of a back button press for the current HTML file by putting in a standard HTML element with CSS class "backbuttonadvice", containing a relative path to the other file.
	  * Example: A user pressing the back-button on 01-myscreen.html shall be directed to 00-somescreen.html. We do so by putting a span-element into 01-myscreen.html, having the class "backbuttonadvice". The inner content of the span-element is "00-somescreen.html".

Care to Contribute?
-------------------

Please fork this project! I'd also be happy to receive suggestions or pull requests.