# USerializedSet

## Overview

A serialized form of a Unicode set. Limited manipulations arepossible directly on a serialized set. See below.

## Summary

### Member variables

| Name | Description |
| -- | -- |
| const uint16_t *array | The serialized Unicode Set. |
| int32_t bmpLength | The length of the array that contains BMP characters. |
| int32_t length | The total length of the array. |
| uint16_t staticArray[USET_SERIALIZED_STATIC_ARRAY_CAPACITY] | A small buffer for the array to reduce memory allocations. |


