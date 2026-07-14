# FloatViewProperties

标准悬浮窗窗口的属性。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Window.SessionManager

## avoidArea

```TypeScript
avoidArea: window.AvoidArea
```

标准悬浮窗内容的避让区域。

**注意：**

通过[setUIContext()](arkts-arkui-floatviewcontroller-i.md#setuicontext-1)或
[setUIContextByName()](arkts-arkui-floatviewcontroller-i.md#setuicontextbyname-1)加载的页面中，位于避让区域的组件将不响应手势事件，添加需要手势响应事件
的组件时，请注意避让这些区域。

**类型：** window.AvoidArea

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Window.SessionManager

## displayId

```TypeScript
displayId: number
```

标准悬浮窗所在屏幕ID。
取值限定为整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Window.SessionManager

## inSidebar

```TypeScript
inSidebar: boolean
```

标准悬浮窗是否在侧边栏中。true为在侧边栏中，false为不在侧边栏中。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Window.SessionManager

## templateType

```TypeScript
templateType: FloatViewTemplateType
```

标准悬浮窗的模板类型。

**类型：** FloatViewTemplateType

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Window.SessionManager

## windowId

```TypeScript
windowId: number
```

标准悬浮窗窗口ID。
取值限定为整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Window.SessionManager

## windowRect

```TypeScript
windowRect: window.Rect
```

标准悬浮窗窗口矩形区域。

**类型：** window.Rect

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Window.SessionManager

## windowScale

```TypeScript
windowScale: number
```

标准悬浮窗窗口缩放比例。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Window.SessionManager

