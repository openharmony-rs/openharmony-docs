# DenormalizeUriFn（系统接口）

```TypeScript
type DenormalizeUriFn = (uri: string, callback: AsyncCallback<string>) => void
```

服务端使用的URI转换为用户传入的初始URI操作的属性类型。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-type DenormalizeUriFn = (uri: string, callback: AsyncCallback<string>) => void--><!--Device-unnamed-type DenormalizeUriFn = (uri: string, callback: AsyncCallback<string>) => void-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Provider

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | Indicates the uri to denormalize. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;string&gt; | 是 | Returns the denormalized {@code uri} object if the denormalization is successful; returns the original {@code uri} passed to this method if there is nothing to do; returns {@code null} if the data identified by the original {@code uri} cannot be found in the current environment. |

