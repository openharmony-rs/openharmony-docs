# EmbeddedComponent

创建跨进程嵌入式组件，用于显示同包名或满足跨应用权限条件的EmbeddedUIExtensionAbility的UI。

## EmbeddedComponent

```TypeScript
EmbeddedComponent(
  loader: import('../api/@ohos.app.ability.Want').default,
  type: EmbeddedType
)
```

创建跨进程嵌入式组件，用于显示同包名或满足跨应用权限条件的EmbeddedUIExtensionAbility的UI。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| loader | import('../api/@ohos.app.ability.Want').default | 是 | 表示要加载的EmbeddedUIExtensionAbility。 |
| type | [EmbeddedType](../arkts-apis/arkts-arkui-embeddedtype-e.md) | 是 | 提供方的类型。 |

## EmbeddedComponent

```TypeScript
EmbeddedComponent(
  loader: import('../api/@ohos.app.ability.Want').default,
  type: EmbeddedType,
  options?: EmbeddedOptions
)
```

创建跨进程嵌入式组件，用于显示同包名或满足跨应用权限条件的EmbeddedUIExtensionAbility的UI。相对于API version 12的接口，新增options参数用于传递构造参数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| loader | import('../api/@ohos.app.ability.Want').default | 是 | 要加载的EmbeddedUIExtensionAbility。 |
| type | [EmbeddedType](../arkts-apis/arkts-arkui-embeddedtype-e.md) | 是 | 提供方的类型。 |
| options | [EmbeddedOptions](arkts-arkui-embeddedoptions-i.md) | 否 | 嵌入式组件的可选配置项，用于设置占位符、DPI跟随策略、窗口模式跟随策略等。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [EmbeddedOptions](arkts-arkui-embeddedoptions-i.md) | 用于在EmbeddedComponent创建时传递可选的构造参数。 |
| [TerminationInfo](arkts-arkui-terminationinfo-i.md) | 用于表示被拉起的EmbeddedUIExtensionAbility的返回结果。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [EmbeddedDpiFollowStrategy](arkts-arkui-embeddeddpifollowstrategy-e.md) | DPI跟随策略，用于设置DPI，使其能够跟随宿主或EmbeddedUIExtensionAbility。例如，当EmbeddedUIExtensionAbility需要与宿主应用保持视觉一致性时，可选择跟随宿主DPI；当EmbeddedUIExtensionAbility需要独立适配自身资源的DPI配置时，可选择跟随EmbeddedUIExtensionAbility DPI。 |
| [EmbeddedWindowModeFollowStrategy](arkts-arkui-embeddedwindowmodefollowstrategy-e.md) | 窗口模式跟随策略，用于设置窗口模式跟随宿主或EmbeddedUIExtensionAbility。例如，当EmbeddedUIExtensionAbility需要与宿主应用保持一致的窗口模式（如全屏、分屏）时，可选择跟随宿主；当EmbeddedUIExtensionAbility需要独立控制窗口模式时，可选择跟随EmbeddedUIExtensionAbility。 |
