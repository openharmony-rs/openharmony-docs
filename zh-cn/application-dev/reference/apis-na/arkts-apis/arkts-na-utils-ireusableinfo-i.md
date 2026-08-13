# IReusableInfo

`IReusableInfo`接口提供有关复用池管理的可复用组件的当前数量和数量上限的信息。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export declare interface IReusableInfo--><!--Device-unnamed-export declare interface IReusableInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## count

```TypeScript
readonly count: int
```

池中当前回收的组件数。如果设置了`reuseId`，则`count`指的是具有此特定reuseId的组件数。

**类型：** int

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IReusableInfo-readonly count: int--><!--Device-IReusableInfo-readonly count: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maxCount

```TypeScript
maxCount: int
```

池中允许的最大回收组件数。如果设置了`reuseId`，则`maxCount`指的是具有此特定reuseId的组件数。将此设置为小于当前`count`的值会导致框架异步清除多余组件。在延迟期间，`count`可能暂时超过 `maxCount`。默认值：100，最大值：200。

**类型：** int

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IReusableInfo-maxCount: int--><!--Device-IReusableInfo-maxCount: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## reuseId

```TypeScript
readonly reuseId? : string
```

回收组件时指定的reuseId。如果组件没有使用reuseId回收，则此属性为`undefined`。

**类型：** string

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IReusableInfo-readonly reuseId? : string--><!--Device-IReusableInfo-readonly reuseId? : string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

