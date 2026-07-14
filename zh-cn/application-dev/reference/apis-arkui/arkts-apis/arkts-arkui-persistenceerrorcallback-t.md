# PersistenceErrorCallback

```TypeScript
export declare type PersistenceErrorCallback = (key: string, reason: 'quota' | 'serialization' | 'unknown', 
    message: string, oldValue?: string) => void
```

持久化失败时返回错误原因的回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 出错的键值。 |
| reason | 'quota' \| 'serialization' \| 'unknown' | 是 | 出错的原因类型。 |
| message | string | 是 | 出错的更多消息。 |
| oldValue | string | 否 | 反序列化失败时，返回的旧的存储于磁盘的序列化数据。 |

