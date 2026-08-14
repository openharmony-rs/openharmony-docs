# NormalizeUriFn（系统接口）

```TypeScript
type NormalizeUriFn = (uri: string, callback: AsyncCallback<string>) => void
```

用户给定的URI转换为服务端使用的URI操作的属性类型。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-type NormalizeUriFn = (uri: string, callback: AsyncCallback<string>) => void--><!--Device-unnamed-type NormalizeUriFn = (uri: string, callback: AsyncCallback<string>) => void-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Provider

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | Indicates the uri to normalize. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;string&gt; | 是 | Returns the normalized uri if the data share supports URI normalization. |

