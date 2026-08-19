# PersistentStorage

Defines the PersistentStorage interface.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class PersistentStorage--><!--Device-unnamed-export declare class PersistentStorage-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## deleteProp

```TypeScript
static deleteProp(key: string): void
```

[persistProp](arkts-na-persistentstorage-persistpropsoptions-i.md)的逆向操作。将key对应的属性从PersistentStorage中删除，后续 AppStorage的操作，对 PersistentStorage不会再有影响。该操作会将对应的key从持久化文件中删 除，如果希望再次持久化，可以再次调用[persistProp](arkts-na-persistentstorage-persistpropsoptions-i.md)接口。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PersistentStorage-static deleteProp(key: string): void--><!--Device-PersistentStorage-static deleteProp(key: string): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | PersistentStorage中的属性名。 |

## keys

```TypeScript
static keys(): Array<string>
```

返回所有持久化属性的属性名的数组。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PersistentStorage-static keys(): Array<string>--><!--Device-PersistentStorage-static keys(): Array<string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 返回所有持久化属性的属性名的数组。 |

## persistProp

```TypeScript
static persistProp<T>(key: string, defaultValue: T, toJson?: ToJSONType<T>, fromJson?: FromJSONType<T>): boolean
```

将AppStorage中key对应的属性持久化到文件中。该接口的调用通常在访问 AppStorage之前。 确定属性的类型和值的顺序如下： 1. 如果PersistentStorage文件中存在key对应的属性，则返回false。 2. 如果PersistentStorage文件中没有查询到key对应的属性，则在AppStorage中查找key对应的属性。如果找到key对应的属性，则将该属性持久化，并返回true。 3. 如果AppStorage中也没查找到key对应的属性，则在磁盘中查找key对应的属性。如果找到key对应的属性，则在AppStorage中创建和初始化key对应的属性，并将该属性持久化，最终返回true。 4. 如果磁盘中不存在对应属性，则在AppStorage中创建和初始化key对应的属性，并将该属性持久化，最终返回true。 根据上述的初始化流程，如果AppStorage中有该属性，则会使用其值，覆盖掉PersistentStorage文件中的值。由于AppStorage是内存内数据，该行为会导致数据丧失持久化能力。 5. 对于复杂类型(联合类型都是复杂类型)，开发者必须实现toJson和fromJson才能实现持久化，只有boolean、int、double、long、string，开发者可以不传入toJson和fromJson。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PersistentStorage-static persistProp<T>(key: string, defaultValue: T, toJson?: ToJSONType<T>, fromJson?: FromJSONType<T>): boolean--><!--Device-PersistentStorage-static persistProp<T>(key: string, defaultValue: T, toJson?: ToJSONType<T>, fromJson?: FromJSONType<T>): boolean-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 属性名。 |
| defaultValue | T | 是 | 当在[PersistentStorage](#persistentstorage)和 AppStorage中未查询到key时，使用 defaultValue中。 |
| toJson | [ToJSONType](arkts-na-tojsontype-t.md)&lt;T&gt; | 否 | 见[ToJSONType](arkts-na-tojsontype-t.md)，用于序列化。对于复杂类型（除boolean、int、double、long、string外）， 开发者必须实现该方法才能成功序列化。 |
| fromJson | [FromJSONType](arkts-na-fromjsontype-t.md)&lt;T&gt; | 否 | 见[FromJSONType](arkts-na-fromjsontype-t.md)，用于反序列化。对于复杂类型（除boolean、int、double、long、 string外），开发者必须实现该方法才能成功反序列化。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果PersistentStorage文件中存在key对应的属性，则返回false。否则将依次从AppStorage、磁盘中查找对应属性，若存在，则返回true，若不存在，则创建并持久化 key对应的属性，并返回true。 |

## persistProps

```TypeScript
static persistProps(props: PersistPropsOptions<Any>[]): void
```

将AppStorage中key对应的属性持久化到文件中。与 [persistProp](arkts-na-persistentstorage-persistpropsoptions-i.md)的区别在于可以一次性持久化多个数据，适用场景是：应用启动时调用持久化接口。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PersistentStorage-static persistProps(props: PersistPropsOptions<Any>[]): void--><!--Device-PersistentStorage-static persistProps(props: PersistPropsOptions<Any>[]): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| props | [PersistPropsOptions](arkts-na-persistentstorage-persistpropsoptions-i.md)&lt;Any&gt;[] | 是 | 持久化数组。 |

