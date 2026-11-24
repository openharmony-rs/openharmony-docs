# Camera_OutputCapability

```c
typedef struct Camera_OutputCapability {...} Camera_OutputCapability
```

## Overview

The struct describes the camera output capability.

<!--Device-struct Camera_OutputCapability {...}--><!--Device-struct Camera_OutputCapability {...}-End-->

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

**Related module**: [OH_Camera](capi-camera-kit-oh-camera.md)

**Header file**: [camera.h](capi-camera-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [Camera_Profile*](capi-oh-camera-camera-profile.md)* previewProfiles | Double pointer to the list of preview profiles.<br><!--Device-Camera_Profile** previewProfiles--><!--Device-Camera_Profile** previewProfiles-End--> |
| uint32_t previewProfilesSize | Size of the preview profiles.<br><!--Device-uint32_t previewProfilesSize--><!--Device-uint32_t previewProfilesSize-End--> |
| [Camera_Profile*](capi-oh-camera-camera-profile.md)* photoProfiles | Double pointer to the list of photo profiles.<br> In the configuration file, **size** is set to the width and height of the camera resolution, not the actual width and height of an output image.<br><!--Device-Camera_Profile** photoProfiles--><!--Device-Camera_Profile** photoProfiles-End--> |
| uint32_t photoProfilesSize | Size of the photo profiles.<br><!--Device-uint32_t photoProfilesSize--><!--Device-uint32_t photoProfilesSize-End--> |
| [Camera_VideoProfile*](capi-oh-camera-camera-videoprofile.md)* videoProfiles | Double pointer to the list of video profiles.<br><!--Device-Camera_VideoProfile** videoProfiles--><!--Device-Camera_VideoProfile** videoProfiles-End--> |
| uint32_t videoProfilesSize | Size of the video profiles.<br><!--Device-uint32_t videoProfilesSize--><!--Device-uint32_t videoProfilesSize-End--> |
| [Camera_MetadataObjectType](capi-camera-h.md#camera_metadataobjecttype)** supportedMetadataObjectTypes | Double pointer to the list of the metadata object types supported.<br><!--Device-Camera_MetadataObjectType** supportedMetadataObjectTypes--><!--Device-Camera_MetadataObjectType** supportedMetadataObjectTypes-End--> |
| uint32_t metadataProfilesSize | Size of the metadata profiles.<br><!--Device-uint32_t metadataProfilesSize--><!--Device-uint32_t metadataProfilesSize-End--> |


