# AccessibilityActionInterceptCallback

```TypeScript
export declare type AccessibilityActionInterceptCallback = (action: AccessibilityAction) => AccessibilityActionInterceptResult
```

Defines the callback type used in accessibility action intercept. The value of action indicates the accessibility action type.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare type AccessibilityActionInterceptCallback = (action: AccessibilityAction) => AccessibilityActionInterceptResult--><!--Device-unnamed-export declare type AccessibilityActionInterceptCallback = (action: AccessibilityAction) => AccessibilityActionInterceptResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| action | [AccessibilityAction](arkts-na-common-accessibilityaction-e.md) | 是 | the enum of accessibility action type. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AccessibilityActionInterceptResult](arkts-na-common-accessibilityactioninterceptresult-e.md) | the result of continuing to execute the action or interrupting it or bubbling up |

