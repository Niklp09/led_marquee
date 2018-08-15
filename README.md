# LED marquee mod 

*by Vanessa Dannenberg*

This mod provides set of alphanumeric LED marquee panels, controlled by Mesecons' Digilines mod.

Simply place a panel, right-click it, and set a channel.

Then send a character, a string, or one of several control words to that channel from a Mesecons Lua Controller and the mod will try to display it.  The panels use the standard 7-bit ASCII character set (with a few alterations).

A single character will be displayed on the connected panel.

Strings will be displayed using all panels in a lineup, so long as they all face the same way, starting from the panel the Lua Controller is connected to, going left to right.  The other panels in the line do not need to be connected to anything - think of them as being connected together internally.  Only the panel at the far left need be connected to the Lua Controller.

The string will spread down the line until either a panel is found that faces the wrong way, or has a channel that's not empty/nil and is set to something other than what the first is set to, or if a node is encountered that is not an alpha-numeric panel at all.

Panels to the left of the connected one are ignored (unless they, too, have their own connections).

You can put multiple lines of panels end to end to form independent displays, so long as the panels that start each of the lines have unique channel names set.

The string is padded with spaces and then trimmed to 64 characters.

Any unrecognized symbol or character outside the ASCII 32 - 129 range, whether part of a string or singularly is ignored, except as noted below.

The panels also respond to these control messages:

* the words "off", "colon" and "period" translate to a blank space, ":", and ".", respectively.
* "del" or character code 127 displays a square with an X in it
* "allon" or character code 128 will turn on all LEDs on the panel.
* "cursor" or character code 129 will display a short, thick line at the bottom of the panel.
* "off_multi" turns all panels in a lineup off
* "allon_multi" turns on all LEDs of all panels in a lineup.

A byte value of 0 to 7 will change colors (i.e. string.char(0 to 7) ).  You can select from red (0), orange, yellow, green, cyan, blue, purple, or magenta (7).  The left-most/"master" panel will remember the last color used, and defaults to red.

You can use "get" and "getstr" to read the one character from the connected panel.  These messages will not read the other panels in the lineup.

All panels emit a small amount of light when displaying something.

The panels only mount on a wall.
