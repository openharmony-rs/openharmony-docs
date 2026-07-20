# EmbeddedComponent

定义EmbeddedComponent组件。


## EmbeddedComponent

```TypeScript
EmbeddedComponent(
    loader: import('../api/type: EmbeddedType
  )
```

构造EmbeddedComponent。<br/>在使用EmbeddedComponent时调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-EmbeddedComponentInterface-(
    loader: import('../api/type: EmbeddedType
  ): EmbeddedComponentAttribute--><!--Device-EmbeddedComponentInterface-(
    loader: import('../api/type: EmbeddedType
  ): EmbeddedComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| loader | import('../api/@ohos.app.ability.Want').default | 是 | 表示初始化参数  |
| type | [EmbeddedType](../arkts-apis/arkts-arkui-embeddedtype-e.md) | 是 | 表示EmbeddedComponent的类型  |

## EmbeddedComponent

```TypeScript
EmbeddedComponent(
    loader: import('../api/type: EmbeddedType,
    options?: EmbeddedOptions
  )
```

构造EmbeddedComponent。<br/>在使用EmbeddedComponent时调用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-EmbeddedComponentInterface-(
    loader: import('../api/type: EmbeddedType,
    options?: EmbeddedOptions
  ): EmbeddedComponentAttribute--><!--Device-EmbeddedComponentInterface-(
    loader: import('../api/type: EmbeddedType,
    options?: EmbeddedOptions
  ): EmbeddedComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| loader | import('../api/@ohos.app.ability.Want').default | 是 | 表示初始化参数  |
| type | [EmbeddedType](../arkts-apis/arkts-arkui-embeddedtype-e.md) | 是 | 表示EmbeddedComponent的类型  |
| options | [EmbeddedOptions](arkts-arkui-embeddedoptions-i.md) | 否 | EmbeddedComponent的构造配置  |

## 汇总

- [EmbeddedOptions](arkts-arkui-embeddedcomponent-embeddedoptions-i.md)
- [TerminationInfo](arkts-arkui-embeddedcomponent-terminationinfo-i.md)
- [EmbeddedDpiFollowStrategy](arkts-arkui-embeddedcomponent-embeddeddpifollowstrategy-e.md)
- [EmbeddedWindowModeFollowStrategy](arkts-arkui-embeddedcomponent-embeddedwindowmodefollowstrategy-e.md)
