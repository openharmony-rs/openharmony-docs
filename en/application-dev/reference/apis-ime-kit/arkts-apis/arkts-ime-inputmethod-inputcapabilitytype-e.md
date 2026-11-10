# InputCapabilityType

```TypeScript
export enum InputCapabilityType
```

Enumerates the input capability types. <br> <br>Used by [requestSystemInputCapability](arkts-ime-inputmethod-inputmethodcontroller-i.md#requestsysteminputcapability) to specify the system input capability to request.

**Since:** 26.1.0

<!--Device-inputMethod-export enum InputCapabilityType--><!--Device-inputMethod-export enum InputCapabilityType-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## TRANSLATION

```TypeScript
TRANSLATION = 0
```

Translation input capability. <br> <br>Usage scenarios: Used to request the input method to switch to translation mode. The current input method must be the system default input method; otherwise, the request is rejected with error 12800010.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-InputCapabilityType-TRANSLATION = 0--><!--Device-InputCapabilityType-TRANSLATION = 0-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework
