# CompatibleInitCallback

```TypeScript
export type CompatibleInitCallback = (parent: ESValue) => CompatibleComponentInfo
```

初始化占位组件的回调函数类型。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type CompatibleInitCallback = (parent: ESValue) => CompatibleComponentInfo--><!--Device-unnamed-export type CompatibleInitCallback = (parent: ESValue) => CompatibleComponentInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| parent | ESValue | 是 | the parent of compatible custom component |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CompatibleComponentInfo](arkts-na-interop-compatiblecomponentinfo-i.md) | 占位组件的信息。 |

