# sendEventByKey

## 导入模块

```TypeScript
```

## sendEventByKey

```TypeScript
function sendEventByKey(id: string, action: int, params: string): boolean
```

给指定id的组件发送事件。 此接口仅用于对应用的测试。由于耗时长，不建议测试之外的场景使用。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-inspector-function sendEventByKey(id: string, action: int, params: string): boolean--><!--Device-inspector-function sendEventByKey(id: string, action: int, params: string): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 要触发事件的组件id。 |
| action | int | 是 | 要触发的事件类型，当前支持取值：<br/>点击事件Click：10。<br/>长按事件LongClick：11。 |
| params | string | 是 | 事件参数，无参数时传空字符串""。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 找不到指定id的组件时返回false，其余情况返回true。 |

