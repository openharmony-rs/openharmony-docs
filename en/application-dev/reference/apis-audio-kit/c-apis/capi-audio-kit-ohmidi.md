# OHMIDI

## Overview

Provides the definition of the C interface for the MIDI module.

**System capability**: SystemCapability.Multimedia.Audio.MIDI

**Since**: 24

## Files

| Name | Description |
| -- | -- |
| [native_midi.h](capi-native-midi-h.md) | Declares MIDI related interfaces.<br> MIDI is a technical standard that enables communication between electronic musical instruments, computers, and other devices. The interfaces in this file are used for MIDI device management, MIDI events sending and receiving, and device status monitoring.<br> A common case of using OHMIDI to connect with MIDI device works as follows:<br> <pre> OH_MIDIClient_Create(&client, callbacks, userData);<br> OH_MIDIClient_GetDeviceCount(client, &deviceCount); // The developer should allocate a buffer for 'deviceInfos' based on 'deviceCount'. OH_MIDIClient_GetDeviceInfos(client, deviceInfos, deviceCount, &actualDeviceCount);<br> // Iterate through 'deviceInfos' to get the 'midiDeviceId' and query its ports. OH_MIDIClient_GetPortCount(client, midiDeviceId, &portCount); // The developer should allocate a buffer for 'portInfos' based on 'portCount'. OH_MIDIClient_GetPortInfos(client, midiDeviceId, portInfos, portCount, &actualPortCount);<br> OH_MIDIClient_OpenDevice(client, midiDeviceId, &device); // Or use OH_MIDIClient_OpenBLEDevice to open a BLE device, // waiting for the OH_MIDIClient_OnDeviceOpened callback.<br> // Get the port descriptor from the 'portInfos' array to open the ports. OH_MIDIDevice_OpenInputPort(device, inputportDesc, onMidiReceivedCallback, userData); // The 'onMidiReceivedCallback' is triggered upon receiving MIDI messages.<br> OH_MIDIDevice_OpenOutputPort(device, outputportDesc); OH_MIDIDevice_Send(device, outputportIndex, events, eventCount, &writtenEventCount);<br> ...<br> OH_MIDIClient_CloseDevice(client, device); // Use OH_MIDIDevice_CloseInputPort and OH_MIDIDevice_CloseOutputPort to close specific ports. OH_MIDIClient_Destroy(client); </pre> |
| [native_midi_base.h](capi-native-midi-base-h.md) | Declares the underlying data structure for MIDI module. |
