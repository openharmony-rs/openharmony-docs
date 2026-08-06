# IMEClient

输入控件绑定输入法客户端类型。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

<!--Device-unnamed-declare interface IMEClient--><!--Device-unnamed-declare interface IMEClient-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## setExtraConfig

```TypeScript
setExtraConfig(config: InputMethodExtraConfig): void
```

设置输入法扩展信息。

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-IMEClient-setExtraConfig(config: InputMethodExtraConfig): void--><!--Device-IMEClient-setExtraConfig(config: InputMethodExtraConfig): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 输入法扩展信息。 |

## nodeId

```TypeScript
nodeId: number
```

当前输入控件的组件UniqueId。取值范围大于等于0。

**类型：** number

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-IMEClient-nodeId: number--><!--Device-IMEClient-nodeId: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

