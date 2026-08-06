# request

## request

```TypeScript
export function request(param: RequestParameters, callback: AsyncCallback<RequestCallbackParameters>): void
```

组件使用方向组件提供方主动请求组件。适用于使用方需按需获取提供方组件及数据的场景。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-pluginComponentManager-export function request(param: RequestParameters, callback: AsyncCallback<RequestCallbackParameters>): void--><!--Device-pluginComponentManager-export function request(param: RequestParameters, callback: AsyncCallback<RequestCallbackParameters>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 组件模板的详细请求信息。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;RequestCallbackParameters&gt; | 是 | 此次请求的异步回调，通过回调接口的参数返回请求所获取的数据。 |

