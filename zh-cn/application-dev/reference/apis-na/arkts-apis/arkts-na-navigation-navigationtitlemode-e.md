# NavigationTitleMode

标题栏显示模式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare enum NavigationTitleMode--><!--Device-unnamed-export declare enum NavigationTitleMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Free

```TypeScript
Free = 0
```

当内容为满一屏的可滚动组件时，标题随着内容向上滚动而缩小（子标题的大小不变、淡出）。向下滚动内容到顶时则恢复原样。 **说明：** 标题随着内容滚动大小联动的动效在title设置为ResourceStr和NavigationCommonTitle时生效，设置成其余自定义节点类型时字体样式无法变化，下拉时只影响标题栏偏移。 可滚动组件不满一屏时，如果想使用联动效果，就要使用滚动组件提供的 [edgeEffect](../../../reference/apis-arkui/arkui-ts/ts-container-list.md#edgeeffect)接口将options参数设置为true。未滚动状态，标题 栏高度与Full模式一致；滚动时，标题栏的最小高度与Mini模式一致。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationTitleMode-Free = 0--><!--Device-NavigationTitleMode-Free = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Full

```TypeScript
Full
```

The title is full mode.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationTitleMode-Full--><!--Device-NavigationTitleMode-Full-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Mini

```TypeScript
Mini
```

The title is mini mode.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationTitleMode-Mini--><!--Device-NavigationTitleMode-Mini-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

