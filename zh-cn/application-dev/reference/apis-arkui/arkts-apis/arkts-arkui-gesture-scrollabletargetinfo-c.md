# ScrollableTargetInfo

手势识别器对应的滚动类容器组件的信息，继承于[EventTargetInfo](arkts-arkui-gesture-eventtargetinfo-c.md#EventTargetInfo)。

**继承/实现关系：** ScrollableTargetInfo extends [EventTargetInfo](arkts-arkui-gesture-eventtargetinfo-c.md#EventTargetInfo)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare class ScrollableTargetInfo--><!--Device-unnamed-export declare class ScrollableTargetInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isBegin

```TypeScript
isBegin(): boolean
```

返回当前滚动类容器组件是否在顶部，如果为Swiper组件且在循环模式下返回false。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScrollableTargetInfo-isBegin(): boolean--><!--Device-ScrollableTargetInfo-isBegin(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 当前滚动类容器组件是否在顶部。true表示组件在顶部，false表示组件不在顶部。 |

## isEnd

```TypeScript
isEnd(): boolean
```

返回当前滚动类容器组件是否在底部，如果为Swiper组件且在循环模式下返回false。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScrollableTargetInfo-isEnd(): boolean--><!--Device-ScrollableTargetInfo-isEnd(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 当前滚动类容器组件是否在底部。true表示组件在底部，false表示组件不在底部。 |

