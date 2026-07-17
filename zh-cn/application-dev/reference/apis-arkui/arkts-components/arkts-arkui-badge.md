# Badge

信息标记组件，可以附加在单个组件上用于信息提醒的容器组件。

## 子组件

支持单个子组件。

> **说明：**  
>  
> - 子组件类型：系统组件和自定义组件，支持渲染控制类型（[if/else](docroot://ui/rendering-control/arkts-rendering-control-ifelse.md)、  
> [ForEach]{@link for_each}和[LazyForEach]{@link lazy_for_each}）。  
>  
> - 自定义组件宽高默认为0，需要给其设置宽高，否则标记组件将不显示。  
>  
> - 当存在多个子组件时，只有最后一个子组件会在界面上显示，但其余子组件的状态更新仍会使Badge及其子组件重新布局渲染。  
>  
> - 不影响子组件布局，即不会主动规避子组件内容。

## Badge

```TypeScript
Badge(value: BadgeParamWithNumber)
```

根据数字创建标记组件。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-BadgeInterface-(value: BadgeParamWithNumber): BadgeAttribute--><!--Device-BadgeInterface-(value: BadgeParamWithNumber): BadgeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | BadgeParamWithNumber | 是 | 数字标记组件参数。 |

## Badge

```TypeScript
Badge(value: BadgeParamWithString)
```

根据字符串创建标记组件。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-BadgeInterface-(value: BadgeParamWithString): BadgeAttribute--><!--Device-BadgeInterface-(value: BadgeParamWithString): BadgeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | BadgeParamWithString | 是 | 字符串标记组件参数。 |

## 汇总

- [BadgeParam](arkts-arkui-badge-badgeparam-i.md)
- [BadgeParamWithNumber](arkts-arkui-badge-badgeparamwithnumber-i.md)
- [BadgeParamWithString](arkts-arkui-badge-badgeparamwithstring-i.md)
- [BadgeStyle](arkts-arkui-badge-badgestyle-i.md)
- [BadgePosition](arkts-arkui-badge-badgeposition-e.md)
