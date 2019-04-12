# Isabella for Vivaldi custom css
## Features
- **improve interface animation transitions** By default Vivaldi's animations throughout its interface are pretty inconsistent, some elements just jerk awkwardly between states because they aren't animated at all. Isabella adds smooth transitions to several elements that previously had none.
- **buttons in the tab bar are arranged more consistently** By default, Vivaldi places the window buttons in the far top right of the window, but places all the other buttons in the header just above the address bar. Isabella repositions all the buttons at the top of the window so that they're all vertically centered.
- **more clear tab hovered** When you're moving your mouse over the tabs in the tab bar, Isabella emphasizes the tab that's currently being hovered far more clearly than Vivaldi does by default. 
- **more visible tab stack indicators** Tab stack indicators are easier to see, the topmost tab in a tab stack is easier to distinguish from the others. This is done without requiring more space for the indicators.
- **no top gradient** By default, Vivaldi draws a gradient behind the tabs if various criteria are met by the currently applied theme. In particular if the accent is dark and applied to the window. Isabella removes the gradient.
- **adapt to your preferred color scheme** Don't like the colours Isabella uses? Simply don't use them! If you just want the interface improvements, the css will adapt smoothly into any theme you apply in Vivaldi's settings.
- **make Vivaldi respect your system theme** Isabella integrates with the Isabella gtk theme by forcing Vivaldi to use those window buttons instead.

## Installation (Linux)
**Vivaldi Stable**
```bash
git clone https://github.com/Tiamarth/Isabella.git && cd Isabella/vivaldi
mv isabella.css /opt/vivaldi/resources/vivaldi/style/
mv isabella /opt/vivaldi/resources/vivaldi/style/
sed -i 's/  <\/head>/    <link rel="stylesheet" href="style\/isabella.css" \/>\n  <\/head>/' "/opt/vivaldi/resources/vivaldi/browser.html"
```
**Vivaldi Snapshot**
```bash
git clone https://github.com/Tiamarth/Isabella.git && cd Isabella/vivaldi
mv isabella.css /opt/vivaldi-snapshot/resources/vivaldi/style/
mv isabella /opt/vivaldi-snapshot/resources/vivaldi/style/
sed -i 's/  <\/head>/\n<link rel="stylesheet" href="style\/isabella.css" \/>\n  <\/head>/' "/opt/vivaldi-snapshot/resources/vivaldi/browser.html"
```

### Todo
&#9744; sidebar  
&#9744; scrollbars  
&#9744; status bar  
&#9744; side and bottom tabs  
&#9744; settings menu  
&#9744; color scheme-specific styles  
&#9744; more animations  
&#9744; screenshots  

### Known issues
- buttons in searchfield and addressfield briefly flash a white border on mouse exit
- the internal siteinfo button in the addressfield is transitioned inconsistently with the rest of the interface
