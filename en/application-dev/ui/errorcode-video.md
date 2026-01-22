# Video Component Error Codes
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @sd-wu-->
<!--Designer: @sunbees-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about media error codes, see [Media Error Codes](../apis-media-kit/errorcode-media.md). For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 103601 Failed to Create the Player

**Error Message**

Failed to create the media player.

**Description**

This error code is reported when the player fails to be created.

**Possible Causes**

The media service does not exist, or the memory is insufficient.

**Solution**

Destroy the current instance and re-create an instance. If re-creation fails, stop the related operations.

## 103602 Invalid Video Resource

**Error Message**

Not a valid source.

**Description**

This error code is reported when the configured video source is invalid.

**Possible Causes**

The system cannot locate the resource file, or the resource file is corrupted.

**Solution**

Ensure that the resource file exists and is intact, and then reset the video source for the **Video** component.
