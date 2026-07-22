# FloatViewProperties

标准悬浮窗窗口的属性。

**起始版本：** 26.0.0

<!--Device-floatView-interface FloatViewProperties--><!--Device-floatView-interface FloatViewProperties-End-->

**系统能力：** SystemCapability.Window.SessionManager

## 导入模块

```TypeScript
import { floatView } from '@kit.ArkUI';
```

## avoidArea

```TypeScript
avoidArea: window.AvoidArea
```

标准悬浮窗内容的避让区域。

**注意：**

通过[setUIContext()](arkts-arkui-floatview-floatviewcontroller-i.md#setuicontext)或[setUIContextByName()](arkts-arkui-floatview-floatviewcontroller-i.md#setuicontextbyname)加载的页面中，位于避让区域的组件将不响应手势事件，添加需要手势响应事件的组件时，请注意避让这些区域。

**类型：** window.AvoidArea

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatViewProperties-avoidArea: window.AvoidArea--><!--Device-FloatViewProperties-avoidArea: window.AvoidArea-End-->

**系统能力：** SystemCapability.Window.SessionManager

## displayId

```TypeScript
displayId: number
```

标准悬浮窗所在屏幕ID。取值限定为整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatViewProperties-displayId: int--><!--Device-FloatViewProperties-displayId: int-End-->

**系统能力：** SystemCapability.Window.SessionManager

## inSidebar

```TypeScript
inSidebar: boolean
```

标准悬浮窗是否在侧边栏中。true为在侧边栏中，false为不在侧边栏中。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatViewProperties-inSidebar: boolean--><!--Device-FloatViewProperties-inSidebar: boolean-End-->

**系统能力：** SystemCapability.Window.SessionManager

## templateType

```TypeScript
templateType: FloatViewTemplateType
```

标准悬浮窗的模板类型。

**类型：** FloatViewTemplateType

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatViewProperties-templateType: FloatViewTemplateType--><!--Device-FloatViewProperties-templateType: FloatViewTemplateType-End-->

**系统能力：** SystemCapability.Window.SessionManager

## windowId

```TypeScript
windowId: number
```

标准悬浮窗窗口ID。取值限定为整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatViewProperties-windowId: int--><!--Device-FloatViewProperties-windowId: int-End-->

**系统能力：** SystemCapability.Window.SessionManager

## windowRect

```TypeScript
windowRect: window.Rect
```

标准悬浮窗窗口矩形区域。

**类型：** window.Rect

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatViewProperties-windowRect: window.Rect--><!--Device-FloatViewProperties-windowRect: window.Rect-End-->

**系统能力：** SystemCapability.Window.SessionManager

## windowScale

```TypeScript
windowScale: number
```

标准悬浮窗窗口缩放比例。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatViewProperties-windowScale: double--><!--Device-FloatViewProperties-windowScale: double-End-->

**系统能力：** SystemCapability.Window.SessionManager

