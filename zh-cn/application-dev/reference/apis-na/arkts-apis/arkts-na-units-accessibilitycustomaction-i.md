# AccessibilityCustomAction

自定义无障碍操作接口。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare interface AccessibilityCustomAction--><!--Device-unnamed-export declare interface AccessibilityCustomAction-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## name

```TypeScript
name: ResourceStr
```

自定义操作的名称，用于标识和绑定操作回调。 **说明：** 名称的文本长度需在128字节以内，超出部分将被截断。

**类型：** [ResourceStr](arkts-na-resourcestr-t.md)

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AccessibilityCustomAction-name: ResourceStr--><!--Device-AccessibilityCustomAction-name: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onAction

```TypeScript
onAction: VoidCallback
```

处理自定义操作的回调。

**类型：** [VoidCallback](arkts-na-voidcallback-t.md)

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AccessibilityCustomAction-onAction: VoidCallback--><!--Device-AccessibilityCustomAction-onAction: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

