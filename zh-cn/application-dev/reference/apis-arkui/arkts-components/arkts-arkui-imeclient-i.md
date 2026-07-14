# IMEClient

输入控件绑定输入法客户端类型。

**起始版本：** 20

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## setExtraConfig

```TypeScript
setExtraConfig(config: InputMethodExtraConfig): void
```

设置输入法扩展信息。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | InputMethodExtraConfig | 是 | 输入法扩展信息。 |

## nodeId

```TypeScript
nodeId: number
```

当前输入控件的组件UniqueId。取值范围大于等于0。

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

