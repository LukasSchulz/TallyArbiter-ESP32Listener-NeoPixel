# Tally Arbiter ESP32 Listener
Tally Arbiter ESP32 Listener is a modified Version of the Tally Arbiter M5Stick-C Listener written  by Joseph Adams and is therefore also distributed under the MIT License.

Tally Arbiter ESP32 Listener is an accessory program that allows you to connect to a Tally Arbiter server and control an ESP32 Arduino device and attached NeoPixel (or similiar) LEDs based on the incoming tally information.

To learn more about the Tally Arbiter project, [click here](http://github.com/josephdadams/tallyarbiter).

It is not sold, authorized, or associated with any other company or product.

To contact the author or for more information, please visit [www.techministry.blog](http://www.techministry.blog).

## Soldering 
The NeoPixel-LEDs need to be soldered (or connected via cables) to the ESP32-board for them to light up. GND must connect to GND on the ESP32 board, +5V to +5V or VCC and DIN to the LED_PIN defined in the code (5 by default).

<!-- (Insert an image of an example pinout and connections) -->

## Installing Sketch and Libraries
1. Follow the tutorial for your specific ESP32-borad to download, install, and configure the Arduino IDE program. This is necessary to compile the code for your device.
1. Once you have the Arduino IDE installed and configured for your OS, install the following libraries (if not already installed):
	* `Adafruit_NeoPixel` by Adafruit (depending on the device you are using)
	* `WebSockets` by Markus Sattler
	* `Arduino_JSON` by Arduino

These will have to be included with the sketch file in order for it to compile properly.
## Compile and Upload the Sketch to the Device
1. Once all libraries are downloaded, open the `tallyarbiter-esp32.ino` file in the Arduino IDE.
1. Modify these lines at the top of the file to reflect your wireless network and Tally Arbiter server settings:
	```c++
	//Wifi SSID and password
	const char * networkSSID = "YourNetwork";
	const char * networkPass = "YourPassword";

	//Tally Arbiter Server
	const char * tallyarbiter_host = "192.168.1.100";
	const int tallyarbiter_port = 4455;
	```
1. Save the file.
1. Connect your ESP32 device to the computer via the provided USB-C or micro-USB cable.
1. If not already on, power the device on by holding down the power button (located on the bottom left-hand side) for a couple seconds.
1. Go to Tools > Board > ESP32 Arduino > and choose the right ESP32 based on the board you have. (There are many variants, [with](https://www.dfrobot.com/product-1590.html) or [without](https://www.ebay.de/itm/234033021888) a lipo-charging-controller and many other differences) If it's not listed, you may need to install it through the Boards Manager.
1. Go to Tools > Upload Speed > and choose `750000` (one less from the maximum speed).
1. Go to Tools > Port > and choose the serial port that represents your device.
1. Go to Sketch > and choose `Upload`. The code will compile and upload to the device.

Once the code is successfully compiled and uploaded to the device. the M5Stick-C will boot up and automatically try to connect to your Tally Arbiter server. It will auto-assign itself to the first Device on the server, and you can reassign it through the Settings GUI of Tally Arbiter.

Video Walkthrough (for the M5Stick-C): https://youtu.be/WMrRKD63Jrw

## Using the Device
When you turn on the ESP32 device after it has been programmed, the LEDs will light up blue, then it will automatically connect to the wireless network using the settings provided, and then initiate a connection to the Tally Arbiter server. If the server is offline, just reboot the device after the server is back online.

Other features using various button combinations may be added at a later date with an upgrade to this code.

# Improvements and Suggestions
I welcome all improvements and suggestions. You can submit issues and pull requests.

## Thanks
Thank you to Joseph Adams for this great project!
