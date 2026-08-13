# FocusController

class FocusController

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare class FocusController--><!--Device-unnamed-export declare class FocusController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## activate

```TypeScript
activate(isActive: boolean, autoInactive?: boolean): void
```

Activate focus style.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FocusController-activate(isActive: boolean, autoInactive?: boolean): void--><!--Device-FocusController-activate(isActive: boolean, autoInactive?: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isActive | boolean | 是 | activate/deactivate the focus style. |
| autoInactive | boolean | 否 | deactivate the focus style when touch event or mouse event triggers, the default value is true. |

## clearFocus

```TypeScript
clearFocus(): void
```

clear focus to the root container.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FocusController-clearFocus(): void--><!--Device-FocusController-clearFocus(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isActive

```TypeScript
isActive(): boolean
```

获取焦点样式是否处于激活态。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FocusController-isActive(): boolean--><!--Device-FocusController-isActive(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Whether the focus style is active. |

## requestFocus

```TypeScript
requestFocus(key: string): void
```

request focus to the specific component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FocusController-requestFocus(key: string): void--><!--Device-FocusController-requestFocus(key: string): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | the inspector key of the component. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [150002](../../apis-arkui/errorcode-focus.md#150002-祖先节点无法获得焦点) | This component has an unfocusable ancestor. |
| [150003](../../apis-arkui/errorcode-focus.md#150003-节点不存在) | the component is not on tree or does not exist. |
| [150001](../../apis-arkui/errorcode-focus.md#150001-节点无法获得焦点) | the component cannot be focused. |

## setAutoFocusTransfer

```TypeScript
setAutoFocusTransfer(isAutoFocusTransfer: boolean): void
```

设置是否开启自动焦点转移。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FocusController-setAutoFocusTransfer(isAutoFocusTransfer: boolean): void--><!--Device-FocusController-setAutoFocusTransfer(isAutoFocusTransfer: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isAutoFocusTransfer | boolean | 是 | A Boolean value that indicates whether autofocus transfer is enabled. |

## setKeyProcessingMode

```TypeScript
setKeyProcessingMode(mode: KeyProcessingMode): void
```

设置组件无法处理按键事件时的按键事件处理优先级。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FocusController-setKeyProcessingMode(mode: KeyProcessingMode): void--><!--Device-FocusController-setKeyProcessingMode(mode: KeyProcessingMode): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [KeyProcessingMode](../../apis-arkui/arkts-apis/arkts-arkui-keyprocessingmode-e.md) | 是 | Key processing mode. |

