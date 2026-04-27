# OHMIDI
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @owen_creeper-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

## Overview

This module provides C API definitions for the Musical Instrument Digital Interface (MIDI) module. The APIs are used for MIDI device management and data transmission.

**Since:** 24

## Files

| Name| Description|
| -- | -- |
| [native_midi.h](capi-native-midi-h.md) | Declares MIDI-related APIs. MIDI is a technical standard for communication between electronic musical instruments, computers, and other devices.<br> The APIs in this file are used for managing MIDI devices, sending and receiving MIDI messages, and monitoring device status.<br> The typical process for connecting a MIDI device using OHMIDI is as follows: 1. **Create a client**: Initialize the MIDI client context, and register the device hot swap callback and service exception callback.2. **Discover devices and ports**: Obtain the list of currently connected devices and query the port capabilities of the devices.3. **Open a device**: Establish a device connection session.4. **Enable ports**: Enable the ports based on the port direction (input/output).5. **Perform data interaction**: * **Receiving**: Use the callback function to receive MIDI data in the Universal MIDI Packet (UMP) format. * **Sending**: Construct a UMP data packet and send it through the output port.6. **Release resources**: Close the port and device and destroy the client after use.|
| [native_midi_base.h](capi-native-midi-base-h.md) | Declares the basic data structure of the MIDI module. The file defines the basic types, enumerations, structs, and callback functions of the MIDI APIs.|
<!--no_check-->