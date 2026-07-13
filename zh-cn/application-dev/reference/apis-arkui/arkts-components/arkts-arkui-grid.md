# Grid

网格容器，由“行”和“列”分割的单元格所组成，通过指定“项目”所在的单元格做出各种各样的布局。

> **说明：**

> 组件内部已绑定手势实现跟手滚动等功能，需要增加自定义手势操作时请参考[手势拦截增强]{@link common}进行处理。


## Grid

```TypeScript
Grid(scroller?: Scroller, layoutOptions?: GridLayoutOptions)
```

创建网格容器。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scroller | Scroller | 否 | 可滚动组件的控制器。用于与可滚动组件进行绑定。<br/>**说明：** <br/>不允许和其他滚动类组件，如：[ArcList]{@link @ohos.arkui.ArcList}、[List]{@link list}、[Grid]{@link grid}、[Scroll]{@link scroll}和[WaterFlow]{@link water_flow}绑定同一个滚动控制对象。 |
| layoutOptions | GridLayoutOptions | 否 | Grid布局选项。 |

## 汇总

- [ComputedBarAttribute](arkts-arkui-grid-computedbarattribute-i.md)
- [GridLayoutOptions](arkts-arkui-grid-gridlayoutoptions-i.md)
- [StartLineInfo](arkts-arkui-grid-startlineinfo-i-sys.md)
- [UIGridEvent](arkts-arkui-grid-uigridevent-i.md)
- [OnGetStartIndexByIndexCallback](arkts-arkui-grid-ongetstartindexbyindexcallback-t-sys.md)
- [OnGetStartIndexByOffsetCallback](arkts-arkui-grid-ongetstartindexbyoffsetcallback-t-sys.md)
- [OnGridScrollIndexCallback](arkts-arkui-grid-ongridscrollindexcallback-t.md)
- [GridDirection](arkts-arkui-grid-griddirection-e.md)
- [GridItemAlignment](arkts-arkui-grid-griditemalignment-e.md)
