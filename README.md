# TrafficLight
Smart traffic light for Bathroom/Toilet

this Project utilizes an ESP8266 as a micro controller for the WS8212B LEDs to serve as a smart traffic light for the toilet. This project also based on HomeAssistant and Tuya magnetic door sensor.

The project was designed to provide a visual and convenient solution to the problem of waiting outside a bathroom. It is also helps to give indication wether you should wait for air to clear before you enter to what needs to be done.

Hardware: ESP8266, WS2812B LEDs, Home Assistant server, Tuya Door Sensor, Home Network.

Software: WLED, Home Assistant.

Integrations: Tuya , WLED.

How it Works:
I'm going to assume that you already have working HA server and if not you can go ahead here *LINK FOR HA INSTALLAION*
There is a hard casing in the shape of a traffic light that contains the LEDs, each section contain 1 LED. all the LEDs are chained and connected to the ESP8266, in addition thes a button to help manually controll the states.

The ESP8266 MicroController has 3 wires connected to the LED :
D2 -> Data 
5v -> Plus (Red wire) 
GND -> Ground (Black wire)
There is also a button connected (could be reversed since it only closes a circuit:
D5 -> Plus
GND -> Minus
After connecting all the wires I flashed WLED for ESP8266 and connected it to my home network *LINK FOR WLED INSTALLAION*
There are attached files for the configurations of the traffic light.

The LEds are are divide to 3 section, one for each color, and each one is lighted up as needed acording to the traffic light state.
each state is saved in in order to help HomeAssistant to utillize it.
the button is used to switch between states in a case of failture or testing.

On the other side theres a Zigbee Tuya door sensor. the reason I chose this product is because I already used the ecosystem so I have periferals and the price is super cheap.

when everything is connected you go to Automation & scenes and add new automations:

 
