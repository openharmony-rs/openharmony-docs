# Security Component Universal Attributes (System API)

<!--Kit: ArkUI-->
<!--Subsystem: Security-->
<!--Owner: @harylee-->
<!--Designer: @linshuqing; @hehehe-li-->
<!--Tester: @leiyuqian-->
<!--Adviser: @zengyawen-->

Universal attributes of security components are basic attributes applicable to all security components.

> **NOTE**
>
> This component is supported since API version 10. Updates will be marked with a superscript to indicate their earliest API version.
>
> This topic describes only system APIs provided by the module. For details about its public APIs, see [Security Component Universal Attributes](ts-securitycomponent-attributes.md).


## key

key(value: string): T

Unique ID you assigned for the component. When this attribute is used in conjunction with [id](ts-securitycomponent-attributes.md#id15), the last assigned value takes effect. You are advised to set only **id**.

This API is used only for test purposes.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Parameter| Type                  | Mandatory| Description                  |
|------------|------|-------|---------|
| value | string |Yes|Unique ID you assigned for the component.<br>The default value is an empty string.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Attributes of the security component.|
