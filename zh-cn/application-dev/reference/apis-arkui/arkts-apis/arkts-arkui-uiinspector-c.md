# UIInspector

class UIInspector

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## createComponentObserver

```TypeScript
createComponentObserver(id: string): inspector.ComponentObserver
```

Sets the component after layout or draw criteria and returns the corresponding listening handle

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | component id. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| inspector.ComponentObserver | create listener for observer component event. |

## createComponentObserver

```TypeScript
createComponentObserver(id: string | number): inspector.ComponentObserver
```

创建当前节点或者当前节点的子节点的布局和送显的事件监听句柄。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string \| number | 是 | 当前节点的inspector key或者唯一id。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| inspector.ComponentObserver | create listener for observer component event. |

