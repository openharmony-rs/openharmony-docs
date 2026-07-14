# createComponentObserver

## createComponentObserver

```TypeScript
function createComponentObserver(id: string): ComponentObserver
```

**起始版本：** 10

**废弃版本：** 18

**替代接口：** createComponentObserver

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | component id. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ComponentObserver | create listener for observer component event. |

**示例：**

```TypeScript
let listener:inspector.ComponentObserver = inspector.createComponentObserver('COMPONENT_ID'); // 监听id为COMPONENT_ID的组件回调事件

```

