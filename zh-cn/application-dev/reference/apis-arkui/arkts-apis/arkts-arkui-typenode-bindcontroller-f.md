# bindController

## bindController

```TypeScript
export function bindController(node: FrameNode, controller: TextController, nodeType: 'Text'): void
```

将文本控制器[TextController](arkts-arkui-text-textcontroller-c.md#TextController)绑定到[Text](arkts-arkui-typenode-text-t.md#Text)节点。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言
访问，则抛出异常。该接口不支持声明式方式创建的节点。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | FrameNode | 是 | 绑定文本控制器的目标节点。 |
| controller | TextController | 是 | 文本控制器。 |
| nodeType | 'Text' | 是 | 绑定输入框控制器的目标节点的节点类型为Text。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100023](../../errorcode-universal.md#100023-Parameter) | Parameter error. Possible causes: 1. The component type of the node<br/>is incorrect. 2. The node is null or undefined. 3. The controller is null or undefined. |
| [100021](../../errorcode-universal.md#100021-The) | The FrameNode is not modifiable. |


## bindController

```TypeScript
export function bindController(node: FrameNode, controller: SwiperController, nodeType: 'Swiper'): void
```

将控制器[SwiperController](arkts-arkui-swiper-swipercontroller-c.md#SwiperController)绑定到[Swiper](arkts-arkui-typenode-swiper-t.md#Swiper)节点。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果
不支持跨语言访问，则抛出异常。该接口不支持声明式方式创建的节点。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | FrameNode | 是 | 绑定控制器的目标节点。 |
| controller | SwiperController | 是 | Swiper容器组件的控制器。 |
| nodeType | 'Swiper' | 是 | 绑定控制器的目标节点的节点类型为Swiper。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100023](../../errorcode-universal.md#100023-Parameter) | Parameter error. Possible causes: 1. The component type of the node<br/>is incorrect. 2. The node is null or undefined. 3. The controller is null or undefined. |
| [100021](../../errorcode-universal.md#100021-The) | The FrameNode is not modifiable. |


## bindController

```TypeScript
function bindController(node: FrameNode, controller: Scroller, nodeType: 'Scroll'): void
```

将滚动控制器[Scroller](arkts-arkui-scroll-scroller-c.md#Scroller)绑定到[Scroll](arkts-arkui-typenode-scroll-t.md#Scroll)节点。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则抛出异
常。从API version 26.0.0开始，该接口支持声明式方式创建的节点，API version 26.0.0以下版本不支持。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | FrameNode | 是 | 绑定滚动控制器的目标节点。 |
| controller | Scroller | 是 | the controller which is bind to 绑定滚动控制器的目标节点。 |
| nodeType | 'Scroll' | 是 | 绑定滚动控制器的目标节点的节点类型为Scroll。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. the type of the node is error.<br/>2. the node is null or undefined. |
| [100021](../../errorcode-universal.md#100021-The) | The FrameNode is not modifiable. Introduced in API version 15 and will not<br/>be threw above API version 24.&lt;br&gt;**适用版本：** 15 - 24 |


## bindController

```TypeScript
export function bindController(node: FrameNode, controller: Scroller, nodeType: 'List'): void
```

将滚动控制器[Scroller](arkts-arkui-scroll-scroller-c.md#Scroller)绑定到[List](arkts-arkui-typenode-list-t.md#List)节点。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则抛出异常。从
API version 26.0.0开始，该接口支持声明式方式创建的节点，API version 26.0.0以下版本不支持。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | FrameNode | 是 | 绑定滚动控制器的目标节点。 |
| controller | Scroller | 是 | 滚动控制器。 |
| nodeType | 'List' | 是 | 绑定滚动控制器的目标节点的节点类型为List。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100023](../../errorcode-universal.md#100023-Parameter) | Parameter error. Possible causes: 1. The component type of the node is<br/>incorrect. 2. The node is null or undefined. 3. The controller is null or undefined. |
| [100021](../../errorcode-universal.md#100021-The) | The FrameNode is not modifiable. Introduced in API version 20 and will not<br/>be threw above API version 24.&lt;br&gt;**适用版本：** 20 - 24 |


## bindController

```TypeScript
export function bindController(node: FrameNode, controller: TextInputController, nodeType: 'TextInput'): void
```

将输入框控制器[TextInputController](arkts-arkui-textinput-textinputcontroller-c.md#TextInputController)绑定到[TextInput](arkts-arkui-typenode-textinput-t.md#TextInput)节点。若该节点非ArkTS语言创建，则需
要设置是否支持跨语言访问，如果不支持跨语言访问，则抛出异常。该接口从API版本26.0.0开始支持声明式方式创建的节点。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | FrameNode | 是 | 绑定输入框控制器的目标节点。 |
| controller | TextInputController | 是 | 输入框控制器。 |
| nodeType | 'TextInput' | 是 | 绑定输入框控制器的目标节点的节点类型为TextInput。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100023](../../errorcode-universal.md#100023-Parameter) | Parameter error. Possible causes: 1. The component type of the node<br/>is incorrect. 2. The node is null or undefined. 3. The controller is null or undefined. |
| [100021](../../errorcode-universal.md#100021-The) | The FrameNode is not modifiable. |


## bindController

```TypeScript
export function bindController(node: FrameNode, controller: Scroller, nodeType: 'WaterFlow'): void
```

将滚动控制器[Scroller](arkts-arkui-scroll-scroller-c.md#Scroller)绑定到[WaterFlow](arkts-arkui-typenode-waterflow-t.md#WaterFlow)节点。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访
问，则抛出异常。从API version 26.0.0开始，该接口支持声明式方式创建的节点，API version 26.0.0以下版本不支持。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | FrameNode | 是 | 绑定滚动控制器的目标节点。 |
| controller | Scroller | 是 | 滚动控制器。 |
| nodeType | 'WaterFlow' | 是 | 绑定滚动控制器的目标节点的节点类型为WaterFlow。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100023](../../errorcode-universal.md#100023-Parameter) | Parameter error. Possible causes: 1. The component type of the node<br/>is incorrect. 2. The node is null or undefined. 3. The controller is null or undefined. |
| [100021](../../errorcode-universal.md#100021-The) | The FrameNode is not modifiable. Introduced in API version 20 and will not<br/>be threw above API version 24.&lt;br&gt;**适用版本：** 20 - 24 |


## bindController

```TypeScript
export function bindController(node: FrameNode, controller: TextAreaController, nodeType: 'TextArea'): void
```

将输入框控制器[TextAreaController](arkts-arkui-textarea-textareacontroller-c.md#TextAreaController)绑定到[TextArea](arkts-arkui-typenode-textarea-t.md#TextArea)节点。若该节点非ArkTS语言创建，则需要设置是
否支持跨语言访问，如果不支持跨语言访问，则抛出异常。该接口从API版本26.0.0开始支持声明式方式创建的节点。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | FrameNode | 是 | 绑定输入框控制器的目标节点。 |
| controller | TextAreaController | 是 | 输入框控制器。 |
| nodeType | 'TextArea' | 是 | 绑定输入框控制器的目标节点的节点类型为TextArea。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100023](../../errorcode-universal.md#100023-Parameter) | Parameter error. Possible causes: 1. The component type of the node<br/>is incorrect. 2. The node is null or undefined. 3. The controller is null or undefined. |
| [100021](../../errorcode-universal.md#100021-The) | The FrameNode is not modifiable. |


## bindController

```TypeScript
export function bindController(node: FrameNode, controller: Scroller, nodeType: 'Grid'): void
```

将滚动控制器[Scroller](arkts-arkui-scroll-scroller-c.md#Scroller)绑定到[Grid](arkts-arkui-typenode-grid-t.md#Grid)节点。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则抛出异常。从
API version 26.0.0开始，该接口支持声明式方式创建的节点，API version 26.0.0以下版本不支持。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | FrameNode | 是 | 绑定滚动控制器的目标节点。 |
| controller | Scroller | 是 | 滚动控制器。 |
| nodeType | 'Grid' | 是 | 绑定滚动控制器的目标节点的节点类型为Grid。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100023](../../errorcode-universal.md#100023-Parameter) | Parameter error. Possible causes: 1. The component type of the node<br/>is incorrect. 2. The node is null or undefined. 3. The controller is null or undefined. |
| [100021](../../errorcode-universal.md#100021-The) | The FrameNode is not modifiable. Introduced in API version 20 and will not<br/>be threw above API version 24.&lt;br&gt;**适用版本：** 20 - 24 |

