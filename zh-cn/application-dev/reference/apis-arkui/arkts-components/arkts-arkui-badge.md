# Badge

信息标记容器组件，可以附加在单个组件上用于信息提醒。支持数字、字符串和圆点三种标记形式，可自定义标记样式（文本颜色、大小、标记颜色和大小）和显示位置。适用于需要提示用户有新消息或未读消息的场景，例如未读消息计数、新功能提示等，帮助用户 快速识别和关注重要信息，提升用户体验。

## 子组件 支持单个子组件。 > **说明：** > > - 子组件类型：系统组件和自定义组件，支持渲染控制类型（[if/else](docroot://ui/rendering-control/arkts-rendering-control-ifelse.md)、 > [ForEach]{@link ./for_each}和[LazyForEach]{@link ./lazy_for_each}）。 > > - 自定义组件宽高默认为0，需要给其设置宽高，否则标记组件将不显示。 > > - 当存在多个子组件时，只有最后一个子组件会在界面上显示，但其余子组件的状态更新仍会触发Badge及其包含的所有子组件重新布局渲染。 > > - 不影响子组件布局，即不会主动规避子组件内容。

## Badge

```TypeScript
Badge(value: BadgeParamWithNumber)
```

根据数字创建标记组件。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-BadgeInterface-(value: BadgeParamWithNumber): BadgeAttribute--><!--Device-BadgeInterface-(value: BadgeParamWithNumber): BadgeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 数字标记组件参数，用于配置根据数字创建的Badge组件，包含消息数、显示位置和样式等属性。  |

## Badge

```TypeScript
Badge(value: BadgeParamWithString)
```

根据字符串创建标记组件。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-BadgeInterface-(value: BadgeParamWithString): BadgeAttribute--><!--Device-BadgeInterface-(value: BadgeParamWithString): BadgeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 字符串标记组件参数。  |

## 汇总

