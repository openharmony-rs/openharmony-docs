# push（系统接口）

## 导入模块

```TypeScript
```

## push

```TypeScript
export function push(param: PushParameterForStage, callback: AsyncCallback<void>): void
```

组件提供方向组件使用方主动发送组件与数据。组件使用方需通过onPush事件监听接收数据。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-pluginComponentManager-export function push(param: PushParameterForStage, callback: AsyncCallback<void>): void--><!--Device-pluginComponentManager-export function push(param: PushParameterForStage, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | [PushParameterForStage](../../apis-arkui/arkts-apis/arkts-arkui-plugincomponentmanager-pushparameterforstage-i-sys.md) | 是 | 组件提供方要发送的参数。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 此次接口调用的异步回调。 |

