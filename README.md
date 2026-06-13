# Glimmer
Glimmer is an [WLED](https://github.com/wled/WLED) controller board. It supports all the most common LED strip voltages over 6.3mm jack and 5V over USB-C, audio reactivity, IR control, and driving two separate data channels at once.

<details>
<summary>Photos</summary>

![render.png](/images/render.png)
![assembled.jpg](/images/assembled.jpg)

[schematics.pdf](/images/schematics.pdf)

</details>

## OSHWLab Stars 2026
The project had to be remade in EasyEDA in order to be submitted to the OSHWLab Stars competition. I'm not the biggest fan of the program, but it is what it is.

If you like the project feel free to check out it's OSHWLab page and maybe even leave a like if you're generous like that.

Link to the project over there: https://oshwlab.com/x3no/project_caxlifbu

## Software
The controller is meant to run under WLED. Check their docs for info about configuration and flashing.
Website: https://kno.wled.ge/
Github: https://github.com/WLED/WLED

There is an USB autoflashing circuitry present on the board, but you can use the UART port as well. If you do want to do it you should desolder the 0-ohm R22 and R22 resistors - they bridge the USB-UART controller with the ESP32.

If you want to use WLED-MM a platformio compilation environment is available [here](https://gist.github.com/X3NOOO/2119d469b6a600acc29e1caa4ec98841).

### UART LEDs

If the TX/RX LEDs are not flashing when talking with the board via USB your CP2102N didn't come with TXT and RXT enabled by default. You can change that using the [Simplicity Studio 5](https://www.silabs.com/software-and-tools/simplicity-studio/simplicity-studio-version-5). Download it, connect the board, and change the GPIO settings from GPIO to TXT and RXT. Doing this is not neccesary for the board to work though.

## Usage
Flashed your board with WLED? Good, now it's the time to wire it up. The first thing to do is to place a properly rated fuse into the fuse holder. The [3557-2 fuseholder](https://www.keyelco.com/userAssets/file/K75p47.pdf) takes both standard and mini automotive fuses. You can calculate the fuse value using the WLED calculator. The big screw terminal is responsible for power delivery. When holding your controller with the USB port up and facing you:
- The first hole is VDC, it's the barrel jack input, except it's fused via the fuse you just put in.
- The second hole is VUSB, it's the same power your USB port supplies. There is an 2A polyfuse placed on it's line, so that's the limit on the power you can pull through it.
- The third hole is GND.

Then, there is the smaller screw terminal. It is used to communicate with your LEDs and houses the data lines. Both of them are levelshifted to 5V. The one on the left is mapped to your ESP32's GPIO23 and the right one is GPIO18.

Now you connect the inputs board. Place some doublesided tape on the back of it and secure it in the cutout on the shell. Wire the connector 1:1, you can check the pinout if you're not sure if you're doing it right.

## Case
The .stl files of the enclosure are available in the Releases tab.

## Pricing
Prices at JLCPCB.

### Controller
- $160: Price for 2 assembled and 3 bare PCBs. All in black.
- $100: Price for 2 assembled and 3 bare PCBs w/o the ESP32 which forces you to pick standard assembly.
- $30: Price for 2+3 with most of the extended components excluded if you're willing to source and solder them yourself.

### Inputs board
Header is not soldered in any of the variants.
- $70: 2 assembled and 3 bare ones.
- $20: 2 assembled and 3 bare ones w/o the microphone as it forces standard assembly.

### Shell
- Up to $10: 1 bottom + 1 top. 

### Additional
- 4x >33mm M2 screws.
- 4x M2 threaded M2 insert nuts. Length=2mm, OD=4mm.
- A bit of double sided tape if your Inputs Board doesn't hold in place.

## Get it
All the files necessary to get the board made at JLCPCB are available in the Releases tab. They include all the components, so you can expect a to see a high price if you use them as they are. You can tweak the assembly components after uploading the BOM to the website to lower the price.

## IMPORTANT
I am not an engineer - the PCB works, but I cannot guarantee it will not burn your house down. I do not take any responsibility for y'all being silly.

## Sidenotes
- Thank you to the (unfortunately dead) [yawl controller](https://github.com/lizardsystems/yawl-controller) project - I stole your levelshifter.

- Thank you to the creators of the [OSHWLab Stars](https://oshwlab.com/activities/stars2026) competition for making it possible to get this board manufactured in a reasonable price.
