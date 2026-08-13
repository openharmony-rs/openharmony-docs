# IRemoteAuthCallback（系统接口）

远程认证回调接口。该接口用于远程认证场景，提供获取远程认证页面参数和返回认证结果的回调能力。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-userAuth-interface IRemoteAuthCallback--><!--Device-userAuth-interface IRemoteAuthCallback-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**系统接口：** 此接口为系统接口。

## onGetRemoteAuthWidgetParam

```TypeScript
onGetRemoteAuthWidgetParam: WidgetParamCallback
```

获取远程认证页面参数的回调函数。在远程设备发起认证请求时，系统会调用此回调获取认证界面配置参数。

**类型：** [WidgetParamCallback](arkts-userauthentication-userauth-widgetparamcallback-t-sys.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IRemoteAuthCallback-onGetRemoteAuthWidgetParam: WidgetParamCallback--><!--Device-IRemoteAuthCallback-onGetRemoteAuthWidgetParam: WidgetParamCallback-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**系统接口：** 此接口为系统接口。

## onRemoteAuthResult

```TypeScript
onRemoteAuthResult: ResultCallback
```

返回远程认证结果的回调函数。在远程认证完成后，系统会调用此回调将认证结果返回给发起方。

**类型：** [ResultCallback](arkts-userauthentication-userauth-resultcallback-t-sys.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IRemoteAuthCallback-onRemoteAuthResult: ResultCallback--><!--Device-IRemoteAuthCallback-onRemoteAuthResult: ResultCallback-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**系统接口：** 此接口为系统接口。

