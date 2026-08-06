# PersistenceErrorCallback

```TypeScript
export declare type PersistenceErrorCallback = (key: string, reason: string, message: string, 
    oldValue?: string) => void
```

持久化失败时返回错误原因的回调。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare type PersistenceErrorCallback = (key: string, reason: string, message: string,     oldValue?: string) => void--><!--Device-unnamed-export declare type PersistenceErrorCallback = (key: string, reason: string, message: string,     oldValue?: string) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 出错的键值。  |
| reason | string | 是 | 出错的原因类型。  |
| message | string | 是 | 出错的更多消息。  |
| oldValue | string | 否 | 反序列化失败时返回原始序列化数据。  |

