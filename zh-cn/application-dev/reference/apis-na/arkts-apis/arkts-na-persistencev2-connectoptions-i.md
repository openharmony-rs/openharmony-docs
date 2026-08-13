# ConnectOptions

globalConnect参数类型。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export declare interface ConnectOptions--><!--Device-unnamed-export declare interface ConnectOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## areaMode

```TypeScript
areaMode?: contextConstant.AreaMode
```

加密级别：EL1-EL5，详见[加密级别](../../../application-models/application-context-stage.md#获取和修改加密分区)，不传时默认为EL2，不同加密级别对应不同的加密分 区，即不同的存储路径。

**类型：** contextConstant.AreaMode

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ConnectOptions-areaMode?: contextConstant.AreaMode--><!--Device-ConnectOptions-areaMode?: contextConstant.AreaMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## defaultCreator

```TypeScript
defaultCreator?: StorageDefaultCreator<T>
```

默认数据的构造器，默认值为undefined，建议传递，如果globalConnect是第一次连接key，不传会报错。

**类型：** [StorageDefaultCreator](arkts-na-storagedefaultcreator-t.md)&lt;T&gt;

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ConnectOptions-defaultCreator?: StorageDefaultCreator<T>--><!--Device-ConnectOptions-defaultCreator?: StorageDefaultCreator<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## defaultSubCreators

```TypeScript
defaultSubCreators?: StorageDefaultSubCreators
```

保存对象类型及其默认构造器的Map。用于恢复内层对象数据。默认值为undefined。

**类型：** [StorageDefaultSubCreators](arkts-na-storagedefaultsubcreators-t.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ConnectOptions-defaultSubCreators?: StorageDefaultSubCreators--><!--Device-ConnectOptions-defaultSubCreators?: StorageDefaultSubCreators-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableAutoSave

```TypeScript
enableAutoSave?: boolean
```

是否自动持久化存储数据，默认值为true。

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ConnectOptions-enableAutoSave?: boolean--><!--Device-ConnectOptions-enableAutoSave?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fromJson

```TypeScript
fromJson?: FromJSONType<T>
```

转换JSON格式对象到存储对象的函数。

**类型：** [FromJSONType](arkts-na-fromjsontype-t.md)&lt;T&gt;

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ConnectOptions-fromJson?: FromJSONType<T>--><!--Device-ConnectOptions-fromJson?: FromJSONType<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## key

```TypeScript
key?: string
```

传入的key，不传则使用type的名字作为key。

**类型：** string

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ConnectOptions-key?: string--><!--Device-ConnectOptions-key?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## toJson

```TypeScript
toJson?: ToJSONType<T>
```

转换存储对象到JSON格式对象的函数。

**类型：** [ToJSONType](arkts-na-tojsontype-t.md)&lt;T&gt;

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ConnectOptions-toJson?: ToJSONType<T>--><!--Device-ConnectOptions-toJson?: ToJSONType<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: Class
```

指定的类型。

**类型：** Class

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ConnectOptions-type: Class--><!--Device-ConnectOptions-type: Class-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

