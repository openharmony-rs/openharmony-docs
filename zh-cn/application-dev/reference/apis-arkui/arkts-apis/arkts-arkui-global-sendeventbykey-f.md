# sendEventByKey

## sendEventByKey

```TypeScript
export declare function sendEventByKey(id: string, action: number, params: string): boolean
```

Sends an event to the component with the specified ID.

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | ID of the component for which the event is to be sent. |
| action | number | 是 | Type of the event to be sent. The options are as follows: Click event: 10 LongClick: 11. |
| params | string | 是 | Event parameters. If there is no parameter, pass an empty string "". |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | @syscap SystemCapability.ArkUI.ArkUI.Full@crossplatform@atomicservice |

