# @ohos.inputMethod.ExtraConfig(Input Method Extension Information)

This module manages input method extension information. It enables the ArkUI editor to pass such information to the
 input method application when the input method is launched. After processing the extension information,
 the input method application can retrieve the details added by the host application.
 The total length of the information cannot exceed 32 KB.<br>
 <br> > **NOTE**
 <br> >
 <br> >The initial APIs of this module are supported since API version 22.
 Newly added APIs will be marked with a superscript to indicate their earliest API version.



## Modules to Import

```TypeScript
import { InputMethodExtraConfig } from '@kit.IMEKit';
```

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [InputMethodExtraConfig](arkts-ime-inputmethod-extraconfig-inputmethodextraconfig-i.md) | Represents the extension information of an input method. |

### Types

| Name | Description |
| --- | --- |
| [CustomValueType](arkts-ime-customvaluetype-t.md) | Represents the extension information type. The specific type of the parameter depends on its functionality. |
