# EventTargetInfo

手势识别器对应组件的信息。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class EventTargetInfo--><!--Device-unnamed-export declare class EventTargetInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getId

```TypeScript
getId(): string
```

返回当前组件的组件标识。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EventTargetInfo-getId(): string--><!--Device-EventTargetInfo-getId(): string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 当前组件的[组件标识]{ |

## getUniqueId

```TypeScript
getUniqueId(): int
```

返回当前组件的唯一id。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EventTargetInfo-getUniqueId(): int--><!--Device-EventTargetInfo-getUniqueId(): int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 当前组件的唯一id。 |

