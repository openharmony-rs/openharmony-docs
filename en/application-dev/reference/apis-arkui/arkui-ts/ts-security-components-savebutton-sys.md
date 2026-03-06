# SaveButton (System API)

<!--Kit: ArkUI-->
<!--Subsystem: Security-->
<!--Owner: @harylee-->
<!--Designer: @linshuqing; @hehehe-li-->
<!--Tester: @leiyuqian-->
<!--Adviser: @zengyawen-->

**SaveButton** is a security component that provides a save button. After it is integrated into your application and is used for the first time, a dialog box is displayed to ask for user authorization. If the user taps **Allow**, the application automatically obtains the permission to access the media library within a short period of time. No more dialog box is displayed for authorization. For API version 19 and earlier, the authorization duration is 10 seconds. For API version 20 and later, the authorization duration is 1 minute.


> **NOTE**
>
> This component is supported since API version 12. Updates will be marked with a superscript to indicate their earliest API version.
>
> This topic describes only system APIs provided by the module. For details about its public APIs, see [SaveButton](ts-security-components-savebutton.md).


## APIs

## SaveIconStyle

Enumerates icon styles of the **SaveButton** component.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Value| Description|
| -------- | -------- | -------- |
| PICTURE | 2 | Picture-attached icon.|
