# ToJSONType

```TypeScript
export declare type ToJSONType<T> = (value: T) => jsonx.JsonElement
```

> **说明：** > > 静态ArkTS序列化接口，需开发者自己实现。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare type ToJSONType<T> = (value: T) => jsonx.JsonElement--><!--Device-unnamed-export declare type ToJSONType<T> = (value: T) => jsonx.JsonElement-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | T | 是 | toJson value |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| jsonx.JsonElement | Json stringify element object |

