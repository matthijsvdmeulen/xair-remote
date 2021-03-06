# atem-remote

Use a Behringer X-Touch Mini MIDI controller to remote control a Blackmagic Design ATEM Switcher through the ATEM network protocol.

## Installing

You need Python 3.5 or later. Please make sure to install required libraries:

	$ sudo pip3 install -r requirements.txt

## Update

If you update from a previous version, please make sure that you run at least Python 3.5 and install all required libraries as described in the previous section.

The X-Touch device needs to be running in MC mode. Make sure that the MC LED is lit after connecting the device by pressing the MC button during startup.

## Running

To get help run:

	$ python3 atem-remote.py -h

The app will automatically detect both your X-Touch controller and the ATEM Switcher. So connect the controller and make sure the ATEM Switcher is reachable on your network. Now you can start the app:

	$ python3 atem-remote.py

If the app can not find your controller or connect to the ATEM Switcher, it will terminate with an error message explaining the problem. If everything started up successfully, the X-Touch mini will reflect the current switcher state and the console output will look like this:

	Using MIDI input: X-TOUCH MINI 1
	Using MIDI output: X-TOUCH MINI 2
	Connected to ATEM Mini on 192.168.1.6

Startup will fail if the X-Touch controller is not connected or the ATEM Switcher could not be located on the network. In the latter case you could try to specify the IP address of the switcher on the command line:

	$ python3 atem-remote.py 192.168.1.6

The app can monitor the X-Touch connection and exit if the controller is disconnected. This functionality is enabled by setting the parameter `-m`:

	$ python3 atem-remote.py -m

Note: Monitoring does not work on all platforms. Linux and Windows work fine while MacOS does not detect disconnects.

## Using

The following image is a schematic of all available controls on the X-Touch Mini:

![X-Touch Mini controls](img/xtm-layout.png)

You need to configure the device to start in MC mode. If the MC mode LED is not lit up, hold down the MC button while connecting the device.

To exit press `CTRL + C`.

The folder `labels` contains labels to print and attach to your X-Touch as Excel file. You can change the labels to your specific setup. Make sure you print them in 100% size.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details
