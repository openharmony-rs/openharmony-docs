# MediaQuery

class MediaQuery

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

<!--Device-unnamed-export class MediaQuery--><!--Device-unnamed-export class MediaQuery-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## matchMediaSync

```TypeScript
matchMediaSync(condition: string): mediaQuery.MediaQueryListener
```

Sets the media query criteria and returns the corresponding listening handle

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-MediaQuery-matchMediaSync(condition: string): mediaQuery.MediaQueryListener--><!--Device-MediaQuery-matchMediaSync(condition: string): mediaQuery.MediaQueryListener-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| condition | string | 是 | media conditions |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| mediaQuery.MediaQueryListener | the corresponding listening handle |

