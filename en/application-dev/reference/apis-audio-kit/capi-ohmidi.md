# OHMIDI
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @owen_creeper-->
<!--Designer: @trytocalm-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=0578931480203da834b543b8c823f3ce7e94473d translatedAt=2026-11-03T04:32:46.026Z pushedAt=2026-11-04T03:11:47.057Z nl=1 -->

## Overview

Provides the C API definitions of the Musical Instrument Digital Interface (MIDI) module for MIDI device management and data transmission. It supports MIDI device discovery and connection, device hot-swap status monitoring, port capability query and switching, and data sending and receiving in the Universal MIDI Packet (UMP) format. It applies to scenarios where applications need to connect to peripherals such as electronic musical instruments and MIDI controllers and exchange MIDI data.

**Since:** 24

## Files

| Name| Description|
| -- | -- |
| [native_midi.h](capi-native-midi-h.md) | Declares MIDI-related APIs. MIDI is a technical standard for communication between electronic musical instruments, computers, and other devices.<br> The APIs in this file are used for MIDI device management, MIDI message sending and receiving, device status monitoring, and so on.<br> The typical process of using OHMIDI to connect to a MIDI device is as follows:<br> 1. **Create a client**: Initialize the MIDI client context, and register the device hot swap callback and the service exception callback.<br> 2. **Discover devices and ports**: Obtain the list of currently connected devices, and query the port capabilities of the devices.<br> 3. **Open a device**: Establish a device connection session.<br> 4. **Open a port**: Open the port based on its direction (input/output).<br> 5. **Data exchange**: * **Receive**: Receive MIDI data in UMP (Universal MIDI Packet) format through the callback function. * **Send**: Construct a UMP (Universal MIDI Packet) and send it through the output port.<br> 6. **Release resources**: Close the port and device, and destroy the client after use. |
| [native_midi_base.h](capi-native-midi-base-h.md) | Declares the basic data structure of the MIDI module. The file defines the basic types, enumerations, structs, and callback functions of the MIDI APIs.|
