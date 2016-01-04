# Kaiju Flambeaux Corps lightsuits

This is the program that we will be running on the 2016 Kaiju Flambeaux Corps suits, pedalcart and flambeauxs.

## Workflow

tl;dr: Do your work in feature branches, then merge it into master. I imagine this is a pretty standard git workflow, but here it is summarised anyway:

Once you've cloned the repository and gotten it working, create a new branch and make your changes there. You may push your branch to the repository every so often to make sure it's backed up. When your modifications are complete, do a `git pull`, check out the master branch, and merge your branch into it. When this is finished and master has your changes merged in, push master back to github (`git push origin master`).

## Getting started

### Prerequisite software

#### All platforms

- [Arduino Software][2] (1.6.4 or later)
- Your preferred IDE or text editor (makefile support encouraged)

#### Windows

I've had a lot of trouble getting GNU Make to work on Windows -- it often complains about missing files when the file exists. If you get this project to build using Arduino-Makefile as it is designed, please document your process, and submit any necessary changes to the source in a pull request.

### Initial setup

You'll need to configure a handful of options in the makefile before the project will build and upload. Open `kaiju_program/makefile` and make these changes:

- Set `PROJECT_DIR` to an absolute path to your `kaiju_program` directory
- Set `ARDUINO_DIR` to an absolute path to your Arduino Software installation (for example, `/home/tully/ArduinoSDK/1.6.6`)
- Set `MONITOR_PORT` to the port you use to communicate with your programmer.
  - On Windows, this will be a COM port.
  - On Linux, this will be `/dev/ttyUSB*` or `/dev/ttyACM*` depending on the type of programmer you have.
  - I don't have a Mac handy, but I think it shows up as `/dev/tty.usbmodem*`.
- **If you are using different hardware than the [Anarduino MiniWireless][3]**, you may need to update `BOARD_TAG` and `BOARD_SUB`. These correspond to the *Board* and *Processor* settings in the Arduino Software's *Tools* menu, but are not the same as the displayed text in that menu. The correct values can be found in the `boards.txt` file in your Arduino Software installation.

**NB: please don't commit these changes back to the repository, otherwise other members will be prompted to merge your personal configuration.**

### Building the project

From a console, enter the `kaiju_program` directory and execute `make all`. If the build succeeds, the static memory usage of the program will be displayed.

### Uploading the program

From a console, enter the `kaiju_program` directory and execute `make upload`. If your build succeeds, `avrdude done.  Thank you.` will be displayed.

[2]: https://arduino.cc/en/Main/Software
[3]: http://www.anarduino.com/miniwireless/
