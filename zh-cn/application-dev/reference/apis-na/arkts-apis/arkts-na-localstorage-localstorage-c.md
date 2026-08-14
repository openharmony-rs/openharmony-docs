# LocalStorage

LocalStorage Class implements a Map of ObservableObjectBase UI state variables. Instances can be created to manage UI state within a limited "local" access, and life cycle as defined by the app. AppStorage singleton is sub-class of LocalStorage for UI state of app-wide access and same life cycle as the app.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare class LocalStorage--><!--Device-unnamed-export declare class LocalStorage-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## clear

```TypeScript
public clear(): boolean
```

Delete all properties from the LocalStorage instance Precondition is that there are no subscribers. method returns false and deletes no properties if there is any property that still has subscribers

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LocalStorage-public clear(): boolean--><!--Device-LocalStorage-public clear(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean |  |

## constructor

```TypeScript
public constructor(initializingProperties?: RecordData)
```

Construct new instance of LocalStorage initialize with all properties and their values that Object.keys(params) returns Property values must not be undefined.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LocalStorage-public constructor(initializingProperties?: RecordData)--><!--Device-LocalStorage-public constructor(initializingProperties?: RecordData)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| initializingProperties | [RecordData](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-recorddata-t.md) | 否 | initializing Properties |

## delete

```TypeScript
public delete(propName: string): boolean
```

Delete property from StorageBase Use with caution: Before deleting a prop from LocalStorage all its subscribers need to unsubscribe from the property. This method fails and returns false if given property still has subscribers Another reason for failing is unknown property. Developer advise: Subscribers are created with see link(), see prop() and also via @LocalStorageLink and @LocalStorageProp state variable decorators. That means as long as their is a @Component instance that uses such decorated variable or a sync relationship with a SubscribedAbstractProperty variable the property can nit (and also should not!) be deleted from LocalStorage.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LocalStorage-public delete(propName: string): boolean--><!--Device-LocalStorage-public delete(propName: string): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | false if method failed |

## get

```TypeScript
public get<T>(propName: string): T | undefined
```

Returns value of given property return undefined if no property with this name

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LocalStorage-public get<T>(propName: string): T | undefined--><!--Device-LocalStorage-public get<T>(propName: string): T | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | property name |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | property value if found or undefined |

## has

```TypeScript
public has(propName: string): boolean
```

Check if LocalStorage has a property with given name return true if property with given name exists same as ES6 Map.prototype.has()

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LocalStorage-public has(propName: string): boolean--><!--Device-LocalStorage-public has(propName: string): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | searched property |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true if property with such name exists in LocalStorage |

## keys

```TypeScript
public keys(): IterableIterator<string>
```

Provide names of all properties in LocalStorage same as ES6 Map.prototype.keys()

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LocalStorage-public keys(): IterableIterator<string>--><!--Device-LocalStorage-public keys(): IterableIterator<string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;string&gt; | return a Map Iterator |

## link

```TypeScript
public link<T>(propName: string): SubscribedAbstractProperty<T> | undefined
```

Create and return a two-way sync "(link") to named property

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LocalStorage-public link<T>(propName: string): SubscribedAbstractProperty<T> | undefined--><!--Device-LocalStorage-public link<T>(propName: string): SubscribedAbstractProperty<T> | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | name of source property in LocalStorage |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubscribedAbstractProperty](../../apis-arkui/arkts-apis/arkts-arkui-storageproperty-subscribedabstractproperty-i.md)&lt;T&gt; | instance of SubscribedAbstractProperty&lt;T&gt;, return undefined if named property does not already exist in LocalStorage. |

## ref

```TypeScript
public ref<T>(propName: string): AbstractProperty<T> | undefined
```

Obtain a handler or an alias to LocalStorage property with given name.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LocalStorage-public ref<T>(propName: string): AbstractProperty<T> | undefined--><!--Device-LocalStorage-public ref<T>(propName: string): AbstractProperty<T> | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | LocalStorage property name |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AbstractProperty](../../apis-arkui/arkts-apis/arkts-arkui-storageproperty-abstractproperty-i.md)&lt;T&gt; | AbstractProperty object if property with given name exists return undefined otherwise. |

## set

```TypeScript
public set<T>(propName: string, newValue: T): boolean
```

Set value of given property in LocalStorage Method sets nothing and returns false if property with this name does not exist in LocalStorage newValue can be undefined or null from API 20.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LocalStorage-public set<T>(propName: string, newValue: T): boolean--><!--Device-LocalStorage-public set<T>(propName: string, newValue: T): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 |  |
| newValue | T | 是 | must be of type T, can be undefined or null |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true on success, i.e. when above conditions are satisfied, otherwise false |

## setAndLink

```TypeScript
public setAndLink<T>(propName: string, defaultValue: T): SubscribedAbstractProperty<T>
```

Like see link(), but will create and initialize a new source property in LocalStorage if missing

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LocalStorage-public setAndLink<T>(propName: string, defaultValue: T): SubscribedAbstractProperty<T>--><!--Device-LocalStorage-public setAndLink<T>(propName: string, defaultValue: T): SubscribedAbstractProperty<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | name of source property in LocalStorage |
| defaultValue | T | 是 | value to be used for initializing new property in LocalStorage default value must be of type T, can be undefined or null. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubscribedAbstractProperty](../../apis-arkui/arkts-apis/arkts-arkui-storageproperty-subscribedabstractproperty-i.md)&lt;T&gt; | instance of SubscribedAbstractProperty&lt;T&gt; Apps can use SDK functions of base class SubscribedAbstractProperty&lt;T&gt; |

## setAndRef

```TypeScript
public setAndRef<T>(propName: string, defaultValue: T): AbstractProperty<T>
```

Obtain a handler or an alias to LocalStorage property with given name. If property does not exist in LocalStorage, create it with given default value.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LocalStorage-public setAndRef<T>(propName: string, defaultValue: T): AbstractProperty<T>--><!--Device-LocalStorage-public setAndRef<T>(propName: string, defaultValue: T): AbstractProperty<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | LocalStorage property name |
| defaultValue | T | 是 | If property does not exist in LocalStorage, create it with given default value. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AbstractProperty](../../apis-arkui/arkts-apis/arkts-arkui-storageproperty-abstractproperty-i.md)&lt;T&gt; | AbstractProperty object |

## setOrCreate

```TypeScript
public setOrCreate<T>(propName: string, newValue: T): boolean
```

Set value of given property, if it exists, see set() . Add property if no property with given name and initialize with given value. newValue can be undefined or null from API 12

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LocalStorage-public setOrCreate<T>(propName: string, newValue: T): boolean--><!--Device-LocalStorage-public setOrCreate<T>(propName: string, newValue: T): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 |  |
| newValue | T | 是 | must be of type T, can be undefined or null |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true on success, i.e. when above conditions are satisfied, otherwise false |

## size

```TypeScript
public size(): int
```

Returns number of properties in LocalStorage same as Map.prototype.size()

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LocalStorage-public size(): int--><!--Device-LocalStorage-public size(): int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | return number of properties |

