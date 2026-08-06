# TerminationInfo（系统接口）

用于表示被拉起的UIExtensionAbility通过调用terminateSelfWithResult或者terminateSelf正常退出时的返回结果。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

<!--Device-unnamed-declare interface TerminationInfo--><!--Device-unnamed-declare interface TerminationInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## code

```TypeScript
code: number
```

被拉起的UIExtensionAbility退出时返回的结果码，返回的结果码由terminateSelfWithResult或者terminateSelf被调用时传入的数据决定。 若通过terminateSelf退出，code取默认值0。

**类型：** number

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TerminationInfo-code: number--><!--Device-TerminationInfo-code: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## want

```TypeScript
want?: import('../api/@ohos.app.ability.Want').default
```

被拉起的UIExtensionAbility退出时返回的数据。默认值为undefined。

**类型：** import('../api/@ohos.app.ability.Want').default

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TerminationInfo-want?: import('../api/@ohos.app.ability.Want').default--><!--Device-TerminationInfo-want?: import('../api/@ohos.app.ability.Want').default-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

