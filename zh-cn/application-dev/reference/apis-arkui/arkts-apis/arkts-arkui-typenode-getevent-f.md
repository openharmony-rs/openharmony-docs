# getEvent

## getEvent

```TypeScript
function getEvent(node: FrameNode, nodeType: 'Scroll'): UIScrollEvent | undefined
```

获取Scroll节点中持有的UIScrollEvent对象，用于设置滚动事件。设置的滚动事件与声明式定义的事件平行；设置的滚动事件不覆盖原有的声明式事件。同时设置两个事件回调的时候，优先回调声明式事件。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-typeNode-function getEvent(node: FrameNode, nodeType: 'Scroll'): UIScrollEvent | undefined--><!--Device-typeNode-function getEvent(node: FrameNode, nodeType: 'Scroll'): UIScrollEvent | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 获取事件时所需的目标节点。 |
| nodeType | 'Scroll' | 是 | 获取Scroll节点类型的滚动事件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [UIScrollEvent](../arkts-components/arkts-arkui-uiscrollevent-i.md) | **UIScrollEvent** object for the **Scroll** node, or **undefined** if it fails to be obtained. |


## getEvent

```TypeScript
function getEvent(node: FrameNode, nodeType: 'List'): UIListEvent | undefined
```

获取List节点中持有的UIListEvent对象，用于设置滚动事件。设置的滚动事件与声明式定义的事件平行；设置的滚动事件不覆盖原有的声明式事件。同时设置两个事件回调的时候，优先回调声明式事件。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-typeNode-function getEvent(node: FrameNode, nodeType: 'List'): UIListEvent | undefined--><!--Device-typeNode-function getEvent(node: FrameNode, nodeType: 'List'): UIListEvent | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 获取事件时所需的目标节点。 |
| nodeType | 'List' | 是 | 获取List节点类型的滚动事件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [UIListEvent](../arkts-components/arkts-arkui-uilistevent-i.md) | **UIListEvent** object for the **List** node, or **undefined** if it fails to be obtained. |


## getEvent

```TypeScript
function getEvent(node: FrameNode, nodeType: 'WaterFlow'): UIWaterFlowEvent | undefined
```

获取[WaterFlow](arkts-arkui-typenode-waterflow-t.md)节点中持有的UIWaterFlowEvent对象，用于设置滚动事件。设置的滚动事件与声明式定义的事件平行；设置的滚动事件不覆盖原有的声明式事件。同时设置两个事件回调的时候，优先回调声明式事件。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-typeNode-function getEvent(node: FrameNode, nodeType: 'WaterFlow'): UIWaterFlowEvent | undefined--><!--Device-typeNode-function getEvent(node: FrameNode, nodeType: 'WaterFlow'): UIWaterFlowEvent | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 获取事件时所需的目标节点。 |
| nodeType | 'WaterFlow' | 是 | 获取WaterFlow节点类型的滚动事件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [UIWaterFlowEvent](../arkts-components/arkts-arkui-uiwaterflowevent-i.md) | **UIWaterFlowEvent** object for the **WaterFlow** node, or **undefined** if it fails to be obtained. |


## getEvent

```TypeScript
function getEvent(node: FrameNode, nodeType: 'Grid'): UIGridEvent | undefined
```

获取Grid节点中持有的UIGridEvent对象，用于设置滚动事件。设置的滚动事件与声明式定义的事件平行；设置的滚动事件不覆盖原有的声明式事件。同时设置两个事件回调的时候，优先回调声明式事件。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-typeNode-function getEvent(node: FrameNode, nodeType: 'Grid'): UIGridEvent | undefined--><!--Device-typeNode-function getEvent(node: FrameNode, nodeType: 'Grid'): UIGridEvent | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 获取事件时所需的目标节点。 |
| nodeType | 'Grid' | 是 | 获取Grid节点类型的滚动事件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [UIGridEvent](../arkts-components/arkts-arkui-uigridevent-i.md) | **UIGridEvent** object for the **Grid** node, or **undefined** if it fails to be obtained. |

