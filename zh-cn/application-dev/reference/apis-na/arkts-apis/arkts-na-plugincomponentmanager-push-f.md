# push

## push

```TypeScript
export function push(param: PushParameters, callback: AsyncCallback<void>): void
```

组件提供方向组件使用方主动发送组件和数据。适用于提供方数据更新后需主动通知使用方刷新显示的场景。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-pluginComponentManager-export function push(param: PushParameters, callback: AsyncCallback<void>): void--><!--Device-pluginComponentManager-export function push(param: PushParameters, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | [PushParameters](arkts-na-plugincomponentmanager-pushparameters-i.md) | 是 | 推送组件的详细参数。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 此次接口调用的异步回调。 |

