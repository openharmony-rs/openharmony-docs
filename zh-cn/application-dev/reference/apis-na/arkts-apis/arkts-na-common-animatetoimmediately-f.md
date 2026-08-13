# animateToImmediately

## animateToImmediately

```TypeScript
export declare function animateToImmediately(value: AnimateParam, processor: VoidCallback): void
```

Define animation functions for immediate distribution. This interface depends on the UI context and cannot be used when the UI context is unclear. It is recommended to use animateToImmediately to explicitly specify the UI context.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function animateToImmediately(value: AnimateParam, processor: VoidCallback): void--><!--Device-unnamed-export declare function animateToImmediately(value: AnimateParam, processor: VoidCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [AnimateParam](arkts-na-common-animateparam-i.md) | 是 | Set animation effect parameters. |
| processor | [VoidCallback](../../apis-arkui/arkts-apis/arkts-arkui-voidcallback-t.md) | 是 | Specify the closure function that displays dynamic effects, and the system will automatically insert transition animations for state changes caused by the closure function. |

