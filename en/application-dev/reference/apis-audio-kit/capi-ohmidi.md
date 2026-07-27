# OHMIDI

<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @owen_creeper-->
<!--Designer: @trytocalm-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=1961de06e85063963f633ec54a8a4baaf5cb7dc8 translatedAt=2026-07-21T04:01:58.738Z pushedAt=2026-07-22T01:21:49.840Z -->

## Overview

This module provides C API definitions for the Musical Instrument Digital Interface (MIDI) module. The APIs are used for MIDI device management and data transmission.

**Since:** 24

## Files

| Name| Description|
| -- | -- |
| [native_midi.h](capi-native-midi-h.md) | Declares MIDI-related APIs. MIDI is a technical standard for communication between electronic musical instruments, computers, and other devices.<br> The APIs in this file are used for MIDI device management, MIDI message sending and receiving, device status monitoring, and more.<br> The typical process of using OHMIDI to connect to a MIDI device is as follows:<br> 1. **Create a client**: Initialize the MIDI client context, and register the device hot-swap callback and service exception callback.<br> 2. **Discover devices and ports**: Obtain the list of currently connected devices, and query the port capabilities of the devices.<br> 3. **Open a device**: Establish a device connection session.<br> 4. **Open a port**: Open ports based on the port direction (input/output).<br> 5. **Exchange data**: * **Receiving**: Receive MIDI data in UMP format through a callback function. * **Sending**: Construct UMP packets and send them through the output port.<br> 6. **Release resources**: Close the ports and device, and destroy the client after use. |
| [native_midi_base.h](capi-native-midi-base-h.md) | Declares the basic data structure of the MIDI module. The file defines the basic types, enumerations, structs, and callback functions of the MIDI APIs.|