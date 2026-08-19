# LineOptions

用于描述Line组件绘制属性。 > **说明：** > > 为规范匿名对象的定义，API 18版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素@since版本号高于内层元素版本号的情况，但这不影响接口的使用。

**起始版本：** 18

<!--Device-unnamed-interface LineOptions--><!--Device-unnamed-interface LineOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { CommonModifier, ColumnModifier, ColumnSplitModifier, RowModifier, RowSplitModifier, SideBarContainerModifier, BlankModifier, DividerModifier, GridColModifier, GridRowModifier, NavDestinationModifier, NavigatorModifier, StackModifier, NavigationModifier, NavRouterModifier, StepperItemModifier, TabsModifier, GridModifier, GridItemModifier, ListModifier, ListItemModifier, ListItemGroupModifier, ScrollModifier, SwiperModifier, WaterFlowModifier, ButtonModifier, CounterModifier, TextPickerModifier, TimePickerModifier, ToggleModifier, CalendarPickerModifier, CheckboxModifier, CheckboxGroupModifier, DatePickerModifier, RadioModifier, RatingModifier, SelectModifier, SliderModifier, PatternLockModifier, SpanModifier, RichEditorModifier, RefreshModifier, SearchModifier, TextAreaModifier, TextModifier, TextInputModifier, ImageSpanModifier, ImageAnimatorModifier, ImageModifier, VideoModifier, DataPanelModifier, GaugeModifier, LoadingProgressModifier, MarqueeModifier, ProgressModifier, QRCodeModifier, TextClockModifier, TextTimerModifier, LineModifier, PathModifier, PolygonModifier, PolylineModifier, RectModifier, ShapeModifier, AlphabetIndexerModifier, HyperlinkModifier, MenuModifier, MenuItemModifier, PanelModifier, SymbolGlyphModifier, AttributeUpdater, ContainerSpanModifier, SymbolSpanModifier, ParticleModifier, StepperModifier, UIPickerComponentModifier, ModifierUtils } from '@kit.ArkUI';
```

## height

```TypeScript
height?: Length
```

高度。 值为异常值或缺省时，根据startPoint和endPoint自动计算所需的绘制区域高度。 默认单位：vp

**类型：** Length

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-LineOptions-height?: Length--><!--Device-LineOptions-height?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: Length
```

宽度。 值为异常值或缺省时，根据startPoint和endPoint自动计算所需的绘制区域宽度。 默认单位：vp

**类型：** Length

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-LineOptions-width?: Length--><!--Device-LineOptions-width?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

