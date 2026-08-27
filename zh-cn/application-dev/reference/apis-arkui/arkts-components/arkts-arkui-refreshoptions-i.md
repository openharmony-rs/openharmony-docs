# RefreshOptions

用于设置Refresh组件参数。

> **补充说明：**
> 
> - 当未设置builder或refreshingContent时，是通过更新子组件的translate属性实现的下拉
> 位移效果。下拉位移过程中不会触发子组件的
> onAreaChange事件。子组件设置
> translate属性时不会生效。
> 
> - 当设置了builder或refreshingContent时，是通过更新子组件相对于Refresh组件的位置实现的下拉位移效果。下拉位移过程中可以触发子组件的
> onAreaChange事件。子组件设置
> position属性时会固定子组件相对于Refresh组件的位置，导致子组件不会跟手进行下拉位移。
> 
> - 通过builder参数设置的自定义组件在未指定宽度和高度时，其尺寸将自适应子组件，在指定宽度而未指定高度时，其高度将自适应下拉距离。通过refreshingContent参数设置的自定义组件若未指定高度，其高度同样会自适应下拉
> 距离。当自定义组件高度自适应下拉距离时，随着下拉距离的增加，该组件的高度亦随之增加；当自定义组件的高度设定为固定值或自适应至最大高度时，随着下拉距离的增加，自定义组件与Refresh组件上边界之间的间距亦会随之增加。

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## builder

```TypeScript
builder?: CustomBuilder
```

自定义刷新区域显示内容。   
**说明：**API version 10及之前版本，自定义组件的高度限制在64vp之内。API version 11及以后版本没有此限制。 自定义组件设置了固定高度时，自定义组件会以固定高度显示在刷新区域下方；自定义组件未设置高度时，自定义组件高度会自适应刷新区域高度，会发生自定义组件高度跟随刷新区域变化至0的现象。 建议对自定义组件设置最小高度约束来避免自定义组件高度小于预期的情况发生，具体可参照 示例3。 从API version 12开始，建议使用refreshingContent参数替代builder参数自定义刷新区域显示内容，以避免刷新过程中因自定义组件销毁重建造成的动画中断问题。

**类型：** [CustomBuilder](arkts-arkui-custombuilder-t.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## friction

```TypeScript
friction?: number | string
```

下拉摩擦系数，取值范围为0到100。默认值：62  
- 0表示下拉刷新容器不跟随手势下拉而下拉。  
- 100表示下拉刷新容器紧紧跟随手势下拉而下拉。  
- 数值越大，下拉刷新容器跟随手势下拉的反应越灵敏。   
**说明：** 从API version 8开始支持，从API version 11开始废弃，建议使用 [pullDownRatio](arkts-arkui-refresh-attribute.md#pulldownratio)替代。

**类型：** number \| string

**起始版本：** 8

**废弃版本：** 11

**替代接口：** [pullDownRatio](arkts-arkui-refresh-attribute.md#pulldownratio)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: number | string
```

下拉起点距离组件顶部的距离。默认值：16，单位vp。类型为string时，需要显式指定像素单位，如'10px'；未指定像素单位时，如'10'，单位为vp。   
**说明：** 从API version 8开始支持，从API version 11开始废弃，无替代接口。
**说明：**offset取值范围[0vp,64vp]。大于64vp按照64vp处理。不支持百分比，不支持负数。

**类型：** number \| string

**起始版本：** 8

**废弃版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## promptText

```TypeScript
promptText?: ResourceStr
```

设置刷新区域底部显示的自定义文本。   
**说明：**输入文本的限制参考Text组件，使用builder或refreshingContent参数自定义刷新区域显示内容时，promptText不显示。 promptText设置有效时， [refreshOffset](arkts-arkui-refresh-attribute.md#refreshoffset)属性默认值为96vp。 自定义文本最大的字体缩放倍数 maxFontScale为2。

**类型：** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## refreshing

```TypeScript
refreshing: boolean
```

组件当前是否处于刷新中状态。true表示处于刷新中状态，false表示未处于刷新中状态。默认值：false该参数支持\$\$双向绑定变量。

**类型：** boolean

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## refreshingContent

```TypeScript
refreshingContent?: ComponentContent
```

自定义刷新区域显示内容。   
**说明：**与builder参数同时设置时builder参数不生效。 自定义组件设置了固定高度时，自定义组件会以固定高度显示在刷新区域下方；自定义组件未设置高度时，自定义组件高度会自适应刷新区域高度，会发生自定义组件高度跟随刷新区域变化至0的现象。 建议对自定义组件设置最小高度约束来避免自定义组件高度小于预期的情况发生，具体可参照 示例4。

**类型：** ComponentContent

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
