# @ohos.inputMethod.ExtraConfig (Input Method Extension Information)
<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @illybyy-->
<!--Designer: @andeszhang-->
<!--Tester: @murphy1984-->
<!--Adviser: @zhang_yixin13-->

This module manages input method extension information. It enables the ArkUI editor to pass such information to the input method application when the input method is launched. After processing the extension information, the input method application can retrieve the details added by the host application. The total length of the information cannot exceed 32 KB.
> **NOTE**
>
>The initial APIs of this module are supported since API version 22. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { InputMethodExtraConfig } from '@kit.IMEKit';
```

## CustomValueType

type CustomValueType = number | string | boolean

Represents the extension information type. The specific type of the parameter depends on its functionality.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

| Type   | Description                |
| ------- | -------------------- |
| string  | String. |
| number  | Number.  |
| boolean | Boolean.|

## InputMethodExtraConfig

Represents the extension information of an input method.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

| Name  |Type   |Read-Only   |Optional   |Description   |
|---------|----------|----------|--------|--------|
| customSettings    |Record\<string, [CustomValueType](#customvaluetype)\>    | No  | No   |Input method extension information, which is used to store custom key-value pairs. These key-value pairs can be any configuration information related to the input method, such as user input habits, shortcut key settings, theme colors, and more. The settings are loaded when the input method application is bound to the system, delivering a personalized user experience. The total length of the information cannot exceed 32 KB.|
