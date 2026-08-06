# AbstractProperty

Define AbstractProperty\_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_ interface. AbstractProperty can be understood as a handler or an alias to a property inside LocalStorage / AppStorage singleton allows to read the value with @see get and to change the value with @see set.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface AbstractProperty<T>--><!--Device-unnamed-export declare interface AbstractProperty<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## get

```TypeScript
get(): T
```

读取\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_/ \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_中所引用属性的数据。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AbstractProperty-get(): T--><!--Device-AbstractProperty-get(): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | AppStorage/LocalStorage中所引用属性的数据。 |

## info

```TypeScript
default info(): string
```

读取\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_/ \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_中所引用属性的属性名。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AbstractProperty-default info(): string--><!--Device-AbstractProperty-default info(): string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | AppStorage/LocalStorage中所引用属性的属性名。 |

## onChange

```TypeScript
default onChange(onChangeFunc: OnChangeType<T> | undefined): void
```

注册\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_/ \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_中所引用属性变化的事件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AbstractProperty-default onChange(onChangeFunc: OnChangeType<T> | undefined): void--><!--Device-AbstractProperty-default onChange(onChangeFunc: OnChangeType<T> | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| onChangeFunc | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; \| undefined | 是 | 属性变化回调函数。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_如果传入有效值，则添加到监听属性变化的函数列表中。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_如果传入undefined，则清除所有监听回调。 |

## set

```TypeScript
default set(newValue: T): void
```

更新\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_/ \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_中所引用属性的数据，newValue必须是T类型，可以为null或 undefined。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AbstractProperty-default set(newValue: T): void--><!--Device-AbstractProperty-default set(newValue: T): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| newValue | T | 是 | 要更新的数据，可以为null或undefined。 |

