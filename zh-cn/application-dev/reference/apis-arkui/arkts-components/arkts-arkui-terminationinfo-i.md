# TerminationInfo

用于表示被拉起的EmbeddedUIExtensionAbility的返回结果。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## code

```TypeScript
code: number
```

被拉起的EmbeddedUIExtensionAbility退出时返回的结果码，由terminateSelfWithResult或者terminateSelf被调用时传入的数据决定。 若通过terminateSelf退出，code取默认值0。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## want

```TypeScript
want?: import('../api/@ohos.app.ability.Want').default
```

被拉起的EmbeddedUIExtensionAbility退出时返回的数据。若通过terminateSelf退出，则该值为undefined。

**类型：** import('../api/@ohos.app.ability.Want').default

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
