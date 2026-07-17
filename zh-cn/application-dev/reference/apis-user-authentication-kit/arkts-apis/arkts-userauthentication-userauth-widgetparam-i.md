# WidgetParam

用户认证界面配置相关参数。该接口用于配置认证界面的显示样式和交互方式，包括标题、导航按钮文本、窗口模式等。通过合理配置这些参数，可以为用户提供清晰的认证引导和良好的交互体验。

**起始版本：** 10

<!--Device-userAuth-interface WidgetParam--><!--Device-userAuth-interface WidgetParam-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## 导入模块

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## navigationButtonText

```TypeScript
navigationButtonText?: string
```

导航按键的说明文本，最大长度为60字符。点击该按钮可触发应用自定义的操作，如跳转到自定义认证页面或取消认证等。在单指纹、单人脸场景下支持，从API 18开始，增加支持人脸+指纹组合认证场景。默认为不展示自定义导航按键。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WidgetParam-navigationButtonText?: string--><!--Device-WidgetParam-navigationButtonText?: string-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## title

```TypeScript
title: string
```

用户认证界面的标题，建议传入认证目的，例如用于支付、登录应用等，不支持传空字串，最大长度为500字符。标题会显示在认证界面，帮助用户理解当前认证的目的，提升用户信任度和配合度。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WidgetParam-title: string--><!--Device-WidgetParam-title: string-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## uiContext

```TypeScript
uiContext?: Context
```

以模应用弹窗方式显示身份认证对话框，仅支持在2in1设备上使用。传入有效的uiContext后，认证对话框将以模应用弹窗方式显示，认证结果返回后应用需先获取控件释放消息（订阅[on('authTip')](arkts-userauthentication-userauth-userauthinstance-i.md#on-2)并等待WIDGET_RELEASED状态）才能弹出其他窗口。如果没有此参数或其他类型的设备，身份认证对话框将以模系统弹窗方式显示，此时控件释放后应用可直接进行后续操作。

**默认值：** 以模系统弹窗方式显示身份认证对话框。

**类型：** Context

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-WidgetParam-uiContext?: Context--><!--Device-WidgetParam-uiContext?: Context-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

