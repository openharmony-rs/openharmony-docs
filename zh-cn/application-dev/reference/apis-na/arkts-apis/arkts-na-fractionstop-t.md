# FractionStop

```TypeScript
export type FractionStop = [
    double,
    double
]
```

Defines the segment of blur. The first element in the tuple means fraction. The range of this value is [0,1]. A value of 1 means opaque and 0 means completely transparent. The second element means the stop position. The range of this value is [0,1]. A value of 1 means region ending position and 0 means region starting position.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type FractionStop = [    double,    double]--><!--Device-unnamed-export type FractionStop = [    double,    double]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**属性类型：** [
    double,
    double
]

