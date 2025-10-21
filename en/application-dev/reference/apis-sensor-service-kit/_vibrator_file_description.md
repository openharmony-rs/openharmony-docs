# Vibrator_FileDescription
<!--Kit: Sensor Service Kit-->
<!--Subsystem: Sensors-->
<!--Owner: @dilligencer-->
<!--Designer: @butterls-->
<!--Tester: @murphy84-->
<!--Adviser: @hu-zhiqiong-->

## Overview

The **Vibrator_FileDescription** struct describes the vibration file description.

**Since**: 11

**Related module**: [Vibrator](_vibrator.md)

**Header file**: [vibrator_type.h](vibrator_type_8h.md)


## Summary


### Member Variables

| Name| Description|
| -------- | -------- |
| [fd](#fd) | File handle of the custom vibration sequence. |
| [offset](#offset) | Offset address of the custom vibration sequence.|
| [length](#length) | Total length of the custom vibration sequence.|


## Member Variable Description


### fd

```
int32_t Vibrator_FileDescription::fd
```
**Description**

File handle of the custom vibration sequence.


### offset

```
int64_t Vibrator_FileDescription::offset
```
**Description**

 Offset address of the custom vibration sequence.

### length

```
int64_t Vibrator_FileDescription::length
```

**Description**

Total length of the custom vibration sequence.
