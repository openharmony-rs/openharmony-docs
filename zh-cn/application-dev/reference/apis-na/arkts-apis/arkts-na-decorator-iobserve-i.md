# IObserve

Define IObserve interface.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface IObserve--><!--Device-unnamed-export declare interface IObserve-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## shouldAddRef

```TypeScript
shouldAddRef(iObjectsRenderId: RenderIdType): boolean
```

Collect the dependancy for UI component with state variable

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IObserve-shouldAddRef(iObjectsRenderId: RenderIdType): boolean--><!--Device-IObserve-shouldAddRef(iObjectsRenderId: RenderIdType): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| iObjectsRenderId | [RenderIdType](arkts-na-renderidtype-t.md) | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean |  |

## renderingComponent

```TypeScript
readonly renderingComponent: int
```

Rendering component.

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IObserve-readonly renderingComponent: int--><!--Device-IObserve-readonly renderingComponent: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## renderingId

```TypeScript
readonly renderingId: RenderIdType
```

Rendering component id.

**类型：** [RenderIdType](arkts-na-renderidtype-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IObserve-readonly renderingId: RenderIdType--><!--Device-IObserve-readonly renderingId: RenderIdType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

