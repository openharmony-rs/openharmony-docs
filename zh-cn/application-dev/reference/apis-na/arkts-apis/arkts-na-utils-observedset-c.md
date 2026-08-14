# ObservedSet

继承自Set&lt;K&gt;，为可观察API操作的Set对象。详见 ObservedArray/ObservedMap/ObservedSet/ObservedDate：具有观察能力的Built-in类型。

**继承/实现关系：** ObservedSet extends Set<K>

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export declare class ObservedSet--><!--Device-unnamed-export declare class ObservedSet-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
public constructor()
```

无参构造函数。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ObservedSet-public constructor()--><!--Device-ObservedSet-public constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
public constructor(bucketsCount: int)
```

使用指定的容量创建ObservedSet实例。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ObservedSet-public constructor(bucketsCount: int)--><!--Device-ObservedSet-public constructor(bucketsCount: int)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bucketsCount | int | 是 | 指定的初始容量。 |

## constructor

```TypeScript
public constructor(values: K[])
```

使用元素数组创建ObservedSet实例。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ObservedSet-public constructor(values: K[])--><!--Device-ObservedSet-public constructor(values: K[])-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| values | K[] | 是 | 初始元素数组。 |

## constructor

```TypeScript
public constructor(set: Set<K>)
```

使用已有Set对象创建ObservedSet实例。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ObservedSet-public constructor(set: Set<K>)--><!--Device-ObservedSet-public constructor(set: Set<K>)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| set | Set&lt;K&gt; | 是 | 初始Set对象。 |

