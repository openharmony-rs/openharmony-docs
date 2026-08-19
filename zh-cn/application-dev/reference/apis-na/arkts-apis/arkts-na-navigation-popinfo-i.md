# PopInfo

下一个页面返回的回调信息载体。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface PopInfo--><!--Device-unnamed-export declare interface PopInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## info

```TypeScript
info: NavPathInfo
```

页面触发返回时的当前页面信息，系统自动获取填入，无需开发者传入。

**类型：** [NavPathInfo](arkts-na-navigation-navpathinfo-c.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PopInfo-info: NavPathInfo--><!--Device-PopInfo-info: NavPathInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## result

```TypeScript
result: Object
```

页面触发返回时的结果，开发者自定义对象。

**类型：** Object

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PopInfo-result: Object--><!--Device-PopInfo-result: Object-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

