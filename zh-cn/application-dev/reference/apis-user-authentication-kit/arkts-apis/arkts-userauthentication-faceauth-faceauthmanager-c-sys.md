# FaceAuthManager(人脸认证)（系统接口）

人脸认证管理器对象。用于提供人脸录入过程中的管理功能，目前支持设置人脸预览界面的Surface ID。

**起始版本：** 23

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

**起始版本：** 23

<!--Device-FaceAuthManager-constructor()--><!--Device-FaceAuthManager-constructor()-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.FaceAuth

**系统接口：** 此接口为系统接口。

**示例**

```TypeScript
import { faceAuth } from '@kit.UserAuthenticationKit';

let faceAuthManager = new faceAuth.FaceAuthManager();
```

## setSurfaceId

```TypeScript
setSurfaceId(surfaceId: string): void
```

用于在录入人脸时设置人脸预览界面的Surface ID。该接口需要配合 [addCredential](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-useridentitymanager-c-sys.md#addcredential)使用，通过 getXComponentSurfaceId组件的Surface来显示人脸预览画面。

**起始版本：** 23

**需要权限：** ohos.permission.MANAGE_USER_IDM

<!--Device-FaceAuthManager-setSurfaceId(surfaceId: string): void--><!--Device-FaceAuthManager-setSurfaceId(surfaceId: string): void-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.FaceAuth

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| surfaceId | string | 是 | XComponent持有Surface的ID。用于在人脸录入过程中显示人脸 预览画面。 <br>**说明：**需在XComponent完成初始化后，通过getXComponentSurfaceId方法 获取有效的surfaceId，若传入无效的surfaceId可能导致预览画面无法正常显示或接口调用失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12700001](../errorcode-useriam.md#12700001-人脸服务不可用) | The service is unavailable. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied. Called by non-system application. |

**示例**

```TypeScript
import { faceAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 该surfaceId应通过XComponentController.getXComponentSurfaceId()方法从XComponent控件获取，此处仅用作示例。
let surfaceId = '123456';
let faceManager = new faceAuth.FaceAuthManager();
try {
  faceManager.setSurfaceId(surfaceId);
  console.info('set surface id successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`set surface id failed, Code is ${err?.code}, message is ${err?.message}`);
}
```

