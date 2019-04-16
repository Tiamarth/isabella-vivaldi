# Isabella for Vivaldi custom css
![vivaldi screenshot](https://i.imgur.com/ASoZP30.png)

## Features
- **improve interface animation transitions** By default Vivaldi's animations throughout its interface are pretty inconsistent, some elements just jerk awkwardly between states because they aren't animated at all. Isabella adds smooth transitions to several elements that previously had none.
- **buttons in the tab bar are arranged more consistently** By default, Vivaldi places the window buttons in the far top right of the window, but places all the other buttons in the header just above the address bar. Isabella repositions all the buttons at the top of the window so that they're all vertically centered.
- **force window border around content** Default Vivaldi doesn't have a window border unless you enable native window decorations in the settings, but this makes it occasionally difficult to differentiate the Vivaldi window from other applications when the page content is a similar color as background apps. Isabella forces a window border even when native window is disabled.
- **more clear tab hovered** When you're moving your mouse over the tabs in the tab bar, Isabella emphasizes the tab that's currently being hovered far more clearly than Vivaldi does by default. 
- **more visible tab stack indicators** Tab stack indicators are easier to see, the topmost tab in a tab stack is easier to distinguish from the others. This is done without requiring more space for the indicators.
- **no top gradient** By default, Vivaldi draws a gradient behind the tabs if various criteria are met by the currently applied theme. In particular if the accent is dark and applied to the window. Isabella removes the gradient.
- **completely adaptable** Don't like the colours Isabella uses? Simply don't use them! If you just want the interface improvements, the css will adapt smoothly into any theme you apply in Vivaldi's settings.
- **make Vivaldi respect your system theme** Isabella integrates with the Isabella gtk theme, or with Adwaita, by forcing Vivaldi to use those window buttons instead.
- **no addressfield overlay** Default Vivaldi contains an element in the addressfield (where the url goes) that overlays everything in the input area. This results in an inconsistent color display in the addressfield, as the overlay is an entirely different color and just slightly transparent. Isabella removes the overlay entirely, so that the color isn't changed.
- **more frequent use of highlight** Default Vivaldi barely uses your highlight color. Isabella uses it in various more places, especially on buttons and links.

## Installation
Download the [latest vivaldi zip](https://github.com/Tiamarth/Isabella/releases/download/04%2F14%2F19/vivaldi.zip) from the [releases tab](https://github.com/Tiamarth/Isabella/releases/) of the repo, and put `isabella.css`, `isabella-window-buttons.css` and the "isabella" folder in `resources/vivaldi/style` in your Vivaldi install directory, then edit the `<head>` of `resources/vivaldi/browser.html` with a reference to `isabella.css`.

The window button css should be loaded automatically if it exists, so if you want the interface modifications except for the window buttons, just don't use either of the button css files. Or if you just want the window buttons and not the rest of the interface modifications, *only* use the button css you want, and reference it instead of `isabella.css` in `browser.html`.

The `<head>` of `browser.html` should look like this after you're done:

```html
  <head>
    <meta charset="UTF-8" />
    <title>Vivaldi</title>
    <link rel="stylesheet" href="style/common.css" />
    <link rel="stylesheet" href="style/isabella.css" />
  </head>
```

Or, if you're on Linux using the standard install path for Vivaldi, you can just use these commands:

**Vivaldi Stable**
```bash
git clone https://github.com/Tiamarth/Isabella.git && cd Isabella/vivaldi
mv isabella.css /opt/vivaldi/resources/vivaldi/style/
mv window-buttons/isabella-buttons.css /opt/vivaldi/resources/vivaldi/style/
mv window-buttons/isabella-buttons /opt/vivaldi/resources/vivaldi/style/
sed -i 's/  <\/head>/    <link rel="stylesheet" href="style\/isabella.css" \/>\n  <\/head>/' "/opt/vivaldi/resources/vivaldi/browser.html"
```
**Vivaldi Snapshot**
```bash
git clone https://github.com/Tiamarth/Isabella.git && cd Isabella/vivaldi
mv isabella.css /opt/vivaldi-snapshot/resources/vivaldi/style/
mv window-buttons/isabella-buttons.css /opt/vivaldi-snapshot/resources/vivaldi/style/
mv window-buttons/isabella-buttons /opt/vivaldi-snapshot/resources/vivaldi/style/
sed -i 's/  <\/head>/\n<link rel="stylesheet" href="style\/isabella.css" \/>\n  <\/head>/' "/opt/vivaldi-snapshot/resources/vivaldi/browser.html"
```

Note that these commands will clone the whole repo onto your system, including the [gtk and gnome-shell theme](https://github.com/Tiamarth/Isabella/tree/master/sublime) and the [Sublime Text color scheme.](https://github.com/Tiamarth/Isabella/tree/master/sublime)

Also, you can use the Adwaita window buttons instead if you copy the `adwaita-buttons` folder and `adwaita-buttons.css` instead of the Isabella buttons.

### Todo
&#9744; sidebar  
&#9744; scrollbars  
&#9744; status bar  
&#9744; side and bottom tabs  
&#9744; settings menu  
&#9744; more animations  

### Known issues
- the internal siteinfo button in the addressfield is transitioned inconsistently with the rest of the interface
