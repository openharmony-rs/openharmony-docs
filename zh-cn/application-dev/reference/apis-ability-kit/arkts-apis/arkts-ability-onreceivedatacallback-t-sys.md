# OnReceiveDataCallback（系统接口）

```TypeScript
export type OnReceiveDataCallback = (data: Record<string, RecordData>) => void
```

从UIExtensionComponent控件接收数据的回调方法。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type OnReceiveDataCallback = (data: Record<string, RecordData>) => void--><!--Device-unnamed-export type OnReceiveDataCallback = (data: Record<string, RecordData>) => void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | Record&lt;string, [RecordData](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-recorddata-t.md)&gt; | 是 | 回调函数，返回接收的数据。 |

