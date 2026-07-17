# SystemBarProperties

状态栏<!--Del-->、三键导航栏的<!--DelEnd-->属性。

**起始版本：** 6

<!--Device-window-interface SystemBarProperties--><!--Device-window-interface SystemBarProperties-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## 导入模块

```TypeScript
import { window } from '@kit.ArkUI';
```

## enableNavigationBarAnimation

```TypeScript
enableNavigationBarAnimation?: boolean
```

是否启用三键导航栏属性变化时的动画效果。true表示启用；false表示不启用。默认值：false。

<!--RP13--><!--RP13End-->

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SystemBarProperties-enableNavigationBarAnimation?: boolean--><!--Device-SystemBarProperties-enableNavigationBarAnimation?: boolean-End-->

**系统能力：** SystemCapability.Window.SessionManager

## enableStatusBarAnimation

```TypeScript
enableStatusBarAnimation?: boolean
```

是否启用状态栏属性变化时的动画效果。true表示启用；false表示不启用。默认值：false。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SystemBarProperties-enableStatusBarAnimation?: boolean--><!--Device-SystemBarProperties-enableStatusBarAnimation?: boolean-End-->

**系统能力：** SystemCapability.Window.SessionManager

## isNavigationBarLightIcon

```TypeScript
isNavigationBarLightIcon?: boolean
```

三键导航栏图标是否为高亮状态。true表示高亮；false表示不高亮。默认值：false。

<!--RP13--><!--RP13End-->

**类型：** boolean

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SystemBarProperties-isNavigationBarLightIcon?: boolean--><!--Device-SystemBarProperties-isNavigationBarLightIcon?: boolean-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## isStatusBarLightIcon

```TypeScript
isStatusBarLightIcon?: boolean
```

状态栏图标是否为高亮状态。true表示高亮；false表示不高亮。默认值：false。

**类型：** boolean

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SystemBarProperties-isStatusBarLightIcon?: boolean--><!--Device-SystemBarProperties-isStatusBarLightIcon?: boolean-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## navigationBarColor

```TypeScript
navigationBarColor?: string
```

三键导航栏背景颜色。作为入参时格式为十六进制RGB或ARGB颜色，不区分大小写，例如'#00FF00'或'#FF00FF00'；作为返回值时格式固定为ARGB颜色，如'#FF00FF00'，默认值为系统配置的颜色。

<!--RP13--><!--RP13End-->

**类型：** string

**起始版本：** 6

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SystemBarProperties-navigationBarColor?: string--><!--Device-SystemBarProperties-navigationBarColor?: string-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## navigationBarContentColor

```TypeScript
navigationBarContentColor?: string
```

三键导航栏文字颜色。当设置此属性后，`isNavigationBarLightIcon`属性设置无效。默认值：`'#E5FFFFFF'`。

<!--RP13--><!--RP13End-->

**类型：** string

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SystemBarProperties-navigationBarContentColor?: string--><!--Device-SystemBarProperties-navigationBarContentColor?: string-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## statusBarColor

```TypeScript
statusBarColor?: string
```

状态栏背景颜色。作为入参时格式为十六进制RGB或ARGB颜色，不区分大小写，例如'#00FF00'或'#FF00FF00'；作为返回值时格式固定为ARGB颜色，如'#FF00FF00'，默认值为系统配置的颜色。

**类型：** string

**起始版本：** 6

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SystemBarProperties-statusBarColor?: string--><!--Device-SystemBarProperties-statusBarColor?: string-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## statusBarContentColor

```TypeScript
statusBarContentColor?: string
```

状态栏文字颜色。当设置此属性后，`isStatusBarLightIcon`属性设置无效。默认值：`'#E5FFFFFF'`。

**类型：** string

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SystemBarProperties-statusBarContentColor?: string--><!--Device-SystemBarProperties-statusBarContentColor?: string-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

