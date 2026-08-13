# onAVMusicTemplateCreate（系统接口）

## onAVMusicTemplateCreate

```TypeScript
function onAVMusicTemplateCreate(callback: Callback<AVMusicTemplateDescriptor>): void
```

注册音频模板创建的监听。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_MEDIA_RESOURCES

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-avMusicTemplate-function onAVMusicTemplateCreate(callback: Callback<AVMusicTemplateDescriptor>): void--><!--Device-avMusicTemplate-function onAVMusicTemplateCreate(callback: Callback<AVMusicTemplateDescriptor>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AVMusicTemplateDescriptor](arkts-avsession-avmusictemplate-avmusictemplatedescriptor-i-sys.md)&gt; | 是 | 回调函数，参数为音频模板描述。用于监听音频模板创建事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function onAVMusicTemplateCreate can not work correctly due to limited device capabilities. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verify failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |

