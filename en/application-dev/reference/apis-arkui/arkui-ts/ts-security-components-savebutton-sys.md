# SaveButton (System API)

<!--Kit: ArkUI-->
<!--Subsystem: Security-->
<!--Owner: @harylee-->
<!--Designer: @linshuqing; @hehehe-li-->
<!--Tester: @leiyuqian-->
<!--Adviser: @zengyawen-->

## Overview

**SaveButton** is a system API for the save security control. It applies to scenarios where apps need temporary media library access permissions to save images or videos, such as saving images to albums and exporting media content.

After the **SaveButton** component is integrated into an app, a confirmation dialog will appear when the user taps the component for the first time. If the user allows access, the app obtains temporary authorization to call media library APIs. For related APIs, see [Interface (PhotoAccessHelper)](../../apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAccessHelper.md). If the user denies access or dismisses the dialog, authorization will not be granted for this operation. No more dialog box is displayed for authorization.

For API version 19 and earlier, the authorization duration is 10 seconds. For API version 20 and later, the authorization duration is 1 minute.

You need to call media library APIs to obtain file handles and complete temporary-authorized operations such as creating media resources within the authorization period. After authorization expires, existing file handles acquired during the valid period remain available for read and write operations.

> **NOTE**
>
> This component is supported since API version 12. Updates will be marked with a superscript to indicate their earliest API version.
>
> This topic describes only system APIs provided by the module. For details about its public APIs, see [SaveButton](ts-security-components-savebutton.md).

## Key Classes and APIs

### Key Enums

- [SaveIconStyle](#saveiconstyle): Enumeration of icon styles for the save button. Extends icon styles for the system API.

## SaveIconStyle

Enumerates icon styles of the **SaveButton** component.

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Value| Description|
| -------- | -------- | -------- |
| PICTURE | 2 | Picture-attached icon.|
