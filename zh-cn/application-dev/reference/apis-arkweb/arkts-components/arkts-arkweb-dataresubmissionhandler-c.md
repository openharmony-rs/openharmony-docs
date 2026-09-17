# DataResubmissionHandler

DataResubmissionHandler是Web组件中处理网页表单数据重新提交的处理类。当网页需要重新提交之前已发送的表单数据时，Web组件会通过`onDataResubmitted`事件回调提供DataResubmissionHandler实例给应用，允许应用决定是否重新提交表单数据或取消导航。

**起始版本：** 9

**系统能力：** SystemCapability.Web.Webview.Core

## cancel

```TypeScript
cancel(): void
```

取消重新发送表单数据。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

DataResubmissionHandler的构造函数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## resend

```TypeScript
resend(): void
```

重新发送表单数据。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Web.Webview.Core
