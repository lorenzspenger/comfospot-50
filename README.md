# Comfospot 50

Findings from reverse engineering the Zehnder Comfospot 50 to get it into Home Assistant.

# Idea
While some efforts where made to analyze the [serial connection on the main board](https://kaspars.net/blog/zehnder-comfospot-protocol) of the ventilation system, I tried a more 'analog', less invasive route.
The idea was to put a microcontroller behind the button controls on the front of the device and intercept and manipulate the signals coming from, and going to the control panel.
To do this I had to find the correct connector. The [Würth Electronics WR-MM IDC Connector System](https://www.we-online.com/en/components/products/em/connectors/wire-to-board/wr-mm_mini_module) is used, with 14 Pins.


## Pin Definitions
### TO DO: Insert Pin definition picture
First I analyzed which pin was responsible for which button press and LED on the control panel. And the most important question was if there is a supply voltage to drive a microcontroller, preferably 3.3V.


## PCB
### TO DO: Insert Schematics PDF
I built a PCB which can be clipped directly onto the control panel and sit between it and the ecu of the system.
On the PCB we need an __ESP32 C3__, a __female__ and a __male WR-MM connector__.


## Home Assistant Integration
For the programming of the microcontroller I settled on ESPHome, since I'm quite familiar with the system and I can integrate it without any additional work into Home Assistant.

All functions which can be controlled from the control panel can be controlled from within HA.
* fan speed (readout and control)
* fan direction / exchange
* change filter and error LED
* reset filter

While all of these functions can be controlled from within HA, the control panel remains fully functional, and every state change triggered on the device itself will be reflected in HA.

### TO DO: 
* Add Gerber files
* Add BOM
* Add YAML
