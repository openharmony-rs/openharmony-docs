# ScrollBar属性/事件

除支持通用属性外，还支持以下属性：

**继承/实现关系：** ScrollBarAttribute extends CommonMethod<ScrollBarAttribute>

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## enableNestedScroll

```TypeScript
enableNestedScroll(enabled: Optional<boolean>)
```

设置滚动条是否嵌套滚动。用于多层滚动容器、嵌套列表等需要通过滚动条拖动内层可滚动组件并联动父级滚动的场景，仅当ScrollBar通过Scroller与可滚动组件绑定时生效。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 是否执行嵌套滚动。当需要在多层滚动容器之间传递滚动事件时设置为true；不需要嵌套滚动时设置为false。默认值：false |

## scrollBarColor

```TypeScript
scrollBarColor(color: Optional<ColorMetrics>)
```

设置滚动条的颜色，仅滚动条不放置子组件时生效。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-optional-t.md)&lt;ColorMetrics&gt; | 是 | 滚动条的颜色，仅滚动条不放置子组件时生效。默认值：ColorMetrics.numeric(0x66182431) |
