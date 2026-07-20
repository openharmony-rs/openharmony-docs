# SubWindowAttachOptions（系统接口）

子窗与主窗保持相对位置不变时的参数。

**起始版本：** 24

<!--Device-window-interface SubWindowAttachOptions--><!--Device-window-interface SubWindowAttachOptions-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { window } from '@kit.ArkUI';
```

## currentLayoutMode

```TypeScript
currentLayoutMode?: string
```

子窗当前布局模式，用于控制应用定制的UI效果。若不传，则默认为空字符串。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SubWindowAttachOptions-currentLayoutMode?: string--><!--Device-SubWindowAttachOptions-currentLayoutMode?: string-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

## isIntersectedHeightLimit

```TypeScript
isIntersectedHeightLimit?: boolean
```

是否使用处于协同关系中两个窗口的高度限制的交集。

**类型：** boolean

**默认值：** false

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SubWindowAttachOptions-isIntersectedHeightLimit?: boolean--><!--Device-SubWindowAttachOptions-isIntersectedHeightLimit?: boolean-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

## isIntersectedWidthLimit

```TypeScript
isIntersectedWidthLimit?: boolean
```

是否使用处于协同关系中两个窗口的宽度限制的交集。

**类型：** boolean

**默认值：** false

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SubWindowAttachOptions-isIntersectedWidthLimit?: boolean--><!--Device-SubWindowAttachOptions-isIntersectedWidthLimit?: boolean-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

## parentWindowSizeChangeCallback

```TypeScript
parentWindowSizeChangeCallback?: Callback<Size>
```

父窗大小变化的回调。绑定后立即回调一次，后续父窗大小变化时通知。默认不传，无法收到父窗大小变化通知。

**类型：** Callback&lt;Size&gt;

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SubWindowAttachOptions-parentWindowSizeChangeCallback?: Callback<Size>--><!--Device-SubWindowAttachOptions-parentWindowSizeChangeCallback?: Callback<Size>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

## parentWindowStatusChangeCallback

```TypeScript
parentWindowStatusChangeCallback?: Callback<WindowStatusType>
```

父窗模式变化的回调。绑定后立即回调一次，后续父窗模式变化时通知。默认不传，无法收到父窗模式变化通知。

**类型：** Callback&lt;WindowStatusType&gt;

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SubWindowAttachOptions-parentWindowStatusChangeCallback?: Callback<WindowStatusType>--><!--Device-SubWindowAttachOptions-parentWindowStatusChangeCallback?: Callback<WindowStatusType>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

