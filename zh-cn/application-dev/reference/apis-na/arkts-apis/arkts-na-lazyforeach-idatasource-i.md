# IDataSource

LazyForEach的数据源。ArkTS-Sta中IDataSource强制要求声明`&lt;T&gt;`类型。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface IDataSource--><!--Device-unnamed-export interface IDataSource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getData

```TypeScript
getData(index: int): T
```

获取索引值index对应的数据。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IDataSource-getData(index: int): T--><!--Device-IDataSource-getData(index: int): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 获取索引值index对应的数据，由数据源决定具体类型。 |

## registerDataChangeListener

```TypeScript
registerDataChangeListener(listener: DataChangeListener): void
```

注册数据改变的监听器。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IDataSource-registerDataChangeListener(listener: DataChangeListener): void--><!--Device-IDataSource-registerDataChangeListener(listener: DataChangeListener): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| listener | [DataChangeListener](arkts-na-lazyforeach-datachangelistener-i.md) | 是 |  |

## totalCount

```TypeScript
totalCount(): int
```

获得数据总数。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IDataSource-totalCount(): int--><!--Device-IDataSource-totalCount(): int-End-->

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 获得数据总数，由数据源决定实际大小。 |

## unregisterDataChangeListener

```TypeScript
unregisterDataChangeListener(listener: DataChangeListener): void
```

注销数据改变的监听器。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IDataSource-unregisterDataChangeListener(listener: DataChangeListener): void--><!--Device-IDataSource-unregisterDataChangeListener(listener: DataChangeListener): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| listener | [DataChangeListener](arkts-na-lazyforeach-datachangelistener-i.md) | 是 |  |

