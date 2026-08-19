# OnCreateFn（系统接口）

```TypeScript
type OnCreateFn = (want: Want, callback: AsyncCallback<void>) => void
```

业务逻辑初始化操作的属性类型。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-type OnCreateFn = (want: Want, callback: AsyncCallback<void>) => void--><!--Device-unnamed-type OnCreateFn = (want: Want, callback: AsyncCallback<void>) => void-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Provider

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | Indicates connection information about the datashare extension ability. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | callback function, no return value. |

