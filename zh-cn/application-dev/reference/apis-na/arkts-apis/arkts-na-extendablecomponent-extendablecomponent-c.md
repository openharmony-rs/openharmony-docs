# ExtendableComponent

可扩展组件，是自定义组件和自定义对话框的基类。

**继承/实现关系：** ExtendableComponent implements [LifeCycle](arkts-na-extendablecomponent-lifecycle-i.md#LifeCycle), [IVariableOwner](arkts-na-decorator-ivariableowner-i.md#IVariableOwner)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare abstract class ExtendableComponent--><!--Device-unnamed-export declare abstract class ExtendableComponent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getDialogController

```TypeScript
getDialogController(): promptAction.DialogController | undefined
```

The dialog controller of the custom component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableComponent-getDialogController(): promptAction.DialogController | undefined--><!--Device-ExtendableComponent-getDialogController(): promptAction.DialogController | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| promptAction.DialogController | The controller of dialog, or undefined if the custom component does not display in the dialog. |

## getUIContext

```TypeScript
getUIContext(): UIContext
```

获取UIContext对象。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableComponent-getUIContext(): UIContext--><!--Device-ExtendableComponent-getUIContext(): UIContext-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [UIContext](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md) | 返回UIContext实例对象。在异步调用的回调方法中使用该接口，或者该接口的起始调用不在当前页面时，可能导致接口调用发生在自定义组件销毁之后，返回undefined。 |

## getUniqueId

```TypeScript
getUniqueId(): int
```

获取当前组件的UniqueId。UniqueId为系统为每个组件分配的Id，可保证当前应用中的唯一性。若在组件对应的节点未创建或已销毁时获取，返回无效UniqueId：-1。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableComponent-getUniqueId(): int--><!--Device-ExtendableComponent-getUniqueId(): int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回当前Component的UniqueId。 |

## onWillApplyTheme

```TypeScript
onWillApplyTheme(theme: Theme): void
```

onWillApplyTheme函数用于获取当前组件上下文的Theme对象，在创建自定义组件的新实例后，在执行其build()函数之前执行。允许在onWillApplyTheme函数中改变状态变量， 更改将在后续执行build()函数中生效。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableComponent-onWillApplyTheme(theme: Theme): void--><!--Device-ExtendableComponent-onWillApplyTheme(theme: Theme): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| theme | [Theme](../../apis-arkui/arkts-apis/arkts-arkui-arkui-theme-theme-i.md) | 是 | 自定义组件当前生效的Theme对象。 |

## queryNavDestinationInfo

```TypeScript
queryNavDestinationInfo(): NavDestinationInfo | undefined
```

查询自定义组件所属的NavDestination信息，仅当自定义组件在NavDestination的内部时才生效。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableComponent-queryNavDestinationInfo(): NavDestinationInfo | undefined--><!--Device-ExtendableComponent-queryNavDestinationInfo(): NavDestinationInfo | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NavDestinationInfo](../../apis-arkui/arkts-components/arkts-arkui-navdestinationinfo-t.md) | The navigation destination information, or undefined if it is not available. |

## queryNavDestinationInfo

```TypeScript
queryNavDestinationInfo(isInner: boolean | undefined): NavDestinationInfo | undefined
```

查询当前自定义组件距离最近的NavDestination信息（要求该NavDestination是Navigation的导航页或子页），isInner为true表示向内查找，false表示向外查找。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableComponent-queryNavDestinationInfo(isInner: boolean | undefined): NavDestinationInfo | undefined--><!--Device-ExtendableComponent-queryNavDestinationInfo(isInner: boolean | undefined): NavDestinationInfo | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isInner | boolean \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NavDestinationInfo](../../apis-arkui/arkts-components/arkts-arkui-navdestinationinfo-t.md) | The navigation destination information, or undefined if it is not available. |

## queryNavigationInfo

```TypeScript
queryNavigationInfo(): NavigationInfo | undefined
```

查询自定义组件所属的Navigation信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableComponent-queryNavigationInfo(): NavigationInfo | undefined--><!--Device-ExtendableComponent-queryNavigationInfo(): NavigationInfo | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NavigationInfo](../../apis-arkui/arkts-components/arkts-arkui-navigationinfo-t.md) | The navigation information, or undefined if it is not available |

## queryRouterPageInfo

```TypeScript
queryRouterPageInfo(): RouterPageInfo | undefined
```

获取RouterPageInfo实例对象。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableComponent-queryRouterPageInfo(): RouterPageInfo | undefined--><!--Device-ExtendableComponent-queryRouterPageInfo(): RouterPageInfo | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RouterPageInfo](../../apis-arkui/arkts-components/arkts-arkui-routerpageinfo-t.md) | The router page information, or undefined if it is not available. |

