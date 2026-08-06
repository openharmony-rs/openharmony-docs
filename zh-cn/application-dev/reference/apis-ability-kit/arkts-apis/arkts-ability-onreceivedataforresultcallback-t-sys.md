# OnReceiveDataForResultCallback（系统接口）

```TypeScript
export type OnReceiveDataForResultCallback = (data: Record<string, RecordData>) => Record<string, RecordData>
```

从UIExtensionComponent控件接收数据带返回值的回调方法。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type OnReceiveDataForResultCallback = (data: Record<string, RecordData>) => Record<string, RecordData>--><!--Device-unnamed-export type OnReceiveDataForResultCallback = (data: Record<string, RecordData>) => Record<string, RecordData>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | Record&lt;string, RecordData&gt; | 是 | 回调函数，返回带返回值的接收的数据。  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Record&lt;string, RecordData&gt; | 返回的数据对象。 |

