# request

## 导入模块

```TypeScript
```

## request

```TypeScript
export function request(param: RequestParameters, callback: AsyncCallback<RequestCallbackParameters>): void
```

组件使用方向组件提供方主动请求组件。适用于使用方需按需获取提供方组件及数据的场景。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-pluginComponentManager-export function request(param: RequestParameters, callback: AsyncCallback<RequestCallbackParameters>): void--><!--Device-pluginComponentManager-export function request(param: RequestParameters, callback: AsyncCallback<RequestCallbackParameters>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | [RequestParameters](../../apis-arkui/arkts-apis/arkts-arkui-plugincomponentmanager-requestparameters-i.md) | 是 | 组件模板的详细请求信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[RequestCallbackParameters](../../apis-arkui/arkts-apis/arkts-arkui-plugincomponentmanager-requestcallbackparameters-i.md)&gt; | 是 | 此次请求的异步回调，通过回调接口的参数返回请求所获取的数据。 |

