# USerializedSet

## Overview

A serialized form of a Unicode set. Limited manipulations arepossible directly on a serialized set. See below.

<!--Device-struct USerializedSet {...}--><!--Device-struct USerializedSet {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| const uint16_t *array | The serialized Unicode Set.<br><!--Device-const uint16_t *array--><!--Device-const uint16_t *array-End--> |
| int32_t bmpLength | The length of the array that contains BMP characters.<br><!--Device-int32_t bmpLength--><!--Device-int32_t bmpLength-End--> |
| int32_t length | The total length of the array.<br><!--Device-int32_t length--><!--Device-int32_t length-End--> |
| uint16_t staticArray[USET_SERIALIZED_STATIC_ARRAY_CAPACITY] | A small buffer for the array to reduce memory allocations.<br><!--Device-uint16_t staticArray[USET_SERIALIZED_STATIC_ARRAY_CAPACITY]--><!--Device-uint16_t staticArray[USET_SERIALIZED_STATIC_ARRAY_CAPACITY]-End--> |


