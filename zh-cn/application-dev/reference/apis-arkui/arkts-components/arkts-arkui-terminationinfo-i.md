# TerminationInfo

用于表示被拉起的EmbeddedUIExtensionAbility的返回结果。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-unnamed-declare interface TerminationInfo--><!--Device-unnamed-declare interface TerminationInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## code

```TypeScript
code: number
```

被拉起的EmbeddedUIExtensionAbility退出时返回的结果码，由terminateSelfWithResult或者terminateSelf被调用时传入的数据决定。 若通过terminateSelf退出，code取默认值0。

**类型：** number

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TerminationInfo-code: number--><!--Device-TerminationInfo-code: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## want

```TypeScript
want?: import('../api/@ohos.app.ability.Want').default
```

被拉起的EmbeddedUIExtensionAbility退出时返回的数据。若通过terminateSelf退出，则该值为undefined。

**类型：** import('../api/@ohos.app.ability.Want').default

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TerminationInfo-want?: import('../api/@ohos.app.ability.Want').default--><!--Device-TerminationInfo-want?: import('../api/@ohos.app.ability.Want').default-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

