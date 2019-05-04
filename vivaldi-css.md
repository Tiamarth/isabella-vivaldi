# Isabella for Vivaldi custom css
![screenshot](https://isabella-theme.github.io/assets/img/isabella-vivaldi/preview.png)

I'm writing this css to fix some issues I have with Vivaldi's default interface *and* to force it to integrate better with gtk apps, specifically using Epiphany as a reference. I'm not the only Vivaldi user who wants the ui to be more respectful of system themes and appearances, but I'm unaware of other projects to actually solve the issue. Vivaldi is one of only a few apps I have installed that seems utterly disinterested to integrate with my system, and it's the *only* web browser I know of that doesn't integrate.

Vivaldi's "enable native window" is *not* a solution.

## Features
- **buttons in the tab bar are arranged more consistently** By default, Vivaldi places the window buttons in the far top right of the window, but places all the other buttons in the header just above the address bar. Isabella repositions all the buttons at the top of the window so that they're all vertically centered. In the following screenshot, the top bar is default Vivaldi using the default "Dark" theme, and the bottom bar is Isabella using the "Isabella" theme.
![screenshot of "buttons in the tab bar are arranged more consistently"](https://isabella-theme.github.io/assets/img/isabella-vivaldi/buttons_tab_bar.png)
- **"metro" speed dial folders** Isabella makes the speed dial look more modern by disabling the default folder backgrounds and displaying only the thumbnails of the bookmarks contained in the folder.
![screenshot of "'metro' speed dial folders"](https://isabella-theme.github.io/assets/img/isabella-vivaldi/metro_speed_dial.png)
- **overlay find in page** Isabella makes the find in page not disrupt the flow of content by overlaying it over the page instead of shifting everything out of the way.
![gif of "overlay find in page"](https://github.com/isabella-theme/isabella-theme.github.io/blob/master/assets/img/isabella-vivaldi/find.gif)
- **force window border around content** Default Vivaldi doesn't have a window border unless you enable native window decorations in the settings, but this makes it occasionally difficult to differentiate the Vivaldi window from other applications when the page content is a similar color as background apps. Isabella forces a window border even when native window is disabled.
![screenshot of "force window border around content"](https://isabella-theme.github.io/assets/img/isabella-vivaldi/window_border.png)
- **more clear tab hovered** When you're moving your mouse over the tabs in the tab bar, Isabella emphasizes the tab that's currently being hovered far more clearly than Vivaldi does by default. 
![gif of "more clear tab hovered"](https://github.com/isabella-theme/isabella-theme.github.io/blob/master/assets/img/isabella-vivaldi/more_clear_tab_hovered.gif)
- **more visible tab stack indicators** Tab stack indicators are easier to see, the topmost tab in a tab stack is easier to distinguish from the others. This is done without requiring more space for the indicators.
![screenshot of "more visible tab stack indicators"](https://isabella-theme.github.io/assets/img/isabella-vivaldi/stack_indicators.png)
- **no top gradient** By default, Vivaldi draws a gradient behind the tabs if various criteria are met by the currently applied theme. In particular if the accent is dark and applied to the window. Admittedly, in most themes the gradient is very subtle and probably doesn't bother most users, but it did bother me so Isabella removes the gradient. In the following screenshot, the top bar is default Vivaldi using the default "Subtle" theme, and the bottom bar is Isabella using the default "Subtle" theme.
![screenshot of "no top gradient"](https://isabella-theme.github.io/assets/img/isabella-vivaldi/no_top_gradient.png)
- **completely adaptable** Don't like the colours Isabella uses? Simply don't use them! If you just want the interface improvements, the css will adapt smoothly into any theme you apply in Vivaldi's settings.
![gif of "completely adaptable"](https://github.com/isabella-theme/isabella-theme.github.io/blob/master/assets/img/isabella-vivaldi/adaptable.gif)
- **make Vivaldi respect your system theme** Isabella integrates with the Isabella gtk theme, or with Adwaita, by forcing Vivaldi to use those window buttons instead.
![screenshot of "make Vivaldi respect your system theme"](https://isabella-theme.github.io/assets/img/isabella-vivaldi/respect_theme.png)
- **no addressfield overlay** Default Vivaldi contains an element in the addressfield (where the url goes) that overlays everything in the input area. This results in an inconsistent color display in the addressfield, as the overlay is an entirely different color and just slightly transparent. Isabella removes the overlay entirely, so that the color isn't changed.
![screenshot of "no addressfield overlay"](https://isabella-theme.github.io/assets/img/isabella-vivaldi/addressfield_overlay.png)
- **improve interface animation transitions** By default Vivaldi's animations throughout its interface are pretty inconsistent, some elements just jerk awkwardly between states because they aren't animated at all. Isabella adds smooth transitions to several elements that previously had none.
- **more frequent use of highlight** Default Vivaldi barely uses your highlight color. Isabella uses it in various more places, especially on buttons, links, and input fields. This is intended to add more color to the interface and to mimic the behavior of of gtk apps, which also use the current theme's highlight color on focused input fields.

## Installation
Put `isabella.css`, `isabella-window-buttons.css` and the "isabella" folder in `resources/vivaldi/style` in your Vivaldi install directory, then edit the `<head>` of `resources/vivaldi/browser.html` with a reference to `isabella.css`.

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
git clone https://github.com/isabella-theme/isabella-vivaldi.git && cd isabella-vivaldi
mv isabella.css /opt/vivaldi/resources/vivaldi/style/
mv window-buttons/isabella-buttons.css /opt/vivaldi/resources/vivaldi/style/
mv window-buttons/isabella-buttons /opt/vivaldi/resources/vivaldi/style/
sed -i 's/  <\/head>/    <link rel="stylesheet" href="style\/isabella.css" \/>\n  <\/head>/' "/opt/vivaldi/resources/vivaldi/browser.html"
```

**Vivaldi Snapshot**
```bash
git clone https://github.com/isabella-theme/isabella-vivaldi.git && cd isabella-vivaldi
mv isabella.css /opt/vivaldi-snapshot/resources/vivaldi/style/
mv window-buttons/isabella-buttons.css /opt/vivaldi-snapshot/resources/vivaldi/style/
mv window-buttons/isabella-buttons /opt/vivaldi-snapshot/resources/vivaldi/style/
sed -i 's/  <\/head>/\n<link rel="stylesheet" href="style\/isabella.css" \/>\n  <\/head>/' "/opt/vivaldi-snapshot/resources/vivaldi/browser.html"
```

Also, you can use the Adwaita window buttons instead if you copy the `adwaita-buttons` folder and `adwaita-buttons.css` instead of the Isabella buttons.

**Note:** I use Vivaldi's snapshot cycle, so that's the version that this skin is being written on. It should work just as well on the stable version but please let me know if you encounter any issues.

### Known issues
- the internal siteinfo button in the addressfield is transitioned inconsistently with the rest of the interface
