# MediaQuery

class MediaQuery

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class MediaQuery--><!--Device-unnamed-export declare class MediaQuery-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## matchMediaSync

```TypeScript
matchMediaSync(condition: string): mediaQuery.MediaQueryListener
```

Sets the media query criteria and returns the corresponding listening handle

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

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

