# IRemoteAuthCallback（系统接口）

提供远端认证场景下获取WigetParam的接口。

**起始版本：** 26.0.0

<!--Device-userAuth-interface IRemoteAuthCallback--><!--Device-userAuth-interface IRemoteAuthCallback-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## onGetRemoteAuthWidgetParam

```TypeScript
onGetRemoteAuthWidgetParam: WidgetParamCallback
```

调用以获取远程身份验证的用户身份验证页面上显示的信息。

**类型：** WidgetParamCallback

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IRemoteAuthCallback-onGetRemoteAuthWidgetParam: WidgetParamCallback--><!--Device-IRemoteAuthCallback-onGetRemoteAuthWidgetParam: WidgetParamCallback-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**系统接口：** 此接口为系统接口。

## onRemoteAuthResult

```TypeScript
onRemoteAuthResult: ResultCallback
```

调用返回认证结果。如果鉴权成功。UserAuthResult中包含token信息。

**类型：** ResultCallback

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IRemoteAuthCallback-onRemoteAuthResult: ResultCallback--><!--Device-IRemoteAuthCallback-onRemoteAuthResult: ResultCallback-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**系统接口：** 此接口为系统接口。

