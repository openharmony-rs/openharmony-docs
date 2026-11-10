# OHMIDI
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @owen_creeper-->
<!--Designer: @trytocalm-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=1e020c03bdc7e8347d2df773c6dec6050603f0f7 translatedAt=2026-11-10T03:11:21.293Z pushedAt=2026-11-10T04:49:36.824Z nl=1 -->

## Overview

Provides the C interface definitions of the MIDI (Musical Instrument Digital Interface) module for MIDI device management and data transmission. It supports MIDI device discovery and connection, device hot swap status monitoring, port capability query and switching, and data transmission and reception in the UMP (Universal MIDI Packet) format. It is applicable to scenarios where applications need to connect to peripherals such as electronic musical instruments and MIDI controllers and exchange MIDI data.

**Since:** 24

## Files

| Name| Description|
| -- | -- |
| [native_midi.h](capi-native-midi-h.md) | Declares MIDI-related APIs. MIDI is a technical standard for communication between electronic musical instruments, computers, and other devices.<br> The APIs in this file are used for MIDI device management, MIDI message sending and receiving, and device status monitoring.<br> The typical process of connecting to a MIDI device using OHMIDI is as follows:<br> 1. **Create a client**: Initialize the MIDI client context, and register the device hot-swap callback and the service exception callback.<br> 2. **Discover devices and ports**: Obtain the list of currently connected devices, and query the port capabilities of the devices.<br> 3. **Open a device**: Establish a device connection session.<br> 4. **Open a port**: Open the port based on its direction (input/output).<br> 5. **Data exchange**: * **Receive**: Receive MIDI data in UMP (Universal MIDI Packet) format through the callback function. * **Send**: Construct a UMP (Universal MIDI Packet) and send it through the output port.<br> 6. **Release resources**: Close the port and device, and destroy the client after use. |
| [native_midi_base.h](capi-native-midi-base-h.md) | Declares the basic data structure of the MIDI module. The file defines the basic types, enumerations, structs, and callback functions of the MIDI APIs.|
