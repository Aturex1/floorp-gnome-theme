<img src="icon.svg" alt="Floorp GNOME theme" width="128" align="left"/>

# Floorp GNOME theme

[![GitHub](https://img.shields.io/github/license/rafaelmardojai/firefox-gnome-theme.svg)](https://github.com/rafaelmardojai/firefox-gnome-theme/blob/master/LICENSE)
[![Donate](https://img.shields.io/badge/PayPal-Donate-gray.svg?style=flat&logo=paypal&colorA=0071bb&logoColor=fff)](https://paypal.me/RafaelMardojaiCM)
[![Liberapay](https://img.shields.io/liberapay/receives/rafaelmardojai.svg?logo=liberapay)](https://liberapay.com/rafaelmardojai/donate)

<br>

**A GNOME theme for Floorp**

This theme follows latest GNOME Adwaita style.

### Disclaimer:

**Only the auto install script and flatpak installations are supported!!**
**The curl installation is currently not working!**

> ### Disclaimer:
> Be aware that this theme might do things that are not supported by upstream Floorp. If you face an issue while using this theme, report it here first or test if it is reproducible in vanilla Floorp.
>
> If you are a software distribution maintainer, please do not ship this changes by default to your users unless you made extremely clear that they are using a modified version of Floorp UI.

![Screenshot of the theme](screenshot.png)

## Description

This is a bunch of CSS code to make Floorp look closer to GNOME's native apps.

### Getting in Touch

Matrix room: [#firefox-gnome-theme:matrix.org](https://matrix.to/#/#firefox-gnome-theme:matrix.org)

### Firefox versions support

The `master` branch of this repo supports the current Firefox stable release `121`.

Theme versions compatible with older Firefox releases are preserved as git tags.

We also have the `beta` and `nightly` branches for fixes only applicable to the current Firefox beta and nightly versions.

## One command install with curl

To install this theme, you can run this command, which uses *curl* to download a script that will also download the latest released version of the theme (not the master version) and run the **auto-install** script for you.

> **Warning**: Always be careful when running scripts from the Internet.

# **This won't work**

```sh
curl -s -o- https://raw.githubusercontent.com/Aturex1/floorp-gnome-theme/master/scripts/install-by-curl.sh | bash
```

## Installation scripts

If you want to use other version of the theme than the stable one you can manually download the theme and run its install scripts.

First you need to grab a fresh copy of the theme repository by cloning it with git.

1. Clone this repo and enter folder:

	```sh
	git clone https://github.com/Aturex1/floorp-gnome-theme.git
	cd floorp-gnome-theme
	```
2. Checkout a git branch or tag if needed, otherwise use `master` and ignore this step.
	```sh
	git checkout beta # Set beta branch
	git checkout v78.1 # Set v78.1 tag
	```

This theme provides two installation scripts in addition to the curled one.

### Auto install script

This script will only look for Floorp profiles from Flatpak and install the theme in that. 
It will also enable a color variant for your GTK theme if it exists.

You can execute it by running:

```sh
./scripts/auto-install.sh
```

## Required Floorp preferences
We provide a **user.js** configuration file in `configuration/user.js` that enable some preferences required by this theme to work.

You should already have this file installed if you followed one of the installation methods, but in any case be sure this preferences are enabled under `about:config`:

- `toolkit.legacyUserProfileCustomizations.stylesheets`

	This preference is required to load the custom CSS in Floorp, otherwise the theme wouldn't work.

- `svg.context-properties.content.enabled`

	This preference is required to recolor the icons, otherwise you will get black icons everywhere.

> For other non essential preferences checkout `configuration/user.js`.

## Updating

You can follow the installation script steps again to update the theme.

## Uninstalling
1. Go to your profile folder. (Go to `about:support` in Floorp > Application Basics > Profile Directory > Open Directory)
2. Remove `chrome` folder.
3. Remove the unwanted preferences from your `user.js` inside your profile folder. The install script append the needed prefs in that file, you can check what preferences does it append by checking `configuration/user.js` in this repo.

## Enabling optional features
Optional features can be enabled by creating new `boolean` preferences in `about:config`.

1. Go to the `about:config` page
2. Type the key of the feature you want to enable
3. Set it as a `boolean` and click on the add button
4. Restart Floorp

### Features

- **Hide single tab** `gnomeTheme.hideSingleTab`

	Hide the tab bar when only one tab is open.

	> **Note:** You should move the new tab button out of the tabbar or it will be hidden when there is only one tab. You can rearrange the toolbars doing a right-click on any toolbar and selecting "Customize Toolbar…".

	> **Note 2:** This feature doesn't work when tabs are hidden, like when using the Simple Tab Groups extension. In this case, there's no way to tell from CSS that there's only one visible tab.

- **Normal width tabs** `gnomeTheme.normalWidthTabs`

	Use normal width tabs as default Floorp.

- **Swap tab close button position** `gnomeTheme.swapTabClose`

	By default the tab close buttons follows the position of the window controls, this preference reverts that behavior.

- **Bookmarks toolbar under tabs** `gnomeTheme.bookmarksToolbarUnderTabs`

	Move Bookmarks toolbar under tabs.

- **Active tab contrast** `gnomeTheme.activeTabContrast`

	Add more contrast to the active tab.

- **Close only selected tabs** `gnomeTheme.closeOnlySelectedTabs`

	Show the close button on the selected tab only.

- **System icons** `gnomeTheme.systemIcons`

	Use system theme icons instead of Adwaita icons included by theme.

	> **Note:** This feature has a [known color bug](#icons-color-broken-with-system-icons).

- **Symbolic tab icons** `gnomeTheme.symbolicTabIcons`

	Make all tab icons look kinda like symbolic icons.

- **Hide WebRTC indicator** `gnomeTheme.hideWebrtcIndicator`

	Hide redundant WebRTC indicator since GNOME provides their own privacy icons in the top right.

- **Hide unified extensions button** `gnomeTheme.hideUnifiedExtensions`

	Hide unified extensions button from the navbar, you can also use `extensions.unifiedExtensions.enabled` instead, which is only going to work till Floorp 111.

- **Drag window from headerbar buttons** `gnomeTheme.dragWindowHeaderbarButtons`

	Allow dragging the window from headerbar buttons.

	> **Note:** This feature is BUGGED. It can activate the button with unpleasant behavior.

- **Tabs as headerbar** `gnomeTheme.tabsAsHeaderbar`

	Place the tabs on the top of the window, and use the tabs bar to hold the window controls, like Floorp's standard tab bar.
	
	> **Note:** Enabling with `gnomeTheme.hideSingleTab` will replace the single tab with a title bar.

### Extensions support

We also have optional features to enable support for some Floorp extensions.

> **Be aware that extensions support are maintained by the community, so requests to support new extensions are not allowed and the included ones could get broken until someone shows up to fix them.**

- **Tab center reborn support** `gnomeTheme.extensions.tabCenterReborn`

	Enable the vertical tab trough the extension : [Tab Center Reborn](https://addons.mozilla.org/en-US/firefox/addon/tabcenter-reborn/).

	> **Note:** You also need to copy the contents of the file `configuration/extensions/tab-center-reborn.css` into the settings page of Tabcenter-reborn..\
	> **Note2:** You can also maintain the vertical tab always open with `gnomeTheme.extensions.tabCenterReborn.alwaysOpen`
 	> **Note2:** You can disable animation by disabling animation into the extension and adding the flags `gnomeTheme.extensions.tabCenterReborn.animationDisabled`
	
## Known bugs

### CSD have sharp corners
See upstream [bug](https://bugzilla.mozilla.org/show_bug.cgi?id=1408360).

#### Wayland fix:
1. Go to the `about:config` page
2. Search for the `layers.acceleration.force-enabled` preference and set it to true.
3. Now restart Floorp, and it should look good!

#### X11 fix:
1. Go to the `about:config` page
2. Type `mozilla.widget.use-argb-visuals`
3. Set it as a `boolean` and click on the add button
4. Now restart Floorp, and it should look good!

### Icons color broken with System icons
Icons might appear black where they should be white on some systems. I have no idea why, but you can adjust them directly in the `system-icons.css` file, look for `--gnome-icons-hack-filter` & `--gnome-window-icons-hack-filter` vars and play with css filters.

## Development

If you wanna mess around the styles and change something, you might find these
things useful.

To use the Inspector to debug the UI, open the developer tools (F12) on any
page, go to options, check both of those:

- Enable browser chrome and add-on debugging toolboxes
- Enable remote debugging

Now you can close those tools and press Ctrl+Alt+Shift+I to Inspect the browser
UI.

Also you can inspect any GTK3 application, for example type this into a terminal
and it will run Epiphany with the GTK Inspector, so you can check the CSS styles
of its elements too.

```sh
GTK_DEBUG=interactive epiphany
```

Feel free to use any parts of my code to develop your own themes, I don't force
any specific license on your code.

## Credits
Developed by **[Rafael Mardojai CM](https://github.com/rafaelmardojai)** and [contributors](https://github.com/rafaelmardojai/firefox-gnome-theme/graphs/contributors). Based on **[Luna Kurame](https://github.com/lunakurame/firefox-gnome-theme)**'s original work.

## Donate
If you want to support development, consider donating via [PayPal](https://paypal.me/RafaelMardojaiCM). Also consider donating upstream, [Firefox](https://donate.mozilla.org/) & [GNOME](https://www.gnome.org/support-gnome/).
