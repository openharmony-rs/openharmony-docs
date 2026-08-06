# push（系统接口）

## push

```TypeScript
export function push(param: PushParameterForStage, callback: AsyncCallback<void>): void
```

组件提供方向组件使用方主动发送组件与数据。组件使用方需通过onPush事件监听接收数据。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-pluginComponentManager-export function push(param: PushParameterForStage, callback: AsyncCallback<void>): void--><!--Device-pluginComponentManager-export function push(param: PushParameterForStage, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 组件提供方要发送的参数。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 此次接口调用的异步回调。 |

