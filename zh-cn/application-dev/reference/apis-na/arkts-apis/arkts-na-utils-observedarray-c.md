# ObservedArray

继承自Array&lt;T&gt;，为可观察API操作的Array对象。详见 ObservedArray/ObservedMap/ObservedSet/ObservedDate：具有观察能力的Built-in类型。

**继承/实现关系：** ObservedArray extends Array<T>

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare class ObservedArray--><!--Device-unnamed-export declare class ObservedArray-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
public constructor()
```

无参构造函数。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ObservedArray-public constructor()--><!--Device-ObservedArray-public constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
public constructor(first: T, ...d: T[])
```

使用元素列表初始化ObservedArray实例。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ObservedArray-public constructor(first: T, ...d: T[])--><!--Device-ObservedArray-public constructor(first: T, ...d: T[])-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| first | T | 是 | 第一个元素。 |
| d | T[] | 是 | 其余元素组成的数组，默认为[]。 |

## constructor

```TypeScript
public constructor(arrayLen: int, initializer: ObservedArrayInitializer<T>)
```

使用指定的长度和初始化函数初始化ObservedArray实例。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ObservedArray-public constructor(arrayLen: int, initializer: ObservedArrayInitializer<T>)--><!--Device-ObservedArray-public constructor(arrayLen: int, initializer: ObservedArrayInitializer<T>)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| arrayLen | int | 是 | 数组初始长度。 |
| initializer | [ObservedArrayInitializer](arkts-na-observedarrayinitializer-t.md)&lt;T&gt; | 是 | 数组元素初始化函数。 |

