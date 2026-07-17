# @ohos.userIAM.faceAuth

**faceAuth**模块是OpenHarmony用户身份认证体系（UserIAM）的重要组成部分，用于管理人脸录入功能。该模块提供了面部认证管理的核心API，使开发者能够在应用内录入和管理人脸信息。

该模块主要用于以下场景：

- 需要实现人脸录入功能的应用。  
- 需要与系统级身份认证服务集成的场景。  
- 需要自定义人脸预览界面的应用。

**起始版本：** 9

<!--Device-unnamed-declare namespace faceAuth--><!--Device-unnamed-declare namespace faceAuth-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.FaceAuth

## 导入模块

```TypeScript
import { faceAuth } from '@kit.UserAuthenticationKit';
```

## 汇总

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [FaceAuthManager](arkts-userauthentication-faceauth-faceauthmanager-c-sys.md) | 人脸认证管理器对象。用于提供人脸录入过程中的管理功能，包括设置人脸预览界面的Surface ID等。 |
<!--DelEnd-->

