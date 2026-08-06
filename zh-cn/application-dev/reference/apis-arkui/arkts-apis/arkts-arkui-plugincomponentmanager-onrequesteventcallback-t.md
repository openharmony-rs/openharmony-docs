# OnRequestEventCallback

```TypeScript
export type OnRequestEventCallback = (source: Want, name: string, data: KVObject) => RequestEventResult
```

对应request事件的监听回调函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-pluginComponentManager-export type OnRequestEventCallback = (source: Want, name: string, data: KVObject) => RequestEventResult--><!--Device-pluginComponentManager-export type OnRequestEventCallback = (source: Want, name: string, data: KVObject) => RequestEventResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| source | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | request请求发送方相关信息。  |
| name | string | 是 | 请求的组件名称。  |
| data | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | request事件中传递的数据内容，以键值对形式存储，键和值类型由业务定义。  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 注册request监听方法后，接收到请求事件时回应请求的数据类型。 |

