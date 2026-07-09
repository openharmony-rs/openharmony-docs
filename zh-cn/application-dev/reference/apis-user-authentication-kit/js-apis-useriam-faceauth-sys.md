# @ohos.userIAM.faceAuth (人脸认证)(系统接口)

<!--Kit: User Authentication Kit-->
<!--Subsystem: UserIAM-->
<!--Owner: @WALL_EYE-->
<!--Designer: @lichangting518-->
<!--Tester: @jane_lz-->
<!--Adviser: @zengyawen-->

**faceAuth**模块是OpenHarmony用户身份认证体系（UserIAM）的重要组成部分，用于管理人脸录入功能。该模块提供了面部认证管理的核心API，使开发者能够在应用内录入和管理人脸信息。

该模块主要用于以下场景：
- 需要实现人脸录入功能的应用。
- 需要与系统级身份认证服务集成的场景。
- 需要自定义人脸预览界面的应用。


> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
> - 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本模块为系统接口。

## 关键Class/Interface介绍

### 核心类

- **[FaceAuthManager](#faceauthmanager)**：faceAuth模块的核心管理类，提供了人脸录入过程中所需的基本功能。

主要功能包括：
- 创建面部认证管理器实例。
- 将人脸录入时预览页面的surface对象设置到人脸认证服务。

![类关系图](figures/uml_faceauth.png)

## API组合使用关系说明

使用faceAuth模块的典型流程如下：

```ts
// 以下为阐述调用逻辑的伪代码，仅提供步骤说明，不提供详细的可执行代码。
// 1. 创建FaceAuthManager实例。
let faceAuthManager = new faceAuth.FaceAuthManager();

// 2. 获取XComponent的surfaceId（通过XComponentController）。
let surfaceId = xComponentController.getXComponentSurfaceId();

// 3. 设置surfaceId用于人脸预览页面。
faceAuthManager.setSurfaceId(surfaceId);

// 4. 配合osAccount模块的addCredential完成人脸录入。
// osAccount.userIdentityManager.addCredential(...)
```

## 导入模块

```ts
import { faceAuth } from '@kit.UserAuthenticationKit';
```

## FaceAuthManager

人脸认证管理器对象。用于提供人脸录入过程中的管理功能，包括设置人脸预览界面的Surface ID等。

### constructor

constructor()

用于创建人脸认证管理器对象。

**系统能力：** SystemCapability.UserIAM.UserAuth.FaceAuth

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型                   | 说明                 |
| ---------------------- | -------------------- |
| [FaceAuthManager](#faceauthmanager) | 人脸认证管理器对象。创建后可调用setSurfaceId方法设置人脸预览界面。 |

**示例：**

```ts
import { faceAuth } from '@kit.UserAuthenticationKit';

let faceAuthManager = new faceAuth.FaceAuthManager();
```

### setSurfaceId

setSurfaceId(surfaceId: string): void

用于在录入人脸时设置人脸预览界面的Surface ID。该接口需要配合[addCredential](../apis-basic-services-kit/js-apis-osAccount-sys.md#addcredential8)使用，通过[getXComponentSurfaceId](../apis-arkui/arkui-ts/ts-basic-components-xcomponent.md#getxcomponentsurfaceid9)组件的Surface来显示人脸预览画面。

**系统能力：** SystemCapability.UserIAM.UserAuth.FaceAuth

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.MANAGE_USER_IDM

**参数：**

| 参数名         | 类型                               | 必填 | 说明                       |
| -------------- | ---------------------------------- | ---- | -------------------------- |
| surfaceId       | string     | 是   | [XComponent](../apis-arkui/arkui-ts/ts-basic-components-xcomponent.md#getxcomponentsurfaceid9) 持有 Surface 的 ID。用于在人脸录入过程中显示人脸预览画面，该ID需通过XComponentController的getXComponentSurfaceId方法获取。 |

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[用户认证错误码](errorcode-useriam.md)。

**错误码：**

| 错误码ID | 错误信息 |
| -------- | ------- |
| 201 | Permission denied. |
| 202 | Permission denied. Called by non-system application. |
| 12700001 | The service is unavailable. |

**示例：**

```ts
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
