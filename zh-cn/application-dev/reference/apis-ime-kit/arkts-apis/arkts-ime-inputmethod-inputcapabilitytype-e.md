# InputCapabilityType

```TypeScript
export enum InputCapabilityType
```

系统输入能力类型。用于[requestSystemInputCapability](arkts-ime-inputmethod-inputmethodcontroller-i.md#requestsysteminputcapability)指定请求的系统输入能力类型。

**起始版本：** 26.1.0

<!--Device-inputMethod-export enum InputCapabilityType--><!--Device-inputMethod-export enum InputCapabilityType-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## TRANSLATION

```TypeScript
TRANSLATION = 0
```

翻译输入能力。<br> <br>使用场景：用于请求输入法切换到翻译模式。当前输入法须为系统预置默认输入法，否则请求将被拒绝并返回12800010错误码。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InputCapabilityType-TRANSLATION = 0--><!--Device-InputCapabilityType-TRANSLATION = 0-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework
