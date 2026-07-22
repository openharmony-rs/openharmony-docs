# FaceAuthManager（系统接口）

人脸认证管理器对象。用于提供人脸录入过程中的管理功能，包括设置人脸预览界面的Surface ID等。

**起始版本：** 9

<!--Device-faceAuth-class FaceAuthManager--><!--Device-faceAuth-class FaceAuthManager-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.FaceAuth

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { faceAuth } from '@kit.UserAuthenticationKit';
```

## constructor

```TypeScript
constructor()
```

用于创建人脸认证管理器对象。

**起始版本：** 9

<!--Device-FaceAuthManager-constructor()--><!--Device-FaceAuthManager-constructor()-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.FaceAuth

**系统接口：** 此接口为系统接口。

**示例：**

```TypeScript
import { faceAuth } from '@kit.UserAuthenticationKit';

let faceAuthManager = new faceAuth.FaceAuthManager();

```

## setSurfaceId

```TypeScript
setSurfaceId(surfaceId: string): void
```

用于在录入人脸时设置人脸预览界面的Surface ID。该接口需要配合[addCredential](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-useridentitymanager-c-sys.md#addcredential)使用，通过[getXComponentSurfaceId](../../apis-arkui/arkts-components/arkts-arkui-xcomponentcontroller-c.md#getxcomponentsurfaceid)组件的Surface来显示人脸预览画面。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_USER_IDM

<!--Device-FaceAuthManager-setSurfaceId(surfaceId: string): void--><!--Device-FaceAuthManager-setSurfaceId(surfaceId: string): void-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.FaceAuth

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| surfaceId | string | 是 | [XComponent](../../apis-arkui/arkts-components/arkts-arkui-xcomponentcontroller-c.md#getxcomponentsurfaceid) 持有 Surface 的 ID。用于在人脸录入过程中显示人脸预览画面，该ID需通过XComponentController的getXComponentSurfaceId方法获取。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied. Called by non-system application. |
| [12700001](../errorcode-useriam.md#12700001-人脸服务不可用) | The service is unavailable. |

**示例：**

```TypeScript
import { faceAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 该surfaceId应该从XComponent控件获取，此处仅用作示例。
let surfaceId = '123456';
let manager = new faceAuth.FaceAuthManager();
try {
  manager.setSurfaceId(surfaceId);
  console.info('set surface id successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`set surface id failed, Code is ${err?.code}, message is ${err?.message}`);
}

```

