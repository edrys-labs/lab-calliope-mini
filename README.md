# Calliope Mini Lab

An interactive remote laboratory for programming the Calliope mini microcontroller with MicroPython.

Import the lab into your Edrys classroom using the following link:

https://raw.githubusercontent.com/edrys-labs/lab-calliope-mini/main/lab_calliope_mini.yaml

or just click the deploy button below:

[<img src="https://img.shields.io/badge/%F0%9F%9A%80%20-%20Deploy%20Lab%20-%20light?style=plastic" height="25" />](https://edrys-labs.github.io/?/deploy/https://raw.githubusercontent.com/edrys-labs/lab-calliope-mini/main/lab_calliope_mini.yaml)

## Overview

This laboratory practicum offers students the opportunity to learn the basics of programming embedded systems with MicroPython – directly using the Calliope mini microcontroller as an example. The lab is accessible as a remote laboratory through the Edrys platform, allowing students to experiment with real hardware from anywhere.

Students develop applications for the Calliope mini where environmental data is read from integrated sensors and visualized on the LED matrix.

## Learning Objectives

- First steps in programming embedded systems with MicroPython
- Getting to know the hardware functions of the Calliope mini (sensors, LEDs, buttons)
- Independent experimentation with environmental sensors and the LED matrix
- Development of structured, reusable programs in MicroPython
- Using the serial interface for communication and error analysis

## Lab Structure

The lab is divided into several areas:

1. **Lobby**: Introduction and overview of the lab with tutorial video
2. **Room 1**: Basic information about the Calliope mini, learning objectives, and hardware layout
3. **Station**: Practical programming with code editor, live stream of hardware, and terminal for code execution

## Requirements (Terminal)

After importing the predefined configuration, you have to open a station and start the pyxtermjs server, running on localhost.

The easiest way to do this, is by installing docker and running the following command:

```bash
docker run -it -p 5000:5000 --device=/dev/ttyACM0:/dev/ttyACM0 edryslabs/module-pyxtermjs:latest
```
This will download the pyxtermjs terminal-server from docker-hub and run it in a secure environment.

(Code execution is handled via [mpremote](https://docs.micropython.org/en/latest/reference/mpremote.html) which connects to the Calliope mini and transfers the Python code for execution)
