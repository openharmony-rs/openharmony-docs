# NavigationMode

导航页显示模式。Navigation处于分栏显示状态时，导航页和内容区之间会显示分割线。

> **说明：**  
>  
> 为了简化表示，可以将`组件宽度 - minContentWidth - 分割线宽度 (1px)`称为calcNavBarWidth。

**表1** navBarWidth最终取值与开发者设置值的关系表

| 开发者设置的navBarWidth值 | calcNavBarWidth计算值 | navBarWidth最终取值 |  
| --- | --- | --- |  
| navBarWidth < minNavBarWidth | NA | minNavBarWidth |  
| navBarWidth > maxNavBarWidth | calcNavBarWidth > maxNavBarWidth | maxNavBarWidth |  
| navBarWidth > maxNavBarWidth | calcNavBarWidth < minNavBarWidth | minNavBarWidth |  
| navBarWidth > maxNavBarWidth | minNavBarWidth ≤ calcNavBarWidth ≤ maxNavBarWidth | calcNavBarWidth |  
| minNavBarWidth ≤ navBarWidth ≤ maxNavBarWidth | calcNavBarWidth ≤ minNavBarWidth | minNavBarWidth |  
| minNavBarWidth ≤ navBarWidth ≤ maxNavBarWidth | minNavBarWidth < calcNavBarWidth <= navBarWidth | calcNavBarWidth |  
| minNavBarWidth ≤ navBarWidth ≤ maxNavBarWidth | calcNavBarWidth > navBarWidth | navBarWidth |

**起始版本：** 9

<!--Device-unnamed-declare enum NavigationMode--><!--Device-unnamed-declare enum NavigationMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Stack

```TypeScript
Stack
```

导航页与内容区独立显示，相当于两个页面。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationMode-Stack--><!--Device-NavigationMode-Stack-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Split

```TypeScript
Split
```

导航页与内容区分两栏显示。

**1.** navBarWidth最终取值与开发者设置值的关系参见表1。

**2.** 缩小组件尺寸时，先缩小内容区的尺寸至minContentWidth，然后再缩小导航页的尺寸至minNavBarWidth。若继续缩小，先缩小内容区，内容区消失后再缩小导航页。

**3.** 设置导航页为固定尺寸时，若持续缩小组件尺寸，导航页最后压缩显示。

**4.** 若只设置了navBarWidth属性，则导航页宽度为navBarWidth，且分割线不可拖动。

**5.** 分割线的热区左右各2vp，建议避让4vp以上。

**6.** Split模式下，内容区若只存在一个页面，则页面左上角不会显示返回按钮。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationMode-Split--><!--Device-NavigationMode-Split-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Auto

```TypeScript
Auto
```

API version 9及之前版本，Navigation宽度>=520vp时，采用Split模式显示；Navigation宽度<520vp时，采用Stack模式显示。

从API version 10开始：Navigation宽度>=600vp时，采用Split模式显示；Navigation宽度<600vp时，采用Stack模式显示，600vp等于minNavBarWidth(240vp) +minContentWidth (360vp)。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationMode-Auto--><!--Device-NavigationMode-Auto-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## AUTO_WITH_ASPECT_RATIO

```TypeScript
AUTO_WITH_ASPECT_RATIO
```

Navigation宽度>=600vp且高宽比小于等于1.2时，采用Split模式显示；否则采用Stack模式显示。600vp等于minNavBarWidth(240vp) + minContentWidth (360vp)。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationMode-AUTO_WITH_ASPECT_RATIO--><!--Device-NavigationMode-AUTO_WITH_ASPECT_RATIO-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

