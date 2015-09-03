# PicoLoader

PicoLoader simple javascript wrapper that will allow you to use PICO-8 web player outstide official Lexaloffle's BBS.

Features:

 * Embedding PICO-8 using only one simple javascript command
 * Send button states to web player
 * Pause, Reset cart, Set or toggle volume (mute)
 * Basic and advanced examples included

*Notice: Examples will not work without pico8.data file! Read "Basic usage" for more information!*


## Basic usage

First download '**pico.data**' from Lexaloffle's BBS (http://www.lexaloffle.com/bbs/pico8.data) and place it to the same folder as your html script.

In your html's head load '**picoloader.js**' just as you do with other scripts and add **div** container with ID assigned.

After document is ready, just call **PicoLoad**(*[container-id]*, *[cart-file]*) like this:

```javascript
document.addEventListener("DOMContentLoaded", function(event) { 
	PicoLoad('container', 'cart.p8.png');
});
```
If you are using jQuery you can do the same this way:
```javascript
$(document).ready(function () {
	PicoLoad('container', 'cart.p8.png');
});
```

## Advanced usage

If you need more control over your PICO-8 web player, you can use following methods

**PicoLoad**(*[element]*, *[cart]*, *[library]*)

	element - you can provide element or element's id (canvas will be created inside that element)
    cart - path to cart you want to load
    library - if you want to use custom web player library, provide path here

**PicoPress**(*[key]*, *[player]*)

	Press the controller's button. Use same code that you are used to in your pico console.
	0=LEFT, 1=RIGHT, 2=UP, 3=DOWN, 4=A, 5=B
    0/1 as player number
    
**PicoRelease**(*[key]*, *[player]*)

	Release the controller's button. Same usage as PicoPress.

**PicoMute**()

	Toggles volume between 0 and 256.

**PicoVolume**(*[vol]*)

	Sets the volume to value between 0 and 255.

**PicoPause**()

	Pause or resume PICO-8 machine.

**PicoReset**()

	Restarts loaded cart.

## Resolution

PICO-8 web player doesn't allow to change canvas resolution, but you can download pico8.js file and hack it to support whatever resolution you need.

* download pico8.js from Lexaloffle's BBS (http://www.lexaloffle.com/bbs/pico8.js)
* open it up in your favorice code editor and search for ```c[206279]=580;c[206280]=540;l=580;m=540```
* replace 580 and 540 values with your own
* load your custom pico8.js instead of default one using PicoLoad command.

*Notice: For best results be sure to use multiples of base resolution (145x135)!*


## Why you have to download js and data files?

Those files are made by Lexaloffle's staff and are certainly not public domain or open-source of any kind. I have created this project just to help people who desperately want to experiment with their PICO-8 games outside official BBS or just publish them on their website. Later, hopefully, official way to embed our games will be available and this little script will become obsolete.