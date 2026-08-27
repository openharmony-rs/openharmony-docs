# WebLayoutMode

Web布局模式的配置，用于控制Web内容的页面布局方式，帮助开发者根据屏幕尺寸和显示需求优化网页的适配性和用户体验。

**起始版本：** 11

**系统能力：** SystemCapability.Web.Webview.Core

## NONE

```TypeScript
NONE = 0
```

Web布局跟随系统。适用于传统网页布局场景，保持与系统默认行为一致。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## FIT_CONTENT

```TypeScript
FIT_CONTENT = 1
```

Web基于页面大小的自适应网页布局。适用于需要根据屏幕尺寸自动调整布局的场景，推荐用于移动端网页优化。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core
