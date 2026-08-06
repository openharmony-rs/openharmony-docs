# FromJSONType

```TypeScript
export declare type FromJSONType<T> = (element: jsonx.JsonElement) => T
```

> **说明：** > > 静态ArkTS反序列化接口，需开发者自己实现。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare type FromJSONType<T> = (element: jsonx.JsonElement) => T--><!--Device-unnamed-export declare type FromJSONType<T> = (element: jsonx.JsonElement) => T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| element | jsonx.JsonElement | 是 | json element |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | deserialization result |

