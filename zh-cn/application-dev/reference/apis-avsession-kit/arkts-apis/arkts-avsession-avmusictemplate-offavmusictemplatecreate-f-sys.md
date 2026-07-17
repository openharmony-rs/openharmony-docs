# offAVMusicTemplateCreate（系统接口）

## 导入模块

```TypeScript
import { avMusicTemplate } from '@kit.AVSessionKit';
```

## offAVMusicTemplateCreate

```TypeScript
function offAVMusicTemplateCreate(callback?: Callback<AVMusicTemplateDescriptor>): void
```

注销音频模板创建监听。

**起始版本：** 23

**需要权限：** ohos.permission.MANAGE_MEDIA_RESOURCES

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-avMusicTemplate-function offAVMusicTemplateCreate(callback?: Callback<AVMusicTemplateDescriptor>): void--><!--Device-avMusicTemplate-function offAVMusicTemplateCreate(callback?: Callback<AVMusicTemplateDescriptor>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<AVMusicTemplateDescriptor> | 否 | 回调函数，返回音频模板描述。不填该参数则注销该类型对应的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verify failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function offAVMusicTemplateCreate can not work correctly due to limited device capabilities. |

