# ReuseObject

Define ReuseObject for aboutToReuse method.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare class ReuseObject--><!--Device-unnamed-export declare class ReuseObject-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## $_get

```TypeScript
$_get(key: string): RecordData
```

Get value from the ReuseObject by key.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ReuseObject-$_get(key: string): RecordData--><!--Device-ReuseObject-$_get(key: string): RecordData-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | the key of target value. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RecordData](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-recorddata-t.md) | the target value. |

## has

```TypeScript
has(key: string): boolean
```

Returns if the key is in the ReuseObject.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ReuseObject-has(key: string): boolean--><!--Device-ReuseObject-has(key: string): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | the key of target value. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | if the key is in the ReuseObject. |

## keys

```TypeScript
keys(): string[]
```

Returns the keys array of the ReuseObject.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ReuseObject-keys(): string[]--><!--Device-ReuseObject-keys(): string[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string[] | the keys array of the ReuseObject. |

