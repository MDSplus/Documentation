# jScope

**jScope** allows you to view individual data points similar to the output you would receive in an oscilloscope.

## Opening jScope
To open in Linux, open a terminal window and type the following. This command is case sensitve in Linux.

```sh
jScope
```
You can also type `jscope` in your OS app search.

## Connect to a Server

### Add a server to the server list

[screenshot: menu with 'edit server list' highlighted]
`Network` > `Edit server list`

[screenshot: Server list popup]


### Select a server
`Network` > `Server`
choose a server
click `apply`

## Add plots to the window

`Customize > Setup data source...` (or `right click > Setup data source...`)

[screenshot goes here: the setup  screen]
Y axis: 
X Axis
7


`File > Close` closes a single window
`File > Exit` will exit out of the program if you tell it to close all



`Autoscale`  > All Y
this is popular:

[screenshot]
right click > `all same x, auto y` will scale all the panels at the same time

[screenshot: "Default setup"]
`Customize > global settings` -- will probably want 
this changes default settings for any panel
useful for starting scale, experiment, and shot

[screenshot: customize > window]  
`Customize > window`
adjust the sliders to show number of graphs per panel
you can click and drag with mouse
or hightlight the slider and press up/down with keyboard to adjust


`Title`
This is for the whole window. `Title` is a TDI expression--you can get things from nodes. to provide an uncalculated name, you must wrap it in quotation marks (`""`).

[screenshot color configuration dialog]  
`Customize > colors list` but this only has graphical sliders
if you want to type in numbers, go to `File > Properties`



`Customize > Save as> `  
Allows you to save the current view
`.jscp` is the jscope standard and has additional features
`.dat` is the dwscope standard and is feature limited


[screenshot]  
`Update > (checkbox on/off)`
This just tells it to update the graph as signals come in (such as during an experiment)


## Help menu, but don't actually publish this?
The URL there is this:
https://www.mdsplus.org/index.php?title=Documentation:Tutorial:UsingScope
