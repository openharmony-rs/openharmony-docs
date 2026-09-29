# Vibrator_FileDescription

```c
struct Vibrator_FileDescription {...}
```

## Overview

Defines the vibration file description. This method is used to describe the file information of a custom vibration pattern. You can use a custom vibration file to implement precise vibration control.

**System capability**: SystemCapability.Sensors.MiscDevice

**Since**: 11

**Related module**: [Vibrator](capi-vibrator.md)

**Header file**: [vibrator_type.h](capi-vibrator-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t fd | File handle of the customized vibration sequence, which must point to a valid file that contains the * vibration sequence data. Before using this API, you must open the file and obtain the file descriptor using * the file operation API such as **open**. The file descriptor must be valid and readable. It cannot be a * negative value or an invalid handle. |
| int64_t offset | Offset address of the custom vibration sequence, in bytes. This parameter specifies the start position * for reading the vibration sequence from the file. The value of **offset** must be greater than or equal to 0 * and less than the file size. If **offset** is 0, the file is read from the beginning. If **offset** is greater * than 0, the first **offset** bytes are skipped. If the value of **offset** exceeds the file size, undefined * behavior may occur. |
| int64_t length | Total length of the custom vibration sequence, in bytes. This parameter specifies the number of bytes * to read from the position specified by **offset**. The value of **length** must be greater than 0, and the sum * of **offset** and **length** cannot exceed the file size. If the value of **length** exceeds the remaining * file size, the read operation may fail or undefined behavior may occur. |


