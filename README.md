# TrafficLight
Smart Bathroom Indicator System
This project is a home automation solution that provides a clear visual status of a bathroom's occupancy using a smart traffic light. It was developed to solve the common problem of waiting outside a bathroom and to indicate when enough time has passed to let the air clear.

# Key Features
Visual Occupancy Indicator: A custom-built traffic light signals whether a bathroom is occupied (red), vacant (green), or recently vacated with a specific condition (red-yellow).

Automated State Logic: Utilizes a Home Assistant server to interpret data from a Tuya door sensor and automatically control the traffic light's state.

Customizable Logic: Includes a "poop mark" feature—a configurable timer that changes the indicator's color after a set duration, providing an additional layer of information.

Night Light Mode: A bonus feature that provides a low-brightness night light, activated during late hours to assist in navigation.

# Technologies Used
This project demonstrates proficiency in the following areas:

Hardware Integration: ESP8266 microcontroller, Addressable LEDs (WS2812B), and a Zigbee Tuya Door Sensor.

Firmware: Flashing and configuring WLED on the ESP8266.

Home Automation: Setting up automations, helpers, and devices within Home Assistant.

Networking: Integrating various IoT devices over a home network.

Physical Prototyping: Designing and building a custom traffic light casing.

# System Architecture
The system's logic is built around the interaction between three main components: the Tuya door sensor, the Home Assistant server, and the ESP8266 with WLED.

Input: A Tuya door sensor detects when the bathroom door opens or closes.

Processing: Home Assistant receives the sensor's state and processes it using a series of automations and a Boolean "helper" to track occupancy duration.

Output: Based on the automation rules, Home Assistant sends commands to the WLED firmware on the ESP8266, which controls the color of the LED traffic light.

# Hardware and Setup
1. **Physical Assembly**

This Project assumes you already have have Home Assistant server running, if you don't you can follow instructions [here](https://www.home-assistant.io/installation/) to install on your machine

use a hard casing for the Traffic light, presumably a 3D-Printed one (I used a concrete one I had laying around, like every other normal person), with each section containing a single WS2812B LED. The LEDs are daisy-chained and connected to the ESP8266 microcontroller.
I used kitchen Wax paper and plastic bow lid i cut to diffuse the light from the led.

The wiring is as follows:

ESP8266 to LED Strip:

D2 → Data

5V → Plus (Red wire)

GND → Ground (Black wire)

Button (Optional): A button is connected to D5 and GND to allow for manual state overrides during testing or failure.

3. **Firmware**

   
After connecting the wires, I flashed the WLED firmware onto the ESP8266 and connected it to my home network, you can find WLED repository [here](https://github.com/WLED/WLED) 

The LEDs were divided into three segments—one for each color—and configured to respond to commands from Home Assistant.

5. **Home Assistant Configuration**

   
The logic for the traffic light is managed through Home Assistant automations.

Helper: A new Boolean helper named "poop mark" was created to act as a flag. This flag is triggered by an automation that checks if the door has been closed for more than three minutes.

Automations: Four primary automations were created to handle different scenarios:

1. when door is closed -> turn Traffic light to red
2. when door is open and the mark is triggerd -> turn Traffic light to red_Yellow
3. when door is open and the mark is  not triggerd -> turn Traffic light to Green
4. BONUS: I also added a 4th state for a night lamp so during the late night the traffic light is a low brightness solution for the sleepless who wonder to the tiolet during the dark hours.

![Watch the video](https://github.com/Avishyf/TrafficLight/blob/main/demo.gif)


![Demonstration](https://github.com/Avishyf/TrafficLight/blob/main/Image_1.jpg)
![Demonstration](https://github.com/Avishyf/TrafficLight/blob/main/Image_2.jpg)


