# getAllAVMusicTemplateDescriptors（系统接口）

## getAllAVMusicTemplateDescriptors

```TypeScript
function getAllAVMusicTemplateDescriptors(userId?: int): AVMusicTemplateDescriptor[]
```

获取所有的音频模板描述，返回音频模板描述的集合。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_MEDIA_RESOURCES

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-avMusicTemplate-function getAllAVMusicTemplateDescriptors(userId?: int): AVMusicTemplateDescriptor[]--><!--Device-avMusicTemplate-function getAllAVMusicTemplateDescriptors(userId?: int): AVMusicTemplateDescriptor[]-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | int | 否 | 用户ID。以用户传递为准，可为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AVMusicTemplateDescriptor](arkts-avsession-avmusictemplate-avmusictemplatedescriptor-i-sys.md)[] | 音频模板描述的集合。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function getAllAVMusicTemplateDescriptors can not work correctly due to limited device capabilities. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verify failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |

