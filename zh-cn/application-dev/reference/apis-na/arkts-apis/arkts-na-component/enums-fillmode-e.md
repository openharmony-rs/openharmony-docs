# FillMode

设置当前播放方向下，动画开始前和结束后的状态。动画结束后的状态由fillMode和reverse属性共同决定。例如，fillMode为Forwards表示停止时维持动画最后一个关键帧的状态，若reverse为false则维持正播的最后 一帧，即最后一张图，若reverse为true则维持逆播的最后一帧，即第一张图。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare enum FillMode--><!--Device-unnamed-export declare enum FillMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## None

```TypeScript
None = 0
```

动画未执行时，不应用任何样式到目标；播放完成后，恢复初始默认状态。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FillMode-None = 0--><!--Device-FillMode-None = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Forwards

```TypeScript
Forwards = 1
```

目标将保留动画执行期间最后一个关键帧的状态。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FillMode-Forwards = 1--><!--Device-FillMode-Forwards = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Backwards

```TypeScript
Backwards = 2
```

动画应用于目标时，立即采用第一个关键帧定义的值，并在delay期间保留此值。第一个关键帧取决于playMode，playMode为Normal或Alternate时，帧为from状态；playMode为Reverse或 AlternateReverse时，帧为to状态。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FillMode-Backwards = 2--><!--Device-FillMode-Backwards = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Both

```TypeScript
Both = 3
```

动画将遵循Forwards和Backwards的规则，从而在两个方向上扩展动画属性。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FillMode-Both = 3--><!--Device-FillMode-Both = 3-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

