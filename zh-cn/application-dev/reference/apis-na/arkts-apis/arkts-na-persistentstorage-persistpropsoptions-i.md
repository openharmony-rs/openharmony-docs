# PersistPropsOptions

指定持久化属性及其默认值的键值对对象，作为[persistProps](#PersistPropsOptions)参数传入。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface PersistPropsOptions--><!--Device-unnamed-export declare interface PersistPropsOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## defaultValue

```TypeScript
defaultValue: T
```

当在[PersistentStorage](arkts-na-persistentstorage-persistentstorage-c.md#PersistentStorage)和 AppStorage中未查询到key时，使用 defaultValue中。

**类型：** T

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PersistPropsOptions-defaultValue: T--><!--Device-PersistPropsOptions-defaultValue: T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fromJson

```TypeScript
fromJson?: FromJSONType<T>
```

默认值为undefined。见[FromJsonType](arkts-na-fromjsontype-t.md#FromJSONType)，用于反序列化。对于复杂类型（除boolean、int、double、long、string外），开发者必须实现该方法才能成功反序列 化。

**类型：** [FromJSONType](arkts-na-fromjsontype-t.md)&lt;T&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PersistPropsOptions-fromJson?: FromJSONType<T>--><!--Device-PersistPropsOptions-fromJson?: FromJSONType<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## key

```TypeScript
key: string
```

属性名。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PersistPropsOptions-key: string--><!--Device-PersistPropsOptions-key: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## toJson

```TypeScript
toJson?: ToJSONType<T>
```

默认值为undefined。见[ToJsonType](arkts-na-tojsontype-t.md#ToJSONType)，用于序列化。对于复杂类型（除boolean、int、double、long、string外），开发者必须实现该方法才能成功序列化。

**类型：** [ToJSONType](arkts-na-tojsontype-t.md)&lt;T&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PersistPropsOptions-toJson?: ToJSONType<T>--><!--Device-PersistPropsOptions-toJson?: ToJSONType<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

