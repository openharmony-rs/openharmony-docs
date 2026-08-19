# ObservedMap

继承自Map&lt;K, V&gt;，为可观察API操作的Map对象。详见 ObservedArray/ObservedMap/ObservedSet/ObservedDate：具有观察能力的Built-in类型。

**继承/实现关系：** ObservedMap extends Map<K, V>

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare class ObservedMap--><!--Device-unnamed-export declare class ObservedMap-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
public constructor()
```

无参构造函数。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ObservedMap-public constructor()--><!--Device-ObservedMap-public constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
public constructor(initialCapacity: int)
```

使用指定的容量创建ObservedMap实例。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ObservedMap-public constructor(initialCapacity: int)--><!--Device-ObservedMap-public constructor(initialCapacity: int)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| initialCapacity | int | 是 | 指定的初始容量。 |

## constructor

```TypeScript
public constructor(entries: [K, V][])
```

使用键值对数组创建ObservedMap实例。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ObservedMap-public constructor(entries: [K, V][])--><!--Device-ObservedMap-public constructor(entries: [K, V][])-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| entries | [K, V][] | 是 | 初始键值对数组。 |

## constructor

```TypeScript
public constructor(map: Map<K, V>)
```

使用已有Map对象创建ObservedMap实例。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ObservedMap-public constructor(map: Map<K, V>)--><!--Device-ObservedMap-public constructor(map: Map<K, V>)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| map | Map&lt;K, V&gt; | 是 | 初始Map对象。 |

