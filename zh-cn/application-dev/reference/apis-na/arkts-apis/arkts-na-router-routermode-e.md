# RouterMode

路由跳转模式。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-router-export enum RouterMode--><!--Device-router-export enum RouterMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Standard

```TypeScript
Standard
```

Default route mode. The page will be added to the top of the page stack.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RouterMode-Standard--><!--Device-RouterMode-Standard-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Single

```TypeScript
Single
```

Single route mode. If the target page already has the same url page in the page stack, the same url page closest to the top of the stack will be moved to the top of the stack. If the target page url does not exist in the page stack, route will use default route mode.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RouterMode-Single--><!--Device-RouterMode-Single-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

