# Calliope Mini Lab

An interactive remote laboratory for programming the Calliope mini microcontroller with MicroPython.

Import the lab into your Edrys classroom using the following link:

https://raw.githubusercontent.com/edrys-labs/lab-calliope-mini/main/lab_calliope_mini.yaml

or just click the deploy button below:

[<img src="https://img.shields.io/badge/%F0%9F%9A%80%20-%20Deploy%20Lab%20-%20light?style=plastic" height="25" />](https://edrys-labs.github.io/?/deploy/https://raw.githubusercontent.com/edrys-labs/lab-calliope-mini/main/lab_calliope_mini.yaml)

## Overview

This laboratory practicum offers students the opportunity to learn the basics of programming embedded systems with MicroPython – directly using the Calliope mini microcontroller as an example. The lab is accessible as a remote laboratory through the Edrys platform, allowing students to experiment with real hardware from anywhere.

The main task is a weather display: students read the temperature from the Calliope mini's sensors, show it as a symbol on the LED matrix, and detect large temperature changes between two measurements. Students who finish can extend it, for example with a darkness alarm, switching between temperature and light with buttons A and B, or logging the values over the serial interface.

Students develop and test their program in a simulator first, where they can set the temperature and light level with sliders and press the buttons. On the station, the sensor values cannot be changed remotely (the room temperature is nearly constant and the station light is on while someone is in the room), so the station is used to run the program on the real hardware and check that it gives plausible values.

The lab content is in German.

## Learning Objectives

- First steps in programming embedded systems with MicroPython
- Getting to know the hardware functions of the Calliope mini (sensors, LED matrix, buttons)
- Reading environmental sensors and showing the values on the LED matrix
- Development of structured, reusable programs in MicroPython
- Using the serial interface for communication and error analysis

## Lab Structure

1. **Lobby**: Introduction and overview of the lab with tutorial video
2. **Room 1**: Learning objectives, the main task and its extensions, and the hardware layout of the Calliope mini 3
3. **Room 2**: Simulator exercise: a code editor and a simulated Calliope mini 3 ([module-micropython-simulator](https://github.com/edrys-labs/module-micropython-simulator)) with sliders for temperature and light level. Runs in the browser, no hardware needed.
4. **Station**: Practical programming on the real Calliope mini with code editor, live stream of the hardware, terminal for code execution, and a feedback survey

## Station Requirements

The station needs a Calliope mini 3 with MicroPython, connected via USB, and a camera pointed at it.

### Terminal

After importing the predefined configuration, you have to open a station and start the pyxtermjs server, running on localhost.

The easiest way to do this, is by installing docker and running the following command:

```bash
docker run -it -p 127.0.0.1:5000:5000 --device=/dev/ttyACM0:/dev/ttyACM0 edryslabs/module-pyxtermjs:latest
```
This will download the pyxtermjs terminal-server from docker-hub and run it in a secure environment. If the Calliope mini shows up under another device on your machine, replace the first `/dev/ttyACM0` with it.

The terminal uses the `micropython` workflow of [module-pyxtermjs](https://github.com/edrys-labs/module-pyxtermjs): code execution is handled via [mpremote](https://docs.micropython.org/en/latest/reference/mpremote.html), which connects to the first serial device it finds, copies the code to the Calliope mini as `main.py` and runs it.

### Station light (optional)

The station-only light control module switches an Elgato light on while users are in the station. It needs the light server running on the station's machine:

```bash
docker run --init -p 127.0.0.1:3000:3000 edryslabs/station-lights-server
```

Set the light's IP address (`lightIp`) in the module's station settings. See [module-station-light-control](https://github.com/edrys-labs/module-station-light-control) for details. Without a light, remove the module from the configuration.
