# OH_PackingOptionsForSequence
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @liyang_bryan-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct OH_PackingOptionsForSequence OH_PackingOptionsForSequence
```

## Overview

OH_PackingOptionsForSequence is an image sequence encoding option struct encapsulated at the native layer. It cannot be manipulated directly; instead, functions shall be called to create and release the struct, and operate on its specific fields.

The [OH_PackingOptionsForSequence_Create](capi-image-packer-native-h.md#oh_packingoptionsforsequence_create) function is used to create the OH_PackingOptionsForSequence struct.

The [OH_PackingOptionsForSequence_Release](capi-image-packer-native-h.md#oh_packingoptionsforsequence_release) function is used to release the OH_PackingOptionsForSequence struct.

| Field Type| Field Name| Field Description|Operation Function| Function Description|
| -------- | -------- | -------- | -------- | -------- |
| uint32_t | frameCount | Number of frames.| [OH_PackingOptionsForSequence_GetFrameCount](capi-image-packer-native-h.md#oh_packingoptionsforsequence_getframecount) | Obtains the number of frames specified for encoding.|
| uint32_t | frameCount | Number of frames.| [OH_PackingOptionsForSequence_SetFrameCount](capi-image-packer-native-h.md#oh_packingoptionsforsequence_setframecount) | Sets the number of frames specified for encoding.|
| int32_t * | delayTimeList | Delay time array.| [OH_PackingOptionsForSequence_GetDelayTimeList](capi-image-packer-native-h.md#oh_packingoptionsforsequence_getdelaytimelist) | Obtains the delay time array of images during encoding.|
| int32_t * | delayTimeList | Delay time array.| [OH_PackingOptionsForSequence_SetDelayTimeList](capi-image-packer-native-h.md#oh_packingoptionsforsequence_setdelaytimelist) | Sets the delay time array of images during encoding.|
| uint32_t * | disposalTypes | Number of frames.| [OH_PackingOptionsForSequence_GetDisposalTypes](capi-image-packer-native-h.md#oh_packingoptionsforsequence_getdisposaltypes) | Obtains the disposal type array for image sequence encoding.|
| uint32_t * | disposalTypes | Number of frames.| [OH_PackingOptionsForSequence_SetDisposalTypes](capi-image-packer-native-h.md#oh_packingoptionsforsequence_setdisposaltypes) | Sets the disposal type array of images during encoding.|
| uint32_t | loopCount | Number of frames.| [OH_PackingOptionsForSequence_GetLoopCount](capi-image-packer-native-h.md#oh_packingoptionsforsequence_getloopcount) | Obtains the number of image loops during encoding.|
| uint32_t | loopCount | Number of frames.| [OH_PackingOptionsForSequence_SetLoopCount](capi-image-packer-native-h.md#oh_packingoptionsforsequence_setloopcount) | Sets the number of image loops during encoding. The value range is [0, 65535]. The value **0** indicates infinite looping. If this field is not set, the playback does not loop.|

**Since**: 18

**Related module**: [Image_NativeModule](capi-image-nativemodule.md)

**Header file**: [image_packer_native.h](capi-image-packer-native-h.md)
