Übersicht World Clock Modified by Richard Tanksley

A desktop world clock for macOS, built as an Übersicht widget. It shows your local time plus any cities you choose, with a row of hour-tiles for each so you can convert times across zones at a glance.

Features
Your Time row on top, detected automatically from your Mac's time zone (follows you when you travel)
24 hour-tiles per city, aligned so each column is the same moment everywhere; the current hour is outlined
Color-coded hours: slate blue for working hours (8am to 6pm), gray for early morning and evening, dark for night
Midnight tiles show the date, so you can see where the next day starts
Native hour format: follows your Mac's 12-hour or 24-hour setting
Handles daylight saving and half-hour zones (e.g. Phoenix, Mumbai) automatically
No external scripts or network calls; runs entirely on your Mac

Default cities: San Francisco, London, Singapore, Mumbai, Phoenix, Atlanta.

Install
Download and install Übersicht. If macOS blocks it, go to System Settings > Privacy & Security and click Open Anyway.
Click the Übersicht icon in the menu bar and choose Open Widgets Folder. (Or in Finder press Cmd+Shift+G and go to ~/Library/Application Support/Übersicht/widgets.)
Copy world-clock.jsx into that folder.
The clock appears in the bottom-left of your desktop within a few seconds. If not, choose Refresh All Widgets from the Übersicht menu.

Tip: turn on Launch at login in Übersicht's preferences so the clock is always there.

Customize

Open world-clock.jsx in a plain text editor (in TextEdit, first choose Format > Make Plain Text) and edit the settings at the top.

Cities
js
const ZONES = [
  { name: "San Francisco", tz: "America/Los_Angeles" },
  { name: "London", tz: "Europe/London" },
  { name: "Singapore", tz: "Asia/Singapore" },
  { name: "Mumbai", tz: "Asia/Kolkata" },
  { name: "Phoenix", tz: "America/Phoenix" },
  { name: "Atlanta", tz: "America/New_York" },
];
name is the label shown on the widget.
tz must be an IANA time zone name. See the full list.
Keep the quotes, braces and trailing commas.
A city in the same zone as your Mac is merged into the Your Time row.
Other settings
Setting	Default	What it does
TILE_COUNT	24	Number of hour-tiles per row
HOURS_BEFORE	3	Past hours shown to the left of the current hour
ACCENT	
#8BA1BB	Color of working-hours tiles
Position

Edit the className block. For example, to place it top-right:

js
export const className = `
  top: 24px;
  right: 24px;
  ...
`;

Save the file and the widget reloads automatically.

Troubleshooting
Can't see the widget: it sits behind your windows. Show the desktop (Fn+F11 or Mission Control) and check the bottom-left corner.
Red error on the desktop: usually a missing comma or quote in ZONES, or curly quotes inserted by a rich-text editor.
File not loading: make sure the name ends in exactly .jsx (not .jsx.txt or .jsx.download).
Two clocks showing: an older copy of the file is still in the widgets folder; delete it.
