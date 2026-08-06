# IMEClient

输入控件绑定输入法客户端类型。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

<!--Device-unnamed-export declare interface IMEClient--><!--Device-unnamed-export declare interface IMEClient-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## setExtraConfig

```TypeScript
setExtraConfig(config: InputMethodExtraConfig): void
```

设置输入法扩展信息。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IMEClient-setExtraConfig(config: InputMethodExtraConfig): void--><!--Device-IMEClient-setExtraConfig(config: InputMethodExtraConfig): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 输入法扩展信息。 |

## nodeId

```TypeScript
nodeId: long
```

当前输入控件的组件UniqueId。取值范围大于等于0。

**类型：** long

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IMEClient-nodeId: long--><!--Device-IMEClient-nodeId: long-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

