# UserAuthIcon

**userAuthIcon**模块是OpenHarmony用户身份认证体系（UserIAM）的UI组件模块，提供了一个开箱即用的身份认证图标组件（UserAuthIcon）。该组件用于在应用UI中展示人脸认证或指纹认证的图标，支持自定义图标颜色和尺寸，并可在点击图标时直接启动系统身份认证弹窗组件。

该模块主要用于以下场景：

- 在应用界面中快速集成人脸或指纹认证入口。  
- 需要统一风格的生物特征认证图标展示。  
- 点击图标即可触发系统级身份认证流程。

**起始版本：** 12

**装饰器类型：** @Component

<!--Device-unnamed-export default struct UserAuthIcon--><!--Device-unnamed-export default struct UserAuthIcon-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## 导入模块

```TypeScript
import { UserAuthIcon } from '@kit.UserAuthenticationKit';
```

## authParam

```TypeScript
authParam: userAuth.AuthParam
```

用户认证相关参数。包含挑战值(challenge)、认证类型列表(authType)、认证可信等级(authTrustLevel)等配置。挑战值用于防重放攻击，认证类型指定可用的认证方式（如人脸、指纹、PIN），认证可信等级决定认证的安全强度。

**类型：** userAuth.AuthParam

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UserAuthIcon-authParam: userAuth.AuthParam--><!--Device-UserAuthIcon-authParam: userAuth.AuthParam-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## iconColor

```TypeScript
iconColor?: ResourceColor
```

图标颜色。设置认证图标的颜色，支持颜色值、资源引用等多种格式。默认使用系统激活色，开发者可根据应用主题自定义颜色，如使用Color.Blue或$r('app.color.primary')。

**类型：** ResourceColor

**默认值：** $r('sys.color.ohos_id_color_activated')

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UserAuthIcon-iconColor?: ResourceColor--><!--Device-UserAuthIcon-iconColor?: ResourceColor-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## iconHeight

```TypeScript
iconHeight?: Dimension
```

图标高度。设置认证图标的高度，宽高比为1:1（即高度和宽度相等）。默认值为64fp，不支持百分比字符串。建议根据界面布局选择合适的大小。

**类型：** Dimension

**默认值：** 64fp

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UserAuthIcon-iconHeight?: Dimension--><!--Device-UserAuthIcon-iconHeight?: Dimension-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## onAuthResult

```TypeScript
onAuthResult: (result: userAuth.UserAuthResult) => void
```

认证结果回调。用户完成认证后触发此回调，回调参数包含认证结果码(result)、认证令牌(token)、认证类型(authType)等信息。应用需在此回调中处理认证结果，如认证通过时获取token用于后续安全操作，认证失败时提示用户重新尝试。

**注意：** 应用需申请`ohos.permission.ACCESS_BIOMETRIC`权限，否则应用将仅展示图标，无法正常拉起身份认证控件。

**类型：** (result: userAuth.UserAuthResult) =&gt; void

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UserAuthIcon-onAuthResult: (result: userAuth.UserAuthResult) => void--><!--Device-UserAuthIcon-onAuthResult: (result: userAuth.UserAuthResult) => void-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## onIconClick

```TypeScript
onIconClick?: () => void
```

图标点击回调。用户点击认证图标时触发此回调，可在回调中执行点击前的准备工作或记录用户行为日志。如果未设置此回调，点击图标后直接触发认证流程。

**类型：** () =&gt; void

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UserAuthIcon-onIconClick?: () => void--><!--Device-UserAuthIcon-onIconClick?: () => void-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## widgetParam

```TypeScript
widgetParam: userAuth.WidgetParam
```

用户认证界面配置相关参数。包含认证界面标题(title)、导航按钮文本(navigationButtonText)等配置，用于自定义认证弹窗的显示内容。

**类型：** userAuth.WidgetParam

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UserAuthIcon-widgetParam: userAuth.WidgetParam--><!--Device-UserAuthIcon-widgetParam: userAuth.WidgetParam-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

