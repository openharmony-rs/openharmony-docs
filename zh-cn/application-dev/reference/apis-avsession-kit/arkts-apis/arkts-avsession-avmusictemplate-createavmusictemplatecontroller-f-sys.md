# createAVMusicTemplateController（系统接口）

## 导入模块

```TypeScript
import { avMusicTemplate } from '@kit.AVSessionKit';
```

## createAVMusicTemplateController

```TypeScript
function createAVMusicTemplateController(sessionId: string): AVMusicTemplateController
```

创建音频模板控制器，返回音频模板控制器对象。

**起始版本：** 23

**需要权限：** ohos.permission.MANAGE_MEDIA_RESOURCES

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-avMusicTemplate-function createAVMusicTemplateController(sessionId: string): AVMusicTemplateController--><!--Device-avMusicTemplate-function createAVMusicTemplateController(sessionId: string): AVMusicTemplateController-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | string | 是 | AVSession对象唯一的会话标识。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AVMusicTemplateController](arkts-avsession-avmusictemplate-avmusictemplatecontroller-c.md) | 音频模板控制器实例，用于与接入音频模板的媒体应用进行数据交互。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verify failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function createAVMusicTemplateController can not work correctly due to limited device capabilities. |
| [35000002](../errorcode-avmusictemplate.md#35000002-音频模板控制器创建失败) | Failed to create the AVMusicTemplate controller. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |

