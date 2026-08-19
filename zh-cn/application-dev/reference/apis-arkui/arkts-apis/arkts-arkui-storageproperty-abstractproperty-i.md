# AbstractProperty

Define AbstractProperty&lt;T&gt; interface. AbstractProperty can be understood as a handler or an alias to a property inside LocalStorage / AppStorage singleton allows to read the value with @see get and to change the value with @see set.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface AbstractProperty--><!--Device-unnamed-export declare interface AbstractProperty-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## get

```TypeScript
get(): T
```

读取AppStorage/ LocalStorage中所引用属性的数据。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AbstractProperty-get(): T--><!--Device-AbstractProperty-get(): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | AppStorage/LocalStorage中所引用属性的数据。 |

## info

```TypeScript
info(): string
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-AbstractProperty-info(): string--><!--Device-AbstractProperty-info(): string-End-->

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string |  |

## onChange

```TypeScript
onChange(onChangeFunc: OnChangeType<T> | undefined): void
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-AbstractProperty-onChange(onChangeFunc: OnChangeType<T> | undefined): void--><!--Device-AbstractProperty-onChange(onChangeFunc: OnChangeType<T> | undefined): void-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| onChangeFunc | [OnChangeType](arkts-arkui-onchangetype-t.md)&lt;T&gt; \| undefined | 是 |  |

## set

```TypeScript
set(newValue: T): void
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-AbstractProperty-set(newValue: T): void--><!--Device-AbstractProperty-set(newValue: T): void-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| newValue | T | 是 |  |

## default

```TypeScript
default
```

注册AppStorage/ LocalStorage中所引用属性变化的事件。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AbstractProperty-default--><!--Device-AbstractProperty-default-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

