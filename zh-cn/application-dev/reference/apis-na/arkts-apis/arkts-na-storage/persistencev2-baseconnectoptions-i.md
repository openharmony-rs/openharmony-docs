# BaseConnectOptions

connect参数类型。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare interface BaseConnectOptions<T extends object>--><!--Device-unnamed-export declare interface BaseConnectOptions<T extends object>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableAutoSave

```TypeScript
enableAutoSave?: boolean
```

是否自动持久化存储数据，默认值为true。

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseConnectOptions-enableAutoSave?: boolean--><!--Device-BaseConnectOptions-enableAutoSave?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fromJson

```TypeScript
fromJson?: FromJSONType<T>
```

转换JSON格式对象到存储对象的函数。

**类型：** FromJSONType&lt;T&gt;

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseConnectOptions-fromJson?: FromJSONType<T>--><!--Device-BaseConnectOptions-fromJson?: FromJSONType<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## toJson

```TypeScript
toJson?: ToJSONType<T>
```

转换存储对象到JSON格式对象的函数。

**类型：** ToJSONType&lt;T&gt;

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseConnectOptions-toJson?: ToJSONType<T>--><!--Device-BaseConnectOptions-toJson?: ToJSONType<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

