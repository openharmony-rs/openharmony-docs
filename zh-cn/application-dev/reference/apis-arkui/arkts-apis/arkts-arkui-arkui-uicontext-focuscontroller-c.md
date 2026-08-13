# FocusController

提供控制焦点的能力，如清除、移动和激活焦点等功能。 > **说明：** > > 以下API需先使用UIContext中的[getFocusController()](arkts-arkui-arkui-uicontext-uicontext-c.md#getFocusController)方法获取FocusController实例，再通过该实例调用对应方法。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-unnamed-export class FocusController--><!--Device-unnamed-export class FocusController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## activate

```TypeScript
activate(isActive: boolean, autoInactive?: boolean): void
```

设置当前界面的[焦点激活态](../../../ui/arkts-common-events-focus-event.md)。

**起始版本：** 14

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为14。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-FocusController-activate(isActive: boolean, autoInactive?: boolean): void--><!--Device-FocusController-activate(isActive: boolean, autoInactive?: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isActive | boolean | 是 | 设置是否进入/退出焦点激活态。&lt;br/&gt;true表示设置进入焦点激活态，false表示设置退出焦点激活态。 |
| autoInactive | boolean | 否 | 设置焦点激活态退出逻辑。&lt;br/&gt;为true时，会自动在触摸事件、鼠标事件触发时退出，为false时，仅受开发者API控制。&lt;br/&gt;默认值：true |

## clearFocus

```TypeScript
clearFocus(): void
```

清除焦点，将焦点强制转移到页面根容器节点，焦点链路上其他节点失焦。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FocusController-clearFocus(): void--><!--Device-FocusController-clearFocus(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isActive

```TypeScript
isActive(): boolean
```

返回UI实例的焦点激活态。 焦点激活态可参考[基础概念：焦点激活态](../../../ui/arkts-common-events-focus-event.md#基础概念)。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-FocusController-isActive(): boolean--><!--Device-FocusController-isActive(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回UI实例的焦点激活态。true表示当前进入焦点激活态，false表示当前已退出焦点激活态。 |

## requestFocus

```TypeScript
requestFocus(key: string): void
```

通过组件的id将焦点转移到组件树对应的实体节点，当前帧生效。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FocusController-requestFocus(key: string): void--><!--Device-FocusController-requestFocus(key: string): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 节点对应的组件标识。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [150002](../errorcode-focus.md#150002-祖先节点无法获得焦点) | This component has an unfocusable ancestor. |
| [150003](../errorcode-focus.md#150003-节点不存在) | the component is not on tree or does not exist. |
| [150001](../errorcode-focus.md#150001-节点无法获得焦点) | the component cannot be focused. |

## setAutoFocusTransfer

```TypeScript
setAutoFocusTransfer(isAutoFocusTransfer: boolean): void
```

设置页面切换时，新的页面是否需要主动获取焦点。

**起始版本：** 14

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为14。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-FocusController-setAutoFocusTransfer(isAutoFocusTransfer: boolean): void--><!--Device-FocusController-setAutoFocusTransfer(isAutoFocusTransfer: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isAutoFocusTransfer | boolean | 是 | 设置页面切换时，新的页面是否需要主动获取焦点，例如[Router](arkts-router.md#@ohos.router)、 Navigation、Menu、Dialog、 Popup等。true表示需要主动获取焦点，false表示不需要主动获取焦点。默认值为true。 |

## setKeyProcessingMode

```TypeScript
setKeyProcessingMode(mode: KeyProcessingMode): void
```

设置按键事件处理的优先级。

**起始版本：** 15

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为15。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-FocusController-setKeyProcessingMode(mode: KeyProcessingMode): void--><!--Device-FocusController-setKeyProcessingMode(mode: KeyProcessingMode): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [KeyProcessingMode](arkts-arkui-keyprocessingmode-e.md) | 是 | 按键处理模式。 |

