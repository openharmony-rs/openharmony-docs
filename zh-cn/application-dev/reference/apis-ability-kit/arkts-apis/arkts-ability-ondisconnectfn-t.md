# OnDisconnectFn

```TypeScript
type OnDisconnectFn = (elementName: ElementName) => void
```

与指定的后台服务成功断开连接时，会触发该回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-type OnDisconnectFn = (elementName: ElementName) => void--><!--Device-unnamed-type OnDisconnectFn = (elementName: ElementName) => void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elementName | [ElementName](arkts-ability-elementname-i.md) | 是 | 目标Ability的elementName。 |

