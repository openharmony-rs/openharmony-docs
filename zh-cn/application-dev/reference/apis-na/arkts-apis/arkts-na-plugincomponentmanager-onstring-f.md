# on_string

## on_string

```TypeScript
export function on(eventType: string, callback: OnPushEventCallback | OnRequestEventCallback): void
```

提供方监听"request"类型的事件，给使用方返回通过request接口主动请求的数据；使用方监听"push"类型的事件，接收提供方通过push接口主动推送的数据。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-pluginComponentManager-export function on(eventType: string, callback: OnPushEventCallback | OnRequestEventCallback): void--><!--Device-pluginComponentManager-export function on(eventType: string, callback: OnPushEventCallback | OnRequestEventCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventType | string | 是 | 监听的事件类型，可选值为："push"、"request"。"push"：指组件提供方向使用方主动推送数据。"request"：指组件使用方向提供方主动请求数据。 |
| callback | [OnPushEventCallback](arkts-na-plugincomponentmanager-onpusheventcallback-t.md) \| [OnRequestEventCallback](arkts-na-plugincomponentmanager-onrequesteventcallback-t.md) | 是 | 对应监听回调， push事件对应回调类型为OnPushEventCallback，request事件对应回调类型为OnRequestEventCallback。 |

