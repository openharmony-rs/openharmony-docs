# getUserAuthWidgetMgr（系统接口）

## 导入模块

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

<a id="getuserauthwidgetmgr"></a>
## getUserAuthWidgetMgr

```TypeScript
function getUserAuthWidgetMgr(version: number): UserAuthWidgetMgr
```

获取身份认证组件管理器对象。用于获取UserAuthWidgetMgr实例，通过该实例可将自定义身份认证控件注册到系统进行统一管理。

> **说明：**  
>  
> 每个UserAuthWidgetMgr实例可管理一个身份认证控件，若需要管理多个控件则需获取多个实例。

**起始版本：** 10

**需要权限：** ohos.permission.SUPPORT_USER_AUTH

<!--Device-userAuth-function getUserAuthWidgetMgr(version: int): UserAuthWidgetMgr--><!--Device-userAuth-function getUserAuthWidgetMgr(version: int): UserAuthWidgetMgr-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| version | number | 是 | 身份认证组件的版本号。用于指定组件的版本，目前支持版本1。组件版本决定了组件与框架之间的通信协议和功能支持范围。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [UserAuthWidgetMgr](arkts-userauthentication-userauth-userauthwidgetmgr-i-sys.md) | 身份认证组件管理器对象。可用于订阅和取消订阅来自用户认证框架的命令。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied. Called by non-system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [12500002](../errorcode-useriam.md#12500002-身份认证系统通用错误码) | General operation error. |

**示例：**

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let userAuthWidgetMgrVersion = 1;
try {
  let userAuthWidgetMgr = userAuth.getUserAuthWidgetMgr(userAuthWidgetMgrVersion);
  console.info('get userAuthWidgetMgr instance successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`userAuth widgetMgr failed. Code is ${err?.code}, message is ${err?.message}`);
}

```

