# AutoFillTriggerType (System API)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @hanchen45-->
<!--Designer: @ccllee1-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

This module specifies how the autofill service is triggered, based on different user gestures.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 23. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The APIs of this module can be used only in the stage model.
> - The APIs provided by this module are system APIs.

## Modules to Import

```ts
import { autoFillManager } from '@kit.AbilityKit';
```

## AutoFillTriggerType

Defines the trigger type for launching the autofill service, with three possible values: **AUTO_REQUEST**, **MANUAL_REQUEST**, and **PASTE_REQUEST**. This enumeration is used by the system API [FillRequest.triggerType](./js-apis-inner-application-autoFillRequest-sys.md#fillrequest).

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.AbilityCore

| Name          | Value | Description                              |
| -------------- | --- | --------------------------------- |
| AUTO_REQUEST | 0 | Automatically triggers the autofill service when a [TextInput](../../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md) component gains focus.|
| MANUAL_REQUEST | 1 | Manually triggers the autofill service by long-pressing any input component to bring up a secondary menu and selecting autofill.|
| PASTE_REQUEST | 2 | Triggers the autofill service via paste by long-pressing a username or password in the password vault to select secure copy, long-pressing any input component to bring up a secondary menu, and selecting paste.|
